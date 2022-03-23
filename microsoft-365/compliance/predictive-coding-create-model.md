---
title: Opret en forudsigelig kodningsmodel i Advanced eDiscovery
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
description: Få mere at vide om, hvordan du opretter en forudsigelig kodningsmodel Advanced eDiscovery. Dette er det første trin til at bruge maskinel indlæringsegenskaber i Advanced eDiscovery til at hjælpe dig med at identificere relevant og ikke-relevant indhold i et gennemsynssæt.
ms.openlocfilehash: 4366c5779aaca6973f5a2c0cc526086d0742d069
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593294"
---
# <a name="create-a-predictive-coding-model-preview"></a>Opret en forudsigelig kodningsmodel (forhåndsvisning)

Det første trin til at bruge maskinlæringsegenskaber fra forudsigelig kodning i Advanced eDiscovery at oprette en forudsigelig kodningsmodel. Når du har oprettet en model, kan du træne den til at identificere relevant og ikke-relevant indhold i et korrektursæt.

Hvis du vil gennemse den forudsigelige kodningsarbejdsproces, [skal du se Få mere at vide om forudsigelig kodning Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Før du opretter en model

- Der skal være mindst 2.000 elementer i et korrektursæt for at oprette en forudsigelig kodningsmodel.

- Sørg for at bekræfte alle samlinger i korrektursættet, før du opretter en model. Elementer, der føjes til et korrektursæt, efter modellen er oprettet, behandles ikke og tildeles en forudsigelsesscore, der genereres af modellen.

- Et element i korrektursættet, der ikke indeholder tekst, bliver ikke behandlet af modellen eller tildelt en forudsigelsesscore. Elementer med tekst medtages i kontrolelementet eller et kursussæt.

## <a name="create-a-model"></a>Opret en model

1. I dialogboksen Microsoft 365 Overholdelsescenter du åbne en Advanced eDiscovery en sag og derefter vælge **fanen Gennemse sæt**.

2. Åbn et korrektursæt, og **klik derefter på AnalyticsManage** >  **predictive coding (preview)**.

   ![Klik på rullemenuen Analysér i korrektur indstillet til at gå til siden Forudsigelig kodning.](..\media\ManagePredictiveCoding.png)

3. Klik på **Ny model på siden Forudsigelige kodningsmodeller (****forhåndsvisning**).

4. På pop op-siden skal du skrive et navn til modellen og en valgfri beskrivelse.

5. Du kan også konfigurere avancerede indstillinger (ved at klikke på Avancerede  indstillinger på pop op-siden), der er relateret til tillidsniveauet og fejlmargenen. Disse indstillinger påvirker antallet af elementer i kontrolelementet. *Kontrolsættet bruges* under uddannelsesprocessen til at evaluere de forudsigelsesresultater, som modellen tildeler elementer med den mærkat, du udfører under træningsrundne. Hvis din organisation har retningslinjer for tillidsniveau og fejlmargen til gennemsyn af dokumentet, skal du angive dem i de relevante felter. Ellers skal du bruge standardindstillingerne.

6. Klik **på Gem** for at oprette modellen.

   Det tager et par minutter, før systemet forbereder din model. Når den er klar, kan du udføre den første runde af kurser.

## <a name="what-happens-after-you-create-a-model"></a>Hvad sker der, når du har oprettet en model?

Når du har oprettet en model, sker følgende ting i baggrunden under oprettelsen og klargøringen af modellen:

- Systemet beregner antallet af elementer for kontrolelementsættet. Denne størrelse er baseret på antallet af elementer i korrektursættet og indstillingerne for tillidsniveauet og fejlmargenen. Elementer i kontrolelementsættet vælges tilfældigt og angives som elementer i kontrolelementsættet. Systemet indeholder 10 elementer fra det kontrolelement, der er angivet i den første kursusrunde.

- Systemet vælger tilfældigt 40 elementer fra det korrektursæt, der skal medtages i træningssættet til den første kursusrunde. Derfor indeholder den første runde af kurser 50 elementer til mærkning: 40 elementer fra træningssættet og 10 elementer fra kontrolsættet.

## <a name="next-steps"></a>Næste trin

Når du har oprettet en model til et korrektursæt, udfører næste trin undervisningsrunder for at "lære" modellen at identificere indhold, der er relevant for din undersøgelse. Få mere at vide under [Træn en forudsigelig kodningsmodel](predictive-coding-train-model.md).
