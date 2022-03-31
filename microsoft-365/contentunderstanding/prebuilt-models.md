---
title: Brug en færdigpakket model til at udtrække oplysninger fra fakturaer eller kvitteringer i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du opretter og konfigurerer en færdigbyggende model SharePoint Syntex.
ms.openlocfilehash: 7867fe197fd53e6095f51869fc5aaad18af9157b
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63601032"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-sharepoint-syntex"></a>Brug en færdigpakket model til at udtrække oplysninger fra fakturaer eller kvitteringer i Microsoft SharePoint Syntex

Indbyggede modeller er indbyggede til at genkende dokumenter og de strukturerede oplysninger i dokumenterne. I stedet for at skulle oprette en ny brugerdefineret model fra bunden kan du bruge en eksisterende foruddefineret model til at tilføje bestemte felter, der passer til organisationens behov. 

Der findes i øjeblikket to indbyggede modeller: faktura og kvittering.

- *Fakturamodellen analyserer og* udtrækker vigtige oplysninger fra salgsfakturaer. API'en analyserer fakturaer i forskellige formater og [](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) udtrækker vigtige fakturaoplysninger som f.eks. kundenavn, faktureringsadresse, forfaldsdato og forfaldsdato.

- Den *indbyggede model for kvitteringer* analyserer og henter vigtige oplysninger fra salgskvitteringerne. API'en analyserer udskrevne og håndskrevne kvitteringer og henter oplysninger om nøglekvittering, f.eks. sælgernavn, forhandlertelefonnummer, transaktionsdato, moms og [transaktionstotal](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) .

Yderligere færdigbuilte modeller bliver tilgængelige i fremtidige versioner.

## <a name="create-a-prebuilt-model"></a>Opret en færdigbuilt model

Følg disse trin for at oprette en færdigbyggende model til at klassificere dokumenter SharePoint Syntex.

1. Vælg **Opret en** model på **siden Modeller**.

    ![Skærmbillede af siden Modeller, der viser knappen Opret en model.](../media/content-understanding/prebuilt-create-model-button.png) 

2. Skriv **navnet på** modellen i **feltet Navn** i panelet Opret en model.

    ![Skærmbillede af panelet Nyt dokument med forståelse af model, der viser de tilgængelige modeltyper.](../media/content-understanding/prebuilt-create-panel.png) 

3. Vælg en af de indbyggede modeller i sektionen **Modeltype** :
   - **Fakturabehandling er færdigbuilt**
   - **Behandling af kvitteringer i forbehandling**

   Hvis du vil oprette en traditionel, utrænet dokumentforståelsesmodel i stedet for en færdigbyggede model, skal du vælge **Brugerdefineret dokumentforståelse**.

4. Hvis du vil ændre indholdstypen eller tilføje en opbevaringsetiket, skal du vælge **Avancerede indstillinger**.

    > [!NOTE]
    > Følsomhedsmærkater er i øjeblikket ikke tilgængelige for indbyggede modeller.

5. Vælg **Opret**. Modellen gemmes i biblioteket **Modeller** .

## <a name="add-a-file-to-analyze"></a>Tilføj en fil, der skal analyseres

