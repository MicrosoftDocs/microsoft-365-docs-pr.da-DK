---
title: Kom i gang med trænbare klassificeringer
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: En Microsoft 365 klassificering er et værktøj, du kan oplære til at genkende forskellige typer indhold ved at give det eksempler, du kan se på. I denne artikel kan du se, hvordan du opretter og oplærer en brugerdefineret klassificering, og hvordan du omskoler dem for at øge nøjagtigheden.
ms.openlocfilehash: d3a7639ed31dc42688cffbffb151049659a41660
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173187"
---
# <a name="get-started-with-trainable-classifiers"></a>Kom i gang med trænbare klassificeringer

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

En Microsoft 365 klassificering, der kan oplæres, er et værktøj, du kan oplære til at genkende forskellige typer indhold ved at give det eksempler, du kan se på. Når du har oplært, kan du bruge den til at identificere elementer til anvendelse af Office følsomhedsmærkater, politikker for kommunikation med overholdelse af angivne standarder og politikker for opbevaringsmærkater.

Oprettelse af en brugerdefineret klassificering, der kan oplæres, omfatter først at give den eksempler, der er valgt af mennesker, og som stemmer positivt overens med kategorien. Derefter tester du klassificeringens evne til at forudsige ved at give den en blanding af positive og negative prøver, når den har behandlet dem. I denne artikel kan du se, hvordan du opretter og oplærer en brugerdefineret klassificering, og hvordan du kan forbedre ydeevnen for brugerdefinerede klassificeringer og færdiguddannede klassificeringer gennem omskoling.

Hvis du vil vide mere om de forskellige klassificeringstyper, skal [du se Få mere at vide om klassificeringer, der kan oplæres](classifier-learn-about.md).

Se denne video for at få en hurtig oversigt over, hvordan du opretter en klassificering, der kan oplæres. Du skal stadig læse denne komplette artikel for at få detaljerne.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Forudsætninger

### <a name="licensing-requirements"></a>Licenskrav

Klassificeringer er en funktion til Microsoft 365 E5 eller E5-overholdelse. Du skal have et af disse abonnementer for at kunne bruge dem.

### <a name="permissions"></a>Tilladelser

Sådan får du adgang til klassificeringer i brugergrænsefladen: 

- Den globale administrator skal tilmelde sig lejeren for at oprette brugerdefinerede klassificeringer.
- Rollen som overholdelsesadministrator kræves for at oplære en klassificering.

Du skal bruge konti med disse tilladelser for at bruge klassificeringer i disse scenarier:

- Politikscenarie for opbevaringsmærkat: Roller til administration af poster og opbevaringsstyring 
- Politikscenarie for følsomhedsmærkat: Sikkerhedsadministrator, overholdelsesadministrator, administrator af overholdelsesdata
- Scenarie for politik for overholdelse af kommunikation: Administrator af styring af insiderrisiko, administrator af tilsynsgennemsyn 

> [!IMPORTANT]
> Som standard er det kun den bruger, der opretter en brugerdefineret klassificering, der kan oplære og gennemse forudsigelser foretaget af den pågældende klassificering.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Forbered dig på en brugerdefineret klassificering, der kan oplæres 

Det er nyttigt at forstå, hvad der er involveret i at oprette en brugerdefineret klassificering, der kan oplæres, før du dykker ind. 

### <a name="timeline"></a>Tidslinjen

Denne tidslinje afspejler et eksempel på udrulning af klassificeringer, der kan oplæres.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Tilmelding er påkrævet første gang for klassificerere, der kan oplæres. Det tager 12 dage, før Microsoft 365 har gennemført en grundlæggende evaluering af organisationens indhold. Kontakt din globale administrator for at starte tilmeldingsprocessen.

### <a name="overall-workflow"></a>Overordnet arbejdsproces

