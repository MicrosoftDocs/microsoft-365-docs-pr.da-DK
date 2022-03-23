---
title: Hurtige opgaver til at komme i gang med Microsoft 365 overholdelse af regler og standarder
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
description: Få mere at vide om opgaver, der hjælper dig med hurtigt at komme i gang med overholdelse Microsoft 365.
ms.openlocfilehash: 1fb1a94e41550e10288bc42b3900cb10e76362bc
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63590279"
---
# <a name="quick-tasks-for-getting-started-with-microsoft-365-compliance"></a>Hurtige opgaver til at komme i gang med Microsoft 365 overholdelse af regler og standarder

Hvis du er ny bruger af overholdelse Microsoft 365 og spekulerer over, hvor du skal starte, giver denne artikel vejledning i det grundlæggende og prioriterer vigtige overholdelsesopgaver. Denne artikel hjælper dig med hurtigt at komme i gang med at administrere og overvåge dine data, beskytte oplysninger og minimere insider-risici.

Denne artikel er også nyttig, hvis du finder ud af, hvordan du bedst administrerer risici, beskytter dine data og forbliver i overensstemmelse med bestemmelser og standarder med en nylig ekstern arbejdsstyrke. Medarbejdere samarbejder nu og opretter forbindelse til hinanden på nye måder, og det betyder, at dine eksisterende overholdelsesprocesser og kontroller kan være nødt til at tilpasse sig. At identificere og administrere disse nye risici i forbindelse med overholdelse i din organisation er afgørende for at indsamle dine data og minimere trusler og risici.

Når du har gennemført disse grundlæggende overholdelsesopgaver, kan du overveje at udvide dækningen af overholdelse i organisationen ved at implementere Microsoft 365 løsninger til overholdelse af regler og standarder.

## <a name="task-1-configure-compliance-permissions"></a>Opgave 1: Konfigurere tilladelser til overholdelse af regler og standarder

Det er vigtigt at administrere, hvem i organisationen der har adgang til organisationens Microsoft 365 Overholdelsescenter at få vist indhold og udføre administrationsopgaver. Microsoft 365 giver administrative roller, der er specifikke for overholdelse af regler og standarder og for brugen af de værktøjer, der er inkluderet i Microsoft 365 Overholdelsescenter.

Start med at tildele overholdelsestilladelser til personer i organisationen, så de kan udføre disse opgaver, og for at forhindre uautoriserede personer i at få adgang til områder uden for deres ansvarsområder. Du skal sikre dig, at du har tildelt de rette personer til administratorrollerne overholdelsesdata og overholdelsesadministrator, før du begynder at konfigurere og implementere overholdelsesløsninger, der følger med Microsoft 365. Du skal også tildele brugere rollen som global Azure Active Directory til at få vist data i Overholdelsesstyring.

