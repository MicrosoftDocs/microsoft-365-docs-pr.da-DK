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
ms.openlocfilehash: 5e9be6065e0328a412e73680a0200ea7929c8011
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594188"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Opret en klassificering i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

En klassificering er en type model, du kan bruge til at automatisere identifikation og klassificering af en dokumenttype. Det kan f.eks. være, at  du vil identificere alle dokumenter til kontraktfornyelse, som er føjet til dit dokumentbibliotek, som vist i nedenstående illustration.

![Dokument til fornyelse af kontrakt.](../media/content-understanding/contract-renewal.png)

Når du opretter en klassificering, kan du oprette en ny [SharePoint, der](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) skal knyttes til modellen.

Når du opretter klassificeringen, skal du oprette forklaringer *for* at definere modellen. Dette giver dig mulighed for at notere fælles data, som du ville forvente at finde denne dokumenttype konsekvent. 

Brug eksempler på dokumenttypen ("eksempelfiler") til at "træne" modellen til at identificere filer, der har den samme indholdstype.

Hvis du vil oprette en klassificering, skal du:
1. Navngive din model.
2. Tilføj dine eksempelfiler.
3. Giv dine eksempelfiler et navn.
4. Oprette en forklaring.
5. Test din model.

> [!NOTE]
> Mens din model bruger en klassificering til at identificere og klassificere dokumenttyper, kan du også vælge at trække bestemte oplysninger fra hver fil, der identificeres af modellen. Gør dette ved at oprette en **extractor,** der skal føjes til din model. Se [Opret en extractor](create-an-extractor.md).

## <a name="name-your-model"></a>Navngive din model

Det første trin til at oprette din model er at give den et navn:

1. I indholdscenteret skal du **vælge Ny** og derefter **Opret en model**.
2. Skriv **navnet på modellen i** feltet Navn **i ruden** Ny dokumentforståelsesmodel. Hvis du f.eks. vil identificere dokumenter til fornyelse af kontrakt, kan du navngive modellen for *kontraktfornyelse*.
3. Vælg **Opret**. Dette opretter en startside for modellen.</br>

    ![Startsiden for klassificeringsmodel.](../media/content-understanding/model-home.png)

Når du opretter en model, opretter du også en ny webstedsindholdstype. En indholdstype repræsenterer en kategori af dokumenter, der har fælles karakteristika og deler en samling af kolonner eller metadataegenskaber for det pågældende indhold. SharePoint indholdstyper administreres via [galleriet Indholdstyper](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f). Når du opretter modellen i dette eksempel, opretter du en ny indholdstype *til* kontraktfornyelse.

Vælg **Avancerede indstillinger**, hvis du vil knytte denne model til en eksisterende virksomhedsindholdstype i galleriet SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">indholdstype</a> for at bruge dens skema. Virksomhedsindholdstyper gemmes i Hub til indholdstype i SharePoint Administration og syndikeres på alle websteder i lejeren. Bemærk, at selvom du kan bruge en eksisterende indholdstype til at anvende dens skema til identifikation og klassificering, skal du stadig træne din model til at udtrække oplysninger fra filer, den identificerer.</br>

