---
title: Konfigurere Microsoft 365 egenskaber for brugerkonti med PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Brug PowerShell til Microsoft 365 til at konfigurere egenskaber for individuelle eller flere brugerkonti i din Microsoft 365 lejer.
ms.openlocfilehash: 01b17837e4babc31d385be66f9387129baf87da1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590938"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Konfigurere Microsoft 365 egenskaber for brugerkonti med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">til</a> at konfigurere egenskaber for brugerkontiene for din Microsoft 365 lejer. I PowerShell kan du også gøre dette samt nogle andre ting, du ikke kan gøre i Administration.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

For at konfigurere egenskaber for brugerkonti i Azure Active Directory PowerShell til Graph-modulet skal du bruge [**cmdlet'en Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) og angive de egenskaber, der skal angives eller ændres.

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Rediger egenskaberne for en bestemt brugerkonto

Du identificerer kontoen med *ObjectID-parameteren og* angiver eller ændrer bestemte egenskaber ved hjælp af yderligere parametre. Her er en liste over de mest almindelige parametre:
  
- -Afdeling "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Efternavn "\<user last name>"

- -Mobile "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- By "\<city name>"

- -Stat "\<state name>"

- -PostalCode "\<postal code>"

- -Land "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Dette er lande- eller områdekoden for to bogstaver i ISO 3166-1 alpha-2 (A2).

Du kan finde yderligere parametre [under Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Før du kan tildele licenser til en brugerkonto, skal du tildele en brugsplacering.

Kør følgende kommando for at få vist brugerens hovednavn for dine brugerkonti.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1. Sortér listen over brugerens hovednavne alfabetisk (**Sortér UserPrincipalName**), og send den til den næste kommando (**|**).

1. Vis kun egenskaben Brugerens hovednavn for hver konto (**Vælg UserPrincipalName**).

1. Vise dem ét skærmbillede ad gangen (**Mere**).

For at få vist brugerens hovednavn for en konto baseret på dens viste navn (for- og efternavn) skal du køre følgende kommandoer. Udfyld *variablen $userName* , og fjern tegnene \< and > :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

I dette eksempel vises brugerens hovednavn for den brugerkonto, der har det viste navn *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Ved hjælp af *$upn* variabel kan du foretage ændringer til individuelle konti baseret på deres viste navn. Her er et eksempel, der angiver *belinda Newmans* brugsplacering til Frankrig. Men den angiver hendes viste navn i stedet for brugerens hovednavn:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Rediger egenskaberne for alle brugerkonti

Hvis du vil ændre egenskaberne for alle brugere, kan du bruge en kombination af cmdlet'erne **Get-AzureADUser** og **Set-AzureADUser** . I følgende eksempel ændres brugsplaceringen for alle brugere til *Frankrig*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1. Angiv brugerplaceringen til Frankrig (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Rediger egenskaberne for et bestemt sæt brugerkonti

Hvis du vil ændre egenskaberne for et bestemt sæt brugerkonti, kan du bruge en kombination af cmdlet'erne **Get-AzureADUser**, **Where** og **Set-AzureADUser** . I følgende eksempel ændres brugsplaceringen for alle brugere i regnskabsafdelingen til *Frankrig*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1.  Find alle de brugerkonti, der har deres *afdelingsegenskab* angivet til "Regnskab" (**Hvor {$_. Afdeling -eq "Accounting"}**), og send de resulterende oplysninger til den næste kommando (**|**).

1. Angiv brugerplaceringen til Frankrig (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

For at konfigurere egenskaber for brugerkonti med Microsoft Azure Active Directory-modulet til Windows PowerShell skal du bruge **cmdlet'en Set-MsolUser** og angive de egenskaber, der skal angives eller ændres.

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Rediger egenskaberne for en bestemt brugerkonto

Hvis du vil konfigurere egenskaber for en bestemt brugerkonto, skal du bruge [**cmdlet'en Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) og angive de egenskaber, der skal angives eller ændres. 

Du identificerer kontoen med parameteren *-UserPrincipalName* og angiver eller ændrer specifikke egenskaber ved hjælp af yderligere parametre. Her er en liste over de mest almindelige parametre.
  
- By "\<city name>"

- -Land "\<country name>"

- -Afdeling "\<department name>"

- -DisplayName "\<full user name>"

- -Fax "\<fax number>"

- -Fornavn "\<user first name>"

- -Efternavn "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- -Office "\<office location>"

- -Telefonnummer "\<office phone number>"

- -PostalCode "\<postal code>"

- -PreferredLanguage "\<language>"

- -Stat "\<state name>"

- -StreetAddress "\<street address>"

- -Title "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    Dette er lande- eller områdekoden for to bogstaver i ISO 3166-1 alpha-2 (A2).

Du kan finde yderligere parametre [under Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Kør følgende kommando for at få vist brugerens hovednavne for alle dine brugere:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).

1. Sortér listen over brugerens hovednavne alfabetisk (**Sortér UserPrincipalName**), og send den til den næste kommando (**|**).

1. Vis kun egenskaben Brugerens hovednavn for hver konto (**Vælg UserPrincipalName**).

1. Vise dem ét skærmbillede ad gangen (**Mere**).

For at få vist brugerens hovednavn for en konto baseret på dens viste navn (for- og efternavn) skal du køre følgende kommandoer. Udfyld *variablen $userName* , og fjern tegnene \< and > .
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

I dette eksempel vises brugerens hovednavn for den bruger, der hedder Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Ved hjælp af *$upn* variabel kan du foretage ændringer til individuelle konti baseret på deres viste navn. Her er et eksempel, der angiver *Belinda Newmans* brugsplacering til *Frankrig*, men angiver hendes visningsnavn i stedet for brugerens hovednavn:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Rediger egenskaberne for alle brugerkonti

Hvis du vil ændre egenskaberne for alle brugere, skal du bruge en kombination af **cmdlet'erne Get-MsolUser** og **Set-MsolUser** . I følgende eksempel ændres brugsplaceringen for alle brugere til *Frankrig*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).

1. Angiv brugerplaceringen til Frankrig (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Rediger egenskaberne for et bestemt sæt brugerkonti

Hvis du vil ændre egenskaberne for et bestemt sæt brugerkonti, kan du bruge en kombination af cmdlet'erne **Get-MsolUser**, **Where** og **Set-MsolUser** . I følgende eksempel ændres brugsplaceringen for alle brugere i regnskabsafdelingen til *Frankrig*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).

1. Find alle brugerkonti, der har deres *afdelingsegenskab* angivet til "Regnskab" (**hvor {$_. Afdeling -eq "Accounting"}**) og sende de resulterende oplysninger til den næste kommando (**|**).

1. Angiv brugerplaceringen til Frankrig (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
