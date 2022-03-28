---
title: Planlæg antivirusscanninger ved hjælp af PowerShell
description: Planlæg antivirusscanninger ved hjælp af PowerShell
keywords: hurtig scanning, fuld scanning, antivirus, tidsplan, PowerShell
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
ms.openlocfilehash: e1cbdd156306d7cc2ee41fd85baadb1fa51cf1ac
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597966"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planlæg antivirusscanninger ved hjælp af PowerShell

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Denne artikel beskriver, hvordan du konfigurerer planlagte scanninger ved hjælp af PowerShell-cmdlet'er. Hvis du vil have mere at vide om planlægning af scanninger og om scanningstyper, skal du se Konfigurer Microsoft Defender Antivirus [scanninger](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Brug PowerShell-cmdlet'er til at planlægge scanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Få mere at vide under Brug [PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>PowerShell-cmdlet'er til planlægning af scanninger, når et slutpunkt ikke er i brug

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/).

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, imødekommer scanninger ikke CPU-begrænsningskonfigurationen og udnytter de tilgængelige ressourcer til at fuldføre scanningen så hurtigt som muligt.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>PowerShell-cmdlet'er til planlægning af scanninger for at fuldføre afhjælpningen

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>PowerShell-cmdlet'er til planlægning af daglige scanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Du kan finde flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus, under Brug [PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus [og Defender Antivirus-cmdlet'er](/powershell/module/defender/).
