---
title: Anvend filteret med forudsigelsesresultatet på et korrektursæt
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
description: Brug et filter til forudsigelsesscore til at vise elementer, som en forudsigende kodningsmodel er forudsagt som relevant eller ikke relevant.
ms.openlocfilehash: 64abac8b9f53baa9afb869d77296089544919fea
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096606"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Anvend et filter for forudsigelsesscore på et korrektursæt (eksempelvisning)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har oprettet en forudsigende kodemodel i Microsoft Purview eDiscovery (Premium) og oplært den til det punkt, hvor den er stabil, kan du anvende filteret til forudsigelsesscore til at vise elementer, som modellen har angivet er relevante (eller ikke relevante). Når du opretter en model, oprettes der også et tilsvarende filter for forudsigelsesscore. Du kan bruge dette filter til at få vist elementer, der er tildelt en forudsigelsesscore inden for et angivet område. Generelt tildeles forudsigelsesscore mellem **0** og **0,5** elementer, som modellen har forudsagt, ikke relevante. Elementer, der er tildelt forudsigelsesscores mellem **.5** og **1.0** , er elementer, som modellen har forudsagt, er relevante.

Her er to måder, du kan bruge filteret for forudsigelsesscore på:

- Prioriter gennemgangen af elementer i et korrektursæt, som modellen har forudsagt er relevante.

- Elementer til udsætning fra det korrektursæt, som modellen har forudsagt, er ikke relevante. Alternativt kan du bruge filteret for forudsigelsesscore til at fraprioritere gennemgangen af ikke-relevante elementer.

## <a name="before-you-apply-a-prediction-score-filter"></a>Før du anvender et filter til forudsigelsesscore

- Opret en forudsigende kodemodel, så der oprettes et tilsvarende filter for forudsigelsesscore.

- Du kan anvende et filter for forudsigelsesscore efter en af oplæringsrunderene. Det kan dog være en god idé at vente, når du har udført flere runder, eller indtil modellen er stabil, før du bruger filteret for forudsigelsesscore.

## <a name="apply-a-prediction-score-filter"></a>Anvend et filter til forudsigelsesscore

1. Åbn eDiscovery-sagen (Premium) på Microsoft Purview-overholdelsesportalen, vælg fanen **Gennemse sæt**, og åbn derefter korrektursættet.

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

  > [!TIP]
  > Hvis du vil have vist den faktiske forudsigelsesscore, der er tildelt et dokument, kan du klikke på fanen **Metadata** i læseruden. Forudsigelsesscorerne for alle modeller i korrektursættet vises i egenskaben **Relevansscores-metadata** .

## <a name="more-information"></a>Flere oplysninger

- Du kan få flere oplysninger om brug af filtre under [Forespørg om og filtrer indhold i et anmeldelsessæt](review-set-search.md).
