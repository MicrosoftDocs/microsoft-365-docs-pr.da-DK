---
title: Start din portal ved hjælp af Portalstartstyring
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
description: I denne artikel beskrives det, hvordan du kan starte portalen ved hjælp af Portalstartstyring.
ms.openlocfilehash: 2eef7a8488db579f4ba946342213b822227229d1
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941058"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Start din portal ved hjælp af startstyringen af SharePoint-portalen

En portal er et SharePoint-kommunikationswebsted på intranettet, der er i høj trafik – et websted, der har alt fra 10.000 til over 100.000 seere i løbet af flere uger. Brug Portalstartstyring til at starte din portal for at sikre, at brugerne får en problemfri visningsoplevelse, når de får adgang til din nye SharePoint-portal.
<br>
<br>
Portalstartstyringen er designet til at hjælpe dig med at følge en trinvis udrulning ved at batchindstille seere i bølger og administrere URL-omdirigeringer for den nye portal. Under lanceringen af hver bølge kan du indsamle brugerfeedback, overvåge portalens ydeevne og afbryde start midlertidigt for at løse problemer, før du fortsætter med den næste bølge. Få mere at vide om, hvordan [du planlægger en portalstart i SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**Der er to typer omdirigeringer:**

- **Tovejs**: Start en ny moderne SharePoint-portal, der skal erstatte en eksisterende klassisk eller moderne Portal i SharePoint
- **Omdiriger til en midlertidig side**: Start en ny moderne SharePoint-portal uden eksisterende SharePoint-portal

Webstedstilladelser skal konfigureres separat fra bølger som en del af start. Hvis du f.eks. frigiver en portal for hele organisationen, kan du angive tilladelser til "Alle undtagen eksterne brugere", og derefter adskille brugerne i bølger ved hjælp af sikkerhedsgrupper. Tilføjelse af en sikkerhedsgruppe til en bølge giver ikke denne sikkerhedsgruppe adgang til webstedet.

> [!NOTE]
>
> - Denne funktion vil være tilgængelig fra panelet **Indstillinger** på startsiden for SharePoint-kommunikationswebsteder.
> - Denne funktion kan kun bruges på moderne SharePoint-kommunikationswebsteder ved hjælp af webstedssider, da de er standardtypen og den anbefalede type, der skal bruges til portaler.
> - Du skal have tilladelser som webstedsejer, for at webstedet kan tilpasse og planlægge starten af en portal.
> - Lanceringer skal planlægges mindst syv dage i forvejen, og hver bølge kan vare en til syv dage.
> - Antallet af påkrævede bølger bestemmes automatisk af det forventede antal brugere.
> - Før du planlægger en portalstart, skal [værktøjet Sidediagnosticering for SharePoint køres for](https://aka.ms/perftool) at kontrollere, at webstedets startside fungerer korrekt.
> - I slutningen af lanceringen vil alle brugere med tilladelser til webstedet kunne få adgang til det nye websted.
> - Hvis din organisation bruger [Viva-forbindelser](https://microsoft.sharepoint.com/teams/MicrosoftViva/SitePages/Viva-Connections.aspx), kan brugerne se organisationens ikon på Microsoft Teams-applinjen, men når ikonet er valgt, kan brugerne ikke få adgang til portalen, før deres bølge er startet.
> - Denne funktion er ikke tilgængelig for Office 365 Germany, Office 365 drevet af 21Vianet (Kina) eller Microsoft 365 US Government-planer.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Forstå forskellene mellem indstillingerne for portalstartstyring:

Tidligere kunne portalstarter kun planlægges via SharePoint PowerShell. Nu har du to muligheder, der kan hjælpe dig med at planlægge og administrere portalens start. Få mere at vide om de vigtigste forskelle mellem begge værktøjer:

**SharePoint PowerShell-version:**

- Der kræves administratorlegitimationsoplysninger for at bruge [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Minimumskrav til én bølge
- Planlæg din start baseret på UTC-tidszone (Coordinated Universal Time)

**Version i produktet:**

- Der kræves legitimationsoplysninger til webstedsejeren
- Minimumkrav til to bølger
- Planlæg start baseret på portalens lokale tidszone som angivet i internationale indstillinger

## <a name="get-started-using-the-portal-launch-scheduler"></a>Kom i gang med at bruge portalstartstyring

1. Før du bruger værktøjet Til portalstart af tidsplan, [skal du tilføje alle brugere, der skal have adgang til dette websted](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) , via **Webstedstilladelser som webstedsejer** , webstedsmedlem eller Besøgende.

2. Start derefter planlægningen af portalens start ved at få adgang til Portal Launch Scheduler på en af to måder:

   **Mulighed 1**: De første par gange, du redigerer og publicerer ændringer på startsiden – eller indtil startsiden version 3.0 – bliver du bedt om at bruge værktøjet Portal launch scheduler. Vælg **Planlæg start** for at gå videre med planlægningen. Eller vælg **Genudgiv** for at publicere dine sideredigeringer igen uden at planlægge starten.

   ![Billede af prompten om at bruge portalstartstyringen, når startsiden publiceres igen.](../media/portal-launch-republish-2.png)

   **Mulighed 2**: Når som helst kan du navigere til startsiden for SharePoint-kommunikationswebstedet, vælge **Indstillinger** og derefter **planlægge start af webstedet** for at planlægge start af portalen.

   ![Billede af ruden Indstillinger med Planlæg en start af et websted fremhævet.](../media/portal-launch-settings-2.png)

3. Derefter skal du bekræfte portalens tilstandsscore og foretage forbedringer af portalen, hvis det er nødvendigt, ved hjælp af [værktøjet Sidediagnosticering til SharePoint](https://aka.ms/perftool) , indtil portalen modtager en score **for i orden** . Vælg derefter **Næste**.

   ![Billede af værktøjet Portal launch scheduler.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Webstedets navn og beskrivelse kan ikke redigeres fra Portalstartstyring og kan i stedet ændres ved at vælge **Indstillinger** og derefter **Webstedsoplysninger** på startsiden.

4. Vælg **Antallet af forventede brugere** på rullelisten. Dette tal repræsenterer antallet af brugere, der med størst sandsynlighed skal have adgang til webstedet. Portalstartstyringen bestemmer automatisk det ideelle antal bølger, afhængigt af de forventede brugere som denne:

   - Mindre end 10.000 brugere: To bølger
   - 10.000 til 30.000 brugere: Tre bølger
   - 30k+ til 100.000 brugere: Fem bølger
   - Mere end 100.000 brugere: Fem bølger, og kontakt Microsoft Support via de trin, der er angivet i afsnittet Start portal med mere end 100.000 brugere.

5. Find derefter den **type omdirigering** , der skal bruges:

   **Mulighed 1: Send brugere til en eksisterende SharePoint-side (tovejs)** – Brug denne indstilling, når du starter en ny moderne SharePoint-portal til at erstatte en eksisterende SharePoint-portal. Brugere i aktive bølger omdirigeres til det nye websted, uanset om de navigerer til det gamle eller nye websted. Brugere i en ikke-lanceret bølge, der forsøger at få adgang til det nye websted vil blive omdirigeret tilbage til det gamle websted, indtil deres bølge er lanceret.

   > [!NOTE]
   > Når du bruger den tovejsindstilling, skal den person, der planlægger starten, også have tilladelser som ejer af webstedet til den anden SharePoint-portal.

   **Mulighed 2: Send brugere til en automatisk genereret midlertidig side (midlertidig sideomdirigering)** – Brug en midlertidig sideomdirigering, når der ikke findes en eksisterende SharePoint-portal. Brugerne dirigeres til en ny moderne SharePoint-portal, og hvis en bruger befinder sig i en bølge, der ikke er blevet startet, omdirigeres de til en midlertidig side.

   **Mulighed 3: Send brugere til en ekstern side** – angiv en ekstern URL-adresse til en midlertidig landingssideoplevelse, indtil brugerens bølge startes.

6. Bryd publikum op i bølger. Tilføj op til 20 sikkerhedsgrupper pr. bølge. Bølgedetaljer kan redigeres indtil lanceringen af hver bølge. Hver bølge kan vare mindst én dag (24 timer) og højst syv dage. Dette giver SharePoint og dit tekniske miljø mulighed for at akklimatisere og skalere til den store mængde webstedsbrugere. Når du planlægger en start via brugergrænsefladen, er tidszonen baseret på webstedets internationale indstillinger.

   > [!NOTE]
   >
   > - Portalstartstyringen vil automatisk som standard bruge mindst 2 bølger. PowerShell-versionen af dette værktøj tillader dog 1 bølge.
   > - Microsoft 365-grupper understøttes ikke af denne version af Portal Launch Scheduler.

7. Afgør, hvem der skal have vist webstedet med det samme, og angiv deres oplysninger i feltet Brugere, der **er undtaget fra bølger** . Disse brugere er udelukket fra bølger og omdirigeres ikke før, under eller efter lanceringen.

    >[!NOTE]
    > Der kan maksimalt tilføjes op til 50 forskellige brugere eller sikkerhedsgrupper. Brug sikkerhedsgrupper, når du har brug for mere end 50 personer for at få adgang til portalen, før bølgerne starter.

8. Bekræft, at portalen starter detaljer, og vælg **Planlæg**. Når lanceringen er planlagt, skal eventuelle ændringer af Startsiden for SharePoint-portalen modtage et sundt diagnosticeringsresultat, før portalen startes igen.

### <a name="launch-a-portal-with-over-100k-users"></a>Start en portal med over 100.000 brugere

Hvis du planlægger at starte en portal med over 100.000 brugere, skal du indsende en supportanmodning ved at følge nedenstående trin. Sørg for at inkludere alle de ønskede oplysninger.

> [!NOTE]
>
> - Denne proces bør kun følges, hvis du opfylder følgende krav:
> - Startsiden er fuldført.
> - [Portalens tilstandsvejledning](https://aka.ms/portalhealth) er blevet fulgt.
> - Startdatoen er inden for 14 dage.

**Følg disse trin:**

1. Som administrator skal du klikke på følgende link, hvor en Hjælp-forespørgsel udfyldes i Administration.

[Start SharePoint Portal med 100.000 brugere](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. Nederst i ruden skal du vælge **Kontakt support** og derefter vælge **Ny serviceanmodning**.

3. Under **Beskrivelse** skal du skrive "Start SharePoint Portal med 100.000 brugere".

4. Udfyld de resterende oplysninger, og vælg **Kontakt mig**.

5. Når billetten er oprettet, skal du sørge for at give supportagenten følgende oplysninger:
   - URL-adresse til portal
   - Antal forventede brugere
   - Anslået tidsplan for lancering (med detaljer om bølgestørrelserne)
   - Brug værktøjet Sidediagnosticering til at "eksportere HAR-filen" for startsiden og dele filen med understøttelse

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Foretag ændringer af en planlagt portalstart

Startdetaljer kan redigeres for hver bølge indtil datoen for bølgens lancering.

1. Hvis du vil redigere oplysninger om portalstart, skal du gå til **Indstillinger** og vælge **Planlæg start af websted**.
2. Vælg derefter **Rediger**.
3. Når du er færdig med at foretage dine ændringer, skal du vælge **Opdater**.

## <a name="delete-a-scheduled-portal-launch"></a>Slet en planlagt portalstart

Starter, der er planlagt ved hjælp af værktøjet Portal launch scheduler, kan annulleres eller slettes når som helst, også selvom nogle bølger allerede er blevet startet.

1. Hvis du vil annullere portalens start, skal du gå til **Indstillinger** og **Planlæg webstedsstart**.

2. Vælg derefter **Slet** , og når du får vist meddelelsen nedenfor, skal du vælge **Slet** igen.

   ![Billede af den prompt, der spørger, om du vil slette eller bevare en planlagt start.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>Brug startstyringen af PowerShell-portalen

Startstyringsværktøjet til SharePoint Portal var oprindeligt kun tilgængeligt via [SharePoint PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) og understøttes fortsat via PowerShell for kunder, der foretrækker denne metode. De samme noter i starten af denne artikel gælder for begge versioner af Portal Launch Scheduler.

> [!NOTE]
> Du skal have administratorrettigheder for at kunne bruge SharePoint PowerShell.
> Oplysninger om portalstart for start, der er oprettet i PowerShell, vises og kan administreres i det nye værktøj Portal Launch Scheduler i SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Appkonfiguration og oprettelse af forbindelse til SharePoint Online

1. [Download den nyeste SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Hvis du har installeret en tidligere version af SharePoint Online Management Shell, skal du gå til Tilføj eller fjern programmer og fjerne "SharePoint Online Management Shell".
    >
    > Vælg dit sprog på siden Download Center, og klik derefter på knappen Download. Du bliver bedt om at vælge mellem at downloade en x64- og x86-.msi-fil. Download x64-filen, hvis du kører 64-bit versionen af Windows eller x86-filen, hvis du kører 32-bit versionen. Hvis du ikke ved det, kan du se [Hvilken version af Windows-operativsystemet kører jeg?](https://support.microsoft.com/help/13443/windows-which-operating-system). Når filen er downloadet, skal du køre den og følge trinnene i installationsguiden.

2. Opret forbindelse til SharePoint som [global administrator eller SharePoint-administrator](/sharepoint/sharepoint-admin-role) i Microsoft 365. Du kan få mere at vide om, hvordan [du kommer i gang med SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Få vist alle eksisterende konfigurationer af portalstart

Sådan kan du se, om der er eksisterende konfigurationer for portalstart:

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Planlæg en portalstart på webstedet

Det antal bølger, der kræves, afhænger af den forventede startstørrelse.

- Mindre end 10.000 brugere: Én bølge
- 10.000 til 30.000 brugere: Tre bølger
- 30k+ til 100.000 brugere: Fem bølger
- Mere end 100.000 brugere: Fem bølger, og kontakt dit Microsoft-kontoteam

#### <a name="steps-for-bidirectional-redirection"></a>Trin til tovejsomdirigering

Tovejsomdirigering omfatter start af en ny moderne SharePoint Online-portal, der skal erstatte en eksisterende klassisk eller moderne Portal i SharePoint. Brugere i aktive bølger omdirigeres til det nye websted, uanset om de navigerer til det gamle eller nye websted. Brugere i en ikke-lanceret bølge, der forsøger at få adgang til det nye websted vil blive omdirigeret tilbage til det gamle websted, indtil deres bølge er lanceret.

Vi understøtter kun omdirigering mellem standardstartsiden på det gamle websted og standardstartsiden på det nye websted. Hvis du har administratorer eller ejere, der skal have adgang til de gamle og nye websteder uden at blive omdirigeret, skal du sikre, at de er angivet ved hjælp af `WaveOverrideUsers` parameteren .

Sådan overfører du brugere fra et eksisterende SharePoint-websted til et nyt SharePoint-websted på en faseinddelt måde:

1. Kør følgende kommando for at angive startbølger for portalen.

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

2. Fuldfør valideringen. Det kan tage 5-10 minutter, før omdirigeringen fuldfører konfigurationen på tværs af tjenesten.

#### <a name="steps-for-redirection-to-temporary-page"></a>Trin til omdirigering til midlertidig side

Midlertidig sideomdirigering skal bruges, når der ikke findes en eksisterende SharePoint-portal. Brugerne dirigeres til en ny moderne SharePoint Online-portal på en faseinddelt måde. Hvis en bruger befinder sig i en bølge, der ikke er blevet startet, omdirigeres vedkommende til en midlertidig side (enhver URL-adresse).

1. Kør følgende kommando for at angive startbølger for portalen.

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

2. Fuldfør valideringen. Det kan tage 5-10 minutter, før omdirigeringen fuldfører konfigurationen på tværs af tjenesten.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Stands eller genstart en portalstart på webstedet

1. Kør følgende kommando for at afbryde en igangværende portalstart midlertidigt og forhindre kommende bølgeprogressioner:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Valider, at alle brugere omdirigeres til det gamle websted.

3. Kør følgende kommando for at genstarte en portalstart, der er blevet afbrudt midlertidigt:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Kontrollér, at omdirigeringen nu er gendannet.

### <a name="delete-a-portal-launch-on-the-site"></a>Slet en portalstart på webstedet

1. Kør følgende kommando for at slette en portalstart, der er planlagt eller i gang for et websted.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Kontrollér, at der ikke sker nogen omdirigering for alle brugere.

## <a name="learn-more"></a>Lær mere

[Planlægning af udrulningsplanen for din portal i SharePoint Online](./planportallaunchroll-out.md)

[Planlæg dit kommunikationswebsted](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
