---
title: Undersøg forbindelseshændelser, der opstår bag fremadrettet proxyer
description: Få mere at vide om, hvordan du bruger avanceret HTTP-niveauovervågning via netværksbeskyttelse i Microsoft Defender til slutpunkt, som viser et rigtigt mål i stedet for en proxy.
keywords: proxy, netværksbeskyttelse, videressendelse af proxy, netværkshændelser, overvågning, blok, domænenavne, domæne
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c0a2bdab641f0289975f1d8475627d3066ecf1f8
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593540"
---
# <a name="investigate-connection-events-that-occur-behind-forward-proxies"></a>Undersøg forbindelseshændelser, der opstår bag fremadrettet proxyer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Defender til Slutpunkt understøtter overvågning af netværksforbindelser fra forskellige niveauer i netværksstakken. En udfordrende sag er, når netværket bruger en videresendelsesproxy som en gateway til internettet.

Proxyen fungerer, som om det var destinationsslutpunktet. I disse tilfælde vil skærme med enkle netværksforbindelser overvåge forbindelserne med den proxy, der er korrekt, men har en lavere undersøgelsesværdi.

Defender til Slutpunkt understøtter avanceret overvågning på HTTP-niveau via netværksbeskyttelse. Når den er slået til, vises en ny type begivenhed, som fremviser de rigtige domænenavne for destinationen.

## <a name="use-network-protection-to-monitor-network-connection-behind-a-firewall"></a>Brug netværksbeskyttelse til at overvåge netværksforbindelsen bag en firewall

Overvågning af netværksforbindelsen bag en videresendelsesproxy er mulig på grund af andre netværkshændelser, der stammer fra netværksbeskyttelse. Hvis du vil se dem på en tidslinje på en enhed, skal du aktivere netværksbeskyttelse (som minimum i overvågningstilstand).

Netværksbeskyttelse kan styres ved hjælp af følgende tilstande:

- **Bloker**: Brugere eller apps vil blive blokeret fra at oprette forbindelse til skadelige domæner. Du vil kunne se denne aktivitet i Microsoft 365 Defender.
- **Overvågning**: Brugere eller apps vil ikke blive blokeret fra at oprette forbindelse til skadelige domæner. Du kan dog stadig se denne aktivitet i Microsoft 365 Defender.


Hvis du deaktiverer netværksbeskyttelse, vil brugere eller apps ikke blive blokeret fra at oprette forbindelse til skadelige domæner. Du får ikke vist nogen netværksaktivitet i Microsoft 365 Defender.

Hvis du ikke konfigurerer det, vil blokering af netværk som standard være slået fra.

Du kan få mere at vide [under Aktivér netværksbeskyttelse](enable-network-protection.md).

## <a name="investigation-impact"></a>Undersøgelsespåvirkning

Når netværksbeskyttelse er slået til, kan du se, at IP-adressen på en enheds tidslinje fortsat repræsenterer proxyen, mens den rigtige måladresse vises.

![Billede af netværkshændelser på enhedens tidslinje.](images/atp-proxy-investigation.png)

Andre hændelser, der udløses af netværksbeskyttelseslaget, er nu tilgængelige til at få vist de rigtige domænenavne selv bag en proxy.

Oplysninger om begivenhed:

![Billede af enkelt netværkshændelse.](images/atp-proxy-investigation-event.png)

## <a name="hunt-for-connection-events-using-advanced-hunting"></a>Lede efter forbindelsesbegivenheder ved hjælp af avanceret jagt

Alle nye forbindelsesbegivenheder er også tilgængelige, så du kan være på jagt efter avanceret jagt. Da disse hændelser er forbindelseshændelser, kan du finde dem under tabellen DeviceNetworkEvents under handlingstypen `ConnecionSuccess` .

Ved hjælp af denne enkle forespørgsel får du vist alle de relevante begivenheder:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| take 10
```

![Billede af avanceret forespørgsel.](images/atp-proxy-investigation-ah.png)

Du kan også filtrere de hændelser, der er relateret til forbindelsen til selve proxyen.

Brug følgende forespørgsel til at filtrere forbindelserne til proxyen fra:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"
| take 10
```

## <a name="related-topics"></a>Relaterede emner

- [Anvendelse af netværksbeskyttelse med GP – politik-CSP](/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
