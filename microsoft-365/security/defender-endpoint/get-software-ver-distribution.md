---
title: Liste over softwareversionsdistribution
description: Henter en liste over organisationens softwareversionsdistribution
keywords: apis, graph api, understøttede API'er, hent, softwareversionsdistribution, Microsoft Defender til Endpoint tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 5c2c743981f27cb59250815cefa2ed4a34fda93f
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592688"
---
# <a name="list-software-version-distribution"></a>Liste over softwareversionsdistribution

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Henter en liste over organisationens softwareversionsdistribution.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Software.Read.All|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|Software.Read|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/Software/{Id}/distributions
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Navn|Type|Beskrivelse
|---|---|---|
|Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med en liste over softwarefordelingsdata i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/distributions
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json

{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Distributions",
    "value": [
        {
            "version": "11.0.17134.1039",
            "installations": 1,
            "vulnerabilities": 11
        },
        {
            "version": "11.0.18363.535",
            "installations": 750,
            "vulnerabilities": 0
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventory over & af sikkerhedssikkerhedsrisiko](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
