---
title: Microsoft 365 principper for netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Denne artikel indeholder den nyeste vejledning til sikker optimering af Microsoft 365-netværksforbindelsen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 76bbad1b392966f9140db36cf4adbbfff7b62b2b
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940948"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Microsoft 365 principper for netværksforbindelse

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Før du begynder at planlægge dit netværk til Microsoft 365-netværksforbindelsen, er det vigtigt at forstå principperne for sikker administration af Microsoft 365-trafik og opnå den bedst mulige ydeevne. Denne artikel hjælper dig med at forstå den nyeste vejledning til sikker optimering af Microsoft 365-netværksforbindelsen.
  
Traditionelle virksomhedsnetværk er primært designet til at give brugerne adgang til programmer og data, der hostes i virksomhedsdrevne datacentre med stærk perimetersikkerhed. Den traditionelle model forudsætter, at brugerne får adgang til programmer og data fra virksomhedens netværksperimeter, via WAN-links fra forgreninger eller fjernadgang via VPN-forbindelser.
  
Indførelsen af SaaS-programmer som Microsoft 365 flytter nogle kombinationer af tjenester og data uden for netværksperimeteren. Uden optimering er trafik mellem brugere og SaaS-programmer underlagt ventetid, der introduceres af pakkekontrol, netværkshårnåle, utilsigtede forbindelser til geografisk fjerne slutpunkter og andre faktorer. Du kan sikre den bedste ydeevne og pålidelighed i Microsoft 365 ved at forstå og implementere retningslinjer for nøgleoptimering.
  
I denne artikel får du mere at vide om:
  
