---
title: Stream Microsoft 365 Defender begivenheder
description: Få mere at vide om, hvordan Microsoft 365 Defender til at streame avancerede rævebegivenheder til Hændelseshubs eller Azure-lagerkonto
keywords: rå dataeksport, streaming-API, API, hændelseshubs, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
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
ms.openlocfilehash: c6c3cedffb1b827d441d37cc8beb53b20f3521f2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63597960"
---
# <a name="streaming-api"></a>Streaming-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Stream avancerede rævebegivenheder til Event Hubs og/eller Azure Storage-konto.

Microsoft 365 Defender understøtter streaminghændelser [via Avanceret jagt](../defender/advanced-hunting-overview.md) på [en Event Hubs](/azure/event-hubs/) og/eller [Azure Storage-konto](/azure/event-hubs/).

Du kan finde flere Microsoft 365 Defender om streaming-API i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
:---|:---
[Stream begivenheder til Azure Event Hubs](streaming-api-event-hub.md)| Få mere at vide om aktivering af streaming-API'en i din lejer, og konfigurer Microsoft 365 Defender at [streame Avanceret](../defender/advanced-hunting-overview.md) jagt til Event Hubs.
[Stream begivenheder til din Azure Storage-konto](streaming-api-storage.md)| Få mere at vide om aktivering af streaming-API'en i din lejer, og konfigurer Microsoft 365 Defender at [streame Avanceret jagt](advanced-hunting-overview.md) til din Azure-lagerkonto.
[Understøttede hændelsestyper](supported-event-types.md) | Få mere at vide om, hvilke advanced hunting-hændelsestyper streaming-API'en understøtter.


## <a name="related-topics"></a>Relaterede emner
- [Oversigt over Avanceret jagt](../defender/advanced-hunting-overview.md)
- [Azure Event Hubs-dokumentation](/azure/event-hubs/)
- [Azure Storage firmadokumentation](/azure/storage/common/storage-account-overview)
