---
title: Deaktiver adgang til Microsoft 365-tjenester med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel kan du få mere at vide om, hvordan du bruger PowerShell til at deaktivere Microsoft 365-tjenester for brugerne.
ms.openlocfilehash: bce02c40bf6ca99d74b8747fb0c5eb5c0b485888
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594228"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Deaktiver adgang til Microsoft 365-tjenester med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Når en Microsoft 365-konto er tildelt en licens fra en licensplan, gøres Microsoft 365 tjenester tilgængelige for brugeren fra den pågældende licens. Du kan dog styre de Microsoft 365, som brugeren kan få adgang til. Selvom licensen tillader adgang til SharePoint Online-tjenesten, kan du f.eks. deaktivere adgangen til den. Du kan bruge PowerShell til at deaktivere adgang til et hvilket som helst antal tjenester for en bestemt licensplan for:

- En individuel konto.
- En gruppe af konti.
- Alle konti i organisationen.

>[!Note]
>Der er Microsoft 365 tjenesteafhængigheder, der kan forhindre dig i at deaktivere en bestemt tjeneste, når andre tjenester er afhængige af den.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Brug derefter denne kommando til at få vist dine tilgængelige licensplaner, også kaldet AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Få mere at vide under [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
Hvis du vil se resultaterne af før og efter procedurerne i dette emne, skal du [se Få vist oplysninger om kontolicens og tjeneste med PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
Der findes et PowerShell-script, der automatiserer de procedurer, der er beskrevet i dette emne. Med scriptet kan du få vist og deaktivere tjenester i din Microsoft 365, herunder Sway. Få mere at vide under [Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Deaktivere bestemte Microsoft 365 for bestemte brugere for en bestemt licensplan
  
Hvis du vil deaktivere et bestemt sæt Microsoft 365 for brugere i en bestemt licensplan, skal du udføre følgende trin:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Trin 1: Identificer de uønskede tjenester i licensplanen ved hjælp af følgende syntaks:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

I følgende eksempel **oprettes der et LicenseOptions-objekt**, der deaktiverer Office og SharePoint Online-tjenester i den licensplan `litwareinc:ENTERPRISEPACK` , der hedder (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Trin 2: Brug **objektet LicenseOptions** fra trin 1 på en eller flere brugere.
    
Hvis du vil oprette en ny konto, hvor tjenesterne er deaktiveret, skal du bruge følgende syntaks:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

I følgende eksempel oprettes der en ny konto for Allie Bellew, som tildeler licensen og deaktiverer de tjenester, der er beskrevet i trin 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Du kan finde flere oplysninger om oprettelse af brugerkonti i PowerShell Microsoft 365 i [Opret brugerkonti med PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
Hvis du vil deaktivere tjenesterne for en eksisterende licenseret bruger, skal du bruge følgende syntaks:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

I dette eksempel deaktiveres tjenesterne for brugeren BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

For at deaktivere de tjenester, der er beskrevet i trin 1 for alle eksisterende licenserede brugere, skal du angive navnet på din Microsoft 365-plan fra visningen af **Cmdlet'en Get-MsolAccountSku** (f.eks **litwareinc:ENTERPRISEPACK**) og derefter køre følgende kommandoer:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Hvis du bruger **cmdlet'en Get-MsolUser** uden at bruge parameteren _Alle_ , er det kun de første 500 brugerkonti, der returneres.

Hvis du vil deaktivere tjenesterne for en gruppe af eksisterende brugere, skal du bruge en af følgende metoder til at identificere brugerne:
    
**Metode 1. Filtrere kontiene baseret på en eksisterende kontoattribut** 

For at gøre dette skal du bruge følgende syntaks:
    
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
    
1. Opret en tekstfil, der indeholder én konto på hver linje således:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   I dette eksempel er tekstfilen C:\\Mine dokumenterAccounts.txt\\ .
    
2. Kør følgende kommando:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

Hvis du vil deaktivere adgang til tjenester for flere licensplaner, skal du gentage ovenstående instruktioner for hver licensplan og sikre, at:

- Brugerkontiene er blevet tildelt licensplanen.
- De tjenester, der skal deaktiveres, er tilgængelige i licensplanen.

Hvis du Microsoft 365 tjenester for brugere, mens du tildeler dem en licensplan, skal du se Deaktivere adgang til tjenester[, mens du tildeler brugerlicenser](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>Tildele alle tjenester i en licensplan til en brugerkonto

For brugerkonti, der har deaktiveret tjenester, kan du aktivere alle tjenester for en bestemt licensplan med disse kommandoer:

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
