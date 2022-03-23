---
title: Fejlfinding af problemer med kerneudvidelsen i Microsoft Defender til slutpunkt på macOS
description: Fejlfinding i forbindelse med udvidelsesrelaterede problemer i Microsoft Defender til slutpunkt på macOS.
keywords: microsoft, defender, Microsoft Defender til Slutpunkt, mac, kernel, udvidelse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ba52d9587a2ac530eabeacf8c72336751a1a17d7
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63591824"
---
# <a name="troubleshoot-kernel-extension-issues-in-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af problemer med kerneudvidelsen i Microsoft Defender til slutpunkt på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Denne artikel indeholder oplysninger om fejlfinding af problemer med kerneudvidelsen, der er installeret som en del af Microsoft Defender til slutpunkt på macOS.

Fra og med macOS High Sierra (10.13) kræver macOS alle kerneudvidelser for at blive eksplicit godkendt, før de må køre på enheden.

Hvis du ikke godkender kerneudvidelsen under udrulning/installation af Microsoft Defender til slutpunkt på macOS, viser programmet et banner, der beder dig om at aktivere den:

   ![Skærmbilledet RTP deaktiveret.](images/mdatp-32-main-app-fix.png)

Du kan også køre ```mdatp health```. Den rapporterer, hvis beskyttelse i realtid er aktiveret, men ikke tilgængelig. Dette angiver, at kerneudvidelsen ikke er godkendt til at køre på din enhed.

```bash
mdatp health
```
```Output
...
real_time_protection_enabled                : false
real_time_protection_available              : true
...
```

De følgende afsnit indeholder en vejledning til, hvordan du kan løse dette problem, afhængigt af den metode, du brugte til at installere Microsoft Defender for Endpoint på macOS.

## <a name="managed-deployment"></a>Administreret installation

Se de instruktioner, der svarer til det administrationsværktøj, du brugte til at installere produktet:

- [SYLF-baseret installation](mac-install-with-jamf.md)
- [Microsoft Intune-baseret installation](mac-install-with-intune.md#create-system-configuration-profiles)

## <a name="manual-deployment"></a>Manuel udrulning

Hvis der er gået mindre end 30 minutter, siden produktet blev installeret, skal du gå til Sikkerhed og beskyttelse af personlige oplysninger **&** **Systemindstillinger**\>, hvor du skal **Tillade systemsoftware** fra udviklere "Microsoft Corporation".

Hvis du ikke kan se denne prompt, betyder det, at der er gået 30 minutter eller mere, og kerneudvidelsen stadig ikke er godkendt til at køre på din enhed:

![Skærmbilledet Sikkerhed og beskyttelse af personlige oplysninger efter prompten er udløbet.](images/mdatp-33-securityprivacysettings-noprompt.png)

I dette tilfælde skal du udføre følgende trin for at udløse godkendelsesflowet igen.

1. Forsøg at installere driveren i Terminal. Følgende handling mislykkes, fordi kerneudvidelsen ikke blev godkendt til at køre på enheden. Det udløser dog godkendelsesflowet igen.

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    ```Output
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Diagnostics for /Library/Extensions/wdavkext.kext:
    ```

2. Åbn **Systemindstillinger Sikkerhed** \> **og &** i menuen. (Luk det først, hvis det er åbnet.)

3. **Tillad** systemsoftware fra udviklere "Microsoft Corporation"

4. Installer driveren igen i Terminal. Denne gang lykkes handlingen:

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    Banneret burde forsvinde fra Defender-programmet og bør nu ```mdatp health``` rapportere, at beskyttelse i realtid både er aktiveret og tilgængelig:

    ```bash
    mdatp health
    ```

    ```Output
    ...
    real_time_protection_enabled                : true
    real_time_protection_available              : true
    ...
    ```
