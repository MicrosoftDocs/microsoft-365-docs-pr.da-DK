---
title: Fejlfinding af ydeevne i forbindelse med planen for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
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
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: Denne artikel kan hjælpe dig med at Office 365 problemer med ydeevnen og endda løse nogle af de mest almindelige problemer.
ms.openlocfilehash: 23779158c250a94873f44139faa783e0079ab642
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601589"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Fejlfinding af ydeevne i forbindelse med planen for Office 365

Har du brug for at kende trinnene til at identificere og løse forsinkelser, problemer med, at programmet hænger, og langsom ydeevne mellem SharePoint Online, OneDrive for Business, Exchange Online eller Skype for Business Online og klientcomputeren? Før du ringer til supporten, kan denne artikel hjælpe dig med Office 365 problemer med ydeevnen og endda løse nogle af de mest almindelige problemer.

Denne artikel er faktisk en handlingsplan, som du kan bruge til at registrere værdifulde data om ydelsesproblemet, mens det sker. Nogle af de vigtigste problemer er også medtaget i denne artikel.

Hvis du er ny bruger af netværksydeevne og ønsker at udarbejde en langsigtet plan til overvågning af ydeevnen mellem dine klientcomputere og Office 365, kan du se nærmere på justering af ydeevnen og fejlfinding Office 365 Administration og [it-Pro](performance-tuning-using-baselines-and-history.md).

## <a name="sample-performance-troubleshooting-action-plan"></a>Eksempel på handlingsplan til fejlfinding af ydeevne

Denne handlingsplan består af to dele: en forberedelsesfase og en logføringsfase. Hvis du har et ydelsesproblem lige nu, og du skal udføre dataindsamling, kan du begynde at bruge denne plan med det samme.

### <a name="prepare-the-client-computer"></a>Forbered klientcomputeren

