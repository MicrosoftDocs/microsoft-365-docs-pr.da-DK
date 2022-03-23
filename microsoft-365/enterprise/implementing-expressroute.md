---
title: Implementering af ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du implementerer ExpressRoute til Office 365, som giver en alternativ routingsti til mange internetadresser Office 365 tjenester.
ms.openlocfilehash: 9fbfaec8304c0ad5273aed3f07cb3d32c590c638
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591390"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementering af ExpressRoute til Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

ExpressRoute til Office 365 giver en alternativ routingsti til mange internet mod Office 365-tjenester. Arkitekturen i ExpressRoute til Office 365 er baseret på annoncering af offentlige IP-præfikser for Office 365-tjenester, der allerede er tilgængelige via internettet, i dine klargjorte ExpressRoute-kredsløb til efterfølgende redistribution af disse IP-præfikser i dit netværk. Med ExpressRoute aktiverer du effektivt flere forskellige routingstier via internettet og via ExpressRoute til mange Office 365 tjenester. Denne routingtilstand på dit netværk kan betyde en betydelig ændring af, hvordan din interne netværktopologi er designet.
  
 **Status:** Komplet vejledning v2
  
Du skal nøje planlægge din ExpressRoute til Office 365-implementering for at tage højde for netværkskompleksiteterne ved at have routing tilgængelig både via et dedikeret kredsløb med ruter, der er tilføjet i kernenetværket og på internettet. Hvis du og dit team ikke udfører den detaljerede planlægning og testning i denne vejledning, er der en høj risiko for, at du vil miste forbindelsen til Office 365-tjenester periodisk eller fuldstændigt, når ExpressRoute-kredsløbet er aktiveret.
  
For at få en vellykket implementering skal du analysere dine krav til infrastruktur, gennemgå detaljeret netværksvurdering og -design, omhyggeligt planlægge implementeringen i faser og på kontrolleret vis og opbygge en detaljeret plan for validering og test. For et stort, distribueret miljø er det ikke ualmindeligt, at implementeringen strækker sig over flere måneder. Denne vejledning er beregnet til at hjælpe dig med at planlægge fremad.
  
Store vellykkede udrulninger kan tage seks måneders planlægning og omfatter ofte teammedlemmer fra mange områder i organisationen, herunder netværks-, firewall- og proxyserveradministratorer, Office 365-administratorer, sikkerhed, slutbrugersupport, projektstyring og ledelsens støtte. Din investering i planlægningsprocessen vil reducere sandsynligheden for, at du vil opleve installationsfejl, der medfører nedetid eller kompleks og dyr fejlfinding.
  
Vi forventer, at følgende er gennemført, før denne implementeringsvejledning startes.
  
1. Du har gennemført en netværksvurdering for at afgøre, om ExpressRoute anbefales og godkendes.

2. Du har valgt en ExpressRoute-serviceudbyder. Find oplysninger om [ExpressRoute-partnere og peeringplaceringer](/azure/expressroute/expressroute-locations).

