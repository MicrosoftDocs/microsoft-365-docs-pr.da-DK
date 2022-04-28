---
title: Konfigurer egenskaber for Microsoft 365 brugerkonto med PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: Brug PowerShell til Microsoft 365 til at konfigurere egenskaber for individuelle eller flere brugerkonti i din Microsoft 365 lejer.
ms.openlocfilehash: 3a1aa77a6af3995d7cd4d072b6b6c6047bf89942
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091341"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Konfigurer egenskaber for Microsoft 365 brugerkonto med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> til at konfigurere egenskaber for brugerkontiene i din Microsoft 365 lejer. I PowerShell kan du også gøre dette plus nogle andre ting, du ikke kan gøre i Administration.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Hvis du vil konfigurere egenskaber for brugerkonti i modulet Azure Active Directory PowerShell til Graph, skal du bruge [**Set-AzureADUser-cmdlet'en**](/powershell/module/azuread/set-azureaduser) og angive de egenskaber, der skal angives eller ændres.

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>Skift egenskaber for en bestemt brugerkonto

Du identificerer kontoen med parameteren *-ObjectID* og angiver eller ændrer specifikke egenskaber ved hjælp af yderligere parametre. Her er en liste over de mest almindelige parametre:
  
- -Afdeling "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Efternavn "\<user last name>"

- -Mobile "\<mobile phone number>"

- -Jobtitel "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -By "\<city name>"

- -Tilstand "\<state name>"

- -PostalCode "\<postal code>"

- -Land "\<country name>"

- -Telefonnummer "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    Dette er ISO 3166-1 alpha-2 (A2) med to bogstaver for lande- eller områdekoden.

Du kan finde flere parametre under [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> Før du kan tildele licenser til en brugerkonto, skal du tildele en anvendelsesplacering.

Kør følgende kommando for at få vist brugerens hovednavn for dine brugerkonti.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1. Sortér listen over brugerens hovednavne alfabetisk (**Sortér UserPrincipalName**), og send den til den næste kommando (**|**).

1. Vis kun egenskaben Brugerens hovednavn for hver konto (**vælg UserPrincipalName**).

1. Vis dem én skærm ad gangen (**Flere**).

Hvis du vil have vist brugerens hovednavn for en konto baseret på dens viste navn (for- og efternavn), skal du køre følgende kommandoer. Udfyld variablen *$userName* , og fjern tegnene \< and > :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

I dette eksempel vises brugerens hovednavn for den brugerkonto, der har det viste navn *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Ved hjælp af en *$upn* variabel kan du foretage ændringer af individuelle konti på baggrund af deres viste navn. Her er et eksempel, der angiver *Belinda Newmans* forbrugsplacering til Frankrig. Men det angiver hendes viste navn i stedet for brugerens hovednavn:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Skift egenskaber for alle brugerkonti

Hvis du vil ændre egenskaber for alle brugere, kan du bruge en kombination af Cmdlet'erne **Get-AzureADUser** og **Set-AzureADUser** . I følgende eksempel ændres forbrugsplaceringen for alle brugere til *Frankrig*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1. Angiv brugerens placering til Frankrig (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Skift egenskaber for et bestemt sæt brugerkonti

Hvis du vil ændre egenskaber for et bestemt sæt brugerkonti, kan du bruge en kombination af Cmdlet'erne **Get-AzureADUser**, **Where** og **Set-AzureADUser** . I følgende eksempel ændres anvendelsesplaceringen for alle brugere i regnskabsafdelingen til *Frankrig*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).

1.  Find alle de brugerkonti, hvor egenskaben *Afdeling* er angivet til "Regnskab" (**Hvor {$_. Department -eq "Accounting"}**), og send de resulterende oplysninger til den næste kommando (**|**).

1. Angiv brugerens placering til Frankrig (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Hvis du vil konfigurere egenskaber for brugerkonti med Microsoft Azure Active Directory modulet for Windows PowerShell, skal du bruge **Set-MsolUser-cmdlet'en** og angive de egenskaber, der skal angives eller ændres.

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>Skift egenskaber for en bestemt brugerkonto

Hvis du vil konfigurere egenskaber for en bestemt brugerkonto, skal du bruge [**Set-MsolUser-cmdlet'en**](/previous-versions/azure/dn194136(v=azure.100)) og angive de egenskaber, der skal angives eller ændres. 

Du identificerer kontoen med parameteren *-UserPrincipalName* og angiver eller ændrer specifikke egenskaber ved hjælp af yderligere parametre. Her er en liste over de mest almindelige parametre.
  
- -By "\<city name>"

- -Land "\<country name>"

- -Afdeling "\<department name>"

- -DisplayName "\<full user name>"

- -Fax "\<fax number>"

- -FirstName "\<user first name>"

- -LastName "\<user last name>"

- -Mobiltelefon "\<mobile phone number>"

- -Office "\<office location>"

- -PhoneNumber "\<office phone number>"

- -PostalCode "\<postal code>"

- -PreferredLanguage "\<language>"

- -Tilstand "\<state name>"

- -StreetAddress "\<street address>"

- -Titel "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    Dette er ISO 3166-1 alpha-2 (A2) med to bogstaver for lande- eller områdekoden.

Du kan finde flere parametre under [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

Hvis du vil se brugerens hovednavn på alle dine brugere, skal du køre følgende kommando:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til næste kommando (**|**).

1. Sortér listen over brugerens hovednavne alfabetisk (**Sortér UserPrincipalName**), og send den til den næste kommando (**|**).

1. Vis kun egenskaben Brugerens hovednavn for hver konto (**vælg UserPrincipalName**).

1. Vis dem én skærm ad gangen (**Flere**).

Hvis du vil have vist brugerens hovednavn for en konto baseret på dens viste navn (for- og efternavn), skal du køre følgende kommandoer. Udfyld variablen *$userName* , og fjern tegnene \< and > .
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

I dette eksempel vises brugerens hovednavn for brugeren med navnet Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Ved hjælp af en *$upn* variabel kan du foretage ændringer af individuelle konti på baggrund af deres viste navn. Her er et eksempel, der angiver *Belinda Newmans* forbrugsplacering til *Frankrig*, men angiver hendes viste navn i stedet for brugerens hovednavn:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Skift egenskaber for alle brugerkonti

Hvis du vil ændre egenskaber for alle brugere, skal du bruge en kombination af Cmdlet'erne **Get-MsolUser** og **Set-MsolUser** . I følgende eksempel ændres forbrugsplaceringen for alle brugere til *Frankrig*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).

1. Angiv brugerens placering til Frankrig (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Skift egenskaber for et bestemt sæt brugerkonti

Hvis du vil ændre egenskaber for et bestemt sæt brugerkonti, kan du bruge en kombination af Cmdlet'erne **Get-MsolUser**, **Where** og **Set-MsolUser** . I følgende eksempel ændres anvendelsesplaceringen for alle brugere i regnskabsafdelingen til *Frankrig*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).

1. Find alle brugerkonti, hvor egenskaben *Afdeling er* angivet til "Regnskab" (**Hvor {$_. Department -eq "Accounting"}**), og send de resulterende oplysninger til den næste kommando (**|**).

1. Angiv brugerens placering til Frankrig (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
