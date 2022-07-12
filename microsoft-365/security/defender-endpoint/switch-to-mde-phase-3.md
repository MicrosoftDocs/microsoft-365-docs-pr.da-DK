---
title: Skift til Microsoft Defender for Endpoint - onboard
description: Skift til Microsoft Defender for Endpoint. Onboard enheder, og fjern derefter din ikke-Microsoft-løsning.
keywords: migrering, Microsoft Defender for Endpoint, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.topic: article
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: d927f1a5972e24c3bae0329bd866a4b56b0a5d95
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717244"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Skift til Microsoft Defender for Endpoint - fase 3: Onboard

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Fase 1: Forbered3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Fase 1: Forbered](switch-to-mde-phase-1.md) | [![Fase 2: Konfigurer](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Fase 2: Konfigurer](switch-to-mde-phase-2.md) | ![Fase 3: Onboard](images/phase-diagrams/onboard.png#lightbox)<br/>Fase 3: Onboard |
|--|--|--|
|| |*Du er her!* |

**Velkommen til fase 3, hvor [du skifter til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Denne overførselsfase omfatter følgende trin:

1. [Onboarder enheder til Defender for Endpoint](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [Kør en registreringstest](#run-a-detection-test).
3. [Bekræft, at Microsoft Defender Antivirus er i passiv tilstand på dine slutpunkter](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [Hent opdateringer til Microsoft Defender Antivirus](#get-updates-for-microsoft-defender-antivirus).
5. [Fjern din ikke-Microsoft-løsning](#uninstall-your-non-microsoft-solution).
6. [Kontrollér, at Defender for Endpoint fungerer korrekt](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Om bord på enheder til Microsoft Defender for Endpoint

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** \> **Slutpunkter** \> **Onboarding** (under **Enhedshåndtering**).

3. Vælg et operativsystem på listen **Vælg operativsystem for at starte onboardingprocessen** .

4. Vælg en indstilling under **Installationsmetode**. Følg linkene og prompterne for at onboarde din organisations enheder. Har du brug for hjælp? Se [Onboarding-metoder](#onboarding-methods) (i denne artikel).

> [!NOTE]
> Hvis noget går galt under onboarding, skal du se [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md). I denne artikel beskrives det, hvordan du løser onboardingproblemer og almindelige fejl på slutpunkter.

### <a name="onboarding-methods"></a>Onboardingmetoder

> [!IMPORTANT]
> Hvis du bruger Microsoft Defender for Cloud, skal du se [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

Installationsmetoder varierer, afhængigt af operativsystemet og foretrukne metoder. I følgende tabel vises en liste over ressourcer, der kan hjælpe dig med at onboarde til Defender for Endpoint:

|Operativsystemer  |Metoder  |
|---------|---------|
|Windows 10 eller nyere<br/><br/>Windows Server 2019 eller nyere<br/><br/>Windows Server, version 1803 eller nyere<br/><br/>Windows Server 2012 R2 og 2016<sup>[[1](#fn1)]<sup>  |   [Lokalt script (op til 10 enheder)](configure-endpoints-script.md)<br><br/>   [Gruppepolitik](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[Microsoft Endpoint Manager/Mobile Enhedshåndtering (Intune)](configure-endpoints-mdm.md)<br>    [VDI-scripts](configure-endpoints-vdi.md) <br><br> **BEMÆRK**! Et lokalt script er velegnet til blåstempling, men bør ikke bruges til produktionsinstallation. I forbindelse med en produktionsinstallation anbefaler vi, at du bruger Gruppepolitik, Microsoft Endpoint Configuration Manager eller Intune. |
|Windows Server 2008 R2 SP1 | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)  eller [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **BEMÆRK**! Microsoft Monitoring Agent er nu Azure Log Analytics-agent. Du kan få mere at vide under [Oversigt over Log Analytics-agent](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 SP1 Pro<br/><br/>Windows 7 SP1| [Microsoft-overvågningsagent (MMA)](onboard-downlevel.md) <br><br> **BEMÆRK**! Microsoft Monitoring Agent er nu Azure Log Analytics-agent. Du kan få mere at vide under [Oversigt over Log Analytics-agent](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (se [Systemkrav](microsoft-defender-endpoint-mac.md) | [Lokalt script](mac-install-manually.md)<br/><br/>[Microsoft Endpoint Manager](mac-install-with-intune.md)<br/><br/>[JAMF Pro](mac-install-with-jamf.md)<br/><br/>[Mobil Enhedshåndtering](mac-install-with-other-mdm.md)   |
| Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements)) |  [Lokalt script](linux-install-manually.md) <br><br/> [Marionet](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| Ios | [Microsoft Endpoint Manager](ios-install.md)     |
|Android  | [Microsoft Endpoint Manager](android-intune.md)  | 

(<a id="fn1">1</a>) Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

## <a name="run-a-detection-test"></a>Kør en registreringstest

Hvis du vil kontrollere, at dine onboardede enheder er korrekt forbundet til Defender for Endpoint, kan du køre en registreringstest.

|Operativsystem|Vejledning|
|---|---|
|Windows 10 eller nyere<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server, version 1803 eller nyere<br/><br/>Windows Server 2016<br/><br/>Windows Server 2012 R2|Se [Kør en registreringstest](run-detection-test.md).|
|macOS (se [Systemkrav](microsoft-defender-endpoint-mac.md)|Download og brug diy-appen på <https://aka.ms/mdatpmacosdiy>. <br/><br/> Du kan finde flere oplysninger under [Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md).|
|Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements))|1. Kør følgende kommando, og søg efter resultatet **1**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. Åbn et terminalvindue, og kør følgende kommando: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. Kør følgende kommando for at få vist eventuelle registrerede trusler: `mdatp threat list`.<br/><br/>Du kan finde flere oplysninger under [Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md).|

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Bekræft, at Microsoft Defender Antivirus er i passiv tilstand på dine slutpunkter

Nu, hvor dine slutpunkter er blevet onboardet til Defender for Endpoint, er dit næste trin at sikre, at Microsoft Defender Antivirus kører i passiv tilstand. Du kan bruge en af flere metoder, som beskrevet i følgende tabel:

|Metode|Sådan gør du|
|---|---|
|Kommandoprompten|1. Åbn kommandoprompten på en Windows-enhed.<br/><br/>2. Skriv `sc query windefend`, og tryk derefter på Enter.<br/><br/>3. Gennemse resultaterne for at bekræfte, at Microsoft Defender Antivirus kører i passiv tilstand.|
|PowerShell|1. Åbn Windows PowerShell som administrator på en Windows-enhed.<br/><br/>2. Kør følgende PowerShell-cmdlet: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. Gennemse resultaterne. Du bør se **Passiv tilstand**.|
|Windows Sikkerhed app|1. Åbn appen Windows Sikkerhed på en Windows-enhed.<br/><br/>2. Vælg **Virus & trusselsbeskyttelse**.<br/><br/>3. Under **Hvem beskytter mig?** skal du vælge **Administrer udbydere**.<br/><br/>4. Søg efter **Microsoft Defender Antivirus er slået** til under **Antivirus** på siden **Sikkerhedsudbydere**.|
|Jobliste|1. Åbn appen Jobliste på en Windows-enhed.<br/><br/>2. Vælg fanen **Detaljer** . Søg efter **MsMpEng.exe** på listen.|

> [!NOTE]
> Du kan muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus* i nogle versioner af Windows.
> Hvis du vil vide mere om passiv tilstand og aktiv tilstand, skal du se [Flere oplysninger om Microsoft Defender Antivirus-tilstande](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Indstil Microsoft Defender Antivirus på Windows Server til passiv tilstand manuelt

Hvis du vil indstille Microsoft Defender Antivirus til passiv tilstand på Windows Server, version 1803 eller nyere eller Windows Server 2019 eller Windows Server 2022, skal du følge disse trin:

1. Åbn Registreringseditor, og naviger derefter til `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Rediger (eller opret) en DWORD-post med navnet **ForceDefenderPassiveMode**, og angiv følgende indstillinger:

   - Angiv DWORD-værdien til **1**.

   - Under **Base** skal du vælge **Hexadecimal**.

> [!NOTE]
> Du kan bruge andre metoder til at angive registreringsdatabasenøglen, f.eks. følgende:
>
> - [Gruppepolitik indstillinger](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [Værktøjet Lokal Gruppepolitik objekt](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [En pakke i Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Start Microsoft Defender Antivirus på Windows Server 2016

Hvis du bruger Windows Server 2016, skal du muligvis starte Microsoft Defender Antivirus manuelt. Du kan udføre denne opgave ved hjælp af PowerShell-cmdlet'en `mpcmdrun.exe -wdenable` på enheden.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Hent opdateringer til Microsoft Defender Antivirus

Det er vigtigt at holde Microsoft Defender Antivirus opdateret for at sikre, at dine enheder har den nyeste teknologi og de funktioner, der er nødvendige for at beskytte mod nye malware- og angrebsteknikker, også selvom Microsoft Defender Antivirus kører i passiv tilstand. (Se [Microsoft Defender Antivirus-kompatibilitet](microsoft-defender-antivirus-compatibility.md)).

Der er to typer opdateringer, der er relateret til at holde Microsoft Defender Antivirus opdateret:

- Opdateringer til sikkerhedsintelligens

- Produktopdateringer

Hvis du vil hente dine opdateringer, skal du følge vejledningen i [Administrer Microsoft Defender Antivirus-opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>Fjern din ikke-Microsoft-løsning

Hvis du på dette tidspunkt har:

- Har onboardet din organisations enheder til Defender for Endpoint, og

- Microsoft Defender Antivirus er installeret og aktiveret,

Derefter er dit næste trin at fjerne din ikke-Microsoft-antivirus-, antimalware- og slutpunktsbeskyttelsesløsning. Når du fjerner din ikke-Microsoft-løsning, skifter Microsoft Defender Antivirus fra passiv tilstand til aktiv tilstand. I de fleste tilfælde sker dette automatisk. 

> [!IMPORTANT]
> Hvis Microsoft Defender Antivirus af en eller anden grund ikke går i aktiv tilstand, når du har fjernet din ikke-Microsoft-antivirus-/antimalwareløsning, kan du se [, at Microsoft Defender Antivirus ser ud til at være fastlåst i passiv tilstand](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

Kontakt deres tekniske supportteam for at få hjælp til at fjerne din ikke-Microsoft-løsning.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Kontrollér, at Defender for Endpoint fungerer korrekt

Nu, hvor du har onboardet til Defender for Endpoint, og du har fjernet din tidligere ikke-Microsoft-løsning, er dit næste skridt at sikre, at Defender for Endpoint fungerer korrekt. 

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Slutpunkter** > **Enhedslager** i navigationsruden. Der kan du se beskyttelsesstatus for enheder.

Du kan få mere at vide under [Enhedsoversigt](machines-view-overview.md).

## <a name="next-steps"></a>Næste trin

**Tillykke**! Du har fuldført [overførslen til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Besøg dashboardet til sikkerhedshandlinger](security-operations-dashboard.md) på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

- [Administrer Defender for Endpoint efter overførsel](manage-mde-post-migration.md).
