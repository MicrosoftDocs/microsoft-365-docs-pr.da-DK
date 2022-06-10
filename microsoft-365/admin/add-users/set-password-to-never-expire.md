---
title: Angiv en individuel brugers adgangskode til aldrig at udløbe
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: Log på din Microsoft 365 administratorkonto for at angive, at nogle individuelle brugeradgangskoder aldrig skal udløbe, ved hjælp af Azure AD PowerShell.
ms.openlocfilehash: a8357e3c72ea4bcd30234492b30e75eff8cb123a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010184"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Angiv en individuel brugers adgangskode til aldrig at udløbe

I denne artikel forklares det, hvordan du angiver en adgangskode for en individuel bruger, så den ikke udløber. Du skal fuldføre disse trin ved hjælp af PowerShell.

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er til personer, der angiver en politik for udløb af adgangskode for en virksomhed, skole eller nonprofitorganisation. Hvis du vil fuldføre disse trin, skal du logge på med din Microsoft 365 administratorkonto. Se [Oversigt over Microsoft 365 Administration](/microsoft-365/admin/admin-overview/admin-center-overview).

Du skal være [global administrator eller adgangskodeadministrator](about-admin-roles.md) for at kunne udføre disse trin.

En global administrator af en Microsoft-cloudtjeneste kan bruge [Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2) til at angive adgangskoder, der ikke skal udløbe for bestemte brugere. Du kan også bruge [](/powershell/module/Azuread) AzureAD-cmdlet'er til at fjerne konfigurationen, der aldrig udløber, eller til at se, hvilke brugeradgangskoder der er angivet til aldrig at udløbe.

Denne vejledning gælder for andre udbydere, f.eks. Intune og Microsoft 365, som også er afhængige af Azure AD for identitets- og katalogtjenester. Udløb af adgangskode er den eneste del af politikken, der kan ændres.

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Sådan kontrollerer du udløbspolitikken for en adgangskode

Du kan få flere oplysninger om kommandoen Get-AzureADUser i AzureAD-modulet i referenceartiklen [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

Kør en af følgende kommandoer:

- Hvis du vil se, om en enkelt brugers adgangskode er indstillet til aldrig at udløbe, skal du køre følgende cmdlet ved hjælp af UPN (f.eks. *user@contoso.onmicrosoft.com*) eller bruger-id'et for den bruger, du vil kontrollere:

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    Eksempel:

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- Hvis du vil se, at indstillingen **Adgangskode aldrig udløber** for alle brugere, skal du køre følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Sådan henter du en rapport over alle brugere med PasswordNeverExpires i HTML på skrivebordet for den aktuelle bruger med navnet  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Sådan henter du en rapport over alle brugere med PasswordNeverExpires i CSV på skrivebordet for den aktuelle bruger med navnet **ReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- Hvis du vil angive adgangskoder for alle brugerne i en organisation til aldrig at udløbe, skal du køre følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Brugerkonti, der er konfigureret med parameteren `-PasswordPolicies DisablePasswordExpiration` still age baseret på attributten `pwdLastSet` . Hvis du på baggrund af attributten `pwdLastSet` ændrer udløb til `-PasswordPolicies None`, kræver alle adgangskoder, der har et pwdLastSet, der er ældre end 90 dage, at brugeren ændrer dem, næste gang de logger på. Denne ændring kan påvirke et stort antal brugere.

### <a name="set-a-password-to-expire"></a>Angiv en adgangskode, der skal udløbe

Kør en af følgende kommandoer:

- Hvis du vil angive adgangskoden for én bruger, så adgangskoden udløber, skal du køre følgende cmdlet ved hjælp af UPN eller brugerens bruger-id:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Hvis du vil angive adgangskoderne for alle brugere i organisationen, så de udløber, skal du bruge følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Relateret indhold

[Lad brugerne nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)\
[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)\
[Angiv politikken for udløb af adgangskode for din organisation](../manage/set-password-expiration-policy.md) (artikel)
