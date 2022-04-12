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
ms.openlocfilehash: 8961428acee5d166b0cdad4982aa5f9ed48020af
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788826"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>Planlæg antivirusscanninger ved hjælp af PowerShell

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

I denne artikel beskrives det, hvordan du konfigurerer planlagte scanninger ved hjælp af PowerShell-cmdlet'er. Hvis du vil vide mere om planlægning af scanninger og scanningstyper, skal du se [Konfigurer planlagte hurtig- eller komplette Microsoft Defender Antivirus scanninger](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>Brug PowerShell-cmdlet'er til at planlægge scanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre cmdlet'er til Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) og [Defender Antivirus](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>PowerShell-cmdlet'er til planlægning af scanninger, når et slutpunkt ikke er i brug

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, overholder scanningerne ikke CPU-begrænsningskonfigurationen og drager fuld fordel af de ressourcer, der er tilgængelige til at fuldføre scanningen så hurtigt som muligt.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>PowerShell-cmdlet'er til planlægning af scanninger for at fuldføre afhjælpningen

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>PowerShell-cmdlet'er til planlægning af daglige scanninger

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

Du kan få flere oplysninger om, hvordan du bruger PowerShell sammen med Microsoft Defender Antivirus i [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)