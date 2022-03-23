---
title: Konfigurere Clutter i din organisation
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
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'Lær at aktivere eller deaktivere Clutter-funktionen for alle eller bestemte brugere i organisationen ved hjælp Exchange PowerShell. '
ms.openlocfilehash: 5037e7cb6518ca90f3d12c183fcff3c838c29907
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589964"
---
# <a name="configure-clutter-for-your-organization"></a>Konfigurere Clutter i din organisation

> [!TIP]
> [Fokuseret indbakke](../setup/configure-focused-inbox.md) erstatter Clutter. Få mere at vide: [Opdatere om Fokuseret indbakke og vores planer for Clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Som administrator skal du muligvis administrere Clutter-funktionen i Microsoft 365. Hvis du vil slå Clutter-funktionen til/fra for brugere i organisationen, skal du bruge Exchange PowerShell. (Enkeltpersoner kan slå funktionen til/fra ved hjælp af denne vejledning: [Slå Clutter fra eller Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Se Brug [PowerShell med Exchange Online og](/powershell/exchange/exchange-online-powershell) [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få mere at vide om, Exchange PowerShell. Du skal have en konto, der har mindst Exchange-tjenesteadministratorrollen og mulighed for at oprette forbindelse til Exchange Online med PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Slå Clutter til ved hjælp Exchange PowerShell

Du kan aktivere Clutter manuelt for en postkasse ved at køre [cmdlet'en Set-Clutter](/powershell/module/exchange/set-clutter) . Du kan også få vist Clutter-indstillinger for postkasser i organisationen ved at køre [cmdlet'en Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Slå Clutter til for en enkelt bruger ved navn Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Slå Clutter fra ved hjælp Exchange PowerShell

Du kan deaktivere Clutter manuelt for en postkasse ved at køre [cmdlet'en Set-Clutter](/powershell/module/exchange/set-clutter) . Du kan også få vist **Clutter-indstillinger** for postkasser i organisationen ved at køre [cmdlet'en Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Slå Clutter fra for en enkelt bruger ved navn Allie Bellew:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Hvis du bruger PowerShell til at oprette flere brugere flere, skal du køre [Set-Clutter](/powershell/module/exchange/set-clutter) i forhold til hver brugers postkasse for at administrere Clutter. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Hvornår vises kontakten til at slå Clutter til/fra for brugere Outlook på internettet?
<a name="bkmk_onoff"> </a>

Som administrator kan du genaktivere Clutter ved hjælp Exchange PowerShell. Når dette er gjort, deaktiveres Fokuseret indbakke, og Clutter vil være aktiv igen. 
  
 **Hvis du bruger en Outlook på internettet med et Microsoft 365 Business Premium abonnement:**
  
- Hvis brugeren aktuelt har Clutter aktiveret: 
    
  - Indstillinger for Clutter vises
    
- Hvis brugeren aktuelt har Fokuseret indbakke aktiveret: 
    
  - Indstillinger for Clutter vises ikke
    
- Hvis hverken Clutter eller Fokuseret indbakke er aktiveret: 
    
  - Både Clutter og Fokuseret indbakke vises som indstillinger i brugerens Indstillinger
    
 **Hvis du bruger Outlook.com:**
  
- Hvis brugeren aktuelt har Clutter aktiveret: 
    
  - Indstillinger for Clutter vises
    
- Hvis brugeren aktuelt har Fokuseret indbakke aktiveret: 
    
  - Indstillinger for Clutter vises ikke
    
- Hvis hverken Clutter eller Fokuseret indbakke er aktiveret: 
    
  - Både Clutter og Fokuseret indbakke vises som indstillinger i brugerens Indstillinger
    
- Hvis brugeren tidligere har aktiveret Fokuseret indbakke:
    
  - Indstillinger for Clutter vises aldrig
    
    Ellers 
    
  - Indstillinger for Clutter vises
    
## <a name="related-content"></a>Relateret indhold

[Brug Clutter til at sortere meddelelser med lav prioritet Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (artikel)\
[Brug Clutter til at sortere meddelelser med lav prioritet i OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (artikel)\
[Slå Clutter fra Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (artikel)
