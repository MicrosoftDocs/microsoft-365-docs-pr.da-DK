---
title: Brug PowerShell til at udføre en migrering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: Få mere at vide om, hvordan du bruger PowerShell til at flytte indholdet fra et kildemailsystem på én gang ved at udføre en Microsoft 365.
ms.openlocfilehash: 65f48d95a73742a0ba4e5225361ecfb0fbf66c40
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63590314"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en migrering til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan overføre indholdet af brugerpostkasser fra et kildemailsystem til at Microsoft 365 på én gang ved hjælp af en enkelt migrering. Denne artikel gennemgår opgaverne i forbindelse med en migrering af mail ved hjælp Exchange Online PowerShell.

Ved at gennemgå emnet Hvad du bør vide om en komplet mailoverførsel til [Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration), kan du få et overblik over overførselsprocessen. Når du er fortrolig med indholdet af den pågældende artikel, skal du bruge denne for at starte overførslen af postkasser fra ét mailsystem til et andet.

> [!NOTE]
> Du kan også bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Administration Exchange at</a> udføre en fuld migrering. Se [Udfør en migrering af mails for at Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tidspunkt for at fuldføre denne opgave: 2-5 minutter til at oprette en overførselsbatch. Når overførselsbatchen startes, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan finde oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser Microsoft 365, under [Ydeevne for overførsel](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Hvis du vil se, hvilke tilladelser du skal bruge, skal du se posten "Overførsel" i en tabel [under emnet Modtagertilladelser](/exchange/recipients-permissions-exchange-2013-help) .

For at bruge Exchange Online PowerShell-cmdlet'er skal du logge på og importere cmdlet'er til din lokale Windows PowerShell session. Se [Forbind at Exchange Online bruge Remote PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få en vejledning.

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-a-cutover-migration"></a>Trin 1: Forberede en migrering
<a name="BK_Step1"> </a>

- **Tilføj din lokale Exchange som et accepteret domæne for din Microsoft 365 organisation.** Overførselstjenesten bruger SMTP-adressen på dine lokale postkasser til at oprette bruger-id og mailadresse til Microsoft Online Services til de nye Microsoft 365 postkasser. Overførslen mislykkes, hvis Exchange domæne ikke er et accepteret domæne eller dit Microsoft 365 domæne. Du kan få mere at vide [under Bekræfte dit domæne](../admin/setup/add-domain.md).

- **Konfigurer Outlook hvor som helst på din lokale Exchange server.** Tjenesten til overførsel af mail bruger RPC over HTTP eller Outlook et vilkårligt sted til at oprette forbindelse til din lokale Exchange server. Du kan finde oplysninger om, hvordan du konfigurerer Outlook Anywhere til Exchange 2010, Exchange 2007 og Exchange 2003, i følgende:

  - [Exchange 2010: Aktivér Outlook overalt](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: Sådan aktiveres Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: Installationsscenarier for RPC over HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [Sådan konfigurerer du Outlook hvor som helst med Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > Din Outlook hvor som helst skal konfigureres med et certifikat udstedt af et pålideligt nøglecenter. Det kan ikke konfigureres med et selv signeret certifikat. Du kan få mere at vide [under Sådan konfigureres SSL til Outlook hvor som helst](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **Kontrollér, at du kan oprette forbindelse til din Exchange ved hjælp af Outlook Anywhere.** Prøv en af disse metoder til at teste forbindelsesindstillingerne:

  - Brug Microsoft Outlook uden for virksomhedens netværk til at oprette forbindelse til din lokale Exchange postkasse.

  - Brug Microsoft [Exchange Remote Connectivity Analyzer til](https://www.testexchangeconnectivity.com/) at teste dine forbindelsesindstillinger. Brug Outlook overalt (RPC over HTTP) eller Outlook Autodiscover-test.

  - Kør følgende kommandoer i Exchange Online PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Tildele en lokal brugerkonto de nødvendige tilladelser til at få adgang til postkasser i din Exchange organisation.** Den lokale brugerkonto, du bruger til at oprette forbindelse til din lokale Exchange-organisation (også kaldet overførselsadministratoren), skal have de nødvendige tilladelser til at få adgang til de lokale postkasser, du vil overføre til Microsoft 365. Denne brugerkonto bruges til at oprette et overførselsslutpunkt for din lokale organisation.

    Følgende liste viser de administrative rettigheder, der kræves for at overføre postkasser ved hjælp af en komplet migrering. Der er tre mulige indstillinger.

  - Overførselsadministratoren skal være medlem af **gruppen Domæneadministratorer** i Active Directory i den lokale organisation.

    Eller

  - Overførselsadministratoren skal **tildeles FullAccess-tilladelsen** for hver lokal postkasse.

    Eller

  - Overførselsadministratoren skal have tildelt **tilladelsen Receive As** i den lokale postkassedatabase, der lagrer brugerpostkasserne.

- **Deaktiver Unified Messaging.** Hvis de lokale postkasser, du overfører, er aktiveret til UM (Unified Messaging), skal du deaktivere UM i postkasserne, før du overfører dem. Du kan derefter aktivere UM i postkasserne, når overførslen er fuldført.

- **Sikkerhedsgrupper og stedfortrædere** Tjenesten til overførsel af mail kan ikke registrere, om lokale Active Directory-grupper er sikkerhedsgrupper eller ej, så den kan ikke klargøre eventuelle overførte grupper som sikkerhedsgrupper i Microsoft 365. Hvis du vil have sikkerhedsgrupper i din Microsoft 365-lejer, skal du først klargøre en tom mailaktiveret sikkerhedsgruppe i din Microsoft 365-lejer, før du starter den uoverensgjorte migrering. Desuden flytter denne overførselsmetode kun postkasser, mailbrugere, mailkontakter og mailaktiverede grupper. Hvis et andet Active Directory-objekt, f.eks. en bruger, der ikke er overført til Microsoft 365, tildeles som leder eller stedfortræder for et objekt, der overføres, skal de fjernes fra objektet, før du overfører.

### <a name="step-2-create-a-migration-endpoint"></a>Trin 2: Oprette et overførselsslutpunkt
<a name="BK_Step2"> </a>

For at overføre mails korrekt skal Microsoft 365 oprette forbindelse til og kommunikere med kildemailsystemet. For at gøre dette Microsoft 365 et overførselsslutpunkt. Hvis du vil oprette Outlook hvor som helst overførselsslutpunkt til en uoverenssluttet migrering, skal [du først oprette forbindelse Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

Kør følgende kommandoer i Exchange Online PowerShell:

```powershell
$Credentials = Get-Credential
```

I eksemplet bruges cmdlet'en [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) til at hente og teste forbindelsesindstillingerne til den lokale Exchange-server og bruger derefter disse forbindelsesindstillinger til at oprette overførselsslutpunktet "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-MigrationEndpoint-cmdletten** kan bruges til at angive en database for tjenesten, der skal bruges, ved hjælp **af indstillingen -TargetDatabase**. Ellers tildeles en database tilfældigt fra Active Directory Federation Services (AD FS) 2.0-webstedet, hvor administrationspostkassen er placeret.

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

I Exchange Online PowerShell skal du køre følgende kommando for at få vist oplysninger om slutpunktet for "CutoverEndpoint"-overførslen:

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Trin 3: Opret den klippede overførselsbatch
<a name="BK_Step3"> </a>

Du kan bruge **New-MigrationBatch-cmdlet'en** i Exchange Online PowerShell til at oprette en overførselsbatch til en cutover-overførsel. Du kan oprette en overførselsbatch og starte den automatisk ved at medtage _autostartparameteren_ . Du kan også oprette overførselsbatchen og derefter starte den manuelt bagefter ved hjælp af **cmdlet'en Start-MigrationBatch** . I dette eksempel oprettes en overførselsbatch kaldet "CutoverBatch" og bruger overførselsslutpunktet, der blev oprettet i det forrige trin.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

I dette eksempel oprettes også en overførselsbatch med navnet "CutoverBatch" og bruges til overførselsslutpunktet, der blev oprettet i det forrige trin. Da  _autostartparameteren_ ikke er inkluderet, skal overførselsbatchen startes manuelt på dashboardet for overførsel eller ved hjælp af cmdlet'en **Start-MigrationBatch** . Som nævnt tidligere kan der kun findes én enkelt overførselsbatch ad gangen.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

For at bekræfte, at du har oprettet en overførselsbatch til en fuldført overførsel, skal du køre følgende kommando i Exchange Online PowerShell for at få vist oplysninger om den nye overførselsbatch:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Trin 4: Start den klippede overførselsbatch

For at starte overførselsbatchen Exchange Online PowerShell skal du køre følgende kommando. Dette vil oprette en overførselsbatch med navnet "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Hvis en overførselsbatch er startet korrekt, angives dens status på dashboardet til overførsel som Synkroniserer. For at bekræfte, at du har startet en overførselsbatch ved hjælp Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Trin 5: Omrute dine mails til Microsoft 365

Mailsystemer bruger en DNS-post, der kaldes en MX-post, til at finde ud af, hvor mails skal leveres. Under mailoverførselsprocessen pegede din MX-post på dit kildemailsystem. Nu hvor overførslen af mail til Microsoft 365 er fuldført, er det tid til at få din MX-post til at pege Microsoft 365. Dette er med til at sikre, at mail leveres til Microsoft 365 postkasser. Ved at flytte MX-posten kan du også deaktivere dit gamle mailsystem, når du er klar.

For mange DNS-udbydere er der specifikke instruktioner til at ændre din MX-post. Hvis din DNS-udbyder ikke er inkluderet, eller hvis du vil have en fornemmelse af de generelle retningslinjer, får du også en generel vejledning til [MX-poster](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) .

Det kan tage op til 72 timer, før dine kunders og partneres mailsystemer genkender den ændrede MX-post. Vent mindst 72 timer, før du går videre til den næste opgave: [Trin 6: Slet den klippede overførselsbatch](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Trin 6: Slet den klippede overførselsbatch

Når du har ændret MX-posten og bekræfter, at alle mails dirigeres til Microsoft 365-postkasser, skal du give brugerne besked om, at deres mail sendes Microsoft 365. Derefter kan du slette den klippede overførselsbatch. Kontrollér følgende, før du sletter overførselsbatchen.

- Alle brugere bruger Microsoft 365 postkasser. Når batchen slettes, kopieres de mails, der sendes til postkasser i det lokale Exchange Server, ikke til de tilsvarende Microsoft 365 postkasser.

- Microsoft 365 postkasser blev synkroniseret mindst én gang, efter at mails begyndte at blive sendt direkte til dem. For at gøre dette skal du sørge for, at værdien i feltet Seneste synkroniseringstid for overførselsbatchen er af nyere dato end tidspunktet, hvor mail begyndte at blive dirigeret direkte til Microsoft 365 postkasser.

Hvis du vil slette overførselsbatchen "CutoverBatch" Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Afsnit 7: Tildel brugerlicenser

 **Aktivér Microsoft 365 brugerkonti for de overførte konti ved at tildele licenser.** Hvis du ikke tildeler en licens, deaktiveres postkassen, når prøveperioden udløber (efter 30 dage). Hvis du vil tildele en licens Microsoft 365 Administration, skal du [se Tildele eller fjerne tildeling af licenser](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Trin 8: Udføre opgaver efter overførslen

- **Opret en Autodiscover DNS-post, så brugerne nemt kan få adgang til deres postkasser.** Når alle lokale postkasser er blevet overført til Microsoft 365, kan du konfigurere en Autodiscover DNS-post for din Microsoft 365-organisation, så brugerne nemt kan oprette forbindelse til deres nye Microsoft 365-postkasser med Outlook og mobilklienter. Denne nye Autodiscover DNS-post skal bruge det samme navneområde, som du bruger til din Microsoft 365 organisation. Hvis f.eks. dit skybaserede navneområde er cloud.contoso.com, er Autodiscover DNS-posten, du skal oprette, autodiscover.cloud.contoso.com.

    Hvis du beholder din Exchange Server, skal du også sørge for, at Autodiscover DNS CNAME-post peger på Microsoft 365 i både intern og ekstern DNS efter overførslen, så Outlook-klienten opretter forbindelse til den korrekte postkasse.

    > [!NOTE]
    >  I Exchange 2007, Exchange 2010 og Exchange 2013 skal du også angive `Set-ClientAccessServer AutodiscoverInternalConnectionURI` til `Null`.

    Microsoft 365 anvender en CNAME-post til at implementere Autodiscover-tjenesten for Outlook og mobilklienter. Autodiscover CNAME-posten skal indeholde følgende oplysninger:

  - **Alias:** autodiscover

  - **Destination:** autodiscover.outlook.com

    Få mere at vide under [Tilføj DNS-poster for at forbinde dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Udrævn lokale servere Exchange serverne.** Når du har bekræftet, at alle mails dirigeres direkte til Microsoft 365-postkasserne, og du ikke længere har brug for at bevare din lokale mailorganisation eller ikke har planer om implementering af en løsning med enkelt logon (SSO), kan du fjerne Exchange fra dine servere og fjerne din lokale Exchange-organisation.

    Brug nedenstående links til at få flere oplysninger:

  - [Ændre eller fjerne Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Sådan fjernes en Exchange 2007-organisation](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Sådan fjernes Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))