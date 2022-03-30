---
title: Forudsigelig kodningsreference
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
ms.openlocfilehash: ff681793a86d9953088c2c4da65553e1d2c54d22
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63599431"
---
# <a name="predictive-coding-reference-preview"></a>Forudsigelig kodningsreference (eksempel)

I denne artikel beskrives nøglekoncepterne og målepunkter for forudsigelig kodningsværktøjet i Advanced eDiscovery. Afsnittene i artiklen er angivet i alfabetisk rækkefølge.

## <a name="confidence-level"></a>Tillidsniveau

Tillidsniveauet er en avanceret indstilling, når du opretter en forudsigelig kodningsmodel. Den definerer, at modellens målepunkter for ydeevne (f.eks. udvidede værdier, præcision og tilbagekaldelse) falder inden for et angivet interval (som har fastlagt den fejlmargen, der er defineret for modellen), som er repræsentativ for de sande værdier i prognosen, giver modellen karakterer for elementer i korrektursættet. Værdierne for tillidsniveauet og fejlmargenen hjælper også med at afgøre, hvor mange elementer, der medtages i kontrolelementsættet. Standardværdien for tillidsniveauet er 0,95 eller 95 %.

## <a name="control-set"></a>Kontrolelementsæt

Et kontrolsæt bruges under undervisningsprocessen af en forudsigelig kodningsmodel. Kontrolelementsættet er at evaluere forudsigelsesresultater, som modellen tildeler elementer med den mærkat, du udfører under træningsrunder. Størrelsen på kontrolelementsættet er baseret på antallet af elementer i korrektursættet og tillidsniveauet og margenen for fejlværdier, der er angivet ved oprettelse af modellen. Elementer i kontrolelementsættet ændres aldrig og kan ikke identificeres af brugerne. Det samlede antal elementer i kontrolelementet vises på pop op-siden for en træningsrund.

## <a name="control-set-confusion-matrix"></a>Matrix med kontrolsætforvirring

Når du har fuldført en træningsrund, tildeler modellen en forudsigelsesscore på de 10 elementer i det kontrolelement, du navnerede under træningsrunden. Modellen sammenligner forudsigelsen for disse 10 elementer med den faktiske etiket, du har tildelt til elementet under træningsrunden. Baseret på denne sammenligning identificerer modellen følgende klassificeringer for at vurdere modellens forudsigelsesydeevne:

<br>

****

|Etiket|Model forudsiger, at elementet er relevant|Model forudsiger, at element ikke er relevant|
|---|---|---|
|**Elementet korrekturlæseretiketter som relevante**|Sand positiv|Falsk positiv|
|**Elementet korrekturlæseretiketter er ikke relevante**|Falsk negativ|Sand negativ|
|

Baseret på disse sammenligninger udleder modellen værdier for F-score, præcision og tilbagekaldelse af målepunkter og fejlmargenen for hver enkelt. Antallet af hver af forvirringstyperne i matrixen vises på pop op-siden for en kursusrunde.

## <a name="f-score"></a>F-score

F-scoren er et vægtet gennemsnit af pointværdierne for præcisionen og tilbagekaldelsen af målepunkter.  Intervallerne for denne metrik er fra **0** til **1**. En score tættere på **1 angiver** , at modellen mere nøjagtigt registrerer relevante elementer. F-score-metrikværdien vises på modeldashboardet og på pop op-siden for hver træningsrund.

## <a name="margin-of-error"></a>Fejlmargen

Fejlmargenen er en avanceret indstilling, når du opretter en forudsigelig kodningstilstand. Den angiver antal fejl i målepunkter for ydeevnen (f.eks. udvidede værdier, præcision og tilbagekaldelse), der er afledt af det tilfældige udvalg af elementer i dit kontrolelementsæt. En lavere fejlmargen kræver et større kontrolsæt for at sikre, at modellens målepunkter for ydeevne falder inden for et mindre område. Værdierne for fejlmargenen og tillidsniveauet hjælper også med at afgøre, hvor mange elementer, der medtages i kontrolelementsættet. Standardværdien for fejlmargenen er 0,05 eller 5 %.

## <a name="model-stability"></a>Modelstabilitet

Modelstabilitet angiver modellens mulighed for nøjagtigt at forudsige, om et dokument i et korrektursæt er relevant eller ej. Når en model er ustabil, skal der muligvis udføres flere træningsrunder for at medtage modellens stabilitet. Når modellen er stabil, skal der muligvis ikke udføres flere træningsrunder. Modeldashboardet angiver den aktuelle tilstand af modellens stabilitet. Når en model er stabil, har målepunkter for ydeevnen nået et niveau, der svarer til indstillingerne for tillidsniveau og fejlmargen.

