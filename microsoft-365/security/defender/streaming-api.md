---
title: Stream Microsoft 365 Defender hændelser
description: Få mere at vide om, hvordan du konfigurerer Microsoft 365 Defender til at streame avancerede jagthændelser til Event Hubs eller Azure Storage-konto
keywords: rå dataeksport, streaming-API, API, Hændelseshubber, Azure Storage, lagerkonto, Avanceret jagt, rådatadeling
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
ms.openlocfilehash: d9f980656df636632c5903853c2784de81131d81
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621423"
---
# <a name="streaming-api"></a>Streaming-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Stream Advanced Hunting-hændelser til Event Hubs og/eller Azure Storage-konto.

Microsoft 365 Defender understøtter streaminghændelser via [Avanceret jagt](../defender/advanced-hunting-overview.md) til en [Event Hubs](/azure/event-hubs/)- og/eller [Azure Storage-konto](/azure/event-hubs/).

Du kan få flere oplysninger om Microsoft 365 Defender streaming-API i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
:---|:---
[Stream-hændelser til Azure Event Hubs](streaming-api-event-hub.md)| Få mere at vide om, hvordan du aktiverer streaming-API'en i din lejer og konfigurerer Microsoft 365 Defender til at streame [Avanceret jagt](../defender/advanced-hunting-overview.md) til Event Hubs.
[Stream-hændelser til din Azure Storage-konto](streaming-api-storage.md)| Få mere at vide om, hvordan du aktiverer streaming-API'en i din lejer og konfigurerer Microsoft 365 Defender til at streame [Avanceret jagt](advanced-hunting-overview.md) til din Azure Storage-konto.
[Understøttede hændelsestyper](supported-event-types.md) | Få mere at vide om, hvilke advanced hunting-hændelsestyper streaming-API'en understøtter.

Se denne korte video for at få mere at vide om, hvordan du konfigurerer streaming-API'en til at sende hændelsesoplysninger direkte til Azure Event-hubs til forbrug af visualiseringstjenester, databehandlingsprogrammer eller Azure Storage til langsigtet dataopbevaring.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga]

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](../defender/advanced-hunting-overview.md)
- [Dokumentation til Azure Event Hubs](/azure/event-hubs/)
- [dokumentation til Azure Storage-konto](/azure/storage/common/storage-account-overview)
