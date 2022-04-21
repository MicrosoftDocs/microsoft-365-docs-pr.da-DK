---
title: Opret eDiscovery-ventepositioner i en eDiscovery-sag (Standard)
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
description: Du kan oprette en venteposition, der er knyttet til en eDiscovery-sag (Standard), i Microsoft 365 for at bevare indhold, der er relevant for en undersøgelse eller en juridisk sag.
ms.openlocfilehash: 87a75923ccc270e7b9802ae5d366dd2930a84d82
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001230"
---
# <a name="create-an-ediscovery-hold"></a>Opret en eDiscovery-venteposition

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge en Microsoft Purview eDiscovery-sag (Standard) til at oprette ventepositioner for at bevare indhold, der kan være relevant for sagen. Du kan placere en venteposition på de Exchange postkasser og OneDrive for Business konti for personer, du undersøger i sagen. Du kan også placere en venteposition på de postkasser og websteder, der er knyttet til Microsoft Teams, Office 365 grupper og Yammer grupper. Når du placerer indholdsplaceringer i venteposition, bevares indholdet, indtil du fjerner indholdsplaceringen fra ventepositionen, eller indtil du sletter ventepositionen.

Når du har oprettet en eDiscovery-venteposition, kan det tage op til 24 timer, før ventepositionen træder i kraft.

Når du opretter en venteposition, har du følgende muligheder for at tilpasse omfanget af det indhold, der bevares på de angivne indholdsplaceringer:
  
- Opret en uendelig venteposition, hvor alt indhold på de angivne placeringer sættes i venteposition. Du kan også oprette en forespørgselsbaseret venteposition, hvor det kun er indholdet på de angivne placeringer, der svarer til en søgeforespørgsel, der sættes i venteposition.

- Angiv et datointerval for kun at bevare det indhold, der blev sendt, modtaget eller oprettet inden for dette datointerval. Du kan også opbevare alt indhold på de angivne placeringer, uanset hvornår det blev sendt, modtaget eller oprettet.
  
## <a name="how-to-create-an-ediscovery-hold"></a>Sådan opretter du en eDiscovery-venteposition

Sådan opretter du en eDiscovery-venteposition, der er knyttet til en eDiscovery-sag (Standard):
  
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a> , og log på med legitimationsoplysningerne for den brugerkonto, der er tildelt de relevante eDiscovery-tilladelser.

2. Klik på **Vis alle** i navigationsruden til venstre, og klik derefter på **eDiscovery > Core**.

3. Klik på navnet på den sag, du vil oprette venteposition for, på siden **eDiscovery (Standard** ).

4. Klik **på fanen** **Hold** på startsiden for sagen.
  
5. Klik på **Opret** på siden **Venteposition**.

6. Angiv et navn til ventepositionen på siden **Navngiv din venteposition** , og tilføj en valgfri beskrivelse, og klik derefter på **Næste**. Navnet på ventepositionen skal være entydigt i din organisation.

