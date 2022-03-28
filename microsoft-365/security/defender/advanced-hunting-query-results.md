---
title: Arbejd med avancerede resultater af forespørgselsforespørgsel i Microsoft 365 Defender
description: Få mest muligt ud af de forespørgselsresultater, der returneres ved avanceret jagt i Microsoft 365 Defender
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, visualisering, diagram, filtre, analyse ned
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
ms.openlocfilehash: 41427760a0a02f0dafbb9685da457a473698207c
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755002"
---
# <a name="work-with-advanced-hunting-query-results"></a>Arbejd med avancerede resultater af en forespørgsel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Selvom du kan [oprette dine avancerede](advanced-hunting-overview.md) forespørgselsforespørgsler for at returnere præcise oplysninger, kan du også arbejde med forespørgselsresultaterne for at få yderligere indsigt og undersøge specifikke aktiviteter og indikatorer. Du kan udføre følgende handlinger for dine forespørgselsresultater:

- Få vist resultater som en tabel eller et diagram
- Eksportér tabeller og diagrammer
- Analyser ned til detaljerede enhedsoplysninger
- Tilpas dine forespørgsler direkte fra resultaterne, eller anvend filtre

## <a name="view-query-results-as-a-table-or-chart"></a>Få vist forespørgselsresultater som en tabel eller et diagram
Avanceret forespørgsel viser som standard forespørgselsresultater som tabeldata. Du kan også få vist de samme data som et diagram. Avanceret ræv understøtter følgende visninger:

| Visningstype | Beskrivelse |
|--|--|
| **Tabel** | Viser forespørgselsresultaterne i tabelformat |
| **Søjlediagram** | Gengiver en række entydige elementer på x-aksen som lodrette søjler, hvis højder repræsenterer numeriske værdier fra et andet felt |
| **Stablet søjlediagram** | Gengiver en række entydige elementer på x-aksen som stablede lodrette søjler, hvis højde repræsenterer numeriske værdier fra et eller flere andre felter |
| **Cirkeldiagram** | Gengiver sektionsudsnit, der repræsenterer unikke elementer. Størrelsen på hvert cirkeldiagram repræsenterer numeriske værdier fra et andet felt. |
| **Donutdiagram** | Gengiver sektionsbu buer, der repræsenterer entydige elementer. Længden på hver bue repræsenterer numeriske værdier fra et andet felt. |
| **Kurvediagram** | Afbilder numeriske værdier for en række unikke elementer og forbinder de afbildede værdier |
| **Punktdiagram** | Afbilder numeriske værdier for en række entydige elementer |
| **Områdediagram** | Afbilder numeriske værdier for en række entydige elementer og udfylder sektionerne under de afbildede værdier |

### <a name="construct-queries-for-effective-charts"></a>Oprette forespørgsler til effektive diagrammer
Når du gengiver diagrammer, identificerer avanceret jagt automatisk kolonner af interesse og de numeriske værdier, der skal lægges sammen. Hvis du vil have meningsfulde diagrammer, skal du opbygge dine forespørgsler for at returnere de bestemte værdier, du vil have vist visualiseret. Her er nogle eksempelforespørgsler og de resulterende diagrammer.

#### <a name="alerts-by-severity"></a>Beskeder efter alvorsgrad
Brug operatoren `summarize` til at få et numerisk antal af de værdier, du vil oprette et diagram for. Nedenstående forespørgsel anvender `summarize` operatoren til at få antallet af beskeder efter alvorsgrad.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
Når resultaterne gengives, viser et søjlediagram hver alvorlighedsværdi som en separat kolonne:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="Et eksempel på et diagram, der viser avancerede ræveresultater i Microsoft 365 Defender portal" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*Forespørgselsresultater for beskeder efter alvorsgrad vist som et søjlediagram*


#### <a name="phishing-emails-across-top-ten-sender-domains"></a>Phishingmails på tværs af top ti afsenderdomæner
Hvis du arbejder med en liste over værdier, der ikke er endelige, `Top` kan du kun bruge operatoren til at oprette diagrammer med de fleste forekomster. Hvis du f.eks. vil have de 10 mest populære afsenderdomæner med de fleste phishing-mails, skal du bruge forespørgslen nedenfor:

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
Brug cirkeldiagramvisningen til effektivt at vise distribution på tværs af de øverste domæner:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="Cirkeldiagrammet, der viser avancerede ræveresultater i Microsoft 365 Defender portal" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*Cirkeldiagram, der viser fordelingen af phishingmails på tværs af de mest populære afsenderdomæner*

#### <a name="file-activities-over-time"></a>Filaktiviteter over tid
Med operatoren `summarize` med funktionen `bin()` kan du kontrollere, om der er hændelser med en bestemt indikator over tid. Nedenstående forespørgsel tæller hændelser, der involverer `invoice.doc` filen med 30-minutters intervaller, for at vise samlingerne i aktivitet relateret til den pågældende fil:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
Kurvediagrammet nedenfor fremhæver tydeligt tidsperioder med mere aktivitet, der involverer `invoice.doc`: 

:::image type="content" source="../../media/line-chart-a.png" alt-text="Kurvediagrammet, der viser avancerede ræveresultater i Microsoft 365 Defender portal" lightbox="../../media/line-chart-a.png":::
*Kurvediagram, der viser antallet af hændelser, der involverer en fil over tid*


## <a name="export-tables-and-charts"></a>Eksportér tabeller og diagrammer
Når du har kørt en forespørgsel, skal **du vælge** Eksportér for at gemme resultaterne til en lokal fil. Den valgte visning bestemmer, hvordan resultaterne eksporteres:

- **Tabelvisning** – forespørgselsresultaterne eksporteres i tabelformat som en Microsoft Excel projektmappe
- **Ethvert diagram** – forespørgselsresultaterne eksporteres som et JPEG-billede af det gengivne diagram

## <a name="drill-down-from-query-results"></a>Analysere ned fra forespørgselsresultater
Hvis du hurtigt vil undersøge en post i forespørgselsresultaterne, skal du markere den tilsvarende række for at åbne **panelet Undersøg** post. Panelet indeholder følgende oplysninger baseret på den valgte post:

- **Aktiver** – opsummeret visning af de vigtigste aktiver (postkasser, enheder og brugere), der findes i posten, og som er beriget med tilgængelige oplysninger, f.eks. risiko- og eksponeringsniveauer
- **Alle detaljer** – alle værdierne fra kolonnerne i posten  

:::image type="content" source="../../media/results-inspect-record.png" alt-text="Den valgte post med panel til undersøgelse af posten i Microsoft 365 Defender portal" lightbox="../../media/results-inspect-record.png":::

Hvis du vil have vist flere oplysninger om en bestemt enhed i forespørgselsresultaterne, f.eks. en computer, fil, bruger, IP-adresse eller URL-adresse, skal du vælge enheds-id'en for at åbne en detaljeret profilside for den pågældende enhed.

## <a name="tweak-your-queries-from-the-results"></a>Tilpasse dine forespørgsler fra resultaterne
Vælg de tre prik til højre for en vilkårlig kolonne i panelet **Undersøg** post. Du kan bruge indstillingerne til at:

- Søge eksplicit efter den valgte værdi (`==`)
- Udelade den valgte værdi fra forespørgslen (`!=`)
- Få mere avancerede operatorer til at føje værdien til din forespørgsel, f.eks `contains`. , `starts with`og `ends with` 

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="Ruden Handlingstype på siden Undersøg post i Microsoft 365 Defender portal" lightbox="../../media/work-with-query-tweak-query.png":::



>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige på Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)
