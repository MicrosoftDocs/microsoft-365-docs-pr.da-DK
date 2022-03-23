---
title: Forklaringstyper i Microsoft SharePoint Syntex
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
description: Få mere at vide om udtryksliste, regulære udtryk og afstandsforklaringstyper i Microsoft SharePoint Syntex.
ms.openlocfilehash: 71c7379b3a9fcd71b996da5eefd18b6aaaef5016
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589826"
---
# <a name="explanation-types-in-microsoft-sharepoint-syntex"></a>Forklaringstyper i Microsoft SharePoint Syntex

Forklaringer bruges til at definere de oplysninger, du vil navnte og udtrække i dokumentets forståelse af modeller i Microsoft SharePoint Syntex. Når du opretter en forklaring, skal du vælge en forklaringstype. Denne artikel hjælper dig med at forstå de forskellige forklaringstyper, og hvordan de bruges.

![Skærmbillede af panelet Opret en forklaring, der viser de tre forklaringstyper.](../media/content-understanding/explanation-types.png)

Disse forklaringstyper er tilgængelige:

- [**Liste over**](#phrase-list) udtryk: Liste over ord, sætninger, tal eller andre tegn, du kan bruge i det dokument eller de oplysninger, du udtrækker. Tekststrengen, der refererer *til læge* , findes f.eks. i alle lægehenvisningsdokumenter, du identificerer. Eller *telefonnummeret på* den refererende læge fra alle lægehenvisningsdokumenter, som du identificerer.

- [**Regulært**](#regular-expression) udtryk: Bruger en mønstersammenholdelses-notation til at finde bestemte tegnmønstre. Du kan f.eks. bruge et regulært udtryk til at finde alle forekomster *af et* mailadressemønster i et sæt af dokumenter.

- [**Afstand**](#proximity): Beskriver, hvor tæt forklaringer er på hinanden. En liste med udtryk  i gadenummer vises f.eks.  lige før listen med gadenavne uden nogen tokens imellem (du får mere at vide om tokens senere i denne artikel). Brugen af afstandstypen kræver, at du har mindst to forklaringer i modellen, ellers deaktiveres indstillingen.

## <a name="phrase-list"></a>Liste over udtryk

Forklaringstypen Udtryksliste bruges typisk til at identificere og klassificere et dokument gennem din model. Som beskrevet i eksemplet  med henvisning til lægemærkat er det en streng med ord, sætninger, tal eller tegn, der konsekvent findes i de dokumenter, du identificerer.

Selvom det ikke er et krav, kan du opnå bedre succes med din forklaring, hvis den sætning, du optager, er placeret på en ensartet placering i dokumentet. Eksempelvis kan den *refererende lægemærkat* være konsekvent placeret i dokumentets første afsnit. Du kan også bruge indstillingen Konfigurer, hvor udtryk forekommer i **[dokumentets](explanation-types-overview.md#configure-where-phrases-occur-in-the-document)** avancerede indstilling til at vælge bestemte områder, hvor udtrykket er placeret, især hvis der er risiko for, at udtrykket kan forekomme flere forskellige steder i dokumentet.

Hvis følsomhed over for store og små bogstaver er et krav til at identificere din etiket, kan du ved hjælp af listetypen udtryk angive det i din  forklaring ved at markere afkrydsningsfeltet Kun nøjagtig brug af store bogstaver.

![Følsomhed over for store og små bogstaver.](../media/content-understanding/case-sensitivity.png)

En udtrykstype er især nyttig, når du opretter en forklaring, der identificerer og udtrækker oplysninger i forskellige formater, f.eks. datoer, telefonnumre og kreditkortnumre. En dato kan f.eks. vises i mange forskellige formater (01-01-2020, 1-1-2020, 01-01-20, 01-01-2020 eller 1. januar 2020). Når du definerer en sætningsliste, bliver din forklaring mere effektiv ved at registrere eventuelle variationer af de data, du forsøger at identificere og udtrække.

I eksemplet *med telefonnummeret* udtrækker du telefonnummeret for hver henvisende læge fra alle medicinske henvisningsdokumenter, som modellen identificerer. Når du opretter forklaringen, skal du skrive de forskellige formater, som et telefonnummer kan vise i dokumentet, så du kan registrere mulige variationer.

![Telefon mønstre for taludtryk.](../media/content-understanding/pattern-list.png)

I dette eksempel skal du i Avanceret **Indstillinger** markere afkrydsningsfeltet Et ciffer fra **0-9** for at genkende hver "0"-værdi, der bruges på listen over udtryk, til at være et vilkårligt ciffer fra 0 til 9.

![Et vilkårligt ciffer fra 0-9.](../media/content-understanding/digit-identity.png)

På samme måde skal du, hvis du opretter en sætningsliste, der indeholder teksttegn, markere afkrydsningsfeltet Bogstavet Et bogstav fra **a-z** for at genkende hvert "a"-tegn, der bruges på listen over udtryk, til at være ethvert tegn fra "a" til "z".

Hvis du f.eks. opretter  en liste med datoudtryk, og du vil sikre dig, at et datoformat som f.eks. 1. januar *2020* genkendes, skal du:

- Føj *aaa 0, 0000* og *aaa 00.0000* til din udtryksliste.
- Sørg for, **at Alle bogstaver fra a-z** også er markeret.

![Et bogstav fra a-z.](../media/content-understanding/any-letter.png)

Hvis du har brug for store bogstaver på listen over udtryk, kan du markere afkrydsningsfeltet Kun **nøjagtigt brug af store** bogstaver. Hvis det første bogstav i måneden skal skrives med stort, skal du i datoeksem blot:

- Føj *Aaa 0, 0000 og* *Aaa 00.0000* til din udtryksliste.
- Sørg for, **at kun nøjagtig stavning af** store bogstaver også er markeret.

![Kun eksakt brug af store bogstaver.](../media/content-understanding/exact-caps.png)

> [!NOTE]
> I stedet for manuelt at oprette en forklaring til en sætningsliste kan du bruge forklaringsbiblioteket til at bruge udtrykslisteskabeloner til en fælles sætningsliste, f.eks. *dato,* *telefonnummer eller kreditkortnummer*.[](explanation-templates.md)

## <a name="regular-expression"></a>Regulært udtryk

En forklaringstype til regulære udtryk gør det muligt at oprette mønstre, der hjælper med at finde og identificere bestemte tekststrenge i dokumenter. Du kan bruge regulære udtryk til hurtigt at fortolke store mængder tekst til:

- Find bestemte tegnmønstre.
- Valider tekst for at sikre, at den svarer til et foruddefineret mønster (f.eks. en mailadresse).
- Udtræk, rediger, erstat eller slet tekstunderstrenge.

En almindelig udtrykstype er især nyttig, når du opretter en forklaring, der identificerer og udtrækker oplysninger i lignende formater, f.eks. mailadresser, bankkontonumre eller URL-adresser. Eksempelvis vises en mailadresse, f.eks. megan@contoso.com, i et bestemt mønster ("megan" er den første del, og "com" er den sidste del).

Det regulære udtryk for en mailadresse er: **[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+.[ A-Za-z]{2,6}**.

Dette udtryk består af fem dele i denne rækkefølge:

1. En vilkårlig mængde af følgende tegn:

   a. Bogstaver fra a til z

   b. Tal fra 0-9

   c. Periode, understregningstegn, procent eller bindestreg

2. @-symbolet

3. En vilkårlig mængde af de samme tegn som den første del af mailadressen

4. Et punktum

5. To til seks bogstaver

Sådan tilføjes en forklaringstype til regulære udtryk:

1. Vælg **Regulært udtryk** **under** Forklaringstype i panelet Opret **en forklaring**.

   ![Skærmbillede, der viser panelet Opret en forklaring med Regulært udtryk markeret.](../media/content-understanding/create-regular-expression.png)

2. Du kan enten skrive et udtryk i **tekstfeltet Regulært** udtryk eller vælge **Tilføj et regulært udtryk fra en skabelon**.

   Når du tilføjer et regulært udtryk ved hjælp af en skabelon, tilføjes navnet og det regulære udtryk automatisk i tekstfeltet. Hvis du f.eks. vælger **skabelonen** Mailadresse, **udfyldes panelet** Opret en forklaring.

   ![Skærmbillede, der viser panelet Opret en forklaring med anvendt mailadresseskabelon.](../media/content-understanding/create-regular-expression-email.png)

### <a name="limitations"></a>Begrænsninger

Følgende tabel viser indstillinger for indbyggede tegn, der aktuelt ikke er tilgængelige til brug i regulære udtryksmønstre.

|Indstilling  |Stat  |Aktuel funktionalitet  |
|---------|---------|---------|
|Følsomhed over for store og små bogstaver | Understøttes ikke i øjeblikket. | Der kan ikke foretages store og små bogstaver i alle resultater, der udføres.  |
|Stregankre     | Understøttes ikke i øjeblikket. | Det er ikke muligt at angive en bestemt placering i en streng, hvor der skal forekomme et match.   |

## <a name="proximity"></a>Afstand

Afstandsforklaringstypen hjælper modellen med at identificere data ved at definere, hvor tæt et andet datastykke er på dem. I modellen kan du f.eks. sige, at du har defineret to forklaringer, der både mærker kundens *adressenummer* *og telefonnummer*.

Bemærk, at kundens telefonnumre altid vises før postadressenummeret.

Alex Wilburn<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Brug afstandsforklaringen til at definere, hvor langt væk forklaringen af telefonnummeret er, for bedre at identificere postadressenummeret i dine dokumenter.

![Afstandsforklaring.](../media/content-understanding/proximity.png)

> [!NOTE]
> Regulære udtryk kan i øjeblikket ikke bruges med afstandsforklaringstypen.

#### <a name="what-are-tokens"></a>Hvad er tokens?

Hvis du vil bruge afstandsforklaringstypen, skal du forstå, hvad et token er. Antallet af tokens bruges til at se, hvordan afstandsforklaringen måler afstanden fra én forklaring til en anden. Et token er et kontinuert tidsrum (ikke mellemrum eller tegnsætning) af bogstaver og tal.

Følgende tabel viser eksempler på, hvordan du bestemmer antallet af tokens i en sætning.

|Udtryk|Antal tokens|Forklaring|
|--|--|--|
|`Dog`|1|Et enkelt ord uden tegnsætning eller mellemrum.|
|`RMT33W`|1|Et postsøgernummer. Det kan indeholde tal og bogstaver, men ikke tegnsætning.|
|`425-555-5555`|5|Et telefonnummer. Hvert tegnsætningstegn er et enkelt token, så det `425-555-5555` er fem tokens:<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555` |
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`<br>|

#### <a name="configure-the-proximity-explanation-type"></a>Konfigurere afstandsforklaringstypen

I eksemplet skal du konfigurere afstandsindstillingen til at definere området for antallet af tokens i forklaringen af telefonnummeret fra *adressenummerets* forklaring. Bemærk, at minimumintervallet er "0", fordi der ikke er nogen tokens mellem telefonnummeret og postadressenummeret.

Men nogle telefonnumre i eksempeldokumenterne er tilføjet med *(mobil)*.

Nestor Wilke<br>
111-111-1111 (mobil)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Der er tre tokens i *(mobil)*:

|Udtryk|Antal tokens|
|--|--|
|(|1|
|mobil|2|
|)|3|

Konfigurer afstandsindstillingen til at have et område på 0 til 3.

![Eksempel på afstand.](../media/content-understanding/proximity-example.png)

## <a name="configure-where-phrases-occur-in-the-document"></a>Konfigurere, hvor udtryk forekommer i dokumentet

Når du opretter en forklaring, søges der som standard i hele dokumentet efter den sætning, du forsøger at udtrække. Du kan dog bruge indstillingen **Hvor disse** udtryk forekommer avanceret som en hjælp til at isolere en bestemt placering i dokumentet, som et udtryk forekommer på. Denne indstilling er nyttig i situationer, hvor lignende forekomster af et udtryk kan vises et andet sted i dokumentet, og du vil sikre dig, at den rigtige er markeret.

Henvisning til vores eksempel på et lægehenvisningsdokument *, er den refererende* læge altid nævnt i dokumentets første afsnit. Med indstillingen **Where these phrases occur** i dette eksempel kan du konfigurere din forklaring til kun at søge efter denne etiket i begyndelsen af dokumentet eller en anden placering, hvor den kan forekomme.

![Hvor disse udtryk forekommer indstilling.](../media/content-understanding/phrase-location.png)

Du kan vælge følgende indstillinger for denne indstilling:

- Et vilkårligt sted i filen: Hele dokumentet søges efter sætningen.

- Starten af filen: Der søges i dokumentet fra begyndelsen til sætningens placering.

   ![Starten af filen.](../media/content-understanding/beginning-of-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet til at medtage den placering, hvor fasen forekommer. Værdien **for Slutplacering** opdateres for at vise antallet af tokens, som dit valgte område omfatter. Du kan også opdatere **værdien for Slutplacering** for at justere det markerede område.

   ![Feltet Starten af filens placering.](../media/content-understanding/beginning-box.png)

- Slutningen af filen: Der søges i dokumentet fra slutningen til sætningens placering.

   ![Slutningen af filen.](../media/content-understanding/end-of-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet til at medtage den placering, hvor fasen forekommer. Værdien **for Startposition** opdateres, så den viser antallet af tokens, som dit valgte område omfatter. Du kan også opdatere værdien for Startposition for at justere det markerede område.

   ![Feltet Slut på filslut.](../media/content-understanding/end-box.png)

- Brugerdefineret område: Der søges i dokumentet i et bestemt område efter sætningens placering.

   ![Brugerdefineret område.](../media/content-understanding/custom-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet til at medtage den placering, hvor fasen forekommer. Hvis du vil bruge denne indstilling, skal du vælge **en start-** og en **slutplacering** . Disse værdier repræsenterer antallet af tokens fra begyndelsen af dokumentet. Selvom du manuelt kan angive disse værdier, er det nemmere at justere markeringsfeltet manuelt i fremviseren.
    
## <a name="considerations-when-configuring-explanations"></a>Overvejelser i forbindelse med konfiguration af forklaringer
Når du opundervisning en klassificering, er der nogle ting, du skal huske på, som vil give mere forudsigelige resultater:

- Jo flere dokumenter, du træner med, jo mere nøjagtig bliver klassificeringen.  Når det er muligt, skal du bruge mere end 5 gode dokumenter og bruge mere end ét ugyldigt dokument.  Hvis de biblioteker, du arbejder med, indeholder flere forskellige dokumenttyper, fører flere af hver type til mere forudsigelige resultater.
- Mærkater på dokumentet spiller en vigtig rolle i uddannelsesprocessen.  De bruges sammen med forklaringer til at træne modellen.  Du kan få vist nogle anomaler, når du kursus en klassificering med dokumenter, der ikke har en masse indhold i dem.  Forklaringen stemmer muligvis ikke overens med noget i dokumentet, men da det blev mærket som et "godt" dokument, ser du måske, at det matcher under undervisningen.
- Når der oprettes forklaringer, bruges ELLER-logik sammen med navnet for at afgøre, om der er tale om et match.  Regulære udtryk, der bruger OG-logik, kan være mere forudsigelige.  Her er et eksempel på et regulært udtryk, der kan bruges på rigtige dokumenter, mens du lærer dem at finde dem.  Bemærk, at den tekst, der er fremhævet med rødt, er de udtryk, du leder efter.

    <pre>(?=.*network provider)(?=.*participating providers).*</pre>
    
- Etiketter og forklaringer arbejder sammen og bruges i uddannelse af modellen.  Det er ikke en række regler, der kan frakobles og præcis vægtning eller forudsigelse anvendt på hver variabel, der er konfigureret.  Jo større variationen af dokumenter, der bruges i kurset, desto mere nøjagtighed giver modellen.

### <a name="see-also"></a>Se også

[Brug forklaringsskabeloner i SharePoint Syntex](explanation-templates.md)
