---
title: List machineActions API
description: Få mere at vide om, hvordan du bruger List MachineActions API til at hente en samling af computerhandlinger i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, machineaction-samling
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
ms.openlocfilehash: 0c7f5b1097e7fe59f9ccaa28800da27d943f1176
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597626"
---
# <a name="list-machineactions-api"></a>List MachineActions API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling af [computerhandlinger](machineaction.md).

[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).

OData-forespørgslen understøttes `$filter` på: `id`, `status`, `machineId`, `type`og `requestor``creationDateTimeUtc` egenskaber.

`$stop` med en maks. værdi på 10.000

`$skip`

Se eksempler på [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md)

## <a name="limitations"></a>Begrænsninger

1. Den maksimale sidestørrelse er 10.000.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.Read.All|"Læs alle maskinprofiler"
Program|Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.Read|"Læs maskinoplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.ReadWrite|"Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machineactions
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med en samling [af machineAction-enheder](machineaction.md) .

## <a name="example-1"></a>Eksempel 1

### <a name="example-1-request"></a>Eksempel 1 anmodning

Her er et eksempel på anmodningen om en organisation, der har tre MachineActions.

```http
GET https://api.securitycenter.microsoft.com/api/machineactions
```

### <a name="example-1-response"></a>Eksempel 1-svar

Her er et eksempel på svaret.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions",
    "value": [
        {
            "id": "69dc3630-1ccc-4342-acf3-35286eec741d",
            "type": "CollectInvestigationPackage",
            "scope": null,
            "requestor": "Analyst@contoso.com",
            "requestorComment": "test",
            "status": "Succeeded",
            "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
            "computerDnsName": "desktop-39g9tgl",
            "creationDateTimeUtc": "2018-12-04T12:43:57.2011911Z",
            "lastUpdateTimeUtc": "2018-12-04T12:45:25.4049122Z",
            "relatedFileInfo": null
        },
        {
            "id": "2e9da30d-27f6-4208-81f2-9cd3d67893ba",
            "type": "RunAntiVirusScan",
            "scope": "Full",
            "requestor": "Analyst@contoso.com",
            "requestorComment": "Check machine for viruses due to alert 3212",
            "status": "Succeeded",
            "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
            "computerDnsName": "desktop-39g9tgl",
            "creationDateTimeUtc": "2018-12-04T12:18:27.1293487Z",
            "lastUpdateTimeUtc": "2018-12-04T12:18:57.5511934Z",
            "relatedFileInfo": null
        },
        {
            "id": "44cffc15-0e3d-4cbf-96aa-bf76f9b27f5e",
            "type": "StopAndQuarantineFile",
            "scope": null,
            "requestor": "Analyst@contoso.com",
            "requestorComment": "test",
            "status": "Succeeded",
            "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
            "computerDnsName": "desktop-39g9tgl",
            "creationDateTimeUtc": "2018-12-04T12:15:40.6052029Z",
            "lastUpdateTimeUtc": "2018-12-04T12:16:14.2899973Z",
            "relatedFileInfo": {
                "fileIdentifier": "a0c659857ccbe457fdaf5fe21d54efdcbf6f6508",
                "fileIdentifierType": "Sha1"
            }
        }
    ]
}
```

## <a name="example-2"></a>Eksempel 2

### <a name="example-2-request"></a>Eksempel 2 på anmodning

Her er et eksempel på en anmodning, der filtrerer MachineActions efter maskin-id og viser de seneste to MachineActions.

```http
GET https://api.securitycenter.microsoft.com/api/machineactions?$filter=machineId eq 'f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f'&$top=2
```

### <a name="example-2-response"></a>Eksempel 2-svar

Her er et eksempel på svaret.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions",
    "value": [
        {
            "id": "69dc3630-1ccc-4342-acf3-35286eec741d",
            "type": "CollectInvestigationPackage",
            "scope": null,
            "requestor": "Analyst@contoso.com",
            "requestorComment": "test",
            "status": "Succeeded",
            "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
            "computerDnsName": "desktop-39g9tgl",
            "creationDateTimeUtc": "2018-12-04T12:43:57.2011911Z",
            "lastUpdateTimeUtc": "2018-12-04T12:45:25.4049122Z",
            "relatedFileInfo": null
        },
        {
            "id": "2e9da30d-27f6-4208-81f2-9cd3d67893ba",
            "type": "RunAntiVirusScan",
            "scope": "Full",
            "requestor": "Analyst@contoso.com",
            "requestorComment": "Check machine for viruses due to alert 3212",
            "status": "Succeeded",
            "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
            "computerDnsName": "desktop-39g9tgl",
            "creationDateTimeUtc": "2018-12-04T12:18:27.1293487Z",
            "lastUpdateTimeUtc": "2018-12-04T12:18:57.5511934Z",
            "relatedFileInfo": null
        }
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md)
