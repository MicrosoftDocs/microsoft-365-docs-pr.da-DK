---
title: Brug PowerShell-cmdlet'erne til central installation til at administrere tilføjelsesprogrammer
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
description: Brug PowerShell-cmdlet'erne til central installation for at hjælpe dig med at udrulle og administrere Office tilføjelsesprogrammer til din Microsoft 365 organisation.
ms.openlocfilehash: 9f9a3e36c6e1c76d99d8abb7dc47f97a04541322
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824734"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Brug PowerShell-cmdlet'erne til central installation til at administrere tilføjelsesprogrammer

Som Microsoft 365 global administrator kan du udrulle Office tilføjelsesprogrammer til brugere via funktionen Central installation (se [Udrul Office tilføjelsesprogrammer i Administration](../admin/manage/manage-deployment-of-add-ins.md). Ud over at udrulle Office tilføjelsesprogrammer via Microsoft 365 Administration kan du også bruge Microsoft PowerShell. Installér [O365 Centraliseret Add-In udrulningsmodul til Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).

Når du har downloadet modulet, skal du åbne et almindeligt Windows PowerShell vindue og køre følgende cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```

## <a name="connect-using-your-admin-credentials"></a>Forbind ved hjælp af dine administratorlegitimationsoplysninger

Før du kan bruge cmdlet'erne til central installation, skal du logge på.

1. Start PowerShell.

2. Forbind til PowerShell ved hjælp af dine legitimationsoplysninger som virksomhedsadministrator. Kør følgende cmdlet.

  ```powershell
  Connect-OrganizationAddInService
  ```

3. Angiv dine **legitimationsoplysninger** til Microsoft 365 **Brugeradministrator** eller **Global administrator** på siden Angiv legitimationsoplysninger. Du kan også angive dine legitimationsoplysninger direkte i cmdlet'en.

    Kør følgende cmdlet, der angiver dine legitimationsoplysninger som virksomhedsadministrator som et PSCredential-objekt.

  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Du kan få flere oplysninger om brug af PowerShell under [Forbind til at Microsoft 365 med PowerShell](./connect-to-microsoft-365-powershell.md).

## <a name="upload-an-add-in-manifest"></a>Upload et tilføjelsesprogrammanifest

Kør **cmdlet'en Ny-organisationTilføj** for at uploade et tilføjelsesprogrammanifest fra en sti, som enten kan være en filplacering eller EN URL-adresse. I følgende eksempel vises en filplacering for værdien af  _ManifestPath-parameteren_ .

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Du kan også køre **cmdlet'en Ny-OrganisationTilføj** for at uploade et tilføjelsesprogram og tildele det til brugere eller grupper direkte ved hjælp af parameteren  _Medlemmer_ , som vist i følgende eksempel. Adskil medlemmernes mailadresser med et komma.

```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Upload et tilføjelsesprogram fra Office Store

Kør **Cmdlet'en New-OrganizationAddIn** for at uploade et manifest fra Office Store.

I følgende eksempel angiver **cmdlet'en New-OrganizationAddIn** AssetId for et tilføjelsesprogram for en USA placering og indholdsmarked.

```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Hvis du vil bestemme værdien for parameteren _AssetId_, kan du kopiere den fra URL-adressen på den Office Store webside for tilføjelsesprogrammet. AssetIds starter altid med "WA" efterfulgt af et tal. I det forrige eksempel er kilden til værdien AssetId for WA104099688 f.eks. den Office Store URL-adresse på websiden for tilføjelsesprogrammet: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).

Værdierne for parameteren Locale og parameteren _ContentMarket_ er _identiske_ og angiver det land/område, du forsøger at installere tilføjelsesprogrammet fra. Formatet er en-US, fr-FR. og så videre.

> [!NOTE]
> Tilføjelsesprogrammer, der uploades fra Office Store, opdateres automatisk inden for nogle få dage, efter at den seneste opdatering er tilgængelig på Office Store.

## <a name="get-details-of-an-add-in"></a>Få oplysninger om et tilføjelsesprogram

Kør **Cmdlet'en Get-OrganizationAddIn** som vist nedenfor for at få oplysninger om alle tilføjelsesprogrammer, der er uploadet til lejeren, herunder produkt-id'et for et tilføjelsesprogram.

```powershell
Get-OrganizationAddIn
```

Kør **Cmdlet'en Get-OrganizationAddIn** med en værdi for parameteren  _ProductId_ for at angive, hvilket tilføjelsesprogram du vil hente oplysninger om.

```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Hvis du vil have detaljerede oplysninger om alle tilføjelsesprogrammer plus de tildelte brugere og grupper, skal du sende outputtet fra **Get-OrganizationAddIn-cmdlet'en** til cmdlet'en Format-List, som vist i følgende eksempel.

```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Slå et tilføjelsesprogram til eller fra

Hvis du vil slå et tilføjelsesprogram fra, så brugere og grupper, der er tildelt det, ikke længere har adgang, skal du køre **Set-OrganizationAddIn-cmdlet'en** med parameteren  _ProductId_ og parameteren  _Enabled_ indstillet til  `$false`, som vist i følgende eksempel.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Hvis du vil slå et tilføjelsesprogram til igen, skal du køre den samme cmdlet, hvor parameteren  _Enabled_ er angivet til  `$true`.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Tilføje eller fjerne brugere fra et tilføjelsesprogram

Hvis du vil føje brugere og grupper til et bestemt tilføjelsesprogram, skal du køre cmdlet'en **Set-OrganizationAddInAssignments** med parametrene  _ProductId_,  _Add_ og  _Members_ . Adskil medlemmernes mailadresser med et komma.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Hvis du vil fjerne brugere og grupper, skal du køre den samme cmdlet ved hjælp af parameteren  _Remove_ .

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Hvis du vil tildele et tilføjelsesprogram til alle brugere i lejeren, skal du køre den samme cmdlet ved hjælp af parameteren  _AssignToEveryone_ , hvor værdien er angivet til  `$true`.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Hvis du ikke vil tildele et tilføjelsesprogram til alle og vende tilbage til de tidligere tildelte brugere og grupper, kan du køre den samme cmdlet og slå parameteren  _AssignToEveryone_ fra ved at angive dens værdi til  `$false`.

```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Opdater et tilføjelsesprogram

Hvis du vil opdatere et tilføjelsesprogram fra et manifest, skal du køre **Set-OrganizationAddIn-cmdlet'en** med parametrene  _ProductId_,  _ManifestPath_ og  _Locale_ som vist i følgende eksempel.

```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Tilføjelsesprogrammer, der uploades fra Office Store, opdateres automatisk inden for nogle få dage, efter at den seneste opdatering er tilgængelig på Office Store.

## <a name="delete-an-add-in"></a>Slet et tilføjelsesprogram

Hvis du vil slette et tilføjelsesprogram, skal du køre **cmdlet'en Remove-OrganizationAddIn** med parameteren  _ProductId_ som vist i følgende eksempel.

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

To customize an add-in, run the **Set -OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

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
| \<IconURL>   </br>| The URL of the image used as the add-in's icon (in admin center). |
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
          <bt:Image id="img16icon" DefaultValue="https://site.com/img.jpg"
    </bt:Images>
</Resources>
```
In this case, the element id for the image is "img16icon" and the value associated with it is "http:<i></i>//site.<i></i>com/img.jpg."

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{"ElementID" = "New Value"; "NextElementID" = "Next New Value"}
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

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remove an add-in from cache:

1. Navigate to the "Users" folder in C:\
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Få detaljeret hjælp til hver cmdlet

Du kan se detaljeret hjælp til hver cmdlet ved hjælp af cmdlet'en Get-help. Følgende cmdlet indeholder f.eks. detaljerede oplysninger om Remove-OrganizationAddIn-cmdlet'en.

```powershell
Get-help Remove-OrganizationAddIn -Full
```
