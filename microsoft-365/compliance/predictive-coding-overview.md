---
title: Forudsigeligt kodningsmodul til Advanced eDiscovery (eksempel)
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
description: Det nye forudsigelige kodningsmodul i Advanced eDiscovery bruger maskinlæring til at analysere elementer i et korrektursæt for at forudsige, hvilke elementer der er relevante for din sag eller undersøgelse.
ms.openlocfilehash: 60f0fc2f53c8bfbde2a4a1d5cccb4eb678f7c33e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592142"
---
# <a name="learn-about-predictive-coding-in-advanced-ediscovery-preview"></a>Få mere at vide om forudsigelig kodning Advanced eDiscovery (eksempel)

Forudsigeligt kodningsmodul i Advanced eDiscovery bruger de intelligente maskinlæringsfunktioner til at hjælpe dig med at reducere mængden af indhold, der skal gennemgås. Forudsigelig kodning hjælper dig med at reducere og cullere store mængder sagsindhold til et relevant sæt af elementer, som du kan prioritere til gennemsyn. Dette opnås ved at oprette og træne dine egne forudsigelige kodningsmodeller, der hjælper dig med at prioritere gennemgangen af de mest relevante elementer i et korrektursæt.

Predictive coding modulet er designet til at strømline kompleksiteten ved administration af en model i et korrektursæt og give en iterativ tilgang til uddannelse af din model, så du kan komme hurtigere i gang med de maskinel indlæringsegenskaber i Advanced eDiscovery. For at komme i gang kan du oprette en model og navn så få som 50 elementer som relevante eller ikke relevante. Systemet bruger dette kursus til at anvende forudsigelsesresultater for hvert element i korrektursættet. Dette gør det muligt at filtrere elementer baseret på forudsigelsesresultatet, hvilket giver dig mulighed for at gennemse de mest relevante (eller ikke-relevante) elementer først. Hvis du vil træne modeller med højere inaktler og tilbagekaldelseshastigheder, kan du fortsætte med at navnmærke elementer i efterfølgende træningsrunder, indtil modellen er stabil.  

## <a name="the-predictive-coding-workflow"></a>Den forudsigelige kodningsarbejdsproces

Her er en oversigt over og en beskrivelse af hvert trins forudsigelig kodningsarbejdsproces. Hvis du vil have en mere detaljeret beskrivelse af begreberne og terminologien for forudsigelig kodningsprocessen, skal du [se Reference til forudsigelig kodning](predictive-coding-reference.md).

![Forudsigelig kodningsarbejdsproces.](..\media\PredictiveCodingWorkflow.png)

1. **Opret en ny forudsigelig kodningsmodel i korrektursættet**. Det første trin er at oprette en ny forudsigelig kodningsmodel i korrektursættet. Du skal have mindst 2.000 elementer i korrektursættet for at oprette en model. Når du har oprettet en model, bestemmer systemet antallet af elementer, der skal bruges som *et kontrolelementsæt*. Kontrolsættet bruges under uddannelsesprocessen til at evaluere de forudsigelsesresultater, som modellen tildeler elementer med den mærkat, du udfører under træningsrundne. Størrelsen på kontrolelementsættet er baseret på antallet af elementer i korrektursættet og tillidsniveauet og margenen for fejlværdier, der er angivet ved oprettelse af modellen. Elementer i kontrolelementsættet ændres aldrig og kan ikke identificeres af brugerne.

   Få mere at vide under [Opret en forudsigelig kodningsmodel](predictive-coding-create-model.md).

2. **Fuldfør den første træningsrund ved at navngivet elementer som relevante eller ikke relevante**. Næste trin er at træne modellen ved at starte den første træningsrund. Når du starter en træningsrund, vælger modellen tilfældigt flere elementer fra korrektursættet, som kaldes *træningssættet*. Disse elementer (både fra kontrolelementsættet og kursussættet) vises for dig, så du kan navnde hver enkelt som enten "relevant" eller "ikke relevant". Relevans er baseret på indholdet i elementet og ikke nogen af dokumentets metadata. Når du har fuldført navneprocessen i træningsrunden, "lærer" modellen baseret på, hvordan du har navnmærket elementerne i træningssættet. Baseret på dette kursus vil modellen behandle elementerne i korrektursættet og anvende en forudsigelsesscore på hver enkelt.

   Få mere at vide under [Træn en forudsigelig kodningsmodel](predictive-coding-train-model.md).

3. **Anvend forudsigelsesscorefilteret på elementer i korrektursæt**. Når det forrige kursustrin er fuldført, er næste trin at anvende forudsigelsesscorefilteret på elementerne i anmeldelsen for at få vist de elementer, som modellen har fastlagt, er "mest relevante" (du kan også bruge et forudsigelsesfilter til at vise elementer, der ikke er "relevante"). Når du anvender forudsigelsesfilteret, angiver du en række forudsigelser, der skal filtreres. Prognoseresultaterne falder mellem **0 og** **1**, hvor **0** er "ikke-relevant" og **1** er relevante. Generelt betragtes elementer med forudsigelsesresultater mellem **0** og **0,5** som "ikke-relevante", og elementer med forudsigelsesresultater mellem **0,5** og **1** betragtes som relevante.

   Få mere at vide under [Anvend et forudsigelsesfilter på et korrektursæt](predictive-coding-apply-prediction-filter.md).

4. **Udfør flere træningsrunder, indtil modellen er stabil**. Du kan udføre yderligere runder med kurser, hvis du vil oprette en model med større nøjagtighed forudsigelser og øgede tilbagekaldelseshastigheder. *Tilbagekaldelseshastigheden* måler den del af elementer, som den forudsagte model har været relevant for, blandt de elementer, der faktisk er relevante (dem, du har markeret som relevante under uddannelse). Tilbagekaldelseshastigheden varierer fra **0** til **1**. Et pointtal tættere på **1** angiver, at modellen identificerer mere relevante elementer. I en ny træningsrund angiver du yderligere elementer i et nyt kursussæt. Når du har gennemført denne træningsrund, opdateres modellen på baggrund af ny viden fra din seneste runde af navneelementer i træningssættet. Modellen behandler elementerne i korrektursættet igen og anvender nye forudsigelsesresultater. Du kan fortsætte med at udføre træningsrunder, indtil modellen er stabil. En model betragtes som stabil, når den efter den seneste kursusrunde er mindre end 5 %. *Churn-rente* defineres som procentdelen af elementer i et korrektursæt, hvor forudsigelsesresultatet blev ændret mellem træningsrunder. Forudsigelig kodningsdashboardet viser oplysninger og statistikker, der hjælper dig med at vurdere stabiliteten af en model.

5. **Anvend det "endelige" forudsigelsesresultatfilter for at gennemgå de sæt elementer, der skal prioriteres i gennemgangen**. Når du har fuldført alle træningsrundne og har stabilt modellen, er det sidste trin at anvende det endelige forudsigelsesresultat på korrektursættet for at prioritere gennemgangen af relevante og ikke-relevante elementer. Dette er den samme opgave, du udførte på trin 3, men på dette tidspunkt er modellen stabil, og du har ikke planer om at køre flere træningsrunder.
