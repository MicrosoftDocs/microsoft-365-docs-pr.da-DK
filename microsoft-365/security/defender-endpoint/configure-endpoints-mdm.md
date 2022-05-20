---
title: Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder
description: Brug Mobil-Enhedshåndtering værktøjer til at installere konfigurationspakken på enheder, så de er onboardet til Defender for Endpoint-tjenesten.
keywords: onboard devices using mdm, device management, onboard Microsoft Defender for Endpoint devices, mdm
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
ms.openlocfilehash: 3e81470cb02742eb94e62118f77f1ae0e8c62f90
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599658"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Du kan bruge MDM-løsninger (Mobile Device Management) til at konfigurere Windows 10 enheder. Defender for Endpoint understøtter MDMs ved at levere OMA-URIs til at oprette politikker til administration af enheder.


Du kan finde flere oplysninger om brug af Defender for Endpoint CSP i DDF-filen [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) og [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Før du begynder

Hvis du bruger Microsoft Intune, skal du have enheden MDM-tilmeldt. Ellers anvendes indstillingerne ikke korrekt.

Du kan få flere oplysninger om aktivering af MDM med Microsoft Intune under [Tilmelding af enhed (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Onboarde enheder ved hjælp af Microsoft Intune

Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier til installation af Defender for Endpoint.

Følg vejledningen fra [Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).


Du kan finde flere oplysninger om brug af Defender for Endpoint CSP i DDF-filen [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) og [WindowsAdvancedThreatProtection](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - Politikken **Tilstandsstatus for onboardede enheder bruger skrivebeskyttede** egenskaber og kan ikke afhjælpes.
> - Konfiguration af frekvensen for rapportering af diagnosticeringsdata er kun tilgængelig for enheder på Windows 10, version 1703.


Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier i udrulningen af Microsoft Defender for Endpoint.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding
Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at en enhed er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Offboard og overvåg enheder ved hjælp af værktøjer til Enhedshåndtering til mobilenheder

Af sikkerhedsmæssige årsager udløber den pakke, der bruges til Offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal:</a>

   1. I navigationsruden skal du vælge **Indstillinger** \> **Slutpunkter** \> **Administration af** \> enhed **offboarding**.

   1. Vælg Windows 10 eller Windows 11 som operativsystem.

   1. Vælg **Mobil Enhedshåndtering/Microsoft Intune** i feltet **Installationsmetode**.

   1. Klik på **Download pakke**, og gem filen .zip.

2. Udpak indholdet af .zip-filen på en delt, skrivebeskyttet placering, som netværksadministratorerne kan få adgang til, og som skal installere pakken. Du skal have en fil med navnet *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding*.

3. Brug Microsoft Intune brugerdefinerede konfigurationspolitik til at installere følgende understøttede OMA-URI-indstillinger.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Datotype: Streng
   - Værdi: [Kopiér og indsæt værdien fra indholdet af filen WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding]

Du kan få flere oplysninger om Microsoft Intune politikindstillinger [under Windows 10 politikindstillinger i Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> Politikken **Tilstandsstatus for offboardede enheder bruger skrivebeskyttede** egenskaber og kan ikke afhjælpes.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md)
- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
