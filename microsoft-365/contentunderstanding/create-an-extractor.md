---
title: Opret en udtrækningsmaskine til Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du opretter en udtrækningsmaskine i Microsoft SharePoint Syntex.
ms.openlocfilehash: 2089a5a52148ed4c00294895cd15e8af9c473cdb
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823118"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>Opret en udtrækningsmaskine i Microsoft SharePoint Syntex


<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

<br/>

Før eller efter du opretter en klassificeringsmodel for at automatisere identifikation og klassificering af bestemte dokumenttyper, kan du eventuelt vælge at føje udtrækninger til din model for at hente bestemte oplysninger fra disse dokumenter. Det kan f.eks. være, at din model ikke kun skal identificere alle dokumenter til *kontraktfornyelse* , der er føjet til dokumentbiblioteket, men også vise *tjenestens startdato* for hvert dokument som en kolonneværdi i dokumentbiblioteket.

Du skal oprette en udtrækningsenhed for hver enhed i det dokument, du vil udtrække. I vores eksempel vil vi udtrække **tjenestens startdato** for hvert **kontraktfornyelsesdokument** , der identificeres af modellen. Vi vil gerne have vist en visning i dokumentbiblioteket for alle dokumenter om **kontraktfornyelse** med en kolonne, der viser værdien for **tjenestens** startdato for hvert dokument.

> [!NOTE]
> Hvis du vil oprette en udtrækningsmaskine, skal du bruge de samme filer, som du tidligere har uploadet, til at oplære klassificeringen.

## <a name="name-your-extractor"></a>Navngiv udpakningen

1. På modellens startside skal du i feltet **Opret og oplær udtrækningsmaskiner** vælge **Oplær udtrækningsmaskine**.

2. På skærmen **New entity extractor** skal du skrive navnet på udtrækningsenheden i feltet **Nyt udtræksnavn** . Navngiv den f.eks. **Tjenestens startdato** , hvis du vil udtrække tjenestens startdato fra hvert kontraktfornyelsesdokument. Du kan også vælge at genbruge en tidligere oprettet kolonne (f.eks. en administreret metadatakolonne).

    Kolonnetypen er som standard **Enkelt tekstlinje**. Hvis du vil ændre kolonnetypen, skal du vælge **Avancerede** **indstillingerKolonnetype** >  og derefter vælge den type, du vil bruge.

    ![Skærmbillede af delen Avancerede indstillinger i panelet Udtræk af ny enhed, der viser indstillingen Kolonnetype.](../media/content-understanding/advanced-settings-column-type.png)

    > [!NOTE]
    > For uddrage med kolonnetypen **Enkelt tekstlinje** er den maksimale tegngrænse 255. Alle tegn, du skriver, som overskrider grænsen, afkortes.

3. Når du er færdig, skal du vælge **Opret**.

## <a name="add-a-label"></a>Tilføj en etiket

Det næste trin er at navngive det objekt, du vil udtrække i dine eksempeltræningsfiler.

Når udtrækningen oprettes, åbnes udtrækningssiden. Her kan du se en liste over dine eksempelfiler, hvor den første fil vises på listen i fremviseren.

1. Vælg de data, du vil udtrække fra filerne, i fremviseren. Hvis du f.eks. vil udtrække *startdatoen*, skal du fremhæve datoværdien i den første fil (*mandag den 14. oktober 2019*). og vælg derefter **Gem**. Du bør kunne se den værdi, der vises fra filen, på listen Navngivne eksempler under kolonnen **Mærkat** .
2. Vælg **Næste fil** for at gemme automatisk, og åbn den næste fil på listen i fremviseren. Eller vælg **Gem** , og vælg derefter en anden fil på listen **Navngivne eksempler** .
3. Gentag trin 1 og 2 i fremviseren, og gentag derefter, indtil du har gemt mærkaten i alle fem filer.

    ![Avancerede indstillinger.](../media/content-understanding/select-service-start-date.png)

Når du har mærket fem filer, vises der et meddelelsesbanner, der informerer dig om at flytte til træning. Du kan vælge at angive flere mærkater for flere dokumenter eller gå videre til oplæringen.

