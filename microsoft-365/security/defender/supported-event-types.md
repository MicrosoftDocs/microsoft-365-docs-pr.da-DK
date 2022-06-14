---
title: Microsoft 365 Defender streaminghændelsestyper, der understøttes i API'en til hændelsesstreaming
description: Få mere at vide om, hvilke streaminghændelsestyper (tabeller) der understøttes af streaming-API'en
keywords: rå dataeksport, Streaming-API, API, Hændelseshubber, Azure Storage, lagerkonto, Jagt, rådatadeling
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
ms.openlocfilehash: 4f6f098c9d2ec09a777110955b8acb1663e102ed
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057845"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Understøttede Microsoft 365 Defender streaminghændelsestyper i API'en til hændelsesstreaming

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


Api'en til hændelsesstreaming udvides konstant for at understøtte flere hændelsestyper. Få mere at vide om, hvilke Jagt-tabeller der er offentligt tilgængelige, i øjeblikket i offentlig prøveversion eller endnu ikke understøttes. 
**Ny – Mailhændelsestyper/-tabeller er nu offentligt tilgængelige**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Jagttabeller understøtter status i API til hændelsesstreaming

Følgende tabel indeholder kun listen over de tabeller, der understøttes i streaming-API'en, og den omfatter ikke alt AH-skema. Du kan finde en komplet liste over API'en [under Få mere at vide om skematabellerne](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Tabelnavn | Status<br>(Kommerciel) | GCC | GCC Høj | Dod |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | GA | GA | GA | GA |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |GA | GA | GA | GA |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |GA | GA | GA | GA |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | GA | GA | GA | GA |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | GA | GA | GA | GA |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | GA | GA | GA | GA |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |GA | GA | GA | GA |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | GA | GA | GA | GA |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | GA | GA | GA | GA |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | GA | GA | GA | GA |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | GA |![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | GA |![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | GA |![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | GA |![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|GA|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|GA|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|GA|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|GA|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|![Nej](../defender-endpoint/images/svg/check-no.svg)|
