---
title: Administrer konfigurationen af relevans i Advanced eDiscovery
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
description: Læs anbefalingerne til konfiguration af relevanskurser i Advanced eDiscovery at score filer ud fra deres relevans og generere analytiske resultater.
ms.openlocfilehash: bed912c0631511e9d3d4839e5d6925de79554163
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587715"
---
# <a name="manage-relevance-setup-in-advanced-ediscovery-classic"></a>Administrer konfigurationen af relevans i Advanced eDiscovery (klassisk)

> [!NOTE]
> Advanced eDiscovery kræver en Office 365 E3 med tilføjelsesprogrammet Avanceret overholdelse eller et E5-abonnement til din organisation. Hvis du ikke har den plan og gerne vil prøve Advanced eDiscovery, kan du tilmelde dig [en prøveversion af Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 Advanced eDiscovery relevansteknologi anvender ekspertguidet software til scorefiler ud fra deres relevans. Advanced eDiscovery relevans kan bruges til ECA (Early Case Assessment), nedslagning og gennemgang af fileksempel. 
  
 Advanced eDiscovery indeholder komponenter til relevanskurser og mærkning af filer, der er relevante for en sag. Advanced eDiscovery lærer af de uddannede eksempler på relevante og ikke relevante filer for at levere relevansresultater for hver fil og genererer analytiske resultater, der kan bruges under og efter filgennemsynsprocessen. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Retningslinjer for konfiguration af relevanskurser

 På forhånd eDiscovery skal du i **vinduet Sager** vælge en sag og klikke på **Gå til sag**. Klik på **Konfiguration af relevans** \> **.** Følg disse anbefalede retningslinjer for at konfigurere Relevans. 
  
- **Mærkning**: Effektiviteten af kursusprocessen for iterativ relevans afhænger af ekspertens mulighed for at mærke fileksempler med præcision og ensartethed.

- **Sagsproblemer**:
  
  - For hvert problem skal du bruge den samme ekspert under hele relevans-uddannelsesprocessen. Samtidig mærkning af det samme problem af flere eksperter er ikke tilladt.
  
  - Afgør, om hver gruppe af filer kun er relevant for et bestemt problem.

  - Hvis et problem er defineret for generelt, kan Advanced eDiscovery give for mange filer, der ikke er relevante. Hvis et problem er defineret for smalt, kan uddannelsesprocessen Relevans tage længere tid. 

  - Under hvert relevanskursus i Advanced eDiscovery fokus på et enkelt aktivt problem, og midlertidige eksempelresultater vises tilsvarende.

  - I et scenarie med flere problemer gør stikprøvetilstand det muligt at inkludere valget af problemer i behandlingen. Problemer defineret som "fra" håndteres ikke, før deres stikprøvetilstand ændres. Et problem kan være "inaktivt" eller "on" for kun én ekspert.

  - Advanced eDiscovery kan bruges til at generere kandidaternes rettighedsfiler. Konfigurer et separat problem for rettigheder. Hvis det er muligt, skal du først træne og cull for relevans og derefter kun træne til rettighedsberegninger på det bestødede sæt (genindlæs det omdøbte sæt som en separat sag). 

  - Batchberegning kan kun udføres, når der ikke er nogen åbne eksempler (når du klikker på Batchberegning, vises der en liste over brugere med åbne eksempler). Hvis du vil "lukke" eksempler på andre brugere (dette bør kun udføres, hvis disse brugere ikke mærker disse eksempler), kan en administrator bruge værktøjet "Rediger relevans" med indstillingen "Alle brugere eksempel".

- **Metadata**: Advanced eDiscovery fokuserer på indhold. Metadata er ikke en del af relevanskriterierne.

- **Richness**: If the Richness for an issue is less than 3% after Assessment, consider seeding the Relevance training with known Relevant and Not Relevant files.

- **Filstørrelse**: Store filer (over 5.242.880 tegn udtrukket tekst) ignoreres i relevans. Filerne deltager ikke i relevanskursusprocessen og får ikke et relevansscore efter batchberegning. Filer på mere end 5 MB kan medtages i Bedømmelsessættet.

## <a name="setting-up-case-issues"></a>Konfiguration af sagsproblemer

De parametre, der er beskrevet i dette afsnit, er tilgængelige i Advanced eDiscovery **for relevans**\>.
  
- Der skal tildeles problemer til en bruger, der skal oplære filerne.

- Importerede filer skal derefter føjes til den belastning, der behandles.

- Definer og organiser problemer omhyggeligt, da dette kan påvirke resultaterne af relevanskurserne.

Når parametrene er angivet, kan korrekturlæseren/eksperten begynde at uddanne filerne på **fanen** Relevans.
