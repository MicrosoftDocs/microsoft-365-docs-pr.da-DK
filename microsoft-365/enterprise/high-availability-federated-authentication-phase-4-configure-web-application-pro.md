---
title: Godkendelse med høj tilgængelighed Fase 4 Konfigurer webprogram-proxyer
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Oversigt: Konfigurer webprogrammets proxyservere for din godkendelse i organisationsnetværket med høj tilgængelighed for Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: ea50a48fe4bebd997ecf6b472a60e57772bf2b0f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590582"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 4: Konfigurer webprogram-proxyer

I denne fase af udrulning af høj tilgængelighed for Microsoft 365 i organisationsnetværket i Azure-infrastrukturtjenester, skal du oprette en intern belastningsbalancere og to AD FS-servere.
  
Du skal fuldføre denne fase, før du går [videre til Fase 5: Konfigurer federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Se [Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faser.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Opret en internetbaseret belastningsbalance i Azure

Du skal oprette en belastningsbalance, der vender mod internettet, så Azure distribuerer trafik til indgående klientgodkendelse fra internettet jævnt blandt de to webprogramproxyservere.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Når du har angivet placerings- og ressourcegruppeværdier, skal du køre den resulterende blok ved Azure PowerShell kommandoprompt eller i PowerShell ISE.
  
> [!TIP]
> Hvis du vil generere powerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du [Microsoft Excel projektmappen til konfiguration](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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

For at få vist den offentlige IP-adresse, der er tildelt din internetrettede belastningsbalance, skal du køre disse kommandoer i Azure PowerShell på din lokale computer:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Fastlægge din sammenslutningstjeneste FQDN og oprette DNS-poster

Du skal bestemme DNS-navnet for at identificere navnet på din sammenslutningstjeneste på internettet. Azure AD Forbind konfigurerer Microsoft 365 med dette navn i fase 5, som bliver en del af URL-adressen, som Microsoft 365 sender til at oprette forbindelse til klienter for at få et sikkerhedstoken. Et eksempel er fs.contoso.com (fs står for sammenslutningstjeneste).
  
Når du har din sammenslutningstjeneste FDQN, skal du oprette et offentligt DNS-domæne En post for sammenslutningstjenesten FDQN, der løses til den offentlige IP-adresse for den belastningsbalancere, der er vendt mod Azure på internettet.
  
|**Navn**|**Type**|**TTL**|**Værdi**|
|:-----|:-----|:-----|:-----|
|sammenslutningstjeneste FDQN  <br/> |A  <br/> |3600  <br/> |offentlig IP-adresse for belastningsbalancen for Azure på internettet (vises ved kommandoen **Skrivevært** i forrige afsnit) <br/> |
   
Her er et eksempel:
  
|**Navn**|**Type**|**TTL**|**Værdi**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
Dernæst skal du føje en DNS-adressepost til din organisations private DNS-navneområde, som løser din sammenslutningstjenestes FQDN til den private IP-adresse, der er tildelt den interne belastningsbalance for AD FS-servere (Tabel I, element 4, kolonnen Værdi).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Opret virtuelle webprogramproxyservercomputere i Azure

Brug følgende blok af Azure PowerShell til at oprette de virtuelle maskiner til de to webprogramproxyservere. 
  
Bemærk, at følgende Azure PowerShell som kommandosæt bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V til indstillingerne for virtuelt netværk
    
- Tabel S til dine undernet
    
- Tabel I til dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du definerede Tabel M i Fase [2: Konfigurer](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) domænecontrollere og tabellerne R, V, S, I og A i [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved Azure PowerShell kommandoprompt eller i PowerShell ISE.
  
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
> Da disse virtuelle computere er til et intranetprogram, er de ikke tildelt en offentlig IP-adresse eller et DNS-domænenavnenavn, der vises på internettet. Men det betyder også, at du ikke kan oprette forbindelse til dem fra Azure-portalen. Indstillingen **Forbind** ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til fjernskrivebord eller et andet Fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller DNS-navn på intranettet og legitimationsoplysningerne for den lokale administratorkonto.
  
Her er konfigurationen, der fremkommer, når denne fase er fuldført, med pladsholdercomputernavne.
  
**Fase 4: Internet-modstående belastningsbalancer og webprogramproxyservere for din infrastruktur til godkendelse i organisationsnetværket med høj tilgængelighed i Azure**

![Fase 4 af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure med webprogrammets proxyservere.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Næste trin

Brug [Fase 5: Konfigurer federated authentication for Microsoft 365 at](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) fortsætte med at konfigurere denne arbejdsbyrde.
  
## <a name="see-also"></a>Se også

[Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identitet i organisationsnetværk for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 og arkitekturcenter](../solutions/index.yml)