---
title: Fjern Microsoft 365 licenser fra brugerkonti med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Beskriver, hvordan du bruger PowerShell til at fjerne Microsoft 365 licenser, der tidligere er tildelt til brugere.
ms.openlocfilehash: c3317c651c561da4c8650e45ba3b64a135a1f6ce
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823140"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>Fjern Microsoft 365 licenser fra brugerkonti med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

>[!Note]
>[Få mere at vide om, hvordan du fjerner licenser fra brugerkonti](../admin/manage/remove-licenses-from-users.md) med Microsoft 365 Administration. Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Tildeling og fjernelse af licenser for en bruger kræver User.ReadWrite.All-tilladelsesomfanget eller en af de andre tilladelser, der er angivet på [siden "Tildel licens" Graph API-referenceside](/graph/api/user-assignlicense).

Der kræves tilladelsesomfanget Organization.Read.All for at læse de licenser, der er tilgængelige i lejeren.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Hvis du vil have vist licensplanoplysningerne i din organisation, skal du se følgende emner:

- [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)

- [Få vist oplysninger om kontolicens og -tjeneste med PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)

### <a name="removing-licenses-from-user-accounts"></a>Fjernelse af licenser fra brugerkonti

Hvis du vil fjerne licenser fra en eksisterende brugerkonto, skal du bruge følgende syntaks:
  
```powershell
Set-MgUserLicense -UserId "<Account>" -RemoveLicenses @("<AccountSkuId1>") -AddLicenses @{}
```

I dette eksempel fjernes **SPE_E5** (Microsoft 365 E5)-licensplanen fra **brugerens BelindaN@litwareinc.com**:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -RemoveLicenses @($e5Sku.SkuId) -AddLicenses @{}
```

Hvis du vil fjerne alle licenser fra en gruppe af eksisterende brugere med licens, skal du bruge følgende syntaks:

```powershell
$licensedUsers = Get-MgUser -Filter 'assignedLicenses/$count ne 0' `
    -ConsistencyLevel eventual -CountVariable licensedUserCount -All `
    -Select UserPrincipalName,DisplayName,AssignedLicenses

foreach($user in $licensedUsers)
{
    $licencesToRemove = $user.AssignedLicenses | Select -ExpandProperty SkuId
    $user = Set-MgUserLicense -UserId $user.UserPrincipalName -RemoveLicenses $licencesToRemove -AddLicenses @{} 
}
```

En anden måde at frigøre en licens på er ved at slette brugerkontoen. Du kan finde flere oplysninger under [Slet og gendan brugerkonti med PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

>Den Set-AzureADUserLicense cmdlet er planlagt til at blive trukket tilbage. Overfør dine scripts til Graph SDK'ens Set-MgUserLicense-cmdlet som beskrevet ovenfor. Du kan få flere oplysninger under [Overfør dine apps for at få adgang til API'erne til licensstyring fra Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Derefter skal du angive licensplanerne for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Derefter skal du hente logonnavnet på den konto, du vil fjerne en licens for, også kendt som brugerens hovednavn (UPN).

Til sidst skal du angive navnene på brugerlogon og licensplan, fjerne tegnene "<" og ">" og køre disse kommandoer.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

Hvis du vil fjerne alle licenser for en bestemt brugerkonto, skal du angive brugerens logonnavn, fjerne tegnene "<" og ">" og køre disse kommandoer.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $Licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

>[!Note]
>Cmdlet'erne Set-MsolUserLicense og New-MsolUser (-LicenseAssignment) er planlagt til at blive udgået. Overfør dine scripts til Graph SDK'ens Set-MgUserLicense-cmdlet som beskrevet ovenfor. Du kan få flere oplysninger under [Overfør dine apps for at få adgang til API'erne til licensstyring fra Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Hvis du vil have vist licensplanen (**AccountSkuID**) i din organisation, skal du se følgende emner:
    
  - [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [Få vist oplysninger om kontolicens og -tjeneste med PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
Hvis du bruger **Cmdlet'en Get-MsolUser** uden at bruge parameteren _-All_ , returneres kun de første 500 konti.
    
### <a name="removing-licenses-from-user-accounts"></a>Fjernelse af licenser fra brugerkonti

Hvis du vil fjerne licenser fra en eksisterende brugerkonto, skal du bruge følgende syntaks:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

I dette eksempel fjernes **licensen litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) fra brugerkontoen BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Du kan ikke bruge cmdlet'en `Set-MsolUserLicense` til at fjerne tildelingen af brugere fra *annullerede* licenser. Det skal du gøre enkeltvist for hver brugerkonto i Microsoft 365 Administration.
>

Hvis du vil fjerne alle licenser fra en gruppe af eksisterende brugere med licens, skal du bruge en af følgende metoder:
  
- **Filtrer kontiene baseret på en eksisterende kontoattribut** Det gør du ved at bruge følgende syntaks:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

I dette eksempel fjernes alle licenser fra alle brugerkonti i salgsafdelingen i USA.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Brug en liste over bestemte konti for en bestemt licens** Det gør du ved at udføre følgende trin:
    
1. Opret og gem en tekstfil, der indeholder én konto på hver linje som denne:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Brug følgende syntaks:
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
I dette eksempel fjernes **licensen litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) fra de brugerkonti, der er defineret i tekstfilen C:\My Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

Hvis du vil fjerne alle licenser fra alle eksisterende brugerkonti, skal du bruge følgende syntaks:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

En anden måde at frigøre en licens på er ved at slette brugerkontoen. Du kan finde flere oplysninger under [Slet og gendan brugerkonti med PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
