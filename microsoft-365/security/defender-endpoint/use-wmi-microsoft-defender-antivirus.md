---
title: Konfigurer Microsoft Defender Antivirus med WMI
description: Få mere at vide om, hvordan du konfigurerer og administrerer Microsoft Defender Antivirus ved hjælp af WMI-scripts til at hente, redigere og opdatere indstillinger i Microsoft Defender for Endpoint.
keywords: wmi, scripts, instrumentering af Windows-styring, konfiguration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 8ef8355afe3019c2a179f59d83faddac4aa5792a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418996"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug WMI (Windows Management Instrumentation) til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

WMI (Windows Management Instrumentation) er en scriptgrænseflade, der giver dig mulighed for at hente, redigere og opdatere indstillinger.

Læs mere om WMI i [biblioteket Microsoft Developer Network System Administration](/windows/win32/wmisdk/wmi-start-page).

Microsoft Defender Antivirus har en række specifikke WMI-klasser, der kan bruges til at udføre de fleste af de samme funktioner som Gruppepolitik og andre administrationsværktøjer. Mange af klasserne er analoge med [Defender for Cloud PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md).

[Referencebiblioteket for MSDN Windows Defender WMIv2 Provider](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) viser de tilgængelige WMI-klasser til Microsoft Defender Antivirus og indeholder eksempelscripts.

Ændringer, der foretages med WMI, påvirker lokale indstillinger på det slutpunkt, hvor ændringerne installeres eller foretages. Det betyder, at udrulninger af politikker med Gruppepolitik, Microsoft Endpoint Configuration Manager eller Microsoft Intune kan overskrive ændringer, der er foretaget med WMI. 

Du kan [konfigurere, hvilke indstillinger der kan tilsidesættes lokalt med tilsidesættelser af lokale politikker](configure-local-policy-overrides-microsoft-defender-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-topics"></a>Relaterede emner

- [Referenceemner om administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
