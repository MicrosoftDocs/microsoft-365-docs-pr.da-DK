---
title: Gendan filer i karantæne i Microsoft Defender Antivirus
description: Du kan gendanne filer og mapper, der er sat i karantæne af Microsoft Defender Antivirus.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/19/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 14b6f6812e88a49220230e0e422d5c95f90fe187
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790586"
---
# <a name="restore-quarantined-files-in-microsoft-defender-antivirus"></a>Gendan filer i karantæne i Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Hvis Microsoft Defender Antivirus er konfigureret til at registrere og afhjælpe trusler på din enhed, Microsoft Defender Antivirus sætte mistænkelige filer i karantæne. Hvis du er sikker på, at en karantænefil ikke er en trussel, kan du gendanne den.

1. Åbn **Windows Sikkerhed**.
2. Vælg **Virus & trusselsbeskyttelse,** og klik derefter på **Beskyttelseshistorik**.
3. På listen over alle de seneste elementer skal du filtrere efter **Elementer i karantæne**.
4. Vælg et element, du vil beholde, og udfør en handling, f.eks. gendannelse.

> [!TIP]
> Du kan også gendanne en fil fra karantæne ved hjælp af kommandoprompten. Se [Gendan en fil fra karantæne](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#restore-file-from-quarantine). 

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

- [Konfigurer afhjælpning for scanninger](configure-remediation-microsoft-defender-antivirus.md)
- [Gennemse scanningsresultater](review-scan-results-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)