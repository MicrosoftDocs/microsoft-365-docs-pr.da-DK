---
title: Tag dokumenter i et korrektursæt
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
description: Mærkning af dokumenter i et korrektursæt hjælper med at fjerne unødvendigt indhold og identificere relevant indhold i Advanced eDiscovery sag.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 43b0bf42bcd94f0bc3ade169ee5b41ee33dcbc5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587506"
---
# <a name="tag-documents-in-a-review-set-in-advanced-ediscovery"></a>Tag dokumenter i et korrektursæt i Advanced eDiscovery

Det er vigtigt at organisere indhold i et gennemsynssæt for at fuldføre forskellige arbejdsprocesser i eDiscovery-processen. Dette omfatter:

- Dette beregner unødvendigt indhold

- Identificere relevant indhold

- Identificere indhold, der skal gennemses af en ekspert eller advokat

When experts, attorneys, or other users review content in a review set, their opinions related to the content can be captured by using tags. Hvis formålet f.eks. er at fjerne unødvendigt indhold, kan en bruger mærke dokumenter med et mærke, f.eks. "ikke-hurtig". Når indhold er blevet gennemgået og mærket, kan der oprettes en søgning i korrektursættet for at udelukke alt indhold, der er mærket som "ikke-hurtig". Denne proces eliminerer det ikke-dynamiske indhold fra de næste trin i eDiscovery-arbejdsprocessen. Mærkningspanelet i et korrektursæt kan tilpasses til alle tilfælde, så mærkerne understøtter den tilsigtede arbejdsproces for gennemsyn af sagen.

> [!NOTE]
> Omfanget af mærker er en Advanced eDiscovery store og små bogstaver. Det betyder, at en sag kun kan have ét sæt mærker, som korrekturlæsere kan bruge til at mærke dokumenter med korrektursæt. Du kan ikke konfigurere et andet sæt mærker til brug i forskellige korrektursæt i samme tilfælde.

## <a name="tag-types"></a>Mærketyper

Advanced eDiscovery indeholder to typer mærker:

- **Enkelte mærker:** Begrænser korrekturlæsere til at vælge et enkelt mærke i en gruppe. Disse typer af mærker kan være nyttige til at sikre, at korrekturlæsere ikke vælger modstridende mærker som f.eks. "hurtig" og "ikke-hurtig". Mærker for enkelte valgmuligheder vises som alternativknapper.

- **Flere mærker:** Tillad anmeldelser at markere flere mærker i en gruppe. Disse typer mærker vises som afkrydsningsfelter.

## <a name="tag-structure"></a>Mærkestruktur

Ud over mærketyperne kan strukturen i, hvordan mærker organiseres i mærkepanelet, bruges til at gøre mærkning af dokumenter mere intuitive. Mærker grupperes efter sektioner. Søgning efter korrektursæt understøtter muligheden for at søge efter mærke og efter mærkesektion. Det betyder, at du kan oprette en søgning i et gennemsynssæt for at hente dokumenter, der er mærket med et hvilket som helst mærke i en sektion.

![Mærke sektioner i mærkepanelet.](../media/TagTypes.png)

Du kan organisere mærker yderligere ved at indlejre dem i en sektion. Hvis formålet f.eks. er at identificere og mærke privilegeret indhold, kan indlejring bruges til at gøre det klart, at en korrekturlæser kan mærke et dokument som "Privilegeret" og vælge typen af rettigheder ved at markere den relevante indlejrede kode.

![Indlejrede mærker i en mærkesektion.](../media/NestingTags.png)

## <a name="creating-and-applying-tags"></a>Oprette og anvende mærker

Mærkning af elementer i korrektursæt er en proces i to trin. Det første trin er at oprette mærker, der derefter anvendes til at gennemse sætelementer. Når du har oprettet mærker, kan du og andre korrekturlæsere anvende dem på elementer i et korrektursæt. Som tidligere beskrevet kan en Advanced eDiscovery kun have ét sæt mærker, som korrekturlæsere kan bruge til at mærke korrektursætelementer.

### <a name="create-tags"></a>Opret mærker

Før du anvender mærker på elementer i et korrektursæt, skal du oprette en mærkestruktur.

1. Åbn et korrektursæt, gå til kommandolinjen, og vælg **Tag filer**.

