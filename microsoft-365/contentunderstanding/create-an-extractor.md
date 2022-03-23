---
title: Opret en extractor Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du opretter en extractor i Microsoft SharePoint Syntex.
ms.openlocfilehash: 1d0aebf610897d07d051ba9e5f3e218dd582bbad
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/19/2022
ms.locfileid: "63588261"
---
# <a name="create-an-extractor-in-microsoft-sharepoint-syntex"></a>Opret en extractor i Microsoft SharePoint Syntex


<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

<br/> 

Før eller efter du opretter en klassificeringsmodel for at automatisere identifikation og klassificering af bestemte dokumenttyper, kan du vælge at tilføje uddrag til modellen for at udtrække bestemte oplysninger fra disse dokumenter. Det kan f.eks. være, at du ikke kun vil  have din model til at identificere alle dokumenter til kontraktfornyelse, der er føjet til dit dokumentbibliotek, men også at vise tjenestens *startdato for hvert* dokument som en kolonneværdi i dokumentbiblioteket.

Du skal oprette en udtrækker for hver enhed i det dokument, du vil udtrække. I vores eksempel vil vi  **udtrækkeServiceStart Datefor**   **eachContract Renewaldocument** , der identificeres af modellen. Vi vil gerne kunne se en visning i dokumentbiblioteket for  **allContract Renewaldocuments**  med en kolonne, der viser værdien for **tjenestens** startdato for hvert dokument. 

> [!NOTE]
> Hvis du vil oprette en extractor, skal du bruge de samme filer, du tidligere har uploadet, til at oplære klassificeringen. 

## <a name="name-your-extractor"></a>Navngive din extractor

1. Fra modellens startside skal du i feltet **Opret udtræk og tog** klikke på **Træudtræk.**

2. På skærmen **Ny enhedsudtrækor** skal du skrive navnet på din extractor i **feltet New extractor name** . Navngive tjenestens startdato **, hvis du vil** udtrække tjenestens startdato fra hvert dokument til fornyelse af kontrakt. Du kan også vælge at genbruge en tidligere oprettet kolonne (f.eks. en kolonne med administrerede metadata).

    Som standard er kolonnetypen **Enkelt tekstlinje**. Hvis du vil ændre kolonnetypen, skal du **vælge Avancerede** >  **indstillingerKolonnetype** og derefter vælge den type, du vil bruge.

    ![Skærmbillede af delen Avancerede indstillinger i panelet Ny enhedsudtræk, der viser indstillingen Kolonnetype.](../media/content-understanding/advanced-settings-column-type.png) 

    > [!NOTE]
    > For udtræk med kolonnetypen **Enkelt tekstlinje er** den maksimale tegngrænse 255. Alle tegn, du indtaster, og som overskrider grænsen, afkortes.

3. Klik på Opret, når du er **færdig**.

## <a name="add-a-label"></a>Tilføj en etiket

Næste trin er at navnmærke den enhed, du vil udtrække i dine eksempelkursusfiler.

Hvis du opretter extractoren, åbnes extractor-siden. Her kan du se en liste over dine eksempelfiler, hvor den første fil på listen vises i fremviseren.

1. Vælg i fremviseren de data, du vil udtrække fra filerne. Hvis du f.eks. vil udtrække *startdatoen*, skal du fremhæve datoværdien i den første fil (mandag *, 14. oktober 2019*). og derefter klikke på **Gem**.  Du bør få vist værdien fra filen på listen Etiketekseler under **kolonnen** Navn.
2. Vælg **Næste fil** for automatisk at gemme og åbne den næste fil på listen i fremviseren. Du kan **også vælge** Gem og derefter vælge en anden fil **på listen Med etiketter.**
3. Gentag trin 1 og 2 i fremviseren, og gentag derefter, indtil du har gemt navnet i alle fem filer.

    ![Avancerede indstillinger.](../media/content-understanding/select-service-start-date.png) 

 
Når du har markeret fem filer, vises der et meddelelsesbanner, der informerer dig om at gå til uddannelse. Du kan vælge at navnmærke flere dokumenter eller gå videre til kurser. 

### <a name="use-find-to-search-your-file"></a>Brug Find til at søge i din fil

Du kan bruge funktionen **Søg** til at søge efter en enhed i dokumentet, som du vil navnmærke.

   ![Søg i fil.](../media/content-understanding/find-feature.png) 

Funktionen Søg er nyttig, hvis du søger i et stort dokument, eller hvis der er flere forekomster af enheden i dokumentet. Hvis du finder flere forekomster, kan du vælge den, du skal bruge i søgeresultaterne, for at gå til den pågældende placering i fremviseren for at markere den.


## <a name="add-an-explanation"></a>Tilføj en forklaring

I vores eksempel skal vi oprette en forklaring, der giver et tip om selve enhedsformatet, og variationer, det kan have i eksempeldokumenterne. En datoværdi kan f.eks. være i en række forskellige formater, f.eks.:
- 10/14/2019
- 14. oktober 2019
- mandag d. 14. oktober 2019
 

