---
title: Opret en klassificering i Microsoft SharePoint Syntex
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du opretter en klassificering i Microsoft SharePoint Syntex.
ms.openlocfilehash: 6c47d2fe2f7f2b67533587f0956281c2b577dbe0
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882368"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Opret en klassificering i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

En klassificering er en type model, som du kan bruge til at automatisere identifikation og klassificering af en dokumenttype. Det kan f.eks. være, at du vil identificere alle *kontraktfornyelsesdokumenter* , der føjes til dokumentbiblioteket, som vist i følgende illustration.

![Kontraktfornyelsesdokument.](../media/content-understanding/contract-renewal.png)

Når du opretter en klassificering, kan du oprette en ny [SharePoint indholdstype](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview), der er knyttet til modellen.

Når du opretter klassificeringen, skal du oprette *forklaringer* for at definere modellen. Dette giver dig mulighed for at notere almindelige data, som du ville forvente konsekvent at finde denne dokumenttype. 

Brug eksempler på dokumenttypen ("eksempelfiler") til at "oplære" din model til at identificere filer, der har samme indholdstype.

Hvis du vil oprette en klassificering, skal du:
1. Navngiv din model.
2. Tilføj dine eksempelfiler.
3. Mærk dine eksempelfiler.
4. Opret en forklaring.
5. Test din model.

> [!NOTE]
> Mens din model bruger en klassificering til at identificere og klassificere dokumenttyper, kan du også vælge at hente bestemte oplysninger fra hver fil, der er identificeret af modellen. Gør dette ved at oprette en **udtrækningsmaskine** , der skal føjes til din model. Se [Opret en udtrækningsmaskine](create-an-extractor.md).

## <a name="name-your-model"></a>Navngiv din model

Det første trin til at oprette din model er at give den et navn:

1. Vælg **Ny** i indholdscenteret, og vælg derefter **Opret en model**.
2. I ruden **Nyt dokument med forståelse af model** skal du i feltet **Navn** skrive navnet på modellen. Hvis du f.eks. vil identificere dokumenter om kontraktfornyelse, kan du navngive modellen *Kontraktfornyelse*.
3. Vælg **Opret**. Dette opretter en startside for modellen.</br>

    ![Startside for klassificeringsmodel.](../media/content-understanding/model-home.png)

Når du opretter en model, opretter du også en ny webstedsindholdstype. En indholdstype repræsenterer en kategori af dokumenter, der har fælles egenskaber, og som deler en samling kolonner eller metadataegenskaber for det pågældende indhold. SharePoint indholdstyper administreres via [galleriet Indholdstyper](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f). Når du i dette eksempel opretter modellen, opretter du en ny indholdstype *for kontraktfornyelse* .

Vælg **Avancerede indstillinger**, hvis du vil knytte denne model til en eksisterende virksomhedsindholdstype i galleriet med SharePoint indholdstyper for at bruge <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">skemaet</a>. Virksomhedsindholdstyper gemmes i indholdstypehubben i SharePoint Administration og syndikeres på alle websteder i lejeren. Bemærk, at selvom du kan bruge en eksisterende indholdstype til at udnytte skemaet til at hjælpe med identifikation og klassificering, skal du stadig oplære din model til at udtrække oplysninger fra filer, den identificerer.</br>

