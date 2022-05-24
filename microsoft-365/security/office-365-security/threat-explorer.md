---
title: Trusselsoversigt og registreringer i realtid
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Brug Stifinder- og realtidsregistreringer på Microsoft 365 Defender-portalen til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0920439345b026879b86ad3b2ce104d3ea8174d1
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649425"
---
# <a name="threat-explorer-and-real-time-detections"></a>Trusselsoversigt og registreringer i realtid

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis din organisation har [Microsoft Defender for Office 365](defender-for-office-365.md), og du har de [nødvendige tilladelser](#required-licenses-and-permissions), har du enten **Stifinder**- eller **Realtidsregistreringer** (tidligere *rapporter i realtid* – [se nyheder](#new-features-in-threat-explorer-and-real-time-detections)!). I Security & Compliance Center skal du gå til **Trusselsstyring** og derefter vælge **Stifinder**_- eller_ **realtidsregistreringer**.

|Med Microsoft Defender for Office 365 Plan 2 kan du se:|Med Microsoft Defender for Office 365 Plan 1 kan du se:|
|---|---|
|![Trusselsudforsker.](../../media/threatmgmt-explorer.png)|![Registreringer i realtid](../../media/threatmgmt-realtimedetections.png)|

Opdagelser i Stifinder eller realtid hjælper dit team med sikkerhedshandlinger med at undersøge og reagere effektivt på trusler. Rapporten ligner følgende billede:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Menupunktet Stifinder på portalen Sikkerhed & overholdelse" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Med denne rapport kan du:

- [Se malware, der er registreret af Microsoft 365 sikkerhedsfunktioner](#see-malware-detected-in-email-by-technology)
- [Vis phishing-URL-adresse, og klik på domsdata](#view-phishing-url-and-click-verdict-data)
- [Start en automatisk undersøgelses- og svarproces fra en visning i Stifinder](#start-automated-investigation-and-response) (kun Defender for Office 365 Plan 2)
- [Undersøg ondsindet mail m.m.](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Forbedringer af Threat Hunting Experience

### <a name="introduction-of-alert-id-for-defender-for-office-365-alerts-within-explorerreal-time-detections"></a>Introduktion af besked-id for Defender for Office 365 beskeder i Stifinder/Registreringer i realtid

Hvis du i dag navigerer fra en besked til Threat Explorer, åbner den en filtreret visning i Stifinder med visningen filtreret efter id for beskedpolitik (politik-id er et entydigt id for en beskedpolitik).
Vi gør denne integration mere relevant ved at introducere besked-id'et (se et eksempel på besked-id nedenfor) i Threat Explorer og registreringer i realtid, så du kan se meddelelser, der er relevante for den specifikke besked, samt en optælling af mails. Du kan også se, om en meddelelse var en del af en besked, og du kan også navigere fra den pågældende meddelelse til den specifikke besked.

Besked-id er tilgængeligt i URL-adressen, når du får vist en individuel besked. et eksempel på en .`https://protection.office.com/viewalerts?id=372c9b5b-a6c3-5847-fa00-08d8abb04ef1`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtrering af besked-id" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Pop op-vinduet Besked-id i detaljer" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days"></a>Udvidelse af dataopbevarings- og søgegrænsen for prøvelejere (og registreringer i realtid) fra 7 til 30 dage

Som en del af denne ændring kan du søge efter og filtrere maildata på tværs af 30 dage (en stigning fra de forrige 7 dage) i Threat Explorer/Realtidsregistreringer for både Defender for Office P1- og P2-prøveversionslejere.
Dette påvirker ikke nogen produktionslejere for både P1- og P2/E5-kunder, som allerede har de 30 dages dataopbevarings- og søgefunktioner.

### <a name="updated-limits-for-export-of-records-for-threat-explorer"></a>Opdaterede grænser for eksport af poster for Threat Explorer

Som en del af denne opdatering øges antallet af rækker for mailposter, der kan eksporteres fra Threat Explorer, fra 9990 til 200.000 poster. Det sæt kolonner, der kan eksporteres i øjeblikket, forbliver det samme, men antallet af rækker øges fra den aktuelle grænse.

### <a name="tags-in-threat-explorer"></a>Tags i Threat Explorer

> [!NOTE]
> Brugertagsfunktionen er *tilgængelig som prøveversion*, er ikke tilgængelig for alle og kan ændres. Du kan få oplysninger om udgivelsesplanen i køreplanen for Microsoft 365.

Brugerkoder identificerer bestemte grupper af brugere i Microsoft Defender for Office 365. Du kan få flere oplysninger om mærker, herunder licenser og konfiguration, under [Brugerkoder](user-tags.md).

I Threat Explorer kan du se oplysninger om brugerkoder i følgende oplevelser.

#### <a name="email-grid-view"></a>Mailgittervisning

Kolonnen **Mærker** i mailgitteret indeholder alle de mærker, der er anvendt på afsender- eller modtagerpostkasser. Som standard vises systemkoder som prioritetskonti først.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Filtrer mærker i mailgittervisning" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrering

Du kan bruge mærker som et filter. Jagt på tværs af prioritetskonti eller specifikke scenarier med brugertags. Du kan også udelade resultater, der har bestemte mærker. Kombiner denne funktionalitet med andre filtre for at begrænse undersøgelsens omfang.

[![Filtrer mærker.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="De mærker, der ikke er filtreret" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>Pop op-vindue med maildetaljer

Hvis du vil have vist de enkelte mærker for afsender og modtager, skal du vælge emnet for at åbne pop op-vinduet med meddelelsesoplysninger. Under fanen **Oversigt** vises afsender- og modtagerkoderne separat, hvis de findes til en mail.
Oplysningerne om individuelle mærker for afsender og modtager udvides også til eksporterede CSV-data, hvor du kan se disse oplysninger i to separate kolonner.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Mærkerne Mailoplysninger" lightbox="../../media/tags-flyout.png":::

Oplysninger om mærker vises også i pop op-vinduet med URL-klik. Hvis du vil have den vist, skal du gå til visningen Phish eller Alle mails og derefter til fanen **URL-adresser** eller **URL-klik** . Vælg et separat pop op-vindue til URL-adresser for at få vist yderligere oplysninger om klik for den pågældende URL-adresse, herunder mærker, der er knyttet til det pågældende klik.

### <a name="updated-timeline-view"></a>Opdateret tidslinjevisning

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="URL-mærkerne" lightbox="../../media/tags-urls.png":::
>
Få mere at vide ved at se [denne video](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Forbedringer af truslen jagt erfaring (kommende)

### <a name="updated-threat-information-for-emails"></a>Opdaterede trusselsoplysninger for mails

Vi har fokuseret på forbedringer af platform og datakvalitet for at øge datanøjagtigheden og ensartetheden af mailposter. Forbedringer omfatter konsolidering af oplysninger om forudlevering og efter levering, f.eks. handlinger, der udføres på en mail som en del af ZAP-processen, til en enkelt post. Yderligere oplysninger som spam-dom, trusler på enhedsniveau (f.eks. hvilken URL-adresse der var skadelig), og seneste leveringsplaceringer er også inkluderet.

Efter disse opdateringer får du vist en enkelt post for hver meddelelse, uanset hvilke forskellige hændelser efter levering der påvirker meddelelsen. Handlinger kan omfatte ZAP, manuel afhjælpning (hvilket betyder administratorhandling), [Dynamisk levering](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) osv.

Ud over at vise malware- og phishingtrusler kan du se den spam-dom, der er knyttet til en mail. I mailen kan du se alle de trusler, der er knyttet til mailen, sammen med de tilsvarende registreringsteknologier. En mail kan have nul, en eller flere trusler. Du kan se de aktuelle trusler i afsnittet **Detaljer** i mail-pop op-vinduet. For flere trusler (f.eks. malware og phishing) viser det **tekniske felt Detection** kortlægning af trusselsregistrering, som er den opdagelsesteknologi, der identificerede truslen.

Sættet af opdagelsesteknologier omfatter nu nye opdagelsesmetoder samt teknologier til registrering af spam. Du kan bruge det samme sæt registreringsteknologier til at filtrere resultaterne på tværs af de forskellige mailvisninger (malware, phish, alle mails).

> [!NOTE]
> Analyse af dom er muligvis ikke nødvendigvis knyttet til enheder. En mail kan f.eks. klassificeres som phish eller spam, men der er ingen URL-adresser, der er stemplet med en phish/spam-dom. Det skyldes, at filtrene også evaluerer indhold og andre oplysninger for en mail, før der tildeles en dom.

#### <a name="threats-in-urls"></a>Trusler i URL-adresser

Du kan nu se den specifikke trussel for en URL-adresse på fanen **Detaljer** i mail. Truslen kan være *malware*, *phish*, *spam* eller *ingen*.)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/URL_Threats.png" alt-text="URL-truslerne" lightbox="../../media/URL_Threats.png":::

### <a name="updated-timeline-view-upcoming"></a>Opdateret tidslinjevisning (kommende)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Email_Timeline.png" alt-text="Den opdaterede tidslinjevisning" lightbox="../../media/Email_Timeline.png":::

Tidslinjevisning identificerer alle leverings- og efterleveringshændelser. Den indeholder oplysninger om den trussel, der er identificeret på det pågældende tidspunkt for en delmængde af disse hændelser. Tidslinjevisning indeholder også oplysninger om eventuelle yderligere handlinger, der udføres (f.eks. ZAP eller manuel afhjælpning) sammen med resultatet af denne handling. Oplysninger om tidslinjevisning omfatter:

- **Kilde:** Kilden til hændelsen. Det kan være administrator/system/bruger.
- **Begivenhed:** Omfatter hændelser på øverste niveau, f.eks. oprindelig levering, manuel afhjælpning, ZAP, indsendelser og dynamisk levering.
- **Handling:** Den specifikke handling, der blev udført enten som en del af ZAP- eller administratorhandlingen (f.eks. blød sletning).
- **Trusler:** Dækker de trusler (malware, phish og spam), der blev identificeret på det pågældende tidspunkt.
- **Resultat/detaljer:** Flere oplysninger om resultatet af handlingen, f.eks. om den blev udført som en del af ZAP/admin-handlingen.

### <a name="original-and-latest-delivery-location"></a>Oprindelig og seneste leveringsplacering

I øjeblikket vises leveringsplaceringen i mailgitteret og mail-pop op-vinduet. Feltet **Leveringsplacering** omdøbes **_til Oprindelig leveringsplacering_*_. Og vi introducerer et andet felt, _*_Seneste leveringsplacering_**.

**Den oprindelige leveringsplacering** giver flere oplysninger om, hvor en mail blev leveret i starten. **Den seneste leveringsplacering** angiver, hvor en mail landede efter systemhandlinger, f.eks. *ZAP* - eller administratorhandlinger, f.eks. *Flyt til slettede elementer*. Den seneste leveringsplacering er beregnet til at fortælle administratorer om meddelelsens sidst kendte placering efter levering eller eventuelle system-/administratorhandlinger. Den indeholder ingen handlinger fra slutbrugere i mailen. Hvis en bruger f.eks. har slettet en meddelelse eller flyttet meddelelsen til arkiv/pst, opdateres meddelelsens placering "levering" ikke. Men hvis en systemhandling opdaterer placeringen (f.eks. ZAP, hvilket medfører, at en mail flyttes til karantæne), vises **den seneste leveringsplacering** som "karantæne".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Delivery_Location.png" alt-text="De opdaterede leveringsplaceringer" lightbox="../../media/Updated_Delivery_Location.png":::

> [!NOTE]
> Der er nogle få tilfælde, hvor **handlingen Leveringsplacering** og **Levering** kan vises som "ukendt":
>
> - Du kan se **Leveringsplacering** som "leveret" og **Leveringsplacering** som "ukendt", hvis meddelelsen blev leveret, men en indbakkeregel flyttede meddelelsen til en standardmappe (f.eks Kladde eller Arkiv) i stedet for til mappen Indbakke eller Uønsket mail.
>
> - **Den seneste leveringsplacering** kan være ukendt, hvis der blev forsøgt en administrator-/systemhandling (f.eks. ZAP), men meddelelsen blev ikke fundet. Handlingen sker typisk, når brugeren har flyttet eller slettet meddelelsen. I sådanne tilfælde skal du bekræfte kolonnen **Result/Details** i tidslinjevisning. Søg efter sætningen "Meddelelsen er flyttet eller slettet af brugeren".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Timeline_Delivery_Location.png" alt-text="Leveringsplaceringerne for tidslinjen" lightbox="../../media/Updated_Timeline_Delivery_Location.png":::

### <a name="additional-actions"></a>Yderligere handlinger

Der blev anvendt *yderligere handlinger* efter levering af mailen. De kan omfatte *ZAP*, *manuel afhjælpning* (handling, der udføres af en Administration f.eks. blød sletning), *Dynamisk levering* og *oparbejdet* (for en mail, der blev registreret med tilbagevirkende kraft som god).

> [!NOTE]
> Som en del af de ventende ændringer forsvinder værdien "Fjernet af ZAP", der aktuelt vises i filteret Leveringshandling. Du kan søge efter alle mails med ZAP-forsøget via **Yderligere handlinger**.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Additional_Actions.png" alt-text="De ekstra handlinger i Stifinder" lightbox="../../media/Additional_Actions.png":::

### <a name="system-overrides"></a>Systemtilsidesættelser

*Systemtilsidesættelser* gør det muligt for dig at gøre undtagelser fra den tilsigtede leveringsplacering for en meddelelse. Du tilsidesætter den leveringsplacering, der leveres af systemet, baseret på de trusler og andre registreringer, der er identificeret af filtreringsstakken. Systemtilsidesættelser kan angives via lejer- eller brugerpolitikken for at levere meddelelsen som foreslået af politikken. Tilsidesættelser kan identificere utilsigtet levering af skadelige meddelelser på grund af konfigurationshuller, f.eks. en alt for bred Pengeskab afsenderpolitik, der er angivet af en bruger. Disse tilsidesættelsesværdier kan være:

- Tilladt af brugerpolitik: En bruger opretter politikker på postkasseniveau for at tillade domæner eller afsendere.

- Blokeret af brugerpolitik: En bruger opretter politikker på mailfeltniveau for at blokere domæner eller afsendere.

- Tilladt af organisationspolitik: Organisationens sikkerhedsteams angiver politikker eller Exchange regler for mailflow (også kendt som transportregler) for at tillade afsendere og domæner for brugere i deres organisation. Det kan være for et sæt brugere eller hele organisationen.

- Blokeret af organisationens politik: Organisationens sikkerhedsteam angiver politikker eller regler for mailflow for at blokere afsendere, domæner, meddelelsessprog eller kilde-IP-adresser for brugere i deres organisation. Dette kan anvendes på et sæt brugere eller hele organisationen.

- Filtypenavn blokeret af organisationspolitik: En organisations sikkerhedsteam blokerer et filtypenavn via politikindstillingerne for antimalware. Disse værdier vises nu i mailoplysninger som en hjælp til undersøgelser. Secops-teams kan også bruge rich-filtering-funktionen til at filtrere på blokerede filtypenavne.

[![Systemtilsidesættelser i Stifinder.](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/System_Overrides_Grid.png" alt-text="Systemet tilsidesætter gitteret i Stifinder" lightbox="../../media/System_Overrides_Grid.png":::

### <a name="improvements-for-the-url-and-clicks-experience"></a>Forbedringer af URL-adressen og klikoplevelsen

Forbedringerne omfatter:

- Vis den fulde url-adresse, der klikkes på (herunder eventuelle forespørgselsparametre, der er en del af URL-adressen) i afsnittet **Klik** i pop op-vinduet for URL-adressen. URL-domænet og stien vises i øjeblikket på titellinjen. Vi udvider disse oplysninger til at vise hele URL-adressen.

- Rettelser på tværs af URL-filtre (*URL-adresse* i forhold til *URL-domæne* i forhold til *URL-domæne og sti*): Opdateringerne påvirker søgningen efter meddelelser, der indeholder en URL-adresse/klik-dom. Vi har aktiveret understøttelse af protokolagnostiske søgninger, så du kan søge efter en URL-adresse uden at bruge `http`. Som standard knyttes URL-søgningen til http, medmindre der udtrykkeligt er angivet en anden værdi. Eksempel:
  - Søg med og uden præfikset `http://` i filterfelterne **URL-adresse**, **URL-domæne og URL-domæne og sti**.  Søgninger bør vise de samme resultater.
  - Søg efter præfikset `https://` i **URL-adressen**. Når der ikke er angivet en værdi, antages præfikset `http://` .
  - `/` ignoreres i starten og slutningen af **URL-stien**, **URL-domænet**, **URL-domænet og stifelterne** . `/` i slutningen af FELTET **URL-adresse** ignoreres.

### <a name="phish-confidence-level"></a>Phish konfidensniveau

Phish-tillidsniveau hjælper med at identificere graden af tillid, som en mail blev kategoriseret som "phish". De to mulige værdier er *High* og *Normal*. I de indledende faser er dette filter kun tilgængeligt i Phish-visningen af Threat Explorer.

[![Phish-konfidensniveau i Stifinder.](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>ZAP URL-signal

ZAP URL-signalet bruges typisk til ZAP Phish-beskedscenarier, hvor en mail blev identificeret som Phish og fjernet efter levering. Dette signal forbinder beskeden med de tilsvarende resultater i Stifinder. Det er en af IIC'erne for beskeden.

For at forbedre jagtprocessen har vi opdateret Threat Explorer og registreringer i realtid for at gøre jagtoplevelsen mere ensartet. Ændringerne er beskrevet her:

- [Forbedringer af tidszone](#timezone-improvements)
- [Opdater i opdateringsprocessen](#update-in-the-refresh-process)
- [Diagramudledning, der skal føjes til filtre](#chart-drilldown-to-add-to-filters)
- [I opdateringer af produktoplysninger](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Filtrer efter brugerkoder

Du kan nu sortere og filtrere efter system- eller brugerdefinerede brugertags for hurtigt at forstå omfanget af trusler. Du kan få mere at vide under [Brugerkoder](user-tags.md).

> [!IMPORTANT]
> Filtrering og sortering efter brugerkoder er i øjeblikket en offentlig prøveversion. Denne funktionalitet kan blive ændret væsentligt, før den udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der gives om det.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-tags.png" alt-text="Kolonnen Mærker i Stifinder" lightbox="../../media/threat-explorer-tags.png":::

### <a name="timezone-improvements"></a>Forbedringer af tidszone

Du kan se tidszonen for mailposterne på portalen samt for eksporterede data. Den vil være synlig på tværs af oplevelser som mailgitter, pop op-vinduet Detaljer, Mailtidslinje og Lignende mails, så tidszonen for resultatsættet er klar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/TimezoneImprovements.png" alt-text="Tidszonen Vis i Stifinder" lightbox="../../media/TimezoneImprovements.png":::

### <a name="update-in-the-refresh-process"></a>Opdater i opdateringsprocessen

Nogle brugere har kommenteret på forvirring med automatisk opdatering (f.eks. så snart du ændrer datoen, siden opdateres) og manuel opdatering (for andre filtre). På samme måde fører fjernelse af filtre til automatisk opdatering. Ændring af filtre under redigering af forespørgslen kan medføre uoverensstemmende søgeoplevelser. For at løse disse problemer flytter vi til en mekanisme til manuel filtrering.

Ud fra en erfaringsmæssigt synspunkt kan brugeren anvende og fjerne det forskellige filterområde (fra filtersættet og datoen) og vælge opdateringsknappen for at filtrere resultaterne, når de har defineret forespørgslen. Opdateringsknappen fremhæves nu også på skærmen. Vi har også opdateret de relaterede værktøjstip og dokumentationen i produktet.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ManualRefresh.png" alt-text="Knappen Opdater for at filtrere resultater" lightbox="../../media/ManualRefresh.png":::

### <a name="chart-drilldown-to-add-to-filters"></a>Diagramudledning, der skal føjes til filtre

Du kan nu oprette et diagram over forklaringsværdier for at tilføje dem som filtre. Vælg knappen **Opdater** for at filtrere resultaterne.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ChartDrilldown.png" alt-text="Detailudledning via diagrammer, der skal filtreres" lightbox="../../media/ChartDrilldown.png":::

### <a name="in-product-information-updates"></a>Opdateringer af oplysninger i produktet

Der er nu flere oplysninger tilgængelige i produktet, f.eks. det samlede antal søgeresultater i gitteret (se nedenfor). Vi har forbedret mærkater, fejlmeddelelser og værktøjstip for at give flere oplysninger om filtre, søgeoplevelse og resultatsæt.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ProductInfo.png" alt-text="De oplysninger i produktet, der skal vises" lightbox="../../media/ProductInfo.png":::

## <a name="extended-capabilities-in-threat-explorer"></a>Udvidede funktioner i Threat Explorer

### <a name="top-targeted-users"></a>Mest målrettede brugere

I dag fremviser vi listen over de mest målrettede brugere i malwarevisningen for mails i afsnittet **Mest populære malwarefamilier** . Vi udvider også denne visning i visningerne Phish og Alle mails. Du kan se de øverste fem målrettede brugere sammen med antallet af forsøg for hver bruger for den tilsvarende visning. For Phish-visning kan du f.eks. se antallet af Phish-forsøg.

Du kan eksportere listen over målrettede brugere op til en grænse på 3.000 sammen med antallet af forsøg på offlineanalyse for hver mailvisning. Hvis du vælger antallet af forsøg (f.eks. 13 forsøg på billedet nedenfor), åbnes der desuden en filtreret visning i Threat Explorer, så du kan se flere oplysninger på tværs af mails og trusler for den pågældende bruger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="De mest målrettede brugere" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Exchange transportregler

Som en del af databerigelse kan du se alle de forskellige transportregler for Exchange, der blev anvendt på en meddelelse. Disse oplysninger vil være tilgængelige i gittervisningen Mail. Hvis du vil have den vist, skal du vælge **Kolonneindstillinger** i gitteret og derefter **Tilføje Exchange Transportregel** fra kolonneindstillingerne. Den vil også være synlig i pop op-vinduet **Detaljer** i mailen.

Du kan se både GUID og navnet på de transportregler, der er anvendt på meddelelsen. Du kan søge efter meddelelserne ved hjælp af navnet på transportreglen. Dette er en "Indeholder"-søgning, hvilket betyder, at du også kan foretage delvise søgninger.

> [!IMPORTANT]
> Tilgængeligheden af ETR-søgning og -navn afhænger af den specifikke rolle, der er tildelt til dig. Du skal have en af følgende roller/tilladelser for at få vist ETR-navnene og søgningen. Hvis du ikke har fået tildelt nogen af disse roller, kan du ikke se navnene på transportreglerne eller søge efter meddelelser ved hjælp af ETR-navne. Du kan dog se ETR-mærkaten og GUID-oplysningerne i Mailoplysninger. Andre oplevelser med postvisning i mailgitre, pop op-vinduet Mail, Filtre og Eksport påvirkes ikke.
>
> - Kun EXO – forebyggelse af datatab: Alle
> - Kun EXO – O365SupportViewConfig: Alle
> - Microsoft Azure Active Directory eller EXO – Sikkerheds Administration: Alle
> - AAD eller EXO – Sikkerhedslæser: Alle
> - Kun EXO – Transportregler: Alle
> - Kun EXO – View-Only konfiguration: Alle
>
> I mailgitteret, pop op-vinduet Detaljer og Eksporteret CSV præsenteres ETR'er med et navn/GUID som vist nedenfor.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Reglerne for Exchange transport" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Indgående forbindelser

Forbindelser er en samling instruktioner, der tilpasser, hvordan dine mailflows til og fra din Microsoft 365 eller Office 365 organisation. De giver dig mulighed for at anvende eventuelle sikkerhedsbegrænsninger eller kontrolelementer. I Threat Explorer kan du nu få vist de connectors, der er relateret til en mail, og søge efter mails ved hjælp af connectornavne.

Søgningen efter connectorer er "indeholder" i naturen, hvilket betyder, at delvise nøgleordssøgninger også skal fungere. I visningen Hovedgitter, pop op-vinduet Detaljer og Den Eksporterede CSV vises connectorerne i formatet Navn/GUID som vist her:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Oplysninger om connectoren" lightbox="../../media/Connector_Details.png":::

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nye funktioner i Threat Explorer og registreringer i realtid

- [Vis phishing-mails, der sendes til repræsenterede brugere og domæner](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [Vis mailheader, og hent brødteksten i mailen](#preview-email-header-and-download-email-body)
- [Mailtidslinje](#email-timeline)
- [Eksportér klikdata for URL-adresse](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Vis phishing-mails, der sendes til repræsenterede brugere og domæner

Hvis du vil identificere phishingforsøg mod brugere og domæner, der repræsenteres af brugere, skal du føje dem til listen over *brugere for at beskytte* dem. For domæner skal administratorer enten aktivere *organisationsdomæner* eller føje et domænenavn til *Domæner for at beskytte*. De domæner, der skal beskyttes, findes på *siden Politik til bekæmpelse af phishing* i afsnittet *Repræsentation* .

Hvis du vil gennemse phish-meddelelser og søge efter repræsenterede brugere eller domæner, skal du bruge [> Visningen Phish](threat-explorer-views.md) i Stifinder.

I dette eksempel bruges Threat Explorer.

1. I [Security & Compliance Center](https://protection.office.com) (https://protection.office.com)vælg Threat Management > Explorer (eller registreringer i realtid).

2. Vælg Mail i menuen Vis > Phish.

   Her kan du vælge **repræsenteret domæne** eller **repræsenteret bruger**.

3. **VÆLG ENTEN** **Repræsenteret domæne**, og skriv derefter et beskyttet domæne i tekstfeltet.

   Søg f.eks. efter beskyttede domænenavne, f.eks. *contoso*, *contoso.com* eller *contoso.com.au*.

4. Vælg Emne for en meddelelse under fanen Mail > fanen Detaljer for at få vist yderligere repræsentationsoplysninger, f.eks. repræsenteret domæne/registreret placering.

    **ELLER**

    Vælg **Repræsenteret bruger,** og skriv en beskyttet brugers mailadresse i tekstfeltet.

    > [!TIP]
    > **Du opnår det bedste resultat** ved at bruge *komplette mailadresser* til at søge efter beskyttede brugere. Du finder hurtigere og mere effektivt din beskyttede bruger, hvis du søger efter *firstname.lastname@contoso.com*, f.eks. når du undersøger brugerrepræsentation. Når du søger efter et beskyttet domæne, tager søgningen roddomænet (f.eks. contoso.com) og domænenavnet (*contoso*). Hvis du søger efter *contoso.com* for roddomænet, returneres både repræsentationer af *contoso.com* og domænenavnet *contoso*.

5. Vælg **Emne** for en meddelelse under **fanen** >  **MailDetails** for at få vist yderligere repræsentationsoplysninger om brugeren eller domænet og den *registrerede placering*.

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Detaljeruden for Threat Explorer for en beskyttet bruger, der viser registreringsplaceringen og den trussel, der blev registreret (her skal du repræsentere en bruger)" lightbox="../../media/threat-ex-views-impersonated-user-image.png":::

> [!NOTE]
> Hvis du i trin 3 eller 5 vælger **Registreringsteknologi** og vælger Henholdsvis **Repræsentationsdomæne** eller **Repræsentationsbruger**, vises oplysningerne **under fanen** >  **MailDetails** om brugeren eller domænet og placeringen *Registreret* kun på de meddelelser, der er relateret til den bruger eller det domæne, der er angivet på siden *Anti-Phishing-politik*.

### <a name="preview-email-header-and-download-email-body"></a>Vis mailheader, og hent brødteksten i mailen

Du kan nu få forhåndsvist en mailheader og downloade mailbrødteksten i Threat Explorer. Administratorer kan analysere downloadede brevhoveder/mails for trusler. Da download af mails kan risikere eksponering af oplysninger, styres denne proces af rollebaseret adgangskontrol. Der kræves en ny rolle, *prøveversion*, for at give mulighed for at downloade mails i visningen med alle mails. Visning af mailheaderen kræver dog ikke yderligere rolle (ud over det, der kræves for at få vist meddelelser i Threat Explorer). Sådan opretter du en ny rollegruppe med rollen Eksempel:

1. Vælg en indbygget rollegruppe, der kun har rollen Prøveversion, f.eks. Dataforsker eller eDiscovery Manager.
2. Vælg **Kopiér rollegruppe**.
3. Vælg et navn og en beskrivelse til din nye rollegruppe, og vælg **Næste**.
4. Rediger rollerne ved at tilføje og fjerne roller efter behov, men lade rollen Eksempel være.
5. Tilføj medlemmer, og vælg derefter **Opret rollegruppe**.

Stifinder- og realtidsregistreringer får også nye felter, der giver et mere komplet billede af, hvor dine mails lander. Disse ændringer gør det nemmere at jagte sikkerhedsops. Men det vigtigste resultat er, at du hurtigt kan se placeringen af problemmails.

Hvordan sker det? Leveringsstatus er nu opdelt i to kolonner:

- **Leveringshandling** – Status for mailen.
- **Leveringsplacering** – Hvor mailen blev distribueret.

*Leveringshandling* er den handling, der udføres på en mail på grund af eksisterende politikker eller registreringer. Her er de mulige handlinger for en mail:

|Leveret|Junked|Blokeret|Erstattet|
|---|---|---|---|
|Mailen blev leveret til en brugers indbakke eller mappe, og brugeren kan få adgang til den.|Der blev sendt en mail til brugerens mappe med uønsket eller slettet post, og brugeren kan få adgang til den.|Mails, der er sat i karantæne, som mislykkedes eller blev droppet. Disse mails er utilgængelige for brugeren.|Mailen havde skadelige vedhæftede filer erstattet af .txt filer, der angiver, at den vedhæftede fil var skadelig.|

Her er, hvad brugeren kan og ikke kan se:

|Tilgængelig for slutbrugere|Utilgængelig for slutbrugere|
|---|---|
|Leveret|Blokeret|
|Junked|Erstattet|

**Leveringsplaceringen** viser resultaterne af politikker og registreringer, der kører efter levering. Den er knyttet til **_handlingen Levering_**. Dette er de mulige værdier:

- *Indbakke eller mappe*: Mailen er i indbakken eller en mappe (i henhold til dine mailregler).
- *I det lokale miljø eller eksternt*: Postkassen findes ikke i skyen, men er i det lokale miljø.
- *Mappen Uønsket* mail: Mailen er i en brugers mappe med uønsket mail.
- *Mappen Slettet post*: Mailen i en brugers mappe Slettet post.
- *Karantæne*: Mailen er i karantæne og ikke i en brugers postkasse.
- *Mislykket*: Mailen kunne ikke få forbindelse til postkassen.
- *Mistet*: Mailen gik tabt et sted i mailflowet.

### <a name="email-timeline"></a>Mailtidslinje

**Mailtidslinjen er en ny Explorer-funktion**, der forbedrer jagtoplevelsen for administratorer. Det reducerer den tid, der bruges på at kontrollere forskellige placeringer, for at forsøge at forstå hændelsen. Når der sker flere hændelser på eller tæt på samme tid, som der modtages en mail, vises disse hændelser i en tidslinjevisning. Nogle hændelser, der sker med din mail efter levering, registreres i kolonnen **Speciel handling** . Administratorer kan kombinere oplysninger fra tidslinjen med den særlige handling, der udføres på postleveringen, for at få indsigt i, hvordan deres politikker fungerer, hvor mailen endelig blev distribueret, og i nogle tilfælde, hvad den endelige vurdering var.

Du kan få flere oplysninger under [Undersøg og afhjælp skadelige mails, der blev leveret i Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>Eksportér klikdata for URL-adresse

Du kan nu eksportere rapporter for klik på URL-adresser for at Microsoft Excel for at få vist deres **netværksmeddelelses-id** og **klikke på dom**, hvilket hjælper med at forklare, hvor url-adressens kliktrafik stammer fra. Sådan fungerer det: I Threat Management på den Office 365 hurtig start-linje skal du følge denne kæde:

**Explorer** \> **Vis phish** \> **Klik** \> **Øverste URL-adresser** eller **URL-adresse De øverste klik** \> vælger en post for at åbne URL-pop op-vinduet.

Når du vælger en URL-adresse på listen, får du vist **en ny** eksportknap på fly-out-panelet. Brug denne knap til at flytte data til et Excel regneark for at lette rapporteringen.

Følg denne sti for at komme til den samme placering i rapporten Registreringer i realtid:

**Explorer** \> **Registreringer i** \> realtid **Vis phish** \> **Webadresser** \> **De mest populære URL-adresser** eller **de mest populære klik** \> Vælg en post for at åbne URL-pop op-vinduet \> , og gå til fanen **Klik** .

> [!TIP]
> Netværksmeddelelses-id'et knytter klik tilbage til bestemte mails, når du søger på id'et via Stifinder eller tilknyttede tredjepartsværktøjer. Disse søgninger identificerer den mail, der er knyttet til et klikresultat. At have det korrelerede netværksmeddelelses-id giver hurtigere og mere effektive analyser.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tp_ExportClickResultAndNetworkID.png" alt-text="Fanen Klik i Stifinder" lightbox="../../media/tp_ExportClickResultAndNetworkID.png":::

## <a name="see-malware-detected-in-email-by-technology"></a>Se malware, der er registreret i en mail efter teknologi

Forestil dig, at du vil se malware, der er registreret i en mail, sorteret efter Microsoft 365 teknologi. Det gør du ved at bruge [visningen Mail > Malware](threat-explorer-views.md#email--malware) i Stifinder (eller registreringer i realtid).

1. I Security & Compliance Center (<https://protection.office.com>) skal du vælge **Threat management** \> **Explorer** (eller **registreringer i realtid**). (I dette eksempel bruges Stifinder).

2. Vælg **Mailmalware** \> i menuen **Vis**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailMalwareMenu.png" alt-text="Menuen Vis for Stifinder" lightbox="../../media/ExplorerViewEmailMalwareMenu.png":::

3. Klik på **Afsender**, og vælg derefter **Basic** \> **Detection-teknologi**.

   Dine registreringsteknologier er nu tilgængelige som filtre for rapporten.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTech.png" alt-text="Teknologierne til registrering af malware" lightbox="../../media/ExplorerEmailMalwareDetectionTech.png":::

4. Vælg en indstilling. Vælg derefter knappen **Opdater** for at anvende filteret.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTechATP.png" alt-text="Den valgte registreringsteknologi" lightbox="../../media/ExplorerEmailMalwareDetectionTechATP.png":::

Rapporten opdateres for at vise de resultater, som malware har registreret i en mail, ved hjælp af den valgte teknologiindstilling. Herfra kan du foretage yderligere analyser.

## <a name="view-phishing-url-and-click-verdict-data"></a>Vis phishing-URL-adresse, og klik på domsdata

Lad os antage, at du vil se phishingforsøg via URL-adresser i en mail, herunder en liste over URL-adresser, der er tilladt, blokeret og tilsidesat. Hvis du vil identificere URL-adresser, der blev klikket på, skal [Pengeskab Links](safe-links.md) være konfigureret. Sørg for, at du konfigurerer [politikker for Pengeskab links](set-up-safe-links-policies.md) til beskyttelsestid og logføring af klik-dommene fra Pengeskab Links.

Hvis du vil gennemse phish-URL-adresser i meddelelser og klikke på URL-adresser i phish-meddelelser, skal du bruge visningen [**EmailPhish** > ](threat-explorer-views.md#email--phish) i Stifinder eller registreringer i realtid.

1. I Security & Compliance Center (<https://protection.office.com>) skal du vælge **Threat management** \> **Explorer** (eller **registreringer i realtid**). (I dette eksempel bruges Stifinder).

2. Vælg **Mail-phish** \> i menuen **Vis**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menuen Vis for Explorer i phishing-kontekst" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Klik på **Afsender**, og vælg derefter **URL-adresser** \> **Klik på Dom**.

4. Vælg en eller flere indstillinger, f.eks **. Blokeret** og **Bloker tilsidesat**, og vælg derefter knappen **Opdater** på samme linje som indstillingerne for at anvende filteret. (Opdater ikke browservinduet).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png" alt-text="URL-adresserne og klik på dommene" lightbox="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png":::

   Rapporten opdateres for at vise to forskellige URL-tabeller under fanen URL-adresse under rapporten:

   - **De mest populære URL-adresser** er URL-adresserne i de meddelelser, du filtrerede ned til, og antallet af handlinger til levering af mails for hver URL-adresse. I mailvisningen Phish indeholder denne liste typisk legitime URL-adresser. Hackere inkluderer en blanding af gode og dårlige URL-adresser i deres meddelelser for at forsøge at få dem leveret, men de får de skadelige links til at se mere interessante ud. Tabellen med URL-adresser sorteres efter det samlede antal mails, men denne kolonne er skjult for at forenkle visningen.

   - **De mest populære klik** er de Pengeskab linksombrudte URL-adresser, der blev klikket på, sorteret efter det samlede antal klik. Denne kolonne vises heller ikke for at forenkle visningen. Det samlede antal pr. kolonne angiver antallet af Pengeskab links, der klikker på dom for hver url-adresse, der klikkes på. I mailvisningen Phish er disse normalt mistænkelige eller skadelige URL-adresser. Men visningen kan indeholde URL-adresser, der ikke er trusler, men som findes i phish-meddelelser. URL-klik på links, der ikke er føjet til, vises ikke her.

   De to tabeller med URL-adresser viser de mest populære URL-adresser i phishing-mails efter leveringshandling og placering. Tabellerne viser klik på URL-adresser, der er blokeret eller besøgt trods en advarsel, så du kan se, hvilke potentielle forkerte links der blev præsenteret for brugerne, og at brugeren har klikket på dem. Herfra kan du foretage yderligere analyser. Under diagrammet kan du f.eks. se de øverste URL-adresser i mails, der er blokeret i organisationens miljø.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="De URL-adresser til Stifinder, der blev blokeret" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Vælg en URL-adresse for at få vist mere detaljerede oplysninger.

   > [!NOTE]
   > I dialogboksen URL-adresse er filtreringen af mails fjernet for at få vist den fulde visning af URL-adressens eksponering i dit miljø. Dette giver dig mulighed for at filtrere efter mails, du er bekymret for i Stifinder, finde bestemte URL-adresser, der er potentielle trusler, og derefter udvide din forståelse af eksponeringen af URL-adresser i dit miljø (via dialogboksen MED URL-oplysninger) uden at skulle føje URL-filtre til selve Stifinder-visningen.

### <a name="interpretation-of-click-verdicts"></a>Fortolkning af click-dommene

I pop op-vinduet Mail eller URL-adresse, Top clicks samt i vores filtreringsoplevelser kan du se forskellige click-domsværdier:

- **Ingen:** Dommen for URL-adressen kunne ikke registreres. Brugeren har muligvis klikket via URL-adressen.
- **Tilladt:** Brugeren fik tilladelse til at navigere til URL-adressen.
- **Blokeret:** Brugeren blev blokeret fra at navigere til URL-adressen.
- **Afventer dom:** Brugeren blev præsenteret for den side, der afventer detonation.
- **Blokeret tilsidesat:** Brugeren blev blokeret fra at navigere direkte til URL-adressen. Men brugeren tilsidesætter blokken for at navigere til URL-adressen.
- **Afventer dom omgået:** Brugeren blev præsenteret for detonationssiden. Men brugeren tilsidesætter meddelelsen for at få adgang til URL-adressen.
- **Fejl:** Brugeren blev præsenteret for fejlsiden, eller der opstod en fejl under hentning af dommen.
- **Fiasko:** Der opstod en ukendt undtagelse under hentning af dommen. Brugeren har muligvis klikket via URL-adressen.

## <a name="review-email-messages-reported-by-users"></a>Gennemse mails, der er rapporteret af brugere

Lad os antage, at du vil have vist mails, som brugerne i din organisation har rapporteret som *uønsket*, *ikke uønsket* eller *phishing* via [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md). Hvis du vil se dem, skal du bruge visningen [**EmailSubmissions** > ](threat-explorer-views.md#email--submissions) i Stifinder (eller registreringer i realtid).

1. I Security & Compliance Center (<https://protection.office.com>) skal du vælge **Threat management** \> **Explorer** (eller **registreringer i realtid**). (I dette eksempel bruges Stifinder).

2. Vælg **Mailindsendelser** \> i menuen **Vis**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/explorer-view-menu-email-user-reported.png" alt-text="Menuen Vis for Stifinder for mails" lightbox="../../media/explorer-view-menu-email-user-reported.png":::

3. Klik på **Afsender**, og vælg derefter **Grundlæggende** \> **rapporttype**.

4. Vælg en indstilling, f.eks **. Phish**, og vælg derefter knappen **Opdater** .

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/EmailUserReportedReportType.png" alt-text="Den brugerrapporterede phish" lightbox="../../media/EmailUserReportedReportType.png":::

Rapporten opdateres for at vise data om mails, som personer i din organisation har rapporteret som et phishingforsøg. Du kan bruge disse oplysninger til at foretage yderligere analyser og om nødvendigt justere dine [anti-phishing-politikker i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Start automatiseret undersøgelse og svar

> [!NOTE]
> Automatiserede undersøgelses- og svarfunktioner er tilgængelige i *Microsoft Defender for Office 365 Plan 2* og *Office 365 E5*.

[Automatiseret undersøgelse og svar](automated-investigation-response-office.md) kan spare tid og kræfter på at undersøge og mitigere cyberangreb på dit sikkerhedsteam. Ud over at konfigurere beskeder, der kan udløse en sikkerhedslegebog, kan du starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder. Du kan finde flere oplysninger under [Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Stifinder](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Flere måder at bruge Stifinder- og realtidsregistreringer på

Ud over de scenarier, der er beskrevet i denne artikel, har du mange flere tilgængelige rapporteringsindstillinger i Stifinder (eller registreringer i realtid). Se følgende artikler:

- [Find og undersøg ondsindet mail, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Vis skadelige filer, der er registreret i SharePoint Online, OneDrive og Microsoft Teams](./mdo-for-spo-odb-and-teams.md)
- [Få et overblik over visningerne i Threat Explorer (og registreringer i realtid)](threat-explorer-views.md)
- [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender for Office 365](defender-for-office-365.md) for at bruge Stifinder- eller realtidsregistreringer.

- Explorer er inkluderet i Defender for Office 365 Plan 2.
- Rapporten med registreringer i realtid er inkluderet i Defender for Office 365 Plan 1.
- Planlæg at tildele licenser til alle brugere, der skal beskyttes af Defender for Office 365. Explorer- og realtidsregistreringer viser registreringsdata for brugere med licens.

Hvis du vil have vist og bruge Stifinder- eller realtidsregistreringer, skal du have de relevante tilladelser, f.eks. dem, der er tildelt en sikkerhedsadministrator eller sikkerhedslæser.

- For Security & Compliance Center skal du have en af følgende roller tildelt:

  - Organisationsadministration
  - Sikkerhedsadministrator (dette kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser

- For Exchange Online skal du have en af følgende roller tildelt enten i Exchange Administration (EAC) eller [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell):

  - Organisationsadministration
  - View-Only organisationsstyring
  - View-Only modtagere
  - Overholdelsesstyring

Du kan få mere at vide om roller og tilladelser i følgende ressourcer:

- [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md)
- [Funktionstilladelser i Exchange Online](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Forskelle mellem trusselsoversigt og registreringer i realtid

- Rapporten *med registreringer i realtid* er tilgængelig i Defender for Office 365 Plan 1. *Threat Explorer* er tilgængelig i Defender for Office 365 Plan 2.
- Rapporten Registreringer i realtid giver dig mulighed for at få vist registreringer i realtid. Threat Explorer gør det også, men det indeholder også yderligere oplysninger om et givent angreb.
- En *alle-mailvisning* er tilgængelig i Threat Explorer, men ikke i rapporten registreringer i realtid.
- Flere filtreringsfunktioner og tilgængelige handlinger er inkluderet i Threat Explorer. Du kan få flere oplysninger [under Microsoft Defender for Office 365 Servicebeskrivelse: Funktionstilgængelighed på tværs af Defender for Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="other-articles"></a>Andre artikler

[Undersøg mails med mailenhedssiden](mdo-email-entity-page.md)
