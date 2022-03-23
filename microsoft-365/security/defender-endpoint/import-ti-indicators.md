---
title: API'en Importér indikatorer
description: Få mere at vide om, hvordan du bruger Import-batchen af Indikator-API i Microsoft Defender til slutpunkt.
keywords: API'er, understøttede API'er, indsend, ti, indikator, opdatering
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
ms.custom: api
ms.openlocfilehash: 7306489e537e583055e037ce9d8ce04add248844
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592135"
---
# <a name="import-indicators-api"></a>API'en Importér indikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Sender eller opdaterer batchen [af indikatorenheder](ti-indicator.md) .

CIDR-notation for IP'er understøttes ikke.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 30 opkald pr. minut.
2. Der er en grænse på 15.000 aktive [indikatorer pr](ti-indicator.md) . lejer.
3. Den maksimale batchstørrelse for et API-opkald er 500.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Ti.ReadWrite|"Læs og skriv Indikatorer"
Program|Ti.ReadWrite.All|"Læs og skriv alle indikatorer"
Delegeret (arbejds- eller skolekonto)|Ti.ReadWrite|"Læs og skriv Indikatorer"

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|streng|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
:---|:---|:---
Indikatorer|Listeindikator<[liste](ti-indicator.md)>|Liste over [indikatorer](ti-indicator.md). **Påkrævet**

## <a name="response"></a>Svar

- Hvis det lykkes, returnerer denne metode 200 - OK-svarkode med en liste over importresultater pr. indikator, se eksemplet nedenfor.
- Hvis det ikke lykkes: Denne metode returnerer 400 – dårlig anmodning. Dårlig anmodning angiver normalt forkert brødtekst.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>Relateret emne

- [Administrer indikatorer](manage-indicators.md)
