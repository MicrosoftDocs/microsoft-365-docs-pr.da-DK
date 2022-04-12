---
title: Konfigurer lokale tilsidesættelser for Microsoft Defender Antivirus indstillinger
description: Aktivér eller deaktiver brugere i at ændre indstillinger lokalt i Microsoft Defender AV.
keywords: lokal tilsidesættelse, lokal politik, gruppepolitik, gruppepolitik, låsning, fletning, lister
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: ae90694bab8191c2ad83fa1de7563bc2ba7643e8
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789750"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Undgå eller tillad, at brugerne ændrer Microsoft Defender Antivirus politikindstillinger lokalt


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Som standard forhindrer Microsoft Defender Antivirus indstillinger, der installeres via et Gruppepolitik objekt til slutpunkterne i dit netværk, brugerne i at ændre indstillingerne lokalt. Du kan ændre dette i nogle tilfælde.

Det kan f.eks. være nødvendigt at give visse brugergrupper (f.eks. sikkerhedsforskere og trusselsforskere) yderligere kontrol over individuelle indstillinger på de slutpunkter, de bruger.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Konfigurer lokale tilsidesættelser for Microsoft Defender Antivirus indstillinger

Standardindstillingen for disse politikker er **Deaktiveret**.

Hvis de er **indstillet til Aktiveret**, kan brugere på slutpunkter foretage ændringer af den tilknyttede indstilling med [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md), lokale indstillinger for Gruppepolitik og PowerShell-cmdlet'er (hvor det er relevant).

I følgende tabel vises hver af politikindstillingen til tilsidesættelse og konfigurationsvejledningen for den tilknyttede funktion eller indstilling.

Sådan konfigurerer du disse indstillinger:

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. I **redigeringseditoren til Gruppepolitik** skal du gå til **Computerkonfiguration** og klikke på **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** >  **Microsoft Defender Antivirus** og derefter den **Placering,** der er angivet i tabellen med indstillinger (i denne artikel).

4. Dobbeltklik på **politikindstillingen** som angivet i tabellen nedenfor, og angiv indstillingen til den ønskede konfiguration. Klik på **OK**, og gentag for andre indstillinger.

5. Installer det Gruppepolitik objekt som normalt.

## <a name="table-of-settings"></a>Tabel med indstillinger

<br/><br/>

| Placering | Indstilling | Artikel |
|---|---|---|---|
| KORT |Konfigurer tilsidesættelse af lokale indstillinger for rapportering til Microsoft MAPS|[Aktivér skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Karantæne|Konfigurer tilsidesættelse af lokale indstillinger for fjernelse af elementer fra karantænemappen|[Konfigurer afhjælpning for scanninger](configure-remediation-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for overvågning af fil- og programaktivitet på computeren|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for overvågning for indgående og udgående filaktivitet | [Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for aktivering af overvågning af funktionsmåde|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokal indstilling for at aktivere beskyttelse i realtid|[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse og overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Oprydning|Konfigurer tilsidesættelse af lokal indstilling for tidspunktet på dagen for at køre en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurer afhjælpning for scanninger](configure-remediation-microsoft-defender-antivirus.md) |
| Skan|Konfigurer tilsidesættelse af lokal indstilling for maksimal procentdel af CPU-udnyttelse|[Konfigurer og kør scanninger](run-scan-microsoft-defender-antivirus.md) |
| Skan|Konfigurer tilsidesættelse af lokal indstilling for planlægning af scanningsdag|[Konfigurer planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skan|Konfigurer tilsidesættelse af lokal indstilling for planlagt hurtigsøgningstid|[Konfigurer planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skan|Konfigurer tilsidesættelse af lokal indstilling for planlagt scanningstid|[Konfigurer planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Skan|Konfigurer tilsidesættelse af lokal indstilling for den scanningstype, der skal bruges til en planlagt scanning|[Konfigurer planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Konfigurer, hvordan lister over trusler og udeladelser, der er defineret lokalt og globalt, flettes

Du kan også konfigurere, hvordan lokalt definerede lister kombineres eller flettes med globalt definerede lister. Denne indstilling gælder for [udeladelseslister](configure-exclusions-microsoft-defender-antivirus.md), [angivne afhjælpningslister](configure-remediation-microsoft-defender-antivirus.md) og [reduktion af angrebsoverfladen](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Lister, der er konfigureret i den lokale gruppepolitik og Windows Sikkerhed-appen, flettes som standard med lister, der er defineret af det relevante Gruppepolitik objekt, som du har installeret på netværket. Hvis der er konflikter, har den globalt definerede liste forrang.

Du kan deaktivere denne indstilling for at sikre, at der kun bruges globalt definerede lister (f.eks. lister fra alle udrullede gruppepolitikobjekter).

### <a name="use-group-policy-to-disable-local-list-merging"></a>Brug Gruppepolitik til at deaktivere fletning af lokale lister

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. I **redigeringseditoren til Gruppepolitik** skal du gå til **Computerkonfiguration** og klikke på **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus**.

4. Dobbeltklik på **Konfigurer funktionsmåden for lokal administratorfletning for lister** , og angiv indstillingen til **Deaktiveret**. Klik på **OK**.

> [!NOTE]
> Hvis du deaktiverer fletning af lokale lister, tilsidesættes indstillinger for kontrolleret mappeadgang. Den tilsidesætter også alle beskyttede mapper eller tilladte apps, der er angivet af den lokale administrator. Du kan få flere oplysninger om indstillinger for kontrolleret mappeadgang under [Tillad en blokeret app i Windows Sikkerhed](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurer slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md)
