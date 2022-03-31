---
title: Start din portal ved hjælp af planlæggeren til portalstart
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: I denne artikel beskrives det, hvordan du kan åbne din portal ved hjælp af planlæggeren til portalstart
ms.openlocfilehash: 99462adb9deb19ec54d9679451877b5398c9c820
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63601723"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Start din portal ved hjælp SharePoint planlægning for lancering af portal

En portal er et SharePoint-kommunikationswebsted på intranettet, der er meget trafik – et websted med et sted mellem 10.000 og over 100.000 seere i løbet af flere uger. Brug Portal Launch Scheduler til at starte din portal for at sikre, at brugerne får en problemfri visningsoplevelse, når de åbner din nye SharePoint portal.
<br>
<br>
Planlæggeren til portalstart er udviklet til at hjælpe dig med at følge en faseopfaset implementerings tilgang ved at batche seere i etaper og administrere URL-omdirigeringer for den nye portal. Under lanceringen af hver runde kan du indsamle brugerfeedback, overvåge portalens ydeevne og afbryde lanceringen for at løse problemer, før du fortsætter med næste bølge. Få mere at vide om, [hvordan du planlægger en portallancering SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**Der findes to typer omdirigeringer:**

- **Tovejs**: Start en ny, moderne SharePoint portal for at erstatte en eksisterende SharePoint klassisk eller moderne portal
- **Omdirigere til en midlertidig side**: start en ny, moderne SharePoint portal uden nogen SharePoint portal

Webstedstilladelser skal konfigureres separat fra runder som en del af lanceringen. Hvis du f.eks. udgiver en portal for hele organisationen, kan du angive tilladelser til "Alle undtagen eksterne brugere", og derefter adskille brugerne i runder ved hjælp af sikkerhedsgrupper. Når du føjer en sikkerhedsgruppe til en bølge, får den pågældende sikkerhedsgruppe ikke adgang til webstedet.

> [!NOTE]
>
> - Denne funktion vil være tilgængelig fra **Indstillinger** på startsiden på SharePoint kommunikationswebsteder.
> - Denne funktion kan kun bruges på moderne SharePoint kommunikationswebsteder ved hjælp af webstedssider, da de er standardtypen og den anbefalede type, der skal bruges til portaler.
> - Du skal have tilladelser som ejer af webstedet for at kunne tilpasse og planlægge lanceringen af en portal.
> - Start skal planlægges mindst syv dage i forvejen, og hver bølge kan vare fra én til syv dage.
> - Antallet af påkrævede runder bestemmes automatisk af det forventede antal brugere.
> - Før du planlægger en portalstart, skal værktøjet [Sidediagnosticering til SharePoint køres for](https://aka.ms/perftool) at bekræfte, at webstedets startside er sund.
> - I slutningen af lanceringen vil alle brugere med tilladelser til webstedet kunne få adgang til det nye websted.
> - Hvis din organisation bruger [Viva Connections](/SharePoint/viva-connections), kan brugerne se organisationens ikon på applinjen i Microsoft Teams, men når ikonet er markeret, kan brugerne ikke få adgang til portalen, før deres runde er startet.
> - Denne funktion er ikke tilgængelig for Office 365 Germany, Office 365 drevet af 21Vianet (Kina) eller Microsoft 365 amerikanske regerings planer.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Forstå forskellene mellem indstillingerne for Portal launch scheduler:

Tidligere kunne portallanceringerne kun planlægges via SharePoint PowerShell. Nu har du to muligheder for at hjælpe dig med at planlægge og administrere lanceringen af din portal. Få mere at vide om de vigtigste forskelle mellem begge værktøjer:

**SharePoint version af PowerShell:**

- Legitimationsoplysninger for administratorer skal angives for at [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Minimumskravet til én bølge
- Planlæg din lancering baseret på tidszonen Coordinated Universal Time (UTC)

**Produktversion:**

- Webstedets ejers legitimationsoplysninger er påkrævede
- Minimumskravet til to runder
- Planlæg lanceringen baseret på portalens lokale tidszone som angivet i internationale indstillinger

## <a name="get-started-using-the-portal-launch-scheduler"></a>Kom i gang med at bruge Portal Launch Scheduler

1. Før du bruger værktøjet Til planlægning af portalstart [, skal](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) du tilføje alle brugere, der skal have adgang til dette websted, via **webstedstilladelser** som ejer af webstedet, medlem af webstedet eller gæst.

2. Start derefter planlægningen af din portals start ved at åbne Portal Launch Scheduler på en af to måder:

   **Mulighed 1**: De første par gange, du redigerer og genudgiver ændringer på din startside – eller indtil startsiden version 3.0 – bliver du bedt om at bruge værktøjet til planlægning af portalstart. Vælg **Planlæg start** for at gå fremad med planlægning. Eller vælg **Genudgiv for** at genudgive dine sideredigeringer uden at planlægge lanceringen.

   ![Billede af prompten om at bruge planlæggeren til portalstart, når du genudgiver startsiden.](../media/portal-launch-republish-2.png)

   **Mulighed 2**: Du kan når som helst gå til startsiden for SharePoint-kommunikationswebstedet, vælge **Indstillinger** og derefter planlægge start af webstedet for at  planlægge lanceringen af din portal.

   ![Billede af ruden Indstillinger planlæg en start af et websted fremhævet.](../media/portal-launch-settings-2.png)

3. Bekræft derefter portalens tilstandsresultat, og foretag forbedringer af portalen, hvis det er nødvendigt, ved hjælp af værktøjet [Sidediagnosticering til SharePoint](https://aka.ms/perftool), indtil din portal modtager **et resultat af "Sund**". Vælg derefter **Næste**.

   ![Billede af værktøjet til planlægning af portalstart.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Webstedets navn og beskrivelse kan ikke redigeres fra Portal Launch Scheduler og kan i stedet ændres ved at vælge **Indstillinger** og derefter Webstedsoplysninger fra startsiden.

4. Vælg **Antallet af forventede** brugere på rullelisten. Denne figur repræsenterer antallet af brugere, der højst sandsynligt skal have adgang til webstedet. Planlægningsstyring for portalstarter bestemmer automatisk det ideelle antal runder afhængigt af de forventede brugere på følgende måde:

   - Mindre end 10.000 brugere: To runder
   - 10k til 30.000 brugere: Tre runder
   - 30k+ til 100k brugere: Fem runder
   - Mere end 100.000 brugere: Fem runder, og kontakt Microsoft Support via de trin, der er angivet i Afsnittet Start portal med mere end 100.000 brugere.

5. Find derefter den **type omdirigering, der skal** bruges:

   **Mulighed 1: Send brugere til en eksisterende SharePoint-side (** tovejs) – Brug denne indstilling, når du starter en ny moderne SharePoint-portal for at erstatte en eksisterende SharePoint-portal. Brugere i aktive runder omdirigeres til det nye websted, uanset om de navigerer til det gamle eller nye websted. Brugere i en ikke-lanceret bølge, der forsøger at få adgang til det nye websted, bliver omdirigeret tilbage til det gamle websted, indtil deres bølge startes.

   > [!NOTE]
   > Når du bruger indstillingen Tovejs, skal den person, der planlægger lanceringen, også have webstedsejertilladelser til den anden SharePoint portal.

   **Mulighed 2: Send brugere til en automatiskgenereret** midlertidig side (midlertidig sideomdirigering) – Brug en midlertidig sideomdirigering, der skal bruges, når der ikke SharePoint eksisterende portal. Brugere dirigeres til en ny moderne SharePoint-portal, og hvis en bruger er i en bølge, der ikke er blevet lanceret, bliver de omdirigeret til en midlertidig side.

   **Mulighed 3: Send brugere** til en ekstern side – Angiv en ekstern URL-adresse til en midlertidig landingssideoplevelse, indtil brugerens bølge startes.

6. Opbryd dit publikum i runder. Tilføj op til 20 sikkerhedsgrupper pr. bølge. Wave details can be edited up until the launch of each wave. Hver bølge kan vare mindst én dag (24 timer) og højst syv dage. Dette giver SharePoint og dit tekniske miljø mulighed for at acclimere og skalere til den store mængde af webstedsbrugere. Når du planlægger en start via brugergrænsefladen, er tidszonen baseret på webstedets internationale indstillinger.

   > [!NOTE]
   >
   > - Planlæggeren til portalstart indstiller automatisk til mindst to runder. Men PowerShell-versionen af dette værktøj giver mulighed for 1 bølge.
   > - Microsoft 365 grupper understøttes ikke af denne version af Portal Launch Scheduler.

7. Bestem, hvem der skal have vist webstedet med det samme, og angiv deres oplysninger i **feltet Brugere, der er undtaget fra runder** . Disse brugere er udelukket fra runder og vil ikke blive omdirigeret før, under eller efter lanceringen.


    >[!NOTE]
    > Der kan tilføjes op til 50 særskilte brugere eller sikkerhedsgrupper. Brug sikkerhedsgrupper, når du har brug for mere end 50 personer for at få adgang til portalen, før bølgerne begynder at starte. 

8.  Bekræft oplysninger om portalstart, og vælg **Planlæg**. Når lanceringen er blevet planlagt, skal eventuelle ændringer af SharePoint-portalens startside modtage et sund diagnosticeringsresultat, før portalstart genoptages.


### <a name="launch-a-portal-with-over-100k-users"></a>Start en portal med mere end 100.000 brugere

Hvis du planlægger at starte en portal med mere end 100.000 brugere, skal du sende en supportanmodning ved at følge nedenstående trin. Sørg for at medtage alle de ønskede oplysninger.

> [!NOTE]
>
> - Denne proces bør kun følges, hvis du opfylder følgende krav:
> - Siden Start er afsluttet.
> - [Sundhedsvejledning for portal](https://aka.ms/portalhealth) er blevet fulgt.
> - Startdatoen er inden for 14 dage.

**Følg disse trin:**

1. Som administrator skal du klikke på følgende link, som udfylder en Hjælp-forespørgsel i Administration. 

[Start SharePoint portal med 100k-brugere](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. Nederst i ruden skal du vælge **Kontakt support** og derefter vælge **Ny serviceanmodning**. 

3. Under **Beskrivelse** skal du skrive "Start SharePoint Portal med 100k-brugere". 

4. Udfyld de resterende oplysninger, og vælg **Kontakt mig**.

5. Når billeten er blevet oprettet, skal du sørge for at give supportmedarbejderen følgende oplysninger:
   - URL-adresse til portal
   - Antal brugere forventet
   - Anslået tidsplan for lancering (detaljeret beskrivelse af bølgestørrelserne)
   - Brug værktøjet Sidediagnosticering til at "Eksportere HAR-filen" på startsiden og dele filen med support

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Foretage ændringer i en planlagt portallancering

Startdetaljer kan redigeres for hver runde frem til datoen for lanceringen af runden.

1. For at redigere detaljer om portalstart skal du **gå Indstillinger** og vælge **Planlæg webstedslancering**.
2. Vælg derefter **Rediger**.
3. Når du er færdig med dine redigeringer, skal du vælge **Opdater**.

## <a name="delete-a-scheduled-portal-launch"></a>Slet en planlagt portallancering

Starter, der er planlagt ved hjælp af værktøjet Til planlægning af portalstart, kan annulleres eller slettes når som helst, selvom der allerede er startet nogle runder.

1. Hvis du vil annullere lanceringen af din portal, skal du gå **til Indstillinger** og **Planlæg start af websted**.

2. Vælg derefter Slet **,** og når du ser meddelelsen nedenfor, skal du igen **vælge Slet** .

   ![Billede af prompten, der spørger, om du vil slette eller beholde en planlagt start.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>Brug PowerShell Portal Launch Scheduler

Værktøjet SharePoint portalstartplanlæg var oprindeligt kun tilgængeligt via [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) og vil fortsat være understøttet via PowerShell for kunder, der foretrækker denne metode. De samme noter i starten af denne artikel gælder for begge versioner af Portal Launch Scheduler.

> [!NOTE]
> Du skal have administratorrettigheder for at bruge SharePoint PowerShell.
> Oplysninger om portallancering for lanceringer, der er oprettet i PowerShell, vises og kan administreres i det nye værktøj til planlægning af portallancering SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Appkonfiguration og oprettelse af forbindelse til SharePoint Online

1. [Download den nyeste SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Hvis du har installeret en tidligere version af SharePoint Online Management Shell, skal du gå til Tilføj eller fjern programmer, og fjern "SharePoint Online Management Shell".
    > 
    > På siden Download Center skal du vælge dit sprog og derefter klikke på knappen Download. Du bliver bedt om at vælge mellem at hente en x64- og x86-.msi fil. Download x64-filen, hvis du kører 64-bit versionen af Windows eller x86-filen, hvis du kører 32-bit-versionen. Hvis du ikke ved det, skal du [se Hvilken version Windows af operativsystemet kører jeg?](https://support.microsoft.com/help/13443/windows-which-operating-system). Når filen er hentet, skal du køre den og følge trinnene i guiden Konfiguration.

2. Forbind at SharePoint som [global administrator eller SharePoint administrator](/sharepoint/sharepoint-admin-role) i Microsoft 365. Se hvordan under Introduktion [til SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Få vist eventuelle eksisterende konfigurationer af portallancering

Sådan kan du se, om der er eksisterende konfigurationer for portallancering:

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Planlæg en portallancering på webstedet

Det antal runder, der kræves, afhænger af den forventede startstørrelse.

- Mindre end 10.000 brugere: One Wave
- 10k til 30.000 brugere: Tre runder 
- 30k+ til 100k brugere: Fem runder
- Mere end 100.000 brugere: Fem runder, og kontakt dit Microsoft-kontoteam

#### <a name="steps-for-bidirectional-redirection"></a>Trin til tovejs omdirigering

Todirectional redirection involves launching a new modern SharePoint Online portal to replace an existing SharePoint classic or modern portal. Brugere i aktive runder omdirigeres til det nye websted, uanset om de navigerer til det gamle eller nye websted. Brugere i en ikke-lanceret bølge, der forsøger at få adgang til det nye websted, bliver omdirigeret tilbage til det gamle websted, indtil deres bølge startes.

Vi understøtter kun omdirigering mellem standard-startsiden på det gamle websted og standard-startsiden på det nye websted. Hvis du har administratorer eller ejere, der skal have adgang til de gamle og nye websteder uden at blive omdirigeret, skal du sikre dig, at de er angivet ved hjælp af `WaveOverrideUsers` parameteren.

Sådan overføres brugere fra et eksisterende SharePoint websted til et nyt SharePoint i faser:

1. Kør følgende kommando for at angive portallanceringsbølger.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType Bidirectional -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Eksempel:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType Bidirectional -RedirectUrl "https://contoso.sharepoint.com/teams/oldsite" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves ' 
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"}, 
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Fuldfør valideringen. Det kan tage fem til ti minutter, før omdirigeringen fuldfører konfigurationen på tværs af tjenesten.

#### <a name="steps-for-redirection-to-temporary-page"></a>Trin til omdirigering til midlertidig side

Midlertidig sideomdirigering bør bruges, når der ikke SharePoint eksisterende portal. Brugere dirigeres til en ny moderne SharePoint Online-portal i faser. Hvis en bruger er i en bølge, der ikke er blevet lanceret, bliver de omdirigeret til en midlertidig side (enhver URL).

1. Kør følgende kommando for at angive portallanceringsbølger.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType ToTemporaryPage -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Eksempel:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType ToTemporaryPage -RedirectUrl "https://portal.contoso.com/UnderConstruction.aspx" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves ' 
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"}, 
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Fuldfør valideringen. Det kan tage fem til ti minutter, før omdirigeringen fuldfører konfigurationen på tværs af tjenesten.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Sætte en portalstart på pause eller genstarte den på webstedet

1. Hvis du vil sætte en portallancering på pause i gang og midlertidigt forhindre kommende bølgeforløb, skal du køre følgende kommando:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Valider, at alle brugere omdirigeres til det gamle websted.

3. For at genstarte en portallancering, der er blevet sat på pause, skal du køre følgende kommando:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Valider, at omdirigeringen nu gendannes.

### <a name="delete-a-portal-launch-on-the-site"></a>Slet en portallancering på webstedet

1. Kør følgende kommando for at slette en portalstart, der er planlagt eller i gang for et websted.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Valider, at der ikke sker nogen omdirigering for alle brugere.

## <a name="learn-more"></a>Lær mere

[Planlægning af udrulning af portalstartplan i SharePoint Online](./planportallaunchroll-out.md)

[Planlæg dit kommunikationswebsted](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
