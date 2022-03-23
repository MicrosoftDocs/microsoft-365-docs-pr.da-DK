---
title: Identitet i organisationsnetværk for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Oversigt: Konfigurer federated authentication for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 6553590c06df4caf099c7b4db47d253bd37b39fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591395"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Identitet i organisationsnetværk for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Microsoft 365 understøtter identitet i organisationsnetværket. Det betyder, at i stedet for at udføre valideringen af selve legitimationsoplysningerne, refererer Microsoft 365 den forbindelsesbruger til en organisationsnetværksgodkendelsesserver, som Microsoft 365 tillid til. Hvis brugerens legitimationsoplysninger er korrekte, udsteder den organisationsnetværksgodkendelsesserveren et sikkerhedstoken, som klienten derefter sender til Microsoft 365 som godkendelsesbevis. Identitet i organisationsnetværket gør det muligt at aflæse og skalere godkendelse til et Microsoft 365-abonnement og avancerede godkendelses- og sikkerhedsscenarier.
  
I denne artikel beskrives det, hvordan du konfigurerer federated authentication for Microsoft 365 testmiljø, hvilket resulterer i følgende:

![Godkendelse i organisationsnetværket for Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5-prøve- eller produktionsabonnement.
    
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af fem virtuelle computere på et undernet af et virtuelt Azure-netværk (DC1, APP1, CLIENT1, ADFS1 og PROXY1). Azure AD Forbind app1 for at synkronisere listen over konti i domænet Active Directory-domæneservices at Microsoft 365. PROXY1 modtager anmodninger om indgående godkendelse. ADFS1 validerer legitimationsoplysninger med DC1 og udsteder sikkerhedstokens.
    
Konfiguration af dette testmiljø omfatter fem faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Opret AD FS-serveren](#phase-2-create-the-ad-fs-server)
- [Fase 3: Opret webproxyserveren](#phase-3-create-the-web-proxy-server)
- [Fase 4: Opret et selv signeret certifikat, og konfigurer ADFS1 og PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Fase 5: Konfigurer Microsoft 365 for identitet i organisationsnetværk](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Du kan ikke konfigurere dette testmiljø med et Azure Trial-abonnement.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i synkronisering [af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Den resulterende konfiguration ser sådan ud:
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveversion eller betalte abonnementer.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk. Azure AD Forbind kører på APP1 for med jævne mellemrum at synkronisere TESTLAB Active Directory-domæneservices-domænet (AD DS) med Azure AD-lejeren for dine Microsoft 365-abonnementer.

## <a name="phase-2-create-the-ad-fs-server"></a>Fase 2: Opret AD FS-serveren

En AD FS-server giver godkendelse i organisationsnetværket mellem Microsoft 365 og kontiene i det corp.contoso.com domæne, der er hostet på DC1.
  
Hvis du vil oprette en virtuel Azure-maskine til ADFS1, skal du udfylde navnet på dit abonnement og ressourcegruppen og Azure-placeringen for din grundlæggende konfiguration og derefter køre disse kommandoer ved Azure PowerShell-kommandoprompten på din lokale computer.
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Brug derefter [Azure-portalen](https://portal.azure.com) til at oprette forbindelse til den virtuelle ADFS1-maskine ved hjælp af det lokale ADFS1-administratorkontonavn og adgangskode, og åbn derefter en Windows PowerShell kommandoprompt.
  
Du kan kontrollere navneopløsningen og netværkskommunikationen mellem ADFS1 og DC1 ved at køre **kommandoen ping dc1.corp.contoso.com** og kontrollere, at der er fire svar.
  
Derefter skal du slutte den virtuelle ADFS1-maskine til CORP-domænet med disse kommandoer ved Windows PowerShell på ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Den resulterende konfiguration ser sådan ud:
  
![AD FS-serveren føjet til DirSync til Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Fase 3: Opret webproxyserveren

PROXY1 leverer proxying af godkendelsesmeddelelser mellem brugere, der forsøger at godkende, og ADFS1.
  
Hvis du vil oprette en virtuel Azure-maskine til PROXY1, skal du udfylde navnet på din ressourcegruppe og Azure-placering og derefter køre disse kommandoer ved Azure PowerShell-kommandoprompten på din lokale computer.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1 tildeles en statisk offentlig IP-adresse, fordi du skal oprette en offentlig DNS-post, der peger på den, og den må ikke ændres, når du genstarter den virtuelle PROXY1-computer.
  
Dernæst skal du føje en regel til netværkssikkerhedsgruppen for CorpNet-undernettet for at tillade uopfordret indgående trafik fra internettet til PROXY1's private IP-adresse og TCP-port 443. Kør disse kommandoer ved Azure PowerShell kommandoprompten på din lokale computer.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Brug derefter [Azure-portalen](https://portal.azure.com) til at oprette forbindelse til den virtuelle PROXY1-maskine ved hjælp af den lokale PROXY1-administratorkontos navn og adgangskode, og åbn derefter en Windows PowerShell-kommandoprompt på PROXY1.
  
Du kan kontrollere navneopløsningen og netværkskommunikationen mellem PROXY1 og DC1 ved at køre **kommandoen ping dc1.corp.contoso.com** og kontrollere, at der er fire svar.
  
Dernæst skal du slutte den virtuelle maskine PROXY1 til CORP-domænet med disse kommandoer ved Windows PowerShell på PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Vis den offentlige IP-adresse for PROXY1 med disse Azure PowerShell kommandoer på din lokale computer.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Dernæst skal du arbejde sammen med din offentlige DNS-udbyder og oprette en ny offentlig DNS A-post **til fs.testlab.**\<*your DNS domain name*> , der løses til den IP-adresse, der vises af **kommandoen Write-Host** . **FS.testlab.**\<*your DNS domain name*> kaldes herefter for  *sammenslutningstjenesten FQDN*.
  
Brug derefter [Azure-portalen](https://portal.azure.com) til at oprette forbindelse til den virtuelle DC1-maskine ved hjælp af legitimationsoplysningerne for CORPUser1\\, og kør derefter følgende kommandoer på administratorniveau Windows PowerShell kommandoprompten:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Disse kommandoer opretter en intern DNS A-post, så virtuelle maskiner på Azures virtuelle netværk kan løse den interne sammenslutningstjeneste FQDN til ADFS1's private IP-adresse.
  
Den resulterende konfiguration ser sådan ud:
  
![Webprogrammets proxyserver føjet til DirSync til Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Fase 4: Opret et selv signeret certifikat, og konfigurer ADFS1 og PROXY1

I denne fase skal du oprette et selv signeret digitalt certifikat til din sammenslutningstjeneste FQDN og konfigurere ADFS1 og PROXY1 som en AD FS-farm.
  
Først skal du bruge [Azure-portalen](https://portal.azure.com) til at oprette forbindelse til den virtuelle DC1-maskine ved hjælp af legitimationsoplysningerne for CORPUser1\\ og derefter åbne en Windows PowerShell på administratorniveau.
  
Derefter skal du oprette en AD FS-tjenestekonto med denne kommando Windows PowerShell kommandoprompten på DC1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Bemærk, at denne kommando beder dig om at angive adgangskoden til kontoen. Vælg en stærk adgangskode, og optag den på en sikret placering. Du skal bruge den til denne fase og til fase 5.
  
Brug [Azure-portalen til](https://portal.azure.com) at oprette forbindelse til den virtuelle ADFS1-maskine ved hjælp af legitimationsoplysningerne fra CORPUser1\\. Åbn en Windows PowerShell-kommandoprompt på ADFS1 på administratorniveau, udfyld din sammenslutningstjenesteS FQDN, og kør derefter disse kommandoer for at oprette et selv signeret certifikat:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Derefter skal du bruge disse trin til at gemme det nye selv signerede certifikat som en fil.
  
1. Vælg **Start**, indtast **mmc.exe**, og tryk derefter på **Enter**.
    
2. Vælg **FileAdd** > **/Remove Snap-in**.
    
3. I **Tilføj eller fjern snap-ins** skal du dobbeltklikke  på Certifikater på listen over tilgængelige snap-ins, vælge **Computerkonto** og derefter vælge **Næste**.
    
4. Vælg **Udfør i** Vælg **computer**, og vælg derefter **OK**.
    
5. I træruden skal du **åbne Certifikater (lokal computer) > Personal > Certifikater**.
    
6. Vælg og hold (eller højreklik) på certifikatet med din sammenslutningstjeneste FQDN, markér **Alle opgaver**, og vælg derefter **Eksportér**.
    
7. På **velkomstsiden** skal du vælge **Næste**.
    
8. På siden **Eksportér privat** nøgle skal du **vælge Ja** og derefter vælge **Næste**.
    
9. På siden **Eksportér filformat** skal du vælge **Eksportér alle udvidede egenskaber** og derefter vælge **Næste**.
    
10. På siden **Sikkerhed** skal du vælge **Adgangskode og** angive en adgangskode i **Adgangskode og** **Bekræft adgangskode.**
    
11. På siden **Fil, der skal eksporteres** skal du vælge **Gennemse**.
    
12. Gå til **mappen C:\\Certifikater** , angiv **SSL** i **filnavn**, og vælg derefter **Gem.**
    
13. På siden **Fil, der skal eksporteres** skal du vælge **Næste**.
    
14. På siden **Fuldførelse af guiden Certifikateksport** skal du vælge **Udfør**. Vælg OK, når du bliver **bedt om det**.
    
Derefter skal du installere AD FS-tjenesten med denne kommando ved Windows PowerShell kommandoprompten på ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Vent på, at installationen afsluttes.
  
Dernæst skal du konfigurere AD FS-tjenesten med disse trin:
  
1. Vælg **Start**, og vælg derefter **ikonet Serverstyring** .
    
2. Vælg **AD FS** i træruden i Serverstyring.
    
3. Vælg det orange advarselssymbol på værktøjslinjen øverst, og vælg derefter **Konfigurer sammenslutningstjenesten på denne server**.
    
4. På **velkomstsiden i** konfigurationsguiden til Active Directory Federation Services skal du vælge **Næste**.
    
5. På siden **Forbind næste AD DS** du vælge **Næste**.
    
6. På siden **Angiv tjenesteegenskaber** :
    
  - For **SSL-certifikat** skal du vælge pil ned og derefter vælge certifikatet med navnet på din sammenslutningstjenesteSQDN.
    
  - I **Sammenslutningstjenestes visningsnavn** skal du skrive navnet på din fiktive organisation.
    
  - Vælg **Næste**.
    
7. På siden **Angiv tjenestekonto** skal du vælge **Vælg** for **kontonavn**.
    
8. I **Vælg bruger- eller tjenestekonto** skal **du angive ADFS-Service**, **vælge Kontrollér navne** og derefter vælge **OK**.
    
9. I **Adgangskode til** konto skal du angive adgangskoden til ADFS-Service kontoen og derefter vælge **Næste**.
    
10. På siden **Angiv konfigurationsdatabase** skal du vælge **Næste**.
    
11. På siden **Indstillinger for gennemsyn** skal du vælge **Næste**.
    
12. På siden **Nødvendige kontroller skal** du vælge **Konfigurer**.

13. På siden **Resultater** skal du vælge **Luk**.
    
14. Vælg **Start**, vælg tænd/tilbage-ikonet, **vælg Genstart**, og vælg derefter **Fortsæt**.
    
Fra [Azure-portalen skal](https://portal.azure.com) du oprette forbindelse til PROXY1 med legitimationsoplysningerne til CORPUser1-kontoen\\.
  
Derefter skal du bruge disse trin til at installere det selv signerede certifikat **på både PROXY1 og APP1**.
  
1. Vælg **Start**, indtast **mmc.exe**, og tryk derefter på **Enter**.
    
2. Vælg **Filer > tilføj/fjern snap-in**.
    
3. I **Tilføj eller fjern snap-ins** skal du dobbeltklikke  på Certifikater på listen over tilgængelige snap-ins, vælge **Computerkonto** og derefter vælge **Næste**.
    
4. Vælg **Udfør i** Vælg **computer**, og vælg derefter **OK**.
    
5. Åbn Certifikater **(lokal computer)** >  > **PersonalCertificates i træruden**.
    
6. Markér og hold (eller højreklik) Personlig **nede**, markér **Alle opgaver**, og vælg derefter **Importér**.
    
7. På **velkomstsiden** skal du vælge **Næste**.
    
8. På siden **Fil, der** skal importeres skal du **\\\\angive adfs1certssl.pfx\\\\** og derefter vælge **Næste**.
    
9. På siden **Beskyttelse af private** nøgler skal du angive adgangskoden til certifikatet **i Adgangskode** og derefter vælge **Næste.**
    
10. På siden **Certifikatlager** skal du vælge **Næste.**
    
11. Vælg Udfør **på** siden **Fuldførelse**.
    
12. På siden **Certifikat Store** skal du vælge **Næste**.
    
13. Vælg OK, når du bliver **bedt om det**.
    
14. Vælg Certifikater i **træruden**.
    
15. Vælg og hold (eller højreklik) på certifikatet, og vælg derefter **Kopiér**.
    
16. I træruden skal du åbne **Rodnøglecenter, der er** >  tillid **tilCertificates**.
    
17. Flyt musemarkøren under listen over installerede certifikater, markér og hold (eller højreklik) nede, og vælg derefter **Sæt ind**.
    
Åbn en PowerShell-kommandoprompt på administratorniveau, og kør følgende kommando:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Vent på, at installationen afsluttes.
  
Brug disse trin til at konfigurere webprogrammets proxytjeneste til at bruge ADFS1 som dets sammenslutningsserver:
  
1. Vælg **Start**, og vælg derefter **Serverstyring**.
    
2. Vælg Fjernadgang i **træruden**.
    
3. Vælg det orange advarselssymbol på værktøjslinjen øverst, og vælg derefter Åbn guiden **Webprogramproxy**.
    
4. På **velkomstsiden** i guiden Konfiguration af webprogramproxy skal du vælge **Næste**.
    
5. Gør følgende **på siden Sammenslutningsserver** :
    
  - I feltet **Sammenslutningstjenestenavn** skal du angive din sammenslutningstjeneste-FQDN.
    
  - Skriv **CORPUser1 i feltet\\ Brugernavn**.
    
  - I feltet **Adgangskode** skal du angive adgangskoden til Brugerkonto1-kontoen.
    
  - Vælg **Næste**.
    
6. På siden **AD FS-proxycertifikat** skal du vælge pil ned, vælge certifikatet med dit sammenslutningstjeneste-FQDN og derefter vælge **Næste**.
    
7. På siden **Bekræftelse** skal du vælge **Konfigurer**.
    
8. På siden **Resultater** skal du vælge **Luk**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Fase 5: Konfigurer Microsoft 365 for identitet i organisationsnetværk

Brug [Azure-portalen til](https://portal.azure.com) at oprette forbindelse til den virtuelle APP1-maskine med legitimationsoplysningerne til CORPUser1-kontoen\\.
  
Brug disse trin til at konfigurere Azure AD Forbind og dit Microsoft 365 til federated authentication:
  
1. Dobbeltklik på **Azure AD-ikonet på skrivebordet Forbind**.
    
2. På siden **Velkommen til Azure AD Forbind** du vælge **Konfigurer**.
    
3. På siden **Yderligere opgaver** skal du **vælge Skift bruger-logon** og derefter vælge **Næste**.
    
4. På siden **Forbind Azure AD** skal du angive dit globale administratorkontonavn og din adgangskode og derefter vælge **Næste**.
    
5. På siden **Bruger-logon** skal du vælge **Sammenslutning med AD FS** og derefter vælge **Næste**.
    
6. På AD **FS-farmsiden** skal du vælge Brug en eksisterende **AD FS-farm**, angive **ADFS1** i **feltet Servernavn** og derefter vælge **Næste**.
    
7. Når du bliver bedt om legitimationsoplysninger til serveren, skal du angive legitimationsoplysningerne for CORPUser1-kontoen\\ og derefter vælge **OK**.
    
8. På siden **Legitimationsoplysninger** for domæneadministrator skal du angive **CORPUser1\\** i feltet  Brugernavn, angive adgangskoden til kontoen i feltet Adgangskode  og derefter vælge **Næste**.
    
9. På siden **AD FS-tjenestekonto** skal du angive **CORPADFS-Service\\** i feltet  Domænebrugernavn, angive adgangskoden til kontoen i  feltet Adgangskode til domænebruger og derefter vælge **Næste**.
    
10. På siden **Azure AD Domain** i **Domain** skal du vælge navnet på det domæne, du tidligere har oprettet og føjet til dit abonnement i Fase 1, og derefter vælge **Næste**.
    
11. På siden **Klar til at konfigurere** skal du vælge **Konfigurer**.
    
12. På siden **Installation fuldført skal** du vælge **Bekræft**.
    
    Du bør få vist meddelelser, der angiver, at både intranet- og internetkonfigurationen er blevet bekræftet.
    
13. På siden **Installation fuldført** skal du vælge **Afslut**.
    
Sådan demonstrerer du, at federated authentication fungerer:
  
1. Åbn en ny privat forekomst af din browser på din lokale computer, og gå til [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. For logonoplysninger skal du skrive **user1@**\<*the domain created in Phase 1*>.
    
    Hvis testdomænet f.eks **. testlab.contoso.com**, skal du skrive "user1@testlab.contoso.com". Tryk på **tabulatortasten**, eller Microsoft 365 at omdirigere dig automatisk.
    
    Du bør nu se en **Din forbindelse er ikke en privat** side. Dette vises, fordi du har installeret et selv signeret certifikat på ADFS1, som din stationære computer ikke kan validere. I en produktionsinstallation af federated authentication ville du bruge et certifikat fra et pålideligt nøglecenter, og dine brugere ville ikke få vist denne side.
    
3. På siden **Din forbindelse er ikke privat** skal du vælge **Avanceret** og derefter vælge **Fortsæt til \<*your federation service FQDN*>**. 
    
4. På siden med navnet på din fiktive organisation skal du logge på med følgende:
    
  - **CORP\\ Bruger1** for navnet
    
  - Adgangskoden til Brugerkonto1-kontoen
    
    Du bør få vist **Microsoft Office startsiden**.
    
Denne procedure viser, at dit prøveabonnement er tilknyttet det AD DS corp.contoso.com domæne, der er hostet på DC1. Her er de grundlæggende oplysninger om godkendelsesprocessen:
  
1. Når du bruger det sammensluttede domæne, som du oprettede i Fase 1 i logonkontoens navn, omdirigerer Microsoft 365 din browser til din sammenslutningstjeneste FQDN og PROXY1.
    
2. PROXY1 sender din lokale computer til den fiktive virksomheds logonside.
    
3. Når du sender CORPUser1\\ og adgangskoden til PROXY1, videresendes de til ADFS1.
    
4. ADFS1 validerer CORPUser1\\ og adgangskoden med DC1 og sender din lokale computer et sikkerhedstoken.
    
5. Din lokale computer sender sikkerhedstokenet til Microsoft 365.
    
6. Microsoft 365 validerer, at sikkerhedstokenet blev oprettet af ADFS1 og tillader adgang.
    
Dit prøveabonnement er nu konfigureret med federated authentication. Du kan bruge dette udviklings-/testmiljø til avancerede godkendelsesscenarier.
  
## <a name="next-step"></a>Næste trin

Når du er klar til at installere produktionsklar, godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Azure, skal du se Installér godkendelse i organisationsnetværket med høj tilgængelighed [til Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
