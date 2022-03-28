---
title: Anvend Microsoft Defender Antivirus opdateringer efter bestemte hændelser
description: Administrer, Microsoft Defender Antivirus anvender sikkerhedsintelligensopdateringer efter start eller modtagelse af registreringsrapporter, der leveres i skyen.
keywords: opdateringer, beskyttelse, gennemtvinge opdateringer, begivenheder, start, se efter seneste, meddelelser
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
ms.openlocfilehash: c99e4e085de32ac4e7ec77a2155182f1a930d432
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597884"
---
# <a name="manage-event-based-forced-updates"></a>Administrer begivenhedsbaserede gennemtvungne opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus giver dig mulighed for at afgøre, om opdateringer skal (eller ikke bør) udføres efter bestemte hændelser, f.eks ved start eller efter modtagelse af bestemte rapporter fra den skybaserede tjeneste til levering af beskyttelse.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Søg efter beskyttelsesopdateringer, før du kører en scanning

Du kan bruge Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell-cmdlet'er og WMI til at tvinge Microsoft Defender Antivirus til at kontrollere og hente beskyttelsesopdateringer, før du kører en planlagt scanning.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Brug Konfigurationsstyring til at søge efter sikkerhedsopdateringer, før du kører en scanning

1. På din Microsoft Endpoint Manager-konsol skal du åbne den antimalwarepolitik, du vil ændre (klik på  Aktiver og overholdelse af regler og standarder i navigationsruden til venstre,  \> og udvid derefter træet til Oversigt **Endpoint Protection** \> **Antimalwarepolitikker**)

2. Gå til sektionen **Planlagte scanninger** , og angiv **Søg efter de seneste sikkerhedsintelligensopdateringer, før du kører en scanning** til **Ja**.

3. Klik på **OK**.

4. [Installér den opdaterede politik som normalt](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Brug Gruppepolitik til at søge efter sikkerhedsopdateringer, før du kører en scanning

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scanning**.

5. Dobbeltklik på Kontrollér **, om der er de nyeste virus- og spywaredefinitioner** , før du kører en planlagt scanning, og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Brug PowerShell-cmdlet'er til at søge efter sikkerhedsopdateringer, før du kører en scanning

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Brug Windows (WMI) til at søge efter sikkerhedsopdateringer, før du kører en scanning

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
CheckForSignaturesBeforeRunningScan
```

Du kan finde flere oplysninger [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Søg efter beskyttelsesopdateringer ved start

Du kan bruge Gruppepolitik at tvinge Microsoft Defender Antivirus til at søge efter og hente beskyttelsesopdateringer, når computeren er startet.

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Sikkerhedsvidens opdateringer**.

5. Dobbeltklik på Kontrollér **, om der er de nyeste virus- og spywaredefinitioner ved opstart,** og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

Du kan også bruge Gruppepolitik, PowerShell eller WMI til at konfigurere Microsoft Defender Antivirus til at søge efter opdateringer ved start, også selvom den ikke kører.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug Gruppepolitik til at hente opdateringer, når Microsoft Defender Antivirus ikke er til stede

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Ved hjælp **Gruppepolitik Administrationseditor** skal du gå **til Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Sikkerhedsvidens opdateringer**.

5. Dobbeltklik på **Påbegynde sikkerhedsintelligensopdatering ved** start, og angiv indstillingen til **Aktiveret**.

6. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug PowerShell-cmdlet'er til at hente opdateringer, Microsoft Defender Antivirus ikke er til stede

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Få mere at vide under Brug [PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at administrere Microsoft Defender Antivirus- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/index) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Brug Windows (WMI) til at hente opdateringer, når Microsoft Defender Antivirus ikke er til stede

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Du kan finde flere oplysninger [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Tillad ad hoc-ændringer af beskyttelse baseret på cloud-leveret beskyttelse

Microsoft Defender AV kan foretage ændringer i beskyttelsen baseret på cloud-leveret beskyttelse. Sådanne ændringer kan forekomme uden for normale eller planlagte opdateringer til beskyttelse.

Hvis du har aktiveret skybaseret beskyttelse, sender Microsoft Defender AV filer, som det har mistanke om, til den Windows Defender skyen. Hvis skytjenesten rapporterer, at filen er skadelig, og filen registreres i en nylig beskyttelsesopdatering, kan du bruge Gruppepolitik til at konfigurere Microsoft Defender AV til automatisk at modtage denne sikkerhedsopdatering. Andre vigtige sikkerhedsopdateringer kan også anvendes.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Brug Gruppepolitik til automatisk at hente de seneste opdateringer baseret på skybaseret beskyttelse

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Sikkerhedsvidens opdateringer**.

5. Dobbeltklik på Tillad **sikkerhedsintelligensopdateringer i realtid baseret på rapporter til Microsoft MAPS** , og angiv indstillingen til **Aktiveret**. Klik derefter på **OK**.

6. **Tillad meddelelser for at deaktivere definitionsbaserede rapporter til Microsoft MAPS** , og angiv indstillingen til **Aktiveret**. Klik derefter på **OK**.

> [!NOTE]
> **Tillad, at meddelelser deaktiverer definitionerbaserede rapporter** , gør det muligt for Microsoft MAPS at deaktivere de definitioner, der er kendt for at forårsage falske positive rapporter. Du skal konfigurere computeren til at deltage i Microsoft MAPS, for at denne funktion kan fungere.

## <a name="see-also"></a>Se også

- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
