---
title: Omdøb en udtrækningsmaskine i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan og hvorfor du omdøber en udtrækningsmaskine i Microsoft SharePoint Syntex.
ms.openlocfilehash: feba0d8850a534e7f5e5d985bf3424f931e0ceb0
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916155"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>Omdøb en udtrækningsmaskine i Microsoft SharePoint Syntex

På et tidspunkt skal du muligvis omdøbe en udtrækningsmaskine, hvis du vil referere til et udtrukket datafelt med et andet navn. Din organisation beslutter f.eks. at foretage ændringer i sine kontraktdokumenter og henviser til "kunder" som "klienter" i deres dokumenter. Hvis du udtrækker et "Kunde"-felt i din model, kan du vælge at omdøbe det til "Klient".

Når du synkroniserer den opdaterede model med dit SharePoint dokumentbibliotek, får du vist en ny "klient"-kolonne i dokumentbibliotekets visning. Visningen bevarer kolonnen "Kunde" for tidligere aktiviteter, men opdaterer den nye kolonne "Klient" for alle nye dokumenter, der behandles af din model. 

> [!IMPORTANT]
>  Sørg for at synkronisere den opdaterede model med de dokumentbiblioteker, hvor du tidligere har anvendt den, så det nye kolonnenavn vises. 

## <a name="rename-an-extractor"></a>Omdøb en udtrækningsmaskine

Følg disse trin for at omdøbe en objektudtrækning.

1. I indholdscenteret skal du vælge **Modeller** for at få vist listen over modeller.

2. Vælg den model, du vil omdøbe en udtrækning for, i kolonnen **Navn** på siden **Modeller**.

3. Under **Objektudtrækninger** skal du vælge navnet på den udtrækningsenhed, du vil omdøbe, og derefter vælge **Omdøb**.

    ![Skærmbillede af afsnittet Objektudtrækninger, der viser en valgt udtrækningsenhed med indstillingen Omdøb fremhævet.](../media/content-understanding/entity-extractor-rename.png) 

4. På panelet **Omdøb objektudtrækning** :

   a. Under **Nyt navn** skal du angive det nye navn på udpakningen.

    ![Skærmbillede, der viser panelet Objektudtrækning.](../media/content-understanding/rename-entity-extractor-panel.png) 

   b. (Valgfrit) Under **Avancerede indstillinger** skal du vælge, om du vil tilknytte en eksisterende webstedskolonne.

5. Vælg **Omdøb**.

## <a name="see-also"></a>Se også
[Opret en udtrækningsmaskine](create-an-extractor.md)

[Opret en klassificering](create-a-classifier.md)

[Omdøb en model](rename-a-model.md)

[Forklaringstyper](explanation-types-overview.md)

[Udnyt ordbankens taksonomi, når du opretter en udtrækningsfunktion](leverage-term-store-taxonomy.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Anvend en model](apply-a-model.md) 
