---
title: Markér dokumenter i et valideringssæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Mærkning af dokumenter i et korrektursæt hjælper med at fjerne unødvendigt indhold og identificere relevant indhold i en eDiscovery(Premium)-sag.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 6130a50c966fe23b1218c98efde381dc64fcb009
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996699"
---
# <a name="tag-documents-in-a-review-set-in-ediscovery-premium"></a>Mærk dokumenter i et korrektursæt i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Det er vigtigt at organisere indhold i et korrektursæt for at fuldføre forskellige arbejdsprocesser i eDiscovery-processen. Dette omfatter:

- Udsortering af unødvendigt indhold

- Identificering af relevant indhold

- Identificering af indhold, der skal gennemses af en ekspert eller advokat

Når eksperter, advokater eller andre brugere gennemser indhold i et anmeldelsessæt, kan deres udtalelser, der er relateret til indholdet, registreres ved hjælp af tags. Hvis hensigten f.eks. er at fjerne unødvendigt indhold, kan en bruger mærke dokumenter med et mærke, f.eks. "ikke-dynamisk". Når indholdet er blevet gennemset og mærket, kan der oprettes en søgning i et gennemsynssæt for at udelade alt indhold, der er mærket som "ikke-dynamisk". Denne proces fjerner det indhold, der ikke svarer, fra de næste trin i eDiscovery-arbejdsprocessen. Taggingpanelet i et korrektursæt kan tilpasses for hver sag, så mærkerne understøtter den tilsigtede arbejdsproces til gennemsyn for sagen.

> [!NOTE]
> Omfanget af mærker er en eDiscovery-sag (Premium). Det betyder, at en sag kun kan have ét sæt mærker, som korrekturlæsere kan bruge til at mærke dokumenter, der er angivet til gennemsyn. Du kan ikke konfigurere et andet sæt mærker til brug i forskellige korrektursæt i samme tilfælde.

## <a name="tag-types"></a>Mærketyper

eDiscovery (Premium) indeholder to typer mærker:

- **Mærker med et enkelt valg**: Begrænser korrekturlæsere til at vælge et enkelt mærke i en gruppe. Disse typer mærker kan være nyttige til at sikre, at korrekturlæsere ikke vælger modstridende mærker, f.eks. "dynamisk" og "ikke-dynamisk". Enkelte valgtags vises som alternativknapper.

- **Flere valgtags**: Tillad, at korrekturer vælger flere mærker i en gruppe. Disse typer mærker vises som afkrydsningsfelter.

## <a name="tag-structure"></a>Kodestruktur

Ud over mærketyperne kan strukturen af, hvordan tags er organiseret i tagpanelet, bruges til at gøre mærkning af dokumenter mere intuitiv. Mærker er grupperet efter sektioner. Gennemsynssætsøgning understøtter muligheden for at søge efter kode og efter kodesektion. Det betyder, at du kan oprette en gennemsynssætsøgning for at hente dokumenter, der er mærket med et hvilket som helst mærke i en sektion.

![Mærkesektioner i kodepanelet.](../media/TagTypes.png)

Du kan organisere mærker yderligere ved at indlejre dem i en sektion. Hvis hensigten f.eks. er at identificere og mærke privilegeret indhold, kan indlejring bruges til at gøre det klart, at en korrekturlæser kan mærke et dokument som "Privilegeret" og vælge rettighedstypen ved at kontrollere det relevante indlejrede tag.

