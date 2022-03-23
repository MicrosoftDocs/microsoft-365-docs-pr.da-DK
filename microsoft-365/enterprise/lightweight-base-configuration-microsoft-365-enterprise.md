---
title: Let basiskonfiguration
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
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Brug denne Test Lab-vejledning til at oprette et let testmiljø til test Microsoft 365 til virksomheder.
ms.openlocfilehash: 742fc93b64d2e3c1d858931eb7dbc591ebcd8e9d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588684"
---
# <a name="the-lightweight-base-configuration"></a>Den lette basiskonfiguration

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Denne artikel beskriver, hvordan du opretter et forenklet miljø med et Microsoft 365 E5 abonnement og en computer, der Windows 10 Enterprise.

![Det lette Microsoft 3656 Enterprise-testmiljø.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Oprettelse af et let testmiljø omfatter fem faser:
- [Fase 1: Opret dit Microsoft 365 E5 abonnement](#phase-1-create-your-microsoft-365-e5-subscription)
- [Fase 2: Konfigurer dit Office 365-prøveabonnement](#phase-2-configure-your-office-365-trial-subscription)
- [Fase 3: Tilføj et Microsoft 365 E5-prøveabonnement](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Fase 4: Opret en Windows 10 Enterprise computer](#phase-4-create-a-windows-10-enterprise-computer)
- [Fase 5: Deltag i Windows 10 til Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

Brug det resulterende miljø til at teste funktionerne og funktionaliteten [i Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/enterprise).

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Du kan finde et visuelt kort til alle artikler i Microsoft 365 for Enterprise Test Lab Guide stack i [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Det kan være en ide at udskrive denne artikel for at registrere de specifikke oplysninger, du skal bruge til dette miljø i løbet af de 30 dage, du Office 365-prøveabonnementet. Du kan nemt forlænge trail-abonnementet med yderligere 30 dage. For et permanent testmiljø skal du oprette et nyt betalt abonnement med en separat Azure AD-lejer og et lille antal licenser.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Fase 1: Opret dit Microsoft 365 E5 abonnement

Vi starter med et Microsoft 365 E5-prøveabonnement og føjer derefter Microsoft 365 E5-abonnementet til det.

>[!NOTE]
>Vi anbefaler, at du opretter et prøveabonnement på Office 365 så dit testmiljø har en separat Azure AD-lejer fra alle betalte abonnementer, du aktuelt har. Denne adskillelse betyder, at du kan tilføje og fjerne brugere og grupper i testlejeren uden at påvirke dine produktionsabonnementer.

For at starte Microsoft 365 E5 dit prøveabonnement skal du først have et fiktivt firmanavn og en ny Microsoft-konto.
  
1. Vi anbefaler, at du bruger en variant af firmanavnet Contoso som firmanavn, som er et fiktivt firma, der bruges i Microsoft-eksempelindhold, men det er ikke påkrævet. Optag dit fiktive firmanavn her: ![Linje.](../media/Common-Images/TableLine.png)
    
2. Hvis du vil tilmelde dig en ny Microsoft-konto, skal du [https://outlook.com](https://outlook.com) gå til og oprette en konto med en ny mailkonto og adresse. Du skal bruge denne konto til at tilmelde dig Office 365.
    
    - Optag for- og efternavnet på din nye konto her: ![Linje.](../media/Common-Images/TableLine.png)
    
    - Optag den nye mailadresse til mailkontoen her: ![Linje.](../media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Tilmeld dig et Office 365 E5-prøveabonnement

1. I din browser skal du gå til [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. I trin 1 på **siden Tak, fordi du Office 365 E5** din nye mailadresse.
3. I trin 2 i abonnementsprocessen skal du angive de ønskede oplysninger og derefter udføre bekræftelsen.
4. I trin 3 skal du angive et organisationsnavn og derefter et kontonavn, som skal være den globale administrator for abonnementet.
5. I trin 4 skal du registrere logonsiden her (vælg og kopiér): ![Linje.](../media/Common-Images/TableLine.png)
6. Optag bruger-id'et her: ![Line.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   Optag den adgangskode, du har angivet, på et sikkert sted.
   Denne værdi kaldes for navnet på **den globale administrator**.
7. Vælg **Gå til konfiguration**.
8. I Office 365 E5 skal du vælge Fortsæt med at bruge ***din organization.onmicrosoft.com* til** mail og logge på og derefter vælge **Afslut, og fortsæt senere**.

Du bør kunne se Microsoft 365 Administration.
    
## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Fase 2: Konfigurer dit Office 365-prøveabonnement

I denne fase skal du konfigurere dit abonnement med flere brugere og tildele dem Office 365 E5 licenser.
  
Hvis du vil oprette forbindelse til dit abonnement med Azure Active Directory PowerShell til Graph-modulet fra din computer, skal du bruge instruktionerne [i Forbind til Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
    
I dialogboksen **Windows PowerShell legitimationsanmodning** skal du skrive navnet på den globale administrator (f.eks *jdoe@contosotoycompany.onmicrosoft.com*) og en adgangskode.
  
Udfyld organisationens navn (f.eks. *contosotoycompany*), den totegns landekode for din placering, en fælles kontoadgangskode, og kør derefter følgende kommandoer fra prompten i PowerShell:

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
> Brug af en fælles adgangskode her er til automatisering og nem konfiguration i et testmiljø. Dette frarådes naturligvis på det kraftigste i forbindelse med produktionsabonnementer. 

### <a name="record-key-information-for-future-reference"></a>Registrere vigtige oplysninger til fremtidig brug

Hvis du ikke allerede har registreret disse værdier, skal du optage dem nu:
  
- Navn på global administrator: ![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com (fra trin 6 i fase 1)
    
    Optag også adgangskoden til denne konto på et sikkert sted.
    
- Organisationens navn på prøveabonnement: ![Linje.](../media/Common-Images/TableLine.png) (fra trin 4 i fase 1)
    
- For at få vist kontiene for Bruger 2, Bruger 3, Bruger 4 og Bruger 5 skal du køre følgende kommando fra Windows Azure Active Directory-modulet for at Windows PowerShell meddelelse:
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Optag kontonavnene her:
    
  - Bruger 2 kontonavn: bruger2 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Bruger 3 kontonavn: bruger3 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Bruger 4 kontonavn: bruger4 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Bruger 5 kontonavn: bruger5 @![Linje.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
    Optag også den fælles adgangskode til disse konti på et sikkert sted.
   
### <a name="using-an-office-365-test-environment"></a>Brug af Office 365 testmiljø

Hvis du kun har brug for Office 365 testmiljø, behøver du ikke at læse resten af denne artikel.

Du kan finde flere Test Lab-vejledninger, der gælder for både Office 365 og Microsoft 365, [Microsoft 365 for Enterprise Test Lab Guides](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Fase 3: Tilføj et Microsoft 365 E5-prøveabonnement

I denne fase tilmelder du dig det Microsoft 365 E5-prøveabonnement og føjer det til den samme organisation som Office 365 E5-prøveabonnement.
  
Først skal du tilføje Microsoft 365 E5-prøveabonnementet og tildele den nye Microsoft 365 til din globale administratorkonto.
  
1. I et privat vindue i en internetbrowser skal du bruge legitimationsoplysningerne for din globale administratorkonto til at logge på Microsoft 365 Administration på [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. På siden **Microsoft 365 Administration** navigation skal du vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**BillingPurchase-tjenester i venstre navigationsrude**</a>. > 
    
3. På siden **Køb tjenester** skal du **vælge Microsoft 365 E5** og derefter vælge **Hent gratis prøveversion**.

4. På siden **Microsoft 365 E5 prøveversion** skal du beslutte at modtage en sms eller et telefonopkald, angive dit telefonnummer og derefter vælge Sms **mig** eller **Ring til mig**. Udfør bekræftelsen.

5. På siden **Bekræft din ordre** skal du vælge **Prøv nu**.

6. På siden **Ordrekvittering** skal du vælge **Fortsæt**.

7. Vælg Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Brugereaktive brugere**</a> >  i dialogboksen Indstillinger.

8. Vælg **din administratorkonto** i Aktive brugere.

9. Vælg **Licenser og apps**.

10. Deaktiver licensen for Office 365 Enterprise E5, og aktivér licensen for Microsoft 365 E5.

11. Vælg **Gem ændringer**, og luk derefter oplysningsruden for brugerkontoen.

Gentag derefter trin 8 til 11 i den forrige procedure for alle dine andre konti (Bruger 2, Bruger 3, Bruger 4 og Bruger 5).
  
> [!NOTE]
> Længden af det Microsoft 365 E5 er 30 dage. For et permanent testmiljø skal du konvertere dette prøveabonnement til et betalt abonnement med et lille antal licenser.
  
Dit testmiljø har nu:
  
- Et Microsoft 365 E5-prøveabonnement.
- Alle dine relevante brugerkonti (enten kun den globale administrator eller alle fem brugerkonti) er aktiveret til at bruge Microsoft 365 E5.
    
Din resulterende konfiguration, som tilføjer Microsoft 365 E5, ser sådan ud:
  
![Fase 3 i Microsoft 3656 Enterprise-testmiljøet.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Fase 4: Opret en Windows 10 Enterprise computer

I denne fase opretter du en enkeltstående computer, der Windows 10 Enterprise som enten en fysisk computer, en virtuel maskine eller en virtuel Azure-computer.
  
### <a name="physical-computer"></a>Fysisk computer

På en personlig computer skal du installere Windows 10 Enterprise. Du kan downloade Windows 10 Enterprise [prøveversionen her](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Virtuel maskine

Brug den foretrukne hypervisor til at oprette en virtuel maskine, og installér Windows 10 Enterprise på den. Du kan downloade Windows 10 Enterprise [prøveversionen her](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Virtuel maskine i Azure

Hvis du Windows 10 en virtuel maskine i Microsoft Azure, skal du ***have et Visual Studio-baseret*** abonnement, der har adgang til billedet for Windows 10 Enterprise. Andre typer Azure-abonnementer, f.eks. prøveabonnementer og betalte abonnementer, har ikke adgang til dette billede. Du kan finde de seneste oplysninger [i Windows klient i Azure til udviklings-/testscenarier](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> Følgende kommandosæt bruger den nyeste version af Azure PowerShell. Se [Introduktion til Azure PowerShell cmdlet'er](/powershell/azureps-cmdlets-docs/). Disse kommandosæt opbygger en Windows 10 Enterprise virtuel maskine med navnet WIN10 og al dens nødvendige infrastruktur, herunder en ressourcegruppe, en lagerkonto og et virtuelt netværk. Hvis du allerede kender til Azure-infrastrukturtjenester, kan du tilpasse disse instruktioner til din nuværende installerede infrastruktur.
  
Start først en Microsoft PowerShell-prompt.
  
Log på din Azure-konto med denne kommando.
  
```powershell
Connect-AzAccount
```

Få dit abonnementsnavn ved hjælp af denne kommando.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Angiv dit Azure-abonnement. Erstat alt mellem anførselstegnene, inklusive \< and > tegnene, med det korrekte navn.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Dernæst skal du oprette en ny ressourcegruppe. Hvis du vil finde et entydigt ressourcegruppenavn, skal du bruge denne kommando til at angive dine eksisterende ressourcegrupper.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Opret din nye ressourcegruppe med disse kommandoer. Erstat alt mellem anførselstegnene, inklusive \< and > tegnene, med de korrekte navne.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Dernæst skal du oprette et nyt virtuelt netværk og den virtuelle WIN10-maskine med disse kommandoer. Når du bliver bedt om det, skal du angive navn og adgangskode for den lokale administratorkonto til WIN10 og gemme disse på et sikkert sted.
  
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

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Fase 5: Deltag i Windows 10 til Azure AD

Når den fysiske eller virtuelle maskine med Windows 10 Enterprise, skal du logge på med en lokal administratorkonto.
  
> [!NOTE]
> For en virtuel maskine i Azure skal du bruge  [denne vejledning til](/azure/virtual-machines/windows/connect-logon) at oprette forbindelse til den.
  
Derefter skal du slutte computeren WIN10 til Azure AD-lejeren for Microsoft 365 E5 abonnementet.
  
1. På skrivebordet på WIN10-computeren skal du vælge **Start > Indstillinger > Konti > Access til arbejds- eller > Forbind**.
    
2. I dialogboksen **Konfigurer en arbejds- eller skolekonto skal** du vælge **Deltag i denne enhed for at Azure Active Directory**.
    
3. I **arbejds- eller skolekonto** skal du angive navnet på den globale administratorkonto for Microsoft 365 E5 og derefter vælge **Næste**.
    
4. I **Angiv adgangskode** skal du angive adgangskoden til din globale administratorkonto og derefter vælge **Log på**.
    
5. Når du bliver bedt om at sikre, at dette er din organisation, **skal du vælge Deltag** og derefter vælge **Udført**.
    
6. Luk vinduet Indstillinger.
    
Derefter skal du Microsoft 365 Apps for enterprise på WIN10-computeren:
  
1. Åbn browseren Microsoft Edge, og log på Microsoft 365 Administration [med](https://admin.microsoft.com) legitimationsoplysningerne for din globale administratorkonto.
    
2. På fanen **Microsoft Office Hjem** skal du vælge **Installér Office**.
    
3. Når du bliver spurgt, hvad du skal gøre, **skal** du vælge Kør og **derefter vælge Ja** **til kontrol af brugerkonti**.
    
4. Vent på Office installationen fuldføres. Når du ser **Du er klar! skal du** vælge **Luk to** gange.
    
Det resulterende miljø ser sådan ud:

![Fase 5 af Microsoft 3656 Enterprise-testmiljøet.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Dette omfatter den WIN10-computer, der har:

- Tilmeldte sig Azure AD-lejeren for Microsoft 365 E5 abonnement.
- Tilmeldt som Azure AD-enhed i Microsoft Intune (EMS).
- Microsoft 365 Apps for enterprise installeret.
  
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
