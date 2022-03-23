---
title: Godkendelse med høj tilgængelighed Fase 2 Konfigurer domænecontrollere i organisationsnetværket
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Oversigt: Konfigurer domænecontrollere og katalogsynkroniseringsserveren for din godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: 82199d6782e9c2497214d501da9e27ac0956edcd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594249"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 2: Konfigurer domænecontrollere

I denne fase med implementering af høj tilgængelighed til Microsoft 365 i organisationsnetværket i Azure-infrastrukturtjenester konfigurerer du to domænecontrollere og katalogsynkroniseringsserveren i det virtuelle Azure-netværk. Klientwebanmodninger om godkendelse kan derefter godkendes i det virtuelle Azure-netværk i stedet for at sende denne godkendelsestrafik på tværs af websteds-VPN-forbindelsen til dit lokale netværk.
  
> [!NOTE]
> Active Directory Federation Services (AD FS) kan ikke bruge Azure Active Directory (Azure AD) som erstatning for Active Directory-domæneservices (AD DS)-domænecontrollere. 
  
Du skal fuldføre denne fase, før du går videre til [Fase 3: Konfigurer AD FS-servere](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Se [Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faser.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Opret virtuelle domænecontrollerens virtuelle maskiner i Azure

Først skal du udfylde kolonnen Med navnet på den **virtuelle** maskine i Tabel M og ændre størrelser på virtuel maskine efter behov i **kolonnen Mindste** størrelse.
  
|**Element**|**Navn på virtuel maskine**|**Galleribillede**|**Storage type**|**Minimumsstørrelse**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![.](../media/Common-Images/TableLine.png) (første domænecontroller, eksempel DC1)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![.](../media/Common-Images/TableLine.png) (anden domænecontroller, eksempel DC2)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![.](../media/Common-Images/TableLine.png) (katalogsynkroniseringsserver, eksempel DS1)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![.](../media/Common-Images/TableLine.png) (første AD FS-server, eksempel ADFS1)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![.](../media/Common-Images/TableLine.png) (anden AD FS-server, eksempel ADFS2)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![.](../media/Common-Images/TableLine.png) (første webprogramproxyserver, eksempel WEB1)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![.](../media/Common-Images/TableLine.png) (proxyserver for andet webprogram, eksempel WEB2)  <br/> |Windows Server 2016-datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **Tabel M – Virtuelle maskiner til godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Azure**
  
Du kan se en komplet liste over størrelser på virtuelle maskiner [under Størrelser for virtuelle maskiner](/azure/virtual-machines/virtual-machines-windows-sizes).
  
Følgende kommandoblok Azure PowerShell de virtuelle maskiner for de to domænecontrollere. Angiv værdierne for variablerne, og fjern tegnene \< and > . Bemærk, at Azure PowerShell bruger værdier fra følgende tabeller:
  
- Tabel M til dine virtuelle maskiner
    
- Tabel R for dine ressourcegrupper
    
- Tabel V til indstillingerne for virtuelt netværk
    
- Tabel S til dine undernet
    
- Tabel I til dine statiske IP-adresser
    
- Tabel A for dine tilgængelighedssæt
    
Husk, at du definerede Tabeller R, V, S, I og A i [Fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell](/powershell/azure/get-started-azureps). 
  
Når du har angivet alle de korrekte værdier, skal du køre den resulterende blok ved Azure PowerShell-prompten eller i PowerShell Integrated Script Environment (ISE) på din lokale computer.
  
> [!TIP]
> Hvis du vil generere powerShell-kommandoblokke, der er klar til kørsel, baseret på dine brugerdefinerede indstillinger, skal du [Microsoft Excel projektmappen til konfiguration](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx). 

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
> Da disse virtuelle computere er til et intranetprogram, er de ikke tildelt en offentlig IP-adresse eller et DNS-domænenavnenavn, der vises på internettet. Men det betyder også, at du ikke kan oprette forbindelse til dem fra Azure-portalen. Indstillingen **Forbind** ikke tilgængelig, når du får vist egenskaberne for den virtuelle maskine. Brug tilbehøret Forbindelse til fjernskrivebord eller et andet fjernskrivebord-værktøj til at oprette forbindelse til den virtuelle maskine ved hjælp af dens private IP-adresse eller DNS-navn på intranettet.
  
## <a name="configure-the-first-domain-controller"></a>Konfigurere den første domænecontroller

Brug en klient til fjernskrivebord efter eget valg, og opret en forbindelse til fjernskrivebord til den første virtuelle domænecontroller. Brug dets intranet-DNS eller computernavn samt legitimationsoplysningerne for den lokale administratorkonto.
  
Derefter skal du føje den ekstra datadisk til den første domænecontroller med denne kommando fra en Windows PowerShell **kommandoprompt på den første virtuelle domænecontrollers virtuelle maskine**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Dernæst skal du teste den første domænecontrollers forbindelse til placeringer på organisationens netværk ved hjælp af **kommandoen ping til at pinge** navne og IP-adresser på ressourcer på organisationens netværk.
  
Denne procedure sikrer, at DNS-navneoversætning fungerer korrekt (at den virtuelle maskine er korrekt konfigureret med lokale DNS-servere), og at pakker kan sendes til og fra det virtuelle netværk på tværs af lokale netværk. Hvis denne grundlæggende test mislykkes, skal du kontakte din it-afdeling for at foretage fejlfinding af DNS-navneopløsningen og pakkeleveringsproblemer.
  
Derefter skal du køre Windows PowerShell kommandoprompt på den første domænecontroller:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

Du bliver bedt om at angive legitimationsoplysningerne for en domæneadministratorkonto. Computeren genstartes.
  
## <a name="configure-the-second-domain-controller"></a>Konfigurere den anden domænecontroller

Brug en klient til fjernskrivebord efter eget valg, og opret en forbindelse til fjernskrivebord til den anden virtuelle domænecontroller. Brug dets intranet-DNS eller computernavn samt legitimationsoplysningerne for den lokale administratorkonto.
  
Derefter skal du føje den ekstra datadisk til den anden domænecontroller med denne kommando fra en Windows PowerShell-kommandoprompt på den anden virtuelle **domænecontrollers virtuelle maskine**:
  
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
  
Derefter skal du opdatere DNS-serverne for dit virtuelle netværk, så Azure tildeler virtuelle maskiner IP-adresserne på de to nye domænecontrollere til at bruge dem som deres DNS-servere. Udfyld variablerne, og kør derefter disse kommandoer fra en Windows PowerShell kommandoprompt på din lokale computer:
  
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

Bemærk, at vi genstarter de to domænecontrollere, så de ikke er konfigureret med de lokale DNS-servere som DNS-servere. Da de begge er selve DNS-servere, blev de automatisk konfigureret med de lokale DNS-servere som DNS-videresendere, da de blev videresendt til domænecontrollere.
  
Dernæst skal vi oprette et Active Directory-replikeringswebsted for at sikre, at servere i det virtuelle Azure-netværk bruger de lokale domænecontrollere. Forbind domænecontroller med en domæneadministratorkonto, og kør følgende kommandoer fra en administratorniveau Windows PowerShell prompt:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>Konfigurere katalogsynkroniseringsserveren

Brug en klient til fjernskrivebord efter eget valg, og opret en fjernskrivebord-forbindelse til den virtuelle computer til katalogsynkroniseringsserveren. Brug dets intranet-DNS eller computernavn samt legitimationsoplysningerne for den lokale administratorkonto.
  
Derefter skal du slutte den til det AD DS domæne med disse kommandoer ved Windows PowerShell prompten.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Her er konfigurationen, der fremkommer, når denne fase er fuldført, med pladsholdercomputernavne.
  
**Fase 2: Domænecontrollere og katalogsynkroniseringsserveren for din godkendelsesinfrastruktur i organisationsnetværket med høj tilgængelighed i Azure**

![Fase 2 af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure med domænecontrollere.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Næste trin

Brug [Fase 3: Konfigurer AD FS-servere for at](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) fortsætte med at konfigurere denne arbejdsbyrde.
  
## <a name="see-also"></a>Se også

[Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identitet i organisationsnetværk for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 og arkitekturcenter](../solutions/index.yml)