---
title: Få vist oplysninger om Microsoft 365-kontolicens og -tjeneste med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Beskriver, hvordan du bruger PowerShell til at bestemme de Microsoft 365 tjenester, der er tildelt til brugere.
ms.openlocfilehash: 01f8865faeb187bef23c5757a0373fbc8be2d139
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095570"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>Få vist oplysninger om Microsoft 365-kontolicens og -tjeneste med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

I Microsoft 365 giver licenser fra licensplaner (også kaldet SKU'er eller Microsoft 365 planer) brugerne adgang til de Microsoft 365 tjenester, der er defineret for disse planer. En bruger har dog muligvis ikke adgang til alle de tjenester, der er tilgængelige i en licens, der i øjeblikket er tildelt dem. Du kan bruge PowerShell til Microsoft 365 til at få vist status for tjenester på brugerkonti.

Du kan få flere oplysninger om licensplaner, licenser og tjenester under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Hvis du vil læse brugeregenskaber, herunder licensoplysninger, skal du have tilladelsesomfanget User.Read.All eller en af de andre tilladelser, der er angivet på [siden "Hent en bruger" Graph API-referenceside](/graph/api/user-get).

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Derefter skal du angive licensplanerne for din lejer med denne kommando.

```powershell
Get-MgSubscribedSku
```

Brug disse kommandoer til at få vist en liste over de tjenester, der er tilgængelige i hver licensplan.

```powershell

$allSKUs = Get-MgSubscribedSku -Property SkuPartNumber, ServicePlans 
$allSKUs | ForEach-Object {
    Write-Host "Service Plan:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

Brug disse kommandoer til at få vist en liste over de licenser, der er tildelt en brugerkonto.

```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

Eksempel:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

### <a name="to-view-services-for-a-user-account"></a>Sådan får du vist tjenester for en brugerkonto

Hvis du vil have vist alle de Microsoft 365 tjenester, som en bruger har adgang til, skal du bruge følgende syntaks:
  
```powershell
(Get-MgUserLicenseDetail -UserId <user account UPN> -Property ServicePlans)[<LicenseIndexNumber>].ServicePlans
```

I dette eksempel vises de tjenester, som brugeren BelindaN@litwareinc.com har adgang til. Dette viser de tjenester, der er knyttet til alle licenser, der er tildelt til hendes konto.
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans).ServicePlans
```

I dette eksempel vises de tjenester, som brugeren BelindaN@litwareinc.com har adgang til fra den første licens, der er tildelt kontoen (indeksnummeret er 0).
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans)[0].ServicePlans
```

Hvis du vil have vist alle tjenester for en bruger, der har fået tildelt *flere licenser*, skal du bruge følgende syntaks:

```powershell
$userUPN="<user account UPN>"
$allLicenses = Get-MgUserLicenseDetail -UserId $userUPN -Property SkuPartNumber, ServicePlans
$allLicenses | ForEach-Object {
    Write-Host "License:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Derefter skal du angive licensplanerne for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Brug disse kommandoer til at få vist en liste over de tjenester, der er tilgængelige i hver licensplan.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Brug disse kommandoer til at få vist en liste over de licenser, der er tildelt en brugerkonto.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kør derefter denne kommando for at få vist de licensplaner, der er tilgængelige i din organisation. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Kør derefter denne kommando for at få vist de tjenester, der er tilgængelige i hver licensplan, og den rækkefølge, de er angivet i (indeksnummeret).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Brug denne kommando til at angive de licenser, der er tildelt en bruger, og den rækkefølge, som brugeren er angivet i (indeksnummeret).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>Sådan får du vist tjenester for en brugerkonto

Hvis du vil have vist alle de Microsoft 365 tjenester, som en bruger har adgang til, skal du bruge følgende syntaks:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

I dette eksempel vises de tjenester, som brugeren BelindaN@litwareinc.com har adgang til. Dette viser de tjenester, der er knyttet til alle licenser, der er tildelt til hendes konto.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

I dette eksempel vises de tjenester, som brugeren BelindaN@litwareinc.com har adgang til fra den første licens, der er tildelt kontoen (indeksnummeret er 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Hvis du vil have vist alle tjenester for en bruger, der har fået tildelt *flere licenser*, skal du bruge følgende syntaks:

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
