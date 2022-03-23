---
title: Understøttede Microsoft 365 Defender API'er
description: Understøttede Microsoft 365 Defender API'er
keywords: Microsoft 365 Defender, API'er, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1785186f778c489cb4a254fe39cc41921a4de86e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63591744"
---
# <a name="supported-microsoft-365-defender-apis"></a>Understøttede Microsoft 365 Defender API'er 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

## <a name="list-of-available-apis"></a>Liste over tilgængelige API'er

Artikel | Beskrivelse
-|-
[Avanceret api til jagt](api-advanced-hunting.md) | Kør avancerede jagtforespørgsler.
[Hændelses-API'er](api-incident.md) | Opliste og opdatere hændelser samt andre praktiske opgaver.
[Streaming-API](streaming-api.md) | Send begivenheder og beskeder i realtid, som de sker i en enkelt datastrøm.

### <a name="endpoint-uris"></a>Slutpunkts-URI'er

Grund-URI'en for begge de primære API'er er: https://api.security.microsoft.com. Du kan opnå en bedre ydeevne ved at bruge en server, der er tættere på din geoplacering:

- USA: api-us.security.microsoft.com
- Europa: api-eu.security.microsoft.com
- Storbritannien: api-uk.security.microsoft.com

Tokens kan erhverves ved at få adgang til https://api.security.microsoft.com.

Alle API'er langs stien `/api` bruger [OData-protokollen](/odata/overview) , f.eks. https://api.security.microsoft.com/api/incidents.

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Streaming-API](../defender-endpoint/raw-data-export.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
