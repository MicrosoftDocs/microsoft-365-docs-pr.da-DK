---
title: Begrænsninger i den grundlæggende eDiscovery-sag
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
description: I denne artikel beskrives begrænsningerne i den centrale eDiscovery-sag Microsoft 365.
ms.openlocfilehash: 28db179aea27bfff2520199d89b93c8260b7f089
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63599837"
---
# <a name="limits-in-core-ediscovery"></a>Begrænsninger i Core eDiscovery

I følgende tabel vises begrænsningerne for de centrale eDiscovery-sager og ventelister, der er knyttet til en grundlæggende eDiscovery-sag. Du kan finde flere oplysninger om Core eDiscovery under [Oversigt over Core eDiscovery](./get-started-core-ediscovery.md).
    
  | Beskrivelse af grænse | Grænse |
  |:-----|:-----|
  |Maksimale antal sager for en organisation.  <br/> |Ingen grænse  <br/> |
  |Maksimale antal ventende sager for en organisation.  <br/> |10,000  <br/> |
  |Maksimale antal postkasser i et enkelt sags hold. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper.  <br/> |1,000  <br/> |
  |Maksimale antal websteder i én enkelt venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint-websteder og de websteder, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper.  <br/> |100  <br/> |
  |Det maksimale antal sager, der vises på kernefanen eDiscovery, og det maksimale antal elementer, der vises på fanerne Vente hold, Søgninger og Eksportér i en sag. <sup>1</sup> |1,000|
  |||

   > [!NOTE]
   > <sup>1</sup> Hvis du vil have vist en liste over mere end 1.000 sager, ventepositioner, søgninger eller eksporter, kan du bruge de tilsvarende Office 365 Security & Compliance PowerShell-cmdlet'er:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Du kan finde flere oplysninger om begrænsninger i forbindelse med søgninger og eksporter, der er knyttet til en core eDiscovery-sag, under Begrænsninger for indholdssøgning og [Core eDiscovery](limits-for-content-search.md).