7. Vælg de **indholdsplaceringer** , du vil placere i venteposition, på siden Guiden Vælg placeringer. Du kan placere postkasser, websteder og offentlige mapper i venteposition.

    ![Vælg de indholdsplaceringer, der skal placeres i venteposition.](../media/eDiscoveryHoldLocations.png)
  
   1. **Exchange postkasser**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg brugere, grupper eller teams** for at angive de postkasser, der skal sættes i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition på gruppemedlemmernes postkasser) til at placere dem i venteposition. Du kan også placere en venteposition på den tilknyttede postkasse for et Microsoft-team, Office 365-gruppe og Yammer-gruppe. Du kan finde flere oplysninger om de programdata, der bevares, når en postkasse er sat i venteposition, under Indhold, der er [gemt i postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg websteder** for at angive, SharePoint websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til det SharePoint websted for et Microsoft-team, en Office 365-gruppe eller en Yammer gruppe.
  
   3. **Exchange offentlige mapper**: Indstil til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online-organisation i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-knappen være slået fra, hvis du ikke vil sætte offentlige mapper i venteposition.

   > [!IMPORTANT]
   > Når du føjer Exchange postkasser eller SharePoint websteder til venteposition, skal du eksplicit føje mindst én indholdsplacering til ventepositionen. Hvis du med andre ord angiver til/fra-knappen til **Til** for postkasser eller websteder, skal du vælge bestemte postkasser eller websteder, der skal føjes til ventepositionen. Ellers oprettes eDiscovery-ventepositionen, men der føjes ingen postkasser eller websteder til ventepositionen, og statistikkerne viser, at der ikke er nogen indholdsplaceringer eller elementer i venteposition.

8. Når du er færdig med at føje placeringer til ventepositionen, skal du klikke på **Næste**.

9. Hvis du vil oprette en forespørgselsbaseret venteposition ved hjælp af nøgleord eller betingelser, skal du udføre følgende trin. Klik på **Næste** for at bevare alt indhold på de angivne indholdsplaceringer.

    ![Opret en forespørgselsbaseret venteposition med nøgleord og betingelser.](../media/eDiscoveryHoldQuery.png)
  
    1. I feltet under **Nøgleord** skal du skrive en forespørgsel for kun at bevare det indhold, der svarer til forespørgselskriterierne. Du kan angive nøgleord, egenskaber for mailmeddelelser eller webstedsegenskaber, f.eks. filnavne. Du kan også bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks **. AND**, **OR** eller **NOT**.

    2. Klik på **Tilføj betingelse** for at tilføje en eller flere betingelser for at indsnævre forespørgslen for ventepositionen. Hver betingelse føjer en delsætning til den KQL-søgeforespørgsel, der oprettes og køres, når du opretter ventepositionen. Du kan f.eks. angive et datointerval, så mail- eller webstedsdokumenter, der blev oprettet inden for det datointerval, bevares. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i feltet **Nøgleord** ) og andre betingelser af operatoren **AND** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og den betingelse, der skal bevares.

    Du kan finde flere oplysninger om oprettelse af en søgeforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

10. Når du har konfigureret en forespørgselsbaseret venteposition, skal du klikke på **Næste**.

11. Gennemse dine indstillinger (og rediger dem, hvis det er nødvendigt), og klik derefter på **Send**.

> [!NOTE]
> Når du opretter en forespørgselsbaseret venteposition, sættes alt indhold fra valgte placeringer i første omgang i venteposition. Efterfølgende ryddes alt indhold, der ikke stemmer overens med den angivne forespørgsel, fra ventepositionen hver 7. til 14. dag. En forespørgselsbaseret venteposition rydder dog ikke indhold, hvis der anvendes mere end fem ventepositioner af nogen type på en indholdsplacering, eller hvis et element har problemer med indeksering.

## <a name="query-based-holds-placed-on-sites"></a>Forespørgselsbaserede ventepositioner, der er placeret på websteder

Vær opmærksom på følgende ting, når du placerer en forespørgselsbaseret eDiscovery-venteposition på dokumenter, der er placeret på SharePoint websteder:

- En forespørgselsbaseret venteposition bevarer alle dokumenter på et websted i en kort periode, efter at de er slettet. Det betyder, at når et dokument slettes, flyttes det til biblioteket bevarelsesposition, selvom det ikke stemmer overens med kriterierne for den forespørgselsbaserede venteposition. Slettede dokumenter, der ikke svarer til en forespørgselsbaseret venteposition, fjernes dog af et timerjob, der behandler biblioteket bevarelsesventeposition. Timerjobbet kører jævnligt og sammenligner alle dokumenter i biblioteket bevarelsesposition med dine forespørgselsbaserede eDiscovery-ventepositioner (og andre typer ventepositioner og opbevaringspolitikker). Timerjobbet sletter de dokumenter, der ikke stemmer overens med en forespørgselsbaseret venteposition, og bevarer de dokumenter, der gør det.

