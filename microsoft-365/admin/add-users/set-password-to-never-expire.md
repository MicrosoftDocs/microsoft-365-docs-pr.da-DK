---
title: Indstil en individuel brugers adgangskode til aldrig at udløbe
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
description: Log på din Microsoft 365-administratorkonto for at indstille nogle individuelle brugeradgangskoder til aldrig at udløbe ved hjælp Windows PowerShell.
ms.openlocfilehash: f0eff70b2b95c7e318f8a7e52777d4b684dbd8bf
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589287"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Indstil en individuel brugers adgangskode til aldrig at udløbe

I denne artikel forklares det, hvordan du angiver en adgangskode for en enkelt bruger til ikke at udløbe. Du skal udføre disse trin ved hjælp af PowerShell.

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er for personer, der angiver udløbspolitikken for adgangskoder for en virksomhed, skole eller non-profit organisation. For at fuldføre disse trin skal du logge på med Microsoft 365 administratorkonto. Se [Oversigt over Microsoft 365 Administration](/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide).

Du skal være [global administrator eller adgangskodeadministrator for](about-admin-roles.md) at udføre disse trin.

En global administrator for en Microsoft-skytjeneste kan bruge [Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2) angive adgangskoder, der ikke udløber for bestemte brugere. Du kan også bruge [](/powershell/module/Azuread) AzureAD-cmdlet'er til at fjerne konfigurationen udløber aldrig eller for at se, hvilke brugeradgangskoder der er indstillet til aldrig at udløbe.

Denne vejledning gælder for andre udbydere, f.eks. Intune og Microsoft 365, som også er afhængige af Azure AD til identitets- og katalogtjenester. Udløb af adgangskode er den eneste del af politikken, der kan ændres.


## <a name="how-to-check-the-expiration-policy-for-a-password"></a>Sådan kontrolleres udløbspolitikken for en adgangskode

Du kan finde flere oplysninger Get-AzureADUser kommando i AzureAD-modulet i referenceartikel [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

Kør en af følgende kommandoer:

- Hvis du vil se, om en enkelt brugers adgangskode er indstillet til aldrig at udløbe, skal du køre følgende cmdlet ved hjælp af UPN (f.eks *. user@contoso.onmicrosoft.com*) eller bruger-id'et for den bruger, du vil kontrollere:

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

- Hvis du vil **have vist indstillingen Adgangskode udløber aldrig** for alle brugere, skal du køre følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- Sådan får du en rapport over alle brugere med PasswordNeverExpires i HTML på skrivebordet for den aktuelle bruger  **medReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- Sådan får du en rapport over alle brugere med PasswordNeverExpires i CSV på skrivebordet for den aktuelle bruger **medReportPasswordNeverExpires.csv**

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

- Hvis du vil indstille adgangskoderne for alle brugerne i en organisation til aldrig at udløbe, skal du køre følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> Brugerkonti, der er konfigureret med `-PasswordPolicies DisablePasswordExpiration` parameteren, stadig alder baseret på attributten `pwdLastSet` . Hvis du ændrer `pwdLastSet` udløb til , vil alle adgangskoder med `-PasswordPolicies None`en pwdLastSet, der er ældre end 90 dage, kræve, at brugeren ændrer dem, næste gang der logges på, baseret på attributten. Denne ændring kan påvirke et stort antal brugere.

### <a name="set-a-password-to-expire"></a>Angiv en adgangskode til at udløbe

Kør en af følgende kommandoer:

- Hvis du vil angive adgangskoden for en bruger, så adgangskoden udløber, skal du køre følgende cmdlet ved hjælp af brugerens UPN eller bruger-id:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- Hvis du vil angive adgangskoder for alle brugere i organisationen, så de udløber, skal du bruge følgende cmdlet:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>Relateret indhold

[Lad brugere nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)\
[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)\
[Angiv udløbspolitikken for adgangskoder for organisationen](../manage/set-password-expiration-policy.md) (artikel)
