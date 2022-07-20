---
title: Brug følsomhedsmærkater med Microsoft Teams-, Microsoft 365-grupper- og SharePoint-websteder
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
description: Brug følsomhedsmærkater til at beskytte indhold på SharePoint- og Microsoft Teams-websteder og Microsoft 365-grupper.
ms.openlocfilehash: 820ed3e8c629056165661c90ec9cd612222cdbbf
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882269"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Brug følsomhedsmærkater til at beskytte indhold i Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Ud over at bruge [følsomhedsmærkater](sensitivity-labels.md) til at beskytte dokumenter og mails kan du også bruge følsomhedsmærkater til at beskytte indhold i følgende objektbeholdere: Microsoft Teams-websteder, Microsoft 365-grupper ([tidligere Office 365 grupper](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) og SharePoint-websteder. Brug følgende navneindstillinger til denne beskyttelse på objektbeholderniveau:

- Beskyttelse af personlige oplysninger (offentlige eller private) for teamswebsteder og Microsoft 365-grupper
- Ekstern brugeradgang
- Ekstern deling fra SharePoint-websteder
- Adgang fra ikke-administrerede enheder
- Godkendelseskontekster (som prøveversion)
- Standardlink til deling for et SharePoint-websted (konfiguration kun i PowerShell)
- Prøveversion: Indstillinger for webstedsdeling (konfiguration kun i PowerShell)

> [!IMPORTANT]
> Indstillingerne for ikke-administrerede enheder og godkendelseskontekster fungerer sammen med betinget adgang til Azure Active Directory. Du skal konfigurere denne afhængige funktion, hvis du vil bruge en følsomhedsmærkat til disse indstillinger. Yderligere oplysninger er inkluderet i de efterfølgende instruktioner.

Når du anvender denne følsomhedsmærkat på en understøttet objektbeholder, anvender mærkaten automatisk følsomhedskategorien og konfigurerede beskyttelsesindstillinger på webstedet eller gruppen.

