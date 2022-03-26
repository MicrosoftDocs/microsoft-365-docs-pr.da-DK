---
title: Anvende forudsigelsesscorefilteret på elementer i et korrektursæt
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
description: Brug et forudsigelsesscorefilter til at vise elementer, som en forudsigelig kodningsmodel som forventet relevant eller ikke relevant.
ms.openlocfilehash: 04d0881e36c28a70df58a1aa7b054c641dfeeb2a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63595955"
---
# <a name="apply-a-prediction-score-filter-to-a-review-set-preview"></a>Anvende et forudsigelsesscorefilter på et korrektursæt (forhåndsvisning)

Når du har oprettet en forudsigelig kodningsmodel i Advanced eDiscovery og trænet den til det punkt, hvor den er stabil, kan du anvende forudsigelsesscorefilteret til at vise korrektursætelementer, som modellen har fastsat, relevante (eller ikke relevante). Når du opretter en model, oprettes også et tilsvarende forudsigelsesscorefilter. Du kan bruge dette filter til at vise elementer, der er tildelt en forudsigelsesscore inden for et angivet område. Generelt er forudsigelsesresultater mellem **0** og **5** tildelt elementer, som modellen har forudsagt, ikke relevante. Elementer, der er tildelt **forudsigelsesresultater mellem 0,5** **og 1,0** , er elementer, som modellen har forudsagt, er relevante.

Her er to måder, hvorpå du kan bruge forudsigelsesscorefilteret:

- Prioriter gennemgangen af elementer i et korrektursæt, som modellen har forudsagt, er relevante.

- Cull-elementer fra det korrektursæt, som modellen har forudsagt, er ikke relevante. Alternativt kan du bruge forudsigelsesscorefilteret til at af prioritere gennemgangen af ikke-relevante elementer.

## <a name="before-you-apply-a-prediction-score-filter"></a>Før du anvender et forudsigelsesscorefilter

- Opret en forudsigelig kodningsmodel, så der oprettes et tilsvarende forudsigelsesscorefilter.

- Du kan anvende et forudsigelsesscorefilter efter en hvilken som helst af træningsrunderne. Men det kan være en ide at vente, efter der er udført flere runder, eller indtil modellen er stabil, før du bruger filteret til forudsigelsesscore.

## <a name="apply-a-prediction-score-filter"></a>Anvend et forudsigelsesscorefilter

1. I Microsoft 365 Overholdelsescenter skal du åbne Advanced eDiscovery store og små bogstaver, vælge **fanen Gennemse sæt** og derefter åbne korrektursættet.

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

  > [!TIP]
  > Hvis du vil have vist den faktiske forudsigelsesscore for et dokument, kan du klikke **på fanen Metadata** i læseruden. Forudsigelsens resultater for alle modeller i korrektursættet vises i **metadataegenskaben Relevansstegn** .

## <a name="more-information"></a>Flere oplysninger

- Du kan finde flere oplysninger om brug af filtre [under Forespørg og filtrer indhold i et korrektursæt](review-set-search.md).
