---
title: Navngivning af ændringer i Microsoft 365 Defender avancerede jagtskema
description: Spor og gennemse navngivningsændringer i tabeller og kolonner i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, data, navngive ændringer, omdøbe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 4e58bb3d8c8cc7c507c4136abcabeb7e42b6827d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731499"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Avanceret jagtskema – navngivningsændringer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Det [avancerede jagtskema](advanced-hunting-schema-tables.md) opdateres jævnligt for at tilføje nye tabeller og kolonner. I nogle tilfælde omdøbes eller erstattes eksisterende kolonnenavne for at forbedre brugeroplevelsen. Se denne artikel for at gennemse navneændringer, der kan påvirke dine forespørgsler.

Navngivningsændringer anvendes automatisk på forespørgsler, der er gemt i Defender for Cloud, herunder forespørgsler, der bruges af regler for brugerdefineret registrering. Du behøver ikke at opdatere disse forespørgsler manuelt. Du skal dog opdatere følgende forespørgsler:
- Forespørgsler, der køres ved hjælp af API'en
- Forespørgsler, der er gemt et andet sted uden for Defender for Cloud

## <a name="december-2020"></a>december 2020

| Tabelnavn | Oprindeligt kolonnenavn | Nyt kolonnenavn | Årsag til ændring
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Kundefeedback |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Kundefeedback |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Kundefeedback |

## <a name="january-2021"></a>Januar 2021

| Kolonnenavn | Navn på oprindelig værdi | Nyt værdinavn | Årsag til ændring
|--|--|--|--|
| `DetectionSource` | Defender for Cloud Apps | Microsoft Defender for Cloud Apps | Rebranding |
| `DetectionSource` | WindowsDefenderAtp| Slutpunktsregistrering og -svar| Rebranding |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Rebranding |
| `DetectionSource` | WindowsDefenderSmartScreen |  Smartscreen | Rebranding |
| `DetectionSource` | CustomerTI | Brugerdefineret TI | Rebranding |
| `DetectionSource` | OfficeATP | Microsoft Defender for Office 365 | Rebranding |
| `DetectionSource` | MTP | Microsoft 365 Defender | Rebranding |
| `DetectionSource` | AzureATP | Microsoft Defender for Identity | Rebranding |
| `DetectionSource` | Brugerdefineret registrering | Brugerdefineret registrering | Rebranding |
| `DetectionSource` | AutomatedInvestigation |Automatiseret undersøgelse | Rebranding |
| `DetectionSource` | ThreatExperts | Microsoft Threat Experts | Rebranding |
| `DetectionSource` | Tredjeparts-TI | Sensorer fra tredjepart | Rebranding |
| `ServiceSource` | Microsoft Defender ATP| Microsoft Defender for Endpoint | Rebranding |
|`ServiceSource` |Microsoft Threat Protection | Microsoft 365 Defender | Rebranding |
| `ServiceSource` | Office 365 ATP |Microsoft Defender for Office 365 | Rebranding |
| `ServiceSource` |Azure ATP |Microsoft Defender for Identity | Rebranding |

`DetectionSource` er tilgængelig i tabellen [AlertInfo](advanced-hunting-alertinfo-table.md) . `ServiceSource` er tilgængelig i tabellerne [AlertEvidence](advanced-hunting-alertevidence-table.md) og [AlertInfo](advanced-hunting-alertinfo-table.md) . 

## <a name="february-2021"></a>I februar 2021

1. I tabellerne [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) og [EmailEvents](advanced-hunting-emailevents-table.md) er kolonnerne `MalwareFilterVerdict`og `PhishFilterVerdict` blevet erstattet af kolonnen `ThreatTypes` . Kolonnerne `MalwareDetectionMethod` og `PhishDetectionMethod` blev også erstattet af kolonnen `DetectionMethods` . Denne strømlining giver os mulighed for at angive flere oplysninger under de nye kolonner. Tilknytningen er angivet nedenfor.

    | Tabelnavn | Oprindeligt kolonnenavn | Nyt kolonnenavn | Årsag til ændring
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Medtag flere registreringsmetoder |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Medtag flere trusselstyper |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Medtag flere registreringsmetoder |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Medtag flere trusselstyper |


2. I tabellerne `EmailAttachmentInfo` og `EmailEvents` blev kolonnen `ThreatNames` tilføjet for at give flere oplysninger om mailtruslen. Denne kolonne indeholder værdier som spam eller phish.

3. I tabellen [DeviceInfo](advanced-hunting-deviceinfo-table.md) blev kolonnen `DeviceObjectId` erstattet af kolonnen `AadDeviceId` baseret på kundefeedback.

4. I tabellen [DeviceEvents](advanced-hunting-deviceevents-table.md) blev flere ActionType-navne ændret, så de bedre afspejler beskrivelsen af handlingen. Du kan finde oplysninger om ændringerne nedenfor.

    | Tabelnavn | Oprindeligt navn på ActionType | Nyt navn på actiontype | Årsag til ændring
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | Kundefeedback |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | Kundefeedback |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | Kundefeedback |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | Kundefeedback |

## <a name="march-2021"></a>Marts 2021

Tabellen `DeviceTvmSoftwareInventoryVulnerabilities` frarådes. Erstatning af den er tabellerne `DeviceTvmSoftwareInventory` og `DeviceTvmSoftwareVulnerabilities` .

## <a name="may-2021"></a>Maj 2021

Tabellen `AppFileEvents` frarådes. Tabellen `CloudAppEvents` indeholder oplysninger, der tidligere var i tabellen `AppFileEvents` , sammen med andre aktiviteter i cloudtjenester.

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
