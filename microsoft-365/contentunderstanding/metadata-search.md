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
description: Lær at bruge avanceret metadatasøgning og søge efter brugerdefinerede webstedskolonner for at finde elementer i SharePoint ved hjælp af SharePoint Syntex.
ms.openlocfilehash: f010c6944fdcb05fcfe2c254274249b2dcabe99e
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595351"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Søg efter metadata i dokumentbiblioteker i Microsoft SharePoint Syntex

Funktionen avanceret søgning efter metadata i SharePoint Syntex gør det muligt at udføre bestemte metadatabaserede forespørgsler på SharePoint dokumentbiblioteker. Du kan gøre det hurtigere og mere præcise forespørgsler baseret på specifikke kolonneværdier for metadata i stedet for blot at søge efter nøgleord.

Avanceret søgning efter metadata gør det muligt at bruge de metadata, der er knyttet til et dokument, til at finde filen SharePoint et dokumentbibliotek. Denne funktion er især nyttig, når du har en bestemt oplysning, du vil søge efter, f.eks. hvornår et dokument sidst blev ændret, en bestemt person, der er knyttet til en fil, eller en bestemt filtype.

> [!NOTE]
> Denne funktion er kun tilgængelig for brugere, der har licens til SharePoint Syntex. 

## <a name="to-use-advanced-metadata-search"></a>Sådan bruges avanceret metadatasøgning

1. Vælg søgeikonet metadata (skærmbillede ![af metadatasøgeikonet) i feltet Søg i dette bibliotek SharePoint et dokumentbibliotek.](../media/content-understanding/metadata-search-icon.png)

    ![Skærmbillede af en side i et dokumentbibliotek, der viser søgefeltet med søgeikonet for metadata fremhævet.](../media/content-understanding/metadata-search-box.png)

2. Skriv teksten i søgeruden metadata, eller vælg den parameter, du vil søge efter, i et eller flere af søgefelterne.

    ![Skærmbillede af en side i et dokumentbibliotek, der viser søgeruden metadata.](../media/content-understanding/metadata-search-pane.png)

   Følgende metadatasøgefelter er i øjeblikket tilgængelige. Der tilføjes flere felter i fremtiden.

   |Felt    |Brug dette felt til at  |
   |---------|---------|
   |Nøgleord |Søg efter et strengmatch i metadata eller i hele teksten i et dokument. |
   |Filnavn     |Søg i **kolonnen** Navn i biblioteket.          |
   |Personer   |Søg efter match på personer i en vilkårlig kolonne i biblioteket.   |
   |Ændringsdato |Søg efter det valgte datointerval **i kolonnen** Ændret i biblioteket.         |
   |Filtype     |Søg efter den valgte filtype (f.eks. Word-dokument eller PDF).        |
   |Indholdstype  |Søg efter den valgte indholdstype. Denne indstilling vises kun, hvis der er anvendt en ikke-standardindholdstype på biblioteket. Standardindholdstyper er *dokument* og *mappe*.        |

3. Du kan også søge efter brugerdefinerede webstedskolonner, der findes i den aktuelle biblioteksvisning. Dette er især nyttigt, hvis der kører en model på biblioteket, fordi metadataudtrækene automatisk udfylder oplysninger i webstedskolonner.  

    Hvis du vil føje en brugerdefineret webstedskolonne til søgningen, skal du vælge Tilføj flere indstillinger og derefter vælge navnet på webstedskolonnen.

    ![Skærmbillede af menuen Tilføj flere indstillinger i søgeruden metadata.](../media/content-understanding/metadata-search-add-more-options.png)

    > [!NOTE]
    > I øjeblikket er muligheden for at tilføje administrerede metadatafelter eller felter med flere tekstlinjer ikke tilgængelig. 

4. Vælg **Søg**. De dokumenter, der svarer til din metadatasøgning, vises på resultatsiden. 
