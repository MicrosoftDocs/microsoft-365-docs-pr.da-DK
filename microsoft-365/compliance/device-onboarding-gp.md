---
title: Onboard Windows 10 og Windows 11 enheder via Gruppepolitik
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Brug Gruppepolitik til at installere konfigurationspakken på Windows 10 og Windows 11 enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: fbba73fcf15ee9f71c4caacc57155a64e6cb9e9c
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/12/2021
ms.locfileid: "63601038"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Onboard Windows 10 enheder og Windows 11 ved hjælp af Gruppepolitik 

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- Gruppepolitik

> [!NOTE]
> For at Gruppepolitik (GP)-opdateringer til at installere pakken skal du være på Windows Server 2008 R2 eller nyere.

> For Windows Server 2019 skal du muligvis erstatte NT AUTHORITY\Well-Known-System-Account med NT AUTHORITY\SYSTEM i den XML-fil, som Gruppepolitik-indstillingen opretter.

## <a name="onboard-devices-using-group-policy"></a>Onboard-enheder med Gruppepolitik

1. Åbn [Overholdelsescenter](https://compliance.microsoft.com).

2. I navigationsruden skal du **vælge Indstillinger** >  **Enheder Onboarding**.

3. Vælg **Gruppepolitik i** feltet **Installationsmetode**.

4. Klik **på Download** pakke, og gem .zip fil.

5. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enheden. Du skal have en mappe med *navnet OptionalParamsPolicy* og filen *DeviceComplianceLocalOnboardingScript.cmd*.

6. Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

7. I Gruppepolitik **administrationseditor** skal du **gå til Computerkonfiguration** **og derefter** Indstillinger og **derefter indstillinger for Kontrolpanel**.

8. Højreklik på Planlagte **opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave (mindst Windows 7)**.

9. I vinduet **Opgave** , der åbnes, skal du gå **til fanen** Generelt. Klik **på Skift bruger** **eller gruppe under Sikkerhedsindstillinger, og** skriv SYSTEM, og klik derefter **på Kontrollér navne** og **OK**. NT AUTHORITY\SYSTEM vises som den brugerkonto, opgaven kører som.

10. Vælg **Kør, om brugeren er logget på eller** ej, **og markér afkrydsningsfeltet Kør med højeste** rettigheder.

11. Gå til fanen **Handlinger,** og klik på **Ny...** Sørg for **, at Start et** program er markeret i **feltet** Handling. Angiv filnavnet og placeringen af den delte *WindowsDefenderATPOnboardingScript.cmd-fil* .

12. Klik **på OK** , og luk alle åbne GPMC-vinduer.

## <a name="offboard-devices-using-group-policy"></a>Offboard-enheder, der bruger Gruppepolitik
Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken fra [Microsoft Compliance Center](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. I navigationsruden skal du **vælge Indstillinger** > **//Device onboardingOffboarding** > .

3. Vælg **Gruppepolitik i** feltet **Installationsmetode**.

4. Klik **på Download** pakke, og gem .zip fil.

5. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enheden. Du skal have en fil med *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

7. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration og** **derefter Indstillinger og** **derefter indstillinger for Kontrolpanel**.

8. Højreklik på Planlagte **opgaver**, peg på Ny **, og** klik derefter på **Øjeblikkelig opgave**.

9. I vinduet **Opgave** , der åbnes, skal du gå **til fanen** Generelt. Vælg den lokale SYSTEM-brugerkonto (BUILTIN\SYSTEM) under **Sikkerhedsindstillinger**.

10. Vælg **Kør, om brugeren er logget på** eller ej, **og markér afkrydsningsfeltet Kør med** højeste rettigheder.

11. Gå til fanen **Handlinger** , og klik på **Ny...**. Sørg for **, at Start et** program er markeret i **feltet** Handling. Angiv filnavnet og placeringen af den delte  *DeviceComplianceOffboardingScript_valid_until_YYYY-DD.cmd-filen* .

12. Klik **på OK** , og luk alle åbne GPMC-vinduer.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden.


## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration
Med Gruppepolitik er der ikke mulighed for at overvåge implementering af politikker på enhederne. Overvågning kan udføres direkte på portalen eller ved hjælp af de forskellige installationsværktøjer.

## <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.
2. Klik **på listen** Enheder.
3. Kontrollér, at enheder vises.

> [!NOTE]
> Det kan tage flere dage, før enhederne begynder at blive vist **på listen Enheder**. Dette omfatter den tid, det tager for politikkerne at blive distribueret til enheden, den tid, det tager for brugeren at logge på, og den tid, det tager slutpunktet at starte rapporteringen.


## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenheder](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)