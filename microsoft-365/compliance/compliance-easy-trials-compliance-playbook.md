---
title: Prøveversion af Microsoft Purview-løsninger
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Prøveversion af Microsoft Purview-løsninger.
ms.custom: trial-playbook
ms.openlocfilehash: 981f4d619eeef380625d6de8194e9cb0c42e2011
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530274"
---
# <a name="trial-playbook-microsoft-purview-solutions"></a>Playbook til prøveversion: Microsoft Purview-løsninger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Velkommen til prøveversionen af Microsoft Purview-løsninger. Denne playbook hjælper dig med at få mest ud af din 90-dages gratis prøveversion ved at hjælpe dig med at finde robuste og omfattende funktioner i Microsoft Purview- og sikkerhedsprodukter.

Når du prøver hver løsning, kan du træffe velunderbyggede beslutninger for at opfylde organisationens behov for overholdelse af angivne standarder.

Funktioner:

- [Overvågning (Premium)](#audit-premium)
- [Kommunikation med overholdelse af angivne standarder](#communication-compliance)
- [Overholdelsesstyring](#compliance-manager)
- [Administration af datalivscyklus](#data-lifecycle-management)
- [Microsoft Purview Forebyggelse af datatab](#data-loss-prevention)
- [eDiscovery](#ediscovery)
- [Information Protection](#information-protection)
- [Styring af insiderrisiko](#insider-risk-management)
- [Datastyring](#records-management)

Valgfrie tilføjelsesprogrammer:

- [Premiumvurderinger af Overholdelsesstyring](#compliance-manager-premium-assessments)
- [Microsoft Priva håndtering af privatlivsrisici og Microsoft Priva Anmodninger om den registreredes rettigheder](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-purview"></a>Handlinger til overholdelse af angivne standarder med Microsoft Purview

Du kan nemt og hurtigt begynde at prøve Microsofts løsninger til overholdelse af angivne standarder uden at ændre organisationens metadata. Afhængigt af dine prioriteter kan du starte med et hvilket som helst af disse løsningsområder for at se øjeblikkelig værdi. Nedenfor er fem vigtigste organisatoriske bekymringer som kommunikeret af vores kunder og anbefalede løsninger til at starte med.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Handlinger for overholdelse af angivne standarder med Microsoft 365":::

## <a name="audit-premium"></a>Overvågning (Premium)

**Udfør undersøgelser**:

Microsoft Purview-gennemgang (Premium) hjælper organisationer med at udføre tekniske undersøgelser og undersøgelser af overholdelse af angivne standarder ved at øge den opbevaring af overvågningsloggen, der kræves for at udføre en undersøgelse, give adgang til vigtige hændelser, der hjælper med at bestemme omfanget af kompromiser og give hurtigere adgang til API'en for Office 365 managementaktivitet.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>Trin 1: [Anvend E5-licensen på hver bruger, som du vil generere E5-hændelser for](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Overvågningsfunktioner (Premium), f.eks. muligheden for at logføre vigtige hændelser som MailItemsAccessed og Send, kræver en passende E5-licens, der er tildelt til brugerne. Derudover skal app-/tjenesteplanen Avanceret overvågning være aktiveret for disse brugere.

Konfigurer overvågning (Premium) for brugere – udfør [følgende trin for hver bruger](set-up-advanced-audit.md#step-1-set-up-audit-premium-for-users) for at bekræfte, at appen Avanceret overvågning er tildelt til brugere.

1. Aktivér overvågningshændelser (Premium) – [aktivér, at SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-audit-premium-events) overvåges for hver bruger i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. Konfigurer politikker for opbevaring af overvågning – [opret yderligere politikker for opbevaring af overvågningslog](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) for at opfylde kravene i organisationens sikkerhedshandlinger, it og overholdelsesteams.
1. Søg efter Overvågningshændelser (Premium) – [søg efter vigtige overvågningshændelser (Premium)](set-up-advanced-audit.md#step-4-search-for-audit-premium-events) og andre aktiviteter, når der udføres kriminaltekniske undersøgelser.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>Trin 2: [Opret nye politikker for overvågningslogfiler for at angive, hvor længe overvågningslogge i organisationen skal bevares for aktiviteter, der udføres af brugere, og definere prioritetsniveauer for dine politikker](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Bedste praksis for prøveversion: Opret inden for de første 30 dage

Opbevaringspolitikker for overvågningslog er en del af de nye overvågningsfunktioner (Premium) i Microsoft Purview. En opbevaringspolitik for overvågningslog giver dig mulighed for at angive, hvor længe overvågningslogge skal bevares i din organisation.

1. Før du opretter en opbevaringspolitik for overvågningsloggen – [vigtige ting at vide,](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) før du opretter din politik.
1. [Opret en opbevaringspolitik for overvågningslog](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Administrer opbevaringspolitikker for overvågningslog i Microsoft Purview-compliance-portal](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-compliance-portal) – Opbevaringspolitikker for overvågningslog vises under fanen Overvågning af opbevaringspolitikker (også kaldet dashboardet). Du kan bruge dashboardet til at få vist, redigere og slette politikker for overvågningsopbevaring.
1. Opret og administrer opbevaringspolitikker for overvågningslog på PowerShell – Du kan også bruge PowerShell til sikkerhed & overholdelse af angivne standarder til at [oprette og administrere opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). En af grundene til at bruge PowerShell er at oprette en politik for en posttype eller aktivitet, der ikke er tilgængelig i brugergrænsefladen.

## <a name="communication-compliance"></a>Kommunikation med overholdelse af angivne standarder

**Identificer og håndtér ordensregler for politikovertrædelser**:

Microsoft Purview Kommunikationsoverholdelse hjælper dig med på intelligent vis at identificere kommunikationsovertrædelser for at understøtte et kompatibelt og sundt arbejdsmiljø ved at hjælpe dig med at registrere upassende meddelelser, undersøge mulige politikovertrædelser og træffe foranstaltninger til afhjælpning.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>Trin 1: [Aktivér tilladelser til kommunikation med overholdelse af angivne standarder](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

[Tildel alle brugere af overholdelse af angivne standarder til rollegruppen Kommunikationsoverholdelse](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

### <a name="step-2-enable-the-audit-log"></a>Trin 2: [Aktivér overvågningsloggen](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Bedste praksis for prøveversion: Konfiguration inden for de første 30 dage

Hvis du vil bruge denne funktion, skal du aktivere overvågning, så din organisation kan begynde at optage bruger- og administratoraktivitet i din organisation. Når du slår dette til, registreres aktiviteten i overvågningsloggen og bliver tilgængelig til visning i en rapport. Du kan få mere at vide under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>Trin 3: [Opret en politik for overholdelse af angivne standarder for kommunikation](communication-compliance-policies.md)

[Opret en politik for overholdelse af angivne standarder for kommunikation ved hjælp af de eksisterende skabeloner](communication-compliance-policies.md): 1 - Upassende indhold; 2- Følsomme oplysninger; 3 - Lovmæssig overholdelse; 4 - Interessekonflikt.

### <a name="step-4-investigate-and-remediate-alerts"></a>Trin 4: [Undersøg og afhjælp beskeder](communication-compliance-investigate-remediate.md)

[Undersøg og afhjælp](communication-compliance-investigate-remediate.md) beskeder om kommunikation med overholdelse af angivne standarder.

## <a name="compliance-manager"></a>Overholdelsesstyring

**Administrer nemt organisationens overholdelse af angivne standarder**:

Microsoft Purview Compliance Manager kan hjælpe dig gennem hele overholdelsesrejsen, lige fra opgørelse af dine databeskyttelsesrisici til administration af kompleksiteten ved implementering af kontroller, overholdelse af regler og certificeringer og rapportering til auditører.

### <a name="step-1-get-to-know-compliance-manager"></a>Trin 1: [Lær Overholdelsesstyring at kende](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Oversigtssiden For Overholdelsesstyring er det bedste første stop for en omfattende gennemgang af, hvad Overholdelsesstyring er, og hvordan det fungerer. Det kan også være en god idé at gå direkte til vigtige afsnit i vores dokumentation ved hjælp af nedenstående links:

- [Forstå din overholdelsesscore](compliance-manager.md#understanding-your-compliance-score)
- [Oversigt over nøgleelementer: kontrolelementer, vurderinger, skabeloner og forbedringshandlinger](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Forstå dashboardet Overholdelsesstyring](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Filtrer din dashboardvisning](compliance-manager-setup.md#filtering-your-dashboard-view)
- [Få mere at vide om forbedringshandlinger](compliance-manager-setup.md#improvement-actions-page)
- [Forstå vurderinger](compliance-manager.md#assessments)
- [Foretage en hurtig scanning af dit miljø ved hjælp af Microsoft Compliance Configuration Manager](compliance-manager-mcca.md)

![Overholdelsesstyring – dashboard.](../media/compliance-manager-dashboard.png "Dashboardet Overholdelsesstyring")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>Trin 2: [Konfigurer Overholdelsesstyring for at administrere dine aktiviteter for overholdelse af angivne standarder](compliance-manager-assessments.md)

> [!TIP]
> Bedste praksis for prøveversion: Undersøg inden for de første 30 dage

Begynd at arbejde med vurderinger og udføre forbedringshandlinger for at implementere kontrolelementer og forbedre din score for overholdelse af angivne standarder.

1. [Vælg en færdigbygget skabelon til at oprette og administrere din første vurdering](compliance-manager-assessments.md).
1. [Forstå, hvordan du bruger skabeloner til oprettelse af vurderinger](compliance-manager-templates.md).
1. [Udfør implementerings- og testarbejde på forbedringshandlinger for at fuldføre kontrolelementer i dine vurderinger](compliance-manager-improvement-actions.md).
1. [Få en bedre forståelse af, hvordan forskellige handlinger påvirker din score for overholdelse af angivne standarder](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365- eller Office 365 E1/E3-abonnementet indeholder skabelonen Microsoft Data Protection Baseline. Microsoft 365 eller Office 365 E5, E5 Compliance indeholder skabeloner til:
>
> - Microsoft Data Protection Baseline
> - EU's GDPR  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Overholdelsesstyring indeholder mere end 300 lovmæssige eller Premium-skabeloner, der kan købes som et tilføjelsesprogram. Se listen her. Med alle Premium-skabeloner (inkluderet i dit abonnement eller købt som tilføjelsesprogram) modtager du den universelle version af disse skabeloner, så du kan administrere din overholdelse af alle produkter eller tjenester

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>Trin 3: [Opskalering: Brug avanceret funktionalitet til at opfylde dine brugerdefinerede behov](compliance-manager-templates-create.md)

Brugerdefinerede vurderinger er nyttige i forbindelse med:

- Administration af overholdelse af angivne standarder for ikke-Microsoft 365-produkter, f.eks. tredjepartsapps og -tjenester, programmer i det lokale miljø og andre aktiver
- Administration af dine egne brugerdefinerede eller virksomhedsspecifikke kontrolelementer til overholdelse af angivne standarder

1. [Udvid en skabelon for Overholdelsesstyring ved at tilføje dine egne kontrolelementer og forbedringshandlinger](compliance-manager-templates-extend.md)
1. [Opret din egen brugerdefinerede skabelon](compliance-manager-templates-create.md)
1. [Rediger en eksisterende skabelon for at tilføje eller fjerne kontrolelementer og handlinger](compliance-manager-templates-modify.md)
1. [Konfigurer automatiseret test af forbedringshandlinger](compliance-manager-setup.md#set-up-automated-testing)
1. [Overdrag forbedringshandlinger til en anden bruger](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-lifecycle-management"></a>Administration af datalivscyklus

**Styr i stor skala med automatisering**:

Gør det bedre at tilpasse dig ændringer i din organisation med politikområder, der automatisk opdateres. Automatiser mærkning af indhold for at reducere den manuelle indsats og forbedre overholdelsesholdning.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>Trin 1: Målret dynamisk opbevaringspolitikker med tilpassede politikområder

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Tilpassede politikområder giver dig mulighed for dynamisk at målrette en politik til bestemte brugere, grupper eller websteder baseret på deres AD-attributter.  Attributter for områder kan vælges på en liste eller tilpasses ved hjælp af en avanceret forespørgselsgenerator.

Politikker, der bruger tilpassede politikområder, forbliver opdaterede, efterhånden som organisationen ændres, når nye medarbejdere tilmelder sig eller forlader virksomheden. Derudover er de ikke underlagt de tidligere grænser på 100/1.000 placeringer, der er inkluderet i en politik.

- Opret et adaptivt politikområde, og brug det sammen med en opbevaringspolitik

### <a name="step-2-automate-labeling-to-apply-a-label-to-all-items-by-default"></a>Trin 2: Automatiser mærkning for at anvende en etiket på alle elementer som standard

> [!TIP]
> Bedste praksis for prøveversion: Konfiguration inden for de første 30 dage

Standardnavne giver dig mulighed for automatisk at anvende en opbevaringsmærkat på alle elementer i et angivet bibliotek, en angivet mappe eller et angivet dokumentsæt i SharePoint.

- Publicer en etiket, og anvend den som standard i SharePoint

## <a name="data-loss-prevention"></a>Forebyggelse af datatab

**Beskyt følsomme data**:

Organisationer skal beskytte følsomme oplysninger for at overholde forretningsstandarder og brancheregler for at forhindre utilsigtede afsløringer. Konfigurer Microsoft Purview Forebyggelse af datatab politikker for at identificere, overvåge og automatisk beskytte følsomme oplysninger på tværs af Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>Trin 1: [Beskyt datatab på Teams-placeringer](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Hvis din organisation har forebyggelse af datatab, kan du definere politikker, der forhindrer personer i at dele følsomme oplysninger i en Microsoft Teams-kanal eller -chatsession.

1. Få mere at vide om [DLP-licenser til Microsoft Teams og omfanget af DLP-beskyttelse](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Føj Microsoft Teams som en placering til eksisterende DLP-politikker](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Konfigurer vores DLP-standardpolitik for Teams](mip-easy-trials.md) eller [Definer en ny DLP-politik for Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>Trin 2: [Beskyt datatab på enhedens placeringer](endpoint-dlp-getting-started.md)

> [!TIP]
> Bedste praksis for prøveversion: Konfiguration inden for de første 30 dage

Med Microsoft Endpoint DLP kan du overvåge Windows 10 enheder og registrere, hvornår følsomme elementer bruges og deles.

1. Forbered dine slutpunkter – sørg for, at de Windows 10- og macOS-enheder, du planlægger at installere Endpoint DLP, for at [opfylde disse krav](endpoint-dlp-getting-started.md)
1. [Onboarder enheder i enhedsadministration](endpoint-dlp-getting-started.md)  – Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres i Microsoft Purview-compliance-portal.
   - Scenarie 1 – [Onboarding-enheder](endpoint-dlp-getting-started.md) , der endnu ikke er onboardet.
   - Scenarie 2 – [Microsoft Defender for Endpoint er allerede installeret, og der rapporteres slutpunkter i](endpoint-dlp-getting-started.md). Alle disse slutpunkter vises på listen over administrerede enheder.
1. [Konfigurer vores DLP-standardpolitik for enheder](mip-easy-trials.md#dlp-for-devices) eller [Definer en ny DLP-politik for enheder](endpoint-dlp-learn-about.md).
1. [Vis DLP-beskeder for slutpunktet](dlp-configure-view-alerts-policies.md) i dashboardet administration af DLP-beskeder.
1. [Vis DLP-data for slutpunktet](data-classification-activity-explorer.md) i aktivitetsoversigten.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>Trin 3: [Udvid politikker i omfang eller beskyttelse](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

Du har fleksibilitet i den måde, du konfigurerer dine DLP-politikker på. Du kan starte med vores DLP-standardpolitik for Teams og enheder og udvide disse politikker for at beskytte yderligere placeringer, følsomme oplysningstyper eller mærkater. Derudover kan du udvide politikhandlingerne og tilpasse beskeder.

1. Tilføj placeringer
1. Tilføj følsomme oplysningstyper eller mærkater for at beskytte
1. Tilføj handlinger
   - Hold:
      - [Undgå ekstern adgang til følsomme dokumenter](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Få politiktips, der kan hjælpe med at oplære brugere og instruktioner i tilpasning af politiktips](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Enheder: Skift kun fra overvågning til blok
1. [Konfigurer og få vist beskeder om politikker til forebyggelse af datatab – Microsoft Purview | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eDiscovery

**Få mere at vide med en komplette arbejdsproces**:

Udnyt en arbejdsproces fra start til slut til bevarelse, indsamling, analyse og eksport af indhold, der reagerer på din organisations interne og eksterne undersøgelser. Juridiske teams kan også administrere hele processen for anmeldelse af juridiske ventepositioner ved at kommunikere med tilsynsførende, der er involveret i en sag.

### <a name="step-1-required-permissions"></a>Trin 1 (påkrævet): [Tilladelser](https://aka.ms/ediscoveryninja)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Hvis du vil have adgang til eDiscovery (Premium) eller tilføjes som medlem af en eDiscovery-sag (Premium), skal en bruger tildeles de relevante tilladelser.

1. [Konfigurer eDiscovery (Premium) – tildel eDiscovery-tilladelser](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Tilføj eller fjern medlemmer fra en sag](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>Trin 2 (påkrævet): Opret en sag

> [!TIP]
> Bedste praksis for prøveversion: Opret inden for de første 30 dage

Flere organisationer bruger eDiscovery-løsningen (Premium) i Microsoft Purview til kritiske eDiscovery-processer. Dette omfatter besvarelse af lovmæssige anmodninger, undersøgelser og retssager.

1. Administrer eDiscovery (Premium) – [få mere at vide om, hvordan du konfigurerer eDiscovery (Premium), administrerer sager, administrerer en arbejdsproces i eDiscovery (Premium) og analyserer søgeresultaterne for eDiscovery (Premium](/learn/modules/manage-advanced-ediscovery)).
1. [Opret en eDiscovery-sag ved hjælp af det nye sagsformat i Advance eDiscovery](advanced-ediscovery-new-case-format.md)
1. [Luk eller slet en sag](close-or-delete-case.md) – Når sagen eller undersøgelsen er afsluttet, kan du lukke eller slette den. Du kan også genåbne en lukket sag.

### <a name="step-3-optional-settings"></a>Trin 3 (valgfrit): Indstillinger

Hvis du vil tillade, at personer i din organisation begynder at oprette og bruge sager, skal du konfigurere globale indstillinger, der gælder for alle sager i din organisation. På nuværende tidspunkt er den eneste globale indstilling **registrering af rettigheder for advokater og klienter** (flere globale indstillinger vil være tilgængelige i fremtiden).

1. [Konfigurer eDiscovery (Premium) – globale indstillinger](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-ediscovery-premium)
1. [Konfigurer indstillinger for søgning og analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [Administrer job i eDiscovery (Premium)](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>Trin 4 (valgfrit): [Overholdelsesgrænser](set-up-compliance-boundaries.md)

Overholdelsesgrænser opretter logiske grænser i en organisation, der styrer placeringen af brugerindhold (f.eks. postkasser, OneDrive-konti og SharePoint-websteder), som eDiscovery-ledere kan søge i. De styrer også, hvem der kan få adgang til eDiscovery-sager, der bruges til at administrere de juridiske, menneskelige ressourcer eller andre undersøgelser i din organisation.

![Overholdelsesgrænser består af søgetilladelsesfiltre, der styrer adgangen til agenturer og administratorrollegrupper, der styrer adgangen til eDiscovery-sager.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser:

1. [Identificer en brugerattribut for at definere dine agenturer](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Opret en rollegruppe for hvert agentur](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Opret et filter for søgetilladelser for at gennemtvinge overholdelsesgrænsen](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Opret en eDiscovery-sag for en undersøgelse inden for bureauet](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>Trin 5 (valgfrit): [Få mere at vide om søgeværktøjet indhold](search-for-content.md)

Brug søgeværktøjet indhold i Microsoft Purview-compliance-portal til hurtigt at finde mails i Exchange-postkasser, dokumenter på SharePoint-websteder og OneDrive-placeringer og chatsamtaler i Skype for Business. Du kan bruge værktøjet til indholdssøgning til at søge efter mail, dokumenter og chatsamtaler i samarbejdsværktøjer, f.eks. Microsoft Teams og Microsoft 365-grupper.

- [Få mere at vide om eDiscovery-søgning (Premium)](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Information Protection

**Find, klassificer og beskyt dine følsomme oplysninger**:

Implementer Microsoft Purview Information Protection og følsomhedsmærkater for at hjælpe dig med at finde, klassificere og beskytte dit følsomme indhold, uanset hvor det bor eller rejser.

### <a name="step-1-start-your-information-protection-trial"></a>Trin 1: [Start prøveversionen af beskyttelse af oplysninger](mip-easy-trials.md)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Berettigede kunder kan aktivere standardmærkater og -politikker for Microsoft Purview Information Protection. Når du aktiverer standardkonfigurationen i prøveversionen, tager det ca. 2 minutter at konfigurere alle politikker for din lejer og op til 24 timer for at se resultaterne af disse standardpolitikker.

Hvis du vælger standardkonfigurationen med et enkelt klik, konfigureres følgende automatisk:

- Følsomhedsmærkater og en politik for følsomhedsmærkater
- Automatisk mærkning på klientsiden
- Automærkater på tjenestesiden
- DLP-politikker (forebyggelse af datatab) for Teams og enheder

[Aktivér standardmærkater og -politikker](mip-easy-trials.md#activate-the-default-labels-and-policies). Hvis det er nødvendigt, kan du redigere manuelt, når konfigurationen er fuldført.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>Trin 2: [Anvend automatisk følsomhedsmærkater på dokumenter](apply-sensitivity-label-automatically.md)

> [!TIP]
> Bedste praksis for prøveversion: Konfiguration inden for de første 30 dage

Når du opretter en følsomhedsmærkat, kan du automatisk tildele denne mærkat til filer og mails, når den opfylder betingelser, som du angiver.

1. [Opret og konfigurer følsomhedsmærkater](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Publicer politik for følsomhedsmærkat til alle brugere](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Opret en politik for automatisk mærkning](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Vælg de oplysninger, som mærkaten skal anvendes på
   - Definer de placeringer, der skal anvendes mærkat
   - Vælg det navn, der skal anvendes
   - [Kør politik i simuleringstilstand](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Ny politikkonfiguration til automatisk mærkning.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>Trin 3: [Gennemse og slå politik for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) til

Nu kan du på siden **Information Protection** > **Auto-labeling** se din politik for automatisk mærkning i afsnittet **Simulering** .

Vælg din politik for at få vist detaljer om konfigurationen og status. Når simuleringen er fuldført, skal du vælge fanen Elementer, der skal gennemses for at se, hvilke mails eller dokumenter der stemmer overens med de angivne regler.

Når du er klar til at køre politikken uden simulering, skal du vælge indstillingen **Slå politik** til.

## <a name="insider-risk-management"></a>Styring af insiderrisiko

**Registrer og afhjælp insiderrisici**:

Udnyt kunstig intelligens, så du hurtigt kan identificere, sortere og afhjælpe interne risici. Ved hjælp af logge fra Microsoft 365- og Azure-tjenester kan du definere politikker, der overvåger for insiderrisikosignaler, og derefter udføre afhjælpningshandlinger, f.eks. fremme af brugeruddannelse eller starte en undersøgelse.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Trin 1 (påkrævet): [Aktivér tilladelser til styring af insiderrisiko](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Der er fire rollegrupper, der bruges til at konfigurere tilladelser til at administrere funktioner til styring af insiderrisiko.

[Føj brugere til en rollegruppe for styring af insiderrisiko.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

Hvis du ikke kan se tilladelser, skal du kontakte din lejeradministrator for at tildele de korrekte roller.

### <a name="step-2-start-with-user-quick-start-guide"></a>Trin 2: [Start med brugervejledning til hurtig start](insider-risk-management-configure.md#recommended-actions-preview)

Kom hurtigt i gang, og få mest ud af funktionerne til styring af insiderrisiko med anbefalede handlinger. Inkluderet på siden Oversigt hjælper anbefalede handlinger dig gennem trinnene til konfiguration og installation af politikker og undersøgelseshandlinger for brugerhandlinger, der genererer beskeder fra politikforekomster.

[Vælg en anbefaling på listen](insider-risk-management-configure.md#recommended-actions-preview) for at komme i gang med at konfigurere styring af insiderrisiko.

![Anbefalede handlinger til styring af insiderrisiko.](../media/insider-risk-recommended-actions.png)

Hver anbefalet handling guider dig gennem de påkrævede aktiviteter for anbefalingen, herunder eventuelle krav, hvad du kan forvente, og virkningen af at konfigurere funktionen i din organisation.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>Trin 3 (påkrævet): [Aktivér Microsoft 365-overvågningsloggen](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Overvågning er som standard aktiveret for Microsoft 365-organisationer. Nogle organisationer kan have deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for din organisation, kan det skyldes, at en anden administrator har deaktiveret den. Vi anbefaler, at du bekræfter, at det er OK at aktivere overvågning igen, når du fuldfører dette trin.

Du kan finde en trinvis vejledning til, hvordan du slår overvågning til, under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md). Når du har slået overvågning til, vises der en meddelelse om, at overvågningsloggen er ved at blive forberedt, og at du kan køre en søgning om et par timer, efter at forberedelsen er fuldført. Du behøver kun at gøre denne handling én gang. Du kan finde flere oplysninger om, hvordan du bruger Microsoft 365-overvågningsloggen, under [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>Trin 4 (påkrævet): [Aktivér og få vist indsigt i insiderrisikoanalyse](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Analyse af styring af insiderrisiko giver dig mulighed for at evaluere potentielle insiderrisici i din organisation uden at konfigurere nogen politikker for insiderrisiko. Resultaterne af analysescanningen kan tage op til 48 timer, før indsigt er tilgængelig som rapporter til gennemsyn. Hvis du vil vide mere om indsigt i analyse, skal du se [Indstillinger for styring af insiderrisiko: Analytics (prøveversion)](insider-risk-management-settings.md) og se [videoen Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) for at hjælpe dig med at forstå din insiderrisikoholdning og hjælpe dig med at træffe foranstaltninger ved at konfigurere relevante politikker for at identificere risikable brugere.

Hvis du vil aktivere insiderrisikoanalyse, skal du være medlem af Insider Risk Management eller Insider Risk Management Administration. [Udfør disse trin for at aktivere insiderrisikoanalyse](insider-risk-management-configure.md).

## <a name="records-management"></a>Datastyring

**Administrer elementer af høj værdi for forretnings-, juridiske eller lovmæssige krav til registrering**:

Brug Microsoft Purview-datastyring funktioner til at automatisere opbevaringsplanen for organisatoriske lovmæssige, juridiske og forretningskritiske poster. Udnyt automatiseringsfunktioner fra oprettelse gennem samarbejde for at deklarere poster, bevare indhold og fjerne dem til sidst.

### <a name="step-1-mark-contents-as-records"></a>Trin 1: Markér indhold som poster  

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Når indhold erklæres som en post, er der begrænsninger for elementet med hensyn til, hvilke handlinger der er tilladt eller blokeret, yderligere aktiviteter om elementerne logføres, og du har bevis for fordeling, hvis elementerne slettes ved slutningen af deres opbevaringsperiode.

- Opret en opbevaringsmærkat, der deklarerer indhold som en post eller en lovmæssig post

### <a name="step-2-review-content-to-approve-before-its-permanently-deleted"></a>Trin 2: Gennemse indhold, der skal godkendes, før det slettes permanent

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Når opbevaringsperioden udløber, kan de brugere, du angiver ("validatorer"), få besked om at gennemse indholdet og godkende den permanente bortskaffelse. Dette understøtter, hvis en anden handling end sletning er mere relevant, f.eks. tildeling af en anden opbevaringsperiode til indholdet eller suspendering af sletning i forbindelse med en overvågning.

- Opret en opbevaringsmærkat, der bruger dispositionsgennemgang

### <a name="step-3-apply-labels-automatically-to-content-that-matches-specific-conditions"></a>Trin 3: Anvend automatisk mærkater på indhold, der opfylder bestemte betingelser

> [!TIP]
> Bedste praksis for prøveversion: Konfiguration inden for de første 30 dage

Automatisk anvendelse af mærkater fjerner behovet for, at brugerne manuelt udfører mærkataktiviteterne. Du kan automatisk anvende opbevaringsmærkater på indhold, når der ikke allerede er anvendt en opbevaringsmærkat for dette indhold, og det indeholder følsomme oplysninger, nøgleord eller søgbare egenskaber eller et match for klassificeringer, der kan oplæres.

- Anvend automatisk opbevaringsmærkater på indhold med bestemte typer følsomme oplysninger
- Anvend automatisk opbevaringsmærkater på indhold ved hjælp af klassificeringer, der kan oplæres
- Anvend automatisk opbevaringsmærkater med nøgleord eller søgbare egenskaber

## <a name="additional-trials-and-add-ons"></a>Yderligere prøveversioner og tilføjelsesprogrammer

### <a name="compliance-manager-premium-assessments"></a>Premiumvurderinger af Overholdelsesstyring

**Vurder risici, og reager effektivt**:

Hjælp din organisation med at vurdere risici og effektivt reagere på nationer, regionale krav og branchekrav til indsamling og brug af data.

[Du kan få flere oplysninger om prøveversionen af Premium Assessments for Overholdelsesstyring](compliance-easy-trials-compliance-manager-assessments.md).

[Playbook til prøveversion: Premium-vurderinger fra Microsoft Purview Compliance Manager](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Priva håndtering af privatlivsrisici og Microsoft Priva Anmodninger om den registreredes rettigheder

**Identificer & undgå risici for beskyttelse af personlige oplysninger**:

Identificer og beskyt proaktivt mod risici for beskyttelse af personlige oplysninger, f.eks. datasøgning, dataoverførsler og dataoverdragelser, og hjælp din organisation med at automatisere og administrere emneanmodninger i stor skala.

[Få mere at vide om Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[Playbook til prøveversion: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Yderligere ressourcer

**Inkluderet**: Du kan se en komplet liste over Microsoft Purview-løsninger og -funktioner, der er angivet efter produktniveau, ved at se [funktionsmatrixen](https://go.microsoft.com/fwlink/?linkid=2139145).

**Microsoft Security Technical Content Library**: Udforsk dette bibliotek for at finde interaktive vejledninger og andet læringsindhold, der er relevant for dine behov. [Besøg bibliotek](/security).

**Microsoft-sikkerhedsressourcer**: Fra antimalware til Nul tillid kan du hente alle relevante ressourcer til din organisations sikkerhedsbehov.
