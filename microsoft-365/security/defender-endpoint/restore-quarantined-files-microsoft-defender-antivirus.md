---
title: Gendan filer, der er sat i karantæne, Microsoft Defender Antivirus
description: Du kan gendanne filer og mapper, der er blevet sat i karantæne af Microsoft Defender Antivirus.
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
ms.openlocfilehash: 717efaff970165c52c15e0422e6e2be4bc832d00
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63595883"
---
# <a name="restore-quarantined-files-in-microsoft-defender-antivirus"></a>Gendan filer, der er sat i karantæne, Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis Microsoft Defender Antivirus er konfigureret til at registrere og afhjælpe trusler på din enhed, skal Microsoft Defender Antivirus sætte mistænkelige filer i karantæne. Hvis du er sikker på, at en fil, der er sat i karantæne, ikke er en trussel, kan du gendanne den.

1. Åbn **Windows Sikkerhed**.
2. Vælg **Virusbeskyttelse& og** klik derefter på **historikken for beskyttelse**.
3. På listen over alle seneste elementer skal du filtrere efter Elementer, der **er sat i karantæne**.
4. Vælg et element, du vil beholde, og gør en handling, f.eks. gendan.

> [!TIP]
> Du kan også gendanne en fil fra karantæne ved hjælp af Kommandoprompt. Se [Gendan en fil fra karantæne](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#restore-file-from-quarantine). 

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer afhjælpning af scanninger](configure-remediation-microsoft-defender-antivirus.md)
- [Gennemse scanningsresultater](review-scan-results-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse af filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)