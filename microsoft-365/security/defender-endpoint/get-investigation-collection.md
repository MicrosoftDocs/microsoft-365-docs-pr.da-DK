---
title: API'en Listeundersøgelse
description: Brug denne API til at oprette opkald, der er relateret til indsamling af undersøgelser
keywords: API'er, graph api, understøttede API'er, undersøgelsessamling
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f5a37d8cbbaeca3dd14c51e1d5c6adcefabf2db8
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592072"
---
# <a name="list-investigations-api"></a>API'en Listeundersøgelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling [af undersøgelser](investigation.md).

[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).

OData-forespørgslen understøttes `$filter` på: `startTime`, `id`, `state`og `machineId` `triggeringAlertId` egenskaber.
<br>```$stop``` med en maks. værdi på 10.000
<br>```$skip```

Se eksempler på [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Begrænsninger

1. Den maksimale sidestørrelse er 10.000.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alert.Read.All|"Læs alle beskeder"
Program|Alert.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto)|Alert.Read|"Læsebeskeder"
Delegeret (arbejds- eller skolekonto)|Alert.ReadWrite|"Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET https://api.securitycenter.microsoft.com/api/investigations
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med en samling [af undersøgelsesenheder](investigation.md) .

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på en anmodning om at få alle undersøgelser:

```http
GET https://api.securitycenter.microsoft.com/api/investigations
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret:

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Investigations",
    "value": [
        {
            "id": "63017",
            "startTime": "2020-01-06T14:11:34Z",
            "endTime": null,
            "state": "Running",
            "cancelledBy": null,
            "statusDetails": null,
            "machineId": "a69a22debe5f274d8765ea3c368d00762e057b30",
            "computerDnsName": "desktop-gtrcon0",
            "triggeringAlertId": "da637139166940871892_-598649278"
        }
        ...
    ]
}
```
