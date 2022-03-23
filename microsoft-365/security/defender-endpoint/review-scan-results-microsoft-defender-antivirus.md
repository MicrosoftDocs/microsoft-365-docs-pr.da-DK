---
title: Gennemse resultaterne af Microsoft Defender Antivirus scanninger
description: Gennemse resultaterne af scanninger ved hjælp Microsoft Endpoint Configuration Manager, Microsoft Intune eller Windows Sikkerhed appen
keywords: scanningsresultater, afhjælpning, fuld scanning, hurtig scanning
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
ms.openlocfilehash: 79c435618f03a8bdbd69638c66b728597cd63cab
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593828"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Gennemse Microsoft Defender Antivirus scanningsresultater

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når en Microsoft Defender Antivirus scanningen er fuldført, uanset om det er en [](run-scan-microsoft-defender-antivirus.md) scanning efter behov eller [planlagt, optages](scheduled-catch-up-scans-microsoft-defender-antivirus.md) resultaterne, og du kan få vist resultaterne. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Brug Konfigurationsstyring til at gennemse scanningsresultater

Se [Sådan overvåges Endpoint Protection status](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Brug PowerShell-cmdlet'er til at gennemse scanningsresultater

Følgende cmdlet returnerer hver registrering på slutpunktet. Hvis der er flere registreringer af den samme trussel, angives hver registrering separat baseret på tidspunktet for hver registrering:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="skærmbillede af PowerShell-cmdlet'er og -output.":::

Du kan angive, `-ThreatID` at outputtet kun skal vise registreringerne for en bestemt trussel.

Hvis du vil oprette en liste over trusselsregistreringer, men kombinere registreringer af den samme trussel til et enkelt element, kan du bruge følgende cmdlet:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="PowerShell-kode.":::

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Brug Windows management instruction (WMI) til at gennemse scanningsresultater

Brug metoden [**Hent** fra MSFT_MpThreat **og MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) klasser.


## <a name="related-articles"></a>Relaterede artikler

- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
