---
title: Microsoft Produktivitet Scor indholdssamarbejdsindsigt
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
description: Detaljer om indholdssamarbejdet – personer oplever produktivitetsscore.
ms.openlocfilehash: db747819b4c6a6599d1d7919c2a36f34204779a1
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466432"
---
# <a name="content-collaboration--people-experiences"></a>Indholdssamarbejde – personoplevelser

Produktivitetsscore giver indsigt i din organisations digitale transformationsrejse gennem brugen af Microsoft 365 og de teknologioplevelser, der understøtter den. Din organisations score afspejler målingerne af person- og teknologioplevelsen og kan sammenlignes med benchmarks fra organisationer, der svarer til dine. Kategorien indholdssamarbejde er en del af de personer, der oplever målinger. Du kan få mere at vide ved at se [oversigten over produktivitetsscore](productivity-score.md) og læse [Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Forudsætninger

For at komme i gang med indsigt i indholdssamarbejde skal personer i din organisation have licens til:

- OneDrive for Business
- SharePoint
- Exchange Online

Du kan få flere oplysninger under [Tildel licenser til brugere](../manage/assign-licenses-to-users.md).

 Når personer har været aktive i ovenstående produkter mindst én gang inden for de sidste 28 dage, begynder du at se indsigten.

## <a name="why-your-organization39s-content-collaboration-score-matters"></a>Hvorfor din organisation&#39;vigtige resultater for samarbejde om indhold

Et vigtigt aspekt ved digital transformation er, hvordan personer samarbejder i filer. Med dit indhold på Microsoft 365 får andre adgang til, opretter, redigerer og samarbejder om indhold med andre personer fra en hvilken som helst placering. Undersøgelser viser, at når folk samarbejder med onlinefiler, sparer hver person i gennemsnit 100 minutter om ugen.

## <a name="how-we-calculate-the-content-collaboration-score"></a>Sådan beregner vi scoren for indholdssamarbejde

Vi giver en primær indsigt, der indeholder de vigtigste målepunkter for indholdssamarbejde i din organisation. Derefter bruges en scorestruktur, der er beskrevet nedenfor, til disse målepunkter til at beregne din organisations score.

> [!NOTE]
> Den 22. april 2021 ændrede vi, hvordan metrikværdien for samarbejdspartnere beregnes. Dette påvirker den [primære indsigt](#primary-insight), [filsamarbejdets indsigt](#number-of-files-collaborated-on) og den måde, scoren for indholdssamarbejde måles på. Denne ændring hjælper med at reducere støj i data fra ikke-menneskelige agenter (eller robotter) fra Microsoft og andre tredjepartsprogrammer, hvilket resulterer i en mere præcis og handlingsorienteret score.

### <a name="primary-insight"></a>Primær indsigt

Microsoft OneDrive for Business og SharePoint hjælpe brugerne med nemt at oprette, læse og finde deres individuelle og delte indhold i Microsoft 365 fra alle enheder og programmer. De giver også brugerne mulighed for sikkert at dele og samarbejde om indhold. Den primære indsigt indeholder oplysninger fra alle, der kan bruge OneDrive for Business og SharePoint. Derudover opdeles oplysningerne om, hvor mange personer der læser, opretter og samarbejder om indhold, der er gemt i OneDrive for Business og SharePoint.

:::image type="content" source="../../media/collabscore_primary.jpg" alt-text="Primær indsigt fra score for kommunikationssamarbejde.":::


Typer, der overvejes til disse oplysninger, omfatter Word-, Excel-, PowerPoint-, OneNote- og PDF-filer.

1. **Header:** Viser procentdelen af personer i din organisation, der har adgang til OneDrive eller SharePoint, der samarbejder om indhold.
2. **Kroppen:** Indeholder flere oplysninger om, hvordan funktionsmåden ved at læse og oprette filer online er kædet sammen med samarbejde om filer.
3. **Visualisering (aktuel tilstand):**
    - Vandrette streger, hvor de blåfarvede dele repræsenterer procentdelen af personer, der er aktiveret til filsamarbejde, via OneDrive eller SharePoint, der har været **læsere, oprettere** eller **samarbejdspartnere** på onlinefiler inden for de seneste 28 dage.

        De defineres på følgende måde:</br>
        **Læsere:** Personer, der får adgang til eller downloader onlinefiler i OneDrive eller SharePoint.</br>
        **Skaberne:** Personer, der opretter, redigerer, uploader, synkroniserer, tjekker ind, kopierer eller flytter online OneDrive eller SharePoint filer.</br>
        **Samarbejdspartnere:** Personer, der samarbejder med onlinefiler ved hjælp af OneDrive eller SharePoint. To personer er samarbejdspartnere, hvis den ene af dem læser eller redigerer en online-Office-app eller PDF, efter at den anden person har oprettet eller ændret den inden for et 28-dages vindue.

        > [!NOTE]
        > De filer, der tages i betragtning i visualiseringen, er Word-, Excel-, PowerPoint-, OneNote- eller PDF-filer, der er online og gemt i OneDrive eller SharePoint. 

    - Fremhævning (tæller/nævner) af brøken bruges til at beregne procentdelen udtrykt i hver af de vandrette søjler.
    
      - **Læsere:**</br>
          - Tæller: Antal personer, der har adgang til eller downloader onlinefiler i OneDrive eller SharePoint inden for de seneste 28 dage</br>
          - Nævner: Antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage</br>
      - **Skaberne:**</br>
        - Tæller: Antal personer, der opretter, ændrer, uploader, synkroniserer, tjekker ind, kopierer eller flytter onlinefiler inden for OneDrive eller SharePoint inden for de seneste 28 dage</br>
        - Nævner: Antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage. </br> 
      - **Samarbejdspartnere:**</br>
        - Tæller: Antal personer, der har samarbejdet om onlinefiler i OneDrive eller SharePoint inden for de seneste 28 dage</br>
        - Nævner: Antal personer, der har haft adgang til i OneDrive eller SharePoint i mindst 1 af de sidste 28 dage

    - Peer benchmark-værdi for hver af læsere, oprettere og samarbejdspartnere vises også som en procentdel. Med andre ord vises værdien af antallet af oprettere som en procentdel af antallet af personer, der har adgang til OneDrive eller SharePoint.
    
1. **Link til ressourcer:** Vælg dette link for at få vist sorterede videoer og andet relateret hjælpindhold.


#### <a name="trend-visualization-of-primary-insight"></a>Trendvisualisering af primær indsigt

Diagrammet over tendensvisualiseringer viser tendenslinjen for de primære indsigtsmålepunkter for læsere, oprettere og samarbejdspartnere i løbet af de sidste 180 dage. Hvert datapunkt i diagrammet er en samlet aktivitet for de sidste 28 dage. Hvert opretterdatapunkt indeholder en optælling af alle personer, der er mærket som oprettere inden for de sidste 28 dage for hver dato på x-aksen.

:::image type="content" source="../../media/trendvisualization.jpg" alt-text="Diagram med tendenser for at få primær indsigt i samarbejdet.":::

### <a name="scoring-framework"></a>Resultatstruktur

Scoren for samarbejde om indhold for din organisation måler på aggregeret niveau (organisation), uanset om personer konsekvent læser, opretter eller samarbejder om online Office filer, f.eks. Word, Excel, PowerPoint, OneNote eller PDF-filer eller i OneDrive eller SharePoint.

Scorer er ikke angivet på individuelt brugerniveau.

## <a name="explore-how-your-organization-collaborates"></a>Udforsk, hvordan din organisation samarbejder

Vi giver dig også oplysninger, der hjælper dig med at få indblik i, hvordan din organisation samarbejder om indhold. Disse ekstra målepunkter bidrager ikke direkte til din produktivitetsscore, men hjælper dig med at oprette en handlingsplan som en del af din digitale transformation for at hjælpe med at optimere den måde, folk arbejder på.

### <a name="creating-files-in-onedrive-or-sharepoint"></a>Oprettelse af filer i OneDrive eller SharePoint

:::image type="content" source="../../media/sharepointonedrivefiles.jpg" alt-text="Diagram, der viser antallet af personer, der opretter filer i OneDrive eller SharePoint.":::

1. **Header:** Fremhæver procentdelen af personer, der er aktive i Microsoft 365 Office programmer, som opretter filer på OneDrive eller SharePoint.
2. **Kroppen:** Indeholder oplysninger om værdien af oprettelse af indhold i OneDrive og SharePoint.
3. **Visualisering:** Opdelingen i visualiseringen repræsenterer i hvor høj grad, de personer, der bruger Microsoft Office apps til at oprette filer i OneDrive og SharePoint, på følgende måde:
      - **OneDrive:** Den blå (farvede) del af linjen og brøken på linjen repræsenterer procentdelen af personer, der er aktive i Office programmer, der opretter indhold på OneDrive på følgende måde:
        - Tæller: Antallet af personer, der opretter, ændrer, uploader, synkroniserer, tjekker ind, kopierer eller flytter online Office filer i OneDrive inden for de seneste 28 dage.</br>
        - Nævner: Antallet af personer, der har adgang til OneDrive eller SharePoint og få adgang til Office-filer inden for de seneste 28 dage.
      - **SharePoint:** Den blå (farvede) del af linjen og brøken på linjen repræsenterer procentdelen af personer, der er aktive i Office programmer, og opretter indhold på SharePoint som:</br>
         - Tæller: Antallet af personer, der opretter, ændrer, uploader, synkroniserer, tjekker ind, kopierer eller flytter online Office filer (Microsoft Word, Excel, PowerPoint eller OneNote filer) på SharePoint inden for de seneste 28 dage.</br>
        - Nævner: Antallet af personer, der har adgang til OneDrive eller SharePoint, og som har fået adgang til Office filer inden for de seneste 28 dage.

4. **Link til ressourcer:** Vælg dette link for at få vist Hjælp-indhold.

### <a name="use-of-attachments-in-email"></a>Brug af vedhæftede filer i mail

**Brug af vedhæftede filer i mail** Forstå, hvor mange brugere der vedhæfter fysiske filer i en mail i stedet for links til indhold i skyen, og overvåg reduktionen af dette antal over tid.

:::image type="content" source="../../media/emailattachments.png" alt-text="Brug af vedhæftede filer i mails.":::

1. **Header:** Fremhæver procentdelen af personer, der bruger vedhæftede filer i mails, som ikke blev gemt i onlinefiler.
2. **Kroppen:** Indeholder oplysninger om værdien af at dele links til onlinefiler fra et samarbejds- og sikkerhedsperspektiv.
3. **Visualisering:** Opdelingen i visualiseringen er beregnet til at repræsentere det omfang, som personer, der vedhæfter indhold i mails, bruger forskellige tilstande (filer, der ikke er gemt i onlinefiler, links til onlinefiler):
      - **Vedhæft filer:** Den blå (farvede) del af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af personer, der bruger vedhæftede filer i mails.
        - Tæller: Antallet af personer, der vedhæfter filer til en mail, som ikke blev gemt i onlinefilen inden for de sidste 28 dage.
        - Nævner: Antallet af personer, der har haft adgang til Exchange og OneDrive, SharePoint eller begge inden for de sidste 28 dage.
      - **Links til onlinefiler:** Den blå (farvede) del af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af personer, der bruger vedhæftede filer, og vedhæfter links til filer i mails.
        - Tæller: Antallet af personer, der vedhæfter links til onlinefiler til mails inden for de sidste 28 dage.
        - Nævner: Antallet af personer, der har adgang til Exchange og OneDrive, SharePoint eller begge inden for de sidste 28 dage.
4. **Link til ressourcer:** Vælg dette link for at få vist Hjælp-indhold.

### <a name="sharing-of-online-files"></a>Deling af onlinefiler

:::image type="content" source="../../media/sharingonlinefiles.png" alt-text="Diagram, der viser antallet af personer, der deler filer online.":::

1. **Header:** Fremhæver procentdelen af personer, der har adgang til for OneDrive eller SharePoint, der deler filer eksternt.
2. **Kroppen:** Indeholder oplysninger om administratorerne&#39; mulighed for at ændre indstillingerne for fildeling i organisationen for at muliggøre det samarbejdsniveau, der passer bedst til din organisation.
3. **Visualisering:** Repræsenterer det omfang, som personer, der har adgang til OneDrive eller SharePoint, deler filer internt eller eksternt:
      - **Eksternt:** Den blå (farvede) del af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af personer, der har adgang til OneDrive eller SharePoint og deler filer eksternt.
        -  Tæller: Antallet af personer, der har delt filer eksternt med inden for de seneste 28 dage
        - Nævner: Det samlede antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
      - **Kun internt:** Den blå (farvede) del af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af personer, der har adgang til OneDrive eller SharePoint og kun deler filer internt.
        - Tæller: Antallet af personer, der kun har delt filer internt inden for de seneste 28 dage
        - Nævner: Det samlede antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
4. **Link til ressourcer:** Vælg dette link for at få vist Hjælp-indhold.

### <a name="number-of-files-collaborated-on"></a>Antal filer, der samarbejdes om

:::image type="content" source="../../media/intensityofcollab.png" alt-text="Diagram, der viser, hvor mange filer der blev samarbejdet mest om.":::

1. **Header:** Fremhæver procentdelen af personer, der har adgang til OneDrive eller SharePoint, der samarbejder om 4 eller flere filer.
2. **Kroppen:** Indeholder oplysninger om, hvordan folk kan udnytte onlinefiler til bedre samarbejde.
3. **Visualisering:** Viser en distribution af de personer, der har adgang til OneDrive eller SharePoint, baseret på det antal filer, de samarbejder om. Dette vises via følgende 4 kategorier (for hver enkelt repræsenterer den blå del af linjen og brøken procentdelen af personer, der har adgang til OneDrive eller SharePoint, der falder inden for den pågældende kategori):
      - **Intet samarbejde:**
        - Tæller: Antallet af personer, der ikke samarbejder om nogen filer inden for de seneste 28 dage.
        - Nævner: Det samlede antal personer, der har adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
      - **Samarbejde om 1-3 filer:**
        - Tæller: Antallet af personer, der samarbejder om 1-3 filer inden for de seneste 28 dage.
        - Nævner: Det samlede antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
      - **Samarbejde om 4-10 filer:**
        - Tæller: Antallet af personer, der samarbejder om 4-10 filer inden for de sidste 28 dage.
        - Nævner: Det samlede antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
      - **Samarbejde om 11 eller flere filer:**
        - Tæller: Antallet af personer, der samarbejder om 11 eller flere filer inden for de seneste 28 dage.
        - Nævner: Det samlede antal personer, der har haft adgang til OneDrive eller SharePoint i mindst 1 af de sidste 28 dage.
        
4. **Link til ressourcer:** Vælg dette link for at få vist Hjælp-indhold.

### <a name="network-performance-strength-for-onedrive-and-sharepoint"></a>Netværksydeevne for OneDrive og SharePoint

:::image type="content" source="../../media/networkperfstrength.png" alt-text="Diagram, der viser netværkets ydeevne for OneDrive og SharePoint.":::

1. **Header:** Fremhæver procentdelen af de enheder, der er testet, og som har dårlig netværksforbindelse til OneDrive og SharePoint. 
2. **Kroppen:** Indeholder oplysninger om, hvorfor netværksforbindelsens ydeevne er vigtig for samarbejde. 
3. **Visualisering:** Viser en procentdel af enheder med forskellige niveauer af netværksforbindelsesydeevne, der er relateret til OneDrive og SharePoint:
      - **81-100 (bedst)**: Den mørkegrønne (farvede) del af linjen repræsenterer procentdelen af enheder med den bedste ydeevne.
      - **61-80**: Den grønne (farvede) del af linjen repræsenterer procentdelen af enheder med en score for netværkets ydeevne mellem 60-80. 
      - **41-60**: Den orange (farvede) del af linjen repræsenterer procentdelen af enheder med en score for netværkets ydeevne mellem 40-60. 
      - **21-40**: Den røde (farvede) del af linjen repræsenterer procentdelen af enheder med en score for netværkets ydeevne mellem 20-40. 
      - **0-20**: Den mørkerøde (farvede) del af linjen repræsenterer procentdelen af enheder med den værste score for netværkets ydeevne mellem 0 og 20. 

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 apps – teknologioplevelser](apps-health.md) (artikel)\
[Kommunikation – personoplevelser](communication.md) (artikel)\
[Møder – personoplevelser](meetings.md) (artikel)\
[Mobilitet – personoplevelser](mobility.md) (artikel)\
[Kontrolelementer til beskyttelse af personlige oplysninger for Produktivitetsscore](privacy.md) (artikel)\
[Teamwork – personoplevelser](teamwork.md) (artikel)
