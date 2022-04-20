---
title: Reference til forudsigende kodning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: ''
ms.openlocfilehash: 2f70039d3e55c429bf175d850db907eb7dc5b598
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942155"
---
# <a name="predictive-coding-reference-preview"></a>Reference til forudsigende kode (prøveversion)

I denne artikel beskrives de vigtigste begreber og målepunkter for værktøjet til forudsigende kodning i Microsoft Purview eDiscovery (Premium). Afsnittene i artiklen er angivet i alfabetisk rækkefølge.

## <a name="confidence-level"></a>Konfidensniveau

Tillidsniveauet er en avanceret indstilling, når du opretter en forudsigende kodemodel. Den definerer, at modellens ydeevnemålepunkter (f.eks. rigdom, præcision og genkaldelse) falder inden for et angivet interval (der bestemmer den fejlmargen, der er defineret for modellen), og som er repræsentativ for de sande værdier for de forudsigelsesscores, som modellen tildeler til elementer i korrektursættet. Værdierne for konfidensniveauet og fejlmargenen hjælper også med at bestemme, hvor mange elementer der er inkluderet i kontrolelementsættet. Standardværdien for konfidensniveauet er 0,95 eller 95 %.

## <a name="control-set"></a>Kontrolelementsæt

Et kontrolelementsæt bruges under oplæringsprocessen for en forudsigende kodemodel. Kontrolelementsættet er til at evaluere de forudsigelsesscores, som modellen tildeler til elementer med den mærkat, du udfører under oplæringsrunder. Størrelsen af kontrolelementsættet er baseret på antallet af elementer i korrektursættet og det tillidsniveau og den margen for fejlværdier, der angives, når modellen oprettes. Elementer i kontrolelementsættet ændres aldrig og kan ikke identificeres af brugerne. Det samlede antal elementer i kontrolelementsættet vises på pop op-siden for en træningsrunde.

## <a name="control-set-confusion-matrix"></a>Kontrolsæt for forvirringsmatrix

Når du har fuldført en træningsrunde, tildeler modellen en forudsigelsesscore til de 10 elementer i kontrolelementsættet, som du mærkede under oplæringsrunden. Modellen sammenligner forudsigelsesscoren for disse 10 elementer med den faktiske mærkat, som du tildelte elementet under oplæringsrunden. Baseret på denne sammenligning identificerer modellen følgende klassificeringer for at vurdere modellens forudsigelsesydeevne:

<br>

****

|Etiket|Elementet Forudsig model er relevant|Elementet forudsagt af modellen er ikke relevant|
|---|---|---|
|**Elementet med korrekturlæsermærkater er relevant**|Sand positiv|Falsk positiv|
|**Elementet for korrekturlæsermærkater er ikke relevant**|Falsk negativ|Sand negativ|
|

Baseret på disse sammenligninger får modellen værdier for F-score, præcision og genkaldelsesmetrik og fejlmargenen for hver enkelt. Antallet af hver af forvirringstyperne fra matrixen vises på pop op-siden for en træningsrunde.

## <a name="f-score"></a>F-score

F-scoren er et vægtet gennemsnit af scorerne for målepunkterne for præcision og genkaldelse.  Intervallet for scorer for denne metrikværdi er fra **0** til **1**. En score, der er tættere på **1** , angiver, at modellen mere præcist registrerer relevante elementer. Metrikværdien for F-score vises på modeldashboardet og på pop op-siden for hver træningsrunde.

## <a name="margin-of-error"></a>Fejlmargen

Fejlmargenen er en avanceret indstilling, når du opretter en forudsigende kodningstilstand. Den angiver graden af fejl i metrikværdier for ydeevne (f.eks. rigdom, præcision og genkaldelse), der er afledt af tilfældigt udsnit af elementer i dit kontrolelementsæt. En lavere fejlmargen kræver et større kontrolelementsæt for at sikre, at modellens målepunkter for ydeevne falder inden for et mindre interval. Værdierne for fejlmargenen og tillidsniveauet hjælper også med at bestemme, hvor mange elementer der er inkluderet i kontrolelementsættet. Standardværdien for fejlmargenen er 0,05 eller 5 %.

## <a name="model-stability"></a>Modelstabilitet

Modelstabilitet angiver modellens mulighed for præcist at forudsige, om et dokument i et korrektursæt er relevant eller ikke relevant. Når en model er ustabil, skal der muligvis udføres flere træningsrunder for at inkludere modellens stabilitet. Når modellen er stabil, skal der muligvis ikke udføres flere træningsrunder. Modeldashboardet angiver den aktuelle tilstand af modellens stabilitet. Når en model er stabil, har målepunkterne for ydeevne nået et niveau, der svarer til indstillingerne for tillidsniveauet og fejlmargenen.

