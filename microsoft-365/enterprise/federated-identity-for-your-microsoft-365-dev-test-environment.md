---
title: Organisationsnetværksidentitet for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Konfigurer godkendelse i organisationsnetværket for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 0214c7778176641c6446106cf92ed173b81b71de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101023"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Organisationsnetværksidentitet for dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

Microsoft 365 understøtter organisationsnetværksidentitet. Det betyder, at i stedet for at udføre valideringen af selve legitimationsoplysningerne henviser Microsoft 365 den bruger, der opretter forbindelse til en godkendelsesserver i organisationsnetværket, som Microsoft 365 har tillid til. Hvis brugerens legitimationsoplysninger er korrekte, udsteder den sammenkædede godkendelsesserver et sikkerhedstoken, som klienten derefter sender til Microsoft 365 som bevis for godkendelse. Organisationsnetværksidentitet giver mulighed for aflastning og opskalering af godkendelse for et Microsoft 365 abonnement samt avancerede godkendelses- og sikkerhedsscenarier.
  
I denne artikel beskrives det, hvordan du konfigurerer godkendelse i organisationsnetværket for dit Microsoft 365 testmiljø, hvilket resulterer i følgende:

![Godkendelse i organisationsnetværket for Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5 prøve- eller produktionsabonnement.
    
- Et forenklet organisationsintranet med forbindelse til internettet, der består af fem virtuelle maskiner på et undernet i et virtuelt Azure-netværk (DC1, APP1, CLIENT1, ADFS1 og PROXY1). Azure AD Forbind kører på APP1 for at synkronisere listen over konti i domænet Active Directory-domæneservices til Microsoft 365. PROXY1 modtager de indgående godkendelsesanmodninger. ADFS1 validerer legitimationsoplysninger med DC1 og udsteder sikkerhedstokens.
    
Konfiguration af dette testmiljø omfatter fem faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Opret AD FS-serveren](#phase-2-create-the-ad-fs-server)
- [Fase 3: Opret webproxyserveren](#phase-3-create-the-web-proxy-server)
- [Fase 4: Opret et selvsigneret certifikat, og konfigurer ADFS1 og PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Fase 5: Konfigurer Microsoft 365 til organisationsnetværksidentitet](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Du kan ikke konfigurere dette testmiljø med et Azure-prøveabonnement.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i [synkronisering af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Den resulterende konfiguration ser sådan ud:
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveperiode eller betalte abonnementer.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk. Azure AD Forbind kører på APP1 for at synkronisere DOMÆNET TESTLAB Active Directory-domæneservices (AD DS) med Azure AD-lejeren for dine Microsoft 365-abonnementer med jævne mellemrum.

## <a name="phase-2-create-the-ad-fs-server"></a>Fase 2: Opret AD FS-serveren

En AD FS-server leverer sammenkædet godkendelse mellem Microsoft 365 og kontiene i det corp.contoso.com domæne, der hostes på DC1.
  
Hvis du vil oprette en virtuel Azure-maskine til ADFS1, skal du udfylde navnet på dit abonnement og ressourcegruppen og Azure-placeringen for din Base Configuration og derefter køre disse kommandoer ved kommandoprompten Azure PowerShell på din lokale computer.
  
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

Derefter skal du bruge [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle ADFS1-maskine ved hjælp af navnet og adgangskoden til den lokale administratorkonto i ADFS1 og derefter åbne en kommandoprompt med Windows PowerShell.
  
Hvis du vil kontrollere navneopløsningen og netværkskommunikationen mellem ADFS1 og DC1, skal du køre kommandoen **ping dc1.corp.contoso.com** og kontrollere, at der er fire svar.
  
Derefter skal du slutte den virtuelle ADFS1-maskine til CORP-domænet med disse kommandoer ved Windows PowerShell prompten på ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Den resulterende konfiguration ser sådan ud:
  
![AD FS-serveren, der er føjet til DirSync for Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Fase 3: Opret webproxyserveren

PROXY1 giver proxy for godkendelsesmeddelelser mellem brugere, der forsøger at godkende, og ADFS1.
  
Hvis du vil oprette en virtuel Azure-maskine til PROXY1, skal du udfylde navnet på din ressourcegruppe og Azure-placering og derefter køre disse kommandoer ved kommandoprompten Azure PowerShell på din lokale computer.
  
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
> PROXY1 tildeles en statisk offentlig IP-adresse, fordi du skal oprette en offentlig DNS-post, der peger på den, og den må ikke ændres, når du genstarter den virtuelle maskine PROXY1.
  
Føj derefter en regel til netværkssikkerhedsgruppen for CorpNet-undernettet for at tillade uopfordret indgående trafik fra internettet til PROXY1's private IP-adresse og TCP-port 443. Kør disse kommandoer ved kommandoprompten Azure PowerShell på din lokale computer.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Derefter skal du bruge [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle maskine PROXY1 ved hjælp af det lokale administratorkontonavn og den lokale adgangskode PROXY1 og derefter åbne en Windows PowerShell kommandoprompt på PROXY1.
  
Hvis du vil kontrollere navneopløsningen og netværkskommunikationen mellem PROXY1 og DC1, skal du køre kommandoen **ping dc1.corp.contoso.com** og kontrollere, at der er fire svar.
  
Slut derefter den virtuelle proxy1-maskine til CORP-domænet med disse kommandoer ved Windows PowerShell prompten på PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Vis den offentlige IP-adresse for PROXY1 med disse Azure PowerShell kommandoer på din lokale computer.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Derefter skal du arbejde sammen med din offentlige DNS-udbyder og oprette en ny offentlig DNS A-post for **fs.testlab.**\<*your DNS domain name*> der omsættes til den IP-adresse, der vises af kommandoen **Write-Host** . **Fs.testlab.**\<*your DNS domain name*> kaldes i det følgende  *FQDN for federation service*.
  
Derefter skal du bruge [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle DC1-maskine ved hjælp af legitimationsoplysningerne for CORPUser1\\ og derefter køre følgende kommandoer på administratorniveau Windows PowerShell kommandoprompt:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Disse kommandoer opretter en intern DNS A-post, så virtuelle maskiner på det virtuelle Azure-netværk kan fortolke FQDN for den interne sammenslutningstjeneste til ADFS1's private IP-adresse.
  
Den resulterende konfiguration ser sådan ud:
  
![Webprogramproxyserveren, der er føjet til DirSync for Microsoft 365 testmiljø.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Fase 4: Opret et selvsigneret certifikat, og konfigurer ADFS1 og PROXY1

I denne fase skal du oprette et selvsigneret digitalt certifikat til FQDN for din sammenslutningstjeneste og konfigurere ADFS1 og PROXY1 som en AD FS-farm.
  
Brug først [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle DC1-maskine ved hjælp af legitimationsoplysningerne for CORPUser1\\ og derefter åbne en kommandoprompt på administratorniveau Windows PowerShell.
  
Opret derefter en AD FS-tjenestekonto med denne kommando ved kommandoprompten Windows PowerShell på DC1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Bemærk, at du i denne kommando bliver bedt om at angive kontoens adgangskode. Vælg en stærk adgangskode, og registrer den på en sikker placering. Du skal bruge den til denne fase og fase 5.
  
Brug [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle maskine ADFS1 ved hjælp af legitimationsoplysningerne for CORPUser1\\. Åbn en kommandoprompt på administratorniveau Windows PowerShell på ADFS1, udfyld FQDN for organisationstjenesten, og kør derefter disse kommandoer for at oprette et selvsigneret certifikat:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Brug derefter disse trin til at gemme det nye selvsignerede certifikat som en fil.
  
1. Vælg **Start**, angiv **mmc.exe**, og tryk derefter på **Enter**.
    
2. Vælg **FilerTilføj** > **/fjern snap-in**.
    
3. Dobbeltklik på **Certifikater** på listen over tilgængelige **snap-ins i Tilføj eller fjern snap-ins**, vælg **Computerkonto**, og vælg derefter **Næste**.
    
4. Vælg **Udfør** i **Vælg computer**, og vælg derefter **OK**.
    
5. Åbn **Certifikater (lokal computer) i træruden > Personlige > Certifikater**.
    
6. Vælg certifikatet, og hold det nede (eller højreklik) med FQDN-organisationstjenesten, vælg **Alle opgaver**, og vælg derefter **Eksportér**.
    
7. Vælg **Næste** på **velkomstsiden**.
    
8. På siden **Eksportér privat nøgle** skal du vælge **Ja** og derefter vælge **Næste**.
    
9. På siden **Eksportér filformat** skal du vælge **Eksportér alle udvidede egenskaber** og derefter vælge **Næste**.
    
10. På siden **Sikkerhed** skal du vælge **Adgangskode** og angive en adgangskode i **Adgangskode** og **Bekræft adgangskode.**
    
11. Vælg Gennemse på siden **Fil, der skal eksporteres**.
    
12. Gå til mappen **C:\\Certs** , angiv **SSL** i **Filnavn**, og vælg derefter **Gem.**
    
13. Vælg **Næste** på siden **Fil, der skal eksporteres**.
    
14. Vælg **Udfør** på siden **Fuldfører guiden Certifikateksport**. Når du bliver bedt om det, skal du vælge **OK**.
    
Installer derefter AD FS-tjenesten med denne kommando ved kommandoprompten Windows PowerShell på ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Vent, indtil installationen er fuldført.
  
Konfigurer derefter AD FS-tjenesten med disse trin:
  
1. Vælg **Start**, og vælg derefter ikonet **Serverstyring** .
    
2. Vælg **AD FS** i træruden i Serverstyring.
    
3. Vælg det orange advarselssymbol på værktøjslinjen øverst, og vælg derefter **Konfigurer samlingstjenesten på denne server**.
    
4. Vælg **Næste** på **velkomstsiden** i guiden Active Directory Federation Services Konfiguration.
    
5. På siden **Forbind til AD DS** skal du vælge **Næste**.
    
6. På siden **Angiv egenskaber for tjeneste** :
    
  - Som **SSL-certifikat** skal du vælge pil ned og derefter vælge certifikatet med navnet på FQDN for din sammenslutningstjeneste.
    
  - Angiv navnet på din fiktive organisation i **Vist navn i Federation Service**.
    
  - Vælg **Næste**.
    
7. På siden **Angiv tjenestekonto** skal du vælge **Vælg** for **Kontonavn**.
    
8. I **Vælg bruger- eller tjenestekonto** skal du angive **ADFS-Tjeneste**, vælge **Kontrollér navne** og derefter vælge **OK**.
    
9. Angiv adgangskoden til den ADFS-Service konto under **Adgangskode til konto**, og vælg derefter **Næste**.
    
10. På siden **Angiv konfigurationsdatabase** skal du vælge **Næste**.
    
11. På siden **Indstillinger for gennemsyn** skal du vælge **Næste**.
    
12. På siden **Forudsætningskontroller** skal du vælge **Konfigurer**.

13. Vælg **Luk** på siden **Resultater**.
    
14. Vælg **Start**, vælg tænd/sikonet, vælg **Genstart**, og vælg derefter **Fortsæt**.
    
Fra [Azure Portal skal du](https://portal.azure.com) oprette forbindelse til PROXY1 med legitimationsoplysningerne for CORPUser1-kontoen\\.
  
Derefter skal du bruge disse trin til at installere det selvsignerede certifikat **på både PROXY1 og APP1**.
  
1. Vælg **Start**, angiv **mmc.exe**, og tryk derefter på **Enter**.
    
2. Vælg **Filer > Tilføj/fjern snap-in**.
    
3. Dobbeltklik på **Certifikater** på listen over tilgængelige **snap-ins i Tilføj eller fjern snap-ins**, vælg **Computerkonto**, og vælg derefter **Næste**.
    
4. Vælg **Udfør** i **Vælg computer**, og vælg derefter **OK**.
    
5. Åbn **Certifikater (lokal computer)** > **PersonalCertificates** >  i træruden.
    
6. Vælg og hold (eller højreklik) **Personlig**, vælg **Alle opgaver**, og vælg derefter **Importér**.
    
7. Vælg **Næste** på **velkomstsiden**.
    
8. Angiv **adfs1certsssl.pfx\\ på siden Fil, der skal importeres\\,\\\\** og vælg derefter **Næste**.
    
9. Angiv adgangskoden til certifikatet i **Adgangskode** på siden **Beskyttelse af privat nøgle**, og vælg derefter **Næste.**
    
10. På siden **Certifikatlager** skal du vælge **Næste.**
    
11. Vælg **Udfør** på siden **Fuldfører**.
    
12. Vælg **Næste** på siden **Certifikat Store**.
    
13. Når du bliver bedt om det, skal du vælge **OK**.
    
14. Vælg **Certifikater** i træruden.
    
15. Vælg certifikatet, og hold det nede (eller højreklik), og vælg derefter **Kopiér**.
    
16. I træruden skal du åbne **Nøglecentre** > , der er tillid **tilCertificates**.
    
17. Flyt musemarkøren ned under listen over installerede certifikater, vælg og hold nede (eller højreklik), og vælg derefter **Sæt ind**.
    
Åbn en PowerShell-kommandoprompt på administratorniveau, og kør følgende kommando:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Vent, indtil installationen er fuldført.
  
Brug disse trin til at konfigurere webprogramproxytjenesten til at bruge ADFS1 som samlingsserver:
  
1. Vælg **Start**, og vælg derefter **Serverstyring**.
    
2. Vælg **Fjernadgang** i træruden.
    
3. Vælg det orange advarselssymbol på værktøjslinjen øverst, og vælg derefter **Åbn guiden Web Programproxy**.
    
4. Vælg **Næste** på **velkomstsiden** i guiden Konfiguration af web Programproxy.
    
5. På siden **Samlingsserver** :
    
  - I feltet **Navn på organisationstjeneste** skal du angive FQDN for organisationstjenesten.
    
  - I feltet **Brugernavn** skal du angive **CORPUser1\\**.
    
  - I feltet **Adgangskode** skal du angive adgangskoden til brugerkontoen User1.
    
  - Vælg **Næste**.
    
6. På siden **AD FS Proxy Certificate** skal du vælge pil ned, vælge certifikatet med dit FQDN for organisationsnetværkstjenesten og derefter vælge **Næste**.
    
7. På siden **Bekræftelse** skal du vælge **Konfigurer**.
    
8. Vælg **Luk** på siden **Resultater**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Fase 5: Konfigurer Microsoft 365 til organisationsnetværksidentitet

Brug [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle app1-maskine med legitimationsoplysningerne til CORPUser1-kontoen\\.
  
Brug disse trin til at konfigurere Azure AD-Forbind og dit Microsoft 365-abonnement til godkendelse i organisationsnetværket:
  
1. Dobbeltklik på **Azure AD** Forbind på skrivebordet.
    
2. På siden **Velkommen til Azure AD Forbind** skal du vælge **Konfigurer**.
    
3. På siden **Yderligere opgaver** skal du vælge **Skift brugerlogon** og derefter vælge **Næste**.
    
4. Angiv dit globale administratorkontonavn og din adgangskode på siden **Forbind til Azure AD**, og vælg derefter **Næste**.
    
5. På logonsiden **Bruger** skal du vælge **Sammenslutning med AD FS** og derefter vælge **Næste**.
    
6. På siden **AD FS-farm** skal du vælge **Brug en eksisterende AD FS-farm**, angive **ADFS1** i feltet **Servernavn** og derefter vælge **Næste**.
    
7. Når du bliver bedt om at angive serverlegitimationsoplysninger, skal du angive legitimationsoplysningerne for kontoen CORPUser1\\ og derefter vælge **OK**.
    
8. På siden **Legitimationsoplysninger for domæneadministrator** skal du angive **CORPUser1\\** i feltet **Brugernavn**, angive adgangskoden til kontoen i feltet **Adgangskode** og derefter vælge **Næste**.
    
9. På siden **AD FS-tjenestekonto** skal du angive **CORPADFS-Service\\** i feltet **Domænebrugernavn**, angive kontoens adgangskode i feltet **Domænebrugeradgangskode** og derefter vælge **Næste**.
    
10. På siden **Azure AD Domain** i **Domain** skal du vælge navnet på det domæne, du tidligere har oprettet og føjet til dit abonnement i Fase 1, og derefter vælge **Næste**.
    
11. På siden **Klar til at konfigurere** skal du vælge **Konfigurer**.
    
12. På siden **Installation fuldført** skal du vælge **Bekræft**.
    
    Du bør få vist meddelelser, der angiver, at både intranet- og internetkonfigurationen er bekræftet.
    
13. Vælg **Afslut** på siden **Installation fuldført**.
    
Sådan demonstrerer du, at godkendelse i organisationsnetværket fungerer:
  
1. Åbn en ny privat forekomst af browseren på din lokale computer, og gå til [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Angiv **user1@**\<*the domain created in Phase 1*> for logonlegitimationsoplysninger.
    
    Hvis dit testdomæne f.eks. er **testlab.contoso.com**, skal du angive "user1@testlab.contoso.com". Tryk på **tabulatortasten**, eller tillad, at Microsoft 365 automatisk omdirigerer dig.
    
    Du bør nu kunne se siden **Din forbindelse er ikke privat** . Du får vist dette, fordi du har installeret et selvsigneret certifikat på ADFS1, som din stationære computer ikke kan validere. I en produktionsinstallation af godkendelse i organisationsnetværket skal du bruge et certifikat fra et nøglecenter, der er tillid til, og dine brugere vil ikke kunne se denne side.
    
3. På siden **Din forbindelse er ikke privat** skal du vælge **Avanceret** og derefter vælge **Fortsæt til \<*your federation service FQDN*>**. 
    
4. Log på med følgende på siden med navnet på din fiktive organisation:
    
  - **CORP\\ User1** for navnet
    
  - Adgangskoden til user1-kontoen
    
    Du bør kunne se siden **Microsoft Office startside**.
    
Denne procedure viser, at dit prøveabonnement er sammenkædet med AD DS-corp.contoso.com domæne, der hostes på DC1. Her er de grundlæggende funktioner i godkendelsesprocessen:
  
1. Når du bruger det domæne i organisationsnetværket, som du oprettede i fase 1 i logonkontonavnet, omdirigerer Microsoft 365 din browser til FQDN og PROXY1 for din organisationstjeneste.
    
2. PROXY1 sender den fiktive firmalogonside til din lokale computer.
    
3. Når du sender CORPUser1\\ og adgangskoden til PROXY1, videresendes de til ADFS1.
    
4. ADFS1 validerer CORPUser1\\ og adgangskoden med DC1 og sender en sikkerhedstoken til din lokale computer.
    
5. Den lokale computer sender sikkerhedstokenet til Microsoft 365.
    
6. Microsoft 365 validerer, at sikkerhedstokenet blev oprettet af ADFS1 og giver adgang.
    
Dit prøveabonnement er nu konfigureret med godkendelse i organisationsnetværket. Du kan bruge dette udviklings-/testmiljø til avancerede godkendelsesscenarier.
  
## <a name="next-step"></a>Næste trin

Når du er klar til at udrulle organisationsnetværksgodkendelse med høj tilgængelighed til Microsoft 365 i Azure, skal du se [Installér organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