2. Klik på **Opret/** rediger mærker på pop **op-siden Tag filer**.

   ![Klik på Opret/rediger mærker på pop op-siden.](../media/CreateAeDTags1.png)

3. På siden **Mærker** skal du vælge **Tilføj sektion**.

4. Skriv en kodegruppetitel og en valgfri beskrivelse, og klik derefter **påGem**.

5. Vælg rullemenuen tredobbelt prik ud for kodegruppens titel, og klik **på Tilføj afkrydsningsfelt** eller **knappen Tilføj indstilling**.

6. Skriv et navn og en beskrivelse af afkrydsningsfeltet eller alternativknappen.

7. Gentag denne proces for at oprette nye kodesnit, mærkeindstillinger og afkrydsningsfelter. Følgende skærmbillede viser f.eks. en kodegruppe med navnet **Gennemse, som** består af **afkrydsningsfelterne Responsive** og **Not-responsive** .

   ![Konfigurer kodestruktur.](../media/ManageTagOptions3.png)

### <a name="apply-tags"></a>Anvend mærker

Når mærkestrukturen er på plads, kan korrekturlæsere anvende mærker på elementer i et korrektursæt ved at konfigurere indstillinger for mærkning.

1. På kommandolinjen for korrektursættet skal du **vælge Tag filer** for at få **vist pop** op-siden Med mærker til filer (også *kaldet mærkningspanelet*).

   ![Klik på Mærker filer på kommandolinjen for at åbne mærkningspanelet.](../media/TagFilesFlyoutPage.png)

2. På pop **op-siden** Tag files kan du angive følgende indstillinger for at konfigurere, hvordan du mærker elementer, der vises i korrektursættet. De filtre eller filterforespørgsler, der aktuelt anvendes på korrektursættet, bestemmer, hvilke elementer der vises, og derfor de elementer, du kan anvende mærker på. Få mere at vide under [Forespørg og filtrer indhold i et gennemsynssæt](review-set-search.md).

   - **Vælg markering**. Vælg en af følgende indstillinger for at bestemme omfanget af elementer, der skal anvendes mærker på.

      - **Tilmærke markerede elementer**: Denne indstilling anvender mærker på de elementer, du vælger. Du kan markere elementer før eller efter start af mærkningspanelet. Denne indstilling viser (i realtid) antallet af markerede elementer, der skal mærkes.

      - **Mærke alle elementer på listen**: Denne indstilling anvender mærker på alle elementer, der vises i korrektursættet. Denne indstilling viser det samlede antal elementer, der skal mærkes.

   - **Udvid markeringen**: Brug følgende indstillinger til at mærke andre elementer, der er relateret til mærkede elementer i korrektursættet.

      - **Medtag tilknyttede familieelementer**: Denne indstilling anvender det samme mærke på de tilknyttede familieelementer for elementer, der mærkes.  *Familieelementer er* elementer, der deler den samme **Egenskabsværdi for FamilyId-metadata** . Eksempelvis deler et dokument, der er vedhæftet en mail, det samme **FamilyId** som mailen. Så hvis denne indstilling er valgt i dette eksempel, mærkes mailen og dokumentet, selvom dokumentet muligvis ikke er medtaget på listen over elementer i korrektursættet.

      - **Medtag tilknyttede** samtaleelementer: Denne indstilling anvender det samme mærke på alle elementer, der er i samme Teams eller Yammer samtale som de elementer, der mærkes. *Samtaleelementer er* elementer, der deler den samme **Egenskabsværdi for ConversationId-metadata** . Alle meddelelser, indlæg og tilsvarende afskriftsfil for en samtale deler det samme **ConversationId**. Hvis denne indstilling er valgt, mærkes alle elementer i den samme samtale (og afskriftsfilen), selvom nogle af disse samtaleelementer muligvis ikke er medtaget på listen over gennemsynssætelementer. Du kan finde flere oplysninger om samtaleelementer i afsnittet "[Gruppering" i Advanced eDiscovery for indhold i Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#grouping).

      - **Ingen**: Denne indstilling anvender ikke mærker på familieelementer eller samtaleelementer. Den anvender kun mærker på de elementer, der er markeret, eller på alle elementer på listen over korrektursæt.

   > [!NOTE]
   > Medtagende tilknyttede familie- eller samtaleelementer ændrer ikke antallet af elementer, der vises i Mærket **markerede** elementer eller **Tag alle elementer på listeindstillingerne** . Med andre ord vises antallet af tilknyttede elementer, der mærkes, ikke.

   - **Tildel** mærker: Denne sektion viser de mærker (organiseret efter mærkegrupper), som du kan anvende på dokumenter. Du kan kun anvende ét enkeltvalgsmærke (identificeres ved hjælp af en alternativknap) pr. mærkegruppe. Du kan dog anvende flere mærker med flere valgmuligheder (som identificeres ved hjælp af et afkrydsningsfelt).

3. Klik **på Anvend mærker** for at anvende mærkerne baseret på dine indstillinger.

   **Statusmeddelelsen Anvendelse** af mærker vises for hver mærkegruppe i mærkningspanelet for at angive, at et mærkejob er blevet startet. Mærker for hver mærkegruppe i **sektionen Tildel** mærker er nedtonede, indtil jobbet er fuldført.

> [!TIP]
> Hvis du er i gang med at konfigurere indstillingerne på mærkningspanelet, men vil starte forfra, skal du klikke på Nulstil tildeling af mærker for at fjerne den aktuelle indstilling. Dette kontrolelement gælder ikke for elementer, der allerede er mærket, og det ændrer eller fjerner ikke mærker fra tidligere mærkede elementer.  

#### <a name="monitor-tagging-jobs"></a>Overvåge mærkningsjob

Når du mærker et stort antal elementer (eller vælger indstillingen **Markér** alle elementer på listen), oprettes der et mærke **til** dokumenter. Du får vist status for dette job **under fanen** Jobs i sagen. På den måde kan du spore store mærkningsjob, som kan tage lang tid at gennemføre. I nogle tilfælde kan et mærkejob være færdigt, men **statusmeddelelsen** Anvend mærker i mærkningspanelet vises stadig. Hvis du vil opdatere status for mærkning af job, skal du **klikke på** Opdater på kommandolinjen for korrektursæt.

## <a name="removing-tags"></a>Fjerne mærker

Du kan fjerne mærker fra elementer i et korrektursæt. Du kan dog ikke fjerne et enkeltvalgsmærke, der er blevet anvendt på et gennemsynssætelement. Du kan kun ændre et enkeltvalgsmærke til et andet enkeltvalgsmærke inden for den samme mærkegruppe.

Sådan fjerner du et mærke:

1. Markér de elementer, du vil fjerne mærket fra.

2. Klik **på Tag filer** for at få vist mærkningspanelet.

3. Under **Tildel mærker** skal du fjerne markeringen af mærket og derefter klikke på **Anvend mærker**.

Du kan også bruge den forrige fremgangsmåde til at ændre det mærke, der er anvendt på markerede elementer. Når du har fjernet markeringen af det aktuelle mærke, kan du vælge et andet.
