---
title: Fejlfinding af problemer, når du skifter til Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du foretager fejlfinding af problemer, når du skifter til Microsoft Defender for Endpoint.
keywords: overførsel, windows defender, avanceret slutpunktsbeskyttelse, antivirus, antimalware, passiv tilstand, aktiv tilstand, fejlfinding
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 8334ce03bac5b7d4518433f83ab34d5f86e71339
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634157"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Fejlfinding af problemer, når du skifter til Microsoft Defender for Endpoint

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Denne artikel indeholder fejlfindingsoplysninger til sikkerhedsadministratorer, der oplever problemer, når de skifter fra en ikke-Microsoft-løsning til Microsoft Defender for Endpoint.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Microsoft Defender Antivirus bliver fjernet på Windows Server

Når du skifter til Defender for Endpoint, starter du med din ikke-Microsoft-antivirus-/antimalwarebeskyttelse i aktiv tilstand. Som en del af konfigurationsprocessen skal du konfigurere Microsoft Defender Antivirus i passiv tilstand. Nogle gange kan din ikke-Microsoft-antivirus-/antimalwareløsning forhindre brugere Microsoft Defender Antivirus at køre på Windows Server. Det kan faktisk se ud som om Microsoft Defender Antivirus er blevet fjernet fra Windows Server.

Du kan løse dette problem ved at gøre følgende:

1. [Føj Microsoft Defender for Endpoint til udeladelseslisten](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Angiv Microsoft Defender Antivirus til passiv tilstand manuelt](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Føje Microsoft Defender for Endpoint til udeladelseslisten

Visse undtagelser for Defender til slutpunkt skal defineres i din eksisterende løsning til ikke-Microsoft-slutpunktsbeskyttelse. Sørg for at tilføje følgende udeladelse:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Angiv Microsoft Defender Antivirus til passiv tilstand manuelt

På Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 eller Windows Server 2012 R2 skal du manuelt angive Microsoft Defender Antivirus til passiv tilstand. Denne handling hjælper med at forhindre problemer, der skyldes, at flere antivirusprodukter er installeret på en server. Du kan indstille Microsoft Defender Antivirus til passiv tilstand ved hjælp af PowerShell, Gruppepolitik eller en registreringsdatabasenøgle.

Du kan indstille Microsoft Defender Antivirus til passiv tilstand ved at angive følgende registreringsdatabasenøgle:

Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Navn: `ForceDefenderPassiveMode`

Skriv: `REG_DWORD`

Værdi: `1`

> [!NOTE]
> For at passiv tilstand kan fungere på slutpunkter, der kører Windows Server 2016 og Windows Server 2012 R2, skal disse slutpunkter være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

Du kan finde flere oplysninger [Microsoft Defender Antivirus på Windows Server](microsoft-defender-antivirus-on-windows-server.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Microsoft Defender Antivirus ser ud til at være gået i stå i passiv tilstand

Hvis Microsoft Defender Antivirus sidder fast i passiv tilstand, kan du indstille den til aktiv tilstand manuelt ved at følge disse trin:

1. På din Windows skal du åbne Registreringseditor som administrator.

2. Gå til `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. Angiv eller definer **en REG_DWORD** , der hedder `ForceDefenderPassiveMode`, og angiv dens værdi til `0`.

4. Genstart enheden.

> [!IMPORTANT]
> Hvis du stadig har problemer med at konfigurere Microsoft Defender Antivirus aktiv tilstand, efter du har fulgt denne procedure, skal du [kontakte support](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Jeg har problemer med at genaktivere Microsoft Defender Antivirus på Windows Server 2016

Hvis du bruger en løsning, der ikke er Microsoft-antivirus/antimalware på Windows Server 2016, skal din eksisterende løsning muligvis være Microsoft Defender Antivirus for at være deaktiveret eller fjernet. Du kan bruge[ værktøjet malwarebeskyttelse Command-Line at](command-line-arguments-microsoft-defender-antivirus.md) genaktivere Microsoft Defender Antivirus på Windows Server 2016.

1. Åbn Kommandoprompt som lokal administrator på serveren.

2. Kør følgende kommando: `MpCmdRun.exe -wdenable`

3. Genstart enheden.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)

- [Onboardingværktøjer og metoder til Windows enheder i Defender til Slutpunkt](configure-endpoints.md) 
