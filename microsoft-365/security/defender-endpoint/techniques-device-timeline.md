---
title: Teknikker på enhedens tidslinje
description: Forstå enhedens tidslinje i Microsoft Defender for Endpoint
keywords: enhedens tidslinje, slutpunkt, MITRE, MITRE ATT&CK, teknikker, taktik
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d724b7663bd4484c630e97362eb5766490e1fa8e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465899"
---
# <a name="techniques-in-the-device-timeline"></a>Teknikker på enhedens tidslinje

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan få mere indsigt i en undersøgelse ved at analysere de hændelser, der er sket på en bestemt enhed. Først skal du vælge den enhed, der har interesse, [på listen Enheder](machines-view-overview.md). På enhedssiden kan du vælge fanen Tidslinje for **at** få vist alle de hændelser, der er opstået på enheden.

## <a name="understand-techniques-in-the-timeline"></a>Forstå teknikker på tidslinjen

> [!IMPORTANT]
> Nogle oplysninger relaterer til en allerede udgivet produktfunktion i offentlig prøveversion, som kan være væsentligt ændret, før den frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

I Microsoft Defender for Endpoint er **Techniques** en yderligere datatype i begivenhedstidslinjen. Teknikker giver mere indsigt i aktiviteter, der er knyttet [til MITRE ATT&CK-teknikker](https://attack.mitre.org/) eller underteknikker.

Denne funktion forenkler undersøgelsesoplevelsen ved at hjælpe analytikere med at forstå de aktiviteter, der er blevet observeret på en enhed. Analytikere kan derefter beslutte at undersøge yderligere.

For offentlig forhåndsvisning er Teknikker tilgængelige som standard og vises sammen med begivenheder, når en enheds tidslinje vises.

:::image type="content" source="images/device-timeline-2.png" alt-text="Teknikkerne på enhedens tidslinje" lightbox="images/device-timeline-2.png":::

Teknikker fremhæves med fed tekst og vises med et blåt ikon til venstre. Den tilsvarende MITRE ATT&CK-id og det tilhørende tekniknavn vises også som mærker under Yderligere oplysninger.

Indstillingerne Søg og Eksportér er også tilgængelige for teknikker.

## <a name="investigate-using-the-side-pane"></a>Undersøg ved hjælp af sideruden

Vælg en teknik for at åbne den tilhørende siderude. Her kan du se yderligere oplysninger og indsigter som f.eks. relateret att&ck-teknikker, -taktikker og -beskrivelser.

Vælg den specifikke *Angrebsteknik for* at åbne den relaterede ATT&CK-teknikside, hvor du kan finde flere oplysninger om den.

Du kan kopiere oplysninger om en enhed, når du ser et blåt ikon til højre. Hvis du f.eks. vil kopiere en relateret fils SHA1, skal du vælge det blå sideikon.

:::image type="content" source="images/techniques-side-pane-clickable.png" alt-text="Oplysninger om at kopiere enhed" lightbox="images/techniques-side-pane-clickable.png":::

Du kan gøre det samme for kommandolinjer.

:::image type="content" source="images/techniques-side-pane-command.png" alt-text="Muligheden for at kopiere kommandolinjen" lightbox="images/techniques-side-pane-command.png":::

## <a name="investigate-related-events"></a>Undersøg relaterede hændelser

Hvis du vil [bruge avanceret jagt](advanced-hunting-overview.md) til at finde begivenheder, der er relateret til den valgte teknik, **skal du vælge Søg efter relaterede begivenheder**. Dette fører til den avancerede jagtside med en forespørgsel for at finde begivenheder, der er relateret til Teknik.

:::image type="content" source="images/techniques-hunt-for-related-events.png" alt-text="Indstillingen Lede efter relaterede begivenheder" lightbox="images/techniques-hunt-for-related-events.png":::

> [!NOTE]
> Forespørgsel ved hjælp af **knappen** Søg efter relaterede hændelser fra sideruden Teknik viser alle de hændelser, der er relateret til den identificerede metode, men inkluderer ikke selve teknik i forespørgselsresultaterne.

## <a name="customize-your-device-timeline"></a>Tilpas din enheds tidslinje

I øverste højre side af enhedens tidslinje kan du vælge et datointerval for at begrænse antallet af begivenheder og teknikker på tidslinjen.

Du kan tilpasse, hvilke kolonner der skal vises. Du kan også filtrere efter markerede begivenheder efter datatype eller efter begivenhedsgruppe.

### <a name="choose-columns-to-expose"></a>Vælg kolonner at vise

Du kan vælge, hvilke kolonner der skal vises på tidslinjen, ved at **vælge knappen Vælg** kolonner.

:::image type="content" source="images/filter-customize-columns.png" alt-text="Den rude, hvor du kan tilpasse kolonner" lightbox="images/filter-customize-columns.png":::


Derfra kan du vælge, hvilke oplysninger der skal medtages.

### <a name="filter-to-view-techniques-or-events-only"></a>Filtrer for kun at få vist teknikker eller hændelser

Hvis du kun vil have vist enten begivenheder eller teknikker, skal **du vælge Filtre** fra enhedens tidslinje og vælge den foretrukne Datatype, du vil have vist.

:::image type="content" source="images/device-timeline-filters.png" alt-text="Ruden Filtre" lightbox="images/device-timeline-filters.png":::

## <a name="see-also"></a>Se også

- [Få vist og organiser listen Enheder](machines-view-overview.md)
- [Microsoft Defender for Endpoint med flag til tidslinje på enheden](device-timeline-event-flag.md)
