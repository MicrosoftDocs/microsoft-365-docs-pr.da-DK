---
title: Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Få mere at vide om, hvordan du konfigurerer et virtuelt Azure-netværk på tværs af det lokale miljø for Office serverarbejdsbelastninger med en VPN-forbindelse fra websted til websted.'
ms.openlocfilehash: 8f9d8336bb50821374ada700613d2ae6142baf6d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094852"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk

Et virtuelt Azure-netværk på tværs af det lokale miljø er forbundet til dit lokale netværk og udvider dit netværk til at omfatte undernet og virtuelle maskiner, der hostes i Azure-infrastrukturtjenester. Denne forbindelse gør det muligt for computere på dit lokale netværk at få direkte adgang til virtuelle maskiner i Azure og omvendt. 

En katalogsynkroniseringsserver, der kører på en virtuel Azure-maskine, skal f.eks. forespørge dine lokale domænecontrollere om ændringer af konti og synkronisere disse ændringer med dit Microsoft 365 abonnement. I denne artikel kan du se, hvordan du konfigurerer et virtuelt Azure-netværk på tværs af det lokale miljø ved hjælp af en vpn-forbindelse (virtual private network), der er klar til at hoste virtuelle Azure-maskiner.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Konfigurer et virtuelt Azure-netværk på tværs af det lokale miljø

Dine virtuelle maskiner i Azure behøver ikke at være isoleret fra dit lokale miljø. Hvis du vil forbinde virtuelle Azure-maskiner med dine netværksressourcer i det lokale miljø, skal du konfigurere et virtuelt Azure-netværk på tværs af det lokale miljø. I følgende diagram vises de komponenter, der kræves for at installere et virtuelt Azure-netværk på tværs af det lokale miljø med en virtuel maskine i Azure.
  
