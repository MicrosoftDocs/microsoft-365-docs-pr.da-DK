---
title: Kør og tilpas scanninger efter behov i Microsoft Defender Antivirus
description: Kør og konfigurer on-demand-scanninger ved hjælp af PowerShell, Windows Management Instrumentation eller individuelt på slutpunkter med Windows Sikkerhed-appen
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
ms.openlocfilehash: b22e59f5f54b556b32140640f1210e04389148cb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415546"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Konfigurer og kør scanninger efter behov Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan køre en on-demand-scanning på individuelle slutpunkter. Disse scanninger starter med det samme, og du kan definere parametre for scanningen, f.eks. placeringen eller typen. Når du kører en scanning, kan du vælge mellem tre typer: Hurtig scanning, fuld scanning og brugerdefineret scanning. I de fleste tilfælde skal du bruge en hurtig scanning. En hurtig scanning ser på alle de steder, hvor der kan være malware registreret til at starte med systemet, såsom registreringsdatabasenøgler og kendte Windows startmapper.

Kombineret med altid aktiveret beskyttelse i realtid, som gennemgår filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe, hjælper en hurtig scanning med at yde stærk beskyttelse mod malware, der starter med systemet og malware på kerneniveau. I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede mulighed for planlagte scanninger eller on-demand-scanninger. [Få mere at vide om scanningstyper](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> Microsoft Defender Antivirus kører i konteksten af [LocalSystem-kontoen](/windows/win32/services/localsystem-account), når der udføres en lokal scanning. I forbindelse med netværksscanninger bruges enhedskontoens kontekst. Hvis domæneenhedskontoen ikke har de nødvendige tilladelser til at få adgang til delingen, fungerer scanningen ikke. Sørg for, at enheden har tilladelser til netværkssharet med adgang.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Brug Microsoft Endpoint Manager til at køre en scanning

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. På listen over faner skal du vælge **Windows 10 usunde slutpunkter** eller **Windows 11 usunde slutpunkter**.

4. På listen over angivne handlinger skal du vælge **Hurtig scanning** (anbefales) eller **Fuld scanning**.

   [![Scanningsindstillinger på fanen Windows 10 usunde slutpunkter.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Du kan få flere oplysninger om, hvordan du bruger Microsoft Endpoint Manager til at køre en scanning, under [Antimalware- og firewallopgaver: Sådan udfører du en scanning efter behov](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Brug kommandolinjeværktøjet mpcmdrun.exe til at køre en scanning

Brug følgende `-scan` parameter:

```console
mpcmdrun.exe -scan -scantype 1
```

Du kan finde flere oplysninger om, hvordan du bruger værktøjet og yderligere parametre, herunder start af en fuld scanning eller definition af stier, under [Brug kommandolinjeværktøjet mpcmdrun.exe til at konfigurere og administrere Microsoft Defender Antivirus](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>Brug Microsoft Intune til at køre en scanning

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Enheder** \> **Alle enheder** på sidepanelet, og vælg den enhed, du vil scanne.

3. Vælg **... Mere**. Vælg **Hurtig scanning** (anbefales) eller **Fuld scanning** under indstillingerne.

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Brug appen Windows Sikkerhed til at køre en scanning

Se [Kør en scanning i Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md) for at få oplysninger om, hvordan du kører en scanning på individuelle slutpunkter.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Brug PowerShell-cmdlet'er til at køre en scanning

Brug følgende cmdlet:

```PowerShell
Start-MpScan
```

Du kan få flere oplysninger om, hvordan du bruger PowerShell sammen med Microsoft Defender Antivirus i [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Brug WMI (Windows Management Instruction) til at køre en scanning

Brug [metoden **Start**](/previous-versions/windows/desktop/defender/start-msft-mpscan) for klassen **MSFT_MpScan**.

Du kan få flere oplysninger om, hvilke parametre der er tilladt, [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)