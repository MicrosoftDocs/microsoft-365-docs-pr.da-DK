---
title: Tildel Microsoft 365 licenser til brugerkonti med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: I denne artikel kan du lære, hvordan du bruger PowerShell til at tildele Microsoft 365 licens til brugere uden licens.
ms.openlocfilehash: b9f076e4856820d9f10e4cf92718dd6ddd3971c5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590539"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Tildel Microsoft 365 licenser til brugerkonti med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Brugere kan ikke bruge nogen Microsoft 365, før deres konto er blevet tildelt en licens fra en licensplan. Du kan bruge PowerShell til hurtigt at tildele licenser til konti uden licens. 

Brugerkonti skal først tildeles en placering. Angivelse af en placering er en påkrævet del af at oprette en ny brugerkonto [i Microsoft 365 Administration](../admin/add-users/add-users.md). 

Konti, der synkroniseres fra dit lokale Active Directory-domæneservices ikke har en placering angivet som standard. Du kan konfigurere en placering for disse konti fra:

- Den Microsoft 365 Administration
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - [Azure-portalen](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**Active** **DirectoryUsers** >  > en brugerkonto > **ProfileContact** >  **infoCountry** >  eller område).

>[!Note]
>[Få mere at vide om, hvordan du tildeler licenser til](../admin/manage/assign-licenses-to-users.md) brugerkonti Microsoft 365 Administration. Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Dernæst skal du oprette en liste over licensplaner for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Dernæst skal du hente logonnavnet på den konto, hvor du vil tilføje en licens, også kaldet brugerens hovednavn (UPN).

Dernæst skal du sikre dig, at brugerkontoen har fået tildelt en brugsplacering.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Hvis der ikke er tildelt en brugsplacering, kan du tildele en med disse kommandoer:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Til sidst skal du angive brugerens logonnavn og licensplannavn og køre disse kommandoer.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Bemærk, at vi begynder at fraråde dette modul, når funktionaliteten af dette modul er tilgængelig i den nyere [Azure Active Directory PowerShell til Graph](/powershell/azuread/v2/azureactivedirectory) modul. Vi anbefaler kunder, der opretter nye PowerShell-scripts, at bruge det nyere modul i stedet for dette modul.

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kør kommandoen `Get-MsolAccountSku` for at få vist de tilgængelige licensplaner og antallet af tilgængelige licenser i hver plan i organisationen. Antallet af tilgængelige licenser i hver plan er ActiveUnitsWarningUnitsConsumedUnits -  - . Du kan finde flere oplysninger om licensplaner, licenser og tjenester under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Kør denne kommando for at finde konti uden licens i organisationen.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Du kan kun tildele licenser til brugerkonti, der har egenskaben **Brugsplacering** angivet til en gyldig ISO 3166-1 alpha-2-landekode. EKSEMPELVIS USA for USA og FRANKRIG for Frankrig. Nogle Microsoft 365 tjenester er ikke tilgængelige i visse lande. Du kan finde flere oplysninger [under Om licensbegrænsninger](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Kør denne kommando for at finde konti, der **ikke har** en Brugsplacering-værdi.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Kør denne kommando **for at angive værdien UsageLocation** for en konto.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Eksempel:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Hvis du bruger **cmdlet'en Get-MsolUser** uden at bruge parameteren **-All** , returneres kun de første 500 konti.

### <a name="assigning-licenses-to-user-accounts"></a>Tildeling af licenser til brugerkonti
    
Hvis du vil tildele en licens til en bruger, skal du bruge følgende kommando i PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

I dette eksempel tildeles en licens fra **abonnementsplanen litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) til brugeren **belindan\@ litwareinc.com uden licens**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Kør denne kommando for at tildele en licens til alle brugere uden licens.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Du kan ikke tildele flere licenser til en bruger fra den samme licensplan. Hvis du ikke har nok tilgængelige licenser, tildeles licenserne til brugerne i den rækkefølge, de returneres af cmdlet'en **Get-MsolUser** , indtil de tilgængelige licenser er løbet ud.
>

I dette eksempel tildeles licenser fra **abonnementsplanen litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) til alle brugere uden licens:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

I dette eksempel tildeles de samme licenser til brugere uden licens i salgsafdelingen i USA:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Flyt en bruger til et andet abonnement (licensplan) med Azure Active Directory PowerShell til Graph abonnement

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Dernæst skal du hente logonnavnet på den brugerkonto, du vil skifte abonnementer for, også kaldet brugerens hovednavn (UPN).

Dernæst skal du oprette en liste over abonnementer (licensplaner) for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Dernæst skal du oprette en liste over de abonnementer, som brugerkontoen aktuelt har med disse kommandoer.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identificer det abonnement, som brugeren aktuelt har (FROM-abonnementet) og det abonnement, som brugeren flytter til (TO-abonnementet).

Til sidst skal du angive TO- og FROM-abonnementsnavnene (varenumre til SKU'en) og køre disse kommandoer.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Du kan bekræfte ændringen i abonnementet for brugerkontoen med disse kommandoer.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Se også

[Administrer brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
