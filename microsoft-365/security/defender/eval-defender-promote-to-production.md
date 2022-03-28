---
title: Trin 7. Ynde dit Microsoft 365 Defender-evalueringsmiljø til produktion
description: Brug denne artikel til at promovere dine fordampninger af MDI, MDO, MDE og Defender til skyapps til dit livemiljø i Microsoft 365 Defender eller M365D.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 47f36d965c9b2b6ef5f106c590e47fe0251163d8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596834"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>Trin 7. Fremme dit Microsoft 365 Defender evalueringsmiljø til produktion

**Gælder for:**
- Microsoft 365 Defender

Hvis du vil promovere dit Microsoft 365 Defender til produktion, skal du først købe den nødvendige licens. Følg trinnene i [Opret eval-miljøet,](eval-create-eval-environment.md) og køb Office 365 E5 licensen (i stedet for at vælge Start gratis prøveversion).

Dernæst skal du fuldføre enhver yderligere konfiguration og udvide dine pilotgrupper, indtil disse har nået fuld produktion.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Defender for Identity kræver ikke yderligere konfiguration. Du skal blot sikre dig, at du har købt de nødvendige licenser og installeret sensoren på alle dine Active Directory-domænecontrollere og AD FS-servere (Active Directory Federation Services).

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender til Office 365

Når du har evalueret eller piloteret MDO, kan den promoveres til hele produktionsmiljøet.

1. Køb og klargør de nødvendige licenser, og tildel dem til produktionsbrugere.
2. Kør anbefalede politikkonfigurationer for grundlinjer (enten Standard eller Streng) mod dit produktionsmaildomæne eller bestemte grupper af brugere.
3. Du kan også oprette og konfigurere eventuelle brugerdefinerede MDO-politikker i forhold til dit produktionsmaildomæne eller grupper af brugere.  Husk dog, at alle tildelte oprindelige politikker altid tilsidesætter brugerdefinerede politikker.
4. Opdater den offentlige MX-post for dit produktionsmaildomæne for at blive løst direkte til EOP.
5. Afslut alle SMTP-gateways fra tredjepart, og deaktiver eller slet eventuelle EXO-forbindelser, der er knyttet til denne relay.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender til Slutpunkt

Hvis du vil promovere Microsoft Defender til slutpunktsevalueringsmiljø fra et pilotprojekt til en produktion, skal du blot onboarde flere slutpunkter til tjenesten ved hjælp af et af de [understøttede værktøjer og metoder](../defender-endpoint/onboard-configure.md).

Brug følgende generelle retningslinjer til at tilføje flere enheder på Microsoft Defender for Endpoint.

1. Kontrollér, at enheden opfylder [minimumskravene](../defender-endpoint/minimum-requirements.md).
2. Afhængigt af enheden skal du følge de konfigurationstrin, der er angivet i onboardingsektionen i Defender for Endpoint-portalen.
3. Brug det relevante administrationsværktøj og installationsmetode til dine enheder.
4. Kør en registreringstest for at bekræfte, at enhederne er korrekt onboardet og rapporterer til tjenesten.

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender til skyapps

Microsoft Defender til skyapps kræver ikke yderligere konfiguration. Bare sørg for, at du har købt de nødvendige licenser. Hvis du har begrænset installationen til bestemte brugergrupper, skal du øge omfanget af disse grupper, indtil du når produktionsskalaen.
