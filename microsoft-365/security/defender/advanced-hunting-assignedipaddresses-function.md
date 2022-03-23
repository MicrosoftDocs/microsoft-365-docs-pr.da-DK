---
title: Funktionen AssignedIPAddresses() i avanceret jagt på Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger funktionen AssignedIPAddresses() til at få de seneste IP-adresser tildelt til en enhed
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, FileProfile, filprofil, funktion, berigende
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
ms.openlocfilehash: b82a079a476ee6ed3d5465b52bca381cd49746b5
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592857"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Brug funktionen `AssignedIPAddresses()` i dine avancerede [forespørgselsforespørgsler](advanced-hunting-overview.md) til hurtigt at hente de seneste IP-adresser, der er tildelt en enhed. Hvis du angiver et tidsstempelargument, henter denne funktion de seneste IP-adresser på det angivne tidspunkt. 

Denne funktion returnerer en tabel med følgende kolonner:

| Kolonne | Datatype | Beskrivelse |
|------------|-------------|-------------|
| `Timestamp` | `datetime` | Seneste tidspunkt, hvor enheden blev observeret ved hjælp af IP-adressen |
| `IPAddress` | `string` | IP-adresse, der bruges af enheden |
| `IPType` | `string` | Angiver, om IP-adressen er en offentlig eller privat adresse |
| `NetworkAdapterType` | `int` | Type af netværksadapter, der bruges af den enhed, der har fået tildelt IP-adressen. For de mulige værdier skal du se [denne optælling](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | Netværk, som adapteren med den tildelte IP-adresse er forbundet til. Hver JSON-matrix indeholder netværksnavn, kategori (offentligt, privat eller domæne), en beskrivelse og et flag, der angiver, om den har forbindelse offentligt til internettet |

## <a name="syntax"></a>Syntaks

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Argumenter

- **x** –`DeviceId` eller værdi `DeviceName` , der identificerer enheden
- **y**—`Timestamp` (datetime)-værdi, der instruerer funktionen om at hente de seneste tildelte IP-adresser fra et bestemt tidspunkt. Hvis det ikke er angivet, returnerer funktionen de seneste IP-adresser.

## <a name="examples"></a>Eksempler

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Få listen over IP-adresser, der bruges af en enhed for 24 timer siden

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Få IP-adresser brugt af en enhed, og find enheder, der kommunikerer med den
Denne forespørgsel bruger funktionen `AssignedIPAddresses()` til at få tildelte IP-adresser for enheden (`example-device-name`) på eller før en bestemt dato (`example-date`). Derefter bruges IP-adresserne til at finde forbindelser til den enhed, der er startet af andre enheder. 

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)