### <a name="use-find-to-search-your-file"></a>Brug Find til at søge i filen

Du kan bruge funktionen **Søg** til at søge efter en enhed i dokumentet, som du vil navngive.

   ![Søg i filen.](../media/content-understanding/find-feature.png)

Funktionen Find er nyttig, hvis du søger i et stort dokument, eller hvis der er flere forekomster af objektet i dokumentet. Hvis du finder flere forekomster, kan du vælge den, du skal bruge i søgeresultaterne, for at gå til den pågældende placering i fremviseren for at navngive den.

## <a name="add-an-explanation"></a>Tilføj en forklaring

I vores eksempel opretter vi en forklaring, der giver et tip om selve enhedsformatet og de variationer, der kan være i eksempeldokumenterne. En datoværdi kan f.eks. være i en række forskellige formater, f.eks.:

- 10/14/2019
- 14. oktober 2019
- Mandag den 14. oktober 2019

Du kan oprette en mønsterforklaring for at hjælpe med at identificere *tjenestens startdato* .

1. I afsnittet Forklaring skal du vælge **Ny** og skrive et navn (f.eks *. Dato*).
2. Vælg **Mønsterliste** for Type.
3. For Værdi skal du angive datovariationen, som de vises i eksempelfilerne. Hvis du f.eks. har datoformater, der vises som 00/00/0000, skal du angive eventuelle variationer, der vises i dine dokumenter, f.eks.:
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. Vælg **Gem**.

> [!NOTE]
> Du kan få mere at vide om forklaringstyper under [Forklaringstyper](./explanation-types-overview.md).

### <a name="use-the-explanation-library"></a>Brug forklaringsbiblioteket

Hvis du vil oprette forklaringer til elementer som datoer, er det nemmere at [bruge forklaringsbiblioteket](./explanation-types-overview.md) end manuelt at angive alle variationer. Forklaringsbiblioteket er et sæt færdigbyggede udtryk og mønsterforklaringer. Biblioteket forsøger at levere alle formater til almindelige udtryks- eller mønsterlister, f.eks. datoer, telefonnumre, postnumre og mange andre.

I forbindelse med eksemplet *på tjenestens startdato* er det mere effektivt at bruge den færdigbyggede forklaring til *Dato* i forklaringsbiblioteket:

1. I **afsnittet Forklaring** skal du vælge **Ny** og derefter vælge **Fra forklaringsbibliotek**.
2. Vælg **Dato** i forklaringsbiblioteket. Du kan få vist alle variationer af dato, der genkendes.
3. Vælg **Tilføj**.

    ![Forklaringsbibliotek.](../media/content-understanding/explanation-library.png)

4. På siden **Opret en forklaring** udfylder *datooplysningerne* fra forklaringsbiblioteket automatisk felterne. Vælg **Gem**.

    ![Dato.](../media/content-understanding/date-explanation-library.png)

## <a name="train-the-model"></a>Oplær modellen

Hvis du gemmer din forklaring, startes oplæringen. Hvis din model har tilstrækkelige oplysninger til at udtrække dataene fra dine navngivne eksempelfiler, kan du se hver fil med mærkaten **Match**.

![Matche.](../media/content-understanding/match2.png)

Hvis forklaringen ikke har tilstrækkelige oplysninger til at finde de data, du vil udtrække, får hver fil mærkaten **Uoverensstemmelse**. Du kan vælge **Uoverensstemmende** filer for at få vist flere oplysninger om, hvorfor der opstod en uoverensstemmelse.

## <a name="add-another-explanation"></a>Tilføj en anden forklaring

Ofte er uoverensstemmelsen en indikation af, at den forklaring, vi har angivet, ikke indeholdt tilstrækkelige oplysninger til at udtrække værdien for tjenestens startdato til at matche vores navngivne filer. Du skal muligvis redigere den eller tilføje en anden forklaring.

I vores eksempel kan du se, at tekststrengen *Start Service-datoen* altid kommer før den faktiske værdi. Hvis du vil identificere tjenestens startdato, skal du oprette en sætningsforklaring.

