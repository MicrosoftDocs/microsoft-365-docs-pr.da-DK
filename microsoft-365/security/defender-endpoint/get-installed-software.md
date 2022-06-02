---
title: Hent installeret software
description: Henter en samling af installeret software, der er relateret til et givent enheds-id.
keywords: apis, graf api, understøttede API'er, hent, liste, fil, oplysninger, softwareoversigt, installeret software pr. enhed, trussel & håndtering af sikkerhedsrisici API, Microsoft Defender for Endpoint tvm-api
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
ms.openlocfilehash: 97aa4a668306c4790dcd42c046ba4bf3a04bcf51
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840403"
---
# <a name="get-installed-software"></a>Hent installeret software

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

Henter en samling af installeret software, der er relateret til et givent enheds-id.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
:---|:---|:---
Program |Software.Read.All|"Læs oplysninger om software til trussels- og sårbarhedsstyring"
Uddelegeret (arbejds- eller skolekonto)|Software.Read|"Læs oplysninger om software til trussels- og sårbarhedsstyring"

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{machineId}/software
```

## <a name="request-headers"></a>Anmodningsheadere

Navn|Type|Beskrivelse
:---|:---|:---
Tilladelse|String|Ihændehaver {token}. **Påkrævet**.

## <a name="request-body"></a>Brødtekst i anmodning

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med de installerede softwareoplysninger i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/software
```

### <a name="response-example"></a>Svareksempel

Her er et eksempel på svaret.

```json
{
"@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
"value": [
        {
"id": "microsoft-_-internet_explorer",
"name": "internet_explorer",
"vendor": "microsoft",
"weaknesses": 67,
"publicExploit": true,
"activeAlert": false,
"exposedMachines": 42115,
"impactScore": 46.2037163
        }
    ]
}
```

## <a name="see-also"></a>Se også

- [Risikobaseret administration af trussel & sårbarhed](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Oversigt over sårbarheder i forbindelse med trussel &](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
