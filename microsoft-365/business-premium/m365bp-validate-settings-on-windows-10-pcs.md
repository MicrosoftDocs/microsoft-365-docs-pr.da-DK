---
title: Valider indstillinger for appbeskyttelse for Windows 10 pc'er
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
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
description: Få mere at vide om, hvordan du kontrollerer, at indstillingerne for beskyttelse af Microsoft 365 Business Premium apps trådte i kraft på dine brugeres Windows 10 enheder.
ms.openlocfilehash: fe91d0b1588d860ee510f2542bc3f11a8cf2812a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858795"
---
# <a name="validate-device-protection-settings-for-windows-10-or-11-pcs"></a>Valider indstillinger for enhedsbeskyttelse for Windows 10 eller 11 pc'er

## <a name="verify-that-windows-10-or-11-device-policies-are-set"></a>Kontrollér, at Windows 10 eller 11 enhedspolitikker er angivet

Når du [har konfigureret enhedspolitikker](../business-premium/m365bp-protection-settings-for-windows-10-devices.md), kan det tage op til et par timer, før politikken træder i kraft på brugernes enheder. Du kan bekræfte, at politikkerne trådte i kraft, ved at se på forskellige skærme med Windows-indstillinger på brugernes enheder. Da brugerne ikke kan ændre indstillingerne for Windows Update og Microsoft Defender Antivirus på deres Windows 10 eller 11 enheder, nedtones mange indstillinger.
  
1. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Update** \> **Genstartsindstillinger**, og bekræft, at alle indstillinger er nedtonet.

    ![Alle indstillinger for Genstart er nedtonet.](../business-premium/media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Update** \> **Avancerede indstillinger**, og bekræft, at alle indstillinger er nedtonet.

    ![Indstillingerne for avancerede opdateringer i Windows er nedtonet.](../business-premium/media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Update** \> **Avancerede indstillinger** \> **Vælg, hvordan opdateringer leveres**.

    Bekræft, at du kan se meddelelsen (med rødt), at nogle indstillinger er skjult eller administreret af din organisation, og at alle indstillingerne er nedtonet.

    ![Vælg, hvordan opdateringerne skal leveres, angiver, at indstillinger skjules eller administreres af din organisation.](../business-premium/media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Hvis du vil åbne Windows Defender Security Center, skal du gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Defender** \> klikke på **Åbn Windows Defender Security Center** \> **Virustrådbeskyttelse &amp;** \> **Indstillinger for beskyttelse mod virustrussel&amp;**.

5. Kontrollér, at alle indstillinger er nedtonet.

    ![Indstillingerne for beskyttelse af virus og trusler er nedtonet.](../business-premium/media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Relateret indhold

[Dokumentation og ressourcer til Microsoft 365 til virksomheder](/admin)

[Angiv enhedskonfigurationer for Windows 10 pc'er](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Næste mål

[Gennemse og rediger beskyttelsespolitikker](m365bp-view-edit-create-mdb-policies.md)
