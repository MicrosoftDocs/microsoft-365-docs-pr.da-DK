---
title: Administrer Skype for Business Online med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: Brug PowerShell til Microsoft 365 at administrere Skype for Business Online-politikker, politikker pr. bruger og mødeindstillinger.
ms.openlocfilehash: cb546a7e4130509d7acd0021b3cb78df23c1819f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474466"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Administrer Skype for Business Online med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Skype for Business Online-administratorer er ansvarlige for administration af politikker. Selvom du kan udføre nogle af disse opgaver i programmet Microsoft 365 Administration, er andre nemmere at udføre i PowerShell.

## <a name="before-you-start"></a>Før du starter

> [!NOTE]
> Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste **Teams offentlige PowerShell-udgivelse**, behøver du ikke at installere Skype for Business Online Connector.

> [!NOTE]
> Skype for Business Online-administratorer kan administrere politikker **for Teams** **onlineapps Skype for Business Online-appen** via PowerShell.

Installer Teams [PowerShell-modulet](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>Forbind bruger administratorlegitimationsoplysninger

1. Åbn et Windows PowerShell kommandopromptvindue, og kør følgende kommandoer:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. Skriv navnet **Windows PowerShell og adgangskoden** til din administratorkonto i dialogboksen Anmod om **legitimationsoplysninger**, og vælg derefter OK.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Forbind bruger en administratorkonto med multifaktorgodkendelse

1. Åbn Windows PowerShell kommandopromptvindue, og kør følgende kommandoer:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Når du bliver bedt om at Skype for Business navnet på din onlineadministratorkonto.

3. I dialogboksen **Log på din konto skal** du skrive din Skype for Business Onlineadministratoradgangskode og vælge **Log på**.

4. I dialogboksen **Log på din konto skal** du følge vejledningen for at tilføje godkendelsesoplysninger, f.eks. en bekræftelseskode, og derefter vælge **Bekræft**.

Du kan finde flere oplysninger under:

- [Administrer Skype for Business Online-politikker med PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [Tildel pr. bruger Skype for Business Online-politikker med PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype for Business PowerShell-cmdlet-referencer](/powershell/module/skype/)
