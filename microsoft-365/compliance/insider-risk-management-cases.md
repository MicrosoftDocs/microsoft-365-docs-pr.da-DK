---
title: Insider-sager om risikostyring
description: Få mere at vide om insider-sager i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: ab0eb6c9f7ecfbc51de4857d708f1fa34bd3f515
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587338"
---
# <a name="insider-risk-management-cases"></a>Insider-sager om risikostyring

Sager er kernen i insider-risikostyring og giver dig mulighed for at undersøge og reagere dybt på problemer, der genereres af risikoindikatorer defineret i dine politikker. Der oprettes manuelt tilfælde ud fra beskeder i situationer, hvor der er behov for yderligere handling for at løse et kompatibilitetsrelateret problem for en bruger. Hver sag er begrænset til en enkelt bruger, og flere beskeder for brugeren kan føjes til en eksisterende sag eller til en ny sag.

Når du har undersøgt detaljerne i en sag, kan du gøre noget ved at:

- sende brugeren en meddelelse
- løsning af sagen som tilsnende
- dele sagen med din ServiceNow-forekomst eller med en mailmodtager
- eskalere sagen til en Advanced eDiscovery undersøgelse

Se videoen [insider-risikostyringsundersøgelse og -eskalering](https://www.youtube.com/watch?v=UONUSmkRC8s) for at få et overblik over, hvordan sager undersøges og administreres i Insider Risk Management.

## <a name="cases-dashboard"></a>Dashboardet Sager

Med dashboardet Insider Risk **Management Cases** kan du få vist og handle på sager. Hver rapportwidget på dashboardet viser oplysninger for de seneste 30 dage.

- **Aktive sager**: Det samlede antal aktive sager, der undersøges.
- **Sager over de seneste 30** dage: Det samlede antal oprettede sager sorteret efter *statussen* *Aktiv og* Lukket.
- **Statistik**: Gennemsnitlig tid for aktive sager, der er angivet i timer, dage eller måneder.

Sagskøen viser alle aktive og lukkede sager for organisationen ud over den aktuelle status for følgende sagsattributter:

- **Sagsnavn**: Navnet på sagen, der er defineret, når en besked bekræftes, og sagen oprettes.  
- **Status**: Status for sagen, enten *Aktiv* eller *Lukket*.
- **Bruger**: Brugeren af sagen. Hvis anonymisering for brugernavne er aktiveret, vises anonymiserede oplysninger.
- **Tidstilfælde åbnet**: Det tidspunkt, der er gået, siden sagen blev åbnet.
- **Beskeder om samlet politik**: Antallet af politik matches, der er medtaget i sagen. Dette tal kan øges, hvis der føjes nye beskeder til sagen.
- **Sag sidst opdateret**: Det tidspunkt, der er gået, siden der er blevet tilføjet en sagsnote eller ændring i sagstilstanden.
- **Senest opdateret af**: Navnet på insider-analytikeren for risikostyring eller den, der senest har opdateret sagen.

![Dashboard for Insider-risikostyringssager.](../media/insider-risk-cases-dashboard.png)

Brug **kontrolelementet Søg** til at søge efter navne på store og små bogstaver for en bestemt tekst, og brug filteret til at sortere sager efter følgende attributter:

- Status
- Tid, hvor store og små bogstaver er åbnet, startdato og slutdato
- Senest opdateret, startdato og slutdato

## <a name="filter-cases"></a>Filtrer sager

Det kan være en udfordring at gennemgå en stor kø af sager afhængigt af antallet og typen af aktive insider-risikostyringspolitikker i organisationen. Brug af sagsfiltre kan hjælpe analytikere og analytikere med at sortere sager efter flere attributter. Hvis du vil filtrere beskeder på **dashboardet Sager**, skal du vælge **kontrolelementet Filter** . Du kan filtrere sager efter en eller flere attributter:

- **Status**: Vælg en eller flere statusværdier for at filtrere sagslisten. Indstillingerne er *Aktive* og *Lukkede*.
- **Tidstilfælde åbnet**: Vælg start- og slutdatoerne for, hvornår sagen blev åbnet.
- **Senest opdateret**: Vælg start- og slutdatoerne for, hvornår sagen blev opdateret.

## <a name="investigate-a-case"></a>Undersøg en sag

En dybere undersøgelse af insider-risikostyringsadvarsler er afgørende for at tage korrekte korrigerende handlinger. Insider-risikostyringssager er det centrale administrationsværktøj til at dykke dybere ned i historikken for brugerrisici, give besked om detaljer, rækkefølgen af risikohændelser og udforske indholdet og meddelelser, der er eksponeret for risici. Risikoanalytikere og analyseanalytikere bruger også tilfælde til at centralisere feedback og noter og behandle sagsløsning.

Når du vælger en sag, åbnes værktøjerne til sagsadministration, og analytikere og analytikere kan grave ned i detaljerne i sager.

### <a name="case-overview"></a>Oversigt over store og små bogstaver

Fanen **Case overview** opsummerer detaljerne for risikoanalytikere og analyseværktøjer. Den indeholder følgende oplysninger i **området Om denne** sag

- **Status**: Den aktuelle status for sagen, enten Aktiv eller Lukket.
- **Sag oprettet den**: Den dato og det klokkeslæt, hvor sagen blev oprettet.
- **Brugerens risikoscore**: Brugerens aktuelle beregnede risikoniveau for sagen. Dette resultat beregnes hver 24. time og bruger advarselskarakterer fra alle aktive beskeder, der er knyttet til brugeren.
- **Mail**: Brugerens mailalias for sagen.
- **Organisation eller afdeling**: Den organisation eller afdeling, brugeren er tildelt til.
- **Administratornavn**: Navnet på brugerens overordnede.
- **Administratormail**: Mailaliaset for brugerens chef.

![Insider-oplysninger om risikostyringssag.](../media/insider-risk-case-details.png)

Fanen **Sagsoversigt** indeholder også sektionen **Vigtige beskeder** , der indeholder følgende oplysninger om beskeder om match af politik, der er knyttet til sagen:

- **Politikken matcher**: Navnet på den insider-risikostyringspolitik, der er knyttet til matchbeskeder for brugeraktivitet.
- **Status**: Beskedens status.
- **Alvorsgrad**: Beskedens alvorsgrad.
- **Registreret tid**: Det tidspunkt, der er gået, siden beskeden blev oprettet.

### <a name="alerts"></a>Beskeder

Fanen **Beskeder opsummerer** de aktuelle beskeder, der er medtaget i sagen. Nye beskeder kan føjes til en eksisterende sag, og de føjes til **beskedkøen** , når de tildeles. Følgende attributter for påmindelser vises i køen:

- Status
- Alvorsgrad
- Registreret klokkeslæt

Vælg en besked fra køen for at få vist **detaljesiden** Besked.

Brug søgekontrolelementet til at søge efter navne på vigtige beskeder efter bestemt tekst, og brug beskedfilteret til at sortere sager efter følgende attributter:

- Status
- Alvorsgrad
- Registreret klokkeslæt, startdato og slutdato

Brug filterkontrolelementet til at filtrere beskeder efter flere attributter, herunder:

- **Status**: Vælg en eller flere statusværdier for at filtrere påmindelseslisten. Indstillingerne er *Bekræftet*, *Afvist*, *Skal gennemgås* og *Løst*.
- **Alvorsgrad**: Vælg et eller flere alvorsniveauer for din besked for at filtrere påmindelseslisten. Indstillingerne er *Høj*, *Mellem* og *Lav*.
- **Det registrerede klokkeslæt**: Vælg start- og slutdatoerne for det tidspunkt, hvor beskeden blev oprettet.
- **Politik**: Vælg en eller flere politikker for at filtrere de beskeder, der genereres af de valgte politikker.

### <a name="user-activity"></a>Brugeraktivitet

Fanen **Brugeraktivitet giver** risikoanalytikere og risikoanalytikere mulighed for at gennemgå detaljer om aktivitet og bruge en visuel repræsentation af alle de aktiviteter, der er forbundet med risikobeskeder og sager. Som en del af triageprocessen af beskeder kan det f.eks. være, at analytikere skal gennemgå alle de risikoaktiviteter, der er forbundet med sagen, for at få flere oplysninger. I tilfælde kan risikoanalyser gennemse detaljer om brugeraktivitet og boblediagrammet for at hjælpe med at forstå det overordnede omfang af de aktiviteter, der er knyttet til sagen. Du kan finde flere oplysninger om diagrammet Brugeraktivitet i [artiklen Om Insider-aktiviteter for risikostyring](insider-risk-management-activities.md#user-activity) .

### <a name="activity-explorer-preview"></a>Aktivitetsstifinder (eksempel)

Fanen **Aktivitetsoversigt** giver risikoanalytikere og risikoanalytikere mulighed for at gennemgå oplysninger om aktivitet, der er knyttet til risikobeskeder. Som en del af handlingerne til sagsstyring kan det f.eks. være, at analytikere og analytikere skal gennemgå alle de risikoaktiviteter, der er forbundet med sagen, for at få flere oplysninger. Med **Aktivitetsoversigt kan** korrekturlæsere hurtigt gennemgå en tidslinje for registreret risikabel aktivitet og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder.

Du kan finde flere oplysninger om Aktivitetsstifinder i [artiklen Om Insider-aktiviteter for](insider-risk-management-activities.md#activity-explorer) risikostyring.

### <a name="content-explorer"></a>Indholdsstifinder

Fanen **Indholdsstifinder** giver mulighed for risiko for at gennemse kopier af alle individuelle filer og mails, der er forbundet med advarsler om risici. Hvis der f.eks. oprettes en besked, når en bruger downloader hundredvis af filer fra SharePoint Online, og aktiviteten udløser en besked om en politik, bliver alle de downloadede filer til beskeden registreret og kopieret til Insider-risikostyringssagen fra de oprindelige lagringskilder.

Indholdsstifinder er et effektivt værktøj med grundlæggende og avancerede søge- og filtreringsfunktioner. Hvis du vil have mere at vide om at bruge Indholdsstifinder, [skal du se Indholdsstifinder til Insider-risikostyring](insider-risk-management-content-explorer.md).

![Insider-sag til risikostyring Indholdsstifinder.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Casenoter

Fanen **Case notes** i sagen er der, hvor risikoanalytikere og analyseanalytikere deler kommentarer, feedback og viden om deres arbejde i sagen. Noter er permanente tilføjelser til en sag og kan ikke redigeres eller slettes, når noten er gemt. Når der oprettes en sag ud fra en besked, tilføjes de kommentarer, der er angivet i dialogboksen Bekræft besked og opret **insider-risiko** sag, automatisk som en casenote.

Dashboardet til sagsnoter viser noter fra den bruger, der har oprettet noten, samt det tidspunkt, der er gået, siden noten blev gemt. Hvis du vil søge i tekstfeltet til store og små bogstaver efter et  bestemt nøgleord, skal du bruge knappen Søg på dashboardet til store og små bogstaver og skrive et bestemt nøgleord.

Sådan føjer du en note til en sag:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge **fanen** Sager.
2. Markér en sag, og vælg derefter fanen **Store og små bogstaver** .
3. Vælg **Tilføj en sagsnote**.
4. Skriv **din note for sagen** i dialogboksen Tilføj en sagsnote. Vælg **Gem** for at føje noten til sagen, eller vælg **Annuller** Luk uden at gemme noten i sagen.

### <a name="contributors"></a>Bidragydere

Fanen **Bidragydere** er der, hvor risikoanalytikere og analyseværktøjer kan føje andre korrekturlæsere til sagen. Som standard er alle brugere, der er **tildelt Insider Risk Management-analytikere** og **rollerne Insider Risk Management angivne** som bidragydere for hver aktiv og lukket sag. Kun de brugere, der **er tildelt rollen Insider Risk Management administration,** har tilladelse til at få vist filer og meddelelser i Indholdsstifinder.

Midlertidig adgang til en sag kan tildeles ved at tilføje en bruger som bidragyder. Bidragydere har al sagsstyringskontrol på den specifikke sag undtagen:

- Tilladelse til at bekræfte eller afvise beskeder
- Tilladelse til at redigere bidragydere til sager
- Tilladelse til at få vist filer og meddelelser i Indholdsstifinder

Sådan føjer du en bidragyder til en sag:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge **fanen** Sager.
2. Vælg en sag, og vælg **derefter fanen Bidragydere** .
3. Vælg **Tilføj bidragyder**.
4. Begynd at **skrive navnet** på den bruger, du vil tilføje, i dialogboksen Tilføj bidragyder, og vælg derefter brugeren på listen over foreslåede brugere. Denne liste genereres fra Azure Active Directory for dit lejerabonnement.
5. Vælg **Tilføj** for at tilføje brugeren som bidragyder, eller vælg **Annuller** luk dialogboksen uden at tilføje brugeren som bidragyder.

## <a name="case-actions"></a>Sagshandlinger

Risici kan handle på en sag i en af flere forskellige metoder afhængigt af sags alvorligheden, historikken for risikoen for brugeren og retningslinjerne for din organisation. I nogle situationer kan det være nødvendigt at eskalere en sag til en bruger eller dataundersøgelse for at samarbejde med andre områder i organisationen og dykke dybere ned i risikoaktiviteter. Insider-risikostyring er tæt integreret med andre Microsoft 365 løsninger til overholdelse af regler og standarder for at hjælpe dig med en ende-til-en-løsningsstyring.

### <a name="send-email-notice"></a>Send en mailmeddelelse

I de fleste tilfælde er brugerhandlinger, der opretter insider-risikobeskeder, utilsigtet eller utilsigtet. At sende en påmindelsesmeddelelse til brugeren via mail er en effektiv metode til at dokumentere sagsgennemgang og -handling og er en metode til at minde brugerne om virksomhedens politikker eller pege dem til at opdatere kurser. Meddelelser genereres fra [meddelelsesskabeloner, som du opretter](insider-risk-management-notices.md) til din Insider-infrastruktur til risikostyring.

Det er vigtigt at huske på, at når du sender en mail til en bruger ***ikke** _løses problemet som _Closed*. I nogle tilfælde kan det være en god ide at lade en sag være åben efter at have sendt en meddelelse til en bruger for at lede efter flere risikoaktiviteter uden at åbne en ny sag. Hvis du vil løse en sag efter afsendelse af en meddelelse, skal du vælge løs  sag som et opfølgningstrin efter afsendelse af en meddelelse.

Sådan sender du en meddelelse til den bruger, der er tildelt en sag:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge **fanen** Sager.
2. Vælg en sag, og vælg derefter **knappen Send mailmeddelelse** på værktøjslinjen sagshandling.
3. I dialogboksen **Send mailmeddelelse skal** du vælge rullelisten **Vælg** en meddelelsesskabelon for at vælge meddelelsesskabelonen for meddelelsen. Denne markering udfylder de andre felter i meddelelsen på forhånd.
4. Gennemse meddelelsesfelterne, og opdater dem efter behov. De værdier, der angives her, tilsidesætter værdierne i skabelonen.
5. Vælg **Send** for at sende meddelelsen til brugeren, eller vælg **Annuller** Luk dialogboksen uden at sende meddelelsen til brugeren. Alle sendte meddelelser føjes til køen med sagsnoter på **dashboardet for sagsnoter** .

### <a name="escalate-for-investigation"></a>Eskaler til undersøgelse

Eskaler sagen til brugerundersøgelse i situationer, hvor yderligere juridisk gennemgang er nødvendig for brugerens risikoaktivitet. Denne eskalering åbner en ny Advanced eDiscovery sag i din Microsoft 365 organisation. Advanced eDiscovery en ende-til-ende-arbejdsproces til at bevare, indsamle, gennemse, analysere og eksportere indhold, der reagerer på din organisations interne og eksterne juridiske undersøgelser. Det giver også dit juridiske team mulighed for at administrere hele arbejdsprocessen for meddelelser om retsligt hold til at kommunikere med personer, der er involveret i en sag. Når du tildeler en korrekturlæser som din Advanced eDiscovery en sag, der er oprettet ud fra en Insider Risk management-sag, kan det hjælpe dit juridiske team med at tage de nødvendige skridt til at administrere opbevaring af indhold. Hvis du vil have mere Advanced eDiscovery om Advanced eDiscovery, [skal du se Oversigt over Advanced eDiscovery i Microsoft 365](overview-ediscovery-20.md).

Sådan eskalerer du en sag til en brugerundersøgelse:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge **fanen** Sager.
2. Vælg en sag, og vælg derefter knappen **Eskaler til undersøgelse** på værktøjslinjen Sagshandling.
3. I dialogboksen **Eskaler til undersøgelse** skal du angive et navn til den nye brugerundersøgelse. Hvis det er nødvendigt, kan du skrive noter om sagen og **vælge Eskaler**.
4. Gennemse meddelelsesfelterne, og opdater dem efter behov. De værdier, der angives her, tilsidesætter værdierne i skabelonen.
5. Vælg **Bekræft** for at oprette brugerundersøgelsessagen, eller vælg **Annuller** for at lukke dialogboksen uden at oprette en ny brugerundersøgelsessag.

Når insider-risikostyringssagen er blevet eskaleret til en ny brugerundersøgelsessag, kan du gennemgå den nye sag i **området eDiscoveryAdvanced** >  på Microsoft 365 Overholdelsescenter.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Kør automatiserede opgaver med Power Automate flows for sagen

Ved hjælp Power Automate dataflows kan risikoanalytikere og analytikere hurtigt reagere på:

- Anmod om oplysninger fra HR eller virksomhed om en bruger i en Insider-risikosag
- Giv besked til chef, når en bruger har en insider-risikobesked
- Opret en post for en insider-risikoadministrationssag i ServiceNow
- Giv brugerne besked, når de føjes til en Insider-risikopolitik

Sådan kører, administrerer eller opretter du Power Automate flows for en insider-risikostyringssag:

1. Vælg **Automatiser** på værktøjslinjen til sagshandling. 
2. Vælg det Power Automate, der skal køres, og vælg **derefter Kør flow**. 
3. Når flowet er fuldført, skal du vælge **Udført**.

Du kan få mere at Power Automate om flow for insider-risikostyring under [Introduktion til indstillinger for insider-risikostyring](insider-risk-management-settings.md#power-automate-flows-preview).

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Få vist eller opret Microsoft Teams team for sagen

Når Microsoft Teams integration for Insider Risk Management er aktiveret i indstillinger, oprettes der automatisk et Microsoft Teams-team, hver gang der bekræftes en besked, og der oprettes en sag. Risici og analytikere kan hurtigt åbne Microsoft Teams og gå direkte til teamet for en sag ved at vælge Vis **Microsoft Teams-team** på værktøjslinjen for sagshandling.

For tilfælde, der åbnes, før Microsoft Team-integration er aktiveret, kan risikoanalyser og analytikere oprette et nyt Microsoft Teams-team til en sag ved at vælge Opret **Microsoft Teams-team** på værktøjslinjen for sagshandling.

Når en sag er løst, arkiveres det tilknyttede Microsoft-team automatisk (skjult og aktiveret som skrivebeskyttet).

Hvis du vil vide mere Microsoft Teams om insider-risikostyring, skal du se [Introduktion til insider-indstillinger for risikostyring](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Løs problemet

Når risikoanalytikere og risikoanalytikere har afsluttet deres gennemgang og undersøgelse, kan en sag løses, så der kan reageres på alle de beskeder, der aktuelt er inkluderet i sagen. Når du løser en sag, tilføjes der en klassificering af løsningen, statussen for sag ændres til *Lukket, og* handlingsårsagen til løsningen føjes automatisk til køen med sagsnoter på dashboardet For **sagsnoter** . Sager løses enten som:

- **Benign**: Klassificeringen af tilfælde, hvor beskeder om match af politikker evalueres som lav risiko, ikke-alvorlig eller falsk positiv.
- **Bekræftet overtrædelse af** politikken: Klassificeringen af tilfælde, hvor beskeder om match af politikker evalueres som risikabelt, alvorlig eller resultatet af ondsindede hensigter.

Sådan løses en sag:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge **fanen** Sager.
2. Markér en sag, og vælg derefter **knappen Løs sag** på værktøjslinjen til sagshandling.
3. I dialogboksen **Løs sag** skal du vælge **rulleelementet Løs** som for at vælge løsningsklassificeringen for sagen. Indstillingerne er **Benign-** eller **Bekræftet politikkrænkelse**.
4. I dialogboksen **Løs sag skal** du angive årsagerne til klassificeringen af løsningen i **tekstfeltet Handling** taget.
5. Vælg **Løs** for at lukke sagen, eller vælg **Annuller** luk dialogboksen uden at løse sagen.
