---
title: DeviceFromIP() i avanceret jagt på Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger funktionen DeviceFromIP() til at hente de enheder, der har fået tildelt en bestemt IP-adresse
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, enhed, devicefromIP, funktion, berigende
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
ms.openlocfilehash: 4a1f1198c247aefbcbb093d1a5f5105704255692
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592041"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Brug funktionen `DeviceFromIP()` i dine avancerede [](advanced-hunting-overview.md) forespørgselsforespørgsler til hurtigt at få listen over enheder, der har fået tildelt en bestemt IP-adresse på et givet tidspunkt. 

Denne funktion returnerer en tabel med følgende kolonner:

| Kolonne | Datatype | Beskrivelse |
|------------|-------------|-------------|
| `IP` | `string` | IP-adresse  |
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |


## <a name="syntax"></a>Syntaks

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Argumenter

Denne funktion aktiveres som en del af en forespørgsel.

- **x** – Den første parameter er typisk allerede en kolonne i forespørgslen. I dette tilfælde er det kolonnen `IP`med navnet , den IP-adresse, du vil have vist en liste over enheder, der er tildelt til den. Det skal være en lokal IP-adresse. Eksterne IP-adresser understøttes ikke.
- **y** – En anden valgfri parameter er `Timestamp`, der instruerer funktionen i at hente de seneste tildelte enheder fra et bestemt tidspunkt. Hvis det ikke er angivet, returnerer funktionen de senest tilgængelige poster.

## <a name="example"></a>Eksempel


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Hent de nyeste enheder, der har fået tildelt bestemte IP-adresser

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
