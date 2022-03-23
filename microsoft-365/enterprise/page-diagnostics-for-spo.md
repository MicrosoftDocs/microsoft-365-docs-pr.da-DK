---
title: Brug værktøjet Sidediagnosticering til SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/03/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: Brug Sidediagnosticering til SharePoint til at analysere SharePoint moderne portal og klassiske publiceringssider ud fra et foruddefineret sæt kriterier for ydeevne.
ms.openlocfilehash: 7e1931b7cdc661b5e0a6ed8751a26f8a77e4bc2e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591017"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Brug sidediagnosticering til SharePoint værktøjet

Denne artikel beskriver, hvordan du bruger værktøjet **Sidediagnosticering til SharePoint** til at analysere moderne og klassiske webstedssider i SharePoint mod et foruddefineret sæt kriterier for ydeevne.

Sidediagnosticering til SharePoint kan installeres til:

- **Microsoft Edge** [(Edge-udvidelse)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(Chrome-udvidelse)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>Version **2.0.0** og nyere indeholder understøttelse af moderne sider ud over klassiske webstedssider. Hvis du ikke er sikker på, hvilken version af værktøjet du bruger, kan du vælge linket  Om eller ellipserne (...) for at bekræfte din version. **Opdater altid til den nyeste version, når** du bruger værktøjet.

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Dette værktøj fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Værktøjet genererer en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et foruddefineret sæt regler, og viser detaljerede oplysninger, når resultaterne for en test ligger uden for den oprindelige værdi. SharePoint Online kan administratorer og designere bruge værktøjet til at foretage fejlfinding af problemer med ydeevnen og til at sikre, at nye sider optimeres før publiceringen.

Værktøjet Sidediagnosticering er udviklet til kun at analysere SharePoint webstedssider, ikke systemsider som *allitems.aspx* eller *sharepoint.aspx*. Hvis du forsøger at køre værktøjet på en systemside eller på en anden side, som ikke er et websted, modtager du en fejlmeddelelse om, at værktøjet ikke kan køres på den pågældende sidetype.

> [!div class="mx-imgBorder"]
> ![Skal køre på en SharePoint side.](../media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Dette er ikke en fejl i værktøjet, da det ikke har nogen værdi at vurdere biblioteker eller systemsider. Gå til en SharePoint for at bruge værktøjet. Hvis denne fejl opstår på SharePoint side, skal du kontrollere mastersiden for at sikre, SharePoint metatags ikke er blevet fjernet.

Hvis du vil give feedback om værktøjet, skal du vælge ellipsen i øverste højre hjørne af værktøjet og derefter vælge [Giv feedback](https://go.microsoft.com/fwlink/?linkid=874109).

> [!div class="mx-imgBorder"]
> ![Giv feedback.](../media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Installere Sidediagnosticering til SharePoint værktøjet

Installationsproceduren i dette afsnit fungerer for både Chrome og Microsoft Edge browsere.

> [!IMPORTANT]
> Microsoft læser ikke data eller sideindhold, der er analyseret af værktøjet Sidediagnosticering til SharePoint, og vi registrerer ikke nogen personlige oplysninger, websteder eller downloadoplysninger. De eneste identificerbare oplysninger, der logføres til Microsoft af værktøjet, er lejernavnet, optællinger af regler, der er mislykkedes, og den dato og det klokkeslæt, hvor værktøjet blev kørt. Disse oplysninger bruges af Microsoft til bedre at forstå brugstendenser og almindelige problemer med ydeevnen for moderne portal- og publiceringswebsteder.

1. Installer Sidediagnosticering til SharePoint til **Microsoft Edge** [(Microsoft Edge-udvidelse)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) **eller Chrome** [(Chrome-udvidelse)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi). Gennemse brugerens politik om beskyttelse af personlige oplysninger, der findes på beskrivelsessiden i butikken. Når du føjer værktøjet til din browser, får du vist følgende meddelelse om tilladelser.

    > [!div class="mx-imgBorder"]
    > ![Udvidelsestilladelser.](../media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Denne meddelelse er på plads, fordi en side kan indeholde indhold fra placeringer uden for SharePoint afhængigt af webdelene og tilpasningerne på siden. Det betyder, at værktøjet læser anmodninger og svar, når der klikkes på startknappen, og kun for den aktive SharePoint, hvor værktøjet kører. Disse oplysninger registreres lokalt i webbrowseren og er tilgængelige for dig via knappen Eksportér til **JSON** eller Eksportér til **HAR** på værktøjets _Netværkssporing-fane_ . Oplysningerne sendes ikke til eller registreres af **Microsoft.** Værktøjet respekterer Microsofts politik om beskyttelse af personlige oplysninger, som er [tilgængelig her](https://go.microsoft.com/fwlink/p/?linkid=857875).

    Tilladelsen _Administrer dine downloads_ dækker brugen af værktøjets Eksportér **til JSON-funktionalitet** . Følg virksomhedens egne retningslinjer for beskyttelse af personlige oplysninger, før du deler JSON-filen uden for din organisation, da resultaterne indeholder URL-adresser og kan klassificeres som PII (personligt identificerbare oplysninger).
1. Hvis du vil bruge værktøjet i tilstanden Incognito eller InPrivate, skal du følge fremgangsmåden for din browser:
    1. I Microsoft Edge du gå til **Udvidelser** eller skrive _edge://extensions_ i URL-linjen og **vælge Detaljer** for udvidelsen. I indstillingerne for udvidelser skal du markere afkrydsningsfeltet for **tillad i InPrivate**.
    1. I Chrome skal du gå **til Udvidelser** eller _chrome://extensions_ i URL-linjen og **vælge Detaljer** for udvidelsen. I indstillingerne for filtypenavn skal du vælge skyderen for **tillad i Incognito**.
1. Gå til siden SharePoint websted på SharePoint Online, som du gerne vil gennemgå. Vi har tilladt at "forsinke indlæsningen" af elementer på sider. derfor stopper værktøjet ikke automatisk (dette er tilst5 for at tage højde for alle sideindlæsningsscenarier). Hvis du vil stoppe indsamlingen, skal du **vælge Stop**. Sørg for, at sideindlæsningen er afsluttet, før du stopper dataindsamlingen, ellers registrerer du kun en delvis sporing.
1. Klik på værktøjslinjen i udvidelsen ![Sidediagnosticering til SharePoint logo.](../media/page-diagnostics-for-spo/pagediag-icon32.png) for at indlæse værktøjet, så får du vist følgende pop op-vindue for filtypenavn:

    ![Pop op-værktøjet Sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-Landing.png)

Vælg **Start for** at begynde at indsamle data til analyse.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Hvad du ser i værktøjet Sidediagnosticering til SharePoint side

1. Klik på ellipserne (...) i øverste højre hjørne af værktøjet for at finde følgende links:
   1. Linket **Yderligere ressourcer** giver generel vejledning og detaljer om værktøjet, herunder et link tilbage til denne artikel.
   1. Linket **Giv feedback** indeholder et link til webstedet SharePoint _og webstedet Samarbejdsbrugerstemme_.
   1. **Om-linket** indeholder den aktuelt installerede version af værktøjet og et direkte link til værktøjets tredjepartsmeddelelse.  
1. **Korrelations-id'et, SPRequestDuration, SPIISLatency****,** sideindlæsningstiden og **URL-oplysningerne** er informations- og kan bruges til nogle få formål.

    > [!div class="mx-imgBorder"]
    > ![Oplysninger om sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **Korrelations-id** er et vigtigt element, når du arbejder med Microsoft Support, da det giver dem mulighed for at indsamle yderligere diagnostiske data til den specifikke side.
   - **SPRequestDuration er** den tid, det tager SharePoint at behandle siden. Strukturel navigation, store billeder, masser af API-opkald kan alle bidrage til længere varighed.
   - **SPIISLatency er** tiden i millisekunder, der er taget for at SharePoint Online med at indlæse siden. Denne værdi omfatter ikke den tid, det tager for webprogrammet at svare.
   - **Sideindlæsningstiden** er den samlede tid, der er registreret af siden fra tidspunktet for anmodningen til det tidspunkt, hvor svaret blev modtaget og gengivet i browseren. Denne værdi påvirkes af en række faktorer, herunder netværksventetid, computerens ydeevne og den tid, det tager browseren at indlæse siden.
   - **URL-adressen** til side (Uniform Resource Locator) er webadressen på den aktuelle side.

1. Fanen [**Diagnosticeringstest**](#how-to-use-the-diagnostic-tests-tab) viser analyseresultaterne i tre kategorier. **Ingen handling påkrævet**, **Forbedringsmuligheder** og **Opmærksomhed påkrævet**. Hvert testresultat repræsenteres af et element i en af disse kategorier som beskrevet i følgende tabel:

    |Kategori  |Farve  |Beskrivelse  |
    |---------|---------|---------|
    |**Handling påkrævet** |Rød |Testresultater ligger uden for den oprindelige værdi og påvirker sidens ydeevne. Følg afhjælpningsvejledningen.|
    |**Muligheder for forbedring** |Gul |Testresultater ligger uden for den oprindelige værdi og kan bidrage til problemer med ydeevnen. Der kan gælde testspecifikke kriterier.|
    |**Ingen handling påkrævet** |Grøn |Testresultatet falder inden for testens oprindelige værdi.|

    > [!div class="mx-imgBorder"]
    > ![Sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Fanen [**Netværkssporing indeholder**](#how-to-use-the-network-trace-tab-and-how-to-export-a-har-file) oplysninger om anmodninger og svar på sideopbygn.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Sådan bruger du fanen Diagnosticeringstest

Når du analyserer en moderne portalside eller en klassisk publiceringsside fra SharePoint med værktøjet Sidediagnosticering til SharePoint, analyseres resultaterne ved hjælp af foruddefinerede regler, der sammenligner resultater med oprindelige værdier og vises på  fanen Diagnosticeringstest. Regler for visse test kan bruge forskellige oprindelige værdier til moderne portalwebsteder og klassiske publiceringswebsteder, afhængigt af hvor specifik ydeevne  karakteristika er forskellige mellem de to.

Testresultater, der vises i  kategorierne Muligheder  for forbedring eller Obligatorisk opmærksomhed, angiver områder, der skal gennemses i forhold til anbefalede fremgangsmåder, og som kan vælges for at vise yderligere oplysninger om resultatet. Detaljer for hvert element indeholder et Få _mere at vide-link_ , som fører dig direkte til den relevante vejledning i forbindelse med testen. Testresultater, der vises i kategorien **Ingen handling påkrævet** angiver overholdelse af den relevante regel og viser ikke yderligere oplysninger, når den er markeret.

Oplysningerne i fanen Diagnosticeringstest fortæller dig ikke, hvordan du designer sider, men fremhæver faktorer, der kan påvirke sidens ydeevne. Nogle sidefunktioner og -tilpasninger har en uundgåelig indvirkning på sidens ydeevne og bør revideres med henblik på potentiel afhjælpning eller udeladelse fra siden, hvis deres virkning har betydning.

Røde eller gule resultater kan også angive webdele, der opdaterer data for ofte. Virksomhedens nyheder opdateres f.eks. ikke hver anden, men brugerdefinerede webdele er ofte opbygget til at hente de seneste nyheder hvert sekund i stedet for at implementere cachelagringselementer, som kan forbedre den samlede brugeroplevelse. Husk, når du med medtage webdele på en side, at der ofte er enkle måder at reducere deres ydeevne på ved at evaluere værdien af hver tilgængelig parameter for at sikre, at den er indstillet korrekt til det tiltænkte formål.

>[!NOTE]
>Klassiske teamwebsteder, der ikke har publiceringsfunktionen aktiveret, kan ikke bruge CDN'er. Når du kører værktøjet på disse websteder, forventes den CDN test at mislykkes og kan ignoreres, men alle de resterende test er gældende. Den ekstra funktionalitet i SharePoint-publiceringsfunktionen kan øge sideindlæsningstider, så den skal ikke være aktiveret blot for at CDN funktionalitet.

>[!IMPORTANT]
>Testregler tilføjes og opdateres jævnligt, så du kan se den nyeste version af værktøjet for at få mere at vide om de aktuelle regler og specifikke oplysninger, der er medtaget i testresultaterne. Du kan kontrollere versionen ved at administrere udvidelser, og udvidelsen vil afgøre, om der findes en opdatering.

## <a name="how-to-use-the-network-trace-tab-and-how-to-export-a-har-file"></a>Sådan bruger du fanen Netværkssporing, og hvordan du eksporterer en HAR-fil

Fanen **Netværkssporing** indeholder detaljerede oplysninger om begge anmodninger om at opbygge siden og de svar, der modtages fra SharePoint.

1. **Se efter elementindlæsningstider, der er markeret som rød**. Hver anmodning og hvert svar er farvekodet for at indikere dens påvirkning af sidens overordnede ydeevne ved hjælp af følgende målepunkter for ventetid:
    - Grøn: \< 500 ms
    - Gul: 500-1000 ms
    - Rød: \> 1000 ms

    > [!div class="mx-imgBorder"]
    > ![Netværkssporing.](../media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    I det billede, der er vist ovenfor, hører det røde element til standardsiden. Den vil altid vise rød, medmindre siden indlæses i \< 1000 ms (mindre end 1 sekund).

2. **Indlæsningstider for testelement**. I nogle tilfælde vil der ikke være nogen klokkeslæts- eller farveindikator, fordi elementerne allerede er cachelagret af browseren. For at teste dette korrekt skal du åbne siden, rydde browsercachen og derefter klikke på **Start** , da det vil gennemtvinge en "fordømt" sideindlæsning og være en sand afspejling af den indledende sideindlæsning. Dette skal derefter sammenlignes med den "varme" sideindlæsning, da det også hjælper med at afgøre, hvilke elementer der cachelagres på siden.

3. **Del relevante oplysninger med andre, som kan hjælpe med at undersøge problemer**. Den anbefalede fremgangsmåde er at dele detaljer eller oplysninger i værktøjet med dine udviklere eller en teknisk supportperson ved hjælp af **Aktivér eksport til HTTP-arkiv (HAR** ). 

   > [!div class="mx-imgBorder"]
   > ![Aktivér eksport til HAR.](../media/page-diagnostics-for-spo/pagediag-submithar.png)

Dette skal være aktiveret, før du klikker på Start, hvilket derefter aktiverer fejlfindingstilstand i din browser. Det genererer en HTTP-arkivfil (HAR), som derefter kan åbnes via fanen "Netværkssporing". Klik på "Eksportér til HAR", og så hentes filen til din computer, og du kan derefter dele den tilsvarende. Filen kan åbnes i en række fejlfindingsværktøjer, f.eks. F12 Udviklerværktøjer og Fiddler.

> [!div class="mx-imgBorder"]
> ![Netværkssporing.](../media/page-diagnostics-for-spo/pagediag-networktracehar.png)

> [!IMPORTANT]
> Disse resultater indeholder URL-adresser, og som kan klassificeres som personidentificerbare oplysninger. Sørg for at følge din organisations retningslinjer, før du distribuerer disse oplysninger.

## <a name="engaging-with-microsoft-support"></a>Samarbejde med Microsoft Support

Vi har inkluderet en **funktion på Microsoft-supportniveau** , der kun bør anvendes, når du arbejder direkte på en supportsag. Brug af denne funktion giver dig ingen fordel, når de bruges uden supportteamets engagement, og det kan få siden til at fungere væsentligt langsommere. Der er ingen yderligere oplysninger, når du bruger denne funktion i værktøjet, da de yderligere oplysninger føjes til logføringen af tjenesten.

Ingen ændring er synlig, bortset fra at du får besked om, at du har aktiveret den, og din sideydeevne vil blive betydeligt forringet med 2-3 gange langsommere ydeevne aktiveret. Det er kun relevant for den pågældende side og den aktive session. Af denne grund bør dette bruges sparsomt og kun, når du aktivt har brug for support.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Sådan aktiveres funktionen på Microsoft-supportniveau

1. Åbn Sidediagnosticering til SharePoint værktøjet.
2. Tryk på **Alt-Skift-L på tastaturet**. Dette viser afkrydsningsfeltet **Aktivér supportlogføring** .
3. Markér afkrydsningsfeltet, og klik derefter på **Start** for at genindlæse siden og generere detaljeret logføring.

   > [!div class="mx-imgBorder"]
   > ![Supportindstillingen er aktiveret.](../media/page-diagnostics-for-spo/pagediag-support.png)
  
    Du skal notere korrelations-id'et (vises øverst i værktøjet) og give det til din supportrepræsentant, så de kan indsamle yderligere oplysninger om den diagnostiske session.

## <a name="related-topics"></a>Relaterede emner

[Finjustere ydeevnen SharePoint Online](tune-sharepoint-online-performance.md)

[Finjustere ydeevnen Office 365 finjustere ydeevnen](tune-microsoft-365-performance.md)

[Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Netværk, der kan levere indhold](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)