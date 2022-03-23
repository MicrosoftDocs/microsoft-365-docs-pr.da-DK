---
title: Kom i gang med klassekammerater, der kan trænes
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
description: En Microsoft 365 er et værktøj, du kan træne til at genkende forskellige typer indhold ved at give den eksempler, du kan kigge på. I denne artikel kan du se, hvordan du opretter og oplærer en brugerdefineret klassificering, og hvordan du omskolinger dem for at øge nøjagtigheden.
ms.openlocfilehash: 263791549e314a116f21231e8dc4cde5be380cb7
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63589812"
---
# <a name="get-started-with-trainable-classifiers"></a>Kom i gang med klassekammerater, der kan trænes

En Microsoft 365 klassekammerat er et værktøj, du kan træne til at genkende forskellige typer indhold ved at give den eksempler, du kan kigge på. Når du er blevet trænet, kan du bruge den til at identificere elementer til Office af følsomhedsmærkater, politikker for overholdelse af kommunikation og opbevaringsetiketpolitikker.

Først skal du oprette en brugerdefineret klassificering, der kan trænes, ved at give den prøver, der er humane og passer positivt til kategorien. Derefter skal du, når den har behandlet disse, teste klassificerings muligheden for at forudsige ved at give den en blanding af positive og negative stikprøver. I denne artikel kan du se, hvordan du opretter og oplærer en brugerdefineret klassificering, og hvordan du forbedrer ydeevnen for brugerdefinerede, trænbare klassificeringer og færdigtrænede klassificeringer i løbet af deres levetid gennem omskoling.

Hvis du vil have mere at vide om de forskellige typer klassificeringer, skal du [se Få mere at vide om trænbare klassificeringer](classifier-learn-about.md).

Watch this video for a quick summary of creating a trainable classifier. Du skal stadig læse denne hele artikel for at få flere oplysninger.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGL7]


## <a name="prerequisites"></a>Forudsætninger

### <a name="licensing-requirements"></a>Licenskrav

Klassificeringer er en Microsoft 365 E5- eller E5-overholdelsesfunktion. Du skal have et af disse abonnementer for at gøre brug af dem.

### <a name="permissions"></a>Tilladelser

Sådan får du adgang til klassificeringer i brugergrænsefladen: 

- den globale administrator skal tilmelde sig lejeren for at oprette brugerdefinerede klassificeringer.
- Der kræves en rolle som overholdelsesadministrator for at kunne oplære en klassificering.

Du skal bruge konti med disse tilladelser for at bruge klassificeringer i disse scenarier:

- Scenarie for opbevaringsetiketpolitik: Roller for administration af poster og opbevaringsstyring 
- Scenarie med følsomhedsmærkatpolitik: Sikkerhedsadministrator, overholdelsesadministrator, overholdelsesdataadministrator
- Scenarie for overholdelse af politik for kommunikation: Administrator for insider-risikostyring, administrator for kontrolvurdering 

> [!IMPORTANT]
> Som standard er det kun den bruger, der opretter en brugerdefineret klassificering, der kan træne og gennemse forudsigelser fra denne klassificering.

## <a name="prepare-for-a-custom-trainable-classifier"></a>Forbered dig på en brugerdefineret, trænbar klassificering 

Det er nyttigt at forstå, hvad det betyder for at oprette en brugerdefineret, trænbar klassificering, før du går i gang. 

### <a name="timeline"></a>Tidslinje

Denne tidslinje afspejler en eksempelinstallation af klassificeringer, der kan trænes.

