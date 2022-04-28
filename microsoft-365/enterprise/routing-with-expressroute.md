---
title: Routing med ExpressRoute til Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel kan du få mere at vide om krav til Azure ExpressRoute-routing, kredsløb og routingdomæner til brug sammen med Office 365.
ms.openlocfilehash: c63e3ae14c9b369265622f17c2e542818620aa3e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092905"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing med ExpressRoute til Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du vil have en korrekt forståelse af routingtrafikken til Office 365 ved hjælp af Azure ExpressRoute, skal du have godt styr på [kernekravene til ExpressRoute-routing](/azure/expressroute/expressroute-routing) og [ExpressRoute-kredsløb og -routingdomæner](/azure/expressroute/expressroute-circuit-peerings). Disse indeholder de grundlæggende funktioner til brug af ExpressRoute, som Office 365 kunder er afhængige af.
  
Nogle af de vigtigste elementer i ovenstående artikler, som du skal forstå, omfatter:
  
- ExpressRoute-kredsløb er ikke knyttet til en bestemt fysisk infrastruktur, men er en logisk forbindelse, der oprettes på en enkelt peeringplacering af Microsoft og en peeringudbyder på dine vegne.

- Der er en 1:1-tilknytning mellem et ExpressRoute-kredsløb og en kundes s-nøgle.

- Hvert kredsløb kan understøtte to uafhængige peeringrelationer (Azure Private Peering og Microsoft Peering); Office 365 kræver Microsoft-peering.

- Hvert kredsløb har en fast båndbredde, der deles på tværs af alle peering-relationer.

- Alle offentlige IPv4-adresser og offentlige AS-numre, der skal bruges til ExpressRoute-kredsløbet, skal valideres som værende ejet af dig eller tildeles udelukkende til dig af ejeren af adresseområdet.

- De virtuelle ExpressRoute-kredsløb er redundante globalt og følger standardpraksis for BGP-routing. Derfor anbefaler vi to fysiske kredsløb pr. udgående forbindelse til din udbyder i en aktiv/aktiv konfiguration.

Se [siden Ofte stillede spørgsmål](/azure/expressroute/expressroute-faqs) for at få flere oplysninger om understøttede tjenester, omkostninger og konfigurationsoplysninger. Se [artiklen Om ExpressRoute-placeringer](/azure/expressroute/expressroute-locations) for at få oplysninger om listen over forbindelsesudbydere, der tilbyder Microsoft-peeringsupport. Vi har også optaget en [Azure ExpressRoute i ti dele til Office 365 træningsserie](https://channel9.msdn.com/series/aer) på Channel 9 for at hjælpe med at forklare koncepterne mere grundigt.
  
## <a name="ensuring-route-symmetry"></a>Sikrer rutesymmetri

De Office 365 frontendservere er tilgængelige både på internettet og ExpressRoute. Disse servere foretrækker at dirigere tilbage til det lokale miljø via ExpressRoute-kredsløb, når begge er tilgængelige. På grund af dette er der en mulighed for rute asymmetri, hvis trafik fra dit netværk foretrækker at dirigere over dine internetkredsløb. Asymmetriske ruter er et problem, fordi enheder, der udfører tilstandsfuld pakkekontrol, kan blokere returtrafik, der følger en anden sti end de udgående pakker, der følges.
  
Uanset om du starter en forbindelse til Office 365 via internettet eller ExpressRoute, skal kilden være en adresse, der kan sendes offentligt. Med mange kunder, der peerer direkte med Microsoft, er det ikke muligt at have private adresser, hvor duplikering er mulig mellem kunder.
  
Følgende er scenarier, hvor kommunikation fra Office 365 til dit lokale netværk startes. Hvis du vil forenkle netværksdesignet, anbefaler vi, at du distribuerer følgende via internetstien.
  
- SMTP-tjenester, f.eks. mail fra en Exchange Online lejer til en lokal vært eller SharePoint Onlinemail, der sendes fra SharePoint Online til en lokal vært. SMTP-protokollen bruges mere bredt på Microsofts netværk, end de rutepræfikser, der deles via ExpressRoute-kredsløb, og annoncering af SMTP-servere i det lokale miljø via ExpressRoute, vil medføre fejl med disse andre tjenester.

- ADFS under validering af adgangskode til logon.

- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid).

