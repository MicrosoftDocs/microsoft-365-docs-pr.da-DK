---
title: Oprettelse og test af binære filer på  Test Base
description: Sådan opretter og tester du binære filer på testbasen
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 04/08/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 99e2a26294d8e67854387d3c4f3d41c469a97a50
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "66858618"
---
# <a name="creating-and-testing-binary-files-on-test-base"></a>Oprettelse og test af binære filer på  Test Base

Dette afsnit indeholder alle de trin, der er nødvendige for at oprette en ny pakke, der indeholder binære filer, til upload og test på testbasen. Hvis du allerede har en færdigbygget .zip-fil, kan du se [Uploader færdigbygget Zip-pakke](uploadApplication.md) for at uploade din fil.

> [!IMPORTANT]
> Hvis du ikke har en **Test Base-konto** , skal du oprette en, før du fortsætter, som beskrevet i [Opret en testbasekonto](createAccount.md).

## <a name="create-a-new-package"></a>Opret en ny pakke

I [Azure Portal](https://portal.azure.com/) skal du gå til den **testbasekonto**, du opretter og uploader din pakke for, og udføre de efterfølgende trin. 

Vælg **Ny pakke** i menuen til venstre under **Pakkekatalog**. Klik derefter på det første kort **'Opret ny pakke online'** for at bygge din pakke online i 5 trin!

> [!div class="mx-imgBorder"]
> ![Opret en ny pakkeguide](Media/testapplication01.png)

### <a name="step-1-define-content"></a>Trin 1. Definer indhold

1. I afsnittet **Pakkekilde** skal du vælge Binære filer (f.eks. .exe, .msi) i kildetypen Pakke.

   > [!div class="mx-imgBorder"]
   > ![Vælg pakkekilden](Media/testapplication02.png)

2. Upload derefter din appfil ved at klikke på knappen 'Vælg fil' eller markere afkrydsningsfeltet for at bruge eksempelskabelonen Testbase som udgangspunkt, hvis du endnu ikke har din fil klar.

   > [!div class="mx-imgBorder"]
   > ![Vælg fil](Media/testapplication03.png)

3. Skriv pakkens navn og version i afsnittet **Grundlæggende oplysninger** .

   > [!NOTE]
   > Kombinationen af pakkenavn og version skal være entydig på din Test Base-konto.

   > [!div class="mx-imgBorder"]
   > ![Angiv grundlæggende oplysninger](Media/testapplication04.png)

4. Når alle de ønskede oplysninger er angivet, kan du gå videre til næste fase ved at klikke på knappen **Næste: Konfigurationstest** .

   > [!div class="mx-imgBorder"]
   > ![Næste trin](Media/testapplication05.png)

### <a name="step-2-configure-test"></a>Trin 2. Konfigurer test

1. Vælg **testtypen**. Der understøttes to testtyper:
   - En **OOB-test (Out of Box)** udfører en installation, start, lukning og fjernelse af pakken. Efter installationen gentages startlukningsrutinen 30 gange, før der køres en enkelt fjernelse. OOB-testen giver dig standardiseret telemetri på din pakke, så du kan sammenligne på tværs af Windows-builds.
   - En **funktionel test** udfører dine uploadede testscript(r) på pakken. Scriptene køres i den angivne rækkefølge, og en fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.

   > [!NOTE]
   > Out of Box-test er valgfri nu.

   > [!div class="mx-imgBorder"]
   > ![Out of Box-test er valgfri](Media/testapplication07.png)

2. Når alle nødvendige oplysninger er udfyldt, kan du gå til trin 3 ved at klikke på knappen Næste nederst. Der vises en meddelelse, når testscripts genereres.

   > [!div class="mx-imgBorder"]
   > ![Generér scriptprompts](Media/testapplication08.png)

### <a name="step-3-edit-package"></a>Trin 3. Rediger pakke

1. Under fanen Rediger pakke kan du
   - Kontrollér pakkemappen og filstrukturen i **Package Preview**.
   - Rediger dine scripts online med **PowerShell-kodeeditoren**.

   > [!NOTE]
   > Der er oprettet nogle eksempelscripts til din reference. Du skal gennemgå hvert script omhyggeligt og erstatte kommando- og procesnavnet med dit eget. 

   > [!div class="mx-imgBorder"]
   > ![rediger scripts online](Media/testapplication09.png)

2. I **prøveversionen af pakken** kan du, afhængigt af dine behov,
   - Opret en ny mappe.
   - Opret et nyt script.
   - Upload en ny fil.

   > [!div class="mx-imgBorder"]
   > ![Opret ressourcer](Media/testapplication10.png)

3. Under **mappen scripts** er der oprettet eksempelscripts og scriptkoder for dig. Alle scriptkoder kan redigeres. Du kan tildele dem igen, så de refererer til dine scriptstier.
   - Hvis **Out of Box-testen** er valgt i trin 2, kan du se mappen **Outofbox** under mappen scripts. Du har også mulighed for at tilføje koden **'Genstart efter installation'** for installationsscriptet.

   > [!div class="mx-imgBorder"]
   > ![Referencescript](Media/testapplication11.png)

   > [!NOTE]
   > Scriptkoder til installation, start og lukning er obligatoriske for OOB-testtypen. Tildeling af koder sikrer, at den korrekte scriptsti bruges, når testen startes.

   > [!div class="mx-imgBorder"]
   > ![Prompt om redigering af pakke](Media/testapplication11-2.png)

   - Hvis **den funktionelle test** er valgt i trin 2, kan du se den **funktionelle** mappe under mappen scripts. Du kan tilføje mere funktionelle testscripts ved hjælp af knappen **'Føj til funktionel testliste'** . Du skal bruge mindst ét (1) script og kan tilføje op til otte (8) funktionelle testscripts.

   > [!div class="mx-imgBorder"]
   > ![Føj til funktionstestliste](Media/testapplication12.png)

   > [!NOTE]
   > Mindst 1 funktionel scriptkode er obligatorisk for den funktionelle testtype.

   Hvis du vil tilføje flere funktionelle scripts, kan du klikke på **listen "Føj til funktionel test"**. Derefter vises handlingspanelet. Du kan:
   - Omarranger scriptstierne ved at trække med venstre ellipseknapper. De funktionelle scripts kører i den rækkefølge, de er angivet i. En fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.
   - Angiv 'Genstart efter udførelse' for flere scripts.
   - Anvend opdatering før på en bestemt scriptsti. Dette er for brugere, der ønsker at udføre funktionelle test, for at angive, hvornår Windows Update programrettelse skal anvendes i sekvensen af udførelsen af deres funktionelle testscripts.

   > [!div class="mx-imgBorder"]
   > ![funktionel test](Media/testapplication13.png)

4. Når alle nødvendige oplysninger er udfyldt, kan du gå til trin 4 ved at klikke på knappen Næste nederst.

### <a name="step-4-test-matrix"></a>Trin 4. Testmatrix

1. Vælg **opdateringstypen for operativsystemet** under fanen Testmatrix. Der understøttes to opdateringstyper for operativsystemet.
   - **Sikkerhedsopdateringerne** gør det muligt for din pakke at blive testet i forhold til trinvise fald i de månedlige sikkerhedsopdateringer, der udgives som foreløbige Windows-opdateringer.
   - **Funktionsopdateringer** gør det muligt for din pakke at blive testet i forhold til de foreløbige Windows-foreløbige funktionsopdateringer, der bygges ud fra Windows Insider Program.

2. Vælg operativsystemversionerne til test af sikkerhedsopdatering.

   Hvis **sikkerhedsopdateringer** er valgt i opdateringstypen for operativsystemet, skal du vælge de operativsystemversioner af Windows, som din pakke skal testes på.

   > [!NOTE]
   > Hvis du vælger at teste pakken i forhold til både server- og klient-OSes, skal du sørge for, at pakken er kompatibel og kan køre på begge OSes.

3. Vælg indstillinger for test af funktionsopdatering.
   - Hvis **funktionsopdateringer** er valgt i opdateringstypen for operativsystemet, skal du fuldføre følgende indstillinger.
   - For **Insider Channel** skal du vælge den Windows Insider Program kanal som det build, som dine pakker skal testes mod. Vi bruger i øjeblikket builds, der flightes i **Insider Beta Channel**.
   - For **OS baseline for Insight** skal du vælge den Windows OS-version, der skal bruges som baseline, når du sammenligner dine testresultater.

   > [!div class="mx-imgBorder"]
   > ![Vælg Windows OS-versionen](Media/testapplication14.png)

4. Når alle de nødvendige oplysninger er udfyldt, kan du gå til trin 5 (det sidste trin) ved at klikke på knappen Næste nederst.

### <a name="step-5-review--publish"></a>Trin 5. Gennemse og publicer

1. Gennemse alle oplysninger for at få korrekthed og nøjagtighed af din kladdepakke. Hvis du vil foretage rettelser, kan du gå tilbage til de tidlige trin, hvor du har angivet indstillingerne efter behov.

   > [!div class="mx-imgBorder"]
   > ![Gennemse pakke](Media/testapplication15.png)

2. Du kan også markere meddelelsesfeltet for at modtage mailmeddelelsen om pakken for meddelelsen om fuldførelse af valideringskørsel.

   > [!div class="mx-imgBorder"]
   > ![Anmeldelse](Media/testapplication16.png)

3. Når du er færdig med at færdiggøre konfigurationen af inputdata, skal du klikke på **Publicer** for at uploade pakken til testbasen.  Den efterfølgende meddelelse vises, når pakken er publiceret og har åbnet bekræftelsesprocessen.  

   > [!NOTE]
   > Pakken skal bekræftes, før den accepteres til fremtidige test. Bekræftelsen kan tage op til 24 timer, da den omfatter kørsel af pakken i et faktisk testmiljø. 

   > [!div class="mx-imgBorder"]
   > ![Prompter om udgivelse af pakke](Media/testapplication17.png)

4. Du omdirigeres til siden **Administrer pakker** for at kontrollere status for den nyligt overførte pakke.

   > [!div class="mx-imgBorder"]
   > ![Administrer pakker](Media/testapplication18.png)

   > [!NOTE]
   > Når bekræftelsesprocessen er fuldført, ændres bekræftelsesstatussen til Accepteret. På nuværende tidspunkt er der ikke behov for yderligere handlinger. Din pakke hentes automatisk til udførelse, når dine konfigurerede operativsystemer har nye tilgængelige opdateringer. Hvis bekræftelsesprocessen mislykkes, er pakken ikke klar til test. Kontrollér loggene, og vurder, om der opstod fejl. Du skal muligvis også kontrollere indstillingerne for pakkekonfigurationen for potentielle problemer.

### <a name="resume-creation-of-a-saved-draft-package"></a>Fortsæt oprettelsen af en gemt kladdepakke

Hvis du har tidligere kladdepakker, kan du få vist listen over dine gemte kladdepakker på siden **Ny pakke** . Hvis du klikker på blyantsikonet **'Rediger'** , kan du fortsætte redigeringen af den pakke, du valgte, hvor du slap, som beskrevet i kolonnen **Status** .

> [!div class="mx-imgBorder"]
> ![Ny pakkeside](Media/testapplication19.png)

> [!NOTE]
> Dashboardet viser kun de gemte kladdepakker. Hvis du vil have vist udgivne pakker, skal du gå til siden Administrer pakker.

