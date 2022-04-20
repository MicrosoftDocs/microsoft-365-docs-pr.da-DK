---
title: Modul med forudsigende kodning til eDiscovery (Premium) (prøveversion)
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
description: Det nye modul med forudsigende kodning i eDiscovery (Premium) bruger maskinel indlæring til at analysere elementer i et korrektursæt for at forudsige, hvilke elementer der er relevante for din sag eller undersøgelse.
ms.openlocfilehash: 2cf8541e3ca3928b1206eb824c21e21e49c4caa9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936549"
---
# <a name="learn-about-predictive-coding-in-ediscovery-premium-preview"></a>Få mere at vide om forudsigende kodning i eDiscovery (Premium) (prøveversion)

Det forudsigende kodningsmodul i eDiscovery (Premium) bruger de intelligente funktioner til maskinel indlæring til at hjælpe dig med at reducere mængden af indhold, der skal gennemses. Forudsigende kodning hjælper dig med at reducere og reducere store mængder sagsindhold til et relevant sæt elementer, som du kan prioritere til gennemsyn. Dette opnås ved at oprette og oplære dine egne forudsigende kodemodeller, der hjælper dig med at prioritere gennemgangen af de mest relevante elementer i et korrektursæt.

Det forudsigende kodemodul er designet til at strømline kompleksiteten ved at administrere en model i et korrektursæt og give en iterativ tilgang til oplæring af din model, så du kan komme hurtigere i gang med funktionerne til maskinel indlæring i eDiscovery (Premium). For at komme i gang kan du oprette en model med så få som 50 elementer som relevante eller ikke-relevante. Systemet bruger denne oplæring til at anvende forudsigelsesscores på hvert element i korrektursættet. Det giver dig mulighed for at filtrere elementer baseret på forudsigelsesscoren, hvilket giver dig mulighed for først at gennemse de mest relevante (eller ikke-relevante) elementer. Hvis du vil oplære modeller med højere tilgængeligheds- og genkaldelsesrater, kan du fortsætte med at mærke elementer i efterfølgende træningsrunder, indtil modellen stabiliseres.  

## <a name="the-predictive-coding-workflow"></a>Arbejdsprocessen for forudsigende kodning

Her er en oversigt over og en beskrivelse af hvert trin i arbejdsprocessen for forudsigende kodning. Du kan finde en mere detaljeret beskrivelse af begreberne og terminologien i forudsigende kodningsproces under [Reference til forudsigende kodning](predictive-coding-reference.md).

![Arbejdsproces til forudsigende kodning.](..\media\PredictiveCodingWorkflow.png)

1. **Opret en ny forudsigende kodemodel i korrektursættet**. Det første trin er at oprette en ny forudsigende kodemodel i korrektursættet. Du skal have mindst 2.000 elementer i korrektursættet for at oprette en model. Når du har oprettet en model, bestemmer systemet antallet af elementer, der skal bruges som et *kontrolelementsæt*. Kontrolelementsættet bruges under oplæringsprocessen til at evaluere de forudsigelsesscores, som modellen tildeler til elementer med den mærkat, du udfører under oplæringsrunder. Størrelsen af kontrolelementsættet er baseret på antallet af elementer i korrektursættet og det tillidsniveau og den margen for fejlværdier, der angives, når modellen oprettes. Elementer i kontrolelementsættet ændres aldrig og kan ikke identificeres af brugerne.

   Du kan finde flere oplysninger under [Opret en forudsigende kodemodel](predictive-coding-create-model.md).

2. **Fuldfør den første træningsrunde ved at markere elementer som relevante eller ikke relevante**. Det næste trin er at oplære modellen ved at starte den første runde af træningen. Når du starter en træningsrunde, vælger modellen tilfældigt yderligere elementer fra korrektursættet, som kaldes *oplæringssættet*. Disse elementer (både fra kontrolelementsættet og oplæringssættet) præsenteres for dig, så du kan angive hver enkelt som enten "relevant" eller "ikke relevant". Relevans er baseret på indholdet i elementet og ikke nogen af dokumentets metadata. Når du har fuldført mærkatprocessen i træningsrunden, "lærer modellen" baseret på, hvordan du mærkede elementerne i oplæringssættet. Baseret på denne oplæring behandler modellen elementerne i korrektursættet og anvender en forudsigelsesscore på hver enkelt.

   Du kan finde flere oplysninger under [Oplær en forudsigende kodemodel](predictive-coding-train-model.md).

3. **Anvend filteret med forudsigelsesresultatet på elementer i korrektursættet**. Når det forrige oplæringstrin er fuldført, er det næste trin at anvende filteret for forudsigelsesscore på elementerne i gennemgangen for at få vist de elementer, som modellen har bestemt, er "mest relevante" (alternativt kan du også bruge et forudsigelsesfilter til at få vist elementer, der ikke er "relevante"). Når du anvender forudsigelsesfilteret, angiver du et interval af forudsigelsesscores, der skal filtreres. Intervallet for forudsigelsesscores ligger mellem **0** og **1**, hvor **0** er "ikke-relevant" og **1** er relevant. Generelt betragtes elementer med forudsigelsesscores mellem **0** og **0,5** som "ikke-relevante", og elementer med forudsigelsesscores mellem **0,5** og **1** anses for at være relevante.

   Du kan finde flere oplysninger under [Anvend et forudsigelsesfilter på et korrektursæt](predictive-coding-apply-prediction-filter.md).

4. **Udfør flere oplæringsrunder, indtil modellen stabiliseres**. Du kan udføre yderligere oplæringsrunder, hvis du vil oprette en model med en højere nøjagtighed af forudsigelse og øget genkaldelseshastighed. *Målinger af tilbagekaldsfrekvensen* viser, hvor stor en del af de elementer, som modellen forudsagde, var relevante for de elementer, der faktisk er relevante (dem, du har markeret som relevante under oplæringen). Scoren for genkaldelsesfrekvensen varierer fra **0** til **1**. En score, der er tættere på **1** , angiver, at modellen identificerer mere relevante elementer. I en ny træningsrunde navngiver du yderligere elementer i et nyt oplæringssæt. Når du har fuldført træningsrunden, opdateres modellen baseret på ny læring fra din seneste runde af mærkatelementer i oplæringssættet. Modellen behandler elementerne i korrektursættet igen og anvender nye forudsigelsesscores. Du kan fortsætte med at udføre oplæringsrunder, indtil din model stabiliseres. En model anses for at være stabiliseret, når faldhastigheden efter den seneste træningsrunde er mindre end 5 %. *Faldfrekvensen* defineres som procentdelen af elementer i et gennemsynssæt, hvor forudsigelsesscoren blev ændret mellem oplæringsrunder. Dashboardet til forudsigende kodning viser oplysninger og statistikker, der hjælper dig med at vurdere stabiliteten af en model.

5. **Anvend filteret til "endelig" forudsigelsesscore for at gennemse sæt elementer for at prioritere gennemsyn**. Når du har fuldført alle oplæringsrunder og stabiliseret modellen, er det sidste trin at anvende den endelige forudsigelsesscore på gennemgangssættet for at prioritere gennemgangen af relevante og ikke-relevante elementer. Dette er den samme opgave, som du udførte i trin 3, men på dette tidspunkt er modellen stabil, og du har ikke planer om at køre flere træningsrunder.
