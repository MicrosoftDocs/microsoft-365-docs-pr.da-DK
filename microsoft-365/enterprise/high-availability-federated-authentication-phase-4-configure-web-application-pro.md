---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 4 Konfigurer proxyer for webprogrammer
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Oversigt: Konfigurer webprogramproxyserverne for din organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: 2200d4f7c0aafbaff11dd5d9b5b5b414fae06b5f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091275"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 4: Konfigurer proxyer for webprogrammer

I denne fase af udrulningen af høj tilgængelighed til Microsoft 365 sammenkædet godkendelse i Azure-infrastrukturtjenester opretter du en intern belastningsjustering og to AD FS-servere.
  
Du skal fuldføre denne fase, før du går videre til [fase 5: Konfigurer godkendelse i organisationsnetværket for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Se [Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faserne.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Opret belastningsjusteringen på internettet i Azure

Du skal oprette en belastningsjustering på internettet, så Azure distribuerer trafik til indgående klientgodkendelse fra internettet jævnt mellem de to proxyservere for webprogrammer.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Når du har angivet værdier for placering og ressourcegruppe, skal du køre den resulterende blok ved kommandoprompten Azure PowerShell eller i PowerShell ISE.
  
> [!TIP]
> Hvis du vil generere PowerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du bruge denne [Microsoft Excel konfigurationsprojektmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Hvis du vil have vist den offentlige IP-adresse, der er tildelt belastningsjusteringen via internettet, skal du køre disse kommandoer ved kommandoprompten Azure PowerShell på din lokale computer:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Fastlæg FQDN for din sammenslutningstjeneste, og opret DNS-poster

Du skal bestemme DNS-navnet for at identificere navnet på din organisationstjeneste på internettet. Azure AD-Forbind konfigurerer Microsoft 365 med dette navn i fase 5, som bliver en del af den URL-adresse, som Microsoft 365 sender til at oprette forbindelse til klienter for at få et sikkerhedstoken. Et eksempel er fs.contoso.com (fs står for federation service).
  
Når du har din FDQN-organisationstjeneste, skal du oprette et offentligt DNS-domæne En post for FDQN-organisationstjenesten, der fortolkes som den offentlige IP-adresse for belastningsjusteringen på Azure Internet.
  
|**Navn**|**Type**|**TTL**|**Værdi**|
|:-----|:-----|:-----|:-----|
|federation service FDQN  <br/> |A  <br/> |3600  <br/> |offentlig IP-adresse for belastningsjusteringen i Azure Internet (vises af kommandoen **Write-Host** i det forrige afsnit) <br/> |
   
Her er et eksempel:
  
|**Navn**|**Type**|**TTL**|**Værdi**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Derefter skal du føje en DNS-adressepost til din organisations private DNS-navneområde, der fortolker FQDN for din sammenslutningstjeneste til den private IP-adresse, der er tildelt den interne belastningsjustering for AD FS-serverne (tabel I, element 4, værdikolonne).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Opret virtuelle maskiner til webprogramproxyserveren i Azure

Brug følgende blok Azure PowerShell kommandoer til at oprette de virtuelle maskiner til de to webprogramproxyservere. 
  
Bemærk, at følgende Azure PowerShell kommandosæt bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V for dine indstillinger for virtuelle netværk
    
- Tabel S for dine undernet
    
- Tabel I for dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du definerede Tabel M i [fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) og Tabeller R, V, S, I og A i [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved kommandoprompten Azure PowerShell eller i PowerShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Da disse virtuelle maskiner er til et intranetprogram, tildeles de ikke en offentlig IP-adresse eller et DNS-domænenavn og vises på internettet. Det betyder dog også, at du ikke kan oprette forbindelse til dem fra Azure Portal. Indstillingen **Forbind** er ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til Fjernskrivebord eller et andet fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller intranet-DNS-navn og legitimationsoplysningerne for den lokale administratorkonto.
  
Her er den konfiguration, der er resultatet af den vellykkede fuldførelse af denne fase med navne på pladsholdercomputere.
  
**Fase 4: Belastningsjustering via internettet og proxyservere for webprogrammer til din netværksbaserede godkendelsesinfrastruktur med høj tilgængelighed i Azure**

![Fase 4 af den høje tilgængelighed Microsoft 365 organisationsnetværket godkendelsesinfrastruktur i Azure med webprogramproxyserverne.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Næste trin

Brug [fase 5: Konfigurer godkendelse i organisationsnetværket for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) for at fortsætte konfigurationen af denne arbejdsbelastning.
  
## <a name="see-also"></a>Se også

[Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Organisationsnetværksidentitet for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)