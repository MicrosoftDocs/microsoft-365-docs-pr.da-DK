---
title: Konfigurere Microsoft Defender Antivirus-funktioner
description: Du kan konfigurere Microsoft Defender Antivirus funktioner med Intune, Microsoft Endpoint Configuration Manager, Gruppepolitik og PowerShell.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, konfigurer, konfiguration, Konfigurationsstyring, Microsoft Endpoint Configuration Manager, SCCM, Intune, MDM, administration af mobilenheder, GP, gruppepolitik, PowerShell
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
ms.date: 10/14/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8a1aa78a153e11f1a36fe9f7dcbd85322e6f258d
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787946"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Konfigurere Microsoft Defender Antivirus-funktioner


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan konfigurere Microsoft Defender Antivirus med en række værktøjer, f.eks.:

- Microsoft Endpoint Manager (herunder Microsoft Intune og Microsoft Endpoint Configuration Manager)
- Gruppepolitik
- PowerShell-cmdlet'er
- WMI (Windows Management Instrumentation)
- [Lejer vedhæft](/mem/configmgr/tenant-attach/)

Følgende brede kategorier af funktioner kan konfigureres:

- Skybaseret beskyttelse. Se [Skybaseret beskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

- Altid i realtid, herunder adfærdsbaseret, heuristisk og maskinel indlæringsbaseret beskyttelse. Se [Konfigurer adfærdsbaseret, heuristisk og beskyttelse i realtid](configure-protection-features-microsoft-defender-antivirus.md).

- Sådan interagerer slutbrugerne med klienten på individuelle slutpunkter. Se følgende ressourcer:
  - [Undgå, at brugerne får vist eller interagerer med den Microsoft Defender Antivirus brugergrænseflade](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Undgå eller tillad, at brugerne ændrer Microsoft Defender Antivirus politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Gennemse [Referenceemner for administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)