---
title: Implementering af OPDELT VPN-tunnelføring til Microsoft 365
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
f1.keywords:
- NOCSH
description: Sådan implementerer du opdelt VPN-tunnelføring til Microsoft 365
ms.openlocfilehash: 6b578b9b1801921644c6982c15c160bce5fbb4dd
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941080"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implementering af OPDELT VPN-tunnelføring til Microsoft 365

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der omhandler Microsoft 365-optimering for fjernbrugere.

>- Du kan se en oversigt over, hvordan du bruger OPDELT VPN-tunnelføring til at optimere Microsoft 365-forbindelse til fjernbrugere, under [Oversigt: VPN-opdelt tunnelføring til Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdelt VPN-tunnelføring under [Almindelige scenarier med opdelt VPN-tunnelføring til Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde vejledning i beskyttelse af Teams-medietrafik i VPN-opdelte tunnelføringsmiljøer under [Sikring af Teams-medietrafik til VPN-opdelt tunnelføring](microsoft-365-vpn-securing-teams.md).
>- Du kan få mere at vide om, hvordan du konfigurerer Stream- og livebegivenheder i VPN-miljøer, under [Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan få oplysninger om optimering af lejerydeevnen i Microsoft 365 over hele verden for brugere i Kina under [Optimering af ydeevnen i Microsoft 365 for brugere i Kina](microsoft-365-networking-china.md).

Microsofts anbefalede strategi for optimering af fjernarbejderens forbindelse fokuserer på hurtigt at afhjælpe problemer og give høj ydeevne med nogle få enkle trin. Disse trin justerer den ældre VPN-tilgang til nogle få definerede slutpunkter, der tilsidesætter flaskehalse for VPN-servere. En tilsvarende eller endda bedre sikkerhedsmodel kan anvendes på forskellige lag for at fjerne behovet for at sikre al trafik ved virksomhedens netværks udgang. I de fleste tilfælde kan dette opnås effektivt inden for få timer og kan derefter skaleres til andre arbejdsbelastninger, efterhånden som kravene til efterspørgsel og tid tillader det.

## <a name="implement-vpn-split-tunneling"></a>Implementer OPDELT VPN-tunnelføring

I denne artikel finder du de enkle trin, der kræves for at overføre din VPN-klientarkitektur fra en _VPN-tvungen tunnel_ til en _VPN-gennemtvunget tunnel med nogle få undtagelser_, [vpn-opdelt tunnelmodel #2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) i [Common VPN-opdelt tunnelføringsscenarier for Microsoft 365](microsoft-365-vpn-common-scenarios.md).

I nedenstående diagram illustreres det, hvordan den anbefalede vpn-opdelte tunnelløsning fungerer:

![Detaljer om VPN-løsning i opdelt tunnel.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identificer de slutpunkter, der skal optimeres

I artiklen [URL-adresser og IP-adresseområder i Microsoft 365 identificerer](urls-and-ip-address-ranges.md) Microsoft tydeligt de vigtige slutpunkter, du skal bruge for at optimere og kategorisere dem som **Optimer**. Der er i øjeblikket kun fire URL-adresser og 20 IP-undernet, der skal optimeres. Denne lille gruppe slutpunkter tegner sig for ca. 70 - 80 % af trafikmængden til Microsoft 365-tjenesten, herunder ventetidsfølsomme slutpunkter, f.eks. for Teams-medier. I bund og grund er dette den trafik, som vi skal tage særligt hensyn til, og er også den trafik, der vil lægge utrolig pres på traditionelle netværksstier og VPN-infrastruktur.

URL-adresser i denne kategori har følgende egenskaber:

- Ejes og administreres Microsoft-slutpunkter, der hostes på Microsofts infrastruktur
- Har IP-adresserne angivet
- Lav ændringsrate og forventes at forblive et lille antal (i øjeblikket 20 IP-undernet)
- Er båndbredde og/eller ventetid følsomme
- Kan have påkrævede sikkerhedselementer, der leveres i tjenesten i stedet for indbygget på netværket
- Tegner sig for ca. 70-80 % af trafikmængden til Microsoft 365-tjenesten

Du kan finde flere oplysninger om Microsoft 365-slutpunkter, og hvordan de er kategoriseret og administreret, under [Administration af Microsoft 365-slutpunkter](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optimer URL-adresser

Du kan finde de aktuelle Optimer URL-adresser i tabellen nedenfor. Under de fleste omstændigheder skal du kun bruge URL-slutpunkter i en [browser-PAC-fil](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) , hvor slutpunkterne er konfigureret til at blive sendt direkte i stedet for til proxyen.

| Optimer URL-adresser | Port/protokol | Formål |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Dette er en af de primære URL-adresser, som Outlook bruger til at oprette forbindelse til Exchange Online-serveren og har en høj mængde båndbreddeforbrug og forbindelsesantal. Lav netværksventetid er påkrævet for onlinefunktioner, herunder: hurtigsøgning, andre postkassekalendere, gratis/optaget opslag, administrer regler og beskeder, Exchange-onlinearkiv, mails, der forlader udbakken. |
| <https://outlook.office.com> | TCP 443 | Denne URL-adresse bruges til Outlook Online Web Access til at oprette forbindelse til Exchange Online-serveren og er følsom over for netværksventetid. Der kræves især forbindelse til upload og download af store filer med SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Dette er den primære URL-adresse til SharePoint Online og har brug for høj båndbredde. |
| \<tenant\>https:// my.sharepoint.com | TCP 443 | Dette er den primære URL-adresse til OneDrive for Business og har et højt båndbreddeforbrug og muligvis et højt forbindelsesantal fra OneDrive for Business-synkroniseringsværktøjet. |
| Teams-medie-IP'er (ingen URL-adresse) | UDP 3478, 3479, 3480 og 3481 | Relæregistreringsallokering og trafik i realtid. Dette er de slutpunkter, der bruges til Skype for Business- og Microsoft Teams Media-trafik (opkald, møder osv.). De fleste slutpunkter leveres, når Microsoft Teams-klienten opretter et opkald (og er indeholdt i de påkrævede IP-adresser, der er angivet for tjenesten). Brug af UDP-protokollen er påkrævet for at opnå optimal mediekvalitet.   |

I ovenstående eksempler skal **lejeren** erstattes med dit Microsoft 365-lejernavn. **Contoso.onmicrosoft.com** vil f.eks. bruge _contoso.sharepoint.com_ og _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optimer IP-adresseområder

På tidspunktet for skrivning er de IP-adresseområder, som disse slutpunkter svarer til, som følger. Det anbefales **på det kraftigste** , at du bruger et [script som f.eks](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) . [Microsoft 365 IP- og URL-webtjenesten](microsoft-365-ip-web-service.md) eller [URL-siden](urls-and-ip-address-ranges.md) til at kontrollere, om der er opdateringer, når du anvender konfigurationen, og placerer en politik for at gøre det regelmæssigt.

```markdown
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. Optimer adgangen til disse slutpunkter via VPN

Nu, hvor vi har identificeret disse kritiske slutpunkter, er vi nødt til at aflede dem væk fra VPN-tunnellen og give dem mulighed for at bruge brugerens lokale internetforbindelse til at oprette direkte forbindelse til tjenesten. Den måde, hvorpå dette opnås, varierer afhængigt af det anvendte VPN-produkt og den anvendte computerplatform, men de fleste VPN-løsninger gør det muligt for en simpel konfiguration af politikken at anvende denne logik. Du kan finde oplysninger om VPN-platformspecifikke vejledninger til opdelt tunnel under [HOWTO-vejledninger til almindelige VPN-platforme](#howto-guides-for-common-vpn-platforms).

Hvis du vil teste løsningen manuelt, kan du udføre følgende PowerShell-eksempel for at emulere løsningen på rutetabelniveau. I dette eksempel føjes der en rute for hvert Af Teams Media IP-undernet til rutetabellen. Du kan teste Teams-medieydeevnen før og efter og se forskellen i ruter for de angivne slutpunkter.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Eksempel: Føj Teams Media IP-undernet til rutetabellen

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

I ovenstående script er _$intIndex_ indekset for den grænseflade, der er forbundet til internettet (find ved at køre **get-netadapter** i PowerShell. Se efter værdien af _ifIndex_), og _$gateway_ er standardgatewayen for den pågældende grænseflade (find ved at køre **ipconfig** i en kommandoprompt eller **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** i PowerShell).

Når du har tilføjet ruterne, kan du bekræfte, at rutetabellen er korrekt, ved at køre **ruteudskrift** i en kommandoprompt eller PowerShell. Outputtet skal indeholde de ruter, du har tilføjet, og som viser grænsefladeindekset (_22_ i dette eksempel) og gatewayen for den pågældende grænseflade (_192.168.1.1_ i dette eksempel):

![Distribuer udskriftsoutput.](../media/vpn-split-tunneling/vpn-route-print.png)

Hvis du vil tilføje ruter for _alle_ aktuelle IP-adresseområder i kategorien Optimer, kan du bruge følgende scriptvariation til at forespørge [Microsoft 365 IP- og URL-webtjenesten](microsoft-365-ip-web-service.md) om det aktuelle sæt optimer IP-undernet og føje dem til rutetabellen.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Eksempel: Føj alle optimer undernet til rutetabellen

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Hvis du utilsigtet har tilføjet ruter med forkerte parametre eller blot ønsker at gendanne dine ændringer, kan du fjerne de ruter, du lige har tilføjet, med følgende kommando:

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

VPN-klienten skal konfigureres, så trafikken til **Optimer** IP-adresser dirigeres på denne måde. Dette gør det muligt for trafikken at anvende lokale Microsoft-ressourcer, f.eks. Microsoft 365 Service Front Doors [, f.eks. Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) , der leverer Microsoft 365-tjenester og forbindelsesslutpunkter så tæt på dine brugere som muligt. Dette giver os mulighed for at levere høje ydeevneniveauer til brugere, uanset hvor i verden de er, og drager fuld fordel af [Microsofts globale netværk i verdensklasse](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), hvilket sandsynligvis ligger inden for nogle få millisekunder af dine brugeres direkte udgående data.

## <a name="howto-guides-for-common-vpn-platforms"></a>HOWTO-vejledninger til almindelige VPN-platforme

Dette afsnit indeholder links til detaljerede vejledninger til implementering af opdelt tunnelføring til Microsoft 365-trafik fra de mest almindelige partnere på dette område. Vi tilføjer yderligere vejledninger, efterhånden som de bliver tilgængelige.

- **Windows 10 VPN-klient**: [Optimering af Microsoft 365-trafik for fjernarbejdere med den oprindelige Windows 10 VPN-klient](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Optimer Anyconnect Split Tunnel til Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [Optimering af Microsoft 365-trafik via VPN Split Tunnel Exclude Access Route](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [Optimering af Microsoft 365-trafik på Fjernadgang via VPN'er, når BIG-IP APM bruges](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix Gateway**: [Optimering af Citrix Gateway VPN-opdelt tunnel til Office365](https://docs.citrix.com/en-us/citrix-gateway/current-release/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN-tunnelføring: Sådan konfigurerer du opdelt tunnelføring for at udelukke Microsoft 365-programmer](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check Point VPN**: [Sådan konfigurerer du Split Tunnel til Microsoft 365 og andre SaaS-programmer](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdelt tunnelføring til Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Almindelige scenarier med opdelt VPN-tunnelføring til Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sikring af Teams-medietrafik til VPN-opdelt tunnelføring](microsoft-365-vpn-securing-teams.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Optimering af ydeevnen i Microsoft 365 for kinabrugere](microsoft-365-networking-china.md)

[Principper for Microsoft 365 Network Connectivity](microsoft-365-network-connectivity-principles.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Microsoft 365-netværk og justering af ydeevne](network-planning-and-performance.md)

[Alternative måder for sikkerhedsteknikere og it-medarbejdere at opnå moderne sikkerhedskontroller i nutidens unikke fjernarbejdsscenarier (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: Brug af Windows 10 VPN-profiler til at tillade automatisk on-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke tilsluttet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
