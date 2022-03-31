---
title: Routing med ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: I denne artikel kan du få mere at vide om Azure ExpressRoute-routingkrav, kredsløb og routingdomæner til brug med Office 365.
ms.openlocfilehash: d6fab2dd9a7e7519eb1f56cebccaf345685cc0cd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63601566"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing med ExpressRoute til Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

For at forstå routing af trafik til Office 365 ved hjælp af Azure ExpressRoute skal du forstå de grundlæggende [krav til ExpressRoute-routing](/azure/expressroute/expressroute-routing) og [ExpressRoute-kredsløb og routingdomæner](/azure/expressroute/expressroute-circuit-peerings). Disse viser de grundlæggende ting for brug af ExpressRoute, Office 365 som kunderne er afhængige af.
  
Nogle af de vigtigste elementer i artiklerne ovenfor, som du skal forstå, omfatter:
  
- ExpressRoute-kredsløb er ikke knyttet til en bestemt fysisk infrastruktur, men er en logisk forbindelse, der er foretaget på en enkelt peeringplacering af Microsoft og en peeringudbyder på dine vegne.

- Der er en 1:1-tilknytning mellem et ExpressRoute-kredsløb og en kundes s-nøgle.

- Hvert kredsløb kan understøtte to uafhængige peeringrelationer (privat Azure-peering og Microsoft-peering). Office 365 kræver Microsoft-peering.

- Hvert kredsløb har en fast båndbredde, der deles på tværs af alle peeringrelationer.

- Alle offentlige IPv4-adresser og offentlige AS-numre, der skal bruges til ExpressRoute-kredsløbet, skal være valideret som ejet af dig eller tildelt udelukkende til dig af ejeren af adresseområdet.

- De virtuelle ExpressRoute-kredsløb er redundante og følger standarderne for BGP-routing. Dette er grunden til, at vi anbefaler to fysiske kredsløb pr. udgangspunkt til din udbyder i en aktiv/aktiv konfiguration.

Se siden med [ofte stillede spørgsmål](/azure/expressroute/expressroute-faqs) for at få flere oplysninger om tjenester, der understøttes, omkostninger og konfigurationsoplysninger. Se artiklen [om ExpressRoute-placeringer for at](/azure/expressroute/expressroute-locations) få oplysninger om listen over forbindelsesudbydere, der tilbyder Microsoft-peeringsupport. Vi har også indspillet en [Azure ExpressRoute](https://channel9.msdn.com/series/aer) i 10 dele til Office 365-kursusserie på kanal 9, der kan hjælpe med at forklare begreberne grundigere.
  
## <a name="ensuring-route-symmetry"></a>Sikre rutesymmetri

Front end Office 365-front end-servere er tilgængelige både på internettet og ExpressRoute. Disse servere vil foretrække at dirigere tilbage til lokale over ExpressRoute-kredsløb, når begge er tilgængelige. Derfor er der mulighed for ruteasymmetri, hvis trafikken fra dit netværk foretrækker at dirigere via dine internetkredsløb. Asymmetriske ruter er et problem, fordi enheder, der udfører STATEFUL-pakkeinspektion, kan blokere returtrafik, der følger en anden sti, end de udgående pakker fulgte.
  
Uanset om du starter en forbindelse til en Office 365 via internettet eller ExpressRoute, skal kilden være en offentlig adresse, der kan rouseres. For mange kunder med peering direkte hos Microsoft er det ikke muligt at have private adresser, hvor duplikering er muligt mellem kunder.
  
Følgende er scenarier, hvor kommunikation fra Office 365 til dit lokale netværk startes. For at forenkle dit netværksdesign anbefaler vi, at du distribuerer følgende via internetstien.
  
- SMTP-tjenester som f.eks. mail fra en Exchange Online-lejer til en lokal vært eller SharePoint-onlinemail, der sendes fra SharePoint Online til en lokal vært. SMTP-protokollen bruges mere bredt inden for Microsofts netværk end de rutepræfikser, der deles via ExpressRoute-kredsløb og annoncering af SMTP-servere i det lokale miljø over ExpressRoute, medfører fejl med disse andre tjenester.

- ADFS under adgangskodevalidering til at logge på.

- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid).

