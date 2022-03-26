---
title: Få relevante oplysninger om en enhed med gå på jagt
description: Få mere at vide om, hvordan du bruger søgeværktøjet til at forespørge hurtigt efter relevante oplysninger om en enhed eller begivenhed ved hjælp af avanceret jagt.
keywords: avanceret jagt, hændelse, pivot, enhed, go hunt, relevante begivenheder, trusselssøgning, cybertrusel, søgning, forespørgsel, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 3d1ec22febe0c0072a4eed2a9b8fece3687762d7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754272"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Hurtig jagt på enheds- eller begivenhedsoplysninger med gå på jagt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Med handlingen *gå på jagt* kan du hurtigt undersøge begivenheder og forskellige enhedstyper ved hjælp af effektive forespørgselsbaserede [avancerede jagtegenskaber](advanced-hunting-overview.md) . Denne handling kører automatisk en avanceret forespørgsel for at finde relevante oplysninger om den valgte hændelse eller enhed.

Handlingen *er tilgængelig* i forskellige afsnit af Defender til skyen. Denne handling er tilgængelig for visning, når oplysninger om hændelse eller enhed vises. Du kan f.eks. bruge *indstillingen gå* på jagt fra følgende afsnit:

- På [hændelsessiden kan](investigate-incidents.md#summary) du gennemse oplysninger om brugere, enheder og mange andre enheder, der er knyttet til en hændelse. Når du vælger en enhed, får du yderligere oplysninger og de forskellige handlinger, du kan udføre på den pågældende enhed. I eksemplet nedenfor er en postkasse markeret og viser detaljer om postkassen og muligheden for at lede efter flere oplysninger om postkassen.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Siden Postkasser med indstillingen Gå på jagt Microsoft 365 Defender portalen" lightbox="../../media/go-hunt-1-incident.png":::

- På hændelsessiden kan du også få adgang til en liste over enheder under **fanen** Beviser. Hvis du vælger en af disse enheder, kan du hurtigt lede efter oplysninger om den pågældende enhed.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="Indstillingen Gå på jagt efter et stykke bevis på siden Hændelse i Microsoft 365 Defender portal" lightbox="../../media/go-hunt-2-entity.png":::


- Når du får vist tidslinjen for en enhed, kan du vælge en begivenhed på tidslinjen for at få vist yderligere oplysninger om den pågældende begivenhed. Når en begivenhed er markeret, får du mulighed for at lede efter andre relevante begivenheder i avanceret jagt.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="Indstillingen Søg efter relaterede begivenheder på en begivenheds side under fanen Tidslinjer i Microsoft 365 Defender portal" lightbox="../../media/go-hunt-3-event.png":::

Når du **vælger Gå på** **jagt eller På jagt efter** relaterede begivenheder, sendes der forskellige forespørgsler, afhængigt af om du har valgt en enhed eller en hændelse.

## <a name="query-for-entity-information"></a>Forespørgsel for enhedsoplysninger
Du kan bruge *gå på jagt* efter oplysninger om en bruger, enhed eller enhver anden type enhed; Forespørgslen kontrollerer alle relevante skematabeller for alle hændelser, der vedrører den pågældende enhed, for at returnere oplysninger. For at holde resultaterne håndterbare er forespørgslen:
- området til omkring den samme tidsperiode som den tidligste aktivitet i de seneste 30 dage, der omfatter enheden
- knyttet til hændelsen.

Her er et eksempel på søgeforespørgslen om en enhed:

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```
### <a name="supported-entity-types"></a>Understøttede enhedstyper
Du kan bruge indstillingen *gå på jagt* efter at have valgt en af disse enhedstyper:

- Filer
- Mails
- Mailklynger
- Postkasser
- Brugere
- Enheder
- IP-adresser
- URL-adresser

## <a name="query-for-event-information"></a>Forespørgsel til oplysninger om begivenhed
Når du *bruger gå på jagt* efter oplysninger om en tidslinjebegivenhed, kontrollerer forespørgslen alle relevante skematabeller for andre hændelser omkring tidspunktet for den valgte begivenhed. I følgende forespørgsel vises hændelser i forskellige skematabeller, der opstod omkring samme tidsperiode på den samme enhed:

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## <a name="adjust-the-query"></a>Juster forespørgslen
Med et kendskab til [forespørgselssproget](advanced-hunting-query-language.md) kan du justere forespørgslen efter dine præferencer. Du kan f.eks. justere denne linje, hvilket bestemmer størrelsen af tidvinduet:

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

Ud over at redigere forespørgslen for at få mere relevante resultater kan du også:
- [Få vist resultaterne som diagrammer](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Oprette en brugerdefineret registreringsregel](custom-detection-rules.md)

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brugerdefinerede registreringsregler](custom-detection-rules.md)
