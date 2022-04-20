---
title: Importér et eksempel på en model til forståelse af et dokument til Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-get-started
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om dokumentforståelse af modeller via eksempelmodellen.
ms.openlocfilehash: 210d5865a6e3208faff16fe1ce14748ee66d63c8
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916199"
---
# <a name="import-a-sample-document-understanding-model-for-microsoft-sharepoint-syntex"></a>Importér et eksempel på en model til forståelse af et dokument til Microsoft SharePoint Syntex

SharePoint Syntex giver dig en eksempelmodel, som du kan bruge til at undersøge, hvilket giver dig en bedre forståelse af, hvordan du opretter dine egne modeller. Eksempelmodellen giver dig også mulighed for at undersøge modelkomponenter, f.eks. klassificering, udtrækninger og forklaringer. Du kan også bruge eksempelfilerne til at oplære modellen.

## <a name="import-the-sample-model"></a>Importér eksempelmodellen

Hvis du vil have adgang til eksempelmodellen, skal du først importere modellen til dit indholdscenter.

1. I indholdscenteret skal du vælge **Modeller** for at få vist listen over modeller.</br>
2. Vælg **Importér eksempelmodel** på siden **Modeller**.</br>

    ![Importér eksempelmodel.](../media/content-understanding/import-sample-model.png) </br>

3. Når importen er fuldført, åbnes startsiden for modellen **BenefitsChangeNotice** . Hvis du har brug for at åbne eksempelmodellen på et senere tidspunkt, kan du gøre dette fra listen over modeller i indholdscenteret. </br>

     ![Eksempel på startside.](../media/content-understanding/sample-home-page.png)</br>

Du kan ikke kun gennemgå analyse af eksempelmodellen for at få en bedre forståelse af, hvordan modellen er konstrueret, men som en fungerende model kan du gå videre og gøre ting som f.eks.:

- Tilføj en anden udtrækningsmaskine. Du kan f.eks. tilføje en, der udtrækker *rabatgebyret*.
- Anvend modellen på et dokumentbibliotek, og upload nogle af oplæringsfilerne til den for at se, hvordan modellen klassificerer filer og udtrækker data fra dem.

## <a name="get-sample-models"></a>Hent eksempelmodeller

Du kan få adgang til [lageret SharePoint Syntex Eksempler](https://github.com/pnp/syntex-samples), som indeholder communityeksempler, der demonstrerer forskellige brugsmønstre for modeller til dokumentforståelse. Eksemplerne i dette lager indeholder både det dokument, der forstår modelfiler, og de filer, der bruges til at oplære modellen. Når de er importeret, kan du bruge disse modeller til at behandle filer og til at få vist og redigere klassificeringen og udtrækningsmaskinerne.

## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Opret en formularbehandlingsmodel](create-a-form-processing-model.md)  
