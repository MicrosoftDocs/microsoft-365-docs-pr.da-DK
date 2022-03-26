---
title: Brug følsomhedsmærkater Microsoft Teams, Microsoft 365, grupper og SharePoint websteder
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkSPO
search.appverid:
- MOE150
- MET150
description: Brug følsomhedsetiketter til at beskytte indhold SharePoint og Microsoft Teams websteder og Microsoft 365 grupper.
ms.openlocfilehash: b5eb295e83e2a87a538201fe58c221f3f9400f97
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63714911"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Ud over at bruge [](sensitivity-labels.md) følsomhedsmærkater til at klassificere og beskytte dokumenter og mails, kan du også bruge følsomhedsmærkater til at beskytte indhold i følgende beholdere: Microsoft Teams-websteder, Microsoft 365 grupper ([tidligere Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601) grupper) og SharePoint-websteder. For denne klassificering og beskyttelse på objektbeholderniveau skal du bruge følgende etiketindstillinger:

- Beskyttelse af personlige oplysninger (offentlig eller privat) for teamswebsteder Microsoft 365 grupper
- Adgang for eksterne brugere
- Ekstern deling fra SharePoint websteder
- Adgang fra ikke-administrerede enheder
- Godkendelseskontekster (i eksempelvisning)
- Standarddelingslink til et SharePoint websted (kun PowerShell-konfiguration)

> [!IMPORTANT]
> Indstillingerne for ikke-administrerede enheder og godkendelseskontekster fungerer sammen med Azure Active Directory Betinget adgang. Du skal konfigurere denne afhængige funktion, hvis du vil bruge et følsomhedsmærkat til disse indstillinger. Yderligere oplysninger er inkluderet i den vejledning, der følger.

Når du anvender denne følsomhedsmærkat på en understøttet beholder, anvender etiketten automatisk klassificeringen og de konfigurerede beskyttelsesindstillinger på webstedet eller gruppen.

