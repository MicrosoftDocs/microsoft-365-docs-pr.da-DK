---
title: Konfiguration af letvægtsbase
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/17/2022
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
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Brug denne testvejledning til at oprette et letvægtstestmiljø til test Microsoft 365 til virksomheder.
ms.openlocfilehash: fcfa3f67ec790244fc44f3539af8da1df7a09432
ms.sourcegitcommit: f645e0e9db74b25663cd9ddec7e3824d6ffc57f7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65444196"
---
# <a name="the-lightweight-base-configuration"></a>Letvægtsbasekonfigurationen

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du opretter et forenklet miljø med et Microsoft 365 E5-abonnement og en computer, der kører Windows 10 Enterprise.

![Det lette Microsoft 3656 Enterprise-testmiljø.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Oprettelse af et letvægtstestmiljø omfatter fem faser:

- [Fase 1: Opret dit Microsoft 365 E5 abonnement](#phase-1-create-your-microsoft-365-e5-subscription)
- [Fase 2: Konfigurer dit Office 365 prøveabonnement](#phase-2-configure-your-office-365-trial-subscription)
- [Fase 3: Tilføj et Microsoft 365 E5 prøveabonnement](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Fase 4: Opret en Windows 10 Enterprise computer](#phase-4-create-a-windows-10-enterprise-computer)
- [Fase 5: Slut din Windows 10 computer til Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

Brug det resulterende miljø til at teste funktionerne og funktionaliteten i [Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise).

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du se [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Det kan være en god idé at udskrive denne artikel for at registrere de specifikke oplysninger, du skal bruge til dette miljø i løbet af de 30 dage, hvor Office 365 prøveabonnement. Du kan nemt forlænge trailabonnementet i yderligere 30 dage. Hvis du vil have et permanent testmiljø, skal du oprette et nyt betalt abonnement med en separat Azure AD lejer og et lille antal licenser.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Fase 1: Opret dit Microsoft 365 E5 abonnement

Vi starter med et Microsoft 365 E5 prøveabonnement og føjer derefter abonnementet Microsoft 365 E5 til det.

>[!NOTE]
>Vi anbefaler, at du opretter et prøveabonnement på Office 365, så dit testmiljø har en separat Azure AD lejer fra de betalte abonnementer, du har i øjeblikket. Denne adskillelse betyder, at du kan tilføje og fjerne brugere og grupper i testlejer uden at påvirke dine produktionsabonnementer.

Hvis du vil starte dit Microsoft 365 E5 prøveabonnement, skal du først have et fiktivt firmanavn og en ny Microsoft-konto.
  
1. Vi anbefaler, at du bruger en variant af firmanavnet Contoso til dit firmanavn, som er en fiktiv virksomhed, der bruges i Microsofts eksempelindhold, men det er ikke påkrævet. Registrer dit fiktive firmanavn her: ![Linje.](../media/Common-Images/TableLine.png)

2. Hvis du vil tilmelde dig en ny Microsoft-konto, skal du gå til [https://outlook.com](https://outlook.com) og oprette en konto med en ny mailkonto og adresse. Du skal bruge denne konto til at tilmelde dig Office 365.

    - Registrer for- og efternavn for din nye konto her: ![Linje.](../media/Common-Images/TableLine.png)

    - Registrer den nye mailadresse her: ![Linje.](../media/Common-Images/TableLine.png)@outlook.com

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Tilmeld dig et Office 365 E5 prøveabonnement

1. Gå til [https://aka.ms/e5trial](https://aka.ms/e5trial)i din browser.

2. På trin 1 på siden **Tak, fordi du valgte Office 365 E5 skal du** angive din nye mailadresse.
3. I trin 2 i processen for trailabonnement skal du angive de ønskede oplysninger og derefter udføre bekræftelsen.
4. I trin 3 skal du angive et organisationsnavn og derefter et kontonavn, der vil være den globale administrator for abonnementet.
5. I trin 4 skal du registrere logonsiden her (vælg og kopiér): ![Linje.](../media/Common-Images/TableLine.png)
6. Registrer bruger-id'et her: ![Line.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   Registrer den adgangskode, du har angivet på en sikker placering.
   Denne værdi kaldes det **globale administratornavn**.
7. Vælg **Gå til Konfiguration**.
8. I Office 365 E5 installation skal du vælge **Fortsæt med at bruge *din organisation.onmicrosoft.com* til mail og logon** og derefter vælge **Afslut og fortsæt senere**.

Du skulle se Microsoft 365 Administration.

## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Fase 2: Konfigurer dit Office 365 prøveabonnement

I denne fase konfigurerer du dit abonnement med flere brugere og tildeler dem Office 365 E5 licenser.
  
Hvis du vil oprette forbindelse til dit abonnement med modulet Azure Active Directory PowerShell til Graph fra din computer, skal du bruge vejledningen i [Forbind til at Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

I dialogboksen **Windows PowerShell anmodning om legitimationsoplysninger** skal du angive det globale administratornavn (f.eks. *jdoe@contosotoycompany.onmicrosoft.com*) og adgangskoden.
  
Udfyld organisationens navn (f.eks. *contosotoycompany*), landekoden på to tegn for din placering, en almindelig kontoadgangskode, og kør derefter følgende kommandoer fra PowerShell-prompten:

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License

for($i=2;$i -le 4; $i++) {
    $userUPN= "user$($i)@$($orgName).onmicrosoft.com"
    New-AzureADUser -DisplayName "User $($i)" -GivenName User -SurName $i -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user$($i)"
    $userObjectID = (Get-AzureADUser -SearchString $userupn).ObjectID
    Set-AzureADUserLicense -ObjectId $userObjectID -AssignedLicenses $LicensesToAssign
}
```

> [!NOTE]
> Brug af en almindelig adgangskode her er til automatisering og nem konfiguration af et testmiljø. Dette frarådes naturligvis i høj grad for produktionsabonnementer.

### <a name="record-key-information-for-future-reference"></a>Registrer nøgleoplysninger til fremtidig reference

Hvis du ikke allerede har registreret disse værdier, kan du optage dem nu:
  
- Global administrator navn: ![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com (fra trin 6 i fase 1)

    Registrer også adgangskoden for denne konto på en sikker placering.

- Organisationen for dit prøveabonnement: ![Linje.](../media/Common-Images/TableLine.png) (fra trin 4 i fase 1)

- Hvis du vil have vist en liste over kontiene for Bruger 2, Bruger 3, Bruger 4 og Bruger 5, skal du køre følgende kommando fra Windows Azure Active Directory modul for Windows PowerShell prompt:

  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Registrer kontonavnene her:

  - Bruger 2-kontonavn: bruger2 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Bruger 3-kontonavn: bruger3 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Bruger 4-kontonavn: bruger4 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Bruger 5-kontonavn: bruger5 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com

    Registrer også den almindelige adgangskode for disse konti på en sikker placering.

### <a name="using-an-office-365-test-environment"></a>Brug af et Office 365 testmiljø

Hvis du kun har brug for et Office 365 testmiljø, behøver du ikke at læse resten af denne artikel.

Du kan finde flere Test Lab-vejledninger, der gælder for både Office 365 og Microsoft 365, [under Microsoft 365 til vejledninger til virksomhedstestlaboratorier](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Fase 3: Tilføj et Microsoft 365 E5 prøveabonnement

I denne fase tilmelder du dig Microsoft 365 E5 prøveabonnementet og føjer det til den samme organisation som dit Office 365 E5 prøveabonnement.
  
Først skal du tilføje prøveabonnementet på Microsoft 365 E5 og tildele den nye Microsoft 365-licens til din globale administratorkonto.
  
1. I et privat vindue i en internetbrowser skal du bruge legitimationsoplysningerne til din globale administratorkonto til at logge på Microsoft 365 Administration på [https://admin.microsoft.com](https://admin.microsoft.com).

2. Vælg **FaktureringKøb** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**tjenester**</a> i venstre navigationsrude på siden **Microsoft 365 Administration**.

3. På siden **Køb tjenester** skal du vælge **Microsoft 365 E5** og derefter vælge **Hent gratis prøveversion**.

4. På siden **Microsoft 365 E5 prøveversion** skal du beslutte at modtage en sms eller et telefonopkald, angive dit telefonnummer og derefter vælge **Tekst mig** eller **Ring til mig**. Udfør bekræftelsen.

5. På siden **Bekræft din ordre** skal du vælge **Prøv nu**.

6. Vælg **Fortsæt** på siden **Ordrekvittering**.

7. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktive**</a> >  brugere i Microsoft 365 Administration.

8. Vælg din administratorkonto under **Aktive brugere**.

9. Vælg **Licenser og apps**.

10. Deaktiver licensen for Office 365 Enterprise E5, og aktivér licensen for Microsoft 365 E5.

11. Vælg **Gem ændringer**, og luk derefter ruden med brugerkontooplysninger.

Gentag derefter trin 8 til 11 i den forrige procedure for alle dine andre konti (Bruger 2, Bruger 3, Bruger 4 og Bruger 5).
  
> [!NOTE]
> Længden på prøveabonnementet på Microsoft 365 E5 er 30 dage. Hvis du vil have et permanent testmiljø, skal du konvertere dette prøveabonnement til et betalt abonnement med et lille antal licenser.
  
Dit testmiljø har nu:
  
- Et Microsoft 365 E5 prøveabonnement.
- Alle dine relevante brugerkonti (enten kun den globale administrator eller alle fem brugerkonti) er aktiveret til at bruge Microsoft 365 E5.

Din resulterende konfiguration, som tilføjer Microsoft 365 E5, ser ud på følgende måde:
  
![Fase 3 i Microsoft 3656 Enterprise-testmiljøet.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Fase 4: Opret en Windows 10 Enterprise computer

I denne fase opretter du en separat computer, der kører Windows 10 Enterprise som enten en fysisk computer, en virtuel maskine eller en virtuel Azure-maskine.
  
### <a name="physical-computer"></a>Fysisk computer

Installer Windows 10 Enterprise på en personlig computer. Du kan downloade prøveversionen af Windows 10 Enterprise [her](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine"></a>Virtuel maskine

Brug den hypervisor, du vælger, til at oprette en virtuel maskine, og installér derefter Windows 10 Enterprise på den. Du kan downloade prøveversionen af Windows 10 Enterprise [her](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine-in-azure"></a>Virtuel maskine i Azure

Hvis du vil oprette en Windows 10 virtuel maskine i Microsoft Azure, ***skal du have et Visual Studio-baseret abonnement***, som har adgang til billedet for Windows 10 Enterprise. Andre typer Azure-abonnementer, f.eks. prøveversioner og betalte abonnementer, har ikke adgang til dette billede. Du kan finde de seneste oplysninger under [Brug Windows klient i Azure til udviklings-/testscenarier](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Kom i gang med Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). Disse kommandosæt opretter en Windows 10 Enterprise virtuel maskine med navnet WIN10 og hele den påkrævede infrastruktur, herunder en ressourcegruppe, en lagerkonto og et virtuelt netværk. Hvis du allerede har kendskab til Azure-infrastrukturtjenester, kan du tilpasse disse instruktioner, så de passer til din aktuelt udrullede infrastruktur.
  
Start først en Microsoft PowerShell-prompt.
  
Log på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Hent dit abonnementsnavn ved hjælp af denne kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt inden for anførselstegnene, herunder tegnene \< and > , med det korrekte navn.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Opret derefter en ny ressourcegruppe. Hvis du vil finde et entydigt navn på en ressourcegruppe, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Opret din nye ressourcegruppe med disse kommandoer. Erstat alt i anførselstegnene, herunder tegnene \< and > , med de korrekte navne.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Opret derefter et nyt virtuelt netværk og den virtuelle WIN10-maskine med disse kommandoer. Når du bliver bedt om det, skal du angive navnet og adgangskoden for den lokale administratorkonto for WIN10 og gemme dem på en sikker placering.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Fase 5: Slut din Windows 10 computer til Azure AD

Når den fysiske eller virtuelle maskine med Windows 10 Enterprise er oprettet, skal du logge på med en lokal administratorkonto.
  
> [!NOTE]
> For en virtuel maskine i Azure skal du bruge  [disse instruktioner](/azure/virtual-machines/windows/connect-logon) til at oprette forbindelse til den.
  
Derefter skal du slutte WIN10-computeren til den Azure AD lejer for dit Microsoft 365 E5 abonnement.
  
1. På skrivebordet på WIN10-computeren skal du vælge **Start > Indstillinger > Konti > Få adgang til arbejds- eller skole > Forbind**.

2. I dialogboksen **Konfigurer en arbejds- eller skolekonto** skal du vælge **Deltag i denne enhed for at Azure Active Directory**.

3. I **Arbejds- eller skolekonto** skal du angive navnet på den globale administratorkonto for dit Microsoft 365 E5 abonnement og derefter vælge **Næste**.

4. Angiv adgangskoden til din globale administratorkonto i **Angiv adgangskode**, og vælg derefter **Log på**.

5. Når du bliver bedt om at sikre dig, at dette er din organisation, skal du vælge **Deltag** og derefter vælge **Udført**.

6. Luk vinduet indstillinger.

Installer derefter Microsoft 365 Apps for enterprise på WIN10-computeren:
  
1. Åbn den Microsoft Edge browser, og log på [Microsoft 365 Administration](https://admin.microsoft.com) med legitimationsoplysningerne til din globale administratorkonto.

2. Vælg **Installér** Office under fanen **Hjem** Microsoft Office.

3. Når du bliver spurgt om, hvad du skal gøre, skal du vælge **Kør** og derefter vælge **Ja** for **Brugerkontokontrol**.

4. Vent på, at Office fuldfører installationen. Når du **ser Du er klar!**, skal du vælge **Luk** to gange.

Dit resulterende miljø ser sådan ud:

![Fase 5 i Microsoft 3656 Enterprise-testmiljøet.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Dette omfatter den WIN10-computer, der har:

- Deltager i Azure AD lejeren for dit Microsoft 365 E5 abonnement.
- Tilmeldt som en Azure AD enhed i Microsoft Intune (EMS).
- Microsoft 365 Apps for enterprise installeret.
  
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
