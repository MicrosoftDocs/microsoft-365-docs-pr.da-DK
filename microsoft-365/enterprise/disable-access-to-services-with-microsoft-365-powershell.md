---
title: Deaktiver adgang til Microsoft 365-tjenester med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: I denne artikel kan du få mere at vide om, hvordan du bruger PowerShell til at deaktivere adgang til Microsoft 365-tjenester for brugere.
ms.openlocfilehash: 0acd174fce25e0332aa8f927595657e4d0a464b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097706"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Deaktiver adgang til Microsoft 365-tjenester med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Når en Microsoft 365 konto tildeles en licens fra en licensplan, gøres Microsoft 365 tjenester tilgængelige for brugeren fra den pågældende licens. Du kan dog styre de Microsoft 365 tjenester, som brugeren har adgang til. Selvom licensen f.eks. giver adgang til SharePoint Online-tjenesten, kan du deaktivere adgang til den. Du kan bruge PowerShell til at deaktivere adgang til et vilkårligt antal tjenester for en bestemt licensplan for:

- En individuel konto.
- En gruppe konti.
- Alle konti i din organisation.

>[!Note]
>Der er Microsoft 365 tjenesteafhængigheder, der kan forhindre dig i at deaktivere en angivet tjeneste, når andre tjenester er afhængige af den.
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Tildeling og fjernelse af licenser for en bruger kræver User.ReadWrite.All-tilladelsesomfanget eller en af de andre tilladelser, der er angivet på [siden "Tildel licens" Graph API-referenceside](/graph/api/user-assignlicense).

Der kræves tilladelsesomfanget Organization.Read.All for at læse de licenser, der er tilgængelige i lejeren.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

Brug derefter denne kommando til at få vist dine tilgængelige licensplaner, også kaldet SkuPartNumber:

```powershell
Get-MgSubscribedSku | Select SkuId, SkuPartNumber, ServicePlans | Sort SkuPartNumber
```

Du kan få flere oplysninger under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

Hvis du vil se før og efter resultaterne af procedurerne i dette emne, skal du se [Få vist oplysninger om kontolicens og tjeneste med PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).

### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Deaktiver specifikke Microsoft 365-tjenester for bestemte brugere for en bestemt licensplan
  
Hvis du vil deaktivere et bestemt sæt Microsoft 365 tjenester for brugere for en bestemt licensplan, skal du udføre følgende trin:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Trin 1: Identificer de uønskede tjenester i licensplanen ved hjælp af følgende syntaks:

Angiv først de licensplaner, der er tilgængelige i din lejer, ved hjælp af følgende kommando.

```powershell
Get-MgSubscribedSku | Select SkuPartNumber

SkuPartNumber
-------------
EMSPREMIUM
SPE_E5
RIGHTSMANAGEMENT_ADHOC

```

Derefter skal du bruge SkuPartNumber fra kommandoen ovenfor og angive de tjenesteplaner, der er tilgængelige for en given licensplan (Sku).

I følgende eksempel vises alle de tjenesteplaner, der er tilgængelige for **SPE_E5** (Microsoft 365 E5).

```powershell
Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5' |  select -ExpandProperty ServicePlans
```

```text
AppliesTo ProvisioningStatus ServicePlanId                        ServicePlanName
--------- ------------------ -------------                        ---------------
User      Success            b21a6b06-1988-436e-a07b-51ec6d9f52ad PROJECT_O365_P3
User      Success            64bfac92-2b17-4482-b5e5-a0304429de3e MICROSOFTENDPOINTDLP
User      Success            199a5c09-e0ca-4e37-8f7c-b05d533e1ea2 MICROSOFTBOOKINGS
User      Success            6db1f1db-2b46-403f-be40-e39395f08dbb CUSTOMER_KEY
User      Success            4a51bca5-1eff-43f5-878c-177680f191af WHITEBOARD_PLAN3
User      Success            07699545-9485-468e-95b6-2fca3738be01 FLOW_O365_P3
User      Success            9c0dab89-a30c-4117-86e7-97bda240acd2 POWERAPPS_O365_P3
User      Success            e212cbc7-0961-4c40-9825-01117710dcb1 FORMS_PLAN_E5
User      Success            57ff2da0-773e-42df-b2af-ffb7a2317929 TEAMS1
User      Success            21b439ba-a0ca-424f-a6cc-52f954a5b111 WIN10_PRO_ENT_SUB
User      Success            eec0eb4f-6444-4f95-aba0-50c24d67f998 AAD_PREMIUM_P2
User      Success            c1ec4a95-1f05-45b3-a911-aa3fa01094f5 INTUNE_A
User      Success            7547a3fe-08ee-4ccb-b430-5077c5041653 YAMMER_ENTERPRISE
User      Success            a23b959c-7ce8-4e57-9140-b90eb88a9e97 SWAY
User      Success            e95bec33-7c88-4a70-8e19-b10bd9d0c014 SHAREPOINTWAC
User      Success            5dbe027f-2339-4123-9542-606e4d348a72 SHAREPOINTENTERPRISE
User      Success            b737dad2-2f6c-4c65-90e3-ca563267e8b9 PROJECTWORKMANAGEMENT
User      Success            43de0ff5-c92c-492b-9116-175376d08c38 OFFICESUBSCRIPTION
User      Success            0feaeb32-d00e-4d66-bd5a-43b5b83db82c MCOSTANDARD
User      Success            9f431833-0334-42de-a7dc-70aa40db46db LOCKBOX_ENTERPRISE
User      Success            efb87545-963c-4e0d-99df-69c6916d9eb0 EXCHANGE_S_ENTERPRISE
```

Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference). (Søg ved hjælp af ServicePlanId til at slå serviceplanens tilsvarende brugervenlige navn op).

