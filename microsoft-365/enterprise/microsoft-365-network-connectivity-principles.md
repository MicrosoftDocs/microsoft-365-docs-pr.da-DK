---
title: Microsoft 365 principper for netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Denne artikel giver den seneste vejledning til sikker optimering af Microsoft 365 netværksforbindelsen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1cea07745295f945f472dfeaa7042d3b027eea85
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63589722"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Microsoft 365 principper for netværksforbindelse

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Før du begynder at planlægge dit netværk til Microsoft 365-netværksforbindelse, er det vigtigt at forstå principperne for netværksforbindelse, der ligger bag sikker styring af Microsoft 365-trafik og for at få den bedst mulige ydeevne. Denne artikel hjælper dig med at forstå den seneste vejledning i sikker optimering af Microsoft 365 netværksforbindelsen.
  
Traditionelle virksomhedsnetværk er primært designet til at give brugere adgang til programmer og data, der er hostet i virksomhedens datacentre, med stærk perimetersikkerhed. Den traditionelle model forudsætter, at brugere vil få adgang til programmer og data inde fra virksomhedens netværksperimeter, via WAN-links fra afdelingskontorer eller eksternt via VPN-forbindelser.
  
Indføring af SaaS-programmer som f.Microsoft 365 flytter en kombination af tjenester og data uden for netværkets perimeter. Uden optimering er trafik mellem brugere og SaaS-programmer underlagt ventetid, der introduceres ved pakkeinspektion, netværks hairpins, utilsigtede forbindelser til geografisk fjern slutpunkter og andre faktorer. Du kan sikre den bedste Microsoft 365 og pålidelighed ved at forstå og implementere retningslinjer for nøgleoptimering.
  
I denne artikel kan du få mere at vide om:
  
