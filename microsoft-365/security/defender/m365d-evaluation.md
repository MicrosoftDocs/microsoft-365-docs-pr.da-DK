---
title: Evaluer Microsoft 365 Defender
description: Konfigurer dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø for at afprøve og opleve den sikkerhedsløsning, der er udviklet til at beskytte enheder, identitet, data og programmer i organisationen.
keywords: Microsoft 365 Defender prøveversion kan du prøve Microsoft 365 Defender, evaluere Microsoft 365 Defender, Microsoft 365 Defender evalueringslaboratorium Microsoft 365 Defender  pilot, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1c260588b80d8325567b74148a7a62586cfbc707
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63599323"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Opret et Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender


Denne vejledning hjælper dig med at arbejde på tværs af konfigurationen af et laboratoriemiljø med brugere og grupper og vejleder dig derefter gennem konfigurationen af funktionerne i Microsoft 365 Defender, så du kan efterligne et trusselsangreb og opnå et meningsfuldt prøveresultat. 

Formålet med at oprette dette prøvelaboratorium eller pilotmiljø er at illustrere de omfattende og Microsoft 365 Defender funktioner. Oplev, hvordan denne intelligente sikkerhedsløsning registrerer, forhindrer, automatisk undersøger og reagerer på avancerede trusler i organisationen. 


Du bliver vejledt gennem trinnene til at starte din Microsoft 365 Defender evaluering baseret på de anbefalede installationsstier. Målet er at hjælpe dig med at konfigurere sikkerhedsløsningen enten i et laboratoriemiljø med en prøvekonto eller i et pilotmiljø i produktion med en fuld licens. Forberedelse af dit prøvelaboratorium eller pilotmiljø kan hjælpe dig med at præsentere sikkerhedshandlingsbrugstilfælde til beslutningstagere i organisationen. Når du er færdig med at køre dine angrebssimuleringer, og du er tilfreds med resultatet, kan du implementere og drifte det fuldt ud i din organisation ved hjælp af Microsofts tekniske salgsmedarbejdere eller eksperter i organisationen. 

Denne vejledning kan hjælpe dig med at:
- Konfigurer din labserver og dine computere
- Konfigurere Active Directory med brugere og grupper
- Konfigurer Microsoft Defender for Identity, Microsoft Defender til Office 365, Microsoft Defender til slutpunkt og Microsoft Cloud App Security
- Konfigurer lokale politikker for din server og dine computere
- Efterligne et trusselsangreb for at generere en testhændelse eller besked i Microsoft 365 Defender

>[!IMPORTANT]
>For at opnå optimale resultater skal du følge instruktionerne til laboratories konfiguration så tæt som muligt.


## <a name="deployment-phases"></a>Installationsfaser

Der er tre faser i oprettelsen af et Microsoft 365 Defender-prøvelaboratormiljø.

![Installationsfaser: klargøring, konfiguration, onboard](../../media/evaluation-guide-phases.png)

|Fase | Beskrivelse | 
|:-------|:-----|
|[Fase 1: Forbered](prepare-m365d-eval.md)| Få mere at vide om, hvad du skal overveje, når du Microsoft 365 Defender i et prøvelaboratorium eller et pilotmiljø: <br><br>- Interessenter og logon <br> - Miljøovervejelser <br>- Access <br>- Azure Active Directory konfiguration <br> - Konfigurationsrækkefølge
|[Fase 2: Konfiguration](setup-m365deval.md)|  Tag de første trin for at få adgang Microsoft 365 Security Center for at konfigurere dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø. Du bliver vejledt i at:<br><br>- Tilmeld dig Microsoft 365 E5 prøveversion <br>  - Konfigurer domæne<br>- Tildel Microsoft 365 E5 licenser<br>- Fuldfør konfigurationsguiden på portalen|
|[Fase 3: Konfigurer & onboard](config-m365d-eval.md) | Konfigurer hver Microsoft 365 Defender søjlesøjle og indbyggede slutpunkter. Du bliver vejledt i at:<br><br>- Konfigurer Microsoft Defender til Office 365<br>- Konfigurer Microsoft Cloud App Security<br>- Konfigurer Microsoft Defender for Identity<br>- Konfigurer Microsoft Defender til slutpunkt


Når du har gennemført denne vejledning, ville du have identificeret de involverede interessenter og de nødvendige godkendelser, have de rette adgangstilladelser, tilmeldt dig prøveversionen, konfigurerede domæner og hver af Microsoft 365 Defender-søjlerne, og dine slutpunkter vil blive onboardet til tjenesten.

## <a name="key-capabilities"></a>Vigtige funktioner

Selvom Microsoft 365 Defender indeholder mange funktioner, er det primære formål med denne installationsvejledning at komme i gang med onboardingenheder. Ud over onboarding får denne vejledning dig i gang med følgende funktioner.


Funktion | Beskrivelse 
:---|:---
Microsoft Defender til Office 365 | Hjælper med at beskytte Office 365 hele din sikkerhed mod dagens trusler
Microsoft Defender for Identity | Identificerer og registrerer trusler på kompromitterede identiteter og ondsindede Insider-handlinger.
Microsoft Cloud App Security | Giver stor synlighed, styrer datarejse og registrerer cybertrusler på tværs af skytjenester.
Microsoft Defender til Slutpunkt | Forhindrer, registrerer og leverer svarfunktioner til avancerede trusler med omfattende slutpunktssikkerhed.


## <a name="in-scope"></a>Inden for området

Følgende opgaver er omfattet af denne vejledning:
-   Konfigurer Azure Active Directory
-   Konfigurer Microsoft 365 Defender
    -   Tilmeld dig prøveversionen Microsoft 365 E5 eller brug din fulde licens, hvis du kører et pilotprojekt
    -   Konfigurer domæne
    -   Tildel Microsoft 365 E5 licenser
    -   Fuldføre konfigurationsguiden på portalen
-   Konfigurer alle Microsoft 365 Defender søjler baseret på bedste praksis
    -   Microsoft Defender til Office 365
    -   Microsoft Defender for Identity
    -   Microsoft Cloud App Security
    -   Microsoft Defender til Slutpunkt

## <a name="out-of-scope"></a>Uden for området

Følgende er ikke omfattet af denne installationsvejledning:

-   Konfiguration af tredjepartsløsninger, der kan integreres med Microsoft 365 Defender
-   Test af test af test i produktionsmiljø

## <a name="next-step"></a>Næste trin
[Fase 1: Forbered](prepare-m365d-eval.md) 
<br> Forbered dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø
