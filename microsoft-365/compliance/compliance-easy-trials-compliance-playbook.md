---
title: Microsoft 365 prøveversion af løsninger til overholdelse af regler og standarder
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Microsoft 365 prøveversion af løsninger til overholdelse af regler og standarder.
ms.openlocfilehash: fc04e5d745997e31799511d4a9edb7e7207f4088
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63606783"
---
# <a name="trial-playbook-microsoft-365-compliance-solutions"></a>Prøvespilbog: Microsoft 365 løsninger til overholdelse af regler og standarder

Velkommen til lærebogen Microsoft 365 løsninger til overholdelse af regler og standarder. Denne strategiplan hjælper dig med at få mest muligt ud af din 90 dages gratis prøveversion ved at hjælpe dig med at opdage robuste og omfattende Microsoft 365 overholdelses- og sikkerhedsprodukter.

Hvis du af prøver hver enkelt løsning, kan det hjælpe dig med at træffe kvalificerede beslutninger, der opfylder din organisations behov for overholdelse.

Funktioner:

- [Avanceret overvågning](#advanced-audit)
- [Kommunikationsoverholdelse](#communication-compliance)
- [Overholdelsesstyring](#compliance-manager)
- [Forebyggelse af datatab](#data-loss-prevention)
- [eDiscovery](#ediscovery)
- [Beskyttelse af oplysninger](#information-protection)
- [Insider Risk Management](#insider-risk-management)
- [Datastyring](#records-management)

Valgfri tilføjelser:

- [Premium-bedømmelser i Compliance Manager](#compliance-manager-premium-assessments)
- [Microsoft Pr privacy Risk Management og Microsoft Pr hele anmodninger om emnerettigheder](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-365"></a>Overholdelseshandlinger med Microsoft 365

Du kan nemt og hurtigt begynde at prøve Microsofts løsninger til overholdelse af regler og standarder uden at ændre organisationens metadata. Afhængigt af dine prioriteter kan du starte med et af disse løsningsområder for at få vist den øjeblikkelige værdi. Nedenfor finder du fem af de vigtigste organisatoriske problemer, som vores kunder kommunikerer og anbefalede løsninger til at starte med.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="Overholdelseshandlinger med Microsoft 365":::

## <a name="advanced-audit"></a>Avanceret overvågning

**Foretage undersøgelser**

Avanceret overvågning hjælper organisationer med at foretage undersøgelser af omfang og overholdelse ved at øge opbevaringen af overvågningslogfiler, der kræves for at udføre en undersøgelse, hvilket giver adgang til vigtige begivenheder, der er med til at fastlægge omfanget af kompromiser, og som giver hurtigere adgang til Office 365 Management Activity API.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>Trin 1: [Anvend E5-licensen på hver enkelt bruger, som du vil generere E5-hændelser for](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Avancerede overvågningsfunktioner, såsom muligheden for at logføre vigtige hændelser som MailItemsAccessed og Send kræver en passende E5-licens, der er tildelt til brugere. Desuden skal avanceret overvågning af app/serviceplan være aktiveret for disse brugere.

Konfigurer Avanceret overvågning for brugere – for at bekræfte, at appen Avanceret overvågning er tildelt til brugere, skal [du udføre følgende trin for hver bruger](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

1. Aktivér Avancerede overvågningshændelser – [aktiver SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-advanced-audit-events), så de overvåges for hver bruger [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. Konfigurer overvågningspolitikker – opret yderligere [](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) opbevaringspolitikker til overvågningslogfiler, der opfylder kravene til organisationens sikkerhedshandlinger, it og overholdelsesteams.
1. Søg efter Avancerede overvågningshændelser – [søg efter vigtige Avancerede overvågningshændelser](set-up-advanced-audit.md#step-4-search-for-advanced-audit-events) og andre aktiviteter, når du udfører undersøgelser, der er ved at blive undersøgt.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>Trin 2: Opret nye politikker for overvågningslogfil for at angive, hvor lang tid overvågningslogfilerne skal bevares i organisationen til aktiviteter, der udføres af brugerne, og definere prioritetsniveauer [for dine politikker](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> Bedste praksis for prøveversion: Oprette inden for de første 30 dage

Opbevaringspolitikker for overvågningslogfiler er en del af de nye avancerede overvågningsfunktioner i Microsoft 365. Med en opbevaringspolitik for overvågningsloggen kan du angive, hvor lang tid overvågningslogfilerne skal bevares i organisationen.

1. Før du opretter en opbevaringspolitik for overvågningsloggen – er [vigtige ting at vide,](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) før du opretter din politik.
1. [Opret en opbevaringspolitik for overvågningslogfiler](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [Administrer opbevaringspolitikker for overvågningslogfiler i Microsoft 365 Overholdelsescenter](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center) – Opbevaringspolitikker for overvågningsloggen er angivet på fanen Politikker for opbevaring af overvågning (også kaldet dashboardet). Du kan bruge dashboardet til at få vist, redigere og slette opbevaringspolitikker for overvågning.
1. Opret og administrer opbevaringspolitikker for overvågningslogfiler på PowerShell – Du kan også bruge Security & Compliance Center PowerShell til at oprette og administrere opbevaringspolitikker [for overvågningslogfiler](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). En grund til at bruge PowerShell er at oprette en politik for en posttype eller aktivitet, der ikke er tilgængelig i brugergrænsefladen.

## <a name="communication-compliance"></a>Kommunikationsoverholdelse

**Identificer og act on code of conduct policy violations**

Kommunikationsoverholdelse hjælper dig med intelligent at identificere kommunikationsbrud for at understøtte et kompatibelt og sund arbejdsplads ved at hjælpe dig med at registrere upassende meddelelser, undersøge mulige overtrædelser af politikker og tage skridt til at løse.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>Trin 1: [Aktivér tilladelser for overholdelse af kommunikationsreglerne](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

[Tildel alle brugere til overholdelse af regler og standarder til rollegruppen Kommunikationsoverholdelse](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).
### <a name="step-2-enable-the-audit-log"></a>Trin 2: [Aktivér overvågningsloggen](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> Bedste fremgangsmåde for prøveversion: Konfiguration inden for de første 30 dage

Hvis du vil bruge denne funktion, skal du aktivere overvågning, så organisationen kan begynde at optage bruger- og administratoraktivitet i din organisation. Når du slår dette til, registreres aktivitet i overvågningsloggen og er tilgængelig for visning i en rapport. Du kan få mere at vide [under Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>Trin 3: Opret [en politik for overholdelse af kommunikation](communication-compliance-policies.md)

[Opret politik for overholdelse af kommunikation ved hjælp af de eksisterende skabeloner](communication-compliance-policies.md): 1- Upassende indhold; 2- Følsomme oplysninger; 3- Lovgivningsmæssig overholdelse; 4– I konflikt med hinanden.

### <a name="step-4-investigate-and-remediate-alerts"></a>Trin 4: [Undersøg og afhjulpet beskeder](communication-compliance-investigate-remediate.md)

[Undersøg og afhjulpet beskeder](communication-compliance-investigate-remediate.md) om kommunikationsoverholdelse.

## <a name="compliance-manager"></a>Overholdelsesstyring

**Administrer nemt organisationens overholdelse af regler og standarder**

Overholdelsesstyring kan hjælpe dig på hele din overholdelsesrejse fra beholdningen af dine databeskyttelsesrisici til administration af kompleksiteten ved implementering af kontroller, holde dig opdateret med bestemmelser og certificeringer og rapportering til revisorer.

### <a name="step-1-get-to-know-compliance-manager"></a>Trin 1: [Bliv bekendt med Overholdelsesstyring](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Vores oversigtsside til Overholdelsesstyring er det bedste første stop til en omfattende gennemgang af, hvad Overholdelsesstyring er, og hvordan den fungerer. Det kan også være en ide at springe direkte til de vigtigste afsnit i vores dokumentation ved hjælp af nedenstående links:

- [Forstå dit overholdelsesresultat](compliance-manager.md#understanding-your-compliance-score)
- [Oversigt over de vigtigste elementer: kontrolelementer, bedømmelser, skabeloner og forbedringshandlinger](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [Forstå dashboardet i Overholdelsesstyring](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [Filtrer din dashboardvisning](compliance-manager-setup.md#filtering-your-dashboard-view)
- [Få mere at vide om forbedringshandlinger](compliance-manager-setup.md#improvement-actions-page)
- [Forstå bedømmelser](compliance-manager.md#assessments)
- [Få en hurtig scanning af dit miljø ved hjælp af Microsoft Compliance Konfigurationsstyring](compliance-manager-mcca.md)

![Overholdelsesstyring – dashboard.](../media/compliance-manager-dashboard.png "Dashboard til Overholdelsesstyring")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>Trin 2: Konfigurer [Overholdelsesstyring til at administrere dine overholdelsesaktiviteter](compliance-manager-assessments.md)

> [!TIP]
> Bedste praksis for prøveversion: Undersøg inden for de første 30 dage

Begynd at arbejde med bedømmelser og foretage forbedringshandlinger for at implementere kontrolelementer og forbedre dit overholdelsesresultat.

1. [Vælg en færdigbyggede skabelon for at oprette og administrere din første vurdering](compliance-manager-assessments.md).
1. [Få mere at vide om, hvordan du bruger skabeloner til at opbygge vurderinger](compliance-manager-templates.md).
1. [Udfør implementerings- og testarbejde med forbedringshandlinger for at fuldføre kontrolelementer i dine bedømmelser](compliance-manager-improvement-actions.md).
1. [Få en bedre forståelse af, hvordan forskellige handlinger påvirker dit resultat af overholdelse](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365 eller Office 365 E1/E3-abonnement omfatter skabelonen Microsoft Data Protection Baseline. Microsoft 365 eller Office 365 E5 indeholder E5 Compliance skabeloner til:
>
> - Microsofts grundlinje for databeskyttelse
> - EU's GDPR  
> - ISO/IEC 27001,
> - NIST 800-53
>
> Overholdelsesstyring indeholder mere end 300 lovgivningsmæssige eller førsteklasses skabeloner, der kan købes som et tilføjelsesprogrammet. Se listen her. Med alle førsteklasses skabeloner (der følger med dit abonnement eller købt som tilføjelsesprogrammet) får du den universelle version af disse skabeloner, så du kan administrere din overholdelse af et produkt eller en tjeneste

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>Trin 3: [Opskalering: Brug avanceret funktionalitet, der opfylder dine brugerdefinerede behov](compliance-manager-templates-create.md)

Brugerdefinerede bedømmelser er nyttige i forbindelse med:

- Administrere overholdelse af regler og Microsoft 365, f.eks. tredjepartsapps og -tjenester, programmer i det lokale miljø og andre aktiver
- Administrere dine egne brugerdefinerede eller forretningsspecifikke kontrolelementer til overholdelse af regler og standarder

1. [Udvide en Overholdelsesstyring-skabelon ved at tilføje dine egne kontrolelementer og forbedringshandlinger](compliance-manager-templates-extend.md)
1. [Opret din egen brugerdefinerede skabelon](compliance-manager-templates-create.md)
1. [Rediger en eksisterende skabelon for at tilføje eller fjerne kontrolelementer og handlinger](compliance-manager-templates-modify.md)
1. [Konfigurere automatiserede test af forbedringshandlinger](compliance-manager-setup.md#set-up-automated-testing)
1. [Tildele forbedringshandlinger til en anden bruger](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-loss-prevention"></a>Forebyggelse af datatab

**Beskyt følsomme data**

For at overholde forretningsstandarder og branchebestemmelser skal organisationer beskytte følsomme oplysninger for at forhindre utilsigtet videregivelse. Konfigurer politikker til forebyggelse af datatab for at identificere, overvåge og automatisk beskytte følsomme oplysninger på tværs Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>Trin 1: [Beskyt datatab Teams placeringer](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Hvis din organisation har forebyggelse af datatab (DLP), kan du definere politikker, der forhindrer personer i at dele følsomme oplysninger i en Microsoft Teams-kanal eller chatsession.

1. Få mere [at vide om DLP-Microsoft Teams og omfanget af DLP-beskyttelse](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [Tilføj Microsoft Teams som en placering til eksisterende DLP-politikker](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [Konfigurer vores DLP-standardpolitik for Teams](mip-easy-trials.md) eller [Definer en ny DLP-politik for Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>Trin 2: [Beskyt datatab på enhedsplaceringer](endpoint-dlp-getting-started.md)

> [!TIP]
> Bedste fremgangsmåde for prøveversion: Konfiguration inden for de første 30 dage

Microsoft Endpoint DLP gør det muligt at overvåge Windows 10 enheder og registrere, når følsomme elementer bruges og deles.

1. Forbered dine slutpunkter – sørg for, at de Windows 10 og macOS-enheder, du planlægger at udrulle Endpoint DLP, [opfylder disse krav](endpoint-dlp-getting-started.md)
1. [Onboard enheder i enhedshåndtering](endpoint-dlp-getting-started.md)  – Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan overvåge og beskytte følsomme elementer på en enhed. Begge disse handlinger udføres i Microsoft 365 Overholdelse.
   - Scenarie 1 – [Onboardingenheder](endpoint-dlp-getting-started.md) , der endnu ikke er blevet onboardet.
   - Scenarie 2 – [Microsoft Defender til slutpunkt er allerede installeret, og der rapporteres slutpunkter i](endpoint-dlp-getting-started.md). Alle disse slutpunkter vises på listen over administrerede enheder.
1. [Konfigurer vores DLP-standardpolitik for enheder eller](mip-easy-trials.md#dlp-for-devices) [Definer en ny DLP-politik for enheder](endpoint-dlp-learn-about.md).
1. [Få vist slutpunkts-DLP-beskeder](dlp-configure-view-alerts-policies.md) i dashboardet til administration af DLP-beskeder.
1. [Vis Slutpunkt-DLP-data](data-classification-activity-explorer.md) i Aktivitetsoversigt.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>Trin 3: [Udvide politikker i omfang eller beskyttelse](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

Du har fleksibilitet i, hvordan du konfigurerer dine DLP-politikker. Du kan starte med vores DLP-standardpolitik for Teams enheder og udvide disse politikker for at beskytte yderligere placeringer, følsomme oplysningstyper eller navne. Desuden kan du udvide politikhandlingerne og tilpasse påmindelser.

1. Tilføj placeringer
1. Tilføj følsomme oplysningstyper eller navne, der skal beskyttes
1. Tilføj handlinger
   - Teams:
      - [Forhindre ekstern adgang til følsomme dokumenter](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [Få politiktip, der kan hjælpe med at informere brugere og vejledninger til tilpasning af politiktip](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - Enheder: Skift fra kun overvågning til blokering
1. [Konfigurer og få vist beskeder om politikker til forebyggelse af datatab – Microsoft 365 overholdelse | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eDiscovery

**Find mere med en fra ende til anden-arbejdsproces**

Udnyt en ende-til-ende-arbejdsproces til at bevare, indsamle, analysere og eksportere indhold, der reagerer på din organisations interne og eksterne undersøgelser. Juridiske teams kan også administrere hele processen med meddelelser om retsligt hold ved at kommunikere med personer, der er involveret i en sag.

### <a name="step-1-required-permissions"></a>Trin 1 (påkrævet): [Tilladelser](https://aka.ms/ediscoveryninja)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

For at Advanced eDiscovery adgang til en bruger eller blive tilføjet som medlem Advanced eDiscovery en sag, skal en bruger have tildelt de relevante tilladelser.

1. [Konfigurer Advanced eDiscovery – Tildel eDiscovery-tilladelser](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [Tilføj eller fjern medlemmer fra en sag](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>Trin 2 (påkrævet): Opret en sag

> [!TIP]
> Bedste praksis for prøveversion: Oprette inden for de første 30 dage

Flere organisationer bruger løsningen Advanced eDiscovery i Microsoft 365 til kritiske eDiscovery-processer. Dette omfatter besvarelse af lovgivningsmæssige anmodninger, undersøgelser og procesførelse.

1. Administrer Advanced eDiscovery – få mere at vide om, hvordan du konfigurerer Advanced eDiscovery, administrerer sager ved hjælp af [Security & Compliance Center, administrerer en arbejdsproces i Advanced eDiscovery og analyserer Advanced eDiscovery søgeresultaterne](/learn/modules/manage-advanced-ediscovery).
1. [Opret en eDiscovery-sag ved hjælp af Advance eDiscoverys nye sagsformat](advanced-ediscovery-new-case-format.md)
1. [Luk eller slet en sag](close-or-delete-case.md) – Når den juridiske sag eller undersøgelsen er færdig, kan du lukke eller slette. Du kan også genåbne en lukket sag.

### <a name="step-3-optional-settings"></a>Trin 3 (valgfrit): Indstillinger

Hvis du vil give personer i organisationen tilladelse til at oprette og bruge sager, skal du konfigurere globale indstillinger, der gælder for alle sager i organisationen. På nuværende tidspunkt er den eneste globale indstilling **registrering af advokat-klient-rettigheder** (flere globale indstillinger vil være tilgængelige i fremtiden).

1. [Konfigurer Advanced eDiscovery – global Indstillinger](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-advanced-ediscovery)
1. [Konfigurere indstillinger for søgning og analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [Administrer job i Advanced eDiscovery](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>Trin 4 (valgfrit): [Overensstemmelsesgrænser](set-up-compliance-boundaries.md)

Overensstemmelsesgrænser opretter logiske grænser i en organisation, der styrer brugerens indholdsplaceringer (f.eks. postkasser, OneDrive-konti og SharePoint-websteder), som eDiscovery-ledere kan søge i. De styrer også, hvem der kan få adgang til eDiscovery-sager, der bruges til at administrere juridiske ressourcer, HR-ressourcer eller andre undersøgelser i din organisation.

![Overholdelsesgrænser består af søgetilladelsesfiltre, der styrer adgangen til myndigheder og administratorrollegrupper, der styrer adgangen til eDiscovery-sager.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser:

1. [Identificer en brugerattribut for at definere dine myndigheder](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [Opret en rollegruppe for hvert agentur](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [Oprette et filter for søgetilladelser for at håndhæve overholdelsesrammen](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [Opret en eDiscovery-sag til undersøgelser af en intra-agency](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>Trin 5 (valgfrit): Få [mere at vide om værktøjet Indholdssøgning](search-for-content.md)

Brug værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter til hurtigt at finde mails i Exchange-postkasser, dokumenter på SharePoint-websteder og OneDrive-placeringer og chatsamtaler i Skype for Business. Du kan bruge værktøjet til indholdssøgning til at søge efter mails, dokumenter og chatsamtaler i samarbejdsværktøjer som f.eks Microsoft Teams og Microsoft 365 Grupper.

- [Få mere at vide Advanced eDiscovery søgning](search-for-content.md#search-for-content)

## <a name="information-protection"></a>Beskyttelse af oplysninger

**Opdag, klassificer og beskyt dine følsomme oplysninger**

Implementer Microsoft Information Protection og følsomhedsetiketter for at hjælpe dig med at opdage, klassificere og beskytte dit følsomme indhold, uanset hvor du befinder dig eller rejser.

### <a name="step-1-start-your-information-protection-trial"></a>Trin 1: [Start din prøveversion af beskyttelse af oplysninger](mip-easy-trials.md)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Berettigede kunder kan aktivere standardnavne og -politikker for Microsoft Information Protection. Når du aktiverer standardkonfigurationen i prøveperioden, tager det ca. 2 minutter at konfigurere alle politikker for din lejer og op til 24 timer for at se resultaterne af disse standardpolitikker.

Når du vælger standardkonfigurationen med et enkelt klik, konfigureres følgende automatisk:

- Følsomhedsmærkater og en følsomhedsmærkatpolitik
- Automatisk mærkning på klientsiden
- Automatisk mærkning på tjenestesiden
- Politikker til forebyggelse af datatab (DLP) for Teams enheder

[Aktivere standardnavnene og -politikkerne](mip-easy-trials.md#activate-the-default-labels-and-policies). Hvis det er nødvendigt, kan du redigere manuelt, når konfigurationen er fuldført.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>Trin 2: [Anvend automatisk følsomhedsmærkater på dokumenter](apply-sensitivity-label-automatically.md)

> [!TIP]
> Bedste fremgangsmåde for prøveversion: Konfiguration inden for de første 30 dage

Når du opretter en følsomhedsmærkat, kan du automatisk tildele den pågældende etiket til filer og mails, når den opfylder de betingelser, du angiver.

1. [Opret og konfigurer følsomhedsmærkater](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [Publicer følsomhedsmærkatpolitik til alle brugere](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [Opret en politik for automatisk mærkater](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - Vælg de oplysninger, som etiketten skal anvendes på
   - Definer placeringer, der skal anvendes på etiketter
   - Vælg den etiket, der skal anvendes
   - [Kør politik i simuleringstilstand](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![Ny politikkonfiguration til automatisk mærkatering.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>Trin 3: [Gennemse og slå automatisk mærkningspolitik til](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

Nu kan du **på siden** **Information protectionAuto-labeling** >  se din automatiske etiketpolitik i afsnittet **Simulering**.

Vælg din politik for at få vist oplysninger om konfiguration og status. Når simulering er fuldført, skal du vælge fanen Elementer, der skal gennemses for at se, hvilke mails eller dokumenter, der matcher de regler, der er angivet.

Når du er klar til at køre politikken uden simulering, skal du **vælge indstillingen Aktiver** politik.

## <a name="insider-risk-management"></a>Insider Risk Management

**Registrer og afhjulpet insider-risici**

Udnyt kunstig intelligens til at hjælpe dig med hurtigt at identificere, triage og afhjælpe interne risici. Ved hjælp af logfiler fra Microsoft 365 og Azure-tjenester kan du definere politikker, der overvåger for Insider-risikosignaler, og derefter foretage afhjælpningshandlinger som f.eks. at promovere brugerundervisning eller starte en undersøgelse.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Trin 1 (påkrævet): [Aktivér tilladelser for Insider Risk Management](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Der bruges fire rollegrupper til at konfigurere tilladelser til at administrere insider-funktioner til risikostyring.

[Føj brugere til en rollegruppe for insider-risikostyring.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

Hvis du ikke kan se tilladelser, skal du kontakte din lejeradministrator for at tildele de korrekte roller.

### <a name="step-2-start-with-user-quick-start-guide"></a>Trin 2: [Start med startvejledningen for brugeren](insider-risk-management-configure.md#recommended-actions-preview)

Kom hurtigt i gang, og få mest muligt ud af insider-funktioner til risikostyring med anbefalede handlinger. På siden Oversigt finder du anbefalede handlinger, der hjælper dig med at konfigurere og implementere politikker og udføre undersøgelseshandlinger for brugerhandlinger, der genererer beskeder ud fra politik matches.

[Vælg en anbefaling på listen for at](insider-risk-management-configure.md#recommended-actions-preview) komme i gang med at konfigurere Insider Risk Management.

![Anbefalede handlinger for Insider-risikostyring.](../media/insider-risk-recommended-actions.png)

Hver anbefalede handling fører dig gennem de påkrævede aktiviteter til anbefalingen, herunder eventuelle krav, hvad du kan forvente, og effekten af at konfigurere funktionen i organisationen.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>Trin 3 (påkrævet): [Aktivér Microsoft 365 overvågningsloggen](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

Overvågning er aktiveret for Microsoft 365 organisationer som standard. Nogle organisationer har deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for organisationen, kan det skyldes, at en anden administrator har slået det fra. Vi anbefaler, at du bekræfter, at det er OK at slå overvågning til igen, når du udfører dette trin.

Du kan finde en trinvis vejledning i at aktivere overvågning i Slå søgning [i overvågningslogfil til eller fra](turn-audit-log-search-on-or-off.md). Når du har aktiveret overvågning, vises der en meddelelse om, at overvågningsloggen forberedes, og at du kan køre en søgning om et par timer, efter at klargøringen er fuldført. Du behøver kun at udføre denne handling én gang. Du kan finde flere oplysninger om Microsoft 365 i Søge [i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>Trin 4 (påkrævet): [Aktivér og få vist indsigt i Insider Risk Analytics](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

Insider-analyse af risikostyring gør det muligt at udføre en evaluering af potentielle insider-risici i din organisation uden at konfigurere insider-risikopolitikker. Analysescanningsresultater kan tage op til 48 timer, før indsigter er tilgængelige som rapporter til gennemsyn. Hvis du vil have mere at vide om analyseindsigt, skal du se Indstillingerne for [Insider-risikostyring: Analyse (forhåndsvisning),](insider-risk-management-settings.md) og se videoen [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) , der kan hjælpe dig med at forstå din insider-risikoindsigt og hjælpe dig med at handle ved at konfigurere relevante politikker til at identificere risikabelt brugere.

For at aktivere Insider Risk Analytics skal du være medlem af Insider Risk Management eller Insider Risk Management-administrator. Fuldfør disse trin for at [aktivere Insider-risikoanalyse](insider-risk-management-configure.md).

## <a name="records-management"></a>Datastyring

**Automatiser opbevaringsplanen for forretningskritiske poster**

Brug integrerede datastyringsfunktioner til at automatisere opbevaringsplanen for organisatoriske lovmæssige, juridiske og forretningsmæssige poster. Få komplet support til indholdslivscyklussen fra oprettelse til samarbejde, registreringserklæring, opbevaring og disposition.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>Trin 1: Målret opbevaringspolitikker dynamisk med tilpassede politikomfang

> [!TIP]
> Bedste praksis for prøveversion: Dag 1

Tilpassede politikområder giver dig mulighed for dynamisk at målrette en politik til bestemte brugere, grupper eller websteder baseret på deres AD-attributter.

Attributter for områder kan vælges fra en liste eller tilpasses ved hjælp af en avanceret forespørgselsgenerator.

Politikker, der anvender tilpassede politikomfang, forbliver aktuelle, efterhånden som organisationen ændrer sig, når nye medarbejdere melder sig til eller forlader virksomheden. Desuden er de ikke underlagt de tidligere begrænsninger på 100/1.000 placeringer, der er inkluderet i en politik.

- Opret et [tilpasset politikområde](retention.md#adaptive-or-static-policy-scopes-for-retention), og brug det med en opbevaringspolitik

### <a name="step-2-automate-labeling-of-sensitive-information-with-the-ability-to-review-before-disposal"></a>Trin 2: Automatiser mærkaten for følsomme oplysninger med muligheden for at gennemse før afhændelse

> [!TIP]
> Bedste fremgangsmåde for prøveversion: Konfiguration inden for de første 30 dage

Opbevaringsetiketter kan konfigureres, så de automatisk anvendes på indhold, når der registreres følsomme oplysninger, f.eks. et kreditkortnummer. Dette fjerner behovet for, at brugerne manuelt udfører etiketaktiviteten.

Ved opbevaringsperiodens afslutning får de brugere, du angiver ("korrekturlæsere"), besked om at gennemgå indholdet og godkende handlingen for permanent afhændelse. Det kan det være, hvis noget skal bevares i længere tid.

Både etiketprogramaktivitet og dispositionsgennemsyn kan ses på skærmen Oversigt over datastyring.

1. [Anvend automatisk opbevaringsnavne på indhold, der indeholder følsomme oplysninger](retention.md#retention-labels)
1. Opret og anvend et opbevaringsmærkat med [dispositionsgennemsyn](disposition.md#disposition-reviews) i slutningen af en opbevaringsperiode

### <a name="step-3-label-content-as-records-automatically-using-trainable-classifiers"></a>Trin 3: Mærkater indhold som poster automatisk ved hjælp af klassificeringer, der kan trænes

Når indhold erklæres som en post, sættes begrænsninger på elementet med hensyn til, hvilke handlinger der tillades eller blokeres, yderligere aktiviteter om elementerne logføres, og du har bevis for, at dispositionen er disposition, hvis elementerne slettes i slutningen af deres opbevaringsperiode.

Trænbare klassificeringer er værktøjer, der genkender forskellige typer indhold, baseret på eksempler, det har fået. Vælg mellem en række indbyggede indstillinger, eller konfigurer en brugerdefineret klassificering, der opfylder dine specifikke behov.

1. Oprette en opbevaringsetiket [, der erklærer indhold som en post eller en lovgivningspost](records-management.md#records)
1. [Anvend automatisk opbevaringsmærkater på indhold med klassificeringer, der kan trænes](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

### <a name="more-information-auto-apply-retention-labels--disposition-review"></a>Flere oplysninger: Anvend automatisk opbevaringsmærkater + gennemgang af disposition

**Anvend navne automatisk for at bevare det, du skal bruge...**
Opbevaringsnavne kan automatisk anvendes på indhold, når det indeholder:

- [Bestemte typer af følsomme oplysninger](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
- [Specifikke nøgleord eller søgbare egenskaber, der svarer til en forespørgsel, du opretter](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Et match til klassekammerater, der kan trænes](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

**... og derefter skaffe dig af med det sikkert i slutningen.**

Når en gennemgang af disposition udløses i slutningen af opbevaringsperioden, modtager de korrekturlæsere, du vælger, en mail om, at de har indhold, der skal gennemgås.

Indhold, der venter på en gennemgang af dispositionen, slettes først permanent, når en korrekturlæser for den sidste fase af dispositionen vælger at slette indholdet permanent.

## <a name="additional-trials-and-add-ons"></a>Yderligere forsøg og tilføjelser

### <a name="compliance-manager-premium-assessments"></a>Premium-bedømmelser i Compliance Manager

**Vurder risici, og res responder effektivt**

Hjælp din organisation med at vurdere risici og reagere effektivt på lande, regionale krav og branchekrav, der styrer indsamling og brug af data.

[Flere oplysninger om prøveversionen af Compliance Manager Premium-vurderinger](compliance-easy-trials-compliance-manager-assessments.md).

[Prøvespilbog: Microsoft Compliance Manager Premium-bedømmelser](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Pr privacy Risk Management og Microsoft Pr hele anmodninger om emnerettigheder

**Identificer & undgå risici i forbindelse med beskyttelse af personlige oplysninger**

Proaktivt identificere og beskytte mod risici i forbindelse med beskyttelse af personlige oplysninger som f.eks. data hoardering, dataoverførsler og datadeling og hjælpe din organisation med at automatisere og administrere emneanmodninger i stor skala.

[Få mere at vide om Microsoft Pr hele webstedet](/privacy/solutions/privacymanagement/privacy-management).

[Prøvespilbog: Microsoft Prbook](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>Yderligere ressourcer

**Hvad er inkluderet**: Du kan se en komplet liste over Microsoft 365 over overholdelsesløsninger og funktioner, der er angivet efter produktniveau, i [Funktionsmatrix](https://go.microsoft.com/fwlink/?linkid=2139145).

**Microsoft Security Technical Content Library: Udforsk** dette bibliotek for at finde interaktive vejledninger og andet læringsindhold, der er relevant for dine behov. [Besøg Bibliotek](/security/content-library).

**Microsoft-sikkerhedsressourcer**: Fra antimalware til Zero Trust får du alle de relevante ressourcer til organisationens sikkerhedsbehov. [Besøg Ressourcer](/security/business/resources).
