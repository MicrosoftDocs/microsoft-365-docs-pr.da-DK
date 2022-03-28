---
title: ASR-regler for implementeringsfase 1 – plan
description: Giver vejledning i at planlægge dine implementeringsregler for reduktion af angrebsoverfladen.
keywords: Implementering af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, beskyttelsessystem til forebyggelse af indtrængen, beskyttelsesregler, anti exploit, udnyttelsesregler, regler for forebyggelse af indtrængen, Microsoft Defender til slutpunkt, konfigurer ASR-regler
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: ecd582f99dd0dfa9df51ce50651904144dcc8ff8
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63596959"
---
# <a name="asr-rules-deployment-phase-1-plan"></a>ASR-regler for installationsfase 1: plan

At starte med at teste ASR-regler indebærer at starte med den rigtige forretningsenhed. Du bør starte med en lille gruppe personer i en bestemt forretningsenhed. Du kan identificere nogle ASR-vindere inden for en bestemt forretningsenhed, som kan sikre den virkelige påvirkning af asr-reglerne og hjælpe dig med at finjustere din implementering.

> [!div class="mx-imgBorder"]
> ![Trin til planlægning af ASR-regler](images/asr-rules-planning-steps.png)

## <a name="start-with-the-right-business-unit"></a>Start med den rigtige forretningsenhed

Hvordan du vælger den forretningsenhed, der skal implementeres i din implementering af ASR-reglerne, afhænger af faktorer som f.eks.:

- Størrelse på forretningsenhed
- Tilgængelighed af ASR-regler for vindere  
- Fordeling og brug af:
  - Software
  - Delte mapper
  - Brug af scripts
  - Office makroer
  - Andre enheder, der er påvirket af ASR-regler

Afhængigt af dine forretningsmæssige behov kan du vælge at medtage flere forretningsenheder for at få et bredt udvalg af software, delte mapper, scripts, makroer osv. Omvendt kan du beslutte at begrænse omfanget af dine første AA-reglers udrulning til en enkelt forretningsenhed og derefter gentage udrulningen af alle AA-regler til dine andre forretningsenheder én ad gangen.

## <a name="identify-asr--rules-champions"></a>Identificer ASR rules champions

Asr rules champions are members in your organization that will help with your initial ASR rules rollout during the preliminary testing and implementation phases. Dine vindere er typisk medarbejdere, som er mere teknisk dygtige, og som ikke afspores af forbitiske arbejdsafbrydelser. The champions' involvement will continue throughout the broader expansion of ASR rules deployment to your organization. Dine regler for asr-regler bliver de bedste til at opleve hvert niveau af udrulningen af ASR-reglerne.

Det er vigtigt at give en feedback- og svarkanal, så dine ASR-regelmestre kan give dig besked om asr-regelrelaterede arbejdsafbrydelser og modtage ASR-regler udrulning af relateret kommunikation.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Få oversigt over line of business-apps, og få et forståelse af processer for forretningsenheder

At have en fuld forståelse for de programmer og processer pr. forretningsenhed, der bruges i hele organisationen, er afgørende for en vellykket installation af ASR-regler. Det er desuden af afgørende betydning, at du forstår, hvordan disse apps bruges inden for de forskellige forretningsenheder i organisationen.
Til at begynde med bør du få en oversigt over de apps, der er godkendt til brug på tværs af brødet i organisationen. Du kan bruge værktøjer som f.eks Microsoft 365 Apps Administration til at hjælpe dig med lagersoftwareprogrammer. Læs: [Oversigt over lageret Microsoft 365 Apps Administration](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team--roles-and-responsibilities"></a>Definer rapporterings- og svarteamroller og -ansvarsområder

Det er tydeligt, at roller og ansvarsområder for personer, der er ansvarlige for overvågning og kommunikation af ASR-reglers status og aktivitet, er en vigtig aktivitet i asr-vedligeholdelse. Det er derfor vigtigt at fastlægge:

- Den person eller det team, der er ansvarlig for indsamling af rapporter
- Hvordan og med hvem rapporter deles
- Hvordan eskalering håndteres for nyligt identificerede trusler eller uønskede blokeringer forårsaget af ASR-regler

Typiske roller og ansvarsområder omfatter:

- It-administratorer: Implementer ASR-regler, administrer udeladelse. Arbejd med forskellige forretningsenheder på apps og processer. Samler og deler rapporter til interessenter
- Csoc-analytiker (Certified Security Operations Center): Ansvarlig for at investere højprioritetsbaserede, blokerede processer for at afgøre, om truslerne er gyldige eller ej
- Chief Information Security Officer (CISO): Ansvarlig for organisationens overordnede sikkerhed og tilstand

## <a name="ring-deployment"></a>Ringinstallation

Til store virksomheder anbefaler Microsoft at udrulle ASR-regler i "ringe". Ringe er grupper af enheder, der visuelt er repræsenteret som koncentriske cirkler, der udad som ikke-overlappende træringe. Når den inderste ring er installeret, kan du skifte den næste ring til testfasen. Grundig vurdering af dine forretningsenheder, ASR-regler for vindere, apps og processer er afgørende for at definere dine ringe.
I de fleste tilfælde vil din organisation have designede installationsringe til faseopderede implementeringer af Windows opdateringer. Du kan bruge dit eksisterende ringdesign til at implementere ASR-regler.
Se: [Oprette en udrulningsplan for Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Flere emner i denne installationssamling

[Oversigt over ASR-regler for installation](attack-surface-reduction-rules-deployment.md)

[Fase 2: Test](attack-surface-reduction-rules-deployment-phase-2.md)

[Fase 3: Implementer](attack-surface-reduction-rules-deployment-phase-3.md)

[Fase 4: Drift](attack-surface-reduction-rules-deployment-phase-4.md)
