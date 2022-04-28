---
title: Forudsigende kodning i eDiscovery (Premium) – Hurtig start
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Få mere at vide om, hvordan du kommer i gang med at bruge modulet med forudsigende kodning i eDiscovery (Premium). I denne artikel gennemgår vi processen fra ende til anden med at bruge forudsigende kodning til at identificere indhold i et anmeldelsessæt, der er mest relevant for din undersøgelse.
ms.openlocfilehash: ac8e31540fbe817b83b5fd0bdae2fadea7040b1a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100781"
---
# <a name="quick-start-predictive-coding-in-ediscovery-premium-preview"></a>Hurtig start: Forudsigende kode i eDiscovery (Premium) (prøveversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel præsenteres en hurtig start til brug af forudsigende kode i Microsoft Purview eDiscovery (Premium). I modulet til forudsigelse af kodning bruges intelligente funktioner til maskinel indlæring til at hjælpe dig med at slå store mængder sagsindhold fra, der ikke er relevant for din undersøgelse. Dette opnås ved at oprette og oplære dine egne forudsigende kodemodeller, der hjælper dig med at prioritere de mest relevante elementer til gennemsyn.

Her er et hurtigt overblik over den forudsigende kodningsproces:

![Hurtig start-processen til forudsigelseskodning.](..\media\PredictiveCodingQuickStartProcess.png)

For at komme i gang skal du oprette en model med så få som 50 elementer som relevante eller ikke relevante. Systemet bruger derefter denne oplæring til at anvende forudsigelsesscores på alle elementer i korrektursættet. Det giver dig mulighed for at filtrere elementer baseret på forudsigelsesscoren, hvilket giver dig mulighed for først at gennemse de mest relevante (eller ikke-relevante) elementer. Hvis du vil oplære modeller med højere tilgængeligheds- og genkaldelsesrater, kan du fortsætte med at mærke elementer i efterfølgende træningsrunder, indtil modellen stabiliseres. Når modellen er stabiliseret, kan du anvende det endelige forudsigelsesfilter til at prioritere elementer, der skal gennemses.

Du kan finde en detaljeret oversigt over forudsigende kodning [under Få mere at vide om forudsigende kodning i eDiscovery (Premium)](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>Trin 1: Opret en ny forudsigende kodemodel

Det første trin er at oprette en ny forudsigende kodemodel i korrektursættet

1. Åbn en eDiscovery-sag (Premium) på Microsoft Purview-overholdelsesportalen, og vælg derefter fanen **Gennemse sæt**.

2. Åbn et korrektursæt, og klik derefter på **AnalyticsAdministrer forudsigende kodning (prøveversion)**. > 

   ![Klik på rullemenuen Analysér i gennemgangssættet for at gå til siden Forudsigende kodning.](..\media\ManagePredictiveCoding.png)

3. Klik på **Ny model** på siden **Forudsigende kodningsmodeller (prøveversion).**

4. Skriv et navn til modellen og en valgfri beskrivelse på pop op-siden.

5. Klik på **Gem** for at oprette modellen.

   Det tager et par minutter, før systemet klargør din model. Når den er klar, kan du udføre den første runde af træningen.

Du kan finde mere detaljerede instruktioner under [Opret en forudsigende kodemodel](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>Trin 2: Udfør den første træningsrunde

Når du har oprettet modellen, er det næste trin at gennemføre den første oplæringsrunde ved at angive elementer som relevante eller ikke relevante.

1. Åbn korrektursættet, og klik derefter på **AnalyticsAdministrer forudsigende kode (prøveversion).**. > 

2. På siden **Forudsigende kodningsmodeller (prøveversion)** skal du vælge den model, du vil oplære.

3. Klik på **Start næste træningsrunde** under **Runde 1** under fanen **Oversigt**.

   Fanen **Oplæring** vises og indeholder 50 elementer, som du kan navngive.

4. Gennemse hvert dokument, og vælg derefter knappen **Relevant** eller **Ikke relevant** nederst i læseruden for at navngive det.

   ![Mærk hvert dokument som relevant eller ikke relevant.](..\media\TrainModel1.png)

5. Når du har markeret alle 50 elementer, skal du klikke på **Udfør**.

    Det tager et par minutter, før systemet "lærer" fra din mærkning og opdaterer modellen. Når processen er fuldført, vises statussen **Ready** for modellen på siden **Predictive coding models (prøveversion).**

Du kan finde mere detaljerede instruktioner under [Oplær en forudsigende kodemodel](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Trin 3: Anvend filteret for forudsigelsesscore på elementer i korrektursæt

Når du har udført leasing én træningsrunde, kan du anvende forudsigelsesscorefilteret på elementer i korrektursæt. Dette giver dig mulighed for at gennemse de elementer, som modellen har forudsagt som relevante eller ikke relevante.   

1. Åbn korrektursættet.

   ![Klik på Filtre for at få vist pop op-siden Filtre.](..\media\PredictionScoreFilter0.png)

   De forudindlæste standardfiltre vises øverst på siden med korrektursæt. Du kan lade disse være angivet til **Enhver**.

2. Klik på **Filtre** for at få vist pop op-siden **Filtre** .

3. Udvid afsnittet **Analyse & forudsigende kodning** for at få vist et sæt filtre.

      ![Filter for forudsigelsesscore i afsnittet Analyse & forudsigende kodning.](..\media\PredictionScoreFilter1.png)

   Navngivningskonventionen for filtre for forudsigelsesscore er **Forudsigelsesscore (modelnavn)**. Filternavnet for forudsigelsesscoren for en model med navnet **Model A** er f.eks. **Forudsigelsesscore (Model A)**.

4. Vælg det filter for forudsigelsesscore, du vil bruge, og klik derefter på **Udført**.

5. På siden med korrektursæt skal du klikke på rullelisten for filteret for forudsigelsesscore og skrive minimum- og maksimumværdier for forudsigelsesresultatintervallet. Følgende skærmbillede viser f.eks. et forudsigelsesscoreinterval mellem **.5** og **1.0**.

   ![Minimum- og maksimumværdier for filteret for forudsigelsesscore.](..\media\PredictionScoreFilter2.png)

6. Klik uden for filteret for automatisk at anvende filteret på korrektursættet.

  En liste over dokumenter med en forudsigelsesscore inden for det angivne område vises på siden med korrektursæt.

Du kan finde flere detaljerede instruktioner under [Anvend et forudsigelsesfilter på et korrektursæt](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>Trin 4: Udfør flere træningsrunder

Det er mere end sandsynligt, at du skal udføre flere oplæringsrunder for at oplære modulet for bedre at forudsige relevante og ikke-relevante elementer i korrektursættet. Generelt skal du oplære modellen nok gange, indtil den stabiliserer nok til at opfylde dine krav.

Du kan finde flere oplysninger under [Udfør yderligere træningsrunder](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Trin 5: Anvend det endelige filter til forudsigelsesscore for at prioritere gennemgangen

Gentag instruktionerne i trin 3 for at anvende den endelige forudsigelsesscore på gennemgangssættet for at prioritere gennemgangen af relevante og ikke-relevante elementer, når du har fuldført alle oplæringsrunder og stabiliseret modellen.
