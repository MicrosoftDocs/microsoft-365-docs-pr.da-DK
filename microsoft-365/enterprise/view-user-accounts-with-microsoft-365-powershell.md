---
title: Få vist Microsoft 365 brugerkonti med PowerShell
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: Få mere at vide om, hvordan du får vist, viser eller viser dine Microsoft 365 brugerkonti på forskellige måder med PowerShell.
ms.openlocfilehash: cbbb188c50e4d163d5ef4226a83968c64e8a260c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090723"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Få vist Microsoft 365 brugerkonti med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge Microsoft 365 Administration til at få vist kontiene for din Microsoft 365 lejer. PowerShell til Microsoft 365 aktiverer dette, men indeholder også yderligere funktionalitet.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Få vist alle konti

Hvis du vil have vist en komplet liste over brugerkonti, skal du køre denne kommando:
  
```powershell
Get-AzureADUser
```

Du bør få oplysninger svarende til dette:
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Få vist en bestemt konto

Kør følgende kommando for at få vist en bestemt brugerkonto. Udfyld logonkontonavnet på brugerkontoen, som også kaldes brugerens hovednavn. Fjern tegnene "<" og ">".
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Få vist yderligere egenskabsværdier for en bestemt konto

Som standard viser cmdlet'en **Get-AzureADUser** kun egenskaberne *ObjectID*, *DisplayName* og *UserPrincipalName* for konti.

Hvis du vil være mere selektiv med hensyn til de egenskaber, der skal vises, skal du bruge cmdlet'en **Vælg** sammen med cmdlet'en **Get-AzureADUser** . Hvis du vil kombinere de to cmdlet'er, skal du bruge tegnet "pipe" ("|"), som fortæller Azure Active Directory PowerShell, at Graph skal tage resultaterne af én kommando og sende den til den næste kommando. Her er et eksempel på en kommando, der viser *DisplayName*, *Department* og *UsageLocation* for hver brugerkonto:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).
    
1.  Vis kun brugerkontonavnet, afdelingen og anvendelsesplaceringen (**Vælg Visningsnavn, Afdeling, UsageLocation**).
  
Hvis du vil se alle egenskaberne for en bestemt brugerkonto, skal du bruge **vælg** cmdlet'en og jokertegnet (*). Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Som et andet eksempel skal du køre følgende kommando for at kontrollere den aktiverede status for en bestemt brugerkonto:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Vis status for kontosynkronisering

Brugerkonti har to kilder: 

- Windows Ad (Server Active Directory), som er konti, der synkroniseres fra AD i det lokale miljø til cloudmiljøet.

- Azure Active Directory (Azure AD)-konti, som oprettes direkte i cloudmiljøet.

Du kan bruge følgende kommando til at finde konti, der synkroniserer fra det **lokale** AD. Den instruerer PowerShell i at få alle brugere, der har attributten *DirSyncEnabled* angivet til *Sand*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Du kan bruge følgende kommando til at finde konti **, der kun findes i skyen** . Den instruerer PowerShell om at få alle brugere, der har attributten *DirSyncEnabled* angivet til *Falsk* eller ikke angivet (*Null*).
*DirSyncEnabled* er angivet til *Null* for en konto, der aldrig blev synkroniseret fra det lokale AD. *DirSyncEnabled* er angivet til *Falsk* for en konto, der oprindeligt blev synkroniseret fra det lokale AD, men som ikke længere synkroniseres. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Få vist konti baseret på en fælles egenskab

Hvis du vil være mere selektiv med hensyn til listen over konti, der skal vises, kan du bruge Where-cmdlet'en sammen med **Cmdlet'en Get-AzureADUser**. Hvis du vil kombinere de to cmdlet'er, skal du bruge tegnet "pipe" ("|"), som fortæller Azure Active Directory PowerShell, at Graph skal tage resultaterne af én kommando og sende den til den næste kommando. Her er et eksempel på en kommando, der kun viser de brugerkonti, der har en ikke-angivet anvendelsesplacering:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Denne kommando instruerer Azure Active Directory PowerShell, så Graph:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).
    
1. Find alle de brugerkonti, der har en ikke-angivet anvendelsesplacering (**Hvor {$\_. UsageLocation -eq $Null}**). I klammeparenteserne instruerer kommandoen PowerShell om kun at finde det sæt konti, som brugerkontoegenskaben UsageLocation (**$\_. UsageLocation**) er ikke angivet (**-eq $Null**).
    
Egenskaben **UsageLocation** er kun én af de mange egenskaber, der er knyttet til en brugerkonto. Hvis du vil have vist alle egenskaberne for en bestemt brugerkonto, skal du bruge cmdlet'en **Vælg** og jokertegnet (*). Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

**City** er f.eks. navnet på en brugerkontoegenskab. Du kan bruge følgende kommando til at få vist alle konti for brugere, der bor i London:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Syntaksen for Where-cmdlet'en i disse eksempler er **Where {$\_.**  [Navn på brugerkontoegenskab] [sammenligningsoperator] [værdi] **}**.> [sammenligningsoperator] er **-eq** for lig med, **-ne** for ikke lig med, **-lt** for mindre end, **-gt** for større end og andre.  [value] er typisk en streng (en sekvens af bogstaver, tal og andre tegn), en numerisk værdi eller **$Null** for ikke-angivet. Du kan få flere oplysninger under [Hvor](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Få vist alle konti

