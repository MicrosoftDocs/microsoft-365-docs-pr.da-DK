---
title: Kør og tilpas scanninger efter behov i Microsoft Defender Antivirus
description: Kør og konfigurer scanninger efter behov ved hjælp af PowerShell, Windows Management Instrumentation eller individuelt på slutpunkter med Windows Sikkerhed-appen
keywords: scan, on-demand, dos, intune, instant scan
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1f82fe410634ab92f7b403a30bcbcdf9a61634ba
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597887"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Konfigurere og køre on-demand-Microsoft Defender Antivirus scanninger

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan køre en scanning efter behov på individuelle slutpunkter. Disse scanninger starter med det samme, og du kan definere parametre for scanningen, f.eks. placeringen eller typen. Når du kører en scanning, kan du vælge mellem tre typer: Hurtig scanning, Fuld scanning og Brugerdefineret scanning. I de fleste tilfælde skal du bruge en hurtig scanning. En hurtig scanning kigger på alle de placeringer, hvor der kan være registreret malware for at starte med systemet, f.eks registreringsdatabasenøgler og kendte Windows startmapper.

Kombineret med altid tændt beskyttelse i realtid, som gennemser filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe, hjælper en hurtig scanning med at yde stærk beskyttelse mod malware, der starter med systemet og malware på kerneniveau. I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede indstilling til planlagte scanninger eller scanninger efter behov. [Få mere at vide om scanningstyper](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> Microsoft Defender Antivirus kører i konteksten for [LocalSystem-kontoen](/windows/win32/services/localsystem-account), når du udfører en lokal scanning. Til netværksscanninger bruger programmet konteksten fra enhedskontoen. Hvis domæneenhedskontoen ikke har de rette tilladelser til at få adgang til delingen, fungerer scanningen ikke. Sørg for, at enheden har tilladelser til at få adgang til netværkssharen.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Brug Microsoft Endpoint Manager til at køre en scanning

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. På listen over faner skal **du Windows 10 for usunde** **slutpunkter eller Windows 11 usunde slutpunkter**.

4. På listen over angivne handlinger skal du **vælge Hurtig scanning** (anbefales) eller **Fuld scanning**.

   [![Indstillinger for scanning Windows 10 usunde slutpunkter.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Du kan finde flere oplysninger Microsoft Endpoint Manager at bruge til at køre en scanning under [Opgaver med antimalware og firewall:](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers) Sådan udfører du en scanning efter behov.

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Brug mpcmdrun.exe kommandolinjeværktøjet til at køre en scanning

Brug følgende `-scan` parameter:

```console
mpcmdrun.exe -scan -scantype 1
```

Du kan finde flere oplysninger om, hvordan du bruger værktøjet og yderligere parametre, herunder at starte en fuld scanning eller definere stier, under Brug [af mpcmdrun.exe-kommandolinjeværktøjet](command-line-arguments-microsoft-defender-antivirus.md) til at konfigurere og administrere Microsoft Defender Antivirus.

## <a name="use-microsoft-intune-to-run-a-scan"></a>Brug Microsoft Intune til at køre en scanning

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg Enheder alle enheder i **sidepanelet**\>, **og** vælg den enhed, du vil scanne.

3. Vælg **... Mere**. Vælg Hurtig scanning ( **anbefales)** eller Fuld scanning under **indstillingerne**.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Brug appen Windows Sikkerhed til at køre en scanning

Se [Kør en scanning i Windows Sikkerhed for vejledning](microsoft-defender-security-center-antivirus.md) til at køre en scanning på individuelle slutpunkter.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Brug PowerShell-cmdlet'er til at køre en scanning

Brug følgende cmdlet:

```PowerShell
Start-MpScan
```

Du kan finde flere oplysninger om, hvordan du bruger PowerShell Microsoft Defender Antivirus i Brug [PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Brug Windows (WMI) til at køre en scanning

Brug [**metoden Start**](/previous-versions/windows/desktop/defender/start-msft-mpscan) i **MSFT_MpScan** klasse.

Du kan finde flere oplysninger om, hvilke parametre der er tilladt, [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)
