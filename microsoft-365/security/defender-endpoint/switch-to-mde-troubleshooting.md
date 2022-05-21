---
title: Fejlfinding af problemer ved skift til Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du foretager fejlfinding af problemer, når du skifter til Microsoft Defender for Endpoint.
keywords: migrering, Windows Defender, avanceret slutpunktsbeskyttelse, antivirus, antimalware, passiv tilstand, aktiv tilstand, fejlfinding
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
ms.date: 05/20/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 9a1a95c927c4f659510c587d2bbc81ad4b9c1264
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621632"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Fejlfinding af problemer ved skift til Microsoft Defender for Endpoint

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Denne artikel indeholder fejlfindingsoplysninger for sikkerhedsadministratorer, der oplever problemer, når de skifter fra en løsning til beskyttelse af slutpunkter, der ikke er fra Microsoft, til Microsoft Defender for Endpoint.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Microsoft Defender Antivirus fjernes på Windows Server

Når du skifter til Defender for Endpoint, starter du med din ikke-Microsoft-antivirus-/antimalwarebeskyttelse i aktiv tilstand. Som en del af konfigurationsprocessen konfigurerer du Microsoft Defender Antivirus i passiv tilstand. Nogle gange kan din ikke-Microsoft-antivirus-/antimalwareløsning forhindre Microsoft Defender Antivirus i at køre på Windows Server. Det kan faktisk se ud som om, Microsoft Defender Antivirus er blevet fjernet fra Windows Server.

Du kan løse problemet ved at benytte følgende fremgangsmåde:

1. [Føj Microsoft Defender for Endpoint til listen over undtagelser](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
2. [Angiv Microsoft Defender Antivirus til passiv tilstand manuelt](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Føj Microsoft Defender for Endpoint til listen over undtagelser

Visse undtagelser for Defender for Endpoint skal defineres i din eksisterende løsning til beskyttelse af slutpunkter, der ikke er fra Microsoft. Sørg for at tilføje følgende undtagelser:

`C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`

`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`

### <a name="set-microsoft-defender-antivirus-to-passive-mode-manually"></a>Angiv Microsoft Defender Antivirus til passiv tilstand manuelt

På Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 eller Windows Server 2012 R2 skal du angive Microsoft Defender Antivirus til passiv tilstand manuelt. Denne handling hjælper med at forhindre problemer, der skyldes, at flere antivirusprogrammer er installeret på en server. Du kan angive Microsoft Defender Antivirus til passiv tilstand ved hjælp af PowerShell, Gruppepolitik eller en registreringsdatabasenøgle.

Du kan angive Microsoft Defender Antivirus til passiv tilstand ved at angive følgende registreringsdatabasenøgle:

Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`

Navn: `ForceDefenderPassiveMode`

Type: `REG_DWORD`

Værdi: `1`

> [!NOTE]
> Hvis passiv tilstand skal fungere på slutpunkter, der kører Windows Server 2016 og Windows Server 2012 R2, skal disse slutpunkter onboardes ved hjælp af vejledningen i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

Du kan få flere oplysninger [under Microsoft Defender Antivirus i Windows](microsoft-defender-antivirus-windows.md).

## <a name="microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode"></a>Microsoft Defender Antivirus ser ud til at sidde fast i passiv tilstand

Hvis Microsoft Defender Antivirus sidder fast i passiv tilstand, skal du angive den til aktiv tilstand manuelt ved at følge disse trin:

1. Åbn Registreringseditor som administrator på din Windows enhed.

2. Gå til `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

3. Angiv eller definer en **REG_DWORD** post, der kaldes `ForceDefenderPassiveMode`, og angiv dens værdi til `0`.

4. Genstart enheden.

> [!IMPORTANT]
> Hvis du stadig har problemer med at angive Microsoft Defender Antivirus til aktiv tilstand efter at have fulgt denne procedure, [skal du kontakte support](../../admin/get-help-support.md).

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Jeg har problemer med at genaktivere Microsoft Defender Antivirus på Windows Server 2016

Hvis du bruger en ikke-Microsoft-antivirus-/antimalwareløsning på Windows Server 2016, kan din eksisterende løsning have krævet, at Microsoft Defender Antivirus deaktiveres eller fjernes. Du kan bruge[ Command-Line Utility til beskyttelse af skadelig software](command-line-arguments-microsoft-defender-antivirus.md) til at genaktivere Microsoft Defender Antivirus på Windows Server 2016.

1. Åbn Kommandoprompt som lokal administrator på serveren.

2. Kør følgende kommando: `MpCmdRun.exe -wdenable`

3. Genstart enheden.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)

- [Onboardingværktøjer og -metoder til Windows enheder i Defender for Endpoint](configure-endpoints.md) 
