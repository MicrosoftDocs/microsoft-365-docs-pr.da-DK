---
title: Vis enheder efter software
description: Hent en liste over enheder, der har denne software installeret.
keywords: apis, graph api, understøttede API'er, hent, liste over enheder, liste over enheder, liste over enheder efter software, Microsoft Defender til Endpoint tvm api
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
ms.openlocfilehash: 32dd0531d0919613621d656f7f3b9aef3e4bec0d
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592947"
---
# <a name="list-devices-by-software"></a>Vis enheder efter software

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Hent en liste over enhedsreferencer, der har denne software installeret.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Software.Read.All|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|Software.Read|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/Software/{Id}/machineReferences 
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Navn|Type|Beskrivelse
|---|---|---|
|Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og en liste over enheder med den software, der er installeret i brødteksten. 

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/machineReferences
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json

{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "7c7e1896fa39efb0a32a2cf421d837af1b9bf762",
            "computerDnsName": "dave_desktop",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        },
        {
            "id": "7d5cc2e7c305e4a0a290392abf6707f9888fda0d",
            "computerDnsName": "jane_PC",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventory over & af sikkerhedssikkerhedsrisiko](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
