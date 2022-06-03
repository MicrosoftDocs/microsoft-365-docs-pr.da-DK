---
title: Upload filer til biblioteket med livebesvaring
description: Få mere at vide om, hvordan du uploader en fil til biblioteket med live-svar.
keywords: apis, graf-API, understøttede API'er, upload til bibliotek
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
ms.openlocfilehash: 8e0bc9ca78a7e0baad7c07e73790215618aff9ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873731"
---
#  <a name="upload-files-to-the-live-response-library"></a>Upload filer til biblioteket med livebesvaring  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Upload fil til biblioteket med live-svar.

## <a name="limitations"></a>Begrænsninger

1.  Begrænsning af filmaks. størrelse er 20 MB.

2.  Hastighedsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Kom i gang](apis-intro.md).


| Tilladelsestype                    | Tilladelse     | Vist navn for tilladelse        |
|------------------------------------|----------------|--------------------------------|
| Program                        | Library.Manage | Administrer bibliotek med live-svar |
| Uddelegeret (arbejds- eller skolekonto) | Library.Manage | Administrer bibliotek med live-svar |

## <a name="http-request"></a>HTTP-anmodning

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>Anmodningsheadere

|  Navn   |    Type    |       Beskrivelse                         |
|-----------------|--------|--------------------------------|
| Tilladelse   | String | Ihændehaver\<token>. Kræves.      |
| Indholdstype    | Streng | flerparts-/formulardata. Kræves. |

## <a name="request-body"></a>Brødtekst i anmodning

Angiv følgende parametre for et formulardataobjekt i anmodningens brødtekst:

| Parameter         |     Type         |       Beskrivelse                                        |
|-----------------------|--------------|------------------------------------------------------------|
| Filer                  | Filindhold | Den fil, der skal overføres til biblioteket med live-svar. Kræves |
| Beskrivelse           | String       | Beskrivelse af filen.                                  |
| ParametersDescription | String       | (Valgfrit) Parametre, der kræves, for at scriptet kan køre. Standardværdien er en tom streng.                |
| OverrideIfExists      | Boolesk       | (Valgfrit) Angiver, om filen skal tilsidesættes, hvis den allerede findes. Standardværdien er en tom streng.          |



## <a name="response"></a>Svar

-   Hvis det lykkes, returnerer denne metode 200 – OK-svarkode og det overførte live response-biblioteksobjekt i svarets brødtekst.

-   Hvis det ikke lykkes: Denne metode returnerer 400 – ugyldig anmodning.  
    Forkert anmodning angiver normalt forkert brødtekst.

## <a name="example"></a>Eksempel

Anmodning

Her er et eksempel på anmodningen ved hjælp af curl.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>Relateret emne

-  [Kør Direkte svar](run-live-response.md) 