![Indlejrede mærker i en kodesektion.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Oprettelse og anvendelse af mærker

Mærkning af elementer i korrektursæt er en proces med to trin. Det første trin er at oprette de mærker, der derefter anvendes til at gennemse sætelementer. Når du har oprettet mærker, kan du og andre korrekturlæsere anvende dem på elementer i et korrektursæt. Som tidligere forklaret kan en eDiscovery-sag (Premium) kun have ét sæt mærker, som korrekturlæsere kan bruge til at mærke elementer, der er angivet til gennemsyn.

### <a name="create-tags"></a>Opret mærker

Før du anvender mærker på elementer i et korrektursæt, skal du oprette en kodestruktur.

1. Åbn et korrektursæt, gå til kommandolinjen, og vælg **Mærk filer**.

2. På pop **op-siden Mærkefiler** skal du klikke på **Opret/rediger mærker**.

   ![Klik på Opret/rediger mærker på pop op-siden.](../media/CreateAeDTags1.png)

3. På siden **Mærker** skal du vælge **Tilføj sektion**.

4. Skriv en kodegruppetitel og en valgfri beskrivelse, og klik derefter **påGem**.

5. Vælg rullemenuen med tre prikker ud for titlen på mærkegruppen, og klik på **Tilføj afkrydsningsfelt** eller **knappen Tilføj indstilling**.

6. Skriv et navn og en beskrivelse til afkrydsningsfeltet eller alternativknappen.

7. Gentag denne proces for at oprette nye kodesektioner, kodeindstillinger og afkrydsningsfelter. På følgende skærmbillede kan du f.eks. se en kodegruppe med navnet **Review**, som består af afkrydsningsfelterne **Dynamisk** og **Ikke-dynamisk** .

   ![Konfigurer kodestrukturen.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Anvend mærker

Når kodestrukturen er på plads, kan korrekturlæsere anvende mærker på elementer i et korrektursæt ved at konfigurere mærkningsindstillinger.

1. Vælg **Mærkefiler** på kommandolinjen for at få vist pop **op-siden Mærkefiler** (også kaldet *markeringspanelet*).

   ![Klik på Mærk filer på kommandolinjen for at åbne mærkningspanelet.](../media/TagFilesFlyoutPage.png)

2. På pop op-siden **Mærk filer** kan du angive følgende indstillinger for at konfigurere, hvordan elementer, der vises i korrektursættet, mærkes. De filtre eller filterforespørgsler, der aktuelt anvendes på korrektursættet, bestemmer, hvilke elementer der vises, og derfor de elementer, du kan anvende mærker på. Du kan få flere oplysninger under [Forespørg om og filtrer indhold i et anmeldelsessæt](review-set-search.md).

   - **Vælg markering**. Vælg en af følgende indstillinger for at bestemme omfanget af elementer, der skal anvendes mærker på.

      - **Markér markerede elementer**: Denne indstilling anvender mærker på de elementer, du vælger. Du kan vælge elementer før eller efter start af mærkningspanelet. Denne indstilling viser (i realtid) antallet af markerede elementer, der skal mærkes.

      - **Markér alle elementer på listen**: Denne indstilling anvender mærker på alle elementer, der vises i korrektursættet. Denne indstilling viser det samlede antal elementer, der skal mærkes.

   - **Udvid markeringen**: Brug følgende indstillinger til at mærke yderligere elementer, der er relateret til mærkede elementer i korrektursættet.

      - **Medtag tilknyttede familieelementer**: Denne indstilling anvender det samme mærke på de tilknyttede familieelementer for elementer, der er mærket.  *Familieelementer* er elementer, der deler den samme **FamilyId-metadataegenskabsværdi** . Et dokument, der er knyttet til en mail, deler f.eks. det samme **FamilyId** som mailen. Så hvis denne indstilling er valgt til dette eksempel, er mailen og dokumentet mærket, selvom dokumentet muligvis ikke er inkluderet på listen over elementer, der er angivet til gennemsyn.

      - **Medtag tilknyttede samtaleelementer**: Denne indstilling anvender det samme mærke for alle elementer, der er i samme Teams eller Yammer samtale som de elementer, der er mærket. *Samtaleelementer* er elementer, der deler den samme **egenskabsværdi for ConversationId-metadata** . Alle meddelelser, indlæg og tilsvarende transskriptionsfil for en samtale deler det samme **Samtale-id**. Hvis denne indstilling er valgt, mærkes alle elementer i den samme samtale (og transskriptionsfil), selvom nogle af disse samtaleelementer muligvis ikke er inkluderet på listen over elementer, der er angivet til gennemsyn. Du kan finde flere oplysninger om samtaleelementer i afsnittet "Gruppering" i [eDiscovery (Premium)-arbejdsprocessen for indhold i Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Ingen**: Denne indstilling anvender ikke mærker på familieelementer eller samtaleelementer. Den anvender kun mærker på de elementer, der er markeret, eller på alle elementer på listen over korrektursæt.

   > [!NOTE]
   > Hvis du medtager tilknyttede familie- eller samtaleelementer, ændres antallet af elementer, der vises i **mærkede markerede elementer** eller **Mærk alle elementer i listeindstillingerne** , ikke. Det vil sige, at antallet af tilknyttede elementer, der skal mærkes, ikke vises.

   - **Tildel mærker**: I dette afsnit vises de mærker (organiseret efter kodegrupper), som du kan anvende på dokumenter. Du kan kun anvende én enkelt valgkode (identificeret af en alternativknap) pr. kodegruppe. Du kan dog anvende flere mærker med flere valgmuligheder (som identificeres af et afkrydsningsfelt).

3. Klik på **Anvend mærker** for at anvende mærkerne baseret på dine indstillinger.

   Meddelelse om **status for anvendelse af mærker** vises for hver mærkegruppe på mærkningspanelet for at angive, at et mærkningsjob er startet. Mærker for hver kodegruppe i sektionen **Tildel mærker** er nedtonet, indtil jobbet er fuldført.

> [!TIP]
> Hvis du er ved at konfigurere indstillingerne på taggingpanelet, men vil starte forfra, skal du klikke på **Nulstil mærketildeling** for at rydde den aktuelle indstilling. Dette kontrolelement gælder ikke for elementer, der allerede er mærket, og det ændrer eller fjerner ikke mærker fra tidligere mærkede elementer.  

#### <a name="monitor-tagging-jobs"></a>Overvåg markeringsjob

Når du markerer et stort antal elementer (eller vælger indstillingen **Markér alle elementer på listen**), oprettes der et job til **mærkning af dokumenter** . Du kan få vist status for dette job under fanen **Job** i sagen. Dette hjælper dig med at spore store mærkningsjob, der kan tage lang tid at fuldføre. I nogle tilfælde kan et mærkningsjob være fuldført, men statusmeddelelsen **Om anvendelse af mærker** i taggingpanelet vises stadig. Hvis du vil opdatere status for mærkningsjob, skal du klikke på **Opdater** på kommandolinjen gennemse sæt.

## <a name="removing-tags"></a>Fjerner mærker

Du kan fjerne mærker fra elementer i et korrektursæt. Du kan dog ikke fjerne et enkelt valgmærke, der er anvendt på et element, der er angivet for gennemsyn. Du kan kun ændre et enkelt valg-mærke til et andet valg-mærke inden for den samme kodegruppe.

Sådan fjerner du et mærke:

1. Vælg de elementer, du vil fjerne mærket fra.

2. Klik på **Mærkefiler** for at få vist markeringspanelet.

3. Fjern markeringen af mærket under **Tildel mærker**, og klik derefter på **Anvend mærker**.

Du kan også bruge den forrige procedure til at ændre det mærke, der er anvendt på valgte elementer. Når du har fravalgt det aktuelle mærke, kan du vælge et andet.
