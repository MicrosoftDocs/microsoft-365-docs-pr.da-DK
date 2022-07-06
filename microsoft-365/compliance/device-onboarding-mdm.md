---
title: Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder
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
description: Brug Mobile Enhedshåndtering værktøjer til at installere konfigurationspakken på enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: d5c03c80c9a38d34ab27f888084604372874a64a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624195"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

Du kan bruge MDM-løsninger (Mobile Device Management) til at konfigurere enheder. Microsoft 365 Information Protection understøtter MDMs ved at levere OMA-URIs til at oprette politikker til administration af enheder.


## <a name="before-you-begin"></a>Før du begynder
Hvis du bruger Microsoft Intune, skal du have enheden MDM-tilmeldt. Ellers anvendes indstillingerne ikke korrekt. 

Du kan få flere oplysninger om aktivering af MDM med Microsoft Intune under [Tilmelding af enhed (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Onboarde enheder ved hjælp af Microsoft Intune

Følg vejledningen fra [Intune](/mem/intune/protect/advanced-threat-protection-configure).
 
> [!NOTE]
> - Politikken **Tilstandsstatus for onboardede enheder bruger skrivebeskyttede** egenskaber og kan ikke afhjælpes.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Offboard og overvåg enheder ved hjælp af værktøjer til Enhedshåndtering til mobilenheder

Af sikkerhedsmæssige årsager udløber den pakke, der bruges til Offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.

2. I navigationsruden skal du vælge **Indstillinger** > **For onboarding af** >  enhed **i Offboarding**.

3. Vælg **Mobil Enhedshåndtering/Microsoft Intune** i feltet **Installationsmetode**.

4. Klik på **Download pakke**, og gem filen .zip.

5. Udpak indholdet af .zip-filen på en delt, skrivebeskyttet placering, som netværksadministratorerne kan få adgang til, og som skal installere pakken. Du skal have en fil med navnet *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding*.

6. Brug Microsoft Intune brugerdefinerede konfigurationspolitik til at installere følgende understøttede OMA-URI-indstillinger.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Hvis Microsoft Defender for Endpoint allerede er konfigureret, kan du **slå onboarding af enheder** til, og trin 6 er ikke længere påkrævet.

> [!NOTE]
> Politikken **Tilstandsstatus for offboardede enheder bruger skrivebeskyttede** egenskaber og kan ikke afhjælpes.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

## <a name="related-topics"></a>Relaterede emner
- [Onboarde Windows 10 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboarde Windows 10 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboarde Windows 10 enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Fejlfinding af onboardingproblemer i Forbindelse med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
