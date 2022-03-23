---
title: Tidslinje for begivenheder i Håndtering af trusler og sikkerhedsrisici
description: Tidslinje for begivenheder er en risiko nyhedsfeed, der hjælper dig med at fortolke, hvor risikoen introduceres i organisationen, og hvilke afhjælpninger der er sket for at reducere den.
keywords: begivenhedstidslinje, tidslinje for Microsoft Defender til slutpunktshændelse, tidslinje for Microsoft Defender for Endpoint-tvm-begivenhed, Håndtering af trusler og sikkerhedsrisici, Microsoft Defender til Slutpunkt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3fe3139f12b863b54d336e52939ffbb3057df6b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593187"
---
# <a name="event-timeline---threat-and-vulnerability-management"></a>Tidslinje for begivenhed – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Begivenhedstidslinje er en risiko nyhedsfeed, der hjælper dig med at fortolke, hvor risikoen introduceres i organisationen gennem nye sårbarheder eller udnyttelser. Du kan få vist hændelser, der kan påvirke din organisations risiko. Du kan f.eks. finde nye sårbarheder, der blev introduceret, sårbarheder, der blev udnyttet, udnyttelse, der blev føjet til en exploit kit, og meget mere.

Begivenhedstidslinje fortæller også historien om din [eksponeringsscore](tvm-exposure-score.md) [og Microsoft Secure Score for](tvm-microsoft-secure-score-devices.md) enheder, så du kan bestemme årsagen til store ændringer. Begivenheder kan påvirke dine enheder eller dine scorer for enheder. Reducer din eksponering ved at adressere, hvad der skal afhjælpes, baseret på de prioriterede [sikkerhedsanbefalinger](tvm-security-recommendation.md).

