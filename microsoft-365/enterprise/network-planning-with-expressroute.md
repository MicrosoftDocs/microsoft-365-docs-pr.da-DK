---
title: Netværksplanlægning med ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel får du mere at vide om Azure ExpressRoute til Office 365 og hvordan du bruger det til netværksplanlægning.
ms.openlocfilehash: d411d44ffe08da684b3cbca9a9449c4d04126a39
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63590573"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Netværksplanlægning med ExpressRoute til Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

ExpressRoute til Office 365 leverer Layer 3-forbindelse mellem dit netværk og Microsofts datacentre. Kredsløbene bruger Border Gateway Protocol(BGP)-ruteannonceringerne for Office 365's front end-servere. Set fra dine lokale enheders perspektiv, når de skal vælge den korrekte TCP/IP-sti til Office 365, ses Azure ExpressRoute som et alternativ til internettet.
  
Azure ExpressRoute tilføjer en direkte sti til et bestemt sæt understøttede funktioner og tjenester, der tilbydes af Office 365-servere inden for Microsofts datacentre. Azure ExpressRoute erstatter ikke internetforbindelsen til Microsofts datacentre eller grundlæggende internettjenester som domænenavnsopløsning. Azure ExpressRoute og dine internetkredsløb skal være sikret og redundante.
  
Følgende tabel fremhæver nogle forskelle mellem internettet og Azure ExpressRoute-forbindelser i forbindelse med Office 365.

