---
title: Microsoft Purview løsninger til risiko og overholdelse af angivne standarder
description: Brug denne artikel til at få mere at vide om Microsoft Purview løsninger til risiko og overholdelse af angivne standarder.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, løsninger
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: m365-security-compliance
ms.openlocfilehash: c56c855983e27a3882796cd1e222c97305a627c4
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101546"
---
# <a name="microsoft-purview-risk-and-compliance-solutions"></a>Microsoft Purview løsninger til risiko og overholdelse af angivne standarder

Microsoft Purview løsninger til risiko og overholdelse af angivne standarder hjælper dig med at administrere og overvåge dine data, beskytte oplysninger, minimere risici for overholdelse af angivne standarder og opfylde lovmæssige krav. Denne artikel hjælper dig med at få mere at vide om Microsoft Purview risiko- og overholdelsesløsninger og hurtigt komme i gang med at udrulle disse løsninger for at imødekomme specifikke behov for overholdelse af angivne standarder for din organisation.

## <a name="protect-sensitive-data-across-clouds-apps-and-devices"></a>Beskyt følsomme data på tværs af clouds, apps og enheder

Din strategi til beskyttelse af oplysninger skal være baseret på dine forretningsbehov, men alle organisationer har et krav om at beskytte nogle eller alle dens data. Brug funktionerne fra [Microsoft Purview Information Protection](/microsoft-365/compliance/information-protection) (tidligere Microsoft Information Protection) til at hjælpe dig med at finde, klassificere, beskytte og styre følsomme oplysninger, uanset hvor de bor eller rejser.

### <a name="know-your-data"></a>Kend dine data

Du har oplysninger, der findes på tværs af alle Microsoft 365 tjenester og i det lokale miljø. Det er centralt at identificere, hvilke elementer der er følsomme, og få indsigt i, hvordan de bruges, i din praksis for beskyttelse af oplysninger. Microsoft Purview omfatter:

- [Følsomme oplysningstyper](/microsoft-365/compliance/sensitive-information-type-learn-about) til at identificere følsomme elementer ved hjælp af indbyggede eller brugerdefinerede regulære udtryk eller en funktion.
- [Klassificeringer, der kan oplæres](/microsoft-365/compliance/classifier-learn-about) til at identificere følsomme elementer ved hjælp af eksempler på de data, du er interesseret i, i stedet for at identificere elementer i elementet.
- [Dataklassificering](/microsoft-365/compliance/data-classification-overview) giver en grafisk identifikation af elementer i din organisation, der har en følsomhedsmærkat, en opbevaringsmærkat eller er blevet klassificeret, og de handlinger, dine brugere foretager på dem

### <a name="protect-your-data"></a>Beskyt dine data

Der er mange funktioner, som du kan bruge fra Microsoft Purview Information Protection-løsningen til at beskytte dine data, uanset hvor de er gemt, og hvordan de tilgås. Følsomhedsmærkater er dog den grundlæggende funktion, der både leverer beskyttelseshandlinger og interagerer med andre Purview-løsninger og -egenskaber.

Følsomhedsmærkater giver brugere og administratorer indblik i følsomheden af de data, de bruger, og mærkaterne kan selv anvende beskyttelseshandlinger, der omfatter kryptering, adgangsbegrænsninger og visuelle markeringer. Du kan finde flere oplysninger om udvalget af understøttede navngivningsscenarier i afsnittet [Almindelige scenarier for følsomhedsmærkater](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels) i dokumentationen til introduktion. Du kan finde flere oplysninger om følsomhedsmærkater under [Få mere at vide om følsomhedsmærkater](/microsoft-365/compliance/sensitivity-labels).

### <a name="prevent-data-loss"></a>Undgå datatab

Utilsigtet deling af følsomme elementer kan forårsage økonomisk skade på din organisation og kan resultere i overtrædelse af love og bestemmelser. [Microsoft Purview Forebyggelse af datatab](/microsoft-365/compliance/dlp-learn-about-dlp) kan hjælpe med at beskytte din organisation mod utilsigtet eller utilsigtet deling af følsomme oplysninger både i og uden for din organisation. I en politik til forebyggelse af datatab:

