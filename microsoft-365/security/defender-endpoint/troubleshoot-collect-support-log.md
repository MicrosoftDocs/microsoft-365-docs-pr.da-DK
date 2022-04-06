---
title: Indsaml supportlogfiler i Microsoft Defender for Endpoint ved hjælp af live-svar
description: Få mere at vide om, hvordan du indsamler logfiler ved hjælp af livesvar for at foretage fejlfinding Microsoft Defender for Endpoint problemer
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
ms.openlocfilehash: 138b532e7786a3d142c3cbbe68f668a4b0e05591
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472567"
---
# <a name="collect-support-logs-in-microsoft-defender-for-endpoint-using-live-response"></a>Indsaml supportlogfiler i Microsoft Defender for Endpoint ved hjælp af live-svar


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)


Når du kontakter support, kan du blive bedt om at levere outputpakken til Microsoft Defender for Endpoint Client Analyzer.

Dette emne indeholder instruktioner om, hvordan du kører værktøjet via Live Response.

1. Download og hent de nødvendige scripts, der er tilgængelige fra undermappen "Værktøjer" [i Microsoft Defender for Endpoint Client Analyzer](https://aka.ms/BetaMDEAnalyzer). <br>
Hvis du f.eks. vil hente de grundlæggende logfiler for sensor og enhedstilstand, skal du hente ".. \Tools\MDELiveAnalyzer.ps1".<br>
Hvis du også kræver, at der logges Defender Antivirus-MpSupportFiles.cab, skal du hente ".. \Tools\MDELiveAnalyzerAV.ps1" 

2. Start en [direkte svarsession på](live-response.md#initiate-a-live-response-session-on-a-device) den computer, du skal undersøge.

3. Vælg **Upload fil til bibliotek**.

   :::image type="content" source="images/upload-file.png" alt-text="Overførselsfilen" lightbox="images/upload-file.png":::

4. Vælg **Vælg fil**.

   :::image type="content" source="images/choose-file.png" alt-text="Knappen Vælg fil-1" lightbox="images/choose-file.png":::

5. Vælg den hentede fil med navnet MDELiveAnalyzer.ps1 og klik derefter på **Bekræft**

   :::image type="content" source="images/analyzer-file.png" alt-text="Knappen Vælg fil-2" lightbox="images/analyzer-file.png":::

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
> - Du kan finde flere oplysninger om indsamling af data lokalt på en computer, hvis computeren ikke kommunikerer med Microsoft Defender for Endpoint-skytjenester eller ikke vises på Microsoft Defender for Endpoint-portalen som forventet, i Bekræfte klientforbindelsen til [ Microsoft Defender for Endpoint til tjenester](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).
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
