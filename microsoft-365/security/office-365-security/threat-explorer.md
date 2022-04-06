---
title: Registreringer af Trusselsstifinder og i realtid
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
description: Brug Explorer- og realtidsregistreringer i Microsoft 365 Defender til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 29a00c20333c27fcd8138063f31316241b784572
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467021"
---
# <a name="threat-explorer-and-real-time-detections"></a>Registreringer af Trusselsstifinder og i realtid

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis din organisation har [Microsoft Defender for Office 365](defender-for-office-365.md), og du har de nødvendige [tilladelser, har](#required-licenses-and-permissions) du enten **Explorer****- eller Realtidsregistreringer** (tidligere rapporter i *realtid – se* [Nyheder! ).](#new-features-in-threat-explorer-and-real-time-detections) I Security & Compliance Center skal du gå til **Trusselsadministration** og derefter vælge **Stifinder**  **eller Registreringer i realtid**.

|Med Microsoft Defender for Office 365 Plan 2 kan du se:|Med Microsoft Defender for Office 365 plan 1 kan du se:|
|---|---|
|![Trusselsstifinder.](../../media/threatmgmt-explorer.png)|![Registreringer i realtid](../../media/threatmgmt-realtimedetections.png)|

Explorer- eller registreringer i realtid hjælper dit sikkerhedsteam med at undersøge og reagere effektivt på trusler. Rapporten ligner følgende billede:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Menupunktet Stifinder i portalen til & overholdelse af regler og standarder" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Med denne rapport kan du:

- [Se malware, der registreres Microsoft 365 af sikkerhedsfunktioner](#see-malware-detected-in-email-by-technology)
- [Få vist phishing-URL-adresse, og klik på vurderingsdata](#view-phishing-url-and-click-verdict-data)
- [Starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder](#start-automated-investigation-and-response) (Defender for Office 365 Plan 2)
- [Undersøg ondsindede mails og meget mere](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Forbedringer af Threat Hunting Experience


### <a name="introduction-of-alert-id-for-defender-for-office-365-alerts-within-explorerreal-time-detections"></a>Introduktion til besked-id til Defender for Office 365 i Explorer/registreringer i realtid

Hvis du i dag navigerer fra en besked til Threat Explorer, åbnes en filtreret visning i Stifinder, hvor visningen filtreres efter politik-id'et Besked (politik-id er et entydig identifier for en beskedpolitik).
Vi gør denne integration mere relevant ved at introducere besked-id'et (se et eksempel med besked-id nedenfor) i Threat Explorer og registreringer i realtid, så du kan se meddelelser, der er relevante for den bestemte besked, samt en optælling af mails. Du kan også se, om en meddelelse var en del af en besked, samt navigere fra den pågældende meddelelse til den specifikke besked.

Besked-id er tilgængeligt i URL-adressen, når du får vist en enkelt besked. et eksempel, der er `https://protection.office.com/viewalerts?id=372c9b5b-a6c3-5847-fa00-08d8abb04ef1`.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtrering af besked-id" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Pop op-id'et med oplysninger" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days"></a>Udvidelse af stifinderen (og registreringer i realtid) af dataopbevaring og søgegrænse for prøvelejere fra 7 til 30 dage

Som en del af denne ændring vil du kunne søge efter og filtrere maildata på tværs af 30 dage (en stigning fra de foregående 7 dage) i Registreringer af Threat Explorer/realtid for både Defender til Office P1- og P2-prøvelejere.
Dette påvirker ikke produktionslejere for både P1- og P2/E5-kunder, som allerede har de 30 dages dataopbevarings- og søgefunktioner.

### <a name="updated-limits-for-export-of-records-for-threat-explorer"></a>Opdaterede grænser for eksport af poster til Threat Explorer

Som en del af denne opdatering er antallet af rækker for mailposter, der kan eksporteres fra Threat Explorer, øget fra 9990 til 200.000 poster. Det sæt kolonner, der kan eksporteres, forbliver de samme, men antallet af rækker øges fra den aktuelle grænse.

### <a name="tags-in-threat-explorer"></a>Mærker i Threat Explorer

> [!NOTE]
> Funktionen for brugermærker er i *forhåndsvisning*, er ikke tilgængelig for alle og kan ændres uden nogen ændringer. Du kan finde oplysninger om udgivelsesplanen i oversigten Microsoft 365 udgivelse.

Brugermærker identificerer bestemte grupper af brugere i Microsoft Defender for Office 365. Du kan finde flere oplysninger om mærker, herunder licenser og konfiguration, under [Brugermærker](user-tags.md).

I Threat Explorer kan du se oplysninger om brugermærker i følgende oplevelser.

#### <a name="email-grid-view"></a>Gittervisning af mail

Kolonnen **Mærker** i mailgitteret indeholder alle de mærker, der er blevet anvendt på afsenderens eller modtagerens postkasser. Systemmærker som prioritetskonti vises som standard først.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Filtermærkerne i mailgittervisning" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrering

Du kan bruge mærker som et filter. Gennemse lige på tværs af prioritetskonti eller bestemte scenarier med brugermærker. Du kan også udelade resultater, der har bestemte mærker. Kombiner denne funktionalitet med andre filtre for at begrænse omfanget af undersøgelsen.

[![Filtermærker.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="De mærker, der ikke er filtreret" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>Pop op-pop op-pop-op-besked med maildetaljer

Hvis du vil have vist de enkelte mærker for afsender og modtager, skal du vælge emnet for at åbne pop op-meddelelsens detaljer. På fanen **Oversigt** vises afsender- og modtagermærkerne separat, hvis de er til stede for en mail.
Oplysningerne om individuelle mærker for afsender og modtager omfatter også eksporterede CSV-data, hvor du kan se disse oplysninger i to separate kolonner.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Mærkerne Maildetaljer" lightbox="../../media/tags-flyout.png":::

Oplysninger om mærker vises også i pop op-pop-op-menuen med URL-klik. Du kan få den vist ved at gå til visningen Phish eller Alle mails og derefter til **fanen URL-adresser** **eller URL-klik** . Vælg pop op-menuen med en individuel URL-adresse for at få vist flere oplysninger om klik for den pågældende URL-adresse, herunder mærker, der er knyttet til det pågældende klik.

### <a name="updated-timeline-view"></a>Opdateret tidslinjevisning

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="URL-koderne" lightbox="../../media/tags-urls.png":::
>
Få mere at vide ved at [se denne video](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Forbedringer af oplevelsen med trusselssøgning (kommende)

### <a name="updated-threat-information-for-emails"></a>Opdaterede oplysninger om trusler til mails

Vi har fokuseret på forbedringer af platform og datakvalitet for at øge datanøjagtigheden og ensartetheden for mailposter. Forbedringerne omfatter konsolidering af oplysninger før levering og efter levering, f.eks. handlinger, der udføres på en mail som en del af ZAP-processen, i en enkelt post. Yderligere oplysninger som f.eks. vurdering af spam, trusler på enhedsniveau (f.eks. hvilken URL-adresse var skadelig), og de seneste leveringsplaceringer er også inkluderet.

Efter disse opdateringer får du vist en enkelt post for hver meddelelse, uanset de forskellige hændelser efter levering, der påvirker meddelelsen. Handlinger kan omfatte ZAP, manuel afhjælpning (hvilket betyder administratorhandling), dynamisk levering osv.

Ud over at vise malware og phishingtrusler, ser du også den spam konklusion, der er knyttet til en mail. I mailen kan du se alle de trusler, der er knyttet til mailen, sammen med de tilsvarende registreringsteknologier. En mail kan have nul, én eller flere trusler. Du kan se de aktuelle trusler i sektionen **Detaljer** i pop op-mail-pop op-mailen. For flere trusler (f.eks. malware og phishing)  viser registreringsteknikfeltet tilknytningen af trusselsregistrering, som er den registreringsteknologi, der identificerede truslen.

Sættet af registreringsteknologier omfatter nu nye registreringsmetoder samt teknologier til registrering af uønsket post. Du kan bruge det samme sæt registreringsteknologier til at filtrere resultaterne på tværs af de forskellige mailvisninger (Malware, Phish, Alle mails).

> [!NOTE]
> Vurderingsanalyse er muligvis ikke nødvendigvis bundet til enheder. Som et eksempel kan en mail være klassificeret som phish eller spam, men der er ingen URL-adresser, der er stemplet med en phish/spam-konklusion. Det skyldes, at filtrene også evaluerer indhold og andre oplysninger for en mail, før der tildeles en konklusion.

#### <a name="threats-in-urls"></a>Trusler i URL-adresser

Du kan nu se den specifikke trussel for en URL-adresse på fanen Detaljer i **pop op-mail** . Truslen kan være *malware*, *phish*, *spam* eller *ingen*).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/URL_Threats.png" alt-text="URL-truslerne" lightbox="../../media/URL_Threats.png":::

### <a name="updated-timeline-view-upcoming"></a>Opdateret tidslinjevisning (kommende)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Email_Timeline.png" alt-text="Den opdaterede tidslinjevisning" lightbox="../../media/Email_Timeline.png":::

Tidslinjevisning identificerer alle leverings- og efterleveringshændelser. Den indeholder oplysninger om den trussel, der på det pågældende tidspunkt blev identificeret for en delmængde af disse hændelser. Tidslinjevisning indeholder også oplysninger om eventuelle yderligere handlinger, der er foretaget (f.eks. ZAP eller manuel afhjælpning) sammen med resultatet af den pågældende handling. Oplysninger om tidslinjevisning omfatter:

- **Kilde:** Kilden til hændelsen. Det kan være administrator/system/bruger.
- **Begivenhed:** Omfatter hændelser på øverste niveau, såsom oprindelig levering, manuel afhjælpning, ZAP, indsendelser og dynamisk levering.
- **Handling:** Den specifikke handling, der blev foretaget enten som en del af ZAP eller som administratorhandling (f.eks. blød sletning).
- **Trusler:** Dækker de trusler (malware, phish, spam), der er identificeret på det pågældende tidspunkt.
- **Resultat/detaljer:** Flere oplysninger om resultatet af handlingen, f.eks. om den blev udført som en del af ZAP/administratorhandlingen.

### <a name="original-and-latest-delivery-location"></a>Oprindelig og seneste leveringssted

I øjeblikket finder vi frem til leveringssted i mailgitteret og mail-pop-op-siden. Feltet **Leveringsplacering** bliver omdøbt **_til Original leveringsplacering_*_. Og vi introducerer et andet felt, _*_Latest delivery location_**.

**Den oprindelige leveringsplacering** giver flere oplysninger om, hvor en mail oprindeligt blev leveret. **Seneste leveringssted vil** angive, hvor en mail er landet efter systemhandlinger som *F.eks. ZAP* eller administratorhandlinger *som f.eks. Flyt til slettede elementer*. Seneste leveringssted er beregnet til at fortælle administratorerne om meddelelsens senest kendte placering efter levering eller eventuelle system-/administratorhandlinger. Den inkluderer ikke eventuelle slutbrugerhandlinger i mailen. Hvis en bruger f.eks. har slettet en meddelelse eller flyttet meddelelsen til arkiv/pst, opdateres placeringen af meddelelsen "levering" ikke. Men hvis en systemhandling opdaterede placeringen (f.eks., at ZAP resulterede i, at en mail flyttes til **karantæne), blev** Den seneste leveringsplacering vist som "karantæne".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Delivery_Location.png" alt-text="De opdaterede leveringsplaceringer" lightbox="../../media/Updated_Delivery_Location.png":::

> [!NOTE]
> Der er nogle få tilfælde, **hvor Leveringsplacering** **og Leveringshandling** kan blive vist som "ukendt":
>
> - Du får muligvis  vist Leveringsplacering som "leveret" og Leveringsplacering som "ukendt", hvis meddelelsen blev leveret, men en Indbakkeregel har flyttet meddelelsen til en standardmappe (f.eks. Kladde eller Arkiv) i stedet for til mappen Indbakke eller Uønsket mail.
>
> - **Den seneste leveringsplacering** kan være ukendt, hvis en administrator-/systemhandling (f.eks. ZAP) blev forsøgt forsøgt, men meddelelsen blev ikke fundet. Handlingen sker typisk, når brugeren har flyttet eller slettet meddelelsen. I sådanne tilfælde skal du bekræfte **kolonnen Resultat/** Detaljer i tidslinjevisning. Se efter sætningen "Meddelelse flyttet eller slettet af brugeren."

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Timeline_Delivery_Location.png" alt-text="Leveringssted for tidslinje" lightbox="../../media/Updated_Timeline_Delivery_Location.png":::

### <a name="additional-actions"></a>Yderligere handlinger

*Der blev* anvendt yderligere handlinger efter levering af mailen. De kan omfatte *ZAP**, manuel* afhjælpning (handling, der er foretaget af en administrator, f.eks. blød *sletning), dynamisk* levering og genbehandlet (for en mail, der blev registreret med tilbagevirkende kraft som god).

> [!NOTE]
> Som en del af de ventende ændringer forsvinder værdien "Fjernet af ZAP", der i øjeblikket findes i filteret Leveringshandling. Du har en metode til at søge efter alle mails med ZAP-forsøg via **Yderligere handlinger**.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Additional_Actions.png" alt-text="De yderligere handlinger i Stifinder" lightbox="../../media/Additional_Actions.png":::

### <a name="system-overrides"></a>Systemet tilsidesætter

*Systemtilsidesættelser* giver dig mulighed for at gøre undtagelser til den tilsigtede leveringsplacering for en meddelelse. Du tilsidesætter leveringsplaceringen, der leveres af systemet, baseret på trusler og andre registreringer, der er identificeret ved filtreringsstakken. Systemtilsidesættelser kan angives via lejer- eller brugerpolitik for at levere meddelelsen som foreslået af politikken. Tilsidesættelser kan identificere utilsigtet levering af skadelige meddelelser på grund af konfigurationsforskelle, f.eks. en alt Pengeskab politik for afsendere, der er angivet af en bruger. Disse tilsidesættelsesværdier kan være:

- Tilladt af brugerpolitik: En bruger opretter politikker på postkasseniveau for at tillade domæner eller afsendere.

- Blokeret af brugerpolitik: En bruger opretter politikker på mailfeltniveau for at blokere domæner eller afsendere.

- Tilladt af organisationspolitikken: Organisationens sikkerhedsteam indstiller politikker eller Exchange regler for mailflow (også kaldet transportregler) for at tillade afsendere og domæner for brugere i organisationen. Dette kan være for en række brugere eller hele organisationen.

- Blokeret af organisationspolitik: Organisationens sikkerhedsteam angiver politikker eller regler for mailflow for at blokere afsendere, domæner, meddelelsessprog eller kilde-IP'er for brugere i organisationen. Dette kan anvendes på et sæt af brugere eller hele organisationen.

- Filtypenavn blokeret af organisationspolitik: En organisations sikkerhedsteam blokerer et filtypenavn via politikindstillingerne for antimalware. Disse værdier vises nu i mailoplysninger for at hjælpe med undersøgelser. Secops-teams kan også bruge omfattende filtreringsfunktionalitet til at filtrere på blokerede filtyper.

[![Systemet tilsidesætter i Stifinder.](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/System_Overrides_Grid.png" alt-text="Systemet tilsidesætter gitteret i Stifinder" lightbox="../../media/System_Overrides_Grid.png":::

### <a name="improvements-for-the-url-and-clicks-experience"></a>Forbedringer af URL-adresse- og klikoplevelsen

Forbedringerne omfatter:

- Vis den fulde klikkede URL-adresse (herunder eventuelle **forespørgselsparametre** , der er en del af URL-adressen) i sektionen Klik i pop op-menuen URL-adresse. I øjeblikket vises URL-domænet og stien i titellinjen. Vi udvider disse oplysninger for at vise den fulde URL-adresse.

- Rettelser på tværs af URL-filtre (*URL* versus *URL-domæne* versus *URL-domæne og sti*): Opdateringerne påvirker søgning efter meddelelser, der indeholder en URL-adresse/klik-konklusion. Vi har aktiveret understøttelse af protokolagnostiske søgninger, så du kan søge efter en URL-adresse uden at bruge `http`. Som standard tilknyttes URL-adressen til http, medmindre en anden værdi udtrykkeligt er angivet. Eksempel:
  - Søg med og uden præfikset `http://` i **felterne URL-adresse**, **URL-domæne** og **URL-domæne og** stifilter. Søgninger bør vise de samme resultater.
  - Søg efter præfikset `https://` i **URL-adressen**. Når der ikke angives nogen værdi, antages `http://` præfikset at være.
  - `/`ignoreres i begyndelsen og slutningen af URL-stien, **URL-domæne,** **URL-domæne og stifelter**. `/` i slutningen af **URL-feltet** ignoreres.

### <a name="phish-confidence-level"></a>Phish-tillidsniveau

Phish-tillidsniveauet hjælper med at identificere den grad af tillid, som en mail blev kategoriseret som "phish". De to mulige værdier er *Høj* og *Normal*. I de indledende faser vil dette filter kun være tilgængeligt i Visningen Phish i Threat Explorer.

[![Phish Confidence-niveau i Stifinder.](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>ZAP URL-signal

ZAP-URL-signalet bruges typisk til scenarier med ZAP Phish-besked, hvor en mail blev identificeret som Phish og fjernet efter levering. Dette signal forbinder beskeden med de tilsvarende resultater i Stifinder. Det er en af IOCs for beskeden.

For at forbedre vores jagtproces har vi opdateret registreringerne af Threat Explorer og i realtid for at gøre jagtoplevelsen mere ensartet. Ændringerne er beskrevet her:

- [Tidszoneforbedringer](#timezone-improvements)
- [Opdater under opdateringsprocessen](#update-in-the-refresh-process)
- [Diagramudse detaljeringsliste, der skal føjes til filtre](#chart-drilldown-to-add-to-filters)
- [I opdateringer til produktoplysninger](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Filtrere efter brugermærker

Du kan nu sortere og filtrere efter system- eller brugerdefinerede brugermærker for hurtigt at forstå omfanget af trusler. Du kan få mere at vide under [Brugermærker](user-tags.md).

> [!IMPORTANT]
> Filtrering og sortering efter brugermærker er i øjeblikket offentlig prøveversion. Denne funktionalitet kan ændres væsentligt, før den frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har om det.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-tags.png" alt-text="Kolonnen Mærker i Stifinder" lightbox="../../media/threat-explorer-tags.png":::

### <a name="timezone-improvements"></a>Tidszoneforbedringer

Du får vist tidszonen for mailposterne i portalen samt for eksporterede data. Den vil være synlig på tværs af oplevelser som f.eks. Mailgitter, Pop op-billede af Detaljer, Tidslinje for mail og Lignende mails, så tidszonen for resultatsættet er klar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/TimezoneImprovements.png" alt-text="Tidszonen Vis i Stifinder" lightbox="../../media/TimezoneImprovements.png":::

### <a name="update-in-the-refresh-process"></a>Opdater under opdateringsprocessen

Nogle brugere har kommenteret forvirringen ved automatisk opdatering (f.eks. så snart du ændrer datoen, opdateres siden) og manuel opdatering (for andre filtre). På samme måde fører fjernelse af filtre til automatisk opdatering. Hvis du ændrer filtre, mens forespørgslen ændres, kan det medføre inkonsekvente søgeoplevelser. For at løse disse problemer flytter vi til en mekanisme til manuel filtrering.

Fra et oplevelses-standpunkt kan brugeren anvende og fjerne de forskellige filtre (fra filtersættet og datoen) og vælge opdateringsknappen for at filtrere resultaterne, efter de har defineret forespørgslen. Knappen Opdater fremhæves også på skærmen. Vi har også opdateret de relaterede værktøjstip og dokumentationen i produktet.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ManualRefresh.png" alt-text="Knappen Opdater for at filtrere resultaterne" lightbox="../../media/ManualRefresh.png":::

### <a name="chart-drilldown-to-add-to-filters"></a>Diagramudse detaljeringsliste, der skal føjes til filtre

Du kan nu tilføje diagramforklaringsværdier som filtre. Vælg knappen **Opdater** for at filtrere resultaterne.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ChartDrilldown.png" alt-text="Analyser ned gennem diagrammer for at filtrere" lightbox="../../media/ChartDrilldown.png":::

### <a name="in-product-information-updates"></a>Opdateringer af produktoplysninger

Der er nu flere oplysninger tilgængelige i produktet, f.eks. det samlede antal søgeresultater i gitteret (se nedenfor). Vi har forbedret etiketter, fejlmeddelelser og værktøjstip for at give flere oplysninger om filtre, søgeoplevelse og resultatsæt.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ProductInfo.png" alt-text="De produktoplysninger, der skal vises" lightbox="../../media/ProductInfo.png":::

## <a name="extended-capabilities-in-threat-explorer"></a>Udvidede funktioner i Threat Explorer

### <a name="top-targeted-users"></a>Mest målrettede brugere

I dag viser vi listen over de mest målrettede brugere i malwarevisningen for mails i sektionen **Vigtigste malwarefamilier** . Vi udvider denne visning i visningerne Phish og Alle mails. Du vil kunne se de fem mest populære brugere sammen med antallet af forsøg for hver bruger for den tilsvarende visning. For phish-visning får du f.eks. vist antallet af Phish-forsøg.

Du kan eksportere listen over målrettede brugere på op til 3.000 sammen med antallet af forsøg på offlineanalyse for hver mailvisning. Desuden vil det at vælge antallet af forsøg (f.eks. 13 forsøg på billedet nedenfor) åbne en filtreret visning i Threat Explorer, så du kan se flere detaljer på tværs af mails og trusler for den pågældende bruger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="De mest populære brugere" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Exchange transportregler

Som en del af databerigende, vil du kunne se alle de forskellige Exchange transportregler (ETR), der blev anvendt på en meddelelse. Disse oplysninger vil være tilgængelige i visningen Mailgitter. Hvis du vil have den vist, **skal** du vælge Kolonneindstillinger i **gitteret og Exchange Tilføj transportregel** i kolonneindstillingerne. Den vil også være synlig i pop op-pop-op-mailen Detaljer.

Du kan se både GUID og navnet på de transportregler, der blev anvendt på meddelelsen. Du kan søge efter meddelelser ved hjælp af navnet på transportreglen. Dette er en søgning af "Indeholder", hvilket betyder, at du også kan udføre delvise søgninger.

> [!IMPORTANT]
> Tilgængeligheden af Etr-søgning og -navn afhænger af den specifikke rolle, du har fået tildelt. Du skal have en af følgende roller/tilladelser for at få vist navnene på et givet produkt og søgefunktionen. Hvis du ikke har fået tildelt nogen af disse roller, kan du ikke se navnene på transportreglerne eller søge efter meddelelser ved hjælp af ETR-navne. Du kan dog se et ETR-navn og GUID-oplysninger i maildetaljerne. Andre oplevelser med visning af poster i Mailgitter, Pop op-pop-op-filer, Filtre og Eksporter påvirkes ikke.
>
> - Kun EXO – forebyggelse af datatab: Alle
> - Kun EXO - O365SupportViewConfig: Alle
> - Microsoft Azure Active Directory eller EXO – Sikkerhedsadministrator: Alle
> - AAD eller EXO – Sikkerhedslæser: Alle
> - Kun EXO - Transportregler: Alle
> - Kun EXO – View-Only konfiguration: Alle
>
> I mailgitteret, pop op-billedet Detaljer og Eksporteret CSV får et Navn/GUID som vist nedenfor.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="De Exchange transportregler" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Indgående forbindelser

Forbindelser er en samling af instruktioner, der tilpasser, hvordan dine mails flyder til og fra din Microsoft 365 eller Office 365 organisation. De gør det muligt for dig at anvende eventuelle sikkerhedsbegrænsninger eller kontrolelementer. I Threat Explorer kan du nu få vist de forbindelser, der er relateret til en mail, og søge efter mails ved hjælp af forbindelsesnavne.

Søgningen efter forbindelser er af "indeholder" karakter, hvilket betyder, at delvise søgninger efter nøgleord også skal fungere. I gittervisningen Hovedgitter, pop op-menuen Detaljer og eksporteret CSV, vises forbindelserne i formatet Navn/GUID som vist her:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Oplysninger om forbindelse" lightbox="../../media/Connector_Details.png":::

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nye funktioner i registreringerne i Threat Explorer og i realtid

- [Få vist phishingmails, der sendes til efterligninger af brugere og domæner](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [Få vist et eksempel på mailoverskriften, og download brødteksten i mailen](#preview-email-header-and-download-email-body)
- [Mailtidslinje](#email-timeline)
- [Eksportér URL-adresse klik på data](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Få vist phishingmails, der sendes til efterligninger af brugere og domæner

Hvis du vil identificere forsøg på phishing mod brugere og domæner, der er efterligninger af brugere, skal du føjes til listen over *brugere for at beskytte dem*. For domæner skal administratorer enten aktivere *organisationsdomæner* eller føje et domænenavn til Domæner for *at beskytte dem*. De domæner, der skal beskyttes, findes på *siden med antiphishing-politikker* *i afsnittet Repræsentation* .

Hvis du vil gennemse phish-meddelelser og søge efterligninger af brugere eller domæner, skal [du bruge visningen > Phish](threat-explorer-views.md) i Stifinder.

I dette eksempel bruges Threat Explorer.

1. I [Security & Compliance Center](https://protection.office.com) (https://protection.office.com)skal du vælge > Explorer (eller Registreringer i realtid).

2. I menuen Vis skal du vælge Mail > Phish.

   Her kan du vælge **efterligning af domæne** eller **efterligning af bruger**.

3. **Vælg** ENTEN **Efterligning af domæne**, og skriv derefter et beskyttet domæne i tekstfeltet.

   Du kan f.eks. søge efter beskyttede *domænenavne som contoso**, contoso.com* eller *contoso.com.au*.

4. Vælg Emnet for en meddelelse under fanen Mail på fanen > Detaljer for at se yderligere oplysninger om efterligning, f.eks. Efterligning af domæne/registreret placering.

    **ELLER**

    Vælg **Efterligning af** bruger, og skriv en beskyttet brugers mailadresse i tekstfeltet.

    > [!TIP]
    > **Du opnår de bedste** resultater ved *at bruge fulde mailadresser* til at søge efter beskyttede brugere. Du vil hurtigere og hurtigere finde den beskyttede bruger, hvis du *søger efter en firstname.lastname@contoso.com*, f.eks. når du undersøger bruger efterligning. Når du søger efter et beskyttet domæne, tager søgningen roddomænet (f.eks contoso.com) og domænenavnet (*contoso*). Når du søger efter *roddomænet contoso.com* både *efterligninger af contoso.com* og domænenavnet *contoso*.

5. Vælg Emne **for** en **meddelelse under** >  fanen MailDetaljer for at få vist yderligere repræsentationsoplysninger om brugeren eller domænet og *den registrerede placering*.

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Detaljeruden i Trusselsstifinder for en beskyttet bruger, der viser registreringsplaceringen og den trussel, der blev registreret (her phish-efterligning af en bruger)" lightbox="../../media/threat-ex-views-impersonated-user-image.png":::

> [!NOTE]
> Hvis du på trin 3 eller 5 vælger registreringsteknologi og  vælger henholdsvis **repræsentationsdomæne** eller efterligningsbruger,  >  vises oplysningerne på fanen Maildetaljer om brugeren eller domænet, og placeringen Registreret kun på de meddelelser, der  er relateret til den bruger eller det domæne, der er angivet på siden med   *antiphishing-politikker*.

### <a name="preview-email-header-and-download-email-body"></a>Få vist et eksempel på mailoverskriften, og download brødteksten i mailen

Du kan nu få vist et eksempel på en mailoverskrift og downloade mailens brødtekst i Threat Explorer. Administratorer kan analysere downloadede brevhoveder/mails for trusler. Da hentning af mails kan give risiko for eksponering for oplysninger, styres denne proces af rollebaseret adgangskontrol (RBAC). En ny rolle, *Preview*, er påkrævet for at give mulighed for at hente mails i visningen alle mails. Visning af mailoverskriften kræver dog ikke nogen yderligere rolle (ud over hvad der kræves for at få vist meddelelser i Threat Explorer). Sådan opretter du en ny rollegruppe med rollen Eksempel:

1. Vælg en indbygget rollegruppe, der kun har preview-rollen, f.eks Data– eller eDiscovery-manager.
2. Vælg **Kopiér rollegruppe**.
3. Vælg et navn og en beskrivelse til din nye rollegruppe, og vælg **Næste**.
4. Du kan ændre rollerne ved at tilføje og fjerne roller efter behov, men forlade rollen Eksempel.
5. Tilføj medlemmer, og vælg **derefter Opret rollegruppe**.

Registreringer af Stifinder og i realtid får også nye felter, der giver et mere komplet billede af, hvor dine mails lander. Disse ændringer gør det nemmere at lede efter Security Ops. Men det primære resultat er, at du hurtigt kan se placeringen af problemmails.

Hvordan gøres dette? Leveringsstatus er nu opdelt i to kolonner:

- **Leveringshandling** – Status for mailen.
- **Leveringssted** – Hvor mailen blev distribueret.

*Leveringshandling* er den handling, der er foretaget på en mail på grund af eksisterende politikker eller registreringer. Her er de mulige handlinger for en mail:

|Leveret|Uønsket|Blokeret|Erstattet|
|---|---|---|---|
|Mail blev leveret til indbakken eller mappen for en bruger, og brugeren kan få adgang til den.|Mail blev sendt til brugerens mappe Uønsket eller Slettet, og brugeren kan få adgang til den.|Mails, der er i karantæne, som mislykkedes eller er blevet tabt. Disse mails er utilgængelige for brugeren.|Mails havde ondsindede vedhæftede filer erstattet af .txt, der viser, at den vedhæftede fil var skadelig.|

Her er, hvad brugeren kan se og ikke kan se:

|Tilgængelig for slutbrugere|Utilgængeligt for slutbrugere|
|---|---|
|Leveret|Blokeret|
|Uønsket|Erstattet|

**Leveringssted** viser resultaterne af politikker og registreringer, der kører efter levering. Det er sammenkædet med **_handlingen Levering_**. Dette er de mulige værdier:

- *Indbakke eller mappe*: Mailen findes i indbakken eller i en mappe (i henhold til dine mailregler).
- *Lokal eller ekstern*: Postkassen findes ikke i skyen, men er lokal.
- *Mappen Uønsket*: Mailen findes i en brugers mappe med Uønsket mail.
- *Mappen Slettet post*: Mailen i en brugers mappe Slettet post.
- *Karantæne*: Mailen er i karantæne og ikke i en brugers postkasse.
- *Mislykket*: Mailen kunne ikke nås til postkassen.
- *Tabt*: Mailen forsvandt et sted i mailflowet.

### <a name="email-timeline"></a>Mailtidslinje

**Mailtidslinjen** er en ny Stifinder-funktion, der forbedrer administratorens jagtoplevelse. Det klipper den tid, du bruger på at kontrollere forskellige placeringer for at forsøge at forstå begivenheden. Når flere begivenheder sker på eller tæt på samme tid, som en mail modtages, vises disse begivenheder i en tidslinjevisning. Nogle hændelser, der sker med din mail efter levering, registreres i **kolonnen Særlige** handlinger. Administratorer kan kombinere oplysninger fra tidslinjen med den særlige handling, der er taget på mailen efter levering, for at få indsigt i, hvordan deres politikker fungerer, hvor mailen sidst blev distribueret, og, i nogle tilfælde, hvad den endelige vurdering var.

Få mere at vide under [Undersøg og afhjulpet skadelige mails, der blev leveret i Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>Eksportér URL-adresse klik på data

Du kan nu eksportere rapporter for URL-klik for at Microsoft Excel for at få vist deres netværksmeddelelses-id og klikke på **konklusion, som** hjælper med at forklare, hvor din URL-adresse klik-trafik stammer fra. Sådan fungerer det: I Threat Management på værktøjslinjen Office 365 hurtig start skal du følge denne kæde:

**Stifinder** \> **Vis phish** \>  \> Klik **Øverste URL-adresser** eller **Øverste klik på URL-adressen vælger** \> en post for at åbne pop op-pop-op-adressen.

Når du vælger en URL-adresse på listen, får du **vist en ny** Eksport-knap i det pop op-panel. Brug denne knap til at flytte data til et Excel regneark for nemmere rapportering.

Følg denne sti for at komme til den samme placering i rapporten registreringer i realtid:

**Stifinder** \> **Registreringer i realtid** \> **Vis phish** \> **URL-adresser** \> **Øverste URL-adresser** **eller Øverste klik Vælg** \> en post for at åbne pop op-knappen \> for URL-adressen, og gå **til fanen Klik** .

> [!TIP]
> Netværksmeddelelses-id'et knytter klik tilbage til bestemte mails, når du søger på id'et via Stifinder eller tilknyttede tredjepartsværktøjer. Sådanne søgninger identificerer den mail, der er knyttet til et klikresultat. Hvis du har det korrelerede netværksmeddelelses-id, får du en hurtigere og mere effektiv analyse.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tp_ExportClickResultAndNetworkID.png" alt-text="Fanen Klik i Stifinder" lightbox="../../media/tp_ExportClickResultAndNetworkID.png":::

## <a name="see-malware-detected-in-email-by-technology"></a>Se malware registreret i mail efter teknologi

Antag, at du vil se malware registreret i mails, der er sorteret efter Microsoft 365 teknologi. Det gør du ved at bruge [visningen > malware](threat-explorer-views.md#email--malware) i Stifinder (eller registreringer i realtid).

1. I Security & Compliance Center (<https://protection.office.com>) skal du **vælge Registreringer** \> af **trusselsadministration (eller Registreringer i realtid**). I dette eksempel bruges Stifinder.

2. Vælg **Mailmalware** i **menuen** \> **Vis**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailMalwareMenu.png" alt-text="Menuen Vis for Stifinder" lightbox="../../media/ExplorerViewEmailMalwareMenu.png":::

3. Klik **på Afsender**, og vælg derefter **Teknologi til** \> **grundlæggende registrering**.

   Dine registreringsteknologier er nu tilgængelige som filtre til rapporten.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTech.png" alt-text="Teknologier til registrering af malware" lightbox="../../media/ExplorerEmailMalwareDetectionTech.png":::

4. Vælg en indstilling. Vælg derefter knappen **Opdater for** at anvende filteret.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTechATP.png" alt-text="Den valgte registreringsteknologi" lightbox="../../media/ExplorerEmailMalwareDetectionTechATP.png":::

Rapporten opdateres for at vise de resultater, som malware registreret i en mail, ved hjælp af den teknologiindstilling, du har valgt. Herfra kan du foretage yderligere analyser.

## <a name="view-phishing-url-and-click-verdict-data"></a>Få vist phishing-URL-adresse, og klik på vurderingsdata

Antag, at du vil se phishingforsøg via URL-adresser i en mail, herunder en liste over URL-adresser, der blev tilladt, blokeret og tilsidesat. For at identificere URL-adresser, der blev [klikket på, Pengeskab der oprettes](safe-links.md) links. Sørg for, at du [har Pengeskab Links-politikker](set-up-safe-links-policies.md) for klik og logføring af klik Pengeskab Links.

Hvis du vil gennemse phish-url-adresser i meddelelser og klikke på URL-adresser i phish-meddelelser, [ > ](threat-explorer-views.md#email--phish) skal du bruge visningen E-mail i Stifinder eller registreringer i realtid.

1. I Security & Compliance Center (<https://protection.office.com>) skal du **vælge Registreringer** \> af **trusselsadministration (eller Registreringer i realtid**). I dette eksempel bruges Stifinder.

2. Vælg **Email** **Phish** i **menuen** \> Vis.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menuen Vis for Stifinder i phishing-kontekst" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Klik **på Afsender**, og vælg derefter **WEBADRESSEr Klik** \> **på konklusion**.

4. Vælg en eller flere indstillinger, f.eks. Blokeret og **Bloker tilsidesættes**, og  vælg derefter knappen Opdater på samme linje som indstillingerne for at anvende det pågældende filter. (Opdater ikke dit browservindue.)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png" alt-text="URL-adresserne, og klik på bedømmelser" lightbox="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png":::

   Rapporten opdateres, så der vises to forskellige URL-tabeller på fanen URL-adresse under rapporten:

   - **Øverste URL-adresser** er URL-adresserne i de meddelelser, du har filtreret ned til, og handlingen til levering af mail tæller for hver URL-adresse. I phish-mailvisningen indeholder denne liste typisk legitime URL-adresser. Hackere har en blanding af gode og dårlige URL-adresser i deres meddelelser for at forsøge at få dem leveret, men de får de ondsindede links til at se mere interessante ud. Tabellen med URL-adresser sorteres efter samlet antal mails, men denne kolonne er skjult for at forenkle visningen.

   - **De mest populære klik** er de Pengeskab URL-adresser, der blev klikket på, sorteret efter samlet antal klik. Denne kolonne vises heller ikke, for at forenkle visningen. Samlet antal pr. kolonne angiver antallet af Pengeskab klik på bedømmelse for hver klikket URL-adresse. I phish-mailvisningen er disse normalt mistænkelige eller skadelige URL-adresser. Men visningen kan indeholde URL-adresser, der ikke er trusler, men som er i phish-meddelelser. Klik på URL-adresse på links, der ikke er blevet åbnet, vises ikke her.

   De to URL-tabeller viser de vigtigste URL-adresser i phishing-mails ved hjælp af leveringshandling og placering. Tabellerne viser URL-klik, der blev blokeret eller besøgt på trods af en advarsel, så du kan se, hvilke potentielle dårlige links der blev vist til brugerne, og som brugeren har klikket på. Herfra kan du foretage yderligere analyser. Eksempelvis kan du under diagrammet se de øverste URL-adresser i mails, der blev blokeret i din organisations miljø.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="URL-adresser for Stifinder, der blev blokeret" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Vælg en URL-adresse for at få vist mere detaljerede oplysninger.

   > [!NOTE]
   > I pop op-dialogboksen URL-adresse fjernes filtreringen af mails for at vise den fulde visning af URL-adressens eksponering i dit miljø. Det gør det muligt at filtrere efter mails, du er bekymret for i Stifinder, finde bestemte URL-adresser, der kan være trusler, og derefter udvide din forståelse af URL-eksponeringen i dit miljø (via dialogboksen med URL-oplysninger) uden at skulle føje URL-filtre til stifindervisningen.

### <a name="interpretation-of-click-verdicts"></a>Fortolkning af klikfortolkninger

I pop op-menuen Mail eller URL-adresse, Topklik samt i vores filtreringsoplevelser får du vist forskellige vurderingsværdier for klik:

- **Ingen:** Det er ikke muligt at registrere konklusionen for URL-adressen. Brugeren har muligvis klikket gennem URL-adressen.
- **Tilladt:** Brugeren har fået tilladelse til at gå til URL-adressen.
- **Blokeret:** Brugeren blev blokeret fra at navigere til URL-adressen.
- **Afventende konklusion:** Brugeren fik vist den detonation-afventende side.
- **Blokeret tilsidesættet:** Brugeren blev blokeret fra at navigere direkte til URL-adressen. Men brugeren overrokerer blokken for at gå til URL-adressen.
- **Afventende konklusion er omgået:** Brugeren fik vist detonationssiden. Men brugeren overroker meddelelsen for at få adgang til URL-adressen.
- **Fejl:** Brugeren fik vist fejlsiden, eller der opstod en fejl ved registrering af konklusionen.
- **Fejl:** Der opstod en ukendt undtagelse, mens konklusionen blev registreret. Brugeren har muligvis klikket gennem URL-adressen.

## <a name="review-email-messages-reported-by-users"></a>Gennemse mails, der er rapporteret af brugere

Antag, at du vil se de mails, som brugerne i organisationen har rapporteret som Uønsket *, Ikke* uønsket eller [](enable-the-report-message-add-in.md) *Phishing* via tilføjelsesprogrammet Rapportmeddelelse eller [tilføjelsesprogrammet Rapportphishing](enable-the-report-phish-add-in.md). Hvis du vil se dem, [**skal du** >  **bruge visningen Mailsubmissioner**](threat-explorer-views.md#email--submissions) i Stifinder (eller registreringer i realtid).

1. I Security & Compliance Center (<https://protection.office.com>) skal du **vælge Registreringer** \> af **trusselsadministration (eller Registreringer i realtid**). I dette eksempel bruges Stifinder.

2. Vælg **Mailindsendelser** **i menuen** \> **Vis**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/explorer-view-menu-email-user-reported.png" alt-text="Menuen Vis for Stifinder for mails" lightbox="../../media/explorer-view-menu-email-user-reported.png":::

3. Klik **på Afsender**, og vælg **derefter Grundlæggende** \> **rapporttype**.

4. Vælg en indstilling, **f.eks. Phish**, og vælg derefter **knappen** Opdater.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/EmailUserReportedReportType.png" alt-text="Den bruger-rapporterede phish" lightbox="../../media/EmailUserReportedReportType.png":::

Rapporten opdateres for at vise data om mails, som personer i organisationen har rapporteret som et forsøg på phishing. Du kan bruge disse oplysninger til at udføre yderligere analyse, og hvis det er nødvendigt, kan du justere dine [antiphishing-politikker Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Start automatiseret undersøgelse og svar

> [!NOTE]
> Automatiserede undersøgelses- og svarmuligheder er tilgængelige *Microsoft Defender for Office 365 Plan 2* *og Office 365 E5*.

[Automatiseret undersøgelse og svar](automated-investigation-response-office.md) kan spare tid og besvær for sikkerhedsteamet, når det bruges på at undersøge og mindske cyberangreb. Ud over at konfigurere beskeder, der kan udløse en sikkerhedsspilbog, kan du starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder. Du kan finde flere [oplysninger i Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Stifinder](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Flere måder at bruge registreringer i Explorer og i realtid på

Ud over de scenarier, der er beskrevet i denne artikel, har du mange flere rapporteringsmuligheder tilgængelige med Stifinder (eller registreringer i realtid). Se følgende artikler:

- [Find og undersøg skadelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Få vist skadelige filer, der er registreret SharePoint Online, OneDrive og Microsoft Teams](./mdo-for-spo-odb-and-teams.md)
- [Få et overblik over visningerne i Threat Explorer (og registreringer i realtid)](threat-explorer-views.md)
- [Statusrapport over trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender for Office 365](defender-for-office-365.md) at bruge Stifinder eller registreringer i realtid.

- Stifinder er inkluderet Defender for Office 365 Plan 2.
- Rapporten registreringer i realtid er inkluderet i Defender for Office 365 Plan 1.
- Planlæg at tildele licenser til alle brugere, der skal være beskyttet af Defender for Office 365. Explorer- og realtidsregistreringer viser registreringsdata for licenserede brugere.

Hvis du vil have vist og bruge Stifinder- eller realtidsregistreringer, skal du have de rette tilladelser, f.eks. tilladelser, der er givet til en sikkerhedsadministrator eller sikkerhedslæser.

- Sikkerheds- og & skal have tildelt en af følgende roller:

  - Organisationsadministration
  - Sikkerhedsadministrator (kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser

- For Exchange Online skal du have en af følgende roller tildelt i enten Exchange Administration (EAC) [eller Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell):

  - Organisationsadministration
  - View-Only organisationsadministration
  - View-Only modtagere
  - Styring af overholdelse

Hvis du vil have mere at vide om roller og tilladelser, skal du se følgende ressourcer:

- [Tilladelser i Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md)
- [Funktionstilladelser i Exchange Online](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Forskelle mellem registreringer i Threat Explorer og realtid

- Rapporten *registreringer i realtid* er tilgængelig i Defender for Office 365 Plan 1. *Threat Explorer* findes i Defender for Office 365 Plan 2.
- Registreringer i realtid gør det muligt at få vist registreringer i realtid. Threat Explorer gør det også, men det indeholder også yderligere oplysninger om et bestemt angreb.
- En *alle mailvisning* er tilgængelig i Threat Explorer, men ikke i realtidsregistreringsrapporten.
- Der er flere filtreringsfunktioner og tilgængelige handlinger i Threat Explorer. Du kan finde flere oplysninger [Microsoft Defender for Office 365 Beskrivelse af tjenesten: Tilgængelighed af funktioner på Defender for Office 365 planerne](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="other-articles"></a>Andre artikler

[Undersøg mails med siden Mailenhed](mdo-email-entity-page.md)
