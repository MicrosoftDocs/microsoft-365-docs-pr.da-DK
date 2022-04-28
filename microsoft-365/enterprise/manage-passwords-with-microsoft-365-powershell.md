---
title: Administrer adgangskoder med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du bruger PowerShell til at administrere adgangskoder.
ms.openlocfilehash: e980e9c4c2511ea1f84df870c790a61a047c3a90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091561"
---
# <a name="manage-passwords-with-powershell"></a>Administrer adgangskoder med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 som et alternativ til Microsoft 365 Administration til at administrere adgangskoder i Microsoft 365. 

Når en kommandoblok i denne artikel kræver, at du angiver variabelværdier, skal du bruge disse trin.

1. Kopiér kommandoblokken til Udklipsholder, og indsæt den i Notesblok eller IE (PowerShell Integrated Script Environment).
2. Udfyld variabelværdierne, og fjern tegnene "<" og ">".
3. Kør kommandoerne i PowerShell-vinduet eller PowerShell ISE.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="set-a-password"></a>Angiv en adgangskode

Brug disse kommandoer til at angive en adgangskode til en brugerkonto.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword
```
### <a name="force-a-user-to-change-their-password"></a>Tving en bruger til at ændre sin adgangskode

Brug disse kommandoer til at angive en adgangskode og tvinge en bruger til at ændre sin nye adgangskode.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -EnforceChangePasswordPolicy $true
```

Brug disse kommandoer til at angive en adgangskode og tvinge en bruger til at ændre sin nye adgangskode, næste gang brugeren logger på.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="set-a-password"></a>Angiv en adgangskode

Brug disse kommandoer til at angive en adgangskode til en brugerkonto.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>Tving en bruger til at ændre sin adgangskode

Brug disse kommandoer til at tvinge en bruger til at ændre sin adgangskode.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)

