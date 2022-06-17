---
title: Brug PowerShell til at udføre en faseinddelt migrering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/07/2022
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
description: Få mere at vide om, hvordan du bruger PowerShell til at flytte indhold fra et kildemailsystem over tid ved hjælp af en faseindsat migrering til Microsoft 365.
ms.openlocfilehash: 0c40e617fbd069ab9894d572a5582985194e7a6e
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139535"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en faseinddelt migrering til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan overføre indholdet af brugerpostkasser fra et kildemailsystem til Microsoft 365 over tid ved hjælp af en faseindsat overførsel.

I denne artikel gennemgås de opgaver, der er involveret i en faseindret mailoverførsel, ved hjælp af Exchange Online PowerShell. Emnet [Hvad du har brug for at vide om en faseindsat mailoverførsel](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration), giver dig et overblik over migreringsprocessen. Når du er fortrolig med indholdet af den pågældende artikel, kan du bruge denne til at begynde at overføre postkasser fra ét mailsystem til et andet.

> [!NOTE]
> Du kan også bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at udføre faseinddelt migrering. Se [Udfør en faseindsat migrering af mail til Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tid til at fuldføre denne opgave: 2-5 minutter for at oprette et overførselsbatch. Når overførselsbatchen er startet, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan få oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser til Microsoft 365, under [Overførselsydeevne](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Overførsel" i emnet [Modtageres tilladelser](/exchange/recipients-permissions-exchange-2013-help) .

Hvis du vil bruge Exchange Online PowerShell-cmdlet'er, skal du logge på og importere cmdlet'erne i din lokale Windows PowerShell session. Se [Forbind til Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få vejledning.

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-a-staged-migration"></a>Trin 1: Forbered en faseindret migrering

Før du overfører postkasser til Microsoft 365 ved hjælp af en trinvis overførsel, er der nogle få ændringer, du skal foretage i dit Exchange miljø.

 **Konfigurer Outlook Anywhere på din lokale Exchange Server** Mailoverførselstjenesten bruger Outlook Anywhere (også kendt som RPC via HTTP) til at oprette forbindelse til dine Exchange Server i det lokale miljø. Du kan finde oplysninger om, hvordan du konfigurerer Outlook Anywhere for Exchange Server 2007 og Exchange 2003, på følgende måde:

- [Exchange 2007: Sådan aktiverer du Outlook overalt](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Sådan konfigurerer du Outlook Anywhere med Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Du skal bruge et certifikat, der er udstedt af et nøglecenter, der er tillid til, sammen med konfigurationen Outlook Anywhere. Outlook Anywhere kan ikke konfigureres med et selvsigneret certifikat. Du kan finde flere oplysninger under [Sådan konfigurerer du SSL til Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **Valgfrit: Kontrollér, at du kan oprette forbindelse til din Exchange organisation ved hjælp af Outlook Anywhere** Prøv en af følgende metoder for at teste dine forbindelsesindstillinger.

- Brug Outlook uden for virksomhedens netværk til at oprette forbindelse til din lokale Exchange postkasse.

- Brug [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/) til at teste dine forbindelsesindstillinger. Brug Outlook Anywhere (RPC via HTTP) eller Outlook Autodiscover-test.

- Kør følgende kommandoer i Exchange Online PowerShell:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Angiv tilladelser** Den brugerkonto i det lokale miljø, som du bruger til at oprette forbindelse til din lokale Exchange organisation (også kaldet overførselsadministratoren), skal have de nødvendige tilladelser til at få adgang til de lokale postkasser, du vil overføre til Microsoft 365. Denne brugerkonto bruges, når du opretter forbindelse til dit mailsystem ved at oprette et overførselsslutpunkt senere i denne procedure [Trin 3: Opret et slutpunkt for overførsel](#step-3-create-a-migration-endpoint).

Hvis du vil overføre postkasserne, skal administratoren have et af følgende tilladelsessæt:

- Vær medlem af gruppen **Domæneadministratorer** i Active Directory i organisationen i det lokale miljø.

    Eller

- Få tildelt **FullAccess-tilladelsen** for hver postkasse i det lokale miljø og tilladelsen **WriteProperty** til at ændre egenskaben **TargetAddress** på brugerkontiene i det lokale miljø.

    Eller

- Få tildelt tilladelsen **Modtag som** i den lokale postkassedatabase, der gemmer brugerpostkasser, og tilladelsen **WriteProperty** til at ændre egenskaben **TargetAddress** for brugerkontiene i det lokale miljø.

Du kan finde oplysninger om, hvordan du angiver disse tilladelser, under [Tildel tilladelser til overførsel af postkasser til Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Deaktiver Unified Messaging (UM)** Hvis UM er slået til for de lokale postkasser, du overfører, skal du slå UM fra før overførsel. Slå UM til for postkasserne, når overførslen er fuldført. Hvis du vil have mere at vide, skal du se[Deaktiver unified messaging](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Brug katalogsynkronisering til at oprette nye brugere i Microsoft 365.** Du kan bruge katalogsynkronisering til at oprette alle brugere i det lokale miljø i din Microsoft 365 organisation.

Du skal licensere brugerne, når de er oprettet. Du har 30 dage til at tilføje licenser, når brugerne er oprettet. Du kan finde trin til tilføjelse af licenser under [Trin 8: Udfør opgaver efter overførsel](#step-8-complete-post-migration-tasks).

 Du kan enten bruge Microsoft Azure Active Directory (Azure AD) Synkroniseringsværktøj eller Microsoft Azure AD Sync Services til at synkronisere og oprette dine lokale brugere i Microsoft 365. Når postkasser er overført til Microsoft 365, kan du administrere brugerkonti i din lokale organisation, og de synkroniseres med din Microsoft 365 organisation. Du kan få flere oplysninger under[Mappeintegration](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Trin 2: Opret en CSV-fil til en faseindsat overførselsbatch

Når du har identificeret de brugere, hvis postkasser i det lokale miljø du vil overføre til Microsoft 365, skal du bruge en fil med kommaseparerede værdier (CSV) til at oprette et overførselsbatch. Hver række i CSV-filen , der bruges af Microsoft 365 til at køre overførslen, indeholder oplysninger om en postkasse i det lokale miljø.

> [!NOTE]
> Der er ikke en grænse for det antal postkasser, du kan overføre til Microsoft 365 ved hjælp af en faseindsat overførsel. CSV-filen til et overførselsbatch kan maksimalt indeholde 2.000 rækker. Hvis du vil overføre mere end 2.000 postkasser, skal du oprette yderligere CSV-filer og bruge hver fil til at oprette et nyt overførselsbatch.

 **Understøttede attributter**

CSV-filen til en faseindsat migrering understøtter følgende tre attributter. Hver række i CSV-filen svarer til en postkasse og skal indeholde en værdi for hver af disse attributter.

|**Attribut**|**Beskrivelse**|**Kræves?**|
|:-----|:-----|:-----|
|Emailaddress  <br/> |Angiver den primære SMTP-mailadresse, f.eks. pilarp@contoso.com, for postkasser i det lokale miljø.  <br/> Brug den primære SMTP-adresse til postkasser i det lokale miljø og ikke bruger-id'er fra Microsoft 365. Hvis domænet i det lokale miljø f.eks. hedder contoso.com, men det Microsoft 365 maildomæne hedder service.contoso.com, skal du bruge det contoso.com domænenavn til mailadresser i CSV-filen.  <br/> |Påkrævet  <br/> |
|Adgangskode  <br/> |Den adgangskode, der skal angives for den nye Microsoft 365 postkasse. Alle adgangskodebegrænsninger, der gælder for din Microsoft 365 organisation, gælder også for de adgangskoder, der er inkluderet i CSV-filen.  <br/> |Valgfrit  <br/> |
|Forcechangepassword  <br/> |Angiver, om en bruger skal ændre adgangskoden, første gang vedkommende logger på den nye Microsoft 365 postkasse. Brug **True** eller **False** til værdien af denne parameter. <br/> > [!NOTE]> Hvis du har implementeret en SSO-løsning (Single Sign-on) ved at installere Active Directory Federation Services (AD FS) eller nyere i din lokale organisation, skal du bruge **False** som værdien af attributten **ForceChangePassword**.          |Valgfrit  <br/> |

 **CSV-filformat**

Her er et eksempel på det korrekte format for CSV-filen. I dette eksempel overføres tre postkasser i det lokale miljø til Microsoft 365.

I den første række, eller overskriftsrækken, i CSV-filen vises navnene på de attributter eller felter, der er angivet i de efterfølgende rækker. De enkelte attributnavne er adskilt af et komma.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Hver række under overskriftsrækken repræsenterer én bruger og leverer de oplysninger, der skal bruges til at overføre brugerens postkasse. Attributværdierne i hver række skal være i samme rækkefølge som attributnavnene i kolonneoverskriften.

Brug en teksteditor eller et program som Excel til at oprette CSV-filen. Gem filen som en .csv- eller .txt-fil.

> [!NOTE]
> Hvis CSV-filen indeholder ikke-ASCII-tegn eller specialtegn, skal du gemme CSV-filen med UTF-8-kodning eller en anden Unicode-kodning. Afhængigt af programmet kan det være nemmere at gemme CSV-filen med UTF-8 eller anden Unicode-kodning, når systemets landestandard for computeren svarer til det sprog, der bruges i CSV-filen.

### <a name="step-3-create-a-migration-endpoint"></a>Trin 3: Opret et overførselsslutpunkt

Hvis du vil overføre mails, skal Microsoft 365 oprette forbindelse og kommunikere med kildemailsystemet. Det gør Microsoft 365 ved at bruge et overførselsslutpunkt. Hvis du vil oprette et slutpunkt for migrering til Outlook Anywhere ved hjælp af PowerShell, skal du først [oprette forbindelse til Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) i forbindelse med trinvis migrering.

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

Hvis du vil oprette et Outlook Anywhere-overførselsslutpunkt med navnet "StagedEndpoint" i Exchange Online PowerShell, skal du køre følgende kommandoer:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Du kan finde flere oplysninger om **New-MigrationEndpoint-cmdlet'en** under [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> **New-MigrationEndpoint-cmdlet'en** kan bruges til at angive en database, som tjenesten skal bruge, ved hjælp af indstillingen **-TargetDatabase**. Ellers tildeles en database tilfældigt fra det Active Directory Federation Services (AD FS) 2.0-websted, hvor administrationspostkassen er placeret.

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

I Exchange Online PowerShell skal du køre følgende kommando for at få vist oplysninger om overførselsslutpunktet "StagedEndpoint":

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Trin 4: Opret og start en batch til faseoverførsel

Du kan bruge **New-MigrationBatch-cmdlet'en** i Exchange Online PowerShell til at oprette et overførselsbatch til en komplet migrering. Du kan oprette et overførselsbatch og starte det automatisk ved at inkludere parameteren _AutoStart_ . Du kan også oprette overførselsbatchen og derefter starte den manuelt bagefter ved hjælp af cmdlet'en **Start-MigrationBatch** . I dette eksempel oprettes et overførselsbatch med navnet "StagedBatch1" og bruger det overførselsslutpunkt, der blev oprettet i det forrige trin.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

I dette eksempel oprettes der også et overførselsbatch med navnet "StagedBatch1" og bruger det overførselsslutpunkt, der blev oprettet i det forrige trin. Da parameteren _AutoStart_ ikke er inkluderet, skal overførselsbatchen startes manuelt på overførselsdashboardet eller ved hjælp af **Start-MigrationBatch-cmdlet'en** . Som tidligere nævnt kan der kun findes én komplet overførselsbatch ad gangen.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om "StagedBatch1":

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Du kan også kontrollere, at batchen er startet, ved at køre følgende kommando:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Du kan få flere oplysninger om **Get-MigrationBatch-cmdlet'en** under [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Trin 5: Konvertér postkasser i det lokale miljø til mailaktiverede brugere

Når du har overført et bundt af postkasser, skal du bruge en metode til at give brugerne mulighed for at få adgang til deres mail. En bruger, hvis postkasse er blevet overført, har nu både en postkasse i det lokale miljø og en i Microsoft 365. Brugere, der har en postkasse i Microsoft 365, stopper med at modtage nye mails i deres lokale postkasse.

Da du ikke er færdig med dine migreringer, er du endnu ikke klar til at dirigere alle brugere til at Microsoft 365 til deres mail. Så hvad gør du for de mennesker, der har begge? Du kan ændre de postkasser i det lokale miljø, som du allerede har overført til mailaktiverede brugere. Når du skifter fra en postkasse til en mailaktiveret bruger, kan du dirigere brugeren til at Microsoft 365 for deres mail i stedet for at gå til deres lokale postkasse.

En anden vigtig årsag til at konvertere postkasser i det lokale miljø til mailaktiverede brugere er at bevare proxyadresser fra de Microsoft 365 postkasser ved at kopiere proxyadresser til de mailaktiverede brugere. Det giver dig mulighed for at administrere skybaserede brugere fra din organisation i det lokale miljø ved hjælp af Active Directory. Hvis du beslutter at tage din lokale Exchange Server organisation ud af drift, når alle postkasser er migreret til Microsoft 365, forbliver de proxyadresser, du har kopieret til de mailaktiverede brugere, i din Active Directory i det lokale miljø.

### <a name="step-6-delete-a-staged-migration-batch"></a>Trin 6: Slet en faseindret overførselsbatch

 Når alle postkasser i en overførselsbatch er blevet overført, og du har konverteret postkasserne i det lokale miljø i batchen til mailaktiverede brugere, er du klar til at slette en faseinddelt overførselsbatch. Sørg for at kontrollere, at mailen videresendes til de Microsoft 365 postkasser i overførselsbatchen. Når du sletter en faseindtømningsbatch, rydder overførselstjenesten op i alle poster, der er relateret til overførselsbatchen, og sletter overførselsbatchen.

Hvis du vil slette overførselsbatchen "StagedBatch1" i Exchange Online PowerShell, skal du køre følgende kommando.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Du kan få flere oplysninger om cmdlet'en **Remove-MigrationBatch** under [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch StagedBatch1
```

Kommandoen returnerer enten overførselsbatchen med statussen **Fjerner**, eller den returnerer en fejl, der angiver, at overførselsbatchen ikke blev fundet, og kontrollerer, at batchen er slettet.

Du kan få flere oplysninger om **Get-MigrationBatch-cmdlet'en** under [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Trin 7: Tildel licenser til Microsoft 365 brugere

Aktivér Microsoft 365 brugerkonti for de migrerede konti ved at tildele licenser. Hvis du ikke tildeler en licens, deaktiveres postkassen, når den udvidede periode (30 dage) udløber. Hvis du vil tildele en licens i Microsoft 365 Administration, skal du se [Tildel eller fjern tildeling af licenser](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Trin 8: Udfør opgaver efter overførsel

- **Opret en Autodiscover DNS-post, så brugerne nemt kan få adgang til deres postkasser.** Når alle postkasser i det lokale miljø er overført til Microsoft 365, kan du konfigurere en Autodiscover DNS-post for din Microsoft 365 organisation, så brugerne nemt kan oprette forbindelse til deres nye Microsoft 365 postkasser med Outlook- og mobilklienter. Denne nye Autodiscover DNS-post skal bruge det samme navneområde, som du bruger til din Microsoft 365 organisation. Hvis dit skybaserede navneområde f.eks. er cloud.contoso.com, er den Autodiscover DNS-post, du skal oprette, autodiscover.cloud.contoso.com.

    Microsoft 365 bruger en CNAME-post til at implementere Autodiscover-tjenesten for Outlook- og mobilklienter. CNAME-posten autodiscover skal indeholde følgende oplysninger:

  - **Alias:** automatisk søgning

  - **Mål:** autodiscover.outlook.com

    Du kan få flere oplysninger under [Tilføj DNS-poster for at oprette forbindelse til dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Demonter lokale Exchange servere.** Når du har bekræftet, at alle mails distribueres direkte til de Microsoft 365 postkasser, og du ikke længere behøver at vedligeholde din lokale mailorganisation eller ikke har planer om at implementere en SSO-løsning, kan du fjerne Exchange fra dine servere og fjerne din lokale Exchange organisation.

> [!NOTE]
> Nedlukning af Exchange kan have utilsigtede konsekvenser. Før du tager din lokale Exchange organisation ud af drift, anbefaler vi, at du kontakter Microsoft Support.

Brug nedenstående links til at få flere oplysninger:

- [Rediger eller fjern Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

- [Sådan fjerner du en Exchange 2007-organisation](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

- [Sådan fjernes Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
