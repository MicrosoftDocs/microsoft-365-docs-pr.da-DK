---
title: Slå krav til stærke adgangskoder fra for brugere
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
description: Få mere at vide om, hvordan du angiver stærke adgangskodekrav for dine brugere ved hjælp Windows PowerShell.
ms.openlocfilehash: 5932f01c2f17a72f4f6a20a6457d263bed7dd85e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63594349"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Slå krav til stærke adgangskoder fra for brugere

I denne artikel forklares det, hvordan du deaktiverer stærke adgangskodekrav for dine brugere. Stærke adgangskodekrav er som standard slået til i din Microsoft 365 for virksomhedsorganisation. Din organisation har muligvis krav om at deaktivere stærke adgangskoder. Følg nedenstående trin for at slå krav til stærke adgangskoder fra. Du skal udføre disse trin ved hjælp af PowerShell.

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er til personer, der administrerer adgangskodepolitik for en virksomhed, skole eller non-profit organisation. For at fuldføre disse trin skal du logge på med Microsoft 365 administratorkonto. [Hvad er en administratorkonto?] (Oversigt over Microsoft 365 Administration](.. /admin-overview/admin-center-overview.md) Du skal være [global administrator eller adgangskodeadministrator for](about-admin-roles.md) at udføre disse trin.

Du skal også oprette forbindelse til Microsoft 365 med PowerShell.

## <a name="set-strong-passwords"></a>Angiv stærke adgangskoder

1. [Forbind til Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Ved hjælp af PowerShell kan du deaktivere stærke adgangskodekrav for alle brugere med følgende kommando:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> userPrincipalName skal være i internetformatet, hvor brugernavnet efterfølges af snultegnet (@) og et domænenavn. For eksempel: user@contoso.com.

## <a name="related-content"></a>Relateret indhold

[Sådan opretter du forbindelse til Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Flere oplysninger om PowerShell MsolUser-kommandoer](/powershell/azure/active-directory/install-adv2)

[Flere oplysninger om adgangskodepolitik](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