Hvis du vil have vist en komplet liste over brugerkonti, skal du køre denne kommando:
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
>

Du bør få oplysninger svarende til dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser-cmdlet'en** har også et sæt parametre til filtrering af det viste sæt brugerkonti. For listen over brugere uden licens (brugere, der er føjet til Microsoft 365, men endnu ikke har fået licens til at bruge nogen af tjenesterne), skal du f.eks. køre denne kommando:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Du bør få oplysninger svarende til dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Du kan finde oplysninger om yderligere parametre til filtrering af det sæt brugerkonti, der vises, under [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Få vist en bestemt konto

Kør følgende kommando for at få vist en bestemt brugerkonto. Udfyld logonnavnet på brugerkontoen, som også kaldes BRUGERENs hovednavn. Fjern tegnene "<" og ">".
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Få vist konti baseret på en fælles egenskab

Hvis du vil være mere selektiv med hensyn til listen over konti, der skal vises, kan du bruge Where-cmdlet'en sammen med **Cmdlet'en Get-MsolUser**. Hvis du vil kombinere de to cmdlet'er, skal du bruge tegnet "pipe" ("|"), som beder PowerShell om at tage resultaterne af én kommando og sende den til den næste kommando. Her er et eksempel, der kun viser de brugerkonti, der har en ikke-angivet anvendelsesplacering:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysningerne om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Find alle brugerkonti, der har en ikke-angivet anvendelsesplacering (**Hvor {$\_. UsageLocation -eq $Null}**). I klammeparenteserne instruerer kommandoen PowerShell om kun at finde det sæt konti, som brugerkontoegenskaben UsageLocation (**$\_. UsageLocation**) er ikke angivet (**-eq $Null**).
    
Du bør få oplysninger svarende til dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Egenskaben *UsageLocation* er kun én af de mange egenskaber, der er knyttet til en brugerkonto. Hvis du vil se alle egenskaberne for brugerkonti, skal du bruge **vælg** cmdlet'en og jokertegnet (*) til at få vist dem alle for en bestemt brugerkonto. Her er et eksempel:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

*City* er f.eks. navnet på en brugerkontoegenskab. Du kan bruge følgende kommando til at få vist alle brugerkonti for brugere, der bor i London:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Syntaksen for Where-cmdlet'en i disse eksempler er **Where {$\_.**  [Navn på brugerkontoegenskab] [sammenligningsoperator] [værdi] **}**.  [sammenligningsoperator] er **-eq** for lig med, **-ne** for ikke lig med, **-lt** for mindre end, **-gt** for større end og andre.  [value] er typisk en streng (en sekvens af bogstaver, tal og andre tegn), en numerisk værdi eller **$Null** for ikke-angivet. Du kan få flere oplysninger under [Hvor](/powershell/module/microsoft.powershell.core/where-object).
  
Hvis du vil kontrollere en brugerkontos blokerede status, skal du bruge følgende kommando:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Vis yderligere egenskabsværdier for konti

**Cmdlet'en Get-MsolUser** viser som standard disse tre egenskaber for brugerkonti:
  
- UserPrincipalName

- Displayname

- isLicensed

Hvis du har brug for yderligere egenskaber, f.eks. den afdeling, hvor brugeren arbejder, og det land/område, hvor brugeren bruger Microsoft 365 tjenester, kan du køre **Get-MsolUser** sammen med Cmdlet'en **Vælg** for at angive listen over egenskaber for brugerkontoen. Her er et eksempel:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Vis kun brugerkontonavnet, afdelingen og anvendelsesplaceringen (**Vælg Visningsnavn, Afdeling, UsageLocation**).
    
Du bør få oplysninger svarende til dette:
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

Med **Vælg** cmdlet kan du vælge, hvilke egenskaber der skal vises. Hvis du vil have vist alle egenskaberne for en bestemt brugerkonto, skal du bruge jokertegnet (*). Her er et eksempel:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Hvis du vil være mere selektiv med hensyn til listen over konti, der skal vises, kan du også **bruge** where-cmdlet'en. Her er et eksempel på en kommando, der kun viser de brugerkonti, der har en ikke-angivet anvendelsesplacering:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Find alle brugerkonti, der har en ikke-angivet anvendelsesplacering (**Hvor {$\_. UsageLocation -eq $Null}**), og send de resulterende oplysninger til den næste kommando (**|**). I klammeparenteserne instruerer kommandoen PowerShell om kun at finde det sæt konti, som brugerkontoegenskaben UsageLocation (**$\_. UsageLocation**) er ikke angivet (**-eq $Null**).
    
1. Vis kun brugerkontonavnet, afdelingen og anvendelsesplaceringen (**Vælg Visningsnavn, Afdeling, UsageLocation**).
    
Du bør få oplysninger svarende til dette:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Hvis du bruger katalogsynkronisering til at oprette og administrere dine Microsoft 365 brugere, kan du få vist den lokale konto, som en Microsoft 365 bruger er blevet forventet fra. I følgende eksempel antages det, at:

- Azure AD Forbind er konfigureret til at bruge standardkildeankeret for ObjectGUID. (Du kan få flere oplysninger om konfiguration af et kildeanker i [Azure AD Forbind: Designbegreber](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- Det Active Directory-domæneservices modul til PowerShell er blevet installeret (se [RSAT-værktøjer](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
