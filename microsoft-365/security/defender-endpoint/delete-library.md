---
title: Slet en fil fra live-svarbiblioteket
description: Få mere at vide om, hvordan du sletter en fil fra det direkte svarbibliotek.
keywords: apis, graph api, understøttede API'er, slet fra bibliotek
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
ms.openlocfilehash: 23625c8b7160d604df5f3a8b1b1387fc31027acf
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705555"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>Slet en fil fra live-svarbiblioteket  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Slet en fil fra live response-bibliotek.

## <a name="limitations"></a>Begrænsninger

1.  Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md).

| Tilladelsestype                    | Tilladelse     | Visningsnavn for tilladelse        |
|------------------------------------|----------------|--------------------------------|
| Program                        | Library.Manage | Administrer live svarbibliotek |
| Delegeret (arbejds- eller skolekonto) | Library.Manage | Administrer live svarbibliotek |

## <a name="http-request"></a>HTTP-anmodning

DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>Anmod om brevhoveder

| Navn            | Type   | Beskrivelse               |
|-----------------|--------|---------------------------|
| Godkendelse   | String | Bearer\<token>\. Påkrævet. |

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

-   Hvis filen findes i biblioteket og slettet 204 Intet indhold.

-   Hvis det angivne filnavn ikke blev fundet 404 Blev ikke fundet.

## <a name="example"></a>Eksempel

Anmod

Her er et eksempel på anmodningen.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>Relateret emne
- [Kør live-svar](run-live-response.md) 