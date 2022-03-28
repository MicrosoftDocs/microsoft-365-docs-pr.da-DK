---
title: Konfigurere Microsoft Defender Antivirus med WMI
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender Antivirus administrerer filer ved hjælp af WMI-scripts til at hente, redigere og opdatere indstillinger i Microsoft Defender til slutpunkt.
keywords: wmi, scripts, windows management instrumentation, konfiguration
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
ms.openlocfilehash: c8057a971576d5511440ac009acd6eab55b302e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597886"
---
# <a name="use-windows-management-instrumentation-wmi-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug Windows WMI (Management Instrumentation) til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Windows Management Instrumentation (WMI) er en scriptinggrænseflade, der gør det muligt at hente, ændre og opdatere indstillinger.

Læs mere om WMI i [microsoft Developer Network System Administration-biblioteket](/windows/win32/wmisdk/wmi-start-page).

Microsoft Defender Antivirus har en række bestemte WMI-klasser, der kan bruges til at udføre de fleste af de samme funktioner som Gruppepolitik og andre administrationsværktøjer. Mange af klasserne svarer til [Defender for Cloud PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md).

[MSDN-Windows Defender WMIv2-providerreferencebiblioteket](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) viser de tilgængelige WMI-klasser for Microsoft Defender Antivirus og indeholder eksempelscripts.

Ændringer, der er foretaget med WMI, påvirker lokale indstillinger på slutpunktet, hvor ændringerne installeres eller foretages. Det betyder, at politikinstallationer med Gruppepolitik, Microsoft Endpoint Configuration Manager eller Microsoft Intune kan overskrive ændringer, der er foretaget med WMI. 

Du kan [konfigurere, hvilke indstillinger der kan tilsidesættes lokalt med tilsidesætter lokal politik](configure-local-policy-overrides-microsoft-defender-antivirus.md).

## <a name="related-topics"></a>Relaterede emner

- [Referenceemner til administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
