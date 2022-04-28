---
title: Netværksplanlægning med ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: I denne artikel får du mere at vide om Azure ExpressRoute til Office 365, og hvordan du bruger den til netværksplanlægning.
ms.openlocfilehash: a284472ad84139a5e76eeab38121d62cf3757829
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095636"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Netværksplanlægning med ExpressRoute til Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

ExpressRoute til Office 365 giver lag 3-forbindelse mellem dit netværk og Microsofts datacentre. Kredsløbene bruger BGP-rutereklamer (Border Gateway Protocol) for Office 365 frontendservere. Når enhederne i det lokale miljø har brug for at vælge den korrekte TCP/IP-sti for at Office 365, ses Azure ExpressRoute som et alternativ til internettet.
  
Azure ExpressRoute føjer en direkte sti til et bestemt sæt understøttede funktioner og tjenester, der tilbydes af Office 365 servere i Microsofts datacentre. Azure ExpressRoute erstatter ikke internetforbindelsen til Microsoft-datacentre eller grundlæggende internettjenester, f.eks. løsning af domænenavne. Azure ExpressRoute og dine internetkredsløb skal sikres og redundante.
  
I følgende tabel fremhæves nogle få forskelle mellem internet- og Azure ExpressRoute-forbindelser i forbindelse med Office 365.

