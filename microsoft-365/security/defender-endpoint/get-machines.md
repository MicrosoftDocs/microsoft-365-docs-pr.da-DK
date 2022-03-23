---
title: Listemaskine-API
description: Få mere at vide om, hvordan du bruger listemaskine-API'en til at hente en samling af computere, der har kommunikeret med Microsoft Defender til slutpunktsskyen.
keywords: apis, graph api, understøttede API'er, hent, enheder
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection: M365-security-compliance
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6e522f2baac234097ed75d26eb1427719211a7de
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591281"
---
# <a name="list-machines-api"></a>Listemaskine-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling af computere [, der](machine.md) har kommunikeret med Microsoft Defender til slutpunktsskyen.

[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).

OData-forespørgslen understøttes `$filter` på: `computerDnsName`, `id`, `version`, `deviceValue`, `aadDeviceId`, `machineTags`, `lastSeen`,`exposureLevel` , `onboardingStatus`, , , `lastIpAddress`, `healthStatus`og `osPlatform``riskScore` `rbacGroupId`.
<br>```$stop``` med en maks. værdi på 10.000
<br>```$skip``` Se eksempler på [OData-forespørgsler med Defender til slutpunkt](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Begrænsninger

1. Du kan få vist enheder sidst i henhold til din konfigurerede opbevaringsperiode.
2. Den maksimale sidestørrelse er 10.000.
3. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time. 

## <a name="permissions"></a>Tilladelser

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.Read.All|"Læs alle maskinprofiler"
Program|Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.Read|"Læs maskinoplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.ReadWrite|"Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)
> - Svar omfatter kun enheder, som brugeren har adgang til, baseret på enhedsgrupperingsindstillinger (Se Opret og [administrer enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og maskiner findes – 200 OK med [liste over enheder](machine.md) på computeren i brødteksten. Hvis der ikke er nogen nyere computere – 404 Blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Machines",
    "value": [
        {
            "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
            "computerDnsName": "mymachine1.contoso.com",
            "firstSeen": "2018-08-02T14:55:03.7791856Z",
            "lastSeen": "2018-08-02T14:55:03.7791856Z",
            "osPlatform": "Windows10" "Windows11",
            "version": "1709",
            "osProcessor": "x64",
            "lastIpAddress": "172.17.230.209",
            "lastExternalIpAddress": "167.220.196.71",
            "osBuild": 18209,
            "healthStatus": "Active",
            "rbacGroupId": 140,
            "rbacGroupName": "The-A-Team",
            "riskScore": "Low",
            "exposureLevel": "Medium",
            "isAadJoined": true,
            "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
            "machineTags": [ "test tag 1", "test tag 2" ]
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md)
