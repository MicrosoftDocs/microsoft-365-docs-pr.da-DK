---
title: Tildel roller Microsoft 365 brugerkonti med PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: I denne artikel får du at vide, hvor hurtigt og nemt du kan bruge PowerShell Microsoft 365 at tildele administratorroller til brugerkonti.
ms.openlocfilehash: 0b0fc0a5da1a6b84d4f13f95ace4846e367ae111
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594212"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>Tildel administratorroller Microsoft 365 brugerkonti med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan nemt tildele roller til brugerkonti ved hjælp af PowerShell til Microsoft 365.

>[!Note]
>Lær, hvordan [du tildeler administratorroller](../admin/add-users/assign-admin-roles.md) til brugerkonti med Microsoft 365 Administration.
>
>Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Du skal først bruge **en Azure AD DC-administrator**, **en Cloud Application-administrator** eller **en global administratorkonto** til at [oprette forbindelse til Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Du kan få mere at vide [under Om administratorroller](/microsoft-365/admin/add-users/about-admin-roles?).

Identificer derefter logonnavnet på den brugerkonto, du vil føje til en rolle (f.eks.: fredsm\@ contoso.com). Dette kaldes også brugerens hovednavn (UPN).

Dernæst skal du bestemme navnet på rollen. Se [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

>[!Note]
>Vær opmærksom på noterne i denne artikel. Nogle rollenavne er forskellige for Azure Active Directory (Azure AD) PowerShell. Eksempelvis er den *SharePoint administratorrolle* i Microsoft 365 Administration *SharePoint tjenesteadministrator* i Azure AD PowerShell.
>

Udfyld derefter logon- og rollenavnene, og kør disse kommandoer:
  
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

Her er et eksempel på et fuldført kommandosæt, der tildeler SharePoint-tjenesteadministratorrollen *til belindan\@ contoso.com kontoen*:
  
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

Hvis du vil have vist listen over brugernavne for en bestemt administratorrolle, skal du bruge disse kommandoer.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Du skal først bruge en global administratorkonto til [at oprette forbindelse til Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>For en enkelt rolleændring

De mest almindelige måder at angive brugerkontoen på er ved at bruge det viste navn eller mailadressen, som også kaldes logonnavnet eller brugerens hovednavn (UPN).

#### <a name="display-names-of-user-accounts"></a>Visningsnavne for brugerkonti

Hvis du er vant til at arbejde med de viste navne på brugerkonti, skal du bestemme følgende oplysninger:
  
- Den brugerkonto, du vil konfigurere
    
    Hvis du vil angive brugerkontoen, skal du bestemme det viste navn. Brug denne kommando for at få en komplet liste over konti:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Denne kommando viser det viste navn for dine brugerkonti, sorteret efter vist navn, ét skærmbillede ad gangen. Du kan filtrere listen til et mindre sæt ved hjælp af **cmdlet'en Where** . Se følgende eksempel.

   >[!Note]
   >PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Denne kommando viser kun de brugerkonti, som Det viste navn starter med "John".
    
- Den rolle, du vil tildele
    
    For at få vist listen over tilgængelige administratorroller, som du kan tildele brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Når du har bestemmet det viste navn for kontoen og navnet på rollen, kan du bruge disse kommandoer til at tildele rollen til kontoen:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Indsæt kommandoerne i Notesblok. Ud for *$dispName* og *$roleName* variabler skal du erstatte beskrivelsesteksten med deres værdier. Fjern tegnene \< and > , men behold anførselstegnene. Indsæt de ændrede linjer i Microsoft Azure Active Directory Module for Windows PowerShell for at køre dem. Alternativt kan du bruge det Windows PowerShell scriptmiljø (ISE).
  
Her er et eksempel på et fuldført kommandosæt:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Logonnavne på brugerkonti

Hvis du er vant til at arbejde med logonnavnene eller UPN'er for brugerkonti, skal du bestemme følgende oplysninger:
  
- Brugerkontoens UPN
    
    Hvis du ikke kender UPN'et, kan du bruge denne kommando:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Denne kommando viser UPN'et for dine brugerkonti, sorteret efter UPN, ét skærmbillede ad gangen. Du kan bruge **Cmdlet'en Where** til at filtrere listen. Her er et eksempel:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Denne kommando viser kun de brugerkonti, som Det viste navn starter med "John".
    
- Den rolle, du vil tildele
    
    For at få vist listen over tilgængelige roller, som du kan tildele brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Når du har fået UPN for kontoen og navnet på rollen, kan du bruge disse kommandoer til at tildele rollen til kontoen:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Kopiér kommandoerne, og indsæt dem i Notesblok. For **$upnName** og **$roleName** variabler. Erstat beskrivelsesteksten med deres værdier. Fjern tegnene \< and > , men behold anførselstegnene. Indsæt de ændrede linjer i Microsoft Azure Active Directory Module for Windows PowerShell for at køre dem. Alternativt kan du bruge den Windows PowerShell ISE.
  
Her er et eksempel på et fuldført kommandosæt:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Flere rolleændringer

Ved ændringer af flere roller skal du fastlægge følgende oplysninger:
  
- Hvilke brugerkonti du vil konfigurere. Du kan bruge metoderne i det forrige afsnit til at samle sættet af viste navne eller UPN'er.
    
- Hvilke roller du vil tildele hver brugerkonto. For at få vist listen over tilgængelige roller, som du kan tildele brugerkonti, skal du bruge denne kommando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Dernæst skal du oprette en kommasepareret tekstfil (CSV), der har det viste navn eller UPN og felterne rollenavn. Du kan nemt gøre dette i Microsoft Excel.

Her er et eksempel på viste navne:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

Dernæst skal du udfylde CSV-filens placering og køre de resulterende kommandoer ved PowerShell-kommandoprompten.
  
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

Dernæst skal du udfylde CSV-filens placering og køre de resulterende kommandoer ved PowerShell-kommandoprompten.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Se også

- [Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
