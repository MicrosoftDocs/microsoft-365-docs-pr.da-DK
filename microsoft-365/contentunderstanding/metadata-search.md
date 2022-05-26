---
title: Søg efter metadata i dokumentbiblioteker i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: kkameth
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
description: Få mere at vide om, hvordan du bruger avanceret metadatasøgning og søgning efter brugerdefinerede webstedskolonner til at finde elementer i SharePoint dokumentbiblioteker ved hjælp af SharePoint Syntex.
ms.openlocfilehash: 50b9ef7ff6fe7942266ec59f8d5ad81e0dfbecd4
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679565"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Søg efter metadata i dokumentbiblioteker i Microsoft SharePoint Syntex

Funktionen til søgning efter avancerede metadata i SharePoint Syntex giver dig mulighed for at udføre specifikke metadatabaserede forespørgsler på SharePoint dokumentbiblioteker. Du kan foretage hurtigere og mere præcise forespørgsler baseret på specifikke kolonneværdier for metadata i stedet for blot at søge efter nøgleord.

Avanceret metadatasøgning giver dig mulighed for at bruge de metadata, der er knyttet til et dokument, til at finde filen i et SharePoint dokumentbibliotek. Denne funktion er især nyttig, når du har en bestemt oplysning, du vil søge efter, f.eks. hvornår et dokument senest blev ændret, en bestemt person, der er knyttet til en fil, eller en bestemt filtype.

> [!NOTE]
> Denne funktion er kun tilgængelig for brugere, der har licens til SharePoint Syntex. 

## <a name="to-use-advanced-metadata-search"></a>Sådan bruger du avanceret metadatasøgning

1. Vælg søgeikonet for metadata i et SharePoint dokumentbibliotek i feltet **Søg i dette bibliotek** (![skærmbillede af søgeikonet for metadata).](../media/content-understanding/metadata-search-icon.png)

    ![Skærmbillede af en side i et dokumentbibliotek, der viser søgefeltet med søgeikonet for metadata fremhævet.](../media/content-understanding/metadata-search-box.png)

2. I søgeruden for metadata skal du skrive teksten eller vælge den parameter, du vil finde, i et eller flere af søgefelterne.

    ![Skærmbillede af en side i et dokumentbibliotek, der viser søgeruden for metadata.](../media/content-understanding/metadata-search-pane.png)

   Følgende søgefelter for metadata er tilgængelige i øjeblikket. Der tilføjes flere felter fremover.

   |Feltet    |Brug dette felt til  |
   |---------|---------|
   |Søgeord |Søg efter et strengmatch i metadata eller i fuld tekst i et dokument. |
   |Filnavn     |Søg i kolonnen **Name** i biblioteket.          |
   |Mennesker   |Søg efter et match på personer i en hvilken som helst kolonne i biblioteket.   |
   |Dato for ændring |Søg efter det valgte datointerval i kolonnen **Ændret** i biblioteket.         |
   |Filtype     |Søg efter den valgte filtype (f.eks. Word-dokument eller PDF).        |
   |Indholdstype  |Søg efter den valgte indholdstype. Denne indstilling vises kun, hvis der anvendes en indholdstype, der ikke er standard, på biblioteket. Standardindholdstyper er *dokument* og *mappe*.        |

3. Du kan også søge efter brugerdefinerede webstedskolonner, der findes i den aktuelle biblioteksvisning. Dette er især nyttigt, hvis du har en model, der kører på biblioteket, fordi metadataudtrækningerne automatisk udfylder oplysninger i webstedskolonner.  

    Hvis du vil føje en brugerdefineret webstedskolonne til din søgning, skal du vælge **Tilføj flere indstillinger** og derefter vælge navnet på webstedskolonnen.

    ![Skærmbillede af menuen Tilføj flere indstillinger i søgeruden for metadata.](../media/content-understanding/metadata-search-add-more-options.png)

4. Vælg **Søg**. De dokumenter, der matcher din metadatasøgning, vises på resultatsiden. 
