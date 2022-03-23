---
title: Oprette og anvende politikker for administration af oplysninger
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
description: Få mere at vide om, hvordan du konfigurerer en politik for administration af oplysninger for at styre, hvor længe oplysninger opbevares, og holde styr på, hvem der bruger oplysningerne.
ms.openlocfilehash: f8a4400e890e02ecd7ac57011770ff4a23a1a5e1
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63587484"
---
# <a name="create-and-apply-information-management-policies"></a>Oprette og anvende politikker for administration af oplysninger

Politikker for administration af oplysninger gør det muligt for organisationen at styre, hvor lang tid indhold opbevares, hvad folk kan gøre med indhold, og føje stregkoder eller etiketter til dokumenter. En politik kan hjælpe med at håndhæve overholdelse af juridiske og statslige love og forordninger eller interne forretningsprocesser. Som administrator kan du konfigurere en politik til at styre, hvordan du kan spore dokumenter, og hvor lang tid dokumenter skal opbevares.

Du kan oprette en politik for administration af oplysninger på tre forskellige steder i webstedshierarkiet fra den bredeste til den smalleste:

- Opret en politik, der skal bruges på flere indholdstyper inden for en gruppe af websteder.
- Opret en politik for en webstedsindholdstype.
- Opret en politik for en liste eller et bibliotek.

Få mere at vide under [Introduktion til politikker for administration af oplysninger](intro-to-info-mgmt-policies.md).

## <a name="create-a-policy-for-multiple-content-types-within-a-site-collection"></a>Opret en politik for flere indholdstyper i en gruppe af websteder
<a name="__toc261001590"> </a>

Overvej at oprette politikken på niveauet for gruppen af websteder for at sikre, at en oplysningspolitik anvendes på alle dokumenter af en bestemt type inden for en gruppe af websteder, og anvend derefter politikken på indholdstyper. Disse kaldes for politikker for grupper af websteder.

