---
title: Få vist licenserede og ikke-licenserede Microsoft 365 brugere med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: I denne artikel forklares det, hvordan du bruger PowerShell til at få vist licenserede og ikke-licenserede Microsoft 365 brugerkonti.
ms.openlocfilehash: 65dcc8e397f9ad56679b880f50caa99a51e4a4c5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095526"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Få vist licenserede og ikke-licenserede Microsoft 365 brugere med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Brugerkonti i din Microsoft 365 organisation kan have nogle, alle eller ingen af de tilgængelige licenser tildelt til dem fra de licensplaner, der er tilgængelige i din organisation. Du kan bruge PowerShell til Microsoft 365 til hurtigt at finde brugere med licens og uden licens i din organisation.

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Hvis du vil læse brugeregenskaber, herunder licensoplysninger, skal du have tilladelsesomfanget User.Read.All eller en af de andre tilladelser, der er angivet på [siden "Hent en bruger" Graph API-referenceside](/graph/api/user-get).

Der kræves tilladelsesomfanget Organization.Read.All for at læse de licenser, der er tilgængelige i lejeren.

```powershell
Connect-Graph -Scopes User.Read.All, Organization.Read.All
```

Hvis du vil have vist licensoplysningerne for en bestemt brugerkonto, skal du køre følgende kommando:
  
```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Eksempel:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

Kør følgende kommando for at få vist listen over alle brugerkonti i organisationen, der IKKE er tildelt nogen af dine licensplaner (brugere uden licens):
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users."
```

Kør følgende kommando for at få vist listen over alle medlemsbrugerkonti (undtagen gæster) i din organisation, der IKKE har fået tildelt nogen af dine licensplaner (brugere uden licens):
  
```powershell
Get-MgUser -Filter "assignedLicenses/`$count eq 0 and userType eq 'Member'" -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users (excluding guests)."
```

Kør følgende kommando for at få vist listen over alle brugerkonti i organisationen, der er tildelt en af dine licensplaner (licenserede brugere):
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count ne 0' -ConsistencyLevel eventual -CountVariable licensedUserCount -All -Select UserPrincipalName,DisplayName,AssignedLicenses | Format-Table -Property UserPrincipalName,DisplayName,AssignedLicenses

Write-Host "Found $licensedUserCount licensed users."
```

Kør følgende kommando for at få vist listen over alle brugerkonti i din organisation, der har en tildelt E5-licens:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

Get-MgUser -Filter "assignedLicenses/any(x:x/skuId eq $($e5sku.SkuId) )" -ConsistencyLevel eventual -CountVariable e5licensedUserCount -All

Write-Host "Found $e5licensedUserCount E5 licensed users."
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Kør følgende kommando for at få vist listen over alle brugerkonti i organisationen, der IKKE er tildelt nogen af dine licensplaner (brugere uden licens):
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Kør følgende kommando for at få vist listen over alle brugerkonti i organisationen, der er tildelt en af dine licensplaner (licenserede brugere):
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Hvis du vil have vist alle brugerne i dit abonnement, skal du bruge `Get-AzureAdUser -All $true` kommandoen .
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Hvis du vil have vist listen over alle brugerkonti og deres licensstatus i din organisation, skal du køre følgende kommando i PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Hvis du vil have vist en liste over alle brugerkonti uden licens i din organisation, skal du køre følgende kommando:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Hvis du vil have vist en liste over alle brugerkonti med licens i din organisation, skal du køre følgende kommando:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
