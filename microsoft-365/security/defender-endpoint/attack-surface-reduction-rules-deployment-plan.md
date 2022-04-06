---
title: Planlæg ASR-regler for reduktion af implementeringsregler for angrebsoverfladen
description: Giver vejledning i at planlægge udrulning af regler for reduktion af angrebsoverfladen.
keywords: Implementering af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, beskyttelsessystem til forebyggelse af indtrængen, beskyttelsesregler, anti exploit, udnyttelsesregler, regler for forebyggelse af indisk virus, Microsoft Defender for Endpoint, konfigurer ASR-regler
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
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 9342e4b3868e5bc0d5701b4a0cfa2e8f0a56937b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477319"
---
# <a name="step-1-plan-asr-rules-deployment"></a>Trin 1: Planlægge udrulning af ASR-regler

Når du tester reduktion af angrebsoverfladen (ASR), er det vigtigt at starte med den rigtige forretningsenhed. Du bør starte med en lille gruppe personer i en bestemt forretningsenhed. Du kan identificere nogle ASR-vindere inden for en bestemt forretningsenhed, som kan give den virkelige påvirkning af asr-reglerne, og hjælpe dig med at finjustere implementeringen.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="Planlægningstrinnene for ASR-regler" lightbox="images/asr-rules-planning-steps.png":::

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

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Definer rapporterings- og svarteamroller og -ansvarsområder

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

[Forudsætninger for implementering af ASR-regler](attack-surface-reduction-rules-deployment.md)

[Trin 2: Test ASR-regler](attack-surface-reduction-rules-deployment-test.md)

[Trin 3: Implementer ASR-regler](attack-surface-reduction-rules-deployment-implement.md)

[Trin 4: At drifte ASR-regler](attack-surface-reduction-rules-deployment-operationalize.md)
