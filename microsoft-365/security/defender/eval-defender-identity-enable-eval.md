---
title: Aktivér evalueringsmiljøet for Microsoft Defender for Identity
description: Konfigurer Microsoft Defender for Identity i Microsoft 365 Defender prøveversionslaboratorium eller i et pilotmiljø ved at installere & konfigurere sensoren og finde lokale administratorer på andre computere.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
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
ms.openlocfilehash: 84b893b6689385e4137778d0d787f42428843d26
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750182"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Aktivér evalueringsmiljøet for Microsoft Defender for Identity

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-identity-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Identity. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-identity-overview.md).

Brug følgende trin til at konfigurere dit Microsoft Defender for Identity miljø. 

:::image type="content" source="../../media/defender/m365-defender-identity-eval-enable-steps.png" alt-text="Trinnene til aktivering af Microsoft Defender for Identity i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-identity-eval-enable-steps.png":::

- [Trin 1. Konfigurer Defender for Identity Instance](#step-1-set-up-the-defender-for-identity-instance)
- [Trin 2. Installér og konfigurer sensoren](#step-2-install-and-configure-the-sensor)
- [Trin 3. Konfigurer hændelseslog- og proxyindstillinger på maskiner med sensoren](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Trin 4. Tillad, at Defender for Identity identificerer lokale administratorer på andre computere](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Trin 1. Konfigurer Defender for Identity Instance

Log på Defender for Identity-portalen for at oprette din forekomst, og opret derefter forbindelse mellem denne forekomst og dit Active Directory-miljø. 

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Opret defender for identitetsforekomsten        | [Hurtig start: Opret din Microsoft Defender for Identity forekomst](/defender-for-identity/install-step1)        |
|2     | Forbind Defender for Identity-forekomsten med dit Active Directory-område   | [Hurtig start: Opret forbindelse til dit Active Directory-område](/defender-for-identity/install-step2)  |

## <a name="step-2-install-and-configure-the-sensor"></a>Trin 2. Installér og konfigurer sensoren

Derefter skal du downloade, installere og konfigurere Defender for Identity-sensoren på domænecontrollere og AD FS-servere i dit lokale miljø.

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Bestem, hvor mange Microsoft Defender for Identity sensorer du har brug for.        | [Planlæg kapacitet til Microsoft Defender for Identity](/defender-for-identity/capacity-planning)   |
|2     | Download pakken til konfiguration af sensor  |  [Hurtig start: Download pakken til konfiguration af Microsoft Defender for Identity sensor](/defender-for-identity/install-step3)   |
|3     | Installér Defender for Identity-sensoren    |  [Hurtig start: Installér Microsoft Defender for Identity-sensoren](/defender-for-identity/install-step4)       |
|4     | Konfigurer sensoren       |  [Konfigurer Microsoft Defender for Identity sensorindstillinger](/defender-for-identity/install-step5)   |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Trin 3. Konfigurer hændelseslog- og proxyindstillinger på maskiner med sensoren

Konfigurer Windows-hændelseslogsamling og internetproxyindstillinger på de computere, du har installeret sensoren på, for at aktivere og forbedre registreringsfunktionerne.

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Konfigurer Windows-hændelseslogsamling         | [Konfigurer Windows-hændelsessamling](/defender-for-identity/configure-windows-event-collection)        |
|2     | Konfigurer indstillinger for internetproxy        | [Konfigurer indstillingerne for slutpunktproxy og internetforbindelse for din Microsoft Defender for Identity sensor](/defender-for-identity/configure-proxy)        |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Trin 4. Tillad, at Defender for Identity identificerer lokale administratorer på andre computere

Microsoft Defender for Identity registrering af tværgående bevægelsesstier er afhængig af forespørgsler, der identificerer lokale administratorer på bestemte maskiner. Disse forespørgsler udføres med SAM-R-protokollen ved hjælp af kontoen Defender for Identity Service. 

Hvis du vil sikre, at Windows-klienter og -servere gør det muligt for din Defender for Identity-konto at udføre SAM-R, skal der foretages en ændring af Gruppepolitik for at tilføje defender for identity-tjenestekontoen ud over de konfigurerede konti, der er angivet i politikken Netværksadgang. Sørg for at anvende gruppepolitikker på alle computere **undtagen domænecontrollere**.

Du kan finde oplysninger om, hvordan du gør dette, under [Konfigurer Microsoft Defender for Identity til at foretage fjernopkald til SAM](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: [Pilot Microsoft Defender for Identity](eval-defender-identity-pilot.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Identity](eval-defender-identity-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
