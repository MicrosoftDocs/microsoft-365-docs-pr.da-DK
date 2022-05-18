---
title: CSV-fil med enhedsliste
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 932e3676-2491-49f0-9177-d893d2f5276e
ROBOTS: NOINDEX
description: Få mere at vide om, hvordan du opretter en CSV-fil til AutoPilot i Microsoft 365 til virksomheder.
ms.openlocfilehash: af695448e31ea93d36b36a8831702acb84a92410
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469552"
---
# <a name="windows-autopilot-device-list-csv-file"></a>Windows CSV-fil med listen over autopilotenheder

## <a name="device-list-csv-file-format"></a>Enhedsliste .csv filformat

Hvis du vil administrere og installere enheder via Windows Autopilot, skal du bruge en .csv fil, der indeholder specifikke oplysninger om enhederne.
  
Kolonnerne i enhedslistefilen skal have følgende overskrifter i den angivne rækkefølge:
  
- Kolonne A: Enhedens serienummer

- Kolonne B: Lad argumentet være tomt

- Kolonne C: Hardwarehash

Du kan få disse oplysninger fra din hardwareleverandør, eller du kan bruge [PowerShell-scriptet Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) , der genererer en CSV-fil. 

Når du tilføjer enheder, skal du også føje dem til en profil. En profil bruges til at anvende AutoPilot-installationsprofiler på en enhed eller en gruppe enheder.
  
## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til forretningsdokumentation og -ressourcer](../../index.yml)
  
[Kom i gang med Microsoft 365 til virksomheder](../../admin/admin-overview/what-is-microsoft-365.md)