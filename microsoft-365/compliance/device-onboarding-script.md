---
title: Onboard Windows 10 og Windows 11 enheder ved hjælp af et lokalt script
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
ms.openlocfilehash: 14412e782cffd597786a4d2c322fe2b8fc20e5ca
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/12/2021
ms.locfileid: "63596951"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Onboard Windows 10 og Windows 11 enheder ved hjælp af et lokalt script

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Du kan også manuelt onboarde individuelle enheder for at Microsoft 365. Det kan være en god ide at gøre dette først, når du tester tjenesten, før du forpligter dig til at onboarde alle enheder i dit netværk.

> [!IMPORTANT]
> Dette script er blevet optimeret til brug på op til 10 enheder.
>
> Brug andre installationsindstillinger for at [udrulle i stor skala](device-onboarding-overview.md). Du kan f.eks. implementere et onboardingscript på mere end 10 enheder i produktion med det script, der er tilgængeligt i [Onboard Windows 10-enheder, der bruger Gruppepolitik](device-onboarding-gp.md).

## <a name="onboard-devices"></a>Onboard-enheder
 
1. Hent konfigurationspakken .zip (*DeviceComplianceOnboardingPackage.zip*) pakke fra [Microsoft Compliance Center](https://compliance.microsoft.com)

2. I navigationsruden skal du <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**vælge Indstillinger**</a> >  **Enheds-onboarding**.

3. I feltet **Installationsmetode** skal du vælge **Lokalt script**.

4. Klik **på Download** pakke, og gem .zip fil.
  
5. Udtræk indholdet af konfigurationspakken til en placering på den enhed, du vil onboarde (f.eks. Skrivebordet). Du skal have en fil med *navnet DeviceOnboardingScript.cmd*.

6. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:

7. Gå til **Start,** og skriv **cmd**.

8. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

    ![Vinduesruden menuen Start pege på Kør som administrator.](../media/dlp-run-as-admin.png)

9. Skriv placeringen af scriptfilen. Hvis du har kopieret filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. Tryk på **Enter,** eller klik på **OK**.

Du kan finde oplysninger om, hvordan du manuelt kan validere, om enheden er kompatibel og korrekt rapporterer sensordata, under Fejlfinding [af onboardingproblemer med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Offboard-enheder, der bruger et lokalt script

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.

2. I navigationsruden skal du <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**vælge Indstillinger**</a> >  **Offboarding**.

3. I feltet **Installationsmetode** skal du vælge **Lokalt script**.

4. Klik **på Download** pakke, og gem .zip fil.

5. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enhederne. Du skal have en fil med *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:

7. Gå til **Start,** og skriv **cmd**.

8. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

    ![Vinduesruden menuen Start pege på Kør som administrator.](../media/dlp-run-as-admin.png)

9. Skriv placeringen af scriptfilen. Hvis du har kopieret filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-DD.cmd*

10. Tryk på **Enter,** eller klik på **OK**.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Du kan følge de forskellige bekræftelsestrin i [Fejlfinding af onboardingproblemer]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) for at bekræfte, at scriptet blev fuldført, og at agenten kører.

Overvågning kan også udføres direkte på portalen eller ved hjælp af de forskellige installationsværktøjer.

### <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen

1. Gå til [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com).

2. Vælg **Indstillinger** >  **Device onboardingDevices** > .

1. Gå til Microsoft 365 Overholdelsescenter, og <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**vælg Indstillinger**</a> >  **Device onboardingDevices** > .

1. Kontrollér, at enheder vises.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)