![Netværk i det lokale miljø, der er forbundet til Microsoft Azure af en VPN-forbindelse fra websted til websted.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
I diagrammet er der to netværk, der er forbundet via en websted til websted-VPN-forbindelse: netværket i det lokale miljø og det virtuelle Azure-netværk. Vpn-forbindelsen fra websted til websted er:

- Mellem to slutpunkter, der er adresserbare og placeret på det offentlige internet.
- Afbrudt af en VPN-enhed på netværket i det lokale miljø og en Azure VPN-gateway på det virtuelle Azure-netværk.

Det virtuelle Azure-netværk hoster virtuelle maskiner. Netværkstrafik, der stammer fra virtuelle maskiner på det virtuelle Azure-netværk, videresendes til VPN-gatewayen, som derefter videresender trafikken på tværs af webstedets VPN-forbindelse til VPN-enheden på netværket i det lokale miljø. Distributionsinfrastrukturen for netværket i det lokale miljø videresender derefter trafikken til destinationen.

>[!Note]
>Du kan også bruge [ExpressRoute](https://azure.microsoft.com/services/expressroute/), som er en direkte forbindelse mellem din organisation og Microsofts netværk. Trafik via ExpressRoute rejser ikke over det offentlige internet. I denne artikel beskrives brugen af ExpressRoute ikke.
>
  
Hvis du vil konfigurere VPN-forbindelsen mellem dit virtuelle Azure-netværk og dit lokale netværk, skal du følge disse trin: 
  
1. **I det lokale miljø:** Definer og opret en netværksrute i det lokale miljø for adresseområdet for det virtuelle Azure-netværk, der peger på din VPN-enhed i det lokale miljø.
    
2. **Microsoft Azure:** Opret et virtuelt Azure-netværk med en VPN-forbindelse fra websted til websted. 
    
3. **I det lokale miljø:** Konfigurer vpn-enheden i det lokale miljø for at afslutte VPN-forbindelsen, som bruger IPsec (Internet Protocol Security).
    
Når du har etableret VPN-forbindelsen fra websted til websted, føjer du virtuelle Azure-maskiner til undernet for det virtuelle netværk.
  
## <a name="plan-your-azure-virtual-network"></a>Planlæg dit virtuelle Azure-netværk
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Forudsætninger
<a name="Prerequisites"></a>

- Et Azure-abonnement. Du kan få oplysninger om Azure-abonnementer på [siden Sådan køber du Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- Et tilgængeligt privat IPv4-adresseområde, der kan tildeles til det virtuelle netværk og dets undernet, med tilstrækkelig plads til vækst til at imødekomme det antal virtuelle maskiner, der er brug for nu og i fremtiden.
    
- En tilgængelig VPN-enhed på netværket i det lokale miljø til at afslutte den VPN-forbindelse, der understøtter kravene til IPsec. Du kan få flere oplysninger under [Om VPN-enheder til virtuelle netværksforbindelser fra websted til websted](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- Ændringer af distributionsinfrastrukturen, så trafik, der dirigeres til adresseområdet i det virtuelle Azure-netværk, videresendes til den VPN-enhed, der er vært for VPN-forbindelsen fra websted til websted.
    
- En webproxy, der giver computere, der har forbindelse til netværket i det lokale miljø og det virtuelle Azure-netværk, adgang til internettet.
    
### <a name="solution-architecture-design-assumptions"></a>Antagelser i forbindelse med løsningsarkitekturdesign

Følgende liste repræsenterer de designvalg, der er foretaget for denne løsningsarkitektur. 
  
- Denne løsning bruger et enkelt virtuelt Azure-netværk med en VPN-forbindelse fra websted til websted. Det virtuelle Azure-netværk hoster et enkelt undernet, der kan indeholde flere virtuelle maskiner. 
    
- Du kan bruge RRAS (Routing and Remote Access Service) i Windows Server 2016 eller Windows Server 2012 til at oprette en IPsec-websted til websted-VPN-forbindelse mellem netværket i det lokale miljø og det virtuelle Azure-netværk. Du kan også bruge andre muligheder, f.eks Cisco eller Juniper Networks VPN-enheder.
    
- Netværket i det lokale miljø kan stadig have netværkstjenester som f.eks. Active Directory-domæneservices (AD DS), Dns (Domain Name System) og proxyservere. Afhængigt af dine krav kan det være en fordel at placere nogle af disse netværksressourcer i det virtuelle Azure-netværk.
    
For et eksisterende virtuelt Azure-netværk med et eller flere undernet skal du afgøre, om der er resterende adresseplads til et ekstra undernet, der skal hoste dine nødvendige virtuelle maskiner, baseret på dine krav. Hvis du ikke har resterende adresseplads til et ekstra undernet, kan du oprette et ekstra virtuelt netværk, der har sin egen VPN-forbindelse fra websted til websted.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Planlæg ændringer af distributionsinfrastrukturen for det virtuelle Azure-netværk

Du skal konfigurere din distributionsinfrastruktur i det lokale miljø for at videresende trafik, der er beregnet til adresseområdet for det virtuelle Azure-netværk, til den VPN-enhed i det lokale miljø, der hoster VPN-forbindelsen fra websted til websted.
  
Den nøjagtige metode til opdatering af distributionsinfrastrukturen afhænger af, hvordan du administrerer distributionsoplysninger, som kan være:
  
- Opdateringer af distributionstabellen baseret på manuel konfiguration.
    
- Routingtabelopdateringer baseret på routingprotokoller, f.eks. RIP (Routing Information Protocol) eller OSPF (Open Shortest Path First).
    
Kontakt distributionsspecialisten for at sikre, at trafik, der er beregnet til det virtuelle Azure-netværk, videresendes til VPN-enheden i det lokale miljø.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Planlæg firewallregler for trafik til og fra VPN-enheden i det lokale miljø

Hvis DIN VPN-enhed er på et perimeternetværk, der har en firewall mellem perimeternetværket og internettet, skal du muligvis konfigurere firewallen for følgende regler for at tillade VPN-forbindelsen fra websted til websted.
  
- Trafik til VPN-enheden (indgående fra internettet):
    
  - DESTINATIONS-IP-adressen for VPN-enheden og IP-protokollen 50
    
  - DESTINATIONS-IP-adressen for VPN-enheden og UDP-destinationsporten 500
    
  - DESTINATIONS-IP-adressen på VPN-enheden og UDP-destinationsporten 4500
    
- Trafik fra VPN-enheden (udgående til internettet):
    
  - IP-kildeadressen for VPN-enheden og IP-protokollen 50
    
  - IP-kildeadresse for VPN-enheden og UDP-kildeport 500
    
  - IP-kildeadresse for VPN-enheden og UDP-kildeport 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Planlæg det private IP-adresseområde i det virtuelle Azure-netværk

Det private IP-adresseområde i det virtuelle Azure-netværk skal kunne rumme adresser, der bruges af Azure til at hoste det virtuelle netværk, og med mindst ét undernet, der har tilstrækkelige adresser til dine virtuelle Azure-maskiner.
  
Hvis du vil bestemme det antal adresser, der skal bruges til undernettet, skal du tælle antallet af virtuelle maskiner, du har brug for nu, beregne den fremtidige vækst og derefter bruge følgende tabel til at bestemme størrelsen af undernettet.
  
|**Antal virtuelle maskiner, der er nødvendige**|**Antal værtsbits, der skal bruges**|**Undernettets størrelse**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Planlægningsregneark til konfiguration af dit virtuelle Azure-netværk
<a name="worksheet"> </a>

Før du opretter et virtuelt Azure-netværk til at hoste virtuelle maskiner, skal du bestemme de indstillinger, der skal bruges i følgende tabeller.
  
Udfyld Tabel V for indstillingerne for det virtuelle netværk.
  
 **Tabel V: Konfiguration af virtuelt netværk på tværs af det lokale miljø**
  
|**Element**|**Konfigurationselement**|**Beskrivelse**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Navn på virtuelt netværk  <br/> |Et navn, der skal tildeles til det virtuelle Azure-netværk (f.eks. DirSyncNet).  <br/> |![Linje.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Placering af virtuelt netværk  <br/> |Azure-datacenteret, der indeholder det virtuelle netværk (f.eks. Det vestlige USA).  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |IP-adresse for VPN-enhed  <br/> |Den offentlige IPv4-adresse på vpn-enhedens grænseflade på internettet. Samarbejd med it-afdelingen om at bestemme denne adresse.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Adresseområde for virtuelt netværk  <br/> |Adresseområdet (defineret i et enkelt præfiks for privat adresse) for det virtuelle netværk. Samarbejd med it-afdelingen om at bestemme dette adresseområde. Adresseområdet skal være i CIDR-format (Classless Interdomain Routing), der også kaldes netværkspræfiksformat. Et eksempel er 10.24.64.0/20.  <br/> |![Linje.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |Delt nøgle til IPsec  <br/> |En 32-tegns tilfældig alfanumerisk streng, der bruges til at godkende begge sider af vpn-forbindelsen fra websted til websted. Samarbejd med it- eller sikkerhedsafdelingen om at bestemme denne nøgleværdi, og gem den derefter på en sikker placering. Alternativt kan du se [Opret en tilfældig streng for en IPsec-foruddelt nøgle](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![Linje.](../media/Common-Images/TableLine.png) <br/> |
   
Udfyld Tabel S for undernet i denne løsning.
  
- For det første undernet skal du bestemme et 28-bit adresseområde (med præfikslængden /28) for Azure Gateway-undernettet. Se [Beregning af adresseområdet for gatewayens undernet for virtuelle Azure-netværk for](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) at få oplysninger om, hvordan du bestemmer dette adresseområde.
    
- For det andet undernet skal du angive et brugervenligt navn, et enkelt IP-adresseområde baseret på det virtuelle netværksadresseområde og et beskrivende formål.
    
Samarbejd med it-afdelingen om at bestemme disse adresseområder fra det virtuelle netværksadresseområde. Begge adresseområder skal være i CIDR-format.
  
 **Tabel S: Undernet i det virtuelle netværk**
  
|**Element**|**Navn på undernet**|**Adresseområde for undernet**|**Formål**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af Azure-gatewayen.  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
Udfyld tabel D for de DNS-servere i det lokale miljø, som de virtuelle maskiner i det virtuelle netværk skal bruge. Giv hver DNS-server et brugervenligt navn og en enkelt IP-adresse. Dette fulde navn behøver ikke at svare til værtsnavnet eller computernavnet på DNS-serveren. Bemærk, at der vises to tomme poster, men du kan tilføje flere. Samarbejd med it-afdelingen om at fastlægge denne liste.
  
 **Tabel D: DNS-servere i det lokale miljø**
  
|**Element**|**Fuldt navn på DNS-server**|**DNS-server-IP-adresse**|
|:-----|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
Hvis du vil distribuere pakker fra det virtuelle Azure-netværk til organisationsnetværket på tværs af VPN-forbindelsen fra websted til websted, skal du konfigurere det virtuelle netværk med et lokalt netværk. Dette lokale netværk har en liste over adresseområderne (i CIDR-format) for alle de placeringer på organisationens lokale netværk, som de virtuelle maskiner i det virtuelle netværk skal nå ud til. Dette kan være alle placeringer på netværket i det lokale miljø eller et undersæt. Listen over adresseområder, der definerer det lokale netværk, skal være entydig og må ikke overlappe de adresseområder, der bruges til dette virtuelle netværk eller dine andre virtuelle netværk i det lokale miljø.
  
I forbindelse med sættet af lokale netværksadresseområder skal du udfylde Tabel L. Bemærk, at der er angivet tre tomme adresser, men du har typisk brug for mere. Samarbejd med it-afdelingen om at fastlægge denne liste.
  
 **Tabel L: Adressepræfikser for det lokale netværk**
  
|**Element**|**Adresseområde på lokalt netværk**|
|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Linje](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Oversigt over udrulning
<a name="DeploymentRoadmap"> </a>

Oprettelse af det virtuelle netværk på tværs af det lokale miljø og tilføjelse af virtuelle maskiner i Azure består af tre faser:
  
- Fase 1: Forbered dit lokale netværk.
    
- Fase 2: Opret det virtuelle netværk på tværs af det lokale miljø i Azure.
    
- Fase 3 (valgfrit): Tilføj virtuelle maskiner.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Fase 1: Forbered dit lokale netværk
<a name="Phase1"></a>

Du skal konfigurere netværket i det lokale miljø med en rute, der peger på og i sidste ende leverer trafik, der er bestemt til adresseområdet for det virtuelle netværk, til routeren på kanten af netværket i det lokale miljø. Kontakt netværksadministratoren for at finde ud af, hvordan du føjer ruten til distributionsinfrastrukturen for netværket i det lokale miljø.
  
Her er din resulterende konfiguration.
  
![Netværket i det lokale miljø skal have en rute til det virtuelle netværks adresseområde, der peger mod VPN-enheden.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Fase 2: Opret det virtuelle netværk på tværs af det lokale miljø i Azure
<a name="Phase2"></a>

Åbn først en Azure PowerShell prompt. Hvis du ikke har installeret Azure PowerShell, skal du se [Kom i gang med Azure PowerShell](/powershell/azure/get-started-azureps).

 
Log derefter på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Hent dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Angiv dit Azure-abonnement med disse kommandoer. Erstat alt i anførselstegnene, herunder < og > tegn, med det korrekte abonnementsnavn.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Opret derefter en ny ressourcegruppe for dit virtuelle netværk. Hvis du vil finde et entydigt navn på en ressourcegruppe, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
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
  
![Det virtuelle netværk har endnu ikke forbindelse til netværket i det lokale miljø.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Derefter skal du bruge disse kommandoer til at oprette gateways for VPN-forbindelsen fra websted til websted.
  
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
  
Konfigurer derefter din VPN-enhed i det lokale miljø for at oprette forbindelse til Azure VPN-gatewayen. Du kan få flere oplysninger under [Om VPN-enheder til Azure-forbindelser fra websted til websted Virtual Network.](/azure/vpn-gateway/vpn-gateway-about-vpn-devices)
  
Hvis du vil konfigurere vpn-enheden, skal du bruge følgende:
  
- Den offentlige IPv4-adresse på Azure VPN-gatewayen for dit virtuelle netværk. Brug kommandoen **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** til at få vist denne adresse.
    
- Den foruddelte IPsec-nøgle for VPN-forbindelsen fra websted til websted (tabel V- Element 5 – kolonnen Værdi).
    
Her er din resulterende konfiguration.
  
![Det virtuelle netværk er nu forbundet til netværket i det lokale miljø.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Fase 3 (valgfrit): Tilføj virtuelle maskiner

Opret de virtuelle maskiner, du har brug for, i Azure. Du kan få flere oplysninger under [Opret en Windows virtuel maskine med Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Brug følgende indstillinger:
  
- Under fanen **Grundlæggende** skal du vælge det samme abonnement og den samme ressourcegruppe som dit virtuelle netværk. Du skal bruge disse senere for at logge på den virtuelle maskine. I afsnittet **Oplysninger om forekomst** skal du vælge den relevante størrelse på den virtuelle maskine. Registrer administratorkontoens brugernavn og adgangskode på en sikker placering. 
    
- Under fanen **Netværk** skal du vælge navnet på dit virtuelle netværk og undernettet til hosting af virtuelle maskiner (ikke GatewaySubnet). Lad alle andre indstillinger være på deres standardværdier.
    
Kontrollér, at din virtuelle maskine bruger DNS korrekt, ved at kontrollere din interne DNS for at sikre, at adresseposter (A) blev tilføjet for dig nye virtuelle maskine. Hvis du vil have adgang til internettet, skal dine virtuelle Azure-maskiner være konfigureret til at bruge dit lokale netværks proxyserver. Kontakt netværksadministratoren for at få yderligere konfigurationstrin, der skal udføres på serveren.
  
Her er din resulterende konfiguration.
  
![Det virtuelle netværk hoster nu virtuelle maskiner, der er tilgængelige fra netværket i det lokale miljø.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Næste trin
  
[Installér synkronisering af Microsoft 365 adresseliste i Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)