- [SharePoint hybridsøgning i organisationsnetværket](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS-hybrid](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business og](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)/eller [Skype for Business sammenslutning](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Skyforbindelse](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

For at Microsoft kan dirigere tilbage til dit netværk for disse tovejstrafikflows, skal BGP-ruterne til dine lokale enheder deles med Microsoft. Når du annoncerer rutepræfikser til Microsoft over ExpressRoute, skal du følge disse bedste fremgangsmåder:

1) Annoncer ikke det samme offentlige IP-adresserutepræfiks på det offentlige internet og over ExpressRoute. Det anbefales, at annonceringerne af IP BGP-rutepræfikser til Microsoft over ExpressRoute er fra et interval, der slet ikke er annonceret til internettet. Hvis dette ikke er muligt at opnå på grund af den tilgængelige IP-adresseplads, er det vigtigt at sikre, at du annoncerer et mere specifikt område over ExpressRoute end nogen internetkredsløb.

2) Brug separate NAT IP-puljer pr. ExpressRoute-kredsløb, og separate dem til dine internetkredsløb.

3) Alle ruter, der annonceres til Microsoft, vil tiltrække netværkstrafik fra enhver server i Microsofts netværk, ikke kun for dem, hvor ruter annonceres over for dit netværk via ExpressRoute. Annoncer kun ruter til servere, hvor routingscenarier defineres og forstås af dit team. Annoncer separate IP-adresserutepræfikser på hvert af flere ExpressRoute-kredsløb fra dit netværk.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Beslutte, hvilke programmer og funktioner der skal dirigeres over ExpressRoute

Når du konfigurerer en peeringrelation ved hjælp af Microsoft-peering-routingdomænet og er godkendt til den relevante adgang, vil du kunne se alle PaaS- og SaaS-tjenester, der er tilgængelige via ExpressRoute. De Office 365 tjenester, der er udviklet til ExpressRoute, kan administreres med [BGP-communities](./bgp-communities-in-expressroute.md) eller [rutefiltre](/azure/expressroute/how-to-routefilter-portal).
  
Hver af de Office 365, der er tilgængelige ved hjælp af Microsoft-peering, er angivet i [artiklen Office 365-slutpunkter](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) efter programtype og FQDN. Årsagen til at bruge FQDN i tabellerne er at tillade kunder at administrere trafik ved hjælp af PAC-filer eller andre proxykonfigurationer, se vores [](./managing-office-365-endpoints.md) vejledning til administration af Office 365-slutpunkter, f.eks PAC-filer.
  
I nogle situationer har vi brugt et jokerdomæne, hvor en eller flere under-FQDN'er annonceres anderledes end jokerdomænet på et højere niveau. Det sker normalt, når jokertegnet repræsenterer en lang liste over servere, der alle er annonceret til ExpressRoute og internettet, mens en lille delmængde af destinationer kun annonceres over for internettet eller det omvendte. Se tabellerne nedenfor for at forstå, hvor forskellene er.
  
Denne tabel viser FQDN'er med jokertegn, der er annonceret til både internettet og Azure ExpressRoute sammen med de under-FQDN'er, der kun er annonceret til internettet.

|**Jokerdomæne annonceret til ExpressRoute og internetkredsløb**|**Under-FQDN kun annonceret til internetkredsløb**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

Som regel er PAC-filer beregnet til at sende netværksanmodninger til ExpressRoute-annoncerede slutpunkter direkte til kredsløbet og alle andre netværksanmodninger til din proxyserver. Hvis du konfigurerer en PAC-fil på denne måde, skal du oprette PAC-filen i følgende rækkefølge:
  
1. Medtag under-FQDN'er fra kolonne to i ovenstående tabel øverst i PAC-filen, hvilket sender trafikken mod din proxyserver. Vi har oprettet en PAC-eksempelfil, som du kan bruge i vores artikel [om administration Office 365 slutpunkter](./managing-office-365-endpoints.md).

2. Medtag alle FQDN'er, der er markeret som [](./urls-and-ip-address-ranges.md) annonceret til ExpressRoute, i denne artikel under den første sektion, hvilket sender trafikken direkte til dit ExpressRoute-kredsløb.

3. Medtag andre netværksslutpunkter eller regler under disse to poster, hvilket sender trafikken mod din proxyserver.

Denne tabel viser de jokertegnsdomæner, der kun er annonceret til internetkredsløb sammen med de under-FQDN'er, der er annonceret til Azure ExpressRoute og Internetkredsløb. For PAC-filen ovenfor er FQDN'er i kolonne 2 i nedenstående tabel angivet som annonceret til ExpressRoute i det link, der refereres til, hvilket betyder, at de skal medtages i den anden gruppe af poster i filen.

|**Domæne med jokertegn kun annonceret til internetkredsløb**|**Under-FQDN annonceret til ExpressRoute og internetkredsløb**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing Office 365 trafik via internettet og ExpressRoute

Hvis du vil Office 365 det program, du vælger, skal du fastlægge en række vigtige faktorer.
  
