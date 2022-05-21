---
title: Plan for fejlfinding af ydeevnen for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Denne artikel kan hjælpe dig med at foretage fejlfinding af Office 365 problemer med ydeevnen og endda løse nogle af de mest almindelige problemer.
ms.openlocfilehash: bb6033461d7b902ce0fad6e2c3b7b3e8f593951c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623035"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Plan for fejlfinding af ydeevnen for Office 365

Har du brug for at kende de trin, du skal udføre for at identificere og løse mellemliggende tid, stop og langsom ydeevne mellem SharePoint Online, OneDrive for Business, Exchange Online eller Skype for Business Online og din klientcomputer? Før du ringer til support, kan denne artikel hjælpe dig med at foretage fejlfinding af Office 365 problemer med ydeevnen og endda løse nogle af de mest almindelige problemer.

Denne artikel er faktisk et eksempel på en handlingsplan, som du kan bruge til at indsamle værdifulde data om problemet med ydeevnen, efterhånden som det sker. Nogle af de mest populære problemer er også inkluderet i denne artikel.

Hvis du ikke kender netværksydeevnen og gerne vil oprette en langsigtet plan for overvågning af ydeevnen mellem dine klientcomputere og Office 365, kan du se [Office 365 justering og fejlfinding af ydeevnen – administrator og it-Pro](performance-tuning-using-baselines-and-history.md).

## <a name="sample-performance-troubleshooting-action-plan"></a>Eksempel på en handlingsplan til fejlfinding af ydeevne

Denne handlingsplan indeholder to dele. en forberedelsesfase og en logføringsfase. Hvis du har problemer med ydeevnen lige nu, og du skal udføre dataindsamling, kan du begynde at bruge denne plan med det samme.

### <a name="prepare-the-client-computer"></a>Forbered klientcomputeren

