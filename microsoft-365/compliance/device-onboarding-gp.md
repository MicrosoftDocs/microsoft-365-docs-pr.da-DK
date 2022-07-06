---
title: Onboard Windows 10- og Windows 11-enheder via gruppepolitik
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
ms.openlocfilehash: 6c8c70d1bfdf3de0bc3848069a22b8610d445e42
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623247"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Onboarde Windows 10 enheder og Windows 11 ved hjælp af Gruppepolitik 

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)
- Gruppepolitik

> [!NOTE]
> Hvis du vil bruge opdateringer af Gruppepolitik (GP) til at installere pakken, skal du være på Windows Server 2008 R2 eller nyere.

> I Windows Server 2019 skal du muligvis erstatte NT AUTHORITY\Well-Known-System-Account med NT AUTHORITY\SYSTEM i den XML-fil, som Gruppepolitik præference opretter.

## <a name="onboard-devices-using-group-policy"></a>Onboarde enheder ved hjælp af Gruppepolitik

1. Åbn [Overholdelsescenter](https://compliance.microsoft.com).

2. Vælg **Indstillinger for** > **enheds onboarding** i navigationsruden.

3. Vælg **Gruppepolitik** i feltet **Installationsmetode**.

4. Klik på **Download pakke** , og gem filen .zip.

5. Udpak indholdet af den .zip fil til en delt, skrivebeskyttet placering, som enheden kan få adgang til. Du skal have en mappe med navnet *OptionalParamsPolicy* og filen *DeviceComplianceLocalOnboardingScript.cmd*.

6. Åbn [GPMC (Gruppepolitik Management Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

7. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration**, derefter **Indstillinger** og derefter **Indstillinger for Kontrolpanel**.

8. Højreklik på **Planlagte opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave (mindst Windows 7).**

9. I vinduet **Opgave** , der åbnes, skal du gå til fanen **Generelt** . Under **Sikkerhedsindstillinger** skal du klikke på **Skift bruger eller gruppe** , skrive SYSTEM og derefter klikke på **Kontrollér navne** og derefter **PÅ OK**. NT AUTHORITY\SYSTEM vises som den brugerkonto, som opgaven kører som.

10. Vælg **Kør, om brugeren er logget på eller ej** , og markér afkrydsningsfeltet **Kør med de højeste rettigheder** .

11. Gå til fanen **Handlinger,** og klik på **Ny...** Kontrollér, at **Start et program** er markeret i feltet **Handling** . Angiv filnavnet og placeringen af den delte *WindowsDefenderATPOnboardingScript.cmd-fil* .

12. Klik på **OK** , og luk alle åbne GPMC-vinduer.

## <a name="offboard-devices-using-group-policy"></a>Offboard-enheder, der bruger Gruppepolitik
Af sikkerhedsmæssige årsager udløber den pakke, der bruges til offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

1. Hent offboarding-pakken fra [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. Vælg **Indstillinger** > **//Enheds onboarding****Offboarding** >  i navigationsruden.

3. Vælg **Gruppepolitik** i feltet **Installationsmetode**.

4. Klik på **Download pakke** , og gem filen .zip.

5. Udpak indholdet af den .zip fil til en delt, skrivebeskyttet placering, som enheden kan få adgang til. Du skal have en fil med navnet *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

6. Åbn [GPMC (Gruppepolitik Management Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

7. I **Gruppepolitik Management Editor** skal du gå til **Computerkonfiguration,** derefter **Indstillinger** og derefter **Indstillinger for Kontrolpanel**.

8. Højreklik på **Planlagte opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave**.

9. I vinduet **Opgave** , der åbnes, skal du gå til fanen **Generelt** . Vælg den lokale SYSTEM-brugerkonto (BUILTIN\SYSTEM) under **Sikkerhedsindstillinger**.

10. Vælg **Kør, om brugeren er logget på eller ej** , og markér afkrydsningsfeltet **Kør med de højeste rettigheder** .

11. Gå til fanen **Handlinger,** og klik på **Ny...**. Kontrollér, at **Start et program** er markeret i feltet **Handling** . Angiv filnavnet og placeringen af den delte  *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd-fil* .

12. Klik på **OK** , og luk alle åbne GPMC-vinduer.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden.


## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration
Med Gruppepolitik er der ikke mulighed for at overvåge udrulningen af politikker på enhederne. Overvågning kan udføres direkte på portalen eller ved hjælp af de forskellige udrulningsværktøjer.

## <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.
2. Klik på Listen **Enheder** .
3. Kontrollér, at enheder vises.

> [!NOTE]
> Det kan tage flere dage, før enhederne begynder at blive vist på **listen Enheder**. Dette omfatter den tid, det tager for politikkerne at blive distribueret til enheden, den tid, det tager, før brugeren logger på, og den tid, det tager for slutpunktet at begynde at rapportere.


## <a name="related-topics"></a>Relaterede emner
- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enheder](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Forbindelse med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