![Avancerede indstillinger.](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Tilføj eksempelfilerne

På modellens startside skal du tilføje dine eksempelfiler, som du skal bruge for at oplære modellen til at identificere din dokumenttype. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Du skal bruge de samme filer til både klassificering og [extractor-kursus](create-an-extractor.md). Du har altid mulighed for at tilføje flere senere, men typisk tilføjer du et helt sæt eksempelfiler. Mærkat nogle for at træne din model og teste de resterende uden navn for at evaluere modeltræning. 

Til dit kursussæt vil du bruge både positive og negative eksempler:
- Positivt eksempel: Dokumenter, der repræsenterer dokumenttypen. Disse indeholder strenge og oplysninger, der altid findes i denne type dokument.
- Negativt eksempel: Alle andre dokumenter, der ikke repræsenterer det dokument, du vil klassificere. 

Sørg for at bruge mindst fem positive eksempler og mindst ét negativt eksempel til at oplære din model.  Du vil oprette flere til at teste modellen efter træningsprocessen.

Sådan tilføjer du eksempelfiler:

1. Klik på Tilføj filer i feltet **Tilføj eksempelfiler** på startsiden **for modellen**.
2. På siden **Vælg eksempelfiler til din model** skal du vælge dine eksempelfiler fra biblioteket Kursusfiler i indholdscenteret. Hvis du ikke allerede har uploadet dem der, skal du vælge at overføre dem nu ved at **klikke Upload** for at kopiere dem til biblioteket Kursusfiler.
3. Når du har valgt dine eksempelfiler, der skal bruges til at træne modellen, skal du klikke **på Tilføj**.

    ![Vælg eksempelfiler.](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Giv dine eksempelfiler et navn

Når du har tilføjet eksempelfilerne, skal du navnmærke dem som enten positive eller negative eksempler.

1. Fra modellens startside skal du på **feltet Klassificer** filer og kør kursus klikke **på Træklasseklasse.**
   Dette viser etiketsiden, der viser en oversigt over dine eksempelfiler, hvor den første fil er synlig i fremviseren.
2. I fremviseren øverst i den første eksempelfil kan du se tekst, der spørger, om filen er et eksempel på den model, du lige har oprettet. Hvis det er et positivt eksempel, skal du vælge **Ja**. Hvis det er et negativt eksempel, skal du vælge **Nej**.
3. Vælg **de ekstra filer, du** vil bruge som eksempler, på listen Med etiketter til venstre, og mærkater til dem. 

    ![Startside for klassificering.](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Navn giv mindst fem positive eksempler. Du skal også navnte mindst ét negativt eksempel. 

## <a name="create-an-explanation"></a>Opret en forklaring

Det næste trin er, at du opretter en forklaring på siden Tog. En forklaring hjælper modellen med at forstå, hvordan dokumentet genkendes. Eksempelvis indeholder dokumenter til fornyelse af kontrakt altid en tekststreng *til anmodning om yderligere* offentliggørelse.

> [!Note]
> Ved brug med udtræk identificerer en forklaring den streng, du vil udtrække fra dokumentet. 

Sådan oprettes en forklaring:

1. Fra modellens startside skal du vælge **fanen Tog** for at gå til siden Tog.
2. På siden Tog bør du i sektionen **Oplærte** filer se en liste over de eksempelfiler, du tidligere har navnmærket. Vælg en af de positive filer på listen, og den vises i fremviseren.
3. I sektionen Forklaring skal du vælge **Ny og** derefter **Tom**.
4. På siden **Opret en forklaring** :</br>
    a. Skriv **navnet (** f.eks. "Hemmeligholdelsesblok").</br>
    b. Vælg **Type**. Vælg listen Udtryk for eksemplet, **da** du tilføjer en tekststreng.</br>
    c. Skriv **strengen** i feltet Skriv her. For stikprøven skal du tilføje "Anmod om yderligere videregivelse". Du kan vælge Store og **små bogstaver** , hvis strengen skal være opmærksom på store og små bogstaver.</br>
    d. Klik på **Gem**.

    ![Opret forklaring.](../media/content-understanding/explanation.png) 
    
5. Indholdscenter kontrollerer nu, om den oprettede forklaring er tilstrækkelig stor til at identificere de resterende etiketterede eksempelfiler korrekt som positive og negative eksempler. I sektionen **Oplærte** filer skal du **markere kolonnen** Evaluering, når kurset er fuldført, for at se resultaterne. Filerne viser en værdi **af Match,** hvis de forklaringer, du har oprettet, er nok til at matche det, du har markeret som positivt eller negativt.

    ![Match værdi.](../media/content-understanding/match.png) 

    Hvis du modtager en **uoverensstemmelse** på de mærkede filer, skal du muligvis oprette en ekstra forklaring for at give modellen flere oplysninger for at identificere dokumenttypen. Hvis dette sker, skal du klikke på filen for at få flere oplysninger om, hvorfor uoverensstemmelsen opstod.

Når du har trænet en extractor, kan den udlærte extractor bruges som forklaring. I sektionen **Forklaringer** vises dette som en **modelreference**.

![Skærmbillede af sektionen Forklaringer, der viser referencen til typen Model.](../media/content-understanding/explanations-model-reference.png)

## <a name="test-your-model"></a>Test din model

Hvis du har modtaget et match på dine etikette eksempelfiler, kan du nu teste din model på dine resterende eksempelfiler uden navn, som modellen ikke har set før. Dette er valgfrit, men et nyttigt trin til at evaluere "fitness" eller parathed af modellen, før du bruger den, ved at teste den på filer, modellen ikke har set før.

1. Fra modellens startside skal du vælge **fanen** Test. Dette kører modellen på dine ikke-navnerede eksempelfiler.
2. På listen **Test filer** vises og viser dine eksempelfiler, om modellen havde forventet, at de var positive eller negative. Brug disse oplysninger til at bestemme effektiviteten af din klassificering til at identificere dine dokumenter.

    ![Test af filer uden navn.](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Se også
[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Forklaringstyper](explanation-types-overview.md)

[Anvend en model](apply-a-model.md) 

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)