---
title: Anvend Microsoft Defender Antivirus opdateringer efter bestemte hændelser
description: Administrer, hvordan Microsoft Defender Antivirus anvender sikkerhedsintelligensopdateringer efter opstart eller modtagelse af skyleverede registreringsrapporter.
keywords: opdateringer, beskyttelse, gennemtving opdateringer, hændelser, start, tjek for nyeste, meddelelser
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 813dfe410a3e6cf198d6d4a36afd6d2987f6d376
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415590"
---
# <a name="manage-event-based-forced-updates"></a>Administrer begivenhedsbaserede gennemtvungne opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Antivirus giver dig mulighed for at afgøre, om opdateringer skal (eller ikke skal) forekomme efter bestemte hændelser, f.eks. ved start eller efter modtagelse af specifikke rapporter fra den cloud-leverede beskyttelsestjeneste.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Kontrollér, om der er opdateringer til beskyttelse, før du kører en scanning

Du kan bruge Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell-cmdlet'er og WMI til at tvinge Microsoft Defender Antivirus til at kontrollere og downloade beskyttelsesopdateringer, før du kører en planlagt scanning.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Brug Configuration Manager til at søge efter beskyttelsesopdateringer, før du kører en scanning

1. Åbn den antimalwarepolitik, du vil ændre, på din Microsoft Endpoint Manager konsol (klik på **Assets and Compliance** i navigationsruden til venstre, og udvid derefter træet til **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. Gå til afsnittet **Planlagte scanninger,** og angiv **Kontrollér, om der er de nyeste sikkerhedsintelligensopdateringer, før du kører en scanning** , til **Ja**.

3. Klik på **OK**.

4. [Installer den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Brug Gruppepolitik til at søge efter beskyttelsesopdateringer, før du kører en scanning

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

5. Dobbeltklik på **Søg efter de nyeste virus- og spywaredefinitioner, før du kører en planlagt scanning** , og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Brug PowerShell-cmdlet'er til at søge efter beskyttelsesopdateringer, før du kører en scanning

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Brug WMI (Windows Management Instruction) til at søge efter beskyttelsesopdateringer, før du kører en scanning

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
CheckForSignaturesBeforeRunningScan
```

Du kan få flere oplysninger [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Kontrollér, om der er opdateringer til beskyttelse ved start

Du kan bruge Gruppepolitik til at tvinge Microsoft Defender Antivirus til at kontrollere og downloade beskyttelsesopdateringer, når computeren startes.

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **sikkerhedsintelligensopdateringer**.

5. Dobbeltklik på **Søg efter de nyeste virus- og spywaredefinitioner ved start** , og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

Du kan også bruge Gruppepolitik, PowerShell eller WMI til at konfigurere Microsoft Defender Antivirus til at søge efter opdateringer ved start, selvom den ikke kører.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug Gruppepolitik til at downloade opdateringer, når der ikke findes Microsoft Defender Antivirus

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **redigeringsprogrammet til Gruppepolitik administration** skal du gå til **Computerkonfiguration**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **sikkerhedsintelligensopdateringer**.

5. Dobbeltklik på **Start sikkerhedsintelligensopdatering ved start** , og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug PowerShell-cmdlet'er til at downloade opdateringer, når Microsoft Defender Antivirus ikke findes

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) og [Defender Antivirus-cmdlet'er](/powershell/module/defender/index) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug WMI (Windows Management Instruction) til at downloade opdateringer, når Microsoft Defender Antivirus ikke findes

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Du kan få flere oplysninger [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Tillad ad hoc-ændringer af beskyttelse baseret på cloudbaseret beskyttelse

Microsoft Defender AV kan foretage ændringer af beskyttelsen baseret på skybaseret beskyttelse. Sådanne ændringer kan forekomme uden for normale eller planlagte beskyttelsesopdateringer.

Hvis du har aktiveret skybaseret beskyttelse, sender Microsoft Defender AV filer, som den er mistænksom over for, til Windows Defender cloud. Hvis cloudtjenesten rapporterer, at filen er skadelig, og filen er registreret i en nylig beskyttelsesopdatering, kan du bruge Gruppepolitik til at konfigurere Microsoft Defender AV til automatisk at modtage denne beskyttelsesopdatering. Der kan også anvendes andre vigtige beskyttelsesopdateringer.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Brug Gruppepolitik til automatisk at downloade de seneste opdateringer baseret på cloudbaseret beskyttelse

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af **administrationseditoren Gruppepolitik** gå til **Computerkonfiguration**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **sikkerhedsintelligensopdateringer**.

5. Dobbeltklik på **Tillad opdateringer af sikkerhedsintelligens i realtid baseret på rapporter til Microsoft MAPS** , og angiv indstillingen til **Aktiveret**. Klik derefter på **OK**.

6. **Tillad, at meddelelser deaktiverer definitionsbaserede rapporter i Microsoft MAPS** , og angiv indstillingen til **Aktiveret**. Klik derefter på **OK**.

> [!NOTE]
> **Tillad meddelelser for at deaktivere definitionsbaserede rapporter** gør det muligt for Microsoft MAPS at deaktivere de definitioner, der er kendt for at forårsage falske positive rapporter. Du skal konfigurere computeren til at deltage i Microsoft MAPS, for at funktionen kan fungere.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Installer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
