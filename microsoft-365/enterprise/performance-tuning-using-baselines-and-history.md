---
title: Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
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
description: Få mere at vide om, hvordan du kontrollerer historikken for dine klientcomputerforbindelser for at hjælpe dig med at registrere nye problemer tidligt.
ms.openlocfilehash: 7395b7459264a9463b2b850590163983873a13db
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63594236"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik

Der er nogle enkle måder at kontrollere ydeevnen i forbindelsen mellem Office 365 og din virksomhed, som gør det muligt at fastlægge en usleben grundlinje for dine forbindelser. Hvis du har en oversigt over ydeevnen for dine klientcomputerforbindelser, kan det hjælpe dig med at registrere nye problemer tidligt, identificere og forudsige problemer.
  
Hvis du ikke er vant til at arbejde på problemer med ydeevnen, er denne artikel beregnet til at hjælpe dig med at overveje nogle af de mest almindelige spørgsmål. Hvordan ved du, at det problem, du oplever, er et ydelsesproblem og ikke en Office 365-tjenestehændelse? Hvordan kan du planlægge god ydeevne på lang sigt? Hvordan kan man holde øje med ydeevnen? Hvis dit team eller dine kunder oplever langsom ydeevne, mens de bruger Office 365, og du er i tvivl om et af disse spørgsmål, skal du læse videre.
  
