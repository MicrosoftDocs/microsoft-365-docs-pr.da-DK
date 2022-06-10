---
title: Brug lean popouts til at reducere den hukommelse, der bruges ved læsning af mails
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Denne artikel indeholder oplysninger om brug af lean popouts til at forbedre ydeevnen for overførsel af meddelelser i Outlook på internettet.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9636fd3beafd169358c4b50cafdc4ac0f9494994
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012676"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Brug lean popouts til at reducere den hukommelse, der bruges ved læsning af mails

Denne artikel indeholder oplysninger til forbedring af ydeevnen for overførsel af meddelelser i Outlook på internettet. Denne artikel er en del af [projektet Netværksplanlægning og justering af ydeevne for Office 365](./network-planning-and-performance.md).
  
Som Office 365 **programadministrator**, **global administrator** eller **brugeradministrator** kan du konfigurere Outlook på internettet til at levere _lean popouts_, en mindre, mindre hukommelseskrævende version af visse mails i Microsoft Edge eller Internet Explorer. Når lean popouts er konfigureret til Outlook på internettet, indlæses gengivne komponenter på serversiden, der optimerer ydeevnen.
  
> [!NOTE]
> Fra og med marts 2018 er lean-popouts ikke tilgængelige for meddelelser, der angiver begrænsninger for brugsrettigheder, f.eks. Information Rights Management (IRM).
  
Disse funktioner vil fortsat fungere i hovedvinduet, men er ikke tilgængelige i lean popouts:
  
- Outlook tilføjelsesprogrammer
  
- Skype for Business tilstedeværelse
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Sådan konfigurerer du lean popouts for alle brugere i din Office 365 organisation
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Kør [Set-OrganizationConfig-cmdlet'en](/powershell/module/exchange/set-organizationconfig) med parameteren LeanPopoutEnabled på følgende måde:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Hvis du f.eks. vil aktivere lean-popouts for alle brugere i din organisation:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Sådan deaktiverer du lean-popouts for alle brugere i din organisation:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
