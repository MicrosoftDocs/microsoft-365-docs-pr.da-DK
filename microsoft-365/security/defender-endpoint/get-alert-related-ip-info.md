---
title: Få beskedrelaterede IP'ers oplysninger
description: Hent alle IP'er, der er relateret til en bestemt besked ved hjælp af Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, få beskedoplysninger, beskedoplysninger, relateret ip
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
ms.openlocfilehash: c2268658223ff0bce0e879e23ea4a5c1ce843aaf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63593536"
---
# <a name="get-alert-related-ips-information-api"></a>Få besked-relaterede IP'ers informations-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter alle IP'er, der er relateret til en bestemt besked.

## <a name="limitations"></a>Begrænsninger

1. Du kan oprette en forespørgsel på beskeder, der senest er opdateret i henhold til din konfigurerede opbevaringsperiode.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|ip.read.all|"Læs IP-adresseprofiler"
Delegeret (arbejds- eller skolekonto)|ip.read.all|"Læs IP-adresseprofiler"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Få mere at vide under [Opret og administrer roller](user-roles.md)
> - Brugeren skal have adgang til den enhed, der er knyttet til beskeden, baseret på enhedsgrupperingsindstillinger (få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md)

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/alerts/{id}/ips
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og der vises en IP- adresse – 200 OK. Hvis beskeden ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/alerts/636688558380765161_2136280442/ips
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/$metadata#Ips",
    "value": [
                {
                    "id": "104.80.104.128"
                },
                {
                    "id": "23.203.232.228
                }
                ...
    ]
}
```
