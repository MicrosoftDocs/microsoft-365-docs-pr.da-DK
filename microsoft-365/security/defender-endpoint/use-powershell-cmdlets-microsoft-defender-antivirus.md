---
title: Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus
description: I Windows 10 og Windows 11 kan du bruge PowerShell-cmdlet'er til at køre scanninger, opdatere sikkerhedsintelligens og ændre indstillingerne i Microsoft Defender Antivirus.
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
ms.openlocfilehash: 075a475ef3135769e90362f441077b1638192e99
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593216"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug PowerShell-cmdlet'er til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan bruge PowerShell til at udføre forskellige funktioner i Windows Defender. Ligesom kommandoprompten eller kommandolinjen er PowerShell en opgavebaseret kommandolinje shell og scripting-sprog, der er udviklet specielt til systemadministration. Du kan læse mere om det i [PowerShell-hubben på MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

Du kan finde en liste over cmdlet'er og deres funktioner og tilgængelige parametre i [emnet Defender Antivirus-cmdlet'er](/powershell/module/defender) .

PowerShell-cmdlet'er er mest nyttige i Windows servermiljøer, der ikke er afhængige af en grafisk brugergrænseflade til konfiguration af software.

> [!NOTE]
> PowerShell-cmdlet'er bør ikke bruges som en erstatning for en komplet infrastruktur til administration af netværkspolitik, f.eks. [Microsoft Endpoint Configuration Manager](/configmgr), [Gruppepolitik Management Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) [eller Microsoft Defender Antivirus Gruppepolitik ADMX-skabeloner](https://www.microsoft.com/download/101445).

Ændringer, der er foretaget med PowerShell, vil påvirke lokale indstillinger på slutpunktet, hvor ændringerne installeres eller foretages. Det betyder, at politikinstallationer med Gruppepolitik, Microsoft Endpoint Configuration Manager eller Microsoft Intune kan overskrive ændringer, der er foretaget med PowerShell.

Du kan [konfigurere, hvilke indstillinger der kan tilsidesættes lokalt med tilsidesætter lokal politik](configure-local-policy-overrides-microsoft-defender-antivirus.md).

PowerShell installeres typisk under mappen `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>Brug Microsoft Defender Antivirus PowerShell-cmdlet'er

1. Skriv powershell Windows søgefeltet i **søgefeltet**.
2. Vælg **Windows PowerShell** i resultaterne for at åbne grænsefladen.
3. Angiv PowerShell-kommandoen og eventuelle parametre.

> [!NOTE]
> Du skal muligvis åbne PowerShell i administratortilstand. Højreklik på elementet i menuen menuen Start, klik på **Kør som administrator,** og klik **på Ja** ved tilladelsesprompten.

Hvis du vil åbne onlinehjælp for en af cmdlet'erne, skal du skrive følgende:

```PowerShell
Get-Help <cmdlet> -Online
```

Udelade parameteren `-online` for at få lokalt cachelagret hjælp.

## <a name="related-topics"></a>Relaterede emner

- [Referenceemner til administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender)
