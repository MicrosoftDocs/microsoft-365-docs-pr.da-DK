---
title: Beslutning baseret på resultaterne i eDiscovery (Premium)
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
description: Få mere at vide om, hvordan fanen Beslut i eDiscovery (Premium) indeholder data, der kan hjælpe dig med at bestemme den korrekte størrelse af korrektursættet af sagsfiler.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6c8759db2445b8d98c47cc1103deda058d2f3508
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64932414"
---
# <a name="decisions-based-on-relevance-results-in-ediscovery-premium"></a>Beslutninger baseret på relevansresultater i eDiscovery (Premium)
  
I relevansmodulet i eDiscovery (Premium) indeholder fanen Beslut yderligere oplysninger til visning og brug af statistik for beslutningssupport til at bestemme størrelsen af korrektursættet af sagsfiler.
  
## <a name="using-the-decide-tab"></a>Brug af fanen Beslut

![Relevans beslutte.](../media/f32fed89-f3b5-404a-90c7-ea25d2eb58a9.png)
  
Denne fane indeholder følgende komponenter:
  
- **Problem**: Herfra kan du vælge spørgsmålet om interesse på listen.

- **Forhold mellem tilbagekald** af anmeldelse: Sammenligninger af eDiscovery-gennemgang (Premium) i henhold til relevansscores. Skæringspunktet i diagrammet repræsenterer den procentdel af filer, der skal gennemses, og som er knyttet til en relevansscore. Dette bruges i relevanstestfasen og som en eksporttærskel for nedslagning. Standardafskæringspunktet for det antal filer, der skal gennemses, er på det punkt, hvor balancen mellem Tilbagekaldelse og Præcision er optimal. Det faktiske skæringspunkt skal bestemmes af brugeren afhængigt af målsætninger og omkostningsafvejning (%review) og risiko (%recall). Ved hjælp af skyderen kan du justere skæringspunktet og se effekten på grafen og parametrene, når du justerer procentdelen af relevante filer, der skal hentes, og før du validerer en beslutning.

- **Parametre: Parametrene** Review, Recall, Next relevant og Total cost er akkumulerede beregnede statistikker, der vedrører gennemgangssættet i forhold til samlingen for hele sagen. Definitioner for disse parametre er som følger:

  - **Anmeldelse**: Procentdel af filer, der skal gennemses baseret på denne skæring.

  - **Husk**: Procentdelen af relevante filer i korrektursættet.

  - **Næste relevant**: Omkostninger ved gennemsyn og identificer en anden relevant fil, der i øjeblikket ikke er i korrektursættet.

  - **Samlede omkostninger**: Omkostninger til gennemsyn af denne procentdel af sagsfilerne. Indstillinger for omkostningsparametre kan angives af Sagsadministrator.

  - **Distribution efter relevansscore**: Filer i den mørke grå skærm til venstre er under skæringsscoren. Et værktøjstip viser relevansscoren og den relaterede procentdel af filer i korrekturfilen, der er angivet i forhold til det samlede antal filer.

Den udvidede rude **Detaljer** viser flere detaljer. Filer i samlingsfigurer indeholder ikke tomme eller tågede filer. Familiefiler repræsenterer filer, der ikke er indlæst i Relevans, men stadig tælles som en del af familien.
