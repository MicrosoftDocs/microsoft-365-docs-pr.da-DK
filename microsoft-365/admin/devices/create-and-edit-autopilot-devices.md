---
title: Opret og rediger AutoPilot-enheder
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Få mere at vide om, hvordan du overfører enheder med AutoPilot Microsoft 365 Business Premium. Du kan tildele en profil til en enhed eller en gruppe af enheder.
ms.openlocfilehash: 784db256bb5dae16739722566b6f7a9c8511a678
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598469"
---
# <a name="create-and-edit-autopilot-devices"></a>Opret og rediger AutoPilot-enheder

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="upload-a-list-of-devices"></a>Upload en liste over enheder

Du kan bruge den [trinvise vejledning til at](add-autopilot-devices-and-profile.md) overføre enheder, men du kan også overføre enheder under **fanen** Enheder. 
  
Enheder skal opfylde følgende krav:
  
- Windows 10, version 1703 eller nyere
    
- Nye enheder, der ikke har fået Windows fra kassen

1. I menuen Microsoft 365 Administration du vælge **Devices** \> **AutoPilot**.
  
2. På siden **AutoPilot** skal du vælge **fanen Enheder** Tilføj \> **enheder**.
    
    ![På fanen Enheder skal du vælge Tilføj enheder.](../../media/6ba81e22-c873-40ad-8a72-ce64d15ea6ba.png)
  
3. På panelet **Tilføj enheder skal** du gå til en [CSV-fil med liste over enheder,](../misc/device-list.md) som du har forberedt \> **Gem** \> **Luk**.
    
    Du kan få disse oplysninger fra din hardwareleverandør, eller du kan bruge scriptet [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) til at generere en CSV-fil. 
    
## <a name="assign-a-profile-to-a-device-or-a-group-of-devices"></a>Tildel en profil til en enhed eller en gruppe af enheder

1. På siden **Gør Windows** skal du vælge **fanen Enheder** og markere afkrydsningsfeltet ud for en eller flere enheder. 
    
2. Vælg **en** profil på rullelisten Tildelt profil **i** panelet Enhed. 
    
    Hvis du endnu ikke har nogen profiler, kan du se vejledningen [Opret og rediger AutoPilot-profiler](create-and-edit-autopilot-profiles.md) . 

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)