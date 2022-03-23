---
title: Simuleret virksomhedsbasekonfiguration til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Brug denne Test Lab-vejledning til at oprette et simuleret virksomhedstestmiljø til Microsoft 365 til virksomheder.
ms.openlocfilehash: d335ed074adc6abe8bc1dabf58392d5b9051ccc6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587668"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Den simulerede virksomhedsbasekonfiguration

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du opretter et forenklet miljø til Microsoft 365 til virksomheder, der indeholder:

- En Microsoft 365 E5 prøveversion eller et betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af tre virtuelle maskiner på et virtuelt Azure-netværk (DC1, APP1 og CLIENT1).
 
![Den simulerede virksomhedsbasekonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Oprettelse af et forenklet testmiljø indebærer to faser:
- [Fase 1: Opret et simuleret intranet](#phase-1-create-a-simulated-intranet)
- [Fase 2: Opret dit Microsoft 365 E5 abonnement](#phase-2-create-your-microsoft-365-e5-subscription)

Du kan bruge det resulterende miljø til at teste funktionerne og funktionaliteten [i Microsoft 365 til](https://www.microsoft.com/microsoft-365/enterprise) virksomheder med yderligere [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md) eller på egen hånd.

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>Fase 1: Opret et simuleret intranet

I denne fase skal du opbygge et simuleret intranet i Azure-infrastrukturtjenester, der omfatter en Active Directory-domæneservices (AD DS)-domænecontroller, en programserver og en klientcomputer.

Du skal bruge disse computere i yderligere Microsoft 365 [til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md) til at konfigurere og demonstrere hybrididentitet og andre funktioner.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Metode 1: Opbyg dit simulerede intranet med en Azure Resource Manager-skabelon

Med denne metode bruger du en Azure Resource Manager-skabelon til at opbygge det simulerede intranet. Azure Resource Manager-skabeloner indeholder alle instruktioner til oprettelse af Azure-netværksinfrastruktur, de virtuelle maskiner og deres konfiguration.

Før du installerer skabelonen, skal du læse [skabelonens README-side og](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) have følgende oplysninger klar:

- Det offentlige DNS-domænenavn for testmiljøet (testlab.\<*your public domain*>). Du skal angive dette navn i feltet **Domænenavn på** siden **Brugerdefineret** installation.
- Et præfiks for DNS-navne for URL-adresserne på dine virtuelle computeres offentlige IP-adresser. Du skal angive denne etiket i feltet **Dns Label Prefix på** **installationssiden Brugerdefineret** .

Når du har læst vejledningen igennem, skal du vælge **Deploy to Azure** på skabelonens [README-side for](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) at komme i gang.

>[!Note]
>Det simulerede intranet, der er bygget af Azure Resource Manager-skabelonen, kræver et betalt Azure-abonnement.

Når skabelonen er færdig, ser konfigurationen sådan ud:

![Det simulerede intranet i Azure-infrastrukturtjenester.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Metode 2: Opbyg dit simulerede intranet Azure PowerShell

På denne metode bruger du Windows PowerShell og Azure PowerShell til at opbygge netværksinfrastrukturen, de virtuelle maskiner og deres konfiguration.

Brug denne metode, hvis du vil have erfaring med at oprette elementer i Azure-infrastruktur ét trin ad gangen med PowerShell. Du kan derefter tilpasse PowerShell-kommandoblokke til din egen installation af andre virtuelle maskiner i Azure.

#### <a name="step-1-create-dc1"></a>Trin 1: Opret DC1

I dette trin skal du oprette et virtuelt Azure-netværk og tilføje DC1, en virtuel maskine, der er domænecontroller for AD DS domæne.

Start først en Windows PowerShell kommandoprompt på din lokale computer.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). 
  
Log på din Azure-konto med følgende kommando.
  
```powershell
Connect-AzAccount
```

Få dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt mellem anførselstegnene, herunder vinkelparenteserne ("<" og ">") med det korrekte navn.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Dernæst skal du oprette en ny ressourcegruppe til dit simulerede testlaboratorium for virksomheder. Hvis du vil finde et entydigt ressourcegruppenavn, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Opret din nye ressourcegruppe med disse kommandoer. Erstat alt mellem anførselstegnene, herunder vinkelparenteserne, med de korrekte navne.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Dernæst skal du oprette det virtuelle TestLab-netværk, der er vært for virksomhedens netværksundernet af det simulerede virksomhedsmiljø og beskytte det med en netværkssikkerhedsgruppe. Udfyld navnet på din ressourcegruppe, og kør disse kommandoer ved PowerShell-kommandoprompten på din lokale computer.
  
```powershell
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Derefter skal du oprette den virtuelle DC1-maskine og konfigurere den som en domænecontroller til **testlab'en.**\<your public domain> AD DS domæne og en DNS-server til de virtuelle computere på TestLab-det virtuelle netværk. Hvis dit offentlige domænenavn f.eks. er **<span>contoso.com</span>**, vil DC1-virtuel maskine være en domænecontroller for **<span>testlab.contoso.com</span>** domæne.
  
Hvis du vil oprette en virtuel Azure-maskine til DC1, skal du udfylde navnet på din ressourcegruppe og køre disse kommandoer ved PowerShell-kommandoprompten på din lokale computer.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Du bliver bedt om at angive et brugernavn og en adgangskode til den lokale administratorkonto på DC1. Brug en stærk adgangskode, og optag både navn og adgangskode på et sikkert sted.
  
Opret derefter forbindelse til den virtuelle DC1-maskine:
  
1. Vælg [Ressourcegrupper på](https://portal.azure.com) **Azure-portalen > <** **_navnet på din nye ressourcegruppe_*_> > _* DC1** >  **Forbind**.
    
2. Vælg Download **RDP-fil i den åbne rude**. Åbn den DC1.rdp-fil, der downloades, og vælg **Forbind**.
    
3. Angiv navnet på den lokale DC1-administratorkonto:
    
   - For Windows 7:
    
     I dialogboksen **Windows Sikkerhed** skal du vælge Brug **en anden konto**. Angiv **navnet på** *DC1local-administratorkontoen* **\\**< i>.
    
   - For Windows 8 eller Windows 10:
    
     I dialogboksen **Windows Sikkerhed** skal du vælge **Flere valgmuligheder** og derefter vælge **Brug en anden konto**. Angiv **navnet på** *DC1local-administratorkontoen* **\\**< i>.
    
4. Skriv **adgangskoden** til den lokale administratorkonto i Adgangskode, og vælg derefter **OK**.
    
5. Vælg Ja, når du bliver **bedt om det**.
    
Derefter skal du tilføje en ekstra datadisk som en ny lydstyrke med drevbogstavet F: med denne kommando på administratorniveau Windows PowerShell kommandoprompt på DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Dernæst skal du konfigurere DC1 som domænecontroller og DNS-server for **testlaboratoren.**\<*your public domain*> domæne. Angiv dit offentlige domænenavn, fjern vinkelparenteserne, og kør derefter disse kommandoer på administratorniveau Windows PowerShell kommandoprompt på DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Du skal angive en administratoradgangskode til fejlsikret tilstand. Store adgangskoden på et sikkert sted.
  
Bemærk, at det kan tage et par minutter at udføre disse kommandoer.
  
Når DC1 er genstartet, skal du igen oprette forbindelse til den virtuelle DC1-maskine.
  
1. Vælg [Ressourcegrupper på](https://portal.azure.com) **Azure-portalen > <** *navnet på din ressourcegruppe*> > **DC1** >  **Forbind**.
    
2. Kør den DC1.rdp-fil, der downloades, og vælg **Forbind**.
    
3. I **Windows Sikkerhed skal** du vælge **Brug en anden konto**. I **Brugernavn skal** du indtaste **navnet på TESTLABlocal-administratorkonto\\**<>.
    
4. Skriv adgangskoden **til** den lokale administratorkonto i feltet Adgangskode, og vælg derefter **OK**.
    
5. Vælg Ja, når du bliver **bedt om det**.
    
Dernæst skal du oprette en brugerkonto i Active Directory, der skal bruges, når du logger på TESTLAB-domænemedlemscomputere. Kør denne kommando på et administratorniveau Windows PowerShell kommandoprompten.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Bemærk, at denne kommando beder dig om at angive adgangskoden til brugerkontoen Bruger1. Denne konto skal bruges til fjernskrivebordsforbindelser til alle testLAB-domænemedlemscomputere, så vælg en stærk adgangskode. Optag brugerens1-kontoadgangskode, og gem den et sikkert sted.
  
Derefter skal du konfigurere den nye Bruger1-konto som domæne-, virksomheds- og skemaadministrator. Kør denne kommando på administratorniveau for at Windows PowerShell kommandoprompten.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

Luk Sessionen af Fjernskrivebord med DC1, og opret derefter forbindelse igen ved hjælp af TESTLABUser1-kontoen\\.
  
For derefter at tillade trafik til værktøjet Ping skal du køre denne kommando på et administratorniveau og Windows PowerShell kommandoprompt.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Din aktuelle konfiguration ser sådan ud:
  
![Trin 1 af den simulerede virksomhedsbasekonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>Trin 2: Konfigurer APP1

I dette trin skal du oprette og konfigurere APP1, som er en programserver, der indledningsvist leverer web- og fildelingstjenester.

Hvis du vil oprette en Azure Virtual Machine til APP1, skal du udfylde navnet på din ressourcegruppe og køre disse kommandoer ved kommandoprompten på din lokale computer.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Opret derefter forbindelse til den virtuelle APP1-maskine ved hjælp af det lokale APP1-administratorkontonavn og adgangskode, og åbn Windows PowerShell kommandoprompt.
  
Kør **ping dc1.testlab for at kontrollere navneopløsning og netværkskommunikation mellem APP1 og DC1.**\<*your public domain name*> og bekræft, at der er fire svar.
  
Dernæst skal du slutte app1-den virtuelle maskine til testlab-domænet med disse kommandoer ved Windows PowerShell prompten.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bemærk, at når du har kørt **kommandoen Tilføj computer** , skal du angive legitimationsoplysningerne til domænekontoen TESTLABUser1\\.
  
Når APP1 er genstartet, skal du oprette forbindelse til den ved hjælp af kontoen TESTLABUser1\\ og derefter åbne en Windows PowerShell på administratorniveau.
  
Dernæst skal du gøre APP1 til en webserver med denne kommando på administratorniveau Windows PowerShell kommandoprompt på APP1.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Dernæst skal du oprette en delt mappe og en tekstfil i mappen på APP1 med disse PowerShell-kommandoer.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Din aktuelle konfiguration ser sådan ud:
  
![Trin 2 af den simulerede virksomhedsbasekonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>Trin 3: Konfigurer KLIENT1

I dette trin skal du oprette og konfigurere CLIENT1, der fungerer som en typisk bærbar computer, tablet eller stationær computer på intranettet.

> [!NOTE]  
> Følgende kommandosæt opretter CLIENT1, der Windows Server 2016-datacenter, som kan udføres for alle typer Azure-abonnementer. Hvis du har et Visual Studio Azure-abonnement, kan du oprette CLIENT1, der Windows 10 med [Azure-portalen](https://portal.azure.com).
  
Hvis du vil oprette en Azure Virtual Machine til KLIENT1, skal du udfylde navnet på din ressourcegruppe og køre disse kommandoer ved kommandoprompten på din lokale computer.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Opret derefter forbindelse til den virtuelle klient1-maskine ved hjælp af den lokale KLIENT1-administratorkontos navn og adgangskode, og åbn derefter en Windows PowerShell-kommandoprompt.
  
Kør **ping dc1.testlab for at kontrollere navneopløsning og netværkskommunikation mellem CLIENT1 og DC1.**\<*your public domain name*> ved en Windows PowerShell, og bekræft, at der er fire svar.
  
Dernæst skal du slutte den virtuelle maskine CLIENT1 til testlab-domænet med disse kommandoer ved Windows PowerShell prompten.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bemærk, at du skal angive legitimationsoplysningerne for dit TESTLABUser1-domæne\\ efter at have kørt **kommandoen Tilføj computer** .
  
Når KLIENT1 er genstartet, skal du oprette forbindelse til den ved hjælp af testlabUser1-kontonavn\\ og adgangskode og derefter åbne en Windows PowerShell på administratorniveau.
  
Dernæst skal du kontrollere, at du kan få adgang til web- og fildelingsressourcer på APP1 fra KLIENT1.
  
1. Vælg Lokal server i træruden i **Serverstyring**.
    
2. I **Egenskaber for KLIENT1 skal** du vælge **Til** ud for **Udvidet sikkerhedskonfiguration i IE**.
    
3. I **Internet Explorers udvidede sikkerhedskonfiguration** skal **du vælge** **Fra** for administratorer **og brugere** og derefter vælge **OK**.
    
4. Vælg **Internet Explorer** på startskærmen, og vælg derefter **OK**.
    
5. Skriv **http <span>://</span>app1.testab**\<*your public domain name*>**/** på adresselinjen, og tryk derefter på **Enter**. Du bør få vist standardwebstedet Internet Information Services for APP1.
    
6. Vælg ikonet Stifinder på proceslinjen på skrivebordet.
    
7. Skriv **app1Files på\\\\ adresselinjen\\**, og tryk derefter på **Enter**. Du bør få vist et mappevindue med indholdet af den delte mappe Filer.
    
8. I vinduet **filer** i den delte mappe skal du dobbeltklikke **påExample.txt** fil. Du bør kunne se indholdet af Example.txt fil.
    
9. Lukexample.txt **- Notesblok og** vinduerne **med** den delte mappe Filer.
    
Din aktuelle konfiguration ser sådan ud:
  
![Trin 3 af den simulerede virksomhedsbasekonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Fase 2: Opret dit Microsoft 365 E5 abonnement

I denne fase opretter du et nyt Microsoft 365 E5, der bruger en ny Azure AD-lejer, som er separat fra dit produktionsabonnement. Det kan du gøre på to måder:

- Brug et prøveabonnement på Microsoft 365 E5.

  Abonnementet Microsoft 365 E5 en prøveversion er 30 dage, som nemt kan forlænges til 60 dage. Når prøveabonnementet udløber, skal du enten konvertere det til et betalt abonnement eller oprette et nyt prøveabonnement. Når du opretter nye prøveabonnementer, forlader du konfigurationen, hvilket kan omfatte komplekse scenarier.  

- Brug et separat produktionsabonnement på Microsoft 365 E5 med et lille antal licenser.

  Dette er en ekstra omkostning, men sikrer, at du har et fungerende testmiljø, der ikke udløber; I den kan du prøve funktioner, konfigurationer og scenarier. Du kan bruge det samme testmiljø på lang sigt for koncepttests, demonstration til peers og administration samt programudvikling og test. Dette er den anbefalede metode.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Tilmeld dig et Office 365 E5-prøveabonnement

Fra Azure-portalen skal du oprette forbindelse til CLIENT1 med CORP\User1-kontoen.

For at oprette et Office 365 E5-prøveabonnement skal du udføre instruktionerne i [Fase 1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) af den lette basiskonfiguration Test Lab Guide.

For at konfigurere dit Office 365 E5-prøveabonnement skal du udføre instruktionerne i [Fase 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) af den lette basiskonfiguration Test Lab Guide.

#### <a name="using-an-office-365-e5-test-environment"></a>Brug af Office 365 E5 testmiljø

Hvis du kun har brug for Office 365 testmiljø, behøver du ikke at læse resten af denne artikel.

Du kan finde flere Test Lab-vejledninger, der gælder for både Microsoft 365 og Office 365, [Microsoft 365 for Enterprise Test Lab Guides](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Tilføj et Microsoft 365 E5-prøveabonnement

Hvis du vil tilføje Microsoft 365 E5-prøveabonnement og konfigurere dine brugerkonti med licenser, skal du udføre instruktionerne i [Fase 3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) af den lette basiskonfiguration Test Lab Guide.

  
## <a name="results"></a>Resultater

Dit testmiljø har nu:
  
- Microsoft 365 E5-prøveabonnement.
- Alle dine relevante brugerkonti er aktiveret til at bruge Microsoft 365 E5.
- En simuleret og forenklet intranet.
    
Din endelige konfiguration ser sådan ud:
  
![Fase 2 af den simulerede virksomhedsbasekonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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