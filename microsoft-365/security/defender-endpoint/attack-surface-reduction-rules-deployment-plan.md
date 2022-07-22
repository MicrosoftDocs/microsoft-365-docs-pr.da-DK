---
title: Planlæg udrulning af reduktion af angrebsoverflade (ASR)
description: Indeholder en vejledning i, hvordan du planlægger udrulningen af asr-regler (Attack Surface Reduction).
keywords: Installation af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, forebyggelsessystem for værtsindtrængen, beskyttelsesregler, regler for bekæmpelse af udnyttelse, anti-exploit, udnyttelsesregler, regler til forebyggelse af infektion, Microsoft Defender for Endpoint, konfigurer ASR-regler
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
- M365-security-compliance
- m365solution-asr-rules
ms.date: 1/18/2022
ms.openlocfilehash: b4617b6a0eeed7013f024c895afed12005ed95c3
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66970138"
---
# <a name="plan-attack-surface-reduction-asr-rules-deployment"></a>Planlæg udrulning af reduktion af angrebsoverflade (ASR)

Når du tester ASR-regler (Attack Surface Reduction), er det vigtigt at starte med den rigtige forretningsenhed. Du skal starte med en lille gruppe personer i en bestemt afdeling. Du kan identificere nogle ASR-mestre i en bestemt forretningsenhed, der kan give virkelige verden indflydelse på ASR-reglerne og hjælpe dig med at tilpasse implementeringen.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="Planlægningstrinnene for ASR-regler" lightbox="images/asr-rules-planning-steps.png":::

## <a name="start-with-the-right-business-unit"></a>Start med den rigtige afdeling

Den måde, du vælger forretningsenheden for at udrulle udrulningen af ASR-regler på, afhænger af faktorer som:

- Afdelingsstørrelse
- Tilgængelighed af asr-regel mestre  
- Distribution og brug af:
  - Software
  - Delte mapper
  - Brug af scripts
  - Office-makroer
  - Andre enheder, der påvirkes af ASR-regler

Afhængigt af dine forretningsbehov kan du vælge at inkludere flere forretningsenheder for at få et bredt udsnit af software, delte mapper, scripts, makroer osv. Omvendt kan du vælge at begrænse omfanget af udrulningen af dine første ASR-regler til en enkelt afdeling og derefter gentage udrulningsprocessen for hele ASR-reglerne til dine andre afdelinger én ad gangen.

## <a name="identify-asr--rules-champions"></a>Identificer asr-regler for mestre

ASR-regler mestre er medlemmer i din organisation, der hjælper med den indledende udrulning af ASR-regler i de indledende test- og implementeringsfaser. Dine mestre er typisk medarbejdere, der er mere teknisk dygtige, og som ikke afspores af forbigående afbrydelser i arbejdsflowet. Mestrenes engagement vil fortsætte i hele den bredere udvidelse af ASR-regler udrulning til din organisation. Mestrene af dine ASR-regler er de første til at opleve hvert niveau af udrulningen af ASR-regler.

Det er vigtigt at give en feedback- og svarkanal til dine asr-regler, som mestrer for at advare dig om asr-regelrelaterede arbejdsforstyrrelser og modtage asr-regeludrulningsrelateret kommunikation.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Få en oversigt over line of business-apps, og forstå forretningsprocesforløbene

Det er afgørende for en vellykket installation af ASR-regler, at du har en fuld forståelse af de programmer og processer pr. afdeling, der bruges på tværs af organisationen. Derudover er det vigtigt, at du forstår, hvordan disse apps bruges i de forskellige forretningsenheder i din organisation.
Til at starte med skal du få en oversigt over de apps, der er godkendt til brug på tværs af hele organisationen. Du kan bruge værktøjer som f.eks. Microsoft 365 Apps Administration til at hjælpe dig med at udarbejde softwareprogrammer. Se: [Oversigt over lagerbeholdning i Microsoft 365 Apps Administration](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Definer rollerne og ansvarsområderne for rapporterings- og svarteamet

En klar formuleret rolle og ansvar for de personer, der er ansvarlige for overvågning og kommunikation af ASR-reglers status og aktivitet, er en central aktivitet i asr-vedligeholdelsen. Det er derfor vigtigt at fastslå:

- Den person eller det team, der er ansvarlig for indsamling af rapporter
- Sådan og med hvem rapporter deles
- Hvordan eskalering håndteres for nyligt identificerede trusler eller uønskede blokeringer forårsaget af ASR-regler

Typiske roller og ansvarsområder omfatter:

- It-administratorer: Implementer ASR-regler, administrer undtagelser. Arbejd med forskellige forretningsenheder i apps og processer. Samle og dele rapporter med interessenter
- Csoc-analytiker (Certified Security Operations Center): Ansvarlig for at investere i blokerede processer med høj prioritet for at fastslå, om truslen er gyldig eller ej
- CISO (Chief Information Security Officer): Ansvarlig for organisationens overordnede sikkerhedsholdning og sundhed

## <a name="ring-deployment"></a>Ring udrulning

For store virksomheder anbefaler Microsoft at implementere ASR-regler i "ringe". Ringe er grupper af enheder, der visuelt repræsenteres som koncentriske cirkler, der udstråler udad som ikke-overlappende træringe. Når den inderste ring er udrullet, kan du overføre den næste ring til testfasen. En grundig vurdering af dine forretningsenheder, mestre, apps og processer i ASR-regler er altafgørende for at definere dine ringe.
I de fleste tilfælde har din organisation designet udrulningsringe til faseinddelte udrulninger af Windows-opdateringer. Du kan bruge dit eksisterende ringdesign til at implementere ASR-regler.
Se: [Opret en installationsplan til Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Yderligere emner i denne installationssamling

[Udrulningsoversigt til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md)

[Regler for testreduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-test.md)

[Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md)

[Operationaliser regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-operationalize.md)

[Henvisning til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)
