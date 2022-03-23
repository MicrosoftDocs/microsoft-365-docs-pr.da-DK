---
title: Advanced eDiscovery dashboard til korrektursæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug dashboardet Advanced eDiscovery til korrektursæt til hurtigt at analysere dine analyser for at identificere tendenser eller nøglestatistik, der kan hjælpe dig med at udvikle din strategi til gennemsyn.
ms.openlocfilehash: b7bc487e95c2dbae1a65aaad94face6bee19d39b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588766"
---
# <a name="advanced-ediscovery-dashboard-for-review-sets"></a>Advanced eDiscovery dashboard til korrektursæt

I nogle Advanced eDiscovery har du måske en stor mængde dokumenter og mails, der skal gennemgås. Før du starter gennemsynsprocessen, kan det være en god ide hurtigt at analysere dine analyser for at identificere tendenser eller nøglestatistik, der kan hjælpe dig med at udvikle din strategi til gennemsyn. For at gøre dette kan du bruge dashboardet Advanced eDiscovery til korrektursæt til hurtigt at analysere dit korpus.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Trin 1: Opret en widget på dashboardet for korrektursæt

1. I Microsoft 365 Overholdelsescenter skal du gå **til eDiscovery > Advanced eDiscovery** at få vist listen over sager i din organisation.
  
2. Vælg en eksisterende sag.
  
3. Klik på **fanen Gennemse** sæt, og vælg derefter et korrektursæt.
  
4. På **rullelisten Individuelle resultater** skal du klikke på **Søg i profilvisning**. 

   ![DashbordPivot.](../media/dashboardpivot.png)

   Siden **Søgeprofilvisning** vises. Første gang du viser denne side, vises tre standardwidgets.

   ![Dashboard.](../media/dashboardonly.png)
  
5. Klik på **widgetten Ny** , og vælg derefter et af følgende elementer:

   ![Rullelisten Ny widget.](../media/NewWidgetDropdownBox.png)

   - **Vælg mellem biblioteker:** Viser et standardbibliotek med widgets. Du klikker på en widget og klikker derefter **på Tilføj** for at føje den til widgets på **siden Søg i profilvisning** .
  
   - **Opret brugerdefineret widget:** Viser en pop op-side, som du kan bruge til at konfigurere en brugerdefineret widget. 

6. Hvis du vil oprette en brugerdefineret widget, skal du gøre følgende **på pop op-siden Tilføj widget** :

   ![Opret widget.](../media/addwidget.png)

    a. Skriv et navn på widgetten, der vises i widgettitlens titellinje. Det er påkrævet at navngive en widget, men det er nyttigt at identificere widgetdataene.

    b. Vælg en egenskab på **rullelisten Vælg** pivot, der skal bruges til widgetdataene. Elementerne på denne liste er de søgbare egenskaber for elementerne i gennemsynssættet. Du kan finde en beskrivelse af disse egenskaber [under Felter til dokumentmetadata Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md). Pivot-indstillingerne for widgetten er angivet i **kolonnen Søgbare feltnavn** i dette emne.

    c. Vælg en diagramtype for at få vist dataene fra den valgte pivotegenskab.

  6. Klik **på Tilføj** for at oprette den brugerdefinerede widget og vise den på **siden Søgeprofilvisning** .

## <a name="step-2-create-a-review-set-search-query"></a>Trin 2: Opret en søgeforespørgsel med et gennemsynssæt

1. Klik **på ...** i widgettitlen, og klik derefter på **Anvend betingelse**.

   ![Dashboard.](../media/searchprofilehome.png)

2. På pop op-siden skal du klikke på et element på widgetnøglen eller widgetdiagrammet for at oprette et filter.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Gentag trin 1-2 for andre widgets med flere widgets. 

4. Når du er færdig, skal du klikke **på Gem som** forespørgsel for at gemme dine betingelser som en ny søgeforespørgsel til gennemsynssættet.

   ![Forespørgsel.](../media/savequery.png)

5. Luk visningen **Søgeprofil for** at vende tilbage til visningen med søgeresultater.

   Hvis du har oprettet visuelle filtre, anvendes den resulterende forespørgsel på de søgeresultater, der vises, og den søgeforespørgsel, du gemte på trin 4, vises under Gemte **forespørgsler**. Du kan finde flere oplysninger om gennemsynssætforespørgsler [under Forespørge dataene i et gennemsynssæt](review-set-search.md).
