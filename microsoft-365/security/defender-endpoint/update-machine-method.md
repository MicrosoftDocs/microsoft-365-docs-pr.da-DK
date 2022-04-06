---
title: Opdater enheds-API til computer
description: Få mere at vide om, hvordan du opdaterer maskinmærker ved hjælp af denne API. Du kan opdatere egenskaberne for mærker og enhedsværdi.
keywords: apis, graph api, understøttede API'er, hent, besked, oplysninger, id
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
ms.openlocfilehash: 77876024faa7452ff284e30a587e72855068cc98
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63606593"
---
# <a name="update-machine"></a>Opdater computer 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Opdaterer egenskaberne for eksisterende [computer](machine.md).

Egenskaber, der kan opdateres, er: `machineTags` og `deviceValue`.

## <a name="limitations"></a>Begrænsninger

1. Du kan opdatere computere, der er tilgængelige i API'en. 
2. Opdater maskine føjer kun mærker til mærkesamlingen. Hvis der findes mærker, skal de medtages i samlingen af mærker i brødteksten.
3. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.ReadWrite.All|"Læs og skriv maskinoplysninger for alle computere"
Delegeret (arbejds- eller skolekonto)|Machine.ReadWrite|"Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
> - Brugeren skal mindst have følgende rolletilladelse: "Undersøgelse af beskeder". Få mere at vide under [Opret og administrer roller](user-roles.md).
> - Brugeren skal have adgang til den enhed, der er knyttet til beskeden, baseret på enhedsgrupperingsindstillinger. Få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md).

## <a name="http-request"></a>HTTP-anmodning

```http
PATCH /api/machines/{machineId}
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|String|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive værdierne for de relevante felter, der skal opdateres.

Eksisterende egenskaber, der ikke er inkluderet i brødteksten i anmodningen, bevarer deres tidligere værdier eller genberegnes baseret på ændringer i andre egenskabsværdier.

Du opnår den bedste ydeevne ved ikke at medtage eksisterende værdier, der ikke er blevet ændret.

Egenskab|Type|Beskrivelse
:---|:---|:---
maskintags|Strengsamling|Sæt af [maskinmærker](machine.md) .
deviceValue|Null-værdi Enum|[Enhedens værdi](tvm-assign-device-value.md). De mulige værdier er: 'Normal', 'Lav' og 'Høj'.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og [computerenheden](machine.md) i svarteksten med de opdaterede egenskaber.

Hvis samlingen af maskinmærker i brødteksten ikke indeholder eksisterende maskinmærker – erstatter alle mærker med de mærker, der findes i brødteksten.

Hvis en computer med det angivne id ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
