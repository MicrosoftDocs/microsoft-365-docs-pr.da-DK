---
title: Grænser i eDiscovery-kernecase
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
description: I denne artikel beskrives grænserne i eDiscovery-kernetilfælde i Microsoft 365.
ms.openlocfilehash: 67f15bb39ed75f40a8ef42747c0d4e2dfcb1297d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949603"
---
# <a name="limits-in-ediscovery-standard"></a>Grænser i eDiscovery (Standard)

I følgende tabel vises grænserne for eDiscovery-kernesager og ventepositioner, der er knyttet til en eDiscovery-kernesag. Du kan finde flere oplysninger om Microsoft Purview eDiscovery (Standard) under [Oversigt over eDiscovery (Standard).](./get-started-core-ediscovery.md)
    
  | Beskrivelse af grænse | Grænse |
  |:-----|:-----|
  |Maksimalt antal sager for en organisation.  <br/> |Ingen grænse  <br/> |
  |Det maksimale antal sagsakter for en organisation.  <br/> |10,000  <br/> |
  |Det maksimale antal postkasser i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer Grupper.  <br/> |1,000  <br/> |
  |Det maksimale antal websteder i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint websteder og de websteder, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer grupper.  <br/> |100  <br/> |
  |Det maksimale antal sager, der vises på eDiscovery-kernestartsiden, og det maksimale antal elementer, der vises på fanerne Ventepositioner, Søgninger og Eksportér i en sag. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> Hvis du vil have vist en liste over mere end 1.000 sager, ventepositioner, søgninger eller eksporter, kan du bruge de tilsvarende PowerShell-cmdlet'er til Office 365 Security & Compliance:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Du kan finde flere oplysninger om grænser, der er relateret til søgninger og eksporter, der er knyttet til en eDiscovery-sag (Standard [), under Grænser for indholdssøgning og eDiscovery (Standard)](limits-for-content-search.md).