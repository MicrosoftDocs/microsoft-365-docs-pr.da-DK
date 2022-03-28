---
title: Fejlfinding af problemer, når du skifter til Microsoft Defender til Slutpunkt
description: Få mere at vide om, hvordan du foretager fejlfinding af problemer, når du skifter til Microsoft Defender til Slutpunkt.
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
ms.topic: conceptual
ms.custom: migrationguides
ms.date: 01/11/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: 6729d136da90c674c0d726f2bfe7321a75bdb79a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63596961"
---
# <a name="troubleshooting-issues-when-switching-to-microsoft-defender-for-endpoint"></a>Fejlfinding af problemer, når du skifter til Microsoft Defender til Slutpunkt

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Denne artikel indeholder fejlfindingsoplysninger til sikkerhedsadministratorer, der oplever problemer, når de skifter fra en ikke-Microsoft-slutpunktsbeskyttelsesløsning til Microsoft Defender til Slutpunkt.

## <a name="microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server"></a>Microsoft Defender Antivirus bliver fjernet på Windows Server

Når du skifter til Defender for Endpoint, starter du med din ikke-Microsoft-antivirus-/antimalwarebeskyttelse i aktiv tilstand. Som en del af konfigurationsprocessen skal du konfigurere Microsoft Defender Antivirus i passiv tilstand. Nogle gange kan din ikke-Microsoft-antivirus-/antimalwareløsning forhindre brugere Microsoft Defender Antivirus at køre på Windows Server. Det kan faktisk se ud som om Microsoft Defender Antivirus er blevet fjernet fra Windows Server.

Du kan løse dette problem ved at gøre følgende:

1. [Indstil registreringsdatabasenøglen DisableAntiSpyware til falsk](#set-the-disableantispyware-registry-key-to-false).
2. [Føj Microsoft Defender til slutpunkt til udeladelseslisten](#add-microsoft-defender-for-endpoint-to-the-exclusion-list).
3. [Angiv Microsoft Defender Antivirus til passiv tilstand manuelt](#set-microsoft-defender-antivirus-to-passive-mode-manually).

### <a name="set-the-disableantispyware-registry-key-to-false"></a>Indstil registreringsdatabasenøglen DisableAntiSpyware til falsk

[Registreringsdatabasenøglen DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) blev tidligere brugt til at deaktivere Microsoft Defender Antivirus og installere et andet antivirusprodukt, f.eks. McAfee,Afee,Afee eller andre. **Generelt bør du ikke have denne registreringsdatabasenøgle** på dine Windows-enheder og slutpunkter.  `DisableAntiSpyware` Men hvis du har konfigureret, kan du her se, hvordan du indstiller dens værdi til falsk:

1. På din Windows Server-enhed skal du åbne Registreringseditor.

2. Gå til `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. I denne mappe skal du se efter en DWORD-post med **navnet DisableAntiSpyware**.
   - Hvis du ikke kan se denne post, er du klar.
   - Hvis du kan se **DisableAntiSpyware**, skal du gå videre til trin 4.

4. Højreklik på DisableAntiSpyware DWORD, og vælg derefter **Rediger**.

5. Angiv værdien til `0`. (Denne handling indstiller registreringsdatabasenøglens værdi *til falsk*).

> [!TIP]
> Du kan få mere at vide om denne registreringsdatabasenøgle [under DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list"></a>Føj Microsoft Defender til slutpunkt til udeladelseslisten

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

## <a name="i-am-having-trouble-re-enabling-microsoft-defender-antivirus-on-windows-server-2016"></a>Jeg har problemer med at genaktivere Microsoft Defender Antivirus på Windows Server 2016

Hvis du bruger en løsning, der ikke er Microsoft-antivirus/antimalware på Windows Server 2016, skal din eksisterende løsning muligvis være Microsoft Defender Antivirus for at være deaktiveret eller fjernet. Du kan bruge[ værktøjet malwarebeskyttelse Command-Line at](command-line-arguments-microsoft-defender-antivirus.md) genaktivere Microsoft Defender Antivirus på Windows Server 2016.

1. Åbn Kommandoprompt som lokal administrator på serveren.

2. Kør følgende kommando: `MpCmdRun.exe -wdenable`

3. Genstart enheden.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)

- [Onboardingværktøjer og metoder til Windows enheder i Defender til Slutpunkt](configure-endpoints.md) 
