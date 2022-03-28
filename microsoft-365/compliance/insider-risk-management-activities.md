---
title: Undersøg insider-risikostyringsaktiviteter
description: Få mere at vide om undersøgelse af insider-risikostyringsaktiviteter Microsoft 365
keywords: Microsoft 365, insider-risiko, risikostyring, overholdelse af regler og standarder
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
ms.openlocfilehash: e56fb2e550adb870ed096f90c7d8d9b90c1de249
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598004"
---
# <a name="investigate-insider-risk-management-activities"></a>Undersøg insider-risikostyringsaktiviteter

Undersøgelse af risikabel brugeraktiviteter er et vigtigt første trin til at minimere insiderrisici i organisationen. Disse risici kan være aktiviteter, der genererer beskeder fra insider-risikostyringspolitikker, eller risici ved aktiviteter, der registreres af politikker, men som ikke straks opretter en insider-risikostyringsadvarsel til brugerne. Du kan undersøge disse typer aktiviteter ved hjælp af **brugeraktivitetsrapporterne (forhåndsvisning)** eller ved hjælp af **dashboardet Besked**.

## <a name="user-activity-reports-preview"></a>Brugeraktivitetsrapporter (forhåndsvisning)

Brugeraktivitetsrapporter giver dig mulighed for at undersøge aktiviteter for bestemte brugere i en defineret tidsperiode uden at skulle tildele dem midlertidigt eller eksplicit til en Insider-politik for risikostyring. I de fleste insider-scenarier for risikostyring er brugerne eksplicit defineret i politikker, og de kan have besked om politikker (afhængigt af udløsende hændelser) og risikoresultater, der er knyttet til aktiviteterne. Men i visse situationer kan det være en god ide at undersøge aktiviteterne for brugere, som ikke eksplicit er defineret i en politik. Disse aktiviteter kan være for brugere, som du har modtaget et tip om brugeren og potentielt risikabelt aktiviteter, eller brugere, der typisk ikke behøver at blive tildelt en Insider-politik for risikostyring.

Når du har konfigureret indikatorer på siden **insider-Indstillinger**, registreres brugeraktivitet for risikabel aktivitet, der er knyttet til de valgte indikatorer. Du behøver ikke at konfigurere en politik for brugeraktivitetsrapporter for at registrere og rapportere risikabelt aktiviteter for brugere i organisationen. Aktiviteter, der er inkluderet i brugeraktivitetsrapporter, kræver ikke, at der udløses hændelser for, at aktiviteterne vises. Denne konfiguration betyder, at al registreret aktivitet for brugeren kan gennemses, uanset om den har en udløsende hændelse, eller hvis der oprettes en besked. Rapporter oprettes pr. bruger og kan omfatte alle aktiviteter for en brugerdefineret periode på 90 dage. Flere rapporter for den samme bruger understøttes ikke.

Når du har undersøgt aktiviteter for en bruger, kan brugere afvise individuelle aktiviteter som benignere, dele eller maile et link til rapporten med andre brugere eller vælge at tildele brugeren midlertidigt eller eksplicit til en insider-politik for risikostyring. Brugere skal være tildelt rollegruppen *Insider Risk Management Administration for* at få vist siden **med brugeraktivitetsrapporter** .  

![Oversigt over brugeraktivitetsrapport for Insiders til risikostyring.](../media/insider-risk-user-activity-report-overview.png)

Du kan komme i gang ved at vælge **Administrer** rapporter i **sektionen** Undersøg brugeraktivitet på siden Oversigt over **insider-risikostyring** . Hvis du vil have vist aktiviteter for en bruger, skal **du først** vælge Opret rapport over brugeraktivitet og udfylde følgende felter i **ruden Ny brugeraktivitetsrapport** :

- **Bruger**: Søg efter en bruger ved hjælp af navn eller mailadresse
- **Startdato**: Brug kalenderkontrolelementet til at vælge startdatoen for brugeraktiviteter.
- **Slutdato**: Brug kalenderkontrolelementet til at vælge slutdatoen for brugeraktiviteter. Den valgte slutdato skal være større end to dage efter den valgte startdato og højst 90 dage fra den valgte startdato.
Nye rapporter tager typisk op til 10 timer, før de er klar til gennemsyn. Når rapporten er klar, vises Rapporten klar i *kolonnen* **Status** på siden Rapport over brugeraktivitet. Vælg brugeren for at få vist den detaljerede rapport:

