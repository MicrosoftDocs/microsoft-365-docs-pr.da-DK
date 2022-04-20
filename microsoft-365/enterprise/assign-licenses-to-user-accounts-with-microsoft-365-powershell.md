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
description: I denne artikel kan du få mere at vide om, hvordan du bruger PowerShell til at tildele en Microsoft 365 licens til brugere uden licens.
ms.openlocfilehash: 3c92b3baaa0b8d67a5d5a626951b296be2516436
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941693"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>Tildel Microsoft 365 licenser til brugerkonti med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Brugerne kan ikke bruge nogen Microsoft 365 tjenester, før deres konto er blevet tildelt en licens fra en licensplan. Du kan bruge PowerShell til hurtigt at tildele licenser til konti uden licens. 

Brugerkonti skal først tildeles en placering. Angivelse af en placering er en nødvendig del af oprettelsen af en ny brugerkonto i [Microsoft 365 Administration](../admin/add-users/add-users.md). 

Der er ikke angivet en placering som standard for konti, der er synkroniseret fra dine Active Directory i det lokale miljø Domænetjenester. Du kan konfigurere en placering for disse konti fra:

- Microsoft 365 Administration
- [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
- [Azure Portal (](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)**Active** **DirectoryUsers** >  > brugerkonto > **ProfileContact** >  **infoCountry** >  eller område).

>[!Note]
>[Få mere at vide om, hvordan du tildeler licenser til brugerkonti](../admin/manage/assign-licenses-to-users.md) med Microsoft 365 Administration. Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Tildeling og fjernelse af licenser for en bruger kræver User.ReadWrite.All-tilladelsesomfanget eller en af de andre tilladelser, der er angivet på [siden "Tildel licens" Graph API-referenceside](/graph/api/user-assignlicense).

Der kræves tilladelsesomfanget Organization.Read.All for at læse de licenser, der er tilgængelige i lejeren.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Kør kommandoen `Get-MgSubscribedSku` for at få vist de tilgængelige licensplaner og antallet af tilgængelige licenser i hver plan i din organisation. Antallet af tilgængelige licenser i hver plan er **ActiveUnitsWarningUnitsConsumedUnits** -  - . Du kan få flere oplysninger om licensplaner, licenser og tjenester under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Kør denne kommando for at finde konti uden licens i din organisation.

```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All
```

Du kan kun tildele licenser til brugerkonti, hvor egenskaben **UsageLocation** er angivet til en gyldig ISO 3166-1 alpha-2-landekode. Det kan f.eks. være USA for USA og Frankrig. Nogle Microsoft 365 tjenester er ikke tilgængelige i visse lande. Du kan få flere oplysninger under [Om licensbegrænsninger](https://go.microsoft.com/fwlink/p/?LinkId=691730).

Kør denne kommando for at finde konti, der ikke har en **UsageLocation-værdi** .

```powershell
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }
```

Kør denne kommando for at angive værdien **UsageLocation** for en konto.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc
```

Eksempel:

```powershell
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US
```

Hvis du bruger **Cmdlet'en Get-MgUser** uden at bruge parameteren **-All** , returneres kun de første 100 konti.

### <a name="assigning-licenses-to-user-accounts"></a>Tildeling af licenser til brugerkonti

Hvis du vil tildele en licens til en bruger, skal du bruge følgende kommando i PowerShell.
  
```powershell
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()
```

I dette eksempel tildeles en licens fra **SPE_E5** (Microsoft 365 E5)-licensplanen til den bruger **uden licens, der er belindan\@ litwareinc.com**:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

I dette eksempel tildeles **SPE_E5** (Microsoft 365 E5) og **EMSPREMIUM** (ENTERPRISE MOBILITY + SECURITY E5) til brugeren **belindan\@ litwareinc.com**:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'
$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

I dette eksempel tildeles **SPE_E5** (Microsoft 365 E5) med **tjenesterne MICROSOFTBOOKINGS** (Microsoft Bookings) og **LOCKBOX_ENTERPRISE** (Customer Lockbox) slået fra:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

I dette eksempel opdateres en bruger med **SPE_E5** (Microsoft 365 E5) og deaktiver Sway- og formulartjenesteplaner, mens brugerens eksisterende deaktiverede planer er i den aktuelle tilstand:
  
```powershell
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

### <a name="assign-licenses-to-a-user-by-copying-the-license-assignment-from-another-user"></a>Tildel licenser til en bruger ved at kopiere licenstildelingen fra en anden bruger

I dette eksempel tildeles **jamesp\@ litwareinc.com** med den samme licensplan, der er anvendt på **belindan\@ litwareinc.com**:

```powershell
$mgUser = Get-MgUser -UserId "belindan@litwareinc.com"
Set-MgUserLicense -UserId "jamesp@litwareinc.com" -AddLicenses $mgUser.AssignedLicenses -RemoveLicenses @()
```

### <a name="move-a-user-to-a-different-subscription-license-plan"></a>Flyt en bruger til et andet abonnement (licensplan)

I dette eksempel opgraderes en bruger fra **SPE_E3** (Microsoft 365 E3)-licensplanen til **SPE_E5** (Microsoft 365 E5)-licensplanen:

```powershell
$e3Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E3'
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

# Unassign E3
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{} -RemoveLicenses @($e3Sku.SkuId)
# Assign E5
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

Du kan bekræfte ændringen i abonnementet for brugerkontoen med denne kommando.

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

>[!Note]
>Den Set-AzureADUserLicense cmdlet er planlagt til at blive trukket tilbage. Overfør dine scripts til Graph SDK'ens Set-MgUserLicense-cmdlet som beskrevet ovenfor. Du kan få flere oplysninger under [Overfør dine apps for at få adgang til API'erne til licensstyring fra Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Derefter skal du angive licensplanerne for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Derefter skal du hente logonnavnet på den konto, du vil føje en licens til, også kendt som brugerens hovednavn (UPN).

Kontrollér derefter, at brugerkontoen har fået tildelt en anvendelsesplacering.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Hvis der ikke er tildelt en anvendelsesplacering, kan du tildele en med disse kommandoer:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Til sidst skal du angive brugerlogonnavnet og licensplanens navn og køre disse kommandoer.

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

>[!Note]
>Cmdlet'erne Set-MsolUserLicense og New-MsolUser (-LicenseAssignment) er planlagt til at blive udgået. Overfør dine scripts til Graph SDK'ens Set-MgUserLicense-cmdlet som beskrevet ovenfor. Du kan få flere oplysninger under [Overfør dine apps for at få adgang til API'erne til licensstyring fra Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kør kommandoen `Get-MsolAccountSku` for at få vist de tilgængelige licensplaner og antallet af tilgængelige licenser i hver plan i din organisation. Antallet af tilgængelige licenser i hver plan er **ActiveUnitsWarningUnitsConsumedUnits** -  - . Du kan få flere oplysninger om licensplaner, licenser og tjenester under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Kør denne kommando for at finde konti uden licens i din organisation.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Du kan kun tildele licenser til brugerkonti, hvor egenskaben **UsageLocation** er angivet til en gyldig ISO 3166-1 alpha-2-landekode. Det kan f.eks. være USA for USA og Frankrig. Nogle Microsoft 365 tjenester er ikke tilgængelige i visse lande. Du kan få flere oplysninger under [Om licensbegrænsninger](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Kør denne kommando for at finde konti, der ikke har en **UsageLocation-værdi** .

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Kør denne kommando for at angive værdien **UsageLocation** for en konto.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Eksempel:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Hvis du bruger **Cmdlet'en Get-MsolUser** uden at bruge parameteren **-All** , returneres kun de første 500 konti.

### <a name="assigning-licenses-to-user-accounts"></a>Tildeling af licenser til brugerkonti
    
Hvis du vil tildele en licens til en bruger, skal du bruge følgende kommando i PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

I dette eksempel tildeles en licens fra **litwareinc:ENTERPRISEPACK**(Office 365 Enterprise E3)-licensplanen til den bruger **uden licens, der er belindan\@ litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Hvis du vil tildele en licens til alle brugere uden licens, skal du køre denne kommando.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>Du kan ikke tildele flere licenser til en bruger fra den samme licensplan. Hvis du ikke har nok tilgængelige licenser, tildeles licenserne til brugerne i den rækkefølge, de returneres af **Get-MsolUser-cmdlet'en** , indtil de tilgængelige licenser udløber.
>

I dette eksempel tildeles licenser fra **litwareinc:ENTERPRISEPACK-licensplanen** (Office 365 Enterprise E3) til alle brugere uden licens:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

I dette eksempel tildeles de samme licenser til brugere uden licens i salgsafdelingen i USA:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Flyt en bruger til et andet abonnement (licensplan) med modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Derefter skal du hente logonnavnet på den brugerkonto, du vil skifte abonnement for, også kendt som brugerens hovednavn (UPN).

Derefter skal du angive abonnementerne (licensplaner) for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Derefter skal du angive de abonnementer, som brugerkontoen i øjeblikket har med disse kommandoer.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identificer det abonnement, som brugeren aktuelt har (FROM-abonnementet) og det abonnement, som brugeren flytter til (TIL-abonnementet).

Til sidst skal du angive TIL- og FROM-abonnementsnavnene (SKU-delnumre) og køre disse kommandoer.

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