|**Forskelle i netværksplanlægning**|**Internetnetværksforbindelse**|**ExpressRoute-netværksforbindelse**|
|:-----|:-----|:-----|
| Adgang til nødvendige internettjenester, herunder;  <br/>  DNS-navneopløsning  <br/>  Bekræftelse af tilbagekaldelse af certifikat  <br/>  Content Delivery Networks (CDN'er)  <br/> |Ja  <br/> |Anmodninger til Microsoft-ejet DNS og/eller CDN-infrastruktur kan bruge ExpressRoute-netværket.  <br/> |
| Adgang til Office 365 tjenester, herunder;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office i en browser  <br/>  Office 365 portal og godkendelse  <br/> |Ja, alle programmer og funktioner  <br/> |Ja, [bestemte programmer og funktioner](./urls-and-ip-address-ranges.md) <br/> |
|Lokal perimetersikkerhed.  <br/> |Ja  <br/> |Ja  <br/> |
|Planlægning af høj tilgængelighed.  <br/> |Fail over to an alternate internet network connection  <br/> |Fail over to an alternate ExpressRoute connection  <br/> |
|Direkte forbindelse med en forudsigelig netværksprofil.  <br/> |Nej  <br/> |Ja  <br/> |
|IPv6-forbindelse.  <br/> |Ja  <br/> |Ja  <br/> |

Udvid titlerne nedenfor for at få mere vejledning i netværksplanlægning. Vi har også indspillet en Azure ExpressRoute i 10 dele [til Office 365 kursusserier](https://channel9.msdn.com/series/aer), der går dybere ned.

## <a name="existing-azure-expressroute-customers"></a>Eksisterende Azure ExpressRoute-kunder

Hvis du bruger et eksisterende Azure ExpressRoute-kredsløb og gerne vil tilføje Office 365-forbindelse over dette kredsløb, skal du se på antallet af kredsløb, udgangspunktplaceringer og størrelsen af kredsløbene for at sikre, at de opfylder behovene i dit Office 365-forbrug. De fleste kunder kræver ekstra båndbredde, og mange kræver flere kredsløb.
  
Hvis du vil aktivere adgang Office 365 adgang til dine eksisterende Azure ExpressRoute-kredsløb[, skal](/azure/expressroute/how-to-routefilter-portal) du konfigurere rutefiltrene for at sikre, at Office 365-tjenesterne er tilgængelige.
  
Azure ExpressRoute-abonnementet er kundecentreret, hvilket betyder, at abonnementer er bundet til kunder. Som kunde kan du have flere Azure ExpressRoute-kredsløb og få adgang til mange Microsoft-skyressourcer over disse kredsløb. Du kan f.eks. vælge at få adgang til en virtuel maskine, der er hostet af Azure, en Office 365-testlejer og en Office 365-produktionslejer over et par redundante Azure ExpressRoute-kredsløb.
  
Denne tabel beskriver de to typer peeringrelationer, du kan vælge at implementere over dine kredsløb.

|**Peering-relation**|**Azure privat**|**Microsoft**|
|:-----|:-----|:-----|
|**Tjenester** <br/> |IaaS: Azure Virtual Machines  <br/> |PaaS: Offentlige Azure-tjenester  <br/> SaaS: Office 365  <br/> Saas: Dynamics 365  <br/> |
|Connection initiation**** <br/> |Kunde-til-Microsoft  <br/> Microsoft-til-kunde  <br/> |Kunde-til-Microsoft  <br/> Microsoft-til-kunde  <br/> |
|**QoS-support** <br/> |Ingen QoS  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> QoS understøtter Skype for Business på nuværende tidspunkt.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planlægning af båndbredde for Azure ExpressRoute

Hver Office 365-kunde har unikke båndbreddebehov afhængigt af antallet af personer på hver placering, hvor aktive de er med hvert Office 365-program og andre faktorer, f.eks. brug af lokalt eller hybridt udstyr og netværkssikkerhedskonfigurationer.
  
For lav båndbredde medfører overbelastning, retransmission af data og uforudsete forsinkelser. For høj båndbredde medfører unødvendige omkostninger. På et eksisterende netværk refereres der ofte til båndbredde i forbindelse med mængden af tilgængelig kapacitet på kredsløbet som en procentdel. En kapacitet på 10 % vil sandsynligvis resultere i overbelastning, og en kapacitet på 80 % betyder generelt unødvendige omkostninger. En typisk målet for en kapacitet er fra 20 til 50 %.
  
Den bedste mekanisme til at finde det rigtige niveau af båndbredde er at teste dit eksisterende netværksforbrug. Dette er den eneste måde at få et rigtigt mål for brug og behov, da alle netværkskonfigurationer og programmer på nogle måder er unikke. Når du måler, skal du være opmærksom på det samlede båndbreddeforbrug, ventetid og TCP-overbelastning for at forstå dine netværksbehov.
  
Når du har en anslået oprindelig plan, der omfatter alle netværksprogrammer, skal du prøve Office 365 med en lille gruppe, der består af de forskellige profiler for personer i organisationen til at bestemme det faktiske forbrug, og bruge de to målinger til at anslå mængden af båndbredde, du skal bruge for hver kontorplacering. Hvis der er problemer med ventetid eller TCP-overbelastning i din test, skal du muligvis flytte udgangspunktet tættere på de personer, der bruger Office 365 eller fjerne krævende netværksscanning, f.eks SSL-dekryptering/inspektion.
  
Alle vores anbefalinger om, hvilken type netværksbehandling der anbefales, gælder for både ExpressRoute og Internetkredsløb. Det samme gælder for resten af vejledningen på vores websted til [justering af ydeevnen](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Anvendelse af sikkerhedskontrolelementer på Azure ExpressRoute Office 365 scenarier

Sikring af Azure ExpressRoute-forbindelsen starter med de samme principper som sikring af internetforbindelsen. Mange kunder vælger at implementere netværks- og perimeterkontrolelementer langs ExpressRoute-stien for at forbinde deres lokale netværk til Office 365 og andre Microsoft-skyer. Disse kontrolelementer kan omfatte firewalls, program proxyer, forebyggelse af datalækage, registrering af indtrængen, systemer til forebyggelse af indtrængen og så videre. I mange tilfælde anvender kunder forskellige niveauer af kontrolelementer til trafik, der startes lokalt og går til Microsoft, kontra trafik, der startes fra Microsoft, og som går til et lokalt netværk hos kunden, kontra trafik, der startes fra det lokale miljø og går til en generel internetdestination.
  
Her er et par eksempler på integration af sikkerhed med den [ExpressRoute-forbindelsesmodel,](/azure/expressroute/expressroute-connectivity-models) du vælger at installere.

|**Integrationsindstillingen ExpressRoute**|**Perimetermodel for netværkssikkerhed**|
|:-----|:-----|
|Coloceret på en skyudveksling  <br/> |Installer ny eller brug eksisterende sikkerheds-/perimeterinfrastruktur i colocation-facilitet, hvor ExpressRoute-forbindelsen etableres.  <br/> Brug kun colocationfaciliteter udelukkende til routing-/forbindelsesformål og back-transportforbindelser fra colocationfaciliteter til den lokale sikkerheds-/perimeterinfrastruktur.  <br/> |
|Punkt-til-punkt-Ethernet  <br/> |Afslut punkt-til-punkt-ExpressRoute-forbindelsen i den eksisterende lokale sikkerheds-/perimeterinfrastrukturplacering.  <br/> Installer ny sikkerheds-/perimeterinfrastruktur, der er specifik for ExpressRoute-stien, og afslut punkt-til-punkt-forbindelsen der.  <br/> |
|En-til-en IPVPN  <br/> |Brug en eksisterende lokal sikkerheds-/perimeterinfrastruktur på alle placeringer, der går ind i den IPVPN, der bruges til ExpressRoute til Office 365 forbindelse.  <br/> Hairpin den IPVPN, der bruges til ExpressRoute til Office 365 bestemte lokale placeringer, der er udpeget til at tjene som sikkerhed/perimeter.  <br/> |

Nogle tjenesteudbydere tilbyder også administreret sikkerheds-/perimeterfunktionalitet som en del af deres integrationsløsninger med Azure ExpressRoute.
  
Når du overvejer den topologiske placering af de netværks-/sikkerhedsperimeterindstillinger, der bruges til ExpressRoute til Office 365 forbindelser, er følgende ekstra overvejelser
  
- Dybden og typen af netværks-/sikkerhedskontrolelementer kan påvirke ydeevnen og skalerbarheden af Office 365 brugeroplevelsen.

- Udgående (i det lokale miljø-Microsoft\>) og indgående (Microsoft-on-premises\>) [hvis aktiveret] flows kan have forskellige krav. Disse er sandsynligvis anderledes end udgående til generelle internetdestinationer.

- Office 365 krav til porte/protokoller og nødvendige IP-undernet er de samme, uanset om trafikken dirigeres gennem ExpressRoute til Office 365 eller via internettet.

- Den topologiske placering af kundens netværk/sikkerhedskontrolelementer bestemmer det ultimative slutpunkt til slutpunkt-netværk mellem brugeren og Office 365-tjenesten og kan have en betydelig indvirkning på netværksventetid og overbelastning.

- Kunder opfordres til at designe deres sikkerheds-/perimetertopologi til brug med ExpressRoute til Office 365 i overensstemmelse med bedste praksis for redundans, høj tilgængelighed og genoprettelse efter nedbrud.

Her er et eksempel på Woodgrove Bank, der sammenligner de forskellige Azure ExpressRoute-forbindelsesindstillinger med de perimetersikkerhedsmodeller, der er nævnt ovenfor.
  
### <a name="example-1-securing-azure-expressroute"></a>Eksempel 1: Sikring af Azure ExpressRoute
  
Woodgrove Bank overvejer at implementere Azure ExpressRoute, og efter at have planlagt den optimale arkitektur for [Routing med ExpressRoute til Office 365](routing-with-expressroute.md) og efter at have brugt ovenstående vejledning til at forstå kravene til båndbredde beslutter de sig for den bedste metode til at sikre deres perimeter.
  
For Woodgrove, som er en flerlandsorganisation med placeringer på flere kontinenter, skal sikkerheden strække sig over alle perimeterer. Den optimale forbindelsesindstilling for Woodgrove er en flerpunktsforbindelse med flere peeringplaceringer i hele verden, så deres medarbejderes behov kan serviceres på hvert kontinent. Hver kontinent omfatter redundante Azure ExpressRoute-kredsløb inden for kontinentet, og sikkerheden skal strække sig over alle disse.
  
Woodgroves eksisterende infrastruktur er pålidelig og kan håndtere det ekstra arbejde. Derfor kan Woodgrove Bank bruge infrastrukturen til deres Azure ExpressRoute og internetperimetersikkerhed. Hvis det ikke var tilfældet, kunne Woodgrove vælge at købe mere udstyr for at supplere deres eksisterende udstyr eller for at håndtere en anden type forbindelse.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Høj tilgængelighed og failover med Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Vi anbefaler klargøring af mindst to aktive kredsløb fra hvert udgangspunkt med ExpressRoute til din ExpressRoute-udbyder. Dette er det mest almindelige sted, vi ser fejl for kunder, og du kan nemt undgå det ved at klargøre et par aktive/aktive ExpressRoute-kredsløb. Vi anbefaler også mindst to aktive/aktive internetkredsløb, da mange Office 365-tjenester kun er tilgængelige via internettet.
  
I udgangspunktet for dit netværk findes mange andre enheder og kredsløb, der spiller en vigtig rolle i, hvordan folk opfatter tilgængelighed. Disse dele af dine forbindelsesscenarier er ikke dækket af ExpressRoute eller Office 365 SLA'er, men de spiller en vigtig rolle for tjenestens tilgængelighed i sidste ende som opfattet af personer i organisationen.
  
Fokuser på de personer, der bruger og bruger Office 365. Hvis en fejl i en af komponenterne påvirker folks oplevelse med at bruge tjenesten, skal du se efter metoder til at begrænse den samlede procentdel af personer, der påvirkes. Hvis en failovertilstand er driftsmæssig kompleks, bør du overveje personers oplevelse af lang tid inden genoprettelse og lede efter driftsmæssige enkle og automatiske failovertilstande.
  
Uden for dit netværk har Office 365, ExpressRoute og din ExpressRoute-udbyder alle forskellige tilgængelighedsniveauer.
  
### <a name="service-availability"></a>Tjenestens tilgængelighed
  
- Office 365-tjenester er dækket af veldefinerede [serviceaftaler](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement), som omfatter målepunkter for oppetid og tilgængelighed for individuelle tjenester. En af grundene Office 365 at opretholde så høje tilgængelighedsniveauer for tjenesten er muligheden for, at individuelle komponenter problemfrit mislykkes mellem de mange Microsoft-datacentre ved hjælp af det globale Microsoft-netværk. Denne failover går fra datacenteret og netværket til flere internet udgangspunkter og muliggør problemfri failover, set fra de personer, der bruger tjenesten.

- ExpressRoute [leverer en SLA for 99,9 %](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) tilgængelighed på individuelle dedikerede kredsløb mellem Microsoft Network Edge og ExpressRoute-udbyderen eller partnerinfrastrukturen. Disse serviceniveauer anvendes på ExpressRoute-kredsløbsniveauet, som består af to [](/azure/expressroute/expressroute-introduction) uafhængige forbindelser mellem det redundante Microsoft-udstyr og netværkudbyderens udstyr i hver peeringplacering.

### <a name="provider-availability"></a>Udbyderens tilgængelighed
  
- Microsofts serviceaftaler stopper hos din ExpressRoute-udbyder eller -partner. Dette er også det første sted, du kan foretage valg, der påvirker dit tilgængelighedsniveau. Du bør evaluere arkitektur, tilgængelighed og fleksibilitet, som din ExpressRoute-udbyder tilbyder mellem din netværksperimeter og din udbyderforbindelse på hver Microsoft-peeringplacering. Vær opmærksom på både de logiske og fysiske aspekter af redundans, peeringudstyr, udbyderen leverede WAN-kredsløb og ekstra værditilf00 tjenester som NAT-tjenester eller administrerede firewalls.

### <a name="designing-your-availability-plan"></a>Designe din tilgængelighedsplan
  
Vi anbefaler på det kraftigste, at du planlægger og designer høj tilgængelighed og fleksibilitet til dine slutpunkt-til-slutpunkt-forbindelsesscenarier for Office 365. Et design bør omfatte:
  
- Ingen enkelte fejlpunkter, herunder både internet- og ExpressRoute-kredsløb.

- Minimering af antallet af personer, der påvirkes, og varigheden af den pågældende påvirkning for de mest forventede fejltilstande.

- Optimering af enkel, gentaget og automatisk gendannelsesproces fra de mest forventede fejltilstande.

- Understøttelse af de fulde krav fra din netværkstrafik og funktionalitet via redundante stier uden betydelig forringelse.

Forbindelsesscenarierne skal omfatte en netværktopologi, der er optimeret til flere uafhængige og aktive netværksstier for at Office 365. Dette giver en bedre end-til-ende tilgængelighed end en topologi, der er optimeret udelukkende til redundans for den enkelte enhed eller det enkelte udstyr.
  
> [!TIP]
> Hvis brugerne er fordelt på tværs af flere kontinenter eller geografiske områder, og hver af disse placeringer opretter forbindelse via redundante WAN-kredsløb til en enkelt lokal placering, hvor et enkelt ExpressRoute-kredsløb er placeret, vil dine brugere opleve mindre tilgængelighed fra slutpunkt til slutpunkt-tjenesten end et netværk topologidesign, der omfatter uafhængige ExpressRoute-kredsløb, der forbinder de forskellige områder til den nærmeste peeringplacering.
  
Vi anbefaler klargøring af mindst to ExpressRoute-kredsløb med hvert kredsløb, der opretter forbindelse til med en anden geografisk peeringplacering. Du skal klargøre dette aktive par kredsløb for hvert område, hvor folk skal bruge ExpressRoute-forbindelsen til Office 365 tjenester. Dette giver mulighed for, at hvert område forbliver forbundet under nedbrud, der påvirker et større område, f.eks. et datacenter eller peeringplacering. Når du konfigurerer dem som aktive/aktive, kan slutbrugerens trafik fordeles på tværs af flere netværksstier. Dette reducerer omfanget af personer, der påvirkes under enheders eller netværksudstyrsafbrydelser.
  
Vi anbefaler ikke, at du bruger et enkelt ExpressRoute-kredsløb med internettet som en sikkerhedskopi.
  
### <a name="example-2-failover-and-high-availability"></a>Eksempel 2: Failover og høj tilgængelighed
  
Woodgrove Banks multiografiske design har gennemgået en vurdering af routing, båndbredde, sikkerhed og skal nu gå gennem en vurdering af høj tilgængelighed. Woodgrove mener, at høj tilgængelighed dækker tre kategorier: fleksibilitet, pålidelighed og redundans.
  
Med fleksibilitet kan Woodgrove hurtigere komme i gang efter nedbrud. Med pålidelighed kan Woodgrove tilbyde et konsistent resultat i systemet. Med redundans kan Woodgrove flytte mellem en eller flere spejlede forekomster af infrastruktur.
  
Inden for hver kantkonfiguration har Woodgrove redundante firewalls, proxyer og IDS. For Nordamerika har Woodgrove én kantkonfiguration i deres datacenter i Dallas og en anden kantkonfiguration i deres datacenter i Virginia. Det redundante udstyr på hver enkelt placering tilbyder fleksibilitet til den nye placering.
  
Netværkskonfigurationen i Woodgrove Bank er bygget på baggrund af nogle få nøgle principper:
  
- Inden for hvert geografisk område er der flere Azure ExpressRoute-kredsløb.

- Hvert kredsløb i et område kan understøtte al netværkstrafik i det pågældende område.

- Routing vil tydeligt foretrække den ene eller den anden sti afhængigt af tilgængelighed, placering osv.

- Failover mellem Azure ExpressRoute-kredsløb sker automatisk, uden der kræves yderligere konfiguration eller handling af Woodgrove.

- Failover mellem internetkredsløb sker automatisk, uden der kræves yderligere konfiguration eller handling af Woodgrove.

I denne konfiguration med redundans på det fysiske og virtuelle niveau kan Woodgrove Bank tilbyde lokal, regional og global fleksibilitet på en pålidelig måde. Woodgrove valgte denne konfiguration efter evaluering af et enkelt Azure ExpressRoute-kredsløb pr. region samt muligheden for mislykket over til internettet.
  
Hvis Woodgrove ikke kunne have flere Azure ExpressRoute-kredsløb pr. region, ville routing af trafik fra Nordamerika til Azure ExpressRoute-kredsløbet i Asien/Stillehavsområdet give en uacceptabel ventetid, og den påkrævede DNS-videresendelseskonfiguration tilføjer kompleksitet.
  
Det anbefales ikke at bruge internettet som en sikkerhedskopieringskonfiguration. Dette bryder Woodgroves pålidelighedsprincip, hvilket resulterer i en inkonsekvent oplevelse ved brug af forbindelsen. Desuden kan manuel konfiguration mislykkes i betragtning af de BGP-annoncer, der er konfigureret, NAT-konfiguration, DNS-konfiguration og proxykonfigurationen. Denne ekstra failoverkompleksitet øger tiden til gendannelse og mindsker deres mulighed for at diagnosticere og foretage fejlfinding af de pågældende trin.
  
Har du stadig spørgsmål om planlægning og implementering af trafikstyring eller Azure ExpressRoute? Læs resten af vores netværks [- og ydeevnevejledning eller](./network-planning-and-performance.md) Ofte stillede [spørgsmål om Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Arbejde med Azure ExpressRoute-udbydere
<a name="BKMK_high-availability"> </a>

Vælg de placeringer af dine kredsløb, der er baseret på din båndbredde, ventetid, sikkerhed og planlægning af høj tilgængelighed. Når du kender de optimale placeringer, vil du gerne placere kredsløb gennemgå [den aktuelle liste over udbydere efter område](/azure/expressroute/expressroute-locations).
  
Arbejd med din udbyder eller udbydere for at vælge de bedste forbindelsesindstillinger, punkt-til-punkt, multipunkt eller hostet. Husk, at du kan blande og matche forbindelsesmulighederne, så længe båndbredden og andre redundante komponenter understøtter dit routing- og høj tilgængelighedsdesign.
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Relaterede emner
<a name="BKMK_high-availability"> </a>

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Routing med ExpressRoute til Office 365](routing-with-expressroute.md)
  
[Implementering af ExpressRoute til Office 365](implementing-expressroute.md)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimere dit netværk til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow med ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevnen](network-planning-and-performance.md)
  
[Office 365 ofte stillede spørgsmål om slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)