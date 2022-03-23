---
title: Brug de Centraliserede udrulning af PowerShell-cmdlet'er til at administrere tilføjelsesinstallationer
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: Brug de centraliserede udrulnings-PowerShell-cmdlet'er til at hjælpe dig med at installere og administrere Office til din Microsoft 365 organisation.
ms.openlocfilehash: acdda1c30dbd0a19762040140b1bb3bf1a7715d4
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63590992"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Brug de Centraliserede udrulning af PowerShell-cmdlet'er til at administrere tilføjelsesinstallationer

Som global Microsoft 365 administrator kan du installere Office-tilføjelsesprogrammet til brugere via funktionen Centraliseret udrulning (se Installér [Office-tilføjelsesprogrammet i Administration](../admin/manage/manage-deployment-of-add-ins.md). Ud over at Office tilføjelser via Microsoft 365 Administration, kan du også bruge Microsoft PowerShell. Installér [O365 Centraliseret Add-In Udrulningsmodul til Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Når du har downloadet modulet, skal du Windows PowerShell et almindeligt vindue og køre følgende cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Forbind bruger dine administratorlegitimationsoplysninger

Før du kan bruge cmdletterne til Centraliseret udrulning, skal du logge på.
  
1. Start PowerShell.
    
2. Forbind til PowerShell ved hjælp af dine legitimationsoplysninger som firmaadministrator. Kør følgende cmdlet:
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. På siden **Angiv legitimationsoplysninger** skal du angive Microsoft 365 **brugeradministrator** eller **globale legitimationsoplysninger**. Alternativt kan du angive dine legitimationsoplysninger direkte i cmdlet'en. 
    
    Kør følgende cmdlet, der angiver dine legitimationsoplysninger for virksomheden som et PSCredential-objekt.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Du kan finde flere oplysninger om brug af PowerShell [Forbind to Microsoft 365 med PowerShell](./connect-to-microsoft-365-powershell.md). 
  
## <a name="upload-an-add-in-manifest"></a>Upload et manifest for tilføjelsesprogrammet

Kør **New-OrganizationAdd-In-cmdlet'en** for at overføre et manifest til tilføjelsesprogrammet fra en sti, som kan være enten en filplacering eller URL-adresse. I følgende eksempel vises en filplacering for værdien af  _parameteren ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Du kan også køre **New-OrganizationAdd-In-cmdlet'en** for at overføre et tilføjelsesprogrammet og tildele den til brugere eller grupper direkte ved hjælp af parameteren  _Members_ , som vist i følgende eksempel. Adskid medlemmers mailadresser med et komma. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Upload et tilføjelsesprogrammet fra Office Store

Kør **New-OrganizationAddIn-cmdlet'en** for at overføre et manifest fra Office Store.
  
I følgende eksempel angiver **New-OrganizationAddIn-cmdlet'en** AssetId'et for et tilføjelsesprogrammet på et amerikansk sted og indholdsmarked.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

For at bestemme værdien for _AssetId-parameteren_ kan du kopiere den fra URL-adressen på Office Store for tilføjelsesprogrammet. AktivId'er starter altid med "WA" efterfulgt af et tal. I det forrige eksempel er kilden til AktivId-værdien af WA104099688 den Office Store url-adresse til tilføjelsesprogrammet: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Værdierne for  _Locale-parameteren_ og  _ContentMarket-parameteren_ er identiske og angiver det land/område, du forsøger at installere tilføjelsesprogrammet fra. Formatet er da-DK, fr-FR. og så videre. 
  
> [!NOTE]
> Tilføjelser, der er overført fra Office Store, opdateres automatisk inden for et par dage efter, at den seneste opdatering er tilgængelig på Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Få oplysninger om et tilføjelsesprogrammet

Kør **Get-OrganizationAddIn-cmdlet'en** som vist nedenfor for at få oplysninger om alle tilføjelser, der er uploadet til lejeren, herunder et tilføjelsesprogrammets produkt-id.
  
```powershell
Get-OrganizationAddIn
```

Kør **Get-OrganizationAddIn-cmdlet'en** med en værdi for  _ProductId-parameteren_ for at angive, hvilket tilføjelsesprogrammet du vil hente oplysninger om. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

For at få detaljerede oplysninger om alle tilføjelses ins plus de tildelte brugere og grupper skal du pipe outputtet fra **Get-OrganizationAddIn-cmdlet'en** til Format-List-cmdlet'en, som vist i følgende eksempel.
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Aktivere eller deaktivere et tilføjelsesprogrammet

Hvis du vil deaktivere et tilføjelsesprogrammet, så brugere og grupper, der er tildelt til det, ikke længere har adgang, skal du køre **Set-OrganizationAddIn-cmdlet'en** med _parameteren ProductId_ og parameteren `$false`_Enabled_ angivet til , som vist i følgende eksempel.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Hvis du vil slå et tilføjelsesprogrammet til igen, skal du køre den samme cmdlet med  _parameteren Enabled_ angivet til  `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Tilføje eller fjerne brugere fra et tilføjelsesprogrammet

Hvis du vil føje brugere og grupper til et bestemt tilføjelsesprogrammet, skal du køre **cmdlet'en Set-OrganizationAddInAssignments** med _parametrene ProductId_, _Add og_ Members. Adskid medlemmers mailadresser med et komma. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Hvis du vil fjerne brugere og grupper, skal du køre den samme cmdlet ved hjælp af  _parameteren Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

For at tildele et tilføjelsesprogrammet til alle brugere på lejeren skal du køre den samme cmdlet ved hjælp af parameteren  _AssignToEveryone_ med den værdi, der er angivet til  `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Hvis du ikke vil tildele et tilføjelsesprogrammet til alle og vende tilbage til de tidligere tildelte brugere og grupper, kan du køre den samme cmdlet og deaktivere  _parameteren AssignToEveryone_ ved  `$false`at angive dens værdi til .
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Opdater et tilføjelsesprogrammet

Hvis du vil opdatere et tilføjelsesprogrammet fra et manifest, skal du køre **Set-OrganizationAddIn-cmdlet'en** med parametrene  _ProductId_,  _ManifestPath_ og  _Locale_ , som vist i følgende eksempel. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Tilføjelser, der er overført fra Office Store, opdateres automatisk inden for et par dage efter, at den seneste opdatering er tilgængelig på Office Store. 
  
## <a name="delete-an-add-in"></a>Slette et tilføjelsesprogrammet

Hvis du vil slette et tilføjelsesprogrammet, skal du køre cmdlet'en **Remove-OrganizationAddIn** med  _parameteren ProductId_ , som vist i følgende eksempel. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Få detaljeret hjælp til hver cmdlet

Du kan se detaljeret hjælp til hver cmdlet ved hjælp af Get-help-cmdlet'en. Følgende cmdlet indeholder f.eks. detaljerede oplysninger om Remove-OrganizationAddIn cmdlet'en.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```
