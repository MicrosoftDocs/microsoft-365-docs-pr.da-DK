---
title: Kør klientanalysen på Windows
description: Få mere at vide om, hvordan du kører Microsoft Defender for Endpoint Client Analyzer på Windows.
keywords: klientanalyse, fejlfinding af sensor, analyse, mdeanalyzer, windows
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
ms.openlocfilehash: 5ac27241297b9943f1559653777b8e1668fe7f89
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783023"
---
# <a name="run-the-client-analyzer-on-windows"></a>Kør klientanalysen på Windows

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. Download [værktøjet MDE-klientanalyse](https://aka.ms/mdatpanalyzer) til den Windows maskine, du skal undersøge.

2. Udpak indholdet af MDEClientAnalyzer.zip på maskinen.

3. Åbn en kommandolinje med administratorrettigheder:
    1. Gå til **Start,** og skriv **cmd**.
    2. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

4. Angiv følgende kommando, og tryk på **Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **Erstat HardDrivePath med den sti, som værktøjet blev udtrukket til, f.eks.:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Ud over ovenstående er der også en mulighed for at [indsamle logfiler for understøttelse af analyse ved hjælp af live-svar.](troubleshoot-collect-support-log.md).

> [!NOTE]
> På Windows 10/11, Windows Server 2019/2022 eller Windows Server 2012R2/2016, hvor den [moderne unified løsning](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) er installeret, kalder klientanalysescriptet til en eksekverbar fil, der kaldes `MDEClientAnalyzer.exe` for at køre forbindelsestest til URL-adresser til cloudtjenesten.
>
> På Windows 8.1, Windows Server 2016 eller en tidligere os-udgave, hvor Microsoft Monitoring Agent (MMA) bruges til onboarding, kalder klientanalysescriptet til en eksekverbar fil, der kaldes `MDEClientAnalyzerPreviousVersion.exe` for at køre forbindelsestest for URL-adresser til kommando og kontrol (CnC), samtidig med at der også ringes til Microsoft Monitoring Agent-forbindelsesværktøjet `TestCloudConnection.exe` til URL-adresser til cyberdatakanaler.


Alle PowerShell-scripts og -moduler, der er inkluderet i analysen, er Signeret af Microsoft.
Hvis filer er blevet ændret på nogen måde, forventes analysen at blive afsluttet med følgende fejl:

:::image type="content" source="images/sigerror.png" alt-text="Klientanalysefejlen" lightbox="images/sigerror.png":::


Hvis denne fejl vises, indeholder outputtet for issuerInfo.txt detaljerede oplysninger om, hvorfor det skete, og hvilken fil der blev påvirket:

:::image type="content" source="images/issuerinfo.png" alt-text="Udstederoplysningerne" lightbox="images/issuerinfo.png":::


Eksempelindhold efter ændring af MDEClientAnalyzer.ps1:

:::image type="content" source="images/modified-ps1.png" alt-text="Den ændrede ps1-fil" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Resultatpakkeindhold på Windows

> [!NOTE]
> De nøjagtige filer, der registreres, kan ændre sig afhængigt af faktorer som:
>
> - Den version af Windows, som analysefunktionen køres på.
> - Tilgængelighed af hændelseslogkanal på computeren.
> - Starttilstanden for den Slutpunktsregistrering og -svar sensor (assistenten stoppes, hvis maskinen endnu ikke er onboardet).
> - Hvis der blev brugt en avanceret fejlfindingsparameter sammen med analysekommandoen.

Den udpakkede MDEClientAnalyzerResult.zip fil indeholder som standard følgende elementer.

- MDEClientAnalyzer.htm

  Dette er den primære HTML-outputfil, som indeholder de resultater og den vejledning, som analysescriptet, der kører på computeren, kan producere.

- Mappen SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    Beskrivelse: Liste over x86-installeret software på x64 OS-software, der er indsamlet fra registreringsdatabasen.

  - AddRemoveProgramsWOW64.csv

    Beskrivelse: Liste over x86-installeret software på x64 OS-software, der er indsamlet fra registreringsdatabasen.

    - CertValidate.log

      Beskrivelse: Detaljeret resultat af certifikattilbagekaldelse udført ved at kalde til [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      Beskrivelse: Output fra kørsel af [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). Dette indeholder oplysninger om computerens Azure AD-status.

    - IFEO.txt

      Beskrivelse: Output af [indstillinger for udførelse af billedfil](/previous-versions/windows/desktop/xperf/image-file-execution-options) , der er konfigureret på computeren

    - MDEClientAnalyzer.txt

      Beskrivelse: Dette er en detaljeret tekstfil, der vises med oplysninger om udførelsen af analysescriptet.

    - MDEClientAnalyzer.xml

      Beskrivelse: XML-format, der indeholder resultaterne af analysescriptet.

    - RegOnboardedInfoCurrent.Json

      Beskrivelse: De onboardede computeroplysninger, der er indsamlet i JSON-format fra registreringsdatabasen.

  - RegOnboardingInfoPolicy.Json

    Beskrivelse: Konfigurationen af onboardingpolitikken, der er indsamlet i JSON-format fra registreringsdatabasen.

    - SCHANNEL.txt

      Beskrivelse: Oplysninger om [SCHANNEL-konfiguration](/windows-server/security/tls/manage-tls) , der anvendes på computeren, som indsamles fra registreringsdatabasen.

    - SessionManager.txt

      Beskrivelse: Session Manager-specifikke indstillinger indsamles fra registreringsdatabasen.

    - SSL_00010002.txt

      Beskrivelse: Oplysninger om [DEN SSL-konfiguration](/windows-server/security/tls/manage-tls) , der anvendes på den computer, der er indsamlet fra registreringsdatabasen.

- EventLogs [mappe]

  - utc.evtx

    Beskrivelse: Eksport af DiagTrack-hændelseslog

  - senseIR.evtx

    Beskrivelse: Eksport af hændelsesloggen til automatiseret undersøgelse

  - sense.evtx

    Beskrivelse: Eksport af hovedhændelsesloggen for sensoren

  - OperationsManager.evtx

    Beskrivelse: Eksport af Microsoft Monitoring Agent-hændelsesloggen




## <a name="see-also"></a>Se også

- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalysen](download-client-analyzer.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)
- [Forstå HTML-analyserapporten](analyzer-report.md)
