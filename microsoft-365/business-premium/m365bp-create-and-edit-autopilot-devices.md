---
title: Opret og rediger Autopilot-enheder
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0f7b1d7c-4086-4331-8534-45d7886f9f34
description: Få mere at vide om, hvordan du uploader enheder ved hjælp af Autopilot i Microsoft 365 Business Premium. Du kan tildele en profil til en enhed eller en gruppe enheder.
ms.openlocfilehash: 994eab29d4b04e2de21d3e42a4abc174270f67f7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858787"
---
# <a name="create-and-edit-autopilot-devices"></a>Opret og rediger Autopilot-enheder

## <a name="upload-a-list-of-devices"></a>Upload en liste over enheder

Du kan bruge den [trinvise vejledning](m365bp-add-Autopilot-devices-and-profile.md) til at uploade enheder, men du kan også uploade enheder under fanen **Enheder** . 
  
Enheder skal opfylde disse krav:
  
- Windows 10, version 1703 eller nyere
    
- Nye enheder, der ikke har været gennem windows-out-of-box-oplevelsen

1. I Microsoft 365 Administration skal du vælge **Enheder** \> **Autopilot**.
  
2. På siden **Autopilot** skal du vælge fanen \> **Enheder** **Tilføj enheder**.
    
    ![Under fanen Enheder skal du vælge Tilføj enheder.](./../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. På panelet **Tilføj enheder** skal du gå til en [CSV-fil med en enhedsliste](../admin/misc/device-list.md)  , som du har forberedt \> **Gem** \> **luk**.
    
    Du kan få disse oplysninger fra din hardwareleverandør, eller du kan bruge [PowerShell-scriptet Get-WindowsAutopilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) til at generere en CSV-fil. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Tildel en profil til en enhed eller en gruppe enheder

1. På siden **Forbered Windows** skal du vælge fanen **Enheder** og markere afkrydsningsfeltet ud for en eller flere enheder. 
    
2. Vælg en profil på rullelisten **Tildelt profil** i panelet **Enhed**. 
    
    Hvis du endnu ikke har nogen profiler, skal du se [Opret og rediger Autopilot-profiler](../admin/devices/create-and-edit-Autopilot-profiles.md) for at få en vejledning. 

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)
