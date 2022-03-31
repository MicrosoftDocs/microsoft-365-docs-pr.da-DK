---
title: Bevar medlemskab af sikkerhedsgruppen med PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Få mere at vide om, hvordan du bruger PowerShell til at bevare medlemskab Microsoft 365 grupper.
ms.openlocfilehash: 3637fb7d2e68091c43e624e9b6780d032c1930bc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601612"
---
# <a name="maintain-security-group-membership-with-powershell"></a>Bevar medlemskab af sikkerhedsgruppen med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 som et alternativ til Microsoft 365 Administration til at bevare sikkerhedsgruppemedlemskab Microsoft 365. 

>[!Note]
>[Lær, hvordan du Microsoft 365 gruppemedlemskab](../admin/create-groups/add-or-remove-members-from-groups.md) med Microsoft 365 Administration. Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul
Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Tilføje eller fjerne brugerkonti som medlemmer af en gruppe

Hvis du vil tilføje en brugerkonto ved hjælp af dens **UPN**, skal du udfylde brugerkontoens brugerens hovednavn (UPN) (f.eks.: belindan@contoso.com) og sikkerhedsgruppens viste navn, fjerne "<" og ">"-tegnene og køre disse kommandoer i PowerShell-vinduet eller det integrerede scriptmiljø (PowerShell Integrated Script Environment – ISE).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis** du vil tilføje en brugerkonto ud fra dens viste navn, skal du udfylde det viste navn for brugerkontoen (f.eks.: Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Hvis du vil fjerne en brugerkonto med brugerens **UPN**, skal du udfylde brugerkontoen UPN (f.eks.: belindan@contoso.com) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis** du vil fjerne en brugerkonto ved det viste navn, skal du udfylde det viste navn for brugerkontoen (f.eks.: Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Tilføje eller fjerne grupper som medlemmer af en gruppe

Sikkerhedsgrupper kan indeholde andre grupper som medlemmer. Microsoft 365 grupper kan dog ikke. Dette afsnit indeholder kun PowerShell-kommandoer til at tilføje eller fjerne grupper for en sikkerhedsgruppe.

Hvis **du** vil tilføje en gruppe ud fra dens viste navn, skal du udfylde det viste navn på den gruppe, du vil tilføje, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Hvis **du** vil fjerne en gruppe ud fra dens viste navn, skal du udfylde det viste navn på den gruppe, du vil fjerne, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Tilføje eller fjerne brugerkonti som medlemmer af en gruppe

Hvis du vil tilføje en brugerkonto ved hjælp af brugerens **UPN**, skal du udfylde brugerkontoens hovednavn (UPN) (eksempel: belindan@contoso.com) og gruppens viste navn, fjerne tegnene "<" og ">" og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis** du vil tilføje en brugerkonto ud fra dens viste navn, skal du udfylde det viste navn for brugerkontoen (f.eks.: Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

Hvis du vil fjerne en brugerkonto med brugerens **UPN**, skal du udfylde brugerkontoen UPN (f.eks.: belindan@contoso.com) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Hvis** du vil fjerne en brugerkonto ved det viste navn, skal du udfylde det viste navn for brugerkontoen (f.eks.: Belinda Newman) og gruppens viste navn og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Tilføje eller fjerne grupper som medlemmer af en gruppe

Sikkerhedsgrupper kan indeholde andre grupper som medlemmer. Microsoft 365 grupper kan dog ikke. Dette afsnit indeholder kun PowerShell-kommandoer til at tilføje eller fjerne grupper for en sikkerhedsgruppe.

Hvis **du** vil tilføje en gruppe ud fra dens viste navn, skal du udfylde det viste navn på den gruppe, du vil tilføje, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

Hvis **du** vil fjerne en gruppe ud fra dens viste navn, skal du udfylde det viste navn på den gruppe, du vil fjerne, og det viste navn på den gruppe, der skal indeholde medlemsgruppen, og køre disse kommandoer i PowerShell-vinduet eller PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)