- [Microsoft 365 arkitektur,](microsoft-365-network-connectivity-principles.md#BKMK_Architecture) som den gælder for kundeforbindelser til skyen
- Opdaterede [Microsoft 365 forbindelse principper](microsoft-365-network-connectivity-principles.md#BKMK_Principles) og strategier for optimering af netværkstrafik og slutbrugeroplevelsen
- [Webtjenesten Office 365 slutpunkter](microsoft-365-network-connectivity-principles.md#BKMK_WebSvc), som giver netværksadministratorer mulighed for at bruge en struktureret liste over slutpunkter til brug i netværksoptimering
- [Nye Office 365 slutpunktskategorier og](microsoft-365-network-connectivity-principles.md#BKMK_Categories) optimeringsvejledning
- [Sammenligning af perimetersikkerhed på netværket med slutpunktssikkerhed](microsoft-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Trinvis optimering af](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) indstillinger for Microsoft 365 trafik
- Testen [Microsoft 365 forbindelse, et](https://aka.ms/netonboard) nyt værktøj til test af grundlæggende forbindelse til Microsoft 365

## <a name="microsoft-365-architecture"></a>Microsoft 365 arkitektur
<a name="BKMK_Architecture"> </a>

Microsoft 365 er en distribueret Software-as-a-Service (SaaS)-sky, der leverer produktivitets- og samarbejdsscenarier gennem et varieret sæt mikrotjenester og programmer, f.eks. Exchange Online, SharePoint Online, Skype for Business Online, Microsoft Teams, Exchange Online Protection, Office i en browser og mange andre. Selvom bestemte Microsoft 365-programmer kan have deres unikke funktioner, som de gælder for kundenetværk og forbindelse til skyen, deler de alle nogle vigtige principper, mål og arkitekturmønstre. Disse principper og arkitekturmønstre for forbindelse er typiske for mange andre SaaS-skyer og på samme tid forskellige fra de typiske implementeringsmodeller af Platform-as-a-Service- og Infrastructure-as-a-Service-skyer, f.eks. Microsoft Azure.
  
En af de mest betydningsfulde arkitektoniske træk ved Microsoft 365 (som ofte mistes eller fejlfortolkes af netværksarkitekter) er, at det er en virkelig global distribueret tjeneste, i forhold til hvordan brugerne opretter forbindelse til den. Placeringen af mållejeren Microsoft 365 er vigtig for at forstå lokaliteten for, hvor kundedata gemmes i skyen, men brugeroplevelsen med Microsoft 365 omfatter ikke direkte forbindelse til diske, der indeholder dataene. Brugeroplevelsen med Microsoft 365 (herunder ydeevne, pålidelighed og andre vigtige kvalitetsegenskaber) omfatter forbindelse gennem stærkt distribuerede forside døre, der skaleres ud over hundredvis af Microsoft-placeringer verden over. I de fleste tilfælde opnås den bedste brugeroplevelse ved at give kundenetværket mulighed for at distribuere brugeranmodninger til det nærmeste Microsoft 365-tjenesteindgangspunkt i stedet for at oprette forbindelse til Microsoft 365 via et udgangspunkt på et centralt sted eller i et område.
  
For de fleste kunder Microsoft 365 brugere fordelt på tværs af mange placeringer. For at opnå de bedste resultater bør principperne i dette dokument ses fra udskaleringspunktet (ikke opskalering), hvor der fokuseres på optimering af forbindelsen til det nærmeste tilstedeværelsespunkt i Microsoft Global Network og ikke fra den geografiske placering af Microsoft 365-lejeren. Faktisk betyder det, at selvom Microsoft 365-lejerdata kan gemmes på en bestemt geografisk placering, forbliver Microsoft 365-oplevelsen for den pågældende lejer distribueret og kan være placeret meget tæt (netværks) tæt på hver slutbrugerplacering, som lejeren har.
  
## <a name="microsoft-365-connectivity-principles"></a>Microsoft 365 forbindelses principper
<a name="BKMK_Principles"> </a>

Microsoft anbefaler følgende principper for at opnå optimal Microsoft 365 forbindelse og ydeevne. Brug disse Microsoft 365 forbindelse principper for administration af din trafik og få den bedste ydeevne, når du opretter forbindelse til Microsoft 365.
  
Det primære mål i netværksdesignet bør være at minimere ventetiden ved at reducere tiden på returkørslen (RTT) fra dit netværk til Microsoft Global Network, Microsofts offentlige netværkssten, der indbyrdes forbinder alle Microsofts datacentre med lav latenstid og indgangspunkter i skyen over hele verden. Du kan få mere at vide om Microsoft Global Network [på Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificer og Microsoft 365 trafik

![Identificer Microsoft 365 trafik.](../media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
At Microsoft 365 netværkstrafik er det første trin i at kunne skelne denne trafik fra generisk internetbundet netværkstrafik. Microsoft 365 forbindelse kan optimeres ved at implementere en kombination af metoder som optimering af netværksrute, firewallregler, indstillinger for browserproxyer og bypass af enheder til netværksinspektion for visse slutpunkter.
  
Forrige Microsoft 365 til optimering opdelt Microsoft 365 slutpunkter i to kategorier, **Obligatorisk** og **Valgfri**. Efterhånden som slutpunkter er blevet tilføjet for at understøtte nye Microsoft 365-tjenester og -funktioner, har vi omorganiseret Microsoft 365 slutpunkter i tre **kategorier:** Optimer **, Tillad** og **Standard**. Retningslinjer for hver kategori gælder for alle slutpunkter i kategorien, hvilket gør optimeringer nemmere at forstå og implementere.
  
Du kan finde flere Microsoft 365 om slutpunktskategorier og optimeringsmetoder i [afsnittet Office 365 kategorier for slutpunkter](microsoft-365-network-connectivity-principles.md#BKMK_Categories).
  
Microsoft udgiver nu alle Microsoft 365 som en webtjeneste og giver vejledning i, hvordan du bedst bruger disse data. Du kan finde flere oplysninger om, hvordan du henter og arbejder med Microsoft 365-slutpunkter, i artiklen [Office 365 URL-adresser og IP-adresseintervaller](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Egress netværksforbindelser lokalt

![Egress netværksforbindelser lokalt.](../media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokal DNS og internet udgangspunkt er af afgørende betydning for at reducere forbindelsens ventetid og sikre, at brugerforbindelserne foretages til det nærmeste indgangspunkt til Microsoft 365 tjenester. I en kompleks netværktopologi er det vigtigt at implementere både lokal DNS og lokalt internet udgangspunkt sammen. Du kan finde flere oplysninger Microsoft 365, hvordan du sender klientforbindelser til det nærmeste indgangspunkt, i artiklen [Klientforbindelser](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Før indførelsen af skytjenester som f.eks. Microsoft 365, var slutbrugerens internetforbindelse som en designfaktor i netværksarkitektur relativt simpelt. Når internettjenester og websteder er fordelt over hele verden, er ventetiden mellem virksomhedens udgangspunkt og et givent destinationsslutpunkt i høj grad en funktion af geografisk afstand.
  
I en traditionel netværksarkitektur kan alle udgående internetforbindelser krydse virksomhedens netværk og udgangspunkt fra en central placering. Efterhånden som Microsofts skybaserede tilbud er modnet, er en distribueret internetbaseret netværksarkitektur blevet afgørende for understøttelse af latenstidsfølsomme skytjenester. Microsoft Global Network er udviklet til at imødekomme krav til ventetid med distributed service front door-infrastruktur, et dynamisk materiale af globale indgangspunkter, der distribuerer indgående skytjenesteforbindelser til det nærmeste indgangspunkt. Dette er beregnet til at reducere længden af de "sidste kilometer" for Microsofts skykunder ved effektivt at afkorte rute mellem kunden og skyen.
  
Enterprise WAN'er er ofte designet til at backhaul-netværkstrafik til et centralt firmas hovedkontor for inspektion før udgang til internettet, normalt via en eller flere proxyservere. Nedenstående diagram illustrerer en sådan netværktopologi.
  
![Traditionel virksomhedsnetværksmodel.](../media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Da Microsoft 365 kører på Microsoft Global Network, som omfatter front end-servere over hele verden, vil der ofte være en front end-server tæt på brugerens placering. Ved at levere lokale internetafslutninger og ved at konfigurere interne DNS-servere til at levere lokal navneopløsning til Microsoft 365-slutpunkter kan netværkstrafik, der er beregnet til Microsoft 365, oprette forbindelse til Microsoft 365-front end-servere så tæt på som muligt for brugeren. Nedenstående diagram viser et eksempel på en netværktopologi, der gør det muligt for brugere, der opretter forbindelse fra hovedkontorer, afdelingskontorer og eksterne placeringer, at følge den korteste vej til det nærmeste Microsoft 365 indgangspunkt.
  
![WAN-netværksmodel med regionale udgangspunkter.](../media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Afkortning af netværksstien til Microsoft 365-indgangspunkter på denne måde kan forbedre forbindelsesydeevnen og slutbrugeroplevelsen i Microsoft 365 og kan også hjælpe med at reducere effekten af fremtidige ændringer af netværksarkitekturen på Microsoft 365 ydeevne og pålidelighed.
  
DNS-anmodninger kan også introducere ventetid, hvis den reagerende DNS-server er fjern eller optaget. Du kan minimere ventetiden for navneopløsning ved at klargøre lokale DNS-servere på afdelingsplaceringer og sørge for, at de er konfigureret til at cachelagre DNS-poster korrekt.
  
Det regionale udgangspunkt kan fungere godt i Microsoft 365, men den optimale forbindelsesmodel vil altid være at levere et netværksud udgangspunkt for brugeren, uanset om det ligger på virksomhedens netværk eller eksterne placeringer, f.eks. huse, cafeer, kaffecentre og lufthavne. Denne lokale direkte udgangspunktsmodel er repræsenteret i nedenstående diagram.
  
![Lokal udgangsnetværksarkitektur.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Virksomheder, der har indført Microsoft 365, kan drage fordel af Microsoft Global Network's Distributed Service Front Door-arkitektur ved at sikre, at brugerforbindelser til Microsoft 365 tager den korteste mulige rute til det nærmeste Microsoft Global Network-indgangspunkt. Den lokale udgangsnetværksarkitektur gør dette ved at tillade Microsoft 365 trafik dirigeres over det nærmeste udgangspunkt, uanset brugerplacering.
  
Den lokale udgangsarkitektur har følgende fordele i forhold til den traditionelle model:
  
- Giver optimal Microsoft 365 ved at optimere rutelængden. Slutbrugerforbindelser dirigeres dynamisk til det nærmeste Microsoft 365 indgangspunkt af distributionstjenestens indgangspunkt.
- Reducerer belastningen på virksomhedens netværksinfrastruktur ved at tillade lokalt udgangspunkt.
- Sikrer forbindelser i begge ender ved at udnytte klientslutpunktsikkerhed og skysikkerhedsfunktioner.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Undgå netværks hairpins

![Undgå hairpins.](../media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Som en tommelfingerregel vil den korteste og mest direkte rute mellem bruger og nærmeste Microsoft 365 give den bedste ydeevne. En hairpin på netværket sker, når WAN- eller VPN-trafik bundet til en bestemt destination først dirigeres til en anden mellemliggende placering (f.eks. sikkerhedsstabling, skyadgangsmægler eller skybaseret webgateway), introducerer ventetid og potentiel omdirigering til et geografisk fjernslutpunkt. Network hairpins can also be caused by routing/peering inefficiencies or suboptimal (remote) DNS lookups.
  
For at sikre, at Microsoft 365-forbindelsen ikke er underlagt netværks hairpins, selv i det lokale udgangspunkt, skal du kontrollere, om den internetudbyder, der bruges til at levere internetud udgangspunktet for brugerplaceringen, har en direkte peeringrelation med Microsofts globale netværk i nærheden af den pågældende placering. Du kan også konfigurere udgangsrouting til at sende pålidelige Microsoft 365-trafik direkte, i modsætning til proxy eller indføring via en tredjepartssky eller skybaseret netværkssikkerhedsleverandør, der behandler din internetbundne trafik. Lokal DNS-navneopløsning for Microsoft 365 slutpunkter hjælper med at sikre, at ud over direkte routing bruges de nærmeste Microsoft 365 postpunkter til brugerforbindelser.
  
Hvis du bruger skybaserede netværk eller sikkerhedstjenester til din Microsoft 365-trafik, skal du sikre dig, at resultatet af hairpinen evalueres, og at dets Microsoft 365 påvirke ydeevnen forstås. Dette kan gøres ved at undersøge antallet og placeringerne af serviceudbyder-placeringer, som trafikken videresendes gennem i forhold til antallet af dine afdelingskontorer og Microsoft Global Network-peeringpunkter, kvaliteten af serviceudbyder-netværks peeringrelationen til din internetudbyder og Microsoft og ydeevnens betydning for backhauling i serviceudbyder-infrastrukturen.
  
På grund af det store antal distribuerede placeringer med Microsoft 365-indgangspunkter og deres afstand til slutbrugere kan routing af Microsoft 365-trafik til et tredjepartsnetværk eller sikkerhedsudbyder have en negativ indvirkning på Microsoft 365-forbindelser, hvis udbydernetværket ikke er konfigureret til optimal Microsoft 365 peering.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Vurder bypass af proxyer, trafikinspektionsenheder og duplikerede sikkerhedsteknologier

![Tilgår proxyer, trafikinspektionsenheder og duplikerede sikkerhedsteknologier.](../media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Virksomhedskunder bør gennemgå deres metoder til netværkssikkerhed og risikobegrænsning specifikt for Microsoft 365 bundet trafik og bruge Microsoft 365-sikkerhedsfunktioner til at reducere deres afhængighed af forstyrrende, ydeevnepåvirkning og dyre netværkssikkerhedsteknologier til Microsoft 365-netværkstrafik.
  
De fleste virksomhedsnetværk gennemtvinger netværkssikkerhed for internettrafik ved hjælp af teknologier som proxyer, SSL-inspektion, pakkeinspektion og systemer til forebyggelse af datatab. Disse teknologier giver vigtig risiko mod afhjælpning i forbindelse med generiske internetanmodninger, men kan markant reducere ydeevnen, skalerbarheden og kvaliteten af slutbrugeroplevelsen, når de anvendes på Microsoft 365 slutpunkter.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 Slutpunkter-webtjeneste

Microsoft 365-administratorer kan bruge et script eller REST-opkald til at bruge en struktureret liste over slutpunkter fra Office 365-slutpunkter-webtjenesten og opdatere konfigurationerne af perimeterfirewalls og andre netværksenheder. Dette sikrer, at trafik bundet til Microsoft 365 identificeres, behandles korrekt og administreres anderledes end netværkstrafik bundet til generiske og ofte ukendte websteder. Du kan finde flere oplysninger om, hvordan du bruger Office 365 Endpoints-webtjenesten, i artiklen [Office 365 URL-adresser og IP-adresseintervaller](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC-scripts (proxy automatisk konfiguration)
<a name="BKMK_WebSvc"> </a>

Microsoft 365 administratorer kan oprette PAC-scripts (Proxy Automatic Configuration), der kan leveres til brugercomputere via WPAD eller gruppepolitikobjekt. PAC-scripts kan bruges til at tilsidesætte proxyer for Microsoft 365-anmodninger fra WAN- eller VPN-brugere, hvilket tillader Microsoft 365-trafik at bruge direkte internetforbindelser i stedet for at analysere virksomhedens netværk.
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365 sikkerhedsfunktioner
<a name="BKMK_WebSvc"> </a>

Microsoft er gennemsigtig omkring datacentersikkerhed, driftssikkerhed og risikoreduktion omkring Microsoft 365 og de netværksslutpunkter, de repræsenterer. Microsoft 365 indbyggede sikkerhedsfunktioner er tilgængelige til at reducere netværkssikkerhedsrisikoen, f.eks forebyggelse af datatab, antivirus, multifaktorgodkendelse, kundelåsefelt, Defender til Office 365, Microsoft 365 Threat Intelligence, Microsoft 365 Secure Score, Exchange Online Protection og Network DDOS Security.
  
Du kan finde flere oplysninger om Microsofts datacenter og global netværkssikkerhed i [Microsoft Center for sikkerhed og sikkerhed](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nye Office 365 slutpunktskategorier
<a name="BKMK_Categories"> </a>

Office 365 slutpunkter repræsenterer et varieret sæt netværksadresser og undernet. Slutpunkter kan være URL-adresser, IP-adresser eller IP-områder, og nogle slutpunkter er angivet med bestemte TCP/UDP-porte. URL-adresser kan enten være et FQDN som *et account.office.net* eller en URL-adresse med jokertegn som *\*f.eks. .office365.com*.
  
> [!NOTE]
> Placeringerne af Office 365 i netværket er ikke direkte relateret til placeringen af Microsoft 365 lejerdata. Derfor bør kunder se på Microsoft 365 som en distribueret og global tjeneste og bør ikke forsøge at blokere netværksforbindelser til Office 365 slutpunkter, der er baseret på geografiske kriterier.
  
I vores tidligere vejledning til administration Microsoft 365, blev slutpunkter organiseret i to **kategorier, Obligatorisk** og **Valgfri**. Slutpunkter inden for hver kategori krævede forskellige optimeringer afhængigt af tjenestens betydning, og mange kunder havde problemer med at berettige anvendelse af de samme netværksoptimeringer til den komplette liste over Office 365 URL-adresser og IP-adresser.
  
I den nye model er slutpunkter opdelt i tre **kategorier,** Optimer **, Tillad** og **Standard, hvilket** giver en prioritetsbaseret pivot, der fokuserer på netværksoptimeringsindsats for at opnå de bedste forbedringer af ydeevnen og investeringsafkast. Slutpunkterne konsolideres i de ovenstående kategorier baseret på følsomheden af den effektive brugeroplevelse for netværkskvalitet, mængde og ydeevnekonvolut for scenarier og nem implementering. Anbefalede optimeringer kan anvendes på samme måde på alle slutpunkter i en given kategori.
  
- **Optimer** slutpunkter er nødvendige for at oprette forbindelse til hver Office 365-tjeneste og repræsenterer over 75 % af Office 365 båndbredde, forbindelser og mængden af data. Disse slutpunkter repræsenterer Office 365 scenarier, der er mest følsomme over for netværkets ydeevne, ventetid og tilgængelighed. Alle slutpunkter er hostet i Microsoft-datacentre. Hastigheden på ændring af slutpunkterne i denne kategori forventes at være meget lavere end for slutpunkterne i de andre to kategorier. Denne kategori indeholder et lille (på rækkefølgen ~ 10) sæt af nøgle-URL-adresser og et defineret sæt IP-undernet, der er dedikeret til centrale Office 365-arbejdsbelastninger som f.eks Exchange Online, SharePoint Online, Skype for Business Online og Microsoft Teams.

    En sammen komprimeret liste over klart definerede kritiske slutpunkter bør hjælpe dig med at planlægge og implementere netværksoptimeringer af høj værdi for disse destinationer hurtigere og nemmere.

    Eksempler på  *optimer*  slutpunkter omfatter *https://outlook.office365.com*, *https://\<tenant\>.sharepoint.com* og *https://\<tenant\>-my.sharepoint.com*.

    Optimeringsmetoder omfatter:

  - Tilsidesætte  *Optimer*  slutpunkter på netværksenheder og -tjenester, der udfører trafikskæring, SSL-dekryptering, omfattende pakkeinspektion og indholdsfiltrering.
  - Tilgår lokale proxyenheder og skybaserede proxytjenester, der ofte bruges til generisk internetbrowsing.
  - Prioriter evalueringen af disse slutpunkter som fuldt ud pålidelig af din netværksinfrastruktur og perimetersystemer.
  - Prioriter reduktion eller udelukkelse af WAN-backhauling, og facilitere direkte distribuerede internetbaserede udgangspunkter for disse slutpunkter så tæt på brugere/afdelingsplaceringer som muligt.
  - Faciliter direkte forbindelse til disse skybaserede slutpunkter for VPN-brugere ved at implementere opdelt netværksforbindelse.
  - Kontrollér, at IP-adresser, der returneres af DNS-navneopløsningen, svarer til routingstien for disse slutpunkter.
  - Prioriter disse slutpunkter for SD-WAN-integration til direkte, minimal latenstidsrouting til det nærmeste internet-peeringpunkt på Microsofts globale netværk.

- **Tillad** slutpunkter er nødvendige for at oprette forbindelse til bestemte Office 365-tjenester og -funktioner, men de er ikke så følsomme over for netværkets ydeevne og ventetid som dem i *kategorien Optimer*. Det overordnede netværkstryk for disse slutpunkter fra båndbreddepunktet og antal forbindelser er også mindre. Disse slutpunkter er dedikeret til Office 365 og er hostet i Microsoft-datacentre. De repræsenterer et bredt sæt Office 365-mikrotjenester og deres afhængigheder (på rækkefølgen af ~ 100 URL-adresser), og de forventes at blive ændret med højere hastighed end dem i kategorien Optimer. Ikke alle slutpunkter i denne kategori er knyttet til definerede dedikerede IP-undernet.

    Netværksoptimeringer *for Tillad* slutpunkter kan forbedre Office 365-brugeroplevelsen, men nogle kunder kan vælge at begrænse disse optimeringer for at minimere ændringer i deres netværk.

    Eksempler på *tillad slutpunkter* omfatter *https://\*.protection.outlook.com* og *https://accounts.accesscontrol.windows.net*.

    Optimeringsmetoder omfatter:

  - Tilsidesætte *Tillad*  slutpunkter på netværksenheder og -tjenester, der udfører trafikskæring, SSL-dekryptering, omfattende pakkeinspektion og indholdsfiltrering.
  - Prioriter evalueringen af disse slutpunkter som fuldt ud pålidelig af din netværksinfrastruktur og perimetersystemer.
  - Prioriter reduktion eller udelukkelse af WAN-backhauling, og facilitere direkte distribuerede internetbaserede udgangspunkter for disse slutpunkter så tæt på brugere/afdelingsplaceringer som muligt.
  - Kontrollér, at IP-adresser, der returneres af DNS-navneopløsningen, svarer til routingstien for disse slutpunkter.
  - Prioriter disse slutpunkter for SD-WAN-integration til direkte, minimal latenstidsrouting til det nærmeste internet-peeringpunkt på Microsofts globale netværk.

- **Standardslutpunkter** repræsenterer Office 365 og afhængigheder, der ikke kræver nogen optimering, og de kan behandles af kundenetværk som almindelig trafik, der er bundet af internettet. Nogle slutpunkter i denne kategori er muligvis ikke hostet i Microsoft-datacentre. Eksempler omfatter  *https://odc.officeapps.live.com*  og  *https://appexsin.stb.s-msn.com*.

Du kan finde flere Office 365 om teknikker til netværksoptimering i artiklen [Office 365 slutpunkter](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Sammenligning af perimetersikkerhed på netværket med slutpunktssikkerhed
<a name="BKMK_SecurityComparison"> </a>

Formålet med traditionel netværkssikkerhed er at skærpe virksomhedens netværksperimeter mod indtrængen og ondsindede udnyttelser. Efterhånden som organisationer Microsoft 365, overføres nogle netværkstjenester og data delvist eller fuldstændigt til skyen. Med hensyn til enhver grundlæggende ændring af netværksarkitekturen kræver denne proces en ny form for netværkssikkerhed, der tager højde for nye faktorer:
  
- Efterhånden som skytjenester anvendes, fordeles netværkstjenester og data mellem lokale datacentre og skyen, og perimetersikkerhed er ikke længere tilstrækkelig i sig selv.
- Eksterne brugere opretter forbindelse til virksomhedens ressourcer både i lokale datacentre og i skyen fra tilgængelige steder som f.eks. huse, huse og kaffecentre.
- Formålsbyggede sikkerhedsfunktioner bliver mere og mere indbyggede i skytjenester og kan potentielt supplere eller erstatte eksisterende sikkerhedssystemer.

Microsoft tilbyder en lang række Microsoft 365-sikkerhedsfunktioner og giver præskriptiv vejledning til at anvende bedste praksis for sikkerhed, der kan hjælpe dig med at sikre data og netværkssikkerhed for Microsoft 365. Anbefalede bedste fremgangsmåder omfatter følgende:
  
- **Brug multifaktorgodkendelse (MFA)** MFA føjer et ekstra lag beskyttelse til en strategi for stærk adgangskode ved at kræve, at brugerne skal bekræfte et telefonopkald, en sms-besked eller en appmeddelelse på deres smartphone efter korrekt indtastning af deres adgangskode.

- **Brug Microsoft Defender til skyapps** Konfigurer politikker til at registrere unormal aktivitet og handle på den. Konfigurer beskeder med Microsoft Defender til skyapps, så administratorer kan gennemse usædvanlig eller risikabel brugeraktivitet, f.eks hentning af store mængder data, flere mislykkede logonforsøg eller forbindelser fra en ukendt eller farlig IP-adresse.

- **Konfigurere forebyggelse af datatab (DLP)** DLP gør det muligt for dig at identificere følsomme data og oprette politikker, der er med til at forhindre dine brugere i utilsigtet eller tilsigtet deling af data. DLP fungerer på tværs Microsoft 365 herunder Exchange Online, SharePoint Online og OneDrive så brugerne kan overholde reglerne uden at afbryde deres arbejdsproces.

- **Brug kunde-lockbox** Som administrator Microsoft 365 administrator kan du bruge kundelåsfeltet til at styre, hvordan en Microsoft-supporttekniker får adgang til dine data under en hjælpesession. I tilfælde hvor teknikeren kræver adgang til dine data for at foretage fejlfinding og løse et problem, giver kundelåsfeltet dig mulighed for at godkende eller afvise adgangsanmodningen.

- **Brug Office 365 Secure Score** A-sikkerhedsanalyseværktøj, der anbefaler, hvad du kan gøre for yderligere at reducere risikoen. Secure Score kigger på dine Microsoft 365 aktiviteter og sammenligner dem med en oprindelig plan, der er oprettet af Microsoft. Du får et resultat, der er baseret på, hvor justeret du er med de bedste sikkerhedsmetoder.

En ekstra tilgang til forbedret sikkerhed bør omfatte overvejelser om følgende:
  
- Skift fokus fra perimetersikkerhed til slutpunktssikkerhed ved at anvende skybaserede og Office klientsikkerhedsfunktioner.
  - Formindsk sikkerhedsperimeteren til datacenteret
  - Aktivere tilsvarende tillid for brugerenheder på kontoret eller på eksterne placeringer
  - Fokuser på sikring af dataplaceringen og brugerplaceringen
  - Administrerede bruger maskiner har større tillid til slutpunktssikkerhed
- Administrer alle oplysningers sikkerhed på egen hånd, ikke udelukkende fokuserer på perimeteren
  - Omdefiner WAN og opbygger perimeternetværkssikkerhed ved at tillade pålidelig trafik at omgå sikkerhedsenheder og adskille ikke-administrerede enheder til Wi-Fi netværk
  - Reducer krav til netværkssikkerhed for virksomhedens WAN-grænse
  - Nogle enheder til perimetersikkerhed for netværket, f.eks. firewalls, er stadig påkrævet, men indlæsningen reduceres
  - Sikrer lokale udgangspunkter for Microsoft 365 trafik
- Forbedringerne kan løses trinvist som beskrevet i [sektionen Trinvis](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) optimering. Nogle optimeringsteknikker kan tilbyde bedre omkostnings-/fordelsforhold afhængigt af din netværksarkitektur, og du skal vælge optimeringer, der giver mest mening for din organisation.

Du kan finde flere Microsoft 365 om sikkerhed og overholdelse af regler og standarder i [artiklerne Microsoft 365 security](../security/index.yml) [and Microsoft 365 compliance](../compliance/index.yml).
  
## <a name="incremental-optimization"></a>Trinvis optimering
<a name="BKMK_IncOpt"> </a>

Vi har repræsenteret den ideelle netværksforbindelsesmodel for SaaS tidligere i denne artikel, men for mange store organisationer med historisk komplekse netværksarkitekturer vil det ikke være praktisk direkte at foretage alle disse ændringer. I dette afsnit gennemgår vi en række trinvise ændringer, der kan hjælpe med at Microsoft 365 ydeevnen og pålideligheden.
  
De metoder, du skal bruge til at optimere Microsoft 365 trafik, varierer afhængigt af din netværktopologi og de netværksenheder, du har implementeret. Store virksomheder med mange placeringer og komplekse netværksikkerhedspraksisser skal udarbejde en strategi, der omfatter de fleste eller alle de principper, der er anført i afsnittet [Microsoft 365 connectivity principles](microsoft-365-network-connectivity-principles.md#BKMK_Principles), mens mindre organisationer muligvis kun behøver at overveje en eller to.
  
Du kan gribe optimering an som en trinvis proces og anvende hver metode efterfølgende. I følgende tabel vises vigtige optimeringsmetoder i rækkefølge efter deres påvirkning på ventetid og pålidelighed for det største antal brugere.
  
|**Optimeringsmetode**|**Beskrivelse**|**Virkning**|
|:-----|:-----|:-----|
|Lokal DNS-opløsning og internet udgangspunkt  <br/> |Klargør lokale DNS-servere på hver placering, og sørg for Microsoft 365 forbindelser til internettet så tæt som muligt på brugerens placering.  <br/> | Minimere ventetid  <br/>  Forbedre pålidelig forbindelse til det nærmeste Microsoft 365 indgangspunkt  <br/> |
|Tilføj regionale udgangspunkter  <br/> |Hvis virksomhedens netværk har flere placeringer, men kun ét udgangspunkt, skal du tilføje regionale udgangspunkter for at give brugerne mulighed for at oprette forbindelse til det nærmeste Microsoft 365 indgangspunkt.  <br/> | Minimere ventetid  <br/>  Forbedre pålidelig forbindelse til det nærmeste Microsoft 365 indgangspunkt  <br/> |
|Tilsidesætte proxyer og inspektionsenheder  <br/> |Konfigurer browsere med PAC-filer, der sender Microsoft 365 anmodninger direkte til udgangspunkter.  <br/> Konfigurer kantoutere og firewalls for at tillade Microsoft 365 uden inspektion.  <br/> | Minimere ventetid  <br/>  Reducer belastningen på netværksenheder  <br/> |
|Aktivér direkte forbindelse for VPN-brugere  <br/> |For VPN-brugere skal du Microsoft 365 forbindelser til at oprette forbindelse direkte fra brugerens netværk i stedet for via VPN-transportnettet ved at implementere opdelte netværksforbindelser.  <br/> | Minimere ventetid  <br/>  Forbedre pålidelig forbindelse til det nærmeste Microsoft 365 indgangspunkt  <br/> |
|Overfør fra traditionel WAN til SD-WAN  <br/> |SD-WANs (Software Defined Wide Area Networks) forenkler WAN-administration og forbedrer ydeevnen ved at erstatte traditionelle WAN-routere med virtuelle hvidevarer på samme måde som virtualisering af computerressourcer ved hjælp af virtuelle maskiner (VMs).  <br/> | Forbedr ydeevnen og administrationen af WAN-trafik  <br/>  Reducer belastningen på netværksenheder  <br/> |

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 over netværksforbindelse](microsoft-365-networking-overview.md)

[Administrere Office 365 slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)

[Content Delivery Networks](content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://aka.ms/netonboard)

[Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Networking-blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
