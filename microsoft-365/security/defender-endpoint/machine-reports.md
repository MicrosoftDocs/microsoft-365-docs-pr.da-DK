---
title: Rapport over enhedens tilstand og overholdelse af angivne standarder i Microsoft Defender for Endpoint
description: Spor tilstandsregistreringer for enheden, antivirusstatus, OS-platform og Windows 10 versioner ved hjælp af rapporten om enhedens tilstand og overholdelse af angivne standarder
keywords: tilstand, antivirus, os-platform, windows 10-version, version, tilstand, overholdelse, tilstand
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d171db0d5009cc32c34c3bf95da907221f275410
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789266"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Rapport over enhedens tilstand og overholdelse af angivne standarder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus 

**Platforme**
- Windows
- Mac OS
- Linux
- Ios
- Android

Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Statusrapporten for enheder indeholder oplysninger på højt niveau om enhederne i din organisation. Rapporten indeholder tendensoplysninger, der viser sensortilstandstilstanden, antivirusstatus, OS-platforme og Windows 10 (og Windows 11) versioner.

Dashboardet er struktureret i to afsnit:

:::image type="content" source="images/device-reports.png" alt-text="Enhedsrapporten" lightbox="images/device-reports.png":::


<br>

****

|Afsnit|Beskrivelse|
|---|---|
|1|Enhedstendenser|
|2|Enhedsoversigt (aktuel dag)|
|||

## <a name="device-trends"></a>Enhedstendenser

Enhedstendenser viser som standard enhedsoplysninger fra den 30-dages periode, der slutter med den seneste hele dag. Hvis du vil have et bedre overblik over tendenser i din organisation, kan du finjustere rapporteringsperioden ved at justere den viste tidsperiode. Hvis du vil justere tidsperioden, skal du vælge et tidsinterval på rullelisten:

- 30 dage
- Tre måneder
- Seks måneder
- Brugerdefinerede

> [!NOTE]
> Disse filtre anvendes kun i afsnittet enhedstendenser. Det påvirker ikke sektionen enhedsoversigt.

## <a name="device-summary"></a>Enhedsoversigt

Mens enhedstendenserne viser populære enhedsoplysninger, viser enhedsoversigten enhedsoplysninger, der er begrænset til den aktuelle dag.

> [!NOTE]
> De data, der afspejles i oversigtsafsnittet, er begrænset til 180 dage før dags dato. Hvis dags dato f.eks. er den 27. marts 2019, afspejler dataene i oversigtsafsnittet tal fra 28. september 2018 til 27. marts 2019.
>
> Filteret, der anvendes på sektionen tendenser, anvendes ikke i oversigtsafsnittet.

Afsnittet om enhedstendenser giver dig mulighed for at foretage detailudledning på enhedslisten med det tilsvarende filter anvendt på den. Hvis du f.eks. klikker på linjen Inactive på kortet Sensortilstand, får du vist enhedslisten med resultater, der kun viser enheder, hvis sensorstatus er inaktiv.

## <a name="device-attributes"></a>Enhedsattributter

Rapporten består af kort, der viser følgende enhedsattributter:

- **Tilstandstilstand**: Viser oplysninger om sensortilstanden på enheder, hvilket giver en samlet visning af enheder, der er aktive, oplever nedsat kommunikation, inaktive, eller hvor der ikke ses sensordata.
- **Antivirusstatus for aktive Windows 10 enheder**: Viser antallet af enheder og status for Microsoft Defender Antivirus.
- **OS-platforme**: Viser distributionen af OS-platforme, der findes i din organisation.
- **Windows 10 versioner**: Viser distributionen af Windows 10 enheder og deres versioner i din organisation.

## <a name="filter-data"></a>Filtrer data

Brug de angivne filtre til at inkludere eller udelade enheder med visse attributter.

Du kan vælge flere filtre, der skal anvendes fra enhedsattributterne.

> [!NOTE]
> Disse filtre gælder for **alle** kort i rapporten.

Hvis du f.eks. vil have vist data om Windows 10 enheder med tilstanden Aktiv sensortilstand:

1. Under **Filtre > Tilstandstilstand for sensor > Aktiv**.
2. Vælg derefter **OS-platforme > Windows 10**.
3. Vælg **Anvend**.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-topic"></a>Relateret emne

- [Rapport om trusselsbeskyttelse](threat-protection-reports.md)
