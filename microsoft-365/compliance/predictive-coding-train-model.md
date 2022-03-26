---
title: Træn en forudsigelig kodningsmodel i Advanced eDiscovery
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
ms.openlocfilehash: b5f1a958696dad84ac2bedec8f1ab7d23dfa6428
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63595957"
---
# <a name="train-a-predictive-coding-model-preview"></a>Træn en forudsigelig kodningsmodel (eksempel)

Når du har oprettet en forudsigelig kodningsmodel i Advanced eDiscovery, er næste trin at udføre den første træningsrund for at træne modellen i, hvad der er relevant og ikke-relevant indhold i dit gennemgangssæt. Når du har gennemført den første kursusrunde, kan du udføre efterfølgende træningsrunder for at forbedre modellens mulighed for at forudsige relevant og ikke-relevant indhold.

Hvis du vil gennemse den forudsigelige kodningsarbejdsproces, [skal du se Få mere at vide om forudsigelig kodning Advanced eDiscovery](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Før du oplærer en model

- Under en undervisningsrund kan du **navnmærke elementer** som **Relevante** eller Ikke relevante baseret på indholdets relevans i dokumentet. Du skal ikke basere din beslutning på værdierne i metadatafelterne. For mails eller samtaler med Teams skal du ikke basere beslutningen på mærkater på meddelelsesdeltagerne.

## <a name="train-a-model-for-the-first-time"></a>Træn en model for første gang

1. I dialogboksen Microsoft 365 Overholdelsescenter du åbne en Advanced eDiscovery en sag og derefter vælge **fanen Gennemse sæt**.

2. Åbn et korrektursæt, og **klik derefter på AnalyticsManage** >  **predictive coding (preview)**.

3. På siden **Predictive coding models (preview)** skal du vælge den model, du vil træne.

4. Klik på **Start** næste **træningsrund** under Rund 1 **på fanen Oversigt**.

   Fanen **Kursus** vises og indeholder 50 elementer, du kan navnmærke.

5. Gennemse hvert dokument, og vælg derefter **knappen Relevant** **eller Ikke relevant** nederst i læseruden for at navnmærke det.

   ![Giv hvert dokument en mærkat som relevant eller ikke relevant.](..\media\TrainModel1.png)

6. Når du har markeret alle 50 elementer, skal du klikke på **Udfør**.

    Det tager et par minutter, før systemet "lærer" af din mærkning og opdaterer modellen. Når denne proces er fuldført, vises status som  Klar for modellen på siden **Forudsigelig kodningsmodeller (forhåndsvisning**).

## <a name="perform-additional-training-rounds"></a>Udfør flere træningsrunder

Når du har den første kursusrunde, kan du udføre efterfølgende træningsrunder ved at følge trinnene i forrige afsnit. Den eneste forskel er nummeret på træningsrunden, som opdateres på fanen Oversigt **over** model. Når du f.eks. har udført den første træningsrund, kan du klikke på **Start** næste træningsrund for at starte den anden kursusrunde. Og så videre.

Hver runde af kurser (både dem, der er i gang, og dem, der er fuldførte), vises på **fanen** Kursus for modellen. Når du vælger en undervisningsrund, vises en pop op-side med oplysninger og målepunkter for afrunding.

## <a name="what-happens-after-you-perform-a-training-round"></a>Hvad sker der, når du udfører en træningsrund?

Når du har den første træningsrund, startes der et job, som gør følgende:

- Baseret på, hvordan du har mærket de 40 elementer i træningssættet, lærer modellen ud fra selve etiketterne og opdateres, så den bliver mere præcis.

- Modellen behandler derefter hvert element i hele korrektursættet og tildeler en forudsigelsesscore mellem **0** (ikke relevant) og **1** (relevant).

- Modellen tildeler et forudsigelsesresultat til de 10 elementer i det kontrolelement, du navnerede under træningsrunden. Modellen sammenligner forudsigelsen for disse 10 elementer med den faktiske etiket, du har tildelt til elementet under træningsrunden. Baseret på denne sammenligning identificerer modellen følgende klassificering (kaldet matrixen for kontrolsætforvirring) for at vurdere modellens forudsigelsesydeevne:

  <br>

  ****

  |Etiket|Model forudsiger, at elementet er relevant|Model forudsiger, at element ikke er relevant|
  |---|---|---|
  |**Elementet korrekturlæseretiketter som relevante**|Sand positiv|Falsk positiv|
  |**Elementet korrekturlæseretiketter er ikke relevante**|Falsk negativ|Sand negativ|
  |

  Baseret på disse sammenligninger udleder modellen værdier for F-score, præcision og tilbagekaldelse af målepunkter og fejlmargenen for hver enkelt. Resultater for disse målepunkter for modellens ydeevne vises på en pop op-side for træningsrunden. Du kan finde en beskrivelse af disse målepunkter [under Reference til forudsigelig kodning](predictive-coding-reference.md).

- Endelig bestemmer modellen de næste 50 elementer, der skal bruges til den næste træningsrund. Denne gang kan modellen vælge 20 elementer i kontrolsættet og 30 nye elementer fra korrektursættet og udpege dem som træningssættet til den næste runde. Stikprøven for den næste kursusrunde prøves ikke ensartet. Modellen optimerer stikprøveudvælgelsen af elementer fra korrektursættet for at vælge elementer, hvor prognosen er tvetydig, hvilket betyder, at forudsigelsen ligger i området 0,5. Denne proces kaldes *for valg af område*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Hvad sker der, når du har efterfølgende træningsrunder

Når du har efterfølgende træningsrunder (efter den første træningsrund), gør modellen følgende:

- Modellen opdateres på baggrund af de etiketter, du har anvendt på træningssættet i den pågældende kursusrunde.

- Systemet evaluerer modellens forudsigelsesresultat på elementerne i kontrolelementet og kontrollerer, om scoren er justeret efter, hvordan du har mærket elementer i kontrolelementet. Evalueringen udføres på alle markerede elementer fra kontrolelementsættet for alle træningsrunder. Resultaterne af denne evaluering integreres i dashboardet på **fanen** Oversigt for modellen.

- Den opdaterede model genbehandler alle elementer i korrektursættet og tildeler hvert element et opdateret forudsigelsesresultat.

## <a name="next-steps"></a>Næste trin

Når du udfører den første træningsrund, kan du udføre flere træningsrunder eller anvende modellens forudsigelsesscorefilter på korrektursættet for at få vist de elementer, modellen har forudsagt som relevante eller ikke relevante. Få mere at vide under [Anvend et forudsigelsesscorefilter på et korrektursæt](predictive-coding-apply-prediction-filter.md).