Indholdet i disse objektbeholdere nedarver dog ikke mærkaterne for følsomhedskategorien eller indstillingerne for filer og mails, f.eks. indholdsmarkeringer og kryptering. Så brugerne kan mærke deres dokumenter på SharePoint-websteder eller teamwebsteder, skal du sørge for, at du har [aktiveret følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Objektbeholdernavne understøtter ikke visning af [andre sprog](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell) og viser kun det oprindelige sprog for navnet og beskrivelsen.

## <a name="using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>Brug af følsomhedsmærkater til Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder

Før du aktiverer følsomhedsmærkater for objektbeholdere og konfigurerer følsomhedsmærkater for de nye indstillinger, kan brugerne se og anvende følsomhedsmærkater i deres apps. Fra Word:

:::image type="content" source=".. /media/sensitivity-label-word.png" alt-text="En følsomhedsmærkat, der vises i Word Desktop-appen." lightbox=".. /media/sensitivity-label-word.png"

Når du har aktiveret og konfigureret følsomhedsmærkater for objektbeholdere, kan brugerne derudover se og anvende følsomhedsmærkater på Microsoft-teamwebsteder, Microsoft 365-grupper og SharePoint-websteder. Når du f.eks. opretter et nyt teamwebsted fra SharePoint:

![En følsomhedsmærkat, når du opretter et teamwebsted fra SharePoint.](../media/sensitivity-labels-new-team-site.png)

> [!NOTE]
> Følsomhedsmærkater for objektbeholdere understøtter [delte Teams-kanaler](/MicrosoftTeams/shared-channels), der i øjeblikket er en prøveversion. Hvis et team har delte kanaler, arver de automatisk indstillinger for følsomhedsmærkat fra deres overordnede team, og denne mærkat kan ikke fjernes eller erstattes med en anden mærkat.

## <a name="how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels"></a>Sådan aktiverer du følsomhedsmærkater for objektbeholdere og synkroniserer mærkater

Hvis du endnu ikke har aktiveret følsomhedsmærkater for objektbeholdere, skal du benytte følgende fremgangsmåde som en engangsprocedure:

1. Da denne funktion bruger Azure AD funktionalitet, skal du følge vejledningen fra dokumentationen til Azure AD for at aktivere understøttelse af følsomhedsmærkater: [Tildel følsomhedsmærkater til Microsoft 365-grupper i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels).

2. Du skal nu synkronisere følsomhedsmærkater for at Azure AD. Først [skal du oprette forbindelse til Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   I en PowerShell-session, som du kører som administrator, skal du f.eks. logge på med en global administratorkonto.

3. Kør derefter følgende kommando for at sikre, at dine følsomhedsmærkater kan bruges sammen med Microsoft 365-grupper:

    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-groups-and-site-settings"></a>Sådan konfigurerer du grupper og webstedsindstillinger

Når følsomhedsmærkater er aktiveret for objektbeholdere som beskrevet i forrige afsnit, kan du derefter konfigurere beskyttelsesindstillinger for grupper og websteder i konfigurationen af følsomhedsmærkater. Indtil følsomhedsmærkater er aktiveret for objektbeholdere, er indstillingerne synlige, men du kan ikke konfigurere dem.

1. Følg de generelle instruktioner for at [oprette eller redigere en følsomhedsmærkat](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) , og sørg for at vælge **Grupper & websteder** for etikettens område: 
    
    ![Indstillinger for følsomhedsmærkatområde for filer og mails.](../media/groupsandsites-scope-options-sensitivity-label.png)
    
    Når kun dette område er valgt for mærkaten, vises mærkaten ikke i Office-apps, der understøtter følsomhedsmærkater og ikke kan anvendes på filer og mails. Det kan være nyttigt for både brugere og administratorer at adskille mærkater, men det kan også forbedre kompleksiteten af udrulningen af mærkater.
    
    Du skal f.eks. omhyggeligt gennemse [etiketrækkefølgen](sensitivity-labels.md#label-priority-order-matters) , fordi SharePoint registrerer, hvornår et navngivet dokument uploades til et websted med mærkater. I dette scenarie genereres der automatisk en overvågningshændelse og en mail, når dokumentet har en følsomhedsmærkat med højere prioritet end webstedets mærkat. Du kan få flere oplysninger i afsnittet [Overvågning af aktiviteter for følsomhedsmærkat](#auditing-sensitivity-label-activities) på denne side. 

2. Vælg derefter en eller begge af de tilgængelige indstillinger på siden **Definer beskyttelsesindstillinger for grupper og websteder** :
    
    - **Indstillinger for beskyttelse af personlige oplysninger og ekstern brugeradgang** for at konfigurere indstillingerne for **beskyttelse af personlige oplysninger** og **eksterne brugeres adgang** . 
    - **Indstillinger for ekstern deling og betinget adgang** for at konfigurere indstillingen **Kontrollér ekstern deling fra navngivne SharePoint-websteder** og **Brug Azure AD Betinget adgang til at beskytte navngivne SharePoint-websteder**.

3. Hvis du har valgt **Indstillinger for beskyttelse af personlige oplysninger og ekstern brugeradgang**, skal du nu konfigurere følgende indstillinger:
    
    - **Beskyttelse af personlige oplysninger**: Bevar standardindstillingen **Offentlig** , hvis du vil have, at nogen i organisationen skal have adgang til teamwebstedet eller gruppen, hvor denne mærkat anvendes.
        
        Vælg **Privat** , hvis du kun vil have adgang til godkendte medlemmer i din organisation.
        
        Vælg **Ingen** , når du vil beskytte indhold i objektbeholderen ved hjælp af følsomhedsmærkaten, men stadig lade brugerne konfigurere indstillingen for beskyttelse af personlige oplysninger selv.
        
        Indstillingerne for **offentligt** eller **privat** sæt og lås indstillingen for beskyttelse af personlige oplysninger, når du anvender denne mærkat på objektbeholderen. Den valgte indstilling erstatter alle tidligere indstillinger for beskyttelse af personlige oplysninger, der kan være konfigureret for teamet eller gruppen, og låser værdien for beskyttelse af personlige oplysninger, så den kun kan ændres ved først at fjerne følsomhedsmærkaten fra objektbeholderen. Når du har fjernet følsomhedsmærkaten, forbliver indstillingen for beskyttelse af personlige oplysninger fra mærkaten, og brugerne kan nu ændre den igen.
    
    - **Ekstern brugeradgang**: Kontrollér, om gruppeejeren kan [føje gæster til gruppen](/office365/admin/create-groups/manage-guest-access-in-groups).

4. Hvis du har valgt **indstillinger for ekstern deling og betinget adgang**, skal du nu konfigurere følgende indstillinger:
    
    - **Kontrollér ekstern deling fra navngivne SharePoint-websteder**: Vælg denne indstilling for at vælge enten ekstern deling for alle, nye og eksisterende gæster, eksisterende gæster eller kun personer i din organisation. Du kan finde flere oplysninger om denne konfiguration og disse indstillinger i Dokumentationen til SharePoint, [Slå ekstern deling til eller fra for et websted](/sharepoint/change-external-sharing-site).
    
    - **Brug Azure AD Betinget adgang til at beskytte navngivne SharePoint-websteder**: Vælg kun denne indstilling, hvis din organisation har konfigureret og bruger [betinget adgang til Azure Active Directory](/azure/active-directory/conditional-access/overview). Vælg derefter en af følgende indstillinger:
    
        - **Bestem, om brugerne kan få adgang til SharePoint-websteder fra ikke-administrerede enheder**: Denne indstilling bruger den SharePoint-funktion, der bruger Azure AD Betinget adgang til at blokere eller begrænse adgang til SharePoint- og OneDrive-indhold fra ikke-administrerede enheder. Du kan finde flere oplysninger under [Kontrollér adgang fra ikke-administrerede enheder](/sharepoint/control-access-from-unmanaged-devices) fra Dokumentationen til SharePoint. Den indstilling, du angiver for denne mærkatindstilling, svarer til at køre en PowerShell-kommando for et websted, som beskrevet i trin 3-5 fra sektionen [Bloker eller begræns adgang til et bestemt SharePoint-websted eller OneDrive](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive) fra instruktionerne til SharePoint.
            
            Du kan finde flere konfigurationsoplysninger under [Flere oplysninger om afhængighederne for indstillingen ikke-administrerede enheder](#more-information-about-the-dependencies-for-the-unmanaged-devices-option) i slutningen af dette afsnit.
            
        - **Vælg en eksisterende godkendelseskontekst**: Denne indstilling er i øjeblikket en prøveversion og giver dig mulighed for at gennemtvinge strengere adgangsbetingelser, når brugere tilgår SharePoint-websteder, hvor denne mærkat er anvendt. Disse betingelser gennemtvinges, når du vælger en eksisterende godkendelseskontekst, der er oprettet og publiceret til din organisations udrulning af betinget adgang. Hvis brugerne ikke opfylder de konfigurerede betingelser, eller hvis de bruger apps, der ikke understøtter godkendelseskontekster, nægtes de adgang.
            
            Du kan finde flere konfigurationsoplysninger under [Flere oplysninger om afhængighederne for indstillingen godkendelseskontekst](#more-information-about-the-dependencies-for-the-authentication-context-option) i slutningen af dette afsnit.
            
            Eksempler på denne etiketkonfiguration:
            
             - Du vælger en godkendelseskontekst, der er konfigureret til at kræve [multifaktorgodkendelse (MFA).](/azure/active-directory/conditional-access/untrusted-networks) Denne mærkat anvendes derefter på et SharePoint-websted, der indeholder meget fortrolige elementer. Når brugere fra et netværk, der ikke er tillid til, forsøger at få adgang til et dokument på dette websted, får de derfor vist MFA-prompten om, at de skal fuldføre, før de kan få adgang til dokumentet.
             
             - Du vælger en godkendelseskontekst, der er konfigureret til [brugsvilkårspolitikker](/azure/active-directory/conditional-access/terms-of-use). Denne mærkat anvendes derefter på et SharePoint-websted, der indeholder elementer, der kræver en accept af vilkår for anvendelse af juridiske eller overholdelsesmæssige årsager. Når brugerne forsøger at få adgang til et dokument på dette websted, får de derfor vist et vilkår for anvendelse af dokumentet, som de skal acceptere, før de kan få adgang til det oprindelige dokument.

> [!IMPORTANT]
> Det er kun disse indstillinger for websted og gruppe, der træder i kraft, når du anvender mærkaten på et team, en gruppe eller et websted. Hvis [mærkatens omfang](sensitivity-labels.md#label-scopes) omfatter filer og mails, anvendes andre mærkatindstillinger, f.eks. kryptering og indholdsmarkering, ikke på indholdet i teamet, gruppen eller webstedet.

Hvis din følsomhedsmærkat ikke allerede er publiceret, kan du nu publicere den ved [at føje den til en politik for følsomhedsmærkat](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy). De brugere, der har fået tildelt en politik for følsomhedsmærkater, som indeholder denne mærkat, kan vælge den for websteder og grupper.

##### <a name="more-information-about-the-dependencies-for-the-unmanaged-devices-option"></a>Flere oplysninger om afhængighederne for indstillingen ikke-administrerede enheder

Hvis du ikke konfigurerer den afhængige politik for betinget adgang for SharePoint som dokumenteret i [Brug app-gennemtvungne begrænsninger](/sharepoint/app-enforced-restrictions), har den indstilling, du angiver her, ingen effekt. Desuden har den ingen effekt, hvis den er mindre restriktiv end en konfigureret indstilling på lejerniveau. Hvis du har konfigureret en indstilling for hele organisationen for ikke-administrerede enheder, skal du vælge en mærkatindstilling, der enten er den samme eller mere restriktiv

Hvis din lejer f.eks. er konfigureret til **tillad begrænset webadgang**, har den mærkatindstilling, der tillader fuld adgang, ingen effekt, fordi den er mindre restriktiv. Til denne indstilling på lejerniveau skal du vælge mærkatindstillingen for at blokere adgang (mere restriktiv) eller mærkatindstillingen for begrænset adgang (det samme som lejerindstillingen).

Da du kan konfigurere SharePoint-indstillingerne separat fra mærkatkonfigurationen, er der ingen kontrol af konfigurationen af følsomhedsmærkaten for, at afhængighederne er på plads. Disse afhængigheder kan konfigureres, når etiketten er oprettet og publiceret, og selv efter at mærkaten er anvendt. Men hvis mærkaten allerede er anvendt, træder indstillingen for mærkat først i kraft, når brugeren næste godkendes.

##### <a name="more-information-about-the-dependencies-for-the-authentication-context-option"></a>Flere oplysninger om afhængighederne for indstillingen godkendelseskontekst

Godkendelseskontekster skal oprettes, konfigureres og publiceres som en del af konfigurationen af Azure Active Directory-betingelsesadgang for at kunne vises på rullelisten til valg. Du kan finde flere oplysninger og instruktioner i afsnittet [Konfigurer godkendelseskontekster](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts) i dokumentationen Azure AD Betinget adgang.

Det er ikke alle apps, der understøtter godkendelseskontekster. Hvis en bruger med en app, der ikke understøttes, opretter forbindelse til det websted, der er konfigureret til en godkendelseskontekst, får vedkommende vist enten en meddelelse om adgang nægtet, eller de bliver bedt om at godkende, men afvist. De apps, der i øjeblikket understøtter godkendelseskontekster:

- Office på internettet, som omfatter Outlook til internettet

- Microsoft Teams til Windows og macOS (omfatter ikke Teams-webapp)

- Microsoft Planner

- Microsoft 365 Apps til Word, Excel og PowerPoint; minimumversioner:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 2.48.303
    - Android: 16.0.13924.10000

- Microsoft 365 Apps til Outlook; minimumversioner:
    - Windows: 2103
    - macOS: 16.45.1202
    - iOS: 4.2109.0
    - Android: 4.2025.1

- OneDrive-synkronisering app, minimumversioner:
    - Windows: 21.002
    - macOS: 21.002
    - iOS: Udrulning i 12.30
    - Android: Understøttes endnu ikke

Kendte begrænsninger for denne prøveversion:

- I forbindelse med OneDrive-synkronisering-appen understøttes kun for OneDrive og ikke for andre websteder.

- Følgende funktioner og apps kan være inkompatible med godkendelseskontekster, så vi opfordrer dig til at kontrollere, at disse fortsat fungerer, når en bruger har fået adgang til et websted ved hjælp af en godkendelseskontekst:
    
    - Arbejdsprocesser, der bruger Power Apps eller Power Automate
    - Tredjepartsapps

### <a name="configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings"></a>Konfigurer indstillinger for standardlinktypen for deling for et websted ved hjælp af avancerede powerShell-indstillinger

Ud over etiketindstillingerne for websteder og grupper, som du kan konfigurere fra Microsoft Purview-compliance-portal, kan du også konfigurere standardlinktypen for deling for et websted. Følsomhedsmærkater for dokumenter kan også konfigureres for en standardlinktype for deling. Disse indstillinger, der hjælper med at forhindre overdeling, vælges automatisk, når brugerne vælger knappen **Del** i deres Office-apps. 

Du kan finde flere oplysninger og instruktioner under [Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter i SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md).

### <a name="configure-site-sharing-permissions-by-using-powershell-advanced-settings"></a>Konfigurer tilladelser til webstedsdeling ved hjælp af avancerede indstillinger i PowerShell

> [!NOTE]
> Denne etiketindstilling er i øjeblikket en prøveversion.

En anden avanceret PowerShell-indstilling, som du kan konfigurere for, at følsomhedsmærkaten skal anvendes på et SharePoint-websted, er **MembersCanShare**. Denne indstilling er den tilsvarende konfiguration, som du kan angive fra SharePoint Administration > **Webstedstilladelser Webstedsdeling** >  > **Rediger, hvordan medlemmer kan dele** > **delingstilladelser**. 

De tre indstillinger er angivet med de tilsvarende værdier for den avancerede PowerShell-indstilling **MembersCanShare**:

|Mulighed fra SharePoint Administration |Tilsvarende PowerShell-værdi for MembersCanShare |
|----------------------------------------|------------------------------------------------|
|**Webstedsejere og -medlemmer kan dele filer, mapper og webstedet. Personer med redigeringstilladelser kan dele filer og mapper.**| MemberShareAll|
|**Webstedsejere og -medlemmer og personer med tilladelse til at redigere kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet.**|MemberShareFileAndFolder|
|**Det er kun webstedsejere, der kan dele filer, mapper og webstedet.**|MemberShareNone|

Du kan finde flere oplysninger om disse konfigurationsindstillinger i [Rediger, hvordan medlemmer kan dele](/microsoft-365/community/sharepoint-security-a-team-effort#change-how-members-can-share) fra dokumentationen til SharePoint-community'et.

Eksempel, hvor følsomhedsmærkaten GUID er **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{MembersCanShare="MemberShareNone"}
````

Du kan finde mere hjælp til at angive avancerede powerShell-indstillinger under [PowerShell-tip til angivelse af avancerede indstillinger](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="sensitivity-label-management"></a>Administration af følsomhedsmærkat

Brug følgende vejledning til, når du opretter, ændrer eller sletter følsomhedsmærkater, der er konfigureret for websteder og grupper.

### <a name="creating-and-publishing-labels-that-are-configured-for-sites-and-groups"></a>Oprettelse og udgivelse af navne, der er konfigureret for websteder og grupper

Brug følgende vejledning til at publicere en mærkat til dine brugere, når etiketten er konfigureret til indstillinger for websted og gruppe:

1. Når du har oprettet og konfigureret følsomhedsmærkaten, skal du føje denne mærkat til en mærkatpolitik, der kun gælder for nogle få testbrugere.

2. Vent på, at ændringen replikeres:
    
   - Nyt navn: Vent mindst én time.
   - Eksisterende etiket: Vent mindst 24 timer.
    
    Du kan få flere oplysninger om timingen af mærkater under [Hvornår du kan forvente, at nye mærkater og ændringer træder i kraft](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect).

3. Efter denne ventetid skal du bruge en af testbrugerkontiene til at oprette et team, en Microsoft 365-gruppe eller et SharePoint-websted med det navn, du oprettede i trin 1.

4. Hvis der ikke er nogen fejl under denne oprettelseshandling, ved du, at det er sikkert at publicere mærkaten til alle brugere i din lejer.

### <a name="modifying-published-labels-that-are-configured-for-sites-and-groups"></a>Ændring af publicerede navne, der er konfigureret for websteder og grupper

Som bedste praksis skal du ikke ændre indstillingerne for webstedet og gruppen for en følsomhedsmærkat, når mærkaten er blevet anvendt på teams, grupper eller websteder. Hvis du gør det, skal du huske at vente i mindst 24 timer på, at ændringerne replikeres til alle objektbeholdere, hvor mærkaten er anvendt.

Hvis dine ændringer omfatter **adgangsindstillingen eksterne brugere** , skal du desuden gøre følgende:

- Den nye indstilling gælder for nye brugere, men ikke for eksisterende brugere. Hvis denne indstilling f.eks. tidligere er valgt, og gæstebrugerne derfor har åbnet webstedet, kan disse gæstebrugere stadig få adgang til webstedet, når denne indstilling er ryddet i etiketkonfigurationen.

- Indstillingerne for beskyttelse af personlige oplysninger for gruppeegenskaberne hiddenMembership og roleEnabled opdateres ikke.

### <a name="deleting-published-labels-that-are-configured-for-sites-and-groups"></a>Sletter publicerede navne, der er konfigureret for websteder og grupper

Hvis du sletter en følsomhedsmærkat, hvor indstillinger for websted og gruppe er aktiveret, og denne mærkat er inkluderet i en eller flere mærkatpolitikker, kan denne handling resultere i oprettelsesfejl for nye teams, grupper og websteder. Brug følgende vejledning for at undgå denne situation:

1. Fjern følsomhedsmærkaten fra alle mærkatpolitikker, der indeholder mærkaten.

2. Vent mindst én time.

3. Efter denne ventetid kan du prøve at oprette et team, en gruppe eller et websted og bekræfte, at etiketten ikke længere er synlig.

4. Hvis følsomhedsmærkaten ikke er synlig, kan du nu slette mærkaten på en sikker måde.

## <a name="how-to-apply-sensitivity-labels-to-containers"></a>Sådan anvender du følsomhedsmærkater på objektbeholdere

Du er nu klar til at anvende følsomhedsmærkaten eller -mærkaterne på følgende objektbeholdere:

- [Microsoft 365-gruppe i Azure AD](#apply-sensitivity-labels-to-microsoft-365-groups)
- [Microsoft Teams-teamwebsted](#apply-a-sensitivity-label-to-a-new-team)
- [Microsoft 365-gruppe i Outlook på internettet](#apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web)
- [SharePoint-websted](#apply-a-sensitivity-label-to-a-new-site)

Du kan bruge PowerShell, hvis du har brug for at [anvende en følsomhedsmærkat på flere websteder](#use-powershell-to-apply-a-sensitivity-label-to-multiple-sites).

### <a name="apply-sensitivity-labels-to-microsoft-365-groups"></a>Anvend følsomhedsmærkater på Microsoft 365-grupper

Du er nu klar til at anvende følsomhedsmærkaten eller -mærkaterne på Microsoft 365-grupper. Gå tilbage til dokumentationen til Azure AD for at få instruktioner:

- [Tildel en etiket til en ny gruppe i Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

- [Tildel en etiket til en eksisterende gruppe i Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

- [Fjern en etiket fra en eksisterende gruppe i Azure Portal](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

### <a name="apply-a-sensitivity-label-to-a-new-team"></a>Anvend en følsomhedsmærkat på et nyt team

Brugerne kan vælge følsomhedsmærkater, når de opretter nye teams i Microsoft Teams. Når de vælger mærkaten på rullelisten **Følsomhed** , ændres indstillingen for beskyttelse af personlige oplysninger muligvis for at afspejle mærkatkonfigurationen. Afhængigt af den indstilling for adgang til eksterne brugere, du har valgt for mærkaten, kan brugerne føje personer uden for organisationen til teamet.

[Få mere at vide om følsomhedsmærkater til Teams](/microsoftteams/sensitivity-labels)

![Indstillingen for beskyttelse af personlige oplysninger, når du opretter et nyt team.](../media/privacy-setting-new-team.png)

Når du har oprettet teamet, vises følsomhedsmærkaten i øverste højre hjørne af alle kanaler.

![Følsomhedsmærkaten vises på teamet.](../media/privacy-setting-teams.png)

Tjenesten anvender automatisk den samme følsomhedsmærkat på Microsoft 365-gruppen og det forbundne SharePoint-teamwebsted.

### <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Anvend en følsomhedsmærkat på en ny gruppe i Outlook på internettet

Når du opretter en ny gruppe i Outlook på internettet, kan du vælge eller ændre indstillingen **Følsomhed** for publicerede mærkater:

![Oprettelse af en gruppe og valg af en indstilling under Følsomhed.](../media/sensitivity-label-new-group.png)

### <a name="apply-a-sensitivity-label-to-a-new-site"></a>Anvend en følsomhedsmærkat på et nyt websted

Administratorer og slutbrugere kan vælge følsomhedsmærkater, når de [opretter moderne teamwebsteder og kommunikationswebsteder](/sharepoint/create-site-collection), og udvide **Avancerede indstillinger**:

![Oprettelse af et websted og valg af en indstilling under Følsomhed.](../media/sensitivity-label-new-communication-site.png)

På rullelisten vises navnenavnene for markeringen, og hjælpikonet viser alle navne med deres værktøjstip, hvilket kan hjælpe brugerne med at bestemme, hvilken etiket der skal anvendes.

Når mærkaten anvendes, og brugerne navigerer til webstedet, får de vist navnet på mærkaten og anvendte politikker. Dette websted er f.eks. markeret som **Fortroligt**, og indstillingen for beskyttelse af personlige oplysninger er angivet til **Privat**:

:::image type ="content" source="../media/sensitivity-label-site.png" alt-text="Et websted, hvor der er anvendt en følsomhedsmærkat." lightbox="../media/sensitivity-label-site.png":::

### <a name="use-powershell-to-apply-a-sensitivity-label-to-multiple-sites"></a>Brug PowerShell til at anvende en følsomhedsmærkat på flere websteder

Du kan bruge [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) og [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/set-spotenant) med parameteren *SensitivityLabel* fra den aktuelle [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) til at anvende en følsomhedsmærkat på mange websteder. Webstederne kan være en hvilken som helst gruppe af SharePoint-websteder eller et OneDrive-websted.

Kontrollér, at du har version 16.0.19418.12000 eller nyere af SharePoint Online Management Shell.

1. Åbn en PowerShell-session med indstillingen **Kør som administrator** .

2. Hvis du ikke kender guid'et for din mærkat: [Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) , og hent listen over følsomhedsmærkater og deres GUID'er.

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. [Opret nu forbindelse til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online), og gem dit mærkat-GUID som en variabel. Eksempel:

   ```powershell
   $Id = [GUID]("e48058ea-98e8-4940-8db0-ba1310fd955e")
   ```

4. Opret en ny variabel, der identificerer flere websteder, der har en identificerende streng til fælles i deres URL-adresse. Eksempel:

   ```powershell
   $sites = Get-SPOSite -IncludePersonalSite $true -Limit all -Filter "Url -like 'documents"
   ```

5. Kør følgende kommando for at anvende mærkaten på disse websteder. Brug af vores eksempler:

   ```powershell
   $sites | ForEach-Object {Set-SPOTenant $_.url -SensitivityLabel $Id}
   ```

Med denne række kommandoer kan du mærke flere websteder på tværs af din lejer med den samme følsomhedsmærkat, hvilket er grunden til, at du bruger Set-SPOTenant-cmdlet'en i stedet for den Set-SPOSite cmdlet, der bruges til konfiguration pr. websted. Brug dog cmdlet'en Set-SPOSite, når du har brug for at anvende en anden mærkat på bestemte websteder ved at gentage følgende kommando for hvert af disse websteder: `Set-SPOSite -Identity <URL> -SensitivityLabel "<labelguid>"`

## <a name="view-and-manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>Få vist og administrer følsomhedsmærkater i SharePoint Administration

Hvis du vil have vist, sortere og søge i de anvendte følsomhedsmærkater, skal du bruge <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> i det nye SharePoint Administration. Du skal muligvis først tilføje kolonnen **Følsomhed** :

:::image type="content" source=".. /media/manage-site-sensitivity-labels.png" alt-text="Kolonnen Følsomhed på siden Aktive websteder." lightbox=".. /media/manage-site-sensitivity-labels.png"

Du kan finde flere oplysninger om administration af websteder fra siden Aktive websteder, herunder hvordan du tilføjer en kolonne, [under Administrer websteder i det nye SharePoint Administration](/sharepoint/manage-sites-in-new-admin-center).

Du kan også ændre og anvende en mærkat fra denne side:

1. Vælg navnet på webstedet for at åbne detaljeruden.

2. Vælg fanen **Politikker** , og vælg derefter **Rediger** for indstillingen **Følsomhed** .

3. Vælg den følsomhedsmærkat, du vil anvende på webstedet, i ruden **Rediger følsomhedsindstilling** . I modsætning til brugerapps, hvor følsomhedsmærkater kan tildeles til bestemte brugere, viser Administration alle følsomhedsmærkater for din lejer. Når du har valgt en etiket, skal du vælge **Gem**.

## <a name="support-for-sensitivity-labels"></a>Understøttelse af følsomhedsmærkater

Når du bruger administrationscentre, der understøtter følsomhedsmærkater, med undtagelse af Azure Active Directory-portalen, får du vist alle følsomhedsmærkater for din lejer. Til sammenligning kan brugerapps og -tjenester, der filtrerer følsomhedsmærkater i henhold til publiceringspolitikker, resultere i, at du får vist et undersæt af disse mærkater. Azure Active Directory-portalen filtrerer også mærkaterne i henhold til publiceringspolitikker.

Følgende apps og tjenester understøtter følsomhedsmærkater, der er konfigureret for websteder og gruppeindstillinger:

- Administration centre:

  - SharePoint Administration
  - Teams Administration
  - Microsoft 365 Administration
  - Microsoft Purview-overholdelsesportal

- Brugerapps og -tjenester:

  - SharePoint
  - Teams
  - Outlook på internettet og til Windows, macOS, iOS og Android
  - Former
  - Stream
  - Planner 

Følgende apps og tjenester understøtter i øjeblikket ikke følsomhedsmærkater, der er konfigureret for websteder og gruppeindstillinger:

- Administration centre:

  - Exchange Administration

- Brugerapps og -tjenester:

  - Dynamics 365
  - Yammer
  - Project
  - Power BI
  - Mine apps portal

## <a name="classic-azure-ad-group-classification"></a>Klassisk Azure AD gruppeklassificering

Når du har aktiveret følsomhedsmærkater for objektbeholdere, understøttes gruppeklassificeringer fra Azure AD ikke længere af Microsoft 365 og vises ikke på websteder, der understøtter følsomhedsmærkater. Du kan dog konvertere dine gamle klassificeringer til følsomhedsmærkater.

Som et eksempel på, hvordan du måske har brugt den gamle gruppeklassificering til SharePoint, skal du se [Klassificering af "moderne" SharePoint-websteder](/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Disse klassificeringer blev konfigureret ved hjælp af Azure AD PowerShell eller PnP-kernebiblioteket og definere værdier for `ClassificationList` indstillingen. Hvis din lejer har defineret klassificeringsværdier, vises de, når du kører følgende kommando fra [AzureADPreview PowerShell-modulet](https://www.powershellgallery.com/packages/AzureADPreview):

```powershell
($setting["ClassificationList"])
```

Benyt en af følgende fremgangsmåder for at konvertere dine gamle klassificeringer til følsomhedsmærkater:

- Brug eksisterende mærkater: Angiv de ønskede mærkatindstillinger for websteder og grupper ved at redigere eksisterende følsomhedsmærkater, der allerede er publiceret.

- Opret nye mærkater: Angiv de ønskede mærkatindstillinger for websteder og grupper ved at oprette og publicere nye følsomhedsmærkater, der har samme navne som dine eksisterende klassificeringer.

Derefter:

1. Brug PowerShell til at anvende følsomhedsmærkater på eksisterende Microsoft 365-grupper og SharePoint-websteder ved hjælp af navnetilknytning. Se næste afsnit for at få instruktioner.

2. Fjern de gamle klassificeringer fra de eksisterende grupper og websteder.

Selvom du ikke kan forhindre brugerne i at oprette nye grupper i apps og tjenester, der endnu ikke understøtter følsomhedsmærkater, kan du køre et tilbagevendende PowerShell-script for at søge efter nye grupper, som brugerne har oprettet med de gamle klassificeringer, og konvertere dem til at bruge følsomhedsmærkater.

For at hjælpe dig med at administrere sameksistensen af følsomhedsmærkater og Azure AD klassificeringer for websteder og grupper, skal du se [Azure Active Directory-klassificering og følsomhedsmærkater til Microsoft 365-grupper](migrate-aad-classification-sensitivity-labels.md).

### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Brug PowerShell til at konvertere klassificeringer for Microsoft 365-grupper til følsomhedsmærkater

1. Først [skal du oprette forbindelse til Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

   Log f.eks. på med en global administratorkonto i en PowerShell-session, som du kører som administrator:

2. Hent listen over følsomhedsmærkater og deres GUID'er ved hjælp af cmdlet'en [Get-Label](/powershell/module/exchange/get-label) :

   ```powershell
   Get-Label |ft Name, Guid
   ```

3. Notér GUID'erne for de følsomhedsmærkater, du vil anvende på dine Microsoft 365-grupper.

4. [Opret nu forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et separat Windows PowerShell vindue.

5. Brug følgende kommando som et eksempel til at få vist en liste over grupper, der i øjeblikket har klassificeringen "Generelt":

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Tilføj den nye GUID for følsomhedsmærkaten for hver gruppe. Eksempel:

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Gentag trin 5 og 6 for dine resterende gruppeklassificeringer.

## <a name="auditing-sensitivity-label-activities"></a>Overvågning af aktiviteter for følsomhedsmærkater

> [!IMPORTANT]
> Hvis du kun bruger mærkatadskillelse ved kun at vælge **området Grupper & websteder** for etiketter, der beskytter objektbeholdere: På grund af den registrerede overvågningshændelse for **følsomhedsovertrædelse for dokumenter** og mail, der er beskrevet i dette afsnit, bør du overveje at [sortere mærkater](sensitivity-labels.md#label-priority-order-matters) før etiketter, der har et område for **Elementer**. 

Hvis nogen uploader et dokument til et websted, der er beskyttet med en følsomhedsmærkat, og deres dokument har en følsomhedsmærkat med [højere prioritet](sensitivity-labels.md#label-priority-order-matters) end den følsomhedsmærkat, der er anvendt på webstedet, blokeres denne handling ikke. Du har f.eks. anvendt mærkaten **Generelt** på et SharePoint-websted, og nogen uploader et dokument med navnet **Fortroligt** til dette websted. Da en følsomhedsmærkat med en højere prioritet identificerer indhold, der er mere følsomhed end indhold, der har en lavere prioritet, kan denne situation være et sikkerhedsproblem.

Selvom handlingen ikke er blokeret, overvåges den og genererer som standard automatisk en mail til den person, der har uploadet dokumentet, og webstedsadministratoren. Derfor kan både brugeren og administratorer identificere dokumenter, der har denne forkerte mærkatprioritet, og udføre handlinger, hvis det er nødvendigt. Slet eller flyt f.eks. det overførte dokument fra webstedet.

Det ville ikke være et sikkerhedsproblem, hvis dokumentet har en følsomhedsmærkat med lavere prioritet end den følsomhedsmærkat, der er anvendt på webstedet. Et dokument med navnet **Generelt** uploades f.eks. til et websted med navnet **Fortroligt**. I dette scenarie genereres der ikke en overvågningshændelse og mail.

> [!NOTE]
> På samme måde som for den politikindstilling, der kræver, at brugerne skal angive en begrundelse for at ændre en mærkat til en lavere klassificering, anses undermærkater for den samme overordnede etiket alle for at have samme prioritet.

Hvis du vil søge i overvågningsloggen efter denne hændelse, skal du søge efter **Registreret uoverensstemmelse mellem dokumentfølsomhed** **fra kategorien Fil- og sideaktiviteter** .

Den automatisk genererede mail har **registreret emnet Inkompatibel følsomhedsmærkat** , og i mailen forklares mærkatuoverensstemmelsen med et link til det uploadede dokument og det uploadede websted. Den indeholder også et dokumentationslink, der forklarer, hvordan brugerne kan ændre følsomhedsmærkaten. Disse automatiserede mails kan ikke tilpasses, men du kan forhindre, at de sendes, når du bruger følgende [PowerShell-kommando fra Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant):

```PowerShell
Set-SPOTenant -BlockSendLabelMismatchEmail $True
```

Når en person tilføjer eller fjerner en følsomhedsmærkat til eller fra et websted eller en gruppe, overvåges disse aktiviteter også, men uden at der genereres en mail automatisk.

Alle disse overvågningshændelser kan findes i kategorien [Aktiviteter for følsomhedsmærkat](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) . Du kan finde instruktioner i, hvordan du søger i overvågningsloggen, [under Søg i overvågningsloggen i Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md).

## <a name="how-to-disable-sensitivity-labels-for-containers"></a>Sådan deaktiverer du følsomhedsmærkater for objektbeholdere

Du kan slå følsomhedsmærkater fra for Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder ved hjælp af de samme instruktioner fra [Aktivér understøttelse af følsomhedsmærkat i PowerShell](/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell). Hvis du vil deaktivere funktionen, skal du dog angive `$setting["EnableMIPLabels"] = "False"`i trin 5.

Ud over at gøre alle indstillingerne utilgængelige for grupper og websteder, når du opretter eller redigerer følsomhedsmærkater, gendanner denne handling den egenskab, objektbeholderne bruger til deres konfiguration. Aktivering af følsomhedsmærkater for Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder skifter den egenskab, der bruges fra **Klassificering** (bruges til [Azure AD gruppeklassificering](#classic-azure-ad-group-classification)) til **Følsomhed**. Når du deaktiverer følsomhedsmærkater for objektbeholdere, ignorerer objektbeholderne egenskaben Følsomhed og bruger egenskaben Klassificering igen.

Det betyder, at alle etiketindstillinger fra websteder og grupper, der tidligere er anvendt på objektbeholdere, ikke gennemtvinges, og objektbeholdere viser ikke længere mærkaterne.

Hvis disse objektbeholdere har Azure AD anvendte klassificeringsværdier, vender objektbeholderne tilbage til at bruge klassificeringerne igen. Vær opmærksom på, at nye websteder eller grupper, der er oprettet efter aktivering af funktionen, ikke viser en mærkat eller har en klassificering. For disse objektbeholdere og eventuelle nye objektbeholdere kan du nu anvende klassificeringsværdier. Du kan finde flere oplysninger under [Klassificering af "moderne" SharePoint-websteder](/sharepoint/dev/solution-guidance/modern-experience-site-classification) og [Opret klassificeringer til Office-grupper i din organisation](../enterprise/manage-microsoft-365-groups-with-powershell.md).

## <a name="additional-resources"></a>Yderligere ressourcer

Se webinarets optagelse og besvarede spørgsmål om [brug af følsomhedsmærkater med Microsoft Teams, O365 Grupper og SharePoint Online-websteder](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380).

Dette webinar blev registreret, da funktionen stadig var en prøveversion, så du vil måske bemærke nogle uoverensstemmelser i brugergrænsefladen. Oplysningerne om denne funktion er dog stadig nøjagtige med alle nye funktioner, der er dokumenteret på denne side.

Du kan finde flere oplysninger om administration af Teams-forbundne websteder og kanalwebsteder under [Administrer Teams-forbundne websteder og kanalwebsteder](/SharePoint/teams-connected-sites).
