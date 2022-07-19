---
title: Konfigurer Windows-enheder til Microsoft 365 Business Premium brugere
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Konfigurer Windows-enheder, der kører Windows 10 Pro for Microsoft 365 Business Premium brugere, og aktivér central administration og sikkerhedskontroller.
ms.openlocfilehash: b9c8a5eb724a74959983e86dcdcb8f2f8f96b540
ms.sourcegitcommit: e6443eb3a4c826792806873428c0c17b59f4fde5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/05/2022
ms.locfileid: "66858670"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Konfigurer Windows-enheder til Microsoft 365 Business Premium brugere

## <a name="before-you-begin"></a>Før du begynder

Før du kan konfigurere Windows-enheder til Microsoft 365 Business Premium brugere, skal du kontrollere, at alle Windows-enheder kører Windows 10 Pro, version 1703 (Creators Update) eller Windows 11 Pro. 

Windows 10 Pro (eller Windows 11 Pro) er en forudsætning for udrulning af Windows 10 Business, som er et sæt cloudtjenester og funktioner til enhedshåndtering, der supplerer Windows 10 Pro og Windows 11 Pro , og aktivér central administration og sikkerhedskontroller af Microsoft 365 Business Premium.

[Få mere at vide om krav til Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro og Windows 11 Pro

Hvis du har Windows-enheder, der kører tidligere versioner af Windows, f.eks. Windows 7 Pro, Windows 8 Pro eller Windows 8.1 Pro, giver dit Microsoft 365 Business Premium-abonnement dig ret til at opgradere disse enheder til Windows 10 Pro eller Windows 11 Pro.
  
Du kan få flere oplysninger om, hvordan du opgraderer Windows-enheder, i følgende artikler:

- [Opgrader Windows Home til Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Opgrader til Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Når du har opgraderet, skal du se [Kontrollér, at enheden har forbindelse til Azure AD](#verify-the-device-is-connected-to-azure-ad) for at bekræfte, at du har opgraderingen, eller for at sikre, at opgraderingen virkede.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Deltag i Windows-enheder i din organisations Azure AD

Når alle virksomhedens Windows-enheder kører Windows 10 Pro eller Windows 11 Pro, kan du slutte disse enheder til organisationens Azure Active Directory (Azure AD). 

1. På en Windows-enhed skal du vælge Windows-logoet og derefter ikonet Indstillinger.
  
2. I **Indstillinger** skal du gå til **Konti** > **Få adgang til arbejde eller skole** \> **Opret forbindelse**.
  
3. Skriv din mailadresse, og vælg derefter **Næste**.

4. Følg prompterne for at fuldføre processen.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Kontrollér, at enheden har forbindelse til Azure AD

Hvis du vil bekræfte din synkroniseringsstatus, skal du på siden **Få adgang til arbejde eller skole** i **Indstillinger** vælge området **Tilsluttet til** __ \<organization name\> for at få vist knapperne **Oplysninger** og **Afbryd forbindelse**. Vælg **Oplysninger** for at få synkroniseringsstatus. 
  
På siden **Synkroniseringsstatus** skal du vælge **Synkroniser** for at få de nyeste politikker for administration af mobilenheder til pc'en.  
  
## <a name="next-steps"></a>Næste trin

Hvis du vil konfigurere dine mobilenheder, skal du se [Konfigurer mobilenheder til Microsoft 365 Business Premium brugere](set-up-mobile-devices.md), 

Hvis du vil øge beskyttelsen, skal du se [Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../security-and-compliance/secure-your-business-data.md).
  

