---
title: Tabellen DeviceNetworkInfo i det avancerede jagtskema
description: Få mere at vide om oplysninger om netværkskonfiguration i tabellen DeviceNetworkInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, machinenetworkinfo, DeviceNetworkInfo, enhed, computer, mac, ip, adapter, dns, dhcp, gateway, gateway
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
ms.openlocfilehash: 86c087c8a8cdfa80904612625c08ec37ca6813ca
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592039"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt



Tabellen `DeviceNetworkInfo` i det avancerede [skema](advanced-hunting-overview.md) indeholder oplysninger om netværkskonfiguration af maskiner, herunder netværksadapter, IP- og MAC-adresser og forbundne netværk eller domæner. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `NetworkAdapterName` | `string` | Navnet på netværksadapteren |
| `MacAddress` | `string` | Mac-adressen på netværksadapteren |
| `NetworkAdapterType` | `string` | Type af netværksadapter. For de mulige værdier skal du se [denne optælling](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | Netværkkortets driftsstatus. For de mulige værdier skal du se [denne optælling](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | Protocoling, if the interface is used for this purpose, for example 6to4, Teredo, ISATAP, PPTP, SSTP, and SSH |
| `ConnectedNetworks` | `string` | Netværk, som adapteren er forbundet til. Hver JSON-matrix indeholder netværksnavn, kategori (offentligt, privat eller domæne), en beskrivelse og et flag, der angiver, om den har forbindelse offentligt til internettet |
| `DnsAddresses` | `string` | DNS-serveradresser i JSON-matrixformat |
| `IPv4Dhcp` | `string` | IPv4-adressen på DHCP-serveren |
| `IPv6Dhcp` | `string` | IPv6-adressen på DHCP-serveren |
| `DefaultGateways` | `string` | Standardgatewayadresser i JSON-matrixformat |
| `IPAddresses` | `string` | JSON-matrix, der indeholder alle de IP-adresser, der er tildelt kortet, sammen med deres respektive undernetpræfiks og IP-adresseområde, f.eks. offentlige, private eller link-lokale |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. For at identificere entydige hændelser skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)