1. På startsiden for gruppen af websteder \> **Indstillinger**![ SharePoint 2016 Indstillinger på titellinjen.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Webstedets Indstillinger**.

    Klik på SharePoint websted i et gruppeforbundet websted, **Indstillinger** på Webstedsindhold **, og** klik derefter på **Webstedsindhold Indstillinger**.

2. På siden Webstedstyper Indstillinger under **Politikskabeloner for administration** \> af **indholdstype for gruppe af websteder**.

   ![Linket Politikskabelon til indholdstype på siden Indstillinger websted.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. På siden Politikker Skal du \> **oprette**.

4. Angiv et navn og en beskrivelse af politikken, og skriv derefter en kort politikerklæring, der forklarer over for brugerne, hvad politikken bruges til.

5. Se næste afsnit om oprettelse af politikker for en webstedsindholdstype for at få mere at vide om, hvordan du konfigurerer de funktioner, du vil knytte til politikken.

6. Vælg **OK**.

## <a name="create-a-policy-for-a-site-content-type"></a>Opret en politik for en webstedsindholdstype
<a name="__create_a_policy"> </a>

Når du føjer en politik for administration af oplysninger til en indholdstype, er det nemt at knytte politikfunktioner til flere lister eller biblioteker. Du kan vælge at føje en eksisterende politik for administration af oplysninger til en indholdstype eller oprette en entydig politik, der er specifik for en enkelt indholdstype.

 Du kan også føje en politik for administration af oplysninger til en indholdstype, der er specifik for lister. Dette har den effekt, at politikken kun anvendes på elementer på den pågældende liste, der bruger indholdstypen.

1. På startsiden for gruppen af websteder \> **Indstillinger**![ SharePoint 2016 Indstillinger på titellinjen.](../media/1c22d2d8-39e0-4930-82c6-c3eee44211d3.png) \>**Webstedets Indstillinger**.

    Klik på SharePoint websted i et gruppeforbundet websted, **Indstillinger** på Webstedsindhold **, og** klik derefter på **Webstedsindhold Indstillinger**.

2. På siden Webstedstyper Indstillinger under **Indholdstyper for gallerier til** \> **webdesigner**.

   ![Link til webstedsindholdstyper på Indstillinger side.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)

3. På siden Webstedsindholdstype Indstillinger du vælge den indholdstype, du vil føje en politik til.

4. På siden Webstedsindholdstype skal du under **Indstillinger indstillinger** \> **for politikker for administration af oplysninger**.

5. Angiv et navn og en beskrivelse af politikken på siden Rediger politik, og skriv derefter en kort beskrivelse, som forklarer over for brugerne, hvad politikken er til.

6. I de næste afsnit skal du vælge de enkelte politikfunktioner, du vil føje til din politik for administration af oplysninger.

   ![Typer af indholdspolitikker.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)

7. Hvis du vil angive en opbevaringsperiode for dokumenter og elementer, der er underlagt denne politik, skal du vælge Aktivér opbevaring og derefter angive opbevaringsperioden og de handlinger, der skal udføres, når elementerne udløber.

   Sådan angiver du en opbevaringsperiode:

   1. Vælg **Tilføj en opbevaringsfase for poster**.

   2. Vælg en indstilling for opbevaringsperiode for at angive, hvornår dokumenter eller elementer skal være indstillet til at udløbe. Udfør et af følgende trin:
      - Hvis du vil angive udløbsdatoen baseret på en datoegenskab, skal **du under** \> Hændelse Denne fase er baseret på en datoegenskab for **elementet og derefter** vælge dokument- eller elementhandlingen (f.eks. Oprettet eller Ændret) og det tidsrum efter denne handling (f.eks. antallet af dage, måneder eller år), hvor elementet skal udløbe.
      - Hvis du vil bruge en brugerdefineret opbevaringsformel til at bestemme udløb, skal du **vælge Angiv af en brugerdefineret opbevaringsformel, der er installeret på denne server**.

        > [!NOTE]
        > Denne indstilling er kun tilgængelig, hvis administratoren har konfigureret en brugerdefineret formel.

   3. Indstillingen **Start en arbejdsproces** er kun tilgængelig, hvis du vil definere en politik for en liste, et bibliotek eller en indholdstype, der allerede har en arbejdsproces tilknyttet. Du får derefter en række arbejdsprocesser at vælge mellem.

   4. I sektionen **Gentagelse** skal du **vælge Gentag denne fases handling ...** og derefter angive, hvor ofte du ønsker, at handlingen skal gentages.

      > [!NOTE]
      >  Denne indstilling er kun tilgængelig, hvis den valgte handling kan gentages. Du kan f.eks. ikke angive en gentagelse af **handlingen Slet permanent**.

   5. Vælg **OK**.

8. Hvis du vil aktivere overvågning for de dokumenter og elementer, der er underlagt denne politik, skal du vælge Aktivér overvågning og derefter angive de **hændelser, du** vil overvåge.

   Sådan aktiveres overvågning:

   1. Vælg Aktivér overvågning på **siden** Rediger politik under **Overvågning, og** markér derefter afkrydsningsfelterne ud for de hændelser, du vil føre en overvågningslog for.

   2. Hvis du vil bede brugerne om at indsætte disse stregkoder i dokumenter, skal du **vælge Bed brugerne om at indsætte en stregkode, før de gemmer eller udskriver**.

   3. Vælg **OK** for at anvende overvågningsfunktionen på politikken.

   Funktionen Overvågningspolitik giver organisationer mulighed for at oprette og analysere revisionsspor for dokumenter og for listeelementer som opgavelister, problemlister, diskussionsgrupper og kalendere. Denne politikfunktion indeholder en overvågningslog, der registrerer hændelser, f.eks. når indhold vises, redigeres eller slettes.

   Når overvågning er aktiveret som en del af en politik for administration af oplysninger, kan administratorer få vist overvågningsdataene i anvendelsesrapporter for politikker, der er baseret på Microsoft Excel og som opsummerer den aktuelle brug. Administratorer kan bruge disse rapporter til at bestemme, hvordan oplysningerne bruges inden for organisationen. Disse rapporter kan også hjælpe organisationer med at bekræfte og dokumentere deres overholdelse af lovgivning eller med at undersøge potentielle problemer.

   Overvågningsloggen registrerer følgende oplysninger: hændelsesnavn, dato og klokkeslæt for hændelsen og systemnavnet på den bruger, der udførte handlingen.

9. Når stregkoder er aktiveret som en del af en politik, føjes de til dokumentegenskaberne og vises i sidehovedområdet i det dokument, hvor stregkoden er anvendt. Ligesom etiketter kan stregkoder også fjernes manuelt fra et dokument. Du kan angive, om brugerne skal blive bedt om at medtage stregkoden, når de udskriver eller gemmer et element, eller om stregkoden skal indsættes  manuelt ved hjælp af fanen Indsæt i Office udgivelsesprogrammer.

   Sådan aktiveres stregkoder:

   1. Vælg **Aktivér stregkoder** på **siden** Rediger politik **under Stregkoder**.

   2. Hvis du vil bede brugerne om at indsætte disse stregkoder i dokumenter, skal du **vælge Bed brugerne om at indsætte en stregkode, før de gemmer eller udskriver**.

   3. Vælg **OK** for at anvende stregkodefunktionen på politikken.

   Stregkodepolitikken genererer standardstregkoder med Code 39-standarden. Hvert stregkodebillede har tekst under stregkodesymbolet, der repræsenterer stregkodeværdien. Dermed kan stregkodedataene bruges, selvom der ikke er scanningshardware tilgængeligt. Brugerne kan skrive stregkodetallet manuelt i søgefeltet for at finde elementet på et websted.  <br/> |

10. Hvis du vil kræve, at dokumenter, der er underlagt denne politik, har etiketter, skal du vælge Aktivér etiketter og derefter angive de ønskede indstillinger for etiketterne.

    Sådan aktiveres etiketter:

    1. Hvis brugerne skal føje en etiket til et dokument, skal du vælge **Spørg brugerne, om der skal indsættes en etiket, før der gemmes eller udskrives**.

       > [!NOTE]
       > Hvis etiketter skal være valgfrie, skal du ikke markere dette afkrydsningsfelt.

    2. Hvis du vil låse en etiket, så den ikke kan ændres, efter den er blevet indsat, skal du vælge **Forbyd ændringer af etiketter, når de er tilføjet**.

       Denne indstilling forhindrer, at etiketteksten opdateres, når først etiketten er blevet indsat i et element i et klientprogram, f.eks. Word, Excel eller PowerPoint. Hvis du vil have, at etiketten opdateres, når egenskaberne for dette dokument eller element opdateres, skal du ikke markere dette afkrydsningsfelt.

    3. Skriv teksten til etiketten i feltet Etiketformat, sådan som den skal vises. Etiketter kan indeholde op til 10 kolonnereferencer, som hver især kan indeholde op til 255 tegn. Hvis du vil oprette formatet for etiketten, skal du gøre følgende:
       - Skriv navnene på de kolonner, du vil medtage i navnet, i den rækkefølge, de skal vises i. Omslut kolonnenavnene i klammeparenteser ({}), som vist i eksemplet på siden Rediger politik.
       - Skriv ord for at identificere kolonnerne uden for de kantede parenteser, som vist i eksemplet på siden Rediger politik.

    4. Hvis du vil tilføje et linjeskift, **skal\n** det sted, hvor linjeskift skal vises.

    5. Vælg den ønskede skriftstørrelse og typografi, og angiv, om etiketten skal placeres til venstre, centreret eller til højre i dokumentet.

       Vælg en skrifttype og typografi, der er tilgængelig på brugernes computere. Størrelsen på skrifttypen påvirker, hvor meget tekst der kan vises på etiketten.

    6. Angiv etikettens højde og bredde. Etikethøjden kan variere fra 0,6 cm 50 cm, og etiketbredden kan variere fra 0,6 cm til 50 cm. Etiketteksten er altid lodret centreret inden for etiketbilledet.

    7. Vælg **Opdater for** at få vist etiketindholdet.

11. Vælg **OK**.

## <a name="create-a-policy-for-a-list-library-or-folder-location-based-retention-policy"></a>Opret en politik for en liste, et bibliotek eller en mappe (placeringsbaseret opbevaringspolitik)
<a name="__create_a_policy"> </a>

Du kan definere en opbevaringspolitik, der kun gælder for en bestemt liste, et bibliotek eller en mappe. Men hvis du opretter en opbevaringspolitik på denne måde, kan du genbruge denne politik på andre lister, biblioteker, mapper eller websteder, og du kan ikke anvende en politik for grupper af websteder på en placeringsbaseret politik.

Hvis du vil anvende en enkelt opbevaringspolitik på alle typer indhold på én placering, vil det sandsynligvis være en god ide at bruge placeringsbaseret opbevaring. I de fleste tilfælde skal du bekræfte, at der er angivet en opbevaringspolitik for alle indholdstyper.

Hver undermappe nedarver opbevaringspolitikken fra den overordnede mappe, medmindre du vælger at bryde nedarvningen og definere en ny opbevaringspolitik på det underordnede niveau.

Hvis du vil definere en anden politik for administration af oplysninger end en opbevaringspolitik for en liste eller et bibliotek, skal du definere en politik for administration af oplysninger for hver enkelt listeindholdstype, der er knyttet til listen eller biblioteket.

Hvis du på noget tidspunkt beslutter at skifte fra indholdstypebaserede til placeringsbaserede politikker for en liste eller et bibliotek, vil kun opbevaringspolitikken blive brugt som placeringsbaseret politik. Alle andre administrationspolitikker (overvågning, stregkoder og stregkoder) nedarves fra de tilknyttede indholdstyper.

Placeringsbaserede politikker kan deaktiveres for en gruppe af websteder ved at deaktivere funktionen Biblioteks- og mappebaseret opbevaring. Dette gør det muligt for administratorer af grupper af websteder at sikre, at deres indholdstypepolitikker ikke tilsidesættes af en listeadministrators placeringsbaserede politikker.

Du skal som minimum have tilladelsen Administrer lister for at ændre politikindstillingerne for administration af oplysninger for en liste eller et bibliotek.

1. Gå til den liste eller det bibliotek, som du vil angive en politik for administration af oplysninger for.

2. På båndet skal du vælge **fanen Bibliotek** **eller Liste** Indstillinger \> **eller** **liste Indstillinger**.

   Klik SharePoint Indstillinger for bibliotek **i Indstillinger** Online, og **klik derefter på Listeindstillinger** **eller Indstillinger for bibliotek**.

3. Under **Indstillinger for politikker for administration af**\> **tilladelser og administration af oplysninger**.

   ![Link til politikker for administration af oplysninger på indstillingssiden for dokumentbibliotek.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. På siden Politik for administration af Indstillinger du sørge for, at kilden til opbevaring for listen eller biblioteket er angivet til Bibliotek og Mapper.

   Hvis **Indholdstype vises** som kilde, skal du klikke **på Skift** kilde og derefter **klikke på Bibliotek og mapper**. Du bliver advaret om, at opbevaringspolitikker for indholdstyper ignoreres. Vælg **OK**.

5. Angiv en kort beskrivelse af den politik, du **opretter**, under Biblioteksbaseret opbevaringstidsplan på siden Rediger politik.

6. Vælg **Tilføj en opbevaringsfase...**

   Bemærk, at du under Poster kan vælge at definere forskellige opbevaringspolitikker for poster ved at vælge indstillingen Definer forskellige opbevaringsfaser for poster.

7. I dialogboksen Egenskaber for fase skal du vælge en indstilling for opbevaringsperiode for at angive, hvornår dokumenter eller elementer skal indstilles til at udløbe. Gør et af følgende:

   - Hvis du vil angive udløbsdatoen baseret på en datoegenskab, skal **du under** \> Hændelse Denne fase er baseret på en datoegenskab for **elementet og derefter** vælge dokument- eller elementhandlingen (f.eks. Oprettet eller Ændret) og det tidsrum efter denne handling (f.eks. antallet af dage, måneder eller år), hvor elementet skal udløbe.

   - Hvis du vil bruge en brugerdefineret opbevaringsformel til at bestemme udløb, skal du **vælge Angiv af en brugerdefineret opbevaringsformel, der er installeret på denne server**.

     > [!NOTE]
     >  Denne indstilling er kun tilgængelig, hvis administratoren har konfigureret en brugerdefineret formel.

   - Under **Handling** skal du angive, hvad der skal ske, når dokumentet eller elementet udløber. Hvis du vil aktivere en bestemt handling, der skal ske med dokumentet eller elementet (f.eks. sletning), skal du vælge en handling på listen.

8. Indstillingen **Start en arbejdsproces** er kun tilgængelig, hvis du vil definere en politik for en liste, et bibliotek eller en indholdstype, der allerede har en arbejdsproces tilknyttet. Du får derefter en række arbejdsprocesser at vælge mellem.

9. Under **Gentagelse** skal du **vælge Gentag denne fases handling ...** og angiv, hvor ofte du ønsker, at handlingen skal gentages.

   > [!NOTE]
   >  Denne indstilling er kun tilgængelig, hvis den valgte handling kan gentages. Du kan f.eks. ikke angive en gentagelse af **handlingen Slet permanent**.

10. Vælg **OK**.

## <a name="apply-a-site-collection-policy-to-a-content-type"></a>Anvend en politik for en gruppe af websteder på en indholdstype
<a name="__apply_a_site"> </a>

Hvis der allerede er oprettet politikker for administration af oplysninger for dit websted som politikker for grupper af websteder, kan du anvende en af politikkerne på en indholdstype. Ved at gøre dette kan du anvende den samme politik på flere indholdstyper i en gruppe af websteder, der ikke deler den samme overordnede indholdstype.

 Hvis du vil anvende politikker på flere indholdstyper i en gruppe af websteder, og du har en Administreret Metadata Service konfigureret, kan du bruge indholdstypepublicering til at publicere politikker for administration af oplysninger på flere grupper af websteder. Se afsnittet Anvend [en politik på tværs af grupper af websteder for at](#apply-a-policy-across-site-collections) få flere oplysninger.

1. Gå til den liste eller det bibliotek, der indeholder den indholdstype, du vil anvende en politik på.

2. På båndet skal du vælge **fanen Bibliotek** **eller Liste** Indstillinger \> **eller** **liste Indstillinger**.

   Klik SharePoint Indstillinger for bibliotek **i Indstillinger** Online, og **klik derefter på Listeindstillinger** **eller Indstillinger for bibliotek**.

3. Under **Indstillinger for politikker for administration af** \> **tilladelser og administration af oplysninger**.

   ![Link til politikker for administration af oplysninger på indstillingssiden for dokumentbibliotek.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)

4. Kontrollér, at politikkilden **er angivet til** Indholdstyper, **og vælg den** indholdstype, du vil anvende politikken på, under Politikker for indholdstype.

5. Under **Angiv politikken Brug** \> **en politik for en gruppe** af websteder, og vælg derefter den politik, du vil anvende, på listen.

   > [!NOTE]
   >  Hvis indstillingen **Brug en politik for en gruppe af** websteder ikke er tilgængelig, er der ikke defineret nogen politikker for gruppen af websteder for gruppen af websteder.

6. Vælg **OK**.

   Hvis den liste eller det bibliotek, du arbejder med, understøtter administration af flere indholdstyper, kan **du under** Indholdstyper vælge den indholdstype, du vil angive en politik for administration af oplysninger for. Dette fører dig direkte til trin 5 ovenfor.

## <a name="apply-a-policy-across-site-collections"></a>Anvend en politik på tværs af grupper af websteder
<a name="__toc260646789"> </a>

Del indholdstyper på tværs af grupper af websteder ved hjælp af et administreret tjenesteprogram til metadata til at konfigurere indholdstypepublicering. Indholdstypepublicering hjælper dig med at administrere indhold og metadata på en ensartet måde på tværs af dine websteder, fordi indholdstyper kan oprettes og opdateres centralt, og opdateringer kan publiceres ud til flere abonnerende grupper af websteder eller webprogrammer.

## <a name="create-a-template-from-an-existing-policy-to-use-across-site-collections"></a>Opret en skabelon ud fra en eksisterende politik, der skal bruges på tværs af grupper af websteder
<a name="__toc262125409"> </a>

Du kan definere en politik for administration af oplysninger og derefter oprette en skabelon ud fra den, som kan bruges efter behov på tværs af flere grupper af websteder. Denne metode kan bruges, hvis du vil have en sikkerhedskopi af dine oplysningspolitikker, eller den kan bruges som en anden metode til at bruge indholdstypepublicering til at anvende én politik på tværs af grupper af websteder. Du opretter en skabelon eller en sikkerhedskopi af politikken ved at eksportere politikken fra én gruppe af websteder og derefter importere den til en gemt placering eller til en anden gruppe af websteder.

> [!IMPORTANT]
> Hvis du bruger eksport/import-funktionen som en metode til at oprette et sæt af politikskabeloner, skal du huske på, at der findes et entydig identifier i .xml fil. Derfor kan du ikke importere denne politik til et websted mere end én gang uden at ændre denne entydig identifier.

### <a name="export-a-policy"></a>Eksportér en politik
<a name="__toc260646790"> </a>

1. På startsiden for gruppen af websteder skal **du vælge Indstillinger**![ Small-Indstillinger, der blev taget i stedet for webstedswebstedet Indstillinger.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Websted Indstillinger**.

   Klik på SharePoint websted i et gruppeforbundet websted, **Indstillinger** på Webstedsindhold **, og** klik derefter på **Webstedsindhold Indstillinger**.

2. På siden Webstedstyper Indstillinger under **Politikskabeloner for administration** \> af **indholdstype for gruppe af websteder**.

   ![Linket Politikskabelon til indholdstype på siden Indstillinger websted.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)

3. Vælg den politik, du vil eksportere, \> rul til bunden **Eksportér**\>.

4. Når du bliver spurgt, om du vil gemme eller åbne filen, **skal du vælge** Gem og derefter vælge en placering, hvor du vil gemme filen. Sørg for at vælge en placering, der er tilgængelig for de grupper af websteder, der importerer politikken.

5. Når dialogboksen Download er fuldført vises, skal du vælge **Luk**.

### <a name="import-a-policy-to-a-different-site-collection"></a>Importere en politik til en anden gruppe af websteder
<a name="__toc260646791"> </a>

Når du importerer en politik for administration af oplysninger, kan du anvende den på flere indholdstyper på websteds- eller listeniveau inden for en bestemt gruppe af websteder. Fordelene ved at gøre dette er dobbelte: Du behøver ikke at definere og anvende politikken på hver indholdstype igen, og du kan nemmere administrere politikændringer ved kun at foretage ændringer i politikken ét sted.

1. På startsiden for den gruppe af websteder, som du vil anvende politikken på, skal du vælge Indstillinger Small **Indstillinger**![ tandhjul, der blev taget i stedet for websted Indstillinger.](../media/a47a06c3-83fb-46b2-9c52-d1bad63e3e60.png)\> **Indstillinger**.

   Klik på SharePoint websted i et gruppeforbundet websted, **Indstillinger** på Webstedsindhold **, og** klik derefter på **Webstedsindhold Indstillinger**.

2. På siden Webstedstyper Indstillinger under **Politikskabeloner for administration** \> af **indholdstype for gruppe af websteder**.

3. På siden Politikker skal du \> **importere Gennemse** \> for at finde XML-filen til politikken.

4. Vælg den XML-fil, som politikken er gemt i, \> **Åbn**.

5. Importér for at føje politikken til gruppen \> **af** websteder på siden Importér en politik for gruppe af websteder.

Din importerede politik kan nu anvendes på en eller flere indholdstyper på websteds- eller listeniveau.

Politikker for administration af oplysninger gør det muligt for organisationen at styre, hvor lang tid indhold opbevares, hvad folk kan gøre med indhold, og føje stregkoder eller etiketter til dokumenter. En politik kan hjælpe med at håndhæve overholdelse af juridiske og statslige love og forordninger eller interne forretningsprocesser. Som administrator kan du konfigurere en politik til at styre, hvordan du kan spore dokumenter, og hvor lang tid dokumenter skal opbevares.

Du kan oprette en politik for administration af oplysninger på tre forskellige steder i webstedshierarkiet fra den bredeste til den smalleste:

- Opret en politik, der skal bruges på flere indholdstyper inden for en gruppe af websteder.
- Opret en politik for en webstedsindholdstype.
- Opret en politik for en liste eller et bibliotek.

Få mere at vide under [Introduktion til politikker for administration af oplysninger](intro-to-info-mgmt-policies.md).
