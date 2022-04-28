---
title: Vedligehold medlemskab af sikkerhedsgrupper med PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Få mere at vide om, hvordan du bruger PowerShell til at vedligeholde medlemskabet i Microsoft 365 grupper.
ms.openlocfilehash: 48720d5f3922598feec5a64eaa2c2532e17248ad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095680"
---
# <a name="maintain-security-group-membership-with-powershell"></a>Vedligehold medlemskab af sikkerhedsgrupper med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 som et alternativ til Microsoft 365 Administration til at vedligeholde medlemskab af sikkerhedsgrupper i Microsoft 365. 

>[!Note]
>[Få mere at vide om, hvordan du vedligeholder Microsoft 365 gruppemedlemskab](../admin/create-groups/add-or-remove-members-from-groups.md) med Microsoft 365 Administration. Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph
Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Tilføj eller fjern brugerkonti som medlemmer af en gruppe

**Hvis du vil tilføje en brugerkonto ved hjælp af dens UPN**, skal du udfylde brugerkontoen UPN (User Principal Name) (f.eks. belindan@contoso.com) og det viste navn for sikkerhedsgruppen, fjerne tegnene "<" og ">" og køre disse kommandoer i PowerShell-vinduet eller IE (Integrated Script Environment i PowerShell).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil tilføje en brugerkonto ved hjælp af dens viste navn**, skal du udfylde det viste navn for brugerkontoen (f.eks. Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil fjerne en brugerkonto med dens UPN**, skal du udfylde brugerkontoens UPN (f.eks. belindan@contoso.com) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil fjerne en brugerkonto ved hjælp af dens viste navn**, skal du udfylde det viste navn for brugerkontoen (f.eks. Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Tilføj eller fjern grupper som medlemmer af en gruppe

Sikkerhedsgrupper kan indeholde andre grupper som medlemmer. Microsoft 365 grupper kan dog ikke. Dette afsnit indeholder PowerShell-kommandoer til kun at tilføje eller fjerne grupper for en sikkerhedsgruppe.

**Hvis du vil tilføje en gruppe efter dens viste navn**, skal du udfylde det viste navn på den gruppe, du vil tilføje, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell-ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil fjerne en gruppe efter dens viste navn**, skal du udfylde det viste navn på den gruppe, du vil fjerne, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell-ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Tilføj eller fjern brugerkonti som medlemmer af en gruppe

**Hvis du vil tilføje en brugerkonto ved hjælp af dens UPN**, skal du udfylde brugerkontoen UPN (User Principal Name) (f.eks. belindan@contoso.com) og gruppens viste navn, fjerne tegnene "<" og ">" og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil tilføje en brugerkonto ved hjælp af dens viste navn**, skal du udfylde det viste navn for brugerkontoen (f.eks. Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil fjerne en brugerkonto med dens UPN**, skal du udfylde brugerkontoens UPN (f.eks. belindan@contoso.com) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis du vil fjerne en brugerkonto ved hjælp af dens viste navn**, skal du udfylde det viste navn for brugerkontoen (f.eks. Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Tilføj eller fjern grupper som medlemmer af en gruppe

Sikkerhedsgrupper kan indeholde andre grupper som medlemmer. Microsoft 365 grupper kan dog ikke. Dette afsnit indeholder PowerShell-kommandoer til kun at tilføje eller fjerne grupper for en sikkerhedsgruppe.

**Hvis du vil tilføje en gruppe efter dens viste navn**, skal du udfylde det viste navn på den gruppe, du vil tilføje, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell-ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Hvis du vil fjerne en gruppe efter dens viste navn**, skal du udfylde det viste navn på den gruppe, du vil fjerne, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell-ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)