|**Forskelle i netværksplanlægning**|**Internetnetværksforbindelse**|**ExpressRoute-netværksforbindelse**|
|:-----|:-----|:-----|
| Adgang til påkrævede internettjenester, herunder  <br/>  DNS-navnefortsættelse  <br/>  Bekræftelse af certifikatforringelse  <br/>  Netværk til levering af indhold (CDN'er)  <br/> |Ja  <br/> |Anmodninger til Microsoft-ejede DNS og/eller CDN infrastruktur kan bruge ExpressRoute-netværket.  <br/> |
| Adgang til Office 365 tjenester, herunder;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office i en browser  <br/>  Office 365 portal og godkendelse  <br/> |Ja, alle programmer og funktioner  <br/> |Ja, [specifikke programmer og funktioner](./urls-and-ip-address-ranges.md) <br/> |
|Sikkerhed i det lokale miljø ved perimeteren.  <br/> |Ja  <br/> |Ja  <br/> |
|Planlægning af høj tilgængelighed.  <br/> |Failover til en alternativ internetnetværksforbindelse  <br/> |Failover til en alternativ ExpressRoute-forbindelse  <br/> |
|Direkte forbindelse med en forudsigelig netværksprofil.  <br/> |Nej  <br/> |Ja  <br/> |
|IPv6-forbindelse.  <br/> |Ja  <br/> |Ja  <br/> |

Udvid titlerne nedenfor for at få mere vejledning til netværksplanlægning. Vi har også optaget en 10-dels [Azure ExpressRoute til Office 365 træningsserie](https://channel9.msdn.com/series/aer), der dykker dybere ned.

## <a name="existing-azure-expressroute-customers"></a>Eksisterende Azure ExpressRoute-kunder

Hvis du bruger et eksisterende Azure ExpressRoute-kredsløb og gerne vil tilføje Office 365 forbindelse via dette kredsløb, bør du se på antallet af kredsløb, udgående placeringer og størrelsen af kredsløbene for at sikre, at de opfylder behovene for din Office 365 brug. De fleste kunder kræver ekstra båndbredde, og mange kræver flere kredsløb.
  
Hvis du vil give adgang til Office 365 via dine eksisterende Azure ExpressRoute-kredsløb, skal du [konfigurere rutefiltrene](/azure/expressroute/how-to-routefilter-portal) for at sikre, at de Office 365 tjenester er tilgængelige.
  
Azure ExpressRoute-abonnementet er kundecentreret, hvilket betyder, at abonnementer er knyttet til kunder. Som kunde kan du have flere Azure ExpressRoute-kredsløb og få adgang til mange Microsoft-cloudressourcer via disse kredsløb. Du kan f.eks. vælge at få adgang til en Azure-hostet virtuel maskine, en Office 365 testlejer og en Office 365 produktionslejer over et par redundante Azure ExpressRoute-kredsløb.
  
I denne tabel beskrives de to typer peeringrelationer, du kan vælge at implementere via dine kredsløb.

|**Peering-relation**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Tjenester** <br/> |IaaS: Azure Virtual Machines  <br/> |PaaS: Offentlige Azure-tjenester  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Start af forbindelse**** <br/> |Kunde til Microsoft  <br/> Microsoft-til-kunde  <br/> |Kunde til Microsoft  <br/> Microsoft-til-kunde  <br/> |
|**QoS-support** <br/> |Ingen QoS  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> QoS understøtter kun Skype for Business på nuværende tidspunkt.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planlægning af båndbredde for Azure ExpressRoute

Hver Office 365 kunde har unikke båndbreddebehov afhængigt af antallet af personer på hvert sted, hvor aktive de er med hver Office 365 program og andre faktorer, f.eks. brugen af lokalt eller hybridudstyr og konfigurationer af netværkssikkerhed.
  
Hvis båndbredden er for lille, vil det medføre overbelastning, videretransmission af data og uforudsigelige forsinkelser. Hvis du har for meget båndbredde, medfører det unødvendige omkostninger. På et eksisterende netværk refereres der ofte til båndbredden i forhold til mængden af tilgængelig headroom på kredsløbet som en procentdel. Hvis der er 10 % headroom, vil det sandsynligvis medføre overbelastning, og hvis der er 80 % headroom, betyder det generelt unødvendige omkostninger. Typiske headroom måltildelinger er 20% til 50%.
  
For at finde det rigtige båndbreddeniveau er den bedste mekanisme at teste dit eksisterende netværksforbrug. Dette er den eneste måde at få en sand måling af brug og behov, da alle netværkskonfigurationer og -programmer på nogle måder er unikke. Når du måler, skal du være opmærksom på det samlede båndbreddeforbrug, ventetid og TCP-overbelastning for at forstå dine netværksbehov.
  
Når du har en anslået baseline, der omfatter alle netværksprogrammer, kan du styre Office 365 med en lille gruppe, der består af de forskellige profiler af personer i din organisation for at bestemme det faktiske forbrug, og bruge de to målinger til at estimere den mængde båndbredde, du skal bruge for hver kontorplacering. Hvis der er problemer med ventetid eller TCP-overbelastning i din test, skal du muligvis flytte udgående data tættere på de personer, der bruger Office 365 eller fjerne intensiv netværksscanning, f.eks. SSL-dekryptering/inspektion.
  
Alle vores anbefalinger til, hvilken type netværksbehandling der anbefales, gælder for både ExpressRoute- og internetkredsløb. Det samme gælder for resten af vejledningen på vores [websted til justering af ydeevne](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Anvendelse af sikkerhedskontroller på Azure ExpressRoute i Office 365 scenarier

Sikring af Azure ExpressRoute-forbindelse starter med de samme principper som sikring af internetforbindelse. Mange kunder vælger at installere netværks- og perimeterkontrolelementer langs ExpressRoute-stien, der forbinder deres lokale netværk med Office 365 og andre Microsoft-cloudmiljøer. Disse kontrolelementer kan omfatte firewalls, programproxyer, forebyggelse af datalækage, registrering af indtrængen, systemer til forebyggelse af indtrængen osv. I mange tilfælde anvender kunder forskellige niveauer af kontrolelementer for trafik, der startes fra det lokale miljø, og som går til Microsoft, i forhold til trafik, der startes fra Microsoft, når de går til kundenetværket i det lokale miljø, i forhold til trafik, der er startet fra det lokale miljø, og som går til en generel internetdestination.
  
Her er et par eksempler på integration af sikkerhed med den [ExpressRoute-forbindelsesmodel,](/azure/expressroute/expressroute-connectivity-models) du vælger at udrulle.

|**ExpressRoute-integrationsmulighed**|**Perimetermodel for netværkssikkerhed**|
|:-----|:-----|
|Samlokeret på en cloududveksling  <br/> |Installér ny, eller brug eksisterende sikkerheds-/perimeterinfrastruktur i den colocationsfacilitet, hvor ExpressRoute-forbindelsen er etableret.  <br/> Brug colocationsfacilitet udelukkende til routing-/interconnect-formål og back-træk-forbindelser fra colocationsfaciliteten til sikkerheds-/perimeterinfrastrukturen i det lokale miljø.  <br/> |
|Point-to-Point Ethernet  <br/> |Afslut Point-to-Point ExpressRoute-forbindelsen på den eksisterende placering af sikkerheds-/perimeterinfrastrukturen i det lokale miljø.  <br/> Installer ny sikkerheds-/perimeterinfrastruktur, der er specifik for ExpressRoute-stien, og afslut Point-to-Point-forbindelsen der.  <br/> |
|Enhver-til-enhver IPVPN  <br/> |Brug en eksisterende sikkerheds-/perimeterinfrastruktur i det lokale miljø på alle placeringer, der ankommer til DET IPVPN, der bruges til ExpressRoute til Office 365 forbindelse.  <br/> Frigør DEN IPVPN, der bruges til ExpressRoute til Office 365 til specifikke placeringer i det lokale miljø, der er udpeget til at fungere som sikkerheds-/perimeter.  <br/> |

Nogle tjenesteudbydere tilbyder også administreret sikkerheds-/perimeterfunktionalitet som en del af deres integrationsløsninger med Azure ExpressRoute.
  
Når du overvejer topologiplaceringen af de netværks-/sikkerhedsperimeterindstillinger, der bruges til ExpressRoute til Office 365 forbindelser, er følgende ekstra overvejelser
  
- Dybde- og typekontrolelementerne for netværk/sikkerhed kan have indflydelse på ydeevnen og skalerbarheden af den Office 365 brugeroplevelse.

- Udgående (i det lokale miljø-Microsoft\>) og indgående (Microsoft-i\> det lokale miljø) [hvis aktiveret] flow kan have forskellige krav. Disse er sandsynligvis anderledes end udgående til generelle internetdestinationer.

- Office 365 krav til porte/protokoller og nødvendige IP-undernet er de samme, uanset om trafikken dirigeres via ExpressRoute for Office 365 eller via internettet.

- Topologisk placering af kundenetværket/sikkerhedskontrollerne bestemmer det endelige ende-til-slut-netværk mellem brugeren og Office 365-tjenesten og kan have stor indvirkning på netværksventetid og overbelastning.

- Kunder opfordres til at designe deres sikkerheds-/perimetertopologi til brug sammen med ExpressRoute til Office 365 i overensstemmelse med bedste praksis for redundans, høj tilgængelighed og it-katastrofeberedskab.

Her er et eksempel på Woodgrove Bank, der sammenligner de forskellige muligheder for Azure ExpressRoute-forbindelse med de perimetersikkerhedsmodeller, der er beskrevet ovenfor.
  
### <a name="example-1-securing-azure-expressroute"></a>Eksempel 1: Sikring af Azure ExpressRoute
  
Woodgrove Bank overvejer at implementere Azure ExpressRoute, og efter at have planlagt den optimale arkitektur for [routing med ExpressRoute til Office 365](routing-with-expressroute.md) og efter at have brugt ovenstående vejledning til at forstå båndbreddekrav, bestemmer de den bedste metode til sikring af deres perimeter.
  
For Woodgrove, en multinational organisation med placeringer på flere kontinenter, skal sikkerheden spænde over alle perimeterer. Den optimale forbindelsesmulighed for Woodgrove er en multipunktforbindelse med flere peering-placeringer over hele verden for at servicere deres medarbejderes behov på hvert kontinent. Hvert kontinent indeholder redundante Azure ExpressRoute-kredsløb på kontinentet, og sikkerhed skal spænde over alle disse.
  
Woodgroves eksisterende infrastruktur er pålidelig og kan håndtere det ekstra arbejde, og Woodgrove Bank kan derfor bruge infrastrukturen til deres Azure ExpressRoute- og internetperimetersikkerhed. Hvis dette ikke var tilfældet, kunne Woodgrove vælge at købe mere udstyr til at supplere deres eksisterende udstyr eller til at håndtere en anden type forbindelse.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Høj tilgængelighed og failover med Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Vi anbefaler, at du klargør mindst to aktive kredsløb fra hver udgående forbindelse med ExpressRoute til din ExpressRoute-udbyder. Dette er det mest almindelige sted, hvor vi ser fejl for kunder, og du kan nemt undgå det ved at klargøre et par aktive/aktive ExpressRoute-kredsløb. Vi anbefaler også mindst to aktive/aktive internetkredsløb, fordi mange Office 365 tjenester kun er tilgængelige via internettet.
  
Inde i udgående punkt i dit netværk er mange andre enheder og kredsløb, der spiller en vigtig rolle i, hvordan folk opfatter tilgængelighed. Disse dele af dine forbindelsesscenarier er ikke omfattet af ExpressRoute eller Office 365 SLA'er, men de spiller en vigtig rolle i forbindelse med tilgængeligheden af tjenesten fra slutpunkt til slutpunkt, som opfattes af personer i din organisation.
  
Fokuser på de mennesker, der bruger og arbejder Office 365, hvis en fejl i en enkelt komponent ville påvirke folks oplevelse ved hjælp af tjenesten, se efter måder at begrænse den samlede procentdel af berørte personer. Hvis en failovertilstand er operationelt kompleks, skal du overveje folks oplevelse af lang tid til genoprettelse og søge efter driftsklare og automatiserede failovertilstande.
  
Uden for dit netværk har Office 365, ExpressRoute og din ExpressRoute-udbyder forskellige tilgængelighedsniveauer.
  
### <a name="service-availability"></a>Tjenestetilgængelighed
  
- Office 365 tjenester er omfattet af veldefinerede [serviceniveauaftaler](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement), som omfatter målepunkter for oppetid og tilgængelighed for individuelle tjenester. En af grundene til, at Office 365 kan opretholde så høje tjenestetilgængelighedsniveauer, er muligheden for, at individuelle komponenter problemfrit kan skifte mellem de mange Microsoft-datacentre ved hjælp af det globale Microsoft-netværk. Denne failover strækker sig fra datacenteret og netværket til de mange internet udgående punkter og muliggør failover problemfrit set fra de personer, der bruger tjenesten.

- ExpressRoute [leverer en SLA med 99,9 % tilgængelighed](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) på individuelle dedikerede kredsløb mellem Microsoft Network Edge og ExpressRoute-udbyderen eller partnerinfrastrukturen. Disse tjenesteniveauer anvendes på ExpressRoute-kredsløbsniveauet, som består af [to uafhængige forbindelser](/azure/expressroute/expressroute-introduction) mellem det redundante Microsoft-udstyr og netværksudbyderudstyret på hver peeringplacering.

### <a name="provider-availability"></a>Udbydertilgængelighed
  
- Microsofts ordninger på tjenesteniveau stopper hos din ExpressRoute-udbyder eller -partner. Dette er også det første sted, hvor du kan foretage valg, der påvirker dit tilgængelighedsniveau. Du bør nøje evaluere arkitekturen, tilgængeligheden og robusthedsegenskaberne, som din ExpressRoute-udbyder tilbyder mellem din netværksperimeter og din udbyderforbindelse på hver Microsoft-peeringplacering. Vær opmærksom på både de logiske og fysiske aspekter af redundans, peeringudstyr, OPERATØR-leverede WAN-kredsløb og eventuelle ekstra værditilføjningstjenester som NAT-tjenester eller administrerede firewalls.

### <a name="designing-your-availability-plan"></a>Design af din tilgængelighedsplan
  
Vi anbefaler på det kraftigste, at du planlægger og designer høj tilgængelighed og robusthed i dine komplette forbindelsesscenarier for Office 365. Et design skal inkludere;
  
- Der er ingen enkelte fejlpunkter, herunder både internet- og ExpressRoute-kredsløb.

- Minimering af antallet af berørte personer og varigheden af denne indvirkning for de mest forventede fejltilstande.

- Optimering til enkel, gentagelig og automatisk gendannelsesproces fra de mest forventede fejltilstande.

- Understøttelse af de fulde krav til netværkstrafik og -funktionalitet via redundante stier uden en væsentlig forringelse.

Dine forbindelsesscenarier skal omfatte en netværkstopologi, der er optimeret til flere uafhængige og aktive netværksstier til Office 365. Dette giver en bedre tilgængelighed fra ende til anden end en topologi, der kun er optimeret til redundans på individuel enhed- eller udstyrsniveau.
  
> [!TIP]
> Hvis dine brugere distribueres på tværs af flere kontinenter eller geografiske områder, og hver af disse placeringer opretter forbindelse via redundante WAN-kredsløb til en enkelt placering i det lokale miljø, hvor et enkelt ExpressRoute-kredsløb er placeret, vil dine brugere opleve mindre tilgængelighed fra ende til anden end et netværkstopologidesign, der omfatter uafhængige ExpressRoute-kredsløb, der forbinder de forskellige områder til den nærmeste peeringplacering.
  
Vi anbefaler, at der klargøres mindst to ExpressRoute-kredsløb, hvor hvert kredsløb opretter forbindelse til med en anden geografisk peeringplacering. Du skal klargøre dette aktive kredsløbspar for hvert område, hvor brugerne skal bruge ExpressRoute-forbindelse til Office 365 tjenester. Dette gør det muligt for hvert område at forblive forbundet under en katastrofe, der påvirker en større placering, f.eks. et datacenter eller en peeringplacering. Hvis du konfigurerer dem som aktive/aktive, kan slutbrugertrafik distribueres på tværs af flere netværksstier. Dette reducerer omfanget af berørte personer under afbrydelser af enhedens eller netværkets udstyr.
  
Vi anbefaler ikke, at du bruger et enkelt ExpressRoute-kredsløb med internettet som sikkerhedskopi.
  
### <a name="example-2-failover-and-high-availability"></a>Eksempel 2: Failover og høj tilgængelighed
  
Woodgrove Banks multigeografiske design har gennemgået en gennemgang af routing, båndbredde, sikkerhed og nu skal igennem en gennemgang af høj tilgængelighed. Woodgrove mener, at høj tilgængelighed dækker tre kategorier; robusthed, pålidelighed og redundans.
  
Robusthed gør det muligt for Woodgrove hurtigt at komme sig efter fejl. Pålidelighed giver Woodgrove mulighed for at tilbyde et ensartet resultat i systemet. Redundans gør det muligt for Woodgrove at flytte mellem en eller flere spejlede forekomster af infrastruktur.
  
I hver edgekonfiguration har Woodgrove redundante firewalls, proxyer og IDS. For Nordamerika har Woodgrove én edge-konfiguration i deres Dallas-datacenter og en anden edge-konfiguration i deres Virginia-datacenter. Det redundante udstyr på hvert sted giver robusthed til det pågældende sted.
  
Netværkskonfigurationen i Woodgrove Bank er baseret på nogle få nøgleprincipper:
  
- Inden for hvert geografisk område er der flere Azure ExpressRoute-kredsløb.

- Hvert kredsløb i et område kan understøtte al netværkstrafik i det pågældende område.

- Distribution foretrækker helt klart den ene eller den anden sti afhængigt af tilgængelighed, placering osv.

- Failover mellem Azure ExpressRoute-kredsløb sker automatisk uden yderligere konfiguration eller handling, der kræves af Woodgrove.

- Failover mellem internetkredsløb sker automatisk uden yderligere konfiguration eller handling, der kræves af Woodgrove.

I denne konfiguration kan Woodgrove Bank med redundans på det fysiske og virtuelle niveau tilbyde lokal robusthed, regional robusthed og global robusthed på en pålidelig måde. Woodgrove valgte denne konfiguration efter at have evalueret et enkelt Azure ExpressRoute-kredsløb pr. område samt muligheden for at mislykkes via internettet.
  
Hvis Woodgrove ikke kunne have flere Azure ExpressRoute-kredsløb pr. område, vil routingtrafik, der stammer fra Nordamerika til Azure ExpressRoute-kredsløbet i Asien og Stillehavsområdet, tilføje en uacceptabel ventetid, og den påkrævede KONFIGURATION af DNS-videresendelse tilføjer kompleksitet.
  
Det anbefales ikke at bruge internettet som en sikkerhedskopikonfiguration. Dette bryder Woodgroves pålidelighedsprincip, hvilket resulterer i en uoverensstemmende oplevelse ved hjælp af forbindelsen. Desuden vil manuel konfiguration være påkrævet for at udføre failover i forhold til de BGP-reklamer, der er konfigureret, NAT-konfiguration, DNS-konfiguration og proxykonfigurationen. Denne ekstra failover-kompleksitet øger den tid, det er nødvendigt at gendanne, og reducerer deres mulighed for at diagnosticere og foretage fejlfinding af de involverede trin.
  
Har du stadig spørgsmål om, hvordan du planlægger og implementerer trafikstyring eller Azure ExpressRoute? Læs resten af vores [vejledning til netværk og ydeevne](./network-planning-and-performance.md) eller [ofte stillede spørgsmål om Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Arbejde med Azure ExpressRoute-udbydere
<a name="BKMK_high-availability"> </a>

Vælg placeringen af dine kredsløb baseret på din båndbredde, ventetid, sikkerhed og planlægning af høj tilgængelighed. Når du kender de optimale placeringer, vil du gerne placere kredsløb, [gennemse den aktuelle liste over udbydere efter område](/azure/expressroute/expressroute-locations).
  
Samarbejd med din udbyder eller udbyderne om at vælge de bedste forbindelsesindstillinger, point-to-point, multi-point eller hostede. Husk, at du kan blande og matche forbindelsesmulighederne, så længe båndbredden og andre redundante komponenter understøtter din routing og design med høj tilgængelighed.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner
<a name="BKMK_high-availability"> </a>

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Implementering af ExpressRoute for Office 365](implementing-expressroute.md)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimering af netværket til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow ved hjælp af ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevne](network-planning-and-performance.md)
  
[Ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)