- Definer de følsomme oplysninger, du vil overvåge for, f.eks. økonomiske, helbredsmæssige, medicinske og personlige oplysninger.
- Hvor du kan overvåge, f.eks. Microsoft 365 tjenester eller Windows og macOS enheder.
- De betingelser, der skal matches, for at en politik kan anvendes på et element, f.eks. elementer, der indeholder kreditkort, kørekort eller cpr-numre.
- De handlinger, der skal udføres, når der findes et match, f.eks. overvågning, blokerer aktiviteten og blokerer aktiviteten med tilsidesættelse.

### <a name="manage-your-data-lifecycle"></a>Administrer din datalivscyklus

[Administration af Microsoft Purview-datalivscyklus](/microsoft-365/compliance/manage-data-governance#microsoft-purview-data-lifecycle-management) (tidligere Microsoft Information Governance) giver dig værktøjer og funktioner til at bevare og slette indhold på tværs af Exchange, SharePoint, OneDrive, Microsoft 365-grupper, Teams og Yammer. Opbevaring og sletning af mails, dokumenter og meddelelser er ofte nødvendige for overholdelse af angivne standarder og lovmæssige krav. Men hvis du sletter indhold, der ikke længere har forretningsværdi, reduceres angrebsoverfladen også.

Du kan finde flere oplysninger under [Få mere at vide om administration af datalivscyklus](/microsoft-365/compliance/data-lifecycle-management).

### <a name="encrypt-your-data-and-control-your-encryption-keys"></a>Kryptér dine data, og styr dine krypteringsnøgler

[Kryptering](/microsoft-365/compliance/encryption) er en vigtig del af din strategi til beskyttelse af filer og beskyttelse af oplysninger. Krypteringsprocessen koder dine data (kaldet almindelig tekst) til kryptering. I modsætning til almindelig tekst kan kryptering ikke bruges af personer eller computere, medmindre og før krypteringen af krypteringen. Dekryptering kræver en krypteringsnøgle, som kun godkendte brugere har. Kryptering hjælper med at sikre, at kun godkendte modtagere kan dekryptere dit indhold.

[Microsoft Purview kryptering med dobbelt nøgle](/microsoft-365/compliance/double-key-encryption) hjælper med at sikre de mest følsomme data, der er underlagt de strengeste beskyttelseskrav. [Microsoft Purview Kundenøgle](/microsoft-365/compliance/customer-key-overview) hjælper dig med at overholde lovmæssige eller overholdelsesforpligtelser til styring af rodnøgler. Du giver udtrykkeligt Microsoft 365 tjenester tilladelse til at bruge dine krypteringsnøgler til at levere ekstra cloudtjenester, f.eks. eDiscovery, antimalware, anti-spam, søgeindeksering osv.

## <a name="identify-data-risks-and-manage-regulatory-compliance-requirements"></a>Identificer datarisici, og administrer lovmæssige krav til overholdelse af angivne standarder

Insiderrisici er en af de største bekymringer for sikkerheds- og overholdelseseksperter på den moderne arbejdsplads. Brancheundersøgelser har vist, at insiderrisici ofte er forbundet med specifikke brugerhændelser eller -aktiviteter. Det kan være en udfordring at beskytte din organisation mod disse risici for at identificere og afhjælpe dem. Insiderrisici omfatter sårbarheder på forskellige områder og kan forårsage store problemer for din organisation lige fra tab af intellektuel ejendom til chikane på arbejdspladsen og meget mere.

Microsoft Purview tilbyder følgende løsninger til overholdelse af angivne standarder, der kan hjælpe din organisation med at administrere datarisiko- og overholdelseskrav:

- [Styring af insider-risiko](#detect-and-act-on-risk-activities-with-insider-risk-management)
- [Kommunikationsoverholdelse](#detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance)
- [Informationsbarrierer](#restrict-communication-and-collaboration-between-users-with-information-barriers)
- [Datastyring](#manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management)
- [Overvågning (Premium) og overvågning (standard)](#log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard)
- [eDiscovery (Premium) og eDiscovery (Standard)](#identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard)

### <a name="detect-and-act-on-risk-activities-with-insider-risk-management"></a>Registrer og handle på risikoaktiviteter med styring af insiderrisiko

[Microsoft Purview Styring af insider-risiko](/microsoft-365/compliance/insider-risk-management) bruger den fulde bredde af tjenesten og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikable brugeraktiviteter i din organisation. Ved hjælp af logge fra Microsoft 365 og Microsoft Graph giver insiderrisikostyring dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer. Når du har identificeret risikable aktiviteter, kan du afhjælpe disse risici.

### <a name="detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance"></a>Registrer og håndtér upassende og følsomme meddelelser med overholdelse af kommunikation

Beskyttelse af følsomme oplysninger og registrering og behandling af chikanehændelser på arbejdspladsen er en vigtig del af overholdelsen af interne politikker og standarder. [Microsoft Purview Kommunikationsoverholdelse](/microsoft-365/compliance/communication-compliance-policies) hjælper med at minimere disse risici ved hurtigt at registrere, registrere og håndtere afhjælpningshandlinger i forbindelse med mail og Microsoft Teams kommunikation. Disse omfatter upassende kommunikation, der indeholder bandeord, trusler og chikane og kommunikation, der deler følsomme oplysninger i og uden for din organisation.

### <a name="restrict-communication-and-collaboration-between-users-with-information-barriers"></a>Begræns kommunikation og samarbejde mellem brugere med informationsbarrierer

[Microsoft Purview informationsbarrierer (IB)](/microsoft-365/compliance/information-barriers) er en overholdelsesløsning, der giver dig mulighed for at begrænse tovejskommunikation og samarbejde mellem grupper og brugere i Microsoft Teams, SharePoint Online og OneDrive for Business. IB bruges ofte i stærkt regulerede brancher og kan hjælpe med at undgå interessekonflikter og beskytte interne oplysninger mellem brugere og organisatoriske områder.

### <a name="manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management"></a>Administrer forretnings-, juridiske eller lovmæssige krav til registrering med datastyring

[Microsoft Purview-datastyring](/microsoft-365/compliance/manage-data-governance#microsoft-purview-records-management) hjælper en organisation med at administrere sine juridiske forpligtelser, giver mulighed for at demonstrere overholdelse af regler og øger effektiviteten med regelmæssig fordeling af elementer, der ikke længere skal bevares, ikke længere er af værdi eller ikke længere kræves til forretningsmæssige formål. Du kan finde flere oplysninger under [Få mere at vide om datastyring](/microsoft-365/compliance/records-management).

### <a name="log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard"></a>Logfør og søg efter overvågede aktiviteter i SharePoint og OneDrive med Overvågning (Premium) eller Overvågning (Standard)

[Microsoft Purview overvågningsløsninger](/microsoft-365/compliance/auditing-solutions-overview) leverer integrerede løsninger, der kan hjælpe organisationer med effektivt at reagere på sikkerhedshændelser, retsmedicinske undersøgelser, interne undersøgelser og overholdelse af angivne standarder. Tusindvis af bruger- og administratorhandlinger, der udføres i mange Microsoft 365 tjenester og løsninger, registreres, registreres og bevares i din organisations samlede overvågningslog. Der kan søges i overvågningsposter for disse hændelser af sikkerhedsadministratorer, it-administratorer, insiderrisikoteams og overholdelses- og juridiske efterforskere i din organisation. Denne funktion giver indblik i de aktiviteter, der udføres på tværs af din Microsoft 365 organisation.

Du kan finde flere oplysninger om overvågningsløsninger under [Overvågning (Premium)](/microsoft-365/compliance/advanced-audit) og [Overvågning (Standard).](/microsoft-365/compliance/set-up-basic-audit)

### <a name="identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard"></a>Identificer og administrer data for juridiske sager med eDiscovery (Premium) eller eDiscovery (Standard)

Elektronisk registrering eller eDiscovery er processen med at identificere, indsamle og overvåge elektroniske oplysninger af juridiske, lovmæssige eller forretningsmæssige årsager. Du kan bruge [Microsoft Purview eDiscovery løsninger](/microsoft-365/compliance/ediscovery) til at søge efter data og indhold i Exchange Online, OneDrive for Business, SharePoint Online, Microsoft Teams, Microsoft 365-grupper og Yammer teams. Du kan søge i postkasser og websteder i den samme eDiscovery-søgning og derefter eksportere søgeresultaterne til analyse og gennemsyn.

Du kan finde flere oplysninger om eDiscovery-løsninger under [eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20) og [eDiscovery (Standard)](/microsoft-365/compliance/get-started-core-ediscovery).

## <a name="get-started-with-regulatory-compliance"></a>Kom i gang med overholdelse af lovmæssige standarder

Organisationer skal overholde et komplekst web, der udvikler sig, af politikker, branchestandarder og regionale bestemmelser og også håndtere de stigende omkostninger ved potentiel manglende overholdelse. Faktisk er der hundredvis af opdateringer om dagen fra tusindvis af regulerende organer, hvilket gør det udfordrende at holde sig ajour med det hurtigt skiftende overholdelseslandskab. Microsoft Purview Overholdelsesstyring og en detaljeret samling af tilbud på overholdelse af angivne standarder kan hjælpe din organisation med at administrere disse lovmæssige krav.

### <a name="get-started-with-compliance-manager"></a>Kom i gang med Overholdelsesstyring

[Microsoft Purview Overholdelsesstyring](/microsoft-365/compliance/compliance-manager) er en funktion i Microsoft Purview-compliance-portal, der hjælper dig med at administrere organisationens overholdelseskrav med større brugervenlighed. Overholdelsesstyring kan hjælpe dig gennem hele overholdelsesrejsen, lige fra opgørelse af dine databeskyttelsesrisici til administration af kompleksiteten ved implementering af kontroller, overholdelse af regler og certificeringer og rapportering til auditører.

### <a name="learn-about-microsoft-regulatory-compliance-offerings"></a>Få mere at vide om tilbud om Microsoft overholdelse af angivne standarder

Microsoft tilbyder et omfattende sæt [af tilbud om overholdelse af angivne standarder](/compliance/regulatory/offering-home) , der hjælper din organisation med at overholde nationale, regionale, internationale og branchespecifikke krav til indsamling og brug af data.

## <a name="deploy-purview-compliance-solutions"></a>Udrul Purview-løsninger overholdelse af angivne standarder

Områdespecifikke løsninger samler den tekniske vejledning, du har brug for til at forstå, planlægge og implementere integrerede løsninger til overholdelse af angivne standarder for sikker og kompatibelt datasamarbejde:

- [Beskyt data med Nul tillid](/security/zero-trust/deploy/data)
- [Udrul en løsning til beskyttelse af oplysninger](/microsoft-365/compliance/information-protection-solution)
- [Udrul en datastyringsløsning](/microsoft-365/compliance/data-governance-solution)
- [Udrul beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger](/microsoft-365/solutions/information-protection-deploy)
- [Udforsk illustrationer af beskyttelse af oplysninger & overholdelse af angivne standarder](/microsoft-365/solutions/productivity-illustrations)

## <a name="next-steps-for-organizations-new-to-risk-and-compliance-solutions"></a>Næste trin for organisationer, der er nye inden for risiko- og overholdelsesløsninger

- [Få mere at vide om prøveversionen af Microsoft Purview-løsningen](/microsoft-365/compliance/compliance-easy-trials)
- [Hurtige opgaver for at komme i gang med overholdelse af angivne standarder i Microsoft Purview](/microsoft-365/compliance/compliance-quick-tasks)
