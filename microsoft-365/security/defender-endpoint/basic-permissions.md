---
title: Brug grundlæggende tilladelser til at få adgang til Microsoft Defender Security Center
description: Få mere at vide om, hvordan du bruger grundlæggende tilladelser til at få adgang til Microsoft Defender for Endpoint-portalen.
keywords: tildel brugerroller, tildel læse- og skriveadgang, tildel skrivebeskyttet adgang, brugerroller, roller
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 27c480a0d4c95e79619e10f8fa42efb2c268b18c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63592842"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>Brug grundlæggende tilladelser til at få adgang til portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- Azure Active Directory
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

Se vejledningen nedenfor for at bruge grundlæggende administration af tilladelser.

Du kan bruge en af følgende løsninger:

- Azure PowerShell
- Azure-portal

Hvis du vil have detaljeret kontrol over tilladelser, [skal du skifte til rollebaseret adgangskontrol](rbac.md).

## <a name="assign-user-access-using-azure-powershell"></a>Tildel brugeradgang ved hjælp Azure PowerShell

Du kan tildele brugere et af følgende tilladelsesniveauer:

- Fuld adgang (læs og skriv)
- Skrivebeskyttet adgang

### <a name="before-you-begin"></a>Før du begynder

- Installér Azure PowerShell. Du kan finde flere oplysninger [under Sådan installeres og konfigureres Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > Du skal køre PowerShell-cmdletterne i en kommandolinje med administrator administrator.

- Forbind til din Azure Active Directory. Du kan finde flere oplysninger [Forbind-MsolService](/powershell/module/msonline/connect-msolservice).

  - **Fuld adgang**: Brugere med fuld adgang kan logge på, få vist alle systemoplysninger og løse beskeder, sende filer til dybdegående analyse og downloade onboardingpakken. Tildeling af fulde adgangsrettigheder kræver, at brugerne føjes til "sikkerhedsadministratoren" eller "global administrator" AAD indbyggede roller.
  - **Skrivebeskyttet adgang**: Brugere med skrivebeskyttet adgang kan logge på, få vist alle beskeder og relaterede oplysninger.

    De vil ikke kunne ændre beskedtilstande, sende filer til dybdegående analyse eller udføre nogen tilstandsændringer.

    Tildeling af skrivebeskyttede adgangsrettigheder kræver, at brugerne føjes til den indbyggede Azure AD-rolle "Sikkerhedslæser".

Brug følgende trin til at tildele sikkerhedsroller:

- For **læse- og skriveadgang** skal du tildele brugere rollen som sikkerhedsadministrator ved hjælp af følgende kommando:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- For **skrivebeskyttet adgang** skal du tildele brugere rollen som sikkerhedslæser ved hjælp af følgende kommando:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

Få mere at vide under [Tilføj eller fjern gruppemedlemmer ved hjælp Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## <a name="assign-user-access-using-the-azure-portal"></a>Tildel brugeradgang via Azure-portalen

Få mere at vide under [Tildel administratorroller og ikke-administratorroller til brugere med Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## <a name="related-topic"></a>Relateret emne

- [Administrer portaladgang ved hjælp af RBAC](rbac.md)