1. I afsnittet Forklaring skal du vælge **Ny** og derefter skrive et navn (f.eks *. præfiksstreng*).
2. Vælg **Udtryksliste** for Type.
3. Brug *tjenestens startdato* som værdien.
4. Vælg **Gem**.

    ![Præfiksstreng.](../media/content-understanding/prefix-string.png)

## <a name="train-the-model-again"></a>Oplær modellen igen

Hvis du gemmer forklaringen, startes oplæringen igen. Denne gang bruges begge forklaringer i eksemplet. Hvis din model har tilstrækkelige oplysninger til at udtrække dataene fra de navngivne eksempelfiler, kan du se hver fil med mærkaten **Match**.

Hvis du igen modtager en **uoverensstemmelse** i dine navngivne filer, skal du sandsynligvis oprette en anden forklaring for at give modellen flere oplysninger for at identificere dokumenttypen eller overveje at foretage ændringer af dine eksisterende filer.

## <a name="test-your-model"></a>Test din model

Hvis du modtager et match på dine mærkede eksempelfiler, kan du nu teste din model på de resterende eksempelfiler, der ikke er forsynet med mærkater. Dette er valgfrit, men et nyttigt trin til at evaluere modellens "fitness" eller parathed, før du bruger den, ved at teste den på filer, som modellen ikke har set før.

1. Vælg fanen **Test** på modellens startside.  Dette kører modellen på dine eksempelfiler, der ikke er navngivet.

2. På listen **Test filer** vises dine eksempelfiler for at vise, om modellen kan udtrække de oplysninger, du har brug for. Brug disse oplysninger til at fastslå klassificeringens effektivitet i identificering af dine dokumenter.

    ![Test af dine filer.](../media/content-understanding/test-filies-extractor.png)

### <a name="further-refine-an-extractor"></a>Forfin en udtrækningsmaskine yderligere

Hvis du har dubletobjekter og kun vil udtrække én værdi eller et bestemt antal værdier, kan du angive en regel for at angive, hvordan den skal behandles. Hvis du vil tilføje en regel for at afgrænse udtrukne oplysninger, skal du følge disse trin:

1. Vælg den udtrækningsenhed, du vil afgrænse, i afsnittet **Objektudtrækninger** på modellens startside, og vælg derefter **Afgræns udtrukne oplysninger**.

    ![Skærmbillede af afsnittet Objektudtrækninger, der viser indstillingen Afgræns udtrukne oplysninger fremhævet.](../media/content-understanding/refine-extracted-info.png)

2. Vælg en af følgende regler på siden **Afgræns udtrukne oplysninger** :

    - Bevar en eller flere af de første værdier
    - Bevar en eller flere af de sidste værdier
    - Fjern dubletværdier
    - Bevar en eller flere af de første linjer
    - Behold en eller flere af de sidste linjer

    ![Skærmbillede af siden Afgræns udtrukne oplysninger, der viser indstillingerne for regler.](../media/content-understanding/refine-extracted-info-page.png)

3. Angiv det antal linjer eller værdier, du vil bruge, og vælg derefter **Afgræns**.

4. Hvis du vil redigere en regel ved at ændre antallet af linjer eller værdier, skal du vælge den udtrækning, du vil redigere, vælge **Afgræns udtrukne oplysninger**, ændre tallet og derefter vælge **Gem**.

5. Når du tester udtrækningen, kan du se afgrænsning i kolonnen **Afgrænsningsresultat** på listen **Test filer** .

    ![Listen Test filer, der viser kolonnen Afgrænsningsresultat.](../media/content-understanding/test-filies-extractor-2.png)

6. Hvis du vil slette en afgrænsningsregel i en udtrækningsmaskine, skal du vælge den udtrækningsmaskine, hvorfra du vil fjerne reglen, vælge **Afgræns udtrukne oplysninger** og derefter vælge **Slet**.

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Forklaringstyper](explanation-types-overview.md)

[Udnyt ordbankens taksonomi, når du opretter en udtrækningsfunktion](leverage-term-store-taxonomy.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Anvend en model](apply-a-model.md)

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)
