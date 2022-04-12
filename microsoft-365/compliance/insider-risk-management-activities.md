---
title: Undersøg insiderrisikostyringsaktiviteter
description: Få mere at vide om undersøgelse af insiderrisikostyringsaktiviteter i Microsoft 365
keywords: Microsoft 365, insiderrisiko, risikostyring, overholdelse af angivne standarder
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
ms.openlocfilehash: b53b67433bea08e20b082f555c26d41edce55daa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783331"
---
# <a name="investigate-insider-risk-management-activities"></a>Undersøg insiderrisikostyringsaktiviteter

Undersøgelse af risikable brugeraktiviteter er et vigtigt første skridt til at minimere insiderrisici for din organisation. Disse risici kan være aktiviteter, der genererer beskeder fra politikker for styring af insiderrisiko eller risici fra aktiviteter, der registreres af politikker, men ikke straks opretter en insiderrisikostyringsbesked til brugerne. Du kan undersøge disse typer aktiviteter ved hjælp af **brugeraktivitetsrapporterne (prøveversion)** eller med **dashboardet Besked**.

## <a name="user-activity-reports-preview"></a>Brugeraktivitetsrapporter (prøveversion)

Brugeraktivitetsrapporter giver dig mulighed for at undersøge aktiviteter for bestemte brugere i en defineret tidsperiode uden at skulle tildele dem midlertidigt eller eksplicit til en insiderrisikostyringspolitik. I de fleste insiderrisikostyringsscenarier er brugerne eksplicit defineret i politikker, og de kan have politikbeskeder (afhængigt af udløsende hændelser) og risikoscores, der er knyttet til aktiviteterne. Men i nogle scenarier kan det være en god idé at undersøge aktiviteterne for brugere, der ikke udtrykkeligt er defineret i en politik. Disse aktiviteter kan være for brugere, som du har modtaget et tip om brugeren og potentielt risikable aktiviteter, eller brugere, der normalt ikke behøver at blive tildelt en insiderrisikostyringspolitik.

Når du har konfigureret indikatorer på siden **styring af** insiderrisiko Indstillinger side, registreres brugeraktivitet for risikable aktiviteter, der er knyttet til de valgte indikatorer. Du behøver ikke at konfigurere en politik for brugeraktivitetsrapporter for at registrere og rapportere risikable aktiviteter for brugere i din organisation. Aktiviteter, der er inkluderet i brugeraktivitetsrapporter, kræver ikke, at udløsende hændelser for aktiviteterne vises. Denne konfiguration betyder, at al registreret aktivitet for brugeren er tilgængelig til gennemsyn, uanset om den har en udløsende hændelse, eller om den opretter en besked. Rapporter oprettes pr. bruger og kan omfatte alle aktiviteter for en brugerdefineret periode på 90 dage. Flere rapporter for den samme bruger understøttes ikke.

Efter undersøgelse af aktiviteter for en bruger kan efterforskere afvise individuelle aktiviteter som godartede, dele eller sende et link til rapporten via mail med andre efterforskere eller vælge at tildele brugeren midlertidigt eller eksplicit til en insiderrisikostyringspolitik. Brugerne skal være tildelt rollegruppen *Insider Risk Management Investigators* for at få vist siden **Brugeraktivitetsrapporter** .  

![Oversigt over brugeraktivitetsrapport for styring af insiderrisiko.](../media/insider-risk-user-activity-report-overview.png)

Du kan komme i gang ved at vælge **Administrer rapporter** i afsnittet **Undersøg brugeraktivitet** på siden **Oversigt over** styring af insiderrisiko. Hvis du vil have vist aktiviteter for en bruger, skal du først vælge **Opret brugeraktivitetsrapport** og udfylde følgende felter i ruden **Rapport over ny brugeraktivitet** :

- **Bruger**: Søg efter en bruger efter navn eller mailadresse
- **Startdato**: Brug kalenderkontrolelementet til at vælge startdatoen for brugeraktiviteter.
- **Slutdato**: Brug kalenderkontrolelementet til at vælge slutdatoen for brugeraktiviteter. Den valgte slutdato skal være større end to dage efter den valgte startdato og højst 90 dage fra den valgte startdato.
Det tager typisk op til 10 timer, før nye rapporter er klar til gennemsyn. Når rapporten er klar, kan du se *Rapport klar* i kolonnen **Status** på siden Brugeraktivitetsrapport. Vælg brugeren for at få vist den detaljerede rapport:

![Brugeraktivitetsrapport for styring af insiderrisiko.](../media/insider-risk-user-activity-report.png)

