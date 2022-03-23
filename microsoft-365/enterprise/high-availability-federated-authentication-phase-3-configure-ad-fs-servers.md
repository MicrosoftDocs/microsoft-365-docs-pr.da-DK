---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 3 Konfigurer AD FS-servere
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: Få mere at vide om, hvordan du opretter og konfigurerer AD FS-servere til din godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Microsoft Azure.
ms.openlocfilehash: c26fc68aa382ce93c62b6edbce4040b7e0813474
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590606"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 3: Konfigurer AD FS-servere

I denne fase af udrulning af høj tilgængelighed for Microsoft 365 i organisationsnetværket i Azure-infrastrukturtjenester, skal du oprette en intern belastningsbalancere og to AD FS-servere.
  
Du skal fuldføre denne fase, før du går videre [til Fase 4: Konfigurer webprogram-proxyer](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Se [Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faser.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>Opret virtuelle AD FS-servercomputere i Azure

Brug følgende blok af PowerShell-kommandoer til at oprette de virtuelle maskiner til de to AD FS-servere. Dette PowerShell-kommandosæt bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V til indstillingerne for virtuelt netværk
    
- Tabel S til dine undernet
    
- Tabel I til dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du definerede Tabel M i Fase [2: Konfigurer](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) domænecontrollere og tabellerne R, V, S, I og A i [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Først skal du oprette en intern Azure-belastningsbalance for de to AD FS-servere. Angiv værdierne for variablerne, og fjern tegnene \< and > . Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved Azure PowerShell kommandoprompt eller i PowerShell ISE.
  
> [!TIP]
> Hvis du vil generere powerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du [Microsoft Excel projektmappen til konfiguration](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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

Dernæst skal du oprette virtuelle AD FS-servercomputere.
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved Azure PowerShell kommandoprompt eller i PowerShell ISE.
  
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
> Da disse virtuelle computere er til et intranetprogram, er de ikke tildelt en offentlig IP-adresse eller et DNS-domænenavnenavn, der vises på internettet. Men det betyder også, at du ikke kan oprette forbindelse til dem fra Azure-portalen. Indstillingen **Forbind** ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til fjernskrivebord eller et andet fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller DNS-navn på intranettet.
  
For hver virtuel maskine skal du bruge den foretrukne fjernskrivebord-klient og oprette en forbindelse til fjernskriveborde. Brug dets intranet-DNS eller computernavn samt legitimationsoplysningerne for den lokale administratorkonto.
  
For hver virtuel maskine skal de joinforbindelse dem til det relevante Active Directory-domæneservices (AD DS)-domæne med disse kommandoer i Windows PowerShell prompten.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Her er konfigurationen, der fremkommer, når denne fase er fuldført, med pladsholdercomputernavne.
  
**Fase 3: AD FS-servere og intern belastningsbalancer for din godkendelsesinfrastruktur i organisationsnetværket med høj tilgængelighed i Azure**

![Fase 3 af den høje tilgængelighed Microsoft 365 organisationsnetværkets godkendelsesinfrastruktur i Azure med AD FS-serverne.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>Næste trin

Brug [Fase 4: Konfigurer webprogram-proxyer for](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) at fortsætte med at konfigurere denne arbejdsbyrde.
  
## <a name="see-also"></a>Se også

[Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identitet i organisationsnetværk for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)