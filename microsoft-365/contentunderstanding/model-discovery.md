---
title: Publicer og find modeller i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du gør oplærte modeller tilgængelige for andre brugere, og hvordan du anvender andre oplærte modeller i Microsoft SharePoint Syntex.
ms.openlocfilehash: 758f6886af6606c57c50c5c4c88e35f7aeeaefe4
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916265"
---
# <a name="publish-and-discover-models-in-microsoft-sharepoint-syntex"></a>Publicer og find modeller i Microsoft SharePoint Syntex

Du kan gøre dine oplærte dokumentforståelsesmodeller tilgængelige, så andre kan få vist og bruge dem direkte fra SharePoint dokumentbibliotek. 

Du kan også finde og evaluere oplærte modeller i andre indholdscentre, der er oprettet af andre i din organisation. Vælg den model, der er mest nyttig til at klassificere dine filer eller udtrække bestemte oplysninger fra dem. 

> [!NOTE]
> Denne funktion er endnu ikke tilgængelig for modeller til formularbehandling.

## <a name="make-your-model-discoverable-to-others"></a>Gør din model tilgængelig for andre

Sådan gør du din oplærte model tilgængelig for andre at bruge:

1. Vælg **Modelindstillinger** på siden **Modeller** for din model.

2. Vælg **Rediger** i afsnittet **Websteder, hvor denne model er tilgængelig** i panelet **Modelindstillinger**.

3. På dette tidspunkt vil panelet **Vælg de websteder, hvor denne model er tilgængelig** , være anderledes, afhængigt af om du er administrator eller ej. 

    Hvis du er SharePoint administrator, får du vist denne visning.

    ![Skærmbillede af panelet Vælg de websteder, hvor denne model er tilgængelig, og som viser indstillingerne for, hvor modellen skal være tilgængelig for andre.](../media/content-understanding/select-sites.png)

    - **Ikke tilgængelig på nogen websteder** – modellen er ikke tilgængelig for andre.
    - **Alle websteder** – modellen er tilgængelig i galleriet med indholdstyper, så andre kan bruge den.
    - **Kun valgte websteder** – Du kan vælge, hvilket eller hvilke websteder modellen skal være tilgængelig på. Klik i tekstfeltet for at søge efter og vælge de websteder, som modellen skal anvendes på. Du kan kun se websteder, som du har adgang til.

    Hvis du *ikke* er SharePoint administrator, får du vist denne visning.

    ![Skærmbillede af panelet Vælg de websteder, hvor denne model er tilgængelig, og som viser indstillingerne for slutbrugere med kun nogle få tilgængelige websteder.](../media/content-understanding/select-site-user.png)

    Du kan kun tilføje eller fjerne tilgængeligheden på de specifikke websteder, som du allerede har adgang til.

4. Vælg de websteder, hvor modellen skal være tilgængelig for andre brugere, og vælg derefter **Gem**.

## <a name="discover-other-trained-models"></a>Opdag andre oplærte modeller

Sådan finder du oplærte modeller, der kan være egnede til dit indhold:

1. I dokumentbiblioteket for din model skal du vælge **AutomateView-modeller** >  til **dokumentforståelse**.

2. På siden **Gennemse modeller og anvend nye** kan du gennemse de anvendte modeller og de modeller, der er tilgængelige for dit dokumentbibliotek.

    ![Skærmbillede af siden Gennemse modeller, og anvend nye, der viser fanerne Anvendt og Tilgængelig.](../media/content-understanding/review-models-apply-new-ones.png)

   - Under fanen **Anvendte** kan du se de modeller, der er anvendt på dit bibliotek. Vælg **Vis modeloplysninger** for at få vist oplysninger om modellen, f.eks. beskrivelse, udtrækninger og andre indstillinger.
   
   - Under fanen **Tilgængelig** kan du se de oplærte modeller, der kan anvendes på dit bibliotek.


### <a name="apply-a-trained-model-to-your-library"></a>Anvend en oplært model på dit bibliotek

Du kan evaluere oplærte modeller i forhold til dit indhold for at hjælpe dig med at finde den mest relevante. Sådan vælger du en model, du vil anvende på dit bibliotek:

1. På siden **Gennemse modeller og anvend nye** skal du vælge fanen **Tilgængelig** for at gennemse modellerne på listen.

    ![Skærmbillede af siden Gennemse modeller, og anvend nye modeller, der viser modellerne under fanen Tilgængelig.](../media/content-understanding/available-models-to-apply.png)

2. Vælg den model, du mener vil give dig de bedste resultater, vælg **Vis modeldetaljer**, og vælg derefter **Anvend på bibliotek**.

### <a name="get-a-recommendation-for-a-trained-model"></a>Få en anbefaling for en oplært model

Hvis du er usikker på, hvilken model der passer bedst til dine filer, kan du bede om en anbefaling. Din anbefaling kan omfatte op til 10 modeller.

1. På siden **Gennemse modeller og anvend nye** skal du vælge fanen **Tilgængelig** .

2. Vælg **Hent anbefaling** i det første felt.

    ![Skærmbillede af siden Gennemse modeller, og anvend nye, der viser indstillingen Hent anbefaling under fanen Tilgængelig.](../media/content-understanding/get-recommendation.png)

3. På siden **Vælg en eller flere modeller til analyse** skal du vælge de modeller, du mener passer bedst til, og derefter vælge **Næste**.

    ![Skærmbillede af siden Vælg en eller flere modeller, der viser de anbefalede modeller med to valgte modeller.](../media/content-understanding/recommendation-results.png)

4. På siden **Vælg en fil, der skal analyseres** skal du vælge en fil af samme eller lignende type, der skal gemmes i biblioteket. Vælg derefter **Vælg**.

    ![Skærmbillede af siden Vælg en fil, der skal analyseres, hvor de filer, der er tilgængelige med én fil valgt, vises.](../media/content-understanding/file-to-analyze.png)

5. På siden **Gennemse resultater og vælg en model** under **Vores anbefaling** kan du se den anbefalede fil. Du behøver ikke at anvende den anbefalede model. Du kan vælge at anvende en anden model, hvis du mener, at den passer bedre.

    ![Skærmbillede af siden Gennemse resultater, og vælg en model, der viser de anbefalede modeller.](../media/content-understanding/review-results.png)

6. For den model, du mener vil give dig de bedste resultater, skal du vælge **Vis modeldetaljer** og derefter vælge **Anvend på bibliotek**.

7. Hvis der ikke er nogen anbefalede modeller, der er baseret på den valgte fil, kan du gå tilbage og vælge en anden fil eller vælge forskellige modeller.

### <a name="remove-an-applied-model"></a>Fjern en anvendt model

Sådan fjerner du en anvendt model fra dokumentbiblioteket:

1. På siden **Gennemse modeller og anvend nye** kan du se de modeller, der er anvendt på dit bibliotek, under fanen **Anvendt** .

2. Vælg **Vis modeldetaljer** i den model, du vil fjerne, og vælg derefter **Fjern fra bibliotek**.


## <a name="see-also"></a>Se også

[Anvend en model til dokumentforståelse](apply-a-model.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
