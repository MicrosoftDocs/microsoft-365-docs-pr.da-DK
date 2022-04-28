---
title: Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 07/08/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
- SPO_Content
description: Få mere at vide om, hvordan du kontrollerer oversigten over forbindelser på klientcomputeren for at hjælpe dig med at registrere nye problemer tidligt.
ms.openlocfilehash: ceb56f88d057d3a003f158369c9d35223852c7fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100429"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik

Der er nogle enkle måder at kontrollere forbindelsesydeevnen mellem Office 365 og din virksomhed på, så du kan etablere en grov grundlinje for din forbindelse. Hvis du kender ydeevnehistorikken for dine klientcomputerforbindelser, kan det hjælpe dig med at registrere nye problemer tidligt, identificere og forudsige problemer.
  
Hvis du ikke er vant til at arbejde med problemer med ydeevnen, er denne artikel designet til at hjælpe dig med at overveje nogle almindelige spørgsmål. Hvordan ved du, at det problem, du oplever, er et problem med ydeevnen og ikke en Office 365 tjenestehændelse? Hvordan kan du planlægge en god ydeevne på lang sigt? Hvordan kan du holde øje med ydeevnen? Hvis dit team eller dine klienter oplever langsom ydeevne, mens du bruger Office 365, og du undrer dig over nogen af disse spørgsmål, kan du læse videre.
  
