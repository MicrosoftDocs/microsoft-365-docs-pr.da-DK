---
title: API'en Listeindikatorer
description: Få mere at vide om, hvordan du bruger listeindikatorer-API'en til at hente en samling af alle aktive indikatorer i Microsoft Defender til slutpunkt.
keywords: API'er, offentlig api, understøttede API'er, samlingen Indikatorer
ms.prod: w10
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: adc3cfecba10431a909b72f875442d80b6638f03
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592687"
---
# <a name="list-indicators-api"></a>API'en Listeindikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling af alle aktive [indikatorer](ti-indicator.md).

[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).

OData-forespørgslen understøttes på: `application`, , `expirationTime``createdByDisplayName`, `generateAlert`, `title`, `rbacGroupNames`, `rbacGroupIds`, `indicatorValue`, , `indicatorType`, `creationTimeDateTimeUtc`, `createdBy`, , `action`og `severity` `$filter` egenskaber.
<br>```$stop``` med en maks. værdi på 10.000. 
<br>```$skip```.

Se eksempler på [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time. 

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Ti.ReadWrite|"Læs og skriv Indikatorer"
Program|Ti.ReadWrite.All|"Læs og skriv alle indikatorer"
Delegeret (arbejds- eller skolekonto)|Ti.ReadWrite|"Læs og skriv Indikatorer"

## <a name="http-request"></a>HTTP-anmodning

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med en samling [af](ti-indicator.md) indikatorenheder.

> [!NOTE]
> Hvis programmet har tilladelsen "Ti.ReadWrite.All", vises den for alle indikatorer. Ellers vises den kun for de symboler, den har oprettet.

## <a name="example-1"></a>Eksempel 1

### <a name="example-1-request"></a>Eksempel 1 anmodning

Her er et eksempel på en anmodning, der henter alle indikatorer

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

### <a name="example-1-response"></a>Eksempel 1-svar

Her er et eksempel på svaret.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "995",
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "action": "Alert",
            "application": "demo-test",
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
            "rbacGroupNames": []
        },
        {
            "id": "996",
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```

## <a name="example-2"></a>Eksempel 2

### <a name="example-2-request"></a>Eksempel 2 på anmodning

Her er et eksempel på en anmodning, der henter alle indikatorer med handlingen "AlertAndBlock" 

```http
GET https://api.securitycenter.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### <a name="example-2-response"></a>Eksempel 2-svar

Her er et eksempel på svaret.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "997",
            "indicatorValue": "111e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```
