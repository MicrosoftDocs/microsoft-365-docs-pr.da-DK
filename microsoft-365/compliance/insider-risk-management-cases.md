---
title: Sager vedrørende styring af insiderrisiko
description: Få mere at vide om sager om styring af insiderrisiko i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse
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
ms.openlocfilehash: 916fb67d8fb2376a1a59d3d2aa61a8e7d041f194
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469376"
---
# <a name="insider-risk-management-cases"></a>Sager vedrørende styring af insiderrisiko

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Sager er kernen i insiderrisikostyring og giver dig mulighed for at undersøge og reagere på problemer, der genereres af risikoindikatorer, der er defineret i dine politikker. Sager oprettes manuelt ud fra beskeder i situationer, hvor der er behov for yderligere handling for at løse et problem relateret til overholdelse af regler og standarder for en bruger. Hver sag er begrænset til en enkelt bruger, og flere beskeder for brugeren kan føjes til en eksisterende sag eller til en ny sag.

Når du har undersøgt detaljerne for en sag, kan du udføre en handling ved at:

- sende brugeren en meddelelse
- løsning af sagen som godartet
- dele sagen med din ServiceNow-forekomst eller med en mailmodtager
- eskalerer sagen for en eDiscovery-undersøgelse (Premium)

Se [videoen Insider Risk Management Investigation and Escalation](https://www.youtube.com/watch?v=UONUSmkRC8s) for at få en oversigt over, hvordan sager undersøges og administreres i styring af insiderrisiko.

## <a name="cases-dashboard"></a>Dashboardet Sager

**Dashboardet Sager** for insiderrisikostyring giver dig mulighed for at få vist og reagere på sager. Hver rapportwidget på dashboardet viser oplysninger for de seneste 30 dage.

- **Aktive sager**: Det samlede antal aktive sager, der undersøges.
- **Sager over de seneste 30 dage**: Det samlede antal sager, der er oprettet *, sorteret* efter aktiv og *lukket* status.
- **Statistik**: Den gennemsnitlige tid for aktive sager, der er angivet i timer, dage eller måneder.

Sagskøen viser alle aktive og lukkede sager for din organisation ud over den aktuelle status for følgende sagsattributter:

- **Sagsnavn**: Navnet på sagen, der defineres, når en besked bekræftes, og sagen oprettes.  
- **Status**: Status for sagen, enten *Aktiv* eller *Lukket*.
- **Bruger**: Brugeren for sagen. Hvis anonymisering af brugernavne er aktiveret, vises anonymiserede oplysninger.
- **Tid åbnet sag**: Det tidspunkt, der er gået, siden sagen blev åbnet.
- **Samlet antal politikbeskeder**: Antallet af politikforekomster, der er inkluderet i sagen. Dette tal kan stige, hvis der føjes nye beskeder til sagen.
- **Sagen blev sidst opdateret**: Det tidspunkt, der er gået, siden der er tilføjet en note eller ændring i sagstilstanden.
- **Sidst opdateret af**: Navnet på den insiderrisikostyringsanalytiker eller efterforsker, der sidst opdaterede sagen.

![Dashboard med sager om insiderrisikostyring.](../media/insider-risk-cases-dashboard.png)

Brug kontrolelementet **Search** til at søge efter navne på små og små bogstaver efter bestemt tekst, og brug sagsfilteret til at sortere sager efter følgende attributter:

- Status
- Tidspunkt for åbning af sag, startdato og slutdato
- Senest opdateret, startdato og slutdato

## <a name="filter-cases"></a>Filtrer sager

Det kan være en udfordring at gennemgå en stor række sager, afhængigt af antallet og typen af aktive politikker for styring af insiderrisiko i din organisation. Brug af sagsfiltre kan hjælpe analytikere og efterforskere med at sortere sager efter flere attributter. Hvis du vil filtrere beskeder på **dashboardet Sager**, skal du vælge kontrolelementet **Filter** . Du kan filtrere sager efter en eller flere attributter:

- **Status**: Vælg en eller flere statusværdier for at filtrere sagslisten. Indstillingerne er *Aktiv* og *Lukket*.
- **Tid for åbning af sag**: Vælg start- og slutdatoerne for, hvornår sagen blev åbnet.
- **Sidst opdateret**: Vælg start- og slutdatoerne for, hvornår sagen blev opdateret.

## <a name="investigate-a-case"></a>Undersøg en sag

En dybere undersøgelse af insiderrisikostyringsbeskeder er afgørende for at kunne udføre korrekte korrigerende handlinger. Insiderrisikostyringssager er det centrale administrationsværktøj til at dykke dybere ned i brugerrisikoaktivitetshistorikken, beskedoplysninger, sekvensen af risikohændelser og til at udforske det indhold og de meddelelser, der eksponeres for risici. Risikoanalytikere og efterforskere bruger også sager til at centralisere feedback og noter om anmeldelser og til at behandle sagsløsning.

Når du vælger en sag, åbnes værktøjerne til sagsstyring, og analytikere og efterforskere kan se nærmere på sagsoplysningerne.

### <a name="case-overview"></a>Oversigt over sager

Under fanen **Sagsoversigt** opsummeres sagsdetaljerne for risikoanalytikere og efterforskere. Den indeholder følgende oplysninger i området **Om denne sag**

- **Status**: Den aktuelle status for sagen, enten Aktiv eller Lukket.
- **Sag oprettet** den: Den dato og det klokkeslæt, hvor sagen blev oprettet.
- **Brugerens risikoscore: Brugerens** aktuelle beregnede risikoniveau for sagen. Denne score beregnes hvert 24. time og bruger scorer for advarselsrisici fra alle aktive beskeder, der er knyttet til brugeren.
- **Mail**: Brugerens mailalias for sagen.
- **Organisation eller afdeling**: Den organisation eller afdeling, som brugeren er tildelt.
- **Ledernavn**: Navnet på brugerens leder.
- **Chefmail**: Mailaliaset for brugerens leder.

![Oplysninger om insiderrisikostyringscases.](../media/insider-risk-case-details.png)

Fanen **Sagsoversigt** indeholder også sektionen **Beskeder** , der indeholder følgende oplysninger om politikmatchbeskeder, der er knyttet til sagen:

- **Politikforekomster**: Navnet på politikken for styring af insiderrisiko, der er knyttet til matchbeskederne for brugeraktivitet.
- **Status**: Status for beskeden.
- **Alvorsgrad**: Alvorsgraden af beskeden.
- **Tid registreret**: Det tidspunkt, der er gået, siden beskeden blev genereret.

### <a name="alerts"></a>Beskeder

Fanen **Beskeder** opsummerer de aktuelle beskeder, der er inkluderet i sagen. Nye beskeder kan føjes til en eksisterende sag, og de føjes til **beskedkøen** , når de tildeles. Følgende beskedattributter er angivet i køen:

- Status
- Sværhedsgraden
- Registreret tid

Vælg en besked fra køen for at få vist siden **Beskedoplysninger** .

Brug søgekontrolelementet til at søge efter beskednavne efter bestemt tekst, og brug beskedfilteret til at sortere sager efter følgende attributter:

- Status
- Sværhedsgraden
- Registreret tid, startdato og slutdato

Brug filterkontrolelementet til at filtrere beskeder efter flere attributter, herunder:

- **Status**: Vælg en eller flere statusværdier for at filtrere beskedlisten. Indstillingerne er *Bekræftet*, *Afvist*, *Skal gennemses* og *Løst*.
- **Alvorsgrad**: Vælg et eller flere niveauer af beskedrisikoen for at filtrere beskedlisten. Indstillingerne er *Høj*, *Mellem* og *Lav*.
- **Registreret tid**: Vælg start- og slutdatoer for, hvornår beskeden blev oprettet.
- **Politik**: Vælg en eller flere politikker for at filtrere de beskeder, der genereres af de valgte politikker.

### <a name="user-activity"></a>Brugeraktivitet

Fanen **Brugeraktivitet** gør det muligt for risikoanalytikere og efterforskere at gennemse aktivitetsoplysninger og bruge en visuel repræsentation af alle de aktiviteter, der er knyttet til risikobeskeder og sager. Som en del af processen til vigtige beskeder skal analytikere f.eks. gennemse alle de risikoaktiviteter, der er knyttet til sagen, for at få flere oplysninger. I tilfælde kan risikoforskere gennemse oplysninger om brugeraktivitet og boblediagrammet for at hjælpe med at forstå det overordnede omfang af de aktiviteter, der er knyttet til sagen. Du kan få flere oplysninger om brugeraktivitetsdiagrammet i artiklen [Insider Risk Management-aktiviteter](insider-risk-management-activities.md#user-activity) .

### <a name="activity-explorer-preview"></a>Aktivitetsoversigt (prøveversion)

Fanen **Aktivitetsoversigt** giver risikoanalytikere og efterforskere mulighed for at gennemse aktivitetsoplysninger, der er knyttet til risikobeskeder. Som en del af sagshåndteringshandlinger kan det f.eks. være nødvendigt for efterforskere og analytikere at gennemse alle de risikoaktiviteter, der er knyttet til sagen, for at få flere oplysninger. Med **Aktivitetsoversigt** kan korrekturlæsere hurtigt gennemse en tidslinje over registreret risikable aktiviteter og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder.

Du kan få flere oplysninger om Aktivitetsoversigt i artiklen [Insider Risk Management-aktiviteter](insider-risk-management-activities.md#activity-explorer) .

### <a name="content-explorer"></a>Indholdsoversigt

Fanen **Indholdsoversigt** giver risikoforskere mulighed for at gennemse kopier af alle individuelle filer og mailmeddelelser, der er knyttet til risikobeskeder. Hvis der f.eks. oprettes en besked, når en bruger downloader hundredvis af filer fra SharePoint Online, og aktiviteten udløser en politikbesked, registreres og kopieres alle de downloadede filer til beskeden til insiderrisikostyringscasen fra oprindelige lagerkilder.

Indholdsoversigt er et effektivt værktøj med grundlæggende og avancerede søge- og filtreringsfunktioner. Hvis du vil vide mere om brug af Indholdsoversigt, skal du se [Indholdsoversigt for styring af insiderrisiko](insider-risk-management-content-explorer.md).

![Insider risk management-sag Indholdsoversigt.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Sagsnoter

Fanen **Case notes** i sagen er det tilfælde, hvor risikoanalytikere og efterforskere deler kommentarer, feedback og indsigt om deres arbejde i forbindelse med sagen. Noter er permanente tilføjelser til en sag og kan ikke redigeres eller slettes, når noten er gemt. Når der oprettes en sag ud fra en besked, tilføjes de kommentarer, der er angivet i dialogboksen **Bekræft besked og opret insiderrisikosag** , automatisk som en sagsbemærkning.

Dashboardet sagsnoter viser noter fra den bruger, der oprettede noten, og det tidspunkt, der er gået, siden noten blev gemt. Hvis du vil søge i tekstfeltet til sagsnoter efter et bestemt nøgleord, skal du bruge knappen **Søg** på sagsdashboardet og angive et bestemt nøgleord.

Sådan føjer du en note til en sag:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Sager**.
2. Vælg en sag, og vælg derefter fanen **Sagsnoter** .
3. Vælg **Tilføj sagsnote**.
4. Skriv din note til sagen i dialogboksen **Tilføj sagsnote** . Vælg **Gem** for at føje noten til sagen, eller vælg **Annuller** luk uden at gemme noten i sagen.

### <a name="contributors"></a>Bidragydere

Fanen **Bidragydere** i sagen er det tilfælde, hvor risikoanalytikere og efterforskere kan føje andre korrekturlæsere til sagen. Alle brugere, der er tildelt **rollerne Insider Risk Management Analysts** og **Insider Risk Management Investigators** , er som standard angivet som bidragydere for hver aktive og lukkede sag. Det er kun brugere, der har fået tildelt rollen **Undersøgere af insiderrisikostyring** , der har tilladelse til at få vist filer og meddelelser i Indholdsoversigt.

Du kan give midlertidig adgang til en sag ved at tilføje en bruger som bidragyder. Bidragydere har al sagsstyringskontrol i den specifikke sag undtagen:

- Tilladelse til at bekræfte eller afvise beskeder
- Tilladelse til at redigere bidragydere for sager
- Tilladelse til at få vist filer og meddelelser i Indholdsoversigt

Sådan føjer du en bidragyder til en sag:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Sager**.
2. Vælg en sag, og vælg derefter fanen **Bidragydere** .
3. Vælg **Tilføj bidragyder**.
4. I dialogboksen **Tilføj bidragyder** skal du begynde at skrive navnet på den bruger, du vil tilføje, og derefter vælge brugeren på listen over foreslåede brugere. Denne liste oprettes ud fra Azure Active Directory for dit lejerabonnement.
5. Vælg **Tilføj** for at tilføje brugeren som bidragyder, eller vælg **Annuller** luk dialogboksen uden at tilføje brugeren som bidragyder.

## <a name="case-actions"></a>Sagshandlinger

Risikoforskere kan handle på en sag på en af flere metoder, afhængigt af sagens alvorsgrad, historikken over risikoen for brugeren og retningslinjerne for risikoen i din organisation. I nogle situationer kan det være nødvendigt at eskalere en sag til en bruger eller en dataundersøgelse for at samarbejde med andre områder i din organisation og dykke dybere ned i risikoaktiviteter. Styring af insiderrisiko er tæt integreret med andre Microsoft Purview løsninger for at hjælpe dig med administration af komplette løsninger.

### <a name="send-email-notice"></a>Send meddelelse via mail

I de fleste tilfælde er brugerhandlinger, der opretter insiderrisikobeskeder, utilsigtede eller utilsigtede. Afsendelse af en påmindelse til brugeren via mail er en effektiv metode til at dokumentere sagsgennemgang og -handling og er en metode til at minde brugerne om virksomhedens politikker eller pege dem på oplæring i opdatering. Meddelelser genereres ud fra [de meddelelsesskabeloner, du opretter](insider-risk-management-notices.md) til din infrastruktur til styring af insiderrisiko.

Det er vigtigt at huske, at afsendelse af en mailmeddelelse til en bruger ***ikke** _ løser sagen som _Closed*. I nogle tilfælde kan det være en god idé at lade en sag være åben, når du har sendt en meddelelse til en bruger for at søge efter flere risikoaktiviteter uden at åbne en ny sag. Hvis du vil løse en sag, når du har sendt en meddelelse, skal du vælge trinnet **Løs sag** som et efterfølgende trin, når du har sendt en meddelelse.

Sådan sender du en meddelelse til den bruger, der er tildelt en sag:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Sager**.
2. Vælg en sag, og vælg derefter knappen **Send meddelelse via mail** på værktøjslinjen med sagshandlingen.
3. I dialogboksen **Send mailmeddelelse** skal du vælge rullelistekontrolelementet **Vælg en meddelelsesskabelon** for at vælge meddelelsesskabelonen til meddelelsen. Dette valg udfylder på forhånd de andre felter i meddelelsen.
4. Gennemse meddelelsesfelterne, og opdater efter behov. De værdier, der angives her, tilsidesætter værdierne i skabelonen.
5. Vælg **Send** for at sende meddelelsen til brugeren, eller vælg **Annuller** luk dialogboksen uden at sende meddelelsen til brugeren. Alle sendte meddelelser føjes til sagsnotekøen på dashboardet **Sagsnoter** .

### <a name="escalate-for-investigation"></a>Eskaler til undersøgelse

Eskaler sagen for brugerundersøgelse i situationer, hvor yderligere juridisk gennemgang er nødvendig for brugerens risikoaktivitet. Denne eskalering åbner et nyt Microsoft Purview eDiscovery-tilfælde (Premium) i din Microsoft 365 organisation. eDiscovery (Premium) indeholder en komplette arbejdsproces til bevarelse, indsamling, gennemgang, analyse og eksport af indhold, der reagerer på din organisations interne og eksterne juridiske undersøgelser. Det giver også dit juridiske team mulighed for at administrere hele arbejdsprocessen for meddelelse om juridiske ventepositioner for at kommunikere med tilsynsførende, der er involveret i en sag. Eskalering til en eDiscovery-sag (Premium) fra en sag om administration af insiderrisiko hjælper dit juridiske team med at træffe de nødvendige foranstaltninger og administrere bevarelse af indhold. Du kan få mere at vide om eDiscovery-sager (Premium) under [Oversigt over Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md).

Sådan eskalerer du en sag til en brugerundersøgelse:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Sager**.
2. Vælg en sag, og vælg derefter knappen **Eskaler til undersøgelse** på værktøjslinjen sagshandling.
3. Angiv et navn til den nye brugerundersøgelse i dialogboksen **Eskaler til undersøgelse** . Angiv evt. noter om sagen, og vælg **Eskaler**.
4. Gennemse meddelelsesfelterne, og opdater efter behov. De værdier, der angives her, tilsidesætter værdierne i skabelonen.
5. Vælg **Bekræft** for at oprette brugerundersøgelsessagen, eller vælg **Annuller** for at lukke dialogboksen uden at oprette en ny brugerundersøgelsessag.

Når insiderrisikostyringscasen er eskaleret til en ny brugerundersøgelsessag, kan du gennemse den nye sag i området **eDiscoveryAdvanced** >  i Microsoft Purview-compliance-portal.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Kør automatiserede opgaver med Power Automate flow for sagen

Ved hjælp af anbefalede Power Automate flow kan risikoforskere og analytikere hurtigt gøre noget for at:

- Anmod HR eller virksomheden om oplysninger om en bruger i en insiderrisikosag
- Giv lederen besked, når en bruger har en insiderrisikobesked
- Opret en post for en sag om styring af insiderrisiko i ServiceNow
- Giv brugerne besked, når de føjes til en insiderrisikopolitik

Sådan kører, administrerer eller opretter du Power Automate flow for en insiderrisikostyringssag:

1. Vælg **Automatiser** på værktøjslinjen til sagshandling. 
2. Vælg det Power Automate flow, der skal køres, og vælg derefter **Kør flow**. 
3. Når flowet er fuldført, skal du vælge **Udført**.

Hvis du vil vide mere om Power Automate flow til styring af insiderrisiko, skal [du se Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#power-automate-flows-preview).

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Få vist eller opret et Microsoft Teams team til sagen

Når Microsoft Teams integration til styring af insiderrisiko er aktiveret i indstillinger, oprettes der automatisk et Microsoft Teams team, hver gang en besked bekræftes, og der oprettes en sag. Risikoforskere og analytikere kan hurtigt åbne Microsoft Teams og navigere direkte til teamet for en sag ved at vælge **Vis Microsoft Teams team** på værktøjslinjen til sagshandling.

I forbindelse med sager, der er åbnet før aktivering af Microsoft Team-integration, kan risikoforskere og analytikere oprette et nyt Microsoft Teams team til en sag ved at vælge **Opret Microsoft Teams team** på værktøjslinjen til sagshandling.

Når en sag er afsluttet, arkiveres det tilknyttede Microsoft-team automatisk (skjult og skrivebeskyttet).

Hvis du vil vide mere om Microsoft Teams til styring af insiderrisiko, [skal du se Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Løs sagen

Når risikoanalytikere og efterforskere har afsluttet deres gennemgang og undersøgelse, kan en sag løses for at reagere på alle de beskeder, der i øjeblikket er inkluderet i sagen. Løsning af en sag tilføjer en løsningsklassificering, ændrer sagsstatus til *Lukket*, og årsagerne til løsningshandlingen føjes automatisk til sagsnotekøen på dashboardet **Sagsnoter** . Sager løses som enten:

- **Godartet**: Klassificeringen for de tilfælde, hvor politikmatchbeskeder evalueres som lav risiko, ikke-alvorlig eller falsk positiv.
- **Bekræftet politikovertrædelse**: Klassificeringen for tilfælde, hvor beskeder om politikmatch evalueres som risikable, alvorlige eller resultatet af ondsindet hensigt.

Sådan løses en sag:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Sager**.
2. Vælg en sag, og vælg derefter knappen **Løs sag** på værktøjslinjen sag.
3. I dialogboksen **Løs sag** skal du vælge rullemenuen **Løs som** for at vælge løsningsklassificeringen for sagen. Indstillingerne er overtrædelse af politikken **Godartet** eller **Bekræftet**.
4. I dialogboksen **Løs sag** skal du angive årsagerne til løsningsklassificeringen i tekstfeltet **Handling udført** .
5. Vælg **Løs** for at lukke sagen, eller vælg **Annuller** Luk dialogboksen uden at løse problemet.
