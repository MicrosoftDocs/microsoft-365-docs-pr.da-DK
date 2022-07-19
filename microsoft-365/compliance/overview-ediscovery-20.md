---
title: Oversigt over eDiscovery-løsningen (Premium) i Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/08/2022
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- m365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Få mere at vide om eDiscovery-løsningen (Premium) i Microsoft Purview. Denne artikel indeholder en oversigt over eDiscovery (Premium) i Microsoft Purview, et værktøj, der kan hjælpe dig med at administrere interne og eksterne undersøgelser. Den rammer også de forretningsmæssige årsager til at bruge eDiscovery (Premium) til at administrere dine juridiske undersøgelser.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7d534012466300675a7143cdada0b43468027104
ms.sourcegitcommit: 75d0403b4114bdd1d228ca05a284b9e514f6f2f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66855081"
---
# <a name="overview-of-microsoft-purview-ediscovery-premium"></a>Oversigt over Microsoft Purview eDiscovery (Premium)

Løsningen Microsoft Purview eDiscovery (Premium) bygger på de eksisterende funktioner i Microsoft eDiscovery og analyse. eDiscovery (Premium) indeholder en arbejdsproces fra start til slut, hvor du kan bevare, indsamle, analysere, gennemse og eksportere indhold, der reagerer på din organisations interne og eksterne undersøgelser. Det giver også juridiske teams mulighed for at administrere hele arbejdsprocessen for meddelelse om juridisk venteposition for at kommunikere med tilsynsførende, der er involveret i en sag.

## <a name="ediscovery-premium-capabilities"></a>eDiscovery-funktioner (Premium)

eDiscovery (Premium) kan hjælpe din organisation med at besvare juridiske spørgsmål eller interne undersøgelser ved at finde data, hvor de er gemt. Du kan problemfrit administrere eDiscovery-arbejdsprocesser ved at identificere personer af interesse og deres datakilder, uden problemer anvende ventepositioner for at bevare data og derefter administrere kommunikationsprocessen for juridiske ventepositioner. Ved at indsamle data fra kilden kan du søge på den dynamiske Microsoft 365-platform for hurtigt at finde det, du har brug for. Intelligente funktioner til maskinel indlæring, f.eks. dyb indeksering, mailtrådning og næsten registrering af dubletter hjælper dig også med at reducere store datamængder til et relevant datasæt.

I følgende afsnit beskrives det, hvordan disse funktioner i eDiscovery (Premium) kan hjælpe din organisation.

![eDiscovery-funktioner (Premium).](../media/advanced-ediscovery-capabilities.png)

### <a name="discover-and-collect-data-in-place"></a>Opdag og indsaml data på stedet

Organisationer, der er afhængige af flere eDiscovery-løsninger fra tredjepart, kræver traditionelt, at store datamængder kopieres ud af Microsoft 365 for at behandle og være vært for dublerede data. Denne nødvendighed øger tiden til at finde relevante data og risikoen, omkostningerne og kompleksiteten ved at administrere flere løsninger.

Med eDiscovery (Premium) i Microsoft 365 kan du finde data ved kilden og holde dig inden for din Microsoft 365-sikkerheds- og overholdelsesgrænse.  Ved at indsamle data på stedet fra livesystemet reducerer eDiscovery (Premium) friktionen ved at gå tilbage til kilden og reducerer unødvendigt arbejde med at finde manglende indhold, hvilket ofte sker, når journaling halter i traditionelle eDiscovery-løsninger.

Oprindelige søge- og samlingsfunktioner for data i Teams, Yammer, SharePoint Online, OneDrive for Business og Exchange Online forbedrer datasøgningen yderligere. For eksempel eDiscovery (Premium):

- Genskaber Teams-samtaler (i stedet for at returnere individuelle meddelelser fra samtaler).

- Indsamler skybaseret indhold, der deles med brugere ved hjælp af links eller moderne vedhæftede filer i mails og Teams-chats.

- Har indbygget understøttelse af hundredvis af filtyper, der ikke er Microsoft 365.

- Indsamler data fra tredjepartskilder (f.eks. Bloomberg, Facebook, Slack og Zoom Meetings), der er importeret og arkiveret i Microsoft 365 af [dataconnectorer](archiving-third-party-data.md).

### <a name="manage-ediscovery-workflow-in-one-platform"></a>Administrer eDiscovery-arbejdsproces på én platform

eDiscovery (Premium) kan hjælpe dig med at reducere antallet af eDiscovery-løsninger, du skal stole på. Den indeholder en strømlinet, end-to-end-arbejdsproces, som alle forekommer i Microsoft 365. eDiscovery (Premium) hjælper med at reducere friktionen ved at identificere og indsamle potentielle kilder til relevante oplysninger ved automatisk at knytte unikke og delte datakilder til den person, der er interesseret (kendt som *en tilsynsførende*), og ved at levere rapportering og analyse af potentielt relevante data, før de indsamles til analyse og gennemgang.

Derudover kan Microsoft Graph-API'er hjælpe dig med at automatisere eDiscovery-arbejdsprocessen og udvide eDiscovery (Premium) til brugerdefinerede løsninger.

### <a name="cull-data-intelligently"></a>Data fra cull på en intelligent måde

Intelligente funktioner til maskinel indlæring i eDiscovery (Premium) hjælper dig med at reducere mængden af data, der skal gennemses. Disse intelligente funktioner hjælper dig med at reducere og reducere store datamængder til et relevant sæt. En indbygget forespørgsel i korrektursæt hjælper f.eks. med kun at filtrere efter entydigt indhold ved at identificere næsten dubletter. Denne funktion kan reducere mængden af data, der skal gennemses, væsentligt.