- Find en klientcomputer, der kan genskabe ydelsesproblemet. Denne computer skal bruges i løbet af fejlfindingsforløbet.
- Skriv de trin ned, der får ydelsesproblemet til at opstå, så du er klar, når det bliver tid til at teste.
- Installér værktøjer til indsamling og registrering af oplysninger:
  - [Installér Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865) (eller brug et tilsvarende værktøj til netværkssporing).
  - Installér den gratis Basic Edition af [HTTPWatch](https://www.httpwatch.com/download/) (eller brug et tilsvarende værktøj til netværkssporing).
  - Brug en skærmoptager, eller kør Trinoptager (PSR.exe), der følger med Windows Vista og nyere, for at holde styr på de trin, du tager under testen.

### <a name="log-the-performance-issue"></a>Logfør ydelsesproblemet

- Luk alle overflødige internetbrowsere.
- Start Trinoptager eller en anden skærmoptager.
- Start din Netmon-registrering (eller værktøjet til netværkssporing).
- Ryd din DNS-cache på klientcomputeren fra kommandolinjen ved at skrive ipconfig /flushdns.
- Start en ny browsersession, og slå HTTPWatch til.
- Valgfrit: Hvis du tester Exchange Online, skal du køre Exchange Client Performance Analyzer fra Office 365 administrationskonsollen.
- Genskab de nøjagtige trin, der forårsager ydelsesproblemet.
- Stop din Netmon eller et andet værktøjs sporing.
- På kommandolinjen skal du køre en sporingsrute til dit Office 365 ved at skrive følgende kommando og derefter trykke på Enter:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Stop Trinoptager, og gem videoen. Sørg for at medtage datoen og klokkeslættene for det hentede, og om den udviser god eller dårlig ydeevne.
- Gem sporingsfilerne. Igen skal du sørge for at medtage datoen og klokkeslættene for det hentede, og om den udviser god eller dårlig ydeevne.

Hvis du ikke ved, hvordan du kører de værktøjer, der er nævnt i denne artikel, skal du ikke bekymre dig, da vi giver dig disse trin som det næste. Hvis du er vant til at udføre denne type netværksoptagelse, kan du gå til Sådan indsamler du oprindelige [planer, som](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines) beskriver filtrering og aflæsning af logfilerne.

### <a name="flush-the-dns-cache-first"></a>Ryd DNS-cachen først

Hvorfor? Ved at rense DNS-cachen kan du starte din test med en ren tavle. Ved at rydde cachen nulstiller du indholdet i DNS Resolver til de mest opdaterede poster. Husk, at flush ikke fjerner HOSTs-filposterne. Hvis du i stor grad bruger HOST-filposter, skal du kopiere disse poster ud til en fil i en anden mappe og derefter tømme HOST-filen.

#### <a name="flush-your-dns-resolver-cache"></a>Ryd din DNS Resolver-cache

1. Åbn kommandoprompten( enten **Start** \> **Kør** \> **cmd eller** **Windows-tast** \> **cmd**).
2. Skriv følgende kommando, og tryk på Enter:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsofts netværksovervågningsværktøj ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analyserer pakker, dvs. trafik, der passerer mellem computere på netværk. Ved at bruge Netmon til at spore trafik med Office 365 kan du registrere, få vist og læse pakkehoveder, identificere mellemliggende enheder, kontrollere vigtige indstillinger på netværkshardware, lede efter tabte pakker og følge strømmen af trafik mellem computere på virksomhedens netværk og Office 365. Da den faktiske brødtekst for trafik er krypteret, dvs. den (rejser på port 443 via SSL/TLS), kan du ikke læse de filer, der sendes. I stedet får du en ufiltreret sporing af stien, som pakken tager, som kan hjælpe dig med at finde problemets funktionsmåde.

Sørg for, at du ikke anvender et filter på nuværende tidspunkt. I stedet skal du køre gennem trinnene og demonstrere problemet, før du stopper sporingen og gemmer.

Når du har installeret Netmon 3.4, skal du åbne værktøjet og følge disse trin:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Lav en Netmon-sporing, og genskab problemet

1. Start Netmon 3.4.
Der er tre ruder på siden **Start** : **Recent Captures**, **Select Networks** og **Getting Started with Microsoft Network Monitor 3.4. Varsel**. Panelet Select Networks giver dig også en liste over de standardnetværk, hvorfra du kan registrere. Sørg for, at netværkskortene er markeret her.

2. Klik **på New Capture** øverst på **startsiden** . Dette tilføjer en ny fane ud for **siden Start** kaldet **Capture 1**.
![Netmons brugergrænseflade med knapperne New Capture, Start og Stop fremhævet.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Klik på Start på værktøjslinjen for at **tage** et enkelt skærmbillede.

4. Genskab de trin, der udgør ydelsesproblemet.

5. Klik **på Stop** \> **gem** \> **fil som**. Husk at angive dato og klokkeslæt med tidszonen og at nævne, hvis den udviser dårlig eller god ydeevne.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch fås](https://www.httpwatch.com/download/) i en opladet og en gratis udgave. Den gratis Basic Edition dækker alt, hvad du skal bruge til denne test. HTTPWatch overvåger netværkstrafik og sideindlæsningstiden direkte fra dit browservindue. HTTPWatch er et plug-in til Internet Explorer, der grafisk beskriver ydeevnen. Analysen kan gemmes og vises i HTTPWatch Studio.

> [!NOTE]
> Hvis du bruger en anden browser, f.eks. Firefox, Google Chrome, eller hvis du ikke kan installere HTTPWatch i Internet Explorer, skal du åbne et nyt browservindue og trykke på F12 på tastaturet. Du bør få vist udviklerværktøjet nederst i din browser. Hvis du bruger Opera, skal du trykke på Ctrl+Skift+I for Web Inspector og  derefter klikke på fanen Netværk og fuldføre testen, som er beskrevet nedenfor. Oplysningerne vil være en smule anderledes, men indlæsningstider vises stadig i millisekunder. > HTTPWatch er også nyttig til problemer med sideindlæsningstider SharePoint Online.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>Kør HTTPWatch, og genskab problemet

HTTPWatch er en browser-plug-in, så det at bruge værktøjet i browseren er en smule anderledes for hver version af Internet Explorer. Du kan typisk finde HTTPWatch under kommandolinjen i Internet Explorer-browseren. Hvis du ikke kan se HTTPWatch-plug-in'en i browservinduet, kan du kontrollere versionen af din browser  \> ved at klikke på Hjælp om eller i nyere versioner af Internet Explorer, klikke på tandhjulssymbolet og **Om Internet Explorer**. Du starter **kommandolinjen ved** at højreklikke på menulinjen i Internet Explorer og klikke **på Kommandolinje**.

Tidligere er HTTPWatch blevet knyttet til både kommandolinjen og Stifinder, så når du installerer, hvis du ikke umiddelbart kan se ikonet (selv efter genstart), skal du se under Funktioner og dine værktøjslinjer for at finde ikonet. Husk, at værktøjslinjer kan tilpasses, og at indstillingerne kan føjes til dem.

![Internet Explorers kommandoværktøjslinje med HTTPWatch-ikonet vist.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Start HTTPWatch i et Internet Explorer-browservindue. Den vises forankret i browseren nederst i vinduet. Klik **på Optag**.

2. Genskab de nøjagtige trin, der er involveret i problemet med ydeevnen. Klik på **knappen Stop** i HTTPWatch.

3. **Gem** HTTPWatch eller **Send via mail**. Husk at navngive filen, så den indeholder oplysninger om dato og klokkeslæt samt en angivelse af, om din Watch indeholder en demonstration af god eller dårlig ydeevne.

![HTTPWatch, der viser fanen Netværk for en sideindlæsning af Office 365 startsiden.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Dette skærmbillede er fra versionen Professional af HTTPWatch. Du kan åbne sporinger, der er taget i Basic Version på en computer med en Professional-version, og læse den der. Ekstra oplysninger kan være tilgængelige via sporingen gennem den pågældende metode.

## <a name="problem-steps-recorder"></a>Optager til problemtrin

Trinoptager, eller PSR.exe, gør det muligt at registrere problemer, efterhånden som de forekommer. Det er et meget nyttigt værktøj og meget nemt at køre.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Kør Optager til problemtrin (PSR.exe) for at optage dit arbejde

1. Brug enten **Start** \> **Kør-type** \> **PSR.exe** \> **OK**, eller klik på **tasten Windows,** \> **PSR.exe** \> tryk derefter på Enter.

2. Når den lille PSR.exe, skal du klikke på **Start optagelse** og genskabe trinnene, der genskaber ydelsesproblemet. Du kan tilføje kommentarer efter behov ved at klikke på **Tilføj kommentarer**.

3. Klik **på Stop optagelse** , når du har fuldført trinnene. Hvis ydelsesproblemet er en sidegengiven, skal du vente på, at siden gengives, før du stopper optagelsen.

4. Klik på **Gem**.

![Et skærmbillede af Trinoptager eller PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Datoen og klokkeslættet registreres for dig. Dette linker din PSR til dit Netmon-spor og HTTPWatch i tide og hjælper med præcisionsfejlfinding. Datoen og klokkeslættet i PSR-posten kan vise, at der er gået et minut mellem logon og søgning på URL-adressen og den delvise gengivelse af administratorwebstedet, f.eks.

## <a name="read-your-traces"></a>Læs dine sporinger

Det er ikke muligt at lære alt om fejlfinding af netværk og ydeevne, som du kan have brug for at vide, via en artikel. En god ydeevne kræver erfaring og viden om, hvordan netværket fungerer og fungerer. Men det er muligt at finde en liste over de vigtigste problemer og vise, hvordan værktøjer kan gøre det nemmere for dig at fjerne de mest almindelige problemer.

Hvis du vil lære færdigheder at læse netværkssporinger for dine Office 365-websteder, er der ingen bedre lærer end at oprette sporinger af sideindlæsninger regelmæssigt og få en bedre oplevelse med at læse dem. Når du f.eks. har en chance, kan du indlæse Office 365 tjeneste og spore processen. Filtrer sporingen for DNS-trafik, eller søg efter navnet på den tjeneste, du har gennemset, i FrameData. Scan sporingen for at få en ide om de trin, der udføres, når tjenesten indlæses. På den måde lærer du, hvordan normal sideindlæsning skal se ud, og i forbindelse med fejlfinding, især i forhold til ydeevne, kan du lære meget at sammenligne gode og dårlige sporinger.

Netmon bruger Microsoft IntelliSense i filterfeltet Display. IntelliSense, eller intelligent kodeudførelse, er det trick, hvor du skriver i en periode, og alle tilgængelige indstillinger vises i en rullelisten. Hvis du f.eks. er bekymret for skaleringen af TCP-vinduet, kan du finde vej til et filter (  `.protocol.tcp.window < 100`f.eks. ) på den måde.

![Skærmbillede af Netmon, der viser, at feltet Vis filter bruger IntelliSense.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Netmon-sporinger kan have en masse trafik i dem. Hvis du ikke er erfaren med at læse dem, kan du blive overvældet, første gang du åbner sporingen. Det første, du skal gøre, er at adskille signalet fra baggrundsstøj i sporingen. Du har testet Office 365, og det er den trafik, du vil have vist. Hvis du er vant til at navigere gennem sporinger, behøver du muligvis ikke denne liste.

Trafikken mellem din klient og Office 365 rejser via TLS, hvilket betyder, at brødteksten i trafik krypteres og ikke kan læses i en generisk Netmon-sporing. Din ydeevneanalyse behøver ikke at kende de specifikke oplysninger i pakken. Den er dog meget interesseret i pakkehovederne og de oplysninger, de indeholder.

### <a name="tips-to-get-a-good-trace"></a>Tips at få et godt spor

- Kend værdien af IPv4- eller IPv6-adressen på klientcomputeren. Du kan få denne fra kommandoprompten ved at skrive **IPConfig og** derefter trykke på Enter. Hvis du kender denne adresse, kan du hurtigt se, om trafikken i sporet direkte involverer klientcomputeren. Hvis der er en kendt proxy, kan du pinge den og få dens IP-adresse.

- Ryd din DNS Resolver-cache, og luk om muligt alle browsere undtagen den browser, hvor du kører dine test. Hvis du ikke kan gøre dette, hvis f.eks. support bruger et browserbaseret værktøj til at se klientcomputerens skrivebord, skal du være klar til at filtrere dit spor.

- I en travl sporing skal du finde Office 365 tjeneste, du bruger. Hvis du aldrig eller sjældent har set din trafik før, er dette et nyttigt trin til at adskille ydelsesproblemet fra anden netværksstøj. Det kan du gøre på flere måder. Direkte før testen kan du bruge _ping eller_ _PsPing mod_ URL-adressen for den specifikke tjeneste (`ping outlook.office365.com` eller `psping -4 microsoft-my.sharepoint.com:443`, for eksempel). Du kan også nemt finde den ping eller PsPing i en Netmon-sporing (ved dens procesnavn). Så er der et sted, du kan begynde at lede.

Hvis du kun bruger Netmon-sporing på tidspunktet for problemet, er det også i orden. Du kan orientere dig ved at bruge et filter som f.eks `ContainsBin(FrameData, ASCII, "office")` . eller `ContainsBin(FrameData, ASCII, "outlook")`. Du kan optage dit rammenummer fra sporingsfilen. Du kan også rulle ruden _Oversigt over_ ramme helt til højre og kigge efter kolonnen Samtale-id. Der er angivet et tal for id'et for denne specifikke samtale, som du også kan optage og se isoleret senere. Husk at fjerne dette filter, før du anvender en anden filtrering.

> [!TIP]
> Netmon indeholder mange praktiske indbyggede filtre. Prøv **knappen Indlæs** filter øverst i _filterruden_ Vis.

![Find din IP ved hjælp af PSPing på kommandolinjen på klientcomputeren.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![Netmon-sporing fra den klient, der viser den samme PSPing-kommando gennem filteret TCP. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Bliv fortrolig med din trafik, og lær at finde de oplysninger, du skal bruge. For example, learn to determine which packet in the trace has the first reference to the Office 365 service you're using (like "Outlook").

Hvis Office 365 Outlook Online som eksempel, begynder trafikken noget i denne måde:

- DNS Standard Query og DNS-svar til outlook.office365.com med matchende forespørgsels-oplysninger. Det er vigtigt at være opmærksom på tidsforskydningen for denne turn-around, samt hvor i verden Office 365 Global DNS sender anmodningen om navneopløsning. Ideelt set så lokalt som muligt, i stedet for halvvejs i den anden ende af verden.

- En HTTP GET-anmodning, hvis statusrapport flyttes permanent (301)

- RWS-trafik herunder RWS Forbind anmodninger og Forbind svar. (Dette er Remote Winsock, der laver forbindelse for dig).

- En TCP SYN- og TCP SYN/ACK-samtale. Mange af indstillingerne i denne samtale påvirker ydeevnen.

- Derefter en række TLS:TLS-trafik, som er det sted, hvor samtaler med TLS handshake og TLS-certifikat foregår. Husk, at dataene er krypteret via SSL/TLS.

Alle dele af trafikken er vigtige og forbundne, men små dele af sporet indeholder oplysninger, der er særligt vigtige med hensyn til fejlfinding af ydeevnen, så vi fokuserer på disse områder. Eftersom vi har udført tilstrækkelig fejlfinding af ydeevnen for Office 365 hos Microsoft til at samle en top ti-liste over almindelige problemer, vil vi fokusere på disse problemer, og hvordan du bruger værktøjerne, ved at udrode dem som det næste.

Hvis du ikke har installeret dem alle klar, gør matrixen herunder brug af flere værktøjer. Hvor det er muligt. Der findes links til installationspunkterne. Listen indeholder almindelige værktøjer til netværkssporing, f.eks [. Netmon](https://www.microsoft.com/download/details.aspx?id=4865) og [Wireshark](https://www.wireshark.org/), men brug et hvilket som helst sporingsværktøj, du er fortrolig med, og hvor du er vant til at filtrere netværkstrafik. Når du tester, skal du huske:

- *Luk dine browsere, og test kun med én browser, der kører*  – Dette vil reducere den samlede trafik, du registrerer. Det giver en mindre travl sporing.
- *Rens din DNS Resolver-cache*  på klientcomputeren – Dette giver dig en ren tavle, når du begynder at tage din optagelse, hvilket giver en renere sporing.

## <a name="common-issues"></a>Almindelige problemer

Nogle almindelige problemer, du kan opleve, og hvordan du finder dem i din netværkssporing.

### <a name="tcp-windows-scaling"></a>TCP Windows skalering

Findes i SYN - SYN/ACK. Ældre eller ældre hardware udnytter muligvis ikke TCP Windows-skalering.  Uden korrekte indstillinger for TCP Windows-skalering udfyldes standard 16-bit bufferen i TCP headere i millisekunder.  Trafik kan ikke fortsætte med at sende, før klienten modtager en bekræftelse, som de oprindelige data er blevet modtaget, hvilket medfører forsinkelser.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Se efter SYN - SYN/ACK-trafik i din netværkssporing.  I Netmon skal du bruge et filter som .`tcp.flags.syn == 1` Dette filter er det samme som i Wireshark.

![Filtrer i Netmon eller Wireshark for Syn-pakker til begge værktøjer: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Bemærk, at for hver SYN findes der en kildeport (SrcPort), der er matchet i destinationsporten (DstPort) for den relaterede Bekræftelse (SYN/ACK).

For at se Windows skaleringsværdi, der bruges af din netværksforbindelse, skal du først udvide SYN og derefter den relaterede SYN/ACK.

![Grafik, der viser, hvordan du matcher SrcPort til DstPort i en sporing for at få deltatidspunkt.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>TCP Idle Time Indstillinger

Historisk set er de fleste perimeternetværk konfigureret til midlertidige forbindelser, hvilket vil sige, at inaktive forbindelser generelt afsluttes. Inaktive TCP-sessioner kan afsluttes af proxyer og firewalls på mere end 100 til 300 sekunder. Dette er problematisk for Outlook Online, fordi den opretter og bruger langsigtede forbindelser, uanset om de er ledige eller ej.

Når forbindelser afbrydes af proxy- eller firewallenheder, informeres klienten ikke, og et forsøg på at bruge Outlook Online betyder, at en klientcomputer forsøger at genskabe forbindelsen gentagne gange, før du foretager en ny. Du får muligvis vist hængere i produktet, prompts eller langsom ydeevne ved indlæsning af siden.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

I Netmon skal du kigge på feltet Time Offset for en returrejse. En returrejse er tiden mellem klienten, der sender en anmodning til serveren og modtager et svar tilbage. Kontrollér mellem klienten og udgangspunktet (f.eks. Klient –\> proxy) eller klient til Office 365 (klient –\> Office 365). Du kan se dette i mange typer pakker.

Som et eksempel kan filteret i Netmon se ud som  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, eller i Wireshark,  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.

> [!TIP]
> Ved du ikke, om IP-adressen i dit spor tilhører din DNS-server? Prøv at søge på kommandolinjen. Klik **på Start** \> **Kør**\>, og **skriv cmd**, eller **tryk Windows-tast**\>, og skriv **cmd**. Når du bliver bedt om det, skal du skrive  `nslookup <the IP address from the network trace>`. For at teste skal du bruge nslookup mod din egen computers IP-adresse. > Se URL-adresser og IP-adresseintervaller for at få vist [en liste Office 365 over Microsofts IP-områder](./urls-and-ip-address-ranges.md).

Hvis der er et problem, kan du forvente, at der vises lange tidsforskydninger i dette tilfælde (Outlook Online), især i TLS:TLS-pakker, der viser passagen af programdata (f.eks. kan du i Netmon finde programdatapakker via `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). Du bør få vist et jævn forløb i tiden på tværs af sessionen. Hvis der vises lange forsinkelser, når du opdaterer din Outlook Online, kan det skyldes, at der sendes en høj grad af nulstillinger.

### <a name="latencyround-trip-time"></a>Ventetid/Returrejsetid

Ventetid er en måling, der kan ændre meget afhængigt af mange variabler, f.eks. opgradering af ældre enheder, tilføjelse af et stort antal brugere til et netværk og procentdelen af den samlede båndbredde, der forbruges af andre opgaver på en netværksforbindelse.

Der er båndbreddeberegnere til Office 365 tilgængelige fra denne netværksplanlægning [og justering af ydeevnen for Office 365](network-planning-and-performance.md) side.

Har du brug for at måle hastigheden på din forbindelse eller din internetudbyders båndbreddeforbindelse? Prøv dette websted (eller lignende websteder): [Speedtest Official Site](https://www.speedtest.net/), eller forespørg din foretrukne søgemaskine efter udtrykket **speed test**.

#### <a name="tools"></a>Værktøjer

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Hvis du vil registrere ventetid i en sporing, kan du drage fordel af at have registreret klientcomputerens IP-adresse og IP-adressen på DNS-serveren Office 365. Dette er med henblik på nemmere filtrering af sporinger. Hvis du opretter forbindelse via en proxy, skal du bruge din klientcomputers IP-adresse, IP-adressen på proxyen/udgangspunktet og IP-adressen Office 365 DNS for at gøre arbejdet nemmere.

En ping-anmodning, der sendes til outlook.office365.com, fortæller dig navnet på det datacenter, der modtager anmodningen, også  *selvom ping muligvis*  ikke kan oprette forbindelse til fortløbende ICMP-pakker. Hvis du bruger PsPing (et gratis værktøj til download), og specifikke port (443) og måske til at bruge IPv4 (-4), får du en gennemsnitlig returtid for pakker, der sendes. Dette fungerer for andre URL-adresser i Office 365 tjenester som f.eks`psping -4 yourSite.sharepoint.com:443`. . Faktisk kan du angive et antal pings for at få en større prøve til dit gennemsnit ved at prøve noget i f.eks `psping -4 -n 20 yourSite-my.sharepoint.com:443`. .

> [!NOTE]
> PsPing sender ikke ICMP-pakker. Det pinger med TCP-pakker over en bestemt port, så du kan bruge en hvilken som helst, du ved er åben. I Office 365, der bruger SSL/TLS, kan du prøve at tilknytte port :443 til din PsPing.

![Skærmbillede, der viser en ping, der løser outlook.office365.com, og en PSPing med 443, der gør det samme, men som også rapporterer en gennemsnitlig RTT på 6,5 ms.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Hvis du har indlæst den langsomme indsætning af Office 365, mens du udfører en netværkssporing, skal du filtrere et Netmon- eller Wireshark-spor for `DNS`. Dette er en af de IP'er, vi leder efter.

Her er de trin, du skal følge for at filtrere din Netmon for at få IP-adressen (og se nærmere på DNS-ventetid). I dette eksempel outlook.office365.com, men kan også bruge URL-adressen for en SharePoint Online-lejer (hithere.sharepoint.com for eksempel).

1. Ping URL-adressen `ping outlook.office365.com` , og registrer navn og IP-adresse på den DNS-server, som ping-anmodningen blev sendt til.
2. Netværkssporing åbner siden eller udfører den handling, der giver dig ydelsesproblemet, eller hvis du ser en lang ventetid på selve pingen, kan du netværksspore den.
3. Åbn sporingen i Netmon, og filtrer efter DNS (dette filter fungerer også i Wireshark, men der er følsomme oplysninger om store og små bogstaver `-- dns`). Da du kender navnet på DNS-serveren fra din ping, kan du også filtrere hurtigere i Netmon som her: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`, hvilket ser sådan ud i Wireshark dns and frame contains "namnorthwest".<br/>Åbn svarpakken, og klik på **DNS** i vinduet Netmon **Frame Details** for at udvide for at få flere oplysninger. I DNS-oplysningerne finder du IP-adressen på den DNS-server, anmodningen kom til Office 365. Du skal bruge denne IP-adresse i næste trin (PsPing-værktøjet). Fjern filteret, højreklik på DNS-svaret i Netmon (**Frame Summary** \> **Find Conversations** \> **DNS**) for at se DNS-forespørgslen og svaret side om side.
4. I Netmon skal du også bemærke kolonnen Time Offset mellem DNS-anmodningen og svaret. I næste trin er det meget praktisk at installere og bruge [PsPing-værktøjet](/sysinternals/downloads/psping) , både fordi ICMP ofte er blokeret på firewalls, og fordi PsPing elegant registrerer ventetiden i millisekunder. PsPing gennemfører en TCP-forbindelse til en adresse og port (i vores tilfælde den åbne port 443).
5. Installer PsPing.
6. Åbn en kommandoprompt (Start \> \> Kør skriv cmd, eller Windows Tasttype \> cmd), og skift mappe til den mappe, hvor du installerede PsPing for at køre PsPing-kommandoen. I mine eksempler kan du se, at jeg har lavet en mappe "Perf" i roden af C. Du kan gøre det samme for at få hurtig adgang.
7. Skriv kommandoen, så du laver din PsPing mod IP-adressen på Office 365 DNS-serveren fra din tidligere Netmon-sporing, herunder portnummeret, f.eks`psping -n 20 132.245.24.82:445`. . Dette vil give dig en stikprøve på 20 pings og beregne gennemsnittet for ventetiden, når PsPing stopper.

Hvis du vil bruge Office 365 en proxyserver, er trinnene lidt anderledes. Du skal først PsPing på din proxyserver for at få en gennemsnitlig værdi for ventetiden i millisekunder til proxy/udgangspunkt og tilbage og derefter enten køre PsPing på proxy eller på en computer med en direkte internetforbindelse for at få den manglende værdi (den, der mangler Office 365 og tilbage).

Hvis du vælger at køre PsPing fra proxy, har du to millisekundværdier: klientcomputer til proxyserver eller udgangspunkt og proxyserver til Office 365. Og så er du færdig! I hvert fald med registrering af værdier.

Hvis du kører PsPing på en anden klientcomputer, der har en direkte forbindelse til internettet, dvs. uden en proxy, vil du have to millisekunder: klientcomputer til proxyserver eller udgangspunkt og klientcomputer til at Office 365. I dette tilfælde skal du subtrahere værdien af klientcomputeren til proxyserveren eller udgangspunktet fra værdien af klientcomputeren til Office 365, og du skal have RTT-numrene fra klientcomputeren til proxyserveren eller udgangspunktet og fra proxyserveren eller udgangspunktet pege på Office 365.

Men hvis du kan finde en klientcomputer på den på påvirkede placering, der er direkte forbundet, eller du kan tilsidesætte proxyen, kan du vælge at se, om problemet gengives der til at begynde med og derefter teste ved hjælp af det.

Ventetid, som det fremgår af en Netmon-sporing, kan disse ekstra millisekunder lægge sammen, hvis der er nok af dem i en given session.

![Generel ventetid i Netmon med Netmon standardtidsdeltakolonnen føjet til Rammeoversigt.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Din IP-adresse kan være forskellig fra de IP-adresser, der er vist her, f.eks. kan din ping returnere noget mere i stil med 157.56.0.0/16 eller et lignende interval. Du kan finde en liste over områder, Office 365 bruger, Office 365 [URL-adresser og IP-adresseintervaller](./urls-and-ip-address-ranges.md).

Husk at udvide alle noderne (der er en knap øverst til dette), hvis du vil søge efter, f.eks. 132,245.

### <a name="proxy-authentication"></a>Godkendelse af proxy

Dette gælder kun for dig, hvis du bruger en proxyserver. Hvis ikke, kan du springe disse trin over. Når proxygodkendelse fungerer korrekt, skal det foregå i millisekunder, på en ensartet måde. Du bør ikke se en periodisk dårlig ydeevne under perioder med spidsbelastninger (for eksempel).

Hvis proxygodkendelse er aktiveret, skal du gennemgå en godkendelsesproces i baggrunden, hver gang du laver en ny TCP-forbindelse til Office 365 for at få oplysninger. Så når du f.eks. skifter fra Kalender til Mail Outlook Online, skal du godkende. Og i SharePoint Online, hvis en side viser medier eller data fra flere websteder eller placeringer, skal du godkende for hver forskellig TCP-forbindelse, der er nødvendig for at gengive dataene.

I Outlook Online kan du opleve langsomme indlæsningstider, når du skifter mellem Kalender og din postkasse, eller langsomme sideindlæsninger i SharePoint Online. Der er dog andre symptomer, der ikke er vist her.

Godkendelse af proxyen er en indstilling på din udgangsproxyserver. Hvis det forårsager problemer med ydeevnen for din Office 365, skal du kontakte dit netværksteam.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Proxygodkendelse finder sted, når en ny TCP-session skal spuns op, normalt for at anmode om filer eller oplysninger fra serveren, eller for at angive oplysninger. Du kan f.eks. få vist proxygodkendelse omkring HTTP GET- eller HTTP POST-anmodninger. Hvis du vil se de rammer, hvor du godkender anmodninger i din sporing, skal du tilføje kolonnen "NTLMSSP-oversigt" til Netmon og filtrere efter  `.property.NTLMSSPSummary`. Hvis du vil se, hvor lang tid godkendelsen tager, skal du tilføje kolonnen Time Delta.

Sådan føjer du en kolonne til Netmon:

1. Højreklik på en kolonne, f.eks **. Beskrivelse**.
2. Klik **på Vælg kolonner**.
3. Find _NTLMSSP-oversigt_ og _Time Delta_ på listen, og klik på **Tilføj**.
4. Flyt de nye kolonner på plads før eller bag _kolonnen Beskrivelse_ , så du kan læse dem side om side.
5. Klik på **OK**.

Selvom du ikke tilføjer kolonnen, fungerer Netmon-filteret. Men fejlfindingen vil være meget nemmere, hvis du kan se, hvilken godkendelsesfase du er i.

Når du søger efter forekomster af proxygodkendelse, skal du sørge for at undersøge alle rammer, hvor der er en NTLM-udfordring, eller hvor en godkendelsesmeddelelse er til stede. Hvis det er nødvendigt, skal du højreklikke på den bestemte trafik og Finde samtale-TCP \> . Vær opmærksom på værdierne for Tidsdelta i disse samtaler.

![Netmon-sporing, der viser proxygodkendelse, filtreret efter samtale.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

En fire sekunders forsinkelse i godkendelse af proxyen, som det fremgår af Wireshark. Kolonnen **Time delta from previous displayed frame** blev udført ved at højreklikke på feltet med samme navn i detaljerne om billedet og vælge Tilføj som kolonne.  <br/> ![I Wireshark kan kolonnen "Time delta from previous displayed frame" oprettes ved at højreklikke på feltet med samme navn i detaljerne om billedet og vælge Tilføj som kolonne.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS-ydeevne

Navneopløsning fungerer bedst og hurtigst, når det sker så tæt på klientens land som muligt.

Hvis DNS-navneopløsningen finder sted oversøisk, kan det føje sekunder til sidebelastninger. Ideelt set sker navneopløsningen på under 100 ms. Hvis dette ikke er gjort, bør du undersøge yderligere.

> [!TIP]
> Er du i tvivl om, hvordan klientforbindelser fungerer i Office 365? Se referencedokumentet til klientforbindelser [her](/previous-versions//dn741250(v=technet.10)).

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Analyse af DNS-ydeevnen er typisk et andet job for en netværkssporing. Men PsPing er også praktisk i forbindelse med at få en mulig årsag i brug eller ej.

DNS-trafik er baseret på TCP- og UDP-anmodninger, og svar er tydeligt markeret med et id, der hjælper med at matche en bestemt anmodning med dens specifikke svar. Du får vist DNS-trafik, når f.eks. SharePoint Online bruger et netværksnavn eller en URL-adresse på en webside. Som en tommelfingerregel kører det meste af denne trafik, undtagen når du overfører zoner, over UDP.

I både Netmon og Wireshark er det mest grundlæggende filter, der giver dig mulighed for at se DNS-trafik, ganske enkelt `dns`. Sørg for at bruge små bogstaver, når du angiver filteret. Husk at rydde din DNS Resolver-cache, før du begynder at genskabe problemet på klientcomputeren. Hvis du f.eks. har en langsom indlæsning af SharePoint Online-siden for startsiden, skal du lukke alle browsere, åbne en ny browser, starte sporing, rydde din DNS Resolver-cache og gå til dit SharePoint Online-websted. Når hele siden er løst, skal du stoppe og gemme sporingen.

![Et grundlæggende filter for DNS i Netmon er DNS.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Du vil se på tidspunktet for forskydning her. Og det kan være nyttigt at tilføje kolonnen **Time Delta** til Netmon, hvilket du kan gøre ved at udføre disse trin:

1. Højreklik på en kolonne, f.eks **. Beskrivelse**.
2. Klik **på Vælg kolonner**.
3. Find _Time Delta på_ listen, og klik på **Tilføj**.
4. Flyt den nye kolonne på plads før eller bag _kolonnen Beskrivelse_ , så du kan læse dem side om side.
5. Klik på **OK**.

Hvis du finder en interessant forespørgsel, kan du overveje at isolere den ved at højreklikke på den pågældende forespørgsel i panelet med rammedetaljer og vælge **Find Conversations** \> **DNS**. Bemærk, at panelet Netværkssamtaler springer direkte til den specifikke samtale i sin log over UDP-trafik.

![En Netmon-sporing af Outlook Online-indlæsning, der er filtreret efter DNS, og brug af Find samtaler og derefter DNS til at indskrænke resultaterne.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

I Wireshark kan du oprette en kolonne til DNS-tid. Tag dit spor (eller åbn en sporing) i Wireshark, og filtrer efter `dns`, eller, mere nyttigt,  `dns.time`. Klik på en DNS-forespørgsel, og udvid detaljerne i panelet, der viser  `Domain Name System (response)` detaljer. Der vises et felt for tid (f.eks. `[Time: 0.001111100 seconds]`. Højreklik denne gang, og vælg **Anvend som kolonne**. Dette giver dig en **Time-kolonne** til hurtigere sortering af din sporing. Klik på den nye kolonne for at sortere efter faldende værdier for at se, hvilke DNS-opkald der tog længst tid at løse.

[En gennemgang af SharePoint Online, der er filtreret i Wireshark af dns.time (små bogstaver) med tiden fra detaljerne til en kolonne og sorteret stigende.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Hvis du vil undersøge DNS-opløsningstiden mere, kan du prøve en PsPing mod den DNS-port, der bruges af TCP (f.eks.  `psping <IP address of DNS server>:53`) . Kan du stadig se ydelsesproblemet? Hvis du gør det, er der større sandsynlighed for, at problemet er et bredere netværksproblem end et problem med et specifikt DNS-program, du skal trykke på for at løse problemet. Det er også værd at nævne, at en ping til outlook.office365.com fortæller dig, hvor DNS-navneopløsningen for Outlook Online finder sted (f.eks. outlook-namnorthwest.office365.com).

Hvis problemet ser ud til at være DNS-specifikt, kan det være nødvendigt at kontakte din it-afdeling for at se DNS-konfigurationer og DNS-videresendere for at undersøge problemet yderligere.

### <a name="proxy-scalability"></a>Proxyskalerbarhed

Tjenester som Outlook Online i Office 365 giver kunder flere langsigtede forbindelser. Derfor kan hver bruger bruge flere forbindelser, der kræver en længere levetid.

#### <a name="tools"></a>Værktøjer

Matematik

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Der er ingen netværkssporing eller fejlfindingsværktøj specifikt til dette. I stedet er den baseret på båndbreddeberegninger med angivne begrænsninger og andre variabler.

### <a name="tcp-max-segment-size"></a>TCP Maks. segmentstørrelse

Findes i SYN - SYN/ACK.  Udfør denne kontrol i en netværkssporing af ydeevne, du har taget, for at sikre, at TCP-pakker er konfigureret til at foretage den maksimale mængde data.

Målet er at se en MSS på 1460 byte til overførsel af data. Hvis du er bag en proxy, eller hvis du bruger en NAT, skal du huske at køre denne test fra klient til proxy/udgangspunkt/NAT og fra proxy/udgangspunkt/NAT til Office 365 for at få de bedste resultater! Disse er forskellige TCP-sessioner.

#### <a name="tools"></a>Værktøjer

Netmon

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

TCP Max Segment Size (MSS) er en anden parameter i den trevejs-handshake i din netværkssporing, det betyder, at du finder de data, du skal bruge, i SYN - SYN/ACK-pakken. MSS er faktisk ret nemt at se.

Åbn netværkssporingen for den ydeevne, du har, og find den forbindelse, du gerne vil vide mere om, eller som demonstrerer ydelsesproblemet.

> [!NOTE]
> Hvis du kigger på en sporing og skal finde den trafik, der er relevant for samtalen, skal du filtrere efter IP på klienten eller IP på proxyserveren eller udgangspunkt eller begge dele. Hvis du går direkte, skal du pinge den URL-adresse, du tester IP-adressen for Office 365 i sporingen, og filtrere efter den.

Kigger du på den brugte sporing? Prøv at bruge filtre til at orientere dig selv. I Netmon skal du køre en søgning baseret på URL-adressen, f.eks `Containsbin(framedata, ascii, "sphybridExample")`, notere dig rammenummeret.

I Wireshark bruger noget i lignende måde  `frame contains "sphybridExample"`. Hvis du bemærker, at du har fundet Remote Winsock(RWS)-trafik (den kan vises som en [PSH, ACK] i Wireshark), skal du huske, at RWS-forbindelse kan ses kort før relevante SYN - SYN/ACKs, som nævnt tidligere.

På dette tidspunkt kan du registrere rammenummeret, slippe filteret, klikke på Al  trafik i vinduet Netværkssamtaler i Netmon for at se på det nærmeste SYN.

Det vigtigste er, at hvis du ikke har modtaget nogen af IP-adresseoplysningerne på tidspunktet for sporingen, får du ip-adresserne til at filtrere efter, hvis du finder din URL-adresse i sporingen ( `sphybridExample-my.sharepoint.com`f.eks. en del af den).

Find forbindelsen i den sporing, du er interesseret i at se. Du kan gøre dette ved enten at scanne sporingen, ved at filtrere efter IP-adresser eller ved at vælge bestemte samtale-chats ved hjælp af vinduet Network Conversations i Netmon. Når du har fundet SYN-pakken, skal du udvide TCP (i Netmon) eller Transmission Control Protocol (i Wireshark) i panelet Frame Details. Udvid TCP-indstillinger og MaxSegmentSize. Find den relaterede SYN-ACK ramme, og udvid TCP-indstillinger og MaxSegmentSize. Den mindste af de to værdier bliver din Maks. segmentstørrelse. På dette billede gør jeg brug af den indbyggede kolonne i Netmon kaldet TCP Troubleshoot.

![Netværkssporing filtreret i Netmon ved hjælp af de indbyggede kolonner.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Den indbyggede kolonne vises øverst i panelet **Frame Details** . (Hvis du vil skifte tilbage til normal visning, skal **du klikke** på Kolonner igen og **derefter vælge Tidszone**).

![Her finder du rullemenuen Kolonner for indstillingen TIL TCP-fejlfinding (oven på Rammeoversigt).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Her er et filtreret spor i Wireshark. Der er et filter specifikt for MSS-værdien (`tcp.options.mss`). Rammerne i en SYN-, SYN/ACK-, ACK-handshake er sammenkædet nederst i Wireshark svarende til rammedetaljerne (så ramme 47 ACK, linker til 46 SYN/ACK, linker til 43 SYN) for at gøre denne type arbejde nemmere.

![Sporing filtreret i Wireshark af tcp.options.mss for maksimal segmentstørrelse (MSS).](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Hvis du har brug for **at kontrollere Selektiv bekræftelse** (næste emne i denne matrix), skal du ikke lukke din sporing!

### <a name="selective-acknowledgment"></a>Selektiv bekræftelse

Findes i SYN - SYN/ACK. Skal rapporteres som Tilladt i både SYN og SYN/ACK. Selektiv bekræftelse (SACK) giver mulighed for en jævnere retransmission af data, når en pakke eller pakker forsvinder. Enheder kan deaktivere denne funktion, hvilket kan medføre problemer med ydeevnen.

Hvis du er bag en proxy, eller hvis du bruger en NAT, skal du huske at køre denne test fra klient til proxy/udgangspunkt/NAT og fra proxy/udgangspunkt/NAT til Office 365 for at få de bedste resultater! Disse er forskellige TCP-sessioner.

#### <a name="tools"></a>Værktøjer

Netmon

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Selektiv bekræftelse (SACK) er en anden parameter i SYN-SYN/ACK-handshake. Du kan filtrere dit spor for SYN - SYN/ACK på mange måder.

Find forbindelsen i den sporing, du er interesseret i at se, ved enten at scanne sporingen, filtrere efter IP-adresser eller ved at klikke på et samtale-id ved hjælp af vinduet Network Conversations i Netmon. Når du har fundet SYN-pakken, skal du udvide TCP i Netmon eller Transmission Control Protocol i Wireshark i sektionen Frame Details. Udvid TCP-indstillinger og derefter SACK. Find den relaterede SYN-ACK ramme, og udvid TCP-indstillinger og dens SACK-felt. Det er tilladt at foretage visse SACK i både SYN og SYN/ACK. Her er SACK-værdier, som det fremgår af både Netmon og Wireshark.

![Selektiv bekræftelse (SACK) i Netmon som et resultat af tcp.flags.syn == 1.](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![SACK som set i Wireshark med filteret tcp.flags.syn == 1.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS Geolocation

Hvor i verden Office 365 at løse dine DNS-opkald, har det indflydelse på forbindelseshastigheden.

I Outlook Online, efter det første DNS-opslag er udført, vil placeringen af den pågældende DNS blive brugt til at oprette forbindelse til dit nærmeste datacenter. Du får forbindelse til en Outlook Online CAS-server, som skal bruge et grundlæggende netværk til at oprette forbindelse til det datacenter (dC), hvor dine data lagres. Dette er hurtigere.

Når du åbner SharePoint Online, bliver en bruger, der rejser i udlandet, omdirigeret til deres aktive datacenter – det er dC, hvis placering er baseret på deres SPO-lejers hjemmebase (altså et dC i USA, hvis brugeren er USA-baseret).

Lync Online har aktive noder i mere end ét dC ad gangen. Når anmodninger sendes til Lync Online-forekomster, afgør Microsofts DNS, hvor i verden anmodningen stammer fra, og returnerer IP-adresser fra det nærmeste regionale dC, hvor Lync Online er aktiv.

> [!TIP]
> Vil du vide mere om, hvordan klienter opretter forbindelse til Office 365? Se nærmere på [referenceartikel om klientforbindelser](/previous-versions//dn741250(v=technet.10)) (og dens nyttige grafik).

#### <a name="tools"></a>Værktøjer

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Hvad du skal søge efter

Anmodninger om navneopløsning fra klientens DNS-servere til Microsofts DNS-servere bør i de fleste tilfælde resultere i, at Microsoft DNS returnerer IP-adressen på et regionalt datacenter (dC). Hvad betyder det for dig? Hvis dit hovedkvarter ligger i Bangalore, Indien, men du er ude at rejse i USA, når browseren foretager en anmodning om Outlook Online, skal Microsofts DNS-servere give dig IP-adresser til datacentre i USA – et regionalt datacenter. Hvis mail er nødvendig fra Outlook, vil disse data komme på tværs af Microsofts hurtige basisnetværk mellem datacentrene.

DNS fungerer hurtigst, når navneopløsningen udføres, så tæt på brugerens placering som muligt. Hvis du er i Europa, vil du gå til et Microsoft DNS i Europa og (ideelt set) have kontakt til et datacenter i Europa. Ydeevnen fra en klient i Europa, der går til DNS og et datacenter i USA, vil være langsommere.

Kør værktøjet mod en outlook.office365.com at afgøre, hvor i verden din DNS-anmodning bliver distribueret. Hvis du er i Europa, bør du kunne se et svar fra noget i outlook-emeawest.office365.com. I USA kan du forvente noget i outlook-namnorthwest.office365.com.

Åbn kommandoprompten på klientcomputeren (via Start Kør \> \> cmd eller Windows-tasttype \> cmd). Skriv ping outlook.office365.com og tryk på Enter. Husk at angive -4, hvis du vil angive, at pinge via IPv4. Det kan være, at du ikke får svar fra ICMP-pakkerne, men du bør kunne se navnet på den DNS, som anmodningen blev distribueret til. Hvis du vil se tallene for ventetiden for denne forbindelse, kan du prøve PsPing til IP-adressen på den server, der returneres af ping.

![Ping på outlook.office365.com, der viser opløsningen i outlook-namnorthwest.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing til den IP-adresse, der returneres af ping til outlook.office365.com viser en gennemsnitlig ventetid på 28 millisekunder.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 programfejlfinding

#### <a name="tools"></a>Værktøjer

- Netmon
- HTTPWatch
- F12-konsol i browseren

Vi dækker ikke værktøjer, der bruges i programspecifik fejlfinding, i denne netværksspecifikke artikel. Men du kan finde ressourcer, du *kan bruge*[, på denne side](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>Relaterede emner

[Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 ofte stillede spørgsmål om slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)