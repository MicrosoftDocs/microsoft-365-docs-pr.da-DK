---
title: Vis Microsoft 365-brugerkonti med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du får vist, viser Microsoft 365 brugerkonti på forskellige måder med PowerShell.
ms.openlocfilehash: 5c434825da95fd7d90594b2424cab287305f7d26
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63591025"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>Vis Microsoft 365-brugerkonti med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan bruge Microsoft 365 Administration til at få vist kontiene for din Microsoft 365 lejer. PowerShell til Microsoft 365 dette, men giver også yderligere funktionalitet.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Få vist alle konti

Kør denne kommando for at få vist den komplette liste over brugerkonti:
  
```powershell
Get-AzureADUser
```

Du bør få oplysninger, der ligner dette:
  
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

Kør følgende kommando for at få vist en bestemt brugerkonto. Udfyld brugerkontoens logonkontonavn, hvilket også kaldes brugerens hovednavn (UPN). Fjern tegnene "<" og ">".
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Få vist flere egenskabsværdier for en bestemt konto

Som standard viser **cmdlet'en Get-AzureADUser** kun *egenskaberne ObjectID*, *DisplayName* og *UserPrincipalName* for konti.

Hvis du vil være mere selektiv med de egenskaber, der skal vises, skal du bruge Cmdlet'en **Select** sammen med **get-AzureADUser-cmdlet'en** . Hvis du vil kombinere de to cmdlet'er, skal du bruge "pipe"-tegnet ("|"), som giver Azure Active Directory PowerShell til Graph besked om at tage resultaterne af én kommando og sende den til den næste kommando. Her er en eksempelkommando, der viser *DisplayName*, *Department* og *UsageLocation* for hver brugerkonto:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).
    
1.  Vis kun brugernavn, afdeling og brugsplacering (**Vælg Visningsnavn, Afdeling, Brugsplacering**).
  
Hvis du vil have vist alle egenskaberne for en bestemt brugerkonto,  skal du bruge cmdlet'en Select og jokertegnet (*). Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

Som et andet eksempel kan du køre følgende kommando for at kontrollere den aktiverede status for en bestemt brugerkonto:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>Vis kontosynkroniseringsstatus

Brugerkonti har to kilder: 

- Windows Server Active Directory (AD), som er konti, der synkroniseres fra det lokale AD til skyen.

- Azure Active Directory konti (Azure AD), der er oprettet direkte i skyen.

Du kan bruge følgende kommando til at finde konti, der synkroniseres fra **ad i det lokale** miljø. Det instruerer PowerShell om at få alle brugere, der har attributten *DirSyncEnabled* angivet til *Sand*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

Du kan bruge følgende kommando til at finde **konti, der kun findes i skyen** . Det instruerer PowerShell om at indstille alle brugere, der har attributten *DirSyncEnabled* angivet til *Falsk* eller ikke (*Null*).
En konto, der aldrig blev synkroniseret fra ad i det lokale miljø, har *DirSyncEnabled angivet* til *Null*. En konto, der oprindeligt blev synkroniseret fra AD i det lokale miljø, men som ikke længere synkroniseres, har *DirSyncEnabled* angivet til *Falsk*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>Få vist konti baseret på en fælles egenskab

Hvis du vil være mere selektiv med listen over konti, der skal vises, kan  du bruge Where-cmdlet'en sammen med cmdlet'en **Get-AzureADUser**. Hvis du vil kombinere de to cmdlet'er, skal du bruge "pipe"-tegnet ("|"), som giver Azure Active Directory PowerShell til Graph besked om at tage resultaterne af én kommando og sende den til den næste kommando. Her er en eksempelkommando, der kun viser de brugerkonti, der har en uspecificeret brugsplacering:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

Denne kommando instruerer Azure Active Directory PowerShell til Graph at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-AzureADUser**), og send dem til den næste kommando (**|**).
    
1. Find alle de brugerkonti, der har en uspecificeret brugsplacering (**hvor {$\_. UsageLocation -eq $Null}**). I klammeparenteserne instruerer kommandoen PowerShell til kun at finde det sæt af konti, for hvilke brugerkontoegenskaben Brugsplacering (**$\_. UsageLocation**) er ikke angivet (**lige $Null**).
    
Egenskaben **Brugsplacering** er kun én af mange egenskaber, der er knyttet til en brugerkonto. Hvis du vil have vist alle egenskaberne for en bestemt brugerkonto,  skal du bruge cmdlet'en Select og jokertegnet (*). Her er et eksempel:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

By er **f.eks** . navnet på en brugerkontoegenskab. Du kan bruge følgende kommando til at få vist alle konti for brugere, der bor i London:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Syntaksen for cmdlet'en **Where** i disse eksempler er **Hvor {$\_.** [navn på brugerkontoegenskab] [sammenligningsoperator] [værdi] **}**.> [sammenligningsoperator] er **-eq** for er lig med, **-ne** for ikke er lig med, **-lt** for mindre end, **-gt** for større end og andre.  [værdi] er typisk en streng (en række bogstaver, tal og andre tegn), en numerisk værdi **eller $Null** for uspecificeret. Du kan finde flere oplysninger under [Hvor](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Få vist alle konti

Kør denne kommando for at få vist den komplette liste over brugerkonti:
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
>