Hvis du vil vide mere om den overordnede arbejdsproces til oprettelse af brugerdefinerede klassificeringer, der kan oplæres, skal du se [Procesforløb til oprettelse af brugerdefinerede klassificeringer, der kan oplæres](classifier-learn-about.md#process-flow-for-creating-custom-classifiers).

### <a name="seed-content"></a>Indhold af frø

Når du ønsker, at en klassificering, der kan oplæres, uafhængigt af hinanden og præcist identificerer et element som en bestemt kategori af indhold, skal du først præsentere det med mange eksempler på den type indhold, der findes i kategorien. Denne fodring af prøver til den klassificering, der kan oplæres, kaldes *såning*. Frøindhold vælges af et menneske og bedømmes til at repræsentere indholdskategorien.

> [!TIP]
> Du skal have mindst 50 positive prøver og op til 500. Den klassificering, der kan oplæres, behandler op til de 500 seneste oprettede eksempler (efter dato-/tidsstempel, der er oprettet af filen). Jo flere eksempler du angiver, jo mere nøjagtige er de forudsigelser, som klassificeringen foretager.

### <a name="testing-content"></a>Test af indhold

Når klassificeringen, der kan oplæres, har behandlet tilstrækkeligt mange positive eksempler til at oprette en forudsigelsesmodel, skal du teste de forudsigelser, den foretager, for at se, om klassificeringen kan skelne korrekt mellem elementer, der svarer til kategorien, og elementer, der ikke har. Det gør du ved at vælge et andet, forhåbentlig større, sæt af menneskeligt plukket indhold, der består af eksempler, der skal falde inden for kategorien, og eksempler, der ikke vil. Du bør teste med andre data end de oprindelige seed-data, du første gang har angivet. Når de er behandlet, gennemgår du resultaterne manuelt og kontrollerer, om hver forudsigelse er korrekt, forkert, eller om du ikke er sikker. Den klassificering, der kan oplæres, bruger denne feedback til at forbedre sin forudsigelsesmodel.

> [!TIP]
> Du opnår det bedste resultat ved at have mindst 200 elementer i testeksemplet med en lige fordeling af positive og negative matches.

## <a name="how-to-create-a-trainable-classifier"></a>Sådan opretter du en klassificering, der kan oplæres

1. Indsaml mellem 50-500 basisindholdselementer. Det må kun være eksempler, der på det kraftigste repræsenterer den type indhold, du ønsker, at den klassificering, der kan oplæres, skal identificeres positivt som værende i klassificeringskategorien. Se [Standardsøgede filtypenavne og fortolkede filtyper i SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for de understøttede filtyper.

   > [!IMPORTANT]
   > Sørg for, at elementerne i dit frøsæt er **stærke** eksempler på kategorien. Den klassificering, der kan oplæres, bygger i første omgang sin model ud fra, hvad du bruger til at bruge den. Klassificeringen antager, at alle frøprøver er stærke positive og ikke har nogen måde at vide, om en prøve er et svagt eller negativt match til kategorien.

2. Placer frøindholdet i en SharePoint Online-mappe, der er dedikeret til kun at indeholde *frøindholdet*. Notér URL-adressen for webstedet, biblioteket og mappen.

   > [!TIP]
   > Hvis du opretter et nyt websted og en ny mappe til dine seed-data, skal du tillade, at mindst en time for denne placering indekseres, før du opretter den klassificering, der kan oplæres, og som skal bruge disse basisdata.

3. Log på Microsoft Purview-overholdelsesportalen med rollen overholdelsesadministrator eller sikkerhedsadministrator, og åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **portalDataklassificering** > .

4. Vælg fanen **Klassificeringskomponenter, der kan oplæres** .

5. Vælg **Opret klassificering, der kan oplæres**.

6. Udfyld de relevante værdier for felterne og `Description` for `Name` den kategori af elementer, som denne klassificering, der kan oplæres, skal identificere.

7. Vælg URL-adressen SharePoint onlinewebsted, -bibliotek og -mappe for webstedet med frøindhold på trin 2. Vælg `Add`.

8. Gennemse indstillingerne, og vælg `Create trainable classifier`.

9. Inden for 24 timer behandler den klassificering, der kan oplæres, frødataene og opretter en forudsigelsesmodel. Klassificeringsstatussen er `In progress` , mens den behandler basisdataene. Når klassificeringen er færdig med at behandle basisdataene, ændres status til `Need test items`.

10. Du kan nu få vist detaljesiden ved at vælge klassificeringen.

    > [!div class="mx-imgBorder"]
    > ![klassificering, der kan oplæres, klar til test.](../media/classifier-trainable-ready-to-test-detail.png)

11. Indsaml mindst 200 testindholdselementer (maks. 10.000) for at få de bedste resultater. Disse bør være en blanding af elementer, der er stærke positive, stærke negativer og nogle, der er lidt mindre indlysende i deres natur. Se [Standardsøgede filtypenavne og fortolkede filtyper i SharePoint Server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for de understøttede filtyper.

12. Placer testindholdet i en SharePoint Online-mappe, der kun skal indeholde *testindholdet*. Notér SharePoint URL-adressen til webstedet, biblioteket og mappen.

    > [!TIP]
    > Hvis du opretter et nyt websted og en ny mappe til dine testdata, skal du tillade, at mindst en time for denne placering indekseres, før du opretter den klassificering, der kan oplæres, og som skal bruge disse basisdata.

13. Vælg `Add items to test`.

14. Vælg URL-adressen SharePoint onlinewebsted, -bibliotek og -mappe for webstedet med testindhold på trin 12. Vælg `Add`.

15. Afslut guiden ved at vælge `Done`. Det tager op til en time at behandle testfilerne med den klassificering, der kan oplæres.

16. Når den klassificering, der kan oplæres, er færdig med at behandle dine testfiler, ændres status på detaljesiden til `Ready to review`. Hvis du har brug for at øge størrelsen på testeksemplet, skal du vælge `Add items to test` og tillade, at den klassificering, der kan oplæres, behandler de ekstra elementer.

    > [!div class="mx-imgBorder"]
    > ![klar til at gennemse skærmbillede.](../media/classifier-trainable-ready-to-review-detail.png)

17. Vælg `Tested items to review` fanen for at gennemse elementer.

18. Microsoft 365 præsenterer 30 elementer ad gangen. Gennemse dem, `We predict this item is "Relevant". Do you agree?` og vælg enten `Yes` eller `No` eller `Not sure, skip to next item`i feltet . Modelnøjagtighed opdateres automatisk efter hver 30 elementer.

    > [!div class="mx-imgBorder"]
    > ![feltet gennemse elementer.](../media/classifier-trainable-review-detail.png)

19. Gennemse *mindst* 200 elementer. Når nøjagtighedsscoren er stabiliseret, bliver **publiceringsindstillingen** tilgængelig, og klassificeringsstatussen siger `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![score for nøjagtighed og klar til publicering.](../media/classifier-trainable-review-ready-to-publish.png)

20. Publicer klassificeringen.

21. Når klassificeringen er publiceret, vil den være tilgængelig som en betingelse i [Office automatisk mærkning med følsomhedsmærkater](apply-sensitivity-label-automatically.md), [automatisk anvende politik for opbevaringsmærkat baseret på en betingelse](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) og i [Kommunikationstilstand](communication-compliance.md).
