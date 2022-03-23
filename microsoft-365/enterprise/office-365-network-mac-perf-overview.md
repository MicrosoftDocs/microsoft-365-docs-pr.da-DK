---
title: Netværksforbindelse i Microsoft 365 Administration Center
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Oversigt over netværksforbindelsen i Microsoft 365 Administration Center
ms.openlocfilehash: c2f44ba97cb3d70dbe065df4a5b631f569460bff
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63591622"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Netværksforbindelse i Microsoft 365 Administration Center

Center Microsoft 365 Administration indeholder nu aggregerede målepunkter for netværksforbindelsen, der er indsamlet fra din Microsoft 365-lejer, og som kun er tilgængelige for administrative brugere i din lejer.

> [!div class="mx-imgBorder"]
> ![Testværktøj til netværksforbindelse.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Netværksvurderinger** **og netværksindsigt** vises i Microsoft 365 Administration under **Tilstandscenter | Netværksforbindelse**.

> [!div class="mx-imgBorder"]
> ![Siden Netværksydeevne.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

>[!NOTE]
>Netværksforbindelsen i Administration understøtter lejere i WW Commercial og Germany, men ikke GCC Moderat, GCC High, DoD eller Kina.

Når du først navigerer til siden med netværksydeevne, skal du konfigurere dine placeringer for at få vist kortet over den globale netværksydeevne, en netværksvurdering, der er omfangsbestemt til hele lejeren, procentdelen af dine brugere, der arbejder eksternt vs. på stedet, og en liste over aktuelle problemer, der skal tages i brug for at foretage yderligere handlinger og/eller undersøge yderligere. Fra oversigtsruden kan du analysere ned for at få vist specifikke målepunkter for netværkets ydeevne og problemer efter placering. Du kan finde flere oplysninger [i Oversigt over netværksydeevne i Microsoft 365 Administration Center](#network-connectivity-overview-in-the-microsoft-365-admin-center).

For at få adgang til siden netværksforbindelse skal du være administrator for organisationen inden for Microsoft 365. Den administrative rolle rapportlæser har læseadgang til disse oplysninger. Hvis du vil konfigurere placeringer og andre elementer i netværksforbindelsen, skal en administrator have rollen som tjenestesupportadministrator.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Forudsætninger for, at der kan vises netværksforbindelsesvurderinger

For at komme i gang skal du aktivere indstillingen for din tilmelding til placering for automatisk at indsamle data fra enheder ved hjælp af Windows-placeringstjenester, gå til listen Placeringer for at tilføje eller uploade placeringsdata eller køre Microsoft 365-netværksforbindelsestesten fra dine kontorplaceringer. Disse tre indstillinger for oplysninger om kontorplacering er beskrevet nedenfor. På grund af den forbedrede netværksforbindelse kan de evalueres i hele organisationen. Alle forbedringer af netværksdesignet skal foretages på bestemte kontorplaceringer. Oplysninger om netværksforbindelsen er angivet for hver placering på kontoret, når disse placeringer kan bestemmes. Der er tre muligheder for at få netværksvurderinger fra dine kontorplaceringer:

### <a name="1-enable-windows-location-services"></a>1. Windows placeringstjenester

Med denne indstilling skal du have mindst to computere, der kører på hver kontorplacering, og som understøtter forudsætningerne. OneDrive til Windows-versionen skal være opdateret og installeret på hver enkelt computer. Du kan finde flere OneDrive versioner i OneDrive [produktbemærkninger](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0). Netværksmål er planlagt til at blive føjet til Office 365 klientprogrammer i den nærmeste fremtid.

Windows placeringstjenesten skal have tilladelse på maskinerne. Du kan teste dette ved at køre **Kort** appen og finde dig selv. Den kan aktiveres på en enkelt computer med **Indstillinger | Beskyttelse af personlige oplysninger | Placering**, hvor indstillingen Tillad _apps at få adgang til din placering_ skal være aktiveret. Windows placeringstjenester kan samtykke implementeres på pc'er ved hjælp af MDM eller Gruppepolitik med indstillingen _LetAppsAccessLocation_.

Du behøver ikke at tilføje placeringer i Administration med denne metode, da de automatisk identificeres ved byopløsningen. Flere kontorplaceringer inden for den samme by vises ikke, når du bruger Windows placeringstjenester. Placeringsoplysninger afrundes til de nærmeste 300 meter gange 300 meter, så der ikke opnås adgang til mere nøjagtige placeringsoplysninger.

Maskinerne skal have et Wi-Fi i stedet for et Ethernet-kabel. Maskiner med et Ethernet-kabel har ikke nøjagtige placeringsoplysninger.

Stikprøver og kontorplaceringer bør begynde at dukke op 24 timer efter, at disse forudsætninger er opfyldt.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Tilføj placeringer, og angiv LAN-undernetoplysninger

Med denne indstilling er hverken Windows placeringstjenester eller Wi-Fi påkrævet. Din OneDrive til Windows-version skal være opdateret og installeret på mindst én computer på placeringen.

Sørg for, at du også tilføjer placeringer på **placeringssiden eller** importerer dem fra en CSV-fil. De placeringer, der tilføjes, skal indeholde dine Office LAN-undernetoplysninger. I dialogboksen til tilføjelse eller redigering af en placering kan du angive et antal LAN-undernet og et antal offentlige IP-undernet for udgangspunkter. LAN-undernet er påkrævede, og et af dem skal svare til LAN-undernetattributten i en modtaget netværksvurdering, for at resultaterne vises. Supernet understøttes ikke, så LAN-undernettet skal svare nøjagtigt til hinanden.

Bemærk, at LAN-undernet normalt er private IP-adresseintervaller som defineret i RFC1918, så brugen af offentlige IP-adresser som LAN-undernet er sandsynligvis forkert. Dialogboksen viser forslag til LAN-undernet, der er blevet set i de seneste test til netværksvurdering for organisationen, så du kan vælge.

Hvis du tilføjer offentlige udgangs-IP-adresser, bruges disse som en sekundær differentiator og er beregnet til, når du har flere websteder, der bruger de samme LAN-undernet IP-adresseområder. For at sikre at dine testresultater vises, skal du starte med at lade de offentlige IP-adresseintervaller for udgangspunktet være tomme. Hvis de er inkluderet, skal et testresultat svare til både et af IP-adresseområdet for LAN-undernettet og et af de offentlige udgangs-IP-adresseintervaller.

Denne indstilling giver dig mulighed for at have flere kontorer defineret inden for en by.

Alle testmål fra klientcomputere indeholder LAN-undernetoplysningerne, som er korreleret med de oplysninger om kontorplacering, du har angivet. Stikprøver og kontorplaceringer bør begynde at dukke op 24 timer efter, at disse forudsætninger er opfyldt.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Saml testrapporter manuelt med Microsoft 365 testværktøj til netværksforbindelse

Med denne indstilling skal du identificere en person på hver placering. Bed dem om at gennemse [Microsoft 365 test af netværksforbindelsen](https://connectivity.office.com) på en Windows computer, de har administrative rettigheder til. På webstedet skal de logge på deres Office 365 for den samme organisation, som du vil have vist resultaterne for. Derefter skal de klikke på **Kør test**. Under testen er der en downloadet Connectivity test EXE. De skal åbne og udføre dette. Når testene er fuldført, uploades testresultatet til Administration.

Testrapporter er sammenkædet med en placering, hvis den blev tilføjet med LAN-undernetoplysninger, ellers vises de kun på byplaceringen.

Stikprøver og kontorplaceringer bør begynde at blive vist 2-3 minutter efter, at en testrapport er færdig. Du kan finde flere oplysninger [Microsoft 365 test af netværksforbindelsen](office-365-network-mac-perf-onboarding-tool.md).

> [!NOTE]
> Når du føjer dine kontorplaceringer til Microsoft 365-netværksforbindelsen i Microsoft 365 Administration, kan du kun angive IPv4-adresser til LAN-undernet. Egress IP-adresser skal bruge IPv4.

## <a name="how-do-i-use-this-information"></a>Hvordan bruger jeg disse oplysninger?

**Netværksindsigt**, deres relaterede anbefalinger om ydeevne og netværksvurderinger er beregnet til at hjælpe med at designe netværksperimetere til dine kontorplaceringer. Hver indsigt giver oplysninger om ydeevnekarakteristika for et bestemt almindeligt netværksproblem for hver geografisk placering, hvor brugerne tilgår din lejer. **Anbefalinger af ydeevne** for hvert netværksindsigt giver specifikke designændringer af netværksarkitekturen, som du kan foretage for at forbedre brugeroplevelsen i Microsoft 365 netværksforbindelsen. Netværksvurderingen viser, hvordan netværksforbindelsen påvirker brugeroplevelsen, så der kan sammenlignes med forskellige netværksforbindelser på brugerplaceringen.

**Netværksvurderinger optimerer** et aggregeret antal af mange målepunkter for netværksydeevne i et øjebliksbillede af virksomhedens netværkstilstand, der repræsenteres af en pointværdi fra 0-100. Netværksvurderinger er fastsat til både hele lejeren og til hver geografisk placering, hvorfra brugerne opretter forbindelse til din lejer, så Microsoft 365-administratorer hurtigt kan forstå virksomhedens netværkstilstand og hurtigt analysere ned i en detaljeret rapport for enhver global kontorplacering.

Komplekse virksomheder med flere kontorplaceringer og ikke-trivielle netværksperimeterarkitekturer kan drage fordel af disse oplysninger enten under deres indledende onboarding til Microsoft 365 eller for at afhjælpe problemer med netværksydeevnen, der opdages med vækst i brugen. Dette er normalt ikke nødvendigt for små virksomheder, der bruger Microsoft 365, eller virksomheder, der allerede har en simpel og direkte netværksforbindelse. Virksomheder med mere end 500 brugere og flere kontorplaceringer forventes at få mest ud af det.

## <a name="enterprise-network-connectivity-challenges"></a>Udfordringer i forbindelse med netværksforbindelse for virksomheder

> [!div class="mx-imgBorder"]
> ![Kundenetværk til skyen.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Mange virksomheder har netværksperimeterkonfigurationer, der er udviklet over tid og primært er designet til at skabe plads til medarbejderens webstedsadgang til internettet, hvor de fleste websteder ikke kendes på forhånd og ikke er tillid til. Det dominerende og nødvendige fokus er at undgå malware og phishing-angreb fra disse ukendte websteder. Denne strategi for netværkskonfiguration kan, selvom det er nyttigt af sikkerhedsmæssige årsager, Microsoft 365 forringelse af brugerens ydeevne og brugeroplevelse.

## <a name="how-we-can-solve-these-challenges"></a>Hvordan vi kan løse disse udfordringer

Virksomheder kan forbedre den generelle brugeroplevelse og sikre deres miljø ved at [Office 365 principperne](./microsoft-365-network-connectivity-principles.md) for netværksforbindelse og ved at bruge funktionen Microsoft 365 Administration Center for netværksforbindelse. I de fleste tilfælde vil det have en væsentlig positiv indvirkning på slutbrugerens ventetid, tjenestepålidelighed og generelle ydeevne for Microsoft 365.

Microsoft bliver nogle gange bedt om at undersøge problemer med netværksydeevnen med Microsoft 365 for store virksomhedskunder, og disse har ofte en rodårsagen relateret til kundens netværksperimeterinfrastruktur. Når der findes en almindelig årsag til et perimeterproblem for et kundenetværk, søger vi at identificere simple testmål, der identificerer det. En test med en målværdi, der identificerer et bestemt problem, er værdifuld, fordi vi kan teste den samme måling på et hvilket som helst sted, afgøre, om denne egentlige årsag findes der, og dele den som et netværksindsigt med administratoren.

Nogle netværksindsigter indikerer blot et problem, der kræver yderligere undersøgelse. Et netværksindsigt, hvor vi har nok test til at vise en bestemt afhjælpningshandling for at rette den egentlige årsag, er angivet som en **anbefalet handling**. Disse anbefalinger, der er baseret på livemålepunkter, der viser værdier, der ligger uden for en foruddefineret grænseværdi, er meget mere værdifulde end generelle råd om bedste praksis, da de er specifikke for dit miljø og viser den faktiske forbedring, når de anbefalede ændringer er foretaget.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Oversigt over netværksforbindelsen i Microsoft 365 Administration Center

Microsoft har eksisterende netværksmål fra flere Office desktop- og webklienter, som understøtter Microsoft 365. Disse målinger bruges nu til at levere designindsigt om netværksarkitektur og en netværksvurdering, som vises  på siden Netværksforbindelse i Microsoft 365 Administration Center.

Som standard identificerer omtrentlige placeringsoplysninger, der er knyttet til netværksmålene, den by, hvor klientenheder er placeret. Netværksvurderingen på hver placering vises med farve, og det relative antal brugere på hver placering er repræsenteret af størrelsen på cirklen.

> [!div class="mx-imgBorder"]
> ![Oversigtskort over netværksindsigt.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

Oversigtssiden viser også netværksvurderingen for kunden som et vægtet gennemsnit på tværs af alle kontorplaceringer.

> [!div class="mx-imgBorder"]
> ![Netværksvurdering.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Du kan få vist en tabelvisning af de placeringer, hvor de kan **filtreres, sorteres og redigeres på fanen** Placeringer. Placeringer med specifikke anbefalinger kan også omfatte en anslået potentiel forbedring af ventetiden. Dette beregnes ved at tage organisationens brugeres medianventetid på placeringen og subtrahere medianventetid for alle organisationer i samme by.

> [!div class="mx-imgBorder"]
> ![Netværksindsigtsplaceringer.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Målepunkter for ekstern medarbejdervurdering og brugerforbindelse

Vi klassificerer netværkstrafiklogfiler som eksterne eller lokale brugere og viser deres procentdele i sektionen med målepunkter for brugerforbindelsen i oversigtsruden. For de byer, hvor du har eksterne brugere, kan du finde det placeringsspecifikke vurderingsresultat for fjernnetværket, når du åbner siden for den pågældende placering. Listen over placeringer har både kontorplaceringer og fjernarbejderbyer, som kan filtreres og sorteres. Vi giver dig vurderingsresultatet for fjernmedarbejdere med opdeling af point for Exchange, SharePoint og Teams.

Indsigter i hjemmenetværk sammenlægges og rapporteres på byniveau og er begrænset til byer med mindst 5 fjernmedarbejdere. Vi identificerer ikke individuelle medarbejdere, der arbejder hjemmefra.

Placeringer klassificeres automatisk som onsite eller fjernplacering, men du har mulighed for at angive alle dine onsite-udgangspunkt-IP-adresser manuelt for at sikre en 100 % klassificering. Hvis du beslutter dig for at gå til denne rute, er du nødt til at markere afkrydsningsfeltet Angiv alle **IP-adresser** for udgangspunktet på stedet manuelt i pop op-pop-op'et Locations Indstillinger efter at have tilføjet alle dine IP-adresser for udgangspunktet. Når dette er gjort, vil alle netværkstrafiklogfiler fra udgangs-IP-adresser, du har markeret som på stedet, altid blive klassificeret som kontorer, og alle andre udgangs-IP-adresser vil blive klassificeret som eksterne.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Specifik oversigt over netværksydeevne og indsigt for specifik office-placering

Når du vælger en kontorplacering, åbnes en placeringsspecifik oversigtsside, der viser oplysninger om det netværks udgangspunkt, der er identificeret ud fra målene for den pågældende kontorplacering.

> [!div class="mx-imgBorder"]
> ![Detaljer om netværksindsigt efter placering.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Et kort over perimeternetværket for organisationens brugere på placeringen vises med nogle eller alle disse elementer:

- **Office placering** – Kontorplaceringen for den side, du kigger på
- **Netværksperimeter** – Placeringen af kilde-IP-adressen for forbindelser fra kontorplaceringen. Dette afhænger af nøjagtigheden af geo-IP-placeringsdatabaser
- **Exchange optimal service frontsideport** – en af de anbefalede Exchange for døre, som brugere på denne kontorplacering skal oprette forbindelse til
- **Exchange en under optimal frontport** – en Exchange, som brugerne har forbindelse til, men som ikke anbefales
- **SharePoint optimal service for dør** – en af de anbefalede SharePoint døre for tjeneste, som brugere på denne kontorplacering skal oprette forbindelse til
- **SharePoint, som ikke er optimale for** service, er en SharePoint, som brugerne har forbindelse til, men som ikke anbefales
- **DNS rekursiv resolver-server** – Placeringen fra en geo IP-database for den registrerede DNS-rekursiv resolver, der bruges til Exchange Online (hvis tilgængelig)
- **Din proxyserver** – Placeringen fra en geo IP-database for den registrerede proxyserver (hvis den er tilgængelig)

Oversigtssiden for kontorplaceringen viser desuden placeringens netværksvurdering, oversigt over netværksvurdering, en sammenligning af denne placerings vurdering til andre kunder i samme by og en liste over specifik viden og anbefalinger, som du kan foretage dig for at forbedre netværkets ydeevne og pålidelighed.

Sammenligninger mellem kunder i den samme by er baseret på forventningen om, at alle kunder har lige adgang til netværkstjenesteudbydere, telekommunikationsinfrastruktur og nærliggende Microsoft-netværkspunkter for tilstedeværelse.

Placeringsnavne kan tilpasses, når du tilføjer en ny placering eller redigerer en eksisterende placering i pop op-pop op-placeringen. Dette giver dig fleksibilitet til at tilpasse dine placeringsnavne når som helst. Når du tilføjer LAN-undernet direkte i pop op-pop-op-placeringen, viser vi desuden en rulleliste med blød matchede LAN-undernet, som du kan vælge mellem. Kredsløbsnavne for bestemte office-udgangs-IP-adresser kan også tilføjes og redigeres.

Fanen detaljer på siden kontorplacering viser de specifikke måleresultater, der blev brugt til at komme med eventuelle indsigter, anbefalinger og netværksvurderingen. Dette er til rådighed, så netværksteknikere kan validere anbefalingerne og faktoren i eventuelle begrænsninger eller specifikke oplysninger i deres miljø. Du kan også finde det anslåede antal brugere for indsamlede eksempler på de pågældende kontorplaceringer samt eksterne medarbejdere i den pågældende by.

> [!div class="mx-imgBorder"]
> ![Placeringsspecifikke detaljer.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Deling af netværksvurderingsdata med Microsoft

Som standard deles netværksvurderinger for din organisation og netværksindsigt med Microsoft-medarbejdere. Dette omfatter ikke personlige data fra dine medarbejdere, men kun de specifikke målepunkter for netværksvurdering og netværksindsigt, der vises i Administration for dine kontorplaceringer. Det omfatter heller ikke navnene på din kontoradresse eller postadresser, så du er nødt til at fortælle dem by og support-id for det kontor, du vil diskutere. Hvis dette deaktiveres, kan de Microsoft-teknikere, som du diskuterer din netværksforbindelse med, ikke få vist nogen af disse oplysninger. Aktivering af denne indstilling deler kun fremtidige data, der starter dagen efter, at du har aktiveret den.

## <a name="csv-import-for-lan-subnet-office-locations"></a>CSV-import til LAN-undernetplaceringer i Office

Du skal tilføje hver placering på forhånd for at kunne identificere LAN-undernetkontorer. I stedet for at tilføje individuelle kontorplaceringer **kan du importere** dem fra en CSV-fil under fanen Placeringer. Du kan muligvis hente disse data fra andre steder, hvor du har gemt dem, f.eks. dashboardet Opkaldskvalitet eller Active Directory-websteder og -tjenester

I CSV-filen vises en fundet byplacering i kolonnen userEntered som tom, og en manuelt tilføjet kontorplacering vises som 1.

1. I hovedvinduet _Forbindelse til Microsoft 365_ skal du klikke **på fanen** Placeringer.

1. Klik på **knappen** Importér lige over listen over placeringer. Pop **op-pop op-pop-op'en Importér kontorplaceringer** vises.

   > [!div class="mx-imgBorder"]
   > ![CSV-importmeddelelse.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Klik på **linket Download aktuelle office-placeringer (.csv)** for at eksportere listen over aktuelle placeringer til en CSV-fil og gemme den på din lokale harddisk. Dette giver dig en korrekt formateret CSV med kolonneoverskrifter, som du kan tilføje placeringer. Du kan lade de eksisterende eksporterede placeringer være, som de er. de bliver ikke duplikeret, når du importerer den opdaterede CSV. Hvis du vil ændre adressen på en eksisterende placering, opdateres den, når du importerer CSV-versionen. Du kan ikke ændre adressen på en by, der opdages.

1. Åbn CSV-csv'en, og tilføj dine placeringer ved at udfylde følgende felter på en ny linje for hver placering, du vil tilføje. Lad alle andre felter være tomme. Værdier, du angiver i andre felter, ignoreres.

   1. **userEntered** (påkrævet): Skal være 1 for en ny LAN-undernetplacering til office, der tilføjes
   1. **Navn** (påkrævet): Navnet på kontorplaceringen
   1. **Adresse** (påkrævet): Kontorets fysiske adresse
   1. **Breddegrad** (valgfrit): Udfyldes Bing kortopslag af adressen, hvis den er tom
   1. **Længdegrad** (valgfrit): Udfyldes fra Bing tilknytter opslag af adressen, hvis det er tomt
   1. **Egress IP-adresseområde 1-5** (valgfrit): For hvert område skal du angive navnet på kredsløbet efterfulgt af en mellemrumssepareret liste over gyldige IPv4 CIDR-adresser. Disse værdier bruges til at skelne mellem flere kontorplaceringer, hvor du bruger de samme LAN-undernet IP-adresser. Egress IP-adresseintervaller skal alle have en /24-netværksstørrelse, og /24 medtages ikke i inputtet.
   1. **LanIps** (påkrævet): Vis en liste over de LAN-undernetintervaller, der bruges på denne kontorplacering. LAN-undernet-id'er skal have en CIDR-netværksstørrelse inkluderet, hvor netværksstørrelsen kan være mellem /8 og /29. Undernetområdet for flere LAN kan adskilles med et komma eller et semikolon.

1. Når du har tilføjet dine kontorplaceringer og gemt filen, skal du klikke  på knappen Gennemse ud for feltet **Upload fuldført** og vælge den gemte CSV-fil.

1. Filen bliver automatisk valideret. Hvis der er valideringsfejl, får du vist fejlmeddelelsen: _Der er nogle fejl i importfilen. Gennemse fejlene, ret importfilen, og prøv igen._ Klik på linket Åbn **fejloplysninger for at** få vist en liste over bestemte feltvalideringsfejl.

   > [!div class="mx-imgBorder"]
   > ![Fejlmeddelelse for CSV-import.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. Hvis der ikke er nogen fejl i filen, får du vist meddelelsen: _Rapporten er klar. Der blev fundet x-placeringer, der skal tilføjes, og x-placeringer, der skal opdateres._ Klik på **knappen Importér** for at overføre CSV-filen.

   > [!div class="mx-imgBorder"]
   > ![Klar meddelelse til CSV-import.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>Ofte stillede spørgsmål

### <a name="what-is-a-microsoft-365-service-front-door"></a>Hvad er en Microsoft 365 service front dør?

Frontporten Microsoft 365 er et indgangspunkt på Microsofts globale netværk, hvor Office klienter og tjenester afslutter deres netværksforbindelse. For at opnå en optimal Microsoft 365 forbindelse til en netværksforbindelse anbefales det, at din netværksforbindelse afsluttes i den nærmeste Microsoft 365 frontport.

>[!NOTE]
>Microsoft 365 servicefrontporte har ingen direkte relation til det Azure Front Door Service-produkt, der er tilgængeligt på Azure Marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Hvad er en optimal Microsoft 365 service front door?

En optimal Microsoft 365 service front door er en, der er tættest på dit netværks udgangspunkt, generelt i din by eller metroområde. Brug Microsoft 365 [forbindelsesværktøjet](office-365-network-mac-perf-onboarding-tool.md) til at bestemme placeringen af din in-use Microsoft 365 service front door og optimal service front door. Hvis værktøjet afgør, at din in-use front door er optimal, opretter du optimal forbindelse til Microsofts globale netværk.

### <a name="what-is-an-internet-egress-location"></a>Hvad er en internet udgangspunkt placering?

Internetudgangsplaceringen er den placering, hvor netværkstrafikken afslutter virksomhedsnetværket og opretter forbindelse til internettet. Dette identificeres også som den placering, hvor du har en enhed til oversættelse af netværksadresse (NAT), og som regel der, hvor du opretter forbindelse til en internetudbyder. Hvis du ser en lang afstand mellem din placering og din internetud udgangspunkt, kan dette indikere en betydelig WAN-backhaul.

### <a name="what-license-is-needed-for-this-capability"></a>Hvilken licens er nødvendig til denne funktion?

Du kræver en licens, der giver adgang til Microsoft 365 Administration.

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 netværksindsigt](office-365-network-mac-perf-insights.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 forbindelsesværktøj](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 til placeringstjenester for netværksforbindelse](office-365-network-mac-location-services.md)