Du kan finde en trinvis vejledning til konfiguration af tilladelser og tildeling af personer til administratorroller under Tilladelser i [Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="task-2-know-your-state-of-compliance"></a>Opgave 2: Kende tilstanden for overholdelse af regler og standarder

Det er svært at vide, hvor du skal hen, hvis du ikke ved, hvor du er. For at opfylde dine behov for overholdelse af regler og standarder kan du også forstå dit aktuelle risikoniveau, samt hvilke opdateringer der kan være behov for i disse skiftende tidspunkter. Uanset om din organisation er ny i forhold til overholdelseskrav eller har stor erfaring med standarder og bestemmelser, der styrer din branche, er det bedste, du kan gøre for at forbedre overholdelse af regler og standarder, at forstå, hvor din organisation står.

[Microsoft Compliance Manager kan](compliance-manager.md) hjælpe dig med at forstå din organisations overholdelsesholdning og fremhæve områder, der kan have brug for forbedring. Overholdelsesstyring anvender et centraliseret dashboard til at beregne et risikobaseret resultat, måle dit fremskridt i forbindelse med fuldførelse af handlinger, som er med til at reducere risici i forhold til databeskyttelse og lovmæssige standarder. Du kan også bruge Overholdelsesstyring som et værktøj til sporing af alle dine risikovurderinger. Den indeholder arbejdsprocesfunktioner, der kan hjælpe dig med effektivt at udføre dine risikovurderingr via et fælles værktøj.

Du kan finde en trinvis vejledning til at komme i gang med Overholdelsesstyring i [Introduktion til Overholdelsesstyring](compliance-manager-setup.md).

> [!IMPORTANT]
> Sikkerhed og overholdelse er tæt integreret for de fleste organisationer. Det er vigtigt, at din organisation tager sig af de grundlæggende sikkerheds-, trusselsbeskyttelses- og identitets- og adgangsstyringsområder for at skabe en indgående forsvar tilgang til både sikkerhed og overholdelse.
>
> Se din [Microsoft 365 Secure Score](../security/defender/microsoft-secure-score.md) på Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portal</a> og fuldføre de opgaver, der er beskrevet i følgende artikler:
>
> - [Sikkerhedsoversigt – Topprioriteter for de første 30 dage, 90 dage og derefter](../security/office-365-security/security-roadmap.md)
> - [De 12 vigtigste opgaver for sikkerhedsteams til at understøtte hjemmearbejde](../security/top-security-tasks-for-remote-work.md)

## <a name="task-3-enable-auditing-for-your-organization"></a>Opgave 3: Aktivér overvågning for organisationen

Nu hvor du har bestemt din organisations aktuelle tilstand, og hvem der kan administrere overholdelsesfunktioner, er næste trin at sikre, at du har dataene til at udføre undersøgelser af overholdelse og generere rapporter for netværk og brugeraktiviteter i organisationen. Aktivering af overvågning er også en vigtig forudsætning for overholdelsesløsninger, der er dækket senere i denne artikel.

Insights, der leveres af overvågningsloggen, er et værdifuldt værktøj, der kan hjælpe dig med at matche dine overholdelseskrav med løsninger, der kan hjælpe dig med at administrere og overvåge de områder, hvor der er behov for forbedring. Overvågningslogføring skal være aktiveret, før aktiviteter registreres, og før du kan søge i overvågningsloggen. Når denne indstilling er aktiveret, registreres bruger- og administratoraktivitet fra organisationen i overvågningsloggen og bevares i 90 dage og op til et år afhængigt af den licens, der er tildelt til brugerne.

Du kan finde en trinvis vejledning i at aktivere overvågning i Slå søgning [i overvågningslogfil til eller fra](turn-audit-log-search-on-or-off.md).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Opgave 4: Opret politikker for at give dig besked om potentielle problemer med overholdelse af regler og standarder

Microsoft indeholder flere indbyggede politikker for påmindelser, der hjælper med at identificere misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler og risici i forbindelse med informationsstyring. Disse politikker er som standard slået til, men du skal muligvis konfigurere brugerdefinerede beskeder for at administrere overholdelseskrav, der er specifikke for din organisation.

Brug beskedpolitik og dashboardværktøjer til påmindelse til at oprette brugerdefinerede påmindelsespolitikker, og få vist de beskeder, der genereres, når brugere udfører aktiviteter, der opfylder politikbetingelserne. Nogle eksempler kan være at bruge beskedpolitikker til at registrere bruger- og administratoraktiviteter, der påvirker overholdelseskrav, tilladelser og datatabshændelser i organisationen.

Du kan finde en trinvis vejledning til at oprette brugerdefinerede påmindelsespolitikker i [Beskedpolitikker i Security and Compliance Center](alert-policies.md).

## <a name="task-5-classify-and-protect-sensitive-data"></a>Opgave 5: Klassificer og beskyt følsomme data

Personer i organisationen samarbejder med andre både i og uden for organisationen for at få arbejdet udført. Det betyder, at indhold ikke længere bliver bag en firewall – det kan rejse overalt, på tværs af enheder, apps og tjenester. Og når den er på vej, skal den gøre det på en sikker og beskyttet måde, der opfylder din organisations forretnings- og overholdelsespolitikker.

[Følsomhedsmærkater](sensitivity-labels.md) lader dig klassificere og beskytte din organisations data, mens de sikrer, at brugernes produktivitet og deres evne til at samarbejde ikke bliver forhindret. Brug følsomhedsmærkater til at håndhæve kryptering og brugsbegrænsninger, anvend visuelle markeringer, og beskyt oplysninger på tværs af platforme og enheder, lokalt og i skyen.

Du kan finde en trinvis vejledning til konfiguration og brug af følsomhedsmærkater i [Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md).

## <a name="task-6-configure-retention-policies"></a>Opgave 6: Konfigurere opbevaringspolitikker

Med [en opbevaringspolitik](retention.md) kan du proaktivt beslutte, om du vil bevare indhold, slette indhold eller begge dele – bevare og derefter slette indholdet i slutningen af en bestemt opbevaringsperiode. Disse handlinger kan være nødvendige for at overholde branchebestemmelser og interne politikker og reducere risikoen i tilfælde af procesførelse eller sikkerhedsbrud.

Når indhold er underlagt en opbevaringspolitik, kan personer fortsat redigere og arbejde med indholdet, som om intet er ændret. Indholdet bevares på sin oprindelige placering. Men hvis nogen redigerer eller sletter indhold, der er underlagt opbevaringspolitikken, gemmes en kopi af det oprindelige indhold på et sikkert sted, hvor det bevares, mens opbevaringspolitikken for det pågældende indhold er gældende.

Du kan hurtigt få opbevaringspolitikker på plads for flere tjenester i dit Microsoft 365-miljø, der omfatter Teams- og Yammer-meddelelser, Exchange-mail, SharePoint-websteder og OneDrive-konti. Der er ingen begrænsninger for antallet af brugere, postkasser eller websteder, som en opbevaringspolitik automatisk kan omfatte. Men hvis du har brug for mere selektiv, kan du gøre det ved enten at konfigurere et tilpasset omfang, der er forespørgselsbaseret til dynamisk at målrette mod bestemte forekomster, eller et statisk omfang, der angiver bestemte forekomster, der altid skal medtages eller altid udelades.

Du kan finde en trinvis vejledning til konfiguration af opbevaringspolitikker i [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md). Da opbevaringspolitikker udgør hjørnestenen i en strategi for informationsstyring for Microsoft 365, skal du [se Introduktion til informationsstyring](get-started-with-information-governance.md).

## <a name="task-7-configure-sensitive-information-and-offensive-language-policies"></a>Opgave 7: Konfigurere følsomme oplysninger og stødende sprogpolitikker

Beskyttelse af følsomme oplysninger og registrering og handling på arbejdspladsens chikanehændelser er en vigtig del af overholdelse af interne politikker og standarder. [Kommunikationsoverholdelse](communication-compliance.md) i Microsoft 365 minimere disse risici ved at hjælpe dig med hurtigt at registrere, registrere og træffe afhjælpningshandlinger for mail og Microsoft Teams kommunikation. Disse omfatter upassende kommunikation, der indeholder bandeord, trusler og chikane og kommunikation, der deler følsomme oplysninger i og uden for din organisation.

En foruddefineret skabelon for stødende sprog og *politik for anti* chikane giver dig mulighed for at scanne intern og ekstern kommunikation for at finde politik match, så de kan blive godkendt af udvalgte korrekturlæsere. Korrekturlæsere kan undersøge scannede mails, Microsoft Teams, Yammer eller tredjepartskommunikation i din organisation og tage relevante afhjælpningshandlinger for at sikre, at de overholder din organisations standarder.

Den foruddefinerede skabelon  til politik for følsomme oplysninger hjælper dig med hurtigt at oprette en politik til scanning af mail og Microsoft Teams-kommunikation med definerede typer af følsomme oplysninger eller nøgleord for at sikre, at vigtige data ikke deles med personer, der ikke bør have adgang. Disse aktiviteter kan omfatte uautoriseret kommunikation om fortrolige projekter eller branchespecifikke regler for insider-handel eller andre coprojektaktiviteter.

Du kan finde en trinvis vejledning i at planlægge og konfigurere overholdelse af regler og standarder i kommunikation i [Plan for](communication-compliance-plan.md) overholdelse af regler og standarder i kommunikation [og Kom i gang med kommunikationsoverholdelse](communication-compliance-configure.md). Du kan finde oplysninger om licenser til overholdelse [af Microsoft 365 i licensvejledning til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Opgave 8: Se, hvad der sker med dine følsomme elementer

Følsomhedsmærkater, følsomme oplysningstyper, opbevaringsetiketter og politikker og trænbare klassificeringer kan bruges til at klassificere og mærke følsomme elementer på tværs af Exchange, SharePoint og OneDrive, som du har set i de tidligere opgaver. Det sidste trin i din hurtige opgaverejse er at se, hvilke elementer der er blevet mærket, og hvilke handlinger dine brugere laver på disse følsomme elementer. [indholdsstifinder](data-classification-content-explorer.md) [og aktivitetsstifinder](data-classification-activity-explorer.md) giver denne synlighed.

### <a name="content-explorer"></a>Indholdsstifinder
Med Indholdsstifinder kan du i deres oprindelige format se alle de elementer, der er klassificeret som en følsom oplysningstype eller hører til en bestemt klassificering af en togbar klassificering, samt alle elementer, der har følsomheds- eller opbevaringsmærkat anvendt.

Du kan finde en trinvis vejledning til brug af indholdsstifinder i Kend dine [data – oversigt over dataklassificering](data-classification-overview.md) og [Introduktion til indholdsstifinder](data-classification-content-explorer.md).

### <a name="activity-explorer"></a>Aktivitetsstifinder
Aktivitetsstifinder hjælper dig med at overvåge, hvad der bliver gjort med dine klassificerede og mærkede følsomme elementer på tværs af:
- SharePoint
- Exchange
- OneDrive

Der er mere end 30 forskellige filtre tilgængelige til brug, nogle er:

- datointerval
- aktivitetstype
- placering
- bruger
- følsomhedsmærkat
- opbevaringsnavn
- filsti
- DLP-politik

Du kan finde en trinvis vejledning til brug af Aktivitetsstifinder i [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md).

## <a name="next-steps"></a>Næste trin

Nu hvor du har konfigureret de grundlæggende funktioner til styring af overholdelse for din organisation, kan du overveje følgende løsninger til overholdelse af regler og standarder i Microsoft 365 for at hjælpe dig med at beskytte følsomme oplysninger og registrere og reagere på yderligere insider-risici.

### <a name="configure-retention-labels"></a>Konfigurere opbevaringsnavne

Mens opbevaringspolitikker automatisk gælder for alle elementer på objektbeholderniveau (f.eks. SharePoint-websteder, brugerpostkasser osv[.), gælder](retention.md#retention-labels) opbevaringsetiketter for individuelle elementer, f.eks. et SharePoint-dokument eller en mail. Du kan anvende disse etiketter manuelt eller automatisk.

Opbevaringsmærkater kan bruges som en del af din strategi for styring af oplysninger til at bevare det, du har brug for, og slette det, du ikke har brug for. Brug disse etiketter, når du har brug for undtagelser til dine opbevaringspolitikker, når bestemte dokumenter eller mails har brug for forskellige indstillinger for opbevaring eller sletning. Din politik for SharePoint opbevarer f.eks. alle dokumenter i tre år, men specifikke forretningsdokumenter skal opbevares i fem år. Få mere at vide under [Opret opbevaringsnavne for undtagelser til dine opbevaringspolitikker](create-retention-labels-information-governance.md).

Men opbevaringsetiketter giver, når de bruges sammen med [datastyring](records-management.md), mange flere administrationsindstillinger, der understøtter den fulde livscyklus for dokumenter og mails. Dette niveau af datastyring er velegnet til elementer af høj værdi til forretningsmæssige, juridiske eller lovgivningsmæssige krav til registrering. Få mere at vide under [Kom i gang med datastyring](get-started-with-records-management.md).

### <a name="identify-and-define-sensitive-information-types"></a>Identificer og definer følsomme oplysningstyper

Definer følsomme oplysningstyper ud fra det mønster, der er indeholdt i oplysningerne i din organisations data. Brug [indbyggede følsomme oplysningstyper til](./sensitive-information-type-entity-definitions.md) at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre og meget mere. Eller opret dine egne [brugerdefinerede følsomhedsoplysninger, der](create-a-custom-sensitive-information-type.md) er specifikke for din organisation.

Du kan finde en trinvis vejledning til at definere brugerdefinerede typer af følsomme oplysninger under Oprette en brugerdefineret type af følsomme oplysninger i [Security & Compliance Center](./create-a-custom-sensitive-information-type.md).

### <a name="prevent-data-loss"></a>Undgå tab af data

[Politikker til forebyggelse af datatab (DLP)](dlp-learn-about-dlp.md) giver dig mulighed for at identificere, overvåge og automatisk beskytte følsomme oplysninger på tværs Microsoft 365 organisationen. Brug DLP-politikker til at identificere følsomme elementer på tværs af Microsoft-tjenester, forhindre utilsigtet deling af følsomme elementer og hjælpe brugerne med at lære at overholde reglerne uden at afbryde deres arbejdsproces.

For at få en trinvis vejledning til konfiguration af DLP-politikker skal [du oprette, teste og finjustere en DLP-politik](create-test-tune-dlp-policy.md). Du kan finde oplysninger om licenser til administration af [datatab Microsoft 365 vejledning i licenser til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Registrer og act on insider risks

Flere og flere medarbejdere har øget adgangen til at oprette, administrere og dele data på tværs af et bredt spektrum af platforme og tjenester. I de fleste tilfælde har organisationer begrænsede ressourcer og værktøjer til at identificere og reducere risici i hele organisationen og samtidig overholde overholdelseskravene og medarbejdernes standarder for beskyttelse af personlige oplysninger. Disse risici kan omfatte datatyveri ved at fjerne medarbejdere og datalækage af oplysninger uden for organisationen ved utilsigtet overdeling eller ondsindede hensigter.

[Insider-risikostyring](insider-risk-management-policies.md) i Microsoft 365 bruger den fulde brødkrud af tjenester og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og handle på risikabel brugeraktivitet. Insider-risikostyring giver dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer og træffe foranstaltninger for at reducere disse risici ved hjælp af logge fra Microsoft 365 og Microsoft Graph.

Du kan finde en trinvis vejledning i at planlægge og konfigurere politikker for insider-risikostyring i [Plan for insider-risikostyring](insider-risk-management-plan.md) og [Kom i gang med insider-risikostyring](insider-risk-management-configure.md). Du kan finde oplysninger om insider-licensering [Microsoft 365 licenseringsvejledning til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
