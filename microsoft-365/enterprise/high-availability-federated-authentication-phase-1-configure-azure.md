---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 1 Konfigurer Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'Oversigt: Konfigurer infrastrukturen for Microsoft Azure til at hoste organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365.'
ms.openlocfilehash: f83aa494fcdead8f29810dea06193934b8ef26b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098378"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Godkendelse i organisationsnetværket med høj tilgængelighed fase 1: Konfigurer Azure

I denne fase opretter du ressourcegrupperne, det virtuelle netværk (VNet) og tilgængelighedssættene i Azure, der skal hoste de virtuelle maskiner i fase 2, 3 og 4. Du skal fuldføre denne fase, før du går videre til [fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Se [Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faserne.
  
Azure skal klargøres med disse grundlæggende komponenter:
  
- Ressourcegrupper
    
- Et virtuelt Azure-netværk på tværs af det lokale miljø (VNet) med undernet til hosting af de virtuelle Azure-maskiner
    
- Netværkssikkerhedsgrupper til udførelse af isolation af undernet
    
- Tilgængelighedssæt
    
## <a name="configure-azure-components"></a>Konfigurer Azure-komponenter

Før du begynder at konfigurere Azure-komponenter, skal du udfylde følgende tabeller. Du kan hjælpe dig med at konfigurere Azure ved at udskrive denne sektion og skrive de nødvendige oplysninger ned eller kopiere sektionen til et dokument og udfylde den. Udfyld Tabel V for at få vist indstillingerne for VNet.
  
|**Element**|**Konfigurationsindstilling**|**Beskrivelse**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNet-navn  <br/> |Et navn, der skal tildeles til VNet (f.eks. FedAuthNet).  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |VNet-placering  <br/> |Det regionale Azure-datacenter, der indeholder det virtuelle netværk.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |IP-adresse for VPN-enhed  <br/> |Den offentlige IPv4-adresse på vpn-enhedens grænseflade på internettet.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet-adresseområde  <br/> |Adresseområdet for det virtuelle netværk. Samarbejd med it-afdelingen om at bestemme dette adresseområde.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Delt nøgle til IPsec  <br/> |En 32-tegns tilfældig alfanumerisk streng, der bruges til at godkende begge sider af vpn-forbindelsen fra websted til websted. Samarbejd med it- eller sikkerhedsafdelingen om at bestemme denne nøgleværdi. Alternativt kan du se [Opret en tilfældig streng for en IPsec-foruddelt nøgle](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel V: Konfiguration af virtuelt netværk på tværs af det lokale miljø**
  
Udfyld derefter Tabel S for undernet for denne løsning. Alle adresseområder skal være i CIDR-format (Classless Interdomain Routing), også kendt som netværkspræfiksformat. Et eksempel er 10.24.64.0/20.
  
For de første tre undernet skal du angive et navn og et enkelt IP-adresseområde baseret på det virtuelle netværksadresseområde. For gatewayundernettet skal du bestemme 27-bit adresseområdet (med præfikslængden /27) for Azure Gateway-undernettet med følgende:
  
1. Angiv variable bits i adresseområdet for VNet til 1 op til de bit, der bruges af gatewayens undernet, og angiv derefter de resterende bit til 0.
    
2. Konvertér de resulterende bit til decimaler, og udtryk det som et adresseområde, hvor præfiksets længde er angivet til størrelsen på gatewayens undernet.
    
Se [Adressepladsberegner til Azure Gateway-undernet](address-space-calculator-for-azure-gateway-subnets.md) for en PowerShell-kommandoblok og C# eller Python-konsolprogram, der udfører denne beregning for dig.
  
Samarbejd med it-afdelingen om at bestemme disse adresseområder fra det virtuelle netværksadresseområde.
  
|**Element**|**Navn på undernet**|**Adresseområde for undernet**|**Formål**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af ad DS-domænecontrolleren (Active Directory-domæneservices) og virtuelle maskiner (VM'er) til katalogsynkroniseringsserver.  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af AD FS VM'er.  <br/> |
|3.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af vm'er til webprogramproxy.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af Azure Gateway VM'er.  <br/> |
   
 **Tabel S: Undernet i det virtuelle netværk**
  
Udfyld derefter Tabel I for de statiske IP-adresser, der er tildelt virtuelle maskiner og belastningsjusteringsforekomster.
  
|**Element**|**Formål**|**IP-adresse på undernet**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statisk IP-adresse for den første domænecontroller  <br/> |Den fjerde mulige IP-adresse for adresseområdet i det undernet, der er defineret i element 1 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Statisk IP-adresse for den anden domænecontroller  <br/> |Den femte mulige IP-adresse for adresseområdet på det undernet, der er defineret i punkt 1 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Statisk IP-adresse på katalogsynkroniseringsserveren  <br/> |Den sjette mulige IP-adresse for adresseområdet på det undernet, der er defineret i punkt 1 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Statisk IP-adresse for den interne belastningsjustering for AD FS-serverne  <br/> |Den fjerde mulige IP-adresse for adresseområdet i det undernet, der er defineret i element 2 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Statisk IP-adresse på den første AD FS-server  <br/> |Den femte mulige IP-adresse for adresseområdet på det undernet, der er defineret i punkt 2 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Statisk IP-adresse for den anden AD FS-server  <br/> |Den sjette mulige IP-adresse for adresseområdet i det undernet, der er defineret i punkt 2 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Statisk IP-adresse på den første webprogramproxyserver  <br/> |Den fjerde mulige IP-adresse for adresseområdet i det undernet, der er defineret i punkt 3 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Statisk IP-adresse på den anden webprogramproxyserver  <br/> |Den femte mulige IP-adresse for adresseområdet på det undernet, der er defineret i punkt 3 i tabel S.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel I: Statiske IP-adresser i det virtuelle netværk**
  
Udfyld tabel D for to DNS-servere (Domain Name System) på netværket i det lokale miljø, som du vil bruge, når du konfigurerer domænecontrollerne i dit virtuelle netværk. Kontakt it-afdelingen for at finde listen.
  
|**Element**|**Fuldt navn på DNS-server**|**DNS-server-IP-adresse**|
|:-----|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel D: DNS-servere i det lokale miljø**
  
Hvis du vil distribuere pakker fra netværket på tværs af det lokale miljø til organisationsnetværket på tværs af VPN-forbindelsen fra websted til websted, skal du konfigurere det virtuelle netværk med et lokalt netværk, der har en liste over adresseområderne (i CIDR-notationen) for alle de placeringer, der kan nås på organisationens lokale netværk. Listen over adresseområder, der definerer det lokale netværk, skal være entydig og må ikke overlappe den adresseplads, der bruges til andre virtuelle netværk eller andre lokale netværk.
  
I forbindelse med sættet af lokale netværksadresseområder skal du udfylde Tabel L. Bemærk, at der er angivet tre tomme adresser, men du har typisk brug for mere. Samarbejd med it-afdelingen om at fastlægge denne liste over adresseområder.
  
|**Element**|**Adresseområde på lokalt netværk**|
|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel L: Adressepræfikser for det lokale netværk**
  
Lad os nu begynde at bygge Azure-infrastrukturen til at hoste din godkendelse i organisationsnetværket for Microsoft 365.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Start først en Azure PowerShell spørg, og log på din konto.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Hvis du vil generere PowerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du bruge denne [Microsoft Excel konfigurationsprojektmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

Hent dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Brug denne kommando i stedet for til ældre versioner af Azure PowerShell.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Angiv dit Azure-abonnement. Erstat alt i anførselstegnene, herunder tegnene \< and > , med det korrekte navn.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Opret derefter de nye ressourcegrupper. Hvis du vil bestemme et entydigt sæt af navne på ressourcegrupper, skal du bruge denne kommando til at få vist dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Udfyld følgende tabel for sættet af entydige navne på ressourcegrupper.
  
|**Element**|**Navn på ressourcegruppe**|**Formål**|
|:-----|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Domænecontrollere  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |AD FS-servere  <br/> |
|3.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Proxyservere for webprogram  <br/> |
|4.  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |Infrastrukturelementer  <br/> |
   
 **Tabel R: Ressourcegrupper**
  
Opret dine nye ressourcegrupper med disse kommandoer.
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Derefter skal du oprette det virtuelle Azure-netværk og dets undernet.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

Derefter skal du oprette netværkssikkerhedsgrupper for hvert undernet, der har virtuelle maskiner. Hvis du vil udføre undernetisolation, kan du føje regler for de specifikke trafiktyper, der er tilladt eller nægtet til netværkssikkerhedsgruppen for et undernet.
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Derefter skal du bruge disse kommandoer til at oprette gateways for VPN-forbindelsen fra websted til websted.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> Godkendelse i organisationsnetværket af individuelle brugere er ikke afhængig af ressourcer i det lokale miljø. Men hvis denne websted til websted-VPN-forbindelse bliver utilgængelig, modtager domænecontrollerne i VNet ikke opdateringer til brugerkonti og grupper, der er oprettet i Active Directory i det lokale miljø Domænetjenester. Hvis du vil sikre, at dette ikke sker, kan du konfigurere høj tilgængelighed for din websted til websted-VPN-forbindelse. Du kan få flere oplysninger under [Yderst tilgængelig på tværs af det lokale miljø og VNet-til-VNet-forbindelse](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Derefter skal du registrere den offentlige IPv4-adresse på Azure VPN-gatewayen for dit virtuelle netværk fra visningen af denne kommando:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Konfigurer derefter din VPN-enhed i det lokale miljø for at oprette forbindelse til Azure VPN-gatewayen. Du kan få flere oplysninger under [Konfigurer VPN-enheden](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Hvis du vil konfigurere din VPN-enhed i det lokale miljø, skal du bruge følgende:
  
- Den offentlige IPv4-adresse for Azure VPN-gatewayen.
    
- Den foruddelte IPsec-nøgle for VPN-forbindelsen fra websted til websted (Tabel V – Element 5 – Kolonnen Værdi).
    
Sørg derefter for, at der er adgang til adresseområdet på det virtuelle netværk fra dit lokale netværk. Dette gøres normalt ved at føje en rute, der svarer til det virtuelle netværksadresseområde, til din VPN-enhed og derefter reklamere for denne rute til resten af distributionsinfrastrukturen i organisationens netværk. Samarbejd med it-afdelingen for at finde ud af, hvordan det skal gøres.
  
Derefter skal du definere navnene på tre tilgængelighedssæt. Udfyld tabel A. 
  
|**Element**|**Formål**|**Navn på tilgængelighedssæt**|
|:-----|:-----|:-----|
|1.  <br/> |Domænecontrollere  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS-servere  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Proxyservere for webprogram  <br/> |![Linje.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel A: Tilgængelighedssæt**
  
Du skal bruge disse navne, når du opretter de virtuelle maskiner i fase 2, 3 og 4.
  
Opret de nye tilgængelighedssæt med disse Azure PowerShell kommandoer.
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

Dette er den konfiguration, der er resultatet af den vellykkede fuldførelse af denne fase.
  
**Fase 1: Azure-infrastrukturen til samlet godkendelse med høj tilgængelighed til Microsoft 365**

![Fase 1 af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelse i Azure med Azure-infrastrukturen.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Næste trin

Brug [fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) for at fortsætte med konfigurationen af denne arbejdsbelastning.
  
## <a name="see-also"></a>Se også

[Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Organisationsnetværksidentitet for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)

[Om Microsoft 365 identitetsmodeller](deploy-identity-solution-identity-model.md)