- Forespørgselsbaserede ventepositioner bør ikke bruges til at udføre målrettet bevarelse, f.eks. bevare dokumenter i en bestemt mappe eller et bestemt websted eller ved hjælp af andre placeringsbaserede kriterier for bevarelse. Det kan have utilsigtede resultater. Vi anbefaler, at du bruger kriterier, der ikke er baseret på placering, f.eks. nøgleord, datointervaller eller andre dokumentegenskaber, for at bevare webstedsdokumenter.

## <a name="ediscovery-hold-statistics"></a>Statistik for eDiscovery-venteposition

Når du har oprettet en eDiscovery-venteposition, vises oplysninger om den nye venteposition på pop op-siden for den valgte venteposition. Disse oplysninger omfatter antallet af postkasser og websteder, der er i venteposition, og statistik over det indhold, der blev sat i venteposition, f.eks. det samlede antal elementer og størrelsen af elementer, der er sat i venteposition, og den sidste gang statistik for venteposition blev beregnet. Disse statistik for bevarelse hjælper dig med at identificere mængden af indhold, der er relateret til sagen, bevares.
  
![Statistik for venteposition.](../media/eDiscoveryHoldStatistics.png)
  
Vær opmærksom på følgende ting i forbindelse med statistik for eDiscovery-venteposition:
  
- Det samlede antal elementer i venteposition angiver antallet af elementer fra alle indholdskilder, der er sat i venteposition. Hvis du har oprettet en forespørgselsbaseret venteposition, angiver denne statistik antallet af elementer, der svarer til forespørgslen.

- Antallet af elementer i venteposition omfatter også ikke-indekserede elementer, der findes på indholdsplaceringerne. Hvis du opretter en forespørgselsbaseret venteposition, sættes alle ikke-indekserede elementer på indholdsplaceringerne i venteposition. Dette omfatter ikke-indekserede elementer, der ikke svarer til søgekriterierne for en forespørgselsbaseret venteposition og ikke-indekserede elementer, der kan falde uden for en datoområdebetingelse. Dette er anderledes end det, der sker, når du kører en søgning, hvor ikke-indekserede elementer, der ikke stemmer overens med søgeforespørgslen eller er udeladt af en datointervalbetingelse, ikke er inkluderet i søgeresultaterne. Du kan få flere oplysninger om ikke-indekserede elementer under [Delvist indekserede elementer](partially-indexed-items-in-content-search.md).

- Du kan få den seneste statistik for venteposition ved at klikke på **Opdater statistik** for at køre et søgeestimat, der beregner det aktuelle antal elementer i venteposition.

- Det er normalt, at antallet af elementer i venteposition øges over tid, fordi brugere, hvis postkasse eller websted er i venteposition, normalt sender eller modtager en ny mail og opretter nye dokumenter i SharePoint og OneDrive.

- Hvis en Exchange postkasse, SharePoint websted eller OneDrive konto flyttes til et andet område i et multi-geo-miljø, medtages statistikkerne for det pågældende websted ikke i statistik for bevarelse. Men indholdet på disse placeringer bevares stadig. Hvis en postkasse eller et websted flyttes til et andet område, opdateres den SMTP-adresse eller URL-adresse, der vises i ventepositionen, heller ikke automatisk. Du skal redigere ventepositionen og opdatere URL-adressen eller SMTP-adressen, så indholdsplaceringerne igen medtages i statistik for venteposition

## <a name="search-locations-on-ediscovery-hold"></a>Søg på placeringer i eDiscovery-venteposition

Når du [søger efter indhold](search-for-content-in-core-ediscovery.md) i en eDiscovery-sag (Standard), kan du hurtigt konfigurere søgningen til kun at søge efter de indholdsplaceringer, der er placeret i en venteposition, der er knyttet til sagen.

