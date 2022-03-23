---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 1 Konfigurer Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Konfigurer den Microsoft Azure til at hoste godkendelse i organisationsnetværket med høj tilgængelighed for Microsoft 365.'
ms.openlocfilehash: 35666baf98b45419f41a0078729ac5a5a6fab995
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63591391"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 1: Konfigurer Azure

I denne fase opretter du ressourcegrupper, virtuelt netværk (VNet) og tilgængelighedssæt i Azure, der er vært for de virtuelle maskiner i faserne 2, 3 og 4. Du skal fuldføre denne fase, før du går videre [til Fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Se [Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faser.
  
Azure skal klargøres med disse grundlæggende komponenter:
  
- Ressourcegrupper
    
- Et virtuelt Azure-netværk på tværs af et miljø (VNet) med undernet til at hoste de virtuelle Azure-maskiner
    
- Netværkssikkerhedsgrupper til udførelse af undernetisolation
    
- Tilgængelighedssæt
    
## <a name="configure-azure-components"></a>Konfigurer Azure-komponenter

Inden du går i gang med at konfigurere Azure-komponenter, skal du udfylde følgende tabeller. For at hjælpe dig med procedurerne til konfiguration af Azure skal du udskrive dette afsnit og skrive de nødvendige oplysninger ned eller kopiere denne sektion til et dokument og udfylde det. Udfyld Tabel V for at se indstillingerne for VNet.
  
|**Element**|**Konfigurationsindstilling**|**Beskrivelse**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNetnavn  <br/> |Et navn, der skal tildeles VNet (f.eks. FedAuthNet).  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |VNetplacering  <br/> |Det regionale Azure-datacenter, der skal indeholde det virtuelle netværk.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |IP-adresse på VPN-enhed  <br/> |Den offentlige IPv4-adresse for din VPN-enheds grænseflade på internettet.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet-adresseområde  <br/> |Adressepladsen til det virtuelle netværk. Arbejd sammen med din it-afdeling for at finde dette adresseområde.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Delt IPsec-nøgle  <br/> |En vilkårlig, alfanumerisk streng på 32 tegn, der skal bruges til at godkende begge sider af VPN-forbindelsen mellem websted og websted. Arbejd med din it- eller sikkerhedsafdeling for at finde frem til denne nøgleværdi. Du kan også se [Opret en tilfældig streng for en IPsec-foruddelt nøgle](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel V: Konfiguration af virtuelt netværk på tværs af lokale netværk**
  
Dernæst skal du udfylde Tabel S for denne løsnings undernet. Alle adresseområder skal være i CIDR-format (Classless Interdomain Routing), også kaldet et format med et netværkspræfiks. Et eksempel er 10.24.64.0/20.
  
For de første tre undernet skal du angive et navn og et enkelt IP-adresseområde, der er baseret på det virtuelle netværks adresseområde. For gatewayundernettet skal du bestemme 27-bit adresseområde (med en længde på /27 præfiks) for Azure gateway-undernettet med følgende:
  
1. Angiv variable bit i adresserummet for VNet til 1, op til de bit, der bruges af gatewayundernettet, og angiv derefter de resterende bit til 0.
    
2. Konvertér de resulterende bit til decimaler, og udtryk dem som et adresseområde med præfikslængden indstillet til størrelsen af gatewayundernettet.
    
Se [Adressepladsberegner til Azure gateway-undernet](address-space-calculator-for-azure-gateway-subnets.md) for en PowerShell-kommandoblok og C# eller Python-konsolprogram, der udfører denne beregning for dig.
  
Arbejd sammen med din it-afdeling for at bestemme disse adresseområder fra det virtuelle netværks adresseområde.
  
|**Element**|**Navn på undernet**|**Undernetadresseområde**|**Formål**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af den Active Directory-domæneservices (AD DS) domænecontroller og virtuelle computere med katalogsynkroniseringsserver (VMs).  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af AD FS VMs.  <br/> |
|3.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af webprogrammets proxy-VM'er.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Det undernet, der bruges af Azure Gateway-VM'er.  <br/> |
   
 **Tabel S: Undernet i det virtuelle netværk**
  
Dernæst skal du udfylde tabel I for de statiske IP-adresser, der er tildelt virtuelle maskiner og belastningsbalancerforekomster.
  
|**Element**|**Formål**|**IP-adresse på undernettet**|**Værdi**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Statisk IP-adresse på den første domænecontroller  <br/> |Den fjerde mulige IP-adresse for adresserummet for undernettet, der er defineret i element 1 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |Statisk IP-adresse på den anden domænecontroller  <br/> |Den femte mulige IP-adresse for adresserummet for undernettet, der er defineret i element 1 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Statisk IP-adresse på katalogsynkroniseringsserveren  <br/> |Den sjette mulige IP-adresse for adresserummet for undernettet, der er defineret i element 1 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Statisk IP-adresse for den interne belastningsbalance for AD FS-servere  <br/> |Den fjerde mulige IP-adresse for adresserummet for undernettet, der er defineret i element 2 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |Statisk IP-adresse på den første AD FS-server  <br/> |Den femte mulige IP-adresse for adresserummet for undernettet, der er defineret i element 2 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |Statisk IP-adresse på den anden AD FS-server  <br/> |Den sjette mulige IP-adresse for adresserummet for det undernet, der er defineret i element 2 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |Statisk IP-adresse på den første webprogramproxyserver  <br/> |Den fjerde mulige IP-adresse for adresserummet for undernettet, der er defineret i element 3 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |Statisk IP-adresse på den anden webprogramproxyserver  <br/> |Den femte mulige IP-adresse for adresserummet for undernettet, der er defineret i element 3 i Tabel S.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel I: Statiske IP-adresser i det virtuelle netværk**
  
Udfyld Tabel D for to DNS-servere (Domain Name System) i dit lokale netværk, som du vil bruge, når du først konfigurerer domænecontrollere i dit virtuelle netværk. Arbejd med din it-afdeling for at finde denne liste.
  
|**Element**|**Navn på dns-servervenligt**|**IP-adresse til DNS-server**|
|:-----|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel D: Lokale DNS-servere**
  
Hvis du vil distribuere pakker fra det lokale netværk til dit organisationsnetværk på tværs af VPN-forbindelsen mellem websted og websted, skal du konfigurere det virtuelle netværk med et lokalt netværk, der har en liste over adresseområderne (i CIDR-notation) for alle tilgængelige placeringer på organisationens lokale netværk. Listen over adresseområder, der definerer dit lokale netværk, skal være entydig og må ikke overlappe med det adresseområde, der bruges til andre virtuelle netværk eller andre lokale netværk.
  
Udfyld Tabel L for sættet af adresseområder i lokalnetværket. Bemærk, at tre tomme poster er angivet, men du har typisk brug for flere. Arbejd sammen med din it-afdeling for at finde denne liste over adresseområder.
  
|**Element**|**Lokal netværksadresseområde**|
|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel L: Adressepræfikser for det lokale netværk**
  
Lad os nu begynde at opbygge Azure-infrastrukturen til at hoste din organisationsnetværksgodkendelse til Microsoft 365.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Start først med en Azure PowerShell og logge på din konto.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> Hvis du vil generere powerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du [Microsoft Excel projektmappen til konfiguration](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

Få dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

For ældre versioner af Azure PowerShell skal du bruge denne kommando i stedet.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

Angiv dit Azure-abonnement. Erstat alt inden for anførselstegnene \< and > , herunder tegnene, med det korrekte navn.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Derefter skal du oprette de nye ressourcegrupper. Hvis du vil fastlægge et entydigt sæt ressourcegruppenavne, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Udfyld følgende tabel for sættet med entydige ressourcegruppenavne.
  
|**Element**|**Ressourcegruppenavn**|**Formål**|
|:-----|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Domænecontrollere  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |AD FS-servere  <br/> |
|3.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Webprogramproxyservere  <br/> |
|4.  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |Infrastrukturelementer  <br/> |
   
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

Derefter skal du oprette netværkssikkerhedsgrupper for hvert undernet, der har virtuelle computere. Hvis du vil udføre undernetisolation, kan du føje regler for bestemte typer trafik, der er tilladt eller afvist, til netværkssikkerhedsgruppen for et undernet.
  
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

Derefter skal du bruge disse kommandoer til at oprette gateways for VPN-forbindelsen mellem websted og websted.
  
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
> Federated Authentication for individuelle brugere er ikke afhængig af lokale ressourcer. Men hvis denne websted-til-websted VPN-forbindelse bliver utilgængelig, vil domænecontrollere i VNet ikke modtage opdateringer til brugerkonti og grupper, der er foretaget i den lokale Active Directory-domæneservices. For at sikre at dette ikke sker, kan du konfigurere høj tilgængelighed for din WEBSTED-til-websted VPN-forbindelse. Du kan få mere at [vide under Meget tilgængelig på tværs af lokale netværk og VNet-til-VNet-forbindelse](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Derefter skal du registrere den offentlige IPv4-adresse for Azure VPN-gatewayen for dit virtuelle netværk fra visningen af denne kommando:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

Dernæst skal du konfigurere din lokale VPN-enhed til at oprette forbindelse til Azure VPN-gatewayen. Få mere at vide under [Konfigurer din VPN-enhed](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
For at konfigurere din lokale VPN-enhed skal du bruge følgende:
  
- Den offentlige IPv4-adresse for Azure VPN-gatewayen.
    
- IPsec-forudseende delt nøgle for websted-til-websted-VPN-forbindelsen (Tabel V - element 5 - værdikolonne).
    
Dernæst skal du sikre dig, at der kan oprettes forbindelse til adressepladsen på det virtuelle netværk fra dit lokale netværk. Dette gøres normalt ved at føje en rute, der svarer til det virtuelle netværks adresseområde, til din VPN-enhed og derefter reklamere for den pågældende rute til resten af organisationens routinginfrastruktur. Arbejd sammen med din it-afdeling for at finde ud af, hvordan du gør dette.
  
Dernæst skal du definere navnene på tre tilgængelighedssæt. Udfyld tabel A. 
  
|**Element**|**Formål**|**Navn på tilgængelighedssæt**|
|:-----|:-----|:-----|
|1.  <br/> |Domænecontrollere  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS-servere  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Webprogramproxyservere  <br/> |![.](../media/Common-Images/TableLine.png)  <br/> |
   
 **Tabel A: Tilgængelighedssæt**
  
Du skal bruge disse navne, når du opretter de virtuelle maskiner i faserne 2, 3 og 4.
  
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
  
**Fase 1: Azure-infrastruktur til godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365**

![Fase 1 af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelse i Azure med Azure-infrastrukturen.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>Næste trin

Brug [Fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) for at fortsætte med konfigurationen af denne arbejdsbyrde.
  
## <a name="see-also"></a>Se også

[Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identitet i organisationsnetværk for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 og arkitekturcenter](../solutions/index.yml)

[Forstå Microsoft 365 identitetsmodeller](deploy-identity-solution-identity-model.md)