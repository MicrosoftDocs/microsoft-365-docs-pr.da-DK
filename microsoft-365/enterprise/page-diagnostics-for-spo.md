---
title: Brug værktøjet Sidediagnosticering til SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Brug værktøjet Sidediagnosticering til SharePoint til at analysere SharePoint moderne portal online og klassiske udgivelsessider i forhold til et foruddefineret sæt ydeevnekriterier.
ms.openlocfilehash: a4d2c0f6d298578290d9f7daf850c4744e2f8dff
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621838"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Brug sidediagnosticering til SharePoint værktøj

I denne artikel beskrives det, hvordan du bruger **sidediagnosticering til SharePoint værktøj** til at analysere SharePoint online moderne og klassiske webstedssider i forhold til et foruddefineret sæt ydeevnekriterier.

Værktøjet Sidediagnosticering til SharePoint kan installeres til:

- **Microsoft Edge** [(Edge-udvidelse)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(Chrome-udvidelse)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>Version **2.0.0** og nyere omfatter understøttelse af moderne sider ud over klassiske webstedssider. Hvis du ikke er sikker på, hvilken version af værktøjet du bruger, kan du vælge linket **Om** eller ellipsen (...) for at bekræfte din version. **Opdater altid til den nyeste version** , når du bruger værktøjet.

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Dette værktøj fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Værktøjet genererer en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et foruddefineret sæt regler, og viser detaljerede oplysninger, når resultaterne for en test falder uden for den oprindelige værdi. SharePoint Online-administratorer og -designere kan bruge værktøjet til at foretage fejlfinding af problemer med ydeevnen og til at sikre, at nye sider optimeres inden publicering.

Værktøjet Sidediagnosticering er udviklet til kun at analysere SharePoint webstedssider og ikke systemsider som *f.eks. allitems.aspx* eller *sharepoint.aspx*. Hvis du forsøger at køre værktøjet på en systemside eller på en anden side, der ikke findes på webstedet, får du vist en fejlmeddelelse, der fortæller, at værktøjet ikke kan køres for den pågældende type side.

> [!div class="mx-imgBorder"]
> ![Skal køre på en SharePoint side.](../media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Dette er ikke en fejl i værktøjet, da der ikke er nogen værdi i at vurdere biblioteker eller systemsider. Naviger til en SharePoint webstedsside for at bruge værktøjet. Hvis denne fejl opstår på en SharePoint side, skal du kontrollere mastersiden for at sikre, at de SharePoint metamærker ikke er blevet fjernet.

Hvis du vil give feedback om værktøjet, skal du vælge ellipsen i øverste højre hjørne af værktøjet og derefter vælge [Giv feedback](https://go.microsoft.com/fwlink/?linkid=874109).

> [!div class="mx-imgBorder"]
> ![Giv feedback.](../media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Installér sidediagnosticering til SharePoint værktøj

Installationsproceduren i dette afsnit fungerer for både Chrome- og Microsoft Edge-browsere.

> [!IMPORTANT]
> Microsoft læser ikke data eller sideindhold, der analyseres af Sidediagnosticering for SharePoint værktøj, og vi registrerer ikke personlige oplysninger, websteder eller downloadoplysninger. De eneste identificerbare oplysninger, der er logført til Microsoft af værktøjet, er lejernavnet, antallet af regler, der er mislykkedes, og den dato og det klokkeslæt, værktøjet blev kørt. Disse oplysninger bruges af Microsoft til bedre at forstå moderne portal- og publiceringstendenser for brug af websteder og almindelige problemer med ydeevnen.

1. Installér sidediagnosticering til SharePoint værktøj til **Microsoft Edge** [(Edge-udvidelse)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) eller **Chrome** [(Chrome-udvidelse)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi). Gennemse politikken for beskyttelse af personlige oplysninger for brugeren, som er angivet på beskrivelsessiden i butikken. Når du føjer værktøjet til din browser, får du vist følgende meddelelse om tilladelser.

    > [!div class="mx-imgBorder"]
    > ![Udvidelsestilladelser.](../media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Denne meddelelse er på plads, fordi en side kan indeholde indhold fra placeringer uden for SharePoint afhængigt af webdelene og tilpasningerne på siden. Det betyder, at værktøjet læser anmodninger og svar, når der klikkes på startknappen, og kun for den aktive SharePoint fane, hvor værktøjet kører. Disse oplysninger registreres lokalt af webbrowseren og er tilgængelige for dig via knappen **Eksportér til JSON** eller **Eksportér til HAR** på værktøjets fanen _Netværkssporing_ . **Oplysningerne sendes ikke til eller registreres af Microsoft.** (Værktøjet respekterer microsofts politik om beskyttelse af personlige oplysninger, der er tilgængelig [her](https://go.microsoft.com/fwlink/p/?linkid=857875)).

    Tilladelsen _Administrer dine downloads_ dækker brugen af værktøjets **Eksportér til JSON-funktionalitet** . Følg virksomhedens egne retningslinjer for beskyttelse af personlige oplysninger, før du deler JSON-filen uden for din organisation, da resultaterne indeholder URL-adresser, og som kan klassificeres som PII (Personligt identificerbare oplysninger).
1. Hvis du vil bruge værktøjet i tilstanden Incognito eller InPrivate, skal du følge proceduren for din browser:
    1. I Microsoft Edge skal du gå til **Udvidelser** eller skrive _edge://extensions_ på URL-adresselinjen og vælge **Detaljer** for udvidelsen. I indstillingerne for udvidelsen skal du markere afkrydsningsfeltet **tillad i InPrivate**.
    1. I Chrome skal du navigere til **Udvidelser** eller skrive _chrome://extensions_ på URL-adresselinjen og vælge **Detaljer** for udvidelsen. I indstillingerne for udvidelsen skal du vælge skyderen for **Tillad i Incognito**.
1. Gå til SharePoint webstedsside på SharePoint Online, som du vil gennemse. Vi har tilladt "forsinkelse af indlæsning" af elementer på sider. derfor stopper værktøjet ikke automatisk (dette er tilsigtet for at imødekomme alle scenarier for sideindlæsning). Hvis du vil stoppe samlingen, skal du vælge **Stop**. Sørg for, at sideindlæsningen er fuldført, før du stopper dataindsamlingen, ellers registrerer du kun en delvis sporing.
1. Klik på knappen på udvidelsens værktøjslinje ![Sidediagnosticering for SharePoint logo.](../media/page-diagnostics-for-spo/pagediag-icon32.png) for at indlæse værktøjet, og du får vist følgende pop op-vindue til udvidelse:

    ![Pop op til Værktøjet Sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-Landing.png)

Vælg **Start** for at begynde at indsamle data til analyse.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Det kan du se i værktøjet Sidediagnosticering for SharePoint

1. Klik på ellipsen (...) i øverste højre hjørne af værktøjet for at finde følgende links:
   1. Linket **Yderligere ressourcer** indeholder generel vejledning og oplysninger om værktøjet, herunder et link tilbage til denne artikel.
   1. Linket **Giv feedback** indeholder et link til _webstedet SharePoint websteder og samarbejdsbrugerens stemmewebsted_.
   1. Linket **Om** indeholder den aktuelt installerede version af værktøjet og et direkte link til værktøjets meddelelse fra tredjepart.  
1. **Oplysninger om korrelations-id, SPRequestDuration, SPIISLatency**, **Sideindlæsningstid** og **URL-adresse** er oplysende og kan bruges til nogle få formål.

    > [!div class="mx-imgBorder"]
    > ![Oplysninger om sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID** er et vigtigt element, når du arbejder med Microsoft Support, da det giver dem mulighed for at indsamle flere diagnosticeringsdata til den specifikke side.
   - **SPRequestDuration** er den tid, det tager SharePoint at behandle siden. Strukturel navigation, store billeder, mange API-kald kan alle bidrage til længere varigheder.
   - **SPIISLatency** er den tid i millisekunder, det tager for SharePoint Online at indlæse siden. Denne værdi omfatter ikke den tid, det tager webprogrammet at svare.
   - **Sideindlæsningstid** er den samlede tid, der registreres af siden fra tidspunktet for anmodningen til det tidspunkt, hvor svaret blev modtaget og gengivet i browseren. Denne værdi påvirkes af forskellige faktorer, herunder netværksventetid, computerens ydeevne og den tid, det tager for browseren at indlæse siden.
   - **Sidens URL-adresse** (Uniform Resource Locator) er webadressen på den aktuelle side.

1. Under fanen [**Diagnosticeringstest**](#how-to-use-the-diagnostic-tests-tab) vises analyseresultaterne i tre kategorier. **Der kræves ingen handling**, **forbedringsmuligheder** og **opmærksomhed kræves**. Hvert testresultat repræsenteres af et element i en af disse kategorier som beskrevet i følgende tabel:

    |Kategori  |Farve  |Beskrivelse  |
    |---------|---------|---------|
    |**Opmærksomhed kræves** |Rød |Testresultatet falder uden for den oprindelige værdi og påvirker sidens ydeevne. Følg afhjælpningsvejledningen.|
    |**Bedre muligheder** |Gul |Testresultatet falder uden for den oprindelige værdi og kan bidrage til problemer med ydeevnen. Der kan gælde testspecifikke kriterier.|
    |**Der kræves ingen handling** |Grøn |Testresultatet falder inden for testens oprindelige værdi.|

    > [!div class="mx-imgBorder"]
    > ![Sidediagnosticering.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Fanen [**Netværkssporing**](#how-to-use-the-network-trace-tab-and-how-to-export-a-har-file) indeholder oplysninger om anmodninger og svar om sidebuild.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Sådan bruger du fanen Diagnosticeringstests

Når du analyserer en SharePoint moderne portalside eller en klassisk udgivelsesside med værktøjet Sidediagnosticering for SharePoint, analyseres resultaterne ved hjælp af foruddefinerede regler, der sammenligner resultater i forhold til oprindelige værdier og vises under fanen **Diagnosticeringstest**. Regler for visse test kan bruge forskellige grundlæggende værdier for moderne portal og klassiske udgivelseswebsteder, afhængigt af hvor specifik ydeevne  karakteristika varierer mellem de to.

Testresultater, der vises i kategorierne **Forbedringsmuligheder** eller **Opmærksomhed påkrævede** kategorier, angiver områder, der skal gennemses i forhold til anbefalede fremgangsmåder, og kan vælges til at vise yderligere oplysninger om resultatet. Detaljer for hvert element omfatter linket _Få mere at vide_ , som fører dig direkte til den relevante vejledning, der er relateret til testen. Testresultater, der vises i kategorien **Ingen handling påkrævet** , angiver overholdelse af den relevante regel og viser ikke yderligere oplysninger, når de er valgt.

Oplysningerne under fanen Diagnosticeringstest fortæller dig ikke, hvordan du designer sider, men fremhæver faktorer, der kan påvirke sidens ydeevne. Nogle sidefunktioner og -tilpasninger har en uundgåelig indvirkning på sidens ydeevne og bør gennemgås for potentiel afhjælpning eller udeladelse fra siden, hvis deres indvirkning er betydelig.

Røde eller gule resultater kan også angive webdele, der opdaterer data for ofte. Virksomhedsnyheder opdateres f.eks. ikke hvert sekund, men brugerdefinerede webdele bygges ofte til at hente de seneste nyheder hvert sekund i stedet for at implementere cachelagringselementer, der kan forbedre den overordnede brugeroplevelse. Vær opmærksom på, når du medtager webdele på en side, at der ofte er enkle måder at reducere deres påvirkning af ydeevnen på ved at evaluere værdien af hver tilgængelig parameter for at sikre, at den er indstillet korrekt til det tilsigtede formål.

>[!NOTE]
>Klassiske teamwebsteder, hvor publiceringsfunktionen ikke er aktiveret, kan ikke bruge CDN'er. Når du kører værktøjet på disse websteder, forventes den CDN test at mislykkes og kan ignoreres, men alle de resterende test er gældende. Den ekstra funktionalitet i SharePoint publiceringsfunktion kan øge indlæsningstiden for sider, så den bør ikke aktiveres udelukkende for at tillade CDN funktionalitet.

>[!IMPORTANT]
>Testregler tilføjes og opdateres jævnligt, så se den nyeste version af værktøjet for at få oplysninger om aktuelle regler og specifikke oplysninger, der er inkluderet i testresultaterne. Du kan bekræfte versionen ved at administrere dine udvidelser, og udvidelsen vil rådgive om, hvorvidt en opdatering er tilgængelig.

## <a name="how-to-use-the-network-trace-tab-and-how-to-export-a-har-file"></a>Sådan bruger du fanen Netværkssporing, og hvordan du eksporterer en HAR-fil

Fanen **Netværkssporing** indeholder detaljerede oplysninger om begge anmodninger om at oprette siden og de svar, der modtages fra SharePoint.

1. **Søg efter indlæsningstider for elementer, der er markeret med rødt**. Hver anmodning og hvert svar farvekodes for at angive dens indvirkning på den overordnede sideydeevne ved hjælp af følgende ventetidsmålepunkter:
    - Grøn: \< 500 ms
    - Gul: 500-1000 ms
    - Rød: \> 1000 ms

    > [!div class="mx-imgBorder"]
    > ![Netværkssporing.](../media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    På det billede, der vises ovenfor, vedrører det røde element standardsiden. Det vises altid rødt, medmindre siden indlæses i \< 1000 ms (mindre end 1 sekund).

2. **Indlæsningstider for testelement**. I nogle tilfælde vil der ikke være tid eller farveindikator, fordi elementerne allerede er cachelagret af browseren. Hvis du vil teste dette korrekt, skal du åbne siden, rydde browsercachen og derefter klikke på **Start** , da det vil gennemtvinge en "kold" sideindlæsning og være en sand afspejling af den indledende sideindlæsning. Dette skal derefter sammenlignes med den "varme" sidebelastning, da det også hjælper med at afgøre, hvilke elementer der cachelagres på siden.

3. **Del relevante oplysninger med andre, der kan hjælpe med at undersøge problemer**. Hvis du vil dele de oplysninger eller oplysninger, der er angivet i værktøjet, med dine udviklere eller en teknisk supportmedarbejder, skal du bruge **funktionen Aktivér eksport til HTTP-arkiv (HAR)** som den anbefalede fremgangsmåde. 

   > [!div class="mx-imgBorder"]
   > ![Aktivér eksport til HAR.](../media/page-diagnostics-for-spo/pagediag-submithar.png)

Det skal aktiveres, før du klikker på Start, hvilket derefter aktiverer fejlfindingstilstand i din browser. Den genererer en HTTP-arkivfil (HAR), som derefter kan tilgås via fanen "Netværkssporing". Klik på "Eksportér til HAR", så downloader den filen til din computer, og du kan derefter dele den i overensstemmelse hermed. Filen kan åbnes i forskellige fejlfindingsværktøjer, f.eks. F12 Developer Tools og Fiddler.

> [!div class="mx-imgBorder"]
> ![Netværkssporing.](../media/page-diagnostics-for-spo/pagediag-networktracehar.png)

> [!IMPORTANT]
> Disse resultater indeholder URL-adresser, og de kan klassificeres som personidentificerbare oplysninger. Sørg for at følge organisationens retningslinjer, før du distribuerer disse oplysninger.

## <a name="engaging-with-microsoft-support"></a>Engagerende med Microsoft Support

Vi har inkluderet en **funktion på Microsoft-supportniveau** , der kun bør anvendes, når du arbejder direkte på en supportsag. Brug af denne funktion vil ikke give dig nogen fordel, når den bruges uden supportteamengagement, og det kan gøre siden betydeligt langsommere. Der er ingen yderligere oplysninger, når du bruger denne funktion i værktøjet, da de yderligere oplysninger føjes til logføringen af tjenesten.

Der er ingen synlig ændring, bortset fra at du får besked om, at du har aktiveret den, og at sideydeevnen degraderes væsentligt med 2-3 gange langsommere ydeevne, mens den er aktiveret. Det vil kun være relevant for den pågældende side og den aktive session. Derfor bør dette bruges sparsomt og kun, når du aktivt er engageret i support.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Sådan aktiverer du funktionen Microsoft Supportniveau

1. Åbn værktøjet Sidediagnosticering for SharePoint.
2. Tryk på **ALT+Skift-L** på tastaturet. Dette viser afkrydsningsfeltet **Aktivér supportlogføring** .
3. Markér afkrydsningsfeltet, og klik derefter på **Start** for at genindlæse siden og generere detaljeret logføring.

   > [!div class="mx-imgBorder"]
   > ![Supportindstilling er aktiveret.](../media/page-diagnostics-for-spo/pagediag-support.png)
  
    Bemærk CorrelationID (vises øverst i værktøjet) og give den til din supportmedarbejder, så de kan indsamle yderligere oplysninger om diagnosticeringssessionen.

## <a name="related-topics"></a>Relaterede emner

[Juster SharePoint onlineydeevne](tune-sharepoint-online-performance.md)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)

[Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Content Delivery Networks](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)