---
title: Vis alle anbefalinger
description: Henter en liste over alle sikkerhedsanbefalinger, der påvirker organisationen.
keywords: apis, graph api, understøttede API'er, hent, sikkerhedsanbefalinger, Microsoft Defender til Endpoint tvm api, Håndtering af trusler og sikkerhedsrisici, Håndtering af trusler og sikkerhedsrisici api
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
ms.openlocfilehash: 727b20e6784016aac423a74c6b564fa96d6f5733
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63603090"
---
# <a name="list-all-recommendations"></a>Vis alle anbefalinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Henter en liste over alle sikkerhedsanbefalinger, der påvirker organisationen.


## <a name="api-description"></a>API-beskrivelse

Returnerer oplysninger om alle sikkerhedsanbefalinger, der påvirker organisationen.

*URL-adresse:* HENT:/api/anbefalinger
<br>[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).
<br>OData-understøttede operatorer:
<br>```$filter```på: ```id```, ```productName```, ```vendor```, ```recommendedVersion```, ```recommendationCategory``````subCategory```, ```severityScore```, ```remediationType```, ```recommendedProgram```, ```recommendedVendor```og ```status``` egenskaber.
<br>```$top``` med en maks. værdi på 10.000.
<br>```$skip```.
<br>Se eksempler på [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md).

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|SecurityRecommendation.Read.All|"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|SecurityRecommendation.Read |"Læs oplysninger om sikkerhed i forbindelse med trussels- og sikkerhedsrisiko"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/recommendations
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med listen over sikkerhedsanbefalinger i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations
```

### <a name="response"></a>Svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11",
            "productName": "windows_10" "Windows_11",
            "recommendationName": "Update Windows 10" "Update Windows 11",
            "weaknesses": 397,
            "vendor": "microsoft",
            "recommendedVersion": "",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": true,
            "activeAlert": false,
            "associatedThreats": [
                "3098b8ef-23b1-46b3-aed4-499e1928f9ed",
                "40c189d5-0330-4654-a816-e48c2b7f9c4b",
                "4b0c9702-9b6c-4ca2-9d02-1556869f56f8",
                "e8fc2121-3cf3-4dd2-9ea0-87d7e1d2b29d",
                "94b6e94b-0c1d-4817-ac06-c3b8639be3ab"
            ],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 7.674418604651163,
            "totalMachineCount": 37,
            "exposedMachinesCount": 7,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Windows 10" "Windows 11"
        }
        ...
     ]
}
```

## <a name="see-also"></a>Se også

- [Risikobaseret administration af & af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Anbefaling om sikkerhed & sikkerhed mod trusler](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
