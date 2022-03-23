---
title: Administrer sikkerhedsgrupper med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du bruger PowerShell til at administrere sikkerhedsgrupper.
ms.openlocfilehash: d07296b88e626e854c57152a079cc96e1e23e8d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593366"
---
# <a name="manage-security-groups-with-powershell"></a>Administrer sikkerhedsgrupper med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 som et alternativ til Microsoft 365 Administration til at administrere sikkerhedsgrupper. 

I denne artikel beskrives det, hvordan du opretter, ændrer indstillinger og fjerner sikkerhedsgrupper. 

Når en kommandoblok i denne artikel kræver, at du angiver variable værdier, skal du følge disse trin.

1. Kopiér kommandoblokken til Udklipsholder, og sæt den ind Notesblok eller det integrerede scriptmiljø (ISE) i PowerShell.
2. Udfyld variable værdier, og fjern tegnene "<" og ">".
3. Kør kommandoerne i PowerShell-vinduet eller PowerShell ISE.

Se [Bevar medlemskab af sikkerhedsgrupper](maintain-group-membership-with-microsoft-365-powershell.md) for at administrere gruppemedlemskab med PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Opliste dine grupper

Brug denne kommando til at få vist alle dine grupper.

```powershell
Get-AzureADGroup
```
Brug disse kommandoer til at få vist indstillingerne for en bestemt gruppe ved hjælp af dens viste navn.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Opret en ny gruppe

Brug denne kommando til at oprette en ny sikkerhedsgruppe.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Ændre indstillingerne for en gruppe

Vis indstillingerne for gruppen med disse kommandoer.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Brug derefter artiklen [Set-AzureADGroup til](/powershell/module/azuread/set-azureadgroup) at afgøre, hvordan du ændrer en indstilling.

### <a name="remove-a-security-group"></a>Fjerne en sikkerhedsgruppe

Brug disse kommandoer til at fjerne en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>Administrere ejerne af en sikkerhedsgruppe

Brug disse kommandoer til at få vist de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
Brug disse kommandoer til at tilføje en brugerkonto med brugerens **hovednavn (UPN)** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Brug disse kommandoer til at føje en brugerkonto med det **viste navn** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Brug disse kommandoer til at fjerne en brugerkonto fra **upn'et** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Brug disse kommandoer til at fjerne en brugerkonto med **dens viste navn** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Opliste dine grupper

Brug denne kommando til at få vist alle dine grupper.

```powershell
Get-MsolGroup
```
Brug disse kommandoer til at få vist indstillingerne for en bestemt gruppe ved hjælp af dens viste navn.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Opret en ny gruppe

Brug denne kommando til at oprette en ny sikkerhedsgruppe.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Ændre indstillingerne for en gruppe

Vis indstillingerne for gruppen med disse kommandoer.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Brug derefter artiklen [Set-MsolGroup til](/powershell/module/msonline/set-msolgroup) at afgøre, hvordan du ændrer en indstilling.

### <a name="remove-a-security-group"></a>Fjerne en sikkerhedsgruppe

Brug disse kommandoer til at fjerne en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)