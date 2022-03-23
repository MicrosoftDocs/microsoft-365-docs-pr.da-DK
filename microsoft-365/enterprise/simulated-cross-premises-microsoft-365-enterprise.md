---
title: Simuleret virtuelt netværk på tværs af rum i Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: seo-marvel-apr2020
description: 'Oversigt: Opret et simuleret virtuelt netværk på tværs af Microsoft Azure som et Microsoft 365 testmiljø.'
ms.openlocfilehash: 0d0e22b5c9a12f4757a6dff5892ef72a757d2bda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588755"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Simuleret virtuelt netværk på tværs af rum i Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

I denne artikel bliver du vejet gennem oprettelsen af et simuleret hybridmiljø i skyen Microsoft Azure brug af to virtuelle Azure-netværk. Her er den resulterende konfiguration. 
  
![Fase 3 af det simulerede virtuelle netværkstestmiljø med DC2-virtuel maskine i XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Dette simulerer et Azure IaaS-hybridmiljø i skyen og består af:
  
- Et simuleret og forenklet lokalt netværk, der er hostet i et virtuelt Azure-netværk (det virtuelle TestLab-netværk).
    
- Et simuleret virtuelt netværk på tværs af rum, der hostes i Azure (XPrem).
    
- En VNet-peeringrelation mellem de to virtuelle netværk.
    
- En sekundær domænecontroller i det virtuelle XPrem-netværk.
    
Dette giver et udgangspunkt og et fælles udgangspunkt, hvorfra du kan: 
  
- Udvikle og teste programmer i et simuleret Azure IaaS-hybridskymiljø.
    
- Opret testkonfigurationer af computere, nogle inden for det virtuelle TestLab-netværk og nogle inden for det virtuelle XPrem-netværk, for at simulere hybride skybaserede it-arbejdsbelastninger.
    
Der er tre større faser i konfigurationen af dette testmiljø:
  
1. Konfigurer det virtuelle TestLab-netværk.
    
2. Opret det virtuelle netværk på tværs af lokale netværk.
    
3. Konfigurer DC2.
    
> [!NOTE]
> Denne konfiguration kræver et betalt Azure-abonnement. 

Du kan bruge det resulterende miljø til at teste funktionerne og funktionaliteten [i Microsoft 365 til](https://www.microsoft.com/microsoft-365/enterprise) virksomheder med yderligere [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md) eller på egen hånd.

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Gå til [Microsoft 365 for enterprise Test Lab-guide](../downloads/Microsoft365EnterpriseTLGStack.pdf) stak for et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: Konfigurer det virtuelle TestLab-netværk

Brug instruktionerne i Fase **1** af den simulerede [virksomhedsbasekonfiguration](simulated-ent-base-configuration-microsoft-365-enterprise.md) til at konfigurere DC1-, APP1- og CLIENT1-computerne i det virtuelle Azure-netværk kaldet TestLab.
  
Dette er din aktuelle konfiguration. 
  
![Den simulerede virksomhedsbasekonfiguration i Azure.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: Opret det virtuelle XPrem-netværk

I denne fase skal du oprette og konfigurere det nye virtuelle XPrem-netværk og derefter forbinde det til det virtuelle TestLab-netværk med VNet-peering.
  
Start med at starte Azure PowerShell besked på din lokale computer.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). 
  
Log på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Få dit abonnementsnavn ved hjælp af denne kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt inden for anførselstegnene \< and > , herunder tegnene, med de korrekte navne.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Opret derefter det virtuelle XPrem-netværk, og beskyt det med en netværkssikkerhedsgruppe med disse kommandoer.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Derefter skal du oprette VNet-peeringrelationen mellem TestLab- og XPrem VNets med disse kommandoer.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Dette er din aktuelle konfiguration. 
  
![Fase 2 af det simulerede, virtuelle netværkstestmiljø med XPrem VNet og VNet-peeringrelationen.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: Konfigurer DC2

I denne fase skal du oprette den virtuelle DC2-maskine i det virtuelle XPrem-netværk og derefter konfigurere den som en repliker domænecontroller.
  
Først skal du oprette en virtuel maskine til DC2. Kør disse kommandoer ved Azure PowerShell kommandoprompten på din lokale computer.
  
```powershell
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Derefter skal du oprette forbindelse til den nye virtuelle DC2-maskine fra [Azure-portalen ved](https://portal.azure.com) hjælp af dens lokale administratorkontonavn og adgangskode.
  
Dernæst skal du konfigurere en Windows Firewall-regel for at tillade trafik til grundlæggende forbindelsestest. Kør disse kommandoer Windows PowerShell en kommandoprompt på DC2 på administratorniveau. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Kommandoen ping bør resultere i fire vellykkede svar fra IP-adresse 10.0.0.4. Dette er en test af trafik på tværs af VNet-peeringrelationen. 
  
Derefter skal du tilføje den ekstra datadisk som en ny lydstyrke med drevbogstavet F: med denne kommando fra Windows PowerShell kommandoprompt på DC2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Dernæst skal du konfigurere DC2 som en repliker domænecontroller for corp.contoso.com domæne. Kør disse kommandoer fra Windows PowerShell kommandoprompten på DC2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Bemærk, at du bliver bedt om at angive både adgangskoden til CORPUser1\\ og en DSRM-adgangskode (Directory Services Restore Mode) og at genstarte DC2. 
  
Nu hvor det virtuelle XPrem-netværk har sin egen DNS-server (DC2), skal du konfigurere det virtuelle XPrem-netværk for at bruge denne DNS-server. Kør disse kommandoer fra Azure PowerShell lokale computer.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Fra Azure-portalen på din lokale computer skal du oprette forbindelse til DC1 med legitimationsoplysningerne for CORPUser1\\. Hvis du vil konfigurere CORP-domænet, så computere og brugere bruger deres lokale domænecontroller til godkendelse, skal du køre disse kommandoer fra en Windows PowerShell-kommandoprompt på DC1 på administratorniveau.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Dette er din aktuelle konfiguration. 
  
![Fase 3 af det simulerede virtuelle netværkstestmiljø med DC2-virtuel maskine i XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Dit simulerede Azure-hybridskymiljø er nu klar til test.
  
Du er nu klar til at eksperimentere med yderligere funktioner [i Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Næste trin

Udforsk disse ekstra sæt test Lab-vejledninger:
  
- [Identitet](m365-enterprise-test-lab-guides.md#identity)
- [Administration af mobilenheder](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Beskyttelse af oplysninger](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)