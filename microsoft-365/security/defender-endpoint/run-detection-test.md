---
title: Kør en registreringstest på en enhed for at bekræfte, at den er blevet korrekt onboardet til Microsoft Defender til Slutpunkt
description: Kør registreringstestscriptet på en enhed, der for nylig er blevet onboardet til Microsoft Defender for Endpoint-tjenesten, for at bekræfte, at den er tilføjet korrekt.
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
ms.openlocfilehash: 41ba14fd2e4a9e3726e4ef4287812cf8d3ffb2d1
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592919"
---
# <a name="run-a-detection-test-on-a-newly-onboarded-microsoft-defender-for-endpoint-device"></a>Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- Windows 11
- Understøttede Windows 10 versioner
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server, version 1803
- Windows Server 2019
- Windows Server 2022
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du føjer en enhed til Microsoft Defender for Endpoint-tjenesten for administration, kaldes det også onboardingenheder. Onboarding gør det muligt for enheder at rapportere signaler om deres tilstand til tjenesten.

At sikre, eller bekræfte, at en enhed er blevet føjet til tjenesten, er et vigtigt trin i hele installationsprocessen. Den forsikrer dig om, at alle de forventede enheder administreres. 

## <a name="verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test"></a>Bekræft microsoft Defender til slutpunkt-onboarding af en enhed ved hjælp af en PowerShell-registreringstest

Kør følgende PowerShell-script på en nyligt onboardet enhed for at bekræfte, at den rapporterer korrekt til Defender for Endpoint-tjenesten.

1. Opret en mappe: 'C:\test-MDATP-test'.
2. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:

   1. Gå til **Start,** og skriv **cmd**.

   1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

      ![Vinduesruden menuen Start pege på Kør som administrator.](images/run-as-admin.png)

3. Når du bliver bedt om det, skal du kopiere og køre følgende kommando:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Vinduet Kommandoprompt lukkes automatisk. Hvis det lykkes, vises der en ny besked i portalen for den onboardede enhed om ca. ti minutter.

## <a name="related-topics"></a>Relaterede emner

- [Onboard Windows-enheder](configure-endpoints.md)
- [Onboard-servere](configure-server-endpoints.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)