- Find en klientcomputer, der kan genskabe problemet med ydeevnen. Denne computer bruges under fejlfinding.
- Skriv de trin ned, der medfører, at problemet med ydeevnen opstår, så du er klar, når det kommer til test.
- Installér værktøjer til indsamling og optagelse af oplysninger:
  - Installér [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865) (eller brug et tilsvarende værktøj til netværkssporing).
  - Installér den gratis Basic-udgave af [HTTPWatch](https://www.httpwatch.com/download/) (eller brug et tilsvarende værktøj til netværkssporing).
  - Brug en skærmoptager, eller kør trinoptageren (PSR.exe), der følger med Windows Vista og nyere, for at registrere de trin, du udfører under testen.

### <a name="log-the-performance-issue"></a>Logfør problemet med ydeevnen

- Luk alle overflødige internetbrowsere.
- Start Trinoptager eller en anden skærmoptager.
- Start din Netmon-registrering (eller værktøjet til netværkssporing).
- Ryd DNS-cachen på klientcomputeren fra kommandolinjen ved at skrive ipconfig /flushdns.
- Start en ny browsersession, og slå HTTPWatch til.
- Valgfrit: Hvis du tester Exchange Online, skal du køre værktøjet Exchange Client Effektivitetsanalyse fra Office 365 administrationskonsollen.
- Genskab de nøjagtige trin, der forårsager problemet med ydeevnen.
- Stop din Netmon eller andre værktøjs sporing.
- Kør en sporingsrute til dit Office 365-abonnement på kommandolinjen ved at skrive følgende kommando og derefter trykke på ENTER:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- Stop Trinoptager, og gem videoen. Sørg for at inkludere dato og klokkeslæt for hentningen, og om det viser en god eller dårlig ydeevne.
- Gem sporingsfilerne. Husk igen at inkludere dato og klokkeslæt for hentningen, og om det viser en god eller dårlig ydeevne.

Hvis du ikke er bekendt med at køre de værktøjer, der er nævnt i denne artikel, skal du ikke bekymre dig, da vi giver disse trin næste. Hvis du er vant til at udføre denne form for netværksopfangning, kan du gå til [Sådan indsamler du baselines](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), som beskriver filtrering og læsning af loggene.

### <a name="flush-the-dns-cache-first"></a>Ryd FØRST DNS-cachen

Hvorfor? Når du rydder DNS-cachen ud, starter du dine test med en ren tavle. Når du rydder cachen, nulstiller du indholdet af DNS-fortolkeren til de mest opdaterede poster. Husk, at en rydning ikke fjerner VÆRTS-filposter. Hvis du bruger MANGE VÆRTS-filposter, skal du kopiere posterne ud til en fil i en anden mappe og derefter tømme HOST-filen.

#### <a name="flush-your-dns-resolver-cache"></a>Ryd din DNS-resolvercache

1. Åbn kommandoprompten (enten **Start kør** \>  \> **cmd** eller **Windows** **nøgle-cmd**\>).
2. Skriv følgende kommando, og tryk på ENTER:

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsofts [Netmon-værktøj](https://www.microsoft.com/download/details.aspx?id=4865) (Network Monitoring) analyserer pakker, dvs. trafik, der overføres mellem computere på netværk. Ved at bruge Netmon til at spore trafik med Office 365 kan du registrere, få vist og læse pakkeheadere, identificere mellemliggende enheder, kontrollere vigtige indstillinger på netværkshardware, søge efter tabte pakker og følge strømmen af trafik mellem computere på virksomhedens netværk og Office 365. Da den faktiske brødtekst i trafikken er krypteret, dvs. den (rejser på port 443 via SSL/TLS, kan du ikke læse de filer, der sendes. I stedet får du en ufiltreret sporing af den sti, som pakken tager, hvilket kan hjælpe dig med at spore problemets funktionsmåde.

Sørg for, at du ikke anvender et filter på nuværende tidspunkt. I stedet skal du gennemgå trinnene og demonstrere problemet, før du stopper sporingen og gemmer.

Når du har installeret Netmon 3.4, skal du åbne værktøjet og udføre disse trin:

### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Tag en Netmon-sporing, og genskab problemet

1. Start Netmon 3.4.
Der er tre ruder **på startsiden**: **Seneste optagelser**, **Vælg netværk** og **Introduktion med Microsoft Network Monitor 3.4. Læg mærke til det**. Panelet Vælg netværk giver dig også en liste over de standardnetværk, du kan hente fra. Sørg for, at netværkskort er valgt her.

2. Klik på **Ny hentning** **øverst på** startsiden. Dette tilføjer en ny fane ud for fanen **Startside** med navnet **Hent 1**.
![Netmons brugergrænseflade med knapperne New Capture, Start og Stop fremhævet.](../media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. Klik på **Start** på værktøjslinjen for at tage et enkelt billede.

4. Genskab de trin, der præsenterer et problem med ydeevnen.

5. Klik på **Stop** \> **fil** \> **gem som**. Husk at angive dato og klokkeslæt sammen med tidszonen og nævne, om det viser dårlig eller god ydeevne.

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/) leveres til betaling og en gratis udgave. Den gratis Basic Edition dækker alt, hvad du har brug for til denne test. HTTPWatch overvåger netværkstrafik og indlæsningstid for sider direkte fra browservinduet. HTTPWatch er en plug-in til Internet Explorer, der grafisk beskriver ydeevnen. Analysen kan gemmes og vises i HTTPWatch Studio.

> [!NOTE]
> Hvis du bruger en anden browser, f.eks. Firefox, Google Chrome, eller hvis du ikke kan installere HTTPWatch i Internet Explorer, skal du åbne et nyt browservindue og trykke på F12 på tastaturet. Du kan se pop op-vinduet Udviklerværktøj nederst i din browser. Hvis du bruger Opera, skal du trykke på CTRL+SKIFT+I for Webfremviser og derefter klikke på fanen **Netværk** og fuldføre den test, der er beskrevet nedenfor. Oplysningerne vil være lidt anderledes, men indlæsningstiden vises stadig i millisekunder. > HTTPWatch er også meget nyttigt i forbindelse med problemer med indlæsningstider for SharePoint onlinesider.

### <a name="run-httpwatch-and-reproduce-the-issue"></a>Kør HTTPWatch, og genskab problemet

HTTPWatch er en browser-plug-in, så det er en smule anderledes at vise værktøjet i browseren for hver version af Internet Explorer. Du kan typisk finde HTTPWatch under kommandolinjen i Internet Explorer-browseren. Hvis du ikke kan se HTTPWatch-plug-in'en i browservinduet, skal du kontrollere versionen af browseren ved at klikke på **Hjælp** \> **om** eller i nyere versioner af Internet Explorer, klikke på tandhjulssymbolet og **Om Internet Explorer**. Hvis du vil **starte kommandolinjen** , skal du højreklikke på menulinjen i Internet Explorer og klikke på **Kommandolinjer**.

HTTPWatch har tidligere været knyttet til både kommandoerne og stifinderlinjerne, så når du først har installeret, skal du kontrollere **Værktøjer** og dine værktøjslinjer for ikonet, hvis du ikke straks ser ikonet (selv efter genstart). Husk, at værktøjslinjer kan tilpasses, og at der kan føjes indstillinger til dem.

![Værktøjslinjen Kommando i Internet Explorer med HTTPWatch-ikonet vist.](../media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)

1. Start HTTPWatch i et Internet Explorer-browservindue. Det vises forankret til browseren nederst i det pågældende vindue. Klik på **Post**.

2. Genskab de nøjagtige trin, der er involveret i problemet med ydeevnen. Klik på knappen **Stop** i HTTPWatch.

3. **Gem** HTTPWatch eller **Send via mail**. Husk at navngive filen, så den indeholder oplysninger om dato og klokkeslæt og en indikation af, om uret indeholder en demonstration af god eller dårlig ydeevne.

![HTTPWatch, der viser fanen Netværk for en sideindlæsning på Office 365 startside.](../media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

Dette skærmbillede er fra Professional-versionen af HTTPWatch. Du kan åbne sporinger, der er taget i den grundlæggende version, på en computer med en Professional-version og læse den der. Der kan være flere oplysninger tilgængelige fra sporingen via denne metode.

## <a name="problem-steps-recorder"></a>Optager til problemtrin

Trinoptager eller PSR.exe giver dig mulighed for at registrere problemer, efterhånden som de opstår. Det er et meget nyttigt værktøj og nemt at køre.

### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>Kør Optager til problemtrin (PSR.exe) for at registrere dit arbejde

1.  \> Brug enten **startkørselstypen** \> **PSR.exe** \> **OK**, eller klik påPSR.exe **Windows** \> **nøgletype**\>, og tryk derefter på ENTER.

2. Når det lille PSR.exe vindue vises, skal du klikke på **Start post** og genskabe de trin, der genskaber problemet med ydeevnen. Du kan tilføje kommentarer efter behov ved at klikke på **Tilføj kommentarer**.

3. Klik på **Stop post** , når du har fuldført trinnene. Hvis problemet med ydeevnen er en sidegengivelse, skal du vente på, at siden gengives, før du stopper optagelsen.

4. Klik på **Gem**.

![Et skærmbillede af Trinoptager eller PSR.exe.](../media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)

Dato og klokkeslæt registreres for dig. Dette linker din PSR til din Netmon-sporing og HTTPWatch i tide og hjælper med fejlfinding af præcision. Datoen og klokkeslættet i PSR-posten kan f.eks. vise, at der gik et minut mellem logon og browsing af URL-adressen og den delvise gengivelse af administrationswebstedet.

## <a name="read-your-traces"></a>Læs dine sporinger

Det er ikke muligt at lære alt om fejlfinding af netværk og ydeevne, som nogen har brug for at vide via en artikel. At blive god til ydeevne kræver erfaring og viden om, hvordan dit netværk fungerer og som regel fungerer. Men det er muligt at runde en liste over de mest almindelige problemer op og vise, hvordan værktøjer kan gøre det nemmere for dig at fjerne de mest almindelige problemer.

Hvis du vil hente færdigheder, der læser netværkssporinger for dine Office 365 websteder, er der ingen bedre lærer end at oprette spor af sidebelastninger regelmæssigt og få erfaring med at læse dem. Når du f.eks. har en chance, skal du indlæse en Office 365 tjeneste og spore processen. Filtrer sporingen for DNS-trafik, eller søg i FrameData efter navnet på den tjeneste, du har gennemset. Scan sporingen for at få en idé om de trin, der opstår, når tjenesten indlæses. Dette vil hjælpe dig med at lære, hvordan normal sidebelastning skal se ud, og i tilfælde af fejlfinding, især omkring ydeevne, kan sammenligning af gode og dårlige spor lære dig meget.

Netmon bruger Microsoft Intellisense i feltet Vis filter. Intellisense eller intelligent kodefuldførelse er det trick, hvor du skriver i en periode, og alle tilgængelige indstillinger vises i en rulleliste. Hvis du f.eks. er bekymret for TCP-vinduesskalering, kan du finde vej til et filter (f.eks.  `.protocol.tcp.window < 100`) på denne måde.

![Skærmbillede af Netmon, der viser, at feltet Visningsfilter bruger intellisense.](../media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)

Netmon spor kan have en masse trafik i dem. Hvis du ikke har erfaring med at læse dem, er det sandsynligt, at du bliver overvældet over at åbne sporingen første gang. Den første ting at gøre er at adskille signalet fra baggrundsstøj i sporingen. Du har testet mod Office 365, og det er den trafik, du vil se. Hvis du er vant til at navigere gennem sporinger, har du muligvis ikke brug for denne liste.

Trafik mellem din klient og Office 365 rejser via TLS, hvilket betyder, at selve trafikken krypteres og ikke kan læses i en generisk Netmon-sporing. Din ydeevneanalyse behøver ikke at kende specifikationerne for oplysningerne i pakken. Den er dog meget interesseret i pakkeheadere og de oplysninger, de indeholder.

### <a name="tips-to-get-a-good-trace"></a>Tips at få en god sporing

- Kend værdien af IPv4- eller IPv6-adressen på klientcomputeren. Du kan hente dette fra kommandoprompten ved at skrive **IPConfig** og derefter trykke på ENTER. Hvis du kender denne adresse, kan du hurtigt se, om trafikken i sporingen direkte involverer din klientcomputer. Hvis der er en kendt proxy, ping det og få sin IP-adresse samt.

- Ryd din DNS-resolvercache, og luk alle browsere undtagen den, hvor du kører dine test, hvis det er muligt. Hvis du f.eks. ikke kan gøre dette, hvis support bruger et browserbaseret værktøj til at se klientcomputerens skrivebord, skal du være forberedt på at filtrere din sporing.

- Find den Office 365 tjeneste, du bruger, i en optaget sporing. Hvis du aldrig eller sjældent har set din trafik før, er dette et nyttigt skridt i forhold til at adskille problemet med ydeevnen fra andre netværksstøj. Der er et par måder at gøre dette på. Direkte før din test kan du bruge _ping_ eller _PsPing_ mod URL-adressen til den specifikke tjeneste (`ping outlook.office365.com` eller `psping -4 microsoft-my.sharepoint.com:443`, f.eks. ). Du kan også nemt finde den ping eller PsPing i en Netmon-sporing (ved dens procesnavn). Det vil give dig et sted at begynde at lede.

Hvis du kun bruger Netmon-sporing på tidspunktet for problemet, er det også i orden. Hvis du vil orientere dig selv, skal du bruge et filter som `ContainsBin(FrameData, ASCII, "office")` eller `ContainsBin(FrameData, ASCII, "outlook")`. Du kan optage dit billednummer fra sporingsfilen. Det kan også være en god idé at rulle i ruden _Rammeoversigt_ helt til højre og kigge efter kolonnen Samtale-id. Der er angivet et nummer for id'et for denne specifikke samtale, som du også kan optage og se isoleret senere. Husk at fjerne dette filter, før du anvender anden filtrering.

> [!TIP]
> Netmon har en masse nyttige indbyggede filtre. Prøv knappen **Indlæs filter** øverst i ruden _Vis_ filter.

![Find din IP-adresse ved hjælp af PSPing på kommandolinjen på klientcomputeren.](../media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)

![Netmon-sporing fra klienten, der viser den samme PSPing-kommando via filteret TCP. Flags.Syn == 1.](../media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)

Bliv fortrolig med din trafik, og få mere at vide om, hvordan du finder de oplysninger, du har brug for. Du kan f.eks. få mere at vide om, hvilken pakke i sporingen der har den første reference til den Office 365 tjeneste, du bruger (f.eks. "Outlook").

Hvis du tager Office 365 Outlook Online som eksempel, starter trafikken noget i stil med dette:

- DNS-standardforespørgsel og DNS-svar for outlook.office365.com med matchende QueryID'er. Det er vigtigt at bemærke tidsforskydningen for denne turn-around, og hvor i verden Office 365 Global DNS sender anmodningen om navnefortsættelse. Ideelt set, så lokalt som muligt, snarere end halvvejs over hele verden.

- En HTTP GET-anmodning, hvis statusrapport er flyttet permanent (301)

- RWS-trafik, herunder RWS-Forbind-anmodninger og Forbind svar. (Dette er Remote Winsock, der opretter en forbindelse for dig).

- En TCP SYN- og TCP SYN/ACK-samtale. Mange indstillinger i denne samtale påvirker din ydeevne.

- Derefter en række TLS:TLS-trafik, som er stedet, hvor TLS-håndtryk og TLS-certifikatsamtaler finder sted. Husk, at dataene er krypteret via SSL/TLS.

Alle dele af trafikken er vigtige og forbundne, men små dele af sporingen indeholder oplysninger, der er vigtige for fejlfinding af ydeevnen, så vi vil fokusere på disse områder. Da vi har gjort nok Office 365 fejlfinding af ydeevnen hos Microsoft for at kompilere en Top Ti-liste over almindelige problemer, vil vi også fokusere på disse problemer, og hvordan du bruger de værktøjer, vi skal bruge til at rodfæste dem ud næste.

Hvis du ikke allerede har installeret dem, bruger matrixen nedenfor flere værktøjer, hvor det nogensinde er muligt. Der leveres links til installationspunkterne. Listen indeholder almindelige værktøjer til netværkssporing, f.eks. [Netmon](https://www.microsoft.com/download/details.aspx?id=4865) og [Wireshark](https://www.wireshark.org/), men brug et hvilket som helst sporingsværktøj, du er fortrolig med, og som du er vant til at filtrere netværkstrafik i. Når du tester, skal du huske:

- *Luk dine browsere, og test med kun én browser kørende*  – dette reducerer den samlede trafik, du registrerer. Det giver en mindre travl spor.
- *Ryd din DNS-resolvercache på klientcomputeren*  – Dette giver dig en ren tavle, når du begynder at tage din registrering, for at få en renere sporing.

## <a name="common-issues"></a>Almindelige problemer

Nogle almindelige problemer, du kan komme ud for, og hvordan du finder dem i din netværkssporing.

### <a name="tcp-windows-scaling"></a>TCP Windows skalering

Fundet i SYN – SYN/ACK. Ældre hardware eller ældre hardware kan muligvis ikke drage fordel af TCP Windows-skalering.  Uden de korrekte tcp-windows-skaleringsindstillinger udfyldes standardbufferen på 16-bit i TCP-headere i millisekunder.  Trafikken kan ikke fortsætte med at sende, før klienten modtager en bekræftelse på, at de oprindelige data er modtaget, hvilket medfører forsinkelser.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Se efter SYN - SYN/ACK-trafikken i din netværkssporing.  I Netmon skal du bruge et filter som  `tcp.flags.syn == 1`. Dette filter er det samme i Wireshark.

![Filtrer i Netmon eller Wireshark for Syn-pakker til begge værktøjer: TCP. Flags.Syn == 1.](../media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

Bemærk, at der for hver SYN er et kildeportnummer (SrcPort), der matches i destinationsporten (DstPort) for den relaterede anerkendelse (SYN/ACK).

Hvis du vil se den Windows skaleringsværdi, der bruges af din netværksforbindelse, skal du først udvide SYN og derefter den relaterede SYN/ACK.

![Grafik, der viser, hvordan du kan matche SrcPort med DstPort i en sporing for at hente deltatiden.](../media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)

### <a name="tcp-idle-time-settings"></a>TCP-inaktiv tid Indstillinger

Historisk set er de fleste perimeternetværk konfigureret til midlertidige forbindelser, hvilket betyder, at inaktive forbindelser generelt afbrydes. Inaktive TCP-sessioner kan afbrydes af proxyer og firewalls på mere end 100 til 300 sekunder. Dette er problematisk for Outlook Online, fordi det opretter og bruger langsigtede forbindelser, uanset om de er inaktive eller ej.

Når forbindelser afbrydes af proxy- eller firewallenheder, informeres klienten ikke, og et forsøg på at bruge Outlook Online betyder, at en klientcomputer gentagne gange vil forsøge at genoplive forbindelsen, før den foretager en ny. Du kan muligvis se, at produktet hænger, bliver bedt om det, eller at ydeevnen er langsom ved sideindlæsning.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

I Netmon skal du se på feltet Tidsforskydning for en rundtur. En rundtur er tiden mellem, at klienten sender en anmodning til serveren og modtager et svar. Kontrollér mellem klienten og udgående punkt (f.eks. Klient –\> proxy) eller den klient, der skal Office 365 (klient –\> Office 365). Du kan se dette i mange typer pakker.

Filteret i Netmon kan f.eks. se ud som  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, eller i Wireshark,  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.

> [!TIP]
> Ved du ikke, om IP-adressen i din sporing tilhører din DNS-server? Prøv at slå det op på kommandolinjen. Klik på **Start** \> **kør**\>, og skriv **cmd**, eller tryk **på Windows og** \> skriv **cmd**. Skriv i prompten  `nslookup <the IP address from the network trace>`. Hvis du vil teste, skal du bruge nslookup mod din egen computers IP-adresse. > Hvis du vil se en liste over Microsofts IP-intervaller, skal du se [Office 365 URL-adresser og IP-adresseområder](./urls-and-ip-address-ranges.md).

Hvis der er et problem, skal du forvente, at lange tidsforskydninger vises i dette tilfælde (Outlook Online), især i TLS:TLS-pakker, der viser passagen af programdata (i Netmon kan du f.eks. finde programdatapakker via `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). Du bør kunne se et gnidningsløst forløb i tiden på tværs af sessionen. Hvis du oplever lange forsinkelser, når du opdaterer dit Outlook Online, kan det skyldes, at der sendes en høj grad af nulstilling.

### <a name="latencyround-trip-time"></a>Ventetid/returtid

Ventetid er en måling, der kan ændre sig meget afhængigt af mange variabler, f.eks. opgradering af aldrende enheder, tilføjelse af et stort antal brugere til et netværk og procentdelen af den samlede båndbredde, der forbruges af andre opgaver på en netværksforbindelse.

Der er båndbreddeberegnere til Office 365 tilgængelige fra denne [netværksplanlægning og justering af ydeevnen for Office 365](network-planning-and-performance.md) side.

Har du brug for at måle hastigheden af din forbindelse eller internetudbyderens båndbredde? Prøv dette websted (eller websteder kan lide det): [Speedtest Official Site](https://www.speedtest.net/), eller forespørg din foretrukne søgemaskine til **sætningen hastighed test**.

#### <a name="tools"></a>Værktøjer

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Hvis du vil spore ventetid i en sporing, kan du drage fordel af at have registreret klientcomputerens IP-adresse og DNS-serverens IP-adresse i Office 365. Dette er for at lette sporingsfiltrering. Hvis du opretter forbindelse via en proxy, skal du bruge din klientcomputers IP-adresse, proxy-/udgående IP-adresse og den Office 365 DNS-IP-adresse for at gøre arbejdet nemmere.

En pinganmodning, der sendes til outlook.office365.com, fortæller dig navnet på det datacenter, der modtager anmodningen, selvom ping  *muligvis*  ikke kan oprette forbindelse for at sende de på hinanden følgende ICMP-pakker med varemærket. Hvis du bruger PsPing (et gratis værktøj til download), og specifikke havnen (443) og måske til at bruge IPv4 (-4) vil du få en gennemsnitlig rundtur-tid for pakker sendt. Dette fungerer for andre URL-adresser i Office 365-tjenester, f.eks`psping -4 yourSite.sharepoint.com:443`. . Faktisk kan du angive et antal pings for at få et større eksempel for dit gennemsnit, prøv noget i stil med `psping -4 -n 20 yourSite-my.sharepoint.com:443`.

> [!NOTE]
> PsPing sender ikke ICMP-pakker. Den pinger med TCP-pakker over en bestemt port, så du kan bruge en hvilken som helst, du kender, til at være åben. I Office 365, der bruger SSL/TLS, kan du prøve at vedhæfte port :443 til din PsPing.

![Skærmbillede, der viser en pingløsning outlook.office365.com og en PSPing med 443, der gør det samme, men som også rapporterer en gennemsnitlig RTT på 6,5 ms.](../media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

Hvis du har indlæst den langsomme ydeevne Office 365 side, mens du udfører en netværkssporing, skal du filtrere en Netmon- eller Wireshark-sporing for `DNS`. Dette er en af de IP-adresser, vi leder efter.

Her er de trin, du skal udføre for at filtrere din Netmon for at få IP-adressen (og se på DNS-ventetid). Dette eksempel bruger outlook.office365.com, men kan også bruge URL-adressen til en SharePoint Online-lejer (f.eks. hithere.sharepoint.com).

1. Ping URL-adressen `ping outlook.office365.com` , og registrer navnet og IP-adressen på den DNS-server, som pinganmodningen blev sendt til, i resultaterne.
2. Netværkssporing, der åbner siden, eller udfører den handling, der giver dig problemet med ydeevnen, eller, hvis du ser en høj ventetid på ping, selve netværket spore den.
3. Åbn sporingen i Netmon, og filtrer for DNS (dette filter fungerer også i Wireshark, men skelner mellem store og små bogstaver `-- dns`). Da du kender navnet på DNS-serveren fra din ping, kan du også filtrere mere hurtigt i Netmon på denne måde: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`, der ser sådan ud i Wireshark dns, og rammen indeholder "namnorthwest".<br/>Åbn svarpakken, og klik på **DNS** i vinduet Netmon **Frame Details** for at få flere oplysninger. I DNS-oplysningerne finder du IP-adressen på den DNS-server, som anmodningen gik til i Office 365. Du skal bruge denne IP-adresse til næste trin (PsPing-værktøjet). Fjern filteret, højreklik på DNS-svaret i Netmon (**Frame Summary** \> **Find Conversations** \> **DNS**) for at se DNS-forespørgslen og -svaret side om side.
4. I Netmon skal du også bemærke kolonnen Time Offset mellem DNS-anmodningen og svaret. I det næste trin kommer det brugervenlige [PsPing-værktøj](/sysinternals/downloads/psping) meget praktisk, både fordi ICMP ofte er blokeret på firewalls, og fordi PsPing elegant sporer ventetid i millisekunder. PsPing afslutter en TCP-forbindelse til en adresse og port (i vores tilfælde åben port 443).
5. Installér PsPing.
6. Åbn en kommandoprompt (\>startkørselstype \> cmd eller Windows Nøgletype \> cmd), og skift mappe til den mappe, hvor du installerede PsPing, for at køre PsPing-kommandoen. I mine eksempler kan du se, at jeg har lavet en "Perf" mappe på roden af C. Du kan gøre det samme for at få hurtig adgang.
7. Skriv kommandoen, så du foretager din PsPing mod IP-adressen på den Office 365 DNS-server fra din tidligere Netmon-sporing, herunder portnummeret, f.eks`psping -n 20 132.245.24.82:445`. . Dette giver dig et udsnit på 20 pings og den gennemsnitlige ventetid, når PsPing stopper.

Hvis du vil Office 365 via en proxyserver, er trinnene lidt anderledes. Du skal først Bruge PsPing til din proxyserver for at få en gennemsnitlig ventetidsværdi i millisekunder til proxy/udgående data og tilbage og derefter enten køre PsPing på proxyen eller på en computer med en direkte internetforbindelse for at få den manglende værdi (den, der skal Office 365 og tilbage).

Hvis du vælger at køre PsPing fra proxyen, har du to millisekundersværdier: Klientcomputer til proxyserver eller udgående punkt og proxyserver til Office 365. Og du er færdig! Nå, optagelse værdier, alligevel.

Hvis du kører PsPing på en anden klientcomputer, der har en direkte forbindelse til internettet, dvs. uden en proxy, har du to millisekundersværdier: Klientcomputer til proxyserver eller udgående punkt og klientcomputer til Office 365. I dette tilfælde skal du trække værdien af klientcomputeren til proxyserver eller udgående punkt fra værdien af klientcomputeren til Office 365, og du vil have RTT-tallene fra klientcomputeren til proxyserveren eller udgående punkt og fra proxyserveren eller udgående punkt til Office 365.

Men hvis du kan finde en klientcomputer på den påvirkede placering, der er direkte forbundet eller tilsidesætter proxyen, kan du vælge at se, om problemet genskabes der til at begynde med, og teste at bruge det derefter.

Ventetid, som vist i en Netmon-sporing, kan disse ekstra millisekunder tilføjes, hvis der er nok af dem i en given session.

![Generel ventetid i Netmon, hvor kolonnen Netmons standardkolonne Time Delta er føjet til Rammeoversigt.](../media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> Din IP-adresse kan være forskellig fra de IP-adresser, der er vist her, f.eks. kan din ping returnere noget mere som 157.56.0.0/16 eller et lignende interval. Hvis du vil se en liste over områder, der bruges af Office 365, skal du se [Office 365 URL-adresser og IP-adresseområder](./urls-and-ip-address-ranges.md).

Husk at udvide alle noder (der er en knap øverst til dette), hvis du vil søge efter f.eks. 132,245.

### <a name="proxy-authentication"></a>Proxygodkendelse

Dette gælder kun for dig, hvis du går gennem en proxyserver. Hvis ikke, kan du springe disse trin over. Når du arbejder korrekt, skal proxygodkendelse ske i millisekunder på samme måde. Du bør ikke se periodisk dårlig ydeevne i perioder med spidsbelastning (f.eks. ).

Hvis proxygodkendelse er slået til, skal du gennemgå en godkendelsesproces bag kulisserne, hver gang du opretter en ny TCP-forbindelse til Office 365 for at få oplysninger. Så når du f.eks. skifter fra Kalender til Mail i Outlook Online, godkendes du. Og hvis en side i SharePoint Online viser medier eller data fra flere websteder eller placeringer, skal du godkende for hver anden TCP-forbindelse, der er nødvendig for at gengive dataene.

I Outlook Online kan du opleve langsomme indlæsningstider, når du skifter mellem Kalender og din postkasse, eller langsomme sidebelastninger i SharePoint Online. Der er dog andre symptomer, der ikke er anført her.

Proxygodkendelse er en indstilling på udgående proxyserver. Hvis det medfører problemer med ydeevnen med Office 365, skal du kontakte netværksteamet.

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Proxygodkendelse finder sted, når en ny TCP-session skal spundes, ofte for at anmode om filer eller oplysninger fra serveren eller for at angive oplysninger. Du kan f.eks. se proxygodkendelse omkring HTTP GET- eller HTTP POST-anmodninger. Hvis du vil se de rammer, hvor du godkender anmodninger i din sporing, skal du føje kolonnen 'NTLMSSP Summary' til Netmon og filtrere efter  `.property.NTLMSSPSummary`. Hvis du vil se, hvor lang tid godkendelsen tager, skal du tilføje kolonnen Time Delta.

Sådan føjer du en kolonne til Netmon:

1. Højreklik på en kolonne, f.eks **Beskrivelse**.
2. Klik på **Vælg kolonner**.
3. Find _NTLMSSP Summary_ and _Time Delta_ på listen, og klik på **Tilføj**.
4. Flyt de nye kolonner på plads før eller bag kolonnen _Beskrivelse_ , så du kan læse dem side om side.
5. Klik på **OK**.

Selvom du ikke tilføjer kolonnen, fungerer Netmon-filteret. Men din fejlfinding bliver meget nemmere, hvis du kan se, hvilken fase af godkendelse du er i.

Når du leder efter forekomster af proxygodkendelse, skal du undersøge alle rammer, hvor der er en NTLM-udfordring, eller der findes en Godkendelsesmeddelelse. Hvis det er nødvendigt, skal du højreklikke på det specifikke stykke trafik og Find samtaler TCP \> . Vær opmærksom på deltaværdierne for tid i disse samtaler.

![Netmon-sporing, der viser proxygodkendelse filtreret efter samtale.](../media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

En fire sekunders forsinkelse i proxygodkendelse som vist i Wireshark. **Deltaet Tid fra forrige viste rammekolonne** blev foretaget ved at højreklikke på feltet med det samme navn i rammedetaljerne og vælge Tilføj som kolonne.  <br/> ![I Wireshark kan kolonnen 'Tidsdelta fra det forrige viste billede' foretages ved at højreklikke på feltet med det samme navn i rammedetaljerne og vælge Tilføj som kolonne.](../media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS-ydeevne

Navneopløsningen fungerer bedst og hurtigst muligt, når den finder sted så tæt på kundens land som muligt.

Hvis DNS-navnefortsættelse finder sted oversøisk, kan det føje sekunder til sidebelastninger. Ideelt set sker navnefortsættelse på under 100 ms. Hvis ikke, bør du undersøge det nærmere.

> [!TIP]
> Er du ikke sikker på, hvordan Client Connectivity fungerer i Office 365? Se dokumentet Reference til klientforbindelsen [her](/previous-versions//dn741250(v=technet.10)).

#### <a name="tools"></a>Værktøjer

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Analyse af DNS-ydeevnen er normalt et andet job for en netværkssporing. PsPing er dog også nyttigt i forbindelse med afgørelsen af en mulig årsag.

DNS-trafik er baseret på TCP- og UDP-anmodninger, og svar er tydeligt markeret med et id, der hjælper med at matche en bestemt anmodning med dets specifikke svar. Du får vist DNS-trafik, når SharePoint Online f.eks. bruger et netværksnavn eller en URL-adresse på en webside. Som tommelfingerregel kører det meste af denne trafik, undtagen når du overfører zoner, over UDP.

I både Netmon og Wireshark er det mest grundlæggende filter, der lader dig se på DNS-trafik, simpelthen `dns`. Sørg for at bruge små bogstaver, når du angiver filteret. Husk at rydde din DNS-løsningscache, før du begynder at genskabe problemet på klientcomputeren. Hvis du f.eks. har en langsom SharePoint Online-sideindlæsning for startsiden, skal du lukke alle browsere, åbne en ny browser, starte sporing, rydde DNS-fortolkercachen og gå til dit SharePoint Online-websted. Når hele siden er løst, skal du stoppe og gemme sporingen.

![Et grundlæggende filter for DNS i Netmon er DNS.](../media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

Du vil se på tidsforskydningen her. Det kan også være nyttigt at føje kolonnen **Time Delta** til Netmon, som du kan gøre ved at udføre disse trin:

1. Højreklik på en kolonne, f.eks **Beskrivelse**.
2. Klik på **Vælg kolonner**.
3. Find _Time Delta_ på listen, og klik på **Tilføj**.
4. Flyt den nye kolonne på plads før eller bag kolonnen _Beskrivelse_ , så du kan læse dem side om side.
5. Klik på **OK**.

Hvis du finder en forespørgsel af interesse, kan du overveje at isolere den ved at højreklikke på forespørgslen i panelet med rammeoplysninger og vælge **Find samtaler** \> **DNS**. Bemærk, at panelet Netværkssamtaler hopper direkte til den specifikke samtale i dens log over UDP-trafik.

![En Netmon-sporing af Outlook Online-indlæsning, der er filtreret efter DNS, og som bruger Find samtaler og derefter DNS til at indsnævre resultaterne.](../media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

I Wireshark kan du oprette en kolonne til DNS-tid. Tag din sporing (eller åbn en sporing) i Wireshark, og filtrer efter `dns`eller, mere nyttigt,  `dns.time`. Klik på en HVILKEN som helst DNS-forespørgsel, og udvid  `Domain Name System (response)` detaljerne i panelet, der viser detaljer. Du får vist et felt for tid (f.eks. `[Time: 0.001111100 seconds]`. Højreklik på dette tidspunkt, og vælg **Anvend som kolonne**. Dette giver dig en **tidskolonne** , hvor du hurtigere kan sortere sporingen. Klik på den nye kolonne for at sortere efter faldende værdier for at se, hvilket DNS-kald der tog længst tid at løse.

[En gennemgang af SharePoint Online filtreret i Wireshark efter (med små bogstaver) dns.time, hvor tiden fra detaljerne blev omdannet til en kolonne og sorteret stigende.](../media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

Hvis du vil undersøge DNS-opløsningstiden mere, kan du prøve en PsPing mod den DNS-port,  `psping <IP address of DNS server>:53`der bruges af TCP (f.eks. ) . Kan du stadig se et problem med ydeevnen? Hvis du gør det, er der større sandsynlighed for, at problemet er et bredere netværksproblem end et problem med specifikt det DNS-program, du er ved at løse. Det er også værd at nævne, igen, at en ping til outlook.office365.com vil fortælle dig, hvor DNS-navnefortsættelsen for Outlook Online finder sted (f.eks. outlook-namnorthwest.office365.com).

Hvis problemet ser ud til at være DNS-specifikt, kan det være nødvendigt at kontakte it-afdelingen for at se på DNS-konfigurationer og DNS-videresendere for at undersøge problemet yderligere.

### <a name="proxy-scalability"></a>Proxyskalerbarhed

Tjenester som Outlook Online i Office 365 tildele klienter flere langsigtede forbindelser. Derfor kan hver bruger bruge flere forbindelser, der kræver en længere levetid.

#### <a name="tools"></a>Værktøjer

Matematik

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Der er ingen specifik netværkssporings- eller fejlfindingsværktøj til dette. Den er i stedet baseret på beregninger af båndbredde, der giver begrænsninger og andre variabler.

### <a name="tcp-max-segment-size"></a>Maksimal TCP-segmentstørrelse

Fundet i SYN – SYN/ACK.  Udfør denne kontrol af en hvilken som helst netværkssporing, du har foretaget, for at sikre, at TCP-pakker er konfigureret til at indeholde den maksimale datamængde.

Målet er at se en MSS på 1460 byte til overførsel af data. Hvis du er bag en proxy, eller du bruger en NAT, skal du huske at køre denne test fra klient til proxy/udgående/NAT og fra proxy/udgående/NAT til Office 365 for at få de bedste resultater! Dette er forskellige TCP-sessioner.

#### <a name="tools"></a>Værktøjer

Netmon

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

TCP Max Segment Size (MSS) er en anden parameter for det trevejs-håndtryk i netværkssporingen, som betyder, at du finder de data, du har brug for, i PAKKEN SYN - SYN/ACK. MSS er faktisk ret enkel at se.

Åbn en hvilken som helst netværkssporing for ydeevnen, og find den forbindelse, du er nysgerrig efter, eller som demonstrerer problemet med ydeevnen.

> [!NOTE]
> Hvis du kigger på en sporing og har brug for at finde den trafik, der er relevant for din samtale, skal du filtrere efter klientens IP-adresse, proxyserverens IP-adresse eller udgangspunktet eller begge dele. Hvis du går direkte, skal du pinge den URL-adresse, du tester for IP-adressen for Office 365 i sporingen, og filtrere efter den.

Ser du på sporingen brugt? Prøv at bruge filtre til at orientere dig selv. I Netmon skal du køre en søgning, der er baseret på URL-adressen, f.eks `Containsbin(framedata, ascii, "sphybridExample")`. , tage rammenummeret til efterretning.

I Wireshark skal du bruge noget i stil med  `frame contains "sphybridExample"`. Hvis du bemærker, at du har fundet RWS-trafik (Remote Winsock) (det kan se ud som en [PSH, ACK] i Wireshark), skal du huske, at RWS-forbindelser kan ses kort før relevante SYN - SYN/ACKs, som beskrevet tidligere.

På dette tidspunkt kan du optage billednummeret, slippe filteret, klikke på **Al trafik** i vinduet Netværkssamtaler i Netmon for at se på den nærmeste SYN.

Det er vigtigt, at hvis du ikke modtog nogen af IP-adresseoplysningerne på tidspunktet for sporingen, vil det give dig IP-adresser at filtrere efter, hvis du finder din URL-adresse i sporingen (f.eks. en del af `sphybridExample-my.sharepoint.com`. ).

Find forbindelsen i den sporing, du er interesseret i at se. Det kan du gøre ved enten at scanne sporingen ved at filtrere efter IP-adresser eller ved at vælge bestemte samtale-id'er ved hjælp af vinduet Netværkssamtaler i Netmon. Når du har fundet SYN-pakken, skal du udvide TCP (i Netmon) eller Transmission Control Protocol (i Wireshark) i panelet Frame Details. Udvid TCP-indstillinger og MaxSegmentSize. Find den relaterede SYN-ACK-ramme, og udvid TCP-indstillinger og MaxSegmentSize. Den mindste af de to værdier er din maksimale segmentstørrelse. På dette billede bruger jeg den indbyggede kolonne i Netmon kaldet TCP-fejlfinding.

![Netværkssporing filtreret i Netmon ved hjælp af de indbyggede kolonner.](../media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

Den indbyggede kolonne er øverst i panelet **Rammedetaljer** . Hvis du vil skifte tilbage til den normale visning, skal du klikke på **Kolonner** igen og derefter vælge **Tidszone**.

![Her kan du finde rullelisten Kolonner for indstillingen TCP-fejlfinding (oven på Rammeoversigt).](../media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

Her er en filtreret sporing i Wireshark. Der er et filter, der er specifikt for MSS-værdien (`tcp.options.mss`). Rammerne for en SYN, SYN/ACK, ACK-håndtryk er sammenkædet nederst i Wireshark, der svarer til Frame Details (så ramme 47 ACK, links til 46 SYN/ACK, links til 43 SYN) for at gøre denne form for arbejde nemmere.

![Sporing filtreret i Wireshark efter tcp.options.mss for Maksimal segmentstørrelse (MSS).](../media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

Hvis du har brug for at kontrollere **Selektiv anerkendelse** (næste emne i denne matrix), skal du ikke lukke sporingen!

### <a name="selective-acknowledgment"></a>Selektiv anerkendelse

Fundet i SYN – SYN/ACK. Skal rapporteres som Tilladt i både SYN og SYN/ACK. SÆKKE (Selective Acknowledgment) giver mulighed for problemfri videretransmission af data, når en pakke eller pakker forsvinder. Enheder kan deaktivere denne funktion, hvilket kan medføre problemer med ydeevnen.

Hvis du er bag en proxy, eller du bruger en NAT, skal du huske at køre denne test fra klient til proxy/udgående/NAT og fra proxy/udgående/NAT til Office 365 for at få de bedste resultater! Dette er forskellige TCP-sessioner.

#### <a name="tools"></a>Værktøjer

Netmon

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

SACK (Selective Acknowledgment) er en anden parameter i SYN-SYN/ACK-håndtrykket. Du kan filtrere din sporing efter SYN – SYN/ACK på mange måder.

Find den forbindelse i sporingen, som du er interesseret i at se, enten ved at scanne sporingen, filtrere efter IP-adresser eller ved at klikke på et samtale-id ved hjælp af vinduet Netværkssamtaler i Netmon. Når du har fundet SYN-pakken, skal du udvide TCP i Netmon eller Transmission Control Protocol i Wireshark i afsnittet Frame Details. Udvid TCP-indstillinger og derefter SACK. Find den relaterede SYN-ACK-ramme, og udvid TCP-indstillinger og feltet SACK. Sørg for, at SACK er tilladt i både SYN og SYN/ACK. Her er SACK-værdier som set i både Netmon og Wireshark.

![Selektiv anerkendelse (SACK) i Netmon som et resultat af tcp.flags.syn == 1.](../media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![SACK som set i Wireshark med filteret tcp.flags.syn == 1.](../media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS Geolocation

Hvor i verden Office 365 forsøger at løse dit DNS-opkald, påvirker din forbindelseshastighed.

Når det første DNS-opslag er fuldført i Outlook Online, bruges placeringen af den pågældende DNS til at oprette forbindelse til dit nærmeste datacenter. Du får forbindelse til en Outlook Online CAS-server, som bruger backbone-netværket til at oprette forbindelse til det datacenter (dC), hvor dine data er gemt. Det her er hurtigere.

Når du tilgår SharePoint Online, bliver en bruger, der rejser i udlandet, dirigeret til deres aktive datacenter – dvs. den dC, hvis placering er baseret på brugerens SPO-lejers hjemmebase (dvs. en dC i USA, hvis brugeren er baseret på USA).

Lync Online har aktive noder i mere end én dC ad gangen. Når der sendes anmodninger om Lync-onlineforekomster, bestemmer Microsofts DNS, hvor i verden anmodningen kom fra, og returnerer IP-adresser fra den nærmeste regionale dC, hvor Lync Online er aktiv.

> [!TIP]
> Har du brug for at vide mere om, hvordan klienter opretter forbindelse til Office 365? Se artiklen [Reference til Client Connectivity](/previous-versions//dn741250(v=technet.10)) (og dens nyttige grafik).

#### <a name="tools"></a>Værktøjer

- Ping
- PsPing

#### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Anmodninger om navnefortsættelse fra klientens DNS-servere til Microsofts DNS-servere bør i de fleste tilfælde resultere i, at Microsoft DNS returnerer IP-adressen for et regionalt datacenter (dC). Hvad betyder det for dig? Hvis dit hovedkvarter befinder sig i Bangalore i Indien, men du rejser i USA, skal Microsofts DNS-servere give dig IP-adresser til datacentre i USA – et regionalt datacenter, når din browser anmoder om Outlook Online. Hvis der er brug for mail fra Outlook, bevæger disse data sig på tværs af Microsofts hurtige backbone-netværk mellem datacentrene.

DNS fungerer hurtigst, når navnefortsættelsen udføres så tæt på brugerens placering som muligt. Hvis du er i Europa, vil du gå til et Microsoft DNS i Europa og (ideelt set) håndtere et datacenter i Europa. Ydeevnen fra en klient i Europa, der går til DNS, og et datacenter i Usa vil være langsommere.

Kør pingværktøjet mod outlook.office365.com for at finde ud af, hvor i verden din DNS-anmodning distribueres. Hvis du er i Europa, bør du se et svar fra noget i stil med outlook-emeawest.office365.com. I Amerika, forventer noget i stil med outlook-namnorthwest.office365.com.

Åbn kommandoprompten på klientcomputeren (via Start \> kør \> cmd eller Windows nøgletype \> cmd). Skriv ping outlook.office365.com, og tryk på ENTER. Husk, at du skal angive -4, hvis du vil angive ping via IPv4. Du kan muligvis ikke få svar fra ICMP-pakkerne, men du får vist navnet på den DNS-adresse, som anmodningen blev sendt til. Hvis du vil se ventetidsnumrene for denne forbindelse, kan du prøve PsPing til IP-adressen på den server, der returneres af ping.

![Ping af outlook.office365.com, der viser opløsningen i outlook-namnorthwest.](../media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing til den IP-adresse, der returneres af ping til outlook.office365.com, der viser den gennemsnitlige ventetid på 28 millisekunder.](../media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>fejlfinding af Office 365 program

#### <a name="tools"></a>Værktøjer

- Netmon
- HTTPWatch
- F12 Console i browseren

Vi dækker ikke værktøjer, der bruges i programspecifik fejlfinding i denne netværksspecifikke artikel. Men du kan finde ressourcer, du  *kan*  bruge [på denne side](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).

## <a name="related-topics"></a>Relaterede emner

[Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)