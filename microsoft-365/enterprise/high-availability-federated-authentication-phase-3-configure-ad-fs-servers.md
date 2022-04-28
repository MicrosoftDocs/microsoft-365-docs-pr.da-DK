---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 3 Konfigurer AD FS-servere
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Få mere at vide om, hvordan du opretter og konfigurerer AD FS-serverne til din organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Microsoft Azure.
ms.openlocfilehash: ed0974c8286a5bbad083152d2e2f9aeb01f659df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101243"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Godkendelse i organisationsnetværket med høj tilgængelighed fase 3: Konfigurer AD FS-servere

I denne fase af udrulningen af høj tilgængelighed til Microsoft 365 sammenkædet godkendelse i Azure-infrastrukturtjenester opretter du en intern belastningsjustering og to AD FS-servere.
  
Du skal fuldføre denne fase, før du går videre til [fase 4: Konfigurer proxyer for webprogrammer](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Se [Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faserne.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Opret virtuelle AD FS-servermaskiner i Azure

Brug følgende blok PowerShell-kommandoer til at oprette de virtuelle maskiner til de to AD FS-servere. Dette PowerShell-kommandosæt bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V for dine indstillinger for virtuelle netværk
    
- Tabel S for dine undernet
    
- Tabel I for dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du definerede Tabel M i [fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) og Tabeller R, V, S, I og A i [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Først skal du oprette en intern Belastningsjustering i Azure for de to AD FS-servere. Angiv værdierne for variablerne, og fjern tegnene \< and > . Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved kommandoprompten Azure PowerShell eller i PowerShell ISE.
  
> [!TIP]
> Hvis du vil generere PowerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du bruge denne [Microsoft Excel konfigurationsprojektmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Opret derefter de virtuelle AD FS-servercomputere.
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved kommandoprompten Azure PowerShell eller i PowerShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> Da disse virtuelle maskiner er til et intranetprogram, tildeles de ikke en offentlig IP-adresse eller et DNS-domænenavn og vises på internettet. Det betyder dog også, at du ikke kan oprette forbindelse til dem fra Azure Portal. Indstillingen **Forbind** er ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til Fjernskrivebord eller et andet fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller intranet-DNS-navn.
  
For hver virtuel maskine skal du bruge den valgte fjernskrivebordsklient og oprette en forbindelse til fjernskrivebord. Brug intranet-DNS- eller computernavnet og legitimationsoplysningerne for den lokale administratorkonto.
  
For hver virtuel maskine skal du slutte dem til det relevante AD DS-domæne (Active Directory-domæneservices) med disse kommandoer ved Windows PowerShell prompt.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Her er den konfiguration, der er resultatet af den vellykkede fuldførelse af denne fase med navne på pladsholdercomputere.
  
**Fase 3: AD FS-serverne og den interne belastningsjustering for din netværksforbundne godkendelsesinfrastruktur med høj tilgængelighed i Azure**

![Fase 3 af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure med AD FS-serverne.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Næste trin

Brug [fase 4: Konfigurer proxyer for webprogrammer](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) for at fortsætte konfigurationen af denne arbejdsbelastning.
  
## <a name="see-also"></a>Se også

[Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Organisationsnetværksidentitet for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)