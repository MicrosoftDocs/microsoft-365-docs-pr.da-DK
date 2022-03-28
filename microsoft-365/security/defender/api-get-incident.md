---
title: Hent hændelses-API
description: Få mere at vide om, hvordan du bruger Hent hændelses-API'en til at få en enkelt hændelse Microsoft 365 Defender.
keywords: apis, graph api, understøttede API'er, hent, fil, hash
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 8861dc3752d2c4cc798bc83475f6a51f8245191a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63597969"
---
# <a name="get-incident-information-api"></a>Hent API med oplysninger om hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en bestemt hændelse ved hjælp af dens id

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Incident.Read.All|"Læs alle hændelser"
Program|Incident.ReadWrite.All|"Læs og skriv alle hændelser"
Delegeret (arbejds- eller skolekonto)|Incident.Read|"Læs hændelser"
Delegeret (arbejds- eller skolekonto)|Incident.ReadWrite|"Læs og skriv hændelser"

> [!NOTE]
>
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: "Vis data"
> - Svaret vil kun omfatte hændelser, som brugeren er eksponeret for

## <a name="http-request"></a>HTTP-anmodning

```console
GET .../api/incidents/{id}
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
---|---|---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og hændelsesenheden i svarteksten.
Hvis hændelsen med det angivne id ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