![Insider-rapport over brugeraktivitet i risikostyring.](../media/insider-risk-user-activity-report.png)

Rapporten **Brugeraktivitet for den** valgte bruger indeholder **fanerne Brugeraktivitet** og **Aktivitetsstifinder** :

- **Brugeraktivitet**: Brug denne diagramvisning til at undersøge aktiviteter og få vist potentielle aktiviteter, der forekommer i sekvenser. Denne fane er struktureret, så der kan foretages en hurtig gennemgang af en sag, herunder en historisk tidslinje for alle aktiviteter, oplysninger om aktivitet, det aktuelle risikoresultat for brugeren i sagen, rækkefølgen af risikohændelser og filtrering af kontrolelementer for at hjælpe med til at håndtere igangværende bestræbelser.
- **Aktivitetsstifinder**: **Fanen Aktivitetsstifinder** indeholder risikorisici med et omfattende analyseværktøj, der indeholder detaljerede oplysninger om aktiviteter. Med Aktivitetsoversigt kan korrekturlæsere hurtigt gennemgå en tidslinje for registreret risikabel aktivitet og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder. Hvis du vil have mere at vide om at bruge Aktivitetsstifinder, skal *du se* afsnittet Aktivitetsstifinder senere i denne artikel.

## <a name="alert-dashboard"></a>Advarselsdashboard

