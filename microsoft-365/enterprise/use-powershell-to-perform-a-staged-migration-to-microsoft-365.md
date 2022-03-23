---
title: Brug PowerShell til at udføre en faseindret migrering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Få mere at vide om, hvordan du bruger PowerShell til at flytte indhold fra et kildemailsystem over tid ved hjælp af en faseindret migrering Microsoft 365.
ms.openlocfilehash: 562dcb8f32a0cd2b8452f2145dcb608dac353e2f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63590330"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en faseindret migrering til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan over tid overføre indholdet af brugerpostkasser fra et kildemailsystem til en Microsoft 365 ved hjælp af en faseindret migrering.

I denne artikel får du en gennemgang af de opgaver, der er involveret i en faseindret migrering af mail ved Exchange Online PowerShell. Dette emne, [Hvad du bør vide om en faseind faseindret mailoverførsel](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration), giver dig et overblik over overførselsprocessen. Når du er fortrolig med indholdet af den pågældende artikel, skal du bruge denne for at starte overførslen af postkasser fra ét mailsystem til et andet.

> [!NOTE]
> Du kan også bruge Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Administration til at</a> udføre faseinddelagt migrering. Se [Udfør en faseindindret migrering af mail for at Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tidspunkt for at fuldføre denne opgave: 2-5 minutter til at oprette en overførselsbatch. Når overførselsbatchen startes, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan finde oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser Microsoft 365, under [Ydeevne for overførsel](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Hvis du vil se, hvilke tilladelser du skal bruge, skal du se posten "Overførsel" [i emnet Modtageretilladelser](/exchange/recipients-permissions-exchange-2013-help) .

For at bruge Exchange Online PowerShell-cmdlet'er skal du logge på og importere cmdlet'er til din lokale Windows PowerShell session. Se [Forbind at Exchange Online bruge Remote PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få en vejledning.

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-a-staged-migration"></a>Trin 1: Forberede en faseindindret migrering

Før du overfører postkasser til Microsoft 365 ved hjælp af en faseindret migrering, er der nogle få ændringer, du skal foretage i dit Exchange miljø.

 **Konfigurer Outlook** hvor som helst i din lokale Exchange Server Tjenesten til overførsel af mail bruger Outlook Anywhere (også kaldet RPC over HTTP) til at oprette forbindelse til din lokale Exchange Server. Hvis du vil have mere at vide om, Outlook konfigurere et vilkårligt sted Exchange Server 2007 og Exchange 2003, skal du se følgende:

- [Exchange 2007: Sådan aktiveres Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Sådan konfigurerer du Outlook hvor som helst med Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Du skal bruge et certifikat udstedt af et pålideligt nøglecenter sammen med din Outlook hvor som helst.. Outlook Hvor som helst kan ikke konfigureres med et selv signeret certifikat. Du kan få mere at vide [under Sådan konfigureres SSL til Outlook hvor som helst](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Valgfrit: Kontrollér,** at du kan oprette forbindelse til din Exchange ved hjælp af Outlook overalt Prøv en af følgende metoder til at afprøve forbindelsesindstillingerne.

- Brug Outlook uden for virksomhedens netværk til at oprette forbindelse til din lokale Exchange postkasse.

- Brug [Microsoft Remote Connectivity Analyzer til at](https://https://testconnectivity.microsoft.com/) teste dine forbindelsesindstillinger. Brug Outlook overalt (RPC over HTTP) eller Outlook Autodiscover-test.

- Kør følgende kommandoer i Exchange Online PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Angiv tilladelser** Den lokale brugerkonto, du bruger til at oprette forbindelse til din lokale Exchange-organisation (også kaldet overførselsadministratoren), skal have de nødvendige tilladelser til at få adgang til de lokale postkasser, du vil overføre til Microsoft 365. Denne brugerkonto bruges, når du opretter forbindelse til dit mailsystem ved at oprette et overførselsslutpunkt senere i denne procedure [Trin 3: Oprette et overførselsslutpunkt](#step-3-create-a-migration-endpoint).

Administratoren skal have et af følgende tilladelsessæt for at kunne overføre postkasserne:

- Være medlem af **gruppen Domæneadministratorer** i Active Directory i den lokale organisation.

    eller

- Have fået **tildelt FullAccess-tilladelse** for hver lokal postkasse og **WriteProperty-tilladelse** for at ændre **TargetAddress-egenskaben** på brugerkonti i det lokale miljø.

    eller

- Have fået tildelt **Receive As-tilladelse** for den lokale postkassedatabase, der lagrer brugerpostkasser, og **WriteProperty-tilladelse** for at ændre **TargetAddress-egenskaben** på brugerkonti i det lokale miljø.

Du kan finde en vejledning til at angive disse tilladelser [i Tildel tilladelser til at overføre postkasser for at Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Deaktivere UM (Unified Messaging)** Hvis UM er aktiveret for de lokale postkasser, du overfører, skal du slå UM fra før overførslen. Slå UM til for postkasserne, når overførslen er fuldført. Du kan finde en vejledning under [Unified Messaging, der kan downloades](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Brug katalogsynkronisering til at oprette nye brugere i Microsoft 365.** Du bruger katalogsynkronisering til at oprette alle de lokale brugere i Microsoft 365 organisation.

Du skal give brugerne licens, efter de er blevet oprettet. Du har 30 dage, efter at brugerne er blevet oprettet, til at tilføje licenser. Du kan finde trin til at tilføje licenser [under Trin 8: Udføre opgaver efter overførslen](#step-8-complete-post-migration-tasks).

 Du kan bruge enten synkroniseringsværktøjet til Microsoft Azure Active Directory (Azure AD) eller Microsoft Azure AD-synkroniseringstjenester til at synkronisere og oprette dine lokale brugere Microsoft 365. Når postkasserne er overført til Microsoft 365, administrerer du brugerkonti i din lokale organisation, og de synkroniseres med din Microsoft 365 organisation. Du kan finde flere oplysninger [iDirectory Integration](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Trin 2: Oprette en CSV-fil til en faseind faseindret overførselsbatch

Når du har identificeret de brugere, hvis lokale postkasser du vil overføre til Microsoft 365, skal du bruge en fil med kommaseparerede værdier (CSV-fil) til at oprette en overførselsbatch. Hver række i CSV-filen – som Microsoft 365 bruges til at køre overførslen – indeholder oplysninger om en lokal postkasse.

> [!NOTE]
> Der er ikke nogen grænse for antallet af postkasser, du kan overføre til en Microsoft 365 hjælp af en faseindret migrering. CSV-filen til en overførselsbatch kan maksimalt indeholde 2.000 rækker. Hvis du vil overføre mere end 2.000 postkasser, skal du oprette flere CSV-filer og bruge hver fil til at oprette en ny overførselsbatch.

 **Understøttede attributter**

CSV-filen for en faseindret migrering understøtter følgende tre attributter. Hver række i CSV-filen svarer til en postkasse og skal indeholde en værdi for hver af disse attributter.

|**Attribut**|**Beskrivelse**|**Påkrævet?**|
|:-----|:-----|:-----|
|Mailadresse  <br/> |Angiver den primære SMTP-mailadresse, f.pilarp@contoso.com, til postkasser i det lokale miljø.  <br/> Brug den primære SMTP-adresse til postkasser i det lokale miljø og ikke bruger-id'er Microsoft 365. Hvis det lokale domæne f.eks. hedder contoso.com men Microsoft 365-maildomænet hedder service.contoso.com, skal du bruge contoso.com-domænenavnet til mailadresser i CSV-filen.  <br/> |Påkrævet  <br/> |
|Adgangskode  <br/> |Adgangskoden skal angives for den nye Microsoft 365 postkasse. Eventuelle adgangskodebegrænsninger, der gælder for din Microsoft 365, gælder også for adgangskoder i CSV-filen.  <br/> |Valgfrit  <br/> |
|GennemtvingÆndringAdgangskode  <br/> |Angiver, om en bruger skal ændre adgangskoden, første gang der logges på den nye Microsoft 365 postkasse. Brug **Sand** eller **Falsk** til værdien af denne parameter. <br/> > [!NOTE]> Hvis du har implementeret en løsning med enkelt logon (SSO) ved at udrulle Ad FS (Active Directory Federation Services) eller højere i din lokale organisation, skal du bruge **False** som værdi for **attributten ForceChangePassword** .          |Valgfrit  <br/> |

 **CSV-filformat**

Her er et eksempel på det korrekte format for CSV-filen. I dette eksempel overføres tre lokale postkasser til Microsoft 365.

I den første række, eller overskriftsrækken, i CSV-filen vises navnene på de attributter eller felter, der er angivet i de efterfølgende rækker. De enkelte attributnavne er adskilt af et komma.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Hver række under kolonneoverskriften repræsenterer én bruger og angiver de oplysninger, der skal bruges til at overføre brugerens postkasse. Attributværdierne i hver række skal stå i samme rækkefølge som attributnavnene i kolonneoverskriften.

Brug en teksteditor eller et program, f.eks. Excel , til at oprette CSV-filen. Gem filen som en .csv eller .txt fil.

> [!NOTE]
> Hvis CSV-filen indeholder ikke-ASCII-tegn eller specialtegn, skal du gemme CSV-filen med UTF-8-kodning eller en anden Unicode-kodning. Afhængigt af programmet kan det være nemmere at gemme CSV-filen med UTF-8-kodning eller en anden Unicode-kodning, når systemets landesprog på computeren stemmer overens med det sprog, der bruges i CSV-filen.

### <a name="step-3-create-a-migration-endpoint"></a>Trin 3: Oprette et overførselsslutpunkt

For at overføre mails korrekt skal Microsoft 365 oprette forbindelse til og kommunikere med kildemailsystemet. For at gøre dette Microsoft 365 et overførselsslutpunkt. Hvis du vil oprette Outlook hvor som helst overførselsslutpunkt ved hjælp af PowerShell, skal du først [oprette forbindelse til Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

Hvis du vil oprette Outlook slutpunkt for overførsel overalt kaldet "StagedEndpoint" Exchange Online PowerShell, skal du køre følgende kommandoer:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Du kan finde flere oplysninger **om New-MigrationEndpoint-cmdlet'en** [iNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> **New-MigrationEndpoint-cmdletten** kan bruges til at angive en database for tjenesten, der skal bruges, ved hjælp **af indstillingen -TargetDatabase**. Ellers tildeles en database tilfældigt fra Active Directory Federation Services (AD FS) 2.0-webstedet, hvor administrationspostkassen er placeret.

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

I Exchange Online PowerShell skal du køre følgende kommando for at få vist oplysninger om overførselsslutpunktet "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Trin 4: Oprette og starte en faseoverførselsbatch

Du kan bruge **New-MigrationBatch-cmdlet'en** i Exchange Online PowerShell til at oprette en overførselsbatch til en cutover-overførsel. Du kan oprette en overførselsbatch og starte den automatisk ved at medtage _autostartparameteren_ . Du kan også oprette overførselsbatchen og derefter starte den manuelt bagefter ved hjælp af **cmdlet'en Start-MigrationBatch** . I dette eksempel oprettes en overførselsbatch kaldet "StagedBatch1" og bruger overførselsslutpunktet, der blev oprettet i forrige trin.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

I dette eksempel oprettes også en overførselsbatch ved navn "StagedBatch1" og bruges til overførselsslutpunktet, der blev oprettet i forrige trin. Da  _autostartparameteren_ ikke er inkluderet, skal overførselsbatchen startes manuelt på dashboardet for overførsel eller ved hjælp af cmdlet'en **Start-MigrationBatch** . Som nævnt tidligere kan der kun findes én enkelt overførselsbatch ad gangen.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Kør følgende kommando i Exchange Online PowerShell for at vise oplysninger om "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Du kan også kontrollere, at batchen er startet, ved at køre følgende kommando:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Du kan finde flere oplysninger **om Get-MigrationBatch-cmdlet'en** [underGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Trin 5: Konvertér lokale postkasser til mailaktiverede brugere

Når du har overført en batch af postkasser, skal du bruge en metode til at give brugerne adgang til deres mail. En bruger, hvis postkasse er blevet overført, har nu både en postkasse lokalt og en Microsoft 365. Brugere, der har en postkasse i Microsoft 365, stopper med at modtage nye mails i deres lokale postkasse.

Da du ikke er færdig med dine overførselr, er du endnu ikke klar til at dirigere alle brugere til Microsoft 365 efter deres mail. Så hvad gør du for de personer, der har begge dele? Det, du kan gøre, er at ændre de lokale postkasser, du allerede har overført til mailaktiverede brugere. Når du skifter fra en postkasse til en mailaktiveret bruger, kan du dirigere brugeren til Microsoft 365 efter sin mail i stedet for at gå til brugerens lokale postkasse.

En anden vigtig grund til at konvertere lokale postkasser til mailaktiverede brugere er at bevare proxyadresser fra Microsoft 365-postkasserne ved at kopiere proxyadresser til de mailaktiverede brugere. Dette giver dig mulighed for at administrere skybaserede brugere fra din lokale organisation ved hjælp af Active Directory. Hvis du beslutter dig for at afvikle din lokale Exchange Server-organisation, efter at alle postkasser er overført til Microsoft 365, forbliver de proxyadresser, du har kopieret til de mailaktiverede brugere, i dit lokale Active Directory.

### <a name="step-6-delete-a-staged-migration-batch"></a>Trin 6: Slet en faseinddeindret overførselsbatch

 Når alle postkasser i en overførselsbatch er blevet overført, og du har konverteret de lokale postkasser i batchen til mailaktiverede brugere, er du klar til at slette en faseindstillet overførselsbatch. Sørg for at kontrollere, at mail bliver videresendt til Microsoft 365 postkasser i overførselsbatchen. Når du sletter en faseinddeindret overførselsbatch, rydder overførselstjenesten op i poster med relation til overførselsbatchen og sletter overførselsbatchen.

Hvis du vil slette overførselsbatchen "StagedBatch1" Exchange Online PowerShell, skal du køre følgende kommando.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Du kan finde flere oplysninger **om cmdlet'en Remove-MigrationBatch** [underRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Kør følgende kommando i Exchange Online PowerShell for at vise oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

Kommandoen returnerer enten overførselsbatchen med statussen **Fjerner, eller** den returnerer en fejl om, at overførselsbatchen ikke blev fundet, og bekræfter, at batchen er blevet slettet.

Du kan finde flere oplysninger **om Get-MigrationBatch-cmdlet'en** [underGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Trin7: Tildel licenser til Microsoft 365 brugere

Aktivér Microsoft 365 brugerkonti for de overførte konti ved at tildele licenser. Hvis du ikke tildeler en licens, deaktiveres postkassen, når prøveperioden udløber (efter 30 dage). Hvis du vil tildele en licens Microsoft 365 Administration, skal du [se Tildele eller fjerne tildeling af licenser](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Trin 8: Udføre opgaver efter overførslen

- **Opret en Autodiscover DNS-post, så brugerne nemt kan få adgang til deres postkasser.** Når alle lokale postkasser er blevet overført til Microsoft 365, kan du konfigurere en Autodiscover DNS-post for din Microsoft 365-organisation, så brugerne nemt kan oprette forbindelse til deres nye Microsoft 365-postkasser med Outlook og mobilklienter. Denne nye Autodiscover DNS-post skal bruge det samme navneområde, som du bruger til din Microsoft 365 organisation. Hvis f.eks. dit skybaserede navneområde er cloud.contoso.com, er Autodiscover DNS-posten, du skal oprette, autodiscover.cloud.contoso.com.

    Microsoft 365 anvender en CNAME-post til at implementere Autodiscover-tjenesten for Outlook og mobilklienter. Autodiscover CNAME-posten skal indeholde følgende oplysninger:

  - **Alias:** autodiscover

  - **Destination:** autodiscover.outlook.com

    Få mere at vide under [Tilføj DNS-poster for at forbinde dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Udrævn lokale servere Exchange serverne.** Når du har bekræftet, at alle mails dirigeres direkte til Microsoft 365-postkasserne, og du ikke længere har brug for at bevare din lokale mailorganisation eller ikke har planer om implementering af en SSO-løsning, kan du fjerne Exchange fra dine servere og fjerne din lokale Exchange-organisation.

    Brug nedenstående links til at få flere oplysninger:

  - [Ændre eller fjerne Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Sådan fjernes en Exchange 2007-organisation](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Sådan fjernes Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