**Brugeraktivitetsrapporten** for den valgte bruger indeholder fanerne **Brugeraktivitet** og **Aktivitetsoversigt**:

- **Brugeraktivitet**: Brug denne diagramvisning til at undersøge aktiviteter og få vist potentielle aktiviteter, der forekommer i sekvenser. Denne fane er struktureret til at muliggøre hurtig gennemgang af en sag, herunder en oversigt over alle aktiviteter, aktivitetsoplysninger, den aktuelle risikoscore for brugeren i sagen, rækkefølgen af risikohændelser og filtreringskontrolelementer som en hjælp til undersøgelsesindsatsen.
- **Aktivitetsoversigt**: Fanen **Aktivitetsoversigt** giver risikoforskere et omfattende analyseværktøj, der indeholder detaljerede oplysninger om aktiviteter. Med Aktivitetsoversigt kan korrekturlæsere hurtigt gennemse en tidslinje over registreret risikable aktiviteter og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder. Du kan få mere at vide om brug af Aktivitetsoversigt i afsnittet *Aktivitetsoversigt* senere i denne artikel.

## <a name="alert-dashboard"></a>Advarselsdashboard

Insiderrisikostyringsbeskeder genereres automatisk af risikoindikatorer, der er defineret i politikker for styring af insiderrisiko. Disse beskeder giver overholdelsesanalytikere og efterforskere en samlet visning af den aktuelle risikostatus og gør det muligt for din organisation at prioritere og udføre handlinger for registrerede risici. Politikker genererer som standard en vis mængde beskeder om lav, mellem og høj alvorsgrad, men du kan [øge eller reducere mængden af beskeder](insider-risk-management-settings.md#alert-volume) , så den passer til dine behov. Du kan også konfigurere [beskedtærsklen for politikindikatorer](insider-risk-management-settings.md#indicator-level-settings-preview) , når du opretter en ny politik med værktøjet til oprettelse af politikker.

Se [videoen Insider Risk Management Alerts Triage Experience](https://www.youtube.com/watch?v=KgmpxBLJLPI) for at få en oversigt over, hvordan beskeder indeholder oplysninger, kontekst og relateret indhold til risikable aktiviteter, og hvordan du kan gøre din undersøgelsesproces mere effektiv.

**Dashboardet med insiderrisikoadvarsel** giver dig mulighed for at få vist og reagere på beskeder, der genereres af politikker for insiderrisiko. Hver rapportwidget viser oplysninger for de seneste 30 dage.

- **Samlet antal beskeder, der skal gennemses**: Det samlede antal beskeder, der skal gennemses og sorteres, vises, herunder en opdeling efter alvorsgrad af beskeder.
- **Åbne beskeder over de seneste 30 dage**: Det samlede antal beskeder, der er oprettet af politikforekomster i løbet af de sidste 30 dage, sorteret efter niveauer for høj, mellem og lav besked alvorsgrad.
- **Gennemsnitlig tid til at løse beskeder**: En oversigt over nyttige beskedstatistikker:
  - Den gennemsnitlige tid til at løse vigtige beskeder med høj alvorsgrad angivet i timer, dage eller måneder.
  - Den gennemsnitlige tid til at løse beskeder om medium alvorsgrad angivet i timer, dage eller måneder.
  - Den gennemsnitlige tid til at løse vigtige beskeder med lav alvorsgrad angivet i timer, dage eller måneder.

![Advarselsdashboard for styring af insiderrisiko.](../media/insider-risk-alerts-dashboard.png)

> [!NOTE]
> Styring af insiderrisiko bruger indbygget begrænsning af vigtige beskeder til at beskytte og optimere din risikoanalyse og gennemgangsoplevelse. Denne begrænsning beskytter mod problemer, der kan resultere i en overbelastning af politikbeskeder, f.eks. forkert konfigurerede dataconnectors eller DLP-politikker. Derfor kan der være en forsinkelse i visningen af nye beskeder for en bruger.

## <a name="alert-status-and-severity"></a>Beskedstatus og alvorsgrad

Du kan opdele beskeder i en af følgende statusser:

- **Bekræftet**: En besked, der er bekræftet og tildelt en ny eller eksisterende sag.
- **Afvist**: En besked blev afvist som godartet i triageprocessen. Du kan angive en årsag til afskedigelsen af beskeden og medtage noter, der er tilgængelige i brugerens beskedoversigt, for at angive yderligere kontekst for fremtidig reference eller for andre korrekturlæsere. Disse årsager kan variere fra forventede aktiviteter, ikke-virkningsfulde hændelser, blot at reducere antallet af beskedaktiviteter for brugeren eller en årsag, der er relateret til beskednoterne. Årsagsklassificeringsvalg omfatter *Aktivitet er forventet for denne bruger*, *Aktivitet er så virkningsfuld, at jeg kan undersøge det nærmere*, og *Beskeder for denne bruger indeholder for meget aktivitet*.
- **Behov for gennemsyn**: En ny besked, hvor der endnu ikke er foretaget triagehandlinger.
- **Løst**: En besked, der er en del af en lukket og afsluttet sag.

Scorer for advarselsrisici beregnes automatisk ud fra flere indikatorer for risikoaktivitet. Disse indikatorer omfatter typen af risikoaktivitet, antallet og hyppigheden af aktivitetens forekomst, historikken for brugerrisikoaktivitet og tilføjelsen af aktivitetsrisici, der kan øge aktivitetens alvor. Scoren for advarselsrisikoen styrer programmatisk tildeling af et niveau for risiko alvorsgrad for hver besked og kan ikke tilpasses. Hvis beskeder forbliver uprøvede, og risikoaktiviteterne fortsat tilfalder beskeden, kan niveauet for risiko alvorsgrad øges. Risikoanalytikere og efterforskere kan bruge alvorsgraden af advarselsrisici til at hjælpe med at håndtere vigtige beskeder i overensstemmelse med organisationens risikopolitikker og standarder.

Niveauerne for beskedrisikoens alvorsgrad er:

- **Høj alvorsgrad**: Aktiviteterne og indikatorerne for beskeden udgør en betydelig risiko. De dertil knyttede risikoaktiviteter er alvorlige, gentagne og tæt forbundet med andre væsentlige risikofaktorer.
- **Mellem alvorlighed**: Aktiviteterne og indikatorerne for beskeden udgør en moderat risiko. De tilknyttede risikoaktiviteter er moderate, hyppige og har en vis korrelation til andre risikofaktorer.
- **Lav alvorsgrad**: Aktiviteterne og indikatorerne for beskeden udgør en mindre risiko. De tilknyttede risikoaktiviteter er mindre, mere sjældne og er ikke knyttet til andre væsentlige risikofaktorer.

## <a name="filter-alerts-on-the-alert-dashboard"></a>Filtrer beskeder på dashboardet Vigtig besked

Det kan være en udfordring at gennemgå en stor kø af beskeder, afhængigt af antallet og typen af aktive politikker for styring af insiderrisiko i din organisation. Brug af beskedfiltre kan hjælpe analytikere og efterforskere med at sortere beskeder efter flere attributter. Hvis du vil filtrere beskeder på **dashboardet Beskeder**, skal du vælge kontrolelementet **Filter** . Du kan filtrere beskeder efter en eller flere attributter:

- **Status**: Vælg en eller flere statusværdier for at filtrere beskedlisten. Indstillingerne er *Bekræftet*, *Afvist*, *Skal gennemses* og *Løst*.
- **Alvorsgrad**: Vælg et eller flere niveauer af beskedrisikoen for at filtrere beskedlisten. Indstillingerne er *Høj*, *Mellem* og *Lav*.
- **Registreret tid**: Vælg start- og slutdatoer for, hvornår beskeden blev oprettet. Dette filter søger efter beskeder mellem UTC 00:00 på startdatoen og UTC 00:00 på slutdatoen. Hvis du vil filtrere beskeder for en bestemt dag, skal du angive datoen for dagen i feltet **Startdato** og datoen for den følgende dag i feltet **Slutdato** .
- **Politik**: Vælg en eller flere politikker for at filtrere de beskeder, der genereres af de valgte politikker.
- **Risikofaktorer**: Vælg en af flere risikofaktorer for at filtrere beskedlisten. Indstillingerne er *Akkumulerede exfiltrationsaktiviteter*, *aktiviteter omfatter prioriteret indhold*, *sekvensaktiviteter* og *aktiviteter omfatter ikke-tilladte domæner*.

## <a name="search-alerts-on-the-alert-dashboard"></a>Søg efter beskeder på dashboardet Vigtig besked

Hvis du vil søge efter et bestemt ord i beskednavnet, skal du vælge kontrolelementet **Søg** og skrive det ord, der skal søges efter. Søgeresultaterne viser alle politikbeskeder, der indeholder det ord, der er defineret i søgningen.

## <a name="dismiss-multiple-alerts-preview"></a>Afvis flere beskeder (prøveversion)

Det kan hjælpe med at spare tid for analytikere og efterforskere til straks at afvise flere beskeder på én gang. Med kommandolinjeindstillingen **Afvis beskeder** kan du vælge en eller flere beskeder med statussen *Behovsgennemgang* på dashboardet og hurtigt afvise disse beskeder efter behov i din triageproces. Du kan vælge op til 400 beskeder, der skal afvises på én gang.

Hvis du vil afvise en insiderrisikobesked, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Beskeder**.
2. På **dashboardet Beskeder** skal du vælge den besked (eller de beskeder) med statussen *Behovsgennemgang* , som du vil afvise.
3. Vælg **Afvis beskeder** på kommandolinjen Beskeder.
4. I detaljeruden **Afvis beskeder** kan du gennemse de bruger- og politikoplysninger, der er knyttet til de valgte beskeder.
5. Vælg **Afvis beskeder** for at løse beskederne som godartede, eller vælg **Annuller** for at lukke detaljeruden uden at afvise beskederne.

## <a name="triage-alerts"></a>Vigtige beskeder

Hvis du vil triage en insiderrisikobesked, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Beskeder**.
2. Vælg den besked, du vil triage, på **dashboardet Beskeder**.
3. På siden **Beskedoplysninger** kan du gennemse oplysninger om beskeden. Du kan bekræfte beskeden og oprette en ny sag, bekræfte beskeden og føje den til en eksisterende sag eller afvise beskeden. Denne side indeholder også den aktuelle status for beskeden og alvorsgraden af beskedrisikoen angivet som Høj, Mellem eller Lav. Alvorsgraden kan stige eller falde over tid, hvis beskeden ikke er triaged.

Brug følgende afsnit og faner på siden Beskedoplysninger for at få flere oplysninger om beskeden:

### <a name="headersummary-section"></a>Sidehoved-/oversigtssektion

Dette afsnit indeholder generelle oplysninger om brugeren og beskeden. Disse oplysninger er tilgængelige i kontekst under gennemgang af detaljerede oplysninger om den registrerede aktivitet, der er inkluderet i beskeden for brugeren:

- **Aktivitet, der genererede denne besked**: Viser den aktivitet og politik for største risiko, der matcher i den aktivitetsevalueringsperiode, der førte til, at beskeden blev genereret.
- **Udløsende hændelse**: Viser den seneste udløsende hændelse, der har bedt politikken om at begynde at tildele risikoscores til brugerens aktivitet.
- **Brugerprofil**: Viser generelle oplysninger om den bruger, der er tildelt beskeden. Hvis anonymisering er aktiveret, anonymiseres felterne brugernavn, mailadresse, alias og organisation.
- **Oversigt over brugerbeskeder**: Viser en liste over beskeder for brugeren for de seneste 30 dage. Indeholder et link til at få vist hele beskedoversigten for brugeren.

### <a name="all-risk-factors"></a>Alle risikofaktorer

Under denne fane åbnes en oversigt over risikofaktorer for brugerens beskedaktivitet. Risikofaktorer kan hjælpe dig med at afgøre, hvor risikabel denne brugers aktivitet er under din gennemgang. Risikofaktorerne omfatter oversigter over:

- **Vigtigste exfiltrationsaktiviteter**: Viser exfiltrationsaktiviteter med det højeste antal eller hændelser for beskeden.
- **Akkumulerede exfiltrationsaktiviteter**: Viser hændelser, der er knyttet til akkumulerede eksfiltrationsaktiviteter.
- **Sekvenser af aktiviteter**: Viser de registrerede aktiviteter, der er knyttet til risikosekvenser.
- **Usædvanlig aktivitet for denne bruger**: Viser aktiviteter for brugeren, der anses for at være usædvanlige, og som er en afvigelse fra deres sædvanlige aktiviteter.
- **Prioritetsindhold**: Viser aktiviteter, der er knyttet til prioriteret indhold.
- **Ikke-tilladte domæner**: Viser aktiviteter for hændelser, der er knyttet til ikke-tilladte domæner.
- **Adgang til tilstandspost**: Viser aktiviteter for hændelser, der er knyttet til adgang til tilstandsposter.

Med disse filtre kan du kun se beskeder med disse risikofaktorer, men den aktivitet, der genererede en besked, falder muligvis ikke ind under nogen af disse kategorier. En besked, der indeholder sekvensaktiviteter, kan f.eks. være genereret, blot fordi brugeren har kopieret en fil til en USB-enhed.

### <a name="content-detected"></a>Registreret indhold

Afsnittet under fanen **Alle risikofaktorer** indeholder indhold, der er knyttet til risikoaktiviteterne for beskeden, og opsummerer aktivitetshændelser efter nøgleområder. Når du vælger et aktivitetslink, åbnes Aktivitetsoversigt, og der vises flere oplysninger om aktiviteten.

### <a name="activity-explorer"></a>Aktivitetsoversigt

Denne fane åbner Aktivitetsoversigt. Du kan få flere oplysninger i afsnittet Aktivitetsoversigt i denne artikel.

### <a name="user-activity"></a>Brugeraktivitet

Diagrammet **Brugeraktivitet** er et af de mest effektive værktøjer til intern risikoanalyse og undersøgelse af beskeder og sager i løsningen til styring af insiderrisiko. Denne fane er struktureret til at muliggøre hurtig gennemgang af alle aktiviteter for en bruger, herunder en oversigt over alle beskeder, beskedoplysninger, den aktuelle risikoscore for brugeren og sekvensen af risikohændelser.  

![Brugeraktivitet i styring af insiderrisiko.](../media/insider-risk-user-activities.png)

1. **Tidsfiltre**: Som standard de sidste tre måneder med aktiviteter, der vises i diagrammet Brugeraktivitet. Du kan nemt filtrere diagramvisningen ved at vælge fanerne *6 måneder*, *3 måneder* eller *1 måned* i boblediagrammet.
2. **Aktivitet og oplysninger om risikobeskeder**: Risikoaktiviteter vises visuelt som farvede bobler i diagrammet Brugeraktivitet. Bobler oprettes for forskellige kategorier af risici og. Vælg en boble for at få vist detaljerne for hver risikoaktivitet. Detaljer omfatter:
    - **Dato** for risikoaktiviteten.
    - **Kategorien Risikoaktivitet**. Det kan f.eks. være *mails med vedhæftede filer, der er sendt uden for organisationen*, eller *filer, der er downloadet fra SharePoint Online*.
    - **Risikoscore** for beskeden. Denne score er den numeriske score for alvorsgraden af beskedrisikoen.
    - Antal hændelser, der er knyttet til beskeden. Der er også links til hver fil eller mail, der er knyttet til risikoaktiviteten.
3. **Filtre og sortering (prøveversion)**:
    - **Risikokategori**: Filtrer aktiviteter efter følgende risikokategorier: *Aktiviteter med risikoscores > 15 (medmindre i en sekvens)* og *sekvensaktiviteter*.
    - **Aktivitetstype**: Filtrer aktiviteter efter følgende typer: *Adgang*, *Sletning*, *Samling*, *Eksfiltration*, *Infiltration*, *Obfuscation* og *Security*.
    - **Sortér efter**: Vis tidslinjeaktiviteter efter *Dato for indtraf* eller *Risikoscore*.
4. **Risikosekvens (prøveversion)**: Den kronologiske rækkefølge af risikable aktiviteter er et vigtigt aspekt af risikoundersøgelsen, og identificering af disse relaterede aktiviteter er en vigtig del af evalueringen af den overordnede risiko for din organisation. Vigtige aktiviteter, der er relateret, vises med forbindelseslinjer for at fremhæve, at disse aktiviteter er knyttet til et større risikoområde. Denne visning af aktiviteter kan hjælpe efterforskerne med bogstaveligt talt at "forbinde prikkerne" for risikoaktiviteter, der kunne være blevet betragtet som isolerede eller engangshændelser. Vælg en boble i sekvensen for at få vist oplysninger om alle de tilknyttede risikoaktiviteter. Detaljer omfatter:

    - **Navnet på** sekvensen.
    - **Dato** eller **datointerval** for sekvensen.
    - **Risikoscore** for sekvensen. Denne score er den numeriske score for rækkefølgen af niveauerne for den kombinerede beskedrisikos alvorsgrad for hver relateret aktivitet i sekvensen.
    - **Antal hændelser, der er knyttet til hver besked i sekvensen**. Der er også links til hver fil eller mail, der er knyttet til hver risikoaktivitet.
    - **Vis aktiviteter i rækkefølge**. Viser sekvensen som en fremhævningslinje i boblediagrammet og udvider beskedoplysningerne for at få vist alle relaterede beskeder i sekvensen.

5. **Forklaring af risikoaktivitet**: Nederst i brugeraktivitetsdiagrammet hjælper en farvekodet forklaring dig med hurtigt at bestemme risikokategorien for hver besked.
6. **Kronologi for risikoaktivitet**: Den fulde kronologi af alle risikobeskeder, der er knyttet til sagen, vises, herunder alle de oplysninger, der er tilgængelige i den tilsvarende beskedboble.
7. **Sagshandlinger**: Indstillingerne for løsning af sagen findes på værktøjslinjen til sagshandling. Når du får vist i en sag, kan du løse en sag, sende en meddelelse via mail til brugeren eller eskalere sagen for en data- eller brugerundersøgelse.

## <a name="activity-explorer"></a>Aktivitetsoversigt

> [!NOTE]
> Aktivitetsoversigt er tilgængelig i området administration af beskeder for brugere med udløsende hændelser, når denne funktion er tilgængelig i din organisation.

Aktivitetsoversigten giver risikoforskere og analytikere et omfattende analyseværktøj, der indeholder detaljerede oplysninger om beskeder. Med Aktivitetsoversigt kan korrekturlæsere hurtigt gennemse en tidslinje over registreret risikable aktiviteter og identificere og filtrere alle risikoaktiviteter, der er knyttet til beskeder. 

Hvis du vil filtrere beskeder i Aktivitetsoversigt for kolonneoplysninger, skal du vælge kontrolelementet Filter. Du kan filtrere beskeder efter en eller flere attributter, der er angivet i detaljeruden for beskeden. Aktivitetsoversigt understøtter også kolonner, der kan tilpasses, for at hjælpe efterforskere og analytikere med at fokusere dashboardet på de oplysninger, der er vigtigst for dem.

Brug filtrene Aktivitetsområde og Risikoindsigt til at få vist og sortere aktiviteter og indsigt for følgende områder.

- **Filtre for aktivitetsområde**: Filtrerer alle scorede aktiviteter for brugeren.
  - Alle aktiviteter med score for denne bruger
  - Kun scoret aktivitet i denne besked

- **Filtre for risikofaktor**: Filtre for risikofaktoraktivitet, der gælder for alle politikker, der tildeler risikoscores Dette omfatter alle aktiviteter for alle politikker for brugere i området.
  - Usædvanlig aktivitet
  - Omfatter hændelser med prioriteret indhold
  - Medtager hændelser med ikke-tilladt domæne
  - Sekvensaktiviteter
  - Akkumulerede eksfiltrationsaktiviteter
  - Aktiviteter for adgang til tilstandsposter

![Oversigt over aktivitetsoversigt for styring af insiderrisikostyring.](../media/insider-risk-activity-explorer.png)

Hvis du vil bruge **Aktivitetsoversigt**, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Beskeder**.
2. Vælg den besked, du vil triage, på **dashboardet Beskeder**.
3. I **detaljeruden Beskeder** skal du vælge **Åbn udvidet visning**.
4. Vælg fanen **Aktivitetsoversigt** på siden for den valgte besked.

Når du gennemser aktiviteter i Aktivitetsoversigt, kan efterforskere og analytikere vælge en bestemt aktivitet og åbne ruden med aktivitetsoplysninger. Ruden viser detaljerede oplysninger om den aktivitet, som efterforskere og analytikere kan bruge under processen til vigtige beskeder. Detaljerede oplysninger kan give kontekst for beskeden og hjælpe med at identificere det fulde omfang af den risikoaktivitet, der udløste beskeden.

Når du vælger en aktivitets hændelser på aktivitetstidslinjen, stemmer antallet af aktiviteter, der vises i stifinderen, muligvis ikke overens med antallet af aktivitetshændelser, der er angivet på tidslinjen. Eksempler på, hvorfor denne forskel kan opstå:

- **Akkumuleret eksfiltrationsregistrering**: Kumulativ eksfiltrationsregistrering analyserer hændelseslogge, men anvender en model, der omfatter de-duplikering af lignende aktiviteter som beregnings kumulativ eksfiltrationsrisiko. Derudover kan der også være en forskel i antallet af aktiviteter, der vises i Aktivitetsoversigt, hvis du har foretaget ændringer af din eksisterende politik eller dine eksisterende indstillinger. Hvis du f.eks. ændrer tilladte/ikke-tilladte domæner eller tilføjer nye undtagelser for filtyper, når der er oprettet en politik, og der er opstået aktivitetsforekomster, vil de akkumulerede aktiviteter til registrering af eksfiltration afvige fra resultaterne, før politikken eller indstillingerne ændres. Samlede aktivitetstotaler for eksfiltrationsregistrering er baseret på konfigurationen af politikken og indstillingerne på beregningstidspunktet og omfatter ikke aktiviteter før ændringerne af politikken og indstillingerne
- **Mails til eksterne modtagere**: Aktivitet for mails, der sendes til eksterne modtagere, tildeles en risikoscore baseret på antallet af sendte mails, som muligvis ikke stemmer overens med aktivitetshændelsesloggene.

![Oplysninger om insiderrisikostyringsaktivitetsoversigt.](../media/insider-risk-activity-explorer-details.png)

## <a name="create-a-case-for-an-alert"></a>Opret en sag for en besked

Når beskeden gennemses og behandles, kan du oprette en ny sag for at undersøge risikoaktiviteten yderligere. Følg disse trin for at oprette en sag for en besked:

1. I [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Beskeder**.
2. På **dashboardet Beskeder** skal du vælge den besked, du vil bekræfte og oprette en ny sag for.
3. I **ruden Beskedoplysninger** skal du vælge **HandlingerBekræft** >  **beskeder & oprette sag**.
4. I dialogboksen **Bekræft besked, og opret insiderrisikosag** skal du angive et navn til sagen, vælge brugere, der skal tilføjes som bidragydere, og tilføje kommentarer efter behov. Kommentarer føjes automatisk til sagen som en sagsnote.
5. Vælg **Opret sag** for at oprette en ny sag, eller vælg **Annuller** for at lukke dialogboksen uden at oprette en sag.

Når sagen er oprettet, kan efterforskere og analytikere administrere og handle på sagen. Du kan få flere oplysninger i artiklen [Insider Risk Management Case](insider-risk-management-cases.md) .

## <a name="retention-and-item-limits"></a>Opbevarings- og elementgrænser

Da insiderrisikostyring giver besked om alder, mindskes deres værdi for at minimere risikofyldte aktiviteter for de fleste organisationer. Omvendt er aktive sager og tilknyttede artefakter (beskeder, indsigt, aktiviteter) altid værdifulde for organisationer og bør ikke have en automatisk udløbsdato. Dette omfatter alle fremtidige beskeder og artefakter i en aktiv status for alle brugere, der er knyttet til en aktiv sag.

For at hjælpe med at minimere antallet af ældre elementer, der giver begrænset aktuel værdi, gælder følgende opbevaring og grænser for insiderrisikostyringsbeskeder, sager og brugeraktivitetsrapporter:

|Element|Opbevaring/begrænsning|
|---|---|
|Status for gennemsyn af beskeder med behov|120 dage fra oprettelsen af beskeden og derefter slettet automatisk|
|Aktive sager (og tilknyttede artefakter)|Ubestemt opbevaring, udløber aldrig|
|Afsluttede sager (og tilknyttede artefakter)|120 dage fra sagsløsningen og derefter slettet automatisk|
|Maksimalt antal aktive sager|100|
|Rapporter over brugeraktiviteter|120 dage fra aktivitetsregistrering og derefter slettet automatisk|

## <a name="get-help-managing-your-insider-risk-alert-queue"></a>Få hjælp til at administrere din kø for insiderrisikobeskeder

Gennemgang, undersøgelse og agering på insiderrisikobeskeder er vigtige dele af minimering af insiderrisici i din organisation. Hurtig handling for at minimere virkningen af disse risici kan potentielt spare tid, penge og lovgivningsmæssige eller juridiske konsekvenser for din organisation. I denne afhjælpningsproces kan det første trin i gennemgangen af beskeder virke som den vanskeligste opgave for mange analytikere og efterforskere. Afhængigt af dine omstændigheder kan du blive udsat for nogle mindre hindringer, når du handler på insiderrisikobeskeder. Gennemse følgende anbefalinger, og få mere at vide om, hvordan du optimerer processen til gennemgang af beskeder.

### <a name="too-many-alerts-to-review"></a>Der er for mange beskeder til, at de kan gennemses

Det kan være frustrerende at blive overvældet over det antal beskeder, der oprettes af politikker for styring af insiderrisiko. Antallet af beskeder kan håndteres hurtigt med enkle trin, afhængigt af de typer beskeder, du modtager. Du modtager muligvis for mange gyldige beskeder eller har for mange uaktuelle beskeder med lav risiko. Overvej at gøre følgende:

- **Juster politikker for insiderrisiko**: Valg og konfiguration af den korrekte politik for insiderrisiko er den mest grundlæggende metode til at håndtere typen og mængden af beskeder. Når du starter med den relevante [politikskabelon](insider-risk-management-policies.md#policy-templates) , hjælper det med at fokusere på de typer af risikoaktiviteter og beskeder, du får vist. Andre faktorer, der kan påvirke mængden af beskeder, er størrelsen af brugere og grupper i området samt det indhold og de [kanaler, der prioriteres](insider-risk-management-policies.md#prioritize-content-in-policies). Overvej at justere politikker for at tilpasse disse områder til det, der er vigtigst for din organisation.
- **Rediger indstillingerne for insiderrisiko**: Indstillinger for insiderrisiko omfatter en lang række konfigurationsindstillinger, der kan påvirke mængden og typerne af beskeder, du modtager. Disse omfatter indstillinger for [politikindikatorer](insider-risk-management-settings.md#indicators), [indikatortærskler](insider-risk-management-settings.md#indicator-level-settings-preview) og [politiktidsrammer](insider-risk-management-settings.md#policy-timeframes). Overvej at konfigurere indstillinger for [intelligente registreringer](insider-risk-management-settings.md#intelligent-detections) for at udelade bestemte filtyper, definer minimumgrænser, før aktivitetsbeskeder rapporteres af dine politikker, og skift konfigurationen af beskedmængden til en lavere indstilling.
- **Massesletning af beskeder, hvor det er relevant**: Det kan hjælpe med at spare tid for dine analytikere og efterforskere til straks at [afvise flere beskeder](insider-risk-management-activities.md#dismiss-multiple-alerts-preview) på én gang. Du kan vælge op til 400 beskeder, der skal afvises på én gang.

### <a name="not-familiar-with-the-alert-triage-process"></a>Ikke bekendt med processen for vigtige beskeder

Det er nemt at undersøge og reagere på beskeder i styring af insiderrisiko:

1. **Gennemse [beskeddashboardet](insider-risk-management-activities.md#alert-dashboard) for beskeder med statussen Behovsgennemgang**. [Filtrer](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter *beskedstatus* , hvis det er nødvendigt for at hjælpe med at finde disse typer beskeder.
2. **Start med beskederne med den højeste alvorsgrad**. [Filtrer](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter *besked alvorsgrad* , hvis det er nødvendigt for at hjælpe med at finde disse typer beskeder.
3. **Vælg en besked for at finde flere oplysninger og gennemse oplysningerne om beskeden**. Hvis det er nødvendigt, kan du bruge [Aktivitetsoversigt](insider-risk-management-activities.md#activity-explorer) til at gennemse en tidslinje over den tilknyttede risikable funktionsmåde og til at identificere alle risikoaktiviteter for beskeden.
4. **Handle på beskeden**. Du kan enten bekræfte og [oprette en sag](insider-risk-management-activities.md#create-a-case-for-an-alert) for beskeden eller afvise og løse beskeden.

### <a name="resource-constraints-in-my-organization"></a>Ressourcebegrænsninger i min organisation

Moderne brugere på arbejdspladsen har ofte en lang række ansvarsområder og krav til deres tid. Der er flere handlinger, du kan udføre for at hjælpe med at løse ressourcebegrænsninger:

- **Fokusanalytiker og efterforsker indsats på den højeste risiko beskeder først**. Afhængigt af dine politikker kan du registrere aktiviteter og generere beskeder med varierende grader af potentiel indvirkning på din risikomitigeringsindsats. [Filtrer beskeder](insider-risk-management-activities.md#filter-alerts-on-the-alert-dashboard) efter alvorsgrad, og prioriter vigtige beskeder med *høj alvorsgrad* .
- **Tildel brugere som analytikere og efterforskere**. Det er en vigtig del af gennemgangsprocessen for insiderrisikobeskeder, at den rette bruger er tildelt de korrekte roller. Sørg for, at du har tildelt de relevante brugere til rollegrupperne *Insider Risk Management Analysts* og *Insider Risk Management Investigators* .  
- **Brug automatiserede insiderrisikofunktioner til at finde de højeste risikoaktiviteter**. [Sekvensregistrering](insider-risk-management-policies.md#sequence-detection-preview) af insiderrisikostyring og [akkumulerede funktioner til registrering af eksfiltration](insider-risk-management-policies.md#cumulative-exfiltration-detection-preview) kan hjælpe dig med hurtigt at finde sværere at finde risici i din organisation. Overvej at finjustere [boostere for din risikoscore](insider-risk-management-settings.md#indicators), [undtagelser for filtyper](insider-risk-management-settings.md#file-type-exclusions), [domæner](insider-risk-management-settings.md#domains) og [minimumindstillingerne for indikatortærskel](insider-risk-management-settings.md#indicator-level-settings-preview) for dine politikker.