- [SharePoint hybridsøgning i organisationsnetværket](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint hybrid BCS](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business hybrid-](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) og/eller [Skype for Business-sammenslutning](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

For at Microsoft kan dirigere tilbage til dit netværk for disse tovejstrafikflow, skal BGP-ruterne til dine enheder i det lokale miljø deles med Microsoft. Når du reklamerer for rutepræfikser til Microsoft via ExpressRoute, skal du følge disse bedste fremgangsmåder:

1) Undlad at annoncere for det samme præfiks for den offentlige IP-adresse til det offentlige internet og over ExpressRoute. Det anbefales, at reklamerne for IP BGP-rutepræfikset til Microsoft over ExpressRoute er fra et interval, der slet ikke annonceres på internettet. Hvis det ikke er muligt at opnå på grund af den tilgængelige IP-adresseplads, er det vigtigt at sikre, at du reklamerer for et mere specifikt interval over ExpressRoute end nogen internetkredsløb.

2) Brug separate NAT IP-puljer pr. ExpressRoute-kredsløb, og adskil dem med internetkredsløbene.

3) Enhver rute, der annonceres til Microsoft, vil tiltrække netværkstrafik fra en hvilken som helst server i Microsofts netværk, ikke kun dem, for hvilke ruter annonceres til dit netværk via ExpressRoute. Reklamer kun for ruter til servere, hvor routingscenarier er defineret og forstås godt af dit team. Gør opmærksom på separate præfikser for IP-adresser på hvert af flere ExpressRoute-kredsløb fra dit netværk.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Beslutning om, hvilke programmer og funktioner der føres over ExpressRoute

Når du konfigurerer en peeringrelation ved hjælp af Domænet for Microsoft-peeringrouting og godkendes til den relevante adgang, kan du se alle PaaS- og SaaS-tjenester, der er tilgængelige via ExpressRoute. De Office 365 tjenester, der er udviklet til ExpressRoute, kan administreres med [BGP-communities](./bgp-communities-in-expressroute.md) eller [rutefiltre](/azure/expressroute/how-to-routefilter-portal).
  
Hver af de Office 365 funktioner, der er tilgængelige ved hjælp af Microsoft Peering, er angivet i [artiklen Office 365 slutpunkter](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) efter programtype og FQDN. Årsagen til at bruge FQDN i tabellerne er at give kunderne mulighed for at administrere trafik ved hjælp af PAC-filer eller andre proxykonfigurationer. Se vores vejledning til [administration af Office 365 slutpunkter](./managing-office-365-endpoints.md), f.eks. PAC-filer.
  
I nogle situationer har vi brugt et jokertegndomæne, hvor et eller flere under-FQDN'er annonceres anderledes end jokertegndomænet på højere niveau. Det sker normalt, når jokertegnet repræsenterer en lang liste over servere, der alle annonceres til ExpressRoute og internettet, mens en lille delmængde af destinationer kun annonceres på internettet eller omvendt. Se tabellerne nedenfor for at forstå, hvor forskellene er.
  
I denne tabel vises jokertegnet FQDN'er, der annonceres til både internettet og Azure ExpressRoute sammen med de under-FQDN'er, der kun annonceres på internettet.

|**Jokertegndomæne annonceret til ExpressRoute og internetkredsløb**|**Under-FQDN annonceres kun til internetkredsløb**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

PAC-filer er normalt beregnet til at sende netværksanmodninger til ExpressRoute annoncerede slutpunkter direkte til kredsløbet og alle andre netværksanmodninger til din proxy. Hvis du konfigurerer en PAC-fil som denne, skal du oprette din PAC-fil i følgende rækkefølge:
  
