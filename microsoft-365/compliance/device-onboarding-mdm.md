---
title: Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Brug værktøjer til administration af mobilenheder til at installere konfigurationspakken på enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: 578a1e06bf5f83f700c5db69ddc32a480d68b729
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63606775"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Du kan bruge MDM-løsninger (mobile device management) til at konfigurere enheder. Microsoft 365 til informationsbeskyttelse understøtter MDMs ved OMA-URIs oprette politikker til administration af enheder.


## <a name="before-you-begin"></a>Før du begynder
Hvis du bruger en Microsoft Intune, skal du have enheden MDM tilmeldt. Ellers anvendes indstillingerne ikke korrekt. 

Du kan finde flere oplysninger om aktivering af MDM Microsoft Intune i [Enhedsregistrering (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Onboard-enheder med Microsoft Intune

Følg vejledningen fra [Intune](/intune/advanced-threat-protection).

> [!NOTE]
> - **Tilstandsstatus for onboardede enheder-politikken** anvender skrivebeskyttede egenskaber og kan ikke afhjælpes.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Offboard og overvåge enheder ved hjælp af værktøjer til administration af mobilenheder

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter.</a>

2. I navigationsruden skal du **vælge Indstillinger** >  **Device onboardingOffboarding** > .

3. I feltet **Installationsmetode** skal du vælge **Administration af mobilenheder/Microsoft Intune**.

4. Klik **på Download** pakke, og gem .zip fil.

5. Udtræk indholdet af filen .zip en delt, skrivebeskyttet placering, der kan åbnes af de netværksadministratorer, der skal installere pakken. Du skal have en fil *med DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Brug den Microsoft Intune konfigurationspolitik til at installere følgende understøttede OMA-URI-indstillinger.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Hvis Microsoft Defender til slutpunkt allerede er konfigureret, kan du Slå **onboarding af enheder** til, og trin 6 er ikke længere påkrævet.

> [!NOTE]
> **Tilstandsstatus for politik for offboardede** enheder anvender skrivebeskyttede egenskaber og kan ikke afhjælpes.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows 10-enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboard Windows 10-enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboarde Windows 10-enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
