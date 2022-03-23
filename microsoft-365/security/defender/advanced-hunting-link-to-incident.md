---
title: Sammenkæde forespørgselsresultater med en hændelse
description: Sammenkæde forespørgselsresultater med en hændelse
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
ms.openlocfilehash: 8a1b8e11d16f0bf0d20739af8ff5699eb150c6f7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593627"
---
# <a name="link-query-results-to-an-incident"></a>Sammenkæde forespørgselsresultater med en hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Med funktionen link til hændelse kan du føje avancerede forespørgselsresultater til en ny eller eksisterende hændelse, der undersøges. Denne funktion hjælper dig med nemt at registrere poster fra avancerede jagtaktiviteter, så du kan oprette en mere omfattende tidslinje eller kontekst for begivenheder vedrørende en hændelse. 

## <a name="link-results-to-new-or-existing-incidents"></a>Sammenkæd resultater med nye eller eksisterende hændelser

1. På siden avanceret forespørgsel skal du først indtaste din forespørgsel i forespørgselsfeltet og derefter vælge **Kør forespørgsel for** at få dine resultater.

    :::image type="content" source="../../media/link-to-incident-1.png" alt-text="Et eksempel på siden **Forespørgsel** i Microsoft 365 Defender portal" lightbox="../../media/link-to-incident-1.png":::

2. På siden Resultater skal du vælge de hændelser eller poster, der er relateret til en ny eller aktuel undersøgelse, du arbejder på, og derefter vælge **Link til hændelse**.

    :::image type="content" source="../../media/link-to-incident-1b.png" alt-text="Indstillingen **Link til hændelse** på fanen **Resultater** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-1b.png":::

3. Find sektionen **Beskeddetaljer** i ruden Link til hændelse, og vælg derefter Opret  ny hændelse for at konvertere hændelserne til beskeder og gruppere dem til en ny hændelse:

    :::image type="content" source="../../media/link-to-incident-3-create-new.png" alt-text="Et eksempel på sektionen **Beskedoplysninger** i ruden **Link til hændelse** i Microsoft 365 Defender portal" lightbox="../../media/link-to-incident-3-create-new.png":::
    
    Eller vælg **Link til en eksisterende hændelse** for at føje de valgte poster til en eksisterende. Vælg den relaterede hændelse på rullelisten over eksisterende hændelser. Du kan også angive de første par tegn i hændelsens navn eller id for at finde den eksisterende hændelse. 

    :::image type="content" source="../../media/link-to-incident-3-link-to-existing.png" alt-text="Et eksempel på sektionen **Beskedoplysninger** i ruden **Link til hændelse** i Microsoft 365 Defender-portalen":::

4. Du kan angive følgende oplysninger i et af valgmulighederne og derefter vælge **Næste**:
      - **Titel for** besked – angiv en beskrivende titel for de resultater, som respondenterne kan forstå. Dette bliver beskedens titel.
      - **Alvorsgrad** – Vælg den alvorlighed, der gælder for gruppen af beskeder.
      - **Kategori** – Vælg den relevante trusselskategori til beskederne.
      - **Beskrivelse** – Giv en nyttig beskrivelse af de grupperede beskeder.
      - **Anbefalede handlinger** – Angiv afhjælpningshandlinger.

5. I sektionen **Berørte enheder skal du** vælge den primære påvirkede eller påvirkede enhed. Kun de relevante enheder, der er baseret på forespørgselsresultaterne, vises i denne sektion. I vores eksempel har vi brugt en forespørgsel til at finde hændelser, der er relateret til en mulig mailudfyldningshændelse, derfor er Afsenderen den påsatte enhed. Hvis der f.eks. er fire forskellige afsendere, oprettes der fire beskeder, som sammenkædes med den valgte hændelse.

     :::image type="content" source="../../media/link-to-incident-4-impacted-entities.png" alt-text="Et eksempel på en påvirket enhed i afsnittet **Link til hændelse** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-4-impacted-entities.png":::

1. Vælg **Næste**.
1. Gennemgå de oplysninger, du har angivet i **sektionen** Oversigt.
     :::image type="content" source="../../media/link-to-incident-5-summary.png" alt-text="Et eksempel på resultatsiden i afsnittet **Link til hændelse** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-5-summary.png":::
     
1. Vælg **Udført**.

## <a name="view-linked-records-in-the-incident"></a>Få vist sammenkædede poster i hændelsen

Du kan vælge navnet på hændelsen for at få vist den hændelse, som hændelserne er knyttet til.
     :::image type="content" source="../../media/link-to-incident-6-incident-pg.png" alt-text="Et eksempel på skærmen med begivenhedsdetaljer på fanen **Oversigt** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-6-incident-pg.png":::

I vores eksempel blev de fire vigtige beskeder, der repræsenterer de fire valgte hændelser, sammenkædet med en ny hændelse. 

På hver af påmindelsessiderne kan du finde alle oplysninger om begivenheden eller hændelserne i tidslinjevisningen (hvis det er tilgængeligt) og visningen med forespørgselsresultater.
     :::image type="content" source="../../media/link-to-incident-7-alert-story.png" alt-text="Et eksempel på alle detaljer om en begivenhed på fanen **Tidslinje** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-7-alert-story.png":::

Du kan også vælge begivenheden for at åbne **ruden Undersøg** post.
:::image type="content" source="../../media/link-to-incident-7-inspect-record.png" alt-text="Et eksempel på undersøg postdetaljerne for en hændelse på fanen **Tidslinje** i Microsoft 365 Defender-portalen" lightbox="../../media/link-to-incident-7-inspect-record.png":::

## <a name="filter-for-events-added-using-advanced-hunting"></a>Filtrer efter begivenheder, der er tilføjet ved hjælp af avanceret jagt
Du kan få vist, hvilke beskeder der blev genereret fra avanceret jagt, ved at filtrere køen Hændelser og beskeder efter kilden **til** manuel registrering.

:::image type="content" source="../../media/link-to-incident-8-filter.png" alt-text="Et eksempel på manuel filtrering af køen hændelser og beskeder på siden **Filtre** i Microsoft 365 Defender portal" lightbox="../../media/link-to-incident-8-filter.png":::
