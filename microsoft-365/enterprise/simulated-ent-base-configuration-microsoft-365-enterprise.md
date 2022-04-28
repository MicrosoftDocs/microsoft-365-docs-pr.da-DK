---
title: Simuleret grundlæggende virksomhedskonfiguration for Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Brug denne testlaboratorievejledning til at oprette et simuleret virksomhedstestmiljø til Microsoft 365 for enterprise.
ms.openlocfilehash: 9c52bf657e91ceca9ef6e43f20a523a57a7b5042
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078707"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Den simulerede basiskonfiguration for virksomhed

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du opretter et forenklet miljø for Microsoft 365 for virksomheder, der omfatter:

- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement.
- Et forenklet organisationsintranet, der er forbundet til internettet, og som består af tre virtuelle maskiner på et virtuelt Azure-netværk (DC1, APP1 og CLIENT1).
 
![Den simulerede grundlæggende konfiguration af virksomheden.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Oprettelse af et forenklet testmiljø omfatter to faser:
- [Fase 1: Opret et simuleret intranet](#phase-1-create-a-simulated-intranet)
- [Fase 2: Opret dit Microsoft 365 E5-abonnement](#phase-2-create-your-microsoft-365-e5-subscription)

Du kan bruge det resulterende miljø til at teste funktionerne og funktionaliteten i [Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise) med yderligere [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md) eller på egen hånd.

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>Fase 1: Opret et simuleret intranet

I denne fase skal du oprette et simuleret intranet i Azure-infrastrukturtjenester, der omfatter en AD DS-domænecontroller (Active Directory-domæneservices), en programserver og en klientcomputer.

Du skal bruge disse computere i yderligere [Microsoft 365 til testlaboratorier i virksomheder til](m365-enterprise-test-lab-guides.md) at konfigurere og demonstrere hybrididentitet og andre funktioner.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Metode 1: Opret dit simulerede intranet med en Azure Resource Manager-skabelon

I denne metode skal du bruge en Azure Resource Manager-skabelon til at udarbejde det simulerede intranet. Azure Resource Manager-skabeloner indeholder alle instruktioner til oprettelse af Azure-netværksinfrastrukturen, de virtuelle maskiner og deres konfiguration.

Før du installerer skabelonen, skal du læse [skabelonens VIGTIGT-side](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) og have følgende oplysninger klar:

- Det offentlige DNS-domænenavn for dit testmiljø (testlab.\<*your public domain*>). Du skal angive dette navn i feltet **Domænenavn** på siden **Brugerdefineret installation** .
- Et DNS-mærkatpræfiks for URL-adresserne for de offentlige IP-adresser på dine virtuelle maskiner. Du skal angive dette navn i feltet **Dns-navnepræfiks** på siden **Brugerdefineret udrulning** .

Når du har læst instruktionerne, skal du vælge **Udrul på Azure** på [siden MED SKABELON VIGTIGT](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) for at komme i gang.

>[!Note]
>Det simulerede intranet, der oprettes af Azure Resource Manager-skabelonen, kræver et betalt Azure-abonnement.

Når skabelonen er fuldført, ser konfigurationen sådan ud:

![Det simulerede intranet i Azure-infrastrukturtjenester.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Metode 2: Opret det simulerede intranet med Azure PowerShell

I denne metode bruger du Windows PowerShell og modulet Azure PowerShell til at bygge netværksinfrastrukturen, de virtuelle maskiner og deres konfiguration.

Brug denne metode, hvis du vil have erfaring med at oprette elementer i Azure-infrastruktur ét trin ad gangen med PowerShell. Du kan derefter tilpasse PowerShell-kommandoblokke til din egen udrulning af andre virtuelle maskiner i Azure.

#### <a name="step-1-create-dc1"></a>Trin 1: Opret DC1

I dette trin skal du oprette et virtuelt Azure-netværk og tilføje DC1, en virtuel maskine, der er en domænecontroller for et AD DS-domæne.

Start først en Windows PowerShell kommandoprompt på din lokale computer.
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). 
  
Log på din Azure-konto med følgende kommando.
  
```powershell
Connect-AzAccount
```

Hent dit abonnementsnavn ved hjælp af følgende kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt inden for anførselstegnene, herunder vinkelparenteserne ("<" og ">"), med det korrekte navn.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Opret derefter en ny ressourcegruppe til dit simulerede virksomhedstestlaboratorium. Hvis du vil finde et entydigt navn på en ressourcegruppe, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Opret din nye ressourcegruppe med disse kommandoer. Erstat alt inden for anførselstegnene, herunder vinkelparenteser, med de korrekte navne.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Opret derefter det virtuelle TestLab-netværk, der skal hoste virksomhedens netværksundernet for det simulerede virksomhedsmiljø, og beskytte det med en netværkssikkerhedsgruppe. Udfyld navnet på din ressourcegruppe, og kør disse kommandoer ved PowerShell-kommandoprompten på din lokale computer.
  
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

Derefter skal du oprette den virtuelle DC1-maskine og konfigurere den som en domænecontroller for **testlab.**\<your public domain> AD DS-domæne og en DNS-server til de virtuelle maskiner i det virtuelle TestLab-netværk. Hvis dit offentlige domænenavn **f.eks. er <span>contoso.com</span>**, vil den virtuelle DC1-maskine være domænecontroller for domænet **<span>testlab.contoso.com</span>**.
  
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

Du bliver bedt om at angive et brugernavn og en adgangskode til den lokale administratorkonto på DC1. Brug en stærk adgangskode, og registrer både navn og adgangskode på en sikker placering.
  
Opret derefter forbindelse til den virtuelle DC1-maskine:
  
1. I [Azure Portal](https://portal.azure.com) skal du vælge **Ressourcegrupper** > <**_navnet på din nye ressourcegruppe_*_> > _* DC1** >  **Forbind**.
    
2. Vælg **Download RDP-fil** i den åbne rude. Åbn den DC1.rdp-fil, der downloades, og vælg derefter **Forbind**.
    
3. Angiv navnet på den lokale DC1-administratorkonto:
    
   - For Windows 7:
    
     I dialogboksen **Windows Sikkerhed** skal du vælge **Brug en anden konto**. Angiv **DC1local\\**< *administratorkontonavn* i **Brugernavn**>.
    
   - For Windows 8 eller Windows 10:
    
     I dialogboksen **Windows Sikkerhed** skal du vælge **Flere valgmuligheder** og derefter vælge **Brug en anden konto**. Angiv **DC1local\\**< *administratorkontonavn* i **Brugernavn**>.
    
4. Angiv adgangskoden til den lokale administratorkonto under **Adgangskode**, og vælg derefter **OK**.
    
5. Når du bliver bedt om det, skal du vælge **Ja**.
    
Tilføj derefter en ekstra datadisk som en ny diskenhed med drevbogstavet F: med denne kommando på administratorniveau Windows PowerShell kommandoprompt på DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Derefter skal du konfigurere DC1 som en domænecontroller og DNS-server for **testlab.**\<*your public domain*> Domæne. Angiv dit offentlige domænenavn, fjern vinkelparenteser, og kør derefter disse kommandoer på administratorniveau Windows PowerShell kommandoprompten på DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Du skal angive en adgangskode til administrator i fejlsikret tilstand. Store denne adgangskode på en sikker placering.
  
Bemærk, at det kan tage et par minutter at fuldføre disse kommandoer.
  
Når DC1 er genstartet, skal du genoprette forbindelsen til den virtuelle DC1-maskine.
  
1. I [Azure Portal](https://portal.azure.com) skal du vælge **Ressourcegrupper** > <*navnet på din ressourcegruppe*> > **DC1** >  **Forbind**.
    
2. Kør den DC1.rdp-fil, der downloades, og vælg derefter **Forbind**.
    
3. I **Windows Sikkerhed** skal du vælge **Brug en anden konto**. I **Brugernavn** skal du angive navnet på **TESTLABlocal\\**< *administratorkonto*>.
    
4. Angiv adgangskoden til den lokale administratorkonto i feltet **Adgangskode** , og vælg derefter **OK**.
    
5. Når du bliver bedt om det, skal du vælge **Ja**.
    
Opret derefter en brugerkonto i Active Directory, der skal bruges, når du logger på testLAB-domænemedlemscomputere. Kør denne kommando på administratorniveau Windows PowerShell kommandoprompt.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Bemærk, at du i denne kommando bliver bedt om at angive adgangskoden til user1-kontoen. Denne konto bruges til fjernskrivebordsforbindelser for alle TESTLAB-domænemedlemscomputere, så vælg en stærk adgangskode. Registrer bruger1-kontoens adgangskode, og gem den på en sikker placering.
  
Konfigurer derefter den nye User1-konto som domæne-, virksomheds- og skemaadministrator. Kør denne kommando på administratorniveau Windows PowerShell kommandoprompt.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

Luk Fjernskrivebord-sessionen med DC1, og opret derefter forbindelse igen ved hjælp af kontoen TESTLABUser1\\.
  
Derefter skal du køre denne kommando på administratorniveau Windows PowerShell kommandoprompt for at tillade trafik for pingværktøjet.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Din aktuelle konfiguration ser sådan ud:
  
![Trin 1 i den simulerede virksomhedsbasiskonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>Trin 2: Konfigurer APP1

I dette trin skal du oprette og konfigurere APP1, som er en programserver, der oprindeligt leverer web- og fildelingstjenester.

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

Opret derefter forbindelse til den virtuelle APP1-maskine ved hjælp af app1-kontoens lokale administratorkontonavn og -adgangskode, og åbn derefter en kommandoprompt af typen Windows PowerShell.
  
Hvis du vil kontrollere navneopløsningen og netværkskommunikationen mellem APP1 og DC1, skal du køre **ping dc1.testlab.**\<*your public domain name*> og kontrollér, at der er fire svar.
  
Slut derefter den virtuelle APP1-maskine til TESTLAB-domænet med disse kommandoer ved Windows PowerShell prompt.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bemærk, at når du har kørt kommandoen **Add-Computer** , skal du angive legitimationsoplysningerne for domænekontoen TESTLABUser1\\.
  
Når APP1 er genstartet, skal du oprette forbindelse til den ved hjælp af kontoen TESTLABUser1\\ og derefter åbne en kommandoprompt på administratorniveau Windows PowerShell.
  
Derefter skal du gøre APP1 til en webserver med denne kommando på administratorniveau Windows PowerShell kommandoprompt på APP1.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Opret derefter en delt mappe og en tekstfil i mappen på APP1 med disse PowerShell-kommandoer.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Din aktuelle konfiguration ser sådan ud:
  
![Trin 2 i den simulerede virksomhedsbasiskonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>Trin 3: Konfigurer CLIENT1

I dette trin skal du oprette og konfigurere CLIENT1, der fungerer som en typisk bærbar, tablet- eller stationær computer på intranettet.

> [!NOTE]  
> Følgende kommandosæt opretter CLIENT1, der kører Windows Server 2016 Datacenter, hvilket kan gøres for alle typer Azure-abonnementer. Hvis du har et Visual Studio-baseret Azure-abonnement, kan du oprette CLIENT1, der kører Windows 10 med [Azure Portal](https://portal.azure.com).
  
Hvis du vil oprette en Virtuel Azure-maskine til CLIENT1, skal du udfylde navnet på din ressourcegruppe og køre disse kommandoer ved kommandoprompten på din lokale computer.
  
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

Derefter skal du oprette forbindelse til den virtuelle klient1-maskine ved hjælp af klient1-kontoens navn og adgangskode og derefter åbne en kommandoprompt på administratorniveau Windows PowerShell.
  
Hvis du vil kontrollere navneopløsningen og netværkskommunikationen mellem CLIENT1 og DC1, skal du køre **ping dc1.testlab.**\<*your public domain name*> ved en Windows PowerShell kommandoprompt og kontrollere, at der er fire svar.
  
Slut derefter den virtuelle KLIENT1-maskine til TESTLAB-domænet med disse kommandoer ved Windows PowerShell prompt.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Bemærk, at du skal angive legitimationsoplysningerne for din TESTLABUser1-domænekonto\\, når du har kørt kommandoen **Add-Computer** .
  
Når CLIENT1 er genstartet, skal du oprette forbindelse til den ved hjælp af kontonavnet og adgangskoden for TESTLABUser1\\ og derefter åbne en kommandoprompt på administratorniveau Windows PowerShell.
  
Derefter skal du kontrollere, at du har adgang til web- og fildelingsressourcer på APP1 fra CLIENT1.
  
1. Vælg **Lokal server** i træruden i Serverstyring.
    
2. Under **Egenskaber for CLIENT1** skal du vælge **Til** ud for **Udvidet sikkerhedskonfiguration i IE**.
    
3. I **Internet Explorer Udvidet sikkerhedskonfiguration** skal du vælge **Fra** for **administratorer** og **brugere** og derefter vælge **OK**.
    
4. Vælg **Internet Explorer** på startskærmen, og vælg derefter **OK**.
    
5. Angiv **http <span>://</span>app1.testab**\<*your public domain name*>**/** i adresselinjen, og tryk derefter på **Enter**. Du får vist standardwebsiden Internet Information Services app1.
    
6. Vælg ikonet Stifinder på proceslinjen på skrivebordet.
    
7. Angiv **\\\\app1Files\\** på adresselinjen, og tryk derefter på **Enter**. Du får vist et mappevindue med indholdet af den delte mappe Filer.
    
8. Dobbeltklik på filen **Example.txt** i vinduet **Filer** med delt mappe. Du bør kunne se indholdet af filen Example.txt.
    
9. Luk vinduerne **example.txt – Notesblok** **og filer til** delte mapper.
    
Din aktuelle konfiguration ser sådan ud:
  
![Trin 3 i den simulerede virksomhedsbasiskonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Fase 2: Opret dit Microsoft 365 E5-abonnement

I denne fase opretter du et nyt Microsoft 365 E5 abonnement, der bruger en ny Azure AD-lejer, som er adskilt fra dit produktionsabonnement. Det kan du gøre på to måder:

- Brug et prøveabonnement på Microsoft 365 E5.

  Prøveabonnementet på Microsoft 365 E5 er 30 dage, hvilket nemt kan forlænges til 60 dage. Når prøveabonnementet udløber, skal du enten konvertere det til et betalt abonnement eller oprette et nyt prøveabonnement. Oprettelse af nye prøveabonnementer betyder, at du efterlader din konfiguration, hvilket kan omfatte komplekse scenarier.  

- Brug et separat produktionsabonnement på Microsoft 365 E5 med et lille antal licenser.

  Dette er en ekstra omkostning, men sikrer, at du har et arbejdsmiljø, der ikke udløber. i den kan du prøve funktioner, konfigurationer og scenarier. Du kan bruge det samme testmiljø på lang sigt til blåstempling, demonstration til peers og administration samt programudvikling og -test. Dette er den anbefalede metode.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Tilmeld dig et Office 365 E5 prøveabonnement

Fra Azure Portal skal du oprette forbindelse til CLIENT1 med kontoen CORP\User1.

Hvis du vil oprette et nyt Office 365 E5 prøveabonnement, skal du udføre vejledningen i [fase 1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) i den lette basiskonfigurationsvejledning til Test Lab.

Hvis du vil konfigurere dit nye Office 365 E5 prøveabonnement, skal du udføre vejledningen i [fase 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) i den lette basiskonfigurationsvejledning til Test Lab.

#### <a name="using-an-office-365-e5-test-environment"></a>Brug af et Office 365 E5 testmiljø

Hvis du kun har brug for et Office 365 testmiljø, behøver du ikke at læse resten af denne artikel.

Du kan finde flere Test Lab-vejledninger, der gælder for både Microsoft 365 og Office 365, [under Microsoft 365 til vejledninger til virksomhedstestlaboratorier](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Tilføj et Microsoft 365 E5 prøveabonnement

Hvis du vil tilføje et Microsoft 365 E5 prøveabonnement og konfigurere dine brugerkonti med licenser, skal du udføre vejledningen i [fase 3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) i den lette basiskonfigurationsvejledning til Test Lab.

  
## <a name="results"></a>Resultater

Dit testmiljø har nu:
  
- Microsoft 365 E5 prøveabonnement.
- Alle dine relevante brugerkonti er aktiveret til at bruge Microsoft 365 E5.
- Et simuleret og forenklet intranet.
    
Din endelige konfiguration ser sådan ud:
  
![Fase 2 af den simulerede virksomhedsbasiskonfiguration.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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