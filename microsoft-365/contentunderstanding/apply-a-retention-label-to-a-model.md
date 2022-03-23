---
title: Anvend et opbevaringsnavn på en model i SharePoint Syntex
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
description: Få mere at vide om, hvordan du anvender et opbevaringsnavn på en model SharePoint Syntex.
ms.openlocfilehash: 112b48af5e07d09faab61bd656c5629b449d9a1c
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63591036"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>Anvend et opbevaringsnavn på en model i SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Du kan nemt anvende et [opbevaringsnavn](../compliance/retention.md) på en model i Microsoft SharePoint Syntex. Du kan gøre dette for både dokumentforståelses- og formularbehandlingsmodeller.

Opbevaringsnavne gør det muligt at anvende opbevaringsindstillinger på de dokumenter, som modellerne identificerer.  Du vil f.eks. gerne have, at modellen ikke  blot identificerer eventuelle forsikringsmeddelelsesdokumenter, der overføres til dokumentbiblioteket, men også anvende et *firmaopbevaringsmærke* på dem, så disse dokumenter ikke kan slettes fra dokumentbiblioteket i den angivne periode (f.eks. de næste fem måneder).

Du kan anvende en eksisterende opbevaringsetiket til modellen via dine modelindstillinger på modellens startside. 

> [!Important]
> For at opbevaringsmærkater kan anvendes på dine dokumentforståelsesmodeller, skal [](../compliance/file-plan-manager.md#create-retention-labels) de oprettes og publiceres i Microsoft 365 Overholdelsescenter.[](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels)

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Sådan føjer du en opbevaringsetiket til en dokumentforståelsesmodel

1. Fra modellens startside skal du vælge **Modelindstillinger**.</br>
2. I **Modelindstillinger skal** du i  sektionen Sikkerhed og overholdelse vælge menuen Opbevaringsetiket for at få vist en liste over opbevaringsnavne, der er tilgængelige for din til at anvende modellen.</br>
 ![Menuen Opbevaringsnavn.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Vælg den opbevaringsmærkat, du vil anvende på modellen, og vælg derefter **Gem**.</br>

Når du har anvendt opbevaringsmærkaten på modellen, kan du anvende den på en:
- Nyt dokumentbibliotek
- Dokumentbibliotek, som modellen allerede er anvendt på
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Anvend opbevaringsmærkaten på et dokumentbibliotek, som modellen allerede er anvendt på

Hvis din dokumentforståelsesmodel allerede er blevet anvendt på et dokumentbibliotek, kan du gøre følgende for at synkronisere opdateringen af din opbevaringsetiket for at anvende den i dokumentbiblioteket:</br>

1. På **modellens** startside skal du i sektionen Biblioteker med denne model vælge det dokumentbibliotek, som du vil anvende opdateringen af opbevaringsetiketten på. </br> 
2. Vælg **Synkroniser**. </br>
 ![Synkroniseringsmodel.](../media/content-understanding/sync-model.png)</br> 


Når du har anvendt opdateringen og synkroniseret den med din model, kan du bekræfte, at den er blevet anvendt, ved at gøre følgende:

1. I indholdscenteret i sektionen **Biblioteker med denne model** skal du klikke på det bibliotek, som den opdaterede model blev anvendt på. </br>
2. I visningen dokumentbibliotek skal du vælge oplysningsikonet for at kontrollere egenskaberne for modellen.</br>  
3. Vælg din **opdaterede model** på listen Aktive modeller.</br>
4. I sektionen **Opbevaringsmærkat** kan du se navnet på den anvendte opbevaringsmærkat.</br>


På modellens visningsside i dokumentbiblioteket vises en ny **opbevaringsmærkatkolonne** .  Efterhånden som modellen klassificerer filer, som den identificerer som tilhører dens indholdstype, og viser dem i biblioteksvisningen, viser kolonnen Opbevaringsnavn også navnet på det opbevaringsnavn, der er blevet anvendt på det via modellen.


Alle forsikringsmeddelelsesdokumenter, som modellen identificerer, vil f.eks. også  få forretningsopbevaringsmærkatet anvendt på dem, hvilket forhindrer dem i at blive slettet fra dokumentbiblioteket i fem måneder. Hvis der gøres forsøg på at slette filen fra dokumentbiblioteket, vises der en fejl, der fortæller, at den ikke er tilladt på grund af den anvendte opbevaringsetiket.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Sådan føjer du et opbevaringsnavn til en formularbehandlingsmodel

> [!Important]
> For at opbevaringsnavne kan anvendes på din formularbehandlingsmodel, skal de oprettes og [](../compliance/file-plan-manager.md#create-retention-labels) [publiceres](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) i Microsoft 365 Overholdelsescenter.

Du kan enten anvende et opbevaringsnavn på en formularbehandlingsmodel, når du opretter en model, eller du kan anvende den på en eksisterende model.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Sådan tilføjer du et opbevaringsnavn, når du opretter en formularbehandlingsmodel

1. Når du opretter [en ny formularbehandlingsmodel, skal](./create-a-form-processing-model.md) du vælge <b>Avancerede indstillinger.</b>
2. Vælg <b>menuen i</b> sektionen Opbevaringsnavn <b>i</b> Avancerede indstillinger, og vælg derefter den opbevaringsetiket, du vil anvende på modellen.</b>

 
     ![Føj til en ny formularbehandlingsmodel.](../media/content-understanding/retention-label-forms.png)</br>

3.  Når du har fuldført dine resterende modelindstillinger, skal du vælge <b>Opret for</b> at opbygge din model.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Sådan føjer du et opbevaringsnavn til en eksisterende formularbehandlingsmodel

Du kan føje et opbevaringsnavn til en eksisterende formularbehandlingsmodel på forskellige måder:
- Via menuen Automatiser i dokumentbiblioteket
- Via indstillingerne for aktive modeller i dokumentbiblioteket 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Sådan føjer du et opbevaringsnavn til en eksisterende formularbehandlingsmodel via menuen Automatiser

Du kan føje et opbevaringsnavn til en eksisterende formularbehandlingsmodel, som du ejer via menuen Automatiser i det dokumentbibliotek, hvor modellen anvendes.


1. I det dokumentbibliotek, som formularbehandlingsmodellen er anvendt på, skal du vælge menuen <b>Automatiser</b> , vælge <b>AI Builder</b> og derefter vælge <b>Vis detaljer om formularbehandlingsmodel</b>.

   ![Menuen Automatiser.](../media/content-understanding/automate-menu.png)</br>

2. Vælg den opbevaringsmærkat, du <b>vil anvende</b> , i sektionen Opbevaringsnavn i modeldetaljerne.  Vælg derefter <b>Gem</b>.

     ![Føj til en eksisterende formularbehandlingsmodel.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Sådan føjer du et opbevaringsnavn til en eksisterende formularbehandlingsmodel i indstillingerne for den aktive model

Du kan føje et opbevaringsnavn til en eksisterende formularbehandlingsmodel, som du ejer via indstillingerne for aktive modeller i det dokumentbibliotek, hvor modellen anvendes.

1. I SharePoint dokumentbibliotek, hvor modellen er anvendt, skal du vælge <b>ikonet</b> Vis aktive modeller og derefter vælge <b>Vis aktive modeller</b>.</b>

   ![Få vist aktive modeller.](../media/content-understanding/info-du.png)</br> 

2. I <b>Aktive modeller</b> skal du vælge den formularbehandlingsmodel, som opbevaringsnavnet skal anvendes på.

     ![Modeldetaljer.](../media/content-understanding/retention-label-model-details.png)</br> 


3. Vælg den opbevaringsmærkat, du <b>vil anvende</b> , i sektionen Opbevaringsnavn i modeldetaljerne.  Vælg derefter <b>Gem</b>.

> [!NOTE]
> Du skal være modelejer for, at ruden Modelindstillinger kan redigeres. 


## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
