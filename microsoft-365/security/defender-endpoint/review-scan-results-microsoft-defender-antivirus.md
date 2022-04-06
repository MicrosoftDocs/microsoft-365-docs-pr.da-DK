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
ms.openlocfilehash: 8727baa9bb1935a1186907ca5f3d9d4f82dad6d4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473645"
---
# <a name="review-microsoft-defender-antivirus-scan-results"></a>Gennemse Microsoft Defender Antivirus scanningsresultater

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når en Microsoft Defender Antivirus scanningen er fuldført, uanset om det er en [](run-scan-microsoft-defender-antivirus.md) scanning efter behov eller [planlagt, optages](scheduled-catch-up-scans-microsoft-defender-antivirus.md) resultaterne, og du kan få vist resultaterne. 


## <a name="use-configuration-manager-to-review-scan-results"></a>Brug Configuration Manager til at gennemse scanningsresultater

Se [Sådan overvåges Endpoint Protection status](/configmgr/protect/deploy-use/monitor-endpoint-protection).

## <a name="use-powershell-cmdlets-to-review-scan-results"></a>Brug PowerShell-cmdlet'er til at gennemse scanningsresultater

Følgende cmdlet returnerer hver registrering på slutpunktet. Hvis der er flere registreringer af den samme trussel, angives hver registrering separat baseret på tidspunktet for hver registrering:

```PowerShell
Get-MpThreatDetection
```

:::image type="content" source="../../media/wdav-get-mpthreatdetection.png" alt-text="PowerShell-cmdlet'er og -output" lightbox="../../media/wdav-get-mpthreatdetection.png":::

Du kan angive, `-ThreatID` at outputtet kun skal vise registreringerne for en bestemt trussel.

Hvis du vil oprette en liste over trusselsregistreringer, men kombinere registreringer af den samme trussel til et enkelt element, kan du bruge følgende cmdlet:

```PowerShell
Get-MpThreat
```

:::image type="content" source="../../media/wdav-get-mpthreat.png" alt-text="PowerShell-koden" lightbox="../../media/wdav-get-mpthreat.png":::

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

## <a name="use-windows-management-instruction-wmi-to-review-scan-results"></a>Brug Windows management instruction (WMI) til at gennemse scanningsresultater

Brug metoden [**Hent** fra MSFT_MpThreat **og MSFT_MpThreatDetection**](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) klasser.


## <a name="related-articles"></a>Relaterede artikler

- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
