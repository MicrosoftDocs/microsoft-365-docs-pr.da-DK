---
title: Aktivér og konfigurer beskyttelsesfunktioner for Microsoft Defender Antivirus
description: Aktivér adfærdsbaseret, heuristisk og beskyttelse i realtid i Microsoft Defender AV.
keywords: heuristisk, maskinel indlæring, adfærdsovervågning, beskyttelse i realtid, always-on, Microsoft Defender Antivirus, antimalware, sikkerhed, defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 59754ac5186b87045e8126114fd7342f5aa9532c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788848"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus 

**Platforme**
- Windows

Microsoft Defender Antivirus bruger flere metoder til at yde trusselsbeskyttelse:

- Cloudbeskyttelse til registrering og blokering af nye og nye trusler næsten øjeblikkeligt
- Altid ved scanning, brug af overvågning af fil- og procesadfærd og andre heuristik (også kendt som "beskyttelse i realtid")
- Dedikerede beskyttelsesopdateringer baseret på maskinel indlæring, analyse af menneskelige og automatiserede big data og dybdegående forskning i trusselsresistens

Du kan konfigurere, hvordan Microsoft Defender Antivirus bruger disse metoder med Gruppepolitik, System Center Configuration Manage, PowerShell-cmdlet'er og WMI (Windows Management Instrumentation).

I dette afsnit beskrives konfigurationen af scanning, der altid er slået til, herunder hvordan du registrerer og blokerer apps, der anses for at være usikre, men som muligvis ikke registreres som malware.

Se [Brug næste generations Microsoft Defender Antivirus-teknologier via cloudbeskyttelse](cloud-protection-microsoft-defender-antivirus.md) for at få oplysninger om, hvordan du aktiverer og konfigurerer Microsoft Defender Antivirus cloudbeskyttelse.

## <a name="in-this-section"></a>I dette afsnit

| Emne|Beskrivelse |
|---|---|
| [Find og bloker potentielt uønskede programmer](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Registrer og bloker apps, der kan være uønskede på dit netværk, f.eks. adware, browsermodifikatorer og værktøjslinjer samt rogue- eller falske antivirusapps |
| [Aktivér og konfigurer funktioner til Microsoft Defender Antivirus beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md)|Aktivér og konfigurer beskyttelse i realtid, heuristik og andre altid tændte Microsoft Defender Antivirus overvågningsfunktioner |

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