Vælg indstillingen **Placeringer i venteposition** for at søge efter alle de indholdsplaceringer, der er sat i venteposition. Hvis sagen indeholder flere eDiscovery-ventepositioner, søges der efter indholdsplaceringer fra alle ventepositioner, når du vælger denne indstilling. Hvis en indholdsplacering blev placeret i en forespørgselsbaseret venteposition, er det desuden kun de elementer, der svarer til ventepositionsforespørgslen, der søges i, når du kører søgningen. Det er med andre ord kun det indhold, der matcher både ventepositionskriterierne og søgekriterierne, der returneres sammen med søgeresultaterne. Hvis en bruger f.eks. blev placeret i forespørgselsbaseret sagsposition, der bevarer elementer, der blev sendt eller oprettet før en bestemt dato, ville der kun blive søgt i disse elementer. Dette opnås ved at forbinde forespørgslen om sag venteposition og søgeforespørgslen af en **AND-operator** .

Her er nogle andre ting, du skal være opmærksom på, når du søger efter placeringer i eDiscovery-venteposition:

- Hvis en indholdsplacering er en del af flere ventepositioner i det samme tilfælde, kombineres ventepositionsforespørgslerne af **OPERATOR'en** , når du søger på denne indholdsplacering ved hjælp af indstillingen alt sagsindhold. Hvis en indholdsplacering på samme måde er en del af to forskellige ventepositioner, hvor den ene er forespørgselsbaseret, og den anden er en uendelig venteposition (hvor alt indhold er sat i venteposition), søger alt indhold på grund af den uendelige venteposition.

- Hvis en søgning er konfigureret til at søge på placeringer i venteposition, og du derefter ændrer en eDiscovery-venteposition i tilfælde (ved at tilføje eller fjerne en placering eller ændre en ventepositionsforespørgsel), opdateres søgekonfigurationen med disse ændringer. Du skal dog køre søgningen igen, når ventepositionen er ændret, for at opdatere søgeresultaterne.

- Hvis flere eDiscovery-ventepositioner placeres på en enkelt placering i en eDiscovery-sag, og du vælger at søge på placeringer i venteposition, er det maksimale antal nøgleord for den pågældende søgeforespørgsel 500. Det skyldes, at søgningen kombinerer alle de forespørgselsbaserede ventepositioner ved hjælp af operatoren **OR** . Hvis der er mere end 500 nøgleord i de kombinerede ventepositionsforespørgsler og søgeforespørgslen, søges der i alt indhold i postkassen, ikke kun det indhold, der stemmer overens med de forespørgselsbaserede sagsbeholdninger.

- Hvis en eDiscovery-venteposition har statussen **On (Pending),** kan du stadig søge i de placeringer, der er i venteposition, mens ventepositionen er aktiveret.

## <a name="preserve-content-in-microsoft-teams"></a>Bevar indhold i Microsoft Teams

Samtaler, der er en del af en Microsoft Teams kanal, gemmes i den postkasse, der er knyttet til Microsoft-teamet. På samme måde gemmes filer, som teammedlemmer deler i en kanal, på teamets SharePoint websted. Derfor skal du placere gruppepostkassen og SharePoint websted i eDiscovery-venteposition for at bevare samtaler og filer i en kanal.

Alternativt gemmes samtaler, der er en del af chatlisten i Teams (kaldet *1:1 chats* eller *1:N gruppechats*), i postkasserne for de brugere, der deltager i chatten. Og filer, som brugerne deler i chatsamtaler, gemmes på den OneDrive konto for den bruger, der deler filen. Derfor skal du føje de enkelte brugerpostkasser og OneDrive konti til en eDiscovery-venteposition for at bevare samtaler og filer på chatlisten. Det er en god idé at sætte en venteposition på postkasserne for medlemmer af et Microsoft-team ud over at sætte gruppepostkassen og webstedet i venteposition.

