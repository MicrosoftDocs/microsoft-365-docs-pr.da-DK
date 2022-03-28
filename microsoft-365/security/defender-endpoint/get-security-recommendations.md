---
title: Få sikkerhedsanbefalinger
description: Henter en samling af sikkerhedsanbefalinger, der er relateret til et bestemt enheds-id.
keywords: apis, graph api, understøttede API'er, hent, liste, fil, oplysninger, sikkerhedsanbefaling pr. enhed, trussel & håndtering af sikkerhedsrisici API, Microsoft Defender til Endpoint tvm api
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
ms.openlocfilehash: 6441610fb9c1ebdee823badce2bd2c5439142cf3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597559"
---
# <a name="get-security-recommendations"></a>Få sikkerhedsanbefalinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Henter en samling af sikkerhedsanbefalinger, der er relateret til et bestemt enheds-id.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|SecurityRecommendation.Read.All|"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|SecurityRecommendation.Read|"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{machineId}/recommendations
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med sikkerhedsanbefalinger i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
...
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Anbefaling om sikkerhed & sikkerhed mod trusler](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
