---
title: Valider indstillinger for appbeskyttelse for Windows 10 pc'er
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Få mere at vide om, hvordan du Microsoft 365 indstillingerne for beskyttelse af apps til virksomheder træder i kraft på dine Windows 10-enheder.
ms.openlocfilehash: 47c220b36050376d1eddf7d83435f175e00f88cb
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64633277"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Valider indstillinger for enhedsbeskyttelse for Windows 10 pc'er

> [!NOTE]
> Microsoft Defender til virksomheder udrulles til Microsoft 365 Business Premium kunder fra d. 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Kontrollér, Windows 10 enhedspolitikker er angivet

Når du [har konfigureret politikker for](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md) enheder, kan det tage op til et par timer, før politikken træder i kraft på brugernes enheder. Du kan bekræfte, at politikkerne er blevet gennemført, ved at Windows Indstillinger forskellige skærme på brugernes enheder. Da brugerne ikke kan ændre indstillingerne for Windows Update og Microsoft Defender Antivirus på deres Windows 10-enheder, vil mange indstillinger være nedtonet.
  
1. Gå til **Indstillinger Indstillinger** \> **for &amp; opdatering** \> **Windows Update** \> **Indstillinger for genstart**, og bekræft, at alle indstillinger er nedtonet. 
    
    ![Alle indstillinger for genstart er nedtonet.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed ved** \> **Windows Update Avancerede** \> **indstillinger,** og bekræft, at alle indstillinger er nedtonet. 
    
    ![Windows avancerede opdateringsindstillinger er alle nedtonet.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Gå til **Indstillinger** \> **Opdateringssikkerhed &amp; Windows Update** \> **avancerede** \> **indstillinger Vælg** \> **, hvordan opdateringer leveres**.
    
    Bekræft, at du kan se meddelelsen (i rød), at nogle indstillinger er skjulte eller administreres af din organisation, og alle indstillingerne er nedtonet.
    
    ![Siden Vælg, hvordan opdateringer leveres angiver, at indstillingerne er skjulte eller administreres af din organisation.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Hvis du vil åbne Windows Defender Security Center, skal du gå til **Indstillinger** \> Opdateringssikkerhedsopdatering **&amp;** \> **Windows Defender** \> klikke **på Åbn Windows Defender Security Center** \> **Beskyttelse &amp;** \> mod **virustrusler med virustrusler &amp; indstillinger**. 
    
5. Kontrollér, at alle indstillinger er nedtonet. 
    
    ![Indstillingerne for virus- og trusselsbeskyttelse er nedtonet.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til virksomhedsdokumentation og -ressourcer](/admin)

[Angiv enhedskonfigurationer for Windows 10 pc'er](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [10 måder at sikre dine Microsoft 365 for business-planer](../../admin/security-and-compliance/secure-your-business-data.md)
