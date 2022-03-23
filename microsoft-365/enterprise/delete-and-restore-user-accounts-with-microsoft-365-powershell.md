---
title: Slet Microsoft 365-brugerkonti med PowerShell
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Lær at bruge forskellige moduler i PowerShell til at slette Microsoft 365 brugerkonti.
ms.openlocfilehash: dc1e5c53f2d356f0585da5a0a5285b9af28dc8f0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589745"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Slet Microsoft 365-brugerkonti med PowerShell

Du kan bruge PowerShell til Microsoft 365 til at slette og gendanne brugerkonti.

>[!Note]
>Lær, hvordan [du gendanner en brugerkonto](../admin/add-users/restore-user.md) ved hjælp af Microsoft 365 Administration.
>
>Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Når du har forbundet, kan du bruge følgende syntaks til at fjerne en individuel brugerkonto:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Dette eksempel fjerner brugerkonto *fabricec\@ litwareinc.com*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> Parameteren *-ObjectID* i cmdlet'en **Remove-AzureADUser** accepterer enten kontoens logonnavn, også kaldet brugerens hovednavn eller kontoens objekt-id.
  
Hvis du vil have vist kontonavnet baseret på brugerens navn, skal du bruge følgende kommandoer:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

I dette eksempel vises kontonavnet for brugeren *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Hvis du vil fjerne en konto, der er baseret på brugerens viste navn, skal du bruge følgende kommandoer:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Når du sletter en brugerkonto via Microsoft Azure Active Directory-Windows PowerShell, slettes kontoen ikke permanent. Du kan gendanne den slettede brugerkonto inden for 30 dage.

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Hvis du vil slette en brugerkonto, skal du bruge følgende syntaks:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
>

I dette eksempel slettes brugerkontoen *BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Hvis du vil gendanne en slettet brugerkonto inden for perioden på 30 dage, skal du bruge følgende syntaks:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

I dette eksempel gendannes den slettede *konto BelindaN\@ litwareinc.com*.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> Kør følgende kommando for at få vist listen over slettede brugere, der kan gendannes:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> Hvis brugerkontoens oprindelige hovednavn bruges af en anden konto, skal du bruge _NewUserPrincipalName-parameteren_ i stedet for _UserPrincipalName_ til at angive et andet brugerens hovednavn, når du gendanner brugerkontoen.


## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)