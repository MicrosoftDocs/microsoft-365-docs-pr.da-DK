---
title: Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'Oversigt: Få mere at vide om, hvordan du konfigurerer et virtuelt Azure-netværk på tværs af Office for en serverbelastning med en WEBSTED-til-websted-VPN-forbindelse.'
ms.openlocfilehash: 5ba05dd432a6f6fe323e9d9cfd2542dcb1cc7efb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590612"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk

Et virtuelt Azure-netværk på tværs af det lokale netværk er forbundet til dit lokale netværk og udvider dit netværk til at omfatte undernet og virtuelle maskiner, der er hostet i Azure-infrastrukturtjenester. Med denne forbindelse kan computere på dit lokale netværk få direkte adgang til virtuelle computere i Azure og omvendt. 

En katalogsynkroniseringsserver, der kører på en virtuel Azure-computer, skal f.eks. forespørge på dine lokale domænecontrollere efter ændringer af konti og synkronisere disse ændringer med dit Microsoft 365-abonnement. Denne artikel viser, hvordan du konfigurerer et virtuelt Azure-netværk på tværs af det lokale miljø ved hjælp af en vpn-forbindelse (virtuelt privat netværk på websted), der er klar til at hoste virtuelle Azure-computere.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Konfigurere et virtuelt Azure-netværk på tværs af et miljø

Dine virtuelle maskiner i Azure behøver ikke at være isolerede fra dit lokale miljø. Hvis du vil forbinde virtuelle Azure-maskiner til dine lokale netværksressourcer, skal du konfigurere et virtuelt Azure-netværk på tværs af det lokale miljø. I nedenstående diagram vises de komponenter, der er nødvendige for at installere et virtuelt Azure-netværk på tværs af det lokale miljø med en virtuel maskine i Azure.
  
