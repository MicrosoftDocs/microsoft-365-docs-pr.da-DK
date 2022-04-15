---
title: Anvend en opbevaringsmærkat på en model i SharePoint Syntex
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
description: Få mere at vide om, hvordan du anvender en opbevaringsmærkat på en model i SharePoint Syntex.
ms.openlocfilehash: 17bfc0121d18f30b03cc42585cb214b649597ff6
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882500"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>Anvend en opbevaringsmærkat på en model i SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Du kan nemt anvende en [opbevaringsmærkat](../compliance/retention.md) på en model i Microsoft SharePoint Syntex. Du kan gøre dette for både modeller til dokumentforståelse og formularbehandling.

Med opbevaringsmærkater kan du anvende opbevaringsindstillinger på de dokumenter, som dine modeller identificerer.  Din model skal f.eks. ikke kun identificere alle *forsikringsmeddelelsesdokumenter*, der uploades til dokumentbiblioteket, men også anvende et virksomhedsopbevaringsmærke på dem, så disse dokumenter ikke kan slettes fra dokumentbiblioteket i den angivne tidsperiode (f.eks. de næste fem måneder).

Du kan anvende en allerede eksisterende opbevaringsmærkat på din model via dine modelindstillinger på din models startside. 

> [!Important]
> Hvis opbevaringsmærkater skal være tilgængelige, så de kan anvendes på modeller, der forstår dit dokument, skal de [oprettes](../compliance/file-plan-manager.md#create-retention-labels) og [publiceres](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) i Microsoft 365 Overholdelsescenter.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Sådan føjer du en opbevaringsmærkat til en model til dokumentforståelse

1. Vælg **Modelindstillinger** på modellens startside.</br>
2. I **Modelindstillinger** skal du i afsnittet **Sikkerhed og overholdelse** vælge menuen **Opbevaringsmærkat** for at få vist en liste over opbevaringsmærkater, som du kan anvende på modellen.</br>
 ![Menuen Opbevaringsmærkat.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Vælg den opbevaringsmærkat, du vil anvende på modellen, og vælg derefter **Gem**.</br>

Når du har anvendt opbevaringsmærkaten på din model, kan du anvende den på en:
- Nyt dokumentbibliotek
- Det dokumentbibliotek, som modellen allerede er anvendt på
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Anvend opbevaringsmærkaten på et dokumentbibliotek, som modellen allerede er anvendt på

Hvis din model til dokumentforståelse allerede er blevet anvendt på et dokumentbibliotek, kan du gøre følgende for at synkronisere opdateringen af opbevaringsmærkaten for at anvende den på dokumentbiblioteket:</br>

1. På startsiden for din model skal du i afsnittet **Biblioteker med denne model** vælge det dokumentbibliotek, som du vil anvende opdateringen af opbevaringsmærkaten på. </br> 
2. Vælg **Synkroniser**. </br>
 ![Synkroniser model.](../media/content-understanding/sync-model.png)</br> 


Når du har anvendt opdateringen og synkroniseret den med din model, kan du bekræfte, at den er blevet anvendt, ved at gøre følgende:

1. Klik på det bibliotek, som den opdaterede model blev anvendt på, i afsnittet **Biblioteker med denne model** i indholdscentret. </br>
2. Vælg oplysningsikonet i visningen af dokumentbiblioteket for at kontrollere modelegenskaberne.</br>  
3. Vælg din opdaterede model på listen **Aktive modeller** .</br>
4. I afsnittet **Opbevaringsmærkat** kan du se navnet på den anvendte opbevaringsmærkat.</br>


På din models visningsside i dokumentbiblioteket vises der en ny kolonne **med opbevaringsmærkater** .  Når din model klassificerer filer, som de tilhører indholdstypen, og viser dem i biblioteksvisningen, viser kolonnen Opbevaringsmærkat også navnet på den opbevaringsmærkat, der er anvendt på den via modellen.


Alle *forsikringsmeddelelsesdokumenter*, som din model identificerer, vil f.eks. også have mærkaten Forretningsopbevaring anvendt på dem, hvilket forhindrer dem i at blive slettet fra dokumentbiblioteket i fem måneder. Hvis der gøres forsøg på at slette filen fra dokumentbiblioteket, vises der en fejl, hvor der står, at den ikke er tilladt på grund af den anvendte opbevaringsmærkat.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Sådan føjer du en opbevaringsmærkat til en formularbehandlingsmodel

> [!Important]
> Hvis opbevaringsmærkater skal være tilgængelige for din formularbehandlingsmodel, skal de [oprettes](../compliance/file-plan-manager.md#create-retention-labels) og [publiceres](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) i Microsoft 365 Overholdelsescenter.

Du kan enten anvende en opbevaringsmærkat på en formularbehandlingsmodel, når du opretter en model, eller du kan anvende den på en eksisterende model.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Sådan tilføjes en opbevaringsmærkat, når du opretter en formularbehandlingsmodel

1. Når du [opretter en ny formularbehandlingsmodel](./create-a-form-processing-model.md), skal du vælge <b>Avancerede indstillinger.</b>
2. I <b>Avancerede indstillinger</b> skal du i afsnittet <b>Opbevaringsmærkat</b> vælge menuen og derefter vælge den opbevaringsmærkat, du vil anvende på modellen.</b>

 
     ![Føj til en ny formularbehandlingsmodel.](../media/content-understanding/retention-label-forms.png)</br>

3.  Når du har fuldført dine resterende modelindstillinger, skal du vælge <b>Opret</b> for at oprette din model.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Sådan føjer du en opbevaringsmærkat til en eksisterende formularbehandlingsmodel

Du kan føje en opbevaringsmærkat til en eksisterende formularbehandlingsmodel på forskellige måder:
- Via menuen Automate i dokumentbiblioteket
- Via indstillingerne for aktiv model i dokumentbiblioteket 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Sådan føjer du en opbevaringsmærkat til en eksisterende formularbehandlingsmodel via menuen Automate

Du kan føje en opbevaringsmærkat til en eksisterende formularbehandlingsmodel, som du ejer, via menuen Automate i det dokumentbibliotek, hvor modellen anvendes.


1. I det dokumentbibliotek, som modellen til formularbehandling anvendes på, skal du vælge menuen <b>Automatiser</b> , vælge <b>AI Builder</b> og derefter vælge <b>Vis modeloplysninger til formularbehandling</b>.

   ![Automatiser menu.](../media/content-understanding/automate-menu.png)</br>

2. Vælg den opbevaringsmærkat, du vil anvende, i afsnittet <b>Opbevaringsmærkat</b> i modeldetaljerne.  Vælg derefter <b>Gem</b>.

     ![Føj til en eksisterende formularbehandlingsmodel.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Sådan føjer du en opbevaringsmærkat til en eksisterende formularbehandlingsmodel i indstillingerne for den aktive model

Du kan føje en opbevaringsmærkat til en eksisterende formularbehandlingsmodel, som du ejer, via indstillingerne for aktiv model i det dokumentbibliotek, hvor modellen anvendes.

1. I det SharePoint dokumentbibliotek, hvor modellen anvendes, skal du vælge ikonet <b>Få vist aktive modeller</b> og derefter vælge <b>Få vist aktive modeller</b>.</b>

   ![Få vist aktive modeller.](../media/content-understanding/info-du.png)</br> 

2. I <b>Aktive modeller</b> skal du vælge den formularbehandlingsmodel, som du vil anvende opbevaringsmærkaten på.

     ![Modeldetaljer.](../media/content-understanding/retention-label-model-details.png)</br> 


3. Vælg den opbevaringsmærkat, du vil anvende, i afsnittet <b>Opbevaringsmærkat</b> i modeldetaljerne.  Vælg derefter <b>Gem</b>.

> [!NOTE]
> Du skal være modelejer, for at ruden med modelindstillinger kan redigeres. 


## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
