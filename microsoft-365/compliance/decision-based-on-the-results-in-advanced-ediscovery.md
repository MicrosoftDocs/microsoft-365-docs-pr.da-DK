---
title: Beslutning baseret på resultaterne i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: aed65bcd-0a4f-43e9-b5e5-b98cc376bdf8
description: Få mere at vide om, hvordan fanen Beslut Advanced eDiscovery indeholder data, der kan hjælpe dig med at bestemme den korrekte størrelse på gennemsynssættet af sagsfiler.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 32682690c6febac247d67e3b78f56d1f71b9a2fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588907"
---
# <a name="decisions-based-on-relevance-results-in-advanced-ediscovery"></a>Beslutninger baseret på resultater af relevans i Advanced eDiscovery
  
Fanen Beslut i modulet Relevans i Advanced eDiscovery indeholder yderligere oplysninger til visning og brug af statistik for beslutningssupport til at fastslå størrelsen på sagsfilernes gennemgangssæt.
  
## <a name="using-the-decide-tab"></a>Brug af fanen Beslut

![Relevans Beslut.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Denne fane indeholder følgende komponenter:
  
- **Problem**: Herfra kan du vælge problemet med interesse på listen.

- **Review-recall ratio**: Sammenligninger af resultater Advanced eDiscovery efter relevansresultater. Skæringspunktet i diagrammet repræsenterer procentdelen af filer, der skal gennemses, knyttet til et relevansscore. Dette bruges i fasen Relevanstest og som en eksporttærskel for nedslagning. Standardskæringspunktet for antallet af filer, der skal gennemgås, er det punkt, hvor balancen mellem Tilbagekaldelse og præcision er optimal. Det faktiske skæringspunkt bør bestemmes af brugeren afhængigt af målsætninger og omkostningsintern kompromis (gennemgang af omkostninger) og risici (%recall). Ved hjælp af skyderen kan du justere skæringspunktet og se effekten på grafen og parametrene, når du justerer procentdelen af relevante filer, der skal hentes, og før du validerer en beslutning.

- **Parametre**: Gennemse, Tilbagekald, Næste relevante og Samlede omkostningsparametre er kumulative beregnede statistikker, der vedrører gennemgangssættet i forhold til samlingen for hele sagen. Definitioner for disse parametre er som følger:

  - **Gennemse**: Procentdel af filer, der skal gennemses, baseret på denne skæring.

  - **Tilbagekaldelse**: Procentdel af relevante filer i gennemsynssættet.

  - **Næste relevant**: Omkostninger til at gennemse og identificere en anden relevant fil, der i øjeblikket ikke er i korrektursættet.

  - **Samlede omkostninger**: Omkostninger til gennemgang af denne procentdel af sagsfilerne. Indstillinger for omkostningsparametre kan angives af Case manager.

  - **Fordeling efter relevansscore**: Filer i den mørkegrå visning til venstre er under skæringsresultatet. Et værktøjstip viser relevansscoren og den relaterede procentdel af filer i gennemsynsfilen angivet i forhold til de samlede filer.

Den udvidede **ruden Detaljer** viser flere detaljer. Filer i samlingsfigurer inkluderer ikke tomme eller overflødige filer. Tal for familiefiler repræsenterer filer, der ikke er indlæst med relevans, men stadig tælles som en del af familien.
