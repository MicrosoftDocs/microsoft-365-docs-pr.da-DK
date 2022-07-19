---
title: Bookings med mig
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ROBOTS: NO INDEX, NO FOLLOW
description: Brug Bookings med mig til at lade andre planlægge møder med dig i Outlook.
ms.openlocfilehash: 076dc353107aa2499ec170ead5299d94404e351a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858803"
---
# <a name="bookings-with-me"></a>Bookings med mig

**Bookinger med mig** i Outlook er en webbaseret personlig planlægningsside, der kan integreres med oplysninger om ledig/optaget tid fra din Outlook-kalender. Bookinger med mig giver folk mulighed for at planlægge et møde eller en aftale med dig. Du kan oprette brugerdefinerede mødetyper, der skal deles med andre, så de nemt kan planlægge tid med dig baseret på din tilgængelighed og dine præferencer. I får begge en bekræftelse via mail, og deltagerne kan opdatere eller annullere planlagte møder med jer fra siden Bookings with me.

> [!NOTE]
> Bookinger hos mig er tilgængelige over hele verden som prøveversion. Funktioner, der er inkluderet i prøveversionen, er muligvis ikke komplette og kan ændres, før de bliver tilgængelige i den offentlige version.

Bookinger hos mig har to forskellige visninger:

- **Assistent-visning** En personlig bookingside, hvor du kan oprette mødetyper, som andre kan booke hos dig. Brugerdefinerede mødetyper giver dig mulighed for at tilpasse, hvornår du vil møde, og hvordan mødetypen deles med andre. Du styrer, om hver mødetype er offentlig for din planlægningsside eller er privat og kun kan tilgås af en udvalgt gruppe personer. Du kan også vælge at føje et Teams-møde til alle møder, der er booket via siden Bookings with me. Du kan få adgang til din Bookings med mig side gennem Outlook på internettet. Når du har konfigureret din side og publiceret den, kan du dele den med andre. Du kan f.eks. føje den til din Outlook-signatur.

- **Visning af deltagere** Når du deler din Bookings med mig-side med andre, får de vist deltagervisningen. Hvis arrangøren har delt deres Bookings med mig side link med dig, vil du kunne se alle deres offentlige møde typer. Hvis arrangøren har delt et mødelink, kan du kun se det pågældende møde.
  - Offentlige møder kan ses og planlægges af alle, der har din Bookings med mig side link. Du har kontrol over, hvem du deler linket med. Alle typer offentlige møder vil være synlige for alle, der har dit link til siden Bookings med mig.
  - Private møder kan kun ses af personer, der har linket til den pågældende mødetype. Forskellen mellem offentlige møder og private møder er, at private møder kan have forskellige links, og linkene udløber efter 90 dage. Du kan også indstille private links til at udløbe efter en engangsreservation. Når du åbner planlægningsvisningen for et privat møde, er det kun denne mødetype, der er synlig.

## <a name="when-to-use-bookings-with-me"></a>Hvornår skal jeg bruge Bookings sammen med mig?

Bookings med mig er en ideel løsning for virksomheder, små virksomheder og brugere i uddannelse til at planlægge 1:1 møder med personer uden for og inden for deres organisationer. Nedenfor kan du se nogle eksempler på, hvordan du kan bruge Bookings sammen med mig.

- Planlæg interviews med eksterne kandidater
- Konfigurer kunde- og klientmøder
- Planlæg teknisk support
- Konfigurer åbningstider
- Konfigurer mentortimer
- 1:1 møder med direkte rapporter
- Frokost og kaffepauser

## <a name="before-you-begin"></a>Før du begynder

Bookinger hos mig kan slås til eller fra for hele organisationen eller for bestemte brugere. Når du aktiverer Bookings for brugere, kan de oprette en Bookings-side, dele deres side med andre og give andre personer tilladelse til at booke tid hos dem. Denne artikel er for ejere og administratorer, der administrerer Bookings med mig for deres organisationer.

Bookinger hos mig er tilgængelige i følgende abonnementer:

- Office 365: A3, A5, E1, E3, E5, F1, F3
- Microsoft 365: A3, A5, E1, E3, E5, F1, F3, Business Basic, Business Standard, Business Premium

Bookinger hos mig er som standard slået til for brugere med disse abonnementer.

Bookinger hos mig skal bruge den **Microsoft Bookings app (serviceplan),** der er tildelt brugerne, for at de kan få adgang til Bookings. Denne tjenesteplan kan aktiveres/deaktiveres af lejeradministratorer. Så hvis **Microsoft Bookings** ikke er tildelt dem, nægtes bookingadgang til brugerne, selvom de er i en af de tidligere angivne SKU'er.

