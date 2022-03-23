---
title: Udgiv og opdag modeller i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du gør uddannede modeller tilgængelige for andre, og hvordan du anvender andre oplærte modeller i Microsoft SharePoint Syntex.
ms.openlocfilehash: 9645b669c6fd419e8866d415cb5d2b0da56ab0e2
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/18/2021
ms.locfileid: "63594624"
---
# <a name="publish-and-discover-models-in-microsoft-sharepoint-syntex"></a>Udgiv og opdag modeller i Microsoft SharePoint Syntex

Du kan gøre dine øvede dokumentforståelsesmodeller tilgængelige, så andre kan se og bruge dem direkte SharePoint dokumentbiblioteket. 

Du kan også finde og evaluere uddannede modeller i andre indholdscentre, der er oprettet af andre i organisationen. Vælg den model, der er mest nyttig til klassificering af dine filer eller til at udtrække bestemte oplysninger fra dem. 

> [!NOTE]
> Denne funktion er endnu ikke tilgængelig for modeller til formularbehandling.

## <a name="make-your-model-discoverable-to-others"></a>Gør din model synlig for andre

Sådan gør du din trænede model tilgængelig for andre til brug:

1. På siden **Modeller** til din model skal du vælge **Modelindstillinger**.

2. I panelet **Modelindstillinger** i sektionen Websteder, **hvor denne model er tilgængelig** skal du vælge **Rediger**.

3. På dette tidspunkt vil panelet **Vælg de** websteder, hvor denne model er tilgængelig være forskellig, afhængigt af om du er administrator eller ej. 

    Hvis du er SharePoint administrator, får du vist denne visning.

    ![Skærmbillede af panelet Vælg de websteder, hvor denne model er tilgængelig, der viser indstillingerne for, hvor du ønsker, modellen skal være tilgængelig for andre.](../media/content-understanding/select-sites.png)

    - **Ikke tilgængelig på nogen** websteder – modellen vil ikke være tilgængelig for andre til brug.
    - **Alle websteder** – modellen vil være tilgængelig i galleriet over indholdstyper, så andre kan bruge den.
    - **Kun valgte websteder** – Du kan vælge, hvilket eller hvilke websteder modellen skal være tilgængelige for. Klik i tekstfeltet for at søge efter og vælge de websteder, som modellen skal anvendes på. Du får kun vist websteder, du har adgang til.

    Hvis du ikke *er* SharePoint administrator, får du vist denne visning.

    ![Skærmbillede af panelet Vælg de websteder, hvor denne model er tilgængelig, der viser indstillingerne for slutbrugere med kun nogle få tilgængelige websteder.](../media/content-understanding/select-site-user.png)

    Du kan kun tilføje eller fjerne tilgængeligheden til bestemte websteder, du allerede har adgang til.

4. Vælg de websteder, hvor modellen skal være tilgængelig for andre brugere, og vælg derefter **Gem**.

## <a name="discover-other-trained-models"></a>Opdag andre trænede modeller

Sådan finder du trænede modeller, der kan være egnet til dit indhold:

1. I dokumentbiblioteket til din model skal du vælge **AutomateView** **dokumentforståelsesmodeller** > .

2. På siden **Gennemse modeller og anvend nye** kan du gennemse de anvendte modeller og de modeller, der kan anvendes i dit dokumentbibliotek.

    ![Skærmbillede af siden Gennemse modeller, og anvend nye, der viser fanerne Anvendt og Tilgængelig.](../media/content-understanding/review-models-apply-new-ones.png)

   - På fanen **Anvendt** skal du se de modeller, der er anvendt på dit bibliotek. Vælg **Vis detaljer om model** for at få vist oplysninger om modellen, f.eks. beskrivelse, udtræk og andre indstillinger.
   
   - På fanen **Tilgængelige** skal du se de oplærte modeller, der kan anvendes på dit bibliotek.


### <a name="apply-a-trained-model-to-your-library"></a>Anvend en uddannet model til dit bibliotek

Du kan evaluere trænede modeller i forhold til dit indhold for at hjælpe dig med at finde den mest passende. Sådan vælger du en model, du vil anvende på dit bibliotek:

1. På siden **Gennemse modeller og anvend nye** skal du vælge **fanen Tilgængelig** for at gennemse modellerne på listen.

    ![Skærmbillede af siden Gennemse modeller, og anvend nye, der viser modellerne på fanen Tilgængelige.](../media/content-understanding/available-models-to-apply.png)

2. Vælg den model, du tror vil give dig de bedste resultater, vælg **Vis modeldetaljer**, og vælg derefter **Anvend på bibliotek**.

### <a name="get-a-recommendation-for-a-trained-model"></a>Få en anbefaling til en uddannet model

Hvis du er usikker på, hvilken model der passer bedst til dine filer, kan du bede om en anbefaling. Din anbefaling kan omfatte op til 10 modeller.

1. På siden **Gennemse modeller og anvend nye skal** du vælge **fanen** Tilgængelige.

2. I det første felt skal du vælge **Få anbefaling**.

    ![Skærmbillede af siden Gennemse modeller og anvend nye, der viser indstillingen Få anbefaling på fanen Tilgængelig.](../media/content-understanding/get-recommendation.png)

3. Vælg de **modeller, du synes** passer bedst, på siden Vælg en eller flere modeller til analyse, og vælg derefter **Næste**.

    ![Skærmbillede af siden Vælg en eller flere modeller, der viser de anbefalede modeller med to modeller, der er valgt.](../media/content-understanding/recommendation-results.png)

4. På siden **Vælg en fil, der skal** analyseres skal du vælge en fil af samme eller lignende type, som skal gemmes i dit bibliotek. Vælg derefter **Vælg**.

    ![Skærmbillede af siden Vælg en fil, der skal analyseres, der viser de filer, der er tilgængelige med én fil, der er markeret.](../media/content-understanding/file-to-analyze.png)

5. På siden **Gennemse resultater og vælg en model** under **Vores anbefaling** får du vist den anbefalede fil. Du behøver ikke at anvende den anbefalede model. Du kan vælge at anvende en anden model, hvis du synes, den passer bedre.

    ![Skærmbillede af Resultaterne fra Gennemse, og vælg en modelside, der viser de anbefalede modeller.](../media/content-understanding/review-results.png)

6. For den model, du mener vil give dig de bedste resultater, skal du **vælge Vis detaljer om model** og derefter **vælge Anvend på bibliotek**.

7. Hvis der ikke er nogen anbefalede modeller baseret på den valgte fil, kan du gå tilbage og vælge en anden fil eller vælge forskellige modeller.

### <a name="remove-an-applied-model"></a>Fjern en anvendt model

Sådan fjerner du en anvendt model fra dokumentbiblioteket:

1. På siden **Gennemse modeller og anvend nye** skal du på **fanen Anvendt** se de modeller, der er blevet anvendt på dit bibliotek.

2. På den model, du vil fjerne, skal du **vælge Vis modeldetaljer** og derefter vælge **Fjern fra bibliotek**.


## <a name="see-also"></a>Se også

[Anvend en dokumentforståelsesmodel](apply-a-model.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
