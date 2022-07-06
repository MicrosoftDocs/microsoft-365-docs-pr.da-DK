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
description: Få mere at vide om, hvordan du bruger SharePoint Syntex til at identificere kontraktfiler og udtrække data ved hjælp af en Microsoft 365-løsning.
ms.openlocfilehash: 2d9967cc432cb4d75bebbc67b7b9b0a812baa031
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631975"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Trin 1. Brug SharePoint Syntex til at identificere kontraktfiler og udtrække data

Din organisation skal bruge en metode til at identificere og klassificere alle kontraktdokumenter fra de mange filer, du modtager. Du ønsker også hurtigt at kunne se flere vigtige elementer i hver af de identificerede kontraktfiler (f.eks *. klient*, *entreprenør* og *gebyrbeløb*). Det kan du gøre ved hjælp af [SharePoint Syntex](index.md) til at oprette en model til forståelse af et dokument og anvende den i et dokumentbibliotek.

## <a name="overview-of-the-process"></a>Oversigt over processen

[Dokumentforståelse](document-understanding-overview.md) bruger AI-modeller (artificial intelligence) til at automatisere klassificering af filer og udtrækning af oplysninger. Modeller til dokumentforståelse er også optimale til at udtrække oplysninger fra ustrukturerede og semi-strukturerede dokumenter, hvor de oplysninger, du har brug for, ikke findes i tabeller eller formularer, f.eks. kontrakter. 

Modeller til dokumentforståelse bruger OCR-teknologien (Optical Character Recognition) til at scanne PDF-filer, billeder og TIFF-filer, både når du oplærer en model med eksempelfiler, og når du kører modellen mod filer i et dokumentbibliotek.

1. Først skal du finde mindst fem eksempelfiler, som du kan bruge til at "oplære" modellen til at søge efter egenskaber, der er specifikke for den indholdstype, du forsøger at identificere (en kontrakt). 

2. Opret en ny model til dokumentforståelse ved hjælp af SharePoint Syntex. Ved hjælp af dine eksempelfiler skal du [oprette en klassificering](create-a-classifier.md). Ved at oplære klassificeringen med dine eksempelfiler lærer du det at søge efter egenskaber, der er specifikke for, hvad du ville se i din virksomheds kontrakter. Du kan f.eks. [oprette en "forklaring"](create-a-classifier.md#create-an-explanation) , der søger efter bestemte strenge, der findes i dine kontrakter, f.eks *. Serviceaftale*, *Aftalevilkår* og *Kompensation*. Du kan endda oplære din forklaring til at søge efter disse strenge i bestemte afsnit i dokumentet eller placeret ud for andre strenge. Når du mener, at du har oplært din klassificering med de oplysninger, den har brug for, kan du teste din model på et eksempelsæt af eksempelfiler for at se, hvor effektiv den er. Efter testen kan du om nødvendigt vælge at foretage ændringer af dine forklaringer for at gøre dem mere effektive. 

3. I din model kan du [oprette en udtrækningsmaskine](create-an-extractor.md) for at udtrække bestemte data fra hver kontrakt. For hver kontrakt er de oplysninger, du er mest bekymret for, f.eks. hvem kunden er, navnet på underleverandøren og de samlede omkostninger.

4. Når du har oprettet din model, [kan du anvende den på et SharePoint-dokumentbibliotek](apply-a-model.md). Når du uploader dokumenter til dokumentbiblioteket, kører modellen til dokumentforståelse og identificerer og klassificerer alle filer, der svarer til den kontraktindholdstype, du har defineret i din model. Alle filer, der er klassificeret som kontrakter, vises i en brugerdefineret biblioteksvisning. Filerne viser også værdierne fra hver kontrakt, du har defineret i udtrækningen.

   ![Kontrakter i dokumentbiblioteket.](../media/content-understanding/doc-lib-solution.png)

5. Hvis du har opbevarings- eller sikkerhedskrav til dine kontrakter, kan du også bruge din model til at anvende en [opbevaringsmærkat](apply-a-retention-label-to-a-model.md) eller en [følsomhedsmærkat](apply-a-sensitivity-label-to-a-model.md) , der forhindrer, at dine kontrakter slettes i et bestemt tidsrum, eller til at begrænse, hvem der har adgang til kontrakterne.

## <a name="steps-to-create-and-train-your-model"></a>Trin til oprettelse og oplæring af din model

> [!NOTE]
> Til disse trin kan du bruge eksempelfilerne i [lageret Med løsningsaktiver til styring af kontrakter](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management). Eksemplerne i dette lager indeholder både det dokument, der forstår modelfiler, og de filer, der bruges til at oplære modellen.

### <a name="create-a-contract-model"></a>Opret en kontraktmodel

Det første trin er at oprette din kontraktmodel.

1. Vælg **Ny** i indholdscenteret, og vælg derefter **Opret en model**.

2. Skriv navnet på modellen i feltet **Navn** i ruden **Nyt dokumentforståelse** af model. I forbindelse med denne kontraktstyringsløsning kan du navngive *modelkontrakten*.

4. Vælg **Opret**. Dette opretter en startside for modellen.</br>

    ![Skærmbillede af startsiden kontrakt.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Oplær din model til at klassificere en filtype

#### <a name="add-example-files-for-your-model"></a>Tilføj eksempelfiler til din model

Du skal tilføje mindst fem eksempelfiler, der er kontraktdokumenter, og én eksempelfil, der ikke er et kontraktdokument (f.eks. en arbejdserklæring). 

1. Vælg **Tilføj** filer under **Nøglehandlinger** > **Tilføj eksempelfiler** på siden **Modeller > Kontrakt**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Tilføj eksempelfiler fremhævet.](../media/content-understanding/key-actions-add-example-files.png)

2. Åbn mappen Kontrakt på siden **Vælg eksempelfiler til din model** , vælg de filer, du vil bruge, og vælg derefter **Tilføj**. Hvis du ikke har eksempelfiler der, skal du vælge **Upload** for at tilføje dem.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Mærk filerne som positive eller negative eksempler

1. Vælg **Oplær klassificering** under **Nøglehandlinger** > **Klassificer filer og kør oplæring** på siden **Modeller > Kontrakt**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Klassificer filer og kør oplæring fremhævet.](../media/content-understanding/key-actions-classify-files.png)

