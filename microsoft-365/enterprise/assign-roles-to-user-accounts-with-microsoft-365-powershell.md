---
title: Tildel roller til Microsoft 365 brugerkonti med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: I denne artikel kan du få mere at vide om, hvor hurtigt og nemt du kan bruge PowerShell til Microsoft 365 til at tildele administratorroller til brugerkonti.
ms.openlocfilehash: 8ac98920dd3d2d0487905b001434d73274463f9a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097442"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Tildel administratorroller til Microsoft 365 brugerkonti med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan nemt tildele roller til brugerkonti ved hjælp af PowerShell til Microsoft 365.

>[!Note]
>Få mere at vide om, hvordan [du tildeler administratorroller](../admin/add-users/assign-admin-roles.md) til brugerkonti med Microsoft 365 Administration.
>
>Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først skal du bruge en **Azure AD DC-administrator**-, **cloudprogramadministrator**- eller **global administratorkonto** til at [oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Du kan få mere at vide under [Om administratorroller](/microsoft-365/admin/add-users/about-admin-roles?).

Derefter skal du identificere logonnavnet på den brugerkonto, du vil føje til en rolle (f.eks. fredsm\@ contoso.com). Dette kaldes også brugerens hovednavn (UPN).

Derefter skal du bestemme navnet på rollen. Se [indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Vær opmærksom på noterne i denne artikel. Nogle rollenavne er forskellige for Azure Active Directory (Azure AD) PowerShell. Rollen *SharePoint administrator* i Microsoft 365 Administration er f.eks. *SharePoint-tjenesteadministrator* i Azure AD PowerShell.
>

Udfyld derefter logon- og rollenavnene, og kør følgende kommandoer:
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Her er et eksempel på et fuldført kommandosæt, der tildeler rollen SharePoint-tjenesteadministrator til *belindan\@ contoso.com-kontoen*:
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Hvis du vil have vist en liste over brugernavne for en bestemt administratorrolle, skal du bruge disse kommandoer.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Brug først en global administratorkonto til at [oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>For en enkelt rolleændring

De mest almindelige måder at angive brugerkontoen på er ved hjælp af det viste navn eller dets mailnavn, som også kaldes dets logonnavn eller brugerens hovednavn (UPN).

#### <a name="display-names-of-user-accounts"></a>Viste navne på brugerkonti

Hvis du er vant til at arbejde med de viste navne på brugerkonti, skal du bestemme følgende oplysninger:
  
- Den brugerkonto, du vil konfigurere
    
    Hvis du vil angive brugerkontoen, skal du bestemme dens viste navn. Hvis du vil hente en komplet liste over konti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Denne kommando viser det viste navn på dine brugerkonti sorteret efter Vist navn, ét skærmbillede ad gangen. Du kan filtrere listen til et mindre sæt ved hjælp af Where-cmdlet'en. Se følgende eksempel.

   >[!Note]
   >PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Denne kommando viser kun de brugerkonti, hvor Vist navn starter med "John".
    
- Den rolle, du vil tildele
    
    Hvis du vil have vist en liste over tilgængelige administratorroller, som du kan tildele til brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Når du har fastlagt det viste navn på kontoen og navnet på rollen, skal du bruge disse kommandoer til at tildele rollen til kontoen:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Indsæt kommandoerne i Notesblok. For variablerne *$dispName* og *$roleName* skal du erstatte beskrivelsesteksten med deres værdier. Fjern tegnene, \< and > men behold anførselstegnene. Indsæt de ændrede linjer i Microsoft Azure Active Directory-modulet, så Windows PowerShell vindue kan køre dem. Du kan også bruge Windows PowerShell ISE (Integrated Script Environment).
  
Her er et eksempel på et fuldført kommandosæt:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Logonnavne på brugerkonti

Hvis du er vant til at arbejde med logonnavne eller UPN'er for brugerkonti, skal du bestemme følgende oplysninger:
  
- Brugerkontoens UPN
    
    Hvis du ikke kender UPN'et, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Denne kommando viser UPN'et for dine brugerkonti sorteret efter UPN, ét skærmbillede ad gangen. Du kan bruge Where-cmdlet'en til at filtrere listen. Her er et eksempel:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Denne kommando viser kun de brugerkonti, hvor Vist navn starter med "John".
    
- Den rolle, du vil tildele
    
    Hvis du vil have vist en liste over tilgængelige roller, som du kan tildele til brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Når du har UPN'et for kontoen og navnet på rollen, kan du bruge disse kommandoer til at tildele rollen til kontoen:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Kopiér kommandoerne, og indsæt dem i Notesblok. For variablerne **$upnName** og **$roleName** . Erstat beskrivelsesteksten med deres værdier. Fjern tegnene, \< and > men behold anførselstegnene. Indsæt de ændrede linjer i Microsoft Azure Active Directory Modul, så Windows PowerShell vindue kan køre dem. Du kan også bruge Windows PowerShell ISE.
  
Her er et eksempel på et fuldført kommandosæt:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Flere rolleændringer

I forbindelse med flere rolleændringer skal du bestemme følgende oplysninger:
  
- Hvilke brugerkonti du vil konfigurere. Du kan bruge metoderne i forrige afsnit til at indsamle sættet af viste navne eller UPN'er.
    
- Hvilke roller du vil tildele til hver brugerkonto. Hvis du vil have vist en liste over tilgængelige roller, som du kan tildele til brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Opret derefter en tekstfil med kommaseparerede værdier (CSV), der har felterne vist navn eller UPN og rollenavn. Det kan du nemt gøre i Microsoft Excel.

Her er et eksempel på viste navne:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Derefter skal du udfylde placeringen af CSV-filen og køre de resulterende kommandoer ved PowerShell-kommandoprompten.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Her er et eksempel på UPN'er:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

Derefter skal du udfylde placeringen af CSV-filen og køre de resulterende kommandoer ved PowerShell-kommandoprompten.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Se også

- [Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