> [!IMPORTANT]
> **Har du problemer med ydeevnen mellem din klient og Office 365 lige nu?** Følg de trin, der er beskrevet i [fejlfindingsplanen for ydeevne for Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Noget, du bør vide om Office 365 ydeevne

Office 365 bor i et dedikeret Microsoft-netværk med høj kapacitet, der overvåges af automatisering og rigtige mennesker. En del af vedligeholdelsen af Office 365 clouden er justering og strømlining af ydeevnen, hvor det er muligt. Da klienter i Office 365 cloud skal oprette forbindelse over internettet, er der også gjort en løbende indsats for at finjustere ydeevnen på tværs af Office 365 tjenester.

Forbedringer af ydeevnen stopper aldrig rigtig i cloudmiljøet, så det er heller ikke erfaringen med at holde clouden sund og hurtig. Hvis du har problemer med ydeevnen, når du opretter forbindelse fra din placering til Office 365, er det bedst ikke at starte med eller vente på en supportsag. Du bør i stedet begynde at undersøge problemet fra "indefra og ud". Det vil altså være, starte inde i dit netværk, og arbejde dig ud til at Office 365. Før du åbner en sag med Support, kan du indsamle data og foretage handlinger, der vil udforske og muligvis løse problemet.
  
> [!IMPORTANT]
> Vær opmærksom på kapacitetsplanlægning og begrænsninger i Office 365. Disse oplysninger vil sætte dig foran kurven, når du forsøger at løse et problem med ydeevnen. Her er et link til [tjenestebeskrivelserne for Microsoft 365 og Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Dette er en central hub, og alle de tjenester, der tilbydes af Office 365 har et link, der går til deres egne tjenestebeskrivelser herfra. Det betyder, at hvis du har brug for at se standardgrænserne for SharePoint Online, skal du f.eks. klikke på [SharePoint beskrivelse af onlinetjenesten](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) og finde [sektionen SharePoint Onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).
  
Sørg for at gå ind i fejlfindingen med forståelsen af, at ydeevnen er en glidende skala. Det handler ikke om at opnå en idealiseret værdi og vedligeholde den permanent. Lejlighedsvise opgaver med høj båndbredde, f.eks. ombordstigning af et stort antal brugere eller store datamigreringer, vil være stressende, så *planlæg* for indvirkning på ydeevnen derefter. Du skal have en grov idé om dine ydeevnemål, men mange variabler spiller ind i ydeevnen, så ydeevnen varierer.
  
Fejlfinding af ydeevnen handler ikke om at opfylde bestemte mål og bevare disse tal på ubestemt tid. Det handler om at forbedre eksisterende aktiviteter på grund af alle variablerne. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>Okay, hvordan ser et problem med ydeevnen ud?

Først skal du sikre dig, at det, du oplever, faktisk er et problem med ydeevnen og ikke en tjenestehændelse. Et problem med ydeevnen er forskelligt fra en tjenestehændelse i Office 365. Sådan adskiller du dem fra hinanden.
  
Tjenestehændelser sker, når selve Office 365-tjenesten har problemer. Du kan muligvis se røde eller gule ikoner under **Aktuel tilstand** i Microsoft 365 Administration. Du kan opleve, at ydeevnen på klientcomputere, der opretter forbindelse til Office 365 er langsom. Hvis Aktuel tilstand f.eks. rapporterer et rødt ikon, og du ser **Undersøgelse** ud for Exchange, kan du også få opkald fra personer i din organisation, der klager over, at klientpostkasser, der bruger Exchange Online er langsomme. I så fald er det rimeligt at antage, at din Exchange Online ydeevne var et offer for problemer med tjenesten.
  
![Dashboardet Office 365 Tilstand, hvor alle arbejdsbelastninger vises med grønt, undtagen Exchange, hvor Service Restored vises.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
På dette tidspunkt skal du, Office 365 administrator, kontrollere **Aktuel tilstand** og derefter **Få vist detaljer og historik**, ofte, for at holde dig opdateret om vedligeholdelsen af systemet. Dashboardet **Aktuel tilstand** blev foretaget for at opdatere dig om ændringer af og problemer i tjenesten. De noter og forklaringer, der er skrevet til tilstandshistorikken, administrator til administrator, er der for at hjælpe dig med at måle og holde dig opdateret om igangværende arbejde.
  
![Et billede af dashboardet Office 365 tilstand, der forklarer, at tjenesten Exchange Online er blevet gendannet, og hvorfor.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Et problem med ydeevnen er ikke en tjenestehændelse, selvom hændelser kan medføre langsom ydeevne. Et problem med ydeevnen ser sådan ud:
  
- Der opstår et problem med ydeevnen, uanset hvad Administration **Aktuel tilstand** rapporterer for tjenesten.
    
-  En funktionsmåde, der bruges til at flowe, tager lang tid at fuldføre eller aldrig fuldføres.
    
- Du kan også replikere problemet, eller du ved, at det vil ske, hvis du udfører den rigtige række trin.
    
-  Hvis problemet er forbigående, kan der stadig være et mønster. Du ved f.eks., at du senest kl. 10:00 har opkald fra brugere, der ikke altid har adgang til Office 365. Opkaldene slutter ved middagstid.
    
Listen lyder nok bekendt. måske for velkendt. Når du er klar over, at det er et problem med ydeevnen, bliver spørgsmålet "Hvad skal du foretage dig?" Resten af denne artikel hjælper dig med at finde ud af præcis det.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Sådan definerer og tester du problemet med ydeevnen

Der opstår ofte problemer med ydeevnen over tid, så det kan være en udfordring at definere det faktiske problem. Opret en god problemsætning med en god idé om problemkontekst, og derefter skal du gentagelige testtrin. Her er nogle eksempler på problemerklæringer, der ikke indeholder tilstrækkelige oplysninger:
  
- At skifte fra min indbakke til min kalender var tidligere noget, jeg ikke bemærkede, og nu er det en kaffepause. Kan du få det til at opføre sig som det plejede?
    
- Det tager for evigt at uploade mine filer til SharePoint Online. Hvorfor er det langsomt om eftermiddagen, men nogen anden gang, det er hurtigt? Kan det ikke bare være hurtigt?
    
Der er flere store udfordringer forbundet med ovenstående problemerklæringer. Specifikt for mange flertydigheder til at håndtere. Eksempel:
  
- Det er uklart, hvordan skift mellem Indbakke og Kalender plejede at fungere på den bærbare computer.
    
- Når brugeren siger "Kan det ikke bare være hurtigt", hvad er "hurtigt"?
    
- Hvor længe er "for evigt"? Er det nogle sekunder? Eller mange minutter? Eller kan brugeren spise frokost, og handlingen afsluttes 10 minutter, efter at vedkommende er kommet tilbage?
    
Administratoren og fejlfindingsværktøjet kan ikke være opmærksomme på *detaljerne* om problemet fra generelle sætninger som disse. De ved f.eks. ikke, hvornår problemet begyndte at ske. Fejlfindingsværktøjet ved muligvis ikke, at brugeren arbejder hjemmefra og kun ser langsom skift, mens vedkommende arbejder på sit hjemmenetværk. Eller at brugeren kører andre RAM-intensive programmer på den lokale klient. Administratorer ved muligvis ikke, at brugeren kører et ældre operativsystem, eller at de ikke har kørt de seneste opdateringer.
  
Når brugerne rapporterer et problem med ydeevnen, er der mange oplysninger, der skal indsamles. Hentning og optagelse af oplysninger kaldes at omforme problemet. Her er en grundlæggende liste over områder, du kan bruge til at indsamle oplysninger om problemer med ydeevnen. Denne liste er ikke udtømmende, men den er et sted, hvor du kan starte:
  
- På hvilken dato skete problemet, og omkring hvilket tidspunkt på dagen eller natten?
    
- Hvilken type klientcomputer brugte du, og hvordan opretter den forbindelse til virksomhedsnetværket (VPN, Kablet, Trådløs)?
    
- Arbejdede du eksternt, eller var du på kontoret?
    
- Har du prøvet de samme handlinger på en anden computer og set den samme funktionsmåde?
    
- Gennemgå de trin, der giver dig problemer, så du kan skrive de handlinger, du foretager.
    
- Hvor langsom i sekunder eller minutter er ydeevnen?
    
- Hvor i verden er du placeret?
    
Nogle af disse spørgsmål er mere indlysende end andre. De fleste alle vil forstå, at et fejlfindingsværktøj skal bruge de nøjagtige trin for at genskabe problemet. Når alt kommer til alt, hvordan kan du ellers registrere, hvad der er galt, og hvordan kan du ellers teste, om problemet er løst? Mindre indlysende er ting som "Hvilken dato og hvilket klokkeslæt så du problemet?", og "Hvor i verden er du placeret?", oplysninger, der kan bruges sammen. Afhængigt af hvornår brugeren arbejdede, kan nogle få timers tidsforskel betyde, at der allerede er vedligeholdelse i gang på dele af virksomhedens netværk. Din virksomhed har f.eks. en hybrid implementering, f.eks. en hybrid SharePoint Search, som kan forespørge søgeindekser i både SharePoint Online og en forekomst i det lokale miljø SharePoint Server 2013, og der kan være opdateringer i gang i farmen i det lokale miljø. Hvis din virksomhed befinder sig i et cloudmiljø, kan systemvedligeholdelse omfatte tilføjelse eller fjernelse af netværkshardware, udrulning af opdateringer i hele virksomheden eller ændring af DNS eller anden kerneinfrastruktur.
  
Når du foretager fejlfinding af et problem med ydeevnen, er det lidt ligesom et gerningssted, du skal være præcis og opmærksom for at drage konklusioner fra beviserne. For at gøre dette skal du få en god problemerklæring ved at indsamle beviser. Den skal omfatte computerens kontekst, brugerens kontekst, hvornår problemet begyndte, og de nøjagtige trin, der viste problemet med ydeevnen. Denne problemerklæring bør være, og forblive, den øverste side i dine noter. Ved at gennemgå problemerklæringen igen, når du har arbejdet på løsningen, tager du trinnene til at teste og bevise, om de handlinger, du foretager, har løst problemet. Dette er afgørende for at vide, hvornår dit arbejde, der, er færdig.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Ved du, hvordan ydeevne plejede at se ud, når det var godt?

Hvis du er uheldig, ved ingen det. Ingen havde numre. Det betyder, at ingen kan besvare det enkle spørgsmål "Hvor mange sekunder brugte det at hente en Indbakke op i Office 365?", eller "Hvor lang tid tog det at tage, da direktørerne havde et Lync Online-møde?", hvilket er et almindeligt scenarie for mange virksomheder.
  
Hvad mangler der her, er en oprindelig ydeevne?
  
Grundlinjer giver dig en kontekst for din ydeevne. Du bør nogle gange bruge en oprindelig plan til ofte, afhængigt af virksomhedens behov. Hvis du er en større virksomhed, kan dit operationsteam allerede tage udgangspunkt i de oprindelige planer for dit lokale miljø. Hvis du f.eks. reparerer alle Exchange servere den første mandag i måneden og alle dine SharePoint servere den tredje mandag, har operationsteamet sandsynligvis en liste over opgaver og scenarier, der køres efter programrettelsen, for at bevise, at kritiske funktioner fungerer. Du kan f.eks. åbne indbakken, klikke på Send/modtag og sikre, at mapperne opdateres, eller i SharePoint gennemse hovedsiden på webstedet, gå til virksomhedssøgesiden og udføre en søgning, der returnerer resultater.
  
Hvis dine programmer er i Office 365, kan du bruge nogle af de mest grundlæggende grundlinjer til at måle tiden (i millisekunder) fra en klientcomputer på netværket til et udgående punkt eller det punkt, hvor du forlader netværket og går ud for at Office 365. Her er nogle nyttige grundlinjer, som du kan undersøge og registrere:
  
- Identificer enhederne mellem klientcomputeren og udgående data, f.eks. proxyserveren.
    
  - Du skal kende dine enheder, så du har kontekst (IP-adresser, enhedstype, et cetera) for problemer med ydeevnen, der opstår.
    
  - Proxyservere er almindelige udgående punkter, så du kan kontrollere din webbrowser for at se, hvilken proxyserver den er indstillet til at bruge, hvis der er nogen.
    
  - Der findes tredjepartsværktøjer, der kan finde og tilknytte dit netværk, men den sikreste måde at kende dine enheder på er ved at spørge et medlem af dit netværksteam.
    
- Identificer internetudbyderen, skriv deres kontaktoplysninger ned, og spørg, hvor mange kredsløb du har.
    
- Identificer ressourcer til enhederne mellem din klient og udgående data i din virksomhed, eller identificer en nødkontakt for at tale med om netværksproblemer.
    
Her er nogle grundlinjer, som simple test med værktøjer kan beregne for dig:
  
- Tid fra klientcomputeren til udgående data i millisekunder
    
- Tid fra dit udgangspunkt til Office 365 i millisekunder
    
- Placering i verden af den server, der fortolker URL-adresserne for Office 365, når du gennemser
    
- Hastigheden for internetudbyderens DNS-opløsning i millisekunder, uoverensstemmelser i pakkemodtagelse (netværks-jitter), upload og downloadtider i millisekunder
    
Hvis du ikke er fortrolig med, hvordan du udfører disse trin, går vi mere i detaljer i denne artikel. 
  
## <a name="what-is-a-baseline"></a>Hvad er en oprindelig plan?

Du kender virkningen, når det går dårligt, men hvis du ikke kender dine historiske ydeevnedata, er det ikke muligt at have en kontekst for, hvor slemt det kan være blevet, og hvornår. Så uden en baseline, mangler du det vigtigste fingerpeg til at løse puslespillet: billedet på puslespillet boksen. I forbindelse med fejlfinding af ydeevnen skal du bruge et  *sammenligningspunkt*. Enkle grundlinjer for ydeevne er ikke svære at tage. Dit operationsteam kan få til opgave at udføre disse efter en tidsplan. Lad os f.eks. sige, at din forbindelse ser sådan ud: 
  
![En grundlæggende netværksgrafik, der viser klient, proxy og Office 365 cloud.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Det betyder, at du har tjekket med dit netværksteam og fundet ud af, at du forlader din virksomhed til internettet via en proxyserver, og at proxyen håndterer alle de anmodninger, som klientcomputeren sender til cloudmiljøet. I dette tilfælde skal du tegne en forenklet version af din forbindelse, der viser alle de mellemliggende enheder. Indsæt nu værktøjer, som du kan bruge til at teste ydeevnen mellem klienten, udgående data (hvor du forlader dit netværk til internettet) og Office 365 cloudmiljøet.
  
![Grundlæggende netværk med klient-, proxy- og cloud- og værktøjsforslag TIL PSPing, TraceTCP og netværkssporinger.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Mulighederne er angivet som **Simple** og **Advanced** på grund af den ekspertise, du har brug for for at finde ydelsesdataene. En netværkssporing vil tage lang tid sammenlignet med at køre kommandolinjeværktøjer som PsPing og TraceTCP. Disse to kommandolinjeværktøjer blev valgt, fordi de ikke bruger ICMP-pakker, som blokeres af Office 365, og fordi de giver den tid i millisekunder, det tager at forlade klientcomputeren eller proxyserveren (hvis du har adgang) og ankommer til Office 365. Hvert enkelt hop fra én computer til en anden vil ende med en tidsværdi, og det er fantastisk til grundlinjer! Lige så vigtigt er det, at disse kommandolinjeværktøjer giver dig mulighed for at føje et portnummer til kommandoen. Dette er nyttigt, fordi Office 365 kommunikerer via port 443, som er den port, der bruges af SSL og TLS (Secure Sockets Layer and Transport Layer Security). Andre tredjepartsværktøjer kan dog være bedre løsninger til din situation. Microsoft understøtter ikke alle disse værktøjer, så hvis du af en eller anden grund ikke kan få PsPing og TraceTCP til at fungere, skal du gå videre til en netværkssporing med et værktøj som Netmon. 
  
Du kan tage en oprindelig plan før arbejdstiden, igen under kraftig brug og derefter igen efter timer. Det betyder, at du kan have en mappestruktur, der ser lidt sådan ud i sidste ende:
  
![Grafik, der foreslår en metode til at organisere dine ydeevnedata i mapper.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Du bør også vælge en navngivningskonvention for dine filer. Her er nogle eksempler:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf
    
Der er mange forskellige måder at gøre dette på, men brug af formatet **\<dateTime\>\<what's happening in the test\>** er et godt sted at starte. Hvis du er omhyggelig med dette, hjælper det meget, når du forsøger at foretage fejlfinding af problemer senere. Senere kan du sige "Jeg tog to spor den 8. februar, en viste god ydeevne og en viste dårlig, så vi kan sammenligne dem". Dette er nyttigt i forbindelse med fejlfinding. 
  
Du skal have en organiseret måde at bevare dine historiske oprindelige planer på. I dette eksempel producerede de enkle metoder tre kommandolinjeoutput, og resultaterne blev indsamlet som skærmbilleder, men du har muligvis netværkshentningsfiler i stedet. Brug den metode, der fungerer bedst for dig. Store dine historiske grundlinjer, og se dem på steder, hvor du bemærker ændringer i funktionsmåden for onlinetjenester. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Hvorfor indsamle ydeevnedata under et pilotprojekt?

Der er ikke noget bedre tidspunkt at begynde at oprette grundlinjer på end under en pilotversion af Office 365-tjenesten. Dit kontor kan have tusindvis af brugere, hundredtusindvis, eller det kan have fem, men selv med nogle få brugere kan du udføre test for at måle udsving i ydeevnen. I tilfælde af en stor virksomhed kan en repræsentativ prøve på flere hundrede brugere, der piloter Office 365 projekteres ud til flere tusinder, så du ved, hvor der kan opstå problemer, før de opstår.
  
I tilfælde af en lille virksomhed, hvor ombordstigning betyder, at alle brugere går til tjenesten på samme tid, og der ikke er nogen pilot, skal du holde præstationsmålinger, så du har data, der skal vises til alle, der muligvis er nødt til at foretage fejlfinding af en handling med dårlig ydeevne. Hvis du f.eks. bemærker, at du pludselig kan gå rundt i din bygning i den tid, det tager at uploade en mellemstor grafik, hvor det plejede at ske hurtigt.
  
## <a name="how-to-collect-baselines"></a>Sådan indsamler du oprindelige planer

For alle fejlfindingsplaner skal du som minimum identificere disse ting:
  
- Den klientcomputer, du bruger (typen af computer eller enhed, en IP-adresse og de handlinger, der forårsagede problemet)
    
- Hvor klientcomputeren er placeret i verden (f.eks. om denne bruger på en VPN-forbindelse til netværket, arbejder eksternt eller på virksomhedens intranet)
    
- Det udgangspunkt, som klientcomputeren bruger fra dit netværk (det punkt, hvor trafikken forlader virksomheden til en internetudbyder eller internettet)
    
 Du kan finde ud af netværkets layout fra netværksadministratoren. Hvis du er på et lille netværk, kan du se på de enheder, der forbinder dig til internettet, og ringe til internetudbyderen, hvis du har spørgsmål om layoutet. Opret et billede af det endelige layout til referencen. 
  
Dette afsnit er opdelt i enkle kommandolinjeværktøjer og -metoder og mere avancerede værktøjer. Vi kommer først ind på enkle metoder. Men hvis du har problemer med ydeevnen lige nu, skal du gå til avancerede metoder og prøve handlingsplan for ydeevnefejlfinding.
  
### <a name="simple-methods"></a>Enkle metoder

Formålet med disse enkle metoder er at lære at tage, forstå og gemme simple grundlinjer for ydeevne korrekt over tid, så du bliver informeret om Office 365 ydeevne. Her er det enkle diagram til simple, som du har set før:
  
![Grundlæggende netværk med klient-, proxy- og cloud- og værktøjsforslag TIL PSPing, TraceTCP og netværkssporinger.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP er inkluderet i dette skærmbillede, fordi det er et nyttigt værktøj til at vise, i millisekunder, hvor lang tid det tager at behandle en anmodning, og hvor mange netværkshop eller forbindelser fra én computer til den næste, som anmodningen tager for at nå frem til en destination. TraceTCP kan også angive navnene på de servere, der bruges under hop, hvilket kan være nyttigt for en Microsoft Office 365 fejlfinding i Support. > TraceTCP-kommandoer kan være meget enkle, f.eks.: >  `tracetcp.exe outlook.office365.com:443`> Husk at medtage portnummeret i kommandoen! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) er en gratis download, men er afhængig af Wincap. Wincap er et værktøj, der også bruges og installeres af Netmon. Vi bruger også Netmon i afsnittet om avancerede metoder. 
  
 Hvis du har flere kontorer, skal du også opbevare et sæt data fra en klient på hver af disse placeringer. Denne test måler ventetid, som i dette tilfælde er en talværdi, der beskriver den tid, der går mellem en klient, der sender en anmodning til Office 365, og Office 365 at svare på anmodningen. Testen stammer fra dit domæne på en klientcomputer og ser ud til at måle en rundtur inde fra dit netværk, ud gennem et udgående punkt på tværs af internettet for at Office 365 og tilbage igen. 
  
Der er et par måder at håndtere udgående punkt på, i dette tilfælde proxyserveren. Du kan enten spore fra 1 til 2 og derefter 2 til 3 og derefter tilføje tallene i millisekunder for at få en endelig total til kanten af dit netværk. Du kan også konfigurere forbindelsen til at tilsidesætte proxyen for Office 365 adresser. I et større netværk med en firewall, omvendt proxy eller en kombination af de to skal du muligvis gøre undtagelser på proxyserveren, der tillader trafik at passere for mange URL-adresser. Du kan finde en liste over de slutpunkter, der bruges af Office 365, [under Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Hvis du har en godkendelsesproxy, skal du begynde med at teste undtagelser for følgende:
  
- Porte 80 og 443
    
- TCP- og HTTP-adresser
    
- Forbindelser, der er udgående til en af disse URL-adresser:
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Alle brugere skal have tilladelse til at få adgang til disse adresser uden proxyforstyrrelser eller godkendelse. På et mindre netværk skal du føje disse til din liste over omgåelse af proxy i webbrowseren. 
  
Hvis du vil føje disse til din proxyoversigt i Internet Explorer, skal du gå til **Funktioner** \> **Internetindstillinger** \> **Forbindelser** \> **LAN-indstillinger** \> **Avanceret**. Under fanen Avanceret kan du også finde proxyserveren og proxyserverporten. Du skal muligvis markere afkrydsningsfeltet **Brug en proxyserver til lan'et for** at få adgang til knappen **Avanceret** . Du skal sikre dig, at **Tilsidesæt proxyserveren for lokale adresser** er markeret. Når du klikker på **Avanceret**, får du vist et tekstfelt, hvor du kan angive undtagelser. Adskil url-adresserne med jokertegn, der er angivet ovenfor, med semikolon, f.eks.:
  
\*.microsoftonline.com; \*.sharepoint.com
  
Når du springer din proxy over, bør du kunne bruge ping eller PsPing direkte på en Office 365 URL-adresse. Det næste trin er at teste ping **outlook.office365.com**. Eller hvis du bruger PsPing eller et andet værktøj, der giver dig mulighed for at angive et portnummer til kommandoen, kan PsPing mod **portal.microsoftonline.com:443** for at se den gennemsnitlige rundturstid i millisekunder. 
  
Rundturstiden eller RTT er en talværdi, der måler, hvor lang tid det tager at sende en HTTP-anmodning til en server, f.eks. outlook.office365.com og få et svar tilbage, der bekræfter, at serveren ved, at du har gjort det. Du kan nogle gange se dette forkortet som RTT. Dette bør være en relativt kort mængde tid.
  
Du skal bruge [PSPing](/sysinternals/downloads/psping) eller et andet værktøj, der ikke bruger ICMP-pakker, der er blokeret af Office 365, for at udføre denne test. 
  
 **Sådan bruger du PsPing til at få en samlet rundturstid i millisekunder direkte fra en Office 365 URL-adresse**
  
1. Kør en kommandoprompt med administratorrettigheder ved at udføre disse trin:
    
1. Klik på **Start**.
    
2. Skriv cmd i feltet **Start søgning** , og tryk derefter på CTRL+SKIFT+ENTER.
    
3. Hvis dialogboksen **Brugerkontokontrol** vises, skal du bekræfte, at den handling, der vises, er, hvad du ønsker, og derefter klikke på **Fortsæt**.
    
2. Naviger til den mappe, hvor værktøjet (i dette tilfælde PsPing) er installeret, og test disse Office 365 URL-adresser:
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![PSPing-kommandoen microsoft-my.sharepoint.com port 443.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Sørg for at inkludere portnummeret 443. Husk, at Office 365 fungerer på en krypteret kanal. Hvis du bruger PsPing uden portnummeret, mislykkes din anmodning. Når du har pinget din korte liste, skal du kigge efter den gennemsnitlige tid i millisekunder (ms). Det er det, du vil optage!
  
![Grafik, der viser en illustration af klient til proxy-PSPing med en rundtur på 2,8 millisekunder.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Hvis du ikke er bekendt med proxy bypass, og foretrækker at tage tingene trin for trin, skal du først finde ud af navnet på din proxy-server. I Internet Explorer skal du gå til **Funktioner** \> **Internetindstillinger** \> **Forbindelser** \> **LAN-indstillinger** \> **Avanceret**. Under fanen **Avanceret** kan du se din proxyserver angivet. Ping proxyserveren ved en kommandoprompt ved at fuldføre denne opgave: 
  
 **Sådan pinger du proxyserveren og får en rundtursværdi i millisekunder for fase 1 til 2**
  
1. Kør en kommandoprompt med administratorrettigheder ved at udføre disse trin:
    
1. Klik på **Start**.
    
2. Skriv cmd i feltet **Start søgning** , og tryk derefter på CTRL+SKIFT+ENTER.
    
3. Hvis dialogboksen **Brugerkontokontrol** vises, skal du bekræfte, at den handling, der vises, er, hvad du ønsker, og derefter klikke på **Fortsæt**.
    
2. Skriv ping \<the name of the proxy server your browser uses, or the IP address of the proxy server\> , og tryk derefter på ENTER. Hvis du har installeret PsPing eller et andet værktøj, kan du vælge at bruge dette værktøj i stedet. 
    
    Kommandoen kan se ud som et af disse eksempler: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Når sporingen stopper med at sende testpakker, får du en lille oversigt, der viser et gennemsnit i millisekunder, og det er den værdi, du er ude efter. Tag et skærmbillede af prompten, og gem den ved hjælp af navngivningskonventionen. På dette tidspunkt kan det også hjælpe at udfylde diagrammet med værdien.
    
Måske har du sporet tidligt om morgenen, og din klient kan hurtigt få adgang til proxyen (eller en hvilken som helst udgangsserver, der forlader internettet). I dette tilfælde kan dine tal se sådan ud:
  
![Grafik, der viser rundturstiden fra en klient til en proxy på 2,8 millisekunder.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Hvis din klientcomputer er en af de få udvalgte med adgang til proxyserveren (eller udgående server), kan du køre den næste del af testen ved at fjerntilslutte den pågældende computer og køre kommandoprompten til PsPing til en Office 365 URL-adresse derfra. Hvis du ikke har adgang til denne computer, kan du kontakte dine netværksressourcer for at få hjælp til det næste ben og få præcise tal på den måde. Hvis det ikke er muligt, skal du tage en PsPing mod den pågældende Office 365 URL-adresse og sammenligne den med PsPing- eller Ping-tiden i forhold til din proxyserver. 
  
Hvis du f.eks. har 51,84 millisekunder fra klienten til URL-adressen til Office 365, og du har 2,8 millisekunder fra klienten til proxyen (eller udgående punkt), har du 49,04 millisekunder fra udgående data til Office 365. Hvis du på samme måde har en PsPing på 12,25 millisekunder fra klienten til proxyen i løbet af dagens højde og 62,01 millisekunder fra klienten til den Office 365 URL-adresse, er din gennemsnitlige værdi for proxyudgang til den Office 365 URL-adresse 49,76 millisekunder.
  
![Yderligere grafik, der viser ping i millisekunder fra klient til proxy ud for klient til Office 365 så værdierne kan trækkes fra.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Med hensyn til fejlfinding kan du finde noget interessant, blot ved at bevare disse grundlinjer. Hvis du f.eks. finder ud af, at du generelt har ca. 40 millisekunder til 59 millisekunders ventetid fra proxy- eller udgående punkt til url-adressen for Office 365 og har en ventetid på ca. 3 millisekunder til 7 millisekunder (afhængigt af den mængde netværkstrafik, du ser i løbet af den pågældende tid på dagen), vil du helt sikkert vide, at der er noget problematisk, hvis din sidste tre klient til proxy- eller udgående baselines viser en ventetid på 45 millisekunder.
  
### <a name="advanced-methods"></a>Avancerede metoder

Hvis du virkelig vil vide, hvad der sker med dine internetanmodninger om at Office 365, skal du blive fortrolig med netværkssporinger. Det er ligegyldigt, hvilke værktøjer du foretrækker til disse sporinger, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, Udviklerdashboardværktøj eller andre, så længe dette værktøj kan registrere og filtrere netværkstrafik. I dette afsnit kan du se, at det er en fordel at køre mere end ét af disse værktøjer for at få et mere komplet billede af problemet. Når du tester, fungerer nogle af disse værktøjer også som proxyer på egen hånd. Værktøjer, der bruges i den medfølgende artikel[: Plan for fejlfinding af ydeevne for Office 365](performance-troubleshooting-plan.md), omfatter [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) eller [WireShark](https://www.wireshark.org/).
  
At tage en grundlæggende ydeevne er den enkle del af denne metode, og mange af trinnene er de samme, som når du foretager fejlfinding af et problem med ydeevnen. De mere avancerede metoder til oprettelse af grundlinjer for ydeevne kræver, at du tager og gemmer netværkssporinger. De fleste af eksemplerne i denne artikel bruger SharePoint Online, men du bør udvikle en liste over almindelige handlinger på tværs af de Office 365 tjenester, som du abonnerer på test og registrer. Her er et eksempel på en oprindelig plan:
  
- Oprindelig liste for SPO - ** Trin 1: ** Gennemse startsiden for SPO-webstedet, og foretag en netværkssporing. Gem sporingen. 
    
- Oprindelig liste for SPO - **trin 2:** Søg efter et ord (f.eks dit firmanavn) via Enterprise Search, og foretag en netværkssporing. Gem sporingen. 
    
- Oprindelig liste for SPO – **trin 3:** Upload en stor fil til et SharePoint Online-dokumentbibliotek og foretage en netværkssporing. Gem sporingen. 
    
- Oprindelig liste for SPO - **trin 4:** Gennemse startsiden for det OneDrive websted, og foretag en netværkssporing. Gem sporingen. 
    
Denne liste bør indeholde de vigtigste almindelige handlinger, som brugerne foretager mod SharePoint Online. Bemærk, at det sidste trin, for at spore gå til OneDrive for Business, bygger i en sammenligning mellem belastningen af SharePoint Online hjemmeside (som ofte er tilpasset af virksomheder) og OneDrive for Business hjemmeside, som sjældent tilpasses. Dette er en grundlæggende test, når det kommer til en langsom indlæsning SharePoint Online-websted. Du kan oprette en post med denne forskel i din test.
  
Hvis du er midt i et problem med ydeevnen, er mange af trinnene de samme, som når du tager en oprindelig plan. Netværkssporinger bliver kritiske, så vi håndterer  *, hvordan*  vi tager de vigtige sporinger næste. 
  
Hvis du vil løse et problem med ydeevnen lige  *nu*, skal du spore det, når du oplever problemet med ydeevnen. Du skal have de rette værktøjer tilgængelige til at indsamle logge, og du skal bruge en handlingsplan, dvs. en liste over fejlfindingshandlinger, der skal udføres for at indsamle de bedste oplysninger, du kan. Det første, du skal gøre, er at registrere datoen og klokkeslættet for testen, så filerne kan gemmes i en mappe, der afspejler tidspunktet. Derefter skal du indsnævre til selve problemtrinnene. Dette er de nøjagtige trin, du skal bruge til test. Glem ikke det grundlæggende: Hvis problemet kun er med Outlook, skal du sørge for at registrere, at problemet kun sker i én Office 365 tjeneste. Hvis du begrænser omfanget af dette problem, kan det hjælpe dig med at fokusere på noget, du kan løse. 
  
## <a name="see-also"></a>Se også

[Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)