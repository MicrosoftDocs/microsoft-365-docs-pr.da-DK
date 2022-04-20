---
title: eDiscovery-dashboard (Premium) til gennemsynssæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug Microsoft Purview eDiscovery(Premium)-dashboardet til gennemgangssæt til hurtigt at analysere dit corpus for at identificere tendenser eller vigtige statistikker, der kan hjælpe dig med at udvikle din korrekturstrategi.
ms.openlocfilehash: 1412df381fff228c37052a6d75113c3a4c4cfcba
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995882"
---
# <a name="ediscovery-premium-dashboard-for-review-sets"></a>eDiscovery-dashboard (Premium) til gennemsynssæt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I nogle tilfælde i Microsoft Purview eDiscovery (Premium) kan du have en stor mængde dokumenter og mails, der skal gennemses. Før du starter korrekturprocessen, kan det være en god idé hurtigt at analysere dit corpus for at identificere tendenser eller vigtige statistikker, der kan hjælpe dig med at udvikle din korrekturstrategi. Det gør du ved at bruge eDiscovery(Premium)-dashboardet til gennemgangssæt til hurtigt at analysere dit corpus.

## <a name="step-1-create-a-widget-on-the-review-set-dashboard"></a>Trin 1: Opret en widget på dashboardet til gennemsynssæt

1. På Microsoft Purview-overholdelsesportalen skal du gå til **eDiscovery > eDiscovery (Premium)** for at få vist listen over sager i din organisation.
  
2. Vælg en eksisterende sag.
  
3. Klik på fanen **Gennemse sæt** , og vælg derefter et korrektursæt.
  
4. Klik på **Søgeprofilvisning** på rullelisten **Individuelle resultater**. 

   ![DashbordPivot.](../media/dashboardpivot.png)

   Siden **Søgeprofilvisning** vises. første gang, du får vist denne side, vises der tre standardwidgets.

   ![Dashboard.](../media/dashboardonly.png)
  
5. Klik på **Ny widget** , og vælg derefter et af følgende elementer:

   ![Ny rulleliste til widget.](../media/NewWidgetDropdownBox.png)

   - **Vælg mellem bibliotek:** Viser et standardbibliotek med widgets. Du klikker på en widget og klikker derefter på **Tilføj** for at føje den til widgets på siden **Søgeprofilvisning** .
  
   - **Opret brugerdefineret widget:** Viser en pop op-side, som du kan bruge til at konfigurere en brugerdefineret widget. 

6. Hvis du vil oprette en brugerdefineret widget, skal du gøre følgende på pop op-siden **Tilføj widget** :

   ![Opret widget.](../media/addwidget.png)

    a. Skriv et navn til widgetten, som vises på widgettens titellinje. Det er nødvendigt at navngive en widget, men det er nyttigt at identificere widgetdataene.

    b. Vælg en egenskab på rullelisten **Vælg pivot** , der skal bruges til widgetdataene. Elementerne på denne liste er de egenskaber, der kan søges efter, for elementerne i korrektursættet. Du kan finde en beskrivelse af disse egenskaber [under Dokumentmetadatafelter i eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md). Pivotindstillingerne for widgetten er angivet i kolonnen **Søgbart feltnavn** i dette emne.

    c. Vælg en diagramtype for at få vist dataene fra den valgte pivotegenskab.

  6. Klik på **Tilføj** for at oprette den brugerdefinerede widget og få den vist på siden **Søgeprofilvisning** .

## <a name="step-2-create-a-review-set-search-query"></a>Trin 2: Opret en søgeforespørgsel for et gennemsynssæt

1. Klik på **...** på titellinjen i widgetten, og klik derefter på **Anvend betingelse**.

   ![Dashboard.](../media/searchprofilehome.png)

2. På pop op-siden skal du klikke på et element i widgetnøglen eller widgetdiagrammet for at oprette et filter.

   ![CreateFilter.](../media/applyconditionfilter.png)

3. Gentag trin 1-2 for andre widgets med flere widgets. 

4. Når du er færdig, skal du klikke på **Gem som forespørgsel** for at gemme dine betingelser som en ny søgeforespørgsel for korrektursættet.

   ![Forespørgsel.](../media/savequery.png)

5. Luk **profilvisningen Søg** for at vende tilbage til visningen med søgeresultater.

   Hvis du har oprettet visuelle filtre, anvendes den resulterende forespørgsel på de søgeresultater, der vises, og den søgeforespørgsel, du gemte i trin 4, vises under **Gemte forespørgsler**. Du kan få flere oplysninger om forespørgsler i korrektursæt under [Forespørg om dataene i et korrektursæt](review-set-search.md).