Yderligere funktioner til maskinel indlæring kan yderligere tilpasse og identificere relevante data ved hjælp af i-mærker og teknologi assisterede korrekturværktøjer som f.eks. relevansmodulerne.

## <a name="ediscovery-premium-alignment-with-the-electronic-discovery-reference-model"></a>Justering af eDiscovery (Premium) med modellen Elektronisk registreringsreference

Den indbyggede arbejdsproces for eDiscovery (Premium) i Microsoft 365 er i overensstemmelse med den eDiscovery-proces, der er beskrevet af EDRM (Electronic Discovery Reference Model).

![EDRM (Electronic Discovery Reference Model).](../media/EDRMv2.png)

(Billede baseret på EDRM-modellen på edrm.net)

På et højt niveau understøtter eDiscovery (Premium) EDRM-arbejdsprocessen:

- **Identifikation.** Når du har identificeret potentielle personer, der er interessante i en undersøgelse, kan du føje dem som tilsynsførende (også kaldet *datavogtere*, da de kan have oplysninger, der er relevante for undersøgelsen) til en eDiscovery-sag (Premium). Når brugere er tilføjet som tilsynsførende, er det nemt at bevare, indsamle og gennemse tilsynsførende dokumenter.

- **Bevarelse.** Med eDiscovery (Premium) kan du bevare og beskytte data, der er relevante for en undersøgelse, i en sag. Du kan også placere data, der ikke er varetægtsfængslede, i venteposition. eDiscovery (Premium) har også en indbygget arbejdsproces for kommunikation, så du kan sende meddelelser om juridisk bevarelse til vogtere og spore deres bekræftelser.

- **Samling.** Når du har identificeret (og bevaret) de datakilder, der er relevante for undersøgelsen, kan du bruge det indbyggede søgeværktøj i eDiscovery (Premium) til at søge efter og indsamle dynamiske data fra datakilder med frihedsberøvelse (og datakilder uden frihedsberøvelse, hvis det er relevant), som kan være relevante for sagen.

- **Behandling.** Når du har indsamlet alle de data, der er relevante for sagen, er næste trin at behandle dem med henblik på yderligere gennemgang og analyse. I eDiscovery (Premium) kopieres de lokale data, som du identificerede i indsamlingsfasen, til en Azure Storage-placering (kaldet et *anmeldelsessæt*), hvilket giver dig en statisk visning af sagsdataene.

- **Anmeld.** Når data er føjet til et korrektursæt, kan du få vist bestemte dokumenter og køre yderligere forespørgsler for at reducere dataene til det, der er mest relevant for sagen. Du kan også anmærke og mærke bestemte dokumenter.

- **Analyse.** eDiscovery (Premium) indeholder et integreret analyseværktøj, der hjælper dig med at finde frem til yderligere data fra det korrektursæt, som du finder ikke er relevant for undersøgelsen. Ud over at reducere mængden af relevante data hjælper Advance eDiscovery dig også med at spare juridiske korrekturomkostninger ved at lade dig organisere indhold for at gøre korrekturprocessen nemmere og mere effektiv.

- **Produktion** og **præsentation.** Når du er klar, kan du eksportere dokumenter fra en korrektur, der er angivet til juridisk gennemsyn. Du kan eksportere dokumenter i deres oprindelige format eller i et EDRM-angivet format, så de kan importeres til programmer til gennemsyn fra tredjepart.

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Du kan finde oplysninger om, hvilke licenser der giver en bruger rettigheder til at drage fordel af eDiscovery (Premium), i [Microsoft 365-vejledningen til overholdelse af & sikkerhed](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-ediscovery) og se afsnittet "eDiscovery og overvågning" i [Sammenligningstabellen til Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2139145).

Du kan få oplysninger om, hvordan du tildeler licenser, under [Tildel licenser til brugere](/microsoft-365/admin/manage/assign-licenses-to-users).

## <a name="get-started-with-ediscovery-premium"></a>Kom i gang med eDiscovery (Premium)

Der er to hurtige og nemme trin til at komme i gang med eDiscovery (Premium).

![Introduktion til arbejdsprocessen med eDiscovery (Premium).](../media/get-started-AeD.png)

|Trin  |Beskrivelse  |
|:---------|:---------|
|[Konfigurer eDiscovery (Premium)](get-started-with-advanced-ediscovery.md)| Når du har bekræftet abonnements- og licenskravene, kan du tildele tilladelser og konfigurere indstillinger for hele organisationen for at komme i gang med at bruge eDiscovery (Premium).|
|[Opret og administrer sager](create-and-manage-advanced-ediscoveryv2-case.md) | Opret sager for at administrere eDiscovery-arbejdsprocessen (Premium) for alle juridiske og andre typer undersøgelser i din organisation.|
|||

## <a name="ediscovery-premium-architecture"></a>eDiscovery-arkitektur (Premium)

Her er et eDiscovery-arkitekturdiagram (Premium), der viser arbejdsprocessen fra slutpunkt til slutpunkt i et enkelt geo-miljø og i et multi-geo-miljø samt dataflowet fra slutpunkt til slutpunkt, der er justeret i forhold til [EDRM](#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model).

[![Modelplakat: eDiscovery (Premium)-arkitektur i Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Vis som et billede](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Download som en PDF-fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Download som en Visio-fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)

## <a name="training"></a>Uddannelse

Oplæring af it-administratorer, eDiscovery-ledere og teams til undersøgelse af overholdelse i de grundlæggende funktioner i eDiscovery (Premium) kan hjælpe din organisation med at komme hurtigere i gang ved hjælp af Microsoft 365 eDiscovery-værktøjer. Microsoft 365 indeholder følgende ressource, der kan hjælpe disse brugere i din organisation med at komme i gang med eDiscovery: [Beskriv eDiscovery- og overvågningsegenskaberne i Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
