---
title: Bloker Microsoft 365 brugerkonti med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/16/2020
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
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Sådan bruger du PowerShell til at blokere og fjerne blokeringen af adgang til Microsoft 365 konti.
ms.openlocfilehash: ffeac03f9f48e6531443a8f90a3d5fd3506172fe
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091605"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>Bloker Microsoft 365 brugerkonti med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Når du blokerer adgang til en Microsoft 365 konto, forhindrer du alle i at bruge kontoen til at logge på og få adgang til tjenesterne og dataene i din Microsoft 365 organisation. Du kan bruge PowerShell til at blokere adgang til individuelle eller flere brugerkonti.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>Bloker adgang til individuelle brugerkonti

Brug følgende syntaks til at blokere en individuel brugerkonto:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Parameteren *-ObjectID* i **Set-AzureAD-cmdlet'en** accepterer enten kontoens logonnavn, også kaldet brugerens hovednavn, eller kontoens objekt-id.

I dette eksempel blokeres adgangen til brugerkontoen *fabricec@litwareinc.com*.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Kør følgende kommando for at fjerne blokeringen af denne brugerkonto:

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Hvis du vil have vist brugerkontoens UPN baseret på brugerens viste navn, skal du bruge følgende kommandoer:

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

I dette eksempel vises brugerkontoen UPN for brugeren  *Caleb Sills*.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Hvis du vil blokere en konto, der er baseret på brugerens viste navn, skal du bruge følgende kommandoer:

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

Hvis du vil kontrollere en brugerkontos blokerede status, skal du bruge følgende kommando:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>Bloker flere brugerkonti

Hvis du vil blokere adgang for flere brugerkonti, skal du oprette en tekstfil, der indeholder ét kontologonnavn på hver linje som denne:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

I følgende kommandoer er eksempeltekstfilen *C:\Mine Documents\Accounts.txt*. Erstat dette filnavn med stien til og filnavnet på tekstfilen.

Kør følgende kommando for at blokere adgangen til de konti, der er angivet i tekstfilen:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

Hvis du vil fjerne blokeringen af de konti, der er angivet i tekstfilen, skal du køre følgende kommando:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>Bloker individuelle brugerkonti

Brug følgende syntaks til at blokere adgang for en individuel brugerkonto:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell modul og cmdlet'er, der har *Msol* i deres navn. Du skal køre disse cmdlet'er fra Windows PowerShell.

I dette eksempel blokeres adgangen til brugerkontoen *fabricec\@ litwareinc.com*.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Kør følgende kommando for at fjerne blokeringen af brugerkontoen:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

Hvis du vil kontrollere en brugerkontos blokerede status, skal du køre følgende kommando:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>Bloker adgang for flere brugerkonti

Først skal du oprette en tekstfil, der indeholder én konto på hver linje som denne:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

I følgende kommandoer er eksempeltekstfilen *C:\Mine Documents\Accounts.txt*. Erstat dette filnavn med stien til og filnavnet på tekstfilen.

Hvis du vil blokere adgang for de konti, der er angivet i tekstfilen, skal du køre følgende kommando:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Kør følgende kommando for at fjerne blokeringen af de konti, der er angivet i tekstfilen:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