Indhold i disse beholdere arver dog ikke etiketterne til klassificering eller indstillinger for filer og mails, f.eks. visuelle markeringer og kryptering. Så brugerne kan mærke deres dokumenter på SharePoint-websteder eller teamwebsteder, skal du kontrollere, at du har aktiveret følsomhedsetiketter [til Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

> [!NOTE]
> Følsomhedsmærkater for beholdere understøttes ikke med Office 365 Content Delivery Networks (CDN'er).

## <a name="using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Brug følsomhedsetiketter til Microsoft Teams, Microsoft 365 grupper og SharePoint websteder

Før du aktiverer følsomhedsmærkater for objektbeholdere og konfigurerer følsomhedsetiketter for de nye indstillinger, kan brugerne se og anvende følsomhedsmærkater i deres apps. F.eks. fra Word:

![Et følsomhedsmærkat, der vises i Word-skrivebordsappen.](../media/sensitivity-label-word.png)

Når du har aktiveret og konfigureret følsomhedsmærkater for objektbeholdere, kan brugerne desuden se og anvende følsomhedsmærkater på Microsoft-teamwebsteder, Microsoft 365 grupper og SharePoint websteder. Når du f.eks. opretter et nyt teamwebsted ud fra SharePoint:

![Et følsomhedsmærkat, når du opretter et teamwebsted SharePoint.](../media/sensitivity-labels-new-team-site.png)

> [!NOTE]
> Følsomhedsmærkater for beholdere [understøtter Teams delte kanaler](/MicrosoftTeams/shared-channels), som i øjeblikket er i forhåndsvisning. Hvis et team har delte kanaler, arver de automatisk indstillinger for følsomhedsmærkater fra deres overordnede team, og denne etiket kan ikke fjernes eller erstattes med en anden etiket.

## <a name="how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels"></a>Sådan aktiverer du følsomhedsmærkater for objektbeholdere og synkroniserer etiketter

Hvis du endnu ikke har aktiveret følsomhedsmærkater for objektbeholdere, kan du udføre følgende trin som en engangsprocedure:

1. Da denne funktion bruger Azure AD-funktionalitet, skal du følge instruktionerne fra Azure AD-dokumentationen for at aktivere understøttelse af følsomhedsmærkater: Tildel følsomhedsmærkater til [Microsoft 365 grupper i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels).

2. Du skal nu synkronisere dine følsomhedsmærkater med Azure AD. Opret først [forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   I en PowerShell-session, som du kører som administrator, skal du f.eks. logge på med en global administratorkonto.

3. Kør derefter følgende kommando for at sikre, at dine følsomhedsmærkater kan bruges med Microsoft 365 grupper:

    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-groups-and-site-settings"></a>Sådan konfigurerer du indstillinger for grupper og websteder

Når følsomhedsmærkaterne er aktiveret for objektbeholdere som beskrevet i forrige afsnit, kan du derefter konfigurere beskyttelsesindstillinger for grupper og websteder i konfigurationen af følsomhedsetiketter. Indtil følsomhedsmærkaterne er aktiveret for objektbeholdere, er indstillingerne synlige, men du kan ikke konfigurere dem.

1. Følg de generelle instruktioner for [at oprette eller](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) redigere en følsomhedsmærkat, og sørg for at **& gruppewebsteder** til etikettens omfang: 
    
    ![Indstillinger for følsomhedsmærkatens omfang for filer og mails.](../media/groupsandsites-scope-options-sensitivity-label.png)
    
    Når der kun er valgt dette område for etiketten, vises navnet ikke i Office-apps, der understøtter følsomhedsmærkater, og som ikke kan anvendes på filer og mails. Denne adskillelse af etiketter kan være nyttig for både brugere og administratorer, men det kan også gøre etiketinstallationen mere kompleks.
    
    Du skal f.eks. nøje gennemgå rækkefølgen [](sensitivity-labels.md#label-priority-order-matters) af dine etiketter, SharePoint registrerer, når et mærket dokument overføres til et mærket websted. I dette scenarie genereres der automatisk en overvågningshændelse og mail, når dokumentet har en følsomhedsmærkat med højere prioritet end webstedets etiket. Du kan finde flere oplysninger i [afsnittet Overvågning af følsomhedsmærkataktiviteter](#auditing-sensitivity-label-activities) på denne side. 

2. Derefter skal du på **siden Definer beskyttelsesindstillinger for grupper og** websteder vælge en eller begge af de tilgængelige indstillinger:
    
    - **Indstillinger for beskyttelse af personlige oplysninger og adgang for eksterne** brugere for at konfigurere **indstillingerne for** beskyttelse af **personlige oplysninger og eksterne brugeres** adgang. 
    - **Indstillinger for ekstern deling og Betinget** adgang for at konfigurere indstillingen Kontroller ekstern deling fra mærket **SharePoint-websteder** og Brug **betinget adgang i Azure AD** til at beskytte de SharePoint indstillinger for websteder.

3. Hvis du har valgt **Indstillinger for beskyttelse af personlige oplysninger og adgang for eksterne** brugere, skal du konfigurere følgende indstillinger:
    
    - **Beskyttelse** af personlige oplysninger: Bevar standardindstillingen Offentlig, hvis du ønsker, at alle i organisationen skal have adgang til det teamwebsted eller den gruppe, hvor denne etiket anvendes.
        
        Vælg **Privat** , hvis du vil begrænse adgangen til kun at være godkendte medlemmer i organisationen.
        
        Vælg **Ingen** , når du vil beskytte indhold i beholderen ved hjælp af følsomhedsmærkaten, men stadig lade brugerne konfigurere indstillingerne for beskyttelse af personlige oplysninger.
        
        Indstillingerne for Offentligt **eller** Privat **sæt og** lås indstillingen for beskyttelse af personlige oplysninger, når du anvender denne etiket på objektbeholderen. Den valgte indstilling erstatter eventuelle tidligere indstillinger for beskyttelse af personlige oplysninger, der muligvis er konfigureret for teamet eller gruppen, og låser værdien for beskyttelse af personlige oplysninger, så den kun kan ændres ved først at fjerne følsomhedsmærkaten fra beholderen. Når du har fjernet følsomhedsmærkatet, forbliver indstillingen for beskyttelse af personlige oplysninger på etiketten, og brugerne kan nu ændre den igen.
    
    - **Ekstern brugeradgang**: Kontroller, om gruppeejeren [kan føje gæster til gruppen](/office365/admin/create-groups/manage-guest-access-in-groups).

4. Hvis du har **valgt Indstillinger for ekstern deling og Betinget adgang**, skal du nu konfigurere følgende indstillinger:
    
    - **Styre ekstern deling fra websteder med navnet SharePoint**: Vælg denne indstilling for derefter at vælge enten ekstern deling for alle, nye og eksisterende gæster, eksisterende gæster eller kun personer i organisationen. Du kan finde flere oplysninger om denne konfiguration og indstillinger i SharePoint, [Slå ekstern deling til eller fra for et websted](/sharepoint/change-external-sharing-site).
    
    - **Brug betinget adgang i Azure AD** til at beskytte SharePoint websteder: Vælg kun denne indstilling, hvis din organisation har konfigureret og bruger [Azure Active Directory Betinget adgang](/azure/active-directory/conditional-access/overview). Vælg derefter en af følgende indstillinger:
    
        - Afgør, om brugere kan få adgang til **SharePoint-websteder** fra ikke-administrerede enheder: Denne indstilling bruger funktionen SharePoint, der bruger betinget adgang til Azure AD til at blokere eller begrænse adgangen til SharePoint- og OneDrive-indhold fra enheder, der ikke er administrerede. Du kan finde flere oplysninger [i Kontrollere adgang fra enheder, der ikke er administrerede](/sharepoint/control-access-from-unmanaged-devices), SharePoint dokumentationen. Den indstilling, du angiver for denne etiketindstilling, svarer til at køre en PowerShell-kommando for et websted som beskrevet i trin 3-5 fra afsnittet Bloker eller begræns adgangen til et bestemt [SharePoint-websted eller OneDrive-afsnit](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive) fra SharePoint-vejledningen.
            
            Du kan finde flere [konfigurationsoplysninger under Flere oplysninger om](#more-information-about-the-dependencies-for-the-unmanaged-devices-option) afhængigheder af indstillingen ikke-administrerede enheder i slutningen af dette afsnit.
            
        - **Vælg en eksisterende godkendelseskontekst**: I øjeblikket kan du bruge denne indstilling til at håndhæve strengere adgangsbetingelser, når brugere får adgang SharePoint websteder, hvor denne etiket er anvendt. Disse betingelser gennemtvinges, når du vælger en eksisterende godkendelseskontekst, der er blevet oprettet og publiceret for din organisations Betinget adgang-installation. Hvis brugerne ikke opfylder de konfigurerede betingelser, eller hvis de bruger apps, der ikke understøtter godkendelseskontekster, nægtes de adgang.
            
            Du kan finde flere [konfigurationsoplysninger under Flere oplysninger om afhængigheder for](#more-information-about-the-dependencies-for-the-authentication-context-option) indstillingen godkendelseskontekst i slutningen af dette afsnit.
            
            Eksempler på denne etiketkonfiguration:
            
             - Du vælger en godkendelseskontekst, der er konfigureret til [at kræve multifaktorgodkendelse (MFA).](/azure/active-directory/conditional-access/untrusted-networks) Denne etiket anvendes derefter på et SharePoint, der indeholder meget fortrolige elementer. Når brugere fra et netværk, der ikke er tillid til, forsøger at få adgang til et dokument på dette websted, får de derfor vist MFA-prompten om, at de skal udføre, før de kan få adgang til dokumentet.
             
             - Du vælger en godkendelseskontekst, der er konfigureret [til politikker for vilkår for anvendelse](/azure/active-directory/conditional-access/terms-of-use). Denne etiket anvendes derefter på et websted på SharePoint, der indeholder elementer, der kræver en vilkår for accept af anvendelse af juridiske årsager eller af hensyn til overholdelse af regler og standarder. Når brugerne forsøger at få adgang til et dokument på dette websted, får de derfor vist et vilkår for anvendelse af dokumentet, som de skal acceptere, før de kan få adgang til det oprindelige dokument.

> [!IMPORTANT]
> Det er kun disse indstillinger for websted og gruppe, der træder i kraft, når du anvender navnet på et team, en gruppe eller et websted. Hvis [navnets](sensitivity-labels.md#label-scopes) omfang omfatter filer og mails, anvendes andre etiketindstillinger, f.eks. kryptering og indholdsmærkning, ikke på indholdet i teamet, gruppen eller webstedet.

Hvis din følsomhedsmærkat ikke allerede er publiceret, kan du nu publicere den [ved at føje den til en følsomhedsmærkatpolitik](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy). De brugere, der er tildelt en følsomhedsmærkatpolitik, der omfatter denne etiket, vil kunne vælge den til websteder og grupper.

##### <a name="more-information-about-the-dependencies-for-the-unmanaged-devices-option"></a>Flere oplysninger om afhængigheder af indstillingen ikke-administrerede enheder

Hvis du ikke konfigurerer den afhængige politik for betinget adgang for SharePoint som dokumenteret i Brug [app-tvungne](/sharepoint/app-enforced-restrictions) begrænsninger, har den indstilling, du angiver her, ingen virkning. Desuden har det ingen virkning, hvis det er mindre restriktivt end en konfigureret indstilling på lejerniveau. Hvis du har konfigureret en indstilling for hele organisationen for enheder, der ikke er administrerede, skal du vælge en etiketindstilling, der enten er den samme eller mere restriktiv.

Hvis din lejer f.eks. er konfigureret til Tillad begrænset adgang, der kun er tilgængelig **via internettet**, har etiketindstillingen, der tillader fuld adgang, ingen virkning, fordi den er mindre restriktiv. For denne indstilling på lejerniveau skal du vælge etiketindstillingen for at blokere adgang (mere restriktiv) eller etiketindstillingen for begrænset adgang (det samme som lejerindstillingen).

Da du kan konfigurere SharePoint indstillingerne separat fra etiketkonfigurationen, er der ingen kontrol med konfigurationen af følsomhedsmærkatet, som afhængighederne er på plads. Disse afhængigheder kan konfigureres, efter etiketten er oprettet og publiceret, og selv når etiketten er anvendt. Men hvis navnet allerede er anvendt, træder etiketindstillingen først i kraft, når brugeren er godkendt.

##### <a name="more-information-about-the-dependencies-for-the-authentication-context-option"></a>Flere oplysninger om afhængigheder af indstillingen for godkendelseskontekst

For at få vist på rullelisten til markering skal godkendelseskontekster oprettes, konfigureres og publiceres som en del Azure Active Directory konfiguration af Betingelsesadgang. Du kan finde flere oplysninger og instruktioner i [afsnittet Konfigurer godkendelseskontekster](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts) fra Azure AD Conditional Access-dokumentationen.

Ikke alle apps understøtter godkendelseskontekster. Hvis en bruger med en ikke-understøttet app opretter forbindelse til det websted, der er konfigureret til godkendelseskontekst, vises der enten en meddelelse om adgang nægtet, eller brugeren bliver bedt om at godkende, men afvist. De apps, der i øjeblikket understøtter godkendelseskontekster:

- Office på internettet, som Outlook til internettet

- Microsoft Teams til Windows og macOS (omfatter Teams webapp)

- Microsoft Planner

- Microsoft 365 Apps til Word, Excel og PowerPoint; minimumsversioner:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 2.48.303
    - Android: 16.0.13924.10000

- Microsoft 365 Apps til Outlook. minimumversioner:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 4.2109.0
    - Android: 4.2025.1

- OneDrive-synkronisering app, minimumversioner:
    - Windows: 21.002
    - macOS: 21.002
    - iOS: Udrulning i 12.30
    - Android: Understøttes endnu ikke

Kendte begrænsninger for denne forhåndsvisning:

- Kun for OneDrive-synkronisering, der understøttes kun OneDrive og ikke for andre websteder.

- Følgende funktioner og apps kan være inkompatible med godkendelseskontekster, så vi opfordrer dig til at kontrollere, at disse fortsat fungerer, efter at en bruger har haft adgang til et websted ved hjælp af en godkendelseskontekst:
    
    - Arbejdsprocesser, der bruger Power Apps eller Power Automate
    - Tredjepartsapps

### <a name="configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings"></a>Konfigurere indstillinger for standardlinktypen for deling for et websted ved hjælp af avancerede indstillinger i PowerShell

Ud over etiketindstillingerne for websteder og grupper, som du kan konfigurere fra overholdelsescenteret, kan du også konfigurere standardtypen for delingslink for et websted. Følsomhedsmærkater for dokumenter kan også konfigureres til en standard kædetype for deling. Disse indstillinger, der forhindrer overdeling, vælges automatisk, når brugerne vælger **knappen Del** i deres Office apps. 

Du kan finde flere oplysninger og instruktioner under Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter [SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md).

## <a name="sensitivity-label-management"></a>Administration af følsomhedsmærkater

Brug følgende vejledning til, når du opretter, redigerer eller sletter følsomhedsmærkater, der er konfigureret til websteder og grupper.

### <a name="creating-and-publishing-labels-that-are-configured-for-sites-and-groups"></a>Oprette og publicere etiketter, der er konfigureret til websteder og grupper

Når et nyt følsomhedsmærkat oprettes og publiceres, er det synligt for brugere i teams, grupper og websteder inden for en time. Men hvis du ændrer en eksisterende etiket, kan der gå op til 24 timer. Brug følgende vejledning til at publicere et navn til dine brugere, når den pågældende etiket er konfigureret til websteds- og gruppeindstillinger:

1. Når du har oprettet og konfigureret følsomhedsmærkatet, kan du føje denne etiket til en etiketpolitik, der kun gælder for nogle få testbrugere.

2. Vent på, at ændringen replikeres:

   - Ny etiket: Vent en time.
   - Eksisterende etiket: Vent i 24 timer.

3. Efter denne ventetid skal du bruge en af testbrugerkontiene til at oprette et team, en Microsoft 365-gruppe eller et SharePoint-websted med den etiket, du oprettede i trin 1.

4. Hvis der ikke er nogen fejl under oprettelsen, ved du, at det er sikkert at publicere etiketten til alle brugere i din lejer.

### <a name="modifying-published-labels-that-are-configured-for-sites-and-groups"></a>Ændring af publicerede navne, der er konfigureret for websteder og grupper

Som bedste fremgangsmåde skal du ikke ændre websteds- og gruppeindstillingerne for en følsomhedsmærkat, når etiketten er blevet anvendt på teams, grupper eller websteder. Hvis du gør det, skal du huske at vente i 24 timer på, at ændringerne replikeres til alle beholdere, hvor etiketten er anvendt.

Hvis dine ændringer omfatter adgangsindstillingen **Eksterne brugere** , skal du desuden gøre følgende:

- Den nye indstilling gælder for nye brugere, men ikke for eksisterende brugere. Hvis denne indstilling f.eks. tidligere blev valgt, og som resultat deraf fik gæstebrugere adgang til webstedet, kan disse gæstebrugere stadig få adgang til webstedet, efter denne indstilling er blevet ryddet i etiketkonfigurationen.

- Indstillingerne for beskyttelse af personlige oplysninger for gruppeegenskaberne skjultMedlemskab og rolleEnabled opdateres ikke.

### <a name="deleting-published-labels-that-are-configured-for-sites-and-groups"></a>Sletning af publicerede navne, der er konfigureret for websteder og grupper

Hvis du sletter et følsomhedsmærkat, der har websteds- og gruppeindstillingerne aktiveret, og den pågældende etiket er inkluderet i en eller flere etiketpolitikker, kan denne handling medføre fejl ved oprettelse af nye teams, grupper og websteder. For at undgå denne situation skal du bruge følgende vejledning:

1. Fjern følsomhedsmærkatet fra alle etiketpolitikker, der omfatter mærkaten.

2. Vent en time.

3. Efter denne ventetid kan du prøve at oprette et team, en gruppe eller et websted og bekræfte, at navnet ikke længere er synligt.

4. Hvis følsomhedsmærkatet ikke er synligt, kan du nu roligt slette mærkaten.

## <a name="how-to-apply-sensitivity-labels-to-containers"></a>Sådan anvender du følsomhedsmærkater på objektbeholdere

Du er nu klar til at anvende følsomhedsmærkatet eller -etiketterne på følgende beholdere:

- [Microsoft 365 gruppe i Azure AD](#apply-sensitivity-labels-to-microsoft-365-groups)
- [Microsoft Teams teamwebsted](#apply-a-sensitivity-label-to-a-new-team)
- [Microsoft 365 gruppen i Outlook på internettet](#apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web)
- [SharePoint websted](#apply-a-sensitivity-label-to-a-new-site)

Du kan bruge PowerShell, hvis du har brug [for at anvende en følsomhedsmærkat på flere websteder](#use-powershell-to-apply-a-sensitivity-label-to-multiple-sites).

### <a name="apply-sensitivity-labels-to-microsoft-365-groups"></a>Anvend følsomhedsetiketter på Microsoft 365 grupper

Du er nu klar til at anvende følsomhedsmærkatet eller -mærkaterne på Microsoft 365 grupper. Gå tilbage til Azure AD-dokumentationen for at få vejledning:

- [Tildel en etiket til en ny gruppe i Azure-portalen](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

- [Tildel en etiket til en eksisterende gruppe i Azure-portalen](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

- [Fjern en etiket fra en eksisterende gruppe i Azure-portalen](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

### <a name="apply-a-sensitivity-label-to-a-new-team"></a>Anvend et følsomhedsmærkat på et nyt team

Brugere kan vælge følsomhedsmærkater, når de opretter nye teams Microsoft Teams. Når de vælger etiketten på rullelisten **Følsomhed** , ændres indstillingen for beskyttelse af personlige oplysninger muligvis, så den afspejler etiketkonfigurationen. Afhængigt af de indstillinger for adgang til eksterne brugere, du har valgt for navnet, kan eller kan brugere ikke føje personer uden for organisationen til teamet.

[Få mere at vide om følsomhedsmærkater for Teams](/microsoftteams/sensitivity-labels)

![Indstillingen for beskyttelse af personlige oplysninger, når du opretter et nyt team.](../media/privacy-setting-new-team.png)

Når du har oprettet teamet, vises følsomhedsmærkatet i øverste højre hjørne af alle kanaler.

![Følsomhedsmærkatet vises på teamet.](../media/privacy-setting-teams.png)

Tjenesten anvender automatisk den samme følsomhedsmærkat på Microsoft 365 og det tilknyttede SharePoint teamwebsted.

### <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Anvend et følsomhedsmærkat på en ny gruppe Outlook på internettet

Når Outlook på internettet ny gruppe i din gruppe, kan du vælge eller ændre **følsomhedsindstillingen** for publicerede navne:

![Oprettelse af en gruppe og valg af en indstilling under Følsomhed.](../media/sensitivity-label-new-group.png)

### <a name="apply-a-sensitivity-label-to-a-new-site"></a>Anvend et følsomhedsmærkat på et nyt websted

Administratorer og slutbrugere kan vælge følsomhedsmærkater, når de [opretter moderne teamwebsteder og kommunikationswebsteder](/sharepoint/create-site-collection) og udvider **Avancerede indstillinger**:

![Oprettelse af et websted og valg af en indstilling under Følsomhed.](../media/sensitivity-label-new-communication-site.png)

Rullelisten viser navnenavnene for markeringen, og Hjælp-ikonet viser alle navne med deres værktøjstip, som kan hjælpe brugerne med at finde den rigtige etiket, der skal anvendes.

Når etiketten er anvendt, og brugerne går til webstedet, kan de se navnet på navnet og anvendte politikker. Dette websted er f.eks. blevet navnmærket **Fortroligt**, og indstillingen for beskyttelse af personlige oplysninger er angivet til **Privat**:

![Et websted, hvor der er anvendt et følsomhedsmærkat.](../media/sensitivity-label-site.png)

### <a name="use-powershell-to-apply-a-sensitivity-label-to-multiple-sites"></a>Brug PowerShell til at anvende et følsomhedsmærkat på flere websteder

Du kan bruge [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite)- og [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/set-spotenant) med *SensitivityLabel-parameteren* fra den aktuelle [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) til at anvende en følsomhedsmærkat på mange websteder. Webstederne kan være alle SharePoint gruppe af websteder eller et OneDrive websted.

Sørg for, at du har version 16.0.19418.12000 eller nyere af SharePoint Online Management Shell.

1. Åbn en PowerShell-session med **indstillingen Kør som** administrator.

2. Hvis du ikke kender dit mærkat-GUID: Forbind [til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell), og få en liste over følsomhedsmærkater og deres GUID'er.

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Opret [nu forbindelse til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online), og gem dit etiket-GUID som en variabel. Eksempel:

   ```powershell
   $Id = [GUID]("e48058ea-98e8-4940-8db0-ba1310fd955e")
   ```

4. Opret en ny variabel, der identificerer flere websteder, der har en identificerende streng til fælles i deres URL-adresse. Eksempel:

   ```powershell
   $sites = Get-SPOSite -IncludePersonalSite $true -Limit all -Filter "Url -like 'documents"
   ```

5. Kør følgende kommando for at anvende navnet på disse websteder. Ved hjælp af vores eksempler:

   ```powershell
   $sites | ForEach-Object {Set-SPOTenant $_.url -SensitivityLabel $Id}
   ```

Med denne række kommandoer kan du markere flere websteder på tværs af din lejer med den samme følsomhedsmærkat, hvilket er grunden til, at du bruger Set-SPOTenant-cmdlet'en i stedet for Set-SPOSite-cmdlet'en, der bruges til konfiguration pr. websted. Brug dog cmdlet'Set-SPOSite, når du har brug for at anvende en anden etiket på bestemte websteder ved at gentage følgende kommando for hver af disse websteder: `Set-SPOSite -Identity <URL> -SensitivityLabel "<labelguid>"`

## <a name="view-and-manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>Få vist og administrer følsomhedsmærkater SharePoint Administration

For at få vist, sortere og søge i de anvendte følsomhedsmærkater <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**skal**</a> du bruge Aktive websteder SharePoint Administration. Du skal muligvis først tilføje **kolonnen** Følsomhed:

![Kolonnen Følsomhed på siden Aktive websteder.](../media/manage-site-sensitivity-labels.png)

Du kan finde flere oplysninger om administration af websteder fra siden Aktive websteder, herunder hvordan du tilføjer en kolonne, [under Administrere websteder i den nye SharePoint Administration](/sharepoint/manage-sites-in-new-admin-center).

Du kan også ændre og anvende et navn fra denne side:

1. Vælg navnet på webstedet for at åbne detaljeruden.

2. Vælg fanen **Politikker** , og vælg derefter **Rediger** for **følsomhedsindstillingen** .

3. I **indstillingsruden Rediger** følsomhed skal du vælge den følsomhedsmærkat, du vil anvende på webstedet. I modsætning til brugerapps, hvor følsomhedsetiketter kan tildeles bestemte brugere, viser Administration alle følsomhedsmærkater for din lejer. Når du har valgt en etiket, skal du vælge **Gem**.

## <a name="support-for-sensitivity-labels"></a>Understøttelse af følsomhedsmærkater

Når du bruger administrationscentre, der understøtter følsomhedsmærkater, med undtagelse Azure Active Directory-portalen, kan du se alle følsomhedsmærkater for din lejer. Til sammenligning kan brugerapps og -tjenester, der filtrerer følsomhedsmærkater i henhold til publiceringspolitikker, resultere i, at du får vist et undersæt af disse etiketter. Portalen Azure Active Directory filtrerer også etiketterne i henhold til publiceringspolitikker.

Følgende apps og tjenester understøtter følsomhedsmærkater, der er konfigureret til indstillinger for websteder og grupper:

- Administration:

  - SharePoint Administration
  - Teams Administration
  - Microsoft 365 Administration
  - Microsoft 365 Overholdelsescenter
  - Azure Active Directory portal

- Brugerapps og -tjenester:

  - SharePoint
  - Teams
  - Outlook på internettet og til Windows, macOS, iOS og Android
  - Formularer
  - Stream
  - Planner 

Følgende apps og tjenester understøtter i øjeblikket ikke følsomhedsmærkater, der er konfigureret til websteder og gruppeindstillinger:

- Administration:

  - Exchange Administration

- Brugerapps og -tjenester:

  - Dynamics 365
  - Yammer
  - Project
  - Power BI

## <a name="classic-azure-ad-group-classification"></a>Klassisk Azure AD-gruppeklassifikation

Når du har aktiveret følsomhedsmærkater for objektbeholdere, understøttes gruppeklassificeringerne fra Azure AD ikke længere af Microsoft 365 og vises ikke på websteder, der understøtter følsomhedsmærkater. Du kan dog konvertere dine gamle klassificeringer til følsomhedsmærkater.

Som et eksempel på, hvordan du kunne have brugt den gamle gruppeklassifikation til SharePoint, kan [du SharePoint "moderne" webstedsklassificering](/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Disse klassificeringer blev konfigureret ved hjælp af Azure AD PowerShell eller PnP Core-biblioteket og definere værdier for `ClassificationList` indstillingen. Hvis din lejer har definerede klassifikationsværdier, vises de, når du kører følgende kommando fra [AzureADPreview PowerShell-modulet](https://www.powershellgallery.com/packages/AzureADPreview):

```powershell
($setting["ClassificationList"])
```

Hvis du vil konvertere dine gamle klassificeringer til følsomhedsmærkater, skal du gøre et af følgende:

- Brug eksisterende etiketter: Angiv de ønskede etiketindstillinger for websteder og grupper ved at redigere eksisterende følsomhedsmærkater, der allerede er publiceret.

- Opret nye etiketter: Angiv de ønskede navneindstillinger for websteder og grupper ved at oprette og publicere nye følsomhedsmærkater, der har de samme navne som dine eksisterende klassificeringer.

Gør derefter følgende:

1. Brug PowerShell til at anvende følsomhedsmærkaterne på eksisterende Microsoft 365 grupper og SharePoint ved hjælp af navnetilknytning. Se næste afsnit for at få vejledning.

2. Fjern de gamle klassificeringer fra de eksisterende grupper og websteder.

Selvom du ikke kan forhindre brugere i at oprette nye grupper i apps og tjenester, der endnu ikke understøtter følsomhedsmærkater, kan du køre et tilbagevendende PowerShell-script for at søge efter nye grupper, som brugere har oprettet med de gamle klassificeringer, og konvertere dem til at bruge følsomhedsmærkater.

For at hjælpe dig med at administrere sameksistensen af følsomhedsmærkater og Azure AD-klassificeringer for websteder og grupper skal du Azure Active Directory klassificerings- og [følsomhedsmærkater for Microsoft 365 grupper](migrate-aad-classification-sensitivity-labels.md).

### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Brug PowerShell til at konvertere klassificeringer for Microsoft 365 til følsomhedsmærkater

1. Opret først [forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   I en PowerShell-session, som du kører som administrator, skal du f.eks. logge på med en global administratorkonto:

2. Få listen over følsomhedsmærkater og deres GUID'er ved hjælp [af Get-Label-cmdlet'en](/powershell/module/exchange/get-label) :

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Noter GUID'erne for de følsomhedsmærkater, du vil anvende på dine Microsoft 365 grupper.

4. Opret [nu forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et separat Windows PowerShell vindue.

5. Brug følgende kommando som et eksempel til at hente listen over grupper, der aktuelt har klassificeringen af "Generelt":

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Tilføj det nye følsomhedsnavn GUID for hver gruppe. Eksempel:

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Gentag trin 5 og 6 for de resterende gruppeklassificeringer.

## <a name="auditing-sensitivity-label-activities"></a>Overvågning af følsomhedsmærkataktiviteter

> [!IMPORTANT]
> Hvis du bruger etiketseparation ved kun at vælge området Grupper **&-websteder** for etiketter, der beskytter beholdere: På  grund af den registrerede dokuments følsomhedsseparationshændelse og [](sensitivity-labels.md#label-priority-order-matters) mails, der er beskrevet i dette afsnit, bør du overveje at bestille etiketter før etiketter, der har et omfang for **Filer &** mails. 

Hvis nogen uploader et dokument til et websted, der er beskyttet med et følsomhedsmærkat, og deres dokument [](sensitivity-labels.md#label-priority-order-matters) har en etiket med højere prioritetsfølsomhed end det følsomhedsmærkat, der er anvendt på webstedet, blokeres denne handling ikke. Du har f.eks. anvendt etiketten  Generelt på et websted SharePoint, og nogen overfører et dokument med navnet Fortroligt til dette **websted**. Da et følsomhedsmærkat med en højere prioritet identificerer indhold, der er mere følsomt end indhold, der har en lavere prioritetsrækkefølge, kan denne situation være et sikkerhedsproblem.

Selvom handlingen ikke er blokeret, overvåges den, og den genererer som standard automatisk en mail til den person, der overførte dokumentet, samt webstedsadministratoren. Det betyder, at både brugeren og administratorer kan identificere dokumenter, der har denne uregelmæssige prioritering af navne og kan handle, hvis det er nødvendigt. Du kan f.eks. slette eller flytte det overførte dokument fra webstedet.

Det ville ikke være et sikkerhedsproblem, hvis dokumentet har en følsomhedsmærkat med lavere prioritet end det følsomhedsmærkat, der er anvendt på webstedet. Eksempelvis uploades et dokument med navnet **Generelt** til et websted med navnet **Fortroligt**. I dette scenarie genereres der ikke en overvågningshændelse og mail.

> [!NOTE]
> Ligesom for den politikindstilling, der kræver, at brugerne skal angive en begrundelse for at ændre en etiket til en lavere klassificering, betragtes undermapper for den samme overordnede etiket alle som at have samme prioritet.

Hvis du vil søge i overvågningsloggen efter denne hændelse, skal du se efter **Registrerede** dokumentfølsomhedsuoverensstemmelse fra **kategorien Filer og sideaktiviteter** .

Den automatisk genererede mail registrerer etiketten  Inkompatibel følsomhed, og mailen forklarer mærkaten uoverensstemmelse med et link til det uploadede dokument og websted. Den indeholder også et link til dokumentation, der forklarer, hvordan brugere kan ændre følsomhedsmærkaten. Disse automatiserede mails kan ikke tilpasses, men du kan forhindre dem i at blive sendt, når du bruger følgende [PowerShell-kommando fra Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant):

```PowerShell
Set-SPOTenant -BlockSendLabelMismatchEmail $True
```

Når nogen tilføjer eller fjerner et følsomhedsmærkat til eller fra et websted eller en gruppe, overvåges disse aktiviteter også, men uden automatisk at generere en mail.

Alle disse overvågningshændelser kan findes i kategorien [Følsomhedsmærkataktiviteter](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) . Du kan finde en vejledning til at søge i [overvågningsloggen i Søge i overvågningsloggen i & Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md).

## <a name="how-to-disable-sensitivity-labels-for-containers"></a>Sådan deaktiverer du følsomhedsmærkater for objektbeholdere

Du kan deaktivere følsomhedsmærkater for Microsoft Teams, Microsoft 365 grupper og SharePoint-websteder ved at bruge den samme vejledning fra Aktivér understøttelse af [følsomhedsetiketter i PowerShell](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell). Men hvis du vil deaktivere funktionen, skal du i trin 5 angive `$setting["EnableMIPLabels"] = "False"`.

Ud over at gøre alle indstillingerne utilgængelige for grupper og websteder, når du opretter eller redigerer følsomhedsmærkater, gendanner denne handling, hvilken egenskab objektbeholderne bruger til deres konfiguration. Aktivering af følsomhedsetiketter for Microsoft Teams, Microsoft 365 grupper og SharePoint-websteder skifter den egenskab, der bruges fra **Klassificering** (bruges til [azure AD-gruppeklassificering](#classic-azure-ad-group-classification)) til **Følsomhed**. Når du deaktiverer følsomhedsmærkater for objektbeholdere, ignorerer objektbeholderne egenskaben Følsomhed og bruger egenskaben Klassificering igen.

Det betyder, at alle etiketindstillinger fra websteder og grupper, der tidligere er anvendt på beholdere, ikke håndhæves, og beholdere viser ikke længere etiketterne.

Hvis disse objektbeholdere anvender klassificeringsværdier for Azure AD, vil objektbeholderne gå tilbage til at bruge klassificeringerne igen. Vær opmærksom på, at nye websteder eller grupper, der er oprettet efter aktivering af funktionen, ikke viser en etiket eller har en klassificering. For disse beholdere og eventuelle nye beholdere kan du nu anvende klassificeringsværdier. Få mere at vide under [klassificering SharePoint "moderne"](/sharepoint/dev/solution-guidance/modern-experience-site-classification) websteder og Opret klassificeringer [til Office grupper i organisationen](../enterprise/manage-microsoft-365-groups-with-powershell.md).

## <a name="additional-resources"></a>Yderligere ressourcer

Se webinaroptagelse og besvarede spørgsmål om brug af følsomhedsetiketter [med Microsoft Teams, O365-grupper og SharePoint Online-websteder](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380).

Dette webinar blev optaget, da funktionen stadig var i forhåndsvisning, så du kan opleve nogle uoverensstemmelser i brugergrænsefladen. Oplysningerne om denne funktion er dog stadig nøjagtige med nye funktioner, der er dokumenteret på denne side.

Du kan finde flere oplysninger Teams administration af forbundne websteder og kanalwebsteder i [Teams forbundne websteder og kanalwebsteder](/SharePoint/teams-connected-sites).
