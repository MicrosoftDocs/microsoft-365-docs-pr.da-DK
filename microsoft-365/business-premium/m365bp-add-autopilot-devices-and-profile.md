---
title: Brug denne trinvise vejledning til at tilføje Autopilot-enheder og -profil
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.localizationpriority: high
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Få mere at vide om, hvordan du bruger Windows Autopilot til at konfigurere nye Windows 10 enheder til din virksomhed, så de er klar til medarbejderbrug.
ms.openlocfilehash: 4ab7925f751d987e9508732202908ad10c9d46b7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858847"
---
# <a name="use-this-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>Brug denne trinvise vejledning til at tilføje Autopilot-enheder og -profil

Du kan bruge Windows Autopilot til at konfigurere **nye** Windows 10 enheder til din virksomhed, så de er klar til brug, når du giver dem til dine medarbejdere.
  
## <a name="device-requirements"></a>Enhedskrav

Enheder skal opfylde disse krav:
  
- Windows 10, version 1703 eller nyere

- Nye enheder, der ikke har været gennem windows-out-of-box-oplevelsen

## <a name="use-the-setup-guide-to-add-devices-and-profiles"></a>Brug installationsvejledningen til at tilføje enheder og profiler

Hvis du endnu ikke har oprettet enhedsgrupper eller profiler, er den bedste måde at komme i gang på ved hjælp af den trinvise vejledning. Du kan også [tilføje Autopilot-enheder](m365bp-create-and-edit-Autopilot-devices.md) og [tildele profiler](../admin/devices/create-and-edit-Autopilot-profiles.md) til dem uden at bruge vejledningen.
  
1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Vælg **Enheder** \> **Autopilot** i navigationsruden til venstre.

    ![I Administration skal du vælge enheder og derefter Autopilot.](../media/Autopilot.png)
  
3. Klik eller tryk på **Start guide** på siden **Autopilot**.

    ![Klik på Start vejledning for at få en trinvis vejledning til Autopilot.](../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
4. På siden **Overfør .csv fil med liste over enheder** skal du gå til en placering, hvor du har den forberedte .CSV fil og derefter **åbne** \> **Næste**. Filen skal have tre overskrifter:

    - Kolonne A: Enhedens serienummer
    - Kolonne B: Windows-produkt-id
    - Kolonne C: Hardwarehash

Du kan få disse oplysninger fra din hardwareleverandør, eller du kan bruge [PowerShell-scriptet Get-WindowsAutopilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) til at generere en CSV-fil.

Du kan få flere oplysninger under [CSV-fil med enhedsliste](../admin/misc/device-list.md). Du kan også downloade en eksempelfil på siden **Upload .csv fil med en liste over enheder** .

> [!NOTE]
> Dette script bruger WMI til at hente de egenskaber, der er nødvendige for, at en kunde kan registrere en enhed med Windows Autopilot. Bemærk, at det er normalt, at den resulterende CSV-fil ikke indsamler en PKID-værdi (Windows Product ID), da dette ikke kræves for at registrere en enhed, og at PKID er NULL i output-CSV, er helt fint. Det er kun serienummeret og hardwarehash'et, der udfyldes.

5. På siden **Tildel en profil** kan du enten vælge en eksisterende profil eller oprette en ny. Hvis du endnu ikke har en, bliver du bedt om at oprette en.

    En profil er en samling indstillinger, der kan anvendes på en enkelt enhed eller på en gruppe enheder.

    Standardfunktionerne er påkrævet og angives automatisk. Standardfunktionerne er:

    - Spring Cortana, OneDrive og OEM-registrering over.

    - Opret logonoplevelse med dit firmamærke.

    - Forbind dine enheder til Azure Active Directory-konti, og tilmeld dem automatisk, så de administreres af Microsoft 365 Business Premium.

    Du kan få flere oplysninger under [Om indstillinger for autopilotprofil](m365bp-Autopilot-profile-settings.md).

6. De andre indstillinger er **Spring indstillinger for beskyttelse af personlige oplysninger over** og **Tillad ikke, at brugeren bliver den lokale administrator**. Disse er begge angivet til **Fra** som standard.

    Vælg **Næste**.

7. **Du er færdig** angiver, at den profil, du har oprettet (eller valgt), anvendes på den enhedsgruppe, du har oprettet, ved at uploade listen over enheder. Indstillingerne er i kraft, når enhedsbrugerne logger på næste. Vælg **Luk**.

## <a name="related-content"></a>Relateret indhold

- [Om Indstillinger for Autopilot-profil](../business-premium/m365bp-Autopilot-profile-settings.md) (artikel)\
- [Indstillinger for beskyttelse af dine enheder og appdata](../admin/devices/choose-device-security.md) (artikel)
- [Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)
