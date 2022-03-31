---
title: Opret eDiscovery-ventende oplysninger i en Core eDiscovery-sag
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Du kan oprette en venteposition, der er knyttet til en Core eDiscovery-sag Microsoft 365 at bevare indhold, der er relevant for en undersøgelse eller en juridisk sag.
ms.openlocfilehash: 976c0e47195c520620cfa57e996cee42df509593
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63599838"
---
# <a name="create-an-ediscovery-hold"></a>Opret en eDiscovery-venteposition

Du kan bruge en Core eDiscovery-sag til at oprette ventende dokumenter for at bevare indhold, der kan være relevant for sagen. Du kan placere en venteposition på Exchange postkasser og OneDrive for Business konti for de personer, du undersøger i sagen. Du kan også placere en venteposition på de postkasser og websteder, der er knyttet til Microsoft Teams, Office 365 Grupper og Yammer Grupper. Når du placerer indholdsplaceringer i venteposition, bevares indhold, indtil du fjerner indholdsplaceringen fra ventepositionen, eller indtil du sletter ventepositionen.

Når du har oprettet en eDiscovery-venteposition, kan det tage op til 24 timer, før ventepositionen træder i kraft.

Når du opretter en venteposition, har du følgende muligheder for at begrænse det indhold, der bevares på de angivne indholdsplaceringer:
  
- Opret et uendeligt hold, hvor alt indhold på de angivne placeringer er sat i venteposition. Du kan også oprette en forespørgselsbaseret venteposition, hvor kun indholdet på de angivne placeringer, der svarer til en søgeforespørgsel, er sat i venteposition.

- Angiv et datoområde for kun at bevare det indhold, der blev sendt, modtaget eller oprettet inden for det pågældende datointerval. Du kan også opbevare alt indhold på bestemte placeringer, uanset hvornår det blev sendt, modtaget eller oprettet.
  
## <a name="how-to-create-an-ediscovery-hold"></a>Sådan opretter du en eDiscovery-venteposition

Sådan oprettes en eDiscovery-venteposition, der er knyttet til en core eDiscovery-sag:
  
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for den brugerkonto, der har fået tildelt de relevante eDiscovery-tilladelser.

2. I venstre navigationsrude skal du klikke **på Vis** alle og derefter klikke **på eDiscovery > Core**.

3. På core **eDiscovery-siden** skal du klikke på navnet på den sag, du vil oprette ventepositionen i.

4. Klik **på fanen** Hold på startsiden **for sagen** .
  
5. Klik på **Opret** på siden **Venteposition**.

6. På siden **Giv guiden Navngive** din venteposition skal du give venteposition et navn og tilføje en valgfri beskrivelse, og derefter skal du klikke på **Næste**. Navnet på ventepositionen skal være entydigt i organisationen.

