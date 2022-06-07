---
title: Opret Microsoft 365-brugerkonti med PowerShell
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
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Sådan bruger du PowerShell til at oprette individuelle eller flere Microsoft 365-brugerkonti.
ms.openlocfilehash: 9f96c5a96e014055622deb34c37cb8523f0041f8
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930235"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>Opret Microsoft 365-brugerkonti med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge PowerShell til Microsoft 365 til effektivt at oprette brugerkonti, herunder flere konti.

Når du opretter brugerkonti i PowerShell, kræves der altid visse kontoegenskaber. Andre egenskaber er ikke påkrævet, men er vigtige. Se følgende tabel.
  
|**Egenskabsnavn**|**Kræves?**|**Beskrivelse**|
|:-----|:-----|:-----|
|**Displayname** <br/> |Ja  <br/> |Dette er det viste navn, der bruges i Microsoft 365-tjenester. For eksempel *Caleb Sills*. <br/> |
|**UserPrincipalName** <br/> |Ja  <br/> |Dette er det kontonavn, der bruges til at logge på Microsoft 365-tjenester. *CalebS\@contoso.onmicrosoft.com* f.eks.  <br/> |
|**Fornavn** <br/> |Nej  <br/> ||
|**Efternavn** <br/> |Nej  <br/> ||
|**Tildeling af licens** <br/> |Nej  <br/> |Dette er licensplanen (også kendt som [licensplanen eller SKU'en](/azure/active-directory/enterprise-users/licensing-service-plan-reference)), hvorfra der tildeles en tilgængelig licens til brugerkontoen. Licensen definerer de Microsoft 365-tjenester, der er tilgængelige for kontoen. Du behøver ikke at tildele en licens til en bruger, når du opretter kontoen, men kontoen skal have en licens for at få adgang til Microsoft 365-tjenester. Du har 30 dage til at licensere brugerkontoen, når du har oprettet den. |
|**Adgangskode** <br/> |Nej  <br/> | Hvis du ikke angiver en adgangskode, tildeles brugerkontoen en tilfældig adgangskode, og adgangskoden er synlig i resultaterne af kommandoen. Hvis du angiver en adgangskode, skal den være på 8 til 16 ASCII-teksttegn af følgende typer: små bogstaver, store bogstaver, tal og symboler.<br/> |
|**UsageLocation** <br/> |Nej  <br/> |Dette er en gyldig ISO 3166-1 alpha-2-landekode. Det kan f.eks. være *USA* for USA og *Frankrig* . Det er vigtigt at angive denne værdi, fordi nogle Microsoft 365-tjenester ikke er tilgængelige i visse lande. Du kan ikke tildele en licens til en brugerkonto, medmindre kontoen har denne værdi konfigureret. Du kan få flere oplysninger under [Om licensbegrænsninger](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |

>[!Note]
>[Få mere at vide om, hvordan du opretter brugerkonti](../admin/add-users/add-users.md) ved hjælp af Microsoft 365 Administration.
> 
> Du kan finde en liste over yderligere ressourcer under [Administrer brugere og grupper](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph-modulet

Først [skal du oprette forbindelse til din Microsoft 365-lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Når du har oprettet forbindelse, skal du bruge følgende syntaks til at oprette en individuel konto:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

I dette eksempel oprettes der en konto for den amerikanske bruger *Caleb Sills*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory-modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365-lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Opret en individuel brugerkonto

Hvis du vil oprette en individuel konto, skal du bruge følgende syntaks:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory Module til Windows PowerShell-modulet og cmdlet'er, der har *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
>

Hvis du vil have vist de tilgængelige [licensplannavne](/azure/active-directory/enterprise-users/licensing-service-plan-reference), skal du bruge denne kommando:

````powershell
Get-MsolAccountSku
````

I dette eksempel oprettes der en konto for den amerikanske bruger *Caleb Sills*, og der tildeles en licens fra `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3)-licensplanen.
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Opret flere brugerkonti

1. Opret en kommasepareret værdifil (CSV), der indeholder de påkrævede brugerkontooplysninger. Eksempel:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >Kolonnenavnene og rækkefølgen i den første række i CSV-filen er vilkårlige. Men sørg for, at rækkefølgen af dataene i resten af filen stemmer overens med rækkefølgen af kolonnenavnene. Og brug kolonnenavnene til parameterværdierne i kommandoen PowerShell til Microsoft 365.
    
2. Brug følgende syntaks:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   I dette eksempel oprettes brugerkonti ud fra filen *C:\Mine Documents\NewAccounts.csv* , og resultaterne logføres i en fil med navnet *C:\Min Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. Gennemse outputfilen for at se resultaterne. Vi angav ikke adgangskoder, så de tilfældige adgangskoder, som Microsoft 365 oprettede, er synlige i outputfilen.
    
## <a name="see-also"></a>Se også

[Administrer Microsoft 365-brugerkonti, -licenser og -grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
