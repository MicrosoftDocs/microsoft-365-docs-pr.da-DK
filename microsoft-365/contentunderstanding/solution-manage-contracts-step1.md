---
title: Trin 1. Brug SharePoint Syntex til at identificere kontraktfiler og udtrække data
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Lær at bruge en SharePoint Syntex at identificere kontraktfiler og udtrække data ved hjælp af en Microsoft 365 løsning.
ms.openlocfilehash: c654c72ef36bf86337b7564efc68e4523516f4f9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63597927"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Trin 1. Brug SharePoint Syntex til at identificere kontraktfiler og udtrække data

Din organisation har brug for en metode til at identificere og klassificere alle kontraktdokumenter fra de mange filer, du modtager. Du ønsker også hurtigt at kunne få vist flere vigtige elementer i hver af de kontraktfiler *, der* er identificeret (f.eks. *beløb* til klient, leverandør *og gebyr*). Det kan du gøre ved SharePoint Syntex [oprette en](index.md) dokumentforståelsesmodel og anvende den i et dokumentbibliotek.

## <a name="overview-of-the-process"></a>Oversigt over processen

[Dokumentforståelse](document-understanding-overview.md) bruger kunstig intelligens til at automatisere klassificeringen af filer og udtræk af oplysninger. Dokumentforståelsesmodeller er også optimal til at udtrække oplysninger fra ustrukturerede og semistrukturerede dokumenter, hvor de oplysninger, du skal bruge, ikke findes i tabeller eller formularer, f.eks. kontrakter. 

Dokumentforståelsesmodeller bruger Optical Character Recognition-teknologi (OCR) til at scanne PDF-filer, billeder og TIFF-filer, både når du træner en model med eksempelfiler, og når du kører modellen mod filer i et dokumentbibliotek.

1. Først skal du finde mindst fem eksempelfiler, som du kan bruge til at "træne" modellen til at søge efter karakteristika, der er specifikke for den indholdstype, du forsøger at identificere (en kontrakt). 

