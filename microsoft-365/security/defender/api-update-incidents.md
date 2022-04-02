---
title: Opdater hændelses-API
description: Få mere at vide om, hvordan du opdaterer hændelser ved Microsoft 365 Defender API
keywords: opdatering, api, hændelse
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 447a4b5eb3f4eb521e7cc3bd2df23a42f16d2ef1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63603003"
---
# <a name="update-incidents-api"></a>Opdater api'en Hændelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

## <a name="api-description"></a>API-beskrivelse

Opdaterer egenskaberne for en eksisterende hændelse. Egenskaber, der kan opdateres, er`determination`: `status`, `classification`, `assignedTo`, `tags`og `comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>Kvoter, ressourceallokering og andre begrænsninger

1. Du kan foretage op til 50 opkald i minuttet eller 1500 opkald pr. time, før du når begrænsningstærsklen.
2. Du kan kun angive egenskaben `determination` , hvis den `classification` er indstillet til TruePositive.

Hvis din anmodning er blevet begrænser, returnerer den en `429` svarkode. Svarteksten angiver tidspunktet, hvor du kan begynde at foretage nye opkald.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, [under Access Microsoft 365 Defender API'er](api-access.md).

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Incident.ReadWrite.All|Læs og skriv alle hændelser
Delegeret (arbejds- eller skolekonto)|Incident.ReadWrite|Læs og skriv hændelser

> [!NOTE]
> Når brugeren får et token med brugerlegitimationsoplysninger, skal han eller hun have tilladelse til at opdatere hændelsen i portalen.

## <a name="http-request"></a>HTTP-anmodning

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
---|---|---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|String|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive værdierne for de felter, der skal opdateres. Eksisterende egenskaber, der ikke er inkluderet i brødteksten i anmodningen, bevarer deres værdier, medmindre de skal genberegnes på grund af ændringer i relaterede værdier. Du opnår den bedste ydeevne ved at udelade eksisterende værdier, der ikke er blevet ændret.

Egenskab|Type|Beskrivelse
---|---|---
status|Enum|Angiver den aktuelle status for hændelsen. De mulige værdier er: `Active`, `Resolved`og `Redirected`.
assignedTo|streng|Ejeren af hændelsen.
klassificering|Enum|Specifikation af hændelsen. De mulige værdier er: `Unknown`, `FalsePositive`, `TruePositive`.
determination|Enum|Angiver bestemmelse af hændelsen. Mulige værdier er: `NotAvailable`, , `Apt``Malware`, `SecurityPersonnel`, `SecurityTesting`, `UnwantedSoftware`, `Other`.
mærker|strengliste|Liste over hændelsesmærker.
kommentar|streng|Kommentar, der skal føjes til hændelsen.

## <a name="response"></a>Svar

Hvis det lykkes, returneres denne metode `200 OK`. Svarteksten indeholder hændelsesenheden med opdaterede egenskaber. Hvis en hændelse med det angivne id ikke blev fundet, returnerer metoden `404 Not Found`.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### <a name="response-example"></a>Eksempel på svar

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comments": [
          {
              "comment": "pen testing",
              "createdBy": "secop2@contoso.com",
              "createdTime": "2021-05-02T09:34:21.5519738Z"
          },
          {
              "comment": "valid incident",
              "createdBy": "secop2@contoso.comt",
              "createdTime": "2021-05-02T09:36:27.6652581Z"
          }
      ]
}
```

## <a name="related-articles"></a>Relaterede artikler

- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Hændelses-API'er](api-incident.md)
- [Liste over hændelser](api-list-incidents.md)
- [Oversigt over hændelser](incidents-overview.md)
