---
title: Opret og anvend politikker for administration af oplysninger
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 8ccac9e4-3a50-49fa-a95b-d186032a6ee3
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du konfigurerer en politik for administration af oplysninger for at styre, hvor længe oplysningerne opbevares, og spor, hvem der bruger oplysningerne.
ms.openlocfilehash: d62eea4c43e6c171bf8c640e341933e81a23e0d0
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758965"
---
# <a name="create-and-apply-information-management-policies"></a>Opret og anvend politikker for administration af oplysninger

Politikker for administration af oplysninger gør det muligt for din organisation at styre, hvor længe indhold skal bevares, overvåge, hvad personer gør med indhold, og føje stregkoder eller mærkater til dokumenter. En politik kan hjælpe med at gennemtvinge overholdelse af juridiske og offentlige bestemmelser eller interne forretningsprocesser. Som administrator kan du konfigurere en politik til at styre, hvordan du sporer dokumenter, og hvor længe dokumenter skal gemmes.

Du kan oprette en politik for administration af oplysninger på tre forskellige steder i webstedshierarkiet– fra den bredeste til den smalleste:

- Opret en politik, der skal bruges på flere indholdstyper i en gruppe af websteder.
- Opret en politik for en webstedsindholdstype.
- Opret en politik for en liste eller et bibliotek.

Du kan få flere oplysninger under [Introduktion til politikker for administration af oplysninger](intro-to-info-mgmt-policies.md).

## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Opret en politik for flere indholdstyper i en gruppe af websteder
<a name="__toc261001590"> </a>

Hvis du vil sikre dig, at der anvendes en informationspolitik på alle dokumenter af en bestemt type i en gruppe af websteder, kan du overveje at oprette politikken på niveauet for gruppen af websteder og derefter senere anvende politikken på indholdstyper. Disse kaldes politikker for grupper af websteder.