I følgende eksempel tildeles **SPE_E5** (Microsoft 365 E5) med **tjenesterne MICROSOFTBOOKINGS** (Microsoft Bookings) og **LOCKBOX_ENTERPRISE** (Customer Lockbox) slået fra:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

Egenskaben DisabledPlans for parameteren AddLicenses i Set-MgUserLicense overskriver brugerens eksisterende Værdi for DisabledPlans. Hvis du vil bevare tilstanden for eksisterende tjenesteplaner, skal brugerens aktuelle tilstand af tjenesteplaner flettes med de nye planer, der deaktiveres.

Hvis de eksisterende DisabledPlans ikke medtages, vil det medføre, at brugerens tidligere deaktiverede plan aktiveres.

I følgende eksempel opdateres en bruger med **SPE_E5** (Microsoft 365 E5) og deaktiver Sway- og formulartjenesteplaner, mens brugerens eksisterende deaktiverede planer er i den aktuelle tilstand:
  
```powershell
## Get the services that have already been disabled for the user.
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

## Get the new service plans that are going to be disabled
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

## Merge the new plans that are to be disabled with the user's current state of disabled plans
$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)
## Update user's license
Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Brug derefter denne kommando til at få vist dine tilgængelige licensplaner, også kaldet AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Du kan få flere oplysninger under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Hvis du vil se før og efter resultaterne af procedurerne i dette emne, skal du se [Få vist oplysninger om kontolicens og tjeneste med PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Der findes et PowerShell-script, der automatiserer de procedurer, der er beskrevet i dette emne. Scriptet giver dig især mulighed for at få vist og deaktivere tjenester i din Microsoft 365 organisation, herunder Sway. Du kan få flere oplysninger under [Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Deaktiver specifikke Microsoft 365-tjenester for bestemte brugere for en bestemt licensplan
  
Hvis du vil deaktivere et bestemt sæt Microsoft 365 tjenester for brugere for en bestemt licensplan, skal du udføre følgende trin:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Trin 1: Identificer de uønskede tjenester i licensplanen ved hjælp af følgende syntaks:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

I følgende eksempel oprettes et **LicenseOptions-objekt**, der deaktiverer tjenesterne Office og SharePoint Online i licensplanen med navnet `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Trin 2: Brug objektet **LicenseOptions** fra Trin 1 på en eller flere brugere.
    
Hvis du vil oprette en ny konto, hvor tjenesterne er deaktiveret, skal du bruge følgende syntaks:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

I følgende eksempel oprettes der en ny konto for Allie Bellew, der tildeler licensen og deaktiverer de tjenester, der er beskrevet i trin 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Du kan få flere oplysninger om oprettelse af brugerkonti i PowerShell til Microsoft 365 under [Opret brugerkonti med PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
Hvis du vil deaktivere tjenesterne for en eksisterende bruger med licens, skal du bruge følgende syntaks:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

I dette eksempel deaktiveres tjenesterne for brugerens BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Hvis du vil deaktivere de tjenester, der er beskrevet i trin 1 for alle eksisterende licenserede brugere, skal du angive navnet på din Microsoft 365 plan fra visningen af Cmdlet'en **Get-MsolAccountSku** (f.eks **. litwareinc:ENTERPRISEPACK**) og derefter køre følgende kommandoer:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Hvis du bruger **Cmdlet'en Get-MsolUser** uden at bruge parameteren _All_ , returneres kun de første 500 brugerkonti.

Hvis du vil deaktivere tjenesterne for en gruppe af eksisterende brugere, skal du bruge en af følgende metoder til at identificere brugerne:
    
**Metode 1. Filtrer kontiene baseret på en eksisterende kontoattribut** 

Det gør du ved at bruge følgende syntaks:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

I følgende eksempel deaktiveres tjenesterne for brugere i salgsafdelingen i USA.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Metode 2: Brug en liste over bestemte konti** 

Det gør du ved at udføre følgende trin:
    
1. Opret en tekstfil, der indeholder én konto på hver linje som denne:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   I dette eksempel er tekstfilen C:\\Dokumenter\\Accounts.txt.
    
2. Kør følgende kommando:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Hvis du vil deaktivere adgang til tjenester for flere licensplaner, skal du gentage ovenstående instruktioner for hver licensplan og sikre, at:

- Brugerkontiene er tildelt licensplanen.
- De tjenester, der skal deaktiveres, er tilgængelige i licensplanen.

Hvis du vil deaktivere Microsoft 365 tjenester for brugere, mens du tildeler dem til en licensplan, skal du se [Deaktiver adgang til tjenester, mens du tildeler brugerlicenser](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Tildel alle tjenester i en licensplan til en brugerkonto

For brugerkonti, hvor tjenester er deaktiveret, kan du aktivere alle tjenester for en bestemt licensplan med disse kommandoer:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>Relateret emne

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
