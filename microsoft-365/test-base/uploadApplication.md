---
title: Upload pakken
description: Sådan uploader du dit program, dine binære filer og dine afhængigheder til testbasen
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 23c21eae9ad149aea5442c0c8a00f716f3d22506
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099471"
---
# <a name="upload-your-test-base-package-zip"></a>Upload din Test Base-pakke (Zip) 

På siden Test Base-portalen skal du gå til indstillingen **Ny pakke** på navigationslinjen til venstre og derefter klikke på **Ældre overførselsoplevelse** for at aktivere zip-overførselsoplevelsen som vist nedenfor:

:::image type="content" alt-text="Upload en ny pakke." source="Media/testapplication01.png" lightbox="Media/testapplication01.png":::

:::image type="content" alt-text="Anvend handlingen." source="Media/testapplication21.png" lightbox="Media/testapplication21.png":::

Når du er der, skal du følge nedenstående trin for at uploade en ny pakke.

## <a name="enter-details-for-your-package"></a>Angiv oplysninger om pakken

Under fanen Testoplysninger skal du skrive pakkens navn, version og andre oplysninger som ønsket.

**Køreklar** og **funktionel test** kan udføres via dette dashboard.

Nedenstående trin indeholder en vejledning i, hvordan du udfylder dine pakkeoplysninger:

1. Angiv det navn, pakken skal have, i feltet `Package name` .

    > [!NOTE]
    > Det angivne pakkenavn og den angivne versionskombination skal være entydig i din organisation. Dette valideres af fluebenet som vist nedenfor.

    - Hvis du vælger at genbruge navnet på en pakke, skal versionsnummeret være entydigt (dvs. det er aldrig blevet brugt med en pakke med det pågældende navn).

    - Hvis kombinationen af pakkenavnet + versionen ikke passerer entydighedskontrollen, får du vist en fejlmeddelelse, hvor der står *"Pakke med denne pakkeversion findes allerede"*.

    :::image type="content" alt-text="Billede til overførsel af pakkeinstruktioner." source="Media/Instructions.png":::

2. Angiv en version i feltet "Pakkeversion".

    :::image type="content" alt-text="Pakkeversion." source="Media/ApplicationVersion.png":::

3. Vælg den testtype, du vil køre på denne pakke.

    En **OOB-test (Out-of-Box)** udfører en *installation*, *start*, *lukning* og *fjernelse* af pakken. Efter installationen gentages startlukningsrutinen 30 gange, før der køres en enkelt fjernelse.

    Denne OOB-test giver dig standardiseret telemetri på din pakke, så du kan sammenligne på tværs af Windows builds.

    En **funktionel test** udfører dine uploadede testscript(r) på pakken. Scriptene køres i overførselssekvensen, og en fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.

    > [!NOTE]
    > **Alle** scripts kører højst i 80 minutter.

4. Vælg opdateringstypen for operativsystemet.

    - 'Sikkerhedsopdateringer' gør det muligt for din pakke at blive testet i forhold til trinvise fald i Windows foreløbige månedlige sikkerhedsopdateringer.
    - 'Funktionsopdateringer' gør det muligt for din pakke at blive testet i forhold til Windows foreløbige toårige funktionsopdateringer builds fra Windows Insider Program.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Opdateringstype for operativsystem." source="Media/OSUpdateType.png":::

5. Vælg operativsystemversionerne til test af sikkerhedsopdatering.

    På rullelisten med flere valg skal du vælge operativsystemversionerne af Windows pakken installeres på.

    - Hvis du kun vil teste pakken i forhold til Windows klientoperativsystemer, skal du vælge de relevante Windows klientoperativsystemer på menulisten.
    - Hvis du kun vil teste pakken i forhold til Windows Server-operativsystemer, skal du vælge de relevante Windows Server OS-versioner på menulisten.
    - Hvis du vil teste pakken i forhold til Windows klient- og Windows serveroperativsystemer, skal du vælge alle relevante operativsystemer på menulisten.

    > [!NOTE]
    > Hvis du vælger at teste pakken mod både server- og klient-OSes, skal du sørge for, at pakken er kompatibel og kan køre på begge OSes

    :::image type="content" alt-text="Valg af en operativsystemversion." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Vælg indstillinger for test af funktionsopdatering:

    - I indstillingen "Vælg insiderkanal" skal du vælge `Windows Insider Program Channel` som det build, som dine pakker skal testes mod.

      Vi bruger i øjeblikket builds, der flightes i Insider Beta Channel.

    - Vælg den Windows os-version, der skal bruges som baseline, når du sammenligner dine testresultater, i indstillingen "Vælg os-baseline for Insight".

    > [!NOTE]
    > Vi understøtter ikke funktionsopdateringstest for server-OSes på nuværende tidspunkt
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Test af funktionsopdatering." source="Media/FeatureUpdate.png":::

7. En side med fuldførte testoplysninger bør se sådan ud:

    :::image type="content" alt-text="Visning af testoplysninger." source="Media/TestDetails.png":::



## <a name="upload-your-binaries-dependencies-and-scripts"></a>Upload dine binære filer, afhængigheder og scripts

