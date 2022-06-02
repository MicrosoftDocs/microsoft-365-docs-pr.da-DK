---
title: Hent manglende KB efter enheds-id
description: Henter manglende sikkerhedsopdateringer efter enheds-id
keywords: apis, graph api, understøttede API'er, hent, liste, fil, oplysninger, enheds-id, trussel & håndtering af sikkerhedsrisici api, Microsoft Defender for Endpoint tvm-api
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
ms.openlocfilehash: 4a570851263b6a52193353e2c229e2df47b677e3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840293"
---
# <a name="get-missing-kbs-by-device-id"></a>Hent manglende KB efter enheds-id

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Henter manglende KB (sikkerhedsopdateringer) efter enheds-id

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{machineId}/getmissingkbs
```
## <a name="permissions"></a>Tilladelser

Følgende tilladelse er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Brug Microsoft Defender for Endpoint API'er](apis-intro.md).

Tilladelsestype | Tilladelse | Vist navn for tilladelse
:---|:---|:---
Program | Software.Read.All | "Læs oplysninger om software til trussels- og sårbarhedsstyring"

## <a name="request-header"></a>Anmodningsheader

Navn|Type|Beskrivelse
:---|:---|:---
Tilladelse | String | Ihændehaver {token}. **Påkrævet**.

## <a name="request-body"></a>Brødtekst i anmodning

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK, hvor den angivne enhed mangler KB-data i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines/2339ad14a01bd0299afb93dfa2550136057bff96/getmissingkbs 
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
                "windows_10",
                "edge",
                "internet_explorer"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 1,
            "cveAddressed": 97
        }
        ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Risikobaseret administration af trussel & sårbarhed](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Oversigt over sårbarheder i forbindelse med trussel &](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
