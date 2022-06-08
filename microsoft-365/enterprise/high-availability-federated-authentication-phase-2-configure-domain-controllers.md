---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 2 Konfigurer domænecontrollere
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Oversigt: Konfigurer domænecontrollere og katalogsynkroniseringsserveren for din organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: 765ccb0aaf2611947f505b53b5689009dadd5148
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940684"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Godkendelse i organisationsnetværket med høj tilgængelighed fase 2: Konfigurer domænecontrollere

I denne fase af udrulningen af høj tilgængelighed til microsoft 365-organisationsnetværksgodkendelse i Azure-infrastrukturtjenester konfigurerer du to domænecontrollere og katalogsynkroniseringsserveren i det virtuelle Azure-netværk. Klientwebanmodninger om godkendelse kan derefter godkendes i det virtuelle Azure-netværk i stedet for at sende denne godkendelsestrafik på tværs af vpn-forbindelsen fra webstedet til webstedet til dit lokale netværk.
  
> [!NOTE]
> AD FS (Active Directory Federation Services) kan ikke bruge Azure Active Directory (Azure AD) som erstatning for AD DS-domænecontrollere (Active Directory Domain Services). 
  
Du skal fuldføre denne fase, før du går videre til [fase 3: Konfigurer AD FS-servere](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Se [Udrul organisationsnetværksgodkendelse med høj tilgængelighed til Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faserne.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Opret de virtuelle domænecontrollercomputere i Azure

Først skal du udfylde kolonnen **Med navnet på den virtuelle maskine** i Tabel M og ændre størrelsen på den virtuelle maskine efter behov i kolonnen **Minimumstørrelse** .
  
|**Element**|**Navn på virtuel maskine**|**Galleribillede**|**Lagertype**|**Mindste størrelse**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (første domænecontroller, f.eks. DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (anden domænecontroller, f.eks. DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (katalogsynkroniseringsserver, eksempel DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (første AD FS-server, f.eks. ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (anden AD FS-server, f.eks. ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (første webprogramproxyserver, eksempel WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![Linje.](../media/Common-Images/TableLine.png) (anden webprogramproxyserver, eksempel WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tabel M – Virtuelle maskiner til organisationsnetværksgodkendelse med høj tilgængelighed til Microsoft 365 i Azure**
  
Du kan se en komplet liste over størrelser på virtuelle [maskiner under Størrelser for virtuelle maskiner](/azure/virtual-machines/sizes).
  
Følgende Azure PowerShell-kommandoblok opretter de virtuelle maskiner til de to domænecontrollere. Angiv værdierne for variablerne, og fjern tegnene \< and > . Bemærk, at denne Azure PowerShell-kommandoblok bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V for dine indstillinger for virtuelle netværk
    
- Tabel S for dine undernet
    
- Tabel I for dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du har defineret tabellerne R, V, S, I og A i [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved Azure PowerShell-prompten eller i PowerShell ISE (Integrated Script Environment) på din lokale computer.
  
> [!TIP]
> Hvis du vil generere PowerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du bruge denne [Microsoft Excel-konfigurationsprojektmappe](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Da disse virtuelle maskiner er til et intranetprogram, tildeles de ikke en offentlig IP-adresse eller et DNS-domænenavn og vises på internettet. Det betyder dog også, at du ikke kan oprette forbindelse til dem fra Azure Portal. Indstillingen **Opret forbindelse** er ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til Fjernskrivebord eller et andet fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller intranet-DNS-navn.
  
## <a name="configure-the-first-domain-controller"></a>Konfigurer den første domænecontroller

Brug den valgte fjernskrivebord-klient, og opret en forbindelse til fjernskrivebord til den første virtuelle maskine til domænecontrolleren. Brug intranet-DNS- eller computernavnet og legitimationsoplysningerne for den lokale administratorkonto.
  
Føj derefter den ekstra datadisk til den første domænecontroller med denne kommando fra en Windows PowerShell-kommandoprompt **på den første virtuelle domænecontrollercomputer**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Test derefter den første domænecontrollers forbindelse til placeringer på organisationens netværk ved hjælp af kommandoen **ping** til at pinge navne og IP-adresser på ressourcer på organisationsnetværket.
  
Denne procedure sikrer, at DNS-navnefortsættelsen fungerer korrekt (at den virtuelle maskine er konfigureret korrekt med LOKALE DNS-servere), og at pakker kan sendes til og fra det virtuelle netværk på tværs af det lokale miljø. Hvis denne grundlæggende test mislykkes, skal du kontakte it-afdelingen for at foretage fejlfinding af problemer med DNS-navnefortsættelse og pakkelevering.
  
Kør derefter følgende kommandoer fra Windows PowerShell-kommandoprompten på den første domænecontroller:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Du bliver bedt om at angive legitimationsoplysningerne for en domæneadministratorkonto. Computeren genstartes.
  
## <a name="configure-the-second-domain-controller"></a>Konfigurer den anden domænecontroller

Brug den valgte fjernskrivebordsklient, og opret en forbindelse til fjernskrivebord til den anden virtuelle domænecontrollercomputer. Brug intranet-DNS- eller computernavnet og legitimationsoplysningerne for den lokale administratorkonto.
  
Derefter skal du føje den ekstra datadisk til den anden domænecontroller med denne kommando fra en Windows PowerShell-kommandoprompt **på den anden virtuelle domænecontrollercomputer**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Kør derefter følgende kommandoer:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

Du bliver bedt om at angive legitimationsoplysningerne for en domæneadministratorkonto. Computeren genstartes.
  
Derefter skal du opdatere DNS-serverne for dit virtuelle netværk, så Azure tildeler virtuelle maskiner IP-adresserne for de to nye domænecontrollere, der skal bruges som deres DNS-servere. Udfyld variablerne, og kør derefter disse kommandoer fra en Windows PowerShell-kommandoprompt på din lokale computer:
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

Bemærk, at vi genstarter de to domænecontrollere, så de ikke er konfigureret med DNS-serverne i det lokale miljø som DNS-servere. Da de begge er begge DNS-servere, blev de automatisk konfigureret med DNS-serverne i det lokale miljø som DNS-videresendere, da de blev overført til domænecontrollere.
  
Derefter skal vi oprette et Active Directory-replikeringswebsted for at sikre, at servere i det virtuelle Azure-netværk bruger de lokale domænecontrollere. Opret forbindelse til en af domænecontrollerne med en domæneadministratorkonto, og kør følgende kommandoer fra en Windows PowerShell-prompt på administratorniveau:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Konfigurer serveren til katalogsynkronisering

Brug den valgte fjernskrivebord-klient, og opret en forbindelse til fjernskrivebord til den virtuelle maskine til katalogsynkroniseringsserveren. Brug intranet-DNS- eller computernavnet og legitimationsoplysningerne for den lokale administratorkonto.
  
Derefter skal du slutte det til det relevante AD DS-domæne med disse kommandoer i Windows PowerShell-prompten.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Her er den konfiguration, der er resultatet af den vellykkede fuldførelse af denne fase med navne på pladsholdercomputere.
  
**Fase 2: Domænecontrollere og katalogsynkroniseringsserveren for din netværksgodkendelsesinfrastruktur med høj tilgængelighed i Azure**

![Fase 2 af den høje tilgængelighed af Microsoft 365-organisationsnetværkets godkendelsesinfrastruktur i Azure med domænecontrollere.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Næste trin

Brug [fase 3: Konfigurer AD FS-servere](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) for at fortsætte med at konfigurere denne arbejdsbelastning.
  
## <a name="see-also"></a>Se også

[Udrul organisationsnetværksgodkendelse med høj tilgængelighed til Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Organisationsnetværksidentitet for dit Microsoft 365-udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)