7. På siden **med guiden Vælg** placeringer skal du vælge de indholdsplaceringer, du vil placere i venteposition. Du kan placere postkasser, websteder og offentlige mapper i venteposition.

    ![Vælg de indholdsplaceringer, der skal være i venteposition.](../media/eDiscoveryHoldLocations.png)
  
   1. **Exchange postkasser**: Indstil til/fra-knappen  til Til, og klik derefter på Vælg brugere, grupper eller teams for at angive **,** hvilke postkasser der skal være i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition i gruppemedlemmers postkasser) for at placere dem i venteposition. Du kan også placere en venteposition på den tilknyttede postkasse for en Microsoft Team-, Office 365-gruppe og Yammer gruppe. Du kan finde flere oplysninger om de programdata, der bevares, når en postkasse er sat i venteposition, under Indhold, der er gemt i [postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til Til, og klik derefter  på Vælg websteder for at angive, SharePoint-websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til SharePoint for et Microsoft-team, en Office 365-gruppe eller en Yammer gruppe.
  
   3. **Exchange offentlige mapper**: Sæt til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Slå til/fra-knappen fra, hvis du ikke vil sætte offentlige mapper i venteposition.

   > [!IMPORTANT]
   > Når du Exchange postkasser eller SharePoint websteder i venteposition, skal du eksplicit føje mindst én indholdsplacering til ventepositionen. Med andre ord, hvis du indstiller til/fra-knappen til **Til for** postkasser eller websteder, skal du vælge bestemte postkasser eller websteder, der skal føjes til ventepositionen. Ellers oprettes eDiscovery-ventepositionen, men postkasser eller websteder føjes ikke til ventepositionen, og statistikken viser, at ingen indholdsplaceringer eller elementer er i venteposition.

8. Når du er færdig med at føje placeringer til ventepositionen, skal du klikke på **Næste**.

9. Hvis du vil oprette en forespørgselsbaseret venteposition ved hjælp af nøgleord eller betingelser, skal du udføre følgende trin. Hvis du vil bevare alt indhold på de angivne indholdsplaceringer, skal du klikke på **Næste**.

    ![Opret en forespørgselsbaseret venteposition med nøgleord og betingelser.](../media/eDiscoveryHoldQuery.png)
  
    1. I feltet under Nøgleord **skal du** skrive en forespørgsel for kun at bevare det indhold, der svarer til forespørgselskriterierne. Du kan angive nøgleord, egenskaber for mail eller webstedsegenskaber, f.eks. filnavne. Du kan også bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. **OG**, **ELLER** eller **IKKE**.

    2. Klik **på Tilføj betingelse** for at tilføje en eller flere betingelser for at indsnævre forespørgslen til venteposition. Hver betingelse føjer en delsætning til KQL-søgeforespørgslen, der oprettes og køres, når du opretter ventepositionen. Du kan f.eks. angive et datointerval, så mails eller webstedsdokumenter, der er oprettet inden for datointervallet, bevares. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i **feltet Nøgleord** ) og andre betingelser af **operatoren AND** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og betingelsen, der skal bevares.

    Du kan finde flere oplysninger om at oprette en søgeforespørgsel og bruge betingelser under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

10. Når du har konfigureret en forespørgselsbaseret venteposition, skal du klikke **på Næste**.

11. Gennemse dine indstillinger (og rediger dem, hvis det er nødvendigt), og klik derefter på **Send**.

> [!NOTE]
> Når du opretter en forespørgselsbaseret venteposition, sættes alt indhold fra valgte placeringer i venteposition. Efterfølgende fjernes alt indhold, der ikke stemmer overens med den angivne forespørgsel, fra ventepositionen hver syv til 14 dage. Men forespørgselsbaseret venteposition rydder ikke indhold, hvis der anvendes mere end fem ventepositioner af enhver type på en indholdsplacering, eller hvis et element har indekseringsproblemer.

## <a name="query-based-holds-placed-on-sites"></a>Forespørgselsbaserede vente hold placeret på websteder

Husk følgende, når du placerer et forespørgselsbaseret eDiscovery-hold på dokumenter, der er placeret på SharePoint websteder:

- En forespørgselsbaseret venteposition bevarer i første omgang alle dokumenter på et websted i kort tid, efter de er blevet slettet. Det betyder, at når et dokument slettes, flyttes det til biblioteket til opbevaring af dokumenter, også selvom det ikke opfylder kriterierne for forespørgselsbaseret venteposition. Men slettede dokumenter, der ikke svarer til en forespørgselsbaseret venteposition, fjernes af et timerjob, der behandler biblioteket til opbevaring af dokumenter. Timerjobbet kører med jævne mellemrum og sammenligner alle dokumenter i biblioteket til opbevaring af dokumenter med dine forespørgselsbaserede eDiscovery-ventepositioner (og andre typer ventepositioner og opbevaringspolitikker). Timerjobbet sletter de dokumenter, der ikke svarer til en forespørgselsbaseret venteposition, og bevarer de dokumenter, der gør.

