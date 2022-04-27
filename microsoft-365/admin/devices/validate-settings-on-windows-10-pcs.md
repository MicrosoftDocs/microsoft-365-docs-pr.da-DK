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
description: Få mere at vide om, hvordan du bekræfter, at beskyttelsesindstillinger for Microsoft 365 til virksomhedsapps trådte i kraft på dine brugeres Windows 10 enheder.
ms.openlocfilehash: c107741d87c63472310352b58872ec0b6ecc1d4d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090657"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Valider indstillinger for enhedsbeskyttelse for Windows 10 pc'er

> [!NOTE]
> Microsoft Defender til virksomheder udrulles til Microsoft 365 Business Premium kunder fra den 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Kontrollér, at Windows 10 enhedspolitikker er angivet

Når du [har konfigureret enhedspolitikker](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md), kan det tage op til et par timer, før politikken træder i kraft på brugernes enheder. Du kan bekræfte, at politikkerne trådte i kraft, ved at se på forskellige Windows Indstillinger skærmbilleder på brugernes enheder. Da brugerne ikke kan ændre indstillingerne for Windows Update og Microsoft Defender Antivirus på deres Windows 10 enheder, nedtones mange indstillinger.
  
1. Gå til **Indstillinger** \> **Opdater &amp; sikkerhedsindstillinger** \> **Windows Update** \> **Genstartsindstillinger**, og bekræft, at alle indstillinger er nedtonet.

    ![Alle indstillinger for Genstart er nedtonet.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Update** \> **Avancerede indstillinger**, og bekræft, at alle indstillinger er nedtonet.

    ![Windows Avancerede opdateringer er nedtonet.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Update** \> **Avancerede indstillinger** \> **Vælg, hvordan opdateringer leveres**.

    Bekræft, at du kan se meddelelsen (med rødt), at nogle indstillinger er skjult eller administreret af din organisation, og at alle indstillingerne er nedtonet.

    ![Vælg, hvordan opdateringerne skal leveres, angiver, at indstillinger skjules eller administreres af din organisation.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Hvis du vil åbne Windows Defender Security Center, skal du gå til **Indstillinger** \> **Opdater &amp; sikkerhed** \> **Windows Defender** \> klikke på **Åbn Windows Defender Security Center** \> **Virustrådbeskyttelse &amp; Beskyttelse mod** \> **virustrussel &amp; indstillinger**.

5. Kontrollér, at alle indstillinger er nedtonet.

    ![Indstillingerne for beskyttelse af virus og trusler er nedtonet.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til forretningsdokumentation og -ressourcer](/admin)

[Angiv enhedskonfigurationer for Windows 10 pc'erTop](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [10 måder at sikre Microsoft 365 til forretningsplaner](../../admin/security-and-compliance/secure-your-business-data.md) på
