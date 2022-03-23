---
title: Microsoft 365 Defender typer af streaminghændelser, der understøttes i Event Streaming API
description: Få mere at vide om, hvilke typer streaminghændelser (tabeller) der understøttes af streaming-API'en
keywords: rå dataeksport, Streaming API, API, Hændelseshubs, Azure-lager, lagerkonto, jagt, rå datadeling
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e8264ccb9e3181f6b58a6206417eb2b842bec6e7
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/15/2021
ms.locfileid: "63592967"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Understøttet Microsoft 365 Defender hændelsestyper for streaming af begivenheder i API'en hændelsesstreaming

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Event Streaming API udvides konstant for at understøtte flere begivenhedstyper. Få mere at vide om, hvilke rævetabeller der er generelt tilgængelige, aktuelt i offentlig prøveversion eller endnu ikke understøttet. 
**Ny – Mailbegivenhedstyper/-tabeller er nu GA**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Understøttelsesstatus for videtabeller i Event Streaming API

Den følgende tabel indeholder kun listen over de tabeller, der understøttes i streaming-API'en, og omfatter ikke hele AH-skemaet. Du kan finde en komplet liste over API'en i [Få mere at vide om skematabellerne](advanced-hunting-schema-tables.md#learn-the-schema-tables).


| Tabelnavn | Status |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA  |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |


