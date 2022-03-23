---
title: Få vist resultaterne af en eDiscovery-søgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få vist et eksempel på de resultater, der returneres af en indholdssøgning eller en grundlæggende eDiscovery-søgning i Microsoft 365 Overholdelsescenter.
ms.openlocfilehash: af0811d0c442d6f064fd336d4261d1f7b2337dc8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593264"
---
# <a name="preview-ediscovery-search-results"></a>Forhåndsvisning af eDiscovery-søgeresultater

Når du har kørt en indholdssøgning eller en søgning, der er knyttet til en Core eDiscovery-sag, kan du få vist et eksempel på et eksempel på de resultater, der returneres af søgningen. Visning af elementer, der returneres af søgeforespørgslen, kan hjælpe dig med at afgøre, om søgningen returnerer de resultater, du håber på, eller om du skal ændre søgeforespørgslen og køre søgningen igen.

Sådan får du vist et eksempel på resultater, der returneres af en søgning:

1. I Microsoft 365 Overholdelsescenter skal du gå til siden Indholdssøgning eller en Core eDiscovery-sag.

2. Vælg Søg for at få vist pop op-siden.

3. Klik på Gennemse eksempel nederst på pop **op-siden**.

   ![Klik på Gennemse eksempel på pop op-siden for at få vist resultaterne.](../media/PreviewSearchResults1.png)

   Der vises en side, der indeholder et eksempel på søgeresultaterne.

4. Vælg et element for at få vist indholdet i læseruden.

   ![Få vist elementer i læseruden.](../media/PreviewSearchResults2.png)

   I det forrige skærmbillede skal du bemærke, at nøgleord fra søgeforespørgslen fremhæves, når du får vist elementer.

## <a name="how-the-search-result-samples-are-selected"></a>Sådan markeres eksempler på søgeresultat

Der kan maksimalt vises 1.000 tilfældigt markerede elementer. Ud over at blive tilfældigt markeret skal elementer, der er tilgængelige til forhåndsvisning, også opfylde følgende kriterier:

- Der kan maksimalt vises 100 elementer fra en enkelt indholdsplacering (en postkasse eller et websted). Det betyder, at det er muligt, at færre end 1.000 elementer kan fås til forhåndsvisning. Hvis du f.eks. søger i fire postkasser, og søgningen returnerer 1.500 anslåede elementer, vil kun 400 være tilgængelige til forhåndsvisning, fordi der kun kan vises 100 elementer fra hver postkasse.

- For postkasseelementer er det kun muligt at få vist mails. Elementer som f.eks. opgaver, kalenderelementer og kontakter kan ikke vises som eksempler.

- Ved webstedselementer er det kun dokumenter, der er tilgængelige til forhåndsvisning. Elementer som mapper, lister eller vedhæftede filer på lister kan ikke vises.

## <a name="file-types-supported-when-previewing-search-results"></a>Understøttede filtyper ved visning af søgeresultater

Du kan få vist understøttede filtyper i indholdsruden. Hvis en filtype ikke understøttes, skal du hente en kopi af filen til din lokale computer (ved at klikke på **Hent det oprindelige element**). For .aspx-websider er URL-adressen til siden inkluderet, selvom du muligvis ikke har tilladelse til at få adgang til siden. Unindexed items aren't available for previewing.

Følgende filtyper understøttes og kan vises i ruden med søgeresultater.
  
- .txt, .html, .mhtml

- .eml

- .doc, .docx, .docm

- .pptm, .pptx

- .pdf

Desuden understøttes følgende filtyper. Du kan få vist listen over filer i beholderen i indholdsruden.
  
- .zip

- .gzip