---
title: Brug kommandolinjen til at administrere Microsoft Defender Antivirus
description: Kør Microsoft Defender Antivirus scanninger, og konfigurer næste generations beskyttelse med et dedikeret kommandolinjeværktøj.
keywords: køre Windows Defender-scanning, køre antivirusscanning fra kommandolinjen, køre Windows Defender-scanning fra kommandolinjen, mpcmdrun, defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 97f818469f9da2616ca5ca2839ddf29ea227b85f
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789728"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Konfigurer og administrer Microsoft Defender Antivirus med kommandolinjeværktøjet mpcmdrun.exe

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus 

**Platforme**
- Windows

Du kan udføre forskellige funktioner i Microsoft Defender Antivirus ved hjælp af det dedikerede kommandolinjeværktøj **mpcmdrun.exe**. Dette værktøj er nyttigt, når du vil automatisere Microsoft Defender Antivirus opgaver. Du kan finde værktøjet i `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Kør den fra en kommandoprompt.

> [!TIP]
> Du skal muligvis åbne en version på administratorniveau af kommandoprompten. Når du søger efter **Kommandoprompt** på menuen Start, skal du vælge **Kør som administrator**. Hvis du kører en opdateret version af Microsoft Defender-platformen til antimalware, skal du køre `MpCmdRun` fra følgende placering: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Du kan få flere oplysninger om antimalwareplatformen [under Microsoft Defender Antivirus opdateringer og grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).

Værktøjet MpCmdRun bruger følgende syntaks:

```console
MpCmdRun.exe [command] [-options]
```

Her er et eksempel:

```console
MpCmdRun.exe -Scan -ScanType 2
```

I vores eksempel starter værktøjet MpCmdRun en komplet antivirusscanning på enheden.

## <a name="commands"></a>Kommandoer

|Kommando|Beskrivelse|
|---|---|
|`-?`**Eller** `-h`|Viser alle tilgængelige indstillinger for værktøjet MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Scanner efter skadelig software. Værdierne for **ScanType** er:<p>**0** Standard i henhold til din konfiguration<p>**1** Hurtig scanning<p>**2** Fuld scanning<p>**3** Brugerdefineret fil- og mappescanning.<p>CpuThrottling kører i henhold til politikkonfigurationer|
|`-Trace [-Grouping #] [-Level #]`|Starter diagnosticeringssporing|
|`-GetFiles [-SupportLogLocation <path>]`|Indsamler supportoplysninger. Se '[indsamling af diagnosticeringsdata](collect-diagnostic-data.md)'|
|`-GetFilesDiagTrack`|Samme som `-GetFiles`, men skriver til en midlertidig DiagTrack-mappe|
|`-RemoveDefinitions [-All]`|Gendanner den installerede Sikkerhedsintelligens til en tidligere sikkerhedskopi eller til det oprindelige standardsæt|
|`-RemoveDefinitions [-DynamicSignatures]`|Fjerner kun den dynamisk downloadede Sikkerhedsintelligens|
|`-RemoveDefinitions [-Engine]`|Gendanner det tidligere installerede program|
|`-SignatureUpdate [-UNC \|-MMPC]`|Kontrollerer, om der er nye sikkerhedsintelligensopdateringer|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Gendanner eller viser elementer i karantæne|
|`-AddDynamicSignature [-Path]`|Indlæser dynamisk sikkerhedsintelligens|
|`-ListAllDynamicSignatures`|Viser en liste over den indlæste dynamiske sikkerhedsintelligens|
|`-RemoveDynamicSignature [-SignatureSetID]`|Fjerner dynamisk sikkerhedsintelligens|
|`-CheckExclusion -path <path>`|Kontrollerer, om en sti er udeladt|
|`-ValidateMapsConnection`|Kontrollerer, at dit netværk kan kommunikere med Microsoft Defender Antivirus cloudtjeneste. Denne kommando fungerer kun på Windows 10 version 1703 eller nyere.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Almindelige fejl i kørsel af kommandoer via mpcmdrun.exe

I følgende tabel vises almindelige fejl, der kan opstå, når værktøjet MpCmdRun bruges.

|Fejlmeddelelse|Mulig årsag|
|---|---|
|**ValidateMapsConnection mislykkedes (800106BA)** eller **0x800106BA**|Tjenesten Microsoft Defender Antivirus er deaktiveret. Aktivér tjenesten, og prøv igen. Hvis du har brug for hjælp til at aktivere Microsoft Defender Antivirus igen, skal du se [Geninstaller/aktivér Microsoft Defender Antivirus på dine slutpunkter](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **TIP**! I Windows 10 1909 eller ældre og Windows Server 2019 eller ældre blev tjenesten tidligere kaldt *Windows Defender Antivirus*.|
|**0x80070667**|Du kører kommandoen `-ValidateMapsConnection` fra en computer, der er Windows 10 version 1607 eller ældre, eller Windows Server 2016 eller ældre. Kør kommandoen fra en computer, der er Windows 10 version 1703 eller nyere, eller Windows Server 2019 eller nyere.|
|**MpCmdRun genkendes ikke som en intern eller ekstern kommando, et driftsklart program eller en batchfil.**|Værktøjet skal køres fra en af `%ProgramFiles%\Windows Defender` eller `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` (hvor `2012.4-0` det kan variere, da platformopdateringer er månedlige undtagen marts)|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=80070005 httpcode=450)**|Kommandoen blev forsøgt ved hjælp af utilstrækkelige rettigheder. Brug kommandoprompten (cmd.exe) som administrator.|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=80070006 httpcode=451)**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=80004005 httpcode=450)**|Mulige netværksrelaterede problemer, f.eks. problemer med navneløsning|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=0x80508015**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=800722F0D**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette forbindelse til MAPS (hr=80072EE7 httpcode=451)**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Konfigurere Microsoft Defender Antivirus-funktioner](configure-microsoft-defender-antivirus-features.md)
- [Konfigurer og valider Microsoft Defender Antivirus netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md)
- [Referenceemner om administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
