---
title: Brug en færdigbygget model til at udtrække oplysninger fra fakturaer eller kvitteringer i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du opretter og konfigurerer en færdigbygget model i SharePoint Syntex.
ms.openlocfilehash: f3b262ca94e0bfc6886a2ce84ae614569c584bf1
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738450"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Brug en færdigbygget model til at udtrække oplysninger fra fakturaer eller kvitteringer i Microsoft SharePoint Syntex

Færdigbyggede modeller er forudlært til at genkende dokumenter og strukturerede oplysninger i dokumenterne. I stedet for at skulle oprette en ny brugerdefineret model fra bunden kan du gentage en eksisterende forududdannet model for at tilføje specifikke felter, der passer til organisationens behov. 

Der er i øjeblikket to færdigbyggede modeller tilgængelige: faktura og kvittering.

- Den *færdigbyggede model til faktura* analyserer og udtrækker vigtige oplysninger fra salgsfakturaer. API'en analyserer fakturaer i forskellige formater og [udtrækker vigtige fakturaoplysninger](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) , f.eks. kundenavn, faktureringsadresse, forfaldsdato og skyldigt beløb.

- Den *færdigbyggede kvitteringsmodel* analyserer og udtrækker vigtige oplysninger fra salgskvitteringer. API'en analyserer trykte og håndskrevne kvitteringer og [udtrækker oplysninger om nøglekvittering](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) , f.eks. handelsnavn, handelstelefonnummer, transaktionsdato, skat og transaktionstotal.

Yderligere færdigbyggede modeller vil være tilgængelige i fremtidige versioner.

## <a name="create-a-prebuilt-model"></a>Opret en færdigbygget model

Følg disse trin for at oprette en færdigbygget model for at klassificere dokumenter i SharePoint Syntex.

1. Vælg **Opret en model** på siden **Modeller**.

    ![Skærmbillede af siden Modeller, der viser knappen Opret en model.](../media/content-understanding/prebuilt-create-model-button.png) 

2. Skriv navnet på modellen i feltet **Navn** i panelet **Opret en model**.

    ![Skærmbillede af panelet Nyt dokument med forståelse af model, der viser de tilgængelige modeltyper.](../media/content-understanding/prebuilt-create-panel.png) 

3. Vælg en af de færdigbyggede modeller i afsnittet **Modeltype** :
   - **Færdigbygget fakturabehandling**
   - **Færdigbygget kvitteringsbehandling**

   Hvis du vil oprette en traditionel, utrænet model til dokumentforståelse i stedet for en færdigbygget model, skal du vælge **Forståelse af brugerdefineret dokument**.

4. Hvis du vil ændre indholdstypen eller tilføje en opbevaringsmærkat, skal du vælge **Avancerede indstillinger**.

    > [!NOTE]
    > Følsomhedsmærkater er ikke tilgængelige for færdigbyggede modeller på nuværende tidspunkt.

5. Vælg **Opret**. Modellen gemmes i biblioteket **Modeller** .

## <a name="add-a-file-to-analyze"></a>Tilføj en fil for at analysere

