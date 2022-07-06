---
title: Hurtige opgaver for at komme i gang med overholdelse af angivne standarder i Microsoft Purview
description: Få mere at vide om opgaver, der hjælper dig med hurtigt at komme i gang med overholdelse af angivne standarder i Microsoft Purview.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
f1.keywords:
- NOCSH
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
ms.openlocfilehash: 5e5b0aa9efb5d00602bba39ca18ef582cf34271a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632635"
---
# <a name="quick-tasks-for-getting-started-with-compliance-in-microsoft-purview"></a>Hurtige opgaver for at komme i gang med overholdelse af angivne standarder i Microsoft Purview

Hvis du ikke kender Microsoft Purview og undrer dig over, hvor du skal starte, indeholder denne artikel en vejledning i de grundlæggende funktioner og prioriterer vigtige opgaver i forbindelse med overholdelse af angivne standarder. Denne artikel hjælper dig med hurtigt at komme i gang med at administrere og overvåge dine data, beskytte oplysninger og minimere insiderrisici.

Denne artikel er også nyttig, hvis du finder ud af, hvordan du bedst administrerer risici, beskytter dine data og overholder regler og standarder med en nyligt ekstern arbejdsstyrke. Medarbejderne samarbejder nu og opretter forbindelse til hinanden på nye måder, og denne ændring betyder, at dine eksisterende processer og kontrolelementer for overholdelse af angivne standarder muligvis skal tilpasses. Det er vigtigt at identificere og administrere disse nye risici for overholdelse af angivne standarder i din organisation for at beskytte dine data og minimere trusler og risici.

Når du har fuldført disse grundlæggende overholdelsesopgaver, kan du overveje at udvide dækningen af overholdelse af angivne standarder i din organisation ved at implementere yderligere Microsoft Purview-løsninger.

## <a name="task-1-configure-compliance-permissions"></a>Opgave 1: Konfigurer tilladelser til overholdelse af regler og standarder

Det er vigtigt at administrere, hvem i din organisation der har adgang til Microsoft Purview-compliance-portal for at få vist indhold og udføre administrationsopgaver. Microsoft 365 indeholder administrative roller, der er specifikke for overholdelse af angivne standarder og for brug af de værktøjer, der er inkluderet i Microsoft Purview-compliance-portal.

Start med at tildele overholdelsestilladelser til personer i din organisation, så de kan udføre disse opgaver og forhindre uautoriserede personer i at få adgang til områder uden for deres ansvar. Du skal sikre dig, at du har tildelt de rette personer til administratorrollerne **overholdelsesdata** og administratorrollerne for **overholdelsesadministratoren** , før du begynder at konfigurere og implementere overholdelsesløsninger, der er inkluderet i Microsoft 365. Du skal også tildele brugere rollen Global læser i Azure Active Directory for at få vist data i Overholdelsesstyring.

