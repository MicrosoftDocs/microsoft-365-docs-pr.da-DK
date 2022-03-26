---
title: Brug kommandolinjen til at administrere Microsoft Defender Antivirus
description: Kør Microsoft Defender Antivirus scanninger, og konfigurer næste generations beskyttelse med et dedikeret kommandolinjeværktøj.
keywords: kør Windows Defender Scan, kør en antivirus-scanning fra kommandolinjen, kør Windows Defender Scan fra kommandolinjen, mpcmdrun, defender
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
ms.openlocfilehash: f7ae9c9d0986463b6d6368edd0dac050600e3373
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/30/2021
ms.locfileid: "63595880"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>Konfigurere og Microsoft Defender Antivirus med mpcmdrun.exe med kommandolinjeværktøjet

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan udføre forskellige funktioner i Microsoft Defender Antivirus ved hjælp af det dedikerede kommandolinjeværktøj **mpcmdrun.exe**. Dette værktøj er nyttigt, når du vil automatisere Microsoft Defender Antivirus opgaver. Du kan finde værktøjet i `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Kør den fra en kommandoprompt.

> [!TIP]
> Du skal muligvis åbne en version på administratorniveau af kommandoprompten. Når du søger efter **Kommandoprompt** på menuen Start, skal du **vælge Kør som administrator**. Hvis du kører en opdateret version af Microsoft Defender-antimalwareplatformen, skal du `MpCmdRun` køre fra følgende placering: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. Du kan finde flere oplysninger om antimalwareplatformen [i Microsoft Defender Antivirus opdateringer og oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

Værktøjet MpCmdRun bruger følgende syntaks:

```console
MpCmdRun.exe [command] [-options]
```

Her er et eksempel:

```console
MpCmdRun.exe -Scan -ScanType 2
```

I vores eksempel starter værktøjet MpCmdRun en fuld antivirusscanning på enheden.

## <a name="commands"></a>Kommandoer

|Kommando|Beskrivelse|
|---|---|
|`-?`**eller** `-h`|Viser alle tilgængelige indstillinger for værktøjet MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|Scanninger for skadelig software. Værdierne for **ScanType** er:<p>**0** Standard, afhængigt af din konfiguration<p>**1** Hurtig scanning<p>**2** Fuld scanning<p>**3 Brugerdefineret** scanning af filer og kataloger.<p>CpuThrottling kører i overensstemmelse med politikkonfigurationer|
|`-Trace [-Grouping #] [-Level #]`|Starter diagnostisk sporing|
|`-GetFiles [-SupportLogLocation <path>]`|Indsamler supportoplysninger. Se "[indsamling af diagnostiske data](collect-diagnostic-data.md)"|
|`-GetFilesDiagTrack`|Samme som `-GetFiles`, men output til midlertidig DiagTrack-mappe|
|`-RemoveDefinitions [-All]`|Gendanner den installerede sikkerhedsintelligens til en tidligere sikkerhedskopi eller til det oprindelige standardsæt|
|`-RemoveDefinitions [-DynamicSignatures]`|Fjerner kun den dynamisk downloadede sikkerhedsintelligens|
|`-RemoveDefinitions [-Engine]`|Gendanner det tidligere installerede program|
|`-SignatureUpdate [-UNC \|-MMPC]`|Kontrollerer, om der er nye sikkerhedsintelligensopdateringer|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|Gendanner eller viser elementer, der er sat i karantæne|
|`-AddDynamicSignature [-Path]`|Indlæser dynamisk sikkerhedsintelligens|
|`-ListAllDynamicSignatures`|Viser den indlæste dynamiske sikkerhedsintelligens|
|`-RemoveDynamicSignature [-SignatureSetID]`|Fjerner dynamisk sikkerhedsintelligens|
|`-CheckExclusion -path <path>`|Kontrollerer, om en sti udelades|
|`-ValidateMapsConnection`|Kontrollerer, at dit netværk kan kommunikere med Microsoft Defender Antivirus skytjenesten. Denne kommando virker kun på Windows 10 version 1703 eller nyere.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>Almindelige fejl ved kørsel af kommandoer via mpcmdrun.exe

I følgende tabel vises almindelige fejl, der kan opstå, når du bruger værktøjet MpCmdRun.

|Fejlmeddelelse|Mulig årsag|
|---|---|
|**ValidateMapsConnection mislykkedes (800106BA)** **eller 0x800106BA**|Tjenesten Microsoft Defender Antivirus deaktiveret. Aktivér tjenesten, og prøv igen. Hvis du har brug for hjælp til at Microsoft Defender Antivirus, skal du se [geninstaller/Microsoft Defender Antivirus på dine slutpunkter](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **Tip**: I Windows 10 1909 eller ældre og Windows Server 2019 eller ældre blev tjenesten tidligere *kaldt Windows Defender Antivirus*.|
|**0x80070667**|Du kører kommandoen `-ValidateMapsConnection` fra en computer, der er Windows 10 version 1607 eller ældre, eller Windows Server 2016 eller ældre. Kør kommandoen fra en computer, der Windows 10 version 1703 eller nyere, eller Windows Server 2019 eller nyere.|
|**MpCmdRun genkendes ikke som en intern eller ekstern kommando, et operandeprogram eller en batchfil.**|Værktøjet skal køres fra enten eller `%ProgramFiles%\Windows Defender` (hvor kan `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` variere, da `2012.4-0` platformopdateringer er månedlige med undtagelse af marts)|
|**ValidateMapsConnection kunne ikke oprette forbindelse til KORT (hr=80070005 httpcode=450)**|Kommandoen blev forsøgt benyttet med utilstrækkelige rettigheder. Brug kommandoprompten (cmd.exe) som administrator.|
|**ValidateMapsConnection kunne ikke oprette en forbindelse til KORT (hr=80070006 httpcode=451)**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette en forbindelse til KORT (hr=80004005 httpcode=450)**|Mulige netværksrelaterede problemer, f.eks. problemer med navneløsning|
|**ValidateMapsConnection kunne ikke oprette en forbindelse til MAPS (hr=0x80508015**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette en forbindelse til MAPS (hr=800722F0D**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|
|**ValidateMapsConnection kunne ikke oprette en forbindelse til MAPS (hr=80072EE7 httpcode=451)**|Firewallen blokerer forbindelsen eller udfører SSL-inspektion.|

## <a name="see-also"></a>Se også

- [Konfigurere Microsoft Defender Antivirus funktioner](configure-microsoft-defender-antivirus-features.md)
- [Konfigurere og validere Microsoft Defender Antivirus netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md)
- [Referenceemner til administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
