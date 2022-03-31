---
title: 'Oversigt: VPN-opdeling af Microsoft 365'
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Oversigt over VPN-opdelte netværksforbindelser med Microsoft 365 optimere forbindelse for eksterne brugere.
ms.openlocfilehash: 67ce8a38b536dab12af679ba860aac6d974db60e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601640"
---
# <a name="overview-vpn-split-tunneling-for-microsoft-365"></a>Oversigt: VPN-opdeling af Microsoft 365

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Hvis du vil have detaljeret vejledning til implementering af VPN-opdeling, skal du [se Implementering af VPN-opdeling for at Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdeling af VPN i Almindelige [scenarier for vpnopdelning af Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde en vejledning til sikring Teams medietrafik i VPN-opdelte netværksmiljøer under Sikring [Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md).
>- Du kan finde oplysninger om, hvordan du konfigurerer Stream og livebegivenheder i VPN-miljøer, under Særlige overvejelser [i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan finde oplysninger om optimering Microsoft 365 globale lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for Brugere i Kina](microsoft-365-networking-china.md).

Virksomheder har traditionelt brugt VPN til at understøtte sikre eksterne oplevelser for deres brugere. Mens de grundlæggende arbejdsbelastninger fortsat var i det lokale miljø, var et VPN fra den eksterne klient, der blev distribueret via et datacenter på virksomhedens netværk, den primære metode for eksterne brugere til at få adgang til virksomhedens ressourcer. For at beskytte disse forbindelser opbygger virksomheder lag af netværkssikkerhedsløsninger langs VPN-stier. Denne sikkerhed er bygget til at beskytte intern infrastruktur og for at beskytte mobilbrowsing på eksterne websteder ved at omaroutere trafik til VPN og derefter ud gennem den lokale internetperimeter. VPN, netværksperimetere og tilknyttet sikkerhedsinfrastruktur var ofte formålsbyggede og skalerede for en defineret mængde trafik, typisk hvor de fleste forbindelser blev startet inde fra virksomhedens netværk, og de fleste af dem holder sig inden for de interne netværksgrænser.

I nogen tid var VPN-modeller, hvor alle forbindelser fra fjernbrugerenheden blev dirigeret tilbage til det lokale netværk (kaldet tvungne fjerninger _), i_ høj gradudstungen, så længe den samtidige skala af fjernbrugere var beskeden, og trafikmængden ved hjælp af VPN var lav.  Nogle kunder fortsætter med at bruge VPN-gennemtvingelse som status, selv efter at deres programmer er flyttet inde fra virksomhedens perimeter til offentlige SaaS-skyer.

Brug af gennemtvungne VPN til at oprette forbindelse til distribuerede og ydelsesfølsomme skyprogrammer er suboptimale, men de negative effekter er blevet accepteret af nogle virksomheder for at bevare sikkerhedsstatussen. Nedenfor kan du se et eksempeldiagram over dette scenarie:

![Gennemtvunget Tunnel VPN-konfiguration.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

_Figur 1: En traditionel gennemtvunget Tunnel VPN-løsning._

Dette problem har været voksende i mange år, hvor mange kunder rapporterer om en betydelig ændring i netværksmønstre. Trafik, der plejede at forblive lokalt, opretter nu forbindelse til eksterne skyslutpunkter. Mange Microsoft-kunder rapporterer, at ca. 80 % af deres netværkstrafik tidligere var til en intern kilde (repræsenteret ved den stiplede linje i ovenstående diagram). I 2020 blev dette tal reduceret til omkring 20 % eller lavere, da de har flyttet større arbejdsbelastninger til skyen. Disse tendenser er ikke ualmindelige med andre virksomheder. Efterhånden som rejsen til skyen skrider frem, bliver ovenstående model med tiden stadig mere besværlig og uholdbar, hvilket forhindrer en organisation i at blive Agile, når de bevæger sig ind i en sky-første verden.

Den verdensomspændende COVID-19-krise har eskaleret problemet til øjeblikkelig afhjælpning. Behovet for at sikre medarbejdernes sikkerhed har genereret omfattende krav til virksomhedens it-medarbejdere for at understøtte arbejde hjemmefra og i stort omfang. Microsoft 365 er godt placeret for at hjælpe kunderne med at opfylde denne efterspørgsel, men høj samtidighed for brugere, der arbejder hjemmefra, genererer en stor mængde Microsoft 365-trafik, som medfører hurtig mætning og kører VPN-infrastruktur ud af kapacitet, hvis de dirigeres gennemtvungne VPN- og lokale netværksperimetere. I denne nye virkelighed er brug af VPN til at få adgang til Microsoft 365 ikke længere blot en blokering af ydeevnen, men en svær væg, der ikke kun påvirker Microsoft 365 men vigtige forretningshandlinger, der stadig er afhængige af VPN til at fungere.

Microsoft har arbejdet tæt sammen med kunderne og den bredere branche om at levere effektive, moderne løsninger på disse problemer fra vores egne tjenester og for at komme i overensstemmelse med branchens bedste praksis. [Principperne for forbindelse](./microsoft-365-network-connectivity-principles.md) for Microsoft 365 er designet til at fungere effektivt for eksterne brugere, samtidig med at det stadig giver en organisation tilladelse til at opretholde sikkerhed og kontrol over deres forbindelse. Disse løsninger kan også gennemføres hurtigt med begrænset arbejde, men samtidig opnå en væsentlig positiv effekt på de problemer, der er beskrevet ovenfor.

For kunder, der forbinder deres fjernarbejderenheder til virksomhedens netværk eller skyinfrastruktur via VPN, anbefaler Microsoft, at de vigtigste **Microsoft 365-scenarier Microsoft Teams**, **SharePoint Online** og **Exchange Online** distribueres via en _vpnopdelt konfiguration af lydenheder_. Dette bliver især vigtigt som den første linjestrategi for at lette fortsat medarbejderproduktivitet under større begivenheder, hvor man arbejder hjemmefra, f.eks. COVID-19-krise.

![Opdel Tunnel VPN-konfiguration.](../media/vpn-split-tunneling/vpn-model-2.png)

_Figur 2: En VPN-opdelt løsning med definerede Microsoft 365 der sendes direkte til tjenesten. Al anden trafik gennem krydser VPN-kanalen uanset destination._

Essensen ved denne tilgang er at give virksomheder en simpel metode til at reducere risikoen for mætning af VPN-infrastruktur og markant forbedre Microsoft 365 ydeevnen i den korteste tidsramme. Når du konfigurerer VPN-klienter til at tillade den mest kritiske, Microsoft 365 trafik til at omgå VPN-forbindelsen, opnår du følgende fordele:

- Afhjælper straks den egentlige årsag til størstedelen af kunderapporterede problemer med ydeevnen og netværkskapaciteten i virksomhedens VPN-arkitekturer, der Microsoft 365 brugeroplevelsen
  
  Den anbefalede løsning er specifikt målrettet Microsoft 365 tjenesteslutpunkter kategoriseret som Optimer  i emnet [Microsoft 365 URL-adresser og IP-adresseintervaller](./urls-and-ip-address-ranges.md). Trafik til disse slutpunkter er meget følsom over for ventetid og båndbreddebegrænsning, og aktivering af den til at omgå VPN-signalet kan forbedre slutbrugeroplevelsen markant og reducere belastningen af virksomhedens netværk. Microsoft 365 forbindelser, der ikke udgør størstedelen af båndbredden eller brugeroplevelseens aftryk, fortsat kan dirigeres gennem VPN-båndbredden sammen med resten af den internetbundne trafik. Du kan finde flere oplysninger [i VPN-opdelt strategi](#the-vpn-split-tunnel-strategy).

- Kan konfigureres, testes og implementeres hurtigt af kunder og uden yderligere krav til infrastruktur eller programmer

  Afhængigt af VPN-platformen og netværksarkitekturen kan implementeringen tage så lidt som et par timer. Få mere at vide under [Implementer VPN-opdeling af inddelning](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling).

- Bevarer sikkerheden for kundens VPN-implementeringer ved ikke at ændre, hvordan andre forbindelser dirigeres, herunder trafik til internettet

  Den anbefalede konfiguration følger princippet for **mindste rettighed** for VPN-trafikundtagelser og giver kunderne mulighed for at implementere opdelt VPN uden at udsætte brugere eller infrastruktur for yderligere sikkerhedsrisici. Netværkstrafik, der dirigeres direkte til Microsoft 365-slutpunkter, krypteres, valideres for integritet af Office-klientprograms stakke og begrænses til IP-adresser, der er dedikeret til Microsoft 365-tjenester, der er hardened på både program- og netværksniveau. Du kan finde flere oplysninger under Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier med fjernarbejde [(Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

- Understøttes indbygget af de fleste VPN-virksomhedsplatforme

  Microsoft fortsætter med at samarbejde med branchepartnere, der producerer kommercielle VPN-løsninger, for at hjælpe partnere med at udvikle målrettet vejledning og konfigurationsskabeloner til deres løsninger i overensstemmelse med ovenstående anbefalinger. Få mere at vide under [HOWTO-vejledninger til almindelige VPN-platforme](microsoft-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms).

>[!TIP]
>Microsoft anbefaler, at du fokuserer opdelt vpn-konfiguration på dokumenterede dedikerede IP-områder til Microsoft 365-tjenester. FQDN- eller AppID-baserede opdelte konfigurationer af distributionsservere, mens det er muligt på visse VPN-klientplatforme, dækker muligvis ikke fuldt ud nøglescenarier Microsoft 365 og kan være i konflikt med IP-baserede VPN-routingregler. Derfor anbefaler Microsoft ikke, at du bruger FQDN'er Microsoft 365 konfigurere opdelt VPN af vpn. Brug af FQDN-konfiguration kan være nyttigt i andre relaterede scenarier, f.eks. tilpasninger af .pac-filer eller til at implementere proxy bypass.

Du kan finde en komplet vejledning til implementering [i Implementering af VPN-opdeling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

Hvis du vil have en trinvis proces til at konfigurere Microsoft 365 til eksterne medarbejdere, skal du se [Konfigurer din infrastruktur til fjernarbejde](..\solutions\empower-people-to-work-remotely.md)

## <a name="the-vpn-split-tunnel-strategy"></a>VPN-opdelt strategi

Traditionelle virksomhedsnetværk er ofte designet til at fungere sikkert i en før-skybaseret verden, hvor de vigtigste data, tjenester, programmer hostes lokalt og har direkte forbindelse til det interne virksomhedsnetværk, og det samme er størstedelen af brugerne. Således opbygges netværksinfrastruktur omkring disse elementer på den måde, at afdelingskontorer har forbindelse til hovedkontoret via _MPLS-netværk (Multiproto megapixel Label Switching_ ), og eksterne brugere skal oprette forbindelse til virksomhedens netværk via et VPN for at få adgang til både lokale slutpunkter og internettet. I denne model krydser al trafik fra eksterne brugere virksomhedens netværk og dirigeres til skytjenesten via et almindeligt udgangspunkt.

![Gennemtvunget VPN-konfiguration.](../media/vpn-split-tunneling/vpn-model-1.png)

_Figur 2: En almindelig VPN-løsning for eksterne brugere, hvor al trafik tvinges tilbage til virksomhedens netværk uanset destination_

Efterhånden som organisationer flytter data og programmer til skyen, er denne model begyndt at blive mindre effektiv, da den hurtigt bliver besværlig, dyr og uoverskuelig og i væsentlig grad påvirker brugernes ydeevne og effektivitet i netværket og begrænser organisationens evne til at tilpasse sig skiftende behov. Mange Microsoft-kunder har rapporteret, at for et par år siden var 80 % af netværkstrafikken til en intern destination, men i 2020 80 % plus trafik opretter forbindelse til en ekstern skybaseret ressource.

COVID-19-krise har fået dette problem til at kræve øjeblikkelige løsninger for størstedelen af organisationer. Mange kunder har opdaget, at den tvungne VPN-model ikke er skalerbar eller performant nok til scenarier med 100 % fjernarbejde, som denne krise har udviklet. Der kræves hurtige løsninger, for at disse organisationer fortsat kan fungere effektivt.

Til Microsoft 365-tjenesten har Microsoft udviklet forbindelseskravene til tjenesten med dette problem helt for øje, hvor et fokuseret, stramt kontrolleret og relativt statisk sæt tjenesteslutpunkter kan optimeres meget enkelt og hurtigt for at levere høj ydeevne for brugere, der får adgang til tjenesten, og reducere belastningen af VPN-infrastrukturen, så den kan bruges af trafik, der stadig kræver det.

Microsoft 365 kategoriserer de nødvendige slutpunkter for Microsoft 365 i tre kategorier: **Optimer****, Tillad** og **Standard**. **Optimer** slutpunkter er vores fokus her og har følgende egenskaber:

- Ejes og administreres af Microsoft-slutpunkter, der hostes på Microsoft-infrastruktur
- Er dedikeret til centrale Microsoft 365 arbejdsbelastninger som f.eks. Exchange Online, SharePoint Online, Skype for Business Online og Microsoft Teams
- Har IP'er angivet
- Lav ændringshastighed og forventes at forblive lille i tal (i øjeblikket 20 IP-undernet)
- Er meget følsom over for lydstyrke og/eller ventetid
- Du kan have påkrævede sikkerhedselementer leveret i tjenesten i stedet for indbygget på netværket
- Tage højde for omkring 70-80 % af mængden af trafik til Microsoft 365 tjeneste

Dette tætbelagte sæt slutpunkter kan opdeles fra den tvungne VPN-forbindelse og sendes sikkert og direkte til Microsoft 365-tjenesten via brugerens lokale grænseflade. Dette kaldes **opdelte inddelning.**

Sikkerhedselementer som DLP, AV-beskyttelse, godkendelse og adgangskontrol kan alle leveres meget mere effektivt mod disse slutpunkter på forskellige lag i tjenesten. Da vi også omdirigerer massen af trafikmængde væk fra VPN-løsningen, frigøres VPN-kapaciteten for forretningskritisk trafik, der stadig er afhængig af den. Det bør også fjerne behovet i mange tilfælde for at gå gennem et længere og dyrere opgraderingsprogram for at håndtere denne nye operativsystem metode.

![Opdel Tunnel VPN-konfigurationsoplysninger.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

_Figur 3: En VPN-opdelt løsning med definerede Microsoft 365 der sendes direkte til tjenesten. Al anden trafik tvinges tilbage til virksomhedens netværk uanset destination._

Ud fra et sikkerhedsperspektiv har Microsoft en række sikkerhedsfunktioner, som kan bruges til at levere lignende eller endda udvidet sikkerhed end den, der leveres ved indbygget inspektion af lokale sikkerhedsstabler. Microsoft Security-teamets blogindlæg Alternative måder [for](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier med eksternt arbejde har en klar oversigt over tilgængelige funktioner, og du kan finde mere detaljeret vejledning i denne artikel. Du kan også læse om Microsofts implementering af VPN-opdeling af VPN-forbindelse ved at køre på [VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

I mange tilfælde kan denne implementering opnås på få timer, hvilket gør det muligt hurtigt at løse et af de mest presserende problemer, som organisationer står over for, når de hurtigt skifter til fjernarbejde i fuld skala. Du kan finde en vejledning til implementering af VPN-opdelte vpn i Implementering af [VPN-opdeling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

## <a name="faq"></a>Ofte stillede spørgsmål

Microsofts sikkerhedsteam har udgivet Alternative måder [for](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) sikkerhedsmedarbejdere og IT til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier med fjernarbejde, et blogindlæg, der beskriver de vigtigste måder for sikkerhedsmedarbejdere, og it-medarbejdere kan opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier med fjernarbejde. Nedenfor finder du desuden nogle af de mest almindelige kundespørgsmål og svar om dette emne.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Hvordan kan jeg stoppe brugeres adgang til andre lejere, jeg ikke har tillid til, hvor de kan eksfiltrere data?

Svaret er en funktion [kaldet lejerbegrænsninger](/azure/active-directory/manage-apps/tenant-restrictions). Godkendelsestrafik er ikke stor lydstyrke eller specielt ventetid følsom, så kan sendes via VPN-løsningen til den lokale proxy, hvor funktionen er anvendt. En tilladelsesliste over lejere, der er tillid til, vedligeholdes her, og hvis klienten forsøger at få et token til en lejer, der ikke er tillid til, afviser proxyen blot anmodningen. Hvis der er tillid til lejeren, er et token tilgængeligt, hvis brugeren har de rigtige legitimationsoplysninger og rettigheder.

Så selvom en bruger kan oprette en TCP/UDP-forbindelse til de optimerede slutpunkter ovenfor uden et gyldigt token for at få adgang til den pågældende lejer, kan de ganske enkelt ikke logge på og få adgang til/flytte data.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Tillader denne model adgang til forbrugertjenester som personlige konti OneDrive forbrugerkonti?

Nej, det gør den ikke, Microsoft 365-slutpunkterne er ikke det samme som forbrugertjenesterne (som et eksempel Onedrive.live.com), så det opdelte slutpunkt giver ikke en bruger direkte adgang til forbrugertjenester. Trafik til forbrugerslutpunkter vil fortsat bruge VPN-forbindelsen, og eksisterende politikker vil fortsat være gældende.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Hvordan anvender jeg DLP og beskytter mine følsomme data, når trafikken ikke længere flyder gennem min lokale løsning?

For at hjælpe dig med at forhindre utilsigtet afsløring af følsomme oplysninger har Microsoft 365 omfattende [indbyggede værktøjer](../compliance/information-protection.md). Du kan bruge de indbyggede [DLP-funktioner i Teams](../compliance/dlp-learn-about-dlp.md) og SharePoint til at registrere upassende gemte eller delte følsomme oplysninger. Hvis en del af din strategi for fjernarbejde indebærer en BYOD-politik (bring-your-own-device), kan du bruge [appbaseret betinget adgang](/azure/active-directory/conditional-access/app-based-conditional-access) til at forhindre, at følsomme data overføres til brugernes personlige enheder

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Hvordan kan jeg evaluere og bevare kontrollen over brugerens godkendelse, når de opretter direkte forbindelse?

Ud over den funktion til lejerbegrænsninger [, der](/azure/active-directory/conditional-access/overview) er angivet i Q1, kan politikker for betinget adgang anvendes til dynamisk at vurdere risikoen for en godkendelsesanmodning og reagere korrekt. Microsoft anbefaler, at [](https://www.microsoft.com/security/zero-trust?rtc=1) nultillidsmodellen implementeres over tid, og vi kan bruge politikker for betinget adgang i Azure AD til at bevare kontrollen i en mobil og skybaseret verden. Politikker for betinget adgang kan bruges til at træffe en beslutning i realtid om, hvorvidt en godkendelsesanmodning lykkes, baseret på en lang række faktorer, f.eks.:

- Enhed, er enheden kendt som en enhed, der er tillid til/domænet er forbundet?
- IP – kommer godkendelsesanmodningen fra en kendt firma-IP-adresse? Eller fra et land, vi ikke har tillid til?
- Program – Er brugeren autoriseret til at bruge dette program?

Vi kan derefter udløse politik som f.eks godkend, udløse MFA eller blokere godkendelse baseret på disse politikker.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Hvordan beskytter jeg mod virus og malware?

Igen giver Microsoft 365 beskyttelse af de optimer markerede slutpunkter i forskellige lag i selve tjenesten, som [er beskrevet i dette dokument](/office365/Enterprise/office-365-malware-and-ransomware-protection). Som nævnt er det meget mere effektivt at levere disse sikkerhedselementer i selve tjenesten i stedet for at forsøge at gøre det på linje med enheder, der muligvis ikke forstår protokollerne/trafikken fuldt ud. Som standard scanner SharePoint Online [automatisk filuploads](../security/office-365-security/virus-detection-in-spo.md) for kendt malware

For de Exchange slutpunkter, der er [anført ovenfor, gør Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) [og Microsoft Defender Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) et fremragende stykke arbejde med at sikre trafikken til tjenesten.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Kan jeg sende mere end blot direkte optimer trafik?

Der bør gives prioritet til de **optimerede** slutpunkter, da disse giver den største fordel for et lavt arbejdsniveau. Men hvis du ønsker det, er Tillad markerede slutpunkter påkrævet for, at tjenesten kan fungere, og IP-adresser er angivet for de slutpunkter, der kan bruges, hvis det er nødvendigt.

There are also various vendors who offer cloud-based proxy/security solutions called _secure web gateways_ which provide central security, control, and corporate policy application for general web browsing. Disse løsninger kan fungere godt i en skybaseret verden, hvis de er meget tilgængelige, performanter og klargjort tæt på dine brugere ved at tillade sikker internetadgang at blive leveret fra en skybaseret placering tæt på brugeren. Dette fjerner behovet for en hairpin via VPN/virksomhedens netværk for generel browsertrafik, mens du stadig tillader central sikkerhedskontrol.

Selv med disse løsninger på plads anbefaler Microsoft dog stadig, at Optimer markeret Microsoft 365-trafik sendes direkte til tjenesten.

Du kan finde en vejledning til at tillade direkte adgang til et Azure Virtual Network under [Fjernarbejde ved hjælp af Azure VPN Gateway Point-to-site](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Hvorfor kræves port 80? Er trafikken helt klar?

Port 80 bruges kun til ting som f.eks. at omdirigere til en port 443-session, ingen kundedata sendes eller er tilgængelige via port 80. [Krypteringen](../compliance/encryption.md) beskriver kryptering af data under overførsel og i hvile for Microsoft 365, og Typer af trafik [](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) beskriver, hvordan vi bruger SRTP til at beskytte Teams medietrafik.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Gælder dette råd for brugere i Kina, der bruger en verdensomspændende forekomst af Microsoft 365?

**Nej**, det gør den ikke. Den eneste advarsel er brugere i Kina, der opretter forbindelse til en verdensomspændende forekomst af Microsoft 365. På grund af den almindelige forekomst af overbelastning af netværk på tværs af grænser i området kan direkte internet udgangspunkt være variabel. De fleste kunder i området bruger et VPN til at få trafikken ind på virksomhedens netværk og bruge deres autoriserede MPLS-kredsløb eller lignende som udgangspunkter uden for landet via en optimeret sti. Dette er beskrevet nærmere i artiklen om [Microsoft 365 optimering af ydeevnen for Kinas brugere](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>Fungerer konfiguration med opdelte konfigurationer for Teams der kører i en browser?

Ja, med advarsel! De Teams funktioner understøttes i de browsere, der er angivet [i Hent klienter Microsoft Teams](/microsoftteams/get-clients#web-client).

Desuden understøtter Microsoft Edge **96** og derover VPN-opdeling af peer-to-peer-trafik ved at aktivere politikken Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled). På nuværende tidspunkt understøtter andre browsere muligvis ikke VPN-opdeling af peer-to-peer-trafik.

## <a name="related-articles"></a>Relaterede artikler

[Implementering af VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier for opdeling af VPN-Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sikring Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimering af ydeevnen for Kinas brugere](microsoft-365-networking-china.md)

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier for fjernarbejde (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: brug Windows 10 VPN-profiler til at tillade automatiske til-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