Hvis du vil have en trinvis vejledning til at konfigurere tilladelser og tildele personer til administratorroller, skal du se [Tilladelser i Security & Compliance Center](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="task-2-know-your-state-of-compliance"></a>Opgave 2: Kend din overholdelsestilstand

Det er svært at vide, hvor du skal hen, hvis du ikke ved, hvor du er. Opfyldelse af dine behov for overholdelse af angivne standarder omfatter forståelse af dit aktuelle risikoniveau, og hvilke opdateringer der kan være behov for i disse stadigt skiftende tider. Uanset om din organisation ikke har erfaring med overholdelse af angivne standarder eller har stor erfaring med standarder og regler, der styrer din branche, er det bedste, du kan gøre for at forbedre overholdelse af angivne standarder, at forstå, hvor din organisation står.

[Microsoft Purview Compliance Manager](/microsoft-365/compliance/compliance-manager) kan hjælpe dig med at forstå din organisations overholdelse af angivne standarder og fremhæve områder, der kan have brug for forbedringer. Overholdelsesstyring bruger et centraliseret dashboard til at beregne en risikobaseret score og måle dine fremskridt med at fuldføre handlinger, der hjælper med at reducere risici i forbindelse med databeskyttelse og lovgivningsmæssige standarder. Du kan også bruge Overholdelsesstyring som et værktøj til at spore alle dine risikovurderinger. Den indeholder funktioner i arbejdsprocesser, der kan hjælpe dig med effektivt at fuldføre dine risikovurderinger via et almindeligt værktøj.

Du kan finde en trinvis vejledning til, hvordan du kommer i gang med Overholdelsesstyring, under [Kom i gang med Overholdelsesstyring](/microsoft-365/compliance/compliance-manager-setup).

> [!IMPORTANT]
> Sikkerhed og overholdelse af angivne standarder er tæt integreret i de fleste organisationer. Det er vigtigt, at din organisation håndterer grundlæggende sikkerheds-, trusselsbeskyttelses- og identitets- og adgangsstyringsområder for at hjælpe med at levere en dybdegående forsvarstilgang til både sikkerhed og overholdelse af angivne standarder.
>
> Kontrollér din [Microsoft 365 Secure Score](/microsoft-365/security/defender/microsoft-secure-score) på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og fuldføre de opgaver, der er beskrevet i følgende artikler:
>
> - [Oversigt over sikkerhed – topprioriteter for de første 30 dage, 90 dage og derefter](/microsoft-365/security/office-365-security/security-roadmap)
> - [Top 12-opgaver til sikkerhedsteams, der understøtter at arbejde hjemmefra](/microsoft-365/security/top-security-tasks-for-remote-work)

## <a name="task-3-enable-auditing-for-your-organization"></a>Opgave 3: Aktivér overvågning for din organisation

Nu, hvor du har bestemt din organisations aktuelle tilstand, og hvem der kan administrere funktioner til overholdelse af angivne standarder, er det næste trin at sikre, at du har dataene til at udføre undersøgelser af overholdelse af angivne standarder og generere rapporter for netværks- og brugeraktiviteter i din organisation. Aktivering af overvågning er også en vigtig forudsætning for løsninger til overholdelse af angivne standarder, som beskrives senere i denne artikel.

Indsigt fra overvågningsloggen er et værdifuldt værktøj til at hjælpe med at matche dine overholdelseskrav til løsninger, der kan hjælpe dig med at administrere og overvåge områder med overholdelse af angivne standarder, der skal forbedres. Overvågningslogføring skal aktiveres, før aktiviteter registreres, og før du kan søge i overvågningsloggen. Når funktionen er aktiveret, registreres bruger- og administratoraktivitet fra din organisation i overvågningsloggen og opbevares i 90 dage og op til et år afhængigt af den licens, der er tildelt brugerne.

Du kan finde en trinvis vejledning til, hvordan du slår overvågning til, under [Slå søgning i overvågningslog til eller fra](/microsoft-365/compliance/turn-audit-log-search-on-or-off).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Opgave 4: Opret politikker for at advare dig om potentielle problemer med overholdelse af angivne standarder

Microsoft leverer flere indbyggede beskedpolitikker, der hjælper med at identificere misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler samt risici for administration af datalivscyklusser. Disse politikker er som standard slået til, men du skal muligvis konfigurere brugerdefinerede beskeder for at hjælpe med at administrere de overholdelseskrav, der er specifikke for din organisation.

Brug værktøjerne til beskedpolitik og dashboard til beskeder til at oprette brugerdefinerede politikker for beskeder og få vist de beskeder, der genereres, når brugerne udfører aktiviteter, der opfylder politikbetingelserne. Nogle eksempler kan være at bruge politikker for beskeder til at spore bruger- og administratoraktiviteter, der påvirker overholdelseskrav, tilladelser og datatabshændelser i din organisation.

Du kan finde en trinvis vejledning i, hvordan du opretter brugerdefinerede politikker for beskeder, [i Beskedpolitikker i Center for sikkerhed og overholdelse af angivne standarder](/microsoft-365/compliance/alert-policies).

## <a name="task-5-classify-and-protect-sensitive-data"></a>Opgave 5: Klassificer og beskyt følsomme data

Personer i din organisation samarbejder med andre både i og uden for organisationen for at få deres arbejde fra hånden. Det betyder, at indhold ikke længere forbliver bag en firewall – det kan roame overalt på tværs af enheder, apps og tjenester. Og når den roamer, vil du gerne have, at den gør det på en sikker og beskyttet måde, der opfylder organisationens politikker for virksomhed og overholdelse af angivne standarder.

[Med følsomhedsmærkater](/microsoft-365/compliance/sensitivity-labels) kan du klassificere og beskytte din organisations data, samtidig med at du sikrer, at brugernes produktivitet og deres mulighed for at samarbejde ikke hindres. Brug følsomhedsmærkater til at gennemtvinge krypterings- og brugsbegrænsninger for visuelle markeringer og beskytte oplysninger på tværs af platforme og enheder, i det lokale miljø og i cloudmiljøet.

Du kan finde en trinvis vejledning til, hvordan du konfigurerer og bruger følsomhedsmærkater, under [Kom i gang med følsomhedsmærkater](/microsoft-365/compliance/get-started-with-sensitivity-labels).

## <a name="task-6-configure-retention-policies"></a>Opgave 6: Konfigurer opbevaringspolitikker

En [opbevaringspolitik](/microsoft-365/compliance/retention) giver dig mulighed for proaktivt at beslutte, om du vil bevare indhold, slette indhold eller begge dele – bevare og derefter slette indholdet i slutningen af en angivet opbevaringsperiode. Disse handlinger kan være nødvendige for at overholde brancheregler og interne politikker og for at reducere din risiko i tilfælde af tvister eller sikkerhedsbrud.

Når indhold er underlagt en opbevaringspolitik, kan personer fortsætte med at redigere og arbejde med indholdet, som om intet er ændret. Indholdet bevares på sin oprindelige placering. Men hvis nogen redigerer eller sletter indhold, der er omfattet af opbevaringspolitikken, gemmes der en kopi af det oprindelige indhold på et sikkert sted, hvor det bevares, mens opbevaringspolitikken for det pågældende indhold er i kraft.

Du kan hurtigt placere opbevaringspolitikker for flere tjenester i dit Microsoft 365-miljø, der omfatter Teams- og Yammer-meddelelser, Exchange-mail, SharePoint-websteder og OneDrive-konti. Der er ingen grænser for antallet af brugere, postkasser eller websteder, som en opbevaringspolitik automatisk kan indeholde. Men hvis du har brug for at blive mere selektiv, kan du gøre det ved at konfigurere enten et adaptivt omfang, der er forespørgselsbaseret til dynamisk at målrette bestemte instanser, eller et statisk område, der angiver, at bestemte instanser altid skal inkluderes eller altid udelades.

Du kan finde en trinvis vejledning til, hvordan du konfigurerer opbevaringspolitikker, under [Opret og konfigurer opbevaringspolitikker](/microsoft-365/compliance/create-retention-policies). Da opbevaringspolitikker udgør hjørnestenen i en strategi for administration af datalivscyklusser for Microsoft 365-apps og -tjenester, skal du også se [Kom i gang med administration af datalivscyklusser](/microsoft-365/compliance/get-started-with-data-lifecycle-management).

## <a name="task-7-configure-sensitive-information-and-inappropriate-language-policies"></a>Opgave 7: Konfigurer følsomme oplysninger og upassende sprogpolitikker

Beskyttelse af følsomme oplysninger og registrering og behandling af chikanehændelser på arbejdspladsen er en vigtig del af overholdelsen af interne politikker og standarder. [Overholdelse af angivne standarder for kommunikation](/microsoft-365/compliance/communication-compliance) i Microsoft Purview hjælper med at minimere disse risici ved hurtigt at registrere, registrere og afhjælpe handlinger i forbindelse med mail og Microsoft Teams-kommunikation. Disse omfatter upassende kommunikation, der indeholder bandeord, trusler og chikane og kommunikation, der deler følsomme oplysninger i og uden for din organisation.

En foruddefineret skabelon til *registrering af upassende tekstpolitik* giver dig mulighed for at scanne intern og ekstern kommunikation for politikkampe, så de kan undersøges af udpegede korrekturlæsere. Korrekturlæsere kan undersøge scannet mail, Microsoft Teams, Yammer eller tredjepartskommunikation i din organisation og udføre de nødvendige afhjælpningshandlinger for at sikre, at de overholder organisationens standarder.

Den foruddefinerede skabelon *Registrer følsomme oplysninger* hjælper dig med hurtigt at oprette en politik til scanning af mail og Microsoft Teams-kommunikation, der indeholder definerede følsomme informationstyper eller nøgleord, for at sikre, at vigtige data ikke deles med personer, der ikke skal have adgang. Disse aktiviteter kan omfatte uautoriseret kommunikation om fortrolige projekter eller branchespecifikke regler for insiderhandel eller andre hemmelige aktiviteter.

Hvis du vil have en trinvis vejledning i at planlægge og konfigurere overholdelse af kommunikation, skal du se [Planlæg overholdelse af kommunikation](/microsoft-365/compliance/communication-compliance-plan) og [Kom i gang med overholdelse af kommunikation](/microsoft-365/compliance/communication-compliance-configure). Du kan finde oplysninger om licenser til overholdelse af kommunikation under [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Opgave 8: Se, hvad der sker med dine følsomme elementer

Følsomhedsmærkater, følsomme oplysningstyper, opbevaringsmærkater og politikker og klassificeringer, der kan oplæres, kan bruges til at klassificere og mærke følsomme elementer på tværs af Exchange, SharePoint og OneDrive, som du har set i de forrige opgaver. Det sidste trin i din hurtige opgaverejse er at se, hvilke elementer der er mærket, og hvilke handlinger dine brugere foretager på disse følsomme elementer. [indholdsoversigt](/microsoft-365/compliance/data-classification-content-explorer) og [aktivitetsoversigt](/microsoft-365/compliance/data-classification-activity-explorer) giver denne synlighed.

### <a name="content-explorer"></a>Indholdsoversigt

Indholdsoversigt giver dig mulighed for i deres oprindelige format at få vist alle de elementer, der er klassificeret som en følsom oplysningstype eller tilhører en bestemt klassificering af en klassificering, der kan oplæres, og alle elementer, der har anvendt følsomhed eller opbevaringsmærkat.

Du kan finde en trinvis vejledning til brug af Indholdsoversigt under [Kend dine data – oversigt over dataklassificering](/microsoft-365/compliance/data-classification-overview) og [Kom i gang med indholdsoversigt.](/microsoft-365/compliance/data-classification-content-explorer)

### <a name="activity-explorer"></a>Aktivitetsoversigt

Aktivitetsoversigt hjælper dig med at overvåge, hvad der udføres med dine klassificerede og mærkede følsomme elementer på tværs af:

- SharePoint
- Exchange
- OneDrive

Der er over 30 forskellige filtre tilgængelige til brug. Nogle er:

- datointerval
- aktivitetstype
- Placering
- Bruger
- følsomhedsmærkat
- opbevaringsmærkat
- filsti
- DLP-politik

Du kan finde en trinvis vejledning til, hvordan du bruger aktivitetsoversigt, under [Kom i gang med aktivitetsoversigt](/microsoft-365/compliance/data-classification-activity-explorer).

## <a name="next-steps"></a>Næste trin

Nu, hvor du har konfigureret de grundlæggende funktioner til administration af overholdelse af angivne standarder for din organisation, kan du overveje følgende løsninger til overholdelse af angivne standarder i Microsoft Purview for at hjælpe dig med at beskytte følsomme oplysninger og registrere og reagere på yderligere insiderrisici.

### <a name="configure-retention-labels"></a>Konfigurer opbevaringsmærkater

Opbevaringspolitikker gælder automatisk for alle elementer på objektbeholderniveau (f.eks. SharePoint-websteder, brugerpostkasser osv.), [og opbevaringsmærkater](/microsoft-365/compliance/retention#retention-labels) gælder for individuelle elementer, f.eks. et SharePoint-dokument eller en mail. Du kan anvende disse mærkater manuelt eller automatisk.

Opbevaringsmærkater kan bruges som en del af din strategi for datastyring til at bevare det, du har brug for, og slette det, du ikke har brug for. Brug disse mærkater, når du har brug for undtagelser fra dine opbevaringspolitikker, når bestemte dokumenter eller mails har brug for forskellige indstillinger for opbevaring eller sletning. Din SharePoint-politik bevarer f.eks. alle dokumenter i tre år, men bestemte forretningsdokumenter skal opbevares i fem år. Du kan få flere oplysninger under [Opret opbevaringsmærkater for undtagelser til dine opbevaringspolitikker](/microsoft-365/compliance/create-retention-labels-data-lifecycle-management).

Opbevaringsmærkater giver dog mange flere administrationsmuligheder, når de bruges med [datastyring](/microsoft-365/compliance/records-management), til at understøtte dokumenter og mails på elementniveau. Dette niveau af dataadministration er velegnet til produkter af høj værdi til forretnings-, juridiske eller lovmæssige krav til registrering. Du kan få flere oplysninger under [Kom i gang med datastyring](/microsoft-365/compliance/get-started-with-records-management).

### <a name="identify-and-define-sensitive-information-types"></a>Identificer og definer typer af følsomme oplysninger

Definer følsomme oplysningstyper på baggrund af mønsteret i oplysningerne i organisationens data. Brug [indbyggede typer følsomme oplysninger](./sensitive-information-type-entity-definitions.md) , der hjælper med at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre og meget mere. Eller opret dine egne [brugerdefinerede typer af følsomhedsoplysninger](/microsoft-365/compliance/create-a-custom-sensitive-information-type) , der er specifikke for din organisation.

Du kan finde en trinvis vejledning til, hvordan du definerer brugerdefinerede typer følsomme oplysninger, [under Opret en brugerdefineret type følsomme oplysninger i Security & Compliance Center](./create-a-custom-sensitive-information-type.md).

### <a name="prevent-data-loss"></a>Undgå datatab

[Microsoft Purview Forebyggelse af datatab politikker (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) giver dig mulighed for at identificere, overvåge og automatisk beskytte følsomme oplysninger på tværs af din Microsoft 365-organisation. Brug DLP-politikker til at identificere følsomme elementer på tværs af Microsoft-tjenester, forhindre utilsigtet deling af følsomme elementer og hjælpe brugerne med at lære, hvordan de forbliver kompatible uden at afbryde deres arbejdsproces.

Hvis du vil have en trinvis vejledning i at konfigurere DLP-politikker, [skal du oprette, teste og justere en DLP-politik](/microsoft-365/compliance/create-test-tune-dlp-policy). Du kan finde oplysninger om licenser til administration af datatab i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Registrer og håndtér insiderrisici

Flere og flere medarbejdere har øget adgang til at oprette, administrere og dele data på tværs af en bred vifte af platforme og tjenester. I de fleste tilfælde har organisationer begrænsede ressourcer og værktøjer til at identificere og afhjælpe risici i hele organisationen, samtidig med at de opfylder kravene til overholdelse af angivne standarder og standarder for beskyttelse af personlige oplysninger for medarbejdere. Disse risici kan omfatte datatyveri ved at afgå fra medarbejdere og datalækager af oplysninger uden for din organisation ved utilsigtet overdeling eller ondsindede hensigter.

[Insiderrisikostyring](/microsoft-365/compliance/insider-risk-management-policies) bruger hele bredden af tjenesten og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikable brugeraktivitet. Ved hjælp af logge fra Microsoft 365 og Microsoft Graph giver insiderrisikostyring dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer og træffe foranstaltninger til at afhjælpe disse risici.

Hvis du vil have en trinvis vejledning i at planlægge og konfigurere politikker for styring af insiderrisiko, skal du se [Planlæg styring af insiderrisiko](/microsoft-365/compliance/insider-risk-management-plan) og [Kom i gang med styring af insiderrisiko](/microsoft-365/compliance/insider-risk-management-configure). Du kan finde oplysninger om licenser til styring af insiderrisiko under [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
