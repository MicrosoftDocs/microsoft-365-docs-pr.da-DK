---
title: Filtype
description: Hent de seneste Microsoft Defender for Endpoint-beskeder, der er relateret til filer.
keywords: apis, graph api, understøttede API'er, hent, beskeder, seneste
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
ms.openlocfilehash: 7fef64136e27b8b9a85163fe9e25fdf59ab6d2aa
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591302"
---
# <a name="file-resource-type"></a>Filtype

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Repræsenterer en filenhed i Defender for Slutpunkt.

## <a name="methods"></a>Metoder

Metode|Returtype |Beskrivelse
:---|:---|:---
[Hent fil](get-file-information.md) | [fil](files.md) | Hent en enkelt fil 
[Vis filrelaterede beskeder](get-file-related-alerts.md) | [samling af](alerts.md) beskeder | Få de [beskedenheder](alerts.md) , der er knyttet til filen.
[Listefilrelaterede maskiner](get-file-related-machines.md) | [maskine samling](machine.md) | Få fat [i de enheder](machine.md) , der er knyttet til beskeden.
[filstatistik](get-file-statistics.md) | Statistikoversigt | Henter den angivne fils ikke-givne fil.


## <a name="properties"></a>Egenskaber

|Egenskab | Type | Beskrivelse |
|:---|:---|:---|
|sha1 | String | Sha1-hash på filens indhold |
|sha256 | String | Sha256 hash for filens indhold |
|globalPrevalence | Null-værdi lang | Fil på tværs af hele organisationen |
|globalFirstObserved | DateTimeOffset | Første gang filen blev observeret |
|globalLastObserved | DateTimeOffset | Sidste gang filen blev observeret |
|størrelse | Null-værdi lang | Filens størrelse |
|fileType | String | Filtypen |
|isPeFile | Boolesk  | sand, hvis filen er bærbar eksekverbar (f.eks. "DLL", "EXE" osv.) |
|filePublisher | String | Filudgiver |
|fileProductName | String | Produktnavn |
|underskriver | String | Fil underskriver |
|udsteder | String | Filudsteder |
|signerHash | String | Hash på signeringscertifikatet |
|isValidCertificate | Boolesk  | Signeringscertifikatet blev bekræftet af Microsoft Defender som slutpunktsagent |
|determinationType | String | Filens bestemmelsestype |
|determinationValue | String | Determinationsværdi |

## <a name="json-representation"></a>Json-repræsentation

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
