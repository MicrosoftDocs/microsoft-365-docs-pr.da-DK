---
title: Brug PowerShell til at udføre en komplet migrering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du bruger PowerShell til at flytte indholdet fra et kildemailsystem på én gang ved at udføre en komplet migrering til Microsoft 365.
ms.openlocfilehash: 3761640c42a6907818886e96c9d6355d70073522
ms.sourcegitcommit: f302de988d98628922eea1f509a3f639634ddc64
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66151200"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en komplet migrering til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan overføre indholdet af brugerpostkasser fra et kildemailsystem til Microsoft 365 på én gang ved hjælp af en komplet migrering. I denne artikel gennemgås opgaverne for en migrering af mail ved hjælp af Exchange Online PowerShell.

Ved at gennemgå emnet [Hvad du har brug for at vide om en komplet mailoverførsel for at Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration), kan du få et overblik over migreringsprocessen. Når du er fortrolig med indholdet af den pågældende artikel, kan du bruge denne til at begynde at overføre postkasser fra ét mailsystem til et andet.

> [!NOTE]
> Du kan også bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at udføre en komplet migrering. Se [Udfør en komplet migrering af mail for at Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tid til at fuldføre denne opgave: 2-5 minutter for at oprette et overførselsbatch. Når overførselsbatchen er startet, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan få oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser til Microsoft 365, under [Overførselsydeevne](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Overførsel" i en tabel i emnet [Modtageres tilladelser](/exchange/recipients-permissions-exchange-2013-help) .

Hvis du vil bruge Exchange Online PowerShell-cmdlet'er, skal du logge på og importere cmdlet'erne i din lokale Windows PowerShell session. Se [Forbind til Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få vejledning.

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-a-cutover-migration"></a>Trin 1: Forbered en komplet migrering
<a name="BK_Step1"> </a>

- **Tilføj din lokale Exchange organisation som et accepteret domæne for din Microsoft 365 organisation.** Overførselstjenesten bruger SMTP-adressen på dine lokale postkasser til at oprette microsoft Online Services-bruger-id'et og mailadressen for de nye Microsoft 365 postkasser. Overførslen mislykkes, hvis dit Exchange domæne ikke er et accepteret domæne eller det primære domæne for din Microsoft 365 organisation. Du kan finde flere oplysninger under [Kontrollér dit domæne](../admin/setup/add-domain.md).

- **Konfigurer Outlook Hvor som helst på Exchange-serveren i det lokale miljø.** Mailoverførselstjenesten bruger RPC via HTTP eller Outlook Anywhere til at oprette forbindelse til din lokale Exchange-server. Du kan finde oplysninger om, hvordan du konfigurerer Outlook Anywhere for Exchange 2010, Exchange 2007 og Exchange 2003, på følgende:

  - [Exchange 2010: Aktivér Outlook overalt](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: Sådan aktiverer du Outlook overalt](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: Installationsscenarier for RPC via HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [Sådan konfigurerer du Outlook anywhere med Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > Din Outlook Anywhere-konfiguration skal konfigureres med et certifikat, der er udstedt af et nøglecenter, der er tillid til. Den kan ikke konfigureres med et selvsigneret certifikat. Du kan finde flere oplysninger under [Sådan konfigurerer du SSL til Outlook hvor som helst](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

- **Kontrollér, at du kan oprette forbindelse til din Exchange organisation ved hjælp af Outlook Anywhere.** Prøv en af disse metoder for at teste dine forbindelsesindstillinger:

  - Brug Microsoft Outlook uden for virksomhedens netværk til at oprette forbindelse til din lokale Exchange postkasse.

  - Brug Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) til at teste dine forbindelsesindstillinger. Brug Outlook Anywhere (RPC via HTTP) eller Outlook Autodiscover-test.

  - Kør følgende kommandoer i Exchange Online PowerShell.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Tildel en brugerkonto i det lokale miljø de nødvendige tilladelser til at få adgang til postkasser i din Exchange organisation.** Den brugerkonto i det lokale miljø, som du bruger til at oprette forbindelse til din lokale Exchange organisation (også kaldet overførselsadministratoren), skal have de nødvendige tilladelser til at få adgang til de lokale postkasser, du vil overføre til Microsoft 365. Denne brugerkonto bruges til at oprette et overførselsslutpunkt til din organisation i det lokale miljø.

    På følgende liste vises de administrative rettigheder, der kræves for at overføre postkasser ved hjælp af en komplet overførsel. Der er tre mulige muligheder.

  - Overførselsadministratoren skal være medlem af gruppen **Domæneadministratorer** i Active Directory i organisationen i det lokale miljø.

    Eller

  - Overførselsadministratoren skal have tildelt **FullAccess-tilladelsen** for hver postkasse i det lokale miljø.

    Eller

  - Overførselsadministratoren skal have tildelt tilladelsen **Modtag som** i den lokale postkassedatabase, der lagrer brugerpostkasserne.

- **Deaktiver Unified Messaging.** Hvis de postkasser i det lokale miljø, du overfører, er aktiveret for Unified Messaging (UM), skal du deaktivere UM i postkasserne, før du overfører dem. Du kan derefter aktivere UM på postkasserne, når overførslen er fuldført.

- **Sikkerhedsgrupper og stedfortrædere** Mailoverførselstjenesten kan ikke registrere, om Active Directory i det lokale miljø grupper er sikkerhedsgrupper eller ej, så den kan ikke klargøre migrerede grupper som sikkerhedsgrupper i Microsoft 365. Hvis du vil have sikkerhedsgrupper i din Microsoft 365 lejer, skal du først klargøre en tom mailaktiveret sikkerhedsgruppe i din Microsoft 365 lejer, før du starter komplet migrering. Denne overførselsmetode flytter desuden kun postkasser, mailbrugere, mailkontakter og mailaktiverede grupper. Hvis et andet Active Directory-objekt, f.eks. en bruger, der ikke er overført til Microsoft 365, tildeles som leder eller stedfortræder til et objekt, der migreres, skal de fjernes fra objektet, før du overfører.

### <a name="step-2-create-a-migration-endpoint"></a>Trin 2: Opret et overførselsslutpunkt
<a name="BK_Step2"> </a>

Hvis du vil overføre mails, skal Microsoft 365 oprette forbindelse og kommunikere med kildemailsystemet. Det gør Microsoft 365 ved at bruge et overførselsslutpunkt. Hvis du vil oprette et Outlook Anywhere-overførselsslutpunkt til komplet migrering, skal du først [oprette forbindelse til Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

Kør følgende kommandoer i Exchange Online PowerShell:

```powershell
$Credentials = Get-Credential
```

I eksemplet bruges cmdlet'en [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) til at hente og teste forbindelsesindstillingerne til Exchange-serveren i det lokale miljø og bruger derefter disse forbindelsesindstillinger til at oprette overførselsslutpunktet "CutoverEndpoint".

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-MigrationEndpoint-cmdlet'en** kan bruges til at angive en database, som tjenesten skal bruge, ved hjælp af indstillingen **-TargetDatabase**. Ellers tildeles en database tilfældigt fra det Active Directory Federation Services (AD FS) 2.0-websted, hvor administrationspostkassen er placeret.

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

I Exchange Online PowerShell skal du køre følgende kommando for at få vist oplysninger om overførselsslutpunktet "CutoverEndpoint":

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Trin 3: Opret komplet overførselsbatch
<a name="BK_Step3"> </a>

Du kan bruge **New-MigrationBatch-cmdlet'en** i Exchange Online PowerShell til at oprette et overførselsbatch til en komplet migrering. Du kan oprette et overførselsbatch og starte det automatisk ved at inkludere parameteren _AutoStart_ . Du kan også oprette overførselsbatchen og derefter starte den manuelt bagefter ved hjælp af cmdlet'en **Start-MigrationBatch** . I dette eksempel oprettes et overførselsbatch med navnet "CutoverBatch" og bruger det overførselsslutpunkt, der blev oprettet i det forrige trin.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

I dette eksempel oprettes der også et overførselsbatch med navnet "CutoverBatch" og bruger det overførselsslutpunkt, der blev oprettet i det forrige trin. Da parameteren  _AutoStart_ ikke er inkluderet, skal overførselsbatchen startes manuelt på overførselsdashboardet eller ved hjælp af **Start-MigrationBatch-cmdlet'en** . Som tidligere nævnt kan der kun findes én komplet overførselsbatch ad gangen.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Hvis du vil bekræfte, at du har oprettet et overførselsbatch til en komplet migrering, skal du køre følgende kommando i Exchange Online PowerShell for at få vist oplysninger om den nye overførselsbatch:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Trin 4: Start komplet overførselsbatch

Kør følgende kommando for at starte overførselsbatchen i Exchange Online PowerShell. Dette opretter et overførselsbatch med navnet "CutoverBatch".

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Hvis et overførselsbatch startes, angives dets status på overførselsdashboardet som Synkronisering. Kør følgende kommando for at bekræfte, at du har startet en overførselsbatch ved hjælp af Exchange Online PowerShell:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Trin 5: Distribuer din mail til Microsoft 365

Mailsystemer bruger en DNS-post kaldet en MX-post til at finde ud af, hvor de skal levere mails. Under mailoverførselsprocessen pegede din MX-post på dit kildemailsystem. Nu, hvor mailoverførslen til Microsoft 365 er fuldført, er det tid til at pege din MX-post på Microsoft 365. Dette hjælper med at sikre, at mail leveres til dine Microsoft 365 postkasser. Når du flytter MX-posten, kan du også slå dit gamle mailsystem fra, når du er klar.

For mange DNS-udbydere er der specifikke instruktioner til at ændre din MX-post. Hvis din DNS-udbyder ikke er inkluderet, eller hvis du vil have en fornemmelse af de generelle retninger, leveres der også [generelle MX-postinstruktioner](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide#add-an-mx-record-for-email-outlook-exchange-online) .

Det kan tage op til 72 timer, før dine kunders og partneres mailsystemer genkender den ændrede MX-post. Vent mindst 72 timer, før du fortsætter til næste opgave: [Trin 6: Slet overførselsbatchen til udskæring](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>Trin 6: Slet komplet overførselsbatch

Når du har ændret MX-posten og bekræftet, at alle mails distribueres til Microsoft 365 postkasser, skal du give brugerne besked om, at deres mail vil Microsoft 365. Derefter kan du slette komplet overførselsbatch. Kontrollér følgende, før du sletter overførselsbatchen.

- Alle brugere bruger Microsoft 365 postkasser. Når batchen er slettet, kopieres mails, der sendes til postkasser i det lokale miljø, Exchange Server ikke til de tilsvarende Microsoft 365 postkasser.

- Microsoft 365 postkasser blev synkroniseret mindst én gang, efter mailen begyndte at blive sendt direkte til dem. Det gør du ved at sikre, at værdien i feltet Senest synkroniseret tid for overførselsbatchen er nyere, end da mailen begyndte at blive distribueret direkte til Microsoft 365 postkasser.

Hvis du vil slette overførselsbatchen "CutoverBatch" i Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Afsnit 7: Tildel brugerlicenser

 **Aktivér Microsoft 365 brugerkonti for de migrerede konti ved at tildele licenser.** Hvis du ikke tildeler en licens, deaktiveres postkassen, når den udvidede periode udløber (30 dage). Hvis du vil tildele en licens i Microsoft 365 Administration, skal du se [Tildel eller fjern tildeling af licenser](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>Trin 8: Udfør opgaver efter overførsel

- **Opret en Autodiscover DNS-post, så brugerne nemt kan få adgang til deres postkasser.** Når alle postkasser i det lokale miljø er overført til Microsoft 365, kan du konfigurere en Autodiscover DNS-post for din Microsoft 365 organisation, så brugerne nemt kan oprette forbindelse til deres nye Microsoft 365 postkasser med Outlook- og mobilklienter. Denne nye Autodiscover DNS-post skal bruge det samme navneområde, som du bruger til din Microsoft 365 organisation. Hvis dit skybaserede navneområde f.eks. er cloud.contoso.com, er den Autodiscover DNS-post, du skal oprette, autodiscover.cloud.contoso.com.

    Hvis du bevarer din Exchange Server, skal du også sørge for, at Autodiscover DNS CNAME-posten skal pege på Microsoft 365 i både intern og ekstern DNS efter migreringen, så den Outlook klient opretter forbindelse til den korrekte postkasse.

    > [!NOTE]
    >  I Exchange 2007, Exchange 2010 og Exchange 2013 skal du også angive `Set-ClientAccessServer AutodiscoverInternalConnectionURI` til `Null`.

    Microsoft 365 bruger en CNAME-post til at implementere Autodiscover-tjenesten for Outlook- og mobilklienter. CNAME-posten autodiscover skal indeholde følgende oplysninger:

  - **Alias:** automatisk søgning

  - **Mål:** autodiscover.outlook.com

    Du kan få flere oplysninger under [Tilføj DNS-poster for at oprette forbindelse til dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Demonter lokale Exchange servere.** Når du har bekræftet, at alle mails distribueres direkte til de Microsoft 365 postkasser, og du ikke længere behøver at vedligeholde din lokale mailorganisation eller ikke har planer om at implementere en SSO-løsning (Single Sign-on), kan du fjerne Exchange fra dine servere og fjerne din lokale Exchange organisation.

    Brug nedenstående links til at få flere oplysninger:

  - [Rediger eller fjern Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Sådan fjerner du en Exchange 2007-organisation](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Sådan fjernes Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))