![Avancerede indstillinger.](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Tilføj dine eksempelfiler

Tilføj dine eksempelfiler på modellens startside, som du skal bruge for at oplære modellen til at identificere dokumenttypen. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Du skal bruge de samme filer til både klassificerings- og [udtrækningstræning](create-an-extractor.md). Du har altid mulighed for at tilføje flere senere, men du tilføjer typisk et komplet sæt eksempelfiler. Mærk nogle for at oplære din model, og test de resterende ikke-navngivne modeller for at evaluere modellens egnethed. 

Til dit oplæringssæt vil du bruge både positive og negative eksempler:
- Positivt eksempel: Dokumenter, der repræsenterer dokumenttypen. Disse indeholder strenge og oplysninger, der altid ville være i denne type dokument.
- Negativt eksempel: Alle andre dokumenter, der ikke repræsenterer det dokument, du vil klassificere. 

Sørg for at bruge mindst fem positive eksempler og mindst ét negativt eksempel til at oplære din model.  Du vil oprette flere for at teste din model efter oplæringsprocessen.

Sådan tilføjer du eksempelfiler:

1. Klik på **Tilføj filer** i feltet **Tilføj eksempelfiler** på modellens startside.
2. På siden **Vælg eksempelfiler til din model** skal du vælge dine eksempelfiler i biblioteket Oplæringsfiler i indholdscenteret. Hvis du ikke allerede havde uploadet dem der, kan du vælge at uploade dem nu ved at klikke **på Upload** for at kopiere dem til biblioteket Oplæringsfiler.
3. Når du har valgt de eksempelfiler, du vil bruge til at oplære modellen, skal du klikke på **Tilføj**.

    ![Vælg eksempelfiler.](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Mærk dine eksempelfiler

Når du har tilføjet dine eksempelfiler, skal du markere dem som enten positive eller negative eksempler.

1. Klik på **Oplær klassificering** i feltet **Klassificer filer, og kør oplæring** på modellens startside.
   Dette viser den etiketside, der viser en liste over dine eksempelfiler, hvor den første fil er synlig i fremviseren.
2. I fremviseren øverst i den første eksempelfil kan du se tekst, hvor du bliver spurgt, om filen er et eksempel på den model, du lige har oprettet. Hvis det er et positivt eksempel, skal du vælge **Ja**. Hvis det er et negativt eksempel, skal du vælge **Nej**.
3. Vælg yderligere filer, som du vil bruge som eksempler, på listen **Navngivne eksempler** til venstre, og mærk dem. 

    ![Klassificeringsstartside.](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Mærk mindst fem positive eksempler. Du skal også navngive mindst ét negativt eksempel. 

## <a name="create-an-explanation"></a>Opret en forklaring

Det næste trin er, at du skal oprette en forklaring på siden Oplær. En forklaring hjælper modellen med at forstå, hvordan dokumentet genkendes. Dokumenterne om kontraktfornyelse indeholder f.eks. altid en *tekststreng til anmodning om yderligere offentliggørelse* .

> [!Note]
> Når den bruges sammen med udtrækninger, identificerer en forklaring den streng, du vil udtrække fra dokumentet. 

Sådan opretter du en forklaring:

1. På startsiden for modellen skal du vælge fanen **Oplær** for at gå til siden Oplær.
2. På siden Oplær i afsnittet **Oplærte filer** kan du se en liste over de eksempelfiler, du tidligere har mærket. Vælg en af de positive filer på listen, så vises den i fremviseren.
3. I afsnittet Forklaring skal du vælge **Ny** og derefter **Tom**.
4. På siden **Opret en forklaring** :</br>
    a. Skriv **navnet** (f.eks. "Afsløringsblok").</br>
    b. Vælg **Type**. I eksemplet skal du vælge **Sætningsliste**, da du tilføjer en tekststreng.</br>
    c. Skriv strengen i feltet **Skriv her** . I eksemplet skal du tilføje "Anmodning om yderligere offentliggørelse". Du kan vælge **Forskel på store og små bogstaver** , hvis strengen skal skelne mellem store og små bogstaver.</br>
    d. Klik på **Gem**.

    ![Opret en forklaring.](../media/content-understanding/explanation.png) 
    
5. Indholdscenteret kontrollerer nu, om den forklaring, du har oprettet, er komplet nok til at identificere de resterende navngivne eksempelfiler korrekt som positive og negative eksempler. I afsnittet **Oplærte filer** skal du markere kolonnen **Evaluering** , når oplæringen er fuldført, for at se resultaterne. Filerne viser værdien **Match**, hvis de forklaringer, du har oprettet, stemmer overens med det, du har mærket som positive eller negative.

    ![Match værdi.](../media/content-understanding/match.png) 

    Hvis du modtager en **uoverensstemmelse** i de navngivne filer, skal du muligvis oprette en yderligere forklaring for at angive modellen flere oplysninger for at identificere dokumenttypen. Hvis det sker, skal du klikke på filen for at få flere oplysninger om, hvorfor uoverensstemmelsen opstod.

Når du har oplært en udtrækningsmaskine, kan den oplærte udtrækningsmaskine bruges som en forklaring. I afsnittet **Forklaringer** vises dette som en **modelreference**.

![Skærmbillede af afsnittet Forklaringer, der viser referencen til typen Model.](../media/content-understanding/explanations-model-reference.png)

## <a name="test-your-model"></a>Test din model

Hvis du har modtaget et match på dine mærkede eksempelfiler, kan du nu teste din model på de resterende eksempelfiler, der ikke er forsynet med mærkater, som modellen ikke har set før. Dette er valgfrit, men et nyttigt trin til at evaluere modellens "fitness" eller parathed, før du bruger den, ved at teste den på filer, som modellen ikke har set før.

1. Vælg fanen **Test** på modellens startside. Dette kører modellen på dine eksempelfiler, der ikke er navngivet.
2. På listen **Test filer** vises dine eksempelfiler, og de vises, hvis modellen forudsagde, at de var positive eller negative. Brug disse oplysninger til at fastslå klassificeringens effektivitet i identificering af dine dokumenter.

    ![Test af filer uden mærkat.](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Se også

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Forklaringstyper](explanation-types-overview.md)

[Anvend en model](apply-a-model.md) 

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)