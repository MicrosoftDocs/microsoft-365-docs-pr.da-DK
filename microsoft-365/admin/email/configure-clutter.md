---
title: Konfigurer Clutter for din organisation
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
description: 'Få mere at vide om, hvordan du aktiverer eller deaktiverer clutter-funktionen for alle eller bestemte brugere i din organisation ved hjælp af Exchange PowerShell. '
ms.openlocfilehash: 64c11b2a8bbce3747727c458a4427f5c0e1b135b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437189"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>Konfigurer Microsoft 365 Clutter for din organisation

> [!TIP]
> [Fokuseret indbakke](../setup/configure-focused-inbox.md) erstatter Clutter. Få mere at vide: [Opdater fokuseret indbakke og vores planer for Clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
Som administrator skal du muligvis administrere funktionen Clutter i Microsoft 365. Hvis du vil slå clutter-funktionen til/fra for brugere i din organisation, skal du bruge Exchange PowerShell. (Enkeltpersoner kan slå den til/fra ved hjælp af disse instruktioner: [Slå Clutter fra/til i Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Se [Brug af PowerShell med Exchange Online](/powershell/exchange/exchange-online-powershell) og [Forbind til at Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få oplysninger om, hvordan du bruger Exchange PowerShell. Du skal have en konto, der mindst har rollen Exchange-tjenesteadministrator og mulighed for at oprette forbindelse til Exchange Online med PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Slå Clutter til ved hjælp af Exchange PowerShell

Du kan aktivere Clutter manuelt for en postkasse ved at køre [Set-Clutter-cmdlet'en](/powershell/module/exchange/set-clutter) . Du kan også få vist Clutter-indstillinger for postkasser i din organisation ved at køre cmdlet'en [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Slå Clutter til for en enkelt bruger med navnet Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Slå Clutter fra ved hjælp af Exchange PowerShell

Du kan deaktivere Clutter manuelt for en postkasse ved at køre [Set-Clutter-cmdlet'en](/powershell/module/exchange/set-clutter) . Du kan også få vist **Clutter-indstillinger** for postkasser i din organisation ved at køre cmdlet'en [Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Slå Clutter fra for en enkelt bruger med navnet Allie Bellew:
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Hvis du bruger PowerShell til at masseopfylde dine brugere, skal du køre [Set-Clutter](/powershell/module/exchange/set-clutter) mod hver brugers postkasse for at administrere Clutter. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Hvornår vises knappen Clutter til/fra for brugere i Outlook på internettet?
<a name="bkmk_onoff"> </a>

Som administrator kan du genaktivere Clutter ved hjælp af Exchange PowerShell. Når dette er gjort, slås Fokuseret indbakke fra, og Clutter er aktivt igen. 
  
 **Hvis du bruger Outlook på internettet med et Microsoft 365 Business Premium-abonnement:**
  
- Hvis brugeren i øjeblikket har Aktiveret Clutter: 
    
  - Indstillinger for Clutter vises
    
- Hvis brugeren i øjeblikket har aktiveret Fokuseret indbakke: 
    
  - Indstillinger for Clutter vises ikke
    
- Hvis hverken Clutter eller Fokuseret indbakke er aktiveret: 
    
  - Både Clutter og Fokuseret indbakke vises som indstillinger i brugerens Mail-Indstillinger
    
 **Hvis du bruger Outlook.com:**
  
- Hvis brugeren i øjeblikket har Aktiveret Clutter: 
    
  - Indstillinger for Clutter vises
    
- Hvis brugeren i øjeblikket har aktiveret Fokuseret indbakke: 
    
  - Indstillinger for Clutter vises ikke
    
- Hvis hverken Clutter eller Fokuseret indbakke er aktiveret: 
    
  - Både Clutter og Fokuseret indbakke vises som indstillinger i brugerens Mail-Indstillinger
    
- Hvis brugeren har aktiveret Fokuseret indbakke på et tidspunkt tidligere:
    
  - Indstillinger for Clutter vises aldrig
    
    Ellers 
    
  - Indstillinger for Clutter vises
    
## <a name="related-content"></a>Relateret indhold

[Brug Clutter til at sortere meddelelser med lav prioritet i Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (artikel)\
[Brug Clutter til at sortere meddelelser med lav prioritet i OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (artikel)\
[Slå Clutter fra i Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (artikel)
