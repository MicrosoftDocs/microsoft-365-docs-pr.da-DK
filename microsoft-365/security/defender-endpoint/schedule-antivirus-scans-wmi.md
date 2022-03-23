---
title: Planlæg antivirusscanninger ved Windows Management Instrumentation
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
ms.openlocfilehash: be22e59f6d2be30ead354099f2cc168868959752
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592444"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>Planlæg antivirusscanninger Windows WMI (Management Instrumentation)

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

I denne artikel beskrives, hvordan du konfigurerer planlagte scanninger ved hjælp af WMI. Hvis du vil have mere at vide om planlægning af scanninger og om scanningstyper, skal du se Konfigurer Microsoft Defender Antivirus [scanninger](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>Brug Windows (WMI) til planlægning af scanninger

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

Du kan finde flere oplysninger og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI til planlægning af scanninger, når et slutpunkt ikke er i brug

Brug [metoden Angiv for MSFT_MpPreference til](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) følgende egenskaber:

```WMI
ScanOnlyIfIdleEnabled
```

Du kan finde flere oplysninger om API'er og tilladte parametre [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, imødekommer scanninger ikke CPU-begrænsningskonfigurationen og udnytter de tilgængelige ressourcer til at fuldføre scanningen så hurtigt som muligt.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI til planlægning af scanninger for at fuldføre afhjælpningen

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

Du kan finde flere oplysninger og tilladte parametre [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI til planlægning af daglige scanninger

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ScanScheduleQuickScanTime
```

Du kan finde flere oplysninger og tilladte parametre [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

