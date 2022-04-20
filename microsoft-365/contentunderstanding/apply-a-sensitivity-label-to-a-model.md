---
title: Anvend en følsomhedsmærkat på en model i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du anvender en følsomhedsmærkat på en model i SharePoint Syntex.
ms.openlocfilehash: 4ab530fbd4a187f03617b01b6b9661332ad1a7d9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945599"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>Anvend en følsomhedsmærkat på en model i Microsoft SharePoint Syntex

Du kan nemt anvende en [følsomhedsmærkat](../compliance/sensitivity-labels.md) til at dokumentere forståelse af modeller i Microsoft SharePoint Syntex. Denne funktion er endnu ikke tilgængelig for modeller til formularbehandling.

Med følsomhedsmærkater kan du anvende kryptering på de dokumenter, som dine modeller identificerer. Din model skal f.eks. ikke kun identificere finansielle dokumenter, der indeholder bankkontonumre eller kreditkortnumre, der uploades til dit dokumentbibliotek, men også anvende en følsomhedsmærkat, der er konfigureret med krypteringsindstillinger for at begrænse, hvem der har adgang til indholdet, og hvordan det kan bruges. SharePoint Syntex modeller anvender reglerne for [navnerækkefølgen](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) og overskriver heller ikke en eksisterende mærkat, der er anvendt manuelt af en bruger på filen. 

Du kan anvende en allerede eksisterende følsomhedsmærkat på din model via dine modelindstillinger på din models startside. Etiketten skal allerede være publiceret, før den kan vælges fra modelindstillingerne. Mærkater gælder for Office filer til Word (.docx), PowerPoint (.pptx) og Excel (.xlsx). 

> [!Important]
> Hvis følsomhedsmærkater skal være tilgængelige, så de kan anvendes på modeller, der forstår dit dokument, skal de [oprettes og publiceres på Microsoft Purview-overholdelsesportalen](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>Føj en følsomhedsmærkat til en model, der forstår dokumentet

1. Vælg **Modelindstillinger** på modellens startside.

   ![Skærmbillede af siden Modeller med indstillingen Modelindstillinger fremhævet.](../media/content-understanding/sensitivity-model-settings.png)

2. I ruden **Modelindstillinger** i afsnittet **Overholdelse** skal du vælge menuen **Følsomhedsmærkat** for at få vist en liste over følsomhedsmærkater, der er tilgængelige for dig at anvende på modellen.

   ![Skærmbillede af ruden Modelindstillinger, der viser menuen for følsomhedsmærkat.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. Vælg den følsomhedsmærkat, du vil anvende på modellen, og vælg derefter **Gem**.

Når du har anvendt følsomhedsmærkaten på din model, kan du anvende den på en:

- Nyt dokumentbibliotek
- Det dokumentbibliotek, som modellen allerede er anvendt på
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Anvend følsomhedsmærkaten på et dokumentbibliotek, som modellen allerede er anvendt på

Hvis din model til dokumentforståelse allerede er blevet anvendt på et dokumentbibliotek, kan du gøre følgende for at synkronisere opdateringen af følsomhedsmærkaten for at anvende den på dokumentbiblioteket:

1. På modellens startside skal du i afsnittet **Biblioteker med denne model** vælge det dokumentbibliotek, som du vil anvende opdateringen af følsomhedsmærkaten på.

2. Vælg **Synkroniser**.

   ![Skærmbillede, der viser biblioteker med dette modelafsnit med Synkronisering fremhævet.](../media/content-understanding/sensitivity-libraries-sync.png)

Når du har anvendt opdateringen og synkroniseret den med din model, kan du bekræfte, at den er blevet anvendt, ved at gøre følgende:

1. I indholdscentret skal du i afsnittet **Biblioteker med denne model** vælge det bibliotek, som din opdaterede model blev anvendt på. 

2. Vælg oplysningsikonet i visningen af dokumentbiblioteket for at kontrollere modelegenskaberne.

3. Vælg din opdaterede model på listen **Aktive modeller** .

4. I afsnittet **Følsomhedsmærkat** kan du se navnet på den anvendte følsomhedsmærkat.

På modellens visningsside i dokumentbiblioteket vises der en ny kolonne **med følsomhedsmærkater** . Når din model klassificerer filer, den identificerer som tilhører indholdstypen og viser dem i biblioteksvisningen, viser kolonnen **Følsomhedsmærkat** også navnet på den følsomhedsmærkat, der er anvendt på den via modellen.

Alle økonomiske dokumenter, som din model identificerer, vil f.eks. også have mærkaten *Krypteringsfølsomhed* anvendt på dem, hvilket forhindrer uautoriserede personer i at få adgang til dem. Hvis en uautoriseret person forsøger at få adgang til filen fra dokumentbiblioteket, vises der en fejl, hvor der står, at den ikke er tilladt på grund af den anvendte følsomhedsmærkat.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft Purview compliance portal](../admin/security-and-compliance/set-up-compliance.md).

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

[Anvend en opbevaringsmærkat](apply-a-retention-label-to-a-model.md)

[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
