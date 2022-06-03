---
title: Overvåg og rapportér om Microsoft Defender Antivirus beskyttelse
description: Brug siem-værktøjer (Configuration Manager eller sikkerhedsoplysninger og hændelsesstyring) til at forbruge rapporter og overvåge Microsoft Defender AV med PowerShell og WMI.
keywords: siem, monitor, report, Microsoft Defender AV
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 46abb6a11e1752934218a031993b10286d8ab420
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872242"
---
# <a name="report-on-microsoft-defender-antivirus"></a>Rapport om Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Antivirus er indbygget i Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016. Microsoft Defender Antivirus er en del af din næste generation af beskyttelse i Microsoft Defender for Endpoint. Næste generations beskyttelse hjælper med at beskytte dine enheder mod softwaretrusler som virus, malware og spyware på tværs af mail, apps, clouden og internettet.

Med Microsoft Defender Antivirus har du flere muligheder for at gennemse beskyttelsesstatus og beskeder. Du kan bruge Microsoft Endpoint Manager til at [overvåge Microsoft Defender Antivirus](/configmgr/protect/deploy-use/monitor-endpoint-protection) eller [oprette mailbeskeder](/configmgr/protect/deploy-use/endpoint-configure-alerts). Du kan også overvåge beskyttelse ved hjælp af [Microsoft Intune](/intune/introduction-intune).

Hvis du har en SIEM-server (third-party security information and event management), kan du også bruge [Windows Defender klienthændelser](/windows/win32/events/windows-events).

Windows hændelser omfatter flere kilder til sikkerhedshændelser, herunder SAM-hændelser (Security Account Manager) ([udvidet for Windows 10](/windows/whats-new/whats-new-windows-10-version-1507-and-1511), se også emnet [Sikkerhedsovervågning](/windows/security/threat-protection/auditing/security-auditing-overview)) og [Windows Defender hændelser](troubleshoot-microsoft-defender-antivirus.md).

Disse hændelser kan samles centralt ved hjælp af [den Windows hændelsessamler](/windows/win32/wec/windows-event-collector). SIEM-servere har ofte forbindelser til Windows hændelser, hvilket giver dig mulighed for at korrelere alle sikkerhedshændelser på din SIEM-server.

Du kan også [overvåge malwarehændelser ved hjælp af løsningen Til vurdering af malware i Log Analytics](/security/benchmark/azure/security-control-logging-monitoring).

Du kan finde oplysninger om overvågning eller fastlæggelse af status med PowerShell, WMI eller Microsoft Azure i [tabellen (indstillinger for installation, administration og rapportering).](deploy-manage-report-microsoft-defender-antivirus.md#ref2)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Installer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
