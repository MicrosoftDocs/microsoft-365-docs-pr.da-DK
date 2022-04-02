---
title: Indsaml supportlogfiler i Microsoft Defender til slutpunkt ved hjælp af live-svar
description: Få mere at vide om, hvordan du indsamler logfiler ved hjælp af livesvar for at foretage fejlfinding af problemer med Microsoft Defender til Slutpunkt
keywords: support, log, indsaml, fejlfinding, live svar, liveanalyzer, analyzer, live, response
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: a0d0f470a2af18dab298ba3a1af642362590da4c
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63603141"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Indsaml supportlogfiler i Microsoft Defender til slutpunkt ved hjælp af live-svar


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Når du kontakter support, kan du blive bedt om at levere outputpakken til værktøjet Microsoft Defender til Endpoint Client Analyzer.

Dette emne indeholder instruktioner om, hvordan du kører værktøjet via Live Response.

1. Download og hent de nødvendige scripts, der er tilgængelige fra undermappen "Værktøjer" i [Microsoft Defender til Endpoint Client Analyzer](https://aka.ms/BetaMDEAnalyzer). <br>
Hvis du f.eks. vil hente de grundlæggende logfiler for sensor og enhedstilstand, skal du hente ".. \Tools\MDELiveAnalyzer.ps1".<br>
Hvis du også kræver, at der logges Defender Antivirus-MpSupportFiles.cab, skal du hente ".. \Tools\MDELiveAnalyzerAV.ps1" 

2. Start en [direkte svarsession på](live-response.md#initiate-a-live-response-session-on-a-device) den computer, du skal undersøge.

3. Vælg **Upload fil til bibliotek**.

    ![Billede af overførselsfil.](images/upload-file.png)

4. Vælg **Vælg fil**.

    ![Billede af knappen Vælg fil1.](images/choose-file.png)

5. Vælg den hentede fil med navnet MDELiveAnalyzer.ps1 og klik derefter på **Bekræft**

   ![Billede af knappen Vælg fil2.](images/analyzer-file.png)

6. Mens du stadig er i LiveResponse-sessionen, kan du bruge kommandoerne nedenfor til at køre analysefilen og indsamle resultatfilen:

    ```console
    Run MDELiveAnalyzer.ps1
    GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
    ```

    [![Billede af kommandoer.](images/analyzer-commands.png)](images/analyzer-commands.png#lightbox)

> [!NOTE]
>
> - Den nyeste prøveversion af MDEClientAnalyzer kan downloades her: [https://aka.ms/Betamdeanalyzer](https://aka.ms/Betamdeanalyzer).
>
> - LiveAnalyzer-scriptet downloader fejlfindingspakken på destinationscomputeren fra: https://mdatpclientanalyzer.blob.core.windows.net.
>
>   Hvis du ikke kan tillade, at maskinen når URL-adressen ovenfor, skal MDEClientAnalyzerPreview.zip filen til biblioteket, før du kører scriptet LiveAnalyzer:
>
>   ```console
>   PutFile MDEClientAnalyzerPreview.zip -overwrite
>   Run MDELiveAnalyzer.ps1
>   GetFile "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\MDEClientAnalyzerResult.zip"
>   ```
>
> - Du kan finde flere oplysninger om indsamling af data lokalt på en computer, hvis computeren ikke kommunikerer med Microsoft Defender til endpoint-skytjenester, eller hvis den ikke vises i Microsoft Defender til Endpoint-portalen som forventet, i Bekræft klientforbindelsen til [Microsoft Defender for Endpoint-tjenestens URL-adresser](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).
> 
> - Som beskrevet i [eksempler](live-response-command-examples.md) på kommandoen Direkte svar kan det være en god ide at bruge symbolet "&" i slutningen af kommandoen til at indsamle logfiler som en baggrundshandling:
>   ```console
>   Run MDELiveAnalyzer.ps1&
>   ```


## <a name="see-also"></a>Se også
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalyse](download-client-analyzer.md)
- [Kør klientanalysen på Windows](run-analyzer-windows.md)
- [Kør klientanalyse på macOS eller Linux](run-analyzer-macos-linux.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)
- [Forstå HTML-analyserapporten](analyzer-report.md)
