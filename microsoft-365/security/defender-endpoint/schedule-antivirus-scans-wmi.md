---
title: Planlæg antivirusscanninger ved hjælp af Windows Management Instrumentation
description: Planlæg antivirusscanninger ved hjælp af WMI
keywords: hurtig scanning, fuld scanning, WMI, tidsplan, antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 2b25876a43dea3b1598d4bdfa89cf4724c0fca14
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788914"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planlæg antivirusscanninger ved hjælp af WMI (Windows Management Instrumentation)

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

I denne artikel beskrives det, hvordan du konfigurerer planlagte scanninger ved hjælp af WMI. Hvis du vil vide mere om planlægning af scanninger og scanningstyper, skal du se [Konfigurer planlagte hurtig- eller komplette Microsoft Defender Antivirus scanninger](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Brug WMI (Windows Management Instruction) til at planlægge scanninger

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Du kan få flere oplysninger og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI til planlægning af scanninger, når et slutpunkt ikke er i brug

Brug [metoden Set for klassen MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) for følgende egenskaber:

```WMI
ScanOnlyIfIdleEnabled
```

Du kan få flere oplysninger om API'er og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, overholder scanningerne ikke CPU-begrænsningskonfigurationen og drager fuld fordel af de ressourcer, der er tilgængelige til at fuldføre scanningen så hurtigt som muligt.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI til planlægning af scanninger for at fuldføre afhjælpning

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Du kan få flere oplysninger og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI til planlægning af daglige scanninger

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ScanScheduleQuickScanTime
```

Du kan få flere oplysninger og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)