---
title: Arbejd med avancerede jagtforespørgslens resultater i Microsoft 365 Defender
description: Få mest ud af de forespørgselsresultater, der returneres af avanceret jagt i Microsoft 365 Defender
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, visualisering, diagram, filtre, detailudledning
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
ms.openlocfilehash: cb17e2a3624471031eb4f72199705d6b8fe06979
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092861"
---
# <a name="work-with-advanced-hunting-query-results"></a>Arbejd med avancerede resultater af jagtforespørgslen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Selvom du kan konstruere dine [avancerede](advanced-hunting-overview.md) jagtforespørgsler for at returnere præcise oplysninger, kan du også arbejde med forespørgselsresultaterne for at få yderligere indsigt og undersøge specifikke aktiviteter og indikatorer. Du kan foretage følgende handlinger på dine forespørgselsresultater:

- Vis resultater som en tabel eller et diagram
- Eksportér tabeller og diagrammer
- Analysér ned til detaljerede enhedsoplysninger
- Tilpas dine forespørgsler direkte fra resultaterne

## <a name="view-query-results-as-a-table-or-chart"></a>Få vist forespørgselsresultater som en tabel eller et diagram

Som standard viser avanceret jagt forespørgselsresultater som tabeldata. Du kan også få vist de samme data som et diagram. Avanceret jagt understøtter følgende visninger:

| Visningstype | Beskrivelse |
|--|--|
| **Tabel** | Viser forespørgselsresultaterne i tabelformat |
| **Søjlediagram** | Gengiver en række entydige elementer på x-aksen som lodrette streger, hvis højde repræsenterer numeriske værdier fra et andet felt |
| **Cirkeldiagram** | Gengiver sektionstærter, der repræsenterer entydige elementer. Størrelsen af hvert cirkeldiagram repræsenterer numeriske værdier fra et andet felt. |
| **Kurvediagram** | Afbilder numeriske værdier for en række entydige elementer og forbinder de afbildede værdier |
| **Punktdiagram** | Afbilder numeriske værdier for en række entydige elementer |
| **Områdediagram** | Afbilder numeriske værdier for en række entydige elementer og udfylder sektionerne under de afbildede værdier |
| **Stablet områdediagram** | Afbilder numeriske værdier for en række entydige elementer og stabler de udfyldte sektioner under de afbildede værdier  |
| **Tidsdiagram** | Afbilder værdier efter antal på en lineær tidsskala |

### <a name="construct-queries-for-effective-charts"></a>Konstruer forespørgsler for effektive diagrammer

Når du gengiver diagrammer, identificerer avanceret jagt automatisk de kolonner, der er interessante, og de numeriske værdier, der skal aggregeres. Hvis du vil have meningsfulde diagrammer, skal du konstruere dine forespørgsler for at returnere de specifikke værdier, du vil have vist visualiseret. Her er nogle eksempelforespørgsler og de diagrammer, der oprettes.

#### <a name="alerts-by-severity"></a>Beskeder efter alvorsgrad

Brug operatoren `summarize` til at få et numerisk antal af de værdier, du vil oprette et diagram over. I forespørgslen nedenfor bruges operatoren `summarize` til at hente antallet af beskeder efter alvorsgrad.

```kusto
AlertInfo
| summarize Total = count() by Severity
```

Når du gengiver resultaterne, viser et søjlediagram hver alvorsgradsværdi som en separat kolonne:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Et eksempel på et diagram, der viser avancerede jagtresultater på Microsoft 365 Defender portalen" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Forespørgselsresultater for beskeder efter alvorsgrad vist som et søjlediagram*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Phishing-mails på tværs af top ti afsenderdomæner

Hvis du har at gøre med en liste over værdier, der ikke er endelige, kan du bruge operatoren `Top` til kun at oprette et diagram over værdierne med de fleste forekomster. Hvis du f.eks. vil have de øverste 10 afsenderdomæner med de mest phishing-mails, skal du bruge forespørgslen nedenfor:

```kusto
EmailEvents
| where ThreatTypes has "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```

Brug cirkeldiagramvisningen til effektivt at vise distribution på tværs af de øverste domæner:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Det cirkeldiagram, der viser avancerede jagtresultater på Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Cirkeldiagram, der viser distribution af phishing-mails på tværs af de mest populære afsenderdomæner*

#### <a name="file-activities-over-time"></a>Filaktiviteter over tid
Ved hjælp af operatoren `summarize` med funktionen `bin()` kan du kontrollere, om der er hændelser, der involverer en bestemt indikator over tid. Forespørgslen nedenfor tæller hændelser, der involverer filen `invoice.doc` , med 30 minutters intervaller for at få vist stigninger i aktiviteter, der er relateret til den pågældende fil:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```

Kurvediagrammet nedenfor fremhæver tydeligt tidsperioder med mere aktivitet, der involverer `invoice.doc`:

:::image type="content" source="../../media/line-chart-a.png" alt-text="Det kurvediagram, der viser avancerede jagtresultater på Microsoft 365 Defender-portalen" lightbox="../../media/line-chart-a.png":::
*Kurvediagram, der viser antallet af hændelser, der involverer en fil over tid*

## <a name="export-tables-and-charts"></a>Eksportér tabeller og diagrammer

Når du har kørt en forespørgsel, skal du vælge **Eksportér** for at gemme resultaterne i den lokale fil. Den valgte visning bestemmer, hvordan resultaterne eksporteres:

- **Tabelvisning** – Forespørgselsresultaterne eksporteres i tabelformat som en Microsoft Excel projektmappe
- **Et diagram** – forespørgselsresultaterne eksporteres som et JPEG-billede af det gengivne diagram

## <a name="drill-down-from-query-results"></a>Analysér ned fra forespørgselsresultater

Hvis du hurtigt vil undersøge en post i dine forespørgselsresultater, skal du vælge den tilsvarende række for at åbne panelet **Undersøg post** . Panelet indeholder følgende oplysninger baseret på den valgte post:

- **Assets** – Opsummeret visning af hovedaktiverne (postkasser, enheder og brugere), der findes i posten, beriget med tilgængelige oplysninger, f.eks. risiko- og eksponeringsniveauer
- **Alle detaljer** – alle værdierne fra kolonnerne i posten

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Den valgte post med panel til undersøgelse af posten på Microsoft 365 Defender-portalen" lightbox="../../media/results-inspect-record.png":::

Hvis du vil have vist flere oplysninger om et bestemt objekt i dine forespørgselsresultater, f.eks. en computer, fil, bruger, IP-adresse eller URL-adresse, skal du vælge enheds-id'et for at åbne en detaljeret profilside for det pågældende objekt.

## <a name="tweak-your-queries-from-the-results"></a>Tilpas dine forespørgsler ud fra resultaterne

Vælg de tre prikker til højre for en hvilken som helst kolonne i panelet **Undersøg post** . Du kan bruge indstillingerne til at:

- Søg eksplicit efter den valgte værdi (`==`)
- Udelad den valgte værdi fra forespørgslen (`!=`)
- Få mere avancerede operatorer til at føje værdien til din forespørgsel, f.eks. `contains`, `starts with`og `ends with`

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Ruden Handlingstype på siden Undersøg post på Microsoft 365 Defender-portalen" lightbox="../../media/work-with-query-tweak-query.png":::

> [!NOTE]
> Nogle tabeller i denne artikel er muligvis ikke tilgængelige på Microsoft Defender for Endpoint. [Slå Microsoft 365 Defender](m365d-enable.md) til for at jagte trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser for jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i [Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)
