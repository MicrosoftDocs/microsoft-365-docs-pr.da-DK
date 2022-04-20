---
title: Grænser i eDiscovery-tilfælde (Standard)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives grænserne i eDiscovery -tilfælde (Standard) i Microsoft 365.
ms.openlocfilehash: 29d1ef4d017ebf26a0c5ed1cc03fcf4361266e94
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994100"
---
# <a name="limits-in-ediscovery-standard"></a>Grænser i eDiscovery (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I følgende tabel vises grænserne for eDiscovery-sager (Standard) og ventepositioner, der er knyttet til en eDiscovery-sag (Standard). Du kan finde flere oplysninger om Microsoft Purview eDiscovery (Standard) under [Oversigt over eDiscovery (Standard).](./get-started-core-ediscovery.md)
    
  | Beskrivelse af grænse | Grænse |
  |:-----|:-----|
  |Maksimalt antal sager for en organisation.  <br/> |Ingen grænse  <br/> |
  |Det maksimale antal sagsakter for en organisation.  <br/> |10,000  <br/> |
  |Det maksimale antal postkasser i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer Grupper.  <br/> |1,000  <br/> |
  |Det maksimale antal websteder i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint websteder og de websteder, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer grupper.  <br/> |100  <br/> |
  |Det maksimale antal sager, der vises på startsiden for eDiscovery (Standard), og det maksimale antal elementer, der vises på fanerne Ventepositioner, Søgninger og Eksportér i en sag. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> Hvis du vil have vist en liste over mere end 1.000 sager, ventepositioner, søgninger eller eksporter, kan du bruge de tilsvarende PowerShell-cmdlet'er til Office 365 Security & Compliance:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Du kan finde flere oplysninger om grænser, der er relateret til søgninger og eksporter, der er knyttet til en eDiscovery-sag (Standard [), under Grænser for indholdssøgning og eDiscovery (Standard)](limits-for-content-search.md).