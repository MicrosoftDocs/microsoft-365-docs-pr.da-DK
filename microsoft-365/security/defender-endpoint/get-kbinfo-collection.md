---
title: Hent KB-samlings-API
description: Hent en samling af vidensbaser (KB'er) og KB-oplysninger med Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede api'er, hent, kb
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ROBOTS: NOINDEX
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 31edd825a20e1f466b2ace4ea3030a10dcdeb3cd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591839"
---
# <a name="get-kb-collection-api"></a>Hent KB-samlings-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Henter en samling af KB'er og KB-oplysninger.

## <a name="permissions"></a>Tilladelser

Brugeren skal have læsetilladelser.

## <a name="http-request"></a>HTTP-anmodning

```http
GET /testwdatppreview/kbinfo
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved|Værdi 
:---|:---
Godkendelse|Bearer {token}. **Påkrævet**.
Indholdstype|application/json

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes – 200 OK.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://graph.microsoft.com/testwdatppreview/KbInfo
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://graph.microsoft.com/testwdatppreview/$metadata#KbInfo",
    "@odata.count": 271,
    "value":[
        {
            "id": "KB3097617 (10240.16549) Amd64",
            "release": "KB3097617 (10240.16549)",
            "publishingDate": "2015-10-16T21:00:00Z",
            "version": "10.0.10240.16549",
            "architecture": "Amd64"
        },
        ...
}
```
