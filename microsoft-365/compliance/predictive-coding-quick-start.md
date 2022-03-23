---
title: Forudsigelig kodning i Advanced eDiscovery – Hurtig start
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
description: Få mere at vide om, hvordan du kommer i gang med at bruge forudsigelig kodningsmodulet Advanced eDiscovery. I denne artikel gennemgås hele processen med at bruge forudsigelig kodning til at identificere indhold i et korrektursæt, der er mest relevant for din undersøgelse.
ms.openlocfilehash: 2266f44e7b95c118314d76fe019a97b2db24f07c
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63593293"
---
# <a name="quick-start-predictive-coding-in-advanced-ediscovery-preview"></a>Hurtig start: Forudsigelig kodning i Advanced eDiscovery (eksempel)

Denne artikel giver en hurtig start på brugen af forudsigelig kodning i Advanced eDiscovery. Forudsigeligt kodningsmodul bruger intelligente maskinlæringsfunktioner til at hjælpe dig med at cullere store mængder sagsindhold, der ikke er relevant for din undersøgelse. Dette opnås ved at oprette og træne dine egne forudsigelige kodningsmodeller, der hjælper dig med at prioritere de mest relevante elementer til gennemsyn.

Her er en hurtig oversigt over forudsigelig kodningsprocessen:

![Hurtig start-proces til forudsigelseskodning.](..\media\PredictiveCodingQuickStartProcess.png)

For at komme i gang skal du oprette en model med et navn på så få som 50 elementer, som relevante eller ikke er relevante. Systemet anvender derefter dette kursus til at anvende forudsigelsesresultater for hvert element i korrektursættet. Dette gør det muligt at filtrere elementer baseret på forudsigelsesresultatet, hvilket giver dig mulighed for at gennemse de mest relevante (eller ikke-relevante) elementer først. Hvis du vil træne modeller med højere inaktler og tilbagekaldelseshastigheder, kan du fortsætte med at navnmærke elementer i efterfølgende træningsrunder, indtil modellen er stabil. Når modellen er stabil, kan du anvende det endelige forudsigelsesfilter til at prioritere elementer til gennemsyn.

Du kan få en detaljeret oversigt over forudsigelig kodning [under Få mere at vide om forudsigelig kodning Advanced eDiscovery](predictive-coding-overview.md).

## <a name="step-1-create-a-new-predictive-coding-model"></a>Trin 1: Opret en ny forudsigelig kodningsmodel

Det første trin er at oprette en ny forudsigelig kodningsmodel i revisionssættet

1. I dialogboksen Microsoft 365 Overholdelsescenter du åbne en Advanced eDiscovery en sag og derefter vælge **fanen Gennemse sæt**.

2. Åbn et korrektursæt, og **klik derefter på AnalyticsManage** >  **predictive coding (preview)**.

   ![Klik på rullemenuen Analysér i korrektur indstillet til at gå til siden Forudsigelig kodning.](..\media\ManagePredictiveCoding.png)

3. Klik på **Ny model på siden Forudsigelige kodningsmodeller (****forhåndsvisning**).

4. På pop op-siden skal du skrive et navn til modellen og en valgfri beskrivelse.

5. Klik **på Gem** for at oprette modellen.

   Det tager et par minutter, før systemet forbereder din model. Når den er klar, kan du udføre den første runde af kurser.

Du kan finde en mere detaljeret vejledning [under Opret en forudsigelig kodningsmodel](predictive-coding-create-model.md).

## <a name="step-2-perform-the-first-training-round"></a>Trin 2: Udfør den første træningsrund

Når du har oprettet modellen, er næste trin at fuldføre den første træningsrund ved at navnmærke elementer som relevante eller ikke relevante.

1. Åbn korrektursættet, og klik **derefter på AnalyticsManage** >  **predictive coding (preview)**.

2. På siden **Predictive coding models (preview)** skal du vælge den model, du vil træne.

