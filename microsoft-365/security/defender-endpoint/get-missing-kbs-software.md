---
title: Hent manglende nøgle'er efter software-id
description: Henter manglende sikkerhedsopdateringer efter software-id
keywords: apis, graph api, understøttede API'er, hent, liste, fil, oplysninger, software-id, & håndtering af sikkerhedsrisici API, Microsoft Defender til Endpoint tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 692d0ca44a46ef11bd7ab3e9bb32a0c98dd7e01a
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591280"
---
# <a name="get-missing-kbs-by-software-id"></a>Hent manglende nøgle'er efter software-id

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Henter manglende NØGLE'er (sikkerhedsopdateringer) efter software-id

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Software.Read.All|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|Software.Read|"Læs oplysninger om software til trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/Software/{Id}/getmissingkbs
```

## <a name="request-header"></a>Anmod om sidehoved

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK, med den angivne software manglende kb-data i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/getmissingkbs
```

### <a name="response"></a>Svar

Her er et eksempel på svaret.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
         {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "edge"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 240,
            "cveAddressed": 14
         },
         ...
        ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Inventory over & af sikkerhedssikkerhedsrisiko](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
