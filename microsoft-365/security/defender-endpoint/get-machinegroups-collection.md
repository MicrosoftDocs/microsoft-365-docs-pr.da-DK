---
title: Hent API til samling af RBAC-computergrupper
description: Få mere at vide om, hvordan du bruger API'en Hent KB-samling til at hente en samling af RBAC-enhedsgrupper i Microsoft Defender for Endpoint.
keywords: apis, graf-API, understøttede API'er, get, RBAC, gruppe
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
ms.openlocfilehash: 528b80b3c40fd7df853190788abb347ed90a82e4
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825162"
---
# <a name="get-kb-collection-api"></a>Hent API til KB-samling

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Henter en samling af RBAC-enhedsgrupper.

## <a name="permissions"></a>Tilladelser

Brugeren skal have læserettigheder.

## <a name="http-request"></a>HTTP-anmodning

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
```

## <a name="request-headers"></a>Anmodningsheadere

Header|Værdi
:---|:---
Tilladelse | Ihændehaver {token}. **Påkrævet**.
Indholdstype | program/json

## <a name="request-body"></a>Brødtekst i anmodning

Tom

## <a name="response"></a>Svar

Hvis det lykkes - 200 OK.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmodning

Her er et eksempel på anmodningen.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>Svareksempel

Her er et eksempel på svaret.
Felt-id'et indeholder **enhedsgruppe-id'et** og er lig med **felt-rbacGroupId** i enhedsoplysninger.
**Ikke-grupperede** felter er kun sande for én gruppe for alle enheder, der ikke er tildelt nogen gruppe. Denne gruppe har som sædvanlig navnet "UnassignedGroup".

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
