---
title: Kør og tilpas planlagte scanninger og scanninger efter behov.
description: Tilpas og initier Microsoft Defender Antivirus scanninger på slutpunkter på tværs af dit netværk
keywords: scan, planlæg, tilpas, udeladelse, udelad filer, afhjælpning, scanningsresultater, karantæne, fjern trussel, hurtig scanning, fuld scanning, Microsoft Defender Antivirus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9acac2868b0bd2449338f4a61f663d8cfe8a8ee4
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63597878"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan bruge Gruppepolitik, PowerShell og Windows Management Instrumentation (WMI) til at konfigurere Microsoft Defender Antivirus scanninger. 

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
---|---
[Konfigurere og validere fil-, mappe- og procesåbnede filude udeladelses Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md) | Du kan udelade filer (herunder filer, der er ændret af angivne processer) og mapper fra scanninger efter behov, planlagte scanninger og altid beskyttelse i realtid samt overvågning og scanning
[Konfigurere Microsoft Defender Antivirus indstillinger for scanning](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Du kan konfigurere Microsoft Defender Antivirus til at medtage visse typer maillagringsfiler, sikkerhedskopierings- eller genparspunkter og arkiverede filer (f.eks. .zip filer) i scanninger. Du kan også aktivere scanning af netværksfil
[Konfigurer afhjælpning af scanninger](configure-remediation-microsoft-defender-antivirus.md) | Konfigurer, Microsoft Defender Antivirus skal gøre, når der registreres en trussel, og hvor længe filer, der er i karantæne, skal opbevares i karantænemappen
[Konfigurere planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Konfigurer tilbagevendende (planlagte) scanninger, herunder hvornår de skal køre, og om de kører som fulde scanninger eller hurtige scanninger
[Konfigurere og køre scanninger](run-scan-microsoft-defender-antivirus.md) | Kør og konfigurer scanninger efter behov ved hjælp af PowerShell, Windows Management Instrumentation eller individuelt på slutpunkter med Windows Sikkerhed-appen
[Gennemse scanningsresultater](review-scan-results-microsoft-defender-antivirus.md) | Gennemse resultaterne af scanninger ved hjælp Microsoft Endpoint Configuration Manager, Microsoft Intune eller Windows Sikkerhed appen