Du kan oprette en forklaring *på et mønster for* at identificere tjenestens startdato.

1. I sektionen Forklaring skal du vælge **Ny og** skrive et navn (f.eks. *Dato*).
2. Under Type skal du vælge **Liste over mønstre**.
3. For Værdi skal du angive datovariationen, som de vises i eksempelfilerne. Hvis du f.eks. har datoformater, der vises som 00-00-0000, skal du angive de variationer, der vises i dine dokumenter, f.eks.:
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. Vælg **Gem**.

> [!NOTE]
> Du kan få mere at vide om forklaringstyper under [Forklaringstyper](./explanation-types-overview.md).  


### <a name="use-the-explanation-library"></a>Brug af forklaringsbiblioteket

Ved at oprette forklaringer til elementer som datoer er det nemmere at [bruge forklaringsbiblioteket](./explanation-types-overview.md) end at angive alle variationer manuelt. Forklaringsbiblioteket er et sæt af foruddefinerede udtryk og mønsterforklaringer. Biblioteket forsøger at give alle formater til almindelige udtryk eller mønsterlister, f.eks. datoer, telefonnumre, postnumre og mange andre. 

For eksempel *på tjenestens startdato* er det mere effektivt at bruge den indbyggede forklaring til *Dato* i forklaringsbiblioteket:

1. I sektionen **Forklaring skal** du vælge **Ny** og derefter vælge **Fra forklaringsbibliotek**.
2. Vælg Dato i **forklaringsbiblioteket**. Du kan få vist alle variationer af dato, der genkendes.
3. Vælg **Tilføj**.

    ![Forklaringsbibliotek.](../media/content-understanding/explanation-library.png) 

4. På siden **Opret en forklaring** *udfylder datooplysningerne* fra forklaringsbiblioteket automatisk felterne. Vælg **Gem**.

    ![Dato.](../media/content-understanding/date-explanation-library.png) 

## <a name="train-the-model"></a>Træn modellen 

Start kurset med at gemme forklaringen. Hvis modellen har tilstrækkeligt med oplysninger til at udtrække data fra dine etiketterede eksempelfiler, får du vist hver fil med navnet **Match**.  

![Match.](../media/content-understanding/match2.png) 

Hvis forklaringen ikke har nok oplysninger til at finde de data, du vil udtrække, bliver hver fil markeret **med Uoverensstemmelse**. Du kan klikke på filer, der **ikke stemmer overens** , for at få vist flere oplysninger om, hvorfor der var en uoverensstemmelse.


## <a name="add-another-explanation"></a>Tilføj en anden forklaring

Ofte indikerer uoverensstemmelsen, at den forklaring, vi gav, ikke gav nok oplysninger til at udtrække værdien for tjenestens startdato, så den svarer til vores etiketfiler. Du skal muligvis redigere den eller tilføje en anden forklaring.

Bemærk i vores eksempel, at tekststrengens *startdato altid* står før den faktiske værdi. For at identificere tjenestens startdato skal du oprette en sætningsforklaring.

1. I sektionen Forklaring skal du vælge **Ny** og derefter skrive et navn (f.eks. *Præfiksstreng*).
2. Ud for Type skal du vælge **Listen Udtryk**.
3. Brug *Tjenestens startdato* som værdien.
4. Vælg **Gem**.

    ![Præfiksstreng.](../media/content-understanding/prefix-string.png) 

## <a name="train-the-model-again"></a>Træn modellen igen

Når du gemmer forklaringen, startes træningen igen, denne gang med begge forklaringer i eksemplet. Hvis modellen har nok oplysninger til at udtrække dataene fra de etiketterede eksempelfiler, kan du se hver fil med navnet **Match**. 

Hvis du igen modtager en  uoverensstemmelse på dine mærkede filer, skal du sandsynligvis oprette en anden forklaring for at levere modellen flere oplysninger for at identificere dokumenttypen, eller du kan overveje at foretage ændringer i de eksisterende.

## <a name="test-your-model"></a>Test din model

Hvis du modtager et match på dine etikette eksempelfiler, kan du nu teste din model på de resterende eksempelfiler uden navn. Dette er valgfrit, men et nyttigt trin til at evaluere "fitness" eller parathed af modellen, før du bruger den, ved at teste den på filer, modellen ikke har set før.

1. Klik på fanen Test fra **modellens** startside.  Dette kører modellen på dine ikke-navnerede eksempelfiler.
2. På listen **Test filer** vises dine eksempelfiler for at vise, om modellen kan udtrække de oplysninger, du skal bruge. Brug disse oplysninger til at bestemme effektiviteten af din klassificering til at identificere dine dokumenter.

    ![Test på dine filer.](../media/content-understanding/test-filies-extractor.png) 

## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Forklaringstyper](explanation-types-overview.md)

[Brug term store-taksonomi ved oprettelse af en extractor](leverage-term-store-taxonomy.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Anvend en model](apply-a-model.md) 

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)
