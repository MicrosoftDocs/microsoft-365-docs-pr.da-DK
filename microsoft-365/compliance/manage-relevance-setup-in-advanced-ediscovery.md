---
title: Administrer opsætning af relevans i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: fd6be6d3-2e8d-449d-9851-03ab7546e6aa
ROBOTS: NOINDEX, NOFOLLOW
description: Læs anbefalingerne til konfiguration af relevanstræning i eDiscovery (Premium) for at score filer efter relevans og generere analytiske resultater.
ms.openlocfilehash: f1a4f1ca9ad9fbf2b63439d463e83723dc2a0e0a
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994848"
---
# <a name="manage-relevance-setup-in-ediscovery-premium-classic"></a>Administrer opsætning af relevans i eDiscovery (Premium) (klassisk)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Microsoft Purview eDiscovery (Premium) kræver et Office 365 E3 med tilføjelsesprogrammet Avanceret overholdelse eller et E5-abonnement for din organisation. Hvis du ikke har denne plan og vil prøve eDiscovery (Premium), kan du [tilmelde dig en prøveversion af Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 eDiscovery (Premium) Relevansteknologi anvender ekspertstyret software til scoring af filer ud fra deres relevans. eDiscovery (Premium) Relevans kan bruges til vurdering af tidlige sager (ECA), gennemsyn af nedslagning og fileksempel. 
  
 eDiscovery (Premium) indeholder komponenter til relevanstræning og mærkning af filer, der er relevante for en sag. eDiscovery (Premium) lærer fra de oplærte eksempler på relevante og ikke relevante filer for at levere relevansscores for hver fil og genererer analyseresultater, der kan bruges under og efter filgennemsynsprocessen. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Retningslinjer for konfiguration af relevanstræning

 På forhånd skal du vælge en sag i vinduet **Sager** og klikke på **Gå til sag**. Klik på Opsætning **af relevans** \> **relevans**. Følg disse anbefalede retningslinjer for at konfigurere Relevans. 
  
- **Mærkning**: Effektiviteten af den iterative relevanstræningsproces afhænger af ekspertens evne til at mærke fileksempler med præcision og konsistens.

- **Sagsproblemer**:
  
  - For hvert problem skal du bruge den samme ekspert i hele relevanstræningsprocessen. Samtidig mærkning af det samme problem af flere eksperter er ikke tilladt.
  
  - Find ud af, om hver gruppe filer kun er relevante for et bestemt problem.

  - Hvis et problem er defineret for generelt, kan eDiscovery (Premium) give for mange filer, der ikke er relevante. Hvis et problem er defineret for snævert, kan relevanstræningsprocessen tage længere tid. 

  - I hver relevanstræningscyklus fokuserer eDiscovery (Premium) på et enkelt aktivt problem, og midlertidige eksempelresultater vises i overensstemmelse hermed.

  - I et scenarie med flere problemer gør samplingstilstanden det muligt at inkludere valg af problemer i behandlingen. Problemer, der er defineret som "fra", håndteres ikke, før samplingstilstanden ændres. Et problem kan være "inaktivt" eller "aktiveret" for kun én ekspert.

  - eDiscovery (Premium) kan bruges til at generere filer med kandidatrettigheder. Konfigurer et separat problem for rettigheder. Hvis det er muligt, skal du først oplære og aflive efter relevans og derefter kun oplære rettighedssortering for det aflivede sæt (genindlæs det frasorterede sæt som et separat tilfælde). 

  - Batchberegning kan kun udføres, når der ikke er nogen åbne eksempler (når du klikker på Batchberegning, vises der en liste over brugere med åbne eksempler). Hvis du vil "lukke" eksempler fra andre brugere (dette skal kun udføres, hvis disse brugere ikke mærker disse eksempler), kan en administrator bruge funktionen "Rediger relevans" med indstillingen "Alle brugere eksempel".

- **Metadata**: eDiscovery (Premium) fokuserer på indhold. Den betragter ikke metadata som en del af relevanskriterierne.

- **Rigdom**: Hvis richness for et problem er mindre end 3 % efter vurdering, bør du overveje at seede relevanstræningen med kendte relevante og ikke relevante filer.

- **Filstørrelse**: Store filer (over 5.242.880 tegn udpakket tekst) ignoreres i relevans. Filerne deltager ikke i relevanstræningsprocessen og modtager ikke en relevansscore efter Batchberegning. Filer på over 5 MB kan inkluderes i vurderingssættet.

## <a name="setting-up-case-issues"></a>Konfiguration af sagsproblemer

De parametre, der er beskrevet i dette afsnit, er tilgængelige i **konfigurationen** af **relevans relevans** \> i eDiscovery (Premium).
  
- Problemer skal tildeles til en bruger, der skal oplære filerne.

- Importerede filer skal derefter føjes til den indlæsning, der behandles.

- Definer og organiser problemer omhyggeligt, da det kan påvirke resultaterne af relevanstræningen.

Når der er angivet parametre, kan korrekturlæseren/eksperten begynde at oplære filerne under fanen **Relevans** .
