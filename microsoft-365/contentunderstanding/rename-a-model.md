---
title: Omdøb en model i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan og hvorfor du omdøber en model til dokumentforståelse i Microsoft SharePoint Syntex.
ms.openlocfilehash: 0044b237705e6a716efb6133db392c68b82c7a25
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916133"
---
# <a name="rename-a-model-in-microsoft-sharepoint-syntex"></a>Omdøb en model i Microsoft SharePoint Syntex

På et tidspunkt kan det være en god idé at omdøbe en model, der forstår dokumentet. Et almindeligt eksempel er, at når du opretter et indledende udkast til en model, har du måske ikke tænkt meget over det endelige navn (du kan f.eks. have kaldt det "AlexWilburModel1"). Når du kommer tættere på at færdiggøre modellen og bruge den, indser du, at et mere korrekt navn ville være "Kontraktfornyelser", og du vil omdøbe den.  

Et andet eksempel er, når din organisation træffer en beslutning om at henvise til en proces- eller dokumenttype med et andet navn. Når du f.eks. har oprettet din model og er klar til at anvende den, kan din organisation give mandat til, at alle "Kontrakter" nu formelt kaldes "Aftaler". Hvis det er nødvendigt, kan du vælge at omdøbe din model fra "Kontraktfornyelser" til "Fornyelse af aftalen".

> [!IMPORTANT]
> Du kan kun omdøbe en model til dokumentforståelse, hvis den ikke er blevet anvendt på et dokumentbibliotek. 

Omdøbning af en model omdøber også den [indholdstype](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) , der er knyttet til modellen.

## <a name="rename-a-model"></a>Omdøb en model

Følg disse trin for at omdøbe en model til dokumentforståelse.

1. I indholdscenteret skal du vælge **Modeller** for at få vist listen over modeller.

2. Vælg den model, du vil omdøbe, på siden **Modeller** .

3. Ved hjælp af båndet eller knappen **Vis handlinger** (ud for modelnavnet) skal du vælge **Omdøb**. </br>

    ![Skærmbillede af siden Modeller, der viser en valgt model med omdøbningsindstillingerne fremhævet.](../media/content-understanding/select-model-rename-both.png) </br>

4. På panelet **Omdøb model** :

   a. Under **Nyt navn** skal du angive det nye navn på den model, du vil omdøbe.</br>

    ![Skærmbillede, der viser panelet Omdøb model.](../media/content-understanding/rename-model-panel.png) </br>

   b. (Valgfrit) Under **Avancerede indstillinger** skal du vælge, om du vil tilknytte en eksisterende [indholdstype](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview). Hvis du vælger **Brug en eksisterende indholdstype**, omdøbes modellen, så den svarer til den valgte indholdstype.

5. Vælg **Omdøb**.

## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Omdøb en udtrækningsmaskine](rename-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Forklaringstyper](explanation-types-overview.md)

[Anvend en model](apply-a-model.md) 
