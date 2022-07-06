---
title: Onboard Windows 10- og Windows 11-enheder ved hjælp af et lokalt script
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
description: Brug et lokalt script til at installere konfigurationspakken på enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: 840573794b447162f917fed162bb1f869585286e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634417"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Onboard Windows 10- og Windows 11-enheder ved hjælp af et lokalt script

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

Du kan også manuelt onboarde individuelle enheder til Microsoft 365. Det kan være en god idé at gøre dette først, når du tester tjenesten, før du forpligter dig til at onboarde alle enheder i dit netværk.

> [!IMPORTANT]
> Dette script er optimeret til brug på op til 10 enheder.
>
> Hvis du vil udrulle i stor skala, skal du bruge [andre udrulningsindstillinger](device-onboarding-overview.md). Du kan f.eks. udrulle et onboardingscript på mere end 10 enheder i produktion med det script, der er tilgængeligt i [Onboard Windows 10 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md).

## <a name="onboard-devices"></a>Onboard enheder
 
1. Hent konfigurationspakken .zip-filen (*DeviceComplianceOnboardingPackage.zip*) fra [Microsoft Purview-compliance-portal](https://compliance.microsoft.com)

2. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> > **For onboarding af enhed i** navigationsruden.

3. Vælg **Lokalt script** i feltet **Installationsmetode**.

4. Klik på **Download pakke** , og gem filen .zip.
  
5. Udtræk indholdet af konfigurationspakken til en placering på den enhed, du vil onboarde (f.eks. Desktop). Du skal have en fil med navnet *DeviceOnboardingScript.cmd*.

6. Åbn en kommandolinjeprompt med administratorrettigheder på enheden, og kør scriptet:

7. Gå til **Start,** og skriv **cmd**.

8. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

    ![Menuen Start i vinduet, der peger på Kør som administrator.](../media/dlp-run-as-admin.png)

9. Skriv placeringen af scriptfilen. Hvis du har kopieret filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Tryk på **Enter** , eller klik på **OK**.

Du kan finde oplysninger om, hvordan du manuelt kan validere, at enheden er kompatibel og rapporterer sensordata korrekt, under [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Offboard-enheder, der bruger et lokalt script

Af sikkerhedsmæssige årsager udløber den pakke, der bruges til Offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.

2. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> > **Enhedens offboarding** i navigationsruden.

3. Vælg **Lokalt script** i feltet **Installationsmetode**.

4. Klik på **Download pakke** , og gem filen .zip.

5. Udpak indholdet af den .zip fil til en delt, skrivebeskyttet placering, som enhederne kan få adgang til. Du skal have en fil med navnet *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Åbn en kommandolinjeprompt med administratorrettigheder på enheden, og kør scriptet:

7. Gå til **Start,** og skriv **cmd**.

8. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

    ![Menuen Start i vinduet, der peger på Kør som administrator.](../media/dlp-run-as-admin.png)

9. Skriv placeringen af scriptfilen. Hvis du kopierede filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. Tryk på **Enter** , eller klik på **OK**.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Du kan følge de forskellige bekræftelsestrin i [Foretag fejlfinding af onboardingproblemer](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) for at bekræfte, at scriptet er fuldført, og at agenten kører.

Overvågning kan også udføres direkte på portalen eller ved hjælp af de forskellige udrulningsværktøjer.

### <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen

1. Gå til [Microsoft Purview-compliance-portal](https://compliance.microsoft.com).

2. Vælg **Indstillinger** > **Enheder til enheds onboarding** > **.**

1. Gå til Microsoft Purview-compliance-portal, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> > **Enheder til onboarding af** > **enheder**.

1. Kontrollér, at enheder vises.

## <a name="related-topics"></a>Relaterede emner
- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Forbindelse med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
