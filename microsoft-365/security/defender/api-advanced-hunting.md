---
title: Microsoft 365 Defender avanceret API
description: Få mere at vide om, hvordan du kører avancerede forespørgselsforespørgsler ved hjælp Microsoft 365 Defender avanceret api på jagt
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
ms.openlocfilehash: 05957fcf7cf2b3b03fbc757fc8b21e67156b285a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500821"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender avanceret api

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

[Avanceret](advanced-hunting-overview.md) jagt er et værktøj til [trusselssøgning](advanced-hunting-query-language.md), der bruger specialkonstruerede forespørgsler til at undersøge de seneste 30 dages begivenhedsdata Microsoft 365 Defender. Du kan bruge avancerede forespørgselsforespørgsler til at undersøge usædvanlig aktivitet, opdage mulige trusler og endda reagere på angreb. Den avancerede jagt-API gør det muligt at forespørge på hændelsesdata automatisk.

## <a name="quotas-and-resource-allocation"></a>Kvoter og ressourceallokering

Følgende betingelser er relateret til alle forespørgsler.

1. Forespørgsler udforsker og returnerer data fra de seneste 30 dage.
2. Resultaterne kan returnere op til 100.000 rækker.
3. Du kan foretage op til 45 opkald pr. minut pr. lejer.
4. Forespørgsler blokeres, hvis lejeren har nået 100 % indtil efter den næste 15-minutters cyklus.
5. Hvis en enkelt anmodning kører i mere end 10 minutter, får den time out og returnerer en fejl.
6. En `429` HTTP-svarkode angiver, at du har nået en kvote, enten efter antal anmodninger, der er sendt, eller efter tildelt kørselstid. Læs svarteksten for at forstå den grænse, du har nået. 

> [!NOTE]
> Alle kvoter, der er angivet ovenfor (f.eks. 15 opkald pr. minut), er pr. lejerstørrelse. Disse kvoter er minimum.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde den avancerede jagt-API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, [under Access Microsoft 365 Defender Api'er til beskyttelse](api-access.md)

Tilladelsestype | Tilladelse | Visningsnavn for tilladelse
-|-|-
Program | AdvancedQuery.Read.All| Køre avancerede forespørgsler
Delegeret (arbejds- eller skolekonto) | AdvancedQuery.Read | Køre avancerede forespørgsler

>[!Note]
> Når du får et token med brugerlegitimationsoplysninger:
>
>- Brugeren skal have AD-rollen "Vis data"
>- Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder.

## <a name="http-request"></a>HTTP-anmodning

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved | Værdi
-|-
Godkendelse | Bearer {token} **-note: påkrævet**
Indholdstype | application/json

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter | Type | Beskrivelse
-|-|-
Forespørgsel | Tekst | Den forespørgsel, der skal køres. **Bemærk! påkrævet**

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode `200 OK`, og et _Forespørgselsrespons-objekt_ i brødteksten.

Svarobjektet indeholder tre egenskaber på øverste niveau:

1. Statistik – En ordbog til statistik for forespørgselsydeevne.
2. Skema – Skemaet for svaret, en liste over Name-Type par for hver kolonne.
3. Resultater – en liste over avancerede jagtbegivenheder.

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

- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