1. Medtag under-FQDN'er fra kolonne 2 i ovenstående tabel øverst i PAC-filen, så trafikken mod din proxy sendes. Vi har bygget et eksempel på en PAC-fil, som du kan bruge i vores artikel om [administration af Office 365 slutpunkter](./managing-office-365-endpoints.md).

2. Medtag alle de FQDN'er, der er markeret som annonceret til ExpressRoute, i [denne artikel](./urls-and-ip-address-ranges.md) under det første afsnit, så trafikken sendes direkte til dit ExpressRoute-kredsløb.

3. Medtag alle andre netværksslutpunkter eller regler under disse to poster, så trafikken sendes til din proxy.

I denne tabel vises de jokertegndomæner, der kun annonceres til internetkredsløb sammen med de under-FQDN'er, der annonceres til Azure ExpressRoute og internetkredsløb. For din PAC-fil ovenfor er FQDN'erne i kolonne 2 i nedenstående tabel angivet som annonceret til ExpressRoute i det link, der refereres til, hvilket betyder, at de vil blive inkluderet i den anden gruppe poster i filen.

|**Jokertegndomæne annonceret kun til internetkredsløb**|**Under-FQDN annonceret til ExpressRoute og internetkredsløb**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing Office 365 trafik via internettet og ExpressRoute

Hvis du vil dirigere til det Office 365 program, du vælger, skal du bestemme en række nøglefaktorer.
  
1. Hvor meget båndbredde programmet kræver. Udsnit af eksisterende forbrug er den eneste pålidelige metode til at bestemme dette i din organisation.

2. Hvilke udgående placeringer netværkstrafikken skal forlade netværket fra. Du bør planlægge at minimere netværksventetiden for forbindelsen til Office 365 da dette vil påvirke ydeevnen. Da Skype for Business bruger stemme og video i realtid, er den udsat for dårlig netværksventetid.

3. Hvis du vil have, at alle eller et undersæt af dine netværksplaceringer skal bruge ExpressRoute.

4. Hvilke placeringer din valgte netværksudbyder tilbyder ExpressRoute fra.