2. Opret SharePoint Syntex dokumentforståelsesmodel ved hjælp af en ny dokumentforståelsesmodel. Ved hjælp af dine eksempelfiler skal du [oprette en klassificering](create-a-classifier.md). Ved at uddanne klassificeringen med dine eksempelfiler lærer du den at søge efter karakteristika, der er specifikke for, hvad du ville se i virksomhedens kontrakter. Du kan [f.eks](create-a-classifier.md#create-an-explanation). oprette en "forklaring", der søger efter bestemte strenge, der findes i dine kontrakter, f.eks. *Serviceaftale**, Vilkår* for aftale og *Løn*. Du kan endda træne din forklaring til at lede efter disse strenge i bestemte afsnit i dokumentet eller ved siden af andre strenge. Når du mener, at du har trænet din klassificering med de oplysninger, den skal bruge, kan du teste din model på et eksempelsæt med eksempelfiler for at se, hvor effektivt det er. Efter testning kan du, hvis det er nødvendigt, vælge at foretage ændringer til dine forklaringer for at gøre dem mere effektive. 

3. I din model kan du [oprette en extractor](create-an-extractor.md) til at udtrække bestemte data fra hver kontrakt. For hver kontrakt gælder det f.eks. om de oplysninger, du er mest bekymret om, hvem klienten er, navnet på entreprenøren og de samlede omkostninger.

4. Når du har oprettet modellen, skal [du anvende den på SharePoint dokumentbibliotek.](apply-a-model.md) Når du overfører dokumenter til dokumentbiblioteket, kører din dokumentforståelsesmodel og identificerer og klassificerer alle filer, der svarer til de kontrakters indholdstype, du har defineret i modellen. Alle filer, der er klassificeret som kontrakter, vises i en brugerdefineret biblioteksvisning. Filerne vil også vise værdierne fra hver kontrakt, som du har defineret i din extractor.

   ![Kontrakter i dokumentbibliotek.](../media/content-understanding/doc-lib-solution.png)

5. Hvis du har opbevarings- eller sikkerhedskrav til dine kontrakter, kan du også bruge modellen til at [](apply-a-retention-label-to-a-model.md) anvende en opbevaringsmærkat eller en følsomhedsmærkat, der kan forhindre, at dine kontrakter slettes i en bestemt tidsperiode, eller til at begrænse, hvem der kan få adgang til kontrakterne.[](apply-a-sensitivity-label-to-a-model.md)

## <a name="steps-to-create-and-train-your-model"></a>Trin til at oprette og træne din model

> [!NOTE]
> Til disse trin kan du bruge eksempelfilerne i lageret [med løsningsaktiver til kontraktstyring](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management). Eksemplerne i dette lager indeholder både dokumentet om modelfiler og de filer, der bruges til at træne modellen.

### <a name="create-a-contract-model"></a>Opret en kontraktmodel

Det første trin er at oprette din kontraktmodel.

1. I indholdscenteret skal du **vælge Ny** og derefter **Opret en model**.

2. Skriv **navnet på modellen i** feltet Navn i **ruden** Ny dokumentforståelsesmodel. For denne løsning til kontraktadministration kan du navngive modellen *Kontrakt*.

4. Vælg **Opret**. Dette opretter en startside for modellen.</br>

    ![Skærmbillede af startsiden for kontrakt.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Træn din model til at klassificere en filtype

#### <a name="add-example-files-for-your-model"></a>Tilføje eksempelfiler til din model

Du skal tilføje mindst fem eksempelfiler, som er kontraktdokumenter, og en eksempelfil, der ikke er et kontraktdokument (f.eks. en arbejdserklæring). 

1. På siden **Modeller > Kontrakt** under **Vigtige handlingerFæl** >  **eksempelfiler**, og vælg **Tilføj filer**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Tilføj eksempelfiler fremhævet.](../media/content-understanding/key-actions-add-example-files.png)

2. På siden **Vælg eksempelfiler til din model** skal du åbne mappen Kontrakt, vælge de filer, du vil bruge, og derefter vælge **Tilføj**. Hvis du ikke har eksempelfiler der, skal du Upload **for** at tilføje dem.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Giv filerne et navn som positive eller negative eksempler

1. På siden **Modeller > Kontrakt** **under** >  Vigtige **handlingerKlassificer filer**, og kør kursus skal du **vælge Træn klassificering**.

   ![Skærmbillede, der viser siden Kontrakter med Klassificer filer og kør kursusvalg fremhævet.](../media/content-understanding/key-actions-classify-files.png)

2. På siden Model **> Contract > Contract-klassificering** i fremviseren øverst i den første eksempelfil får du vist tekst, der spørger, om filen er et eksempel på den kontraktmodel, du har oprettet. Hvis det er et positivt eksempel, skal du vælge **Ja**. Hvis det er et negativt eksempel, skal du vælge **Nej**.

3. På listen **Med etiketter til venstre** skal du markere andre filer, du vil bruge som eksempler, og markere dem med mærkat. 

    ![Startside for klassificering.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Tilføj mindst én forklaring for at oplære klassificeringen 

1. På siden **Model > kontrakt > Contract-klassificering** skal du vælge **fanen** Træ.

2. I sektionen **Oplærte** filer får du vist en liste over de eksempelfiler, du tidligere har navnmærket. Vælg en af de positive filer på listen for at få den vist i fremviseren.

3. I sektionen **Forklaringer** skal du vælge **Ny** og derefter **Tom**.

4. På siden **Opret en forklaring** :

    a. Skriv navnet **på** forklaringen i feltet Navn (f.eks. "Aftale").

    b. I feltet **Forklaringstype** skal du vælge **listen Udtryk**, fordi du tilføjer en tekststreng.

    c. Skriv **strengen (** f.eks. "AFTALE") på listen Udtryk. Du kan vælge Store **og små bogstaver** , hvis der skal være store og små bogstaver i strengen.

    d. Vælg **Gem og træn**.

    ![Skærmbillede af panelet Opret en forklaring.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Test din model

Du kan teste din kontraktmodel på eksempelfiler, den ikke har set før. Dette er valgfrit, men det kan være en nyttig bedste fremgangsmåde.

1. På siden **Modeller > kontrakt > Kontrakt-klassificering** skal du vælge **fanen Test** . Dette kører modellen på dine eksempelfiler uden navn.

2. På listen **Testfiler** vises og vises dine eksempelfiler, hvis modellen forudsagte, at de var positive eller negative. Brug disse oplysninger til at bestemme effektiviteten af din klassificering til at identificere dine dokumenter.

    ![Skærmbillede af filerne uden navn på listen Tekstfiler.](../media/content-understanding/test-on-files.png) 

3. Når du er færdig, skal **du vælge Afslut kursus**.

### <a name="create-and-train-an-extractor"></a>Opret og træn en extractor

1. På siden **Modelmodel > kontrakt** under Vigtige **handlingerOprette** >  og **træne udtrækkere** skal du **vælge Opret udtræk**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Opret og træudtræk fremhævet.](../media/content-understanding/key-actions-create-extractors.png)

2. På panelet **Ny enhedsudtrækeller** i **feltet Nyt navn** skal du skrive navnet på din extractor. Navngive *den f.eks* . Klient, hvis du vil hente navnet på klienten fra hver kontrakt.

3. Vælg Opret, når du er **færdig**.

#### <a name="label-the-entity-you-want-to-extract"></a>Navnknyt den enhed, du vil udtrække

Når du opretter extractoren, åbnes extractor-siden. Her kan du se en liste over dine eksempelfiler, hvor den første fil på listen vises i fremviseren.

![Skærmbillede af siden Klientudtrækeller Med etiketter.](../media/content-understanding/client-extractor-labeled-examples.png) 

Sådan navnmærkes enheden:

1. Vælg i fremviseren de data, du vil udtrække fra filerne. Hvis du f.eks. vil udtrække *klienten, skal* du fremhæve klientværdien i den første fil (i dette eksempel *Bedst til dig organicer*) og derefter vælge **Gem**. Du får vist værdien fra filen på listen **Etiketekseler** **under kolonnen Navn** .

2. Vælg **Næste fil** for at gemme automatisk og åbne den næste fil på listen i fremviseren. Eller vælg **Gem**, og vælg derefter en anden fil **på listen Med etiketter.**

3. Gentag trin 1 og 2 i fremviseren, og gentag derefter, indtil du har gemt navnet i alle filerne.

Når du har mærket filerne, vises der et meddelelsesbanner, som informerer dig om at gå til uddannelse. Du kan vælge at navnmærke flere dokumenter eller gå videre til kurser.

#### <a name="add-an-explanation"></a>Tilføj en forklaring

Du kan oprette en forklaring, der giver et tip om selve enhedsformatet og variationer, det kan have i eksempelfilerne. En datoværdi kan f.eks. være i mange forskellige formater, f.eks.:

- 10/14/2019
- 14. oktober 2019
- mandag d. 14. oktober 2019

Du kan oprette en *forklaring på et mønster for* at identificere startdatoen for kontrakten.

1. I sektionen **Forklaringer** skal du vælge **Ny** og derefter **Tom**.

2. På siden **Opret en forklaring** :

    a. Skriv navnet **på** forklaringen i feltet Navn (f.eks *. Dato*).

    b. I feltet **Forklaringstype** skal du vælge **Listen Mønster**.

    c. Angiv **datovariationen** , som de vises i eksempelfilerne, i feltet Værdi. Hvis du f.eks. har datoformater, der vises som 00-00-0000, skal du angive de variationer, der vises i dine dokumenter, f.eks.:

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. Vælg **Gem og træn**.

#### <a name="test-your-model-again"></a>Test din model igen

Du kan teste din kontraktmodel på eksempelfiler, den ikke har set før. Dette er valgfrit, men det kan være en nyttig bedste fremgangsmåde.

1. På siden **Modeller > kontrakt > Kontrakt-klassificering** skal du vælge **fanen Test** . Dette kører modellen på dine eksempelfiler uden navn.

2. På listen **Test filer** viser og viser dine eksempelfiler, om modellen kan udtrække de oplysninger, du har brug for. Brug disse oplysninger til at bestemme effektiviteten af din klassificering til at identificere dine dokumenter.

3. Når du er færdig, skal **du vælge Afslut kursus**.

### <a name="apply-your-model-to-a-document-library"></a>Anvend din model på et dokumentbibliotek

Sådan anvender du din model på et SharePoint dokumentbibliotek:

1. På siden **Modeller > Kontrakt** under **Vigtige handlingerAnsøg** >  **model på biblioteker skal** du vælge **Anvend model**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Anvend model på biblioteker fremhævet.](../media/content-understanding/key-actions-apply-model.png)

2. I panelet **Tilføj kontrakt** skal du vælge det SharePoint, der indeholder det dokumentbibliotek, som du vil anvende modellen på. Hvis webstedet ikke vises på listen, kan du bruge søgefeltet til at finde det. Vælg **Tilføj**.

    > [!NOTE]
    > Du skal have *tilladelse til* at administrere liste *eller redigere* rettigheder til det dokumentbibliotek, du anvender modellen på.

3. Når du har valgt webstedet, skal du vælge det dokumentbibliotek, som du vil anvende modellen på.

4. Da modellen er knyttet til en indholdstype, tilføjer den indholdstypen og dens visning med de etiketter, du udtrækker, og vises som kolonner, når du anvender den på biblioteket. Denne visning er bibliotekets standardvisning som standard, men du kan vælge ikke at have den som standardvisning ved at markere Avancerede indstillinger og fjerne markeringen  i afkrydsningsfeltet Angiv denne  nye visning som standard.

5. Vælg **Tilføj** for at anvende modellen på biblioteket.

6. På siden **Model >,** i sektionen Biblioteker med denne **model**, får du vist URL-adressen til SharePoint websted.

    ![Skærmbillede af startsiden for kontrakt, der viser sektionen Biblioteker med denne model.](../media/content-understanding/contract-libraries-with-this-model.png)

7. Under **Indstillinger** >  **Library-indstillinger**:

   - Tilføj en kolonne med **navnet Status** , **og vælg Valg** som kolonnetype.
   - Anvend **værdierne Til gennemsyn**, Godkendt **og** Afvist. 

Når du har overført modellen til dokumentbiblioteket, kan du begynde at overføre dokumenter til webstedet og se resultaterne.

## <a name="next-step"></a>Næste trin

[Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal](solution-manage-contracts-step2.md)