![Lokalt netværk, der er forbundet Microsoft Azure af en WEBSTED-til-websted-VPN-forbindelse.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
I diagrammet er der to netværk, der er forbundet via en websted til websted-VPN-forbindelse: det lokale netværk og det virtuelle Azure-netværk. Site-to-site VPN-forbindelsen er:

- Mellem to slutpunkter, der kan adresseres og findes på det offentlige internet.
- Afsluttet af en VPN-enhed på det lokale netværk og en Azure VPN-gateway på det virtuelle Azure-netværk.

Azure Virtual Network hoster virtuelle computere. Netværkstrafik, der kommer fra virtuelle maskiner på det virtuelle Azure-netværk, videresendes til VPN-gatewayen, som derefter videresender trafikken på tværs af websted-til-websted-VPN-forbindelsen til VPN-enheden på det lokale netværk. Routinginfrastrukturen for det lokale netværk videresender derefter trafikken til destinationen.

>[!Note]
>Du kan også bruge [ExpressRoute](https://azure.microsoft.com/services/expressroute/), som er en direkte forbindelse mellem din organisation og Microsofts netværk. Trafik over ExpressRoute rejser ikke via det offentlige internet. I denne artikel beskrives brugen af ExpressRoute ikke.
>
  
Hvis du vil konfigurere VPN-forbindelsen mellem dit virtuelle Azure-netværk og dit lokale netværk, skal du følge disse trin: 
  
1. **Lokalt miljø:** Definer og opret en lokal netværksrute for adresserummet for det virtuelle Azure-netværk, der peger på din lokale VPN-enhed.
    
2. **Microsoft Azure:** Opret et virtuelt Azure-netværk med en WEBSTED-til-websted-VPN-forbindelse. 
    
3. **I det lokale miljø:** Konfigurer din lokale hardware- eller software-VPN-enhed for at afbryde VPN-forbindelsen, som bruger IP-sikkerhed (IPsec).
    
Når du har etableret VPN-forbindelsen mellem websted og websted, føjer du virtuelle Azure-computere til undernet af det virtuelle netværk.
  
## <a name="plan-your-azure-virtual-network"></a>Planlæg dit virtuelle Azure-netværk
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Forudsætninger
<a name="Prerequisites"></a>

- Et Azure-abonnement. Du kan finde oplysninger om Azure-abonnementer på [siden Sådan køber du Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- Et tilgængeligt privat IPv4-adresseområde, der kan tildeles det virtuelle netværk og dets undernet, med tilstrækkelig plads til vækst til at rumme det antal virtuelle maskiner, der skal bruges nu og i fremtiden.
    
- En tilgængelig VPN-enhed i dit lokale netværk til at afbryde VPN-forbindelsen fra websted til websted, der understøtter kravene til IPsec. Du kan finde flere oplysninger [i Om VPN-enheder til virtuelle netværksforbindelser mellem websteder](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- Ændringer i din routinginfrastruktur, så trafik, der dirigeres til adresseområdet for det virtuelle Azure-netværk, videresendes til den VPN-enhed, der hoster WEBSTED-til-websted-VPN-forbindelsen.
    
- En webproxy, der giver computere, der har forbindelse til det lokale netværk, og det virtuelle Azure-netværk adgang til internettet.
    
### <a name="solution-architecture-design-assumptions"></a>Forudsætninger for løsningsarkitekturdesign

Følgende liste repræsenterer de designvalg, der er foretaget for denne løsningsarkitektur. 
  
- Denne løsning bruger et enkelt virtuelt Azure-netværk med en websted-til-websted-VPN-forbindelse. Azure Virtual Network hoster et enkelt undernet, der kan indeholde flere virtuelle maskiner. 
    
- Du kan bruge RRAS (Routing and Remote Access Service) i Windows Server 2016 eller Windows Server 2012 til at etablere en IPsec-WEBSTED-VPN-forbindelse mellem det lokale netværk og det virtuelle Azure-netværk. Du kan også bruge andre indstillinger, f.eks Cisco- eller Juniper Networks VPN-enheder.
    
- Det lokale netværk kan stadig have netværkstjenester som f.eks. Active Directory-domæneservices (AD DS), DNS (Domain Name System) og proxyservere. Afhængigt af dine krav kan det være nyttigt at placere nogle af disse netværksressourcer i det virtuelle Azure-netværk.
    
I forbindelse med et eksisterende virtuelt Azure-netværk med et eller flere undernet skal du afgøre, om der er resterende adresseplads til et ekstra undernet, der skal være vært for dine virtuelle maskiner, baseret på dine krav. Hvis du ikke har resterende adresseplads til et ekstra undernet, skal du oprette et ekstra virtuelt netværk, der har sin egen websted-til-websted-VPN-forbindelse.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Planlæg ændringer i routinginfrastrukturen for det virtuelle Azure-netværk

Du skal konfigurere din lokale routinginfrastruktur for at videresende trafik, der er beregnet til adresseområdet for det virtuelle Azure-netværk, til den lokale VPN-enhed, der er vært for VPN-forbindelsen mellem websted og websted.
  
Den nøjagtige metode til opdatering af din routinginfrastruktur afhænger af, hvordan du administrerer routingoplysninger, som kan være:
  
- Routing af tabelopdateringer baseret på manuel konfiguration.
    
- Routing af tabelopdateringer baseret på routingprotokoller, f.eks. ROUTING Information Protocol (RIP) eller Open Shortest Path First (OSPF).
    
Kontakt din routingspecialist for at sikre, at trafik, der er bestemt for det virtuelle Azure-netværk, videresendes til den lokale VPN-enhed.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Planlæg firewallregler for trafik til og fra den lokale VPN-enhed

Hvis din VPN-enhed er på et perimeternetværk, der har en firewall mellem perimeternetværket og internettet, skal du muligvis konfigurere firewallen for følgende regler for at tillade VPN-forbindelse mellem websted og websted.
  
- Trafik til VPN-enheden (indgående fra internettet):
    
  - DESTINATION IP-adresse for VPN-enheden og IP-protokollen 50
    
  - Destinationens IP-adresse for VPN-enheden og UDP-destinationsport 500
    
  - Destinationens IP-adresse på VPN-enheden og UDP-destinationsport 4500
    
- Trafik fra VPN-enheden (udgående til internettet):
    
  - IP-kildeadresse på VPN-enheden og IP-protokollen 50
    
  - IP-kildeadresse på VPN-enheden og UDP-kildeport 500
    
  - IP-kildeadresse på VPN-enheden og UDP-kildeport 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Planlæg den private IP-adresseplads i det virtuelle Azure-netværk

Det private IP-adresseområde i det virtuelle Azure-netværk skal kunne rumme adresser, der bruges af Azure til at hoste det virtuelle netværk, og med mindst ét undernet, der har nok adresser til dine virtuelle Azure-computere.
  
For at bestemme antallet af adresser, der skal bruges til undernettet, skal du tælle antallet af virtuelle maskiner, du skal bruge nu, anslå fremtidig vækst og derefter bruge følgende tabel til at bestemme størrelsen på undernettet.
  
|**Antal virtuelle maskiner er nødvendige**|**Antal værtsbit, der skal bruges**|**Undernettets størrelse**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Planlægningsregneark til konfiguration af dit virtuelle Azure-netværk
<a name="worksheet"> </a>

Før du opretter et virtuelt Azure-netværk til at hoste virtuelle computere, skal du bestemme de nødvendige indstillinger i følgende tabeller.
  
Udfyld Tabel V for at se indstillingerne for det virtuelle netværk.
  
 **Tabel V: Konfiguration af virtuelt netværk på tværs af lokale netværk**
  
|**Element**|**Konfigurationselement**|**Beskrivelse**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Navn på virtuelt netværk  <br/> |Et navn, der skal tildeles det virtuelle Azure-netværk (f.eks. DirSyncNet).  <br/> |![.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Placering af virtuelt netværk  <br/> |Azure-datacenteret, der skal indeholde det virtuelle netværk (f.eks. Vest US).  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |IP-adresse på VPN-enhed  <br/> |Den offentlige IPv4-adresse for din VPN-enheds grænseflade på internettet. Arbejd sammen med din it-afdeling for at finde denne adresse.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Virtuelt netværksadresseområde  <br/> |Adresserummet (defineret i et enkelt privat adressepræfiks) for det virtuelle netværk. Arbejd sammen med din it-afdeling for at finde dette adresseområde. Adresserummet skal være i CIDR-format (Classless Interdomain Routing), også kaldet et format med et netværkspræfiks. Et eksempel er 10.24.64.0/20.  <br/> |![.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |Delt IPsec-nøgle  <br/> |En vilkårlig, alfanumerisk streng på 32 tegn, der skal bruges til at godkende begge sider af VPN-forbindelsen mellem websted og websted. Arbejd sammen med din it- eller sikkerhedsafdeling om at finde denne nøgleværdi og derefter gemme den et sikkert sted. Du kan også se [Opret en tilfældig streng for en IPsec-foruddelt nøgle](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![.](../media/Common-Images/TableLine.png) <br/> |
   
Udfyld Tabel S for denne løsnings undernet.
  
- For det første undernet skal du bestemme et 28-bit adresseområde (med en længde på /28 præfiks) for Azure gateway-undernettet. Se [Beregne gatewayens undernetadresseplads til virtuelle Azure-netværk for](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) at få oplysninger om, hvordan du bestemmer dette adresseområde.
    
- For det andet undernet skal du angive et brugervenligt navn, et enkelt IP-adresseområde, der er baseret på det virtuelle netværks adresseområde, og et beskrivende formål.
    
Arbejd sammen med din it-afdeling for at bestemme disse adresseområder fra det virtuelle netværks adresseområde. Begge adresseområder skal være i CIDR-format.
  
 **Tabel S: Undernet i det virtuelle netværk**
  
|**Element**|**Navn på undernet**|**Undernetadresseområde**|**Formål**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af Azure-gatewayen.  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
For de lokale DNS-servere, som du vil have de virtuelle maskiner i det virtuelle netværk til at bruge, skal du udfylde Tabel D. Giv hver DNS-server et brugervenligt navn og en enkelt IP-adresse. Dette brugervenlige navn behøver ikke at svare til værtsnavnet eller computernavnet på DNS-serveren. Bemærk, at der vises to tomme poster, men du kan tilføje flere. Arbejd sammen med din it-afdeling for at finde denne liste.
  
 **Tabel D: Lokale DNS-servere**
  
|**Element**|**Navn på dns-servervenligt**|**IP-adresse til DNS-server**|
|:-----|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
Hvis du vil distribuere pakker fra det virtuelle Azure-netværk til organisationens netværk på tværs af WEBSTED-VPN-forbindelsen, skal du konfigurere det virtuelle netværk med et lokalt netværk. Dette lokale netværk har en liste over adresseområder (i CIDR-format) for alle de placeringer på organisationens lokale netværk, som de virtuelle maskiner i det virtuelle netværk skal oprette forbindelse til. Dette kan være alle placeringer på det lokale netværk eller et undersæt. Listen over adresseområder, der definerer dit lokale netværk, skal være entydig og må ikke overlappe med de adresseområder, der bruges til dette virtuelle netværk eller dine andre virtuelle netværk i det lokale miljø.
  
Udfyld Tabel L for sættet af adresseområder i lokalnetværket. Bemærk, at tre tomme poster er angivet, men du har typisk brug for flere. Arbejd sammen med din it-afdeling for at finde denne liste.
  
 **Tabel L: Adressepræfikser for det lokale netværk**
  
|**Element**|**Lokal netværksadresseområde**|
|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![linje](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Installationsoversigt
<a name="DeploymentRoadmap"> </a>

Oprettelse af det virtuelle netværk på tværs af lokale netværk og tilføjelse af virtuelle maskiner i Azure består af tre faser:
  
- Fase 1: Forbered dit lokale netværk.
    
- Fase 2: Opret det virtuelle netværk på tværs af det lokale miljø i Azure.
    
- Fase 3 (Valgfrit): Tilføj virtuelle computere.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Fase 1: Forbered dit lokale netværk
<a name="Phase1"></a>

Du skal konfigurere dit lokale netværk med en rute, der peger på og i sidste ende leverer trafik, der er beregnet til det virtuelle netværks adresseområde til routeren på kanten af det lokale netværk. Kontakt din netværksadministrator for at finde ud af, hvordan du føjer routingen til routinginfrastrukturen for dit lokale netværk.
  
Her er din resulterende konfiguration.
  
![Det lokale netværk skal have en rute til det virtuelle netværks adresseområde, der peger mod VPN-enheden.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Fase 2: Opret det virtuelle netværk på tværs af det lokale miljø i Azure
<a name="Phase2"></a>

Først skal du åbne Azure PowerShell meddelelse. Hvis du ikke har installeret Azure PowerShell, skal du [se Introduktion til Azure PowerShell](/powershell/azure/get-started-azureps).

 
Derefter skal du logge på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Få dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Angiv dit Azure-abonnement med disse kommandoer. Erstat alt mellem anførselstegnene, herunder < og >, med det korrekte abonnementsnavn.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Dernæst skal du oprette en ny ressourcegruppe for dit virtuelle netværk. Hvis du vil finde et entydigt ressourcegruppenavn, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Opret din nye ressourcegruppe med disse kommandoer.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Derefter skal du oprette det virtuelle Azure-netværk.
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Her er din resulterende konfiguration.
  
![Det virtuelle netværk har endnu ikke forbindelse til det lokale netværk.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Derefter skal du bruge disse kommandoer til at oprette gateways for VPN-forbindelsen mellem websted og websted.
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Her er din resulterende konfiguration.
  
![Det virtuelle netværk har nu en gateway.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Dernæst skal du konfigurere din lokale VPN-enhed til at oprette forbindelse til Azure VPN-gatewayen. Du kan finde flere oplysninger [i Om VPN-enheder til websted-til-websted Azure Virtual Network-forbindelser](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
For at konfigurere din VPN-enhed skal du bruge følgende:
  
- Den offentlige IPv4-adresse for Azure VPN-gatewayen for dit virtuelle netværk. Brug kommandoen **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** til at vise denne adresse.
    
- IPsec-forudseende delt nøgle for websted-til-websted-VPN-forbindelsen (Tabel V- element 5 - værdikolonne).
    
Her er din resulterende konfiguration.
  
![Det virtuelle netværk er nu forbundet med det lokale netværk.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Fase 3 (valgfrit): Tilføj virtuelle computere

Opret de virtuelle maskiner, du skal bruge i Azure. Få mere at vide under [Opret en Windows virtuel maskine med Azure-portalen](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Brug følgende indstillinger:
  
- På fanen **Grundlæggende skal** du vælge den samme abonnements- og ressourcegruppe som dit virtuelle netværk. Du skal bruge disse senere for at logge på den virtuelle maskine. I sektionen **Forekomstdetaljer skal** du vælge den relevante virtuelle maskines størrelse. Optag administratorkontoens brugernavn og adgangskode på et sikkert sted. 
    
- På fanen **Netværk** skal du vælge navnet på dit virtuelle netværk og undernettet til at hoste virtuelle computere (ikke Gatewaysubnet). Lad alle andre indstillinger være ved deres standardværdier.
    
Kontrollér, at din virtuelle maskine bruger DNS korrekt ved at kontrollere din interne DNS for at sikre, at der er føjet adresseposter (A) til din nye virtuelle maskine. For at få adgang til internettet skal dine virtuelle Azure-maskiner være konfigureret til at bruge dit lokale netværks proxyserver. Kontakt netværksadministratoren for at få flere konfigurationstrin at udføre på serveren.
  
Her er din resulterende konfiguration.
  
![Det virtuelle netværk er nu vært for virtuelle computere, der er tilgængelige fra det lokale netværk.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Næste trin
  
[Installér Microsoft 365 katalogsynkronisering i Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)