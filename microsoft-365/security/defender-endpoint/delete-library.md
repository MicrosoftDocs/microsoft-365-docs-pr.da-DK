---
title: Slet en fil fra biblioteket med livebesvaring
description: Få mere at vide om, hvordan du sletter en fil fra biblioteket med live-svar.
keywords: apis, graf-API, understøttede API'er, slet fra bibliotek
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 97a2a2152a60ff542cb946c4283fe3f26c4b9c8e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874124"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Slet en fil fra biblioteket med livebesvaring  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Slet en fil fra biblioteket med live-svar.

## <a name="limitations"></a>Begrænsninger

1.  Hastighedsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Kom i gang](apis-intro.md).

| Tilladelsestype                    | Tilladelse     | Vist navn for tilladelse        |
|------------------------------------|----------------|--------------------------------|
| Program                        | Library.Manage | Administrer bibliotek med live-svar |
| Uddelegeret (arbejds- eller skolekonto) | Library.Manage | Administrer bibliotek med live-svar |

## <a name="http-request"></a>HTTP-anmodning

SLETTE https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>Anmodningsheadere

| Navn            | Type   | Beskrivelse               |
|-----------------|--------|---------------------------|
| Tilladelse   | String | Bærer\<token>\. Kræves. |

## <a name="request-body"></a>Brødtekst i anmodning

Tom

## <a name="response"></a>Svar

-   Hvis filen findes i biblioteket og er blevet slettet uden indhold 204.

-   Hvis det angivne filnavn ikke blev fundet, blev 404 ikke fundet.

## <a name="example"></a>Eksempel

Anmodning

Her er et eksempel på anmodningen.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Relateret emne
- [Kør Direkte svar](run-live-response.md) 