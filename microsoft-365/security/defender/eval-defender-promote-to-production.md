---
title: Trin 7. Hæv dit Microsoft 365 Defender evalueringsmiljø til produktion
description: Brug denne artikel til at hæve dine evals af MDI, MDO, MDE og Defender for Cloud Apps til dit livemiljø i Microsoft 365 Defender eller M365D.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 769a70177ada62b4dbb505a8363fe3bdbfc4a59a
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748731"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Trin 7. Hæv dit Microsoft 365 Defender evalueringsmiljø til produktion

**Gælder for:**
- Microsoft 365 Defender

Hvis du vil markedsføre dit Microsoft 365 Defender evalueringsmiljø til produktion, skal du først købe den nødvendige licens. Følg trinnene i [Opret evalueringsmiljøet](eval-create-eval-environment.md), og køb Office 365 E5-licensen (i stedet for at vælge Start gratis prøveversion).

Derefter skal du fuldføre yderligere konfiguration og udvide dine pilotgrupper, indtil disse har nået fuld produktion.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Defender for Identity kræver ikke yderligere konfiguration. Du skal blot sørge for, at du har købt de nødvendige licenser og installeret sensoren på alle dine Active Directory-domænecontrollere og Active Directory Federation Services (AD FS)-servere.

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365

Når du har evalueret eller afprøvet MDO, kan den hæves til hele dit produktionsmiljø.

1. Køb og klargør de nødvendige licenser, og tildel dem til dine produktionsbrugere.
2. Kør de anbefalede konfigurationer for oprindelig politik (enten Standard eller Strict) igen i forhold til dit produktionsmaildomæne eller bestemte grupper af brugere.
3. Du kan eventuelt oprette og konfigurere brugerdefinerede MDO-politikker i forhold til dit produktionsmaildomæne eller grupper af brugere.  Husk dog, at alle tildelte oprindelige politikker altid har forrang frem for brugerdefinerede politikker.
4. Opdater den offentlige MX-post for dit produktionsmaildomæne for at oversætte den direkte til EOP.
5. Deaktiver alle SMTP-gateways fra tredjepart, og deaktiver eller slet alle EXO-connectors, der er knyttet til dette relæ.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

For at fremme Microsoft Defender for Endpoint evalueringsmiljø fra en pilot til produktion skal du blot onboarde flere slutpunkter til tjenesten ved hjælp af et hvilket som helst af de [understøttede værktøjer og metoder](../defender-endpoint/onboard-configure.md).

Brug følgende generelle retningslinjer for at onboarde flere enheder for at Microsoft Defender for Endpoint.

1. Kontrollér, at enheden opfylder [minimumskravene](../defender-endpoint/minimum-requirements.md).
2. Afhængigt af enheden skal du følge de konfigurationstrin, der er angivet i onboardingsektionen på Defender for Endpoint-portalen.
3. Brug det relevante administrationsværktøj og den relevante installationsmetode til dine enheder.
4. Kør en registreringstest for at bekræfte, at enhederne er onboardet korrekt, og at de rapporterer til tjenesten.

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps kræver ikke yderligere konfiguration. Du skal blot sørge for, at du har købt de nødvendige licenser. Hvis du har begrænset udrulningen til bestemte brugergrupper, skal du øge omfanget af disse grupper, indtil du når produktionsskalaen.
