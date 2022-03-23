---
title: Hent brugerrelaterede maskiner API
description: Få mere at vide om, hvordan du bruger Hent brugerrelaterede maskiner API til at hente en samling af enheder, der er relateret til et bruger-id i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, bruger-, brugerrelaterede beskeder
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
ms.openlocfilehash: 5dd8cbd36fdac4aa3d0661a9b418a30ec2bae44f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63592058"
---
# <a name="get-user-related-machines-api"></a>Hent brugerrelaterede maskiner API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse
Henter en samling af enheder, der er relateret til et givet bruger-id.

## <a name="limitations"></a>Begrænsninger

Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program |Machine.Read.All|"Læs alle maskinprofiler"
Program |Machine.ReadWrite.All |"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto) | Machine.Read | "Læs maskinoplysninger"
Delegeret (arbejds- eller skolekonto) | Machine.ReadWrite | "Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data'. Få mere at vide under [Opret og administrer roller](user-roles.md)
> - Svar omfatter kun enheder, som brugeren har adgang til, baseret på enhedsgrupperingsindstillinger. Få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md).

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/users/{id}/machines
```

**Id'et er ikke det fulde UPN, men kun brugernavnet. (for eksempel til at hente maskiner til user1@contoso.com bruge /api/brugere/bruger1/maskiner)**

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og brugeren findes – 200 OK med liste [over enheder](machine.md) på computeren i brødteksten. Hvis brugeren ikke findes – 200 OK med et tomt sæt.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/machines
```