1. Hvor meget båndbredde programmet kræver. Beregning af det eksisterende brug er den eneste pålidelige metode til at afgøre dette i organisationen.

2. Fra hvilket udgangspunkt/hvilke udgangspunkter ønsker du, at netværkstrafikken forlader dit netværk. Du skal planlægge at minimere netværksventetiden for forbindelsen til den Office 365 da dette vil påvirke ydeevnen. Da Skype for Business bruger stemme og video i realtid, er det udsat for dårlig netværksventetid.

3. Hvis du vil have alle eller et undersæt af dine netværksplaceringer til at bruge ExpressRoute.

4. Hvilke placeringer din valgte netværksudbyder tilbyder ExpressRoute fra.

Når du har svarene på disse spørgsmål, kan du klargøre et ExpressRoute-kredsløb, der opfylder kravene til båndbredde og placering. Du kan finde mere hjælp til netværksplanlægning i [Office 365](./network-planning-and-performance.md) vejledning til justering af netværk og casestudiet om, [hvordan Microsoft håndterer planlægningen af netværkets ydeevne](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Eksempel 1: Enkelt geografisk placering
  
Dette eksempel er et scenarie for et fiktivt firma kaldet Trey Research, der har en enkelt geografisk placering.
  
Medarbejdere på Trey Research har kun tilladelse til at oprette forbindelse til de tjenester og websteder på internettet, som sikkerhedsafdelingen udtrykkeligt giver tilladelse til på de to udgående proxyservere, der står mellem virksomhedens netværk og internetudbyderen.
  
Trey Research planlægger at bruge Azure ExpressRoute til Office 365 og genkender, at noget trafik som f.eks. trafik, der er beregnet til netværk til levering af indhold, ikke vil kunne dirigere over ExpressRoute til Office 365 forbindelse. Da al trafik allerede routes til proxyenhederne som standard, vil disse anmodninger fortsat fungere som før. Når Trey Research har bekræftet, at de kan opfylde kravene til Azure ExpressRoute-routing, fortsætter de med at oprette et kredsløb, konfigurere routing og sammenkæde det nye ExpressRoute-kredsløb med et virtuelt netværk. Når den grundlæggende Azure ExpressRoute-konfiguration er på plads, bruger Trey Research [#2 PAC-filen](./managing-office-365-endpoints.md), vi udgiver, til at dirigere trafik med kundespecifikke data over den direkte ExpressRoute til Office 365-forbindelser.
  
Som vist i følgende diagram kan Trey Research opfylde kravet om at dirigere Office 365-trafik via internettet og et undersæt af trafik over ExpressRoute ved hjælp af en kombination af konfigurationsændringer af routing og udgående proxy.
  
1. Brug af [#2 PAC-filen](./managing-office-365-endpoints.md), vi udgiver, til at dirigere trafik gennem et separat internetud udgangspunkt for Azure ExpressRoute til Office 365.

2. Klienter er konfigureret med en standardrute mod Trey Researchs proxyer.

I dette eksempelscenarie bruger Trey Research en udgående proxyenhed. På samme måde kan kunder, der ikke bruger Azure ExpressRoute til Office 365 bruge denne metode til at dirigere trafik baseret på prisen for at undersøge trafik, der er beregnet til kendte slutpunkter med stor volumen.
  
De højeste FQDN'er for Exchange Online, SharePoint Online og Skype for Business Online er følgende:
  
![ExpressRoute med kundekantnetværk.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com sammen med IP-intervallerne for ikke-TCP-trafik

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

Få mere at [vide om implementering og administration af proxyindstillinger i Windows 8](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) og [Office 365, at proxyen ikke bliver Office 365 af din proxyserver](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Med et enkelt ExpressRoute-kredsløb er der ingen høj tilgængelighed for Trey Research. I tilfælde af at Treys redundante grænseenheder, der servicerer ExpressRoute-forbindelsen, mislykkes, er der ikke et ekstra ExpressRoute-kredsløb, der mislykkes. Dette efterlader Trey Research i en knibe, da mislykkes over til internettet kræver manuel omkonfigurering og i nogle tilfælde nye IP-adresser. Hvis Trey ønsker at tilføje høj tilgængelighed, er den mest enkle løsning at tilføje ekstra ExpressRoute-kredsløb for hver placering og konfigurere kredsløbene på en aktiv/aktiv måde.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing af ExpressRoute til Office 365 med flere placeringer

Det sidste scenarie, routing Office 365 over ExpressRoute, er grundlaget for endnu mere kompleks routingarkitektur. Uanset antallet af steder, antal kontinenter, hvor disse placeringer findes, antal ExpressRoute-kredsløb og så videre kan det være nødvendigt at dirigere noget trafik til internettet og noget trafik over ExpressRoute.
  
De ekstra spørgsmål, der skal besvares for kunder med flere forskellige placeringer i flere geografiske områder, omfatter:
  
1. Kræver du et ExpressRoute-kredsløb på alle placeringer? Hvis du bruger Skype for Business Online eller er bekymret over følsomhed over for ventetiden for SharePoint Online eller Exchange Online, anbefales et redundant par aktive/aktive ExpressRoute-kredsløb på hver placering. Se vejledningen Skype for Business af mediekvalitet og netværksforbindelse for at få flere oplysninger.

2. Hvis et ExpressRoute-kredsløb ikke er tilgængeligt i et bestemt område, hvordan skal Office 365 bestemt trafik så dirigeres?

3. Hvad er den foretrukne metode til konsolidering af trafik i netværk med mange små placeringer?

Hver af disse præsenterer en unik udfordring, der kræver, at du evaluerer dit eget netværk og de indstillinger, der er tilgængelige fra Microsoft.

|**Overvejelse**|**Netværkskomponenter, der skal evalueres**|
|:-----|:-----|
|Kredsløb på mere end én placering  <br/> |Vi anbefaler et minimum af to kredsløb, der er konfigureret på en aktiv/aktiv måde.  <br/> Omkostninger, ventetid og båndbreddebehov skal sammenlignes.  <br/> Brug omkostninger til BGP-routing, PAC-filer og NAT til at administrere routing med flere kredsløb.  <br/> |
|Routing fra placeringer uden et ExpressRoute-kredsløb  <br/> |Vi anbefaler udgangspunkt og DNS-løsning så tæt på den person, der har startet anmodningen om Office 365.  <br/> DNS-videresendelse kan bruges til at give eksterne kontorer mulighed for at finde det relevante slutpunkt.  <br/> Klienter på fjernkontoret skal have en rute tilgængelig, der giver adgang til ExpressRoute-kredsløbet.  <br/> |
|Konsolidering af lille kontor  <br/> |Tilgængelig båndbredde og dataforbrug skal sammenlignes omhyggeligt.  <br/> |

> [!NOTE]
> Microsoft vil foretrække ExpressRoute via internettet, hvis ruten er tilgængelig uanset den fysiske placering.
  
Hver af disse overvejelser skal tages i betragtning for hvert entydige netværk. Nedenfor er et eksempel.
  
### <a name="example-2-multi-geographic-locations"></a>Eksempel 2: Flere geografiske placeringer
  
Dette eksempel er et scenarie for et fiktivt firma kaldet "Humongous Insurance", der har flere geografiske placeringer.
  
Humongous Insurance er geografisk spredt med kontorer over hele verden. De ønsker at implementere Azure ExpressRoute til Office 365 at bevare de fleste deres Office 365 trafik på direkte netværksforbindelser. Humongous Insurance har også kontorer på to yderligere kontinenter. Medarbejdere i fjernkontoret, hvor ExpressRoute ikke er muligt, skal dirigere tilbage til en eller begge af de primære faciliteter for at bruge en ExpressRoute-forbindelse.
  
Det ledende princip er at få Office 365 trafik, der er bestemt, til et Microsoft-datacenter så hurtigt som muligt. I dette eksempel skal Humongous Insurance beslutte, om deres fjernkontorer skal dirigere via internettet for at få adgang til et Microsoft-datacenter via en forbindelse så hurtigt som muligt, eller om deres fjernkontorer skal dirigere via et internt netværk for at komme til et Microsoft-datacenter via en ExpressRoute-forbindelse så hurtigt som muligt.
  
Microsofts datacentre, netværk og programarkitektur er designet til at tage globalt separat kommunikation og servicere dem på den mest effektive måde. Dette er et af de største netværk i verden. Anmodninger, der Office 365 der forbliver på kundens netværk længere end nødvendigt, vil ikke kunne udnytte denne arkitektur.
  
I Humongous Insurance's situation skal de fortsætte afhængigt af de programmer, de har til hensigt at bruge over ExpressRoute. Hvis de f.eks. er Skype for Business Online-kunder eller planlægger at bruge ExpressRoute-forbindelsen, når der oprettes forbindelse til eksterne Skype for Business Online-møder, anbefales det design i Skype for Business  Vejledning til online mediekvalitet og netværksforbindelse er at klargøre et ekstra ExpressRoute-kredsløb for den tredje placering. Dette kan være dyrere set i et netværksperspektiv; routing af anmodninger fra ét kontinent til et andet før levering til et Microsoft-datacenter kan medføre en dårlig eller ubrugelig oplevelse under Skype for Business onlinemøder og kommunikation.
  
Hvis Humongous Insurance ikke bruger eller har planer om at bruge Skype for Business Online på nogen måde, kan routing af netværkstrafik, der er bestemt til Office 365, tilbage til et kontinent med en ExpressRoute-forbindelse, være mulig, men det kan medføre unødvendig ventetid eller TCP-overbelastning. I begge tilfælde anbefales det at dirigere trafik, der er bestemt for internettet, til internettet på det lokale websted for at drage fordel af de netværk til levering af indhold, som Office 365 afhænger af.
  
![ExpressRoute multigeografisk.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Når Humongous Insurance planlægger deres multigege geografiske strategi, er der mange ting, de skal overveje vedrørende kredsløbsstørrelsen, antal kredsløb, failover osv.
  
Med ExpressRoute på en enkelt placering med flere områder, der forsøger at bruge kredsløbet, ønsker Humongous Insurance at sikre, at forbindelser til Office 365 fra fjernkontoret sendes til det Office 365-datacenter, der ligger nærmest hovedkontoret og modtages på hovedkontoret. For at gøre dette implementerer Humongous Insurance DNS-videresendelse for at reducere antallet af ture og DNS-opslag, der kræves for at oprette den relevante forbindelse med det Office 365-miljø, der er tættest på hovedkontorets internetud udgangspunkt. Dette forhindrer, at klienten løser en lokal front end-server og sikrer den Front-End-server, som personen opretter forbindelse til, for at være i nærheden af hovedkontoret, hvor Humongous Insurance peering med Microsoft. Du kan også lære at [tildele en betinget videresendelse for et domænenavn](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
I dette scenarie løser trafik fra fjernkontoret Office 365 front end-infrastrukturen i Nordamerika og bruger Office 365 til at oprette forbindelse til backendserverne i henhold til arkitekturen i Office 365-programmet. Eksempelvis ville Exchange Online afbryde forbindelsen i Nordamerika, og disse front end-servere ville oprette forbindelse til backendpostkasseserveren der, hvor lejeren var placeret. Alle tjenester har en alment distribueret front dørtjeneste bestående af unicast- og anycast-destinationer.
  
Hvis Humongous har større kontorer på flere kontinenter, anbefales mindst to aktive/aktive kredsløb pr. region for at reducere ventetiden for følsomme programmer, f.eks. Skype for Business Online. Hvis alle kontorer er på et enkelt kontinent eller ikke bruger samarbejde i realtid, er det en kundespecifik beslutning at have et konsolideret eller distribueret udgangspunkt. Når der er flere tilgængelige kredsløb, sikrer BGP-routing failover, hvis et enkelt kredsløb ikke længere er tilgængeligt.
  
Få mere at vide om [eksempel på routingkonfigurationer](/azure/expressroute/expressroute-config-samples-routing) og [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>Selektiv routing med ExpressRoute

Selektiv routing med ExpressRoute kan være nødvendig af forskellige årsager, f.eks test, udrulning af ExpressRoute til et undersæt af brugere. Der findes forskellige værktøjer, som kunderne kan bruge til selektivt at Office 365 netværkstrafik over ExpressRoute:
  
1. **Distribuere filtrering/opdeling – tillade** BGP-ruter at blive Office 365 over ExpressRoute til et undersæt af dine undernet eller routere. Dette ruter selektivt efter kundenetværkssegment eller fysisk placering af kontor. Dette er fælles for forskudt implementering af ExpressRoute til Office 365 og er konfigureret på dine BGP-enheder.

2. **PAC-filer/URL-adresser** – dirigere Office 365 bestemt netværkstrafik til bestemte FQDN'er på en bestemt sti. Dette ruter selektivt efter klientcomputeren som identificeret af [PAC-filinstallationen](./managing-office-365-endpoints.md).

3. **Rutefiltrering** -  [Rutefiltre](/azure/expressroute/how-to-routefilter-portal) er en metode til at bruge et undersæt af understøttede tjenester via Microsoft-peering.

4. **BGP-communities** – filtrering, der er baseret på [BGP-community-tags](./bgp-communities-in-expressroute.md), giver en kunde mulighed for at bestemme, hvilke Office 365-programmer vil krydse ExpressRoute, og hvilke der vil krydse internettet.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering Office 365 netværksforbindelsen](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administrere ExpressRoute til Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Implementering af ExpressRoute til Office 365](implementing-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimere dit netværk til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow med ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevnen](network-planning-and-performance.md)