1. Vælg **Tilføj fil** i afsnittet **Tilføj en fil, der skal analyseres** på siden **Modeller**.

    ![Skærmbillede af siden nye modeller, der viser afsnittet Tilføj en fil, der skal analyseres.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. På siden **Filer for at analysere modellen** skal du vælge **Tilføj** for at finde den fil, du vil bruge.

    ![Skærmbillede af siden Filer til at analysere modelsiden, der viser knappen Tilføj.](../media/content-understanding/prebuilt-add-file-button.png) 

3. På siden **Tilføj en fil fra biblioteket med oplæringsfiler** skal du vælge filen og derefter vælge **Tilføj**.

    ![Skærmbillede af siden Tilføj en fil fra bibliotekssiden oplæringsfiler.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. Vælg **Næste** på siden **Filer for at analysere modellen**.

## <a name="select-extractors-for-your-model"></a>Vælg udtrækninger til din model

På siden med oplysninger om udtrækning kan du se dokumentområdet til højre og panelet **Udtræk** til venstre. Panelet **Udtrækninger** viser listen over udtrækninger, der er identificeret i dokumentet.

   ![Skærmbillede af siden med oplysninger om udtrækning og panelet Udtræk.](../media/content-understanding/prebuilt-extractor-details-page.png) 

De objektfelter, der er fremhævet med grønt i dokumentområdet, er de elementer, der blev registreret af modellen, da den analyserede filen. Når du vælger en enhed, der skal udtrækkes, ændres det fremhævede felt til blåt. Hvis du senere beslutter ikke at inkludere objektet, ændres det fremhævede felt til gråt. Fremhævninger gør det nemmere at se den aktuelle tilstand for de udtrækningsmaskiner, du har valgt.

> [!TIP]
> Du kan bruge rullehjulet på musen eller kontrolelementerne nederst i dokumentområdet til at zoome ind eller ud efter behov for at læse enhedsfelterne.

### <a name="select-an-extractor-entity"></a>Vælg en udtrækningsenhed

Du kan vælge en udtrækning enten fra dokumentområdet eller fra panelet **Udtrækninger** , afhængigt af hvad du foretrækker.
 
- Hvis du vil vælge en udtrækning fra dokumentområdet, skal du vælge enhedsfeltet.

    ![Skærmbillede af dokumentområdet, der viser, hvordan du vælger et objektfelt.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Hvis du vil vælge en udtrækning i panelet **Udtrækninger** , skal du markere afkrydsningsfeltet til højre for enhedsnavnet.

    ![Skærmbillede af panelet Udtrækninger, der viser, hvordan du vælger et enhedsfelt.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Når du vælger en udtrækningsmaskine, vises der et **udtræksfelt i** dokumentområdet. I feltet vises udtrækningsnavnet, den oprindelige værdi og muligheden for at vælge den som udtrækningsmaskine. For visse datatyper, f.eks. tal eller datoer, vises der også en udtrukket værdi.

   ![Skærmbillede af feltet Vælg udtrækningsfelt på siden med oplysninger om udtrækning.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Den oprindelige værdi er, hvad der rent faktisk er i dokumentet. Den udtrukne værdi er det, der skrives i kolonnen i SharePoint. Når modellen anvendes på et bibliotek, kan du bruge kolonneformatering til at angive, hvordan den skal se ud i dokumentet.

Fortsæt med at vælge de ekstra udtrækninger, du vil bruge. Du kan også tilføje andre filer for at analysere denne modelkonfiguration.

## <a name="rename-an-extractor"></a>Omdøb en udtrækningsmaskine

Du kan omdøbe en udtrækning enten fra modellens startside eller fra panelet **Udtrækninger** . Du kan overveje at omdøbe valgte udtrækningsmaskiner, fordi disse navne bruges som kolonnenavne, når modellen anvendes på biblioteket.

Sådan omdøber du en udtrækning fra modellens startside:

1. I afsnittet **Udtrækninger** skal du vælge den udtrækningsmaskine, du vil omdøbe, og derefter vælge **Omdøb**.

    ![Skærmbillede af afsnittet Udtrækninger med indstillingen Omdøb fremhævet.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. Angiv det nye navn på udtrækningsenheden i panelet **Omdøb objektudtrækning** , og vælg derefter **Omdøb**.

Sådan omdøber du en **udtrækning fra panelet Udtrækninger** :

1. Vælg den udtrækningsmaskine, du vil omdøbe, og vælg derefter **Omdøb**.

    ![Skærmbillede af panelet Udtrækninger, der viser, hvordan du omdøber en udtrækningsmaskine.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. Angiv det nye navn på **udpakningen i feltet Omdøb udtrækning** , og vælg derefter **Omdøb**.

## <a name="apply-the-model"></a>Anvend modellen

- Hvis du vil gemme ændringer og vende tilbage til modellens startside, skal du vælge **Gem og afslut** i panelet **Udtrækninger**.

- Hvis du er klar til at anvende modellen på et bibliotek, skal du vælge **Næste** i dokumentområdet. På panelet **Føj til bibliotek** skal du vælge det bibliotek, du vil føje modellen til, og derefter vælge **Tilføj**.

## <a name="change-the-view-in-a-document-library"></a>Skift visningen i et dokumentbibliotek

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