![trainable-classifier-timeline.](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> Tilmelding er påkrævet første gang for klassificerede, der kan trænes. Det tager 12 dage, Microsoft 365 gennemføre en evaluering af organisationens indhold i en oprindelig plan. Kontakt din globale administrator for at starte tilmeldingsprocessen.

### <a name="overall-workflow"></a>Samlet arbejdsproces

Hvis du vil have mere at vide om den overordnede arbejdsproces for oprettelse af brugerdefinerede, trænbare klassificeringer, skal du se [Procesflow til](classifier-learn-about.md#process-flow-for-creating-custom-classifiers) oprettelse af klassekammerater, der kan bruges af kunder.

### <a name="seed-content"></a>Basisindhold

Når du vil have en korrekt klassificering, der kan trænes, så du nøjagtigt identificerer et element som værende i en bestemt kategori af indhold, skal du først præsentere det med mange eksempler på den type indhold, der er i kategorien. Denne fødning af stikprøver til den togbare klassificering kaldes *for basisring*. Basisindhold vælges af et mennesker og vurderes at repræsentere kategorien for indhold.

> [!TIP]
> Du skal have mindst 50 positive eksempler og op til 500. Den togbare klassificering behandler op til de 500 senest oprettede eksempler (efter fil oprettet dato/tidsstempel). Jo flere stikprøver du angiver, des mere nøjagtige forudsigelser vil klassificeringen give.

### <a name="testing-content"></a>Test af indhold

Når den togbare klassificering har behandlet nok positive stikprøver til at opbygge en forudsigelsesmodel, skal du teste de forudsigelser, den viser, for at se, om klassificeringen kan skelne korrekt mellem elementer, der svarer til kategorien, og elementer, der ikke passer. Det gør du ved at vælge et andet, forhåbentligt større, sæt humane picked indhold, der består af eksempler, der bør falde ind under kategorien, og eksempler, der ikke gør. Du skal teste med andre data end de startdata, du først har angivet. Når programmet behandler disse, skal du manuelt gennemgå resultaterne og kontrollere, om hver forudsigelse er korrekt, forkert, eller du er i tvivl. Den optrænelige klassificering bruger denne feedback til at forbedre forudsigelsesmodellen.

> [!TIP]
> Du opnår de bedste resultater ved at have mindst 200 elementer i dit prøvesæt med en lige fordeling af positive og negative resultater.

## <a name="how-to-create-a-trainable-classifier"></a>Sådan opretter du en klassekammerat, der kan trænes

1. Indsaml mellem 50-500 basisindholdselementer. Disse må kun være eksempler, der på det kraftigste repræsenterer den type indhold, du ønsker, at klassificeringen skal kunne bruges til på en sikker måde at identificere som værende i klassificeringskategorien. Se Standard [for gennemsøgte filtypenavne og fortolkede filtyper i SharePoint server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for de understøttede filtyper.

   > [!IMPORTANT]
   > Sørg for, at elementerne i dit **basissæt er** stærke eksempler på kategorien. Den trainable classifier bygger i første omgang sin model ud fra, hvad du basisner den med. Klassificeringen antager, at alle basiseksempler er stærke positive og ikke kan bruges til at vide, om en stikprøve er svag eller negativ i forhold til kategorien.

2. Placer basisindholdet i en SharePoint Online-mappe, der er dedikeret til kun *at holde basisindholdet*. Noter webstedet, biblioteket og mappens URL-adresse.

   > [!TIP]
   > Hvis du opretter et nyt websted og en ny mappe til dine basisdata, skal du tillade, at mindst en time for den pågældende placering indekseres, før du opretter den klasseklasse, der skal bruge basisdataene.

3. Log på Microsoft 365 Overholdelsescenter med adgang til overholdelsesadministrator eller sikkerhedsadministratorrolle, og <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">åbn Microsoft 365 Overholdelsescenter</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **portalData-klassificering** > .

4. Vælg fanen **Klassekammerater, der kan trænes** .

5. Vælg **Opret klassificering, der kan trænes**.

6. Udfyld relevante værdier for kategorien og `Name` felterne `Description` for den kategori af elementer, du vil have denne trænbare klassificering til at identificere.

7. Vælg webadressen SharePoint Online-websted, -bibliotek og -mappe for basisindholdswebstedet fra trin 2. Vælg `Add`.

8. Gennemse indstillingerne, og vælg `Create trainable classifier`.

9. Inden for 24 timer behandler den trainable klassificering basisdataene og opbygger en forudsigelsesmodel. Klassificeringsstatussen er, mens `In progress` den behandler basisdataene. Når klassificeringen er færdig med at behandle basisdataene, ændres status til `Need test items`.

10. Nu kan du få vist detaljesiden ved at vælge klassificeringen.

    > [!div class="mx-imgBorder"]
    > ![trainable classifier ready for testing.](../media/classifier-trainable-ready-to-test-detail.png)

11. Indsaml mindst 200 testindholdselementer (10.000 maks.) for at få de bedste resultater. Disse bør være en blanding af elementer, der er stærke positive, stærke negativer og nogle, der er lidt mindre tydelige i deres art. Se Standard [for gennemsøgte filtypenavne og fortolkede filtyper i SharePoint server](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for de understøttede filtyper.

12. Placer testindholdet i en SharePoint Online-mappe, der er dedikeret til kun *at holde testindholdet.* Noter webstedet SharePoint Online-webstedet, biblioteket og mappens URL-adresse.

    > [!TIP]
    > Hvis du opretter et nyt websted og en ny mappe til dine testdata, skal du tillade, at mindst en time for den pågældende placering indekseres, før du opretter den klasseklasse, der skal bruge disse basisdata.

13. Vælg `Add items to test`.

14. Vælg SharePoint Online-webstedet, biblioteket og mappens URL-adresse til webstedet til testindhold fra trin 12. Vælg `Add`.

15. Afslut guiden ved at vælge `Done`. Det kan tage op til en time for din op til en time at behandle testfilerne.

16. Når den træbare klassificering er færdig med at behandle dine testfiler, ændres status på detaljesiden til `Ready to review`. Hvis du har brug for at øge prøvestørrelsen, skal du vælge `Add items to test` og lade den trænbare klassificering behandle de ekstra elementer.

    > [!div class="mx-imgBorder"]
    > ![skærmbillede, der er klar til at blive gennemset.](../media/classifier-trainable-ready-to-review-detail.png)

17. Vælg fane `Tested items to review` for at gennemse elementer.

18. Microsoft 365 30 elementer ad gangen. Gennemse dem, og i feltet `We predict this item is "Relevant". Do you agree?` skal du vælge enten `Yes` eller `No` eller `Not sure, skip to next item`. Modelnøjagtigheden opdateres automatisk efter hver 30 elementer.

    > [!div class="mx-imgBorder"]
    > ![feltet Gennemse elementer.](../media/classifier-trainable-review-detail.png)

19. Gennemse *mindst* 200 elementer. Når nøjagtighedsresultatet er stabilt, bliver  publiceringsindstillingen tilgængelig, og klassificeringsstatussen vil angive `Ready to use`.

    > [!div class="mx-imgBorder"]
    > ![nøjagtighedsscore og klar til at publicere.](../media/classifier-trainable-review-ready-to-publish.png)

20. Publicer klassificeringen.

21. Når din klassificering er publiceret[, vil](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) den være tilgængelig som en betingelse [i Office](apply-sensitivity-label-automatically.md) automatisk mærkater med følsomhedsmærkater, anvend automatisk opbevaringsetiketpolitik baseret på en betingelse og i Kommunikation [overensstemmelse.](communication-compliance.md)
