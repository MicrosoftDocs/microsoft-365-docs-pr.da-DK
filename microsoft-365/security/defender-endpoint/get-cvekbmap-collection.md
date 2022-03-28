---
title: Få CVE-KB-kort-API
description: Få mere at vide om, hvordan du bruger Api'en Hent CVE-KB-kort til at hente et kort over CV'er til KB'er og CVE-oplysninger i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede api'er, hent, cve, kb
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
ms.openlocfilehash: d0672804d0d2a8221480fe76e4237114a88f4cfb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597560"
---
# <a name="get-cve-kb-map-api"></a>Få CVE-KB-kort-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Henter et kort over CV'er til CV'er og CVE-oplysninger.

## <a name="permissions"></a>Tilladelser

Brugeren skal have læsetilladelser.

## <a name="http-request"></a>HTTP-anmodning

```http
GET /testwdatppreview/cvekbmap
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved|Værdi
:---|:---
Godkendelse|Bearer {token}. **Påkrævet**.
Indholdstype|application/json

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og kortet findes – 200 OK.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen:

```http
GET https://graph.microsoft.com/testwdatppreview/CveKbMap
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret:

```json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#CveKbMap",
    "@odata.count": 4168,
    "value": [
        {
            "cveKbId": "CVE-2015-2482-3097617",
            "cveId": "CVE-2015-2482",
            "kbId":"3097617",
            "title": "Cumulative Security Update for Internet Explorer",
            "severity": "Critical"
        },
    ...
}
```
