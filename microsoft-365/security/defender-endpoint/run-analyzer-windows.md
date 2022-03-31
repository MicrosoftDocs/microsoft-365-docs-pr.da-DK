---
title: Kør klientanalysen på Windows
description: Få mere at vide om, hvordan du kører Microsoft Defender for Endpoint Client Analyzer på Windows.
keywords: klientanalyse, fejlfinding af sensor, analyseprogram, mdeanalyzer, windows
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 092a89e41efebafae36e81f5faa7cd3b52fde8d9
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/31/2022
ms.locfileid: "63600946"
---
# <a name="run-the-client-analyzer-on-windows"></a>Kør klientanalysen på Windows

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. Download [værktøjet MDE Client Analyzer på](https://aka.ms/mdatpanalyzer) den computer Windows skal undersøge.

2. Udtræk indholdet MDEClientAnalyzer.zip på maskinen.

3. Åbn en administrator-kommandolinje:
    1. Gå til **Start,** og skriv **cmd**.
    2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

4. Angiv følgende kommando, og tryk på **Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **Erstat HardDrivePath med den sti, som værktøjet blev udtrukket til, f.eks.:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Ud over ovenstående er der også mulighed for at indsamle [supportlogfiler fra analyseatoren ved hjælp af livesvar](troubleshoot-collect-support-log.md).

> [!NOTE]
> På Windows 10/11, Windows Server 2019/2022 eller Windows Server 2012R2/2016 med den moderne samlede løsning installeret kalder [](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) `MDEClientAnalyzer.exe` klientanalysescriptet en eksekverbar fil kaldet at køre forbindelsestests til skytjeneste-URL-adresser.
>
> På Windows 8.1, Windows Server 2016 eller en tidligere version af operativsystemet, hvor Microsoft Monitoring Agent (AGENT) bruges til onboarding, kalder klienten Analyzer script calls into an executable `MDEClientAnalyzerPreviousVersion.exe` file called to run connectivity tests for Command and Control (CnC) URL-adresser, mens du også ringer til Microsoft Monitoring Agent Connectivity Tool `TestCloudConnection.exe` for Cyber Data Channel URL-adresser.


Alle PowerShell-scripts og -moduler, der følger med analyseanalysen, er signeret af Microsoft.
Hvis filerne er blevet ændret på nogen måde, forventes analysatoren at afslutte med følgende fejl:

![Billede af fejl i klientanalyse](images/sigerror.png)


Hvis denne fejl vises, indeholder outputtet issuerInfo.txt detaljerede oplysninger om, hvorfor det skete, og hvilken fil der blev påvirket:

![Billede af oplysninger om udsteder](images/issuerinfo.png)


Eksempelindhold, når MDEClientAnalyzer.ps1 er blevet ændret:

![Billede af ændret ps1-fil](images/modified-ps1.png)



## <a name="result-package-contents-on-windows"></a>Indhold af resultatpakke på Windows

> [!NOTE]
> De nøjagtige filer, der registreres, kan ændres afhængigt af faktorer som f.eks.:
>
> - Den version af vinduer, som analysatoren kører på.
> - Tilgængelighed af begivenhedsloggen på computeren.
> - Starttilstanden for sensoren Slutpunktsregistrering og -svar (Sense stoppes, hvis maskinen endnu ikke er onboardet).
> - Hvis en avanceret fejlfindingsparameter blev brugt sammen med analysekommandoen.

Som standard vil den udpakkede MDEClientAnalyzerResult.zip indeholde følgende elementer.

- MDEClientAnalyzer.htm

  Dette er den primære HTML-outputfil, som indeholder de fund og vejledninger, som analysescriptet kan køre på computeren kan producere.

- Mappen SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Beskrivelse: Liste over x86-installeret software på x64 OS-software, der er indsamlet fra registreringsdatabasen.

  - AddRemoveProgramsWOW64.csv

    Beskrivelse: Liste over x86-installeret software på x64 OS-software, der er indsamlet fra registreringsdatabasen.

    - CertValidate.log

      Beskrivelse: Detaljeret resultat af tilbagekaldte certifikater udført ved at kalde op [i CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Beskrivelse: Output fra [kørende dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Dette indeholder oplysninger om Azure AD-status for computeren.

    - IFEO.txt

      Beskrivelse: Output af indstillinger [for billedfiludførelse](/previous-versions/windows/desktop/xperf/image-file-execution-options) konfigureret på computeren

    - MDEClientAnalyzer.txt

      Beskrivelse: Dette er detaljeret tekstfil, der vises med oplysninger om udførelse af scriptet til analyse.

    - MDEClientAnalyzer.xml

      Beskrivelse: XML-format, der indeholder analysescriptet.

    - RegOnboardedInfoCurrent.Json

      Beskrivelse: Oplysningerne om onboarded machine, der er indsamlet i JSON-format fra registreringsdatabasen.

  - RegOnboardingInfoPolicy.Json

    Beskrivelse: Konfigurationen af onboardingpolitikken er indsamlet i JSON-format fra registreringsdatabasen.

    - SCHANNEL.txt

      Beskrivelse: Oplysninger om [SCHANNEL-konfiguration](/windows-server/security/tls/manage-tls) anvendt på computeren, sådan som det er indsamlet fra registreringsdatabasen.

    - SessionManager.txt

      Beskrivelse: Sessionsadministrator bestemte indstillinger, der indsamles fra registreringsdatabasen.

    - SSL_00010002.txt

      Beskrivelse: Oplysninger om [SSL-konfiguration](/windows-server/security/tls/manage-tls) anvendt på den computer, der er indsamlet fra registreringsdatabasen.

- Hændelseslogs [Mappe]

  - utc.evtx

    Beskrivelse: Eksport af DiagTrack-hændelseslog

  - senseIR.evtx

    Beskrivelse: Eksport af hændelsesloggen for automatiseret undersøgelse

  - sense.evtx

    Beskrivelse: Eksport af logbogen for den primære sensorbegivenhed

  - OperationsManager.evtx

    Beskrivelse: Eksport af hændelsesloggen for Microsoft Overvågningsagent




## <a name="see-also"></a>Se også

- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalyse](download-client-analyzer.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)
- [Forstå HTML-analyserapporten](analyzer-report.md)