1. På startsiden \> for gruppen af websteder **Indstillinger**![ SharePoint knappen Indstillinger 2016 på titellinjen.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Webstedet Indstillinger**.

    Klik på **Indstillinger** på et SharePoint gruppeforbundet websted, klik på **Webstedsindhold**, og klik derefter på **Websted Indstillinger**.

2. På siden Indstillinger websted under **Politikskabeloner** for **administration** \> af gruppe af websteder.

   ![Skabelonlink til indholdstypepolitik på siden Indstillinger websted.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Opret **på siden**\> Politikker.

4. Angiv et navn og en beskrivelse af politikken, og skriv derefter en kort politikerklæring, der forklarer brugerne, hvad politikken er beregnet til.

5. Se næste afsnit om oprettelse af politikker for en webstedsindholdstype for at få mere at vide om, hvordan du konfigurerer de funktioner, du vil knytte til politikken.

6. Vælg **OK**.

## <a name="create-a-policy-for-a-site-content-type"></a>Opret en politik for en webstedsindholdstype
<a name="__create_a_policy"> </a>

Hvis du føjer en politik til administration af oplysninger til en indholdstype, er det nemt at knytte politikfunktioner til flere lister eller biblioteker. Du kan vælge at føje en eksisterende politik til administration af oplysninger til en indholdstype eller oprette en entydig politik, der er specifik for en individuel indholdstype.

 Du kan også føje en politik til administration af oplysninger til en indholdstype, der er specifik for lister. Dette medfører, at politikken kun anvendes på elementer på den pågældende liste, der bruger indholdstypen.

1. På startsiden \> for gruppen af websteder **Indstillinger**![ SharePoint knappen Indstillinger 2016 på titellinjen.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Webstedet Indstillinger**.

    Klik på **Indstillinger** på et SharePoint gruppeforbundet websted, klik på **Webstedsindhold**, og klik derefter på **Websted Indstillinger**.

2. På siden Websted Indstillinger under **Gallerier til webdesigner** \> **Webstedsindholdstyper**.

   ![Link til webstedsindholdstyper på siden Indstillinger websted.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)

3. På siden Webstedsindholdstype Indstillinger skal du vælge den indholdstype, du vil føje en politik til.

4. På siden Webstedsindholdstype under **Indstillinger** \> **politikindstillinger for administration af oplysninger**.

5. Angiv et navn og en beskrivelse til politikken på siden Rediger politik, og skriv derefter en kort beskrivelse, der forklarer brugerne, hvad politikken er beregnet til.

6. I de næste afsnit skal du vælge de individuelle politikfunktioner, du vil føje til din politik til administration af oplysninger.

   ![Typer af indholdspolitikker.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)

7. Hvis du vil angive en opbevaringsperiode for dokumenter og elementer, der er omfattet af denne politik, skal du vælge **Aktivér opbevaring** og derefter angive opbevaringsperioden og de handlinger, du vil udføre, når elementerne udløber.

   Sådan angiver du en opbevaringsperiode:

   1. Vælg **Tilføj en opbevaringsfase for poster**.

   2. Vælg en opbevaringsperiodeindstilling for at angive, hvornår dokumenter eller elementer er angivet til at udløbe. Udfør et af følgende trin:
      - Hvis du vil angive udløbsdatoen baseret på en datoegenskab, skal du under **Hændelse** \> **Denne fase være baseret på en datoegenskab på elementet** og derefter vælge handlingen for dokumentet eller elementet (f.eks. Oprettet eller Ændret) og den gradvise forøgelse efter denne handling (f.eks. antallet af dage, måneder eller år), hvor elementet skal udløbe.
      - Hvis du vil bruge en brugerdefineret opbevaringsformel til at bestemme udløb, skal du vælge **Angiv af en brugerdefineret opbevaringsformel, der er installeret på denne server**.

        > [!NOTE]
        > Denne indstilling er kun tilgængelig, hvis administratoren har konfigureret en brugerdefineret formel.

   3. Indstillingen **Start en arbejdsproces** er kun tilgængelig, hvis du definerer en politik for en liste, et bibliotek eller en indholdstype, der allerede har en arbejdsproces tilknyttet. Du får derefter mulighed for at vælge mellem arbejdsprocesser.

   4. I afsnittet **Gentagelse** skal du vælge **Gentag denne fases handling...** og derefter angive, hvor ofte handlingen skal gentages.

      > [!NOTE]
      >  Denne indstilling er kun tilgængelig, hvis den valgte handling kan gentages. Du kan f.eks. ikke angive gentagelse for handlingen **Slet permanent**.

   5. Vælg **OK**.

8. Hvis du vil aktivere overvågning for de dokumenter og elementer, der er omfattet af denne politik, skal du vælge **Aktivér overvågning** og derefter angive de hændelser, du vil overvåge.

   Sådan aktiverer du overvågning:

   1. På siden Rediger politik under **Overvågning** skal du vælge **Aktivér overvågning** og derefter markere afkrydsningsfelterne ud for de hændelser, du vil bevare et overvågningsspor for.

   2. Hvis du vil bede brugerne om at indsætte disse stregkoder i dokumenter, skal du vælge **Bed brugerne om at indsætte en stregkode, før de gemmer eller udskriver**.

   3. Vælg **OK** for at anvende overvågningsfunktionen på politikken.

   Funktionen Overvågningspolitik giver organisationer mulighed for at oprette og analysere overvågningsspor for dokumenter og til at vise elementer, f.eks. opgavelister, problemlister, diskussionsgrupper og kalendere. Denne politikfunktion indeholder en overvågningslog, der registrerer hændelser, f.eks. når indholdet vises, redigeres eller slettes.

   Når overvågning er aktiveret som en del af en politik for administration af oplysninger, kan administratorer få vist overvågningsdataene i politikanvendelsesrapporter, der er baseret på Microsoft Excel, og som opsummerer det aktuelle forbrug. Administratorer kan bruge disse rapporter til at bestemme, hvordan oplysninger bruges i organisationen. Disse rapporter kan også hjælpe organisationer med at bekræfte og dokumentere deres lovmæssige overholdelse af angivne standarder eller med at undersøge potentielle bekymringer.

   Overvågningsloggen registrerer følgende oplysninger: hændelsesnavn, dato og klokkeslæt for hændelsen og systemnavnet på den bruger, der udførte handlingen.

9. Når stregkoder er aktiveret som en del af en politik, føjes de til dokumentegenskaberne og vises i headerområdet i det dokument, som stregkoden anvendes på. På samme måde som med mærkater kan stregkoder også fjernes manuelt fra et dokument. Du kan angive, om brugerne skal blive bedt om at medtage stregkoden, når de udskriver eller gemmer et element, eller om stregkoden skal indsættes manuelt ved hjælp af fanen **Indsæt** i 2010 Office udgivelsesprogrammer.

   Sådan aktiverer du stregkoder:

   1. På siden **Rediger politik** under **Stregkoder** skal du vælge **Aktivér stregkoder**.

   2. Hvis du vil bede brugerne om at indsætte disse stregkoder i dokumenter, skal du vælge **Bed brugerne om at indsætte en stregkode, før de gemmer eller udskriver**.

   3. Vælg **OK** for at anvende stregkodefunktionen på politikken.

   Stregkodepolitikken genererer kode 39 standardstregkoder. Hvert stregkodebillede indeholder tekst under stregkodesymbolet, der repræsenterer stregkodeværdien. Dette gør det muligt at bruge stregkodedataene, selvom scanning af hardware ikke er tilgængelig. Brugerne kan skrive stregkodenummeret manuelt i søgefeltet for at finde elementet på et websted.  <br/> |

10. Hvis du vil kræve, at dokumenter, der er omfattet af denne politik, har mærkater, skal du vælge **Aktivér navne** og derefter angive de ønskede indstillinger for mærkaterne.

    Sådan aktiverer du mærkater:

    1. Hvis du vil kræve, at brugerne skal føje et navn til et dokument, skal du vælge **Spørg brugere, om de vil indsætte en mærkat, før de gemmer eller udskriver**.

       > [!NOTE]
       > Hvis etiketter skal være valgfrie, skal du ikke markere dette afkrydsningsfelt.

    2. Hvis du vil låse en etiket, så den ikke kan ændres, når den er indsat, skal du vælge **Undgå ændringer af mærkater, når de er tilføjet**.

       Denne indstilling forhindrer, at navneteksten opdateres, når navnet er indsat i et element i et klientprogram, f.eks. Word, Excel eller PowerPoint. Hvis etiketten skal opdateres, når egenskaberne for dette dokument eller element opdateres, skal du ikke markere dette afkrydsningsfelt.

    3. I feltet Etiketformat skal du angive teksten til etiketten, som du vil have den vist. Etiketter kan indeholde op til 10 kolonnereferencer, som hver kan indeholde op til 255 tegn. Benyt følgende fremgangsmåde for at oprette formatet for etiketten:
       - Skriv navnene på de kolonner, du vil medtage i etiketten, i den rækkefølge, de skal vises i. Omslut kolonnenavnene med krøllede parenteser ({}), som vist i eksemplet på siden Rediger politik.
       - Skriv ord for at identificere kolonnerne uden for de kantede parenteser, som vist i eksemplet på siden Rediger politik.

    4. Hvis du vil tilføje et linjeskift, **skal du angive\n** , hvor linjeskiftet skal vises.

    5. Vælg den ønskede skriftstørrelse og typografi, og angiv, om etiketten skal placeres til venstre, centreret eller højre i dokumentet.

       Vælg en skrifttype og typografi, der er tilgængelig på brugernes computere. Skriftstørrelsen påvirker, hvor meget tekst der kan vises på etiketten.

    6. Angiv etikettens højde og bredde. Navnehøjden kan variere fra 0,25 tommer til 20 tommer, og navnebredden kan variere fra 0,25 tommer til 20 tommer. Navnetekst centreres altid lodret på etiketbilledet.

    7. Vælg **Opdater** for at få vist mærkatindholdet.

11. Vælg **OK**.

## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Opret en politik for en liste, et bibliotek eller en mappe (placeringsbaseret opbevaringspolitik)
<a name="__create_a_policy"> </a>

Du kan definere en opbevaringspolitik, der kun gælder for en bestemt liste, et bibliotek eller en bestemt mappe. Men hvis du opretter en opbevaringspolitik på denne måde, kan du ikke genbruge denne politik på andre lister, biblioteker, mapper eller websteder, og du kan ikke anvende en politik for grupper af websteder på en placeringsbaseret politik.

Hvis du vil anvende en enkelt opbevaringspolitik på alle typer indhold på en enkelt placering, vil du sandsynligvis bruge placeringsbaseret opbevaring. I de fleste andre tilfælde skal du bekræfte, at der er angivet en opbevaringspolitik for alle indholdstyper.

Hver undermappe nedarver opbevaringspolitikken for dens overordnede, medmindre du vælger at bryde nedarvning og definerer en ny opbevaringspolitik på det underordnede niveau.

Hvis du vil definere en anden politik for administration af oplysninger end opbevaring til en liste eller et bibliotek, skal du definere en politik for administration af oplysninger for hver enkelt listeindholdstype, der er knyttet til listen eller biblioteket.

Hvis du på et tidspunkt beslutter at skifte fra indholdstype til placeringsbaserede politikker for en liste eller et bibliotek, er det kun opbevaringspolitikken, der bruges som den placeringsbaserede politik. Alle andre administrationspolitikker (overvågninger, stregkoder og stregkoder) nedarves fra de tilknyttede indholdstyper.

Placeringsbaserede politikker kan deaktiveres for en gruppe af websteder ved at deaktivere funktionen Biblioteks- og mappebaseret opbevaring. Dette gør det muligt for administratorer af grupper af websteder at sikre, at deres indholdstypepolitikker ikke tilsidesættes af en listeadministrators placeringsbaserede politikker.

Du skal som minimum have tilladelse til at administrere lister for at ændre politikindstillingerne for administration af oplysninger for en liste eller et bibliotek.

1. Gå til den liste eller det bibliotek, du vil angive en politik for administration af oplysninger for.

2. På båndet skal du vælge **biblioteks-** eller **listefanen** \> **Bibliotek Indstillinger** eller **Liste Indstillinger**.

   I SharePoint Online skal du klikke på **Indstillinger** og derefter klikke på **Listeindstillinger** eller **Biblioteksindstillinger**.

3. Under Indstillinger **for politik for administration af** **tilladelser og administrationsoplysninger**\>.

   ![Link til politikker for administration af oplysninger på indstillingssiden for dokumentbiblioteket.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. På siden Politik for administration af oplysninger Indstillinger skal du sørge for, at opbevaringskilden for listen eller biblioteket er angivet til Bibliotek og mapper.

   Hvis **indholdstypen** vises som kilden, skal du klikke på **Skift kilde** og derefter klikke på **Bibliotek og mapper**. Du får besked om, at opbevaringspolitikker for indholdstyper ignoreres. Vælg **OK**.

5. Angiv en kort beskrivelse af den politik, du opretter, under **Biblioteksbaseret opbevaringsplan** på siden Rediger politik.

6. Vælg **Tilføj en opbevaringsfase...**

   Bemærk, at under Poster kan du vælge at definere forskellige opbevaringspolitikker for poster ved at vælge indstillingen Definer forskellige opbevaringsfaser for poster.

7. I dialogboksen Egenskaber for fase skal du vælge en indstilling for opbevaringsperiode for at angive, hvornår dokumenter eller elementer er angivet til at udløbe. Gør et af følgende:

   - Hvis du vil angive udløbsdatoen baseret på en datoegenskab, skal du under **Hændelse** \> **Denne fase være baseret på en datoegenskab på elementet** og derefter vælge handlingen for dokumentet eller elementet (f.eks. Oprettet eller Ændret) og den gradvise forøgelse efter denne handling (f.eks. antallet af dage, måneder eller år), hvor elementet skal udløbe.

   - Hvis du vil bruge en brugerdefineret opbevaringsformel til at bestemme udløb, skal du vælge **Angiv af en brugerdefineret opbevaringsformel, der er installeret på denne server**.

     > [!NOTE]
     >  Denne indstilling er kun tilgængelig, hvis administratoren har konfigureret en brugerdefineret formel.

   - Under **Handling** skal du angive, hvad der skal ske, når dokumentet eller elementet udløber. Hvis du vil aktivere en bestemt handling for dokumentet eller elementet (f.eks. sletning), skal du vælge en handling på listen.

8. Indstillingen **Start en arbejdsproces** er kun tilgængelig, hvis du definerer en politik for en liste, et bibliotek eller en indholdstype, der allerede har en arbejdsproces tilknyttet. Du får derefter mulighed for at vælge mellem arbejdsprocesser.

9. Under **Gentagelse** skal du vælge **Gentag denne fases handling...** og angive, hvor ofte handlingen skal gentages.

   > [!NOTE]
   >  Denne indstilling er kun tilgængelig, hvis den valgte handling kan gentages. Du kan f.eks. ikke angive gentagelse for handlingen **Slet permanent**.

10. Vælg **OK**.

## <a name="apply-a-site-collection-policy-to-a-content-type"></a>Anvend en politik for en gruppe af websteder på en indholdstype
<a name="__apply_a_site"> </a>

Hvis der allerede er oprettet politikker for administration af oplysninger for dit websted som politikker for grupper af websteder, kan du anvende en af politikkerne på en indholdstype. Ved at gøre dette kan du anvende den samme politik på flere indholdstyper i en gruppe af websteder, der ikke deler den samme overordnede indholdstype.

 Hvis du vil anvende politikker på flere indholdstyper i en gruppe af websteder, og du har konfigureret en administreret metadatatjeneste, kan du bruge publicering af indholdstype til at publicere politikker for administration af oplysninger til flere grupper af websteder. Se afsnittet [Anvend en politik på tværs af grupper af websteder](#apply-a-policy-across-site-collections) for at få flere oplysninger.

1. Gå til den liste eller det bibliotek, der indeholder den indholdstype, du vil anvende en politik på.

2. På båndet skal du vælge **biblioteks-** eller **listefanen** \> **Bibliotek Indstillinger** eller **Liste Indstillinger**.

   I SharePoint Online skal du klikke på **Indstillinger** og derefter klikke på **Listeindstillinger** eller **Biblioteksindstillinger**.

3. Under Indstillinger **for politik for administration af** **tilladelser og administrationsoplysninger**\>.

   ![Link til politikker for administration af oplysninger på indstillingssiden for dokumentbiblioteket.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Kontrollér, at politikkilden er angivet til **Indholdstyper**, og vælg den indholdstype, du vil anvende politikken på, under **Indholdstypepolitikker** .

5. Under **Angiv politikken** \> **Brug en politik for en gruppe af websteder**, og vælg derefter den politik, du vil anvende, på listen.

   > [!NOTE]
   >  Hvis politikindstillingen **Brug en gruppe af websteder** ikke er tilgængelig, er der ikke defineret nogen politikker for gruppen af websteder for gruppen af websteder.

6. Vælg **OK**.

   Hvis den liste eller det bibliotek, du arbejder med, understøtter administration af flere indholdstyper, kan du under **Indholdstyper** vælge den indholdstype, du vil angive en politik for administration af oplysninger for. Dette fører dig direkte til trin 5 ovenfor.

## <a name="apply-a-policy-across-site-collections"></a>Anvend en politik på tværs af grupper af websteder
<a name="__toc260646789"> </a>

Del indholdstyper på tværs af grupper af websteder ved hjælp af et tjenesteprogram til administrerede metadata for at konfigurere publicering af indholdstyper. Publicering af indholdstyper hjælper dig med at administrere indhold og metadata ensartet på tværs af dine websteder, fordi indholdstyper kan oprettes og opdateres centralt, og opdateringer kan publiceres til flere grupper af websteder, der abonnerer, eller webprogrammer.

## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Opret en skabelon ud fra en eksisterende politik, der skal bruges på tværs af grupper af websteder
<a name="__toc262125409"> </a>

Du kan definere en politik for administration af oplysninger og derefter oprette en skabelon ud fra den, der skal bruges efter behov på tværs af flere grupper af websteder. Denne metode kan bruges, hvis du vil have en sikkerhedskopi af dine informationspolitikker, eller den kan også bruges som en alternativ metode til at bruge publicering af indholdstyper til anvendelse af én politik på tværs af grupper af websteder. Du kan oprette en skabelon eller sikkerhedskopi af politikken ved at eksportere politikken fra én gruppe af websteder og derefter importere den til en gemt placering eller til en anden gruppe af websteder.

> [!IMPORTANT]
> Hvis du bruger funktionen til eksport/import som en måde at oprette et sæt politikskabeloner på, skal du huske på, at der findes et entydigt id i filen .xml politik. Derfor kan du ikke importere denne politik til et websted mere end én gang uden at ændre dette entydige id.

### <a name="export-a-policy"></a>Eksportér en politik
<a name="__toc260646790"> </a>

1. På startsiden for gruppen af websteder skal du vælge **Indstillinger**![ Small Indstillinger gear, der overtog stedet for Websted Indstillinger.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Websted Indstillinger**.

   Klik på **Indstillinger** på et SharePoint gruppeforbundet websted, klik på **Webstedsindhold**, og klik derefter på **Websted Indstillinger**.

2. På siden Indstillinger websted under **Politikskabeloner** for **administration** \> af gruppe af websteder.

   ![Skabelonlink til indholdstypepolitik på siden Indstillinger websted.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Vælg den politik, du vil eksportere \> , rulle til bunden \> **Eksportér**.

4. Vælg **Gem**, når du bliver bedt om at gemme eller åbne filen, og vælg derefter en placering, hvor filen skal gemmes. Sørg for at vælge en placering, der er tilgængelig for de grupper af websteder, der importerer politikken.

5. Når dialogboksen Overførslen er fuldført vises, skal du vælge **Luk**.

### <a name="import-a-policy-to-a-different-site-collection"></a>Importér en politik til en anden gruppe af websteder
<a name="__toc260646791"> </a>

Når du importerer en politik for administration af oplysninger, kan du anvende den på flere indholdstyper på websteds- eller listeniveau i en hvilken som helst gruppe af websteder. Der er to fordele ved at gøre dette: Du behøver ikke at definere og anvende politikken på hver indholdstype igen, og du kan nemmere administrere politikændringer ved kun at foretage ændringer på ét sted.

1. På startsiden for den gruppe af websteder, du vil anvende politikken på, skal du vælge **Indstillinger**![ Små Indstillinger tandhjul, der overtog stedet for Indstillinger.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Websted Indstillinger**.

   Klik på **Indstillinger** på et SharePoint gruppeforbundet websted, klik på **Webstedsindhold**, og klik derefter på **Websted Indstillinger**.

2. På siden Indstillinger websted under **Politikskabeloner** for **administration** \> af gruppe af websteder.

3. **Importér** \> **Gennemse** på siden \> Politikker for at finde XML-filen til politikken.

4. Vælg den XML-fil, hvor politikken er gemt \> **Åbn**.

5. På siden \> Importér en politik for gruppe af websteder skal du **importere** for at føje politikken til gruppen af websteder.

Den importerede politik kan nu anvendes på en eller flere indholdstyper på websteds- eller listeniveau.

Politikker for administration af oplysninger gør det muligt for din organisation at styre, hvor længe indhold skal bevares, overvåge, hvad personer gør med indhold, og føje stregkoder eller mærkater til dokumenter. En politik kan hjælpe med at gennemtvinge overholdelse af juridiske og offentlige bestemmelser eller interne forretningsprocesser. Som administrator kan du konfigurere en politik til at styre, hvordan du sporer dokumenter, og hvor længe dokumenter skal gemmes.

Du kan oprette en politik for administration af oplysninger på tre forskellige steder i webstedshierarkiet– fra den bredeste til den smalleste:

- Opret en politik, der skal bruges på flere indholdstyper i en gruppe af websteder.
- Opret en politik for en webstedsindholdstype.
- Opret en politik for en liste eller et bibliotek.

Du kan få flere oplysninger under [Introduktion til politikker for administration af oplysninger](intro-to-info-mgmt-policies.md).
