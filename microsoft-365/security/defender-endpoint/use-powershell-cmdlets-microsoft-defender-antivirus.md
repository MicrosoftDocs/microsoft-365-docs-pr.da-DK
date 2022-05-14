---
title: Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus
description: I Windows 10 og Windows 11 kan du bruge PowerShell-cmdlet'er til at køre scanninger, opdatere Security Intelligence og ændre indstillingerne i Microsoft Defender Antivirus.
keywords: scan, kommandolinje, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 7afde73e1e1c1e5ff35ee906331aa2756ba55a21
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419478"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug PowerShell-cmdlet'er til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan bruge PowerShell til at udføre forskellige funktioner i Windows Defender. På samme måde som med kommandoprompten eller kommandolinjen er PowerShell en opgavebaseret kommandolinjeshell og et scriptsprog, der er udviklet specielt til systemadministration. Du kan læse mere om det i [PowerShell-hubben på MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

Du kan se en liste over cmdlet'erne og deres funktioner og tilgængelige parametre under emnet [Defender Antivirus-cmdlet'er](/powershell/module/defender) .

PowerShell-cmdlet'er er mest nyttige i Windows Server-miljøer, der ikke er afhængige af en grafisk brugergrænseflade (GUI) til konfiguration af software.

> [!NOTE]
> PowerShell-cmdlet'er bør ikke bruges som erstatning for en komplet infrastruktur til administration af netværkspolitik, f.eks. [Microsoft Endpoint Configuration Manager](/configmgr), [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) eller [Microsoft Defender Antivirus Gruppepolitik ADMX-skabeloner](https://www.microsoft.com/download/101445).

Ændringer, der foretages med PowerShell, påvirker lokale indstillinger på det slutpunkt, hvor ændringerne installeres eller foretages. Det betyder, at udrulninger af politikker med Gruppepolitik, Microsoft Endpoint Configuration Manager eller Microsoft Intune kan overskrive ændringer, der er foretaget med PowerShell.

Du kan [konfigurere, hvilke indstillinger der kan tilsidesættes lokalt med tilsidesættelser af lokale politikker](configure-local-policy-overrides-microsoft-defender-antivirus.md).

PowerShell installeres typisk under mappen `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Brug Microsoft Defender Antivirus PowerShell-cmdlet'er

1. Skriv **powershell** i søgelinjen Windows.
2. Vælg **Windows PowerShell** i resultaterne for at åbne grænsefladen.
3. Angiv PowerShell-kommandoen og eventuelle parametre.

> [!NOTE]
> Du skal muligvis åbne PowerShell i administratortilstand. Højreklik på elementet i menuen Start, klik på **Kør som administrator**, og klik på **Ja** i tilladelsesprompten.

Hvis du vil åbne onlinehjælpen til en af cmdlet'erne, skal du skrive følgende:

```PowerShell
Get-Help <cmdlet> -Online
```

Udelad `-online` parameteren for at få lokalt cachelagret hjælp.

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
- [cmdlet'er Microsoft Defender Antivirus](/powershell/module/defender)
