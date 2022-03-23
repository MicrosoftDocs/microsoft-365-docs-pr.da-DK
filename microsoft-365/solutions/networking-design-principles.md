---
title: Netværke op (til skyen) – én arkitekts sene
description: Få mere at vide om, hvordan du optimerer dit netværk til skyforbindelse ved at undgå de mest almindelige fejl.
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
ms.openlocfilehash: 519f3035040f563a6f3663198be3952830cb21cb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590897"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Netværke op (til skyen) – én arkitekts sene

I denne artikel beskriver [Ed Fisher](https://www.linkedin.com/in/edfisher/), Security & Compliance Architect hos Microsoft, hvordan du optimerer dit netværk til skyforbindelse ved at undgå de mest almindelige fejl. 

## <a name="about-the-author"></a>Om forfatteren

![Ed Fisher-foto.](../media/solutions-architecture-center/ed-fisher-networking.jpg) 

Jeg er i øjeblikket Principal Technical Specialist i vores team for detail- og forbrugsvarer, hvor jeg fokuserer på & Overholdelse af regler og standarder. Jeg har arbejdet med kunder, der flytter til Office 365 de seneste ti år. Jeg har arbejdet med mindre butikker med en håndfuld placeringer til offentlige myndigheder og virksomheder med millioner af brugere fordelt over hele verden og mange andre kunder imellem. Størstedelen har titusindvis af brugere, flere placeringer i forskellige dele af verden, behovet for en højere grad af sikkerhed og en lang række krav til overholdelse. Jeg har hjulpet hundredvis af virksomheder og millioner af brugere med sikkert og sikkert at flytte til skyen.

Med en baggrund i løbet af de seneste 25 år, som omfatter sikkerhed, infrastruktur og netværksteknik og har flyttet to af mine tidligere arbejdsgivere til Office 365 før jeg blev medlem af Microsoft, har jeg været ved din side af tabellen mange gange og kan huske, hvordan det ser ud. Selv om to kunder aldrig har de samme, har de fleste lignende behov, og når de bruger en standardiseret tjeneste som f.eks. SaaS- eller PaaS-platforme, vil de bedste fremgangsmåder ofte være de samme.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Det er ikke netværket – det er sådan, du (forkert) bruger det!

Uanset hvor mange gange det sker, mislykkes det aldrig at overraske mig over, hvordan  kreative sikkerhedsteams og netværksteams forsøger at få med, hvordan de synes, de skal oprette forbindelse til Microsofts skytjenester. Der er altid nogle sikkerhedspolitik, overholdelsesstandard eller bedre måde, de arbejder på, uden at være villig til at deltage i en samtale om, hvad de forsøger at opnå, eller hvordan  der er bedre, nemmere, mere omkostningseffektiv og mere effektive måder at gøre det på. 

Når denne type ting eskaleres til mig, er jeg normalt villig til at tage udfordringen og hjælpe dem gennem hvordan og hvorfor og få dem til at nå ud til det, de skal. Men hvis jeg bliver helt åbenhjertig, er jeg nødt til at dele, at nogle gange vil jeg bare lade dem gøre det, de vil, og vende tilbage for at sige, at jeg har fortalt dig det, så når de til sidst giver dig besked om, at det ikke virker. Nogle gange vil jeg måske gøre det, men *det vil jeg ikke*. Hvad jeg gør, er at forsøge at forklare alt det, jeg vil medtage i dette indlæg. Uanset din rolle er der sandsynligvis noget over det følgende, der kan hjælpe dig, hvis din organisation ønsker at bruge Microsofts skytjenester.

## <a name="guiding-principles"></a>Styrende principper

Lad os starte med nogle grundregler for, hvad vi laver her. Vi diskuterer, hvordan du på sikker måde kan oprette forbindelse til skytjenester for at sikre den mindst mulige kompleksitet og den maksimale ydeevne, mens vi opretholder den reelle sikkerhed. Intet af det, der følger, er i strid med dette, selv hvis du eller din kunde ikke kommer til at bruge din foretrukne proxyserver til alt.

- **Bare fordi du kan, betyder** det ikke, at du bør: Eller omskrivning af Dr. IanLb fra den amerikanske parkfilm "... Ja, ja, men dit sikkerhedsteam var så optaget af, om de kunne eller ikke kunne, at de ikke stoppede med at tænke, om de skulle."
- **Sikkerhed betyder ikke kompleksitet: Du** er ikke mere sikker, bare fordi du bruger flere penge, dirigerer gennem flere enheder eller klikker på flere knapper.
- **Office 365 tilgås via** internettet: Men det er ikke det samme som Office 365 er internettet. Det er en SaaS-tjeneste, der administreres af Microsoft og administreres af dig. I modsætning til websteder, du besøger på internettet, får du faktisk et smugkig bag dig, og du kan anvende de kontrolelementer, du skal bruge for at overholde dine politikker og overholdelsesstandarder, så længe du forstår, at mens du opfylder dine målsætninger, er du muligvis nødt til at gøre det på en anden måde.
- Slutpunkter er dårlige, lokaliserede **breakouts** er gode: Alle vil altid have al deres internettrafik tilbage for alle deres brugere til et centralt punkt, som regel så de kan overvåge den og håndhæve politikker, men ofte fordi den enten er billigere end klargøring af internetadgang på alle deres placeringer, eller det er kun sådan, de gør det. Men disse slutpunkter er præcis, som... peger på steder, hvor trafikken er stor. Der er intet galt med at forhindre dine brugere i at gennemse til Streaming eller streaming af kattevideoer, men du skal ikke behandle din virksomheds forretningskritiske programtrafik på samme måde.
- Hvis **DNS ikke** er tilfreds, er der ingen, der er tilfreds: Det bedste designede netværk kan være hamlende af dårlig DNS, uanset om det er ved at rekursere anmodninger til servere i andre områder af verden eller ved hjælp af din internetudbyders DNS-servere eller andre offentlige DNS-servere, der cachelagrer DNS-løsningsoplysninger.
- **Bare fordi det er sådan,** du plejede at gøre det, betyder det ikke, at det er sådan, du skal gøre det nu: Teknologi ændres konstant, Office 365 er ingen undtagelse. Hvis du anvender sikkerhedsforanstaltninger, der er udviklet og implementeret til lokale tjenester eller til at kontrollere websurfing, vil det ikke give det samme sikkerhedsniveau og kan have en betydelig negativ indvirkning på ydeevnen.
- **Office 365 blev bygget til at blive åbnet via internettet**: Det var det i en nøddeskal. Uanset hvad du vil gøre mellem dine brugere og kanten, går trafikken stadig over internettet, når den forlader dit netværk, og før den bliver på vores. Selvom du bruger Azure ExpressRoute til at dirigere noget latenstidsfølsom trafik fra dit netværk direkte til vores, er internetforbindelse absolut påkrævet. Acceptér den. Lad være med at tænke over det.

## <a name="where-bad-choices-are-often-made"></a>Hvor der ofte foretages dårlige valg

Selvom der er masser af steder, hvor der foretages dårlige beslutninger i sikkerhedsmæssige navn, er det disse, jeg oftest støder på med kunder. Mange kundesamtaler involverer alle disse på én gang.

### <a name="insufficient-resources-at-the-edge"></a>Utilstrækkelige ressourcer ved kanten

Meget få kunder implementerer greenfield-miljøer, og de har mange års erfaring med, hvordan deres brugere arbejder, og hvordan deres internet udgangspunkt er. Uanset om kunderne har proxyservere eller tillader direkte adgang og blot NAT-udgående trafik, har de gjort det i flere år, og de behøver ikke overveje, hvor meget mere de vil begynde at bevæge sig gennem deres kant, når de flytter traditionelt interne programmer ud til skyen.

Båndbredden er altid et problem, men NAT-enheder har måske ikke nok hestekraft til at håndtere den øgede belastning og kan starte med at lukke forbindelserne for at frigøre ressourcer. Det meste af klientsoftwaren, der opretter forbindelse til Office 365, forventer permanente forbindelser, og en bruger, der fuldt ud Office 365 kan have 32 eller flere samtidige forbindelser. Hvis NAT-enheden slippes af sig selv, svarer disse apps muligvis ikke, når de forsøger at bruge de forbindelser, der ikke længere findes der. Når de giver op og forsøger at oprette nye forbindelser, belaster de netværksudstyret endnu mere.

### <a name="localized-breakout"></a>Lokaliseret breakout

Alt andet på denne liste kommer ned til én ting – komme væk fra dit netværk og over på vores så hurtigt som muligt. Tilbagehasing af dine brugeres trafik til et centralt udgangspunkt, især når dette udgangspunkt er i et andet område end brugerne er i, introducerer unødvendig ventetid og påvirker både klientoplevelsen og downloadhastigheder. Microsoft har tilstedeværelsespunkter over hele verden med front ends for alle vores tjenester og peering etableret med praktisk talt alle større internetudbydere, så routing af dine brugeres trafik lokalt sikrer, at den hurtigt kommer ind i vores netværk med minimumventetid.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>TRAFIK til DNS-opløsning skal følge internetstien

Selvfølgelig skal en klient bruge DNS for at finde et slutpunkt. Microsofts DNS-servere evaluerer kilden til DNS-anmodninger for at sikre, at vi returnerer det svar, der i internetvilkårene er tættest på anmodningens kilde. Sørg for, at din DNS er konfigureret, så anmodninger om navneløsning går fra den samme sti som dine brugeres trafik, hvis du ikke giver dem lokale udgangspunkter, men til et slutpunkt i et andet område. Det betyder, at lokale DNS-servere "gå til rod" i stedet for videresendelse til DNS-servere i fjerndatacentre. Og pas på offentlige og private DNS-tjenester, som kan cachelagre resultater fra én del af verden og betjene dem på anmodninger fra andre dele af verden.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Til proxy eller ikke til proxy, det er spørgsmålet

En af de første ting, du skal overveje, er, om proxybrugeres forbindelser til Office 365. Den her er nem; proxy ikke. Office 365 tilgås via internettet, men det er ikke internettet. Det er en udvidelse af dine kernetjenester og skal behandles som sådan. Alt, hvad du vil have en proxy til at gøre, f.eks DLP eller antimalware eller indholdsinspektion, er allerede tilgængeligt for dig i tjenesten og kan bruges på skala og uden at skulle revne TLS-krypterede forbindelser. Men hvis du virkelig vil proxytrafik, som du ikke ellers kan styre, [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) skal du være opmærksom på vores vejledning på og kategorierne for trafik på [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md). Vi har tre kategorier af trafik til Office 365. Optimer og Tillad skal virkelig gå direkte og tilsidesætte din proxy. Standardværdien kan være proxy. Detaljerne er i disse dokumenter ... kan du læse dem.

De fleste kunder, der hver især bruger proxyen, og de rent faktisk ser på, hvad de laver, indser, at når klienten anmoder om HTTP CONNECT til proxyen, er proxyen nu blot en dyrere ekstra router. De protokoller, der er i brug, f.eks. MAPI og RTC, er ikke en gang protokoller, som web-proxyer forstår, så selv med TLS-revning får du ikke rigtig ekstra sikkerhed. Du *får* ekstra ventetid. Få [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) mere at vide om dette, herunder kategorierne Optimer, Tillad og Standard for Microsoft 365 trafik.

Endelig bør du overveje den overordnede indvirkning for proxyen og dens tilsvarende svar for at håndtere den pågældende påvirkning. Efterhånden som der oprettes flere og flere forbindelser via proxyen, kan det reducere TCP-skalafaktoren, så den ikke behøver at buffere så meget trafik. Jeg har set kunder, hvor deres proxyer var så overbebyrdede, at de brugte en skalafaktor på 0. Da Skalafaktor er en eksponentialværdi, og vi vil bruge 8, har hver reduktion i skaleringsfaktorværdien en enorm negativ påvirkning på overførselshastigheden.

TLS-inspektion betyder SIKKERHED! Men det er ikke rigtigt! Mange kunder med proxyer vil bruge dem til at undersøge al trafik, og det betyder, at TLS "afbryd og undersøg". Når du gør det for et websted, der tilgås via HTTPS (uagtet beskyttelse af personlige oplysninger), kan din proxy være nødt til at gøre det i 10 eller endda 20 samtidige strømme i et par hundrede millisekunder. Hvis der er en stor download eller måske en video involveret, kan en eller flere af disse forbindelser vare meget længere, men på det hele taget etablerer, overfører og lukker de fleste af disse forbindelser meget hurtigt. Når du udfører pause og undersøger noget, betyder det, at proxyen skal gøre det dobbelte af arbejdet. For hver forbindelse fra klienten til proxyen skal proxyen også oprette en separat forbindelse tilbage til slutpunktet. Så 1 bliver 2, 2 bliver 4, 32 bliver 64 ... se hvor jeg skal hen? Du har sandsynligvis tilpasset din proxyløsning helt fint til typisk websurfing, men når du forsøger at gøre det samme for klientforbindelser til Office 365, kan antallet af samtidige, lange forbindelser være ordrer af større størrelse end den størrelse, du har brug for.

### <a name="streaming-isnt-important-except-that-it-is"></a>Streaming er ikke vigtigt, bortset fra at *det er*

De eneste tjenester i Office 365, der bruger UDP, Skype (snart skal udgå) og Microsoft Teams. Teams bruger UDP til streaming af trafik, herunder lyd, video og præsentationsdeling. Streaming af trafik er live, f.eks når du har et onlinemøde med tale, video og præsentation af sæt eller udførelse af demoer. Disse bruger UDP, fordi hvis pakker slippes eller modtages af ordren, er det praktisk talt ikke synligt for brugeren, og strømmen kan bare fortsætte.

Når du ikke tillader udgående UDP-trafik fra klienter til tjenesten, kan de falde tilbage til at bruge TCP. Men hvis en TCP-pakke slippes *, stopper* alt, indtil Retransmission Timeout (RTO) udløber, og den manglende pakke kan gentransmitteres. Hvis en pakke ankommer af ordren, stopper alt, indtil de andre pakker ankommer og kan samles igen i rækkefølge. Begge fører til mærkbare fejl i lyden (husk Max Headroom?) og video (klikkede du på noget... oh, there it is) og føre til dårlig ydeevne og en dårlig brugeroplevelse. Kan du huske, hvad jeg placerede ovenfor om proxyer? Når du gennemtvinger en Teams til at bruge en proxy, gennemtvinger du, at den bruger TCP. Nu forårsager du en negativ påvirkning af ydeevnen to gange.

### <a name="split-tunneling-may-seem-scary"></a>Opdelte dele kan virke skræmmende

Men det er den ikke. Alle forbindelser til Office 365 er over TLS. Vi har tilbudt TLS 1.2 i lang tid og deaktiverer snart ældre versioner, fordi ældre klienter stadig bruger dem, og det er en risiko.

Hvis du gennemtvinger en TLS-forbindelse, eller 32 af dem, for at gå over et VPN, før de derefter går til tjenesten, tilføjer det ikke sikkerhed. Det tilføjer ventetid og reducerer den samlede overførselshastighed. I nogle VPN-løsninger tvinger det endda UDP til at tcp, hvilket igen vil have en meget negativ indvirkning på streamingtrafik. Og medmindre du udfører TLS-inspektion, er der ingen på hovedet, alt sammen på hovedet. Et meget almindeligt tema blandt kunderne, nu hvor de fleste af deres medarbejdere arbejder eksternt, er, at de oplever betydelige båndbredde- og ydeevnepåvirkninger ved at få alle deres brugere til at oprette forbindelse ved hjælp af et VPN, i stedet for at konfigurere opdelte netværksnetværk for at få adgang til kategorien Optimer [Office 365 slutpunkter](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

Det er en nem løsning at opdele opdele, og det er en løsning, du skal gøre. Du kan få mere at vide ved at gennemse [Optimer Office 365 forbindelse for eksterne brugere, der bruger VPN-opdelingsopdelning](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Fortidens synd

Mange gange kommer årsagen til, at der foretages dårlige valg, fra en kombination af (1) ikke at vide, hvordan tjenesten virker, (2) at forsøge at overholde virksomhedspolitikker, der blev skrevet, før de blev taget i brug i skyen, og (3) sikkerhedsteams, som muligvis ikke uden problemer skal overbevises om, at der er mere end én måde at opnå deres mål på. Forhåbentligt hjælper ovenstående og nedenstående links med det første. Ledelsens sponsorat kan være påkrævet for at komme forbi det andet. At adressere sikkerhedspolitikkers mål i stedet for deres metoder hjælper med det tredje. Fra betinget adgang til redigering af indhold, DLP til beskyttelse af oplysninger, validering af slutpunkt til nul dages trusler – et hvilket som helst slutmål med en passende sikkerhedspolitik kan opnås med det, der er tilgængeligt i Office 365, og uden afhængighed af lokale netværksudstyr, gennemtvungne VPN-sikkerhedsnet og TLS pause og undersøgelse.

Andre gange kan hardware, der blev tilpasset og købt, før organisationen begyndte at flytte til skyen, ganske enkelt ikke skaleres op til at håndtere de nye trafikmønstre og -belastninger. Hvis du virkelig skal dirigere al trafik gennem et enkelt udgangspunkt og/eller proxy det, skal du være forberedt til at opgradere netværksudstyr og båndbredde tilsvarende. Overvåg anvendelsen omhyggeligt på begge, da oplevelsen ikke bliver langsommere, når flere brugere kommer i gang. Alt går fint, indtil overfyldningspunktet nås, så det går ud over alle.

## <a name="exceptions-to-the-rules"></a>Undtagelser til reglerne

Hvis din organisation kræver [lejerbegrænsninger, skal](/azure/active-directory/manage-apps/tenant-restrictions) du bruge en proxy med TLS-pause og undersøge for at gennemtvinge noget trafik gennem proxyen, men du behøver ikke at gennemtvinge al trafik gennem den.  Det er ikke alt eller intet andet, så vær opmærksom på, hvad der skal ændres af proxyen.

Hvis du vil tillade opdeling af inddelning, men også bruge en proxy til generel webtrafik, skal du sikre dig, at PAC-filen definerer, hvad der skal gå direkte, samt hvordan du definerer interessant trafik for, hvad der går gennem VPN-klientpalelen. Vi tilbyder PAC-eksempelfiler, [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) der gør det nemmere at administrere.

## <a name="conclusion"></a>Konklusion

Titusindvis af organisationer, herunder næsten alle Fortune 500, bruger hver Office 365 til deres missionskritiske funktioner. De gør det sikkert, og de gør det via internettet.

Uanset hvilke sikkerhedsmål du har i spil, er der måder at opnå dem på, der ikke kræver VPN-forbindelser, proxyservere, pause og undersøgelse af TLS eller centraliseret internetud udgangspunkt for at få dine brugeres trafik fra dit netværk og videre til vores så hurtigt som muligt, hvilket giver den bedste ydeevne, uanset om dit netværk er virksomhedens hovedkontor,  et fjernkontor eller en bruger, der arbejder hjemmefra. Vores vejledning er baseret på, hvordan Office 365 er opbygget, og for at sikre en sikker og effektiv brugeroplevelse.

## <a name="further-reading"></a>Yderligere læsning

[Principperne Office 365 for netværksforbindelse](../enterprise/microsoft-365-network-connectivity-principles.md)

[Office 365-URL-adresser og IP-adresseintervaller](../enterprise/urls-and-ip-address-ranges.md)

[Administrere Office 365 slutpunkter](../enterprise/managing-office-365-endpoints.md)

[Office 365 IP-adresse og URL-webtjeneste](../enterprise/microsoft-365-ip-web-service.md)

[Vurdering Office 365 netværksforbindelsen](../enterprise/assessing-network-connectivity.md)

[Office 365 netværk og justering af ydeevnen](../enterprise/network-planning-and-performance.md)

[Vurdering Office 365 netværksforbindelsen](../enterprise/assessing-network-connectivity.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](../enterprise/performance-tuning-using-baselines-and-history.md)

[Fejlfinding af ydeevne i forbindelse med planen for Office 365](../enterprise/performance-troubleshooting-plan.md)

[Content Delivery Networks](../enterprise/content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://connectivity.office.com/)

[Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Networking-blog](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 forbindelse for eksterne brugere ved hjælp af VPN-opdelt netværksforbindelse](../enterprise/microsoft-365-vpn-split-tunnel.md)
