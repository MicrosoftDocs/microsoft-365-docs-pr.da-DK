---
title: Netværksforbindelse i Microsoft 365 Administration Center
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/15/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: pandrew1
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Oversigt over netværksforbindelsen i Microsoft 365 Administration Center
ms.openlocfilehash: 5c360820c39be6ec1c42ecdfa0a045a51716e408
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115631"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Netværksforbindelse i Microsoft 365 Administration Center

Microsoft 365 Administration Center indeholder nu samlede målepunkter for netværksforbindelsen, der indsamles fra din Microsoft 365 lejer og kun kan ses af administrative brugere i din lejer.

> [!div class="mx-imgBorder"]
> ![Testværktøj til netværksforbindelse.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Netværksvurderinger** og **netværksindsigt** vises i Microsoft 365 Administration Center under **Tilstand | Netværksforbindelse**.

> [!div class="mx-imgBorder"]
> ![Siden Netværksydeevne.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

> [!NOTE]
> Netværksforbindelsen i Administration Center understøtter lejere i WW Commercial og Germany, men ikke GCC Moderate, GCC High, DoD eller China.

Når du første gang navigerer til siden med netværksydeevne, skal du konfigurere dine placeringer for at få vist kortet over den globale netværksydeevne, en netværksvurdering, der er beregnet til hele lejeren, procentdelen af dine brugere, der arbejder eksternt i forhold til onsite, og en liste over aktuelle problemer, der skal udføres handlinger på og/eller for at undersøge yderligere. I oversigtsruden kan du foretage detailudledning for at få vist specifikke målepunkter for netværksydeevne og problemer efter placering. Du kan få flere oplysninger under [Oversigt over netværksydeevne i Microsoft 365 Administration Center](#network-connectivity-overview-in-the-microsoft-365-admin-center).

Hvis du vil have adgang til siden med netværksforbindelsen, skal du være administrator for organisationen i Microsoft 365. Den administrative rolle Rapportlæser har læseadgang til disse oplysninger. Hvis du vil konfigurere placeringer og andre elementer i netværksforbindelsen, skal en administrator have rollen Tjenestesupportadministrator.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Forudsætninger for, at vurderinger af netværksforbindelsen vises

For at komme i gang skal du aktivere indstillingen for tilvalg af placering for automatisk at indsamle data fra enheder ved hjælp af Windows Placeringstjenester, gå til listen Placeringer for at tilføje eller uploade placeringsdata eller køre Microsoft 365 test af netværksforbindelsen fra dine kontorplaceringer. Disse tre muligheder for oplysninger om kontorplacering er beskrevet nedenfor. Selvom netværksforbindelsen kan evalueres på tværs af organisationen, skal alle forbedringer af netværksdesignet udføres for bestemte kontorplaceringer. Oplysninger om netværksforbindelse angives for hver office-placering, når disse placeringer kan bestemmes. Der er tre muligheder for at hente netværksvurderinger fra dine kontorplaceringer:

### <a name="1-enable-windows-location-services"></a>1. Aktivér Windows placeringstjenester

Til denne indstilling skal du have mindst to computere, der kører på hver office-placering, som understøtter forudsætninger. OneDrive til Windows version skal være opdateret og installeret på hver computer. Netværkstests køres kun mere end én gang om dagen på et tilfældigt tidspunkt. Netværksmålinger planlægges snart føjet til andre Office 365 klientprogrammer.

Windows Placeringsservice skal være godkendt på maskinerne. Du kan teste dette ved at køre **appen Kort** og finde dig selv. Den kan aktiveres på en enkelt maskine med **Indstillinger | Beskyttelse af personlige oplysninger | Den placering**, hvor indstillingen _Tillad, at apps får adgang til din placering_, skal være aktiveret. Windows Location Services-samtykke kan installeres på pc'er ved hjælp af MDM eller Gruppepolitik med indstillingen _LetAppsAccessLocation_.

Du behøver ikke at tilføje placeringer i Administration Center med denne metode, da de automatisk identificeres ved byopløsningen. Flere kontorplaceringer i samme by vises ikke, når du bruger Windows Placeringstjenester. Placeringsoplysninger afrundes til de nærmeste 300 meter med 300 meter, så der ikke er adgang til mere præcise placeringsoplysninger. Brug af Windows Placeringstjenester til netværksmålinger er som standard slået fra for kunder. Du skal aktivere den i pop op-vinduet Network Connectivity Indstillinger Location.

   > [!div class="mx-imgBorder"]
   > ![Aktivér placering](../media/m365-mac-perf/m365-mac-perf-location-enable.png)

Maskinerne skal have Wi-Fi netværk i stedet for et Ethernet-kabel. Computere med et Ethernet-kabel har ikke præcise placeringsoplysninger.

Målingseksempler og kontorplaceringer bør begynde at blive vist 24 timer efter, at disse forudsætninger er opfyldt. Office placeringer, der registreres fra Windows Location Services, aggregeres pr. City og bevares i din visning i 90 dage, efter at der ikke længere modtages eksempler. Hvis du vælger at skifte til office-placeringer, der er tilføjet af administratoren med LAN-undernetoplysninger, kan du deaktivere Windows Placeringstjenester og skjule alle de registrerede placeringer. De fjernes efter 90 dages periode.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Tilføj placeringer, og angiv oplysninger om LAN-undernet

Til denne indstilling kræves der hverken Windows placeringstjenester eller Wi-Fi. Din OneDrive til Windows version skal være opdateret og installeret på mindst én computer på placeringen, og du skal kende dine LAN-undernetoplysninger for hvert af dine kontorer. Denne indstilling tillader flere kontorplaceringer pr. by, og du kan navngive dine kontorplaceringer. Du kan også uploade dem fra andre kilder.

Sørg for, at du også tilføjer placeringer på **siden med placeringer eller importerer** dem fra en CSV-fil. De tilføjede placeringer skal indeholde oplysninger om office LAN-undernet. I dialogboksen til tilføjelse eller redigering af en placering kan du angive et antal LAN-undernet og en række offentlige udgående IP-undernet. LAN-undernet er påkrævet, og et af dem skal matche LAN-undernetattributten i en modtaget netværksvurdering, før resultaterne vises. Supernet understøttes ikke, så LAN-undernettet skal matche nøjagtigt.

LAN-undernet er normalt private IP-adresseintervaller som defineret i RFC1918, så brugen af offentlige IP-adresser som LAN-undernet sandsynligvis er forkert. Dialogboksen viser forslag fra LAN-undernet, der er blevet set i de seneste netværksvurderingstest for din organisation, så du kan vælge.

Hvis du tilføjer offentlige udgående IP-adresser, bruges disse som sekundær differentiator og er beregnet til, når du har flere websteder, der bruger de samme LAN-undernet-IP-adresseområder. Hvis du vil sikre dig, at dine testresultater vises, skal du starte med at lade de offentlige udgående IP-adresseintervaller være tomme. Hvis de er inkluderet, skal et testresultat matche både et af LAN-undernettets IP-adresseintervaller og et af de offentlige udgående IP-adresseområder.

Denne indstilling giver dig mulighed for at have flere kontorer defineret i en by.

Alle testmålinger fra klientcomputere omfatter lan-undernetoplysningerne, som er korreleret med de oplysninger om kontorplacering, du har angivet. Målingseksempler og kontorplaceringer bør begynde at blive vist 24 timer efter, at disse forudsætninger er opfyldt.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Indsaml testrapporter manuelt med testværktøjet Microsoft 365 netværksforbindelse

Hvis du vil bruge denne indstilling, skal du identificere en person på hver placering. Bed vedkommende om at gennemse for at [Microsoft 365 test af netværksforbindelsen](https://connectivity.office.com) på en Windows computer, hvor de har administrative tilladelser. På webstedet skal de logge på deres Office 365-konto for den samme organisation, som du vil have vist resultaterne for. Derefter skal de klikke på **Kør test**. Under testen er der en downloadet Connectivity-test-EXE. De skal åbne og udføre det. Når testene er fuldført, uploades testresultatet til Administration Center.

Testrapporter er knyttet til en placering, hvis den blev tilføjet med lan-undernetoplysninger, ellers vises de kun på den registrerede bys placering.

Målingseksempler og kontorplaceringer skal begynde at blive vist 2-3 minutter, efter at en testrapport er fuldført. Du kan finde flere oplysninger under [Microsoft 365 test af netværksforbindelsen](office-365-network-mac-perf-onboarding-tool.md).

> [!NOTE]
> Når du føjer dine kontorplaceringer til Microsoft 365 netværksforbindelse i Microsoft 365 Administration, kan du i øjeblikket kun angive IPv4-adresser til dine LAN-undernet. Egress IP-adresser skal bruge IPv4.

## <a name="how-do-i-use-this-information"></a>Hvordan gør jeg bruge disse oplysninger?

**Netværksindsigt**, deres relaterede ydeevneanbefalinger og netværksvurderinger er beregnet til at hjælpe med at designe netværksperimetre til dine kontorplaceringer. Hver indsigt indeholder oplysninger om ydeevneegenskaberne for et bestemt almindeligt netværksproblem for hver geografisk placering, hvor brugerne får adgang til din lejer. **Anbefalinger til ydeevnen** for hver netværksindsigt tilbyder specifikke designændringer i netværksarkitekturen, som du kan foretage for at forbedre brugeroplevelsen i forbindelse med Microsoft 365 netværksforbindelse. Netværksvurderingen viser, hvordan netværksforbindelsen påvirker brugeroplevelsen, hvilket muliggør sammenligning af forskellige netværksforbindelser til brugerplacering.

**Netværksvurderinger** destillerer en samling af mange målepunkter for netværksydeevne til et øjebliksbillede af virksomhedens netværkstilstand, der repræsenteres af en pointværdi fra 0 til 100. Netværksvurderinger er begrænset til både hele lejeren og for hver geografisk placering, hvorfra brugerne opretter forbindelse til din lejer, hvilket giver Microsoft 365 administratorer en nem måde øjeblikkeligt at forstå en stor del af virksomhedens netværkstilstand og hurtigt analysere ned i en detaljeret rapport for enhver global kontorplacering.

Komplekse virksomheder med flere kontorplaceringer og ikke-trivielle netværksperimetrearkitekturer kan drage fordel af disse oplysninger enten under deres indledende onboarding til Microsoft 365 eller for at afhjælpe problemer med netværksydeevne, der er registreret med forbrugsvækst. Dette er normalt ikke nødvendigt for små virksomheder, der bruger Microsoft 365, eller virksomheder, der allerede har enkel og direkte netværksforbindelse. Virksomheder med over 500 brugere og flere kontorplaceringer forventes at drage størst fordel.

## <a name="enterprise-network-connectivity-challenges"></a>Udfordringer i forbindelse med netværksforbindelsen i virksomheden

> [!div class="mx-imgBorder"]
> ![Kundenetværk til cloud.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Mange virksomheder har netværket perimeter konfigurationer, som er vokset over tid og er primært designet til at imødekomme medarbejderens internet websted adgang, hvor de fleste websteder ikke er kendt på forhånd, og er upålidelige. Det fremherskende og nødvendige fokus er at undgå malware og phishing-angreb fra disse ukendte websteder. Selvom denne strategi for netværkskonfiguration er nyttig af sikkerhedsmæssige årsager, kan det medføre en forringelse af Microsoft 365 brugerydeevne og brugeroplevelse.

## <a name="how-we-can-solve-these-challenges"></a>Hvordan vi kan løse disse udfordringer

Virksomheder kan forbedre den generelle brugeroplevelse og sikre deres miljø ved at følge [principperne for Office 365 forbindelse](./microsoft-365-network-connectivity-principles.md) og ved hjælp af funktionen Microsoft 365 Administration Center for netværksforbindelse. I de fleste tilfælde vil disse generelle principper have en betydelig positiv indvirkning på slutbrugerens ventetid, pålideligheden af tjenesten og den overordnede ydeevne af Microsoft 365.

Microsoft bliver nogle gange bedt om at undersøge problemer med netværkets ydeevne med Microsoft 365 for store virksomhedskunder, og disse har ofte en grundlæggende årsag, der er relateret til kundens netværksperimeterinfrastruktur. Når der findes en fælles rodårsag til problemer med kundenetværksperimeter, forsøger vi at identificere simple testmålinger. En test med en grænseværdi for måling, der identificerer et bestemt problem, er værdifuld, fordi vi kan teste den samme måling på et hvilket som helst sted, fortælle, om denne hovedårsag er til stede der, og dele den som en netværksindsigt med administratoren.

Nogle netværksindsigter vil blot indikere et problem, der kræver yderligere undersøgelse. En netværksindsigt, hvor vi har nok test til at vise en bestemt afhjælpningshandling for at rette rodårsagen, er angivet som en **anbefalet handling**. Disse anbefalinger, der er baseret på dynamiske målepunkter, som afslører værdier, der falder uden for en forudbestemt grænse, er meget mere værdifulde end generelle råd om bedste praksis, da de er specifikke for dit miljø og viser den faktiske forbedring, når de anbefalede ændringer er foretaget.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Oversigt over netværksforbindelser i Microsoft 365 Administration Center

Microsoft har eksisterende netværksmålinger fra flere Office desktop- og webklienter, som understøtter driften af Microsoft 365. Disse målinger bruges nu til at give netværksarkitekturdesignindsigt og en netværksvurdering, som vises på siden **Netværksforbindelse** i Microsoft 365 Administration Center.

Som standard identificerer omtrentlige placeringsoplysninger, der er knyttet til netværksmålingerne, den by, hvor klientenhederne er placeret. Netværksvurderingen på hver placering vises med farve, og det relative antal brugere på hver placering repræsenteres af cirklens størrelse.

> [!div class="mx-imgBorder"]
> ![Oversigtskort over netværksindsigt.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

Oversigtssiden viser også netværksvurderingen for kunden som et vægtet gennemsnit på tværs af alle kontorplaceringer.

> [!div class="mx-imgBorder"]
> ![Netværksvurdering.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Du kan få vist en tabelvisning af de placeringer, hvor de kan filtreres, sorteres og redigeres under fanen **Placeringer** . Placeringer med specifikke anbefalinger kan også omfatte en anslået potentiel ventetidsforbedring. Dette beregnes ved at tage medianventetiden for dine organisationsbrugere på placeringen og fratrække medianventetiden for alle organisationer i samme by.

> [!div class="mx-imgBorder"]
> ![Placeringer med netværksindsigt.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Vurdering af fjernmedarbejdere og målepunkter for brugerforbindelse

Vi klassificerer logge for netværkstrafik som eksterne brugere eller brugere på stedet og viser deres procentdel i afsnittet med brugerforbindelsesmålepunkter i oversigtsruden. I byer, hvor du har fjernbrugere, kan du finde den placeringsspecifikke vurderingsscore for fjernnetværket, når du åbner den pågældende placerings side. Listen over placeringer indeholder både kontorplaceringer og fjernarbejdsbyer, som kan filtreres og sorteres. Vi leverer vurderingsscoren for fjernarbejdere med pointopdeling for Exchange, SharePoint og Teams.

Hjemmebrugernetværksindsigt samles og rapporteres på byniveau og er begrænset til byer med mindst 5 fjernmedarbejdere. Vi identificerer ikke enkelte medarbejdere, der arbejder hjemmefra.

Placeringer klassificeres automatisk som på stedet eller eksternt, men du har mulighed for at indtaste alle dine udgående IP-adresser på stedet manuelt for at sikre en 100% klassificering. Hvis du beslutter dig for at gå denne rute, skal du markere afkrydsningsfeltet **Angiv alle udgående IP-adresser på stedet manuelt** i pop op-vinduet Placeringer Indstillinger, når du har tilføjet alle dine udgående IP-adresser. Når dette er gjort, klassificeres alle netværkstrafiklogge fra udgående IP-adresser, du har markeret som onsite, altid som kontorer, og alle andre udgående IP-adresser klassificeres som fjernadresser.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Oversigt over og indsigt i netværksydeevne for bestemte Office-placeringer

Når du vælger en kontorplacering, åbnes en placeringsspecifik oversigtsside, der viser oplysninger om netværksudgange, der er blevet identificeret fra målinger for den pågældende kontorplacering.

> [!div class="mx-imgBorder"]
> ![Oplysninger om netværksindsigt efter placering.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Der vises et kort over perimeternetværket for dine organisationsbrugere på placeringen med nogle af eller alle disse elementer:

- **Office placering** – Kontorplaceringen for den side, du kigger på
- **Netværksperimeter** – Placeringen af kildens IP-adresse for forbindelser fra kontorplaceringen. Dette afhænger af nøjagtigheden af geo-IP-placeringsdatabaser
- **Exchange optimal service front door** - En af de anbefalede Exchange service front døre, som brugere på dette kontor placering skal oprette forbindelse til
- **Exchange ikke optimal fordør** - En Exchange service front door, som brugerne er tilsluttet, men anbefales ikke
- **SharePoint optimal service front door** - En af de anbefalede SharePoint service front døre, som brugere på dette kontor placering skal oprette forbindelse til
- **SharePoint ikke optimal service front door** - En SharePoint service front door, som brugerne er tilsluttet, men anbefales ikke
- **DNS-rekursiv resolverserver** – Placeringen fra en geo-IP-database for den registrerede REkursive DNS-fortolker, der bruges til Exchange Online (hvis det er muligt)
- **Din proxyserver** – Placeringen fra en geo-IP-database for den registrerede proxyserver (hvis den er tilgængelig)

Oversigtssiden for kontorplacering viser desuden placeringens netværksvurdering, netværksvurderingshistorik, en sammenligning af denne placerings vurdering med andre kunder i samme by og en liste over specifik indsigt og anbefalinger, som du kan påtage dig for at forbedre netværkets ydeevne og pålidelighed.

Sammenligninger mellem kunder i samme by er baseret på forventningen om, at alle kunder har lige adgang til netværkstjenesteudbydere, telekommunikationsinfrastruktur og nærliggende Microsoft-netværkspunkter.

Placeringsnavne kan tilpasses, når du tilføjer en ny placering eller redigerer en eksisterende placering i pop op-vinduet til placering. Dette giver dig fleksibiliteten til at tilpasse dine placeringsnavne når som helst. Når du tilføjer LAN-undernet direkte i pop op-vinduet for placering, viser vi også en rulleliste over soft-matchede LAN-undernet, som du kan vælge imellem. Kredsløbsnavne for bestemte Office-udgående IP-adresser kan også tilføjes og redigeres.

Fanen Detaljer på siden til kontorplacering viser de specifikke måleresultater, der blev brugt til at få indsigt, anbefalinger og netværksvurdering. Dette leveres, så netværksteknikere kan validere anbefalingerne og faktoren i eventuelle begrænsninger eller specifikationer i deres miljø. Du kan også finde det anslåede antal brugere for indsamlede eksempler på de pågældende kontorplaceringer samt fjernarbejdere i den pågældende by.

> [!div class="mx-imgBorder"]
> ![Placeringsspecifikke oplysninger.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Deling af netværksvurderingsdata med Microsoft

Netværksvurderingerne for din organisation og netværksindsigten deles som standard med Microsoft-medarbejdere. Dette omfatter ikke nogen personlige data fra dine medarbejdere, men kun de specifikke målepunkter for netværksvurdering og netværksindsigt, der vises i Administration for dine kontorplaceringer. Den indeholder heller ikke dine kontorplaceringsnavne eller adressenavne, så du skal fortælle dem by- og support-id'et for det kontor, du vil diskutere. Hvis denne er slået fra, kan de Microsoft-teknikere, du diskuterer netværksforbindelsen med, ikke få vist nogen af disse oplysninger. Aktivering af denne indstilling deler kun fremtidige data, der starter dagen efter, at du har aktiveret den.

## <a name="csv-import-for-lan-subnet-office-locations"></a>CSV-import for office-placeringer på LAN-undernet

Hvis du vil have office-id for LAN-undernet, skal du tilføje hver placering på forhånd. I stedet for at tilføje individuelle **Kontorplaceringer** under fanen Placeringer kan du importere dem fra en CSV-fil. Du kan muligvis hente disse data fra andre steder, hvor du har gemt dem, f.eks. dashboardet til opkaldskvalitet eller Active Directory-websteder og -tjenester

I CSV-filen vises en registreret byplacering i kolonnen userEntered som tom, og en manuelt tilføjet Office-placering vises som 1.

1. Klik på fanen **Placeringer** i hovedvinduet _Forbindelse til Microsoft 365_.

1. Klik på knappen **Importér** lige over listen over placeringer. Pop op-vinduet **Importér kontorplaceringer** vises.

   > [!div class="mx-imgBorder"]
   > ![CSV-importmeddelelse.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Klik på linket **Download aktuelle office-placeringer (.csv)** for at eksportere listen over aktuelle placeringer til en CSV-fil, og gem den på din lokale harddisk. Dette giver dig en korrekt formateret CSV med kolonneoverskrifter, som du kan føje placeringer til. Du kan lade de eksisterende eksporterede placeringer forblive, som de er. De duplikeres ikke, når du importerer den opdaterede CSV. Hvis du vil ændre adressen på en eksisterende placering, opdateres den, når du importerer CSV-filen. Du kan ikke ændre adressen på en fundet by.

1. Åbn CSV,og tilføj dine placeringer ved at udfylde følgende felter på en ny linje for hver placering, du vil tilføje. Lad alle andre felter være tomme. værdier, du angiver i andre felter, ignoreres.

   1. **userEntered** (påkrævet): Skal være 1, for at der tilføjes en ny LAN-undernetplacering
   1. **Navn** (obligatorisk): Navnet på kontorplaceringen
   1. **Adresse** (obligatorisk): Kontorets fysiske adresse
   1. **Breddegrad** (valgfrit): Udfyldes fra Bing kortopslag for adressen, hvis den er tom
   1. **Længdegrad** (valgfrit): Udfyldes fra Bing tilknytter adresseopslag, hvis den er tom
   1. **Egress IP-adresseintervaller 1-5** (valgfrit): Angiv kredsløbsnavnet efterfulgt af en mellemrumssepareret liste over gyldige IPv4 CIDR-adresser for hvert område. Disse værdier bruges til at skelne mellem flere Office-placeringer, hvor du bruger de samme LAN-undernet-IP-adresser. Egress IP-adresseområder skal alle være /24-netværksstørrelsen, og /24 er ikke inkluderet i inputtet.
   1. **LanIps** (påkrævet): Angiv de LAN-undernetområder, der er i brug på denne office-placering. LAN-undernet-id'er skal have en CIDR-netværksstørrelse inkluderet, hvor netværksstørrelsen kan være mellem /8 og /29. Flere LAN-undernetområder kan adskilles med et komma eller et semikolon.

1. Når du har tilføjet dine office-placeringer og gemt filen, skal du klikke på knappen **Gennemse** ud for **Upload feltet Fuldført** og vælge den gemte CSV-fil.

1. Filen valideres automatisk. Hvis der er valideringsfejl, får du vist fejlmeddelelsen: _Der er nogle fejl i importfilen. Gennemse fejlene, ret importfilen, og prøv derefter igen._ Klik på linket **Åbn fejloplysninger** for at få vist en liste over specifikke feltvalideringsfejl.

   > [!div class="mx-imgBorder"]
   > ![Fejlmeddelelse om import af CSV.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Hvis der ikke er nogen fejl i filen, får du vist meddelelsen: _Rapporten er klar. Der blev fundet x-placeringer, der skal tilføjes, og x placeringer, der skal opdateres._ Klik på knappen **Importér** for at uploade CSV-filen.

   > [!div class="mx-imgBorder"]
   > ![Meddelelse om klar CSV-import.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="cqd-tsv-import-for-lan-subnet-office-locations"></a>CQD TSV-import for OFFICE-undernetplaceringer

Hvis du har uploadet byggedata til dit dashboard til opkaldskvalitet, kan du tilføje disse placeringer her for at begynde at vurdere deres netværksforbindelse. Dette påvirker ikke dine eksisterende placeringer.

[Gå til Lejerdata Upload](https://cqd.teams.microsoft.com/spd/#/TenantDataUpload) i Dashboard til opkaldskvalitet. Hvis du har uploadet dine byggedata, får du vist en mulighed for at downloade dem til en .tsv-fil. Download .tsv-filen fra Dashboard til opkaldskvalitet, og upload den derefter i CQD-pop op-vinduet ved at følge nedenstående trin. Hvis du vil oprette .tsv-filen manuelt, skal du justere skemaet i forhold til det i Upload oprette datafil eller i stedet prøve office-placeringerne for CSV-import til LAN-undernet.

1. Klik på fanen **Placeringer** i hovedvinduet Forbindelse til Microsoft 365.

2. Klik på knappen **Administrer flere placeringer** lige over listen over placeringer.

   > [!div class="mx-imgBorder"]
   > ![Administrer menuen flere placeringer.](../media/m365-mac-perf/m365-mac-perf-import-cqd-manage-multiple.png)

3. Klik på **tilføj placeringer fra Dashboard til opkaldskvalitet**. Pop op-vinduet **Tilføj placeringer fra Dashboard til opkaldskvalitet** vises.

   > [!div class="mx-imgBorder"]
   > ![Tilføj placeringer fra pop op-vinduet Opkaldskvalitetsdashboard.](../media/m365-mac-perf/m365-mac-perf-import-cqd-add-locations.png)

4. Klik på knappen **Gennemse** ud for feltet **Vælg en .tsv-fil, der skal overføres** , og vælg den gemte TSV-fil. Sørg for, at værdien i filen er tabulatorsepareret.

5. Filen valideres automatisk og fortolkes på listen over Office-placeringer. Hvis der er valideringsfejl, vises der en liste over fejlene i pop op-vinduet **Vi kunne ikke overføre filen** .

   > [!div class="mx-imgBorder"]
   > ![Vi kunne ikke uploade dit fil-pop op-vindue.](../media/m365-mac-perf/m365-mac-perf-import-cqd-couldnt-upload.png)

6. Hvis der ikke er nogen fejl i filen, får du vist meddelelsen: _Din filtest.tsv uploades og er klar. Vælg Importér for at overføre dine oplysninger._

   > [!div class="mx-imgBorder"]
   > ![Vælg en .tsc-fil, der skal overføres.](../media/m365-mac-perf/m365-mac-perf-import-cqd-select-tsv.png)

7. Klik **på Upload** nederst i panelet for at uploade kontorplaceringerne.

## <a name="faq"></a>Ofte stillede spørgsmål

### <a name="what-is-a-microsoft-365-service-front-door"></a>Hvad er en Microsoft 365 hoveddør til service?

Hoveddøren til Microsoft 365-tjenesten er et indgangspunkt på Microsofts globale netværk, hvor Office klienter og tjenester afslutter deres netværksforbindelse. Hvis du vil have en optimal netværksforbindelse til Microsoft 365, anbefales det, at netværksforbindelsen afbrydes til den nærmeste Microsoft 365 hoveddør.

> [!NOTE]
> Microsoft 365 front door-tjeneste har ingen direkte relation til det Azure Front Door Service-produkt, der er tilgængeligt på Azure Marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Hvad er en optimal Microsoft 365 service front door?

En optimal Microsoft 365 service front door er en, der er tættest på dit netværk udgange, generelt i din by eller metro område. Brug [Microsoft 365 forbindelsestestværktøjet](office-365-network-mac-perf-onboarding-tool.md) til at bestemme placeringen af din i brug Microsoft 365 service front door og optimal service front door. Hvis værktøjet bestemmer, at frontdøren i brug er optimal, opretter du optimal forbindelse til Microsofts globale netværk.

### <a name="what-is-an-internet-egress-location"></a>Hvad er en internet udgående placering?

Internet udgangsplaceringen er den placering, hvor netværkstrafikken forlader virksomhedsnetværket og opretter forbindelse til internettet. Dette identificeres også som den placering, hvor du har en NAT-enhed (Network Address Translation), og som regel hvor du opretter forbindelse til en internetudbyder. Hvis du ser en lang afstand mellem din placering og din internet udgående placering, kan dette indikere en betydelig WAN-backhaul.

### <a name="what-license-is-needed-for-this-capability"></a>Hvilken licens skal der bruges til denne funktion?

Du skal have en licens, der giver adgang til Microsoft 365 Administration.

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 netværksindsigt](office-365-network-mac-perf-insights.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 forbindelsestestværktøj](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 placeringstjenester for netværksforbindelsen](office-365-network-mac-location-services.md)