3. Du har allerede læst og forstået [ExpressRoute-dokumentationen](https://azure.microsoft.com/documentation/services/expressroute/) , og dit interne netværk kan opfylde forudsætningerne for ExpressRoute fra ende til anden.

4. Dit team har læst al den offentlige vejledning og dokumentation på , [https://aka.ms/ert](https://aka.ms/ert)og har set [serien Azure ExpressRoute til Office 365-kurser](https://channel9.msdn.com/series/aer) på kanal 9 for at [https://aka.ms/expressrouteoffice365](./azure-expressroute.md)få et overblik over vigtige tekniske detaljer, herunder:

      - Internettets afhængigheder af SaaS-tjenester.

      - Sådan undgår du asymmetriske ruter og håndterer kompleks routing.

      - Sådan inkorporerer du perimetersikkerhed, tilgængelighed og kontrolelementer på programniveau.

## <a name="begin-by-gathering-requirements"></a>Begynd med at indsamle krav
<a name="requirements"> </a>

Start med at beslutte, hvilke funktioner og tjenester du planlægger at indføre inden for organisationen. Du skal bestemme, hvilke funktioner i de forskellige Office 365-tjenester, der skal bruges, og hvilke placeringer på dit netværk, der skal hoste personer, der bruger disse funktioner. Med kataloget af scenarier skal du tilføje de netværksattributter, som hvert af disse scenarier kræver. f.eks. indgående og udgående netværkstrafikflows, og hvis Office 365 slutpunkter er tilgængelige via ExpressRoute eller ej.
  
Sådan indsamler du organisationens krav:
  
- Katalogisere indgående og udgående netværkstrafik for de Office 365, din organisation bruger. Se Office 365 URL-adresser og siden med IP-adresseintervaller for at få en beskrivelse af flows, Office 365 forskellige scenarier kræver.

- Indsamg dokumentation for eksisterende netværktopologi, der viser oplysninger om din interne WAN-basis og -topologi, forbindelsen til satellitwebsteder, forbindelsesmuligheder for slutbrugere, routing til perimeternetværks udgangspunkter og proxytjenester.

  - Identificer indgående tjenesteslutpunkter på de netværksdiagrammer, som Office 365 og andre Microsoft-tjenester opretter forbindelse til, og viser både internetstier og foreslåede ExpressRoute-forbindelsesstier.

  - Identificer alle geografiske brugerplaceringer og WAN-forbindelser mellem placeringer, samt hvilke placeringer der aktuelt har et udgangspunkt til internettet, og hvilke placeringer der foreslås at skulle have et udgangspunkt til en ExpressRoute-peeringplacering.

  - Identificer alle grænseenheder, f.eks. proxyer, firewalls osv., og katalogisere deres relation til flows, der går via internettet og ExpressRoute.

  - Dokument, om slutbrugere skal have adgang Office 365-tjenester via direkte routing eller indirekte programproxy for både internet- og ExpressRoute-flows.

- Føj placeringen af din lejer og meet me-placeringer til dit netværksdiagram.

- Anslå de forventede og observerede egenskaber for netværksydeevne og ventetid fra større brugerplaceringer for at Office 365. Husk på, Office 365 er et globalt og distribueret sæt af tjenester, og brugerne opretter forbindelse til placeringer, der kan være forskellige fra placeringen af deres lejer. Det anbefales derfor at måle og optimere for ventetid mellem brugeren og den nærmeste kant af Microsofts globale netværk via ExpressRoute og internetforbindelser. Du kan bruge dine resultater fra netværksvurderingen til at hjælpe med denne opgave.

- Opliste krav til virksomhedens netværkssikkerhed og høj tilgængelighed, der skal være opfyldt med den nye ExpressRoute-forbindelse. Eksempelvis hvordan brugerne fortsat får adgang til et Office 365 i tilfælde af fejl i internetudfaldet eller ExpressRoute-kredsløbet.

- Dokumenter, hvilke indgående og udgående Office 365 netværksflow, der skal benytte internetstien, og hvilke der skal bruge ExpressRoute. De specifikke geografiske placeringer af dine brugere og oplysningerne om din lokale netværktopologi kræver muligvis, at planen skal være forskellig fra én brugerplacering til en anden.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Katalogisere din udgående og indgående netværkstrafik
<a name="trafficCatalog"> </a>

For at minimere routing og andre komplekse forhold i forbindelse med netværk anbefaler vi, at du kun bruger ExpressRoute til Office 365 til de netværkstrafikflows, der kræves for at gå via en dedikeret forbindelse på grund af lovmæssige krav eller som et resultat af netværksvurderingen. Vi anbefaler desuden, at du faseudjicerer omfanget af ExpressRoute-routing og tilgang til udgående og indgående netværkstrafikflows som forskellige og adskilte faser af implementeringsprojektet. Udrul ExpressRoute til Office 365 kun for brugerinitierede udgående netværkstrafikflows, og lad indgående netværkstrafikflows være på internettet, og det kan hjælpe med at styre den øgede topologiske kompleksitet og risikoen for at introducere yderligere muligheder for asymmetrisk routing.
  
Dit netværkstrafikkatalog skal indeholde lister over alle de indgående og udgående netværksforbindelser, du har mellem dit lokale netværk og Microsoft.
  
- Udgående netværkstrafikflows er alle scenarier, hvor en forbindelse startes fra dit lokale miljø, f.eks. fra interne klienter eller servere, med en destination for Microsoft-tjenester. Disse forbindelser kan være direkte til Office 365 eller indirekte, f.eks. når forbindelsen går gennem proxyservere, firewalls eller andre netværksenheder på stien til Office 365.

- Indgående netværkstrafikflows er alle scenarier, hvor en forbindelse startes fra Microsoft-skyen til en vært i det lokale miljø. Disse forbindelser er typisk nødt til at gå gennem firewalls og anden sikkerhedsinfrastruktur, som kræves af kundens sikkerhedspolitik for flows, som kommer udefra.

Læs afsnittet  Sikre rutesymmetri i artiklen [Routing med ExpressRoute til Office 365 for](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) at afgøre, hvilke tjenester der sender indgående trafik, og se efter den kolonne, der er markeret **med ExpressRoute til Office 365** i [referenceartikel om Office 365-slutpunkter](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) for at bestemme resten af forbindelsesoplysningerne.
  
For hver tjeneste, der kræver en udgående forbindelse, skal du beskrive den planlagte forbindelse for tjenesten, herunder netværksrouting, proxykonfiguration, pakkeinspektion og behov for båndbredde.
  
For hver tjeneste, der kræver en indgående forbindelse, skal du bruge nogle yderligere oplysninger. Servere i Microsoft-skyen opretter forbindelser til dit lokale netværk. For at sikre at forbindelserne er foretaget korrekt, skal du beskrive alle aspekter af denne forbindelse, herunder: de offentlige DNS-poster for de tjenester, der accepterer disse indgående forbindelser, de CIDR-formaterede IPv4 IP-adresser, hvilket internetudbyderudstyr der er involveret, og hvordan indgående NAT eller kilde-NAT håndteres for disse forbindelser.
  
Indgående forbindelser skal gennemses, uanset om de opretter forbindelse via internettet eller ExpressRoute for at sikre, at asymmetrisk routing ikke er blevet introduceret. I nogle tilfælde skal slutpunkter i det lokale miljø, som Office 365-tjenester indgående forbindelser til, muligvis også have adgang til af andre Microsoft- og ikke-Microsoft-tjenester. Det betyder, at aktivering af ExpressRoute-routing til disse Office 365 formål ikke ødelægger andre scenarier. I mange tilfælde kan kunder være nødt til at implementere bestemte ændringer i deres interne netværk, f.eks. kildebaseret NAT, for at sikre, at indgående flows fra Microsoft forbliver symmetriske, når ExpressRoute er aktiveret.
  
Her er et eksempel på det detaljeniveau, der kræves. I dette tilfælde Exchange Hybrid dirigere til det lokale system via ExpressRoute. 

|Forbindelsesegenskab   |Værdi  |
|----------|-----------|
|**Retning af netværkstrafik** <br/> |Indgående  <br/> |
|**Tjeneste** <br/> |Exchange Hybrid  <br/> |
|**Offentligt Office 365 slutpunkt (kilde)** <br/> |Exchange Online (IP-adresser)  <br/> |
|**Offentligt slutpunkt i det lokale miljø (destination)** <br/> |5.5.5.5  <br/> |
|**Offentlig (internet) DNS-post** <br/> |Autodiscover.contoso.com  <br/> |
|**Skal dette slutpunkt i det lokale miljø bruges til af andre (Office 365) Microsoft-tjenester** <br/> |Nej  <br/> |
|**Vil dette slutpunkt i det lokale miljø blive brugt af brugere/systemer på internettet** <br/> |Ja  <br/> |
|**Interne systemer publiceret via offentlige slutpunkter** <br/> |Exchange Server klientadgangsrolle (lokalt miljø) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**IP-annoncering af det offentlige slutpunkt** <br/> |**Til internettet**: 5.5.0.0/16 **til ExpressRoute**: 5.5.5.0/24  <br/> |
|**Sikkerhed/perimeterkontrolelementer** <br/> |**Internetsti**: DeviceID_002  **ExpressRoute-sti**: DeviceID_003  <br/> |
|**Høj tilgængelighed** <br/> |Aktiv/Aktiv på tværs af 2 geo-redundante/ExpressRoute-kredsløb – Chicago og Dallas  <br/> |
|**Kontrol af stiens symmetri** <br/> |**Metode**: Kilde-NAT-internetsti: Indgående kilde-NAT-forbindelser til 192.168.5.5 **ExpressRoute-sti**: Kilde-NAT-forbindelser til 192.168.1.0 (Chicago) og 192.168.2.0 (Dallas)  <br/> |

Her er et eksempel på en tjeneste, der kun er udgående:

|**Forbindelsesegenskab**|**Værdi**|
|----------|-----------|
|**Retning af netværkstrafik** <br/> |Udgående  <br/> |
|**Tjeneste** <br/> |SharePoint Online  <br/> |
|**Slutpunkt i det lokale miljø (kilde)** <br/> |Bruger arbejdsstation  <br/> |
|**Offentligt Office 365 slutpunkt (destination)** <br/> |SharePoint Online (IP-adresser)  <br/> |
|**Offentlig (internet) DNS-post** <br/> |\*.sharepoint.com (og flere FQDN'er)  <br/> |
|**CDN henvisninger** <br/> |cdn.sharepointonline.com (og flere FQDN'er) – IP-adresser, der vedligeholdes af CDN-udbydere)  <br/> |
|**IP-annoncering og NAT i brug** <br/> |**Internetsti/kilde-NAT**: 1.1.1.0/24  <br/> **ExpressRoute-sti/kilde-NAT**: 1.1.2.0/24 (Chicago) og 1.1.3.0/24 (Dallas)  <br/> |
|**Forbindelsesmetode** <br/> |**Internet**: via lag 7-proxy (.pac-fil)  <br/> **ExpressRoute**: direkte routing (ingen proxy)  <br/> |
|**Sikkerhed/perimeterkontrolelementer** <br/> |**Internetsti**: DeviceID_002  <br/> **ExpressRoute-sti**: DeviceID_003  <br/> |
|**Høj tilgængelighed** <br/> |**Internetsti**: Redundant internet udgangspunkt  <br/> **ExpressRoute-sti**: Aktiv "hot potato"-routing på tværs af 2 geo-redundante ExpressRoute-kredsløb – Chicago og Dallas  <br/> |
|**Kontrol af stiens symmetri** <br/> |**Metode**: Kilde-NAT for alle forbindelser  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Dit netværktopologidesign med regionale forbindelser
<a name="topology"> </a>

Når du forstår tjenesterne og deres tilknyttede netværkstrafikflows, kan du oprette et netværksdiagram, der inkorporerer disse nye krav til forbindelse og illustrerer de ændringer, du skal foretage for at bruge ExpressRoute til Office 365. Dit diagram bør omfatte:
  
1. Alle brugerplaceringer, Office 365 adgang til og andre tjenester fra.

2. Alle internet- og ExpressRoute-udgangspunkter.

3. Alle udgående og indgående enheder, der administrerer forbindelsen ind og ud af netværket, herunder routere, firewalls, programproxyservere og registrering/forhindring af indtrængen.

4. Interne destinationer for al indgående trafik, f.eks. interne ADFS-servere, der accepterer forbindelser fra proxyservere for ADFS-webprogrammet.

5. Katalogisering af alle IP-undernet, der annonceres

6. Identificer hver placering, hvor folk Office 365 adgang til, og angiv de meet me-placeringer, der skal bruges til ExpressRoute.

7. Placeringer og dele af din interne netværktopologi, hvor Microsoft IP-præfikser, der er lært fra ExpressRoute, accepteres, filtreres og overføres til.

8. Netværktopologien bør illustrere den geografiske placering af hvert enkelt netværkssegment, og hvordan den opretter forbindelse til Microsoft-netværket via ExpressRoute og/eller internettet.

Nedenstående diagram viser hver placering, hvor folk skal bruge Office 365 fra, sammen med annonceringerne af indgående og udgående routing til Office 365.
  
![ExpressRoute – regionalt geografisk meet me.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
For udgående trafik får folk adgang Office 365 på én af tre måder:
  
1. Gennem en meet me-placering i Nordamerika for personer i Californien.

2. Gennem en meet me-placering i Hongkong for personer i Hongkong.

3. Via internettet i Bangladesh, hvor der er færre personer og ingen ExpressRoute-kredsløb.

![Udgående forbindelser til regionalt diagram.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
På samme måde returneres indgående netværkstrafik fra Office 365 på én af tre måder:
  
1. Gennem en meet me-placering i Nordamerika for personer i Californien.

2. Gennem en meet me-placering i Hongkong for personer i Hongkong.

3. Via internettet i Bangladesh, hvor der er færre personer og ingen ExpressRoute-kredsløb.

![Indgående forbindelser til regionalt diagram.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Bestem den relevante meet me-placering

Valget af meet me-placeringer, som er den fysiske placering, hvor dit ExpressRoute-kredsløb opretter forbindelse til Microsoft-netværket, påvirkes af de placeringer, hvor folk får adgang til Office 365 fra. Som et SaaS-tilbud fungerer Office 365 ikke under den regionale IaaS- eller PaaS-model på samme måde, som Azure gør. I stedet er Office 365 et distribueret sæt samarbejdstjenester, hvor brugerne kan have brug for at oprette forbindelse til slutpunkter på tværs af flere datacentre og områder, som muligvis ikke nødvendigvis er på den samme placering eller i det samme område, hvor brugerens lejer er hostet.
  
Det betyder, at den vigtigste overvejelse, du skal gøre, når du vælger meet me-placeringer til ExpressRoute til Office 365, er det sted, hvor personerne i organisationen skal oprette forbindelse fra. Den generelle anbefaling for optimal Office 365-forbindelse er at implementere routing, så brugeranmodninger om Office 365-tjenester overdrages til Microsoft-netværket via den korteste netværkssti. Dette kaldes ofte "hot potato"-routing. Hvis de fleste af Office 365-brugerne f.eks. befinder sig på en eller to placeringer, vil valg af meet me-placeringer, der ligger tættest på placeringen af disse brugere, skabe det optimale design. Hvis din virksomhed har store brugergrupper i mange forskellige områder, kan du overveje at have flere ExpressRoute-kredsløb og meet me-placeringer. For nogle af dine brugerplaceringer er den korteste/mest optimale sti til Microsoft-netværk og Office 365 muligvis ikke via dine interne WAN- og ExpressRoute meet me-punkter, men via internettet.
  
Ofte er der flere meet me-placeringer, der kan vælges i et område i relativ nærhed til dine brugere. Udfyld følgende tabel for at vejlede dig i dine beslutninger.

**Planlagte meet me-placeringer for ExpressRoute i Californien og New York**

|Placering  <br/> |Antal personer  <br/> |Forventet ventetid til Microsoft-netværk over internet udgangspunkt  <br/> |Forventet ventetid til Microsoft-netværk over ExpressRoute  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10,000  <br/> |~ 15 ms  <br/> |~ 10 ms (via Silicon Valley)  <br/> |
|Washington DC  <br/> |15,000  <br/> |~ 20 ms  <br/> |~ 10 ms (via New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15 ms  <br/> |~ 40 ms (via New York)  <br/> |

Når den globale netværksarkitektur, der viser Office 365-området, ExpressRoute-netværket serviceudbyder meet me-placeringer, og antallet af personer efter placering er blevet udviklet, kan det bruges til at identificere, om der kan foretages nogen optimeringer. Det kan også vise globale hairpin-netværksforbindelser, hvor trafik routes til en fjern placering for at få meet me-placeringen. Hvis der findes en hairpin på det globale netværk, skal det afhjælpes, før du fortsætter. Find enten en anden meet me-placering, eller brug selektive internetudskiftpunkter for at undgå denne hairpin.
  
Det første diagram viser et eksempel på en kunde med to fysiske placeringer i Nordamerika. Du kan se oplysningerne om kontorplaceringer, Office 365 lejerplaceringer og flere valgmuligheder for Meet me-placeringer for ExpressRoute. I dette eksempel har kunden valgt meet me-placeringen baseret på to principper i rækkefølgen:
  
1. Nærmeste afstand til personerne i organisationen.

2. Nærmeste afstand til et Microsoft-datacenter, hvor Office 365 er hostet.

![ExpressRoute – Amerikansk geografisk mød-mig.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Hvis dette koncept udvides en smule yderligere, viser det andet diagram et eksempel på en flerlandskunde, der havde lignende oplysninger og beslutningstagning. Denne kunde har et lille kontor i Bangladesh med kun et lille team på ti personer, der fokuserer på at øge deres aftryk i området. Der findes en meet me-placering i Chennai og et Microsoft-datacenter med Office 365 hostet i Chennai, så en meet me-placering ville give mening, men for ti personer er udgiften til det ekstra kredsløb besværligt. Når du ser på dit netværk, skal du afgøre, om den ventetid, der er involveret i at sende din netværkstrafik på tværs af dit netværk, er mere effektiv end at bruge pengene på at anskaffe et andet ExpressRoute-kredsløb.
  
Alternativt kan ti personer i Bangladesh opleve bedre ydeevne, når deres netværkstrafik sendes via internettet til Microsoft-netværket, end de ville routing på deres interne netværk, som det er vist i de indledende diagrammer og gengivet nedenfor.
  
![Udgående forbindelser til regionalt diagram.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Opret din implementeringsplan for ExpressRoute Office 365 din implementeringsplan
<a name="implementation"> </a>

Din implementeringsplan bør omfatte både de tekniske detaljer ved konfiguration af ExpressRoute og oplysningerne om konfiguration af al anden infrastruktur på dit netværk, f.eks. følgende.
  
- Planlæg, hvilke tjenester der er opdelt mellem ExpressRoute og internettet.

- Planlæg båndbredde, sikkerhed, høj tilgængelighed og failover.

- Design indgående og udgående routing, herunder de rette optimeringer af routingstier for forskellige placeringer

- Beslut, hvor langt ExpressRoute-ruter skal annonceres ind i dit netværk, og hvad mekanismer er for klienter til at vælge internet- eller ExpressRoute-sti; f.eks. direkte routing eller programproxy.

- Planlæg DNS-postændringer, [herunder poster i Sender Policy Framework](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) .

- Planlæg NAT-strategi, herunder udgående og indgående kilde-NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planlæg din routing med både internet- og ExpressRoute-netværksstier
<a name="paths"> </a>

- For din installationsstart anbefales alle indgående tjenester, f.eks. indgående mail eller hybridforbindelse, at bruge internettet.

- Planlæg LAN-routing for slutbrugerklienter, f.eks. konfiguration af en [PAC/WPAD-fil](./managing-office-365-endpoints.md), standardrute, proxyservere og BGP-ruteannoncering.

- Planlæg perimeterrouting, herunder proxyservere, firewalls og skyproxyer.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planlæg din båndbredde, sikkerhed, høj tilgængelighed og failover
<a name="availability"> </a>

Opret en plan for båndbredde, der kræves for hver større Office 365 arbejdsbelastning. Estimat Exchange Online, SharePoint Online og Skype for Business krav til onlinebåndbredde separat. Du kan bruge de beregningsberegnere, vi har angivet for Exchange Online og Skype for Business, som udgangspunkt, men der kræves en prøvetest med en repræsentativ stikprøve af brugerprofiler og placeringer for fuldt ud at forstå organisationens behov for båndbredde.
  
Tilføj, hvordan sikkerhed håndteres på hver internet- og ExpressRoute-udgangsplacering, til din plan. Husk, at alle ExpressRoute-forbindelser til Office 365 bruger offentlig peering og stadig skal være sikret i overensstemmelse med virksomhedens sikkerhedspolitikker for oprettelse af forbindelse til eksterne netværk.
  
Føj oplysninger til din plan om, hvilke personer der påvirkes af hvilken type udfald, og hvordan disse personer på nemmeste vis vil kunne udføre deres arbejde på fuld kapacitet.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planlæg krav til båndbredde, Skype for Business kravene til rysten, ventetid, overbelastning og kapacitet
  
Skype for Business Online har også specifikke ekstra netværkskrav, som er beskrevet i artiklen Mediekvalitet og Ydeevne for [netværksforbindelse i Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Læs afsnittet Planlægning **af båndbredde for Azure ExpressRoute** i [Netværksplanlægning med ExpressRoute til Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Når du udfører en båndbreddevurdering med dine pilotbrugere, kan du bruge vores vejledning; [Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planlægge krav til høj tilgængelighed
  
Opret en plan for høj tilgængelighed, der opfylder dine behov, og inkorponer dette i dit opdaterede diagram over netværkets topologi. Læs afsnittet Høj **tilgængelighed og failover med Azure ExpressRoute** i [Netværksplanlægning med ExpressRoute til Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planlægning af krav til netværkssikkerhed
  
Opret en plan, der opfylder dine krav til netværkssikkerhed, og inkorkorer dette i dit opdaterede diagram over netværkets topologi. Læs afsnittet Anvende **sikkerhedskontrolelementer på Azure ExpressRoute for Office 365 for** scenarier i [Netværksplanlægning med ExpressRoute til Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Design forbindelse til udgående tjenester
<a name="outbound"> </a>

ExpressRoute til Office 365 har *krav til udgående* netværk, der muligvis ikke er bekendte. Specifikt skal de IP-adresser, der repræsenterer dine brugere og netværk for Office 365 og fungerer som kildeslutpunkterne for udgående netværksforbindelser til Microsoft, følge de specifikke krav, der er beskrevet nedenfor.
  
1. Slutpunkterne skal være offentlige IP-adresser, der er registreret for din virksomhed eller for en udbyder, der leverer ExpressRoute-forbindelse til dig.

2. Slutpunkterne skal annonceres over for Microsoft og valideres/accepteres af ExpressRoute.

3. Slutpunkterne må ikke annonceres over for internettet med den samme eller mere foretrukne routingmetrik.

4. Slutpunkterne må ikke bruges til at oprette forbindelse til Microsoft-tjenester, der ikke er konfigureret over ExpressRoute.

Hvis dit netværksdesign ikke opfylder disse krav, er der en høj risiko for, at brugerne vil opleve forbindelsesfejl i Office 365 og andre Microsoft-tjenester på grund af sort indbinding eller asymmetrisk routing. Dette sker, når anmodninger om Microsoft-tjenester dirigeres over ExpressRoute, men svarene dirigeres tilbage via internettet eller omvendt, og svarene går tabt af enheder med stor netværkssikkerhed som f.eks firewalls.
  
Den mest almindelige metode, du kan bruge til at opfylde ovenstående krav, er at bruge kilde-NAT, enten implementeret som en del af dit netværk eller leveret af din ExpressRoute-udbyder. Kilde-NAT gør det muligt at abstrakte detaljer og private IP-adresser fra dit internetnetværk fra ExpressRoute og; kombineret med korrekte IP-ruteannoncering, giver det en nem mekanisme til at sikre symmetri i stierne. Hvis du bruger netværksenheder, der er specifikke for ExpressRoute-peeringplaceringer, skal du implementere separate NAT-puljer for hver ExpressRoute-peering for at sikre symmetri i stierne.
  
Læs mere om [ExpressRoute NAT-kravene](/azure/expressroute/expressroute-nat).
  
Føj ændringerne for den udgående forbindelse til diagrammet over netværkets topologi.
  
### <a name="design-inbound-service-connectivity"></a>Design forbindelse til indgående tjenester
<a name="inbound"> </a>

De fleste Office 365-installationer antager en form for indgående forbindelse fra Office 365 til lokale tjenester, f.eks. til Exchange-, SharePoint- og Skype for Business-hybridscenarier, postkasseoverførsel og godkendelse ved hjælp af ADFS-infrastruktur. Når du aktiverer en ekstra routingsti mellem dit lokale netværk og Microsoft for udgående forbindelse, kan disse indgående forbindelser utilsigtet blive påvirket af asymmetrisk routing, selvom du regner med at have disse flows ved at bruge internettet. Nogle få forholdsregler, der er beskrevet nedenfor, anbefales for at sikre, at internetbaserede indgående flows fra Office 365 til lokale systemer ikke har nogen indvirkning.
  
For at minimere risikoen for asymmetrisk routing for indgående netværkstrafikflows skal alle de indgående forbindelser bruge kilde-NAT, før de distribueres i segmenter af dit netværk, hvor der er routingsynlighed i ExpressRoute. Hvis de indgående forbindelser er tilladt i et netværkssegment med routingsynlighed i ExpressRoute uden kilde-NAT, vil anmodninger, der stammer fra Office 365, komme ind fra internettet, men det svar, der går tilbage til Office 365, vil foretrække ExpressRoute-netværksstien tilbage til Microsoft-netværket, hvilket medfører asymmetrisk routing.
  
Du kan overveje en af følgende implementeringsmønstre for at opfylde dette krav:
  
1. Udfør kilde-NAT, før anmodninger distribueres til dit interne netværk ved hjælp af netværksudstyr som f.eks firewalls eller belastningsbalancer på stien fra internettet til dine lokale systemer.

2. Sørg for, at ExpressRoute-ruter ikke overføres til de netværkssegmenter, hvor indgående tjenester, f.eks. front end-servere eller omvendte proxysystemer, der håndterer internetforbindelser, er placeret.

Hvis du specifikt holder øje med disse scenarier i dit netværk og holder alle indgående netværkstrafikflows via internettet, hjælper det med at minimere risikoen for asymmetrisk routing i forbindelse med udrulning og drift.
  
Der kan være tilfælde, hvor du kan vælge at dirigere nogle indgående flows over ExpressRoute-forbindelser. For disse scenarier skal du tage følgende ekstra overvejelser med i dine overvejelser.
  
1. Office 365 kan kun målrette mod slutpunkter i det lokale miljø, der bruger offentlige IP-adresser. Det betyder, at selvom det indgående slutpunkt i det lokale miljø kun blotlagt for Office 365 via ExpressRoute, skal det stadig have den offentlige IP-adresse knyttet til sig.

2. Alle dns-navneopløsninger, Office 365 udfører for at løse lokale slutpunkter, sker ved hjælp af offentlig DNS. Det betyder, at du skal registrere indgående tjenesteslutpunkters FQDN IP-tilknytninger på internettet.

3. For at kunne modtage indgående netværksforbindelser over ExpressRoute skal de offentlige IP-undernet for disse slutpunkter annonceres over for Microsoft over ExpressRoute.

4. Evaluer omhyggeligt disse indgående netværkstrafikflows for at sikre, at de rette sikkerheds- og netværkskontrolelementer anvendes på dem i overensstemmelse med virksomhedens sikkerhedspolitikker og netværkspolitikker.

5. Når dine indgående slutpunkter i det lokale miljø annonceres over for Microsoft over ExpressRoute, bliver ExpressRoute den foretrukne routingsti til disse slutpunkter for alle Microsoft-tjenester, herunder Office 365. Det betyder, at disse slutpunktsundernet kun må bruges til kommunikation med Office 365-tjenester og ingen andre tjenester på Microsoft-netværket. Ellers vil dit design medføre asymmetrisk routing, hvor indgående forbindelser fra andre Microsoft-tjenester foretrækker at dirigere indgående over ExpressRoute, mens returstien bruger internettet.

6. I tilfælde af at et ExpressRoute-kredsløb eller en meet me-placering er nede, skal du sikre, at indgående slutpunkter i det lokale miljø stadig er tilgængelige til at acceptere anmodninger over en separat netværkssti. Det kan betyde annoncering af undernet for disse slutpunkter gennem flere ExpressRoute-kredsløb.

7. Vi anbefaler at anvende kilde-NAT for alle indgående netværkstrafikflows, der kommer ind i dit netværk via ExpressRoute, især når flows på tværs af netværksenheder som f.eks firewalls.

8. Nogle lokale tjenester, f.eks ADFS-proxy eller Exchange autodiscover, kan modtage indgående anmodninger fra både Office 365-tjenester og brugere fra internettet. For disse anmodninger Office 365 målrette den samme FQDN som brugeranmodninger via internettet. At tillade indgående brugerforbindelser fra internettet til disse lokale slutpunkter, mens gennemtvingelse af Office 365-forbindelser for at bruge ExpressRoute, repræsenterer betydelig routingkompleksitet. For størstedelen af kunderne, der implementerer så komplekse scenarier over ExpressRoute, anbefales det ikke på grund af driftsovervejelser. Denne ekstra spild omfatter administration af risici ved asymmetrisk routing og kræver, at du nøje administrerer routingannoncering og politikker på tværs af flere dimensioner.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Opdater planen for din netværktopologi for at vise, hvordan du vil undgå asymmetriske ruter
<a name="asymmetric"> </a>

Du bør undgå asymmetrisk routing for at sikre, at personer i organisationen uden problemer kan bruge Office 365 og andre vigtige tjenester på internettet. Der er to almindelige konfigurationer, som kunderne har, der medfører asymmetrisk routing. Nu er et godt tidspunkt at gennemgå den netværkskonfiguration, du planlægger at bruge, og kontrollere, om et af disse scenarier med asymmetrisk routing findes.
  
Til at begynde med vil vi undersøge et par forskellige situationer, der er knyttet til følgende netværksdiagram. I dette diagram er alle servere, der modtager indgående anmodninger, f.eks. ADFS eller lokale hybridservere, i datacenteret i New Jersey og annonceres over for internettet.
  
1. Mens perimeternetværket er sikkert, er der ingen kilde-NAT tilgængelig for indgående anmodninger.

2. Serverne i datacenteret i New Jersey kan se både internet- og ExpressRoute-ruter.

![Oversigt over ExpressRoute-forbindelse.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Vi har også forslag til, hvordan du løser dem.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problem 1: Forbindelse fra sky til lokalt miljø via internettet
  
Følgende diagram illustrerer den asymmetriske netværkssti, der tages, når din netværkskonfiguration ikke leverer NAT ved indgående anmodninger fra Microsoft-skyen via internettet.
  
1. Den indgående anmodning fra Office 365 henter IP-adressen på det lokale slutpunkt fra offentlig DNS og sender anmodningen til dit perimeternetværk.

2. I denne fejlbehæftede konfiguration er der ingen kilde-NAT konfigureret eller tilgængelig på perimeternetværket, hvor trafikken sendes til, hvilket medfører, at den faktiske kilde-IP-adresse bruges som returdestination.

  - Serveren på dit netværk ruter returtrafikken til en Office 365 via en hvilken som helst tilgængelig ExpressRoute-netværksforbindelse.

  - Resultatet er en asymmetrisk sti for det pågældende flow til Office 365, hvilket resulterer i en ødelagt forbindelse.

![ExpressRoute asymmetrisk routing , problem 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Løsning 1a: Kilde-NAT
  
Hvis du blot føjer en kilde-NAT til den indgående anmodning, løses problemet med dette forkert konfigurerede netværk. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind gennem New Jersey-datacenterets perimeternetværk. Denne gang er kilde-NAT tilgængelig.

2. Svaret fra serveren routes tilbage mod den IP-adresse, der er knyttet til kilde-NAT i stedet for den oprindelige IP-adresse, hvilket medfører, at svaret returneres langs den samme netværkssti.

![ExpressRoute asymmetrisk routing løsning 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Løsning 1b: Angivelse af rute
  
Alternativt kan du vælge ikke at tillade, at ExpressRoute BGP-præfikser annonceres, hvilket fjerner den alternative netværkssti for disse computere. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind gennem New Jersey-datacenterets perimeternetværk. Denne gang er de præfikser, der annonceres fra Microsoft via ExpressRoute-kredsløbet, ikke tilgængelige for New Jersey-datacenteret.

2. Svaret fra serveren routes tilbage mod den IP-adresse, der er knyttet til den oprindelige IP-adresse via den eneste tilgængelige rute, hvilket medfører, at svaret returneres langs den samme netværkssti.

![ExpressRoute asymmetrisk routing løsning 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problem 2: Forbindelse fra sky til lokalt miljø over ExpressRoute
  
Følgende diagram illustrerer den asymmetriske netværkssti, der tages, når din netværkskonfiguration ikke leverer NAT ved indgående anmodninger fra Microsoft-skyen via ExpressRoute.
  
1. Den indgående anmodning fra Office 365 henter IP-adressen fra DNS og sender anmodningen til dit perimeternetværk.

2. I denne fejlbehæftede konfiguration er der ingen kilde-NAT konfigureret eller tilgængelig på perimeternetværket, hvor trafikken sendes til, hvilket medfører, at den faktiske kilde-IP-adresse bruges som returdestination.

  - Computeren på dit netværk ruter returtrafikken til en Office 365 via en hvilken som helst tilgængelig ExpressRoute-netværksforbindelse.

  - Resultatet er en asymmetrisk forbindelse til Office 365.

![ExpressRoute asymmetrisk routing , problem 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Løsning 2: Kilde-NAT
  
Hvis du blot føjer en kilde-NAT til den indgående anmodning, løses problemet med dette forkert konfigurerede netværk. I dette diagram:
  
1. Den indgående anmodning fortsætter med at komme ind gennem New York-datacenterets perimeternetværk. Denne gang er kilde-NAT tilgængelig.

2. Svaret fra serveren routes tilbage mod den IP-adresse, der er knyttet til kilde-NAT i stedet for den oprindelige IP-adresse, hvilket medfører, at svaret returneres langs den samme netværkssti.

![ExpressRoute asymmetrisk routing – løsning 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Kontrollér på papir, at der er symmetri på netværksdesignet med sti

På dette tidspunkt skal du kontrollere på papir, at din implementeringsplan har rutesymmetri for de forskellige scenarier, du skal bruge Office 365. Du kan identificere den bestemte netværksrute, der forventes at blive taget, når en person bruger forskellige funktioner i tjenesten. Fra det lokale netværk og WAN-routing til perimeterenhederne til forbindelsesstien; ExpressRoute eller internettet og videre til forbindelsen til onlineslutpunktet.
  
Du skal gøre dette for alle de Office 365-netværkstjenester, der tidligere er blevet identificeret som tjenester, som din organisation vil indføre.
  
Det hjælper at udføre denne gennemgang af ruter på papir sammen med en anden person. Forklar dem, hvor hvert netværk hop forventes at få den næste rute fra, og sørg for, at du er fortrolig med routingstierne. Husk, at ExpressRoute altid leverer en mere begrænset rute til Microsoft-serverens IP-adresser for at give lavere omkostninger til rute end en standardrute over internettet.
  
### <a name="design-client-connectivity-configuration"></a>Konfiguration af klientforbindelse
<a name="asymmetric"> </a>

![Brug af PAC-filer med ExpressRoute.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Hvis du bruger en proxyserver til trafik, der er bundet til internettet, skal du justere eventuelle PAC- eller klientkonfigurationsfiler for at sikre, at klientcomputere på dit netværk er konfigureret korrekt til at sende den ExpressRoute-trafik, du ønsker at Office 365, uden at gå ud fra din proxyserver, og at den resterende trafik, herunder noget Office 365-trafik, sendes til den relevante proxy. Læs vores vejledning til [administration Office 365 slutpunkter](./managing-office-365-endpoints.md), f.eks. PAC-filer.
  
> [!NOTE]
> Slutpunkterne ændres ofte, så ofte som ugentligt. Du bør kun foretage ændringer baseret på de tjenester og funktioner, din organisation har indført, for at reducere antallet af ændringer, du skal foretage for at holde dig opdateret. Vær opmærksom på ikrafttrædelsesdatoen  i det RSS-feed, hvor ændringerne annonceres, og en post gemmes for alle tidligere ændringer, IP-adresser, der annonceres, kan ikke annonceres eller fjernes fra annonceringen, indtil ikrafttrædelsesdatoen er nået.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Opbyg dine udrulnings- og testprocedurer
<a name="testing"> </a>

Din implementeringsplan bør omfatte planlægning for både test og annullering af opdatering. Hvis implementeringen ikke fungerer som forventet, skal planen være designet til at påvirke det mindst muligt antal personer, før problemerne opdages. Følgende er nogle principper på højt niveau, som din plan bør tage højde for.
  
1. Gør onboarding af netværkssegment og brugertjeneste i faser for at minimere afbrydelser.

2. Planlæg test af ruter med traceroute og TCP-forbindelse fra en separat internetforbundet vært.

3. Test af indgående og udgående tjenester bør fortrinsvis udføres på et isoleret testnetværk med en Office 365 lejer.

      - Alternativt kan test udføres på et produktionsnetværk, hvis kunden endnu ikke bruger en Office 365 eller er i pilottest.

      - Alternativt kan der udføres test under en produktionsafbrydelse, der kun er sat til side til test og overvågning.

      - Alternativt kan der udføres test ved at kontrollere ruter for hver tjeneste på hver layer 3-routernode. Dette fall back bør kun bruges, hvis ingen anden test er mulig, da manglende fysiske tests introducerer risici.

### <a name="build-your-deployment-procedures"></a>Opbyg dine installationsprocedurer

Dine installationsprocedurer skal udrulles til mindre grupper af personer i faser, så det er muligt at udføre tests, før der udrulles til større grupper af personer. Følgende er flere måder at faseudrulningen af ExpressRoute på.
  
1. Konfigurer ExpressRoute med Microsoft-peering, og få ruteannonceringerne videresendt til en enkelt vært udelukkende til faseopdeparerede testformål.

2. Annoncer ruter over for ExpressRoute-netværket til et enkelt netværkssegment i starten, og udvid ruteannonceringerne efter netværkssegment eller område.

3. Hvis udrulning Office 365 første gang, skal du bruge ExpressRoute-netværksinstallation som et pilotprojekt for nogle få personer.

4. Hvis du bruger proxyservere, kan du alternativt konfigurere en PAC-testfil til at dirigere nogle få personer til ExpressRoute med test og feedback, før du tilføjer flere.

Din implementeringsplan bør opstille hver enkelt af de installationsprocedurer, der skal benyttes, eller kommandoer, der skal bruges til at udrulle netværkskonfigurationen. Når tidspunktet for netværkets strømsvigt ankommer, skal alle de ændringer, der foretages, være fra den skrevne implementeringsplan, der blev udarbejdet på forhånd og er blevet gennemgået af peers. Se vores vejledning til teknisk konfiguration af ExpressRoute.
  
- Opdater dine SPF TXT-poster, hvis du har ændret IP-adresser for eventuelle lokale servere, der fortsætter med at sende mails.

- Opdater eventuelle DNS-poster for lokale servere, hvis du har ændret IP-adresser for at give plads til en ny NAT-konfiguration.

- Sørg for, at du abonnerer på RSS-feedet for at Office 365 slutpunktsmeddelelser for at bevare eventuelle routing- eller proxykonfigurationer.

Når din ExpressRoute-installation er fuldført, skal procedurerne i testplanen udføres. Resultaterne for hver procedure skal logføres. Du skal medtage procedurer for at rulle tilbage til det oprindelige produktionsmiljø i tilfælde af, at resultaterne af testplanen indikerer, at implementeringen ikke blev gennemført.
  
### <a name="build-your-test-procedures"></a>Opbyg dine testprocedurer

Dine testprocedurer skal omfatte tests af hver enkelt udgående og indgående netværkstjeneste for Office 365, både dem, der bruger ExpressRoute, og dem, der ikke gør. Fremgangsmåderne bør omfatte test fra hver entydige netværksplacering, herunder brugere, der ikke er lokale i virksomhedens LAN.
  
Her er nogle eksempler på testaktiviteter.
  
1. Ping fra din router i det lokale miljø til netværksoperatorens router.

2. Valider, at der modtages mere end 500 Office 365- og CRM Online IP-adresseannonceringerne af routeren i det lokale miljø.

3. Valider, at din indgående og udgående NAT kører mellem ExpressRoute og det interne netværk.

4. Valider, at ruter til din NAT annonceres fra routeren.

5. Valider, at ExpressRoute har accepteret dine annoncerede præfikser.

      - Brug følgende cmdlet til at bekræfte peeringannonceringsannoncering:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Valider, at IP-området for din offentlige NAT ikke annonceres over for Microsoft via andre ExpressRoute-kredsløb eller kredsløb via offentlige internetnetværk, medmindre det er et specifikt delsæt af et større område som i det forrige eksempel.

7. ExpressRoute-kredsløb parres, og du skal kontrollere, at begge BGP-sessioner kører.

8. Konfigurer en enkelt vært inde i din NAT, og brug ping, tracert og tcpping til at teste forbindelsen på tværs af de nye kredsløb til værten outlook.office365.com. Alternativt kan du bruge et værktøj som f.eks. Wireshark eller Microsoft Network Monitor 3.4 på en spejlet port til MSEE til at validere, at du kan oprette forbindelse til den IP-adresse, der er knyttet til outlook.office365.com.

9. Test funktionalitet på programniveau for Exchange Online.

  - Test Outlook du kan oprette forbindelse til Exchange Online sende/modtage mails.

  - Test Outlook kan bruge onlinetilstand.

  - Test af smartphoneforbindelse og send/modtag-funktion.

10. Test af funktionalitet på programniveau for SharePoint Online

  - Test OneDrive for Business-synkroniseringsklient.

  - Test SharePoint onlineadgang til internettet.

11. Test funktionalitet på programniveau for Skype for Business alle opkaldsscenarier:

  - Deltag i telefonmøde som godkendt bruger [invitation startet af slutbruger].

  - Invitere bruger til telefonmøde [invitation sendt fra MCU].

  - Deltag i telefonmøde som anonym bruger Skype for Business et webprogram.

  - Deltag i opkald fra din pc-kabelforbindelse, IP-telefon og mobilenhed.

  - Ring til en bruger i organisationsnetværket o Ring til PSTN-validering: opkaldet er afsluttet, opkaldskvaliteten er acceptabel, forbindelsestiden er acceptabel.

  - Bekræft, at kontaktstatus er opdateret for begge medlemmer af lejeren og brugere i organisationsnetværket.

### <a name="common-problems"></a>Almindelige problemer

Asymmetrisk routing er det mest almindelige problem i forbindelse med implementering. Her er nogle almindelige kilder at lede efter:
  
- Brug af en åben eller flad routingtopologi uden kilde-NAT på plads.

- Bruger ikke SNAT til at dirigere til indgående tjenester via både internet- og ExpressRoute-forbindelser.

- Ikke tester indgående tjenester på ExpressRoute på et testnetværk, før bred udrulning.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Udrulning af ExpressRoute-forbindelse via dit netværk
<a name="testing"> </a>

Udrul din installation til ét segment af netværket ad gangen, og udrul gradvist forbindelsen til forskellige dele af netværket med en plan for at rulle tilbage for hvert nye netværkssegment. Hvis din installation er justeret med en Office 365 installation, skal du først udrulle for Office 365 pilotbrugere og udvide derfra.
  
Først til din test og derefter til produktion:
  
- Kør installationstrinnene for at aktivere ExpressRoute.

- Test, at netværksruterne ser ud som forventet.

- Udfør test på hver enkelt indgående og udgående tjeneste.

- Annullering, hvis du opdager problemer.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Konfigurere en testforbindelse til ExpressRoute med et testnetværkssegment

Nu hvor du har gennemført planen på papir, er det tid til at teste i mindre omfang. I denne test skal du oprette en enkelt ExpressRoute-forbindelse med Microsoft Peering til et testundernet på dit lokale netværk. Du kan konfigurere en [prøveversion Office 365-lejer](https://go.microsoft.com/fwlink/p/?LinkID=403802) med forbindelse til og fra testundernettet og medtage alle udgående og indgående tjenester, du skal bruge i produktion i testundernettet. Konfigurer DNS for testnetværkssegmentet og opret alle indgående og udgående tjenester. Udfør din testplan, og sørg for, at du er bekendt med routingen for hver tjeneste og ruteoverføringen.
  
### <a name="execute-the-deployment-and-test-plans"></a>Udfør udrulnings- og testplaner

Efterhånden som du afslutter de elementer, der er beskrevet ovenfor, skal du aftjekke de fuldførte områder og sikre, at du og dit team har gennemgået dem, før du udfører dine udrulnings- og testplaner.
  
- Liste over udgående og indgående tjenester, der er involveret i netværksændringen.

- Diagram over global netværksarkitektur, der viser både internetud udgangspunkter og meet me-placeringer for ExpressRoute.

- Netværksroutingdiagrammer viser de forskellige netværksstier, der bruges til hver tjeneste, der er installeret.

- En udrulningsplan med trin til at implementere ændringerne og annulleringen, hvis det er nødvendigt.

- En testplan til test af hver enkelt Office 365 og netværkstjeneste.

- Fuldført papirvalidering af produktionsruter for indgående og udgående tjenester.

- En gennemført test på tværs af et testnetværkssegment, herunder tilgængelighedstest.

Vælg et strømsvigtvindue, der er langt nok til at køre gennem hele installationsplanen og testplanen, har noget tid tilgængelig tid til fejlfinding og tid til at rulle tilbage, hvis det er nødvendigt.
  
> [!CAUTION]
> På grund af routingens komplekse karakter både via internettet og ExpressRoute anbefales det, at der føjes yderligere buffertid til dette vindue til håndtering af fejlfinding i forbindelse med kompleks routing.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Konfigurer QoS til Skype for Business Online

QoS er nødvendigt for at få tale- og mødefordele til Skype for Business Online. Du kan konfigurere servicetjenesteudbydere, når du har sikret dig, at ExpressRoute-netværksforbindelsen ikke blokerer nogen af dine Office 365 adgang til tjenesten. Konfiguration af QoS er beskrevet i artiklen [ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d).
  
## <a name="troubleshooting-your-implementation"></a>Fejlfinding i forbindelse med din implementering
<a name="troubleshooting"> </a>

Det første sted, du skal kigge, er i trinnene i denne implementeringsvejledning. Er der blevet overset nogen i din implementeringsplan? Gå tilbage, og kør yderligere test i et mindre netværk, hvis det er muligt, for at replikere fejlen og fejlfinde den der.
  
Identificer, hvilke indgående eller udgående tjenester, der mislykkedes under testen. Få specifikke IP-adresser og undernet for hver af de tjenester, der mislykkedes. Gå videre og gennemgå diagrammet over netværkets topologi på papir, og valider routingen. Valider specifikt, hvor ExpressRoute-routingen annonceres til, test denne routing under udfaldet , hvis det er muligt, med sporing.
  
Kør PSPing med en netværkssporing til hvert kundeslutpunkt, og evaluer kilde- og destinations-IP-adresser for at validere, at de er som forventet. Kør telnet til en hvilken som helst mailvært, du eksponerer på port 25, og bekræft, at SNAT skjuler den oprindelige kilde-IP-adresse, hvis det forventes.
  
Husk på, at når du installerer Office 365 med en ExpressRoute-forbindelse, skal du sikre dig, at både netværkskonfigurationen for ExpressRoute er optimalt designet, og at du også har optimeret de andre komponenter på dit netværk, f.eks. klientcomputere. Ud over at bruge denne planlægningsvejledning til at foretage fejlfinding af de trin, du måske er gået glip af, har vi også skrevet en plan for fejlfinding af ydeevne [for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimere dit netværk til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow med ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevnen](network-planning-and-performance.md)
