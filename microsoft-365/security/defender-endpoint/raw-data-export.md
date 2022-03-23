---
title: Stream Microsoft Defender til slutpunktshændelse
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender til slutpunkt til at streame avancerede jagtbegivenheder til Event Hubs eller en Azure Storage-konto
keywords: rå dataeksport, streaming-API, API, hændelseshubs, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
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
ms.custom: api
ms.openlocfilehash: 94a815a6fc734c8e8e310a17f2e73931f4ffab5c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592049"
---
# <a name="raw-data-streaming-api"></a>Raw Data Streaming API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Stream avancerede rævebegivenheder til Event Hubs og/eller Azure Storage-konto

Microsoft Defender til Slutpunkt understøtter streaminghændelser, der er tilgængelige [via Avanceret jagt](../defender/advanced-hunting-overview.md) på en [Event Hubs](/azure/event-hubs/) og/eller [Azure-lagerkonto](/azure/storage/common/storage-account-overview).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4ga]

## <a name="in-this-section"></a>I dette afsnit

Emne|Beskrivelse
:---|:---
[Stream Microsoft Defender til slutpunktshændelser til Azure Event Hubs](raw-data-export-event-hub.md)|Få mere at vide om aktivering af streaming-API'en i din lejer, og konfigurer Defender til slutpunkt for at streame [Avanceret](advanced-hunting-overview.md) jagt til Hændelseshubs.
[Stream Defender til slutpunktshændelser til din Azure-lagerkonto](raw-data-export-storage.md)|Få mere at vide om aktivering af streaming-API'en i din lejer, og konfigurer Defender for Endpoint til at streame [Avanceret jagt](advanced-hunting-overview.md) til din Azure-lagerkonto.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Avanceret jagt](advanced-hunting-overview.md)
- [Azure Event Hubs-dokumentation](/azure/event-hubs/)
- [Azure Storage firmadokumentation](/azure/storage/common/storage-account-overview)