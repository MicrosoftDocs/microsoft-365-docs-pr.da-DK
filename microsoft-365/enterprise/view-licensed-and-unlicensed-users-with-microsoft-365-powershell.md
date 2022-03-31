---
title: Se brugere med og uden licens Microsoft 365 brugere med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel forklares det, hvordan du bruger PowerShell til at få vist licenserede og Microsoft 365-brugerkonti.
ms.openlocfilehash: 015cb63fd692131d77799fe30fc94c6214bb01d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601580"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>Se brugere med og uden licens Microsoft 365 brugere med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Brugerkonti i din Microsoft 365-organisation har muligvis nogle, alle eller ingen af de tilgængelige licenser, der er tildelt dem fra de licensplaner, der er tilgængelige i din organisation. Du kan bruge PowerShell til Microsoft 365 hurtigt at finde brugere med licens og uden licens i organisationen.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
For at få vist listen over alle brugerkonti i organisationen, der IKKE har fået tildelt nogen af dine licensplaner (brugere uden licens), skal du køre følgende kommando:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

For at få vist listen over alle brugerkonti i organisationen, der har fået tildelt en af dine licensplaner (licenserede brugere), skal du køre følgende kommando:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>Hvis du vil have vist alle brugerne i dit abonnement, skal du bruge `Get-AzureAdUser -All $true` kommandoen.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Hvis du vil have vist listen over alle brugerkonti og deres licensstatus i din organisation, skal du køre følgende kommando i PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Kør følgende kommando for at få vist listen over alle brugerkonti uden licens i organisationen:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Kør følgende kommando for at få vist listen over alle licenserede brugerkonti i organisationen:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
