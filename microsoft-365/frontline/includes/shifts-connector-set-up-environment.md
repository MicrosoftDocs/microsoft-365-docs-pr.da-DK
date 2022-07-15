---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: 3d4ec38f0007460fa119e69eadc79cd9c51887ee
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823881"
---
1. Installér PowerShell version 7 eller nyere. Du kan finde en trinvis vejledning under [Installation af PowerShell på Windows](/powershell/scripting/install/installing-powershell-on-windows).

1. Kør PowerShell i administratortilstand.
1. Installér Microsoft Graph PowerShell-modulet.

    ```powershell
    Install-Module Microsoft.Graph
    Import-Module Microsoft.Graph
    ```

    Kontrollér, at det er version 1.6.1 eller nyere.

    ```powershell
    Get-InstalledModule Microsoft.Graph 
    ```

1. Installér Teams Preview PowerShell-modulet.

    ```powershell
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force
    Import-Module MicrosoftTeams 
    ```

    Kontrollér, at den er mindst version 4.1.0 og indeholder Shifts-connector-cmdlet'erne.

    ```powershell
    Get-Command -Module MicrosoftTeams -Name *teamsshiftsconnection* 
    ```

1. Indstil PowerShell til at afslutte, hvis der opstår en fejl, når scriptet køres.

    ```powershell
    $ErrorActionPreference = "Stop" 
    ```

1. Aktivér scripts til at køre i Windows.

    ```powershell
    Set-ExecutionPolicy bypass 
    ```