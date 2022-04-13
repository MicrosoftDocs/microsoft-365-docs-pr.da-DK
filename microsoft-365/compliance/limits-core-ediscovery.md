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
ms.openlocfilehash: 2d920fbe5973d07b7da656d6247038ab785bbe5c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822644"
---
# <a name="limits-in-core-ediscovery"></a>Grænser i kerne-eDiscovery

I følgende tabel vises grænserne for eDiscovery-kernesager og ventepositioner, der er knyttet til en eDiscovery-kernesag. Du kan finde flere oplysninger om Core eDiscovery under [Oversigt over kerne-eDiscovery](./get-started-core-ediscovery.md).
    
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

Du kan finde flere oplysninger om grænser, der er relateret til søgninger og eksporter, der er knyttet til en grundlæggende eDiscovery-sag, under [Grænser for indholdssøgning og Kerne-eDiscovery](limits-for-content-search.md).