---
title: Microsoft Produktivitetsscore og mødeindsigt
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
monikerRange: o365-worldwide
search.appverid:
- MET150
- MOE150
description: Detaljer om møderne – personer oplever score for produktivitet.
ms.openlocfilehash: c680a54c2da2b1d49ecb7af234d85741f384fddc
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466410"
---
# <a name="meetings-insights-score--people-experiences"></a>Score for mødeindsigt – personoplevelser

Produktivitetsscore giver indsigt i din organisations digitale transformationsrejse gennem brugen af Microsoft 365 og de teknologioplevelser, der understøtter den. Din organisations score afspejler målingerne af person- og teknologioplevelsen og kan sammenlignes med benchmarks fra organisationer, der svarer til dine. Mødekategorien er en del af de personer, der oplever målinger. Du kan få mere at vide ved at se [oversigten over produktivitetsscore](productivity-score.md) og læse [Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Forudsætninger

Personer i din organisation skal have licens til følgende for at komme i gang med mødeindsigt:

- Microsoft Teams

Du kan få flere oplysninger under [Tildel licenser til brugere](../manage/assign-licenses-to-users.md).

Når personer har været aktive i Teams mindst én gang inden for de sidste 28 dage, kan du begynde at se indsigten.

## <a name="why-your-organizations-meetings-score-matters"></a>Hvorfor scorer din organisations møder?

Møder, hvor folk udforsker ideer, planlægger, løser problemer og træffer beslutninger, er en grundlæggende søjle for organisationens produktivitet. Forskning viser, at når folk bruger værktøjer til onlinemøder effektivt, har de en tendens til at spare op til 104 minutter om ugen.

## <a name="how-we-calculate-the-meetings-score"></a>Sådan beregner vi scoren for møder

Vi giver en primær indsigt i oplevelsen, der indeholder de vigtigste målepunkter for denne kategori. Derefter bruges en resultatstruktur, der er beskrevet nedenfor, til disse målepunkter til at beregne din organisations score.

### <a name="primary-insight"></a>Primær indsigt

Microsoft Teams integrere med Outlook kalender og indeholder en lang række funktioner, der gør dine møder mere engagerende og effektive. Den primære indsigt ser på alle Microsoft Teams onlinemøder, der blev afholdt i din organisation. Den primære indsigt sporer også, hvor mange møder der følger mindst én af de bedste fremgangsmåder for Teams møder.

:::image type="content" source="../../media/primaryinsights-meetings.png" alt-text="PRimary-indsigt i møder med bedste praksis.":::

1. **Header:** Viser procentdelen af onlinemøder på Microsoft Teams, der er afholdt i løbet af de seneste 28 dage, hvor der blev delt video eller skærm under mødet.
2. **Kroppen:** Indeholder flere oplysninger om, hvordan følgende bedste praksis for engagement under et møde, f.eks. brug af video- eller skærmdeling, kan gøre møder mere effektive.
3. **Visualisering (aktuel tilstand):**

      - I dette vandrette liggende søjlediagram repræsenterer den blå (farvede) del den procentdel, der vises i overskriften
      - Brøken (tæller/nævner) bruges til at beregne den procentdel, der vises i overskriften
         - Tæller: Antallet af online Microsoft Teams møder, herunder personer fra din organisation, der har brugt video- eller skærmdeling.
         - Nævner: Antallet af online Microsoft Teams møder, herunder personer fra din organisation, som blev afholdt inden for de sidste 28 dage.
      - Peer benchmark-værdien for nøglemetrikværdien vises også som en procentdel.
1. **Link til ressourcer:** Vælg dette link for at få vist Hjælp-indhold.

#### <a name="trend-visualization-of-the-primary-insight"></a>Tendensvisualisering af den primære indsigt

I følgende diagram vises tendenslinjerne for både tælleren og nævneren for nøglemetrikværdien fra den primære indsigt. Med andre ord viser den antallet af online Microsoft Teams møder med bedste praksis, f.eks. video- eller skærmdeling, og det samlede antal online Microsoft Teams møder, der er afholdt i løbet af de sidste 180 dage. Hvert datapunkt i kurvediagrammet er en samlet aktivitet for de sidste 28 dage.

:::image type="content" source="../../media/number-meeting-over-time.png" alt-text="Diagram, der viser antallet af online Teams møder inden for de seneste 28 dage.":::

### <a name="scoring-framework"></a>Resultatstruktur

Scoren for møder for din organisation måler, i hvor høj grad online Microsoft Teams møder i din organisation har fulgt bedste praksis inden for de seneste 28 dage. Den vægtes på grundlag af antallet af personer i din organisation, der deltager i møderne, og mødernes varighed.

## <a name="explore-more-about-meetings-in-your-organization"></a>Udforsk mere om møder i din organisation

Vi giver dig også supplerende oplysninger, så du kan forstå, hvordan personer i din organisation som aggregeret udfører møder. Disse ekstra målepunkter bidrager ikke direkte til din produktivitetsscore, men kan hjælpe dig med at oprette en handlingsplan som en del af din digitale transformation.

### <a name="breakdown-of-how-many-meetings-follow-best-practices"></a>Opdeling af, hvor mange møder der følger bedste praksis

:::image type="content" source="../../media/videouse-meetings.png" alt-text="Diagram, der viser primær indsigt for møder – personoplevelser.":::

1. **Header:**  Fremhæver procentdelen af online Microsoft Teams møder, der bruger bedste praksisser for videoer, som tages i betragtning i den primære indsigt og score.
2. **Kroppen:** Hrovides oplysninger om værdien af at bruge disse fremgangsmåder under møder for at gøre dem mere engagerende. 
3. **Visualisering:** Opdelingen i visualiseringen er beregnet til at repræsentere det omfang, som online Microsoft Teams møder følger hver af følgende bedste praksisser: 
    - **Video**: Den farvede del og brøken repræsenterer procentdelen af online Microsoft Teams møder, hvor video er slået til. Brøken er oprettet ud fra: 
        - Tæller: Online Microsoft Teams møder, der er afholdt inden for de seneste 28 dage, hvor video fra mindst én deltager er slået til. 
        - Nævner: Det samlede antal online Microsoft Teams møder i din organisation inden for de seneste 28 dage 
    - **Skærmdeling**: Den farvede del og brøken repræsenterer procentdelen af online Microsoft Teams møder, hvor folk brugte funktionen til skærmdeling. Brøken omfatter: 
        - Tæller: Online Microsoft Teams møder, der er afholdt inden for de sidste 28 dage, hvor mindst én deltager delte deres skærm.
        - Nævner: Det samlede antal online Microsoft Teams møder, der er gennemført i din organisation inden for de seneste 28 dage


### <a name="distribution-of-time-spent-by-people-in-meetings"></a>Fordeling af den tid, som personer bruger på møder

:::image type="content" source="../../media/percentageofpeopleusingteams.png" alt-text="Diagram, der viser procentdelen af personer, der deltager i Teams møder i mere end 20 timer om ugen.":::

1. **Header:** Viser procentdelen af personer i din organisation, der deltager i online Microsoft Teams møder i mere end 20 timer om ugen i gennemsnit baseret på deres aktivitet inden for de seneste 28 dage.
2. **Kroppen:** Indeholder oplysninger om værdien af at bruge bedste praksis for møder for at gøre møder engagerede og produktive
3. **Visualisering:** Viser personer i din organisation baseret på den gennemsnitlige tid, de har brugt pr. uge på møder inden for de seneste 28 dage. Følgende oplysninger angives for hver kategori:
      - **Samlet antal mødedeltagere:** Viser antallet af personer i organisationen, der har deltaget i møder, baseret på det gennemsnitlige interval for mødevarighed i løbet af de seneste 28 dage. Kategorien 6-10 timer angiver f.eks. antallet af personer, der deltog i møder i gennemsnitligt så mange timer om ugen inden for de sidste 28 dage.
      - **Deltagere i møder med video:** For hver kategori viser dette, hvor mange personer i din organisation der har været i et møde med video i de sidste 28 dage.
      - **Deltagere i møder med skærmdeling:** For hver kategori viser dette, hvor mange personer der deltog i et møde, der omfattede skærmdeling i de sidste 28 dage.

### <a name="distribution-of-meeting-length-by-type"></a>Distribution af mødelængde efter type

:::image type="content" source="../../media/distribution-meetinglength.png" alt-text="Diagram, der viser distributionen af mødelængder.":::

1. **Header:** Viser procentdelen af øjeblikkelige (ikke tidligere planlagte) online Microsoft Teams møder i løbet af de sidste 28 dage, der er under 30 minutter.
2. **Kroppen:** Indeholder oplysninger om værdien af at bruge øjeblikkelige møder til hurtigt at løse problemer.
3. **Visualisering:** Viser fordelingen af længden (i minutter) af øjeblikkelige og planlagte møder, der fandt sted i din organisation inden for de sidste 28 dage. Distributionen kategoriserer hvert møde i 1-15 minutter, 16-30 minutter, 31-60 minutter og mere end 60 minutter.

    > [!NOTE]
    > de planlagte møder omfatter alle møder, der vises i personers kalendere. De øjeblikkelige møder omfatter opkald, herunder både 1:1 og gruppeopkald, samt møder, der er begyndt at bruge funktionen &quot;Møde nu&quot; i Microsoft Teams kanaler.


### <a name="use-of-different-meeting-types"></a>Brug af forskellige mødetyper

:::image type="content" source="../../media/percentparticipation-meetingtypes.jpg" alt-text="Diagram, der viser procentvis deltagelse i forskellige mødetyper.":::

1. **Header:** Fremhæver procentdelen af øjeblikkelige online Microsoft Teams møder i løbet af de foregående 28 dage, der er mindre end 30 minutter.
2. **Kroppen:** Indeholder oplysninger om værdien af at bruge &quot;Meet nu&quot; i funktionen Microsoft Teams kanal.
3. **Visualisering:** Viser, hvilken type møder personer, der deltager i onlinemøder Microsoft Teams møder. Hver mødetype repræsenteres som en vandret søjle, hvor den farvede del og brøken repræsenterer følgende:
    - **Øjeblikkeligt 1:1-opkald**:
        - Tæller: Antallet af personer, der deltager i 1:1-opkald inden for de seneste 28 dage
        - Nævner: Antallet af personer, der deltager i et online Microsoft Teams møde i de sidste 28 dage
   - **Opkald til øjeblikkelig gruppe**:
        - Tæller: Antallet af personer, der deltager i gruppeopkald inden for de seneste 28 dage
        - Nævner: Antallet af personer, der deltager i et online Microsoft Teams møde i de sidste 28 dage
   - **Øjeblikkeligt møde nu i kanal**:
        - Tæller: Antallet af personer, der bruger &quot;funktionen Møde nu&quot; i Microsoft Teams kanaler (til øjeblikkelige møder) inden for de seneste 28 dage
        - Nævner: Antallet af personer, der deltager i et online Microsoft Teams møde i de sidste 28 dage
    - **Planlagte engangsmøder:**
        - Tæller: Antallet af personer, der deltager i engangsmøder online Microsoft Teams møder i kalenderen (planlagt) inden for de seneste 28 dage
        - Nævner: Antallet af personer, der deltager i et online Microsoft Teams møde i de sidste 28 dage
    - **Planlagte tilbagevendende møder:**
        - Tæller: Antallet af personer, der deltager i forekomster af tilbagevendende møder i deres kalender (planlagt) i de sidste 28 dage
        - Nævner: Antallet af personer, der deltager i et online Microsoft Teams møde i de sidste 28 dage

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 apps – teknologioplevelser](apps-health.md) (artikel)\
[Kommunikation – personoplevelser](communication.md) (artikel)\
[Indholdssamarbejde – personoplevelser](content-collaboration.md) (artikel)\
[Mobilitet – personoplevelser](mobility.md) (artikel)\
[Kontrolelementer til beskyttelse af personlige oplysninger for Produktivitetsscore](privacy.md) (artikel)\
[Teamwork – personoplevelser](teamwork.md) (artikel)
