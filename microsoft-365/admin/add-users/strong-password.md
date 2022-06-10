---
title: Deaktiver stærke adgangskodekrav for brugere
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Hvis du er administrator og administrerer adgangskodepolitik for en virksomhed, skole eller nonprofitorganisation, kan du angive stærke adgangskodekrav ved hjælp af Azure AD PowerShell.
ms.openlocfilehash: e98c9a3f7b31cbb53d4c853487f4908a6dec72d5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010250"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Deaktiver stærke adgangskodekrav for brugere

I denne artikel forklares det, hvordan du deaktiverer stærke adgangskodekrav for dine brugere. Stærke krav til adgangskoder er som standard slået til i din Microsoft 365 for virksomhedsorganisation. Din organisation kan have krav om at deaktivere stærke adgangskoder. Følg nedenstående trin for at slå stærke krav til adgangskoder fra. Du skal fuldføre disse trin ved hjælp af PowerShell.

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er til personer, der administrerer adgangskodepolitikken for en virksomhed, skole eller nonprofitorganisation. Hvis du vil fuldføre disse trin, skal du logge på med din Microsoft 365 administratorkonto. [Hvad er en administratorkonto?] (Oversigt over Microsoft 365 Administration](.. /admin-overview/admin-center-overview.md) Du skal være [global administrator eller adgangskodeadministrator](about-admin-roles.md) for at kunne udføre disse trin.

Du skal også oprette forbindelse til Microsoft 365 med PowerShell.

## <a name="set-strong-passwords"></a>Angiv stærke adgangskoder

1. [Forbind til at Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Ved hjælp af PowerShell kan du slå stærke adgangskodekrav fra for alle brugere med følgende kommando:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> UserPrincipalName skal være i internetlogonformatet, hvor brugernavnet efterfølges af at-tegnet (@) og et domænenavn. Eksempel: user@contoso.com.

## <a name="related-content"></a>Relateret indhold

[Sådan opretter du forbindelse til Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Flere oplysninger om PowerShell MsolUser-kommandoer](/powershell/azure/active-directory/install-adv2)

[Flere oplysninger om adgangskodepolitik](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
