---
title: CSV-fil med liste over enheder
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
description: Få mere at vide om, hvordan du laver en CSV-fil til AutoPilot Microsoft 365 til virksomheder.
ms.openlocfilehash: 62dbcddbdab1a08ab3b19c6616b814c421a57c04
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2021
ms.locfileid: "63589382"
---
# <a name="device-list-csv-file"></a>CSV-fil med liste over enheder

## <a name="device-list-csv-file-format"></a>Enhedsliste .csv-filformat

For at administrere og udrulle enheder Windows Autopilot, skal du bruge en .csv fil, der indeholder specifikke oplysninger om enhederne.
  
Kolonnerne i enhedslistefilen skal have følgende overskrifter i den angivne rækkefølge:
  
- Kolonne A: Enhedens serienummer

- Kolonne B: lad feltet være tomt

- Kolonne C: Hardwarehash

Du kan få disse oplysninger fra din hardwareleverandør, eller du kan bruge scriptet [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) , der genererer en CSV-fil. 

Når du tilføjer enheder, skal du også føje dem til en profil. En profil bruges til at anvende AutoPilot-udrulningsprofiler på en enhed eller en gruppe af enheder.
  
## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til virksomhedsdokumentation og -ressourcer](../../index.yml)
  
[Introduktion til Microsoft 365 til virksomheder](../../admin/admin-overview/what-is-microsoft-365.md)