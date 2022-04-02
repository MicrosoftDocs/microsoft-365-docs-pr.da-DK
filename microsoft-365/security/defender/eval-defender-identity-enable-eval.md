---
title: Aktivér evalueringsmiljøet for Microsoft Defender for Identity
description: Konfigurer Microsoft Defender for Identity i Microsoft 365 Defender prøveversion eller pilotmiljø ved at installere & konfigurere sensoren og finde lokale administratorer på andre computere.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1be194035348bb8d414b37f16399fdcffe406063
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755035"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Aktivér evalueringsmiljøet for Microsoft Defender for Identity

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-identity-overview.md) i oprettelsen af evalueringsmiljøet for Microsoft Defender for Identity. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-identity-overview.md).

Brug følgende trin til at konfigurere dit Microsoft Defender for Identity-miljø. 

:::image type="content" source="../../media/defender/m365-defender-identity-eval-enable-steps.png" alt-text="Disse trin til at aktivere Microsoft Defender for Identity i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-identity-eval-enable-steps.png":::

- [Trin 1. Konfigurer forekomsten Defender for Identity](#step-1-set-up-the-defender-for-identity-instance)
- [Trin 2. Installer og konfigurer sensoren](#step-2-install-and-configure-the-sensor)
- [Trin 3. Konfigurer hændelseslogfiler og proxyindstillinger på maskiner med sensoren](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Trin 4. Tillad, at Defender for Identity identificerer lokale administratorer på andre computere](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Trin 1. Konfigurer forekomsten Defender for Identity

Log på Defender for Identity-portalen for at oprette din forekomst, og forbind derefter denne forekomst til dit Active Directory-miljø. 

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Oprette forekomsten Defender for Identity        | [Hurtig start: Oprette din Microsoft Defender for Identity-forekomst](/defender-for-identity/install-step1)        |
|2     | Forbind forekomsten Defender for Identity til Active Directory-skoven   | [Hurtig start: Forbind til dit Active Directory-område](/defender-for-identity/install-step2)  |

## <a name="step-2-install-and-configure-the-sensor"></a>Trin 2. Installer og konfigurer sensoren

Derefter skal du downloade, installere og konfigurere Defender for Identity-sensoren på domænecontrollere og AD FS-servere i dit lokale miljø.

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Bestem, hvor mange Microsoft Defender til identitetssensorer du skal bruge.        | [Planlæg kapacitet for Microsoft Defender for Identity](/defender-for-identity/capacity-planning)   |
|2     | Download sensorkonfigurationspakken  |  [Hurtig start: Download konfigurationspakken til Microsoft Defender for Identity-sensoren](/defender-for-identity/install-step3)   |
|3     | Installer Defender for Identity-sensoren    |  [Hurtig start: Installer Microsoft Defender for Identity-sensoren](/defender-for-identity/install-step4)       |
|4     | Konfigurer sensoren       |  [Konfigurer indstillinger for Microsoft Defender for Identity-sensor ](/defender-for-identity/install-step5)   |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Trin 3. Konfigurer hændelseslogfiler og proxyindstillinger på maskiner med sensoren

På de maskiner, som du har installeret sensoren på, skal du konfigurere Windows gruppe af hændelseslogfiler og indstillinger for internetproxyer for at aktivere og forbedre registreringsfunktioner.

|  Trin | Beskrivelse     |Flere oplysninger  |
|---------|---------|---------|
|1     | Konfigurere Windows gruppe af hændelseslogfiler         | [Konfigurere Windows begivenhedssamling](/defender-for-identity/configure-windows-event-collection)        |
|2     | Konfigurere indstillinger for internetproxy        | [Konfigurer indstillinger for slutpunktsproxy og internetforbindelse for din Microsoft Defender for Identity Sensor](/defender-for-identity/configure-proxy)        |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Trin 4. Tillad, at Defender for Identity identificerer lokale administratorer på andre computere

Registrering af lateral bevægelsessti for Microsoft Defender for Identity afhænger af forespørgsler, der identificerer lokale administratorer på bestemte computere. Disse forespørgsler udføres med SAM-R-protokollen ved hjælp af kontoen Defender for Identity Service. 

For at sikre at Windows-klienter og -servere tillader, at din Defender for Identity-konto udfører SAM-R, skal der foretages en ændring af Gruppepolitik for at tilføje tjenestekontoen Defender for Identity ud over de konfigurerede konti, der er angivet i politikken for netværksadgang. Sørg for at anvende gruppepolitikker på alle computere undtagen **domænecontrollere**.

Du kan finde en vejledning til, hvordan du gør dette [, under Konfigurer Microsoft Defender for Identity til at foretage fjernopkald til SAM](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: [Pilot på Microsoft Defender for Identity](eval-defender-identity-pilot.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Identity](eval-defender-identity-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
