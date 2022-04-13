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
description: Få mere at vide om typerne af udtryksliste, regulære udtryk og forklaringstyper for nærhed i Microsoft SharePoint Syntex.
ms.openlocfilehash: ae31ee3e4d9550c54f884360f3beea960db47b20
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824778"
---
# <a name="explanation-types-in-microsoft-sharepoint-syntex"></a>Forklaringstyper i Microsoft SharePoint Syntex

Forklaringer bruges som en hjælp til at definere de oplysninger, du vil navngive og udtrække i dit dokument, og forstå modeller i Microsoft SharePoint Syntex. Når du opretter en forklaring, skal du vælge en forklaringstype. Denne artikel hjælper dig med at forstå de forskellige forklaringstyper, og hvordan de bruges.

![Skærmbillede af panelet Opret en forklaring, der viser de tre forklaringstyper.](../media/content-understanding/explanation-types.png)

Disse forklaringstyper er tilgængelige:

- [**Udtryksliste**](#phrase-list): Liste over ord, udtryk, tal eller andre tegn, du kan bruge i det dokument eller de oplysninger, du uddrager. Tekststrengens *henvisende læge* findes f.eks. i alle de referencedokumenter, du identificerer. Eller *telefonnummeret* på den henvisende læge fra alle dokumenter om henvisning til læge, som du identificerer.

- [**Regulært udtryk**](#regular-expression): Bruger en notation, der matcher et mønster, til at finde bestemte tegnmønstre. Du kan f.eks. bruge et regulært udtryk til at finde alle forekomster af et *mailadressemønster* i et sæt dokumenter.

- [**Nærhed**](#proximity): Beskriver, hvor tætte forklaringer er på hinanden. En *liste med gadenummerudtryk* går f.eks. lige før *listen over gadenavneudtryk* uden tokens imellem (du får mere at vide om tokens senere i denne artikel). Brug af nærhedstypen kræver, at du har mindst to forklaringer i din model, ellers deaktiveres indstillingen.

## <a name="phrase-list"></a>Udtryksliste

En forklaringstype for sætningslisten bruges typisk til at identificere og klassificere et dokument via din model. Som beskrevet i eksemplet *med* henvisningslægemærkaten er det en streng af ord, sætninger, tal eller tegn, der konsekvent findes i de dokumenter, du identificerer.

Selvom det ikke er et krav, kan du opnå bedre succes med din forklaring, hvis det udtryk, du registrerer, er placeret på en ensartet placering i dit dokument. Mærkaten *for den henvisende læge* kan f.eks. være placeret konsekvent i dokumentets første afsnit. Du kan også bruge indstillingen **[Konfigurer, hvor udtryk forekommer i dokumentets](explanation-types-overview.md#configure-where-phrases-occur-in-the-document)** avancerede indstilling til at vælge bestemte områder, hvor udtrykket er placeret, især hvis der er risiko for, at udtrykket kan forekomme flere steder i dokumentet.

Hvis forskel på store og små bogstaver er et krav til identifikation af mærkaten, kan du bruge udtrykslistetypen til at angive det i forklaringen ved at markere afkrydsningsfeltet **Kun nøjagtig brug af store bogstaver** .

![Forskel på små og små bogstaver.](../media/content-understanding/case-sensitivity.png)

En udtrykstype er især nyttig, når du opretter en forklaring, der identificerer og udtrækker oplysninger i forskellige formater, f.eks. datoer, telefonnumre og kreditkortnumre. En dato kan f.eks. vises i mange forskellige formater (1/1/2020, 1-1-2020, 01/01/20, 01/01/2020 eller 1. januar 2020). Hvis du definerer en udtryksliste, bliver din forklaring mere effektiv ved at registrere eventuelle variationer i de data, du forsøger at identificere og udtrække.

I eksemplet med *telefonnummeret* skal du udtrække telefonnummeret til hver henvisende læge fra alle de lægehenvisningsdokumenter, som modellen identificerer. Når du opretter forklaringen, skal du skrive de forskellige formater, som et telefonnummer kan vise i dokumentet, så du kan registrere mulige variationer.

![Telefon mønstre for taludtryk.](../media/content-understanding/pattern-list.png)

I dette eksempel **skal du i Avanceret Indstillinger** markere afkrydsningsfeltet **Et vilkårligt ciffer fra 0-9** for at genkende hver "0"-værdi, der bruges på udtrykslisten, som et vilkårligt ciffer fra 0 til og med 9.

![Et vilkårligt ciffer fra 0-9.](../media/content-understanding/digit-identity.png)

Hvis du på samme måde opretter en udtryksliste, der indeholder teksttegn, skal du markere afkrydsningsfeltet **Ethvert bogstav fra a-z** for at genkende hvert "a"-tegn, der bruges på udtrykslisten, til et vilkårligt tegn fra "a" til "z".

Hvis du f.eks. opretter en **liste med datoudtryk** , og du vil sikre dig, at et datoformat som f.eks. *den 1. januar 2020* genkendes, skal du gøre følgende:

- Føj *aaa 0, 0000* og *aaa 00, 0000* til din udtryksliste.
- Sørg for, at **Alle bogstaver fra a-z** også er markeret.

![Et hvilket som helst brev fra a-z.](../media/content-understanding/any-letter.png)

Hvis du har krav til store bogstaver på udtrykslisten, kan du markere afkrydsningsfeltet **Kun nøjagtig brug af store bogstaver** . Hvis du i datoeksepelet kræver, at det første bogstav i måneden angives med stort, skal du:

- Føj *Aaa 0, 0000* og *Aaa 00, 0000* til din udtryksliste.
- Sørg for, at **kun nøjagtig brug af store bogstaver** også er valgt.

![Kun nøjagtig brug af store bogstaver.](../media/content-understanding/exact-caps.png)

> [!NOTE]
> I stedet for at oprette en forklaring på en udtryksliste manuelt kan du bruge [forklaringsbiblioteket](explanation-templates.md) til at bruge skabeloner til udtrykslister til en almindelig *udtryksliste*, f.eks. dato, *telefonnummer* eller *kreditkortnummer*.

## <a name="regular-expression"></a>Regulært udtryk

En forklaringstype for regulære udtryk giver dig mulighed for at oprette mønstre, der hjælper med at finde og identificere visse tekststrenge i dokumenter. Du kan bruge regulære udtryk til hurtigt at fortolke store mængder tekst til:

- Find specifikke tegnmønstre.
- Valider tekst for at sikre, at den svarer til et foruddefineret mønster (f.eks. en mailadresse).
- Udtræk, rediger, erstat eller slet tekstunderstrenge.

En type regulært udtryk er især nyttig, når du opretter en forklaring, der identificerer og udtrækker oplysninger i lignende formater, f.eks. mailadresser, bankkontonumre eller URL-adresser. En mailadresse, f.eks. megan@contoso.com, vises f.eks. i et bestemt mønster ("Megan" er den første del, og "com" er den sidste del).

Det regulære udtryk for en mailadresse er: **[A-Za-z0-9._%-]+@[A-Za-z0-9.-]+.[ A-Za-z]{2,6}**.

Dette udtryk består af fem dele i denne rækkefølge:

1. En vilkårlig mængde af følgende tegn:

   a. Bogstaver fra a til z

   b. Tal fra 0-9

   c. Periode, understregningstegn, procent eller streg

2. Symbolet @

3. En vilkårlig mængde af de samme tegn som den første del af mailadressen

4. Et punktum

5. To til seks bogstaver

Sådan tilføjer du en forklaringstype for regulært udtryk:

1. Vælg **Regulært udtryk** i panelet **Opret en forklaring** under **Forklaringstype**.

   ![Skærmbillede, der viser panelet Opret en forklaring med Regulært udtryk valgt.](../media/content-understanding/create-regular-expression.png)

2. Du kan enten skrive et udtryk i tekstfeltet **Regulært udtryk** eller vælge **Tilføj et regulært udtryk fra en skabelon**.

   Når du tilføjer et regulært udtryk ved hjælp af en skabelon, føjes navnet og det regulære udtryk automatisk til tekstfeltet. Hvis du f.eks. vælger **skabelonen Mailadresse** , udfyldes panelet **Opret en forklaring** .

   ![Skærmbillede, der viser panelet Opret en forklaring med skabelonen Mailadresse anvendt.](../media/content-understanding/create-regular-expression-email.png)

### <a name="limitations"></a>Begrænsninger

I følgende tabel vises indbyggede tegnindstillinger, der i øjeblikket ikke er tilgængelige til brug i regulære udtryksmønstre.

|Mulighed|Staten|Aktuel funktionalitet|
|---|---|---|
|Forskel på små og små bogstaver|Understøttes ikke i øjeblikket.|Der skelnes ikke mellem store og små bogstaver i alle de udførte matches.|
|Stregankre|Understøttes ikke i øjeblikket.| Det er ikke muligt at angive en bestemt placering i en streng, hvor der skal være et match.|

## <a name="proximity"></a>Nærhed

Forklaringstypen for nærhed hjælper din model med at identificere data ved at definere, hvor tæt en anden datadel er på dem. I din model kan du f.eks. sige, at du har defineret to forklaringer, der angiver både kundens *gadeadressenummer* og *telefonnummer*.

Bemærk, at kundetelefonnumre altid vises før adressenummeret.

Alex Wilburn<br>
555-555-5555<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Brug nærhedsforklaringen til at definere, hvor langt væk forklaringen på telefonnummeret er, for bedre at identificere adressenummeret i dine dokumenter.

![Nærhedsforklaring.](../media/content-understanding/proximity.png)

> [!NOTE]
> Regulære udtryk kan i øjeblikket ikke bruges med forklaringstypen nærhed.

#### <a name="what-are-tokens"></a>Hvad er tokens?

Hvis du vil bruge forklaringstypen nærhed, skal du forstå, hvad et token er. Antallet af tokens er, hvordan nærhedsforklaringen måler afstanden fra én forklaring til en anden. Et token er et fortløbende mellemrum (uden mellemrum eller tegnsætning) af bogstaver og tal.

I følgende tabel vises eksempler på, hvordan du bestemmer antallet af tokens i et udtryk.

|Sætning|Antal tokens|Forklaring|
|---|---|---|
|`Dog`|1|Et enkelt ord uden tegnsætning eller mellemrum.|
|`RMT33W`|1|Et nummer til postsøger. Det kan indeholde tal og bogstaver, men ikke tegnsætning.|
|`425-555-5555`|5|Et telefonnummer. Hvert tegnsætningstegn er et enkelt token, så `425-555-5555` det er 5 tokens:<br>`425`<br>`-`<br>`555`<br>`-`<br>`5555`|
|`https://luis.ai`|7|`https`<br>`:`<br>`/`<br>`/`<br>`luis`<br>`.`<br>`ai`|

#### <a name="configure-the-proximity-explanation-type"></a>Konfigurer forklaringstypen for nærhed

I eksemplet skal du konfigurere nærhedsindstillingen for at definere intervallet for antallet af tokens i *forklaringen til telefonnummeret* fra forklaringen til *adressenummeret* . Bemærk, at minimumintervallet er "0", fordi der ikke er nogen tokens mellem telefonnummer og adressenummer.

Men nogle telefonnumre i eksempeldokumenterne tilføjes med *(mobil)*.

Nestor Wilke<br>
111-111-1111 (mobil)<br>
One Microsoft Way<br>
Redmond, WA 98034<br>

Der er tre tokens i *(mobil)*:

|Sætning|Antal tokens|
|--|--|
|(|1|
|Mobile|2|
|)|3|

Konfigurer nærhedsindstillingen, så den har et interval mellem 0 og 3.

![Eksempel på nærhed.](../media/content-understanding/proximity-example.png)

## <a name="configure-where-phrases-occur-in-the-document"></a>Konfigurer, hvor udtryk forekommer i dokumentet

Når du opretter en forklaring, søges der som standard i hele dokumentet efter det udtryk, du forsøger at udtrække. Du kan dog bruge indstillingen **Hvor disse udtryk forekommer** avanceret til at hjælpe med at isolere en bestemt placering i dokumentet, som et udtryk forekommer. Denne indstilling er nyttig i situationer, hvor lignende forekomster af et udtryk kan blive vist et andet sted i dokumentet, og du vil sikre dig, at den korrekte er valgt.

Den *henvisende læge* nævnes altid i dokumentets første afsnit med henvisningseksempel. Med indstillingen **Hvor disse udtryk forekommer** , kan du i dette eksempel konfigurere din forklaring til kun at søge efter denne mærkat i starten af dokumentet eller en anden placering, hvor det kan forekomme.

![Hvor disse udtryk forekommer indstilling.](../media/content-understanding/phrase-location.png)

Du kan vælge følgende indstillinger for denne indstilling:

- Hvor som helst i filen: Hele dokumentet søges efter udtrykket.

- Starten af filen: Der søges i dokumentet fra starten til sætningsplaceringen.

   ![Starten af filen.](../media/content-understanding/beginning-of-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet for at inkludere den placering, hvor fasen forekommer. Værdien **for Slutposition** opdateres for at vise antallet af tokens, som dit valgte område indeholder. Du kan også opdatere værdien for **slutplaceringen** for at justere det valgte område.

   ![Starten af feltet filplacering.](../media/content-understanding/beginning-box.png)

- Slutningen af filen: Der søges i dokumentet fra slutningen til sætningsplaceringen.

   ![Slutningen af filen.](../media/content-understanding/end-of-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet for at inkludere den placering, hvor fasen forekommer. **Startpositionsværdien** opdateres for at vise antallet af tokens, som det valgte område indeholder. Du kan også opdatere startplaceringsværdien for at justere det valgte område.

   ![Slutning af filslutfelt.](../media/content-understanding/end-box.png)

- Brugerdefineret område: Der søges i dokumentet inden for et angivet område for sætningsplaceringen.

   ![Brugerdefineret område.](../media/content-understanding/custom-file.png)

    I fremviseren kan du manuelt justere markeringsfeltet for at inkludere den placering, hvor fasen forekommer. Til denne indstilling skal du vælge en **start-** og **slutposition** . Disse værdier repræsenterer antallet af tokens fra starten af dokumentet. Selvom du manuelt kan angive disse værdier, er det nemmere at justere markeringsfeltet manuelt i fremviseren.

## <a name="considerations-when-configuring-explanations"></a>Overvejelser i forbindelse med konfiguration af forklaringer

Når du oplærer en klassificering, er der et par ting, du skal være opmærksom på, som giver mere forudsigelige resultater:

- Jo flere dokumenter du oplærer med, jo mere præcis bliver klassificeringen.  Når det er muligt, skal du bruge mere end fem gode dokumenter og bruge mere end ét ugyldigt dokument.  Hvis de biblioteker, du arbejder med, har flere forskellige dokumenttyper, medfører flere af hver type mere forudsigelige resultater.
- Mærkning af dokumentet spiller en vigtig rolle i oplæringsprocessen.  De bruges sammen med forklaringer til at oplære modellen.  Du kan muligvis se nogle uregelmæssigheder, når du oplærer en klassificering med dokumenter, der ikke har meget indhold i dem.  Forklaringen stemmer muligvis ikke overens med noget i dokumentet, men da den er mærket som et "godt" dokument, kan du se, at det er et match under oplæringen.
- Når du opretter forklaringer, bruges OR-logik i kombination med mærkaten til at afgøre, om det er et match.  Regulært udtryk, der bruger AND-logik, kan være mere forudsigeligt.  Her er et eksempel på regulært udtryk, der kan bruges på rigtige dokumenter, når du oplærer dem.  Bemærk, at den tekst, der er fremhævet med rødt, er det eller de udtryk, du vil søge efter.

    <pre>(?=.*network provider)(?=.*participating providers).*</pre>

- Etiketter og forklaringer arbejder sammen og bruges til oplæring af modellen.  Det er ikke en række regler, der kan afkobles og præcise vægte eller forudsigelse anvendes på hver variabel, der er konfigureret.  Jo større variationen af dokumenter, der bruges i oplæringen, giver mere nøjagtighed i modellen.

### <a name="see-also"></a>Se også

[Brug forklaringsskabeloner i SharePoint Syntex](explanation-templates.md)