> [!IMPORTANT]
> **Har du ydelsesproblemet mellem din klient og Office 365 lige nu?** Følg de trin, der er beskrevet i [Planen for fejlfinding af ydeevne for Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Noget, du bør vide om Office 365 ydeevnen

Office 365 bor i et dedikeret Microsoft-netværk med høj kapacitet, som overvåges af automatisering og reelle personer. En del af vedligeholdelsen af Office 365 er justering og strømlining af ydeevnen, hvor det er muligt. Da klienterne fra Office 365-skyen skal oprette forbindelse via internettet, er der en løbende indsats på at finjustere ydeevnen på tværs Office 365-tjenester.

Forbedringer af ydeevnen stopper aldrig rigtigt i skyen, så ingen af delene er at holde skyen sund og hurtig. Hvis du har problemer med ydeevnen, når du opretter forbindelse fra din placering til Office 365, er det bedst ikke at starte med eller vente på en supportsag. I stedet skal du begynde at undersøge problemet indefra og ud. Det vil sige starte inde i dit netværk og gå din vej ud for at Office 365. Før du åbner en sag med Support, kan du indsamle data og udføre handlinger, der vil undersøge og muligvis løse problemet.
  
> [!IMPORTANT]
> Vær opmærksom på kapacitetsplanlægning og begrænsninger i Office 365. Med disse oplysninger kommer du foran kurven, når du forsøger at løse et ydelsesproblem. Her er et link til Microsoft 365 [og Office 365 over tjenester](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Dette er en central hub, og alle de tjenester, der tilbydes af Office 365, har et link, der går til deres egne tjenestebeskrivelser herfra. Det betyder, at hvis du f.eks. skal se standardgrænserne for SharePoint Online, skal du klikke [på Beskrivelse af SharePoint Onlinetjeneste](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) og finde dens [SharePoint Onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).
  
Sørg for, at du går til fejlfindingen med forståelsen for, at ydeevnen er en glidende skala. Det handler ikke om at opnå en idealiseret værdi og opretholde den permanent. Nogle gange vil opgaver med høj båndbredde, f.eks. at få et stort antal brugere til at komme i gang eller store dataoverflytninger, blive stressende, så *planlæg* efterfølgende for at forbedre ydeevnen. Du bør have en grove ide om dine mål, men mange variabler spiller ind i ydeevnen, så ydeevnen varierer.
  
Fejlfinding af ydeevne handler ikke om at opfylde specifikke mål og vedligeholde disse tal på ubestemt tid. Det handler om at forbedre eksisterende aktiviteter på trods af alle variablerne. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>OK, hvordan ser et ydelsesproblem ud?

Først skal du sikre dig, at det, du rent faktisk oplever, er et ydelsesproblem og ikke en tjenestehændelse. Ydelsesproblemet er anderledes end en tjenestehændelse i Office 365. Sådan kan du se, hvordan du kan få dem til at skille sig ud.
  
Tjenestehændelser sker, når Office 365 selv har problemer. Du kan muligvis se røde eller gule ikoner under **Aktuel** tilstand i Microsoft 365 Administration. Du bemærker muligvis ydeevnen på klientcomputere, der opretter forbindelse Office 365 er langsom. Hvis f.eks. Aktuel tilstand rapporterer et rødt ikon, og  du ser Undersøger ud for Exchange, får du muligvis også opkald fra personer i organisationen, der beklager sig over, at klientpostkasser, der bruger Exchange Online, er langsomme. I dette tilfælde er det fornuftigt at antage, at din Exchange Online offer for problemer med tjenesten.
  
![Dashboardet Tilstand Office 365 med alle arbejdsbelastninger, der viser grønt, undtagen Exchange, der viser Tjenesten er gendannet.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
På dette tidspunkt bør du, Office 365 administrator, kontrollere Aktuel tilstand og derefter Få  vist detaljer og **historik ofte for** at holde dig opdateret om vedligeholdelse af systemet. **Dashboardet Aktuel** tilstand blev foretaget for at opdatere dig om ændringer af og problemer med tjenesten. De noter og forklaringer, der er i tilstandshistorikken, fra administrator til administrator, er der for at hjælpe dig med at måle og for at holde dig opdateret om igangværende arbejde.
  
![Et billede af dashboardet Office 365 tilstand, der forklarer, at Exchange Online er blevet gendannet og hvorfor.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Ydelsesproblemet er ikke en tjenestehændelse, selvom hændelser kan medføre langsom ydeevne. Ydelsesproblemet ser sådan ud:
  
- Ydelsesproblemer opstår, uanset hvad Administration Aktuel **tilstand** rapporterer til tjenesten.
    
-  En funktionsmåde, der plejede at forløbe, tager lang tid at fuldføre eller aldrig fuldføre.
    
- Du kan også kopiere problemet, eller du ved, at det vil ske, hvis du udføre de rigtige trin.
    
-  Hvis problemet er periodisk, kan der stadig være et mønster. Du ved f.eks., at kl. 10:00 får du opkald fra brugere, der ikke altid kan få adgang til Office 365. Opkaldene afsluttes omkring middag.
    
Denne liste lyder sandsynligvis velkendt; måske for velkendt. Når du er klar over, at det er et ydelsesproblem, bliver spørgsmålet "Hvad gør du så?" Resten af denne artikel hjælper dig med at finde ud af netop det.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Sådan definerer og tester du ydelsesproblemet

Problemer med ydeevnen opstår ofte over tid, så det kan være en udfordring at definere det egentlige problem. Opret en god problemerklæring med en god ide om problemets kontekst, og så skal du gentage testtrinnene. Her er nogle eksempler på problemsætninger, der ikke giver nok oplysninger:
  
- Det at skifte fra min indbakke til min kalender plejede at være noget, som jeg ikke bemærker, og nu tager det lige så lang tid som en kaffepause. Kan du få det til at fungere, som det plejede?
    
- Det at uploade mine filer SharePoint Online tager uendelig lang tid. Hvorfor er det langsomt om aftenen, men på andre tidspunkt er det hurtigt? Kan det ikke bare være hurtigt?
    
Der er flere store udfordringer med ovenstående problemerklæringer. Mere specifikt er der for mange uklarheder til at håndtere. Eksempel:
  
- Det er uklart, hvordan skiftet mellem Indbakke og Kalender plejede at handle på den bærbare computer.
    
- Når brugeren siger "Kan det ikke blot være hurtigt", hvad er "hurtigt"?
    
- Hvor lang tid er "uendelig lang tid"? Er der flere sekunder? Eller mange minutter? Eller kan brugeren tage frokost, og handlingen blev færdig 10 minutter efter, brugeren kom tilbage?
    
Administratoren og fejlfindingsværktøjet kan ikke være opmærksom på *problemets* detaljer i generelle sætninger som disse. De ved f.eks. ikke, hvornår problemet begyndte at ske. Fejlfindingsværktøjet ved muligvis ikke, om brugeren arbejder hjemmefra og ser kun langsomme skift, mens brugeren er på hjemmenetværket. Eller at brugeren kører andre RAM-krævende programmer på den lokale klient. Administratorer ved muligvis ikke, om brugeren kører et ældre operativsystem eller ikke har kørt de seneste opdateringer.
  
Når brugerne rapporterer om ydelsesproblemer, er der mange oplysninger, der skal indsamles. Henter og registrerer oplysninger kaldes angivelse af problemets område. Her er en grundlæggende liste, du kan bruge til at indsamle oplysninger om problemer med ydeevnen. Listen er ikke komplet, men du kan starte den her:
  
- På hvilken dato skete problemet, og på hvilket tidspunkt af dagen eller om natten?
    
- Hvilken type klientcomputer brugte du, og hvordan opretter den forbindelse til virksomhedens netværk (VPN, kablet, trådløst)?
    
- Arbejdede du eksternt, eller var du på kontoret?
    
- Prøvede du de samme handlinger på en anden computer og fik vist den samme funktionsmåde?
    
- Gennemgå de trin, der giver dig problemer, så du kan skrive de handlinger, du laver.
    
- Hvor langsom i sekunder eller minutter er ydeevnen?
    
- Hvor i verden er du placeret?
    
Nogle af disse spørgsmål er mere tydelige end andre. De fleste vil forstå, at et fejlfindingsværktøjet skal bruge de nøjagtige trin for at genskabe problemet. Hvordan kan man jo ellers registrere, hvad der er galt, og hvordan kan man ellers teste, om problemet er løst? Mindre indlysende er ting som "Hvilken dato og hvilket klokkeslæt fik du vist problemet?" og "Hvor i verden er du placeret?", oplysninger, der kan bruges sammen. Afhængigt af hvornår brugeren arbejdede, kan et par timers tidsforskelle betyde, at der allerede er vedligeholdelse i gang på dele af virksomhedens netværk. Din virksomhed har f.eks. en hybrid implementering, f.eks. en hybrid SharePoint-søgning, som kan forespørgselssøgningsindekser i både SharePoint Online og en lokal SharePoint Server 2013-forekomst, opdateringer er muligvis i gang i den lokale farm. Hvis din virksomhed kun bruger skyen, kan systemvedligeholdelse omfatte tilføjelse eller fjernelse af netværkshardware, udrulning af opdateringer, som gælder for hele virksomheden, eller ændringer af DNS eller anden kerneinfrastruktur.
  
Når du foretager fejlfinding af et ydelsesproblem, er det lidt lige som et gerningssted, du skal være præcis og opmærksom for at drage konklusioner ud fra beviserne. For at gøre dette skal du have en god problemerklæring ved at indsamle beviser. Det bør omfatte computerens kontekst, brugerens kontekst, hvornår problemet startede samt de nøjagtige trin, der afsatte ydelsesproblemet. Problemerklæringen skal være, og skal blive ved med at være, den øverste side i dine noter. Ved at gennemgå problemsætningen igen, når du arbejder på løsningen, tester og beviser du, om de handlinger, du har udføre, har løst problemet. Dette er afgørende for at vide, hvornår dit arbejde er udført.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Ved du, hvordan ydeevnen plejede at se ud, når den var god?

Hvis du er uheldig, er der ingen, der ved det. Ingen havde tal. Det betyder, at ingen kan besvare det simple spørgsmål "Hvor mange sekunder plejede det at tage for at få en indbakke op i Office 365?" eller "Hvor lang tid plejede det at tage, når ledere havde et Lync Online-møde?", hvilket er et almindeligt scenarie for mange virksomheder.
  
Hvad mangler her, er en grundlinje for ydeevnen?
  
Grundlinjer giver dig en kontekst til din ydeevne. Du bør nogle gange have en grundlinje til ofte, afhængigt af behovene i din virksomhed. Hvis du er en større virksomhed, kan dit driftsteam muligvis allerede tage oprindelige planer for dit lokale miljø. Hvis du f.eks. laver programrettelser til alle Exchange-servere den første mandag i måneden og alle dine SharePoint-servere den tredje mandag, har dit Operations-team sandsynligvis en liste over opgaver og scenarier, som det kører efter programrettelsen, for at bevise, at de kritiske funktioner fungerer. Hvis du f.eks. åbner indbakken, klikker på Send/modtag og sikrer, at mapperne opdateres, eller du i SharePoint søger på webstedets hovedside, går til virksomhedens søgeside og foretager en søgning, der returnerer resultater.
  
Hvis dine programmer er i Office 365, vil nogle af de mest grundlæggende grundlinjer, du kan oprette, måle tid (i millisekunder) fra en klientcomputer inden i dit netværk, til et udgangspunkt eller det punkt, hvor du forlader dit netværk og går ud til Office 365. Her er nogle nyttige grundlinjer, som du kan undersøge og registrere:
  
- Identificer enhederne mellem klientcomputeren og dit udgangspunkt, f.eks. din proxyserver.
    
  - Du skal kende dine enheder, så du har kontekst (IP-adresser, enhedstype osv.) for de ydelsesproblemer, der opstår.
    
  - Proxyservere er almindelige udgangspunkter, så du kan kontrollere din webbrowser for at se, hvilken proxyserver den er indstillet til at bruge, hvis dette er nogen.
    
  - Der findes tredjepartsværktøjer, der kan opdage og tilknytte dit netværk, men den sikreste måde at kende dine enheder på er ved at spørge et medlem af dit netværksteam.
    
- Identificer serviceudbyder din internetudbyder (ISP), skriv kontaktoplysningerne ned, og spørg, hvor mange kredsløb, hvor meget båndbredde du har.
    
- Identificer ressourcer inden for virksomheden til enhederne mellem din klient og udgangspunktet, eller identificer en nødkontakt for at tale om netværksproblemer.
    
Her er nogle grundlinjer, som en simpel test med værktøjer kan beregne for dig:
  
- Tid fra klientcomputeren til dit udgangspunkt i millisekunder
    
- Tid fra dit udgangspunkt peger på Office 365 i millisekunder
    
- Placering i verden på den server, der løser URL-adresserne for Office 365, når du gennemser
    
- Hastigheden på din internetudbyders DNS-opløsning i millisekunder, uoverensstemmelser i pakkeankomsten (netværksjitter), tider for upload og download i millisekunder
    
Hvis du ikke ved, hvordan du udfører disse trin, går vi mere i detaljer i denne artikel. 
  
## <a name="what-is-a-baseline"></a>Hvad er en oprindelig plan?

Du kender påvirkningen, når det går dårligt, men hvis du ikke kender dine historiske ydeevnedata, er det ikke muligt at have en kontekst for, hvor dårligt det kan være blevet, og hvornår. Så uden en grundlinje mangler du det vigtigste fingerpeg for at løse puslespillet: billedet på puslespillet. Ved fejlfinding af ydeevne skal du have et  *sammenligningspunkt*. Enkle grundlinjer for ydeevnen er ikke svære at tage. Dit driftsteam kan have til opgave at udføre disse ud fra en tidsplan. Lad os f.eks. sige, at din forbindelse ser sådan ud: 
  
![Grundlæggende netværksgrafik, der viser klient, proxy og Office 365 skyen.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Det betyder, at du har tjekket med dit netværksteam og fandt ud af, at din virksomhed kommer på internettet via en proxyserver, og at proxy håndterer alle anmodninger, som klientcomputeren sender til skyen. I dette tilfælde skal du tegne en forenklet version af din forbindelse, der viser alle de mellemliggende enheder. Nu skal du indsætte værktøjer, som du kan bruge til at teste ydeevnen mellem klienten, udgangspunktet (hvor du efterlader dit netværk til internettet), og Office 365 skyen.
  
![Grundlæggende netværk med klient, proxy og sky, og værktøjsforslagene PSPing, TraceTCP og netværkssporing.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Indstillingerne vises som Enkle og **Avancerede** **på grund** af den mængde ekspertise, du har brug for til at finde dataene for ydeevnen. En netværkssporing tager meget tid sammenlignet med kørende kommandolinjeværktøjer som PsPing og TraceTCP. Disse to kommandolinjeværktøjer blev valgt, fordi de ikke bruger ICMP-pakker, som blokeres af Office 365, og fordi de giver tiden i millisekunder, det tager at forlade klientcomputeren eller proxyserveren (hvis du har adgang) og ankommer til Office 365. Hver enkelt hop fra én computer til en anden ender med en tidsværdi, og det er godt til grundlinjer! Lige så vigtigt er det, at disse kommandolinjeværktøjer giver dig mulighed for at føje et portnummer til kommandoen, dette er nyttigt, fordi Office 365 kommunikerer via port 443, som er den port, der bruges af Secure Sockets Layer og Transport Layer Security (SSL og TLS). Andre tredjepartsværktøjer kan dog være bedre løsninger til din situation. Microsoft understøtter ikke alle disse værktøjer, så hvis du af en eller anden grund ikke kan få PsPing og TraceTCP til at fungere, kan du gå videre til en netværkssporing med et værktøj som Netmon. 
  
Du kan oprette en grundlinje før åbningstid, igen under stor brug og derefter igen efter arbejdstid. Det betyder, at du måske har en mappestruktur, der ser lidt sådan ud i sidste ende:
  
![Grafik, som foreslår en metode til at organisere dine ydeevnedata i mapper.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Du bør også vælge en navngivningskonvention for dine filer. Her er nogle eksempler:
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Der er mange forskellige måder at gøre dette på, men det er et **\<dateTime\>\<what's happening in the test\>** godt sted at starte med at bruge formatet. Det vil hjælpe meget at være omhyggelig med dette, når du forsøger at foretage fejlfinding af problemer senere. Senere kan du sige: "Jeg har taget to sporinger den 8. februar, én viste god ydeevne, og en viste en dårlig ydeevne, så vi kan sammenligne dem". Dette er nyttigt til fejlfinding. 
  
Du skal have en organiseret måde at bevare dine historiske grundlinjer på. I dette eksempel fremstillede de enkle metoder tre kommandolinjeoutput, og resultaterne blev indsamlet som skærmbilleder, men du kan også indsamle filer i stedet. Brug den metode, der fungerer bedst for dig. Store dine historiske grundlinjer, og henvis til dem på punkter, hvor du bemærker ændringer i dine onlinetjenesters funktionsmåde. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Hvorfor indsamle data om ydeevne under et pilotprojekt?

Der er ikke noget bedre tidspunkt at begynde at lave grundlinjer på end under et pilotprojekt med Office 365 tjeneste. Dit Office kan have tusindvis af brugere, hundreder af tusinder, eller det kan have fem, men selv med nogle få brugere kan du udføre test til at måle udsving i ydeevnen. Hvis du arbejder i en stor virksomhed, kan en repræsentativ stikprøve af flere hundrede brugere på Office 365 projicere udad til flere tusinde, så du ved, hvor problemerne kan opstå, før de forekommer.
  
Hvis der er tale om en lille virksomhed, hvor over bordning betyder, at alle brugere går til tjenesten på samme tid, og der ikke er noget pilotprojekt, skal du opbevare målinger for ydeevnen, så du har data, der skal vises til alle, der kan være nødt til at foretage fejlfinding af en operation, hvor der er dårlig ydeevne. Hvis du f.eks. bemærker, at du pludselig kan gå rundt om din bygning i den tid, det tager at overføre en mellemstor grafik, hvor det plejede at ske hurtigt.
  
## <a name="how-to-collect-baselines"></a>Sådan indsamler du grundlinjer

For alle fejlfindingsplaner skal du som minimum identificere disse ting:
  
- Den klientcomputer, du bruger (den type computer eller enhed, en IP-adresse og de handlinger, der forårsagede problemet)
    
- Hvor klientcomputeren er placeret i verden (f.eks. om denne bruger på et VPN til netværket, arbejder eksternt eller på virksomhedens intranet)
    
- Det udgangspunkt, klientcomputeren bruger fra dit netværk (det punkt, hvor trafikken forlader din virksomhed for en internetudbyder eller internettet)
    
 Du kan finde ud, hvordan dit netværk har layout, fra netværksadministratoren. Hvis du er på et lille netværk, kan du kigge lidt på de enheder, der forbinder dig til internettet, og ringe til din internetudbyder, hvis du har spørgsmål til layoutet. Opret et billede af det endelige layout til referencen. 
  
Dette afsnit er opdelt i simple kommandolinjeværktøjer og metoder og mere avancerede værktøjer. Vi kommer først til at dække simple metoder. Men hvis du har et ydelsesproblem lige nu, skal du gå til avancerede metoder og prøve handlingsplanen til fejlfinding af ydeevne.
  
### <a name="simple-methods"></a>Simple metoder

Formålet med disse enkle metoder er at lære at tage, forstå og korrekt gemme simple grundlinjer med ydeevne over tid, så du får oplysninger om Office 365 ydeevnen. Her er det enkle diagram, som du har set før:
  
![Grundlæggende netværk med klient, proxy og sky, og værktøjsforslagene PSPing, TraceTCP og netværkssporing.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP er inkluderet i dette skærmbillede, fordi det er et nyttigt værktøj til at vise, i millisekunder, hvor lang tid det tager at behandle en anmodning, og hvor mange netværk hop eller forbindelser fra den ene computer til den næste, anmodningen bruger på at nå en destination. TraceTCP kan også give navnene på de servere, der blev brugt under hop, hvilket kan være nyttigt for et Microsoft Office 365 i Support. > TraceTCP-kommandoer kan være meget enkle, f.eks.: >  `tracetcp.exe outlook.office365.com:443`> Husk at medtage portnummeret i kommandoen! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) kan hentes gratis, men er afhængig af Wincap. Wincap er et værktøj, der også bruges og installeres af Netmon. Vi bruger også Netmon i afsnittet med avancerede metoder. 
  
 Hvis du har flere kontorer, skal du også beholde et sæt data fra en klient i hver af disse placeringer. Denne test måler ventetid, som i dette tilfælde er en talværdi, der beskriver mængden af tid mellem en klient, der sender en anmodning om at Office 365, Office 365 besvarer anmodningen. Testen stammer inde fra dit domæne på en klientcomputer og ser ud til at måle en returrejse inde fra dit netværk, ud gennem et udgangspunkt, på tværs af internettet for at Office 365 og tilbage. 
  
Der er flere måder at behandle udgangspunktet på, i dette tilfælde proxyserveren. Du kan enten spore fra 1 til 2 og derefter 2 til 3 og derefter tilføje tallene i millisekunder for at få en endelig total til kanten af dit netværk. Eller du kan konfigurere forbindelsen til at tilsidesætte proxyen for Office 365 adresser. I et større netværk med en firewall, omvendt proxy eller en kombination af de to kan det være nødvendigt at gøre undtagelser på proxyserveren, der tillader trafik at videregive mange URL-adresser. Du kan finde en liste over slutpunkter, der Office 365, [under Office 365 URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Hvis du har en godkendende proxy, kan du starte med at teste undtagelser for følgende:
  
- Portene 80 og 443
    
- TCP og HTTP'er
    
- Forbindelser, der er udgående til en af disse URL-adresser:
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Alle brugere skal have tilladelse til at nå disse adresser uden proxyforstyrrelser eller -godkendelse. På et mindre netværk skal du tilføje disse til din proxy-bypassliste i din webbrowser. 
  
Hvis du vil føje disse til din proxytilslutningsliste i Internet Explorer, skal **du gå** \> til Værktøjer **, Internetindstillinger** \> **Connections** \> **LAN settings Advanced**\>. Fanen Avanceret er også der, hvor du finder din proxyserver og proxyserverport. Du skal muligvis klikke på afkrydsningsfeltet Brug **en proxyserver til LAN for at** få adgang til **knappen Avanceret** . Du skal sørge for, at Tilsidesætte **proxyserver for lokale adresser** er markeret. Når du klikker **på** Avanceret, får du vist et tekstfelt, hvor du kan angive undtagelser. Adskil URL-adresserne med jokertegn, der er angivet ovenfor, med semikolon, f.eks.:
  
\*.microsoftonline.com; \*.sharepoint.com
  
Når du tilsidesætter din proxy, skal du kunne bruge ping eller PsPing direkte på en Office 365 URL-adresse. Det næste trin er at teste ping **outlook.office365.com**. Eller, hvis du bruger PsPing eller et andet værktøj, der gør det muligt at angive et portnummer til kommandoen, PsPing mod **portal.microsoftonline.com:443** for at se den gennemsnitlige tiden på returkørslen i millisekunder. 
  
Tiden på returkørslen, eller RTT, er en talværdi, der måler, hvor lang tid det tager at sende en HTTP-anmodning til en server som outlook.office365.com og få svar tilbage, der anerkender, at serveren ved, at det lykkedes. Du får nogle gange vist denne forkortet som RTT. Dette bør tage relativ kort tid.
  
Du skal bruge [PSPing eller](/sysinternals/downloads/psping) et andet værktøj, der ikke bruger ICMP-pakker, der er blokeret af Office 365 for at udføre denne test. 
  
 **Sådan bruger du PsPing til at få en samlet rundturstid i millisekunder direkte fra Office 365 URL-adresse**
  
1. Kør en kommandoprompt med administrator administrator ved at udføre disse trin:
    
1. Klik **på Start**.
    
2. Skriv cmd **i feltet Start** søgning, og tryk derefter på Ctrl+Skift+Enter.
    
3. Hvis dialogboksen **Kontrol af brugerkonti** vises, skal du bekræfte, at den handling, der vises, er den, du ønsker, og derefter klikke på **Fortsæt**.
    
2. Gå til den mappe, hvor værktøjet (i dette tilfælde PsPing) er installeret, og test disse Office 365 URL-adresser:
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![PSPing-kommandoen, der microsoft-my.sharepoint.com port 443.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Sørg for at medtage portnummeret på 443. Husk, Office 365 fungerer på en krypteret kanal. Hvis du psPing uden portnummeret, vil din anmodning mislykkes. Når du har pinget din korte liste, skal du se efter den gennemsnitlige tid i millisekunder (ms). Det er det, du vil optage!
  
![Grafik, der viser en illustration af klienten til PSPing-proxy med tiden for en returkørslen på 2,8 millisekunder.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Hvis du ikke kender til proxy bypass, og foretrækker at tage tingene trin for trin, skal du først finde ud af navnet på din proxyserver. I Internet Explorer skal du gå til **Værktøjer Internetindstillinger** \> **Connections** \>  \> **LAN settings Advanced**\>. Fanen **Avanceret** er det sted, hvor din proxyserver vises. Ping proxyserveren ved en kommandoprompt ved at udføre denne opgave: 
  
 **Sådan pinger du proxyserveren og får en returrejseværdi i millisekunder for trin 1 til 2**
  
1. Kør en kommandoprompt med administrator administrator ved at udføre disse trin:
    
1. Klik **på Start**.
    
2. Skriv cmd **i feltet Start** søgning, og tryk derefter på Ctrl+Skift+Enter.
    
3. Hvis dialogboksen **Kontrol af brugerkonti** vises, skal du bekræfte, at den handling, der vises, er den, du ønsker, og derefter klikke på **Fortsæt**.
    
2. Skriv ping, \<the name of the proxy server your browser uses, or the IP address of the proxy server\> og tryk derefter på Enter. Hvis du har PsPing eller et andet værktøj installeret, kan du vælge at bruge dette værktøj i stedet. 
    
    Din kommando kan se ud som i nogle af disse eksempler: 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Når sporingen stopper med at sende testpakker, får du en lille oversigt, der viser et gennemsnit, i millisekunder, og det er den værdi, du leder efter. Tag et skærmbillede af prompten, og gem den ved hjælp af din navngivningskonvention. På dette tidspunkt kan det også være en hjælp at udfylde diagrammet med værdien.
    
Det kan være, at du har lavet en sporing tidligt om morgen, og din klient kan komme hurtigt til proxyen (eller hvilken som helst udgangsserver der afsluttes til internettet). I dette tilfælde kan dine tal se sådan ud:
  
![Grafik, der viser tiden for en returkørslen fra en klient til en proxy på 2,8 millisekunder.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Hvis din klientcomputer er en af de få udvalgte med adgang til proxyserveren (eller udgangsserveren), kan du køre næste etape af testen ved at oprette fjernforbindelse til den pågældende computer, der kører kommandoprompten til PsPing til en URL-adresse til Office 365 derfra. Hvis du ikke har adgang til computeren, kan du kontakte dine netværksressourcer for at få hjælp til næste etape og få nøjagtige tal på den måde. Hvis det ikke er muligt, kan du tage en PsPing mod den pågældende Office 365-URL-adresse og sammenligne den med PsPing eller pinge tid mod din proxyserver. 
  
Hvis du f.eks. har 51,84 millisekunder fra klienten til URL-adressen til Office 365, og du har 2,8 millisekunder fra klienten til proxy (eller udgangspunkt), har du 49,04 millisekunder fra udgangspunktet til Office 365. Hvis du har en PsPing på 12,25 millisekunder fra klienten til proxyen i løbet af dagens højde, og 62,01 millisekunder fra klienten til URL-adressen til Office 365, så er din gennemsnitlige værdi for proxy udgangspunktet til Office 365 URL-adressen 49,76 millisekunder.
  
![Yderligere grafik, der viser ping i millisekunder fra klient til proxy ud for klienten Office 365 så værdierne kan trækkes fra.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Med hensyn til fejlfinding kan det være, at du finder noget interessant ved blot at beholde disse oprindelige planer. Hvis du f.eks. synes, at du generelt har ca. 40 millisekunder til 59 millisekunder ventetid fra proxyen eller udgangspunktet, peger på Office 365 URL-adressen, og have en klient til at proxy- eller udgangspunktventetid på ca. 3 millisekunder til 7 millisekunder (afhængigt af mængden af netværkstrafik, du ser på det pågældende tidspunkt på dagen), så vil du helt sikkert vide, at noget er problematisk, hvis din sidste tre klient til proxy- eller udgangspunkt viser grundlinjer en ventetid på 45 millisekunder.
  
### <a name="advanced-methods"></a>Avancerede metoder

Hvis du gerne vil vide, hvad der sker med dine internetanmodninger om Office 365, skal du lære netværkssporing at kende. Det er ligegyldigt, hvilke værktøjer du foretrækker til disse sporinger, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, Developer Dashboard tool or any other, vil gøre, så længe dette værktøj kan registrere og filtrere netværkstrafik. I dette afsnit kan du se, at det kan være nyttigt at køre mere end ét af disse værktøjer for at få et mere komplet billede af problemet. Når du tester, fungerer nogle af disse værktøjer også som proxy'er i sig selv. Værktøjerne, der bruges i ledsagerartikel, [Plan for ydeevnefejlfinding for Office 365](performance-troubleshooting-plan.md), omfatter [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) eller [WireShark](https://www.wireshark.org/).
  
At have en grundlinje over ydeevnen er den enkle del af denne metode, og mange af trinnene er de samme, som når du foretager fejlfinding af ydelsesproblemet. De mere avancerede metoder til oprettelse af oprindelige planer for ydeevnen kræver, at du tager og gemmer netværkssporinger. De fleste af eksemplerne i denne artikel bruger SharePoint Online, men du bør udarbejde en liste over almindelige handlinger på tværs af de Office 365-tjenester, du abonnerer på, for at teste og registrere. Her er et eksempel på en grundlinje:
  
- Liste over grundlinje for SPO – ** Trin 1: ** Gå til startsiden for SPO-webstedet, og en netværkssporing. Gem sporingen. 
    
- Liste over grundlinje for SPO – Trin **2:** Søg efter et ord (f.eks. virksomhedens navn) via Enterprise Search, og foretag en netværkssporing. Gem sporingen. 
    
- Liste over grundlinje for SPO – Trin **3:** Upload en stor fil til et SharePoint Online-dokumentbibliotek, og lave en netværkssporing. Gem sporingen. 
    
- Liste over grundlinje for SPO – **Trin 4:** Gå til startsiden for OneDrive og lave en netværkssporing. Gem sporingen. 
    
Denne liste bør indeholde de vigtigste almindelige handlinger, som brugerne kan udføre mod SharePoint Online. Bemærk, at det sidste trin, for sporing, der går til OneDrive for Business, bygger på en sammenligning mellem den belastning af SharePoint Online-startsiden (som ofte tilpasses af virksomheder) og OneDrive for Business-startsiden, som sjældent bliver tilpasset. Dette er en grundlæggende test, når det kommer til en langsom indlæsning SharePoint Online-websted. Du kan oprette en post til denne forskel i din test.
  
Hvis du er midt i et ydelsesproblem, er mange af trinnene de samme, som når du laver en grundlinje. Netværkssporing bliver vigtigt, så vi kan tage os af  *, hvordan*  du skal tage de næste vigtige sporinger. 
  
For at løse et  *ydelsesproblem* skal du lige nu spore det tidspunkt, hvor du oplever ydelsesproblemet. Du skal have de rette værktøjer tilgængelige til at indsamle logfiler, og du skal bruge en handlingsplan, det vil sige en liste over fejlfindingshandlinger, der skal foretages for at indsamle de bedste oplysninger, som du kan. Det første, du skal gøre, er at registrere dato og klokkeslæt for testen, så filerne kan gemmes i en mappe, der afspejler timingen. Derefter skal du indsnævre problemet til sig selv. Dette er de nøjagtige trin, du skal bruge til test. Glem ikke de grundlæggende funktioner: Hvis problemet kun skyldes Outlook, skal du sørge for at registrere, at problemfunktionsmåden kun forekommer i én Office 365 tjeneste. Hvis du indskrænker omfanget af problemet, kan det hjælpe dig med at fokusere på noget, du kan løse. 
  
## <a name="see-also"></a>Se også

[Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)