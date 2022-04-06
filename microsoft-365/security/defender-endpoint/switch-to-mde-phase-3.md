---
title: Skift til Microsoft Defender for Endpoint - Onboard
description: Skift til Microsoft Defender for Endpoint. Onboard enheder, og fjern derefter din løsning, som ikke er en Microsoft-løsning.
keywords: overførsel, Microsoft Defender for Endpoint, edr
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
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 1397c34e8e4a7f1fcb20df192409bd57bc50f40b
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507115"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>Skift til Microsoft Defender for Endpoint - Fase 3: Onboard

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![Fase 1: Forbered3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Fase 1: Forbered](switch-to-mde-phase-1.md) | [![Fase 2: Konfigurer](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Fase 2: Konfigurer](switch-to-mde-phase-2.md) | ![Fase 3: Onboard](images/phase-diagrams/onboard.png#lightbox)<br/>Fase 3: Onboard |
|--|--|--|
|| |*Du er her!* |

**Velkommen til Fase 3 i [skift til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Denne overførselsfase omfatter følgende trin:

1. [Onboard-enheder til Defender til Slutpunkt](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [Kør en registreringstest](#run-a-detection-test).
3. [Kontrollér, Microsoft Defender Antivirus er i passiv tilstand på dine slutpunkter](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [Hent opdateringer til Microsoft Defender Antivirus](#get-updates-for-microsoft-defender-antivirus).
5. [Fjern din løsning, der ikke er fra Microsoft](#uninstall-your-non-microsoft-solution).
6. [Sørg for, at Defender til slutpunkt fungerer korrekt](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Onboard-enheder til Microsoft Defender for Endpoint

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** \> **onboarding af slutpunkter** \> (under **Enhedshåndtering**).

3. Vælg **et operativsystem på listen Vælg operativsystem for at starte onboardingproces** .

4. Vælg **en indstilling** under Installationsmetode. Følg de links og instruktioner, der skal vises for at onboarde din organisations enheder. Har du brug for hjælp? Se [Onboardingmetoder](#onboarding-methods) (i denne artikel).

> [!NOTE]
> Hvis noget går galt under onboarding, skal du [se Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md). Denne artikel beskriver, hvordan du løser onboardingproblemer og almindelige fejl på slutpunkter.

### <a name="onboarding-methods"></a>Onboardingmetoder

> [!IMPORTANT]
> Hvis du bruger Microsoft Defender til skyen, skal du se [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

Installationsmetoderne varierer alt efter operativsystem og foretrukne metoder. I følgende tabel vises ressourcer, der kan hjælpe dig med at komme i gang med Defender til Slutpunkt:

|Operativsystemer  |Metoder  |
|---------|---------|
|Windows 10 eller nyere<br/><br/>Windows Server 2019 eller nyere<br/><br/>Windows Server, version 1803 eller nyere<br/><br/>Windows Server 2012 R2 og 2016<sup>[[1](#fn1)]<sup>  |   [Lokalt script (op til 10 enheder)](configure-endpoints-script.md)<br><br/>   [Gruppepolitik](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[Microsoft Endpoint Manager/mobil Enhedshåndtering (Intune)](configure-endpoints-mdm.md)<br>    [VDI-scripts](configure-endpoints-vdi.md) <br><br> **BEMÆRK**: Et lokalt script er egnet til en koncept proof of concept, men bør ikke bruges til produktionsinstallation. I forbindelse med en produktionsinstallation anbefaler vi, at Gruppepolitik, Microsoft Endpoint Configuration Manager eller Intune. |
|Windows Server 2008 R2 SP1 | [Microsoft Overvågningsagent (PLATFORM)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)  eller [Microsoft Defender til Cloud](/azure/security-center/security-center-wdatp) <br><br> **BEMÆRK**! Microsoft Overvågningsagent er nu agent for Azure Log Analytics. Du kan få mere at vide [under Oversigt over loganalyseagent.](/azure/azure-monitor/platform/log-analytics-agent)  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 SP1-Pro<br/><br/>Windows 7 SP1| [Microsoft Overvågningsagent (ÆLDRE)](onboard-downlevel.md) <br><br> **BEMÆRK**! Microsoft Overvågningsagent er nu agent for Azure Log Analytics. Du kan få mere at vide [under Oversigt over loganalyseagent.](/azure/azure-monitor/platform/log-analytics-agent)  
| macOS (se [Systemkrav)](microsoft-defender-endpoint-mac.md) | [Lokalt script](mac-install-manually.md)<br/><br/>[Microsoft Endpoint Manager](mac-install-with-intune.md)<br/><br/>[SYLTEF Pro](mac-install-with-jamf.md)<br/><br/>[Mobildata Enhedshåndtering](mac-install-with-other-mdm.md)   |
| Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements)) |  [Lokalt script](linux-install-manually.md) <br><br/> [Eller Eller](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| iOS | [Microsoft Endpoint Manager](ios-install.md)     |
|Android  | [Microsoft Endpoint Manager](android-intune.md)  | 


(<a id="fn1">1</a>) Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne [i Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).


## <a name="run-a-detection-test"></a>Kør en registreringstest

Du kan kontrollere, at dine onboardede enheder er korrekt forbundet til Defender til slutpunkt, ved at køre en registreringstest.

<br/><br/>

|Operativsystem|Vejledning|
|---|---|
|Windows 10 eller nyere<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server, version 1803 eller nyere<br/><br/>Windows Server 2016<br/><br/>Windows Server 2012 R2|Se [Kør en registreringstest](run-detection-test.md).<br/><br/>Besøg webstedet for demoscenarierne for Defender for Endpoint (<https://demo.wd.microsoft.com>), og prøv et eller flere af scenarierne. Prøv f.eks. **demonstrationsscenariet med skybaseret** beskyttelse.|
|macOS (se [Systemkrav)](microsoft-defender-endpoint-mac.md)|Download og brug DIY-appen på <https://aka.ms/mdatpmacosdiy>. <br/><br/> Du kan finde flere oplysninger [i Defender til Endpoint på macOS](microsoft-defender-endpoint-mac.md).|
|Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements))|1. Kør følgende kommando, og se efter resultatet **1**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. Åbn et Terminal-vindue, og kør følgende kommando: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. Kør følgende kommando for at få vist en liste over registrerede trusler: `mdatp threat list`.<br/><br/>Du kan finde flere oplysninger [under Defender til slutpunkt på Linux](microsoft-defender-endpoint-linux.md).|

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>Bekræft, Microsoft Defender Antivirus er i passiv tilstand på dine slutpunkter

Nu, hvor dine slutpunkter er blevet onboardet til Defender for Endpoint, er det næste trin at sikre, at Microsoft Defender Antivirus kører i passiv tilstand. Du kan bruge en af flere metoder, som beskrevet i følgende tabel:

<br/><br/>

|Metode|Hvad kan du gøre?|
|---|---|
|Kommandoprompt|1. På en Windows skal du åbne Kommandoprompt.<br/><br/>2. Skriv `sc query windefend`, og tryk derefter på Enter.<br/><br/>3. Gennemse resultaterne for at bekræfte, Microsoft Defender Antivirus kører i passiv tilstand.|
|PowerShell|1. Åbn Windows som administrator på Windows PowerShell enhed.<br/><br/>2. Kør følgende PowerShell-cmdlet: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. Gennemse resultaterne. Du bør få vist **Passiv tilstand**.|
|Windows Sikkerhed app|1. På Windows enhed skal du åbne Windows Sikkerhed appen.<br/><br/>2. Vælg **Virus- & trusselsbeskyttelse**.<br/><br/>3. **Under Who jeg? vælg** **Administrer udbydere**.<br/><br/>4. På **siden Sikkerhedsudbydere** under **Antivirus skal** du se efter **, Microsoft Defender Antivirus er slået til**.|
|Jobliste|1. Åbn Windows Jobliste på en enhed med en anden enhed.<br/><br/>2. Vælg **fanen** Detaljer. Se **efterMsMpEng.exe** på listen.|

> [!NOTE]
> Du får muligvis *vist Windows Defender Antivirus* i *stedet for Microsoft Defender Antivirus* i nogle versioner af Windows.
> Du kan få mere at vide om passiv tilstand og aktiv [tilstand under Flere oplysninger om Microsoft Defender Antivirus tilstande](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>Angiv Microsoft Defender Antivirus på Windows server til passiv tilstand manuelt

Hvis du Microsoft Defender Antivirus til passiv tilstand på Windows Server, version 1803 eller nyere eller Windows Server 2019 eller Windows Server 2022, skal du følge disse trin:

1. Åbn Registreringseditor, og gå derefter til:

   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Rediger (eller opret) en DWORD-post **med navnet ForceDefenderPassiveMode**, og angiv følgende indstillinger:
   - Angiv DWORD'ens værdi til **1**.
   - Under **Base skal** du vælge **Hexadecimal**.

> [!NOTE]
> Du kan bruge andre metoder til at angive registreringsdatabasenøglen, f.eks. følgende:
>
> - [Gruppepolitik indstilling](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [Lokalt Gruppepolitik-objektværktøj](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [En pakke i Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>Starte Microsoft Defender Antivirus på Windows Server 2016

Hvis du bruger en Windows Server 2016, skal du muligvis starte Microsoft Defender Antivirus manuelt. Du kan udføre denne opgave ved hjælp af PowerShell-cmdlet'en `mpcmdrun.exe -wdenable` på enheden.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Hent opdateringer til Microsoft Defender Antivirus

Det er Microsoft Defender Antivirus at holde Microsoft Defender Antivirus opdateret for at sikre, at dine enheder har den nyeste teknologi og de nyeste funktioner, der er nødvendige for at beskytte dig mod nye malware- og angrebsteknikker, selvom Microsoft Defender Antivirus kører i passiv tilstand. (Se [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md)).

Der findes to typer opdateringer, der er relateret Microsoft Defender Antivirus holde dem opdateret:

- Sikkerhedsintelligensopdateringer
- Produktopdateringer

Hvis du vil have dine opdateringer, skal du følge [vejledningen i Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>Fjern din løsning, der ikke er fra Microsoft

Hvis du på dette tidspunkt har:

- Onboardet din organisations enheder til Defender for Endpoint, og
- Microsoft Defender Antivirus er installeret og aktiveret,

Derefter er det næste trin at fjerne din løsning til beskyttelse med antivirus, antimalware og slutpunkter, som ikke er Microsoft. Når du fjerner din løsning, der ikke er Microsoft, Microsoft Defender Antivirus skiftes fra passiv tilstand til aktiv tilstand. I de fleste tilfælde sker dette automatisk. 

> [!IMPORTANT]
> Hvis Microsoft Defender Antivirus af en eller anden grund ikke går i aktiv tilstand, når du har fjernet din løsning, der ikke er Microsoft-antivirus/antimalware, kan du se Microsoft Defender Antivirus ser ud til at være gået i stå i [passiv tilstand](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

Kontakt deres tekniske supportteam for at få hjælp til at fjerne din løsning, der ikke er en Microsoft-løsning.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>Sørg for, at Defender til Slutpunkt fungerer korrekt

Nu hvor du har onboardet Defender til Slutpunkt, og du har fjernet din tidligere løsning, som ikke er Microsoft, er det næste trin at sikre, at Defender til Slutpunkt fungerer korrekt. En god måde at udføre denne opgave på er ved at besøge webstedet for demoscenarier for Defender for Endpoint ([https://demo.wd.microsoft.com](https://demo.wd.microsoft.com)). Prøv et eller flere af demonstrationsscenarierne på den pågældende side, herunder mindst følgende:

- Cloud-leveret beskyttelse
- Potentielt uønskede programmer (PUA)
- Netværksbeskyttelse (NP)

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="next-steps"></a>Næste trin

**Tillykke**! Du har fuldført overførslen [til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Gå til dashboardet for sikkerhedshandlinger](security-operations-dashboard.md) i Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)).
- [Administrer Defender for Slutpunkt efter overførslen](manage-mde-post-migration.md).
