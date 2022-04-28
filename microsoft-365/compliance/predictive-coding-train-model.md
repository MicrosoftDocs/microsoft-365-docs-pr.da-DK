---
title: Oplær en forudsigende kodemodel i eDiscovery (Premium)
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
description: ''
ms.openlocfilehash: 1f94f49f93310ea4b40d588c7c43ecce7ec535cc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091451"
---
# <a name="train-a-predictive-coding-model-preview"></a>Oplær en forudsigende kodemodel (prøveversion)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har oprettet en forudsigende kodemodel i Microsoft Purview eDiscovery (Premium), er det næste trin at udføre den første oplæringsrunde for at oplære modellen i, hvad der er relevant og ikke-relevant indhold i dit anmeldelsessæt. Når du har fuldført den første træningsrunde, kan du udføre efterfølgende oplæringsrunder for at forbedre modellens evne til at forudsige relevant og ikke-relevant indhold.

Hvis du vil gennemse arbejdsprocessen for forudsigende kodning, skal du se [Få mere at vide om forudsigende kodning i eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-train-a-model"></a>Før du oplærer en model

- Under en træningsrunde skal du markere elementer som **Relevante** eller **Ikke relevante** , afhængigt af relevansen af indholdet i dokumentet. Du skal ikke basere din beslutning på værdierne i metadatafelterne. For mails eller Teams samtaler skal du f.eks. ikke basere din beslutning om mærkat på deltagerne i meddelelsen.

## <a name="train-a-model-for-the-first-time"></a>Oplær en model første gang

1. Åbn en eDiscovery-sag (Premium) på Microsoft Purview-overholdelsesportalen, og vælg derefter fanen **Gennemse sæt**.

2. Åbn et korrektursæt, og klik derefter på **AnalyticsAdministrer forudsigende kodning (prøveversion)**. > 

3. På siden **Forudsigende kodningsmodeller (prøveversion)** skal du vælge den model, du vil oplære.

4. Klik på **Start næste træningsrunde** under **Runde 1** under fanen **Oversigt**.

   Fanen **Oplæring** vises og indeholder 50 elementer, som du kan navngive.

5. Gennemse hvert dokument, og vælg derefter knappen **Relevant** eller **Ikke relevant** nederst i læseruden for at navngive det.

   ![Mærk hvert dokument som relevant eller ikke relevant.](..\media\TrainModel1.png)

6. Når du har markeret alle 50 elementer, skal du klikke på **Udfør**.

    Det tager et par minutter, før systemet "lærer" fra din mærkning og opdaterer modellen. Når processen er fuldført, vises statussen **Ready** for modellen på siden **Predictive coding models (prøveversion).**

## <a name="perform-additional-training-rounds"></a>Udfør yderligere træningsrunder

Når du har udført den første træningsrunde, kan du udføre efterfølgende træningsrunder ved at følge trinnene i forrige afsnit. Den eneste forskel er, at antallet af træningsrunden opdateres under fanen **Oversigt for** modellen. Når du f.eks. har udført den første træningsrunde, kan du klikke på **Start næste træningsrunde** for at starte den anden træningsrunde. Og så videre.

Hver træningsrunde (både dem, der er i gang, og dem, der er i gang) vises under fanen **Oplæring** for modellen. Når du vælger en træningsrunde, vises der en pop op-side med oplysninger og målepunkter for runden.

## <a name="what-happens-after-you-perform-a-training-round"></a>Hvad sker der, når du har gennemført en træningsrunde?

Når du har udført den første oplæringsrunde, startes et job, der gør følgende:

- Baseret på hvordan du mærkede de 40 elementer i oplæringssættet, lærer modellen af din mærkning og opdaterer sig selv for at blive mere præcis.

- Modellen behandler derefter hvert element i hele korrektursættet og tildeler en forudsigelsesscore mellem **0** (ikke relevant) og **1** (relevant).

- Modellen tildeler en forudsigelsesscore til de 10 elementer i kontrolelementsættet, som du mærkede under oplæringsrunden. Modellen sammenligner forudsigelsesscoren for disse 10 elementer med den faktiske mærkat, som du tildelte elementet under oplæringsrunden. Baseret på denne sammenligning identificerer modellen følgende klassificering (kaldet *forvirringsmatrixen Kontrolelementsæt*) for at vurdere modellens forudsigelsesydeevne:

  <br>

  ****

  |Etiket|Elementet Forudsig model er relevant|Elementet forudsagt af modellen er ikke relevant|
  |---|---|---|
  |**Elementet med korrekturlæsermærkater er relevant**|Sand positiv|Falsk positiv|
  |**Elementet for korrekturlæsermærkater er ikke relevant**|Falsk negativ|Sand negativ|
  |

  Baseret på disse sammenligninger får modellen værdier for F-score, præcision og genkaldelsesmetrik og fejlmargenen for hver enkelt. Scorer for disse målepunkter for modellens ydeevne vises på en pop op-side for træningsrunden. Du kan finde en beskrivelse af disse målepunkter under [Reference til forudsigende kodning](predictive-coding-reference.md).

- Til sidst bestemmer modellen de næste 50 elementer, der skal bruges til den næste træningsrunde. Denne gang kan modellen vælge 20 elementer fra kontrolelementsættet og 30 nye elementer fra korrektursættet og angive dem som oplæringssæt for den næste runde. Stikprøvetagningen af den næste træningsrunde foretages ikke på en ensartet måde. Modellen optimerer valg af stikprøvetagning af elementer fra korrektursættet for at vælge elementer, hvor forudsigelsen er tvetydig, hvilket betyder, at forudsigelsesscoren er i intervallet 0,5. Denne proces kaldes *forudindtaget markering*.

### <a name="what-happens-after-you-perform-subsequent-training-rounds"></a>Hvad sker der, når du har gennemført efterfølgende træningsrunder?

Når du har udført efterfølgende træningsrunder (efter den første træningsrunde), gør modellen følgende:

- Modellen opdateres på baggrund af de mærkater, du anvendte på oplæringssættet i den pågældende træningsrunde.

- Systemet evaluerer modellens forudsigelsesscore for elementerne i kontrolelementsættet og kontrollerer, om scoren stemmer overens med den måde, du mærkede elementer i kontrolelementsættet på. Evalueringen udføres på alle navngivne elementer fra kontrolelementsættet for alle oplæringsrunder. Resultaterne af denne evaluering inkorporeres i dashboardet under fanen **Oversigt** for modellen.

- Den opdaterede model genbehandler hvert element i korrektursættet og tildeler hvert element en opdateret forudsigelsesscore.

## <a name="next-steps"></a>Næste trin

Når du har udført den første oplæringsrunde, kan du udføre flere oplæringsrunder eller anvende modellens forudsigelsesscorefilter på korrektursættet for at få vist de elementer, som modellen har forudsagt som relevante eller ikke relevante. Du kan finde flere oplysninger under [Anvend et filter for forudsigelsesscore på et korrektursæt](predictive-coding-apply-prediction-filter.md).
