---
title: Microsoft 365 Defender API til avanceret jagt
description: Få mere at vide om, hvordan du kører avancerede jagtforespørgsler ved hjælp af Microsoft 365 Defender avancerede jagt-API
keywords: Avanceret jagt, API'er, api, M365 Defender, Microsoft 365 Defender
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
ms.openlocfilehash: d01cdacc40b58eb940b2773606221b4fdbe18728
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823184"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>api til avanceret jagt Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

[Avanceret jagt](advanced-hunting-overview.md) er et værktøj til trusselsjagt, der bruger [særligt konstruerede forespørgsler](advanced-hunting-query-language.md) til at undersøge de seneste 30 dages hændelsesdata i Microsoft 365 Defender. Du kan bruge avancerede jagtforespørgsler til at inspicere usædvanlig aktivitet, registrere mulige trusler og endda reagere på angreb. Den avancerede jagt-API giver dig mulighed for at sende en programatisk forespørgsel om hændelsesdata.

## <a name="quotas-and-resource-allocation"></a>Kvoter og ressourceallokering

Følgende betingelser er relateret til alle forespørgsler.

1. Forespørgsler udforsker og returnerer data fra de seneste 30 dage.
2. Resultaterne kan returnere op til 100.000 rækker.
3. Du kan foretage op til 45 opkald pr. minut pr. lejer.
4. Forespørgsler blokeres, hvis lejeren har nået 100 % indtil efter den næste 15-minutters cyklus.
5. Hvis en enkelt anmodning kører i mere end 10 minutter, får den timeout og returnerer en fejl.
6. En `429` HTTP-svarkode angiver, at du har nået en kvote, enten efter antal anmodninger, der er sendt, eller af den tildelte kørselstid. Læs svarteksten for at forstå den grænse, du har nået. 

> [!NOTE]
> Alle kvotaer, der er angivet ovenfor (f.eks. 15 opkald pr. min.), er pr. lejerstørrelse. Disse kvoter er minimum.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde API'en for avanceret jagt. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Få adgang til API'er til beskyttelse af Microsoft 365 Defender](api-access.md)

Tilladelsestype | Tilladelse | Vist navn for tilladelse
-|-|-
Program | AdvancedHunting.Read.All| Kør avancerede forespørgsler
Uddelegeret (arbejds- eller skolekonto) | AdvancedHunting.Read | Kør avancerede forespørgsler

>[!Note]
> Når du henter et token ved hjælp af brugerlegitimationsoplysninger:
>
>- Brugeren skal have AD-rollen 'Vis data'
>- Brugeren skal have adgang til enheden baseret på indstillingerne for enhedsgruppe.

## <a name="http-request"></a>HTTP-anmodning

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>Anmodningsheadere

Header | Værdi
-|-
Tilladelse | Ihændehaver {token} **Bemærk! påkrævet**
Indholdstype | program/json

## <a name="request-body"></a>Brødtekst i anmodning

Angiv følgende parametre for et JSON-objekt i anmodningens brødtekst:

Parameter | Type | Beskrivelse
-|-|-
Forespørgsel | Tekst | Den forespørgsel, der skal køres. **Bemærk! påkrævet**

## <a name="response"></a>Svar

Hvis det lykkes, returnerer `200 OK`denne metode og et _QueryResponse-objekt_ i svarbrødteksten.

Svarobjektet indeholder tre egenskaber på øverste niveau:

1. Statistik – en ordbog over statistik for forespørgselsydeevne.
2. Schema – Skemaet for svaret, en liste over Name-Type par for hver kolonne.
3. Results – En liste over avancerede jagtbegivenheder.

## <a name="example"></a>Eksempel

I følgende eksempel sender en bruger forespørgslen nedenfor og modtager et API-svarobjekt, der indeholder `Stats`, `Schema`og `Results`.

### <a name="query"></a>Forespørgsel

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>Svarobjekt

```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

## <a name="related-articles"></a>Relaterede artikler

- [Få adgang til de Microsoft 365 Defender API'er](api-access.md)
- [Få mere at vide om API-grænser og -licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
