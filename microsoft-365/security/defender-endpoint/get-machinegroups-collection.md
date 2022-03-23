---
title: Hent RBAC machine groups collection API
description: Få mere at vide om, hvordan du bruger Hent KB-samlings-API'en til at hente en samling af RBAC-enhedsgrupper i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, RBAC, gruppe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
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
ms.date: 10/07/2018
ms.custom: api
ms.openlocfilehash: 699a7e2738f1e0c89977bd152832f45935a06387
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591282"
---
# <a name="get-kb-collection-api"></a>Hent KB-samlings-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Henter en samling af RBAC-enhedsgrupper.

## <a name="permissions"></a>Tilladelser

Brugeren skal have læsetilladelser.

## <a name="http-request"></a>HTTP-anmodning

```http
GET /testwdatppreview/machinegroups
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved|Værdi
:---|:---
Godkendelse | Bearer {token}. **Påkrævet**.
Indholdstype | application/json

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes – 200 OK.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.
Felt-id indeholder **enhedsgruppe-id** og lig med felt **rbacGroupId** i enhedsoplysninger.
**Ugrupperede felter gælder** kun for én gruppe for alle enheder, der ikke er blevet tildelt en gruppe. Denne gruppe har som normalt navnet "Ikke-tildelt gruppe".

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineGroups",
    "@odata.count":7,
    "value":[
        {
            "id":86,
            "name":"UnassignedGroup",
            "description":"",
            "ungrouped":true},
        ...
}
```