1. Vælg **Tilføj fil** i sektionen **Tilføj en fil, der skal analyseres** på **siden Modeller**.

    ![Skærmbillede af siden nye modeller, der viser sektionen Tilføj en fil, der skal analyseres.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. På siden **Filer til analyse af modellen** skal du vælge **Tilføj for** at finde den fil, du vil bruge.

    ![Skærmbillede af siden Filer til analyse af modellen, der viser knappen Tilføj.](../media/content-understanding/prebuilt-add-file-button.png) 

3. På siden **Tilføj en fil fra biblioteket med kursusfiler** skal du markere filen og derefter vælge **Tilføj**.

    ![Skærmbillede af siden Tilføj en fil fra biblioteket med kursusfiler.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. På siden **Filer, der skal analysere modellen** skal du vælge **Næste**.

## <a name="select-extractors-for-your-model"></a>Vælg uddrag til din model

På siden med oplysninger om extractor får du vist dokumentområdet til højre **og panelet** Udtræk i venstre side. Panelet **Udtræk** viser listen over de udtræk, der er identificeret i dokumentet.

   ![Skærmbillede af siden med oplysninger om extractor og panelet Extractor.](../media/content-understanding/prebuilt-extractor-details-page.png) 

De enhedsfelter, der er fremhævet med grønt i dokumentområdet, er de elementer, der blev registreret af modellen, da den analyserede filen. Når du vælger en enhed, der skal udtrækkes, ændres det fremhævede felt til blåt. Hvis du senere beslutter dig for ikke at medtage enheden, ændres det fremhævede felt til gråt. Fremhævninger gør det nemmere at se den aktuelle tilstand for de udtræk, du har valgt.

> [!TIP]
> Du kan bruge rullehjulet på musen eller kontrolelementerne nederst i dokumentområdet til at zoome ind eller ud efter behov for at læse enhedsfelterne.

### <a name="select-an-extractor-entity"></a>Vælg en extractor-enhed

Afhængigt af dine præferencer kan du vælge en extractor **enten fra** dokumentområdet eller fra panelet Udtræk.
 
- Vælg enhedsfeltet for at vælge en extractor fra dokumentområdet.

    ![Skærmbillede af dokumentområdet, der viser, hvordan du vælger et enhedsfelt.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Hvis du vil vælge en extractor fra **panelet Udtræk** , skal du markere afkrydsningsfeltet til højre for enhedsnavnet.

    ![Skærmbillede af panelet Udtræk, der viser, hvordan du vælger et enhedsfelt.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Når du vælger en udtræksmaskine, **vises feltet** Vælg udtræk? i dokumentområdet. Feltet viser udtræksnavnet, den oprindelige værdi og muligheden for at vælge den som en extractor. For visse datatyper, f.eks. tal eller datoer, vises der også en udtruken værdi.

   ![Skærmbillede af feltet Select extractor på siden med oplysninger om extractor.](../media/content-understanding/prebuilt-select-distractor-box.png) 

Den oprindelige værdi er det, der faktisk er i dokumentet. Den udtrukne værdi er det, der bliver skrevet i kolonnen SharePoint. Når modellen anvendes på et bibliotek, kan du bruge kolonneformatering til at angive, hvordan den skal se ud i dokumentet.

Fortsæt med at vælge yderligere udtræk, du vil bruge. Du kan også tilføje andre filer, der skal analyseres for denne modelkonfiguration.

## <a name="rename-an-extractor"></a>Omdøbe en extractor

Du kan omdøbe en extractor enten fra modellens startside eller fra panelet **Udtræk** . Du kan overveje at omdøbe udvalgte udtræksorer, da disse navne skal bruges som kolonnenavne, når modellen anvendes på biblioteket.

Sådan omdøber du en extractor fra modellens startside:

1. I sektionen **Udtræk skal** du vælge den extractor, du vil omdøbe, og derefter vælge **Omdøb**.

    ![Skærmbillede af sektionen Udtræk med indstillingen Omdøb fremhævet.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. På panelet **Omdøb enhedsudtrækeller** skal du angive det nye navn på extractoren og derefter vælge **Omdøb**.

Sådan omdøber du en extractor fra **panelet Udtræk** :

1. Vælg den extractor, du vil omdøbe, og vælg derefter **Omdøb**.

    ![Skærmbillede af panelet Udtræk, der viser, hvordan du omdøber en extractor.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. I feltet **Omdøb uddrager** skal du skrive det nye navn på extractoren og derefter vælge **Omdøb**.

## <a name="apply-the-model"></a>Anvend modellen

- Hvis du vil gemme ændringer og vende tilbage til modellens startside, **skal du vælge** Gem og afslut i **panelet Udtræk**.

- Hvis du er klar til at anvende modellen på et bibliotek, skal du vælge Næste i **dokumentområdet**. På panelet **Føj til bibliotek** skal du vælge det bibliotek, som du vil føje modellen til, og derefter vælge **Tilføj**.

> [!TIP]
> Du kan ændre visningen i dit dokumentbibliotek, så den passer til dine behov eller præferencer. Du kan finde flere oplysninger [i Ændre visningen i et dokumentbibliotek](apply-a-model.md#change-the-view-in-a-document-library).

## <a name="see-also"></a>Se også

[Anvend en dokumentforståelsesmodel](apply-a-model.md)