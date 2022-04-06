---
title: Upload til det direkte svarbibliotek
description: Få mere at vide om, hvordan du overfører en fil til live svarbiblioteket.
keywords: API'er, graph api, understøttede API'er, upload til bibliotek
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
ms.openlocfilehash: 84ec7e361cccdc886650b0710f738a4315c4db8d
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705595"
---
#  <a name="upload-files-to-the-live-response-library"></a>Upload til det direkte svarbibliotek  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Upload til live svarbibliotek.

## <a name="limitations"></a>Begrænsninger

1.  Begrænsning på filstørrelse er 20 MB.

2.  Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md).


| Tilladelsestype                    | Tilladelse     | Visningsnavn for tilladelse        |
|------------------------------------|----------------|--------------------------------|
| Program                        | Library.Manage | Administrer live svarbibliotek |
| Delegeret (arbejds- eller skolekonto) | Library.Manage | Administrer live svarbibliotek |

## <a name="http-request"></a>HTTP-anmodning

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Anmod om brevhoveder

|  Navn   |    Type    |       Beskrivelse                         |
|-----------------|--------|--------------------------------|
| Godkendelse   | String | Bearer\<token>. Påkrævet.      |
| Indholdstype    | streng | multipart/form-data. Påkrævet. |

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et formulardataobjekt med følgende parametre:

| Parameter         |     Type         |       Beskrivelse                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Filer                  | Filindhold | Den fil, der skal uploades til Live Response Library. Påkrævet |
| Beskrivelse           | String       | Beskrivelse af filen.                                  |
| ParametersDescription | String       | (Valgfrit) Parametre, der kræves, for at scriptet kan køres. Standardværdien er en tom streng.                |
| OverrideIfExists      | Boolesk       | (Valgfrit) Om filen skal tilsidesættes, hvis den allerede findes. Standardværdien er en tom streng.          |



## <a name="response"></a>Svar

-   Hvis det lykkes, returnerer denne metode 200 - OK-svarkode og den overførte enhed til Live Response-biblioteket i svarteksten.

-   Hvis det ikke lykkes: Denne metode returnerer 400 - Dårlig anmodning.  
    Dårlig anmodning angiver normalt forkert brødtekst.

## <a name="example"></a>Eksempel

Anmod

Her er et eksempel på anmodningen med krøllede.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Relateret emne

-  [Kør live-svar](run-live-response.md) 