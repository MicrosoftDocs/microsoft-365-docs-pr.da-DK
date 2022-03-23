---
title: Implementering af VPN-opdeling af Microsoft 365
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
description: Sådan implementerer du VPN-opdeling af Microsoft 365
ms.openlocfilehash: ee8c0929682370d581c9d1b5c738d682d3f91a01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594288"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implementering af VPN-opdeling af Microsoft 365

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Du kan få et overblik over, hvordan du bruger VPN-opdelte forbindelser til at optimere Microsoft 365 forbindelse for eksterne brugere, under [Oversigt: VPN-opdelt Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdeling af VPN i Almindelige [scenarier for vpnopdelning af Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde en vejledning til sikring Teams medietrafik i VPN-opdelte netværksmiljøer under Sikring [Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md).
>- Du kan finde oplysninger om, hvordan du konfigurerer Stream og livebegivenheder i VPN-miljøer, under Særlige overvejelser [i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan finde oplysninger om optimering Microsoft 365 globale lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for Brugere i Kina](microsoft-365-networking-china.md).

Microsofts anbefalede strategi til optimering af fjernmedarbejderens forbindelse er fokuseret på hurtigt at mindske problemer og levere høj ydeevne med et par enkle trin. Disse trin justerer den ældre VPN-tilgang for et par definerede slutpunkter, der tilsidesætter flaskehalse-VPN-servere. En tilsvarende eller endda overordnede sikkerhedsmodel kan anvendes i forskellige lag for at fjerne behovet for at sikre al trafik på udgangspunktet for virksomhedens netværk. I de fleste tilfælde kan dette opnås effektivt inden for timer og kan derefter skaleres til andre arbejdsbelastninger, som krav, behov og tid tillader.

## <a name="implement-vpn-split-tunneling"></a>Implementer VPN-opdelingsopdelning

I denne artikel finder du de enkle trin, der kræves for at overføre din VPN-klientarkitektur fra en VPN-gennemtvungen _overførsel_ til en VPN-gennemtvunget forbindelse med et par pålidelige undtagelser, [VPN opdelte arkitekturmodel #2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) i Almindelige VPN-opdelte scenarier [for Microsoft 365](microsoft-365-vpn-common-scenarios.md).

Nedenstående diagram illustrerer, hvordan den anbefalede løsning til opdeling af VPN-løsning til VPN fungerer:

![Opdel detaljer om VPN-løsning i forskellige vpn.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identificer de slutpunkter, der skal optimeres

I artiklen [Microsoft 365 URL-adresser](urls-and-ip-address-ranges.md) og IP-adresseintervaller identificerer Microsoft tydeligt de vigtigste slutpunkter, du skal bruge til at optimere og kategorisere dem som **Optimer**. Der er i øjeblikket kun fire URL-adresser og 20 IP-undernet, der skal optimeres. Denne lille gruppe slutpunkter udgør omkring 70 % - 80 % af trafik til Microsoft 365-tjenesten, herunder følsomme slutpunkter for ventetiden, f.eks. for Teams medier. Dybest set er det den trafik, vi er nødt til at tage særlig hånd om, og det er også den trafik, der vil lægge utroligt tryk på traditionelle netværksstier og VPN-infrastruktur.

URL-adresser i denne kategori har følgende egenskaber:

- Ejes og administreres af Microsoft-slutpunkter, der hostes på Microsoft-infrastruktur
- Har IP'er angivet
- Lav ændringshastighed og forventes at forblive lille i tal (i øjeblikket 20 IP-undernet)
- Er båndbredde- og/eller ventetidsfølsom
- Du kan have påkrævede sikkerhedselementer leveret i tjenesten i stedet for indbygget på netværket
- Tage højde for omkring 70-80 % af mængden af trafik til Microsoft 365 tjeneste

Du kan finde flere Microsoft 365 om slutpunkter, og hvordan de [kategoriseres og administreres, under administrere Microsoft 365 slutpunkter](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optimer URL-adresser

De aktuelle URL-adresser til optimer kan findes i tabellen nedenfor. Under de fleste omstændigheder skal du kun bruge URL-slutpunkter i en [PAC-fil i browseren](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) , hvor slutpunkterne er konfigureret til at blive sendt direkte i stedet for til proxyen.

| Optimer URL-adresser | Port/protokol | Formål |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Dette er en af de primære URL-adresser, Outlook bruger til at oprette forbindelse til dens Exchange Online-server og har en stor mængde båndbreddeforbrug og antal forbindelser. Lav netværksventetid er påkrævet for onlinefunktioner, herunder: hurtigsøgning, andre postkassekalendere, opslag med ledig/optaget tid, administrer regler og beskeder, Exchange onlinearkiv, mails, der forlader udbakken. |
| <https://outlook.office.com> | TCP 443 | Denne URL-adresse bruges til Outlook Online Web Access til at oprette forbindelse Exchange Online serveren og er følsom over for netværksventetid. Forbindelse er især påkrævet til overførsel og download af store filer med SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Dette er den primære URL-adresse til SharePoint Online og har stor brug af båndbredde. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Dette er den primære URL-adresse til OneDrive for Business og har høj båndbreddeforbrug og muligvis højt forbindelsesantal fra OneDrive for Business synkroniseringsværktøjet. |
| Teams Medie-IP'er (ingen URL-adresse) | UDP 3478, 3479, 3480 og 3481 | Relay Discovery-tildeling og trafik i realtid. Disse slutpunkter bruges til at Skype for Business og Microsoft Teams medietrafik (opkald, møder osv.). De fleste slutpunkter angives, når Microsoft Teams-klienten etablerer et opkald (og er indeholdt i de nødvendige IP'er, der er angivet for tjenesten). Brug af UDP-protokollen er påkrævet for at opnå optimal mediekvalitet.   |

I eksemplerne ovenfor skal **lejer erstattes** med dit Microsoft 365 lejernavn. For eksempel **contoso.onmicrosoft.com** bruge _contoso.sharepoint.com_ og _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optimer IP-adresseintervaller

Når du skriver IP-adresseintervaller, svarer disse slutpunkter til, som følger: Det anbefales på  det kraftigste, at du bruger et [script](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) som f.eks. dette eksempel[, Microsoft 365-webtjenesten IP og URL-adressen](microsoft-365-ip-web-service.md) eller [URL/IP-siden](urls-and-ip-address-ranges.md) til at søge efter opdateringer, når du anvender konfigurationen, og lægge en politik på plads for at gøre dette regelmæssigt.

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

Nu, hvor vi har identificeret disse kritiske slutpunkter, skal vi omdirigere dem væk fra VPN-transportpunktet og give dem mulighed for at bruge brugerens lokale internetforbindelse til at oprette direkte forbindelse til tjenesten. Den måde, hvorpå dette opnås, varierer afhængigt af det VPN-produkt og den maskinplatform, der bruges, men de fleste VPN-løsninger tillader en simpel konfiguration af politikken for at anvende denne logik. Du kan finde oplysninger om VPN-platformsspecifik vejledning til opdelte vpn under [HOWTO-vejledninger til almindelige VPN-platforme](#howto-guides-for-common-vpn-platforms).

Hvis du vil teste løsningen manuelt, kan du udføre følgende PowerShell-eksempel for at efterligne løsningen på rutetabelniveau. I dette eksempel tilføjes en rute for hvert Teams MEDIA IP-undernet i rutetabellen. Du kan teste Teams og medieydeevne før og efter og se forskellen på ruterne for de angivne slutpunkter.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Eksempel: Føj Teams IP-undernet til rutetabellen

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

I scriptet ovenfor er _$intIndex_ indekset for grænsefladen, der har forbindelse til internettet (find ved at køre **get-netadapter** i PowerShell; se efter værdien af _ifIndex_), og _$gateway_ er standardgatewayen for den pågældende grænseflade (find ved at køre **ipconfig** i en kommandoprompt eller **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** i PowerShell).

Når du har tilføjet ruterne, kan du bekræfte, at rutetabellen er korrekt, ved  at køre ruteudskriften i en kommandoprompt eller PowerShell. Outputtet skal indeholde de ruter, du har tilføjet, som viser grænsefladeindekset (_22_ i dette eksempel) og gatewayen for den pågældende grænseflade (_192.168.1.1_ i dette eksempel):

![Distribuere udskrift.](../media/vpn-split-tunneling/vpn-route-print.png)

Hvis du vil tilføje _ruter for alle_ aktuelle IP-adresseintervaller i kategorien Optimer, kan du bruge følgende scriptvariation til at forespørge [Microsoft 365-webtjenesten IP og URL-webtjenesten](microsoft-365-ip-web-service.md) for det aktuelle sæt af Optimer IP-undernet og føje dem til rutetabellen.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Eksempel: Føj alle Optimer undernet til rutetabellen

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

Hvis du utilsigtet kommer til at tilføje ruter med forkerte parametre eller blot ønsker at gendanne dine ændringer, kan du fjerne de ruter, du lige har tilføjet, med følgende kommando:

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

VPN-klienten skal konfigureres, så trafik **til optimer** IP'er dirigeres på denne måde. Dette gør det muligt for trafikken at bruge lokale Microsoft-ressourcer, f.eks. Microsoft 365 Service Front Doors, som f.eks[. Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/), der leverer Microsoft 365-tjenester og forbindelsesslutpunkter så tæt på dine brugere som muligt. Dette giver os mulighed for at levere høje ydeevneniveauer til brugere, uanset hvor de befinder sig i verden, og drage fuld fordel af [Microsofts](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) globale netværk i verdensklasse, som sandsynligvis er inden for et par millisekunder med dine brugeres direkte udgangspunkt.

## <a name="howto-guides-for-common-vpn-platforms"></a>HOWTO-vejledninger til almindelige VPN-platforme

Dette afsnit indeholder links til detaljerede vejledninger til implementering af opdelte Microsoft 365 til netværkstrafik fra de mest almindelige partnere i dette område. Vi tilføjer yderligere vejledninger, efterhånden som de bliver tilgængelige.

- **Windows 10 VPN-klient**: [Optimering Microsoft 365 trafik for eksterne medarbejdere med den Windows 10 VPN-klient](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [Optimer split-Tunnel forbindelse til Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [Optimering Microsoft 365 af trafik via VPN opdelt Tunnel ekskluder adgangsrute](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: Optimering Microsoft 365 trafik på fjernadgang via VPN, når du bruger [BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix-gateway**: [Optimering af Citrix Gateway VPN-opdelt gateway til Office365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN-opføring: Sådan konfigurerer du opdeling af inddelning for at Microsoft 365 programmer](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check point VPN**: [Sådan konfigurerer du Split Tunnel til Microsoft 365 og andre SaaS-programmer](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdeling af Microsoft 365](microsoft-365-vpn-split-tunnel.md)

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