> [!TIP]
> Hvis du vil have mails om nye sikkerhedsrisikohændelser, skal [du se Konfigurer mailbeskeder om sikkerhedsrisiko i Microsoft Defender til Endpoint](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-event-timeline-page"></a>Gå til tidslinjesiden for begivenheden

Der er også tre indgangspunkter fra [Håndtering af trusler og sikkerhedsrisici dashboard](tvm-dashboard-insights.md):

- **Scorekort for eksponering i** organisationen: Hold markøren over begivenhedsscore i grafen "Eksponeringsscore over tid", og vælg "Se alle begivenheder fra denne dag". Hændelserne repræsenterer softwarerisici.
- **Microsoft Secure Score til enheder**: Hold markøren over begivenheds prikene i grafen "Dit resultat for enheder over tid", og vælg "Se alle begivenheder fra denne dag". Hændelserne repræsenterer nye konfigurationsvurderinger.
- **Kortet Vigtigste begivenheder**: Vælg "Vis mere" nederst i tabellen over de øverste begivenheder. Kortet viser de tre mest virkningsfulde begivenheder i de seneste 7 dage. Virkningsfulde hændelser kan omfatte, hvis hændelsen påvirker et stort antal enheder, eller hvis det er en kritisk sikkerhedsrisiko.

### <a name="exposure-score-and-microsoft-secure-score-for-devices-graphs"></a>Eksponeringsscore og Microsoft Secure Score for enheder-grafer

I dashboardet Håndtering af trusler og sikkerhedsrisici over eksponeringsscoregrafen for at få vist de vigtigste softwaresikkerhedsrisikohændelser fra den dag, der pådrede dine enheder. Hold markøren over grafen Microsoft Secure Score for Devices for at få vist nye sikkerhedskonfigurationsvurderinger, der påvirker din score.

Hvis der ikke er nogen hændelser, der påvirker dine enheder eller dit resultat for enheder, vises ingen.

![Eksponeringsscore hover.](images/tvm-event-timeline-exposure-score350.png) 
![ Microsoft Secure Score for Devices hover.](images/tvm-event-timeline-device-hover360.png)

### <a name="drill-down-to-events-from-that-day"></a>Analysere ned til begivenheder fra den pågældende dag

Hvis du **vælger Vis alle begivenheder fra denne dag, kommer** du til tidslinjesiden for begivenheden med et brugerdefineret datointerval for den pågældende dag.

![Begivenhedstidslinje valgt brugerdefineret datointerval.](images/tvm-event-timeline-drilldown.png)

Vælg **Brugerdefineret område** for at ændre datointervallet til en anden brugerdefineret eller et forudindstillet tidsinterval.

![Indstillinger for datointerval for begivenhedstidslinje.](images/tvm-event-timeline-dates.png)

## <a name="event-timeline-overview"></a>Oversigt over begivenhedstidslinje

På tidslinjen for begivenheden kan du få vist alle de nødvendige oplysninger, der er relateret til en begivenhed.

Funktioner:

- Tilpas kolonner
- Filtrer efter hændelsestype eller procentdel af på påvirkede enheder
- Vis 30, 50 eller 100 elementer pr. side

De to store tal øverst på siden viser antallet af nye sårbarheder og sårbarheder, der kan udnyttes, ikke begivenheder. Nogle hændelser kan have flere sårbarheder, og nogle sårbarheder kan have flere hændelser.

![Siden med tidslinjen for begivenheder.](images/tvm-event-timeline-overview-mixed-type.png)

### <a name="columns"></a>Kolonner

- **Dato**: måned, dag, år
- **Begivenhed**: virkningsfuld begivenhed, herunder komponent, type og antal på påvirkede enheder
- **Relateret komponent**: software
- **Oprindeligt på påvirkede** enheder: antallet og procentdelen af på påvirkede enheder, da denne hændelse oprindeligt indtraf. Du kan også filtrere efter procentdelen af enheder, der oprindeligt blev påvirket, ud af det samlede antal enheder.
- **Aktuelt på påvirkede** enheder: det aktuelle antal og procentdelen af enheder, som denne hændelse påvirker i øjeblikket. Du kan finde dette felt ved at vælge **Tilpas kolonner**.
- **Typer**: afspejler tidsstemplede hændelser, der påvirker scoren. De kan filtreres.
  - Exploit føjet til en exploit kit
  - Exploit blev bekræftet
  - Ny offentlig udnyttelse
  - Ny sikkerhedsrisiko
  - Ny konfigurationsvurdering
- **Scoretendens**: tendens for eksponeringsscore

### <a name="icons"></a>Ikoner

Følgende ikoner vises ud for begivenheder:

- ![fejlikon.](images/tvm-black-bug-icon.png) Ny offentlig udnyttelse
- ![rapportadvarselsikon.](images/report-warning-icon.png) Ny sikkerhedsrisiko er blevet offentliggjort
- ![exploit kit.](images/bug-lightning-icon2.png) Exploit fundet i exploit kit
- ![fejlikon med advarselsikon.](images/bug-caution-icon2.png) Exploit bekræftet

### <a name="drill-down-to-a-specific-event"></a>Analysere ned til en bestemt begivenhed

Når du har valgt en begivenhed, vises der en pop op-pop op med en liste over de detaljer og aktuelle CV'er, der påvirker dine enheder. Du kan få vist flere CV'er eller få vist den relaterede anbefaling.

Pilen under "scoretendens" hjælper dig med at afgøre, om denne hændelse potentielt kunne hæves eller sænkede din virksomheds eksponeringsscore. Højere eksponeringsscore betyder, at enheder er mere følsomme over for udnyttelse.

![Pop op-pop op-billede for begivenhedstidslinje.](images/tvm-event-timeline-flyout500.png)

Derfra skal du vælge **Gå til relateret sikkerhedsanbefaling** for at se den anbefaling, der adresserer den nye softwaresikkerhedsrisiko på [siden med sikkerhedsanbefalinger](tvm-security-recommendation.md). Når du har læst beskrivelsen og oplysningerne om sikkerhedsrisikoen i sikkerhedsanbefalingerne, kan du sende en afhjælpningsanmodning og spore anmodningen på [afhjælpningssiden](tvm-remediation.md).

## <a name="view-event-timelines-in-software-pages"></a>Få vist tidslinjer for begivenheder på softwaresider

Hvis du vil åbne en softwareside, skal du vælge en begivenhed > vælge softwarenavnet med linket (f.eks. Visual Studio 2017) i afsnittet "Relateret komponent" i pop op-pop-op-pop-programmet. [Få mere at vide om softwaresider](tvm-software-inventory.md#software-pages)

Der vises en hel side med alle oplysningerne om en bestemt software. Hold musen over grafen for at se tidslinjen for begivenheder for den pågældende software.

![Softwareside med en graf over begivenhedstidslinje.](images/tvm-event-timeline-software2.png)

Gå til fanen med tidslinjen for begivenheden for at få vist alle de hændelser, der er relateret til den pågældende software. Du kan også se sikkerhedsanbefalinger, opdaget sårbarheder, installerede enheder og versionsfordeling.

![Softwareside med tidslinjefanen Begivenhed.](images/tvm-event-timeline-software-pages.png)

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Afhjælpe sårbarheder](tvm-remediation.md)
- [Lager over software](tvm-software-inventory.md)
