---
title: Hent API til brugere af computerlogon
description: Få mere at vide om, hvordan du bruger API'en Hent maskinlogonbrugere til at hente en samling af brugere, der er logget på, på en enhed i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, enhed, log på, brugere
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
ms.openlocfilehash: 1c8635e7037f72830584d09d229891822a2e1f52
ms.sourcegitcommit: 2716cb48cc6127f6b851d177af23f276fb07bfc9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63592629"
---
# <a name="get-machine-logon-users-api"></a>Hent API til brugere af computerlogon

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API-beskrivelse
Henter en samling af brugere, der er logget på, på en bestemt enhed.

## <a name="limitations"></a>Begrænsninger
1. Du kan oprette en forespørgsel på beskeder, der senest er opdateret i henhold til din konfigurerede opbevaringsperiode.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program |User.Read.All |"Læs brugerprofiler"
Delegeret (arbejds- eller skolekonto) | User.Read.All | "Læs brugerprofiler"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data'. Få mere at vide under [Opret og administrer roller](user-roles.md).
> - Svar omfatter kun brugere, hvis enheden er synlig for brugeren baseret på enhedsgrupperingsindstillinger. Få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md).

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{id}/logonusers
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og enheden findes – 200 OK med liste [over](user.md) brugerenheder i brødteksten. Hvis enheden ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/logonusers
```

### <a name="response"></a>Svar

Her er et eksempel på svaret.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Users",
    "value": [
        {
            "id": "contoso\\user1",
            "accountName": "user1",
            "accountDomain": "contoso",
            "firstSeen": "2019-12-18T08:02:54Z",
            "lastSeen": "2020-01-06T08:01:48Z",
            "logonTypes": "Interactive",
            "isDomainAdmin": true,
            "isOnlyNetworkUser": false
        },
        ...
    ]
}
```
