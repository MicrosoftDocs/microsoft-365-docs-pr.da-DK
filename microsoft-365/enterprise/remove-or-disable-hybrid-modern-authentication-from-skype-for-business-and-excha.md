---
title: Fjernelse eller deaktivering af hybrid moderne godkendelse fra Skype for Business og Exchange
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel forklares det, hvordan du fjerner eller deaktiverer hybrid moderne godkendelse fra Skype for Business og Exchange.
ms.openlocfilehash: 27768d5f2ee1a2d223d0979a80d3fff003ed65ec
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097332"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Fjernelse eller deaktivering af hybrid moderne godkendelse fra Skype for Business og Exchange

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du kun har aktiveret Hybrid Modern Authentication (HMA) for at finde ud af, at den er uegnet til dit aktuelle miljø, kan du deaktivere HMA. I denne artikel forklares det, hvordan.
  
## <a name="who-is-this-article-for"></a>Who er denne artikel til?

Hvis du har aktiveret moderne godkendelse i Skype for Business Online eller i det lokale miljø og/eller Exchange Online eller i det lokale miljø, og du har brug for at deaktivere HMA, er disse trin noget for dig.

> [!IMPORTANT]
> Se artiklen "[Skype for Business topologier, der understøttes med moderne godkendelse](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)", hvis du er i Skype for Business Online eller i det lokale miljø, har en blandet topologi HMA og skal se på understøttede topologier, før du begynder.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Sådan deaktiverer du hybrid moderne godkendelse (Exchange)

1. **Exchange i det lokale miljø**: Åbn Exchange Management Shell, og kør følgende kommandoer: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Forbind til at Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) med Remote PowerShell. Kør følgende kommando for at ændre  *flaget OAuth2ClientProfileEnabled*  til 'false':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Sådan deaktiverer du hybrid moderne godkendelse (Skype for Business)

1. **Skype for Business i det lokale miljø**: Kør følgende kommandoer i Skype for Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business Online**: [Forbind at Skype for Business Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) med Remote PowerShell. Kør følgende kommando for at deaktivere moderne godkendelse:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Opret et link tilbage til oversigten over moderne godkendelse](hybrid-modern-auth-overview.md) . 