- Forespørgselsbaserede ventepositioner bør ikke bruges til at udføre målrettet opbevaring, såsom at bevare dokumenter i en bestemt mappe eller et bestemt websted eller ved hjælp af andre placeringsbaserede holdkriterier. Det kan have utilsigtede resultater. Vi anbefaler, at du bruger ikke-placeringsbaserede holdkriterier som nøgleord, datointervaller eller andre dokumentegenskaber for at bevare webstedsdokumenter.

## <a name="ediscovery-hold-statistics"></a>eDiscovery-holdstatistik

Når du har oprettet en eDiscovery-venteposition, vises oplysninger om den nye venteposition på pop op-siden for den valgte venteposition. Disse oplysninger omfatter antallet af postkasser og websteder i venteposition og statistik om det indhold, der blev sat i venteposition, f.eks. det samlede antal og størrelsen af elementer, der er sat i venteposition, og den seneste gang statistik for venteposition blev beregnet. Disse statistik for venteposition hjælper dig med at identificere mængden af indhold, der er relateret til sagen, der bevares.
  
![Hold statistik.](../media/eDiscoveryHoldStatistics.png)
  
Husk følgende om statistik for eDiscovery-ventepositioner:
  
- Det samlede antal elementer, der er sat i venteposition, angiver antallet af elementer fra alle indholdskilder, der er sat i venteposition. Hvis du har oprettet en forespørgselsbaseret venteposition, angiver denne statistik antallet af elementer, der svarer til forespørgslen.

- Antallet af elementer, der er i venteposition, omfatter også uindsiderede elementer, der findes på indholdsplaceringerne. Hvis du opretter en forespørgselsbaseret venteposition, er alle elementer, der ikke er identificeret på indholdsplaceringerne, sat i venteposition. Dette omfatter ikke-opdaterede elementer, der ikke opfylder søgekriterierne for forespørgselsbaserede ventepositioner og ikke-opdaterede elementer, der kan falde uden for en betingelse for datointervallet. Dette er anderledes end det, der sker, når du kører en søgning, hvor ikke-opdaterede elementer, der ikke svarer til søgeforespørgslen eller udelades af en betingelse for datoområde, ikke medtages i søgeresultaterne. Du kan finde flere oplysninger om indekserede elementer under [Delvist indekserede elementer](partially-indexed-items-in-content-search.md).

- Du kan få de seneste ventepositionsstatistik ved  at klikke på Opdater statistik for at køre et søgeestimat, der beregner det aktuelle antal elementer i venteposition.

- Det er normalt, at antallet af elementer, der er i venteposition, øges med tiden, fordi brugere, hvis postkasse eller websted er i venteposition, typisk sender eller modtager nye mails og opretter nye dokumenter i SharePoint og OneDrive.

- Hvis en Exchange-postkasse, SharePoint-websted eller OneDrive-konto flyttes til et andet område i et multi-geo-miljø, medtages statistikken for det pågældende websted ikke i ventepositionsstatistikken. Men indholdet på disse placeringer bevares stadig. Og hvis en postkasse eller et websted flyttes til et andet område, opdateres SMTP-adressen eller URL-adressen, der vises i venteposition, ikke automatisk. Du skal redigere ventepositionen og opdatere URL-adressen eller SMTP-adressen, så indholdsplaceringerne igen medtages i ventepositionsstatistikken

## <a name="search-locations-on-ediscovery-hold"></a>Søgeplaceringer på eDiscovery-venteposition

Når [du søger](search-for-content-in-core-ediscovery.md) efter indhold i en core eDiscovery-sag, kan du hurtigt konfigurere søgningen til kun at søge efter de indholdsplaceringer, der er sat i venteposition i forbindelse med sagen.

