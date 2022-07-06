---
title: Vis resultaterne af en eDiscovery-søgning
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få vist et eksempel på de resultater, der returneres af en indholdssøgning eller en eDiscovery-søgning (Standard) i Microsoft Purview-compliance-portal.
ms.openlocfilehash: f369148c6f898c4150d0c86f898640f71ab367a0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628589"
---
# <a name="preview-ediscovery-search-results"></a>Eksportér søgeresultater fra eDiscovery

Når du har kørt en indholdssøgning eller en søgning, der er knyttet til en Microsoft Purview eDiscovery (Standard), kan du få vist et eksempel på de resultater, der returneres af søgningen. Visning af elementer, der returneres af søgeforespørgslen, kan hjælpe dig med at afgøre, om søgningen returnerer de resultater, du håber på, eller om du har brug for at ændre søgeforespørgslen og køre søgningen igen.

Sådan får du vist et eksempel på resultater, der returneres af en søgning:

1. I Microsoft Purview-compliance-portal skal du gå til søgesiden indhold eller en eDiscovery-sag (Standard).

2. Vælg Søg for at få vist pop op-siden.

3. Klik på **Gennemse eksempel** nederst på pop op-siden.

   ![Klik på Gennemse eksempel på pop op-siden for at få vist resultaterne.](../media/PreviewSearchResults1.png)

   Der vises en side, der indeholder et eksempel på søgeresultaterne.

4. Vælg et element for at få vist indholdet i læseruden.

   ![Vis elementer i læseruden.](../media/PreviewSearchResults2.png)

   På det forrige skærmbillede kan du se, at nøgleord fra søgeforespørgslen er fremhævet, når du får vist elementer.

## <a name="how-the-search-result-samples-are-selected"></a>Sådan vælges søgeresultateksempler

Der kan maksimalt vises 1.000 tilfældigt valgte elementer. Ud over at være tilfældigt valgt skal elementer, der er tilgængelige til eksempelvisning, også opfylde følgende kriterier:

- Der kan maksimalt vises 100 elementer fra en enkelt indholdsplacering (en postkasse eller et websted). Det betyder, at der kan være mindre end 1.000 elementer tilgængelige som prøveversion. Hvis du f.eks. søger i fire postkasser, og søgningen returnerer 1.500 anslåede elementer, vil kun 400 være tilgængelige som prøveversion, fordi der kun kan vises 100 elementer fra hver postkasse.

- I forbindelse med postkasseelementer er det kun mailmeddelelser, der er tilgængelige til eksempelvisning. Elementer som opgaver, kalenderelementer og kontakter kan ikke vises.

- For webstedselementer er det kun dokumenter, der kan vises. Elementer som mapper, lister eller vedhæftede filer på lister kan ikke vises.

## <a name="file-types-supported-when-previewing-search-results"></a>Understøttede filtyper ved visning af søgeresultater

Du kan få vist understøttede filtyper i visningsruden. Hvis en filtype ikke understøttes, skal du downloade en kopi af filen til din lokale computer (ved at klikke på **Hent oprindeligt element**). For .aspx-websider er SIDENs URL-adresse inkluderet, selvom du muligvis ikke har tilladelse til at få adgang til siden. Ikke-indekserede elementer er ikke tilgængelige til eksempelvisning.

Følgende filtyper understøttes og kan vises i ruden med søgeresultater.
  
- .txt, .html, .mhtml

- .eml

- .doc, .docx, .docm

- .pptm, .pptx

- .pdf

Følgende filbeholdertyper understøttes også. Du kan få vist listen over filer i objektbeholderen i indholdsruden.
  
- .zip

- .gzip