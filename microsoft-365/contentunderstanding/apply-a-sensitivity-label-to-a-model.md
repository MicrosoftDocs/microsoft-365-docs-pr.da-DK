---
title: Anvend et følsomhedsmærkat på en model i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du anvender et følsomhedsmærkat på en model SharePoint Syntex.
ms.openlocfilehash: 624b441084b418d2bcfc3ab6b623da0f5a969fe8
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592434"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>Anvend et følsomhedsmærkat på en model i Microsoft SharePoint Syntex

Du kan nemt anvende et [følsomhedsmærkat til](../compliance/sensitivity-labels.md) at dokumentere modeller i Microsoft SharePoint Syntex. Denne funktion er endnu ikke tilgængelig for modeller til formularbehandling.

Følsomhedsmærkater gør det muligt at anvende kryptering på de dokumenter, som dine modeller identificerer. Du ønsker f.eks., at din model ikke blot identificerer eventuelle økonomiske dokumenter, der indeholder bankkontonumre eller kreditkortnumre, der overføres til dit dokumentbibliotek, men også at anvende en følsomhedsmærkat, der er konfigureret med krypteringsindstillinger, for at begrænse, hvem der kan få adgang til indholdet, og hvordan det kan bruges. SharePoint Syntex-modellerne [overholde](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) reglerne for navnerækkefølgen og overskriver heller ikke en eksisterende etiket, der er blevet anvendt manuelt af en bruger på filen. 

Du kan anvende en eksisterende følsomhedsmærkat til din model via dine modelindstillinger på modellens startside. Etiketten skal allerede være publiceret, for at den kan vælges mellem modelindstillinger.

> [!Important]
> For at følsomhedsmærkater kan anvendes på dine dokumentforståelsesmodeller, skal de oprettes og publiceres [i Microsoft 365 Compliance Center](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>Føj en følsomhedsmærkat til en dokumentforståelsesmodel

1. Fra modellens startside skal du vælge **Modelindstillinger**.

   ![Skærmbillede af siden Modeller med indstillingen Modelindstillinger fremhævet.](../media/content-understanding/sensitivity-model-settings.png)

2. I **ruden Modelindstillinger** skal du i  sektionen Overholdelse vælge menuen Følsomhedsmærkat for at få vist en liste over følsomhedsmærkater, der er tilgængelige for dig at anvende på modellen.

   ![Skærmbillede af ruden Modelindstillinger, der viser menuen med følsomhedsmærkater.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Vælg den følsomhedsmærkat, du vil anvende på modellen, og vælg derefter **Gem**.

Når du anvender følsomhedsmærkatet på din model, kan du anvende den på en:

- Nyt dokumentbibliotek
- Dokumentbibliotek, som modellen allerede er anvendt på
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Anvend følsomhedsmærkatet på et dokumentbibliotek, som modellen allerede er anvendt på

Hvis din dokumentforståelsesmodel allerede er blevet anvendt på et dokumentbibliotek, kan du gøre følgende for at synkronisere din opdatering af følsomhedsmærkaten for at anvende den i dokumentbiblioteket:

1. På modellens startside skal du i sektionen Biblioteker med denne model vælge det dokumentbibliotek, som du vil anvende opdateringen af **følsomhedsmærkatet** til.

2. Vælg **Synkroniser**.

   ![Skærmbillede, der viser biblioteker med denne modelsektion med Synkroniser fremhævet.](../media/content-understanding/sensitivity-libraries-sync.png)

Når du har anvendt opdateringen og synkroniseret den til din model, kan du bekræfte, at den er blevet anvendt, ved at gøre følgende:

1. I indholdscenteret i sektionen **Biblioteker med denne model skal** du vælge det bibliotek, som den opdaterede model blev anvendt på. 

2. I visningen dokumentbibliotek skal du vælge oplysningsikonet for at kontrollere egenskaberne for modellen.

3. Vælg din **opdaterede model** på listen Aktive modeller.

4. I sektionen **Følsomhedsmærkat** kan du se navnet på den anvendte følsomhedsmærkat.

På modellens visningsside i dokumentbiblioteket vises en ny **følsomhedsmærkatkolonne** . Efterhånden som din model klassificerer filer, den identificerer som tilhører dens indholdstype og viser dem i biblioteksvisningen, viser  kolonnen Følsomhedsmærkat også navnet på den følsomhedsmærkat, der er blevet anvendt på den via modellen.

Eksempelvis vil alle finansielle dokumenter, som modellen identificerer, også få krypteringsfølsom følsomhedsmærkatet anvendt på dem, så uautoriserede personer ikke kan få adgang til dem. Hvis en uautoriseret person forsøger at få adgang til filen fra dokumentbiblioteket, vises en fejl, der fortæller, at den ikke er tilladt på grund af den anvendte følsomhedsmærkat.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft 365 Compliance Center](../admin/security-and-compliance/set-up-compliance.md).

You can either apply a sensitivity label to a form processing model when you are creating a model, or apply it to an existing model.

### Add a sensitivity label when you create a form processing model

1. When you [create a new form processing model](create-a-form-processing-model.md), select **Advanced settings**.

2. In **Advanced settings**, in the **Sensitivity label** section, select the menu and then select the sensitivity label you want to apply to the model.

3.  After you've completed your remaining model settings, select **Create** to build your model.

### Add a sensitivity label to an existing form processing model

You can add a sensitivity label to an existing form processing model in different ways:

- Through the **Automate** menu in the document library
- Through the **Active model** settings in the document library 

#### Add a sensitivity label to an existing form processing model through the Automate menu

You can add a sensitivity label to an existing form processing model that you own through the **Automate** menu in the document library in which the model is applied.

1. In your document library to which the form processing model is applied, select the **Automate** menu, select **AI Builder**, and then select **View form processing model details**.

2. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

#### Add a sensitivity label to an existing form processing model in the active model settings

You can add a sensitivity label to an existing form processing model that you own through the **Active model** settings in the document library in which the model is applied.

1. In the SharePoint document library in which the model is applied, select the **View active models** icon, and then select **View active models**.

2. In **Active models**, select the form processing model to which you want to apply the sensitivity label.

3. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

   > [!NOTE]
   > You must be the model owner for the **Model settings** pane to be editable. 
--->

## <a name="see-also"></a>Se også

[Anvend en opbevaringsetiket](apply-a-retention-label-to-a-model.md)

[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