Vælg indstillingen **Placeringer i venteposition** for at søge i alle de indholdsplaceringer, der er sat i venteposition. Hvis sagen indeholder flere eDiscovery-ventende elementer, søges der i indholdsplaceringer fra alle ventende elementer, når du vælger denne indstilling. Hvis en indholdsplacering blev placeret i en forespørgselsbaseret venteposition, vil der desuden kun blive søgt efter de elementer, der svarer til ventepositionsforespørgslen, når du kører søgningen. Med andre ord er det kun det indhold, der opfylder både kriterierne for venteposition og søgekriterierne, der returneres med søgeresultaterne. Hvis f.eks. en bruger blev placeret på forespørgselsbaseret sags hold, der bevarer elementer, der blev sendt eller oprettet før en bestemt dato, søges der kun i disse elementer. Dette opnås ved at oprette forbindelse til forespørgslen om venteposition og søgeforespørgslen af en **AND-operator** .

Her er nogle andre ting, du skal huske på, når du søger efter placeringer på eDiscovery-venteposition:

- Hvis en indholdsplacering er en del af flere ventepositioner i samme sag, kombineres forespørgslerne om  venteposition af OR-operatorerne, når du søger efter den pågældende indholdsplacering ved hjælp af indstillingen Alt sagsindhold. På samme måde gælder det, at hvis en indholdsplacering er en del af to forskellige ventepositioner, hvor den ene er forespørgselsbaseret, og den anden er et uendeligt hold (hvor alt indhold er sat i venteposition), så er alt indhold søgning på grund af det uendeligt hold.

- Hvis en søgning er konfigureret til at søge efter placeringer i venteposition, og du derefter ændrer et eDiscovery-venteposition i sagen (ved at tilføje eller fjerne en placering eller ændre en ventepositionsforespørgsel), opdateres søgekonfigurationen med disse ændringer. Du skal dog køre søgningen igen, når ventepositionen er ændret, for at opdatere søgeresultaterne.

- Hvis der er placeret flere eDiscovery-ventepositioner på et enkelt sted i en eDiscovery-sag, og du vælger at søge efter placeringer i venteposition, er det maksimale antal nøgleord for den pågældende søgeforespørgsel 500. Det skyldes, at søgningen kombinerer alle de forespørgselsbaserede ventende elementer ved hjælp af **operatoren ELLER** . Hvis der er mere end 500 nøgleord i forespørgslerne om kombineret venteposition og søgeforespørgslen, søges der i alt indhold i postkassen, ikke kun det indhold, der svarer til de forespørgselsbaserede sags hold.

- Hvis en eDiscovery-venteposition har statussen Til (Afventer **)**, kan du stadig søge efter placeringerne i venteposition, mens ventepositionen er aktiveret.

## <a name="preserve-content-in-microsoft-teams"></a>Bevar indhold i Microsoft Teams

Samtaler, der er en del af Microsoft Teams kanal, gemmes i den postkasse, der er knyttet til Microsoft-teamet. Ligeledes gemmes filer, som teammedlemmer deler i en kanal, på teamets websted SharePoint webstedet. Derfor skal du placere teampostkassen og SharePoint på eDiscovery-venteposition for at bevare samtaler og filer i en kanal.

Alternativt gemmes samtaler, der er en del af chatlisten i Teams (kaldet *1:1-chats* eller *1:N-gruppechats*), i postkasserne for de brugere, der deltager i chatten. Og filer, som brugere deler i chatsamtaler, gemmes i OneDrive for den bruger, der deler filen. Derfor skal du føje de enkelte brugerpostkasser og OneDrive-konti til et eDiscovery-venteposition for at bevare samtaler og filer på chatlisten. Det er en god ide at sætte postkasser i venteposition for medlemmer af et Microsoft-team ud over at sætte teampostkassen og webstedet i venteposition.

