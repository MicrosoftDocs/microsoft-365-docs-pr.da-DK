---
title: Implementering af ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Få mere at vide om, hvordan du implementerer ExpressRoute for Office 365, hvilket giver en alternativ routingsti til mange Office 365-tjenester, der er på internettet.
ms.openlocfilehash: d577a30d97630b32fa080c9d17620b429562c5df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090357"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementering af ExpressRoute for Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

ExpressRoute til Office 365 giver en alternativ routingsti til mange tjenester med adgang til internettet Office 365. Arkitekturen i ExpressRoute for Office 365 er baseret på annoncering af offentlige IP-præfikser for Office 365 tjenester, der allerede er tilgængelige via internettet, i dine klargjorte ExpressRoute-kredsløb for efterfølgende videredistribution af disse IP-præfikser til dit netværk. Med ExpressRoute aktiverer du effektivt flere forskellige routingstier via internettet og via ExpressRoute for mange Office 365 tjenester. Denne routingtilstand på netværket kan udgøre en væsentlig ændring af den måde, den interne netværkstopologi er designet på.
  
 **Status:** Komplet vejledning v2
  
Du skal omhyggeligt planlægge din ExpressRoute for Office 365 implementering for at imødekomme netværkskompleksiteten ved at have routing tilgængelig via både et dedikeret kredsløb med ruter, der sprøjtes ind i dit kernenetværk og internettet. Hvis du og dit team ikke udfører den detaljerede planlægning og test i denne vejledning, er der en høj risiko for, at du oplever periodiske eller samlede tab af forbindelse til Office 365 tjenester, når ExpressRoute-kredsløbet er aktiveret.
  
Hvis du vil have en vellykket implementering, skal du analysere dine infrastrukturkrav, gennemgå detaljeret netværksvurdering og -design, planlægge udrulningen omhyggeligt på en faseindtrudført og kontrolleret måde og oprette en detaljeret validerings- og testplan. I et stort distribueret miljø er det ikke ualmindeligt, at implementeringer strækker sig over flere måneder. Denne vejledning er designet til at hjælpe dig med at planlægge fremad.
  
Store vellykkede udrulninger kan tage seks måneder at planlægge og omfatter ofte teammedlemmer fra mange områder i organisationen, herunder netværk, firewall- og proxyserveradministratorer, Office 365 administratorer, sikkerhed, slutbrugersupport, projektstyring og ledelsessponsorater. Din investering i planlægningsprocessen reducerer sandsynligheden for, at du oplever udrulningsfejl, hvilket resulterer i nedetid eller kompleks og dyr fejlfinding.
  
Vi forventer, at følgende forudsætninger er fuldført, før denne implementeringsvejledning startes.
  
1. Du har fuldført en netværksvurdering for at afgøre, om ExpressRoute anbefales og godkendes.

2. Du har valgt en ExpressRoute-netværkstjenesteudbyder. Find oplysninger om [ExpressRoute-partnere og peeringplaceringer](/azure/expressroute/expressroute-locations).

3. Du har allerede læst og forstå dokumentationen til [ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) , og dit interne netværk kan opfylde ExpressRoute-forudsætninger fra ende til anden.