- [Microsoft 365-arkitektur](microsoft-365-network-connectivity-principles.md#BKMK_Architecture) , som den gælder for kundeforbindelse til clouden
- Opdaterede principper og strategier for [microsoft 365-forbindelse](microsoft-365-network-connectivity-principles.md#BKMK_Principles) til optimering af netværkstrafik og slutbrugeroplevelsen
- [Webtjenesten Office 365 Endpoints](microsoft-365-network-connectivity-principles.md#BKMK_WebSvc), som gør det muligt for netværksadministratorer at bruge en struktureret liste over slutpunkter til brug i netværksoptimering
- [Nye Office 365-slutpunktskategorier](microsoft-365-network-connectivity-principles.md#BKMK_Categories) og optimeringsvejledning
- [Sammenligning af netværksperimetersikkerhed med slutpunktssikkerhed](microsoft-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- [Indstillinger for trinvis optimering](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) af Microsoft 365-trafik
- [Microsoft 365-forbindelsestest](https://aka.ms/netonboard), et nyt værktøj til test af grundlæggende forbindelse til Microsoft 365

## <a name="microsoft-365-architecture"></a>Microsoft 365-arkitektur
<a name="BKMK_Architecture"> </a>

Microsoft 365 er en saaS-cloud (Software-as-a-Service), der leverer produktivitets- og samarbejdsscenarier via en lang række mikrotjenester og programmer, f.eks. Exchange Online, SharePoint Online, Skype for Business Online, Microsoft Teams, Exchange Online Protection, Office i en browser og mange andre. Selvom specifikke Microsoft 365-programmer kan have deres unikke funktioner, da det gælder for kundenetværk og forbindelse til clouden, deler de alle nogle vigtige principaler, mål og arkitekturmønstre. Disse principper og arkitekturmønstre for forbindelse er typiske for mange andre SaaS-cloudmiljøer og er samtidig forskellige fra de typiske udrulningsmodeller for cloudmiljøer af typen Platform-as-a-Service og Infrastructure-as-a-Service, f.eks. Microsoft Azure.
  
En af de vigtigste arkitektoniske funktioner i Microsoft 365 (der ofte overses eller misforstås af netværksarkitekter) er, at det er en virkelig global distribueret tjeneste i konteksten af, hvordan brugerne opretter forbindelse til den. Placeringen af Mål-Microsoft 365-lejeren er vigtig for at forstå det sted, hvor kundedata gemmes i cloudmiljøet, men brugeroplevelsen med Microsoft 365 involverer ikke, at der oprettes direkte forbindelse til diske, der indeholder dataene. Brugeroplevelsen med Microsoft 365 (herunder ydeevne, pålidelighed og andre vigtige kvalitetsegenskaber) omfatter forbindelse via yderst distribuerede frontdøre til tjenester, der skaleres ud over hundredvis af Microsoft-placeringer over hele verden. I de fleste tilfælde opnås den bedste brugeroplevelse ved at give kundenetværket tilladelse til at dirigere brugeranmodninger til det nærmeste Microsoft 365-tjenesteindgangspunkt i stedet for at oprette forbindelse til Microsoft 365 via et udgående punkt på en central placering eller et centralt område.
  
For de fleste kunder distribueres Microsoft 365-brugere på tværs af mange placeringer. For at opnå de bedste resultater skal de principper, der er beskrevet i dette dokument, ses ud fra scale-out-synspunkt (ikke scale-up) med fokus på optimering af forbindelsen til det nærmeste tilstedeværelsespunkt i Microsoft Global Network og ikke til den geografiske placering af Microsoft 365-lejeren. Det betyder grundlæggende, at selvom Microsoft 365-lejerdata kan gemmes på en bestemt geografisk placering, forbliver Microsoft 365-oplevelsen for den pågældende lejer distribueret og kan være til stede i meget tæt (netværk) tæt på alle slutbrugerens placeringer, som lejeren har.
  
## <a name="microsoft-365-connectivity-principles"></a>Principper for Microsoft 365-forbindelse
<a name="BKMK_Principles"> </a>

Microsoft anbefaler følgende principper for at opnå optimal forbindelse og ydeevne til Microsoft 365. Brug disse principper for Microsoft 365-forbindelse til at administrere din trafik og opnå den bedste ydeevne, når du opretter forbindelse til Microsoft 365.
  
Det primære mål i netværksdesignet bør være at minimere ventetiden ved at reducere rundturstiden (RTT) fra dit netværk til Microsoft Global Network, Microsofts offentlige netværks backbone, der forbinder alle Microsofts datacentre med lav ventetid og indgangspunkter for cloudprogrammer spredt over hele verden. Du kan få mere at vide om Microsoft Global Network på [Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificer og differentiere Microsoft 365-trafik

![Identificer Microsoft 365-trafik.](../media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identificering af Microsoft 365-netværkstrafik er det første skridt til at kunne skelne denne trafik fra generisk internetbundet netværkstrafik. Microsoft 365-forbindelse kan optimeres ved at implementere en kombination af fremgangsmåder som optimering af netværksrute, firewallregler, browserproxyindstillinger og omgåelse af netværksinspektionsenheder for visse slutpunkter.
  
Tidligere vejledning til Microsoft 365-optimering opdelte Microsoft 365-slutpunkter i to kategorier, **Required** og **Optional**. Da slutpunkter er blevet tilføjet for at understøtte nye Microsoft 365-tjenester og -funktioner, har vi omorganiseret Microsoft 365-slutpunkter i tre kategorier: **Optimer**, **Tillad** og **Standard**. Retningslinjer for hver kategori gælder for alle slutpunkter i kategorien, hvilket gør optimeringer nemmere at forstå og implementere.
  
Du kan finde flere oplysninger om Microsoft 365-slutpunktskategorier og -optimeringsmetoder i afsnittet [Nye Office 365-slutpunktskategorier](microsoft-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft publicerer nu alle Microsoft 365-slutpunkter som en webtjeneste og giver vejledning i, hvordan disse data bedst kan bruges. Du kan finde flere oplysninger om, hvordan du henter og arbejder med Microsoft 365-slutpunkter, i artiklen [Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Udgående netværksforbindelser lokalt

![Udgående netværksforbindelser lokalt.](../media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Lokal DNS- og internetudgående data er afgørende for at reducere forbindelsesventetiden og sikre, at der oprettes brugerforbindelser til det nærmeste indgangspunkt til Microsoft 365-tjenester. I en kompleks netværkstopologi er det vigtigt at implementere både lokal DNS og lokal internet udgang sammen. Du kan få flere oplysninger om, hvordan Microsoft 365 dirigerer klientforbindelser til det nærmeste indgangspunkt, i artiklen [Client Connectivity](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Forud for fremkomsten af cloudtjenester som Microsoft 365 var slutbrugernes internetforbindelse en designfaktor i netværksarkitekturen relativt enkel. Når internettjenester og websteder distribueres rundt om i verden, ventetid mellem virksomhedernes udgående punkter og enhver given destination slutpunkt er stort set en funktion af geografisk afstand.
  
I en traditionel netværksarkitektur gennemgår alle udgående internetforbindelser virksomhedens netværk og udgående data fra en central placering. Efterhånden som Microsofts cloudtilbud er modnet, er en distribueret netværksarkitektur på internettet blevet afgørende for at understøtte ventetidsfølsomme cloudtjenester. Microsoft Global Network er udviklet til at imødekomme ventetidskrav med Front Door-infrastrukturen for distribuerede tjenester, der er et dynamisk stof af globale indgangspunkter, der dirigerer indgående cloudtjenesteforbindelser til det nærmeste indgangspunkt. Dette er beregnet til at reducere længden af den "sidste mil" for Microsoft-cloudkunder ved effektivt at forkorte ruten mellem kunden og cloudmiljøet.
  
Enterprise WAN'er er ofte designet til at backhaul netværkstrafik til en central virksomhed hovedkontor for inspektion, før udgående til internettet, som regel gennem en eller flere proxy-servere. Nedenstående diagram illustrerer en sådan netværkstopologi.
  
![Traditionel virksomhedsnetværksmodel.](../media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Da Microsoft 365 kører på Microsoft Global Network, som omfatter frontendservere over hele verden, vil der ofte være en frontendserver tæt på brugerens placering. Ved at angive lokal internet udgående data og ved at konfigurere interne DNS-servere til at levere lokal navneopløsning for Microsoft 365-slutpunkter kan netværkstrafik, der er beregnet til Microsoft 365, oprette forbindelse til Microsoft 365-frontendservere så tæt som muligt på brugeren. Nedenstående diagram viser et eksempel på en netværkstopologi, der giver brugere, der opretter forbindelse fra hovedkontorer, forgreninger og fjernplaceringer, mulighed for at følge den korteste rute til det nærmeste Microsoft 365-indgangspunkt.
  
![WAN-netværksmodel med regionale udgående punkter.](../media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Hvis netværksstien forkortes til Microsoft 365-indgangspunkter på denne måde, kan det forbedre forbindelsesydeevnen og slutbrugeroplevelsen i Microsoft 365 og kan også hjælpe med at reducere virkningen af fremtidige ændringer af netværksarkitekturen på Microsoft 365-ydeevne og -pålidelighed.
  
DNS-anmodninger kan også medføre ventetid, hvis den reagerende DNS-server er fjern eller optaget. Du kan minimere ventetiden for navnefortsættelse ved at klargøre lokale DNS-servere på forgreningsplaceringer og sikre, at de er konfigureret til at cachelagre DNS-poster korrekt.
  
Mens regional udgående data kan fungere godt for Microsoft 365, er den optimale forbindelsesmodel altid at levere netværksafgang på brugerens placering, uanset om det er på virksomhedens netværk eller fjernplaceringer, f.eks. hjem, hoteller, kaffebarer og lufthavne. Denne lokale model for direkte udgående data er repræsenteret i diagrammet nedenfor.
  
![Arkitektur for lokalt udgående netværk.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Virksomheder, der har indført Microsoft 365, kan drage fordel af Microsoft Global Network's Distributed Service Front Door-arkitektur ved at sikre, at brugerforbindelser til Microsoft 365 tager den kortest mulige rute til det nærmeste Microsoft Global Network-indgangspunkt. Arkitekturen for det lokale udgående netværk gør dette ved at tillade, at Microsoft 365-trafik dirigeres over den nærmeste udgående trafik, uanset brugerens placering.
  
Den lokale udgangsarkitektur har følgende fordele i forhold til den traditionelle model:
  
- Giver optimal ydeevne i Microsoft 365 ved at optimere rutelængden. Slutbrugerforbindelser dirigeres dynamisk til det nærmeste Microsoft 365-indgangspunkt af Front Door-infrastrukturen for distribuerede tjenester.
- Reducerer belastningen af virksomhedens netværksinfrastruktur ved at tillade lokal udgående data.
- Sikrer forbindelser i begge ender ved at udnytte klientslutpunktsikkerhed og cloudsikkerhedsfunktioner.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Undgå netværkshårnåle

![Undgå hårnåle.](../media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Som en generel tommelfingerregel giver den korteste, mest direkte rute mellem brugeren og det nærmeste Microsoft 365-slutpunkt den bedste ydeevne. En netværkspin sker, når WAN- eller VPN-trafik, der er bundet til en bestemt destination, først dirigeres til en anden mellemliggende placering (f.eks. sikkerhedsstak, cloudadgangsmægler eller cloudbaseret webgateway), der introducerer ventetid og potentiel omdirigering til et geografisk fjernt slutpunkt. Netværkshårnåle kan også skyldes ineffektivitet i forbindelse med routing/peering eller ikke-optimale (eksterne) DNS-opslag.
  
Hvis du vil sikre dig, at Microsoft 365-forbindelsen ikke er underlagt netværkspins, selv i det lokale udgående tilfælde, skal du kontrollere, om den internetudbyder, der bruges til at give udgående internet for brugerens placering, har en direkte peering-relation til Microsoft Global Network i nærheden af denne placering. Det kan også være en god idé at konfigurere udgående routing til at sende Microsoft 365-trafik, der er tillid til, direkte i modsætning til proxying eller tunnelføring via en tredjepartsudbyder af cloud- eller cloudbaseret netværkssikkerhed, der behandler din internetbundne trafik. Opløsningen af lokale DNS-navne for Microsoft 365-slutpunkter hjælper med at sikre, at ud over direkte routing bruges de nærmeste Microsoft 365-indgangspunkter til brugerforbindelser.
  
Hvis du bruger cloudbaserede netværks- eller sikkerhedstjenester til din Microsoft 365-trafik, skal du sikre, at resultatet af hårnålen evalueres, og at dets indvirkning på Microsoft 365-ydeevnen forstås. Dette kan gøres ved at undersøge antallet og placeringen af tjenesteudbyderens placeringer, hvorigennem trafikken videresendes i forhold til antallet af dine forgreningskontorer og Microsoft Global Network-peeringpunkter, kvaliteten af netværkspeeringsforholdet mellem tjenesteudbyderen og internetudbyderen og Microsoft samt indvirkningen på ydeevnen af backhauling i tjenesteudbyderens infrastruktur.
  
På grund af det store antal distribuerede placeringer med Microsoft 365-indgangspunkter og deres nærhed til slutbrugere kan routing af Microsoft 365-trafik til et hvilket som helst tredjepartsnetværk eller sikkerhedsudbyder have en negativ indvirkning på Microsoft 365-forbindelser, hvis udbydernetværket ikke er konfigureret til optimal Microsoft 365-peering.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Vurder omgåelse af proxyer, trafikkontrolenheder og duplikerede sikkerhedsteknologier

![Omgå proxyer, trafikkontrolenheder og duplikerede sikkerhedsteknologier.](../media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Virksomhedskunder bør gennemgå deres metoder til netværkssikkerhed og risikoreduktion specifikt for Microsoft 365-bundet trafik og bruge Microsoft 365-sikkerhedsfunktioner til at reducere deres afhængighed af påtrængende, ydeevnepåvirkning og dyre teknologier til netværkssikkerhed til Microsoft 365-netværkstrafik.
  
De fleste virksomhedsnetværk gennemtvinger netværkssikkerhed for internettrafik ved hjælp af teknologier som proxyer, SSL-inspektion, pakkekontrol og systemer til forebyggelse af datatab. Disse teknologier giver en vigtig risikoafhjælpning for generiske internetanmodninger, men kan reducere ydeevnen, skalerbarheden og kvaliteten af slutbrugerens oplevelse væsentligt, når de anvendes på Microsoft 365-slutpunkter.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 Endpoints-webtjeneste

Microsoft 365-administratorer kan bruge et script eller REST-kald til at bruge en struktureret liste over slutpunkter fra Office 365 Endpoints-webtjenesten og opdatere konfigurationerne af perimeterfirewalls og andre netværksenheder. Dette sikrer, at trafik, der er bundet til Microsoft 365, identificeres, behandles korrekt og administreres forskelligt fra netværkstrafik, der er bundet til generiske og ofte ukendte internetwebsteder. Du kan finde flere oplysninger om, hvordan du bruger Office 365 Endpoints-webtjenesten, i artiklen [Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC-scripts (proxy automatisk konfiguration)
<a name="BKMK_WebSvc"> </a>

Microsoft 365-administratorer kan oprette PAC-scripts (proxy automatisk konfiguration), der kan leveres til brugercomputere via WPAD eller GPO. PAC-scripts kan bruges til at omgå proxyer for Microsoft 365-anmodninger fra WAN- eller VPN-brugere, så Microsoft 365-trafik kan bruge direkte internetforbindelser i stedet for at gennemgå virksomhedens netværk.
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365-sikkerhedsfunktioner
<a name="BKMK_WebSvc"> </a>

Microsoft er gennemsigtig omkring datacentersikkerhed, driftsmæssig sikkerhed og risikoreduktion omkring Microsoft 365-servere og de netværksslutpunkter, de repræsenterer. Indbyggede sikkerhedsfunktioner i Microsoft 365 er tilgængelige til reduktion af netværkssikkerhedsrisici, f.eks. Microsoft Purview Data Loss Prevention, Anti-Virus, Multi-Factor Authentication, Customer Lock Box, Defender for Office 365, Microsoft 365 Threat Intelligence, Microsoft 365 Secure Score, Exchange Online Protection og Network DDOS Security.
  
Du kan få flere oplysninger om Microsoft-datacenter og global netværkssikkerhed i [Microsoft Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nye Office 365-slutpunktskategorier
<a name="BKMK_Categories"> </a>

Office 365-slutpunkter repræsenterer et varieret sæt netværksadresser og undernet. Slutpunkter kan være URL-adresser, IP-adresser eller IP-områder, og nogle slutpunkter er angivet med specifikke TCP/UDP-porte. URL-adresser kan enten være et FQDN som *account.office.net* eller en URL-adresse med jokertegn som *\*.office365.com*.
  
> [!NOTE]
> Placeringerne af Office 365-slutpunkter i netværket er ikke direkte relateret til placeringen af Microsoft 365-lejerdataene. Derfor bør kunderne se på Microsoft 365 som en distribueret og global tjeneste og bør ikke forsøge at blokere netværksforbindelser til Office 365-slutpunkter baseret på geografiske kriterier.
  
I vores tidligere vejledning til administration af Microsoft 365-trafik var slutpunkter organiseret i to kategorier: **Påkrævet** og **Valgfri**. Slutpunkter inden for hver kategori krævede forskellige optimeringer afhængigt af tjenestens kritiskhed, og mange kunder stod over for udfordringer ved at retfærdiggøre anvendelsen af de samme netværksoptimeringer til den komplette liste over Office 365 URL-adresser og IP-adresser.
  
I den nye model er slutpunkter opdelt i tre kategorier, **Optimer**, **Tillad** og **Standard**, hvilket giver et prioritetsbaseret pivot for, hvor du kan fokusere på netværksoptimeringsindsatsen for at opnå de bedste ydeevneforbedringer og investeringsafkast. Slutpunkterne konsolideres i ovenstående kategorier baseret på følsomheden af den effektive brugeroplevelse med hensyn til netværkskvalitet, volumen og ydeevnekonvolut af scenarier og nem implementering. Anbefalede optimeringer kan anvendes på samme måde for alle slutpunkter i en given kategori.
  
- **Optimering** af slutpunkter kræves for at oprette forbindelse til alle Office 365-tjenester og repræsenterer over 75 % af Office 365-båndbredde, forbindelser og datamængde. Disse slutpunkter repræsenterer Office 365-scenarier, der er mest følsomme over for netværkets ydeevne, ventetid og tilgængelighed. Alle slutpunkter hostes i Microsoft-datacentre. Ændringshastigheden for slutpunkterne i denne kategori forventes at være meget lavere end for slutpunkterne i de to andre kategorier. Denne kategori indeholder et lille (i rækkefølge efter ca. 10) sæt vigtige URL-adresser og et defineret sæt IP-undernet, der er dedikeret til centrale Office 365-arbejdsbelastninger, f.eks. Exchange Online, SharePoint Online, Skype for Business Online og Microsoft Teams.

    En komprimeret liste over veldefinerede kritiske slutpunkter bør hjælpe dig med at planlægge og implementere netværksoptimeringer med høj værdi for disse destinationer hurtigere og nemmere.

    Eksempler på  *Optimer*  slutpunkter omfatter *https://outlook.office365.com*, *https://\<tenant\>.sharepoint.com* og *https://\<tenant\>-my.sharepoint.com*.

    Optimeringsmetoder omfatter:

  - Tilsidesæt  *optimeringsslutpunkter*  på netværksenheder og -tjenester, der udfører trafikopfangning, SSL-dekryptering, detaljeret pakkekontrol og indholdsfiltrering.
  - Tilsidesæt proxyenheder i det lokale miljø og cloudbaserede proxytjenester, der ofte bruges til generisk internetbrowsing.
  - Prioriter evalueringen af disse slutpunkter, som din netværksinfrastruktur og perimetersystemer har fuld tillid til.
  - Prioriter reduktion eller eliminering af WAN-backhauling, og faciliter direkte distribuerede internetbaserede udgående data for disse slutpunkter så tæt på brugere/forgreninger som muligt.
  - Faciliter direkte forbindelse til disse cloudslutpunkter for VPN-brugere ved at implementere opdelt tunnelføring.
  - Sørg for, at DE IP-adresser, der returneres af DNS-navnefortsættelsen, svarer til routing egress-stien for disse slutpunkter.
  - Prioriter disse slutpunkter for SD-WAN-integration for direkte og minimal ventetidsrouting til det nærmeste internet-peeringpunkt i Microsofts globale netværk.

- **Tillad** slutpunkter er påkrævet for at oprette forbindelse til bestemte Office 365-tjenester og -funktioner, men de er ikke så følsomme over for netværkets ydeevne og ventetid som dem i kategorien *Optimer* . Det samlede netværksaftryk for disse slutpunkter set ud fra båndbredden og antallet af forbindelser er også mindre. Disse slutpunkter er dedikeret til Office 365 og hostes i Microsoft-datacentre. De repræsenterer et bredt sæt office 365-mikrotjenester og deres afhængigheder (i rækkefølgen af ca. 100 URL-adresser) og forventes at ændre sig med en højere hastighed end dem i kategorien  *Optimer*  . Ikke alle slutpunkter i denne kategori er knyttet til definerede dedikerede IP-undernet.

    Netværksoptimeringer for  *Tillad*  slutpunkter kan forbedre Office 365-brugeroplevelsen, men nogle kunder kan vælge at begrænse disse optimeringer mere snævert for at minimere ændringer af deres netværk.

    Eksempler på *Allow* endpoints omfatter *https://\*.protection.outlook.com* og *https://accounts.accesscontrol.windows.net*.

    Optimeringsmetoder omfatter:

  - Tilsidesæt *Tillad*  slutpunkter på netværksenheder og -tjenester, der udfører trafikaflytning, SSL-dekryptering, detaljeret pakkekontrol og indholdsfiltrering.
  - Prioriter evalueringen af disse slutpunkter, som din netværksinfrastruktur og perimetersystemer har fuld tillid til.
  - Prioriter reduktion eller eliminering af WAN-backhauling, og faciliter direkte distribuerede internetbaserede udgående data for disse slutpunkter så tæt på brugere/forgreninger som muligt.
  - Sørg for, at DE IP-adresser, der returneres af DNS-navnefortsættelsen, svarer til routing egress-stien for disse slutpunkter.
  - Prioriter disse slutpunkter for SD-WAN-integration for direkte og minimal ventetidsrouting til det nærmeste internet-peeringpunkt i Microsofts globale netværk.

- **Standardslutpunkter** repræsenterer Office 365-tjenester og -afhængigheder, der ikke kræver nogen optimering, og kan behandles af kundenetværk som normal internetbundet trafik. Nogle slutpunkter i denne kategori hostes muligvis ikke i Microsoft-datacentre. Eksempler omfatter  *https://odc.officeapps.live.com*  og  *`https://appexsin.stb.s-msn.com`*.

Du kan finde flere oplysninger om teknikker til netværksoptimering af Office 365 i artiklen [Administration af Office 365-slutpunkter](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Sammenligning af netværksperimetersikkerhed med slutpunktssikkerhed
<a name="BKMK_SecurityComparison"> </a>

Målet med traditionel netværkssikkerhed er at hærde virksomhedens netværksperimeter mod indtrængen og ondsindede udnyttelser. I takt med at organisationer bruger Microsoft 365, overføres nogle netværkstjenester og data delvist eller fuldstændigt til cloudmiljøet. Hvad angår enhver grundlæggende ændring af netværksarkitekturen, kræver denne proces en revaluering af netværkssikkerheden, hvor der tages højde for nye faktorer:
  
- I takt med at cloudtjenesterne anvendes, distribueres netværkstjenester og data mellem datacentre i det lokale miljø og cloudmiljøet, og perimetersikkerhed er ikke længere tilstrækkelig alene.
- Fjernbrugere opretter forbindelse til virksomhedsressourcer både i datacentre i det lokale miljø og i cloudmiljøet fra ikke-kontrollerede steder, f.eks. hjem, hoteller og kaffebarer.
- Specialbyggede sikkerhedsfunktioner er i stigende grad indbygget i cloudtjenester og kan potentielt supplere eller erstatte eksisterende sikkerhedssystemer.

Microsoft tilbyder en lang række microsoft 365-sikkerhedsfunktioner og giver en præskriptiv vejledning til anvendelse af bedste praksis for sikkerhed, der kan hjælpe dig med at sikre data- og netværkssikkerhed for Microsoft 365. Anbefalede bedste fremgangsmåder omfatter følgende:
  
- **Brug multifaktorgodkendelse (MFA)** MFA føjer et ekstra lag af beskyttelse til en stærk adgangskodestrategi ved at kræve, at brugerne skal bekræfte et telefonopkald, en sms eller en appmeddelelse på deres smartphone, når de har indtastet deres adgangskode korrekt.

- **Brug Microsoft Defender til Cloud Apps** Konfigurer politikker for at spore uregelmæssig aktivitet og reagere på den. Konfigurer beskeder med Microsoft Defender for Cloud Apps, så administratorer kan gennemse usædvanlig eller risikabel brugeraktivitet, f.eks. download af store mængder data, flere mislykkede logonforsøg eller forbindelser fra en ukendt eller farlig IP-adresse.

- **Konfigurer DLP (Forebyggelse af datatab)** DLP giver dig mulighed for at identificere følsomme data og oprette politikker, der hjælper med at forhindre dine brugere i utilsigtet eller bevidst at dele dataene. DLP fungerer på tværs af Microsoft 365, herunder Exchange Online, SharePoint Online og OneDrive, så dine brugere kan overholde angivne standarder uden at afbryde deres arbejdsproces.

- **Brug kundelåseboks** Som Microsoft 365-administrator kan du bruge Customer Lockbox til at styre, hvordan en Microsoft-supporttekniker får adgang til dine data under en hjælpsession. I de tilfælde, hvor teknikeren kræver adgang til dine data for at foretage fejlfinding og løse et problem, giver Customer Lockbox dig mulighed for at godkende eller afvise adgangsanmodningen.

- **Brug Office 365 Secure Score** Et værktøj til sikkerhedsanalyse, der anbefaler, hvad du kan gøre for yderligere at reducere risikoen. Secure Score kigger på dine Microsoft 365-indstillinger og -aktiviteter og sammenligner dem med en baseline, der er oprettet af Microsoft. Du får en score baseret på, hvordan du er justeret i forhold til bedste sikkerhedspraksis.

En holistisk tilgang til forbedret sikkerhed bør omfatte følgende overvejelser:
  
- Skift fokus fra perimetersikkerhed til slutpunktssikkerhed ved at anvende skybaserede sikkerhedsfunktioner og Office-klientsikkerhedsfunktioner.
  - Gør sikkerhedsperimeteren mindre til datacenteret
  - Aktivér tilsvarende tillid for brugerenheder på kontoret eller på eksterne placeringer
  - Fokuser på sikring af dataplaceringen og brugerplaceringen
  - Administrerede brugercomputere har større tillid til slutpunktssikkerhed
- Administrer al informationssikkerhed holistisk, ikke kun med fokus på perimeteren
  - Omdefiner WAN, og opret perimeternetværkssikkerhed ved at tillade pålidelig trafik at omgå sikkerhedsenheder og adskille ikke-administrerede enheder til gæstenetværk Wi-Fi netværk
  - Reducer kravene til netværkssikkerhed for virksomhedens WAN-kant
  - Nogle sikkerhedsenheder til netværksperimeter, f.eks. firewalls, er stadig påkrævet, men belastningen reduceres
  - Sikrer lokal udgang for Microsoft 365-trafik
- Forbedringer kan håndteres trinvist som beskrevet i afsnittet [Trinvis optimering](microsoft-365-network-connectivity-principles.md#BKMK_IncOpt) . Nogle optimeringsteknikker kan give bedre forholdet mellem omkostninger og fordele, afhængigt af din netværksarkitektur, og du bør vælge optimeringer, der giver mest mening for din organisation.

Du kan få flere oplysninger om microsoft 365-sikkerhed og -overholdelse i artiklerne [Microsoft 365-sikkerhed](../security/index.yml) og [Microsoft Purview](../compliance/index.yml).
  
## <a name="incremental-optimization"></a>Trinvis optimering
<a name="BKMK_IncOpt"> </a>

Vi har repræsenteret den ideelle model til netværksforbindelser til SaaS tidligere i denne artikel, men for mange store organisationer med historisk komplekse netværksarkitekturer vil det ikke være praktisk at foretage alle disse ændringer direkte. I dette afsnit gennemgår vi en række trinvise ændringer, der kan hjælpe med at forbedre Ydeevnen og pålideligheden af Microsoft 365.
  
De metoder, du skal bruge til at optimere Microsoft 365-trafik, varierer afhængigt af din netværkstopologi og de netværksenheder, du har implementeret. Store virksomheder med mange placeringer og komplekse fremgangsmåder for netværkssikkerhed skal udvikle en strategi, der indeholder de fleste eller alle de principper, der er angivet i afsnittet [om principper for forbindelse til Microsoft 365](microsoft-365-network-connectivity-principles.md#BKMK_Principles) , mens mindre organisationer muligvis kun skal overveje en eller to.
  
Du kan nærme dig optimering som en trinvis proces og anvende hver metode efterfølgende. I følgende tabel vises nøgleoptimeringsmetoder i rækkefølge efter deres indvirkning på ventetid og pålidelighed for det største antal brugere.
  
|**Optimeringsmetode**|**Beskrivelse**|**Indvirkning**|
|:-----|:-----|:-----|
|Lokal DNS-opløsning og internet udgående data  <br/> |Klargør lokale DNS-servere på hver placering, og sørg for, at Microsoft 365-forbindelser udgående til internettet så tæt som muligt på brugerens placering.  <br/> | Minimer ventetid  <br/>  Gør pålidelig forbindelse til det nærmeste Microsoft 365-indgangspunkt bedre  <br/> |
|Tilføj regionale udgående punkter  <br/> |Hvis virksomhedens netværk har flere placeringer, men kun ét udgående punkt, skal du tilføje regionale udgående punkter for at give brugerne mulighed for at oprette forbindelse til det nærmeste Microsoft 365-indgangspunkt.  <br/> | Minimer ventetid  <br/>  Gør pålidelig forbindelse til det nærmeste Microsoft 365-indgangspunkt bedre  <br/> |
|Omgå proxyer og kontrolenheder  <br/> |Konfigurer browsere med PAC-filer, der sender Microsoft 365-anmodninger direkte til udgående data.  <br/> Konfigurer edge routere og firewalls for at tillade Microsoft 365-trafik uden inspektion.  <br/> | Minimer ventetid  <br/>  Reducer belastningen på netværksenheder  <br/> |
|Aktivér direkte forbindelse for VPN-brugere  <br/> |For VPN-brugere skal du gøre det muligt for Microsoft 365-forbindelser at oprette direkte forbindelse fra brugerens netværk i stedet for via VPN-tunnellen ved at implementere opdelt tunnelføring.  <br/> | Minimer ventetid  <br/>  Gør pålidelig forbindelse til det nærmeste Microsoft 365-indgangspunkt bedre  <br/> |
|Migrer fra traditionelt WAN til SD-WAN  <br/> |SD-WANs (Software Defined Wide Area Networks) forenkler WAN-administration og forbedrer ydeevnen ved at erstatte traditionelle WAN-routere med virtuelle apparater på samme måde som virtualisering af beregningsressourcer ved hjælp af virtuelle maskiner.  <br/> | Gør ydeevnen og administrationen af WAN-trafik bedre  <br/>  Reducer belastningen på netværksenheder  <br/> |

## <a name="related-topics"></a>Relaterede emner

[Oversigt over Microsoft 365 Network Connectivity](microsoft-365-networking-overview.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-adressewebtjeneste](microsoft-365-ip-web-service.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Netværksplanlægning og justering af ydeevne til Microsoft 365](network-planning-and-performance.md)

[Justering af ydeevnen i Office 365 ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Plan for fejlfinding af ydeevne for Office 365](performance-troubleshooting-plan.md)

[Netværk til levering af indhold](content-delivery-networks.md)

[Microsoft 365-forbindelsestest](https://aka.ms/netonboard)

[Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365-netværksblog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
