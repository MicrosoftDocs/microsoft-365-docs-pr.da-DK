---
title: Brug lean popouts til at reducere hukommelse, der bruges, når du læser mails
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Denne artikel indeholder oplysninger om brug af lean popouts til at forbedre ydeevnen for overførsel af meddelelser Outlook på internettet.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaacacc0c1db418181690a5a4691bd251180d97c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591602"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Brug lean popouts til at reducere hukommelse, der bruges, når du læser mails

Denne artikel indeholder oplysninger om forbedring af ydeevnen ved download af meddelelser Outlook på internettet. Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md) projekt.
  
Som Office 365-programadministrator **,** **global** administrator eller brugeradministrator kan du konfigurere Outlook på internettet til at levere lean _popouts_, en mindre version af bestemte mails i Microsoft Edge eller Internet Explorer, der bruger mindre hukommelse. Når lean popouts er konfigureret til Outlook på internettet, indlæses komponenter, der gengives på serversiden, og optimerer ydeevnen.
  
> [!NOTE]
> Fra og med marts 2018 er lean popouts ikke tilgængelige for meddelelser, der angiver begrænsninger for brugsrettigheder, f.eks. IRM (Information Rights Management).
  
Disse funktioner fungerer fortsat i hovedvinduet, men er ikke tilgængelige i lean popouts:
  
- Outlook-tilføjelsesprogrammet
  
- Skype for Business tilstedeværelse
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Sådan konfigurerer du lean popouts for alle brugere i Office 365 organisation
  
1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Kør [cmdlet'en Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) med parameteren LeanPopoutEnabled på følgende måde:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Sådan aktiverer du lean popouts for alle brugere i organisationen:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Sådan deaktiverer du lean popouts for alle brugere i organisationen:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
