---
title: Administrer Microsoft Defender Antivirus i din virksomhed
description: Få mere at vide om, hvordan du bruger Gruppepolitik, Configuration Manager, PowerShell, WMI, Intune og kommandolinjen til at administrere Microsoft Defender AV
keywords: gruppepolitik, gpo, config manager, sccm, scep, powershell, wmi, intune, defender, antivirus, antimalware, sikkerhed, beskyttelse
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
ms.openlocfilehash: 76f6f1cda9b2def0c18be8c368da15645994eece
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787968"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Administrer Microsoft Defender Antivirus i din virksomhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan administrere og konfigurere Microsoft Defender Antivirus med følgende værktøjer:

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (nu en del af Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (nu en del af Microsoft Endpoint Manager)
- [Gruppepolitik](./use-group-policy-microsoft-defender-antivirus.md)
- [PowerShell-cmdlet'er](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [WMI (Windows Management Instrumentation)](./use-wmi-microsoft-defender-antivirus.md)
- [Kommandolinjeværktøjet Microsoft Malware Protection](./command-line-arguments-microsoft-defender-antivirus.md) (kaldet *mpcmdrun.exe* utility

Følgende artikler indeholder flere oplysninger, links og ressourcer til brug af disse værktøjer til at administrere og konfigurere Microsoft Defender Antivirus.

|Artikel|Beskrivelse|
|:---|:---|
|[Administrer Microsoft Defender Antivirus med Microsoft Intune og Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Oplysninger om brug af Intune og Configuration Manager til at installere, administrere, rapportere og konfigurere Microsoft Defender Antivirus|
|[Administrer Microsoft Defender Antivirus med indstillinger for Gruppepolitik](use-group-policy-microsoft-defender-antivirus.md)|Liste over alle Gruppepolitik indstillinger, der er placeret i ADMX-skabeloner|
|[Administrer Microsoft Defender Antivirus med PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instruktioner til brug af PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus samt links til dokumentation for alle cmdlet'er og tilladte parametre|
|[Administrer Microsoft Defender Antivirus med WMI (Windows Management Instrumentation)](use-wmi-microsoft-defender-antivirus.md)|Instruktioner til brug af WMI til at administrere Microsoft Defender Antivirus samt links til dokumentation til WMIv2-API'er (herunder alle klasser, metoder og egenskaber)|
|[Administrer Microsoft Defender Antivirus med kommandolinjeværktøjet MpCmdRun.exe](command-line-arguments-microsoft-defender-antivirus.md)|Instruktioner om brug af det dedikerede kommandolinjeværktøj til at administrere og bruge Microsoft Defender Antivirus|

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)