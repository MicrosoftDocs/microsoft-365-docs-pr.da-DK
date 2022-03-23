---
title: Vis sårbarheder efter anbefaling
description: Henter en liste over sårbarheder, der er knyttet til sikkerhedsanbefalingen.
keywords: apis, graph api, understøttede api'er, hent, liste over sårbarheder, sikkerhedsanbefaling, sikkerhedsanbefaling til sårbarheder, Håndtering af trusler og sikkerhedsrisici, Håndtering af trusler og sikkerhedsrisici API
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
ms.openlocfilehash: 05e4719e69601024af25b2b797477506f195d328
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592627"
---
# <a name="list-vulnerabilities-by-recommendation"></a>Vis sårbarheder efter anbefaling

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Henter en liste over sårbarheder, der er knyttet til sikkerhedsanbefalingen.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Vulnerability.Read.All|"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/recommendations/{id}/vulnerabilities
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med listen over sårbarheder, der er knyttet til sikkerhedsanbefalingen.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations/va-_-google-_-chrome/vulnerabilities
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
        {
            "id": "CVE-2019-13748",
            "name": "CVE-2019-13748",
            "description": "Insufficient policy enforcement in developer tools in Google Chrome prior to 79.0.3945.79 allowed a local attacker to obtain potentially sensitive information from process memory via a crafted HTML page.",
            "severity": "Medium",
            "cvssV3": 6.5,
            "exposedMachines": 0,
            "publishedOn": "2019-12-10T00:00:00Z",
            "updatedOn": "2019-12-16T12:15:00Z",
            "publicExploit": false,
            "exploitVerified": false,
            "exploitInKit": false,
            "exploitTypes": [],
            "exploitUris": []
        }
        ...
     ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Anbefaling om sikkerhed & sikkerhed mod trusler](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
