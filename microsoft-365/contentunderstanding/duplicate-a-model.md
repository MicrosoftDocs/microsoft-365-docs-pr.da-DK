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
description: Få mere at vide om, hvordan og hvorfor dupliker en dokumentforståelsesmodel i Microsoft SharePoint Syntex.
ms.openlocfilehash: 979d5b2cddfa7c565abade7ac66c06e3053bbe4d
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63599347"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>Dupliker en model i Microsoft SharePoint Syntex

Duplikering af en dokumentforståelsesmodel kan spare dig tid og besvær, hvis du har brug for at oprette en ny model og ved, at en eksisterende model minder meget om det, du har brug for.

Eksempelvis klassificerer en eksisterende model med navnet "Kontrakter" de samme filer, du skal arbejde med. Den nye model udtrækker nogle af de eksisterende data, men skal opdateres for at udtrække nogle yderligere data. I stedet for at oprette og træne en ny model fra bunden kan du bruge den duplikerede modelfunktion til at lave en kopi af kontrakter-modellen, som også kopierer alle tilknyttede undervisningselementer, f.eks. filer og enhedsudtræk.

Når du duplikerede modellen, efter du har omdøbt den (f.eks. til "Kontraktfornyelse"), kan du derefter foretage opdateringer af den. Du kan f.eks. vælge at fjerne nogle af de eksisterende udpakkede felter, du ikke har brug for, og derefter træne modellen til at udtrække en ny (f.eks. "Fornyelsesdato").

## <a name="duplicate-a-model"></a>Dupliker en model

Følg disse trin for at duplikere en dokumentforståelsesmodel.

1. I indholdscenteret skal du vælge **Modeller for** at få vist din liste over modeller.

2. Vælg den **model** , du vil duplikere, på siden Modeller.

3. Vælg Dupliker enten ved **hjælp af båndet** eller knappen Vis handlinger (ud for modellens **navn**).</br>

    ![Skærmbillede af siden Modeller, der viser en valgt model med dubletindstillingerne fremhævet.](../media/content-understanding/select-model-duplicate-both.png) </br>

4. På panelet **Dupliker** model:

   a. Under **Navn skal** du skrive det nye navn på den model, du vil duplikere.</br>

    ![Skærmbillede, der viser panelet Dupliker model.](../media/content-understanding/duplicate-model-panel.png) </br>

   b. Tilføj **en** beskrivelse af den nye model under Beskrivelse.

   c. (Valgfrit) Under **Avancerede indstillinger skal** du vælge, om du vil tilknytte en eksisterende [indholdstype](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview).

5. Vælg **Dupliker**.

## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Omdøbe en model](rename-a-model.md)

[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Forklaringstyper](explanation-types-overview.md)

[Anvend en model](apply-a-model.md) 

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)