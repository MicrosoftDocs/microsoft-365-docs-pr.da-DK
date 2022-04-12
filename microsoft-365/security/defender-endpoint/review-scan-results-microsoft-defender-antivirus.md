---
title: Gennemse resultaterne af Microsoft Defender Antivirus scanninger
description: Gennemse resultaterne af scanninger ved hjælp af Microsoft Endpoint Configuration Manager, Microsoft Intune eller appen Windows Sikkerhed
keywords: scan resultater, afhjælpning, fuld scanning, hurtig scanning
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9ffe10560bb36c8fc1311061510f35396934e3b8
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790630"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Gennemse resultaterne Microsoft Defender Antivirus scanningen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Når en Microsoft Defender Antivirus scanning er fuldført, uanset om det er en [on-demand-scanning](run-scan-microsoft-defender-antivirus.md) eller [en planlagt scanning](scheduled-catch-up-scans-microsoft-defender-antivirus.md), registreres resultaterne, og du kan få vist resultaterne. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Brug Configuration Manager til at gennemse scanningsresultater

Se [Sådan overvåger du Endpoint Protection status](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Brug PowerShell-cmdlet'er til at gennemse scanningsresultater

Følgende cmdlet returnerer hver registrering på slutpunktet. Hvis der er flere opdagelser af den samme trussel, vises hver registrering separat baseret på tidspunktet for hver registrering:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="PowerShell-cmdlet'erne og -output" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Du kan angive `-ThreatID` , at outputtet skal begrænses til kun at vise registreringer for en bestemt trussel.

Hvis du vil angive trusselsregistreringer, men kombinere registreringer af den samme trussel i et enkelt element, kan du bruge følgende cmdlet:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="PowerShell-koden" lightbox="../../media/wdav-get-mpthreat.png":::

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Brug WMI (Windows Management Instruction) til at gennemse scanningsresultater

Brug [metoden **Get** for klasserne **MSFT_MpThreat** og **MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)


## <a name="related-articles"></a>Relaterede artikler

- [Tilpas, start og gennemse resultaterne af Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
