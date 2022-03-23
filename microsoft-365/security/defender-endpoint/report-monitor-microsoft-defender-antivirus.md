---
title: Overvåg og rapportér om Microsoft Defender Antivirus beskyttelse
description: Brug Konfigurationsstyring eller sikkerhedsoplysninger og værktøjer til begivenhedsstyring (SIEM) til at bruge rapporter og overvåge Microsoft Defender AV med PowerShell og WMI.
keywords: siem, monitor, rapport, Microsoft Defender AV
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
ms.openlocfilehash: 8d801daed1ae9884d10d6a4eec7059096333ec6f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592372"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Rapport om Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus er indbygget i Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016. Microsoft Defender Antivirus er din næste generations beskyttelse i Microsoft Defender til slutpunkt. Næste generations beskyttelse beskytter dine enheder mod softwaretrusler som virus, malware og spyware på tværs af mail, apps, skyen og internettet.

Med Microsoft Defender Antivirus har du flere muligheder for at gennemse beskyttelsesstatus og beskeder. Du kan bruge Microsoft Endpoint Manager til [at overvåge Microsoft Defender Antivirus](/configmgr/protect/deploy-use/monitor-endpoint-protection) [eller oprette mailbeskeder](/configmgr/protect/deploy-use/endpoint-configure-alerts). Eller du kan overvåge beskyttelsen ved hjælp [Microsoft Intune](/intune/introduction-intune).

Hvis du har en tredjepartssikkerhedsoplysninger og begivenhedsstyringsserver (SIEM), kan du også bruge Windows Defender [klienthændelser](/windows/win32/events/windows-events).

Windows hændelser består af flere forskellige kilder til sikkerhedshændelser, herunder SECURITY Account Manager-hændelser (udvidet [til Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), se også emnet Sikkerhedsrevision[](/windows/device-security/auditing/security-auditing-overview)) [og Windows Defender hændelser](troubleshoot-microsoft-defender-antivirus.md).

Disse begivenheder kan samles centralt ved hjælp af Windows [event collector](/windows/win32/wec/windows-event-collector). Ofte har SIEM-servere forbindelser til Windows hændelser, så du kan korrelere alle sikkerhedshændelser på din SIEM-server.

Du kan også [overvåge malwarehændelser ved hjælp af løsningen til vurdering af malware i Log analytics](/azure/log-analytics/log-analytics-malware).

Du kan finde oplysninger om overvågning eller fastlæggelse af status med PowerShell, WMI eller Microsoft Azure i [tabellen (Indstillinger for installation, administration og rapportering)](deploy-manage-report-microsoft-defender-antivirus.md#ref2).

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
