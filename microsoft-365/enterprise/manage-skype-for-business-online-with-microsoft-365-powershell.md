---
title: Administrer Skype for Business Online med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Brug PowerShell til Microsoft 365 til at administrere Skype for Business Online-politikker, politikker pr. bruger og mødeindstillinger.
ms.openlocfilehash: 1c3a3e06d3fa607765382176a8c291fab2c69636
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097662"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Administrer Skype for Business Online med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Skype for Business Online-administratorer er ansvarlige for at administrere politikker. Selvom du kan udføre nogle af disse opgaver i Microsoft 365 Administration, er andre nemmere at udføre i PowerShell.

## <a name="before-you-start"></a>Før du starter

> [!NOTE]
> Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige **PowerShell-version**, behøver du ikke at installere Skype for Business Online Connector.

> [!NOTE]
> Skype for Business onlineadministratorer kan administrere både **Teams** og **Skype for Business Online-apppolitikker** via PowerShell.

Installér [Teams PowerShell-modulet](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>Forbind ved hjælp af administratorlegitimationsoplysninger

1. Åbn et Windows PowerShell kommandopromptvindue, og kør følgende kommandoer:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. I dialogboksen **Windows PowerShell anmodning om legitimationsoplysninger** skal du skrive administratorkontoens navn og adgangskode og derefter vælge **OK**.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Forbind ved hjælp af en administratorkonto med multifaktorgodkendelse

1. Åbn et Windows PowerShell kommandopromptvindue, og kør følgende kommandoer:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Når du bliver bedt om det, skal du angive navnet på din Skype for Business Online-administratorkonto.

3. I dialogboksen **Log på din konto** skal du skrive din Skype for Business Online-administratoradgangskode og vælge **Log på**.

4. I dialogboksen **Log på din konto** skal du følge vejledningen for at tilføje godkendelsesoplysninger, f.eks. en bekræftelseskode, og derefter vælge **Bekræft**.

Du kan finde flere oplysninger under:

- [Administrer Skype for Business Online-politikker med PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [Tildel Skype for Business onlinepolitikker pr. bruger med PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype for Business PowerShell-cmdlet-referencer](/powershell/module/skype/)
