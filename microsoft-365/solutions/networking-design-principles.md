---
title: Netværk op (til clouden) – en arkitekts synspunkt
description: Få mere at vide om, hvordan du optimerer dit netværk til cloudforbindelse ved at undgå de mest almindelige faldgruber.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 5f90e4616edd3534baefd64bba5a2eec640f6366
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823932"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Netværk op (til clouden) – en arkitekts synspunkt

I denne artikel beskriver [Ed Fisher](https://www.linkedin.com/in/edfisher/), Security & Compliance Architect hos Microsoft, hvordan du optimerer dit netværk til cloudforbindelse ved at undgå de mest almindelige faldgruber.

## <a name="about-the-author"></a>Om forfatteren

![Ed Fisher foto.](../media/solutions-architecture-center/ed-fisher-networking.jpg)

Jeg er i øjeblikket principal teknisk specialist i vores team af detail- og forbrugsvarer med fokus på sikkerhed & overholdelse. Jeg har arbejdet med kunder, der flytter til Office 365 i de sidste ti år. Jeg har arbejdet med mindre butikker med en håndfuld placeringer til offentlige myndigheder og virksomheder med millioner af brugere, der er fordelt over hele verden, og mange andre kunder imellem, hvor størstedelen har titusinder af brugere, flere placeringer i forskellige dele af verden, behovet for en højere grad af sikkerhed og en lang række overholdelseskrav. Jeg har hjulpet hundredvis af virksomheder og millioner af brugere med at flytte sikkert og sikkert til cloudmiljøet.

Med en baggrund i de seneste 25 år, der omfatter sikkerhed, infrastruktur og netværkskonstruktion, og som har flyttet to af mine tidligere arbejdsgivere til Office 365, før jeg kom til Microsoft, har jeg været på din side af tabellen masser af gange og huske, hvordan det er. Selvom ikke to kunder nogensinde er de samme, har de fleste lignende behov, og når du bruger en standardiseret tjeneste som f.eks. en SaaS- eller PaaS-platform, har de bedste tilgange tendens til at være de samme.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Det er ikke netværket – det er sådan, du bruger det (mis)!

Uanset hvor mange gange det sker, forbløffer det mig aldrig, hvordan *kreative* sikkerhedsteams og netværksteams forsøger at få med, hvordan de synes, de skal oprette forbindelse til Microsofts cloudtjenester. Der er altid nogle sikkerhedspolitik, overholdelsesstandard eller bedre måde, de insisterer på at bruge, uden at være villige til at deltage i en samtale om, hvad det er, de forsøger at opnå, eller *hvordan* der er bedre, nemmere, mere omkostningseffektive og mere effektive måder at gøre det på.

Når denne slags ting eskaleres til mig, er jeg normalt villig til at tage udfordringen og gå dem gennem hows og whys og få dem til, hvor de skal være. Men hvis jeg er helt ærlig, jeg er nødt til at dele, at nogle gange jeg ønsker at bare lade dem gøre, hvad de vil, og vende tilbage til at sige, at jeg fortalte dig, så når de endelig indrømme det ikke virker. Det vil jeg måske gerne gøre nogle gange, men *det gør jeg ikke*. Hvad jeg gør, er at forsøge at forklare alle, hvad jeg vil medtage i dette indlæg. Hvis din organisation ønsker at bruge Microsoft-cloudtjenester, er der sandsynligvis nogle visdom i det følgende, der kan hjælpe dig, uanset hvilken rolle du har.

## <a name="guiding-principles"></a>Ledende principper

Lad os starte med nogle grundregler omkring, hvad vi laver her. Vi diskuterer, hvordan du kan oprette sikker forbindelse til cloudtjenester for at sikre minimum kompleksiteten og den maksimale ydeevne, samtidig med at du bevarer ægte sikkerhed. Intet af det følgende er i modstrid med noget af det, selvom du eller din kunde ikke får adgang til at bruge din foretrukne proxyserver til alt.

- **Bare fordi du kan, betyder ikke, du skal**: Eller at omskrive Dr. Ian Malcolm fra Jurassic Park filmen "... Ja, ja, men dit sikkerhedsteam var så optaget af, om de kunne, at de ikke holdt op med at tænke, om de skulle.
- **Sikkerhed betyder ikke kompleksitet**: Du er ikke mere sikker, bare fordi du bruger flere penge, dirigerer gennem flere enheder eller klikker på flere knapper.
- **Office 365 tilgås via internettet**: Men det er ikke det samme som Office 365 er internettet. Det er en SaaS-tjeneste, der administreres af Microsoft og administreres af dig. I modsætning til hjemmesider, du besøger på internettet, du rent faktisk får at smugkig bag gardinet, og kan anvende de kontroller, du har brug for at opfylde dine politikker og dine overholdelsesstandarder, så længe du forstår, at mens du kan opfylde dine mål, kan du bare nødt til at gøre dem på en anden måde.
- **Chokepoints er dårlige, lokaliserede breakouts er gode**: Alle altid ønsker at backhaul alle deres internettrafik for alle deres brugere til nogle centrale punkt, som regel så de kan overvåge det og håndhæve politik, men ofte fordi det er enten billigere end klargøring internetadgang i alle deres placeringer, eller det er bare hvordan de gør det. Men de kvælninger er lige præcis, at... punkter, hvor trafikken formindskes. Der er ikke noget galt med at forhindre dine brugere i at gennemse på Instagram eller streame kattevideoer, men behandl ikke din missionskritiske trafik til virksomhedsprogrammer på samme måde.
- **Hvis DNS ikke er glad, er det ikke noget godt**: Det bedst designede netværk kan forkøjes af dårlig DNS, uanset om det er ved at gentage anmodninger til servere i andre områder af verden eller ved at bruge din internetudbyders DNS-servere eller andre offentlige DNS-servere, der cachelagrer DNS-opløsningsoplysninger.
- **Bare fordi det var sådan, du plejede at gøre det, betyder det ikke, at det er sådan, du skal gøre det nu**: Teknologien ændres konstant, og Office 365 er ingen undtagelse. Anvendelse af sikkerhedsforanstaltninger, der er udviklet og udrullet til tjenester i det lokale miljø eller til at styre websurfing, vil ikke give samme sikkerhedsniveau og kan have en betydelig negativ indvirkning på ydeevnen.
- **Office 365 blev bygget til at få adgang via internettet**: Det er det i en nøddeskal. Uanset hvad du vil gøre mellem dine brugere og din grænse, går trafikken stadig over internettet, når den forlader dit netværk, og før den kommer ind på vores. Selv hvis du bruger Azure ExpressRoute til at dirigere ventetidsfølsom trafik fra dit netværk direkte til vores, er internetforbindelse absolut påkrævet. Acceptér det. Tænk ikke over det.

## <a name="where-bad-choices-are-often-made"></a>Hvor der ofte foretages forkerte valg

Selvom der er masser af steder, hvor der træffes dårlige beslutninger i sikkerhedens navn, er det dem, jeg oftest støder på med kunder. Mange kundesamtaler involverer alle disse på én gang.

### <a name="insufficient-resources-at-the-edge"></a>Utilstrækkelige ressourcer på kanten

Meget få kunder udruller greenfield-miljøer, og de har mange års erfaring med, hvordan deres brugere arbejder, og hvordan deres internet udgående data er. Uanset om kunderne har proxyservere eller tillader direkte adgang og ganske enkelt NAT-udgående trafik, har de gjort det i årevis og overvejer ikke, hvor meget mere de vil begynde at pumpe gennem deres grænse, når de flytter traditionelle interne programmer ud til cloudmiljøet.

Båndbredde er altid et problem, men NAT-enheder har muligvis ikke nok hestekræfter til at håndtere den øgede belastning og kan starte for tidligt at lukke forbindelser for at frigøre ressourcer. De fleste af de klientprogrammer, der opretter forbindelse til Office 365 forventer vedvarende forbindelser, og en bruger, der udnytter Office 365, kan have 32 eller flere samtidige forbindelser. Hvis NAT-enheden slipper dem for tidligt, svarer disse apps muligvis ikke, når de forsøger at bruge de forbindelser, der ikke længere findes. Når de giver op og forsøger at etablere nye forbindelser, lægger de endnu mere belastning på dit netværksudstyr.

### <a name="localized-breakout"></a>Lokaliseret understregningsstreg

Alt andet på denne liste kommer ned til én ting - at komme ud af dit netværk og på vores så hurtigt som muligt. Hvis du backhaulerer dine brugeres trafik til et centralt udgående punkt, især når dette udgående punkt er i et andet område, end dine brugere er i, introducerer du unødvendig ventetid og påvirker både klientoplevelsen og downloadhastighederne. Microsoft har tilstedeværelsespunkter over hele verden med frontends for alle vores tjenester og peering etableret med stort set alle større internetudbydere, så routing af dine brugeres trafik *lokalt* sikrer, at det hurtigt kommer ind i vores netværk med minimal ventetid.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>DNS-opløsningstrafik skal følge udgående internetsti

For at en klient kan finde et hvilket som helst slutpunkt, skal den naturligvis bruge DNS. Microsofts DNS-servere evaluerer kilden til DNS-anmodninger for at sikre, at vi returnerer det svar, der er, i internettermer, tættest på kilden til anmodningen. Sørg for, at din DNS er konfigureret, så anmodninger om navnefortsættelse går den samme sti som dine brugeres trafik, så du ikke giver dem lokal udgående data, men til et slutpunkt i et andet område. Det betyder, at lokale DNS-servere skal "gå til rod" i stedet for at videresende til DNS-servere i eksterne datacentre. Og hold øje med offentlige og private DNS-tjenester, som kan cachelagre resultater fra en del af verden og betjene dem på anmodninger fra andre dele af verden.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>For at proxy eller ikke til proxy, er det spørgsmålet

En af de første ting, du skal overveje, er, om proxybrugernes forbindelser til Office 365 skal overvejes. Det er nemt. ikke proxy. Office 365 tilgås via internettet, men det er ikke INTERNETTET. Det er en udvidelse af dine kernetjenester og bør behandles som sådan. Alt, hvad du vil have en proxy til at gøre, f.eks. DLP eller antimalware eller indholdsinspektion, er allerede tilgængeligt for dig i tjenesten og kan bruges i stor skala og uden at skulle knække TLS-krypterede forbindelser. Men hvis du virkelig ønsker at proxy trafik, som du ikke på anden måde kan styre, skal du være opmærksom på vores vejledning på [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) og kategorierne af trafik på [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md). Vi har tre kategorier af trafik til Office 365. Optimer og Tillad bør virkelig gå direkte og omgå din proxy. Standarden kan proxied. Detaljerne er i disse dokumenter ... læse dem.

De fleste kunder, der insisterer på at bruge en proxy, når de rent faktisk ser på, hvad de gør, kommer til at indse, at når klienten gør en HTTP CONNECT-anmodning til proxyen, proxyen er nu bare en dyr ekstra router. Protokollerne i brug såsom MAPI og RTC er ikke engang protokoller, som web proxyer forstår, så selv med TLS cracking du ikke rigtig får nogen ekstra sikkerhed. Du *får* ekstra ventetid. Se [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) for at få mere at vide om dette, herunder kategorierne Optimer, Tillad og Standard for Microsoft 365 trafik.

Endelig skal du overveje den samlede indvirkning på proxyen og dens tilsvarende svar for at håndtere denne indvirkning. Efterhånden som der oprettes flere og flere forbindelser via proxyen, kan det reducere TCP-skalafaktoren, så den ikke behøver at bufferlagre så meget trafik. Jeg har set kunder, hvor deres proxyer var så overbelastede, at de brugte en skalafaktor på 0. Da Scale Factor er en eksponentiel værdi, og vi kan lide at bruge 8, har hver reduktion i værdien af Skaleringsfaktor en enorm negativ indvirkning på gennemløbet.

TLS-inspektion betyder SIKKERHED! Men ikke rigtig! Mange kunder med proxyer vil gerne bruge dem til at inspicere al trafik, og det betyder, at TLS "afbryder og inspicerer". Når du gør det for et websted, der tilgås via HTTPS (uanset bekymringer om beskyttelse af personlige oplysninger), skal din proxy muligvis gøre det for 10 eller endda 20 samtidige streams i et par hundrede millisekunder. Hvis der er en stor download eller måske en video involveret, kan en eller flere af disse forbindelser vare meget længere, men generelt etablerer, overfører og lukker de fleste af disse forbindelser meget hurtigt. At afbryde og undersøge betyder, at proxyen skal gøre det dobbelte af arbejdet. For hver forbindelse fra klienten til proxyen skal proxyen også oprette en separat forbindelse tilbage til slutpunktet. Så 1 bliver 2, 2 bliver 4, 32 bliver 64...se hvor jeg skal hen? Du sandsynligvis mellemstore din proxy løsning helt fint for typiske web-surfing, men når du forsøger at gøre det samme for klientforbindelser til Office 365, antallet af samtidige, lang levetid forbindelser kan være ordrer af størrelse større end hvad du dimensioneret til.

### <a name="streaming-isnt-important-except-that-it-is"></a>Streaming er ikke vigtigt, bortset fra at det *er*

De eneste tjenester i Office 365, der bruger UDP, er Skype (der snart udgår) og Microsoft Teams. Teams bruger UDP til streamingtrafik, herunder deling af lyd, video og præsentation. Streaming af trafik er live, f.eks. når du har et onlinemøde med stemme,video og præsentationssæt eller udfører demoer. Disse bruger UDP, fordi hvis pakker droppes, eller ankommer i forkert rækkefølge, er det praktisk taget unnoticeable af brugeren, og streamen kan bare fortsætte.

Når du ikke tillader udgående UDP-trafik fra klienter til tjenesten, kan de gå tilbage til at bruge TCP. Men hvis en TCP-pakke slippes, *stopper alt* , indtil RTO 'en (Retransmission Timeout) udløber, og den manglende pakke kan sendes igen. Hvis en pakke ankommer i forkert rækkefølge, stopper alt, indtil de andre pakker ankommer og kan samles igen i rækkefølge. Begge fører til mærkbare fejl i lyden (husk Max Headroom?) og video (har du klikket på noget ... åh, der er den) og føre til dårlig ydeevne og en dårlig brugeroplevelse. Og husk, hvad jeg satte op over om proxyer? Når du tvinger en Teams klient til at bruge en proxy, tvinger du den til at bruge TCP. Så nu forårsager du negative indvirkninger på ydeevnen to gange.

### <a name="split-tunneling-may-seem-scary"></a>Opdelt tunnelføring kan virke skræmmende

Men det er det ikke. Alle forbindelser til Office 365 er over TLS. Vi har tilbudt TLS 1.2 i lang tid nu og vil deaktivere ældre versioner snart, fordi ældre klienter stadig bruger dem, og det er en risiko.

Hvis du tvinger en TLS-forbindelse eller 32 af dem til at gå over en VPN-forbindelse, før de derefter går til tjenesten, tilføjes der ikke sikkerhed. Det tilføjer ventetid og reducerer det overordnede gennemløb. I nogle VPN-løsninger tvinger det endda UDP til at tunnele gennem TCP, hvilket igen vil have en meget negativ indvirkning på streamingtrafikken. Og medmindre du laver TLS-inspektion, er der ingen opadrettede, alle ulemper. Et meget almindeligt tema blandt kunderne, nu hvor det meste af deres arbejdsstyrke er fjernt, er, at de oplever betydelige båndbredde- og ydeevneeffekter fra at få alle deres brugere til at oprette forbindelse ved hjælp af en VPN i stedet for at konfigurere opdelt tunnelføring for at få adgang til [Optimer kategori Office 365 slutpunkter](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

Det er en nem løsning at gøre opdelt tunnelføring, og det er en, du skal gøre. Du kan få mere at vide ved at gennemse [Optimer Office 365 forbindelse for fjernbrugere ved hjælp af opdelt VPN-tunnelføring](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Fortidens synder

Mange gange er årsagen til, at der træffes forkerte valg, fra en kombination af (1) uden at vide, hvordan tjenesten fungerer, (2) forsøger at overholde virksomhedens politikker, der blev skrevet, før du tog cloudmiljøet i brug, og (3) sikkerhedsteams, der måske ikke let er overbevist om, at der er mere end én måde at nå deres mål på. Forhåbentlig ovenstående, og links nedenfor, vil hjælpe med den første. Executive sponsorater kan være påkrævet for at komme forbi den anden. Løsning af sikkerhedspolitikkernes mål i stedet for deres metoder hjælper med den tredje. Fra betinget adgang til indstilling af indhold, DLP til informationsbeskyttelse, validering af slutpunkter til nuldagstrusler – alle slutmål, som en rimelig sikkerhedspolitik kan have, kan opnås med det, der er tilgængeligt i Office 365, og uden nogen afhængighed af netværksudstyr i det lokale miljø, tvungne VPN-tunneler og TLS-afbrydelse og -inspektion.

Andre gange kan hardware, der blev dimensioneret og købt, før organisationen begyndte at flytte til cloudmiljøet, simpelthen ikke skaleres op for at håndtere de nye trafikmønstre og belastninger. Hvis du virkelig skal dirigere al trafik gennem et enkelt udgående punkt, og / eller proxy det, være parat til at opgradere netværksudstyr og båndbredde i overensstemmelse hermed. Overvåg nøje udnyttelsen af begge dele, da oplevelsen ikke reduceres langsomt, efterhånden som flere brugere ombord. Alt vil være fint, indtil vi er nået til vippepunktet, så alle lider.

## <a name="exceptions-to-the-rules"></a>Undtagelser fra reglerne

Hvis din organisation kræver [lejerbegrænsninger](/azure/active-directory/manage-apps/tenant-restrictions), skal du bruge en proxy med TLS-afbrydelse og inspicere for at tvinge noget trafik gennem proxyen, men du behøver ikke at gennemtvinge al trafik gennem den.  Det er ikke en alle eller intet forslag, så vær opmærksom på, hvad der skal ændres af proxyen.

Hvis du vil tillade opdelt tunnelføring, men også bruge en proxy for generel webtrafik, skal du sørge for, at din PAC-fil definerer, hvad der skal gå direkte, samt hvordan du definerer interessant trafik for, hvad der går gennem VPN-tunnellen. Vi tilbyder prøve PAC-filer på [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) , der vil gøre det nemmere at administrere.

## <a name="conclusion"></a>Konklusion

Titusindvis af organisationer, herunder næsten alle Fortune 500, bruger Office 365 hver dag til deres missionskritiske funktioner. Det gør de sikkert, og det gør de via internettet.

Uanset hvilke sikkerhedsmål du har i spil, er der måder at opnå dem på, der ikke kræver VPN-forbindelser, proxyservere, TLS-afbrydelse og -inspektion eller central internetudgående for at få dine brugeres trafik væk fra dit netværk og videre til vores så hurtigt som muligt, hvilket giver den bedste ydeevne, uanset om dit netværk er virksomhedens hovedkvarter,  et fjernkontor eller en bruger, der arbejder hjemme. Vores vejledning er baseret på, hvordan Office 365-tjenesterne bygges, og for at sikre en sikker og effektiv brugeroplevelse.

## <a name="further-reading"></a>Yderligere læsning

[Principperne for Office 365 netværksforbindelsen](../enterprise/microsoft-365-network-connectivity-principles.md)

[Office 365-URL-adresser og IP-adresseintervaller](../enterprise/urls-and-ip-address-ranges.md)

[Administrere Office 365-slutpunkter](../enterprise/managing-office-365-endpoints.md)

[Office 365 IP-adresse og URL-adressewebtjeneste](../enterprise/microsoft-365-ip-web-service.md)

[Vurdering af Office 365 netværksforbindelse](../enterprise/assessing-network-connectivity.md)

[Office 365 netværk og justering af ydeevne](../enterprise/network-planning-and-performance.md)

[Vurdering af Office 365 netværksforbindelse](../enterprise/assessing-network-connectivity.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](../enterprise/performance-tuning-using-baselines-and-history.md)

[Plan for fejlfinding af ydeevnen for Office 365](../enterprise/performance-troubleshooting-plan.md)

[Netværk til levering af indhold](../enterprise/content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://connectivity.office.com/)

[Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 netværksblog](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 forbindelse til fjernbrugere ved hjælp af opdelt VPN-tunnelføring](../enterprise/microsoft-365-vpn-split-tunnel.md)
