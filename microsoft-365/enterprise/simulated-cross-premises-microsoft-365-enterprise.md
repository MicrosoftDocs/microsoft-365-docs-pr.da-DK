---
title: Simuleret virtuelt netværk på tværs af det lokale miljø i et testmiljø Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Opret et simuleret virtuelt netværk på tværs af det lokale miljø i Microsoft Azure som et Microsoft 365 testmiljø.'
ms.openlocfilehash: a3bc5c130ad03d1896abcf98ba9fc26d9ff2f422
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099163"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Simuleret virtuelt netværk på tværs af det lokale miljø i et testmiljø Microsoft 365

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

I denne artikel får du hjælp til at oprette et simuleret hybridt cloudmiljø med Microsoft Azure ved hjælp af to virtuelle Azure-netværk. Her er den resulterende konfiguration. 
  
![Fase 3 af det simulerede virtuelle netværkstestmiljø på tværs af det lokale miljø med den virtuelle DC2-maskine i XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Dette simulerer et Azure IaaS-hybrid cloudproduktionsmiljø og består af:
  
- Et simuleret og forenklet netværk i det lokale miljø, der hostes på et virtuelt Azure-netværk (det virtuelle TestLab-netværk).
    
- Et simuleret virtuelt netværk på tværs af det lokale miljø, der hostes i Azure (XPrem).
    
- En VNet-peering-relation mellem de to virtuelle netværk.
    
- En sekundær domænecontroller i det virtuelle XPrem-netværk.
    
Dette giver dig et grundlag og et fælles udgangspunkt, hvorfra du kan: 
  
- Udvikl og test programmer i et simuleret Azure IaaS-hybridskymiljø.
    
- Opret testkonfigurationer af computere, nogle i det virtuelle TestLab-netværk og nogle i det virtuelle XPrem-netværk, for at simulere hybride cloudbaserede it-arbejdsbelastninger.
    
Der er tre overordnede faser til konfiguration af dette testmiljø:
  
1. Konfigurer det virtuelle TestLab-netværk.
    
2. Opret det virtuelle netværk på tværs af det lokale miljø.
    
3. Konfigurer DC2.
    
> [!NOTE]
> Denne konfiguration kræver et betalt Azure-abonnement. 

Du kan bruge det resulterende miljø til at teste funktionerne og funktionaliteten i [Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise) med yderligere [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md) eller på egen hånd.

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf) for at få et visuelt kort til alle artiklerne i Microsoft 365 for enterprise Test Lab Guide-stakken.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: Konfigurer det virtuelle TestLab-netværk

Brug vejledningen i **fase 1** af den [simulerede grundlæggende konfiguration af virksomheden](simulated-ent-base-configuration-microsoft-365-enterprise.md) til at konfigurere DC1-, APP1- og CLIENT1-computerne i det virtuelle Azure-netværk med navnet TestLab.
  
Dette er din aktuelle konfiguration. 
  
![Den simulerede grundlæggende konfiguration af virksomheden i Azure.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: Opret det virtuelle XPrem-netværk

I denne fase skal du oprette og konfigurere det nye virtuelle XPrem-netværk og derefter forbinde det med det virtuelle TestLab-netværk med VNet-peering.
  
Start først en Azure PowerShell prompt på din lokale computer.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). 
  
Log på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Hent dit abonnementsnavn ved hjælp af denne kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt i anførselstegnene, herunder tegnene \< and > , med de korrekte navne.
  
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

Derefter skal du oprette VNet-peering-relationen mellem TestLab og XPrem VNets med disse kommandoer.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Dette er din aktuelle konfiguration. 
  
![Fase 2 af det simulerede virtuelle netværkstestmiljø på tværs af det lokale miljø med XPrem VNet og VNet-peering-relationen.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: Konfigurer DC2

I denne fase skal du oprette den virtuelle DC2-maskine på det virtuelle XPrem-netværk og derefter konfigurere den som en replikadomænecontroller.
  
Først skal du oprette en virtuel maskine til DC2. Kør disse kommandoer ved kommandoprompten Azure PowerShell på din lokale computer.
  
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

Opret derefter forbindelse til den nye virtuelle DC2-maskine fra [Azure Portal](https://portal.azure.com) ved hjælp af dens lokale administratorkontonavn og -adgangskode.
  
Konfigurer derefter en Windows Firewall-regel for at tillade trafik til grundlæggende forbindelsestest. Kør disse kommandoer fra en kommandoprompt på administratorniveau Windows PowerShell på DC2. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Kommandoen ping skal resultere i fire vellykkede svar fra IP-adressen 10.0.0.4. Dette er en test af trafik på tværs af VNet-peering-relationen. 
  
Tilføj derefter den ekstra datadisk som en ny diskenhed med drevbogstavet F: med denne kommando fra kommandoprompten Windows PowerShell på DC2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Konfigurer derefter DC2 som en replikadomænecontroller for det corp.contoso.com domæne. Kør disse kommandoer fra Windows PowerShell kommandoprompt på DC2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Bemærk, at du bliver bedt om at angive både adgangskoden til CORPUser1\\ og en DSRM-adgangskode (Directory Services Restore Mode) og genstarte DC2. 
  
Nu, hvor det virtuelle XPrem-netværk har sin egen DNS-server (DC2), skal du konfigurere det virtuelle XPrem-netværk til at bruge denne DNS-server. Kør disse kommandoer fra kommandoprompten Azure PowerShell på din lokale computer.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

Fra Azure Portal på din lokale computer skal du oprette forbindelse til DC1 med legitimationsoplysningerne for CORPUser1\\. Hvis du vil konfigurere CORP-domænet, så computere og brugere bruger deres lokale domænecontroller til godkendelse, skal du køre disse kommandoer fra en kommandoprompt på administratorniveau Windows PowerShell på DC1.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Dette er din aktuelle konfiguration. 
  
![Fase 3 af det simulerede virtuelle netværkstestmiljø på tværs af det lokale miljø med den virtuelle DC2-maskine i XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Dit simulerede Azure Hybrid Cloud-miljø er nu klar til test.
  
Du er nu klar til at eksperimentere med yderligere funktioner [i Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Næste trin

Udforsk disse ekstra sæt testlaboratorier:
  
- [Identitet](m365-enterprise-test-lab-guides.md#identity)
- [Administration af mobilenheder](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Beskyttelse af oplysninger](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)