2. På siden **Modeller > Contract > Contract-klassificering** kan du i fremviseren øverst i den første eksempelfil se tekst, hvor du bliver spurgt, om filen er et eksempel på den kontraktmodel, du har oprettet. Hvis det er et positivt eksempel, skal du vælge **Ja**. Hvis det er et negativt eksempel, skal du vælge **Nej**.

3. Vælg andre filer, du vil bruge som eksempler, på listen **Navngivne eksempler** til venstre, og mærk dem. 

    ![Klassificeringsstartside.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Tilføj mindst én forklaring for at oplære klassificeringen 

1. Vælg fanen **Oplær** **på siden Modeller > Contract > Contract classifier**.

2. I afsnittet **Oplærte filer** kan du se en liste over de eksempelfiler, du tidligere har mærket. Vælg en af de positive filer på listen for at få den vist i fremviseren.

3. I afsnittet **Forklaringer** skal du vælge **Ny** og derefter **Tom**.

4. På siden **Opret en forklaring** :

    a. I feltet **Navn** skal du skrive navnet på forklaringen (f.eks. "Aftale").

    b. I feltet **Forklaringstype** skal du vælge **Sætningsliste**, fordi du tilføjer en tekststreng.

    c. Skriv strengen (f.eks. "AGREEMENT") **på listen Udtryk** . Du kan vælge **Forskel på store og små bogstaver** , hvis strengen skal skelne mellem store og små bogstaver.

    d. Vælg **Gem og oplær**.

    ![Skærmbillede af panelet Opret en forklaring.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Test din model

Du kan teste din Kontraktmodel på eksempelfiler, den ikke har set før. Dette er valgfrit, men det kan være en nyttig bedste praksis.

1. Vælg fanen **Test** **på siden Modeller > Contract > Contract classifier**. Dette kører modellen på de eksempelfiler, der ikke er navngivet.

2. På listen **Test filer** vises dine eksempelfiler, og de vises, hvis modellen forudsagde, at de var positive eller negative. Brug disse oplysninger til at fastslå klassificeringens effektivitet i identificering af dine dokumenter.

    ![Skærmbillede af ikke-navngivne filer på listen Tekstfiler.](../media/content-understanding/test-on-files.png) 

3. Når du er færdig, skal du vælge **Afslut oplæring**.

### <a name="create-and-train-an-extractor"></a>Opret og oplær en udtrækningsmaskine

1. På siden **Modeller > Kontrakt** under **Nøglehandlinger** > **Opret og oplær udtrækninger** skal du vælge **Opret udtrækningsmaskine**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Opret og oplær udtræk fremhævet.](../media/content-understanding/key-actions-create-extractors.png)

2. Skriv navnet på udtrækningsenheden i feltet **Nyt navn** i panelet **Udtrækning af ny enhed**. Navngiv det f.eks *. Client* , hvis du vil udtrække navnet på klienten fra hver kontrakt.

3. Når du er færdig, skal du vælge **Opret**.

#### <a name="label-the-entity-you-want-to-extract"></a>Mærk den enhed, du vil udtrække

Når du opretter udtrækningen, åbnes siden extractor. Her kan du se en liste over dine eksempelfiler, hvor den første fil vises på listen i fremviseren.

![Skærmbillede af siden Klientudtrækningsmaskine med navngivne eksempler.](../media/content-understanding/client-extractor-labeled-examples.png) 

Sådan navngiver du objektet:

1. Vælg de data, du vil udtrække fra filerne, i fremviseren. Hvis du f.eks. vil udtrække *klienten*, skal du fremhæve klientværdien i den første fil (i dette eksempel *Bedst til dig organiske elementer*) og derefter vælge **Gem**. Du kan se den værdi, der vises fra filen, på listen **Navngivne eksempler** under kolonnen **Mærkat** .

2. Vælg **Næste fil** for at gemme automatisk, og åbn den næste fil på listen i fremviseren. Eller vælg **Gem**, og vælg derefter en anden fil på listen **Navngivne eksempler** .

3. Gentag trin 1 og 2 i fremviseren, og gentag derefter, indtil du har gemt mærkaten i alle filerne.

Når du har mærket filerne, vises der et meddelelsesbanner, der informerer dig om, at du skal skifte til oplæring. Du kan vælge at navngive flere dokumenter eller gå videre til oplæringen.

#### <a name="add-an-explanation"></a>Tilføj en forklaring

Du kan oprette en forklaring, der giver et tip om selve enhedsformatet og de variationer, der kan være i eksempelfilerne. En datoværdi kan f.eks. være i mange forskellige formater, f.eks.:

- 10/14/2019
- 14. oktober 2019
- Mandag den 14. oktober 2019

Hvis du vil identificere *kontraktens startdato*, kan du oprette en forklaring.

1. I afsnittet **Forklaringer** skal du vælge **Ny** og derefter **Tom**.

2. På siden **Opret en forklaring** :

    a. I feltet **Navn** skal du skrive navnet på forklaringen (f.eks *. Dato*).

    b. I feltet **Forklaringstype** skal du vælge **Sætningsliste**.

    c. I feltet **Værdi** skal du angive datovariationen, som de vises i eksempelfilerne. Hvis du f.eks. har datoformater, der vises som 00/00/0000, skal du angive eventuelle variationer, der vises i dine dokumenter, f.eks.:

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. Vælg **Gem og oplær**.

#### <a name="test-your-model-again"></a>Test din model igen

Du kan teste din Kontraktmodel på eksempelfiler, den ikke har set før. Dette er valgfrit, men det kan være en nyttig bedste praksis.

1. Vælg fanen **Test** **på siden Modeller > Contract > Contract classifier**. Dette kører modellen på de eksempelfiler, der ikke er navngivet.

2. På listen **Test filer** vises dine eksempelfiler, og de viser, om modellen kan udtrække de oplysninger, du har brug for. Brug disse oplysninger til at fastslå klassificeringens effektivitet i identificering af dine dokumenter.

3. Når du er færdig, skal du vælge **Afslut oplæring**.

### <a name="apply-your-model-to-a-document-library"></a>Anvend din model på et dokumentbibliotek

Sådan anvender du din model på et SharePoint-dokumentbibliotek:

1. Vælg **Anvend model** under **Nøglehandlinger** > **Anvend model på biblioteker** på siden **Modeller > Kontrakt**.

   ![Skærmbillede, der viser siden Kontrakter med indstillingen Anvend model på biblioteker fremhævet.](../media/content-understanding/key-actions-apply-model.png)

2. I panelet **Tilføj kontrakt** skal du vælge det SharePoint-websted, der indeholder det dokumentbibliotek, du vil anvende modellen på. Hvis webstedet ikke vises på listen, skal du bruge søgefeltet til at finde det. Vælg **Tilføj**.

    > [!NOTE]
    > Du skal have *tilladelserne Administrer liste* eller *Rediger* til det dokumentbibliotek, du anvender modellen på.

3. Når du har valgt webstedet, skal du vælge det dokumentbibliotek, du vil anvende modellen på.

4. Da modellen er knyttet til en indholdstype, tilføjer den indholdstypen og dens visning med de etiketter, du udtrækkede, og som vises som kolonner, når du anvender den på biblioteket. Denne visning er bibliotekets standardvisning, men du kan eventuelt vælge ikke at få den til at være standardvisning ved at vælge **Avancerede indstillinger** og fjerne markeringen i afkrydsningsfeltet **Angiv denne nye visning som standard** .

5. Vælg **Tilføj** for at anvende modellen på biblioteket.

6. På siden **Modeller > kontrakt** kan du i afsnittet **Biblioteker med denne model** se URL-adressen til det SharePoint-websted, der er angivet.

    ![Skærmbillede af startsiden kontrakt, der viser sektionen Biblioteker med denne model.](../media/content-understanding/contract-libraries-with-this-model.png)

7. Under **Indstillinger for** > **biblioteksindstillinger**:

   - Tilføj en kolonne med navnet **Status,** og vælg **Valg** som kolonnetype.
   - Anvend værdierne **I gennemsyn**, **Godkendt** og **Afvist** .

Når du har anvendt modellen på dokumentbiblioteket, kan du begynde at overføre dokumenter til webstedet og se resultaterne.

## <a name="next-step"></a>Næste trin

[Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal](solution-manage-contracts-step2.md)
