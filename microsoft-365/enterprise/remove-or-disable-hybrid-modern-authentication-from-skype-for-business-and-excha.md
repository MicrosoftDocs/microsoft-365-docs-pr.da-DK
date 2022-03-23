---
title: Fjerne eller deaktivere hybrid moderne godkendelse fra Skype for Business og Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: I denne artikel forklares det, hvordan du fjerner eller deaktiverer moderne hybridgodkendelse Skype for Business og Exchange.
ms.openlocfilehash: efc84ead5ea8219e77391f2a8ebe51e5fa23da8c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589720"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Fjerne eller deaktivere hybrid moderne godkendelse fra Skype for Business og Exchange

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du kun har aktiveret hybrid moderne godkendelse (HMA) for at finde, at det er upassende for dit aktuelle miljø, kan du deaktivere HMA. I denne artikel forklares det hvordan.
  
## <a name="who-is-this-article-for"></a>Who denne artikel til?

Hvis du har aktiveret moderne godkendelse i Skype for Business Online eller lokalt, og/eller Exchange Online eller lokalt, og du har fundet ud af, at du er nødt til at deaktivere HMA, er disse trin for dig.

> [!IMPORTANT]
> Se artiklen "[Skype for Business topologier](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), der understøttes med moderne godkendelse", hvis du er i Skype for Business Online eller Lokalt miljø, har en blandet topologi HMA og har brug for at se understøttede topologier, før du går i gang.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Sådan deaktiveres hybrid moderne godkendelse (Exchange)

1. **Exchange i det lokale miljø**: Åbn Exchange Management Shell, og kør følgende kommandoer: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Forbind til Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) med Remote PowerShell. Kør følgende kommando for at slå dit  *OAuth2ClientProfileEnabled-flag*  til 'falsk':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Sådan deaktiveres hybrid moderne godkendelse (Skype for Business)

1. **Skype for Business lokal: Kør** følgende kommandoer i Skype for Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business Online**: [Forbind Skype for Business Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) med Remote PowerShell. Kør følgende kommando for at deaktivere moderne godkendelse:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Opret et link tilbage til oversigten over moderne godkendelse](hybrid-modern-auth-overview.md) . 