Under denne fane skal du uploade en enkelt zip-pakke, der indeholder dine binære filer, afhængigheder og scripts, der bruges til at køre din testpakke.

> [!NOTE]
> Zip-pakkens størrelse skal være mellem mindst 10 MB og højst 2 GB.

**zip-fil til Upload pakke**

:::image type="content" alt-text="Upload dine binære filer." source="Media/AddBinaries.png":::

  - Uploadede afhængigheder kan omfatte testrammer, scriptingprogrammer eller data, der skal tilgås for at køre dit program eller dine testcases. Du kan f.eks. uploade Selenium og et installationsprogram til webdriver for at hjælpe med at køre browserbaserede test.
  - Det er bedste praksis at sikre, at dine scriptaktiviteter holdes modulopbyggede, dvs. 
    - Scriptet `Install` udfører kun installationshandlinger.
    - Scriptet `Launch` starter kun programmet.
    - Scriptet `Close` lukker kun programmet.
    - Det valgfrie `Uninstall` script fjerner kun programmet.

**I øjeblikket understøtter portalen kun PowerShell-scripts.**



## <a name="the-tasks-tab"></a>Fanen Opgaver

Under fanen Opgaver forventes du at angive stierne til dine testscripts, som findes i den zip-mappe, du overførte under fanen Binære filer.

  - **Testscripts, der ikke er i brug:** Skriv de relative stier til installationen, start, luk og fjern scripts. Du har også mulighed for at vælge yderligere indstillinger for installationsscriptet.
  - **Funktionelle testscripts:** Skriv den relative sti til hvert funktionelt testscript, der uploades. Der kan tilføjes yderligere funktionelle testscripts ved hjælp af knappen ```Add Script``` . Du skal bruge mindst ét (1) script og kan tilføje op til otte (8) funktionelle testscripts. 
  
    Scriptene kører i den rækkefølge, de er angivet i. En fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.
    Du har også mulighed for at vælge yderligere indstillinger for hvert script, der er angivet.

**Angiv scriptsti**

:::image type="content" alt-text="Billede af testopgave." source="Media/testtask.png":::

Nedenfor kan du se et eksempel på, hvordan du angiver den relative sti i en mappestruktur:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** ville have gjort det. _ScriptX.ps1_ som den relative sti.
  - **Script.ps1** vil have _folder1/script.ps1_ som den relative sti.



## <a name="choose-your-test-options"></a>Vælg dine testindstillinger. 

Fanen ```Test Options``` er beregnet til brugere, der ønsker at udføre funktionelle test, for at angive, hvornår Windows Update programrettelse skal anvendes i sekvensen af udførelsen af deres funktionelle testscripts.

:::image type="content" alt-text="Billede af testindstillinger. Enten køreklare eller funktionelle test." source="Media/testoptions.png":::

Vælg _**Gennemse**_ for at navigere til næste fane og gennemse dine valgte testindstillinger.



## <a name="review-your-selections-to-create-your-package"></a>Gennemse dine valg for at oprette pakken.

1. Under denne fane viser tjenesten dine testoplysninger og kører en hurtig fuldstændighedskontrol.

    Du kan se, om du kan fortsætte til næste trin eller ej, ved at få vist en meddelelse om, at valideringen **er bestået** eller **valideringen mislykkedes** .

2. Gennemse dine testoplysninger, og klik på knappen **Opret** , hvis de er opfyldt.

    :::image type="content" alt-text="Vis validering." source="Media/validation.png" lightbox="Media/validation.png":::

3. Dette føjer din pakke til Test Base-miljøet. Hvis pakken oprettes, udløses en automatiseret test, der kontrollerer, om pakken kan udføres korrekt på Azure.

    :::image type="content" alt-text="Vellykket resultat." source="Media/successful.png":::

    > [!NOTE]
    > Du får en meddelelse fra Azure Portal om, at pakkebekræftelsen lykkedes eller mislykkedes.
    >
    > Bemærk, at processen kan tage op til 24 timer, så det er sandsynligt, at din webside får timeout, hvis du ikke er aktiv på den, og derfor informerer meddelelsen dig ikke om fuldførelsen af denne on-demand-kørsel.

    - Peradventure dette sker, kan du få vist status for din pakke på fanen **Administrer pakker** .

      :::image type="content" alt-text="Billede til administration af pakker." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - I forbindelse med vellykkede test kan resultaterne ses via siderne **Testoversigt**, **Resultater af sikkerhedsopdateringer** og **Resultat af funktionsopdateringer** med planlagte intervaller, der ofte starter et par dage efter upload.
  
    - Mens der opstod fejl i testene, skal du overføre en ny pakke. 

      Du kan downloade **testlogfilerne** for yderligere analyse fra siderne **med resultater af sikkerhedsopdateringer** og **funktionsopdateringer** .

    - Hvis du oplever gentagne testfejl, skal du kontakte testbasepreview@microsoft.com med oplysninger om fejlen.

## <a name="next-steps"></a>Næste trin

Se vores retningslinjer for indhold via linket nedenfor.

> [!div class="nextstepaction"]
> [Næste trin](contentguideline.md)