> [!NOTE]
> Hvis din organisation har en Exchange hybridinstallation (eller din organisation synkroniserer en Exchange organisation i det lokale miljø med Office 365) og har aktiveret Microsoft Teams, kan brugere i det lokale miljø bruge Teams chatprogrammet og deltage i 1:1-chats og 1:N-gruppechats. Disse samtaler gemmes i et cloudbaseret lager, der er knyttet til en bruger i det lokale miljø. Hvis en bruger i det lokale miljø er sat i eDiscovery-venteposition, bevares det Teams chatindhold i det skybaserede lager. Du kan finde flere oplysninger under [Søg efter Teams chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

Du kan finde flere oplysninger om bevarelse af Teams indhold under [Placer en Microsoft Teams bruger eller et team i juridisk venteposition](/MicrosoftTeams/legal-hold).

### <a name="preserve-card-content"></a>Bevar kortindhold

På samme måde gemmes kortindhold, der genereres af apps i Teams kanaler, 1:1 chats og 1:N-gruppechat, i postkasser og bevares, når en postkasse placeres i eDiscovery-venteposition. Et *kort* er en brugergrænsefladeobjektbeholder til korte indholdselementer. Kort kan have flere egenskaber og vedhæftede filer og kan indeholde knapper, der udløser korthandlinger. Du kan få flere oplysninger under [Kort](/microsoftteams/platform/task-modules-and-cards/what-are-cards). På samme måde som med andet Teams indhold, hvor kortindholdet gemmes, er det baseret på, hvor kortet blev brugt. Indhold for kort, der bruges i en Teams kanal, gemmes i Teams gruppepostkasse. Kortindhold for 1:1- og 1xN-chats gemmes i chatdeltagernes postkasser.

### <a name="preserve-meeting-and-call-information"></a>Bevar møde- og opkaldsoplysninger

Oversigtsoplysninger for møder og opkald i en Teams kanal gemmes også i postkasserne for de brugere, der ringede til mødet eller opkaldet. Dette indhold bevares også, når en eDiscovery-venteposition er placeret i brugerpostkasser.

### <a name="preserve-content-in-private-channels"></a>Bevar indhold i private kanaler

Fra og med februar 2020 har vi også aktiveret muligheden for at bevare indhold i private kanaler. Da chats med private kanaler gemmes i chatdeltagernes postkasser, bevares chats for private kanaler, når en brugerpostkasse placeres i eDiscovery-venteposition. Hvis en brugerpostkasse blev sat i eDiscovery-venteposition før februar 2020, gælder ventepositionen nu automatisk for private kanalmeddelelser, der er gemt i den pågældende postkasse. Bevarelse af filer, der deles i private kanaler, understøttes også.

### <a name="preserve-wiki-content"></a>Bevar wikiindhold

Alle team- eller teamkanaler indeholder også en wiki til notetagning og samarbejde. Wikiindholdet gemmes automatisk i en fil med et .mht-format. Denne fil er gemt i dokumentbiblioteket Teams wikidata på teamets SharePoint websted. Du kan bevare wikiindholdet ved at føje teamets SharePoint websted til eDiscovery-venteposition.

> [!NOTE]
> Muligheden for at bevare wikiindhold for en team- eller teamkanal (når du placerer teamets SharePoint websted i venteposition) blev udgivet den 22. juni 2017. Hvis et teamwebsted er i venteposition, bevares wikiindholdet fra den pågældende dato. Men hvis et teamwebsted er i venteposition, og wikiindholdet blev slettet før den 22. juni 2017, blev wikiindholdet ikke bevaret.

### <a name="office-365-groups"></a>Office 365 grupper

Teams er baseret på Office 365 grupper. Derfor er det det samme at placere Office 365 grupper i eDiscovery-venteposition Teams indhold i venteposition.

Vær opmærksom på følgende ting, når du placerer både Teams og Office 365 grupper i eDiscovery-venteposition:

- Som tidligere forklaret skal du angive postkassen og SharePoint websted, der er knyttet til en gruppe eller et team, for at placere indhold i Teams og Office 365 grupper i venteposition.

- Kør **Get-UnifiedGroup-cmdlet'en** i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få vist egenskaber for Teams og Office 365 Grupper. Dette er en god måde at få URL-adressen til det websted, der er knyttet til et team eller en Office 365 gruppe. Følgende kommando viser f.eks. de valgte egenskaber for en Office 365 gruppe med navnet Senior Leadership Team:

    ```text
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl

    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Hvis du vil køre **Cmdlet'en Get-UnifiedGroup**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har fået tildelt rollen View-Only modtagere. 
  
- Når der søges i en brugers postkasse, bliver der ikke søgt i team eller Office 365 gruppe, som brugeren er medlem af. På samme måde er det kun gruppepostkassen og gruppewebstedet, der sættes i venteposition, når du placerer en gruppe eller Office 365 gruppe i eDiscovery-venteposition. Postkasserne og OneDrive for Business websteder for gruppemedlemmer sættes ikke i venteposition, medmindre du udtrykkeligt føjer dem til eDiscovery-ventepositionen. Så hvis du af juridiske årsager skal sætte et team eller en Office 365 gruppe i venteposition, kan du overveje at tilføje postkasserne og OneDrive konti for team- eller gruppemedlemmer i samme venteposition.

- Hvis du vil hente en liste over medlemmerne af et team eller en Office 365 gruppe, kan du få vist egenskaberne på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a> i Microsoft 365 Administration. Du kan også køre følgende kommando i Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Hvis du vil køre cmdlet'en **Get-UnifiedGroupLinks**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har tildelt rollen View-Only modtagere.

## <a name="preserve-content-in-onedrive-accounts"></a>Bevar indhold i OneDrive konti

Hvis du vil indsamle en liste over URL-adresserne for de OneDrive for Business websteder i din organisation, så du kan føje dem til en venteposition eller søgning, der er knyttet til en eDiscovery-sag, skal du se [Opret en liste over alle OneDrive placeringer i din organisation](/onedrive/list-onedrive-urls). Scriptet i denne artikel opretter en tekstfil, der indeholder en liste over alle OneDrive websteder i din organisation. Hvis du vil køre dette script, skal du installere og bruge SharePoint Online Management Shell. Sørg for at føje URL-adressen til organisationens MySite-domæne til hvert OneDrive websted, du vil søge på. Dette er det domæne, der indeholder alle dine OneDrive, `https://contoso-my.sharepoint.com`f.eks. . Her er et eksempel på en URL-adresse til en brugers OneDrive websted: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

> [!IMPORTANT]
> URL-adressen til en brugers OneDrive-konto indeholder brugerens hovednavn (UPN) (f.eks. `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). I det sjældne tilfælde, at en persons UPN ændres, ændres vedkommendes OneDrive URL-adresse også for at inkorporere det nye UPN. Hvis en brugers OneDrive konto er en del af en eDiscovery-venteposition, gammel, og vedkommendes UPN ændres, skal du opdatere ventepositionen, og du skal opdatere ventepositionen og tilføje brugerens nye ONEDRIVE URL-adresse og fjerne den gamle. Du kan få flere oplysninger under [Sådan påvirker UPN-ændringer OneDrive URL-adressen](/onedrive/upn-changes).

## <a name="removing-content-locations-from-an-ediscovery-hold"></a>Fjerner indholdsplaceringer fra en eDiscovery-venteposition

Når en postkasse, SharePoint websted eller OneDrive konto er fjernet fra eDiscovery-venteposition, anvendes der en *forsinkelse i venteposition*. Det betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre, at data slettes permanent (fjernes) fra en indholdsplacering. Dette giver administratorer mulighed for at søge efter eller gendanne indhold, der fjernes, når en eDiscovery-venteposition fjernes. Detaljerne om, hvordan forsinkelsesventepositionen fungerer for postkasser og websteder, er forskellige.

- **Postkasser:** Der placeres en forsinkelse i en postkasse, næste gang Assistent til administreret mappe behandler postkassen og registrerer, at en eDiscovery-venteposition er fjernet. Der anvendes specifikt forsinkelse på en postkasse, når Assistent til administreret mappe angiver en af følgende postkasseegenskaber til **Sand**:

   - **DelayHoldApplied:** Denne egenskab gælder for mailrelateret indhold (genereret af personer, der bruger Outlook og Outlook på internettet), der er gemt i en brugers postkasse.

   - **DelayReleaseHoldApplied:** Denne egenskab gælder for skybaseret indhold (genereret af apps, der ikke er Outlook, f.eks. Microsoft Teams, Microsoft Forms og Microsoft Yammer), der er gemt i en brugers postkasse. Clouddata, der genereres af en Microsoft-app, gemmes typisk i en skjult mappe i en brugers postkasse.

   Når der er placeret en forsinkelse i postkassen (når en af de forrige egenskaber er angivet til **Sand**), anses postkassen stadig for at være i venteposition i ubegrænset varighed, som om postkassen var i procesretlig venteposition. Efter 30 dage udløber forsinkelsesventetiden, og Microsoft 365 forsøger automatisk at fjerne forsinkelsesventetiden (ved at angive egenskaben DelayHoldApplied eller DelayReleaseHoldApplied til **Falsk**), så ventepositionen fjernes. Når en af disse egenskaber er angivet til **Falsk**, fjernes de tilsvarende elementer, der er markeret til fjernelse, næste gang postkassen behandles af Assistent til administrerede mapper.

   Du kan få flere oplysninger under [Administration af postkasser i forsinkelsesventeposition](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

- **SharePoint og OneDrive websteder:** Alt SharePoint eller OneDrive indhold, der bevares i biblioteket bevarelsesposition, slettes ikke i løbet af 30-dages forsinkelsesperioden, efter at et websted er fjernet fra eDiscovery-venteposition. Dette svarer til det, der sker, når et websted frigives fra en opbevaringspolitik. Derudover kan du ikke manuelt slette dette indhold i biblioteket bevarelsesventetid i løbet af den 30-dages forsinkelsesperiode. 

   Du kan få flere oplysninger under [Frigivelse af en politik til opbevaring](retention.md#releasing-a-policy-for-retention).

Der anvendes også forsinkelse på indholdsplaceringer i venteposition, når du lukker en eDiscovery(Standard)-sag, fordi ventepositioner er slået fra, når en sag lukkes. Du kan finde flere oplysninger om lukning af en sag under [Luk, genåbn og slet en eDiscovery-sag (Standard).](close-reopen-delete-core-ediscovery-cases.md)

## <a name="ediscovery-hold-limits"></a>Grænser for eDiscovery-venteposition

I følgende tabel vises grænserne for eDiscovery-sager og ventepositioner for sager.

  | Beskrivelse af grænse | Grænse |
  |:-----|:-----|
  |Maksimalt antal sager for en organisation.  <br/> |Ingen grænse  <br/> |
  |Det maksimale antal politikker for eDiscovery-venteposition for en organisation. Denne grænse omfatter det samlede antal ventepositionspolitikker i sager med eDiscovery (Standard) og eDiscovery (Premium).  <br/> |10.0001<sup></sup>  <br/> |
  |Det maksimale antal postkasser i en enkelt eDiscovery-venteposition. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer Grupper.  <br/> |1,000  <br/> |
  |Det maksimale antal websteder i en enkelt eDiscovery-venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint websteder og de websteder, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer grupper.  <br/> |100  <br/> |
  |Det maksimale antal sager, der vises på eDiscovery-startsiden, og det maksimale antal elementer, der vises på fanerne Ventepositioner, Søgninger og Eksportér i en sag.  |1.0001<sup></sup>|

   > [!NOTE]
   > <sup>1</sup> Hvis du vil have vist en liste over mere end 1.000 sager, ventepositioner, søgninger eller eksporter, kan du bruge den tilsvarende PowerShell-cmdlet til sikkerhed & overholdelse:
   >
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)