Når du har fundet svar på disse spørgsmål, kan du klargøre et ExpressRoute-kredsløb, der opfylder båndbredden og placeringsbehovene. Hvis du vil have mere hjælp til netværksplanlægning, skal du se [Office 365 vejledning til netværksjustering](./network-planning-and-performance.md) og [i casestudiet om, hvordan Microsoft håndterer planlægning af netværksydeevne](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Eksempel 1: Enkelt geografisk placering
  
Dette eksempel er et scenarie for et fiktivt firma kaldet Trey Research, der har en enkelt geografisk placering.
  
Medarbejdere hos Trey Research har kun tilladelse til at oprette forbindelse til de tjenester og websteder på internettet, som sikkerhedsafdelingen eksplicit tillader på det par af udgående proxyer, der er placeret mellem virksomhedens netværk og deres internetudbyder.
  
Trey Research planlægger at bruge Azure ExpressRoute til Office 365 og anerkender, at noget trafik, f.eks. trafik, der er beregnet til netværk til levering af indhold, ikke kan dirigeres over ExpressRoute for Office 365 forbindelse. Da al trafik allerede dirigeres til proxyenhederne som standard, vil disse anmodninger fortsat fungere som før. Når Trey Research har fundet ud af, at de kan opfylde kravene til Azure ExpressRoute-routing, fortsætter de med at oprette et kredsløb, konfigurere routing og knytte det nye ExpressRoute-kredsløb til et virtuelt netværk. Når den grundlæggende Konfiguration af Azure ExpressRoute er på plads, bruger Trey Research den [#2 PAC-fil, vi publicerer](./managing-office-365-endpoints.md), til at dirigere trafik med kundespecifikke data via den direkte ExpressRoute til Office 365 forbindelser.
  
Som vist i følgende diagram kan Trey Research opfylde kravet om at dirigere Office 365 trafik over internettet og et undersæt af trafik via ExpressRoute ved hjælp af en kombination af ændringer af routing og udgående proxykonfiguration.
  
1. Ved hjælp af [PAC-filen #2 publicerer vi](./managing-office-365-endpoints.md) for at dirigere trafik gennem et separat internet udgangspunkt for Azure ExpressRoute til Office 365.

2. Klienter er konfigureret med en standardrute mod Trey Researchs proxyer.

I dette eksempelscenarie bruger Trey Research en udgående proxyenhed. På samme måde kan kunder, der ikke bruger Azure ExpressRoute til Office 365 bruge denne teknik til at dirigere trafik baseret på omkostningerne ved at inspicere trafik, der er beregnet til velkendte slutpunkter med høj volumen.
  
Den højeste mængde FQDN'er for Exchange Online, SharePoint Online og Skype for Business Online er følgende:
  
![ExpressRoute- kunde edge-netværk.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com sammen med IP-intervaller for ikke-TCP-trafik

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

Få mere at vide om [udrulning og administration af proxyindstillinger i Windows 8](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) og [sikre, at Office 365 ikke begrænses af din proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Med et enkelt ExpressRoute-kredsløb er der ingen høj tilgængelighed for Trey Research. I tilfælde af at Treys redundante edge-enheder, der servicerer ExpressRoute-forbindelsen, mislykkes, er der ikke et ekstra ExpressRoute-kredsløb at failovere til. Dette efterlader Trey Research i en knibe som ikke over til internettet vil kræve manuel omkonfiguration og i nogle tilfælde nye IP-adresser. Hvis Trey vil tilføje høj tilgængelighed, er den nemmeste løsning at tilføje ekstra ExpressRoute-kredsløb for hver placering og konfigurere kredsløbene på en aktiv/aktiv måde.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing ExpressRoute for Office 365 med flere placeringer

Det sidste scenarie, routing Office 365 trafik via ExpressRoute, er grundlaget for endnu mere kompleks routingarkitektur. Uanset antallet af placeringer, antallet af kontinenter, hvor disse placeringer findes, antallet af ExpressRoute-kredsløb osv., der kan dirigere noget trafik til internettet, og noget trafik via ExpressRoute vil være påkrævet.
  
De ekstra spørgsmål, der skal besvares for kunder med flere placeringer i flere geografiske områder, omfatter:
  
1. Kræver du et ExpressRoute-kredsløb på alle placeringer? Hvis du bruger Skype for Business Online eller er optaget af ventetidsfølsomhed for SharePoint Online eller Exchange Online, anbefales et redundant par aktive/aktive ExpressRoute-kredsløb på hver placering. Se vejledningen til Skype for Business mediekvalitet og netværksforbindelser for at få flere oplysninger.

2. Hvis et ExpressRoute-kredsløb ikke er tilgængeligt i et bestemt område, hvordan skal Office 365 bestemt trafik så dirigeres?

3. Hvad er den foretrukne metode til konsolidering af trafik i tilfælde af netværk med mange små placeringer?

Hver af disse præsenterer en unik udfordring, der kræver, at du evaluerer dit eget netværk og de muligheder, der er tilgængelige fra Microsoft.

|**Overvejelse**|**Netværkskomponenter, der skal evalueres**|
|:-----|:-----|
|Kredsløb på mere end én placering  <br/> |Vi anbefaler mindst to kredsløb, der er konfigureret på en aktiv/aktiv måde.  <br/> Omkostninger, ventetid og båndbreddebehov skal sammenlignes.  <br/> Brug BGP-ruteomkostninger, PAC-filer og NAT til at administrere routing med flere kredsløb.  <br/> |
|Routing fra placeringer uden et ExpressRoute-kredsløb  <br/> |Vi anbefaler, at udgående data og DNS-opløsning er så tæt på den person, der starter anmodningen om Office 365.  <br/> DNS-videresendelse kan bruges til at gøre det muligt for fjernkontorer at finde det relevante slutpunkt.  <br/> Klienter på fjernkontoret skal have en tilgængelig rute, der giver adgang til ExpressRoute-kredsløbet.  <br/> |
|Mindre kontorkonsolidering  <br/> |Tilgængelig båndbredde og dataforbrug skal sammenlignes omhyggeligt.  <br/> |

> [!NOTE]
> Microsoft foretrækker ExpressRoute via internettet, hvis ruten er tilgængelig uanset den fysiske placering.
  
Hver af disse overvejelser skal tages i betragtning for hvert enkelt unikke netværk. Nedenfor er et eksempel.
  
### <a name="example-2-multi-geographic-locations"></a>Eksempel 2: Flere geografiske placeringer
  
Dette eksempel er et scenarie for et fiktivt firma kaldet "Humongous Insurance", som har flere geografiske placeringer.
  
Humongous Insurance er geografisk spredt med kontorer over hele verden. De vil gerne implementere Azure ExpressRoute til Office 365 for at bevare det meste af deres Office 365 trafik på direkte netværksforbindelser. Humongous Insurance har også kontorer på to yderligere kontinenter. Medarbejderne på fjernkontoret, hvor ExpressRoute ikke er praktisk, skal dirigere tilbage til en eller begge af de primære faciliteter for at bruge en ExpressRoute-forbindelse.
  
Det ledende princip er at få Office 365 bestemt trafik til et Microsoft-datacenter så hurtigt som muligt. I dette eksempel skal Humongous Insurance beslutte, om deres fjernkontorer skal dirigere over internettet for at få adgang til et Microsoft-datacenter over en hvilken som helst forbindelse så hurtigt som muligt, eller om deres fjernkontorer skal dirigere over et internt netværk for at komme til et Microsoft-datacenter via en ExpressRoute-forbindelse så hurtigt som muligt.
  
Microsofts datacentre, netværk og programarkitektur er designet til at tage globalt forskellige kommunikationsmuligheder og servicere dem på den mest effektive måde. Dette er et af de største netværk i verden. Anmodninger, der er beregnet til Office 365, som forbliver på kundenetværk længere end nødvendigt, kan ikke drage fordel af denne arkitektur.
  
I Humongous Insurance situation, bør de fortsætte afhængigt af de programmer, de agter at bruge over ExpressRoute. Hvis de f.eks. er Skype for Business Online-kunde eller planlægger at bruge ExpressRoute-forbindelse, når de opretter forbindelse til eksterne Skype for Business Online-møder, anbefales det design, der anbefales i Skype for Business  Onlinevejledning til mediekvalitet og netværksforbindelse er at klargøre et ekstra ExpressRoute-kredsløb til den tredje placering. Det kan være dyrere ud fra et netværksperspektiv. Routinganmodninger fra ét kontinent til et andet, før der leveres til et Microsoft-datacenter, kan dog medføre en dårlig eller ubrugelig oplevelse under Skype for Business onlinemøder og -kommunikation.
  
Hvis Humongous Insurance ikke bruger eller ikke planlægger at bruge Skype for Business Online på nogen måde, kan routing Office 365 bestemt netværkstrafik tilbage til et kontinent med en ExpressRoute-forbindelse være praktisk, men det kan dog medføre unødvendig ventetid eller TCP-overbelastning. I begge tilfælde anbefales det at distribuere internettrafik til internettet på det lokale websted for at drage fordel af de netværk til levering af indhold, som Office 365 er afhængig af.
  
![ExpressRoute med flere geografiske områder.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Når Humongous Insurance planlægger deres multi-geografi strategi, der er mange ting at overveje omkring størrelsen af kredsløb, antallet af kredsløb, failover, og så videre.
  
Med ExpressRoute på en enkelt placering, hvor flere områder forsøger at bruge kredsløbet, ønsker Humongous Insurance at sikre, at forbindelser til Office 365 fra det eksterne kontor sendes til det Office 365 datacenter, der er det nærmeste hovedkvarter, og modtages af hovedkvarterets placering. For at gøre dette implementerer Humongous Insurance DNS-videresendelse for at reducere antallet af rundture og DNS-opslag, der kræves for at etablere den relevante forbindelse til det Office 365 miljø tættest på hovedkvarterets internet udgangspunkt. Dette forhindrer klienten i at løse en lokal frontendserver og sikrer, at den Front-End server, som personen opretter forbindelse til, befinder sig i nærheden af hovedkvarteret, hvor Humongous Insurance peering med Microsoft. Du kan også få mere at vide om [, hvordan du tildeler en betinget videresender til et domænenavn](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
I dette scenarie vil trafik fra fjernkontor løse Office 365 frontendinfrastruktur i Nordamerika og bruge Office 365 til at oprette forbindelse til backendservere i henhold til arkitekturen i Office 365 program. Exchange Online vil f.eks. afslutte forbindelsen i Nordamerika, og disse frontendservere opretter forbindelse til backendpostkasseserveren, uanset hvor lejeren er placeret. Alle tjenester har en bredt distribueret front door service bestående af unicast og anycast destinationer.
  
Hvis Humongous har store kontorer på flere kontinenter, anbefales mindst to aktive/aktive kredsløb pr. region for at reducere ventetiden for følsomme applikationer, f.eks. Skype for Business Online. Hvis alle kontorer befinder sig på et enkelt kontinent eller ikke bruger samarbejde i realtid, er det en kundespecifik beslutning at have et konsolideret eller distribueret udgående punkt. Når flere kredsløb er tilgængelige, sikrer BGP-routing, at failover, hvis et enkelt kredsløb bliver utilgængeligt.
  
Få mere at vide om [konfigurationer af eksempeldistribution](/azure/expressroute/expressroute-config-samples-routing) og [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>Selektiv routing med ExpressRoute

Selektiv routing med ExpressRoute kan være nødvendig af forskellige årsager, f.eks. test, udrulning af ExpressRoute til et undersæt af brugere. Der er forskellige værktøjer, som kunderne kan bruge til selektivt at distribuere Office 365 netværkstrafik via ExpressRoute:
  
1. **Rutefiltrering/-adskillelse** – gør det muligt for BGP-ruterne at Office 365 via ExpressRoute til et undersæt af dine undernet eller routere. Dette distribueres selektivt efter kundenetværkssegment eller fysisk kontorplacering. Dette er almindeligt for overvældende udrulning af ExpressRoute til Office 365 og er konfigureret på dine BGP-enheder.

2. **PAC-filer/URL-adresser** – dirigerer Office 365 bestemt netværkstrafik til bestemte FQDN'er, der skal dirigeres på en bestemt sti. Dette distribueres selektivt efter klientcomputer som identificeret af [PAC-filinstallationen](./managing-office-365-endpoints.md).

3. **Rutefiltrering** -  [Rutefiltre](/azure/expressroute/how-to-routefilter-portal) er en måde at bruge en delmængde af understøttede tjenester på via Microsoft Peering.

4. **BGP-communities** – filtrering baseret på [BGP-communitytags](./bgp-communities-in-expressroute.md) giver en kunde mulighed for at afgøre, hvilke Office 365 programmer der gennemgår ExpressRoute, og hvilke der krydser internettet.

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Relaterede emner

[Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md)
  
[Azure ExpressRoute til Office 365](azure-expressroute.md)
  
[Administration af ExpressRoute for Office 365 forbindelse](managing-expressroute-for-connectivity.md)
  
[Netværksplanlægning med ExpressRoute til Office 365](network-planning-with-expressroute.md)
  
[Implementering af ExpressRoute for Office 365](implementing-expressroute.md)
  
[Mediekvalitet og ydeevne for netværksforbindelsen i Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimering af netværket til Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute og QoS i Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Opkaldsflow ved hjælp af ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Brug af BGP-communities i ExpressRoute til Office 365 scenarier](bgp-communities-in-expressroute.md)
  
[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)
  
[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)
  
[Office 365-URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 netværk og justering af ydeevne](network-planning-and-performance.md)
