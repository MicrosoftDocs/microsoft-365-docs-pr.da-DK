---
title: Administrer sikkerhedsgrupper med PowerShell
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
description: Få mere at vide om, hvordan du bruger PowerShell til at administrere sikkerhedsgrupper.
ms.openlocfilehash: c1ae74e60eb00e74efe5ad881e9ce3c0ebb3cf12
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099405"
---
# <a name="manage-security-groups-with-powershell"></a>Administrer sikkerhedsgrupper med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 som et alternativ til Microsoft 365 Administration til at administrere sikkerhedsgrupper. 

I denne artikel beskrives, hvordan du opretter, ændrer indstillinger og fjerner sikkerhedsgrupper. 

Når en kommandoblok i denne artikel kræver, at du angiver variabelværdier, skal du bruge disse trin.

1. Kopiér kommandoblokken til Udklipsholder, og indsæt den i Notesblok eller IE (PowerShell Integrated Script Environment).
2. Udfyld variabelværdierne, og fjern tegnene "<" og ">".
3. Kør kommandoerne i PowerShell-vinduet eller PowerShell ISE.

Se [Bevar medlemskab af sikkerhedsgrupper](maintain-group-membership-with-microsoft-365-powershell.md) for at administrere gruppemedlemskab med PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>Vis dine grupper

Brug denne kommando til at få vist alle dine grupper.

```powershell
Get-AzureADGroup
```
Brug disse kommandoer til at få vist indstillingerne for en bestemt gruppe efter dens viste navn.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Opret en ny gruppe

Brug denne kommando til at oprette en ny sikkerhedsgruppe.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>Rediger indstillingerne for en gruppe

Vis indstillingerne for gruppen med disse kommandoer.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Brug derefter artiklen [Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) til at bestemme, hvordan du ændrer en indstilling.

### <a name="remove-a-security-group"></a>Fjern en sikkerhedsgruppe

Brug disse kommandoer til at fjerne en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>Administrer ejerne af en sikkerhedsgruppe

Brug disse kommandoer til at få vist de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
Brug disse kommandoer til at føje en brugerkonto ved hjælp af brugerens **hovednavn (UPN)** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
Brug disse kommandoer til at føje en brugerkonto ved hjælp af dens **viste navn** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
Brug disse kommandoer til at fjerne en brugerkonto med dets **UPN** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

Brug disse kommandoer til at fjerne en brugerkonto med det **viste navn** til de aktuelle ejere af en sikkerhedsgruppe.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>Vis dine grupper

Brug denne kommando til at få vist alle dine grupper.

```powershell
Get-MsolGroup
```
Brug disse kommandoer til at få vist indstillingerne for en bestemt gruppe efter dens viste navn.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>Opret en ny gruppe

Brug denne kommando til at oprette en ny sikkerhedsgruppe.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>Rediger indstillingerne for en gruppe

Vis indstillingerne for gruppen med disse kommandoer.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

Brug derefter artiklen [Set-MsolGroup](/powershell/module/msonline/set-msolgroup) til at bestemme, hvordan du ændrer en indstilling.

### <a name="remove-a-security-group"></a>Fjern en sikkerhedsgruppe

Brug disse kommandoer til at fjerne en sikkerhedsgruppe.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)