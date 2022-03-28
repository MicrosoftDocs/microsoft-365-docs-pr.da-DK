---
title: Omdøb en extractor i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan og hvorfor du skal omdøbe en extractor i Microsoft SharePoint Syntex.
ms.openlocfilehash: 850359f71e7ca08b16265f93741ab2498e87d032
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63597868"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>Omdøb en extractor i Microsoft SharePoint Syntex

På et tidspunkt kan det være nødvendigt at omdøbe en extractor, hvis du vil referere til et udpakket datafelt med et andet navn. Din organisation beslutter f.eks. at foretage ændringer i deres kontraktdokumenter og refererer til "kunder" som "kunder" i deres dokumenter. Hvis du udtrækker et felt af "Kunde" i din model, kan du vælge at omdøbe det til "Klient".

Når du synkroniserer din opdaterede model med dit SharePoint dokumentbibliotek, får du vist en ny kolonne med "Klient" i visningen af dokumentbiblioteket. Din visning bevarer kolonnen "Kunde" for tidligere aktivitet, men opdaterer den nye kolonne "Klient" for alle nye dokumenter, der behandles af modellen. 

> [!IMPORTANT]
>  Sørg for at synkronisere den opdaterede model til de dokumentbiblioteker, hvor du tidligere har anvendt den, for at det nye kolonnenavn blev vist. 

## <a name="rename-an-extractor"></a>Omdøbe en extractor

Følg disse trin for at omdøbe en enhedsudtrækning.

1. I indholdscenteret skal du vælge **Modeller for** at få vist din liste over modeller.

2. Vælg **den model** , du vil **omdøbe** en extractor for, i kolonnen Navn på siden Modeller.

3. Under **Enhedsudtrækere** skal du vælge navnet på den extractor, du vil omdøbe, og derefter vælge **Omdøb**.

    ![Skærmbillede af afsnittet Enhedsudtrækere, der viser en valgt extractor med indstillingen Omdøb fremhævet.](../media/content-understanding/entity-extractor-rename.png) 

4. På panelet **Omdøb enhedsudtræk** :

   a. Under **Nyt navn** skal du skrive det nye navn til extractoren.

    ![Skærmbillede, der viser Enhedsudtrækspanelet.](../media/content-understanding/rename-entity-extractor-panel.png) 

   b. (Valgfrit) Under **Avancerede indstillinger skal** du vælge, om du vil tilknytte en eksisterende webstedskolonne.

5. Vælg **Omdøb**.

## <a name="see-also"></a>Se også
[Opret en extractor](create-an-extractor.md)

[Opret en klassificering](create-a-classifier.md)

[Omdøbe en model](rename-a-model.md)

[Forklaringstyper](explanation-types-overview.md)

[Brug term store-taksonomi ved oprettelse af en extractor](leverage-term-store-taxonomy.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Anvend en model](apply-a-model.md) 