Du kan få flere oplysninger under [Elementet Bookings with me Microsoft 365 Roadmap](https://go.microsoft.com/fwlink/?linkid=328648).

### <a name="prerequisites-for-using-bookings-with-me"></a>Forudsætninger for at bruge Bookings hos mig

1. Bookinger med mig og Bookings deler den samme licensmodel. Bookings behøver dog ikke at være aktiveret for organisationen ved hjælp af lejerindstillinger, så brugerne kan få adgang til Bookings med mig. Appen Bookings skal være aktiveret, for at brugerne kan få adgang til Bookings hos mig.

   Hvis du vil slå Bookings med mig til uden adgang til Bookings, skal du blokere adgang til Microsoft Bookings ved hjælp af [PowerShell-kommandoen for OWA-postkassepolitikken](/powershell/module/exchange/set-owamailboxpolicy?view=exchange-ps) eller følge vejledningen her: [Slå Microsoft Bookings til eller fra](turn-bookings-on-or-off.md).

2. Deling af FreeBusy Anonymous-kalenderen skal være aktiveret for at bruge Bookings sammen med mig. Dette giver siden Bookings adgang til oplysningerne om ledig/optaget tid i din Outlook-kalender. Brug PowerShell til at kontrollere status.

   ```PowerShell
     Get-SharingPolicy -Identity "Default Sharing Policy" | fl Domains 
   ```

    "Anonymous:CalendarSharingFreeBusyReviewer"" skal være et af domænerne i svaret.

   Hvis du vil aktivere anonym deling, skal du bruge følgende kommando.

   ```PowerShell
     Set-SharingPolicy "Default Sharing Policy" -Domains @{Add="Anonymous:CalendarSharingFreeBusyReviewer"}
   ```

## <a name="turn-bookings-with-me-on-or-off"></a>Slå Bookings med mig til eller fra

Bookinger hos mig kan slås til eller fra for hele organisationen eller bestemte brugere. Når Bookings hos mig er slået til, kan brugerne oprette en Bookings med mig-side og dele links med andre i eller uden for din organisation.

### <a name="turn-bookings-with-me-on-or-off-for-your-organization-using-powershell"></a>Slå Bookings with me til eller fra for din organisation ved hjælp af PowerShell

Du skal køre følgende kommandoer ved hjælp af Exchange Online PowerShell. Du kan få flere oplysninger om kørsel af Exchange Online cmdlet'er under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil slå Bookings with me til eller fra for din organisation ved hjælp af [PowerShell-cmdlet'en Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [skal du oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) og køre følgende kommandoer.

Brug kommandoerne **Get-OrganizationConfig** og **Set-OrganizationConfig** til at finde ud af status og slå Bookings med mig til eller fra for din organisation.

> [!NOTE]
> Det tager normalt ca. 30 til 60 minutter, før Set-OrganizationConfig kommandoer træder i kraft for dine brugere.

1. Kontrollér EWS-styringsadgangen ved at køre følgende kommando.

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsEnabled
   ```

    Hvis kommandoen returnerer "EwsEnabled: **$true**", skal du fortsætte til trin 2.

    Hvis kommandoen returnerer "EwsEnabled:" (tom er standard), skal du aktivere og fortsætte til Trin 2.

   ```PowerShell
   Set-OrganizationConfig -EwsEnabled: $true
   ```

2. Kontrollér din EwsApplicationAccessPolicy ved at køre følgende kommando:

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **A**. Hvis værdien af **EwsApplicationAccessPolicy** er **EnforceAllowList**, er det kun de programmer, der er angivet i **EwsAllowList** , der har adgang til EWS og REST.

    - Hvis du vil slå Bookings med mig fra for din organisation, skal du fjerne **MicrosoftOWSPersonalBookings**, hvis de findes, fra **EwsAllowList** ved at køre følgende kommando:  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Hvis du vil aktivere Bookings med mig for din organisation, skal du føje **MicrosoftOWSPersonalBookings** til **EwsAllowList** ved at køre følgende kommando:  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Hvis værdien af **EwsApplicationAccessPolicy** er **EnforceBlockList**, har alle programmer tilladelse til at få adgang til EWS og REST, undtagen dem, der er angivet i **EwsBlockList**.

    - Hvis du vil slå Bookings med mig fra for din organisation, skal du tilføje **MicrosoftOWSPersonalBookings ved at** køre følgende kommando:

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Hvis du vil aktivere Bookings sammen med mig, hvis de er blokeret, skal du fjerne **MicrosoftOWSPersonalBookings ved at** køre følgende kommando:

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Hvis værdien af **EwsApplicationAccessPolicy** er tom, har alle programmer tilladelse til at få adgang til EWS og REST.

    - Hvis du vil slå Bookings with me for your organization fra, skal du angive politikken **EnforceBlockList** og føje **MicrosoftOWSPersonalBookings** til bloklisten ved at køre følgende kommando:

   ```PowerShell
   Set-OrganizationConfig -EwsApplicationAccessPolicy EnforceBlockList -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```
   
  > [!NOTE]
  > Parameteren EwsApplicationAccessPolicy definerer, hvilke andre programmer end Entourage, Outlook og Outlook til Mac har adgang til EWS.

### <a name="turn-bookings-with-me-off-or-on-for-individual-users"></a>Slå Bookings med mig fra eller til for individuelle brugere

Brug kommandoerne **Get-CASMailbox** og **Set-CASMailbox** til at kontrollere brugerstatus og slå Bookings med mig til eller fra for individuelle brugere i din organisation.

1. Kontrollér personens adgang til EWS-kontrolelementet ved at køre følgende kommando:

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsEnabled
   ```

    **A**. Hvis kommandoen returnerer "**EwsEnabled: $true**", skal du fortsætte til trin 2.

2. Kontrollér personens **EwsApplicationAccessPolicy** ved at køre følgende kommando:

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **A**. Hvis værdien af **EwsApplicationAccessPolicy** er **EnforceAllowList**, er det kun de programmer, der er angivet i EwsAllowList, der har adgang til EWS og REST.

    - Hvis du vil slå Bookings fra for denne bruger, skal du fjerne **MicrosoftOWSPersonalBookings**, hvis de findes fra **EwsAllowList** , ved at køre følgende kommando:

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Slå Bookings med mig til for denne bruger, føj **MicrosoftOWSPersonalBookings** til **EwsAllowList** ved at køre følgende kommando:

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Hvis værdien af **EwsApplicationAccessPolicy** er **EnforceBlockList**, har alle programmer tilladelse til at få adgang til EWS og REST, undtagen dem, der er angivet i **EwsBlockList**.  

    - Hvis du vil slå Bookings med mig fra for denne bruger, skal du føje **MicrosoftOWSPersonalBookings** til **EnforceBlockList** ved at køre følgende kommando:

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Hvis du vil slå Bookings til for denne bruger, skal du fjerne **MicrosoftOWSPersonalBookings**, hvis de findes fra EnforceBlockList, ved at køre følgende kommando:

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Hvis værdien af EwsApplicationAccessPolicy er tom, har alle programmer tilladelse til at få adgang til EWS og REST.

    - Hvis du vil slå Bookings fra for denne bruger, skal du angive politikken **EnforceBlockList** og føje **MicrosoftOWSPersonalBookings** til EWSBlockList ved at køre følgende kommando:

    ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsApplicationAccessPolicy EnforceBlockList -EWSBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="what-is-the-difference-between-bookings-and-bookings-with-me"></a>Hvad er forskellen mellem Bookings og Bookings hos mig?

Bookinger med mig integreres med din Outlook-kalender og kan kun bruges til 1:1 møder. Bookinger hos mig er beregnet til at planlægge mødetider med individuelle brugere. Bookinger er beregnet til administration af planlægning for en gruppe personer.

Desuden opretter Bookings med mig ikke en ny postkasse for hver Bookings with me-side.

### <a name="why-is-bookings-with-me-in-preview"></a>Hvorfor er Bookings med mig som prøveversion?

Bookinger hos mig er en prøveversion for alle virksomhedsbrugere over hele verden. Vi indsamler feedback og foretager forbedringer, mens den integreres i planlægningsoplevelser i Bookings og Outlook.  

### <a name="who-can-access-my-public-bookings-page"></a>Hvem har adgang til min offentlige bookingside?

Offentlige mødetyper kan tilgås af alle, der har din Bookings med mig sideadresse. Du bestemmer, hvem du deler dine Bookings med mig sideadresse med.

### <a name="what-is-the-difference-between-public-and-private-meeting-types"></a>Hvad er forskellen mellem offentlige og private mødetyper?

Mødetyper kan være offentlige eller private. Offentlige mødetyper er tilgængelige for alle, som du deler dit link til din Bookings-side med. Private mødetyper er kun tilgængelige for personer, som du deler den individuelle private mødetype med.  

Private mødetyper kan også generere links til enkeltbrug. Links til enkelt brug udløber efter deres første booking.

### <a name="do-people-need-to-have-a-microsoft-account-or-bookings-license-to-schedule-time-with-me"></a>Skal folk have en Microsoft-konto eller Bookings-licens for at planlægge tid sammen med mig?

Nej. Alle kan planlægge tid sammen med dig ved hjælp af din Bookings med mig-side, selvom de ikke har en Microsoft-konto. Du skal have en Bookings-licens for at oprette en Bookings med mig-side.

## <a name="privacy"></a>Beskyttelse af personlige oplysninger

### <a name="where-is-bookings-with-me-data-stored"></a>Hvor gemmes Bookings med mig-data?

Bookings med mig er en funktion i Outlook drevet af Bookings. Alle data gemmes på Microsoft 365-platformen og i Exchange. Bookings with me følger politikker for datalagring, der er angivet af Microsoft, som er de samme politikker, som alle Office-apps følger. Alle kundedata (herunder oplysninger fra deltagere, når de booker) registreres i Bookings og gemmes i Exchange. Du kan få flere oplysninger ved at se [Beskyttelse af personlige oplysninger: Det handler om dig](https://www.microsoft.com/en-us/trust-center/privacy).
