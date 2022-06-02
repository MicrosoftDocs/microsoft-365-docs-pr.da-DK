---
title: Få fundne sikkerhedsrisici
description: Henter en samling af registrerede sikkerhedsrisici, der er relateret til et givent enheds-id.
keywords: apis, graf api, understøttede API'er, hent, liste, fil, oplysninger, registrerede sårbarheder, trussel & håndtering af sikkerhedsrisici API, Microsoft Defender for Endpoint tvm-api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6b3271637b1b275fe26d07975d0592bf1e7ae672
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840469"
---
# <a name="get-discovered-vulnerabilities"></a>Få fundne sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse
Henter en samling af registrerede sikkerhedsrisici, der er relateret til et givent enheds-id.

## <a name="limitations"></a>Begrænsninger
1. Hastighedsbegrænsninger for denne API er 50 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype | Tilladelse | Vist navn for tilladelse
:---|:---|:---
Program |Vulnerability.Read.All | 'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring'
Uddelegeret (arbejds- eller skolekonto) | Vulnerability.Read | 'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring'

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{machineId}/vulnerabilities
```

## <a name="request-headers"></a>Anmodningsheadere

Navn|Type|Beskrivelse
:---|:---|:---
Tilladelse | String | Ihændehaver {token}. **Påkrævet**.

## <a name="request-body"></a>Brødtekst i anmodning

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med de fundne oplysninger om sårbarheder i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/vulnerabilities
```

### <a name="response"></a>Svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
        {
            "id": "CVE-2019-1348",
            "name": "CVE-2019-1348",
            "description": "Git could allow a remote attacker to bypass security restrictions, caused by a flaw in the --export-marks option of git fast-import. By persuading a victim to import specially-crafted content, an attacker could exploit this vulnerability to overwrite arbitrary paths.",
            "severity": "Medium",
            "cvssV3": 4.3,
            "exposedMachines": 1,
            "publishedOn": "2019-12-13T00:00:00Z",
            "updatedOn": "2019-12-13T00:00:00Z",
            "publicExploit": false,
            "exploitVerified": false,
            "exploitInKit": false,
            "exploitTypes": [],
            "exploitUris": []
        }
    ]
}
```

## <a name="see-also"></a>Se også

- [Risikobaseret administration af trussel & sårbarhed](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Sikkerhedsrisici i din organisation](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
