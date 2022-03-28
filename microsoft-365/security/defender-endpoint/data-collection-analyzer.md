---
title: Dataindsamling til avanceret fejlfinding på Windows
description: Få mere at vide om, hvordan du bruger klientanalysen til at indsamle data til komplekse fejlfindingsscenarier
keywords: software, indsamle data, foretage fejlfinding af mdeclientanalyzer, avanceret fejlfinding
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 513432dfb24af89451c4d8290ce5fde0951819b9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596860"
---
# <a name="data-collection-for-advanced-troubleshooting-on-windows"></a>Dataindsamling til avanceret fejlfinding på Windows

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når du samarbejder med Microsofts supportmedarbejdere, kan du blive bedt om at bruge klientanalysen til at indsamle data til fejlfinding i mere komplekse scenarier. Analysescriptet understøtter andre parametre til dette formål og kan indsamle et bestemt logsæt baseret på de observerede symptomer, der skal undersøges.

Kør '**MDEClientAnalyzer.cmd /?**' for at få vist listen over tilgængelige parametre og beskrivelsen af dem:

![Billede af parametre for klientanalyse på kommandolinjen.](images/d89a1c04cf8441e4df72005879871bd0.png)

> [!NOTE]
> Når en avanceret fejlfindingsparameter bruges, ringer analysatoren også ind [ iMpCmdRun.exe](/microsoft-365/security/defender-endpoint/command-line-arguments-microsoft-defender-antivirus) indsamle Microsoft Defender Antivirus relaterede supportlogfiler.

**-h** - Opkald [Windows Performance Recorder](/windows-hardware/test/wpt/wpr-command-line-options) for at indsamle en detaljeret generel sporing af ydeevnen ud over standardlogsættet.

**-l** - Opkald i indbygget Windows [Performance Monitor for](/windows-server/remote/remote-desktop-services/rds-rdsh-performance-counters) at indsamle en let perfmon-sporing. Dette kan være nyttigt, når du vil diagnosticere problemer med langsom ydeevne, der kan opstå over tid, men som er svær at genskabe efter behov.

**-c** - Opkald i [procesovervågning](/sysinternals/downloads/procmon) for avanceret overvågning af filsystem, registreringsdatabasen og proces/trådaktivitet i realtid. Dette er især nyttigt ved fejlfinding af forskellige scenarier med programkompatibilitet.

**-i** - Opkald i indbygget [netsh.exe](/windows/win32/winsock/netsh-exe) kommando til at starte en netværks- og Windows Firewall-sporing, der er nyttig til fejlfinding af forskellige netværksrelaterede problemer.

**-b** - Det samme som '-c', men procesovervågningssporingen startes ved næste start og stoppes kun, når -b bruges igen.

**-a** – Opkald [til Windows Performance Recorder](/windows-hardware/test/wpt/wpr-command-line-options) for at indsamle en detaljeret ydeevnesporing, der er specifik for analyse af problemer med høj CPU i forbindelse med antivirusprocessen (MsMpEng.exe).

**-v** – anvenderMpCmdRun.exe [ med kommandolinjeargumentet](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus) med de fleste detaljerede sporingsflag.

**-t** - Starter detaljeret sporing af alle klientsidekomponenter, der er relevante for slutpunktet DLP. Dette er nyttigt til scenarier, hvor [DLP-handlinger](/microsoft-365/compliance/endpoint-dlp-learn-about#endpoint-activities-you-can-monitor-and-take-action-on) ikke sker som forventet for filer.

**-q** - Opkald DLPDiagnose.ps1 script fra analyseværktøjsmappen, der validerer den grundlæggende konfiguration og kravene til Slutpunkt DLP.

**-d** - Indsamler en hukommelsesdump af **MsSenseS**.exe (sensorprocessen på Windows Server 2016 eller ældre operativsystem) og relaterede processer.

- \* Dette flag kan bruges sammen med ovenstående flag.
- \*\* Registrering af et hukommelsesdump af [PPL-beskyttede](/windows-hardware/drivers/install/early-launch-antimalware) processer, f.eks. MsSense.exe eller MsMpEng.exe, understøttes ikke af analyseatoren på nuværende tidspunkt.

**-z** – Konfigurerer registreringsdatabasenøgler på computeren for at forberede den til samling af hukommelsesdump af hele computeren via [CrashOnCtrlScroll](/windows-hardware/drivers/debugger/forcing-a-system-crash-from-the-keyboard). Dette ville være nyttigt til analyse af problemer med computerens frys.

\* Hold Ctrl-tasten længst til højre nede, og tryk to gange på Tasten Scroll Lock.

**-k** – bruger [værktøjet NotMyFault](/sysinternals/downloads/notmyfault) til at tvinge systemet til at gå ned og generere et hukommelsesdump af en maskine. Dette ville være nyttigt til analyse af forskellige stabilitetsproblemer med operativsystemet.

Analyseværktøj og alle ovenstående scenarieflag kan startes eksternt ved at køre 'RemoteMDEClientAnalyzer.cmd', som også er bundtet i analyseværktøjssættet:

![Billede af kommandolinje med analyseoplysninger.](images/57cab9d82d08f672a92bf9e748ac9572.png)

> [!NOTE]
>
> - Når du bruger RemoteMDEClientAnalyzer.cmd, ringer det ind til psexec for at downloade værktøjet fra den konfigurerede filshare og derefter køre det lokalt via PsExec.exe.
    CMD-scriptet anvender et "-r"-flag til at angive, at det kører eksternt i SYSTEM-kontekst, så der vises ingen prompt til brugeren.
> - Det samme flag kan bruges med MDEClientAnalyzer.cmd for at undgå at blive bedt om at angive antallet af minutter til indsamling af data. Eksempel:
>
>    **MDEClientAnalyzer.cmd -r -i -m 5**
>
>   - **-r** – Angiver, at værktøjet køres fra en fjernforbindelse (eller en ikke-interaktiv kontekst)
>   - **-i** - Scenarieflag til indsamling af netværkssporing sammen med andre relaterede logfiler
>   - **-m** \# - Antallet af minutter, der skal køres (5 minutter i eksemplet ovenfor)
