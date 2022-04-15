---
title: Dupliker en model i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan og hvorfor duplikerer en model til dokumentforståelse i Microsoft SharePoint Syntex.
ms.openlocfilehash: 56e05389cad4ad9010324a3efd48bf679700be76
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882236"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>Dupliker en model i Microsoft SharePoint Syntex

Duplikering af en model til dokumentforståelse kan spare dig tid og kræfter, hvis du har brug for at oprette en ny model, og du skal vide, at en eksisterende model minder meget om det, du har brug for.

En eksisterende model med navnet "Kontrakter" klassificerer f.eks. de samme filer, du skal arbejde med. Din nye model udtrækker nogle af de eksisterende data, men skal opdateres for at udtrække nogle yderligere data. I stedet for at oprette og oplære en ny model fra bunden kan du bruge funktionen duplikerede modeller til at oprette en kopi af modellen Kontrakter, som også kopierer alle tilknyttede oplæringselementer, f.eks. eksempelfiler og objektudtræk.

Når du duplikerer modellen, kan du derefter foretage opdateringer af modellen, når du har omdøbt den (f.eks. til "Kontraktfornyelser"). Du kan f.eks. vælge at fjerne nogle af de eksisterende udtrukne felter, du ikke har brug for, og derefter oplære modellen til at udtrække en ny (f.eks. "Fornyelsesdato").

## <a name="duplicate-a-model"></a>Dupliker en model

Følg disse trin for at duplikere en model til dokumentforståelse.

1. I indholdscenteret skal du vælge **Modeller** for at få vist listen over modeller.

2. Vælg den model, du vil duplikere, på siden **Modeller** .

3. Ved hjælp af båndet eller knappen **Vis handlinger** (ud for modelnavnet) skal du vælge **Dupliker**.</br>

    ![Skærmbillede af siden Modeller, der viser en valgt model med dubletindstillingerne fremhævet.](../media/content-understanding/select-model-duplicate-both.png) </br>

4. På panelet **Dupliker model** :

   a. Angiv det nye navn på den model, du vil duplikere, under **Navn**.</br>

    ![Skærmbillede, der viser panelet Dupliker model.](../media/content-understanding/duplicate-model-panel.png) </br>

   b. Under **Beskrivelse** skal du tilføje en beskrivelse af din nye model.

   c. (Valgfrit) Under **Avancerede indstillinger** skal du vælge, om du vil tilknytte en eksisterende [indholdstype](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview).

5. Vælg **Dupliker**.

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Omdøb en model](rename-a-model.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Forklaringstyper](explanation-types-overview.md)

[Anvend en model](apply-a-model.md) 

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)