## <a name="overturn-rate"></a>Omdrejningssats

Omdrejningssatsen er procentdelen af elementer i korrektursættet, hvor forudsigelsesscoren blev ændret mellem oplæringsrunder. En model anses for at være stabil, når omdrejningssatsen er mindre end 5 %. Metrikværdien for omvæltningsfrekvensen vises på modeldashboardet og på pop op-siden for hver træningsrunde. Omdrejningssatsen for den første træningsrunde er nul, fordi der ikke er en tidligere forudsigelsesscore, der kan tilsidesættes.

## <a name="precision"></a>Præcision

Præcisionsmålemetrikværdien måler den andel af elementer, der faktisk er relevante blandt de elementer, som den forudsagte model var relevant. Det betyder, at elementer i kontrolelementsættet, hvor mærkaten er relevant af validatoren og forudsagt som relevant af modellen. Intervallet for scorer for denne metrikværdi er fra **0** til **1**. En score tættere på **1** angiver, at modellen identificerer færre ikke-relevante elementer. Præcisionsmetrikværdien vises på modeldashboardet og på pop op-siden for hver træningsrunde.

## <a name="prediction-score"></a>Forudsigelsesscore

Dette er den score, som en model tildeler til hvert dokument i et korrektursæt. Scoren er baseret på dokumentets relevans sammenlignet med modellens læring fra træningsrunder. Generelt betragtes elementer med forudsigelsesscores mellem **0** og **0,5** ikke som relevante, og elementer med forudsigelsesscores mellem **0,5** og **1** anses for at være relevante. Forudsigelsesresultatet er indeholdt i et dokumentmetadatafelt. Du kan bruge et forudsigelsesfilter til at få vist elementerne i et korrektursæt, der falder inden for et angivet forudsigelsesinterval.

## <a name="recall"></a>Husker

Metrikværdien for tilbagekaldelse måler, hvor stor en del af de elementer, som modellen forudsagde, var relevante blandt elementer, der rent faktisk er relevante. Det betyder, at elementer i kontrolelementsættet, som den forudsagte model var relevante, også er mærket som relevante af korrekturlæseren. Intervallet for scorer for denne metrikværdi er fra **0** til **1**. En score, der er tættere på **1** , angiver, at modellen identificerer en større del af relevante elementer. Metrikværdien for tilbagekaldelse vises på modeldashboardet og på pop op-siden for hver træningsrunde.

## <a name="review-set"></a>Gennemse sæt

Et korrektursæt omfatter omfanget af en forudsigende kodemodel. Når du opretter en ny model for korrektursættet, vælges elementer for kontrolelementsættet og oplæringssæt fra korrektursættet. Når modellen tildeler forudsigelsesscores, tildeles disse scorer elementerne i gennemgangen. Du skal føje alle elementer til korrektursættet, før du opretter en forudsigende kodemodel. Hvis du tilføjer elementer, når du har oprettet en model, tildeles disse elementer ikke en forudsigelsesscore.

## <a name="richness"></a>Rigdom

Metrikværdien richness måler procentdelen af de korrektursætelementer, som modellen forudsiger som relevant. Intervallet for scorer for denne metrikværdi er fra **0** til **1**. Metrikværdien for rigdom vises på modeldashboardet.

## <a name="sampled-items"></a>Eksempler på elementer

Udtrykket *elementer med stikprøver* er en reference til tilfældige eksempler på elementer i et korrektursæt (der indeholder tekst), som er valgt og knyttet til kontrolelementsættet, når du opretter en forudsigende kodemodel. Der vælges også et tilfældigt eksempel på elementer for hver træningsrunde. Elementer, der er valgt for kontrolelementsættet for en model, medtages aldrig i et oplæringssæt for den samme model. Det modsatte er også tilfældet: Elementer i oplæringssæt medtages aldrig i kontrolelementsættet.

## <a name="training-set"></a>Oplæringssæt

Modellen vælger tilfældigt elementer fra korrektursættet og føjer dem til et oplæringssæt. Under en træningsrunde præsenteres elementer fra oplæringssættet (ud over elementer fra kontrolelementsættet), så du kan angive hver enkelt som enten "relevant" eller "ikke relevant". Denne proces til mærkning eller "oplæring" hjælper modellen med at lære, hvordan den forudsiger, hvilke elementer i gennemgangen der er relevante eller ikke relevante. Hver gang du udfører en træningsrunde, vælger modellen flere elementer fra gennemgangen og føjer dem til oplæringssættet for den pågældende træningsrunde. Elementer fra kontrolelementsættet vælges aldrig for et oplæringssæt.