Insider-risikostyringsadvarsler genereres automatisk af risikoindikatorer, der er defineret i insider-risikostyringspolitikker. Disse beskeder giver analytikere og analytikere for overholdelse af regler og standarder en alt-for-overblik over den aktuelle risikostatus og giver din organisation mulighed for at undersøger og udføre handlinger for opdagede risici. Som standard genererer politikker en bestemt mængde lav, mellem og høj alvorsgrad, men du kan øge eller mindske beskedens lydstyrke, så den passer til dine behov.[](insider-risk-management-settings.md#alert-volume) Desuden kan du konfigurere grænseværdien for [påmindelse for politikindikatorer, når](insider-risk-management-settings.md#indicator-level-settings-preview) du opretter en ny politik med værktøjet til oprettelse af politikker.

Se videoen [Om triageoplevelsen i Insider Risk Management](https://www.youtube.com/watch?v=KgmpxBLJLPI) for at få et overblik over, hvordan beskeder giver detaljer, kontekst og relateret indhold til risikabel aktivitet, og hvordan du kan gøre din undersøgelsesproces mere effektiv.

Insider Risk **Alert-dashboardet giver** dig mulighed for at få vist og reagere på beskeder, der genereres af insider-risikopolitikker. Hver rapportwidget viser oplysninger for de seneste 30 dage.

- **Samlet antal vigtige beskeder, der** skal gennemgås: Det samlede antal vigtige beskeder, der skal gennemgås og gennemgås, herunder en opdeling efter alvorsgrad for beskeden.
- **Åbne beskeder over de seneste 30** dage: Det samlede antal beskeder, der er oprettet af politikken, passer i løbet af de seneste 30 dage, sorteret efter høj, mellem og lav alvorsgrad.
- **Gennemsnitlig tid til at løse beskeder**: En oversigt over nyttige statistik for beskeder:
  - Gennemsnitlig tid til løsning af beskeder om høj alvorsgrad angivet i timer, dage eller måneder.
  - Gennemsnitlig tid til at rette beskeder om mellem alvorlighed, der er angivet i timer, dage eller måneder.
  - Gennemsnitlig tid til løsning af beskeder om lav alvorsgrad angivet i timer, dage eller måneder.

![Dashboard for insider-risikostyringsbeskeder.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> Insider-risikostyring bruger indbygget begrænsning af beskeder for at beskytte og optimere din risikoundersøgelses- og gennemsynsoplevelse. Denne begrænsning af problemet kan medføre et overbelastning af politikadvarsler, f.eks. forkert konfigurerede dataforbindelser eller DLP-politikker. Der kan derfor være en forsinkelse i visningen af nye beskeder for en bruger.

## <a name="alert-status-and-severity"></a>Beskedstatus og alvorsgrad

Du kan omdele beskeder i en af følgende statusser:

- **Bekræftet**: En besked bekræftet og tildelt en ny eller eksisterende sag.
- **Afvist**: En besked er blevet afvist som en god i forbindelse med en trepartsproces. Du kan angive en årsag til beskedens indhold og medtage noter, der er tilgængelige i brugerens beskedoversigt, så der kan angives yderligere kontekst til fremtidig brug eller for andre korrekturlæsere. Disse årsager kan variere fra forventede aktiviteter, ikke-virkningsfulde begivenheder, blot reducere antallet af påmindelsesaktiviteter for brugeren eller en årsag til noterne. Valg af *årsagsklassificering* omfatter Aktivitet forventes for denne bruger, Aktivitet er påvirket nok *for* mig til at undersøge yderligere, og beskeder for denne bruger indeholder *for* meget aktivitet.
- **Skal gennemgås**: En ny besked, hvor der endnu ikke er blevet foretaget triagehandlinger.
- **Løst**: En besked, der er en del af en lukket og løst sag.

Besked om risikoresultater beregnes automatisk ud fra flere indikatorer for risikoaktivitet. Disse indikatorer omfatter typen af risikoaktivitet, antallet og hyppigheden af aktivitetsforekomsten, historikken over brugerrisici samt tilføjelsen af aktivitetsrisici, der kan øge aktivitetens alvorlighed. Risikoscoreen for besked driver den programmeringiske tildeling af et risikoniveau for hver besked og kan ikke tilpasses. Hvis beskederne forbliver uadsigende, og risikoaktiviteter fortsat periodiseres til beskeden, kan risikoens alvorsgrad øges. Risikoanalytikere og risikoanalytikere kan bruge risikoens alvorsgrad til at hjælpe med at triage beskeder i overensstemmelse med organisationens risikopolitikker og standarder.

Besked om alvorlighedsniveauer for risici er:

- **Høj alvorsgrad**: Aktiviteterne og indikatorerne for beskeden udgør en betydelig risiko. De tilknyttede risikoaktiviteter er alvorlige, gentagne og centrale elementer, der kraftigt påvirker andre betydelige risikofaktorer.
- **Mellem alvorlighed**: Aktiviteterne og indikatorerne for beskeden udgør en moderat risiko. De tilknyttede risikoaktiviteter er moderate, hyppige og har en vis sammenhæng med andre risikofaktorer.
- **Lav alvorsgrad**: Aktiviteterne og indikatorerne for beskeden udgør en mindre risiko. De tilknyttede risikoaktiviteter er mindre, mere sjældne og omfatter ikke andre væsentlige faktorer.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer beskeder på dashboardet Besked

Det kan være en udfordring at gennemgå en stor kø af beskeder afhængigt af antallet og typen af aktive insider-risikostyringspolitikker i organisationen. Brug af advarselsfiltre kan hjælpe analytikere og sortering af beskeder efter flere attributter. Hvis du vil filtrere beskeder på **dashboardet Vigtige beskeder**, skal du vælge **kontrolelementet Filter** . Du kan filtrere beskeder efter en eller flere attributter:

- **Status**: Vælg en eller flere statusværdier for at filtrere påmindelseslisten. Indstillingerne er *Bekræftet*, *Afvist*, *Skal gennemgås* og *Løst*.
- **Alvorsgrad**: Vælg et eller flere alvorsniveauer for din besked for at filtrere påmindelseslisten. Indstillingerne er *Høj*, *Mellem* og *Lav*.
- **Det registrerede klokkeslæt**: Vælg start- og slutdatoerne for det tidspunkt, hvor beskeden blev oprettet. Dette filter søger efter beskeder mellem UTC 00:00 på startdatoen og UTC 00:00 på slutdatoen. Hvis du vil filtrere beskeder for en bestemt dag, skal du angive datoen for dagen i  feltet Startdato og datoen på den følgende dag **i feltet** Slutdato.
- **Politik**: Vælg en eller flere politikker for at filtrere de beskeder, der genereres af de valgte politikker.
- **Risikofaktorer**: Vælg en af flere faktorer for at filtrere påmindelseslisten. Indstillingerne er *Akkumuleret udfyldningsaktiviteter**, Aktiviteter* omfatter prioritetsindhold *,* Sekvensaktiviteter og *Aktiviteter omfatter ikke-tilladte domæner*.

## <a name="search-alerts-on-the-alert-dashboard"></a>Søgebeskeder på dashboardet Besked

Hvis du vil søge efter beskedens navn efter et bestemt ord, skal du **vælge kontrolelementet Søg** og skrive det ord, du vil søge efter. Søgeresultaterne viser en eventuel besked om en politik, der indeholder det ord, der er defineret i søgningen.

## <a name="dismiss-multiple-alerts-preview"></a>Afvise flere beskeder (eksempel)

Det kan hjælpe med at spare tid for analytikere og analytikere til straks at afvise flere vigtige beskeder på én gang. Med **indstillingen Afvis** vigtige beskeder på kommandolinjen kan du vælge en eller flere vigtige beskeder med  statussen Skal gennemgå på dashboardet og hurtigt afvise disse vigtige beskeder, så de er relevante i din triageproces. Du kan vælge op til 400 beskeder, du vil afvise, på én gang.

Hvis du vil afvise en insider-risikobesked, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå **til Insider-risikostyring** og vælge **fanen Vigtige** beskeder.
2. På **dashboardet Vigtige beskeder skal** du vælge den besked (eller beskeder) med en *status* for gennemsyn, du vil afvise.
3. På kommandolinjen Beskeder skal du vælge **Afvis vigtige beskeder**.
4. I **detaljeruden Afvis vigtige** beskeder kan du gennemse de bruger- og politikoplysninger, der er knyttet til de valgte beskeder.
5. Vælg **Afvis beskeder** for at løse beskederne med god grund, eller  vælg Annuller for at lukke detaljeruden uden at afvise beskederne.

## <a name="triage-alerts"></a>Beskeder om triage

Hvis du vil finde en besked om insider-risici, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå **til Insider-risikostyring** og vælge **fanen Vigtige** beskeder.
2. På **dashboardet Beskeder skal** du vælge den besked, du vil ændre.
3. På siden **Beskeddetaljer** kan du gennemse oplysninger om beskeden. Du kan bekræfte beskeden og oprette en ny sag, bekræfte beskeden og føje den til en eksisterende sag eller afvise beskeden. Denne side indeholder også den aktuelle status for beskeden og risikoens alvorsniveau, der er angivet som Høj, Mellem eller Lav. Alvorsniveauet kan blive større eller mindre med tiden, hvis beskeden ikke er efterseeret.

Brug følgende afsnit og faner på detaljesiden Besked for at få flere oplysninger om beskeden:

### <a name="headersummary-section"></a>Sektionen Sidehoved/oversigt

Dette afsnit indeholder generelle oplysninger om brugeren og besked. Disse oplysninger er tilgængelige for kontekst, mens du gennemgår detaljerede oplysninger om den registrerede aktivitet, der er inkluderet i beskeden for brugeren:

- **Aktivitet, der genererede denne advarsel**: Viser den hyppigste risikoaktivitet og den største politikmatch under den aktivitetsevalueringsperiode, der førte til den påmindelse, der blev genereret.
- **Udløsende hændelse**: Viser den seneste udløsende hændelse, der har bedt politikken om at begynde at tildele risikoresultater til brugerens aktivitet.
- **Brugerprofil**: Viser generelle oplysninger om den bruger, der er tildelt beskeden. Hvis anonymisering er aktiveret, anonymiseres brugernavnet, mailadressen, aliasset og organisationsfelterne.
- **Oversigt over brugerbeskeder**: Viser en liste over beskeder for brugeren de seneste 30 dage. Indeholder et link til at få vist hele beskedoversigten for brugeren.

### <a name="all-risk-factors"></a>Alle faktorer

Denne fane åbner en oversigt over faktorer for brugerens beskedaktivitet. Risikofaktorer kan hjælpe dig med at afgøre, hvor risikabelt denne brugers aktivitet er under din gennemgang. Risikofaktorerne omfatter oversigter for:

- **Vigtigste udfyldningsaktiviteter**: Viser udfyldningsaktiviteter med det højeste antal eller hændelser for beskeden.
- **Akkumulerede udfyldningsaktiviteter**: Viser hændelser, der er knyttet til akkumulerede udfyldningsaktiviteter.
- **Sekvenser af aktiviteter**: Viser de registrerede aktiviteter, der er knyttet til risikosekvenser.
- **Usædvanlig aktivitet for denne bruger**: Viser aktiviteter for den bruger, der betragtes som usædvanlig, og en afgang fra deres sædvanlige aktiviteter.
- **Prioritetsindhold**: Viser aktiviteter, der er knyttet til prioritetsindhold.
- **Ikke-tilladte domæner**: Viser aktiviteter for hændelser, der er knyttet til ikke-tilladte domæner.
- **Adgang til tilstandsposter**: Viser aktiviteter for hændelser, der er knyttet til adgang til tilstandsposter.

Med disse filtre får du kun vist beskeder om disse faktorer, men den aktivitet, der genererede en besked, falder muligvis ikke ind under nogen af disse kategorier. Eksempelvis kan der være genereret en besked, der indeholder sekvensaktiviteter, blot fordi brugeren har kopieret en fil til en USB-enhed.

### <a name="content-detected"></a>Det registrerede indhold

Afsnittet på fanen **Alle risikofaktorer omfatter** indhold, der er knyttet til risikoaktiviteterne for beskeden og opsummerer aktivitetshændelser efter nøgleområder. Når du vælger et aktivitetslink, åbnes Aktivitetsstifinder, og der vises flere oplysninger om aktiviteten.

### <a name="activity-explorer"></a>Aktivitetsstifinder

Denne fane åbner Aktivitetsstifinder. Du kan finde flere oplysninger i sektionen Aktivitetsstifinder i denne artikel.

### <a name="user-activity"></a>Brugeraktivitet

Diagrammet **Brugeraktivitet** er et af de mest effektive værktøjer til intern risikoanalyse og undersøgelse til beskeder og sager i Insider-risikostyringsløsningen. Denne fane er struktureret til at give mulighed for hurtig gennemgang af alle aktiviteter for en bruger, herunder en historisk tidslinje for alle beskeder, beskedoplysninger, brugerens aktuelle risikoscore og rækkefølgen af risikohændelser.  

![Insider-brugeraktivitet i risikostyring.](../media/insider-risk-user-activities.png)

1. **Tidsfiltre**: Som standard vises de sidste tre måneders aktiviteter i diagrammet Brugeraktivitet. Du kan nemt filtrere diagramvisningen ved at vælge fanerne *6* måneder, *3* måneder eller *1 måned* i boblediagrammet.
2. **Aktivitet og detaljer for risikobeskeder**: Risikoaktiviteter vises visuelt som farvede bobler i diagrammet Brugeraktivitet. Boblerne oprettes for forskellige kategorier af risici og. Vælg en boble for at få vist detaljerne for hver risikoaktivitet. Detaljer omfatter:
    - **Dato** for risikoaktiviteten.
    - Kategorien **for risikoaktivitet**. Eksempelvis mails *med vedhæftede filer*, der er sendt uden for organisationen, eller filer, der *er hentet fra SharePoint Online*.
    - **Risikoresultat** for beskeden. Dette score er den numeriske score for alvorsniveauet for beskedrisici.
    - Antal hændelser, der er knyttet til beskeden. Links til hver fil eller mail, der er knyttet til risikoaktiviteten, er også tilgængelige.
3.  **Filtre og sortering (eksempel)**:
    - **Risikokategori**: Filtrer aktiviteter efter følgende risikokategorier: Aktiviteter med risikoresultater *> 15 (medmindre* i en sekvens) og *Sekvensaktiviteter*.
    - **Aktivitetstype**: Filtrer aktiviteter efter følgende typer: *Adgang**, sletning**, samling*, udfyldning, *infiltration**,* sløring og *sikkerhed*. 
    - **Sortér efter**: Vis tidslinjeaktiviteterne efter *dato eller* *Risikoscore*.
4. **Risikosekvens (forhåndsvisning)**: Den kronologiske rækkefølge af risikabelt aktivitet er et vigtigt aspekt af risikoundersøgelse og identificering af disse relaterede aktiviteter er en vigtig del af evalueringen af den overordnede risiko for din organisation. Påmindelsesaktiviteter, der er relaterede, vises med forbindelseslinjer for at fremhæve, at disse aktiviteter er knyttet til et større risikoområde. Denne visning af aktiviteter kan hjælpe dig med bogstaveligt talt at "forbinde dots" for risikoaktiviteter, der kunne være blevet vist som isolerede eller enkeltstående hændelser. Vælg en boble i rækkefølgen for at få vist detaljer for alle de tilknyttede risikoaktiviteter. Detaljer omfatter:

    - **Navnet** på sekvensen.
    - **Dato** - **eller datointervallet** for sekvensen.
    - **Risikoscore** for sekvensen. Dette score er det numeriske score for sekvensen af de kombinerede risiko alvorsniveauer for hver relateret aktivitet i sekvensen.
    - **Antal hændelser, der er knyttet til hver besked i sekvensen**. Links til hver fil eller mail, der er knyttet til hver risikoaktivitet, er også tilgængelige.
    - **Vis aktiviteter i rækkefølge**. Viser sekvens som en fremhævet linje i boblediagrammet og udvider beskeddetaljerne for at vise alle relaterede beskeder i rækkefølgen.

4. **Forklaring til risikoaktivitet**: Nederst i diagrammet med brugeraktivitet hjælper en farvekodet forklaring dig med hurtigt at bestemme risikokategorien for hver besked.
5. **Kronologi for risikoaktivitet**: Den fulde kronologi for alle risikobeskeder, der er knyttet til sagen, vises, herunder alle de oplysninger, der er tilgængelige i den tilsvarende beskedboble.
6. **Sagshandlinger**: Indstillingerne for løsning af sagen findes på værktøjslinjen til sagshandling. Når du får vist en sag, kan du løse en sag, sende en mail til brugeren eller eskalere sagen til en data- eller brugerundersøgelse.

## <a name="activity-explorer"></a>Aktivitetsstifinder

> [!NOTE]
> Aktivitetsstifinder er tilgængelig i området til administration af beskeder for brugere, der udløser hændelser, efter at denne funktion er tilgængelig i din organisation.

Aktivitetsoversigten giver risikoanalyser og analytikere et omfattende analyseværktøj, der indeholder detaljerede oplysninger om beskeder. Med Aktivitetsoversigt kan korrekturlæsere hurtigt gennemgå en tidslinje for registreret risikabel aktivitet og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder. 

Hvis du vil filtrere beskeder på Aktivitetsstifinder for kolonneoplysninger, skal du vælge filterkontrolelementet. Du kan filtrere beskeder efter en eller flere attributter, der er angivet i detaljeruden for beskeden. Aktivitetsstifinder understøtter også kolonner, der kan tilpasses, for at hjælpe analytikere og analytikere med at fokusere dashboardet på de oplysninger, der er vigtigst for dem.

Brug filtrene Aktivitetsområde og Risikoindsigt til at vise og sortere aktiviteter og indsigt for følgende områder.

- **Filtre for aktivitetsområde**: Filtrerer alle scored aktiviteter for brugeren.
    - Al scored aktivitet for denne bruger
    - Kun scored aktivitet i denne besked

- **Risikofaktorfiltre**: Filtre for risikofaktoraktivitet, der gælder for alle politikker, der tildeler risikoresultater Dette omfatter al aktivitet for alle politikker for brugere med in-omfang.
    - Usædvanlig aktivitet
    - Omfatter begivenheder med prioritetsindhold
    - Omfatter hændelser med ikke-tilladt domæne
    - Sekvensaktiviteter
    - Akkumulerede udfyldningsaktiviteter
    - Adgangsaktiviteter for tilstandspost

![Oversigt over Insiders aktivitetsoversigt for risikostyring.](../media/insider-risk-activity-explorer.png)

Hvis du vil bruge **Aktivitetsstifinder**, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå **til Insider-risikostyring** og vælge **fanen Vigtige** beskeder.
2. På **dashboardet Beskeder skal** du vælge den besked, du vil ændre.
3. I **detaljeruden Beskeder skal** du vælge **Åbn udvidet visning**.
4. Vælg fanen Aktivitetsstifinder på siden for den **valgte** besked.

Når du gennemser aktiviteter i Aktivitetsoversigt, kan analytikere og analytikere vælge en bestemt aktivitet og åbne ruden med aktivitetsdetaljer. Ruden viser detaljerede oplysninger om den aktivitet, som analytikere og analytikere kan bruge under triageprocessen for beskeder. Detaljerede oplysninger kan give kontekst til beskeden og hjælpe med at identificere det fulde omfang af den risikoaktivitet, der udløste beskeden.

Når du vælger en aktivitets begivenheder fra tidslinjen for aktivitet, stemmer antallet af aktiviteter, der vises i Stifinder, muligvis ikke overens med antallet af aktivitetshændelser, der er angivet på tidslinjen. Eksempler på, hvorfor denne forskel kan opstå:

- **Kumulativ** registrering af udfyldning: Registrering af kumulativ udfyldning analyserer hændelseslogfiler, men anvender en model, der omfatter deplikering af lignende aktiviteter for at beregne risikoen for kumulativ udfyldning. Desuden kan der også være en forskel i antallet af aktiviteter, der vises i Aktivitetsoversigt, hvis du har foretaget ændringer i din eksisterende politik eller dine eksisterende indstillinger. Hvis du f.eks. redigerer tilladte/ikke-tilladte domæner eller tilføjer nye filtypefratagelser, når en politik er blevet oprettet, og der er foretaget aktivitets match, vil de kumulative registreringsaktiviteter til registrering af udfyldning afvige fra resultaterne, før politikken eller indstillingerne ændres. Samlet registrering af udfyldningsaktivitetstotaler er baseret på politik- og indstillingskonfigurationen på tidspunktet for beregning og omfatter ikke aktiviteter før ændringer af politik og indstillinger
- **Mails til eksterne** modtagere: Aktivitet for mails, der sendes til eksterne modtagere, tildeles et risikoresultat baseret på antallet af sendte mails, som muligvis ikke svarer til aktivitetshændelseslogfilerne.

![Oplysninger om Insiders aktivitetsoversigt for risikostyring.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Oprette en sag for en besked

Når advarslen gennemses og gennemgås, kan du oprette en ny sag for yderligere at undersøge risikoaktiviteten. Hvis du vil oprette en sag for en besked, skal du følge disse trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå **til Insider-risikostyring** og vælge **fanen Vigtige** beskeder.
2. På **dashboardet Beskeder skal** du vælge den besked, du vil bekræfte og oprette en ny sag for.
3. I **detaljeruden Beskeder skal du** vælge **ActionsConfirm** >  **alerts & create case**.
4. I dialogboksen **Bekræft besked og opret insider-risiko** sag skal du skrive et navn på sagen, vælge brugere, der skal tilføjes som bidragydere, og tilføje kommentarer efter behov. Kommentarer føjes automatisk til sagen som en sagsnote.
5. Vælg **Opret sag for** at oprette en ny sag, eller vælg **Annuller** for at lukke dialogboksen uden at oprette en sag.

Når sagen er oprettet, kan analytikere og analytikere administrere og handle på sagen. Du kan finde flere oplysninger i [insider-case-artiklen om risikostyring](insider-risk-management-cases.md) .

## <a name="retention-and-item-limits"></a>Opbevarings- og elementgrænser

Når insider-risikostyring advarer om alder, er deres værdi for at minimere risikabel aktivitet faldende for de fleste organisationer. Omvendt er aktive sager og tilknyttede artefakter (beskeder, indsigter og aktiviteter) altid værdifulde for organisationer og bør ikke have en automatisk udløbsdato. Dette omfatter alle fremtidige beskeder og artefakter i en aktiv status for alle brugere, der er knyttet til en aktiv sag.

Følgende opbevarings- og begrænsninger gælder for insider-risikostyringsbeskeder, sager og brugeraktivitetsrapporter for at minimere antallet af ældre elementer, der giver begrænset aktuel værdi:

|**Element**|**Opbevaring/begrænsning**|
|:-------|:------------------|
| Beskeder med status for gennemsyn af behov | 120 dage fra oprettelse af besked og derefter automatisk slettet |
| Aktive sager (og tilknyttede artefakter) | Opbevaring på ubestemt tid, udløber aldrig |
| Løste sager (og tilknyttede artefakter) | 120 dage fra sagsløsning og derefter automatisk slettet |
| Maksimale antal aktive sager | 100 |
| Brugeraktivitetsrapporter | 120 dage fra aktivitetsregistrering og derefter automatisk slettet |

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Få hjælp til at administrere din insider-risikoadvarselskø

At gennemgå, undersøge og reagere på insider-risikobeskeder er vigtige dele af at minimere insiderrisici i organisationen. Hvis du hurtigt gør noget for at minimere effekten af disse risici, kan du potentielt spare tid, penge og lovgivningsmæssige eller juridiske konsekvenser for din organisation. I denne afhjælpningsproces kan det første trin til gennemgang af beskeder virke som den mest svære opgave for mange analytikere og analytikere. Afhængigt af din situation kan du være udsat for nogle mindre hindringer, når du handler på insider-risikobeskeder. Gennemgå følgende anbefalinger, og lær, hvordan du optimerer gennemsynsprocessen for beskeder.

### <a name="too-many-alerts-to-review"></a>For mange vigtige beskeder til at blive gennemset

Det kan være frustrerende at blive overvældet af det antal beskeder, der produceres af din Insider-risikostyringspolitik. Antallet af beskeder kan hurtigt håndteres med enkle trin, afhængigt af den type beskedmængde, du modtager. Du modtager muligvis for mange gyldige beskeder eller får for mange forældede beskeder med lav risiko. Overvej at udføre følgende handlinger:

- **Juster dine insider-risikopolitikker**: At vælge og konfigurere den korrekte insider-risikopolitik er den mest grundlæggende metode til at håndtere typen og mængden af beskeder. Når du starter med den [relevante politikskabelon](insider-risk-management-policies.md#policy-templates) , hjælper det med at fokusere på de typer af risikoaktiviteter og beskeder, du vil få vist. Andre faktorer, der kan påvirke lydstyrken for beskeder, er størrelsen på den in-omfangsbaserede bruger og de grupper og det indhold og de kanaler, [der er prioriteret](insider-risk-management-policies.md#prioritize-content-in-policies). Overvej at justere politikker for at afgrænse disse områder til det, der er vigtigst for organisationen.
- **Rediger dine insider-risikoindstillinger**: Indstillinger for Insider-risici omfatter en lang række konfigurationsindstillinger, der kan påvirke mængden og typerne af beskeder, du vil modtage. Disse omfatter indstillinger for [politikindikatorer](insider-risk-management-settings.md#indicators), [indikatortærskler](insider-risk-management-settings.md#indicator-level-settings-preview) og [politiktidsrammer](insider-risk-management-settings.md#policy-timeframes). Overvej at konfigurere [intelligente registreringsindstillinger](insider-risk-management-settings.md#intelligent-detections) for at udelukke bestemte filtyper, definere minimumstærskelværdier, før aktivitetsbeskeder rapporteres af dine politikker, og ændre konfigurationen af beskedmængde til en lavere indstilling.
- **Massesletning af beskeder,** hvor det er relevant: Det kan hjælpe med at spare tid på triagetid for dine analytikere og enheder, så du straks kan afvise [flere vigtige beskeder på](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) én gang. Du kan vælge op til 400 beskeder, du vil afvise, på én gang.

### <a name="not-familiar-with-the-alert-triage-process"></a>Ikke kender til triageprocessen for beskeder

Det er nemt at undersøge og reagere på beskeder i Insider Risk Management:

1. **Gennemse [dashboardet til påmindelser](insider-risk-management-activities.md#alert-dashboard) for vigtige beskeder med statussen Skal gennemgås**. [Filtrer](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter *beskedstatus* , hvis det er nødvendigt for at finde disse typer af beskeder.
2. **Start med beskederne med den højeste alvorsgrad**. [Filtrer](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter *alvorsgrad for besked* , hvis det er nødvendigt for at finde disse typer af beskeder.
3. **Vælg en besked for at finde flere oplysninger og for at gennemgå oplysningerne om beskeden**. Hvis det er nødvendigt, [kan du bruge Aktivitetsstifinder](insider-risk-management-activities.md#activity-explorer) til at gennemse en tidslinje med den tilknyttede risikabel adfærd og til at identificere alle risikoaktiviteter for beskeden.
4. **Reagere på beskeden**. Du kan enten bekræfte [og oprette en sag](insider-risk-management-activities.md#create-a-case-for-an-alert) for beskeden eller afvise og løse beskeden.

### <a name="resource-constraints-in-my-organization"></a>Ressourcebegrænsninger i min organisation

Brugere af den moderne arbejdsplads har ofte en lang række ansvarsområder og krav på deres tid. Der er flere handlinger, du kan udføre for at afhjælpe ressourcebegrænsninger:

- **Fokusanalytiker- og analyseindsatser på de højeste risikobeskeder først**. Afhængigt af dine politikker kan du registrere aktiviteter og generere beskeder med forskellige grader af potentiel indvirkning på din risikoreduceringsindsats. [Filtrer beskeder](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter alvorsgrad, og prioriter *vigtige beskeder om høj* alvorsgrad.
- **Tildel brugere som analytikere og makroer**. At have den rigtige bruger tildelt de rette roller er en vigtig del af gennemgangsprocessen for insider-risikobeskeder. Sørg for, at du har tildelt de relevante brugere til *rollegrupperne Insider Risk Management-analytikere* og *insider-risikohåndteringsgrupper* .  
- **Brug automatiserede insider-risikofunktioner til at opdage de aktiviteter, der er størst risiko for**. Registrering af [Insider-risikostyringssekvenser](insider-risk-management-policies.md#sequence-detection-preview) og [funktioner](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) til registrering af kumulativ udfyldning kan hjælpe dig med hurtigt at opdage sværere at finde risici i organisationen. Overvej at finjustere [dine risikoscores](insider-risk-management-settings.md#indicators), [udeladelse](insider-risk-management-settings.md#file-type-exclusions) af filtyper, domæner og minimumsindstillingerne for [indikatortærskelværdier](insider-risk-management-settings.md#domains) for dine politikker.[](insider-risk-management-settings.md#indicator-level-settings-preview)
