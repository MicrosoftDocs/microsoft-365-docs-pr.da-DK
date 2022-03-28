---
title: Hent domænestatistik-API
description: Få mere at vide om, hvordan du bruger Hent domænestatistik-API'en til at hente statistikken på det angivne domæne i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, domæne, domænerelaterede enheder
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
ms.openlocfilehash: 2e07b9545ef6bab0c7b93188edf65d43ae0378b2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597569"
---
# <a name="get-domain-statistics-api"></a>Hent domænestatistik-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter statistikken på det angivne domæne.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.
2. Maksimumværdien for er `lookbackhours` 720 timer (30 dage).

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|URL-adresse. Read.All|"Læse URL-adresser"
Delegeret (arbejds- eller skolekonto)|URL-adresse. Read.All|"Læse URL-adresser"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/domains/{domain}/stats
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved|Værdi
:---|:---
Godkendelse|Bearer {token}. **Påkrævet**.

## <a name="request-uri-parameters"></a>Anmod om URI-parametre

Navn|Type|Beskrivelse
:---|:---|:---
lookBackHours|Int32|Definerer, hvor mange timer vi søger tilbage for at hente statistikken. Er som standard 30 dage. **Valgfrit**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og domænet findes – 200 OK, med et statistikobjekt i svarteksten. Hvis domæne ikke findes – 200 OK med en indstillet til 0.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/domains/example.com/stats?lookBackHours=48
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgDomainStats",
    "host": "example.com",
    "organizationPrevalence": 4070,
    "orgFirstSeen": "2017-07-30T13:23:48Z",
    "orgLastSeen": "2017-08-29T13:09:05Z"
}
```