> [!NOTE]
> Hvis din organisation har en Exchange-hybridinstallation (eller din organisation synkroniserer en lokal Exchange-organisation med Office 365) og har aktiveret Microsoft Teams, kan lokale brugere bruge Teams-chatprogrammet og deltage i 1:1-chats og 1:N-gruppechats. Disse samtaler gemmes i et skybaseret lager, der er knyttet til en lokal bruger. Hvis en lokal bruger sættes i venteposition i et eDiscovery-lager, bevares Teams-chatindhold i det skybaserede lager. Du kan finde flere [oplysninger i Teams oplysninger om chatsamtaler for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

Du kan finde flere oplysninger om Teams indhold i [Sæt en Microsoft Teams eller et team i retslig venteposition](/MicrosoftTeams/legal-hold).

### <a name="preserve-card-content"></a>Bevar kortindhold

På samme måde gemmes kortindhold, der genereres af apps i Teams-kanaler, 1:1-chatsamtaler og 1:N-gruppechats, i postkasser og bevares, når en postkasse placeres i et eDiscovery-venteposition. Et *kort* er en brugergrænsefladebeholder til korte dele af indholdet. Kort kan have flere egenskaber og vedhæftede filer og kan indeholde knapper, der udløser korthandlinger. Du kan finde flere oplysninger under [Kort](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Ligesom andre Teams indhold, hvor kortindhold lagres, er det baseret på, hvor kortet blev brugt. Indhold til kort, der bruges Teams en anden kanal, gemmes i Teams gruppepostkassen. Kortindhold til 1:1- og 1xN-chats gemmes i chatdeltagernes postkasser.

### <a name="preserve-meeting-and-call-information"></a>Bevar møde- og opkaldsoplysninger

Oversigtsoplysninger om møder og opkald i en Teams kanal gemmes også i postkasser for brugere, der ringede til mødet eller opkaldet. Dette indhold bevares også, når et eDiscovery-hold placeres i brugerpostkasser.

### <a name="preserve-content-in-private-channels"></a>Bevar indhold i private kanaler

Fra og med februar 2020 har vi også aktiveret muligheden for at bevare indhold i private kanaler. Da private kanalchats gemmes i chatdeltagernes postkasser, vil en brugerpostkasse på eDiscovery-hold bevare private kanalchats. Og hvis en brugerpostkasse blev placeret i et eDiscovery-venteposition før februar 2020, vil ventepositionen nu automatisk gælde for private kanalmeddelelser, der er gemt i den pågældende postkasse. Bevaring af filer, der deles i private kanaler, understøttes også.

### <a name="preserve-wiki-content"></a>Bevar wikiindhold

Alle teams eller teamkanaler indeholder også en wiki til notetagning og samarbejde. Wiki-indholdet gemmes automatisk i en fil med .mht-format. Denne fil er gemt i Teams wikidatadokumentbiblioteket på teamets websted SharePoint websted. Du kan bevare wiki-indholdet ved at føje teamets websted SharePoint et eDiscovery-hold.

> [!NOTE]
> Muligheden for at bevare Wiki-indhold for en Team- eller teamkanal (når du placerer teamets SharePoint websted i venteposition) blev udgivet d. 22. juni 2017. Hvis et teamwebsted er i venteposition, bevares Wiki-indholdet fra denne dato. Men hvis et teamwebsted er i venteposition, og Wiki-indholdet blev slettet før 22. juni 2017, bevares wiki-indholdet ikke.

### <a name="office-365-groups"></a>Office 365 grupper

Teams er bygget på Office 365 grupper. Derfor er det at placere Office 365 grupper i eDiscovery-venteposition på samme måde Teams indhold i venteposition.

Vær opmærksom på følgende, når du placerer både Teams og Office 365 Grupper i et eDiscovery-venteposition:

- Som beskrevet tidligere skal du for at placere indhold i Teams og Office 365 Grupper i venteposition skal du angive den postkasse og det SharePoint-websted, der er knyttet til en gruppe eller et team.

- Kør **Get-UnifiedGroup-cmdlet'en** [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få vist egenskaber for Teams og Office 365 Groups. Dette er en god måde at få URL-adressen til det websted, der er knyttet til en gruppe eller Office 365 gruppe. Følgende kommando viser f.eks. de valgte egenskaber for Office 365 gruppe med navnet Senior Leadership Team:

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > For at køre cmdlet'en **Get-UnifiedGroup** skal du være tildelt rollen View-Only Modtagere i Exchange Online eller være medlem af en rollegruppe, der er tildelt rollen View-Only Modtagere. 
  
- Når der søges i en brugers postkasse, søges der ikke i teams eller Office 365-grupper, som brugeren er medlem af. På samme måde er det kun gruppepostkassen og gruppens websted, der er sat i venteposition, når du placerer et Team- eller Office 365-gruppe på eDiscovery-venteposition. Postkasser og websteder OneDrive for Business gruppemedlemmer sættes ikke i venteposition, medmindre du eksplicit føjer dem til eDiscovery-ventepositionen. Så hvis du af juridiske årsager skal placere en Team- eller Office 365-gruppe i venteposition, skal du overveje at tilføje postkasser og OneDrive-konti for team- eller gruppemedlemmer i samme venteposition.

- Hvis du vil have en liste over medlemmer af en team- eller Office 365-gruppe, kan du få vist egenskaberne <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> på siden Grupper Microsoft 365 Administration. Alternativt kan du køre følgende kommando i Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > For at køre cmdlet'en **Get-UnifiedGroupLinks** skal du være tildelt rollen View-Only-modtagere i Exchange Online eller være medlem af en rollegruppe, der er tildelt rollen View-Only Modtagere.

## <a name="preserve-content-in-onedrive-accounts"></a>Bevar indhold OneDrive konti

Hvis du vil indsamle en liste over URL-adresserne til OneDrive for Business-webstederne i organisationen, så du kan føje dem til en venteposition eller søge i forbindelse med en eDiscovery-sag, skal du se Oprette en liste [over alle OneDrive-placeringer](/onedrive/list-onedrive-urls) i organisationen. Scriptet i denne artikel opretter en tekstfil, der indeholder en liste over OneDrive websteder i organisationen. For at køre dette script skal du installere og bruge SharePoint Online Management Shell. Sørg for at føje URL-adressen til organisationens domæne for Mit websted til hver af de OneDrive, du vil søge efter. Dette er det domæne, der indeholder alle dine OneDrive, f.eks. `https://contoso-my.sharepoint.com`. Her er et eksempel på en URL-adresse til en brugers websted OneDrive: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> URL-adressen til en brugers konto OneDrive brugerens hovednavn (UPN) (f.eks. `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Hvis det sjældent er tilfældet, at en persons UPN ændres, ændres personens URL-OneDrive til at inkorporere det nye UPN. Hvis en brugers OneDrive-konto er en del af en eDiscovery-venteposition, gammel, og brugerens UPN ændres, skal du opdatere ventepositionen, og du er nødt til at opdatere ventepositionen og tilføje brugerens nye URL-adresse til OneDrive og fjerne den gamle. Du kan finde flere oplysninger [under Sådan påvirker UPN OneDrive URL-adressen](/onedrive/upn-changes).

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>Fjerne indholdsplaceringer fra en eDiscovery-venteposition

Når en postkasse, SharePoint-websted eller OneDrive-konto er fjernet fra en eDiscovery-venteposition, anvendes *der en forsinkelses* venteposition. Det betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre data i at blive slettet permanent (slettet) fra en indholdsplacering. Dette giver administratorer mulighed for at søge efter eller gendanne indhold, der vil blive slettet, når en eDiscovery-venteposition fjernes. Oplysningerne om, hvordan forsinkelses hold fungerer for postkasser og websteder, er forskellige.

- **Postkasser:** En forsinkelse er placeret i en postkasse, næste gang den administrerede mappeassistent behandler postkassen og registrerer, at et eDiscovery-hold er blevet fjernet. Specifikt anvendes en forsinkelse i venteposition på en postkasse, når Den administrerede mappeassistent indstiller en af følgende postkasseegenskaber til **Sand**:

   - **ForsinkelseHoldApplied:** Denne egenskab gælder for mailrelateret indhold (der genereres af personer, Outlook Outlook på internettet), der er gemt i en brugers postkasse.

   - **DelayReleaseHoldApplied:** Denne egenskab gælder for skybaseret indhold (genereres af ikke-Outlook-apps som Microsoft Teams, Microsoft Forms og Microsoft Yammer), der er gemt i en brugers postkasse. Skydata, der genereres af en Microsoft-app, gemmes typisk i en skjult mappe i en brugers postkasse.

   Når en forsinkelse er sat i venteposition i postkassen (når en af de forrige egenskaber er angivet til **Sand), betragtes** postkassen stadig som værende i venteposition i ubegrænset tid, som hvis postkassen var i retslig venteposition. Efter 30 dage udløber forsinkelsen, og Microsoft 365 forsøger automatisk at fjerne forsinkelses ventepositionen (ved at indstille egenskaben DelayHoldApplied eller DelayReleaseHoldApplied til **Falsk**), så ventepositionen fjernes. Når en af disse egenskaber er angivet til **Falsk, fjernes** de tilsvarende elementer, der er markeret til fjernelse, næste gang postkassen behandles af den administrerede mappeassistent.

   Få mere at vide under [Administration af postkasser i venteposition](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **SharePoint- og OneDrive-websteder:** Alt SharePoint- eller OneDrive-indhold, der bevares i biblioteket til opbevaring af dokumenter, slettes ikke i perioden på 30 dage, efter at et websted er blevet fjernet fra et eDiscovery-hold. Dette svarer til, hvad der sker, når et websted frigives fra en opbevaringspolitik. Derudover kan du ikke slette dette indhold manuelt i biblioteket til opbevaring af dokumenter inden for perioden på 30 dage. 

   Få mere at vide under [Frigivelse af en politik til opbevaring](retention.md#releasing-a-policy-for-retention).

Der anvendes også forsinkelse i venteposition på indholdsplaceringer i venteposition, når du lukker en Core eDiscovery-sag, fordi ventepositioner deaktiveres, når en sag lukkes. Du kan finde flere oplysninger om at lukke en sag [under Lukke, genåbne og slette en central eDiscovery-sag](close-reopen-delete-core-ediscovery-cases.md).

## <a name="ediscovery-hold-limits"></a>Begrænsninger for eDiscovery-venteposition

I følgende tabel vises begrænsningerne for eDiscovery-sager og ventende sager.

  | Beskrivelse af grænse | Grænse |
  |:-----|:-----|
  |Maksimale antal sager for en organisation.  <br/> |Ingen grænse  <br/> |
  |Maksimale antal eDiscovery-ventepositionspolitikker for en organisation. Denne grænse omfatter det samlede antal ventepositionspolitikker i Core eDiscovery og Advanced eDiscovery-sager.  <br/> |10.0001<sup></sup>  <br/> |
  |Maksimale antal postkasser i et enkelt eDiscovery-venteposition. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper.  <br/> |1,000  <br/> |
  |Maksimale antal websteder i en enkelt eDiscovery-venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint-websteder og de websteder, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper.  <br/> |100  <br/> |
  |Det maksimale antal sager, der vises på eDiscovery-startsiden, og det maksimale antal elementer, der vises på fanerne Vente hold, Søgninger og Eksportér i en sag.  |1.0002<sup></sup>|
  |||

   > [!NOTE]
   > <sup>1</sup> Når du sætter mere end 1.000 postkasser eller 100 websteder i venteposition i en enkelt politik for venteposition, skalerer systemet automatisk ventepositionen efter behov. Det betyder, at systemet automatisk føjer dataplaceringer til flere politikker for venteposition i stedet for at føje dem til en enkelt politik for venteposition. Men grænsen på 10.000 politikker for venteposition for hver organisation gælder stadig.
   >
   > <sup>2</sup> Hvis du vil have vist en liste over mere end 1.000 sager, ventepositioner, søgninger eller eksporter, kan du bruge den tilsvarende Security & Compliance PowerShell-cmdlet:
   >
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)