## <a name="overturn-rate"></a>Overtælt rente

Overturssatsen er procentdelen af elementer i korrektursættet, hvor forudsigelsesresultatet blev ændret mellem træningsrundne. En model betragtes som stabil, når overturssatsen er mindre end 5 %. Metrikværdien for overvæltningen vises på dashboardet model og på pop op-siden for hver træningsrund. Overtrundingsprocenten for den første træningsrund er nul, fordi der ikke er en tidligere forudsigelsesscore at tilsidesætte.

## <a name="precision"></a>Præcision

Præcisionsmåleværdien måler forholdet mellem elementer, der faktisk er relevante blandt de elementer, som den forudsagte model var relevante. Det betyder, at elementerne i kontrolelementsættet, hvor etiketten er relevant for korrekturlæseren og forudsagt som relevant af modellen. Intervallerne for denne metrik er fra **0** til **1**. Et resultat tættere på **1** angiver, at modellen identificerer færre ikke-relevante elementer. Præcisionsmåleværdien vises på modeldashboardet og på pop op-siden for hver træningsrund.

## <a name="prediction-score"></a>Forudsigelsesscore

Dette er det resultat, som en model tildeler til hvert dokument i et korrektursæt. Resultatet er baseret på dokumentets relevans sammenlignet med modellæring fra træningsrundne. Generelt betragtes elementer med forudsigelsesresultater mellem **0** og **0,5** ikke som relevante, og elementer med forudsigelsesresultater mellem **0,5** og **1** betragtes som relevante. Forudsigelsesresultatet er indeholdt i et dokuments metadatafelt. Du kan bruge et forudsigelsesfilter til at vise elementerne i et korrektursæt, der falder inden for et angivet forudsigelsesområde.

## <a name="recall"></a>Tilbagekaldelse

Tilbagekaldelsesmålet måler forholdet mellem elementer, som den forudsagte model var relevante blandt elementer, der faktisk er relevante. Det betyder, at elementer i det kontrolsæt, som den forudsagte model var relevante, også blev mærket som relevante af korrekturlæseren. Intervallerne for denne metrik er fra **0** til **1**. En score tættere på **1 angiver** , at modellen vil identificere en større del af relevante elementer. Tilbagekaldelsesmåleværdien vises på modeldashboardet og på pop op-siden for hver træningsrund.

## <a name="review-set"></a>Gennemse sæt

Et korrektursæt angiver omfanget af en forudsigelig kodningsmodel. Når du opretter en ny model til korrektursættet, vælges elementer til kontrolelementsættet og kursussæt i korrektursættet. Når modellen tildeler prognoseresultater, tildeles disse karakterer elementer i anmeldelsen. Du skal føje alle elementer til korrektursættet, før du opretter en forudsigelig kodningsmodel. Hvis du tilføjer elementer, efter du har oprettet en model, tildeles disse elementer ikke et forudsigelsesresultat.

## <a name="richness"></a>Richness

Den udvidede metriske værdi måler procentdelen af revisionssætelementer, som modellen forudsiger som relevante. Intervallerne for denne metrik er fra **0** til **1**. Richness-metrikværdien vises på modeldashboardet.

## <a name="sampled-items"></a>Eksempelelementer

Ordet *eksempelelementer* er en reference til tilfældige stikprøver af elementer i et korrektursæt (der indeholder tekst), der er markeret og knyttet til kontrolelementet, når du opretter en forudsigelig kodningsmodel. Der vælges også et tilfældigt udsnit af elementer for hver træningsrund. De elementer, der er valgt til kontrolelementsættet i en model, medtages aldrig i et kursussæt for den samme model. Det omvendte er også tilfældet: Kursussætelementer medtages aldrig i kontrolelementsættet.

## <a name="training-set"></a>Kursussæt

Modellen vælger tilfældigt elementer fra korrektursættet og føjer dem til et kursussæt. Under en træningsrund vises elementer fra træningssættet (ud over elementer fra kontrolelementsættet), så du kan navnmærke hver enkelt af dem som enten "relevant" eller "ikke relevant". Denne etiketproces eller "kursus"-proces hjælper modellen med at lære, hvordan man kan forudsige, hvilke elementer i anmeldelsen, der er relevante eller ikke relevante. Hver gang du udfører en træningsrund, vælger modellen flere elementer fra anmeldelsen og føjer dem til træningssættet for den pågældende træningsrund. Elementer fra kontrolelementsættet vælges aldrig for et kursussæt.