3. Klik på **Start** næste **træningsrund** under Rund 1 **på fanen Oversigt**.

   Fanen **Kursus** vises og indeholder 50 elementer, du kan navnmærke.

4. Gennemse hvert dokument, og vælg derefter **knappen Relevant** **eller Ikke relevant** nederst i læseruden for at navnmærke det.

   ![Giv hvert dokument en mærkat som relevant eller ikke relevant.](..\media\TrainModel1.png)

5. Når du har markeret alle 50 elementer, skal du klikke på **Udfør**.

    Det tager et par minutter, før systemet "lærer" af din mærkning og opdaterer modellen. Når denne proces er fuldført, vises status som  Klar for modellen på siden **Forudsigelig kodningsmodeller (forhåndsvisning**).

Du kan finde en mere detaljeret vejledning [under Træn en forudsigelig kodningsmodel](predictive-coding-train-model.md).

## <a name="step-3-apply-the-prediction-score-filter-to-items-in-review-set"></a>Trin 3: Anvende forudsigelsesscorefilteret på elementer i korrektursæt

Når du har leaset én træningsrund, kan du anvende forudsigelsesscorefilteret på elementer i gennemsynssættet. Dette giver dig mulighed for at gennemse de elementer, modellen har forudsagt, som relevante eller ikke relevante.   

1. Åbn korrektursættet.

   ![Klik på Filtre for at få vist pop op-siden Filtre.](..\media\PredictionScoreFilter0.png)

   De forudindlæste standardfiltre vises øverst på siden med korrektursæt. Du kan lade disse være indstillet **til Enhver**.

2. Klik **på Filtre** for at få **vist pop** op-siden Filtre.

3. Udvid **sektionen Analytics & forudsigelig kodning** for at få vist et sæt filtre.

      ![Forudsigelsesscorefilter i & med forudsigelig kodning.](..\media\PredictionScoreFilter1.png)

   Navngivningskonventionen for forudsigelsesscorefiltre **er Forudsigelsesscore (modelnavn)**. For eksempel er navnet på forudsigelsesscore filteret for en model med navnet **Model A** **Forudsigelsesscore (Model A)**.

4. Vælg det forudsigelsesscorefilter, du vil bruge, og klik derefter på **Udført**.

5. På siden med korrektursæt skal du klikke på rullemenuen for forudsigelsesscorefilteret og skrive minimum- og maksimumværdier for prognoseresultatet. Følgende skærmbillede viser f.eks. et forudsigelsesresultatinterval mellem **0,5** og **1,0**.

   ![Minimum- og maksimumværdier for forudsigelsesscorefilteret.](..\media\PredictionScoreFilter2.png)

6. Klik uden for filteret for automatisk at anvende filteret på korrektursættet.

  En liste over dokumenter med et forudsigelsesresultat inden for det område, du har angivet, vises på siden med korrektursæt.

Du kan finde en mere detaljeret vejledning under [Anvende et forudsigelsesfilter på et korrektursæt](predictive-coding-apply-prediction-filter.md).

## <a name="step-4-perform-more-training-rounds"></a>Trin 4: Udfør flere træningsrunder

Det er mere end sandsynligt, at du er nødt til at udføre flere træningsrunder for at træne modulet til bedre at forudsige relevante og ikke-relevante elementer i korrektursættet. Generelt skal du træne modellen nok gange, indtil den er stabil nok til at opfylde dine krav.

Få mere at vide under [Udfør flere træningsrunder](predictive-coding-train-model.md#perform-additional-training-rounds)

## <a name="step-5-apply-the-final-prediction-score-filter-to-prioritize-review"></a>Trin 5: Anvend det endelige forudsigelsesresultatfilter for at prioritere gennemsyn

Gentag vejledningen i trin 3 for at anvende den endelige forudsigelse på korrektursættet for at prioritere gennemgangen af relevante og ikke-relevante elementer, når du har fuldført alle træningsrundne og har stabilt modellen.
