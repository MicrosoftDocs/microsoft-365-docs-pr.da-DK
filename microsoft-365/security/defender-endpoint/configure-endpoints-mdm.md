---
title: Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder
description: Brug mobile Enhedshåndtering til at installere konfigurationspakken på enheder, så de er onboardet til Defender for Endpoint-tjenesten.
keywords: onboard-enheder ved hjælp af mdm, enhedshåndtering, onboard Microsoft Defender for Endpoint enheder, mdm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f3b13df5b9368609e888b92cbba49a58a0db3008
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634751"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Du kan bruge MDM-løsninger (mobile device management) til at konfigurere Windows 10 enheder. Defender til Slutpunkt understøtter MDMs ved at give OMA-URIs at oprette politikker til administration af enheder.


Du kan finde flere oplysninger om brug af Defender til Slutpunkt CSP i [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) og [WindowsAdvancedThprotecttProtection DDF-fil](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Før du begynder

Hvis du bruger en Microsoft Intune, skal du have enheden MDM tilmeldt. Ellers anvendes indstillingerne ikke korrekt.

Du kan finde flere oplysninger om aktivering af MDM Microsoft Intune i [Enhedsregistrering (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Onboard-enheder med Microsoft Intune

Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier i udrulning af Defender til Slutpunkt.

Følg vejledningen fra [Intune](/mem/intune/protect/advanced-threat-protection-configure).

Du kan finde flere oplysninger om brug af Defender til Slutpunkt CSP i [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) og [WindowsAdvancedThprotecttProtection DDF-fil](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - **Tilstandsstatus for onboardede enheder-politikken** anvender skrivebeskyttede egenskaber og kan ikke afhjælpes.
> - Konfiguration af hyppigheden for rapportering af diagnostiske data er kun tilgængelig for enheder Windows 10 version 1703.


Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier i forbindelse med installation Microsoft Defender for Endpoint.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding
Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Offboard og monitor enheder ved hjælp af Mobile Enhedshåndtering værktøjer

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>:

   1. I navigationsruden skal du **vælge Indstillinger** \> **Endpoints** \> **Device management** \> **Offboarding**.

   1. Vælg Windows 10 eller Windows 11 som operativsystem.

   1. I feltet **Installationsmetode** skal du vælge **Mobil Enhedshåndtering/Microsoft Intune**.

   1. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af filen .zip en delt, skrivebeskyttet placering, der kan åbnes af de netværksadministratorer, der skal installere pakken. Du skal have en fil *med WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Brug den Microsoft Intune konfigurationspolitik til at installere følgende understøttede OMA-URI-indstillinger.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Datotype: Streng
   - Værdi: [Kopiér og indsæt værdien fra indholdet WindowsDefenderATP_valid_until_YYYY-DD.offboarding-filen]

Du kan finde flere Microsoft Intune om politikindstillinger [under Windows 10 under Politikindstillinger Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> **Tilstandsstatus for politik for offboardede** enheder anvender skrivebeskyttede egenskaber og kan ikke afhjælpes.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md)