Du bør få oplysninger, der ligner dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Cmdlet'en Get-MsolUser** har også et sæt parametre til at filtrere sættet af viste brugerkonti. For eksempel skal du køre denne kommando for listen over brugere uden licens (brugere, der er blevet føjet til Microsoft 365, men endnu ikke har fået licens til at bruge nogen af tjenesterne):
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Du bør få oplysninger, der ligner dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Du kan finde oplysninger om yderligere parametre til filtrering af sættet af brugerkonti, der vises, under [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>Få vist en bestemt konto

Kør følgende kommando for at få vist en bestemt brugerkonto. Udfyld logonnavnet på brugerkontoen, hvilket også kaldes brugerens hovednavn (UPN). Fjern tegnene "<" og ">".
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>Få vist konti baseret på en fælles egenskab

Hvis du vil være mere selektiv med listen over konti, der skal vises, kan  du bruge Where-cmdlet'en sammen med cmdlet'en **Get-MsolUser**. For at kombinere de to cmdlet'er skal du bruge "pipe"-tegnet ("|"), som beder PowerShell om at tage resultaterne af én kommando og sende den til den næste kommando. Her er et eksempel, der kun viser de brugerkonti, der har en uspecificeret brugsplacering:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Find alle brugerkonti, der har en uspecificeret brugsplacering (**hvor {$\_). UsageLocation -eq $Null}**). I klammeparenteserne instruerer kommandoen PowerShell til kun at finde det sæt af konti, for hvilke brugerkontoegenskaben Brugsplacering (**$\_. UsageLocation**) er ikke angivet (**lige $Null**).
    
Du bør få oplysninger, der ligner dette:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

Egenskaben *Brugsplacering* er kun én af mange egenskaber, der er knyttet til en brugerkonto. Hvis du vil have vist alle egenskaberne for brugerkonti, skal du bruge Cmdlet'en **Select** og jokertegnet (*) for at få vist dem alle for en bestemt brugerkonto. Her er et eksempel:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

By er *f.eks* . navnet på en brugerkontoegenskab. Du kan bruge følgende kommando til at få vist alle brugerkonti for brugere, der bor i London:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> Syntaksen for cmdlet'en **Where** i disse eksempler er **Hvor {$\_.** [navn på brugerkontoegenskab] [sammenligningsoperator] [værdi] **}**.  [sammenligningsoperator] er **-eq** for er lig med, **-ne** for ikke er lig med, **-lt** for mindre end, **-gt** for større end og andre.  [værdi] er typisk en streng (en række bogstaver, tal og andre tegn), en numerisk værdi **eller $Null** for uspecificeret. Du kan finde flere oplysninger under [Hvor](/powershell/module/microsoft.powershell.core/where-object).
  
Hvis du vil kontrollere blokeret status for en brugerkonto, skal du bruge følgende kommando:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Få vist flere egenskabsværdier for konti

Som standard viser **cmdlet'en Get-MsolUser** disse tre egenskaber for brugerkonti:
  
- UserPrincipalName

- DisplayName

- isLicensed

Hvis du har brug for yderligere egenskaber, f.eks. den afdeling, hvor brugeren arbejder, og det land/område, hvor brugeren bruger Microsoft 365-tjenester, kan du køre **Get-MsolUser** sammen med cmdlet'en **Select** for at angive listen over egenskaber for brugerkontoen. Her er et eksempel:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Vis kun brugernavn, afdeling og brugsplacering (**Vælg Visningsnavn, Afdeling, Brugsplacering**).
    
Du bør få oplysninger, der ligner dette:
  
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

Du **kan bruge** cmdlet'en Select til at vælge, hvilke egenskaber der skal vises. Hvis du vil have vist alle egenskaberne for en bestemt brugerkonto, skal du bruge jokertegnet (*). Her er et eksempel:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

Hvis du vil være mere selektiv med listen over de konti, der skal vises, kan du også bruge **Cmdlet'en** Where. Her er en eksempelkommando, der kun viser de brugerkonti, der har en uspecificeret brugsplacering:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

Denne kommando instruerer PowerShell i at:
  
1. Hent alle oplysninger om brugerkontiene (**Get-MsolUser**), og send dem til den næste kommando (**|**).
    
1. Find alle brugerkonti, der har en uspecificeret brugsplacering (**hvor {$\_). UsageLocation -eq $Null}**), og sende de resulterende oplysninger til den næste kommando (**|**). I klammeparenteserne instruerer kommandoen PowerShell til kun at finde det sæt af konti, for hvilke brugerkontoegenskaben Brugsplacering (**$\_. UsageLocation**) er ikke angivet (**lige $Null**).
    
1. Vis kun brugernavn, afdeling og brugsplacering (**Vælg Visningsnavn, Afdeling, Brugsplacering**).
    
Du bør få oplysninger, der ligner dette:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Hvis du bruger katalogsynkronisering til at oprette og administrere dine Microsoft 365-brugere, kan du få vist den lokale konto, hvorfra en Microsoft 365-bruger er blevet projiceret. I følgende eksempel forudsættes det, at:

- Azure AD Forbind konfigureret til at bruge standardkildeankeret for ObjectGUID. Du kan finde flere oplysninger om konfiguration af et kildeanker i [Azure AD Forbind: Designkoncepter](/azure/active-directory/hybrid/plan-connect-design-concepts).
- Det Active Directory-domæneservices til PowerShell er installeret (se [RSAT-værktøjer](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