4. Dit team har læst al offentlig vejledning og dokumentation på [https://aka.ms/expressrouteoffice365](./azure-expressroute.md), [https://aka.ms/ert](https://aka.ms/ert)og set [Azure ExpressRoute for Office 365 Training-serien](https://channel9.msdn.com/series/aer) på Channel 9 for at få en forståelse af vigtige tekniske detaljer, herunder:

      - Internetafhængighederne for SaaS-tjenester.

      - Sådan undgår du asymmetriske ruter og håndterer kompleks routing.

      - Sådan inkorporerer du kontrolelementer på perimetersikkerhed, tilgængelighed og programniveau.

## <a name="begin-by-gathering-requirements"></a>Begynd med at indsamle krav
<a name="requirements"> </a>

Start med at bestemme, hvilke funktioner og tjenester du planlægger at anvende i din organisation. Du skal afgøre, hvilke funktioner i de forskellige Office 365 tjenester der skal bruges, og hvilke placeringer på netværket der skal være vært for personer, der bruger disse funktioner. Med kataloget over scenarier skal du tilføje de netværksattributter, som hvert af disse scenarier kræver. f.eks. indgående og udgående netværkstrafikflow, og om de Office 365 slutpunkter er tilgængelige via ExpressRoute eller ej.
  
Sådan indsamler du organisationens krav:
  
- Katalogiser den indgående og udgående netværkstrafik for de Office 365 tjenester, din organisation bruger. Se Office 365 URL-adresser og siden MED IP-adresseområder for at få en beskrivelse af flow, som forskellige Office 365 scenarier kræver.

- Indsaml dokumentation for eksisterende netværkstopologi, der viser detaljer om din interne WAN-backbone og -topologi, tilslutning af satellitwebsteder, sidste kilometers brugerforbindelse, routing til udgående netværksperimeterpunkter og proxytjenester.

  - Identificer indgående tjenesteslutpunkter i de netværksdiagrammer, som Office 365 og andre Microsoft-tjenester opretter forbindelse til, og vis både internet- og foreslåede ExpressRoute-forbindelsesstier.

  - Identificer alle geografiske brugerplaceringer og WAN-forbindelser mellem placeringer, sammen med hvilke placeringer der i øjeblikket har en udgående forbindelse til internettet, og hvilke placeringer der foreslås til at have en udgående forbindelse til en ExpressRoute-peeringplacering.

  - Identificer alle edge-enheder, f.eks. proxyer, firewalls osv., og katalogiser deres relation til flow, der går over internettet og ExpressRoute.

  - Dokumentér, om slutbrugerne skal have adgang til Office 365 tjenester via Direct Routing eller indirekte programproxy for både internet- og ExpressRoute-flow.

- Føj lejerens placering og møde mig-placeringer til netværksdiagrammet.

- Estimer den forventede og observerede netværksydeevne og ventetid fra overordnede brugerplaceringer til Office 365. Vær opmærksom på, at Office 365 er et globalt og distribueret sæt tjenester, og at brugerne opretter forbindelse til placeringer, der kan være forskellige fra placeringen af deres lejer. Derfor anbefales det at måle og optimere ventetiden mellem brugeren og den nærmeste kant af Microsofts globale netværk via ExpressRoute og internetforbindelser. Du kan bruge dine resultater fra netværksvurderingen til at hjælpe med denne opgave.

- Angiv virksomhedens krav til netværkssikkerhed og høj tilgængelighed, der skal opfyldes med den nye ExpressRoute-forbindelse. Hvordan kan brugerne f.eks. fortsætte med at få adgang til Office 365 i tilfælde af, at der opstår fejl i udgående data eller ExpressRoute-kredsløb.

- Dokument, som indgående og udgående Office 365 netværksflow bruger internetstien, og som bruger ExpressRoute. Specifikationerne for dine brugeres geografiske placeringer og oplysninger om din lokale netværkstopologi kan kræve, at planen er forskellig fra én brugerplacering til en anden.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Katalogér din udgående og indgående netværkstrafik
<a name="trafficCatalog"> </a>

For at minimere distributionen og andre netværkskompleksiteter anbefaler vi, at du kun bruger ExpressRoute til Office 365 for de netværkstrafikflow, der skal bruges til at oprette en dedikeret forbindelse på grund af lovmæssige krav eller som følge af netværksvurderingen. Derudover anbefaler vi, at du faser omfanget af ExpressRoute-routing og tilgang til udgående og indgående netværkstrafikflow som forskellige og særskilte faser i implementeringsprojektet. Udrul ExpressRoute til Office 365 for udgående netværkstrafikflow, der kun er igangsat af brugere, og lad indgående netværkstrafikflow forblive på tværs af internettet, kan hjælpe med at styre stigningen i topologisk kompleksitet og risici ved at introducere yderligere asymmetriske routingmuligheder.
  
Dit katalog over netværkstrafik skal indeholde lister over alle de indgående og udgående netværksforbindelser, du har mellem dit lokale netværk og Microsoft.
  
- Udgående netværkstrafikflows er alle scenarier, hvor der startes en forbindelse fra dit lokale miljø, f.eks. fra interne klienter eller servere, med en destination for Microsoft-tjenester. Disse forbindelser kan være direkte til Office 365 eller indirekte, f.eks. når forbindelsen går gennem proxyservere, firewalls eller andre netværksenheder på stien til Office 365.

- Indgående netværkstrafikflow er scenarier, hvor der startes en forbindelse fra Microsoft-cloudmiljøet til en vært i det lokale miljø. Disse forbindelser skal typisk gå gennem firewall og anden sikkerhedsinfrastruktur, som kundens sikkerhedspolitik kræver til eksternt opståede flow.

Læs afsnittet **Sikring af rutesymmetri** i artiklen [Routing med ExpressRoute for Office 365 for](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) at finde ud af, hvilke tjenester der sender indgående trafik, og søg efter den kolonne, der er markeret **med ExpressRoute, for Office 365** i artiklen [reference til Office 365 slutpunkter](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) for at bestemme resten af forbindelsesoplysningerne.
  
For hver tjeneste, der kræver en udgående forbindelse, skal du beskrive den planlagte forbindelse til tjenesten, herunder netværksrouting, proxykonfiguration, pakkekontrol og båndbreddebehov.
  
For hver tjeneste, der kræver en indgående forbindelse, skal du bruge nogle yderligere oplysninger. Servere i Microsoft-clouden opretter forbindelser til dit lokale netværk. Hvis du vil sikre dig, at forbindelserne er oprettet korrekt, skal du beskrive alle aspekter af denne forbindelse, herunder; de offentlige DNS-poster for de tjenester, der accepterer disse indgående forbindelser, de CIDR-formaterede IPv4 IP-adresser, som ISP-udstyr er involveret i, og hvordan indgående NAT eller kilde-NAT håndteres for disse forbindelser.
  
Indgående forbindelser skal gennemses, uanset om de opretter forbindelse via internettet eller ExpressRoute, for at sikre, at asymmetrisk routing ikke er blevet introduceret. I nogle tilfælde kan det være nødvendigt, at andre Microsoft- og ikke-Microsoft-tjenester har adgang til slutpunkter i det lokale miljø, som Office 365 tjenester starter indgående forbindelser til. Det er altafgørende, at aktivering af ExpressRoute-routing til disse tjenester til Office 365 formål ikke ødelægger andre scenarier. I mange tilfælde skal kunder muligvis implementere specifikke ændringer af deres interne netværk, f.eks. kildebaseret NAT, for at sikre, at indgående flow fra Microsoft forbliver symmetriske, når ExpressRoute er aktiveret.
  
Her er et eksempel på det påkrævede detaljeniveau. I dette tilfælde dirigerer Exchange Hybrid til systemet i det lokale miljø via ExpressRoute. 

|Forbindelsesegenskab   |Værdi  |
|----------|-----------|
|**Netværkstrafikretning** <br/> |Indgående  <br/> |
|**Tjeneste** <br/> |Exchange Hybrid  <br/> |
|**Offentligt Office 365 slutpunkt (kilde)** <br/> |Exchange Online (IP-adresser)  <br/> |
|**Offentligt slutpunkt i det lokale miljø (destination)** <br/> |5.5.5.5  <br/> |
|**Offentlig (Internet) DNS-post** <br/> |Autodiscover.contoso.com  <br/> |
|**Bruges dette slutpunkt i det lokale miljø af andre (ikke-Office 365) Microsoft-tjenester** <br/> |Nej  <br/> |
|**Vil dette slutpunkt i det lokale miljø blive brugt af brugere/systemer på internettet** <br/> |Ja  <br/> |
|**Interne systemer, der er publiceret via offentlige slutpunkter** <br/> |Exchange Server klientadgangsrolle (i det lokale miljø) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**IP-annoncering af det offentlige slutpunkt** <br/> |**Til internettet**: 5.5.0.0/16 **til ExpressRoute**: 5.5.5.0/24  <br/> |
|**Sikkerheds-/perimeterkontrolelementer** <br/> |**Internetsti**: DeviceID_002  **ExpressRoute-sti**: DeviceID_003  <br/> |
|**Høj tilgængelighed** <br/> |Active/Active på tværs af 2 geo-redundante/ExpressRoute-kredsløb – Chicago og Dallas  <br/> |
|**Stisymmetrikontrolelement** <br/> |**Metode**: Kilde **NAT-internetsti**: Kilde NAT-indgående forbindelser til 192.168.5.5 **ExpressRoute-sti**: Kilde NAT-forbindelser til 192.168.1.0 (Chicago) og 192.168.2.0 (Dallas)  <br/> |

Her er et eksempel på en tjeneste, der kun er udgående:

|**Forbindelsesegenskab**|**Værdi**|
|----------|-----------|
|**Netværkstrafikretning** <br/> |Udgående  <br/> |
|**Tjeneste** <br/> |SharePoint Online  <br/> |
|**Slutpunkt i det lokale miljø (kilde)** <br/> |Brugerarbejdsstation  <br/> |
|**Offentligt Office 365 slutpunkt (destination)** <br/> |SharePoint Online (IP-adresser)  <br/> |
|**Offentlig (Internet) DNS-post** <br/> |\*.sharepoint.com (og flere FQDN'er)  <br/> |
|**CDN henvisninger** <br/> |cdn.sharepointonline.com (og flere FQDN'er) – IP-adresser, der vedligeholdes af CDN udbydere)  <br/> |
|**IP-annoncering og NAT i brug** <br/> |**Internetsti/kilde-NAT**: 1.1.1.0/24  <br/> **ExpressRoute path/Source NAT**: 1.1.2.0/24 (Chicago) og 1.1.3.0/24 (Dallas)  <br/> |
|**Forbindelsesmetode** <br/> |**Internet**: via layer 7-proxy (.pac-fil)  <br/> **ExpressRoute**: direkte routing (ingen proxy)  <br/> |
|**Sikkerheds-/perimeterkontrolelementer** <br/> |**Internetsti**: DeviceID_002  <br/> **Sti til ExpressRoute**: DeviceID_003  <br/> |
|**Høj tilgængelighed** <br/> |**Internetsti**: Redundant internetudgående  <br/> **ExpressRoute-sti**: Aktiv/aktiv distribution af "varme kartofler" på tværs af to geo-redundante ExpressRoute-kredsløb – Chicago og Dallas  <br/> |
|**Stisymmetrikontrolelement** <br/> |**Metode**: Kilde-NAT for alle forbindelser  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Dit design af netværkstopologi med regional forbindelse
<a name="topology"> </a>

Når du har forstået tjenesterne og deres tilknyttede netværkstrafikflow, kan du oprette et netværksdiagram, der inkorporerer disse nye forbindelseskrav og illustrerer de ændringer, du foretager for at bruge ExpressRoute til Office 365. Diagrammet skal indeholde:
  
1. Alle brugerplaceringer, hvor der er adgang til Office 365 og andre tjenester.

2. Alle internet- og ExpressRoute-udgående punkter.

3. Alle udgående og indgående enheder, der administrerer forbindelse ind og ud af netværket, herunder routere, firewalls, programproxyservere og registrering/forebyggelse af indtrængen.

4. Interne destinationer for al indgående trafik, f.eks. interne ADFS-servere, der accepterer forbindelser fra ADFS-webprogramproxyservere.

5. Katalog over alle IP-undernet, der vil blive annonceret

6. Identificer hver placering, hvor personer skal have adgang Office 365 fra, og angiv de mødeplaceringer, der skal bruges til ExpressRoute.

7. Placeringer og dele af din interne netværkstopologi, hvor Microsofts IP-præfikser, der er lært fra ExpressRoute, accepteres, filtreres og overføres til.

8. Netværkstopologien skal illustrere den geografiske placering af hvert netværkssegment, og hvordan det opretter forbindelse til Microsoft-netværket via ExpressRoute og/eller internettet.

Nedenstående diagram viser hver placering, hvor personer skal bruge Office 365 fra sammen med de indgående og udgående routing-reklamer til Office 365.
  
![ExpressRoute regional geografisk møde-mig.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Ved udgående trafik Office 365 personerne på en af tre måder:
  
1. Gennem et møde-mig sted i Nordamerika for folk i Californien.

2. Gennem et møde-mig sted i Hong Kong for folket i Hongkong.

3. Via internettet i Bangladesh, hvor der er færre mennesker, og hvor der ikke er klargjort noget ExpressRoute-kredsløb.

![Udgående forbindelser til områdediagram.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
På samme måde returnerer den indgående netværkstrafik fra Office 365 på en af tre måder:
  
1. Gennem et møde-mig sted i Nordamerika for folk i Californien.

2. Gennem et møde-mig sted i Hong Kong for folket i Hongkong.

3. Via internettet i Bangladesh, hvor der er færre mennesker, og hvor der ikke er klargjort noget ExpressRoute-kredsløb.

![Indgående forbindelser til områdediagram.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Fastlæg den relevante møde-mig-placering

Valget af møde-mig-placeringer, som er den fysiske placering, hvor dit ExpressRoute-kredsløb forbinder dit netværk til Microsoft-netværket, påvirkes af de placeringer, hvor personer får adgang til Office 365 fra. Som et SaaS-tilbud fungerer Office 365 ikke under den regionale IaaS- eller PaaS-model på samme måde som Azure. Office 365 er i stedet et distribueret sæt samarbejdstjenester, hvor brugerne muligvis skal oprette forbindelse til slutpunkter på tværs af flere datacentre og områder, som muligvis ikke nødvendigvis befinder sig på den samme placering eller det samme område, som brugerens lejer hostes på.
  
Det betyder, at den vigtigste overvejelse, du skal gøre, når du vælger møde-mig-placeringer for ExpressRoute for Office 365 er det sted, hvor personerne i din organisation opretter forbindelse fra. Den generelle anbefaling om optimal Office 365 forbindelse er at implementere routing, så brugeranmodninger om at Office 365 tjenester overdrages til Microsoft-netværket via den korteste netværkssti, og det kaldes også ofte "varm kartoffel"-routing. Hvis de fleste af de Office 365 brugere f.eks. befinder sig et eller to steder, vil det optimale design blive oprettet, hvis du vælger møde-mig-placeringer, der ligger tættest på disse brugeres placering. Hvis din virksomhed har store brugerpopulationer i mange forskellige områder, kan du overveje at have flere ExpressRoute-kredsløb og møde-mig-placeringer. For nogle af dine brugerplaceringer er den korteste/mest optimale sti til Microsoft-netværk og Office 365 muligvis ikke via dine interne WAN- og ExpressRoute-mødepunkter, men via internettet.
  
Der er ofte flere møde-mig-placeringer, der kan vælges i et område med relativ nærhed til dine brugere. Udfyld følgende tabel for at vejlede dig i dine beslutninger.

**Planlagte ExpressRoute-mødeplaceringer i Californien og New York**

|Placering  <br/> |Antal personer  <br/> |Forventet ventetid for Microsoft-netværk via internetudgående data  <br/> |Forventet ventetid for Microsoft-netværk via ExpressRoute  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |Ca. 15 ms  <br/> |Ca. 10 ms (via Silicon Valley)  <br/> |
|Washington DC  <br/> |15,000  <br/> |Ca. 20 ms  <br/> |Ca. 10 ms (via New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |Ca. 15 ms  <br/> |Ca. 40 ms (via New York)  <br/> |

Når den globale netværksarkitektur, der viser området Office 365, Udbyderen af ExpressRoute-netværk opfylder mig,og antallet af personer efter placering er blevet udviklet, kan den bruges til at identificere, om der kan foretages optimeringer. Det kan også vise globale hårnål netværksforbindelser, hvor trafik ruter til en fjern placering for at få møde-mig placering. Hvis der opdages en hårnål på det globale netværk, skal den afhjælpes, før den fortsætter. Find en anden møde-mig-placering, eller brug selektive internet udgangspunkter for at undgå hårnålen.
  
Det første diagram viser et eksempel på en kunde med to fysiske placeringer i Nordamerika. Du kan se oplysninger om kontorplaceringer, Office 365 lejerplaceringer og flere valgmuligheder for Møde-mig-placeringer i ExpressRoute. I dette eksempel har kunden valgt mødeplaceringen baseret på to principper i rækkefølge:
  
1. Tættest på personerne i organisationen.

2. Tættest på et Microsoft-datacenter, hvor Office 365 hostes.

![ExpressRoute Geografisk møde-mig i USA.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Hvis man udvider dette koncept lidt yderligere, viser det andet diagram et eksempel på en flernational kunde, der står over for lignende oplysninger og beslutningstagning. Denne kunde har et lille kontor i Bangladesh med kun et lille team på ti personer, der fokuserer på at øge deres fodaftryk i regionen. Der er en møde-mig-placering i Chennai og et Microsoft-datacenter med Office 365 hostet i Chennai, så det ville give mening at mødes på en placering, men for ti personer er udgifterne til det ekstra kredsløb besværlige. Når du ser på dit netværk, skal du afgøre, om ventetiden for at sende netværkstrafikken på tværs af netværket er mere effektiv end at bruge kapitalen til at erhverve et andet ExpressRoute-kredsløb.
  
Alternativt kan de ti personer i Bangladesh opleve bedre ydeevne med deres netværkstrafik sendt over internettet til Microsoft-netværket, end de ville routing på deres interne netværk, som vi viste i de indledende diagrammer og gengivet nedenfor.
  
![Udgående forbindelser til områdediagram.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Opret din ExpressRoute til Office 365 implementeringsplan
<a name="implementation"> </a>

Din implementeringsplan bør omfatte både de tekniske detaljer om konfiguration af ExpressRoute og oplysninger om konfiguration af al anden infrastruktur på netværket, f.eks. følgende.
  
- Planlæg, hvilke tjenester der skal opdeles mellem ExpressRoute og Internet.

- Planlæg båndbredde, sikkerhed, høj tilgængelighed og failover.

- Design indgående og udgående routing, herunder korrekt optimering af routingstier for forskellige placeringer

- Beslut, hvor langt ExpressRoute-ruter skal annonceres i dit netværk, og hvad er mekanismen for klienter til at vælge internet- eller ExpressRoute-sti. f.eks. direkte routing eller programproxy.

- Planlæg ændringer af DNS-poster, herunder poster [i Sender Policy Framework](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) .

- Planlæg NAT-strategi, herunder udgående og indgående kilde NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planlæg distributionen med både internet- og ExpressRoute-netværksstier
<a name="paths"> </a>

- I forbindelse med den indledende udrulning anbefales det, at alle indgående tjenester, f.eks. indgående mail eller hybridforbindelse, bruger internettet.

- Planlæg lan-routing for slutbrugerklienten, f.eks [. konfiguration af en PAC/WPAD-fil](./managing-office-365-endpoints.md), standardrute, proxyservere og BGP-rutereklamer.

- Planlæg perimeterrouting, herunder proxyservere, firewalls og proxyer i cloudmiljøet.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planlæg din båndbredde, sikkerhed, høj tilgængelighed og failover
<a name="availability"> </a>

Opret en plan for båndbredde, der kræves for hver større Office 365 arbejdsbelastning. Estimer separat Exchange Online, SharePoint Online og Skype for Business Online båndbreddekrav. Du kan bruge de skønsberegninger, vi har angivet for Exchange Online og Skype for Business som udgangspunkt. Men en pilottest med et repræsentativt udsnit af brugerprofilerne og placeringerne er påkrævet for fuldt ud at forstå din organisations behov for båndbredde.
  
Føj den måde, sikkerhed håndteres på hvert internet- og ExpressRoute-udgående sted til din plan på. Husk alle ExpressRoute-forbindelser for at Office 365 bruge offentlig peering og skal stadig sikres i overensstemmelse med virksomhedens sikkerhedspolitikker for oprettelse af forbindelse til eksterne netværk.
  
Føj detaljer til din plan om, hvilke personer der påvirkes af, hvilken type afbrydelse, og hvordan disse personer på den nemmeste måde kan udføre deres arbejde i fuld kapacitet.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planlæg krav til båndbredde, herunder krav til Skype for Business for Jitter, Ventetid, Overbelastning og Headroom
  
Skype for Business Online har også specifikke ekstra netværkskrav, som beskrives i artiklen [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Læs afsnittet **Båndbreddeplanlægning for Azure ExpressRoute** i [Netværksplanlægning med ExpressRoute for at få Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Når du udfører en vurdering af båndbredden med dine pilotbrugere, kan du bruge vores vejledning; [Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planlæg krav til høj tilgængelighed
  
Opret en plan for høj tilgængelighed, der opfylder dine behov, og indarbejd dette i dit opdaterede netværkstopologidiagram. Læs afsnittet **Høj tilgængelighed og failover med Azure ExpressRoute** i [Netværksplanlægning med ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planlæg sikkerhedskrav til netværk
  
Opret en plan, der opfylder dine krav til netværkssikkerhed, og integrer den i dit opdaterede netværkstopologidiagram. Læs afsnittet **Anvendelse af sikkerhedskontroller på Azure ExpressRoute til Office 365 scenarier** i [Netværksplanlægning med ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Design forbindelse til udgående tjenester
<a name="outbound"> </a>

ExpressRoute til Office 365 har *udgående* netværkskrav, der kan være ukendte. De IP-adresser, der repræsenterer dine brugere og netværk for at Office 365 og fungere som kildeslutpunkter for udgående netværksforbindelser til Microsoft, skal specifikt følge de specifikke krav, der er beskrevet nedenfor.
  
1. Slutpunkterne skal være offentlige IP-adresser, der er registreret i dit firma, eller til luftfartsselskab, der leverer ExpressRoute-forbindelse til dig.

2. Slutpunkterne skal annonceres til Microsoft og valideres/accepteres af ExpressRoute.

3. Slutpunkterne må ikke annonceres på internettet med den samme eller flere foretrukne routingmetrikværdi.

4. Slutpunkterne må ikke bruges til at oprette forbindelse til Microsoft-tjenester, der ikke er konfigureret via ExpressRoute.

Hvis dit netværksdesign ikke opfylder disse krav, er der stor risiko for, at dine brugere oplever forbindelsesfejl i forbindelse med Office 365 og andre Microsoft-tjenester på grund af distribution af sort holing eller asymmetrisk routing. Dette sker, når anmodninger om Microsoft-tjenester distribueres via ExpressRoute, men svar distribueres tilbage via internettet eller omvendt, og svarene fjernes af tilstandsfulde netværksenheder, f.eks. firewalls.
  
Den mest almindelige metode, du kan bruge til at opfylde ovenstående krav, er at bruge kilde-NAT, enten implementeret som en del af dit netværk eller leveret af din ExpressRoute-udbyder. Kilde NAT giver dig mulighed for at udtrække detaljer og privat IP-adressering for dit internetnetværk fra ExpressRoute og; kombineret med korrekt IP-rute reklamer, give en nem mekanisme til at sikre sti symmetri. Hvis du bruger tilstandsfulde netværksenheder, der er specifikke for ExpressRoute-peeringplaceringer, skal du implementere separate NAT-grupper for hver ExpressRoute-peering for at sikre stisymmetri.
  
Læs mere om [ExpressRoute NAT-kravene](/azure/expressroute/expressroute-nat).
  
Føj ændringerne for den udgående forbindelse til netværkstopologidiagrammet.
  
### <a name="design-inbound-service-connectivity"></a>Design indgående tjenesteforbindelse
<a name="inbound"> </a>

De fleste Office 365 udrulninger i virksomheden forudsætter en form for indgående forbindelse fra Office 365 til tjenester i det lokale miljø, f.eks. til Exchange, SharePoint og Skype for Business hybridscenarier, migrering af postkasser og godkendelse ved hjælp af ADFS-infrastruktur. Når ExpressRoute du aktiverer en ekstra routingsti mellem dit lokale netværk og Microsoft til udgående forbindelser, kan disse indgående forbindelser utilsigtet blive påvirket af asymmetrisk routing, selvom du vil have, at disse flow fortsætter med at bruge internettet. Nogle få forholdsregler, der er beskrevet nedenfor, anbefales for at sikre, at der ikke er nogen indvirkning på internetbaserede indgående flow fra Office 365 til systemer i det lokale miljø.
  
Hvis du vil minimere risikoen for asymmetrisk routing for indgående netværkstrafikflow, skal alle indgående forbindelser bruge kilde-NAT, før de distribueres til segmenter af dit netværk, som har routingsynlighed i ExpressRoute. Hvis indgående forbindelser er tilladt til et netværkssegment med routingsynlighed i ExpressRoute uden kilde-NAT, vil anmodninger fra Office 365 komme ind fra internettet, men svaret, der går tilbage til Office 365 foretrækker expressRoute-netværksstien tilbage til Microsoft-netværket, hvilket medfører asymmetrisk routing.
  
Du kan overveje et af følgende implementeringsmønstre for at opfylde dette krav:
  
1. Udfør nat-kilden, før anmodninger dirigeres til dit interne netværk ved hjælp af netværksudstyr, f.eks. firewalls eller belastningsjusteringer på stien fra internettet til dine systemer i det lokale miljø.

2. Sørg for, at ExpressRoute-ruter ikke overføres til de netværkssegmenter, hvor indgående tjenester, f.eks. frontendservere eller omvendte proxysystemer, håndterer internetforbindelser.

Eksplicit at tage højde for disse scenarier i dit netværk og holde alle indgående netværkstrafikflow over internettet hjælper med at minimere udrulningen og driftsrisikoen for asymmetrisk routing.
  
Der kan være tilfælde, hvor du kan vælge at dirigere nogle indgående flow via ExpressRoute-forbindelser. I forbindelse med disse scenarier skal du tage følgende ekstra overvejelser i betragtning.
  
1. Office 365 kan kun målrette mod slutpunkter i det lokale miljø, der bruger offentlige IP-adresser. Det betyder, at selvom det indgående slutpunkt i det lokale miljø kun eksponeres for Office 365 via ExpressRoute, skal det stadig have en offentlig IP-adresse tilknyttet.

2. Alle DNS-navnefortsættelser, som Office 365 tjenester udfører for at løse slutpunkter i det lokale miljø, sker ved hjælp af offentlig DNS. Det betyder, at du skal registrere indgående tjenesteslutpunkters FQDN til IP-tilknytninger på internettet.

3. Hvis du vil modtage indgående netværksforbindelser via ExpressRoute, skal de offentlige IP-undernet for disse slutpunkter annonceres til Microsoft via ExpressRoute.

4. Evaluer omhyggeligt disse indgående netværkstrafikflow for at sikre, at der anvendes korrekt sikkerhed og netværkskontroller på dem i overensstemmelse med virksomhedens sikkerhed og netværkspolitikker.

5. Når dine indgående slutpunkter i det lokale miljø er annonceret til Microsoft via ExpressRoute, bliver ExpressRoute den foretrukne routingsti til disse slutpunkter for alle Microsoft-tjenester, herunder Office 365. Det betyder, at disse slutpunktundernet kun må bruges til kommunikation med Office 365 tjenester og ingen andre tjenester på Microsoft-netværket. Ellers medfører dit design asymmetrisk routing, hvor indgående forbindelser fra andre Microsoft-tjenester foretrækker at dirigere indgående over ExpressRoute, mens returstien bruger internettet.

6. Hvis et ExpressRoute-kredsløb eller en møde-mig-placering er nede, skal du sikre dig, at de indgående slutpunkter i det lokale miljø stadig er tilgængelige til at acceptere anmodninger via en separat netværkssti. Det kan betyde annoncering af undernet for disse slutpunkter via flere ExpressRoute-kredsløb.

7. Vi anbefaler, at du anvender nat-kilden for alle indgående netværkstrafikflow, der kommer ind på dit netværk via ExpressRoute, især når disse flow er på tværs af tilstandsbaserede netværksenheder, f.eks. firewalls.

8. Nogle tjenester i det lokale miljø, f.eks. ADFS-proxy eller Exchange automatisk søgning, kan modtage indgående anmodninger fra både Office 365 tjenester og brugere fra internettet. For disse anmodninger er Office 365 rettet mod det samme FQDN som brugeranmodninger via internettet. Hvis du tillader indgående brugerforbindelser fra internettet til disse slutpunkter i det lokale miljø, samtidig med at du tvinger Office 365 forbindelser til at bruge ExpressRoute, repræsenterer det en betydelig routingkompleksitet. For langt de fleste kunder, der implementerer sådanne komplekse scenarier via ExpressRoute, anbefales det ikke på grund af driftsmæssige overvejelser. Dette ekstra spild omfatter administration af risici for asymmetrisk routing og kræver, at du omhyggeligt administrerer routingannoncer og politikker på tværs af flere dimensioner.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Opdater din netværkstopologiplan for at vise, hvordan du undgår asymmetriske ruter
<a name="asymmetric"> </a>

Du vil gerne undgå asymmetrisk routing for at sikre, at personer i din organisation problemfrit kan bruge Office 365 samt andre vigtige tjenester på internettet. Der er to almindelige konfigurationer, som kunderne har, som forårsager asymmetrisk routing. Nu er et godt tidspunkt til at gennemse den netværkskonfiguration, du planlægger at bruge, og kontrollere, om der kan være et af disse asymmetriske routingscenarier.
  
Til at begynde med undersøger vi nogle forskellige situationer, der er knyttet til følgende netværksdiagram. I dette diagram er alle servere, der modtager indgående anmodninger, f.eks. ADFS eller hybridservere i det lokale miljø, i New Jersey-datacenteret og annonceres på internettet.
  
1. Selvom perimeternetværket er sikkert, er der ingen kilde-NAT tilgængelig for indgående anmodninger.

2. Serverne i New Jersey-datacenteret kan se både internet- og ExpressRoute-ruter.

![Oversigt over ExpressRoute-forbindelse.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Vi har også forslag til, hvordan du løser dem.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1: Cloud til forbindelse i det lokale miljø via internettet
  
I følgende diagram illustreres den asymmetriske netværkssti, der udføres, når din netværkskonfiguration ikke leverer NAT til indgående anmodninger fra Microsoft-cloudmiljøet via internettet.
  
1. Den indgående anmodning fra Office 365 henter IP-adressen for slutpunktet i det lokale miljø fra offentlig DNS og sender anmodningen til perimeternetværket.

2. I denne fejlbehæftede konfiguration er der ingen kilde-NAT konfigureret eller tilgængelig på perimeternetværket, hvor trafikken sendes, hvilket resulterer i, at den faktiske KILDE-IP-adresse bruges som returdestination.

  - Serveren på netværket dirigerer returtrafikken til Office 365 via en tilgængelig ExpressRoute-netværksforbindelse.

  - Resultatet er en asymmetrisk sti for det pågældende flow til Office 365, hvilket resulterer i en afbrudt forbindelse.

![ExpressRoute Asymetric routing problem 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Løsning 1a: Kilde NAT
  
Hvis du blot føjer en NAT-kilde til den indgående anmodning, løses dette forkert konfigurerede netværk. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind via New Jersey-datacenterets perimeternetværk. Denne gang er kilde-NAT tilgængelig.

2. Svaret fra serveren dirigeres tilbage mod den IP, der er knyttet til Kilde-NAT i stedet for den oprindelige IP-adresse, hvilket resulterer i, at svaret returneres langs den samme netværkssti.

![ExpressRoute Asymetric-routingløsning 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Løsning 1b: Ruteudformning
  
Alternativt kan du vælge ikke at tillade, at expressRoute BGP-præfikser annonceres, og fjerne den alternative netværkssti for disse computere. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind via New Jersey-datacenterets perimeternetværk. Denne gang er de præfikser, der annonceres fra Microsoft via ExpressRoute-kredsløbet, ikke tilgængelige for New Jersey-datacenteret.

2. Svaret fra serveren dirigeres tilbage mod den IP, der er knyttet til den oprindelige IP-adresse, via den eneste tilgængelige rute, hvilket resulterer i, at svaret returneres langs den samme netværkssti.

![ExpressRoute Asymetric-routingløsning 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2: Cloud til forbindelse i det lokale miljø via ExpressRoute
  
I følgende diagram illustreres den asymmetriske netværkssti, der udføres, når netværkskonfigurationen ikke leverer NAT til indgående anmodninger fra Microsoft-cloudmiljøet via ExpressRoute.
  
1. Den indgående anmodning fra Office 365 henter IP-adressen fra DNS og sender anmodningen til perimeternetværket.

2. I denne fejlbehæftede konfiguration er der ingen kilde-NAT konfigureret eller tilgængelig på perimeternetværket, hvor trafikken sendes, hvilket resulterer i, at den faktiske KILDE-IP-adresse bruges som returdestination.

  - Computeren på netværket dirigerer returtrafikken til Office 365 via en tilgængelig ExpressRoute-netværksforbindelse.

  - Resultatet er en asymmetrisk forbindelse til Office 365.

![ExpressRoute Asymetric routing problem 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Løsning 2: Kilde NAT
  
Hvis du blot føjer en NAT-kilde til den indgående anmodning, løses dette forkert konfigurerede netværk. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind via New York-datacenterets perimeternetværk. Denne gang er kilde-NAT tilgængelig.

2. Svaret fra serveren dirigeres tilbage mod den IP, der er knyttet til Kilde-NAT i stedet for den oprindelige IP-adresse, hvilket resulterer i, at svaret returneres langs den samme netværkssti.

![ExpressRoute Asymetric-routingløsning 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papir bekræfter, at netværksdesignet har stisymmetri

På dette tidspunkt skal du på papir bekræfte, at din implementeringsplan tilbyder rutesymmetri for de forskellige scenarier, du bruger Office 365. Du identificerer den specifikke netværksrute, der forventes at blive taget, når en person bruger forskellige funktioner i tjenesten. Fra netværket i det lokale miljø og WAN-routing til perimeterenhederne til forbindelsesstien. ExpressRoute eller internettet og videre til forbindelsen til onlineslutpunktet.
  
Du skal gøre dette for alle de Office 365 netværkstjenester, der tidligere blev identificeret som tjenester, som din organisation vil anvende.
  
Det hjælper at gøre dette papir gennemgang af ruter med en anden person. Forklar dem, hvor hvert netværkshop forventes at få sin næste rute fra, og sørg for, at du kender distributionsstierne. Husk, at ExpressRoute altid giver en mere begrænset rute til Microsoft-serverens IP-adresser, hvilket giver den lavere ruteomkostninger end en internetstandardrute.
  
### <a name="design-client-connectivity-configuration"></a>Konfiguration af Design klientforbindelse
<a name="asymmetric"> </a>

![Brug af PAC-filer med ExpressRoute.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Hvis du bruger en proxyserver til internetbundet trafik, skal du justere alle PAC- eller klientkonfigurationsfiler for at sikre, at klientcomputerne på netværket er konfigureret korrekt til at sende den ExpressRoute-trafik, du ønsker at Office 365 uden at overføre proxyserveren, og at den resterende trafik, herunder noget Office 365 trafik, sendes til den relevante proxy. Læs vores vejledning i [administration af Office 365 slutpunkter](./managing-office-365-endpoints.md), f.eks. PAC-filer.
  
> [!NOTE]
> Slutpunkterne ændres ofte, så ofte som ugentligt. Du bør kun foretage ændringer på baggrund af de tjenester og funktioner, din organisation har vedtaget, for at reducere antallet af ændringer, du skal foretage for at holde dig opdateret. Vær opmærksom på **ikrafttrædelsesdatoen** i RSS-feedet, hvor ændringerne annonceres, og der registreres alle tidligere ændringer, IP-adresser, der annonceres, må ikke annonceres eller fjernes fra annonceringen, indtil ikrafttrædelsesdatoen er nået.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Byg dine udrulnings- og testprocedurer
<a name="testing"> </a>

Din implementeringsplan skal omfatte både test- og annulleringsplanlægning. Hvis din implementering ikke fungerer som forventet, skal planen være designet til at påvirke det mindste antal personer, før der opdages problemer. Følgende er nogle principper på højt niveau, som din plan bør overveje.
  
1. Iscenegør netværkssegmentet og onboarding af brugertjenesten for at minimere afbrydelse.

2. Plan for test af ruter med traceroute og TCP-forbindelse fra en separat vært med internetforbindelse.

3. Det foretrækkes, at test af indgående og udgående tjenester udføres på et isoleret testnetværk med en test Office 365 lejer.

      - Alternativt kan der udføres test på et produktionsnetværk, hvis kunden endnu ikke bruger Office 365 eller er pilot.

      - Alternativt kan der udføres test under en produktionsafbrydelse, der kun afsættes til test og overvågning.

      - Alternativt kan du teste ved at kontrollere ruterne for hver tjeneste på hver lag 3-routernode. Dette tilbagefald bør kun bruges, hvis ingen andre test er mulige, da manglende fysisk test medfører risiko.

### <a name="build-your-deployment-procedures"></a>Opbyg dine installationsprocedurer

Dine udrulningsprocedurer bør udrulles til små grupper af personer i faser, så de kan testes, før de udrulles til større grupper af personer. Følgende er flere måder at forberede installationen af ExpressRoute på.
  
1. Konfigurer ExpressRoute med Microsoft-peering, og få rutereklamerne kun videresendt til en enkelt vært med henblik på trinvis test.

2. Annoncer ruter til ExpressRoute-netværket til et enkelt netværkssegment i første omgang, og udvid ruteannoncer efter netværkssegment eller område.

3. Hvis udrulning af Office 365 første gang, skal du bruge netværksinstallationen ExpressRoute som pilot for nogle få personer.

4. Hvis du bruger proxyservere, kan du alternativt konfigurere en test-PAC-fil for at sende nogle få personer til ExpressRoute med test og feedback, før du tilføjer mere.

Din implementeringsplan skal vise hver af de installationsprocedurer, der skal udføres, eller kommandoer, der skal bruges til at installere netværkskonfigurationen. Når netværksafbrydelsestiden ankommer, skal alle de ændringer, der foretages, være fra den skriftlige udrulningsplan, der blev skrevet på forhånd, og peer review. Se vores vejledning til den tekniske konfiguration af ExpressRoute.
  
- Opdatering af SPF TXT-posterne, hvis du har ændret IP-adresser for servere i det lokale miljø, som fortsat vil sende mails.

- Opdaterer alle DNS-poster for lokale servere, hvis du har ændret IP-adresser for at imødekomme en ny NAT-konfiguration.

- Sørg for, at du abonnerer på RSS-feedet for Office 365 slutpunktsmeddelelser for at vedligeholde alle routing- eller proxykonfigurationer.

Når installationen af ExpressRoute er fuldført, skal procedurerne i testplanen udføres. Resultaterne for hver procedure skal logføres. Du skal inkludere procedurer for tilbagerulning til det oprindelige produktionsmiljø, hvis resultaterne af testplanen angiver, at implementeringen ikke lykkedes.
  
### <a name="build-your-test-procedures"></a>Opbyg dine testprocedurer

Dine testprocedurer skal omfatte test for hver udgående og indgående netværkstjeneste for Office 365 både, der bruger ExpressRoute, og dem, der ikke vil. Procedurerne bør omfatte test fra hver enkelt entydige netværksplacering, herunder brugere, der ikke er i det lokale miljø i virksomhedens LAN.
  
Nogle eksempler på testaktiviteter omfatter følgende.
  
1. Ping fra din lokale router til din netværksoperatørrouter.

2. Valider de mere end 500 Office 365 og CRM Online-IP-adressereklamer, der modtages af routeren i det lokale miljø.

3. Kontrollér, at din indgående og udgående NAT fungerer mellem ExpressRoute og det interne netværk.

4. Valider, at ruter til din NAT annonceres fra din router.

5. Kontrollér, at ExpressRoute har accepteret de annoncerede præfikser.

      - Brug følgende cmdlet til at bekræfte peering-reklamer:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Valider, at dit offentlige NAT-IP-interval ikke annonceres til Microsoft via et andet ExpressRoute- eller offentligt internetnetværkskredsløb, medmindre det er et bestemt undersæt af et større interval som i det forrige eksempel.

7. ExpressRoute-kredsløb parres. Kontrollér, at begge BGP-sessioner kører.

8. Konfigurer en enkelt vært på indersiden af din NAT, og brug ping, tracert og tcpping til at teste forbindelsen på tværs af det nye kredsløb til værts-outlook.office365.com. Du kan også bruge et værktøj som Wireshark eller Microsoft Network Monitor 3.4 på en spejlet port til MSEE til at validere, at du kan oprette forbindelse til den IP-adresse, der er knyttet til outlook.office365.com.

9. Test funktionaliteten på programniveau for Exchange Online.

  - Test Outlook kan oprette forbindelse til Exchange Online og sende/modtage mail.

  - Test Outlook kan bruge onlinetilstand.

  - Test smartphoneforbindelse og send/modtag-funktionalitet.

10. Test funktionalitet på programniveau for SharePoint Online

  - Test OneDrive for Business synkroniseringsklient.

  - Test SharePoint onlinewebadgang.

11. Test funktionaliteten på programniveau for Skype for Business opkaldsscenarier:

  - Deltag i telefonmøde som godkendt bruger [inviter startet af slutbrugeren].

  - Inviter bruger til telefonmøde [invitation sendt fra MCU].

  - Deltag i konferencen som anonym bruger ved hjælp af Skype for Business webprogrammet.

  - Deltag i opkald fra din kablede pc-forbindelse, IP-telefon og mobilenhed.

  - Opkald til den bruger, der er medlem af organisationsnetværket, o Opkald til PSTN-validering: Opkaldet er fuldført, opkaldskvaliteten er acceptabel, forbindelsestiden er acceptabel.

  - Kontrollér, at tilstedeværelsesstatus for kontakter er opdateret for både medlemmer af lejeren og brugere i organisationsnetværket.

### <a name="common-problems"></a>Almindelige problemer

Asymmetrisk routing er det mest almindelige implementeringsproblem. Her er nogle almindelige kilder, du kan søge efter:
  
- Brug af en åben eller flad netværksroutingstopologi uden kilde-NAT på plads.

- Bruger ikke SNAT til at dirigere til indgående tjenester via både internet- og ExpressRoute-forbindelser.

- Der testes ikke indgående tjenester på ExpressRoute på et testnetværk, før de udrulles bredt.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Udrulning af ExpressRoute-forbindelse via dit netværk
<a name="testing"> </a>

Udrulning til ét segment af netværket ad gangen, gradvis udrulning af forbindelsen til forskellige dele af netværket med en plan om at annullere for hvert nyt netværkssegment. Hvis din installation er justeret i forhold til en Office 365 udrulning, skal du først udrulle til dine Office 365 pilotbrugere og udvide derfra.
  
Først til din test og derefter til produktion:
  
- Kør installationstrinnene for at aktivere ExpressRoute.

- Test, om netværksruterne er som forventet.

- Udfør test af hver indgående og udgående tjeneste.

- Annullering, hvis du opdager problemer.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Konfigurer en testforbindelse til ExpressRoute med et testnetværkssegment

Nu, hvor du har den færdige plan på papir, er det tid til at teste i lille skala. I denne test skal du oprette en enkelt ExpressRoute-forbindelse med Microsoft Peering til et testundernet på dit lokale netværk. Du kan konfigurere en [prøveversion Office 365 lejer](https://go.microsoft.com/fwlink/p/?LinkID=403802) med forbindelse til og fra testundernettet og inkludere alle udgående og indgående tjenester, som du bruger i produktionen i testundernettet. Konfigurer DNS for testnetværkssegmentet, og opret alle indgående og udgående tjenester. Udfør din testplan, og sørg for, at du kender distributionen for hver tjeneste og ruteoverførslen.
  
### <a name="execute-the-deployment-and-test-plans"></a>Udfør udrulnings- og testplanerne

Når du har fuldført de elementer, der er beskrevet ovenfor, skal du afkrydse de områder, du har fuldført, og sikre, at du og dit team har gennemgået dem, før du kører dine udrulnings- og testplaner.
  
- Liste over udgående og indgående tjenester, der er involveret i netværksændringen.

- Diagram over global netværksarkitektur, der viser både internet udgående data og ExpressRoute-mødeplaceringer.

- Netværksroutingdiagram, der demonstrerer de forskellige netværksstier, der bruges til hver tjeneste, der er installeret.

- En udrulningsplan med trin til implementering af ændringerne og annullering, hvis det er nødvendigt.

- En testplan til test af hver Office 365 og netværkstjeneste.

- Fuldført papirvalidering af produktionsruter for indgående og udgående tjenester.

- En fuldført test på tværs af et testnetværkssegment, herunder tilgængelighedstest.

Vælg et afbrydelsesvindue, der er langt nok til at gennemgå hele udrulningsplanen og testplanen, og som har lidt tid til rådighed til fejlfinding og tid til at rulle tilbage, hvis det er nødvendigt.
  
> [!CAUTION]
> På grund af den komplekse distribution over både internettet og ExpressRoute anbefales det, at der føjes ekstra buffertid til dette vindue for at håndtere fejlfinding af kompleks routing.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurer QoS for Skype for Business Online

QoS er nødvendigt for at opnå stemme- og mødefordele for Skype for Business Online. Du kan konfigurere QoS, når du har sørget for, at ExpressRoute-netværksforbindelsen ikke blokerer nogen af dine andre Office 365-tjenesteadgang. Konfiguration af QoS er beskrevet i artiklen [ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>Fejlfinding af implementeringen
<a name="troubleshooting"> </a>

Det første sted at se på trinnene i denne implementeringsvejledning, blev nogen savnet i din implementeringsplan? Gå tilbage, og kør yderligere test af små netværk, hvis det er muligt, for at replikere fejlen og foretage fejlfinding af den der.
  
Identificer, hvilke indgående eller udgående tjenester der mislykkedes under testen. Hent specifikt IP-adresserne og undernet for hver af de tjenester, der mislykkedes. Gå videre, og gå i gang med netværkstopologidiagrammet på papir, og valider distributionen. Valider specifikt, hvor ExpressRoute-distributionen annonceres til, Test denne routing under afbrydelsen, hvis det er muligt med sporinger.
  
Kør PSPing med en netværkssporing til hvert kundeslutpunkt, og evaluer kilde- og destinations-IP-adresser for at validere, at de er som forventet. Kør telnet til en hvilken som helst postvært, som du viser på port 25, og kontrollér, at SNAT skjuler den oprindelige kilde-IP-adresse, hvis dette forventes.
  
Vær opmærksom på, at når du udruller Office 365 med en ExpressRoute-forbindelse, skal du sikre, at både netværkskonfigurationen for ExpressRoute er optimalt designet, og at du også har optimeret de andre komponenter på netværket, f.eks. klientcomputere. Ud over at bruge denne planlægningsvejledning til fejlfinding af de trin, du måske gik glip af, har vi også skrevet en [plan for fejlfinding af ydeevnen for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimering af netværket til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow ved hjælp af ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevne](network-planning-and-performance.md)
