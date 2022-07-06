---
title: Opret en forudsigende kodemodel i eDiscovery (Premium)
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
description: Få mere at vide om, hvordan du opretter en forudsigende kodemodel i eDiscovery (Premium). Dette er det første trin i brugen af funktionerne til maskinel indlæring i eDiscovery (Premium) for at hjælpe dig med at identificere relevant og ikke-relevant indhold i et korrektursæt.
ms.openlocfilehash: 1105ff05d323ded2297a92d7b12b44a78c35b11f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635737"
---
# <a name="create-a-predictive-coding-model-preview"></a>Opret en forudsigende kodemodel (prøveversion)

Det første trin i brugen af funktionerne til maskinel indlæring i forbindelse med forudsigende kodning i eDiscovery (Premium) er at oprette en forudsigende kodemodel. Når du har oprettet en model, kan du oplære den til at identificere det relevante og ikke-relevante indhold i et anmeldelsessæt.

Hvis du vil gennemse arbejdsprocessen for forudsigende kodning, skal [du se Få mere at vide om forudsigende kodning i eDiscovery (Premium)](predictive-coding-overview.md#the-predictive-coding-workflow)

## <a name="before-you-create-a-model"></a>Før du opretter en model

- Der skal være mindst 2.000 elementer i et korrektursæt for at oprette en forudsigende kodemodel.

- Sørg for at bekræfte alle samlinger til korrektursættet, før du opretter en model. Elementer, der føjes til et korrektursæt, efter at modellen er oprettet, behandles ikke og tildeles en forudsigelsesscore, der genereres af modellen.

- Alle elementer i korrektursættet, der ikke indeholder tekst, behandles ikke af modellen eller tildeles en forudsigelsesscore. Elementer med tekst medtages i kontrolelementsættet eller et oplæringssæt.

## <a name="create-a-model"></a>Opret en model

1. Åbn en eDiscovery-sag (Premium) i Microsoft Purview-compliance-portal, og vælg derefter fanen **Gennemse sæt**.

2. Åbn et korrektursæt, og klik derefter på **Administrer forudsigende kodning (prøveversion)** i **Analytics** > .

   ![Klik på rullemenuen Analysér i gennemgangssættet for at gå til siden Forudsigende kodning.](..\media\ManagePredictiveCoding.png)

3. Klik på **Ny model** på siden **Forudsigende kodningsmodeller (prøveversion).**

4. Skriv et navn til modellen og en valgfri beskrivelse på pop op-siden.

5. Du kan eventuelt konfigurere avancerede indstillinger (ved at klikke på **Avancerede indstillinger** på pop op-siden) relateret til tillidsniveauet og fejlmargenen. Disse indstillinger påvirker antallet af elementer, der er inkluderet i kontrolelementsættet. *Kontrolelementsættet* bruges under oplæringsprocessen til at evaluere de forudsigelsesscores, som modellen tildeler til elementer med den mærkat, du udfører under oplæringsrunder. Hvis din organisation har retningslinjer for tillidsniveau og fejlmargen til dokumentgennemsyn, skal du angive dem i de relevante felter. Ellers skal du bruge standardindstillingerne.

6. Klik på **Gem** for at oprette modellen.

   Det tager et par minutter, før systemet klargør din model. Når den er klar, kan du udføre den første runde af træningen.

## <a name="what-happens-after-you-create-a-model"></a>Hvad sker der, når du har oprettet en model?

Når du har oprettet en model, sker følgende ting i baggrunden under oprettelsen og forberedelsen af modellen:

- Systemet beregner antallet af elementer for kontrolelementsættet. Denne størrelse er baseret på antallet af elementer i korrektursættet og indstillingerne for tillidsniveauet og fejlmargenen. Elementer for kontrolelementsættet vælges tilfældigt og angives som elementer i kontrolelementsættet. Systemet omfatter 10 elementer fra det kontrolelement, der i første runde af uddannelse.

- Systemet vælger tilfældigt 40 elementer fra gennemgangssættet, der skal inkluderes i træningssættet til den første runde af træningen. Derfor omfatter den første runde af oplæringen 50 elementer til mærkning: 40 elementer fra oplæringssættet og 10 elementer fra kontrolelementsættet.

## <a name="next-steps"></a>Næste trin

Når du har oprettet en model til et anmeldelsessæt, er det næste trin at udføre oplæringsrunder for at "undervise" modellen for at identificere indhold, der er relevant for din undersøgelse. Du kan finde flere oplysninger under [Oplær en forudsigende kodemodel](predictive-coding-train-model.md).
