---
title: Skift til Microsoft Defender til slutpunkt – konfiguration
description: Skift til Defender for Endpoint. Gennemse installationsprocessen, som omfatter installation af Microsoft Defender Antivirus.
keywords: overførsel, Microsoft Defender til slutpunkt, antivirus, passiv tilstand, konfigurationsproces
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom: migrationguides
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 99d0de5562b31cdc0f5d6c17d1e9f855ef5a55ea
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63598561"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Skift til Microsoft Defender til slutpunkt – Fase 2: Konfiguration

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Fase 1: Forbered.](images/phase-diagrams/prepare.png)](switch-to-mde-phase-1.md)<br/>[Fase 1: Forbered](switch-to-mde-phase-1.md)|![Fase 2: Konfigurer.](images/phase-diagrams/setup.png)<br/>Fase 2: Konfigurer|[![Fase 3: Onboard3.](images/phase-diagrams/onboard.png)](switch-to-mde-phase-3.md)<br/>[Fase 3: Onboard](switch-to-mde-phase-3.md)|
|---|---|---|
||*Du er her!*||

**Velkommen til fasen Konfiguration af [skift til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Denne fase omfatter følgende trin:

1. [Geninstaller/Microsoft Defender Antivirus på dine slutpunkter](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Konfigurer Defender til Slutpunkt](#configure-defender-for-endpoint).
3. [Føj Defender til Slutpunkt til udeladelseslisten for din eksisterende løsning](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Føj din eksisterende løsning til udeladelseslisten for Microsoft Defender Antivirus](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Konfigurer dine enhedsgrupper, enhedssamlinger og organisationsenheder](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Geninstaller/Microsoft Defender Antivirus på dine slutpunkter

På visse versioner af Windows blev Microsoft Defender Antivirus fjernet eller deaktiveret, da din ikke-Microsoft-antivirus-/antimalwareløsning blev installeret. Når slutpunkter, der Windows, er onboardet til Defender til slutpunkt, kan Microsoft Defender Antivirus køre i passiv tilstand sammen med en ikke-Microsoft-antivirusløsning. Du kan få mere at vide [under Antivirusbeskyttelse med Defender til slutpunkt](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Når du skifter til Defender for Endpoint, skal du muligvis foretage visse trin for at geninstallere eller aktivere Microsoft Defender Antivirus. I følgende tabel beskrives det, hvad du skal gøre på Windows klienter og servere.
<br/> <br/>

|Slutpunktstype|Hvad kan du gøre?|
|---|---|
|Windows klienter (f.eks. slutpunkter, der Windows 10 og Windows 11)|Generelt behøver du ikke at udføre en handling for Windows kunder (medmindre Microsoft Defender Antivirus er blevet fjernet). Her er årsagen: <br/><br/> Microsoft Defender Antivirus stadig være installeret, men er højst sandsynligt deaktiveret på dette tidspunkt i overførselsprocessen. <br/><br/> Når en ikke-Microsoft antivirus-/antimalwareløsning er installeret, og klienterne endnu ikke er onboardet til Defender til Slutpunkt, deaktiveres Microsoft Defender Antivirus automatisk. <br/><br/> Senere, når klientslutpunkterne er onboardet til Defender for Endpoint, går Microsoft Defender Antivirus i passiv tilstand, hvis disse slutpunkter kører en ikke-Microsoft-antivirusløsning. <br/><br/> Hvis antivirusløsningen, der ikke er Microsoft, fjernes, Microsoft Defender Antivirus automatisk i aktiv tilstand.|
|Windows-servere|På Windows Server skal du geninstallere Microsoft Defender Antivirus og indstille den til passiv tilstand manuelt. På Windows servere, når der er installeret et antivirusprogram/antimalware, Microsoft Defender Antivirus køre sammen med den antivirusløsning, der ikke er Microsoft. I disse tilfælde er Microsoft Defender Antivirus deaktiveret eller fjernet manuelt. <br/><br/> For at geninstallere eller Microsoft Defender Antivirus på Windows Server skal du udføre følgende opgaver: <br/>- [Set DisableAntiSpyware to false on Windows Server](#set-disableantispyware-to-false-on-windows-server) (only if necessary)<br/>- [Geninstaller Microsoft Defender Antivirus på Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Geninstaller Microsoft Defender Antivirus på Windows Server, version 1803 eller nyere](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Indstil Microsoft Defender Antivirus til passiv tilstand på Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Hvis du får problemer med at geninstallere eller genaktivere Microsoft Defender Antivirus på Windows Server, skal du se Fejlfinding: Microsoft Defender Antivirus bliver fjernet [på Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Du kan få mere at Microsoft Defender Antivirus om tilstande med ikke-Microsoft-antivirusbeskyttelse [under Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

### <a name="set-disableantispyware-to-false-on-windows-server"></a>Set DisableAntiSpyware to false on Windows Server

[Registreringsdatabasenøglen DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) blev tidligere brugt til at deaktivere Microsoft Defender Antivirus og installere et andet antivirusprodukt, f.eks. McAfee,Afee,Afee eller andre. **Generelt bør du ikke have denne registreringsdatabasenøgle** på dine Windows-enheder og slutpunkter.  `DisableAntiSpyware` Men hvis du har konfigureret, kan du her se, hvordan du indstiller dens værdi til falsk:

1. På din Windows Server-enhed skal du åbne Registreringseditor.

2. Gå til `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

3. I denne mappe skal du se efter en DWORD-post med **navnet DisableAntiSpyware**.
   - Hvis du ikke kan se denne post, er du klar.
   - Hvis du kan se **DisableAntiSpyware**, skal du gå videre til trin 4.

4. Højreklik på DisableAntiSpyware DWORD, og vælg derefter **Rediger**.

5. Angiv værdien til `0`. (Denne handling indstiller registreringsdatabasenøglens værdi *til falsk*).

> [!TIP]
> Du kan få mere at vide om denne registreringsdatabasenøgle [under DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>Genaktiver Microsoft Defender Antivirus på Windows Server 2016

Du kan bruge værktøjet [malwarebeskyttelse Command-Line at](command-line-arguments-microsoft-defender-antivirus.md) genaktivere Microsoft Defender Antivirus på Windows Server 2016.

1. Åbn Kommandoprompt som lokal administrator på serveren.

2. Kør følgende kommando: `MpCmdRun.exe -wdenable`

3. Genstart enheden.


### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Genaktiver Microsoft Defender Antivirus på Windows Server, version 1803 eller nyere

> [!IMPORTANT]
> Følgende procedure gælder kun for slutpunkter eller enheder, der kører følgende versioner af Windows:
> - Windows Server 2019
> - Windows Server 2022
> - Windows Server, version 1803 (kun i kernetilstand)

1. Som lokal administrator på serveren skal du åbne Windows PowerShell.

2. Kør følgende PowerShell-cmdlet'er:

   ```powershell
   # For Windows Server 2016
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Gui
   # For Windows Server 2019 and Windows Server 2022
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

   Når du bruger DISM-kommandoen i en opgavesekvens, der kører PowerShell, er følgende sti cmd.exe påkrævet.
   Eksempel:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Genstart enheden.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Indstil Microsoft Defender Antivirus til passiv tilstand på Windows Server

> [!TIP]
> Du kan nu køre Microsoft Defender Antivirus i passiv tilstand Windows Server 2012 R2 og 2016. Du kan finde flere oplysninger [under Indstillinger for installation af Microsoft Defender til slutpunkt](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Åbn registreringseditoren, og gå derefter til

   ```text
   Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
   ```

2. Rediger (eller opret) en DWORD-post **med navnet ForceDefenderPassiveMode**, og angiv følgende indstillinger:

   - Angiv DWORD'ens værdi til **1**.
   - Under **Base skal** du vælge **Hexadecimal**.

> [!NOTE]
> Efter onboarding til Defender til slutpunkt skal du muligvis indstille Microsoft Defender Antivirus til passiv tilstand på Windows Server. Hvis du vil validere, at passiv tilstand blev indstillet som forventet, skal du søge efter hændelse *5007* i **Microsoft-Windows-Windows Defender-driftsloggen** (placeret ved) og bekræfte, at `C:\Windows\System32\winevt\Logs`enten **ForceDefenderPassiveMode**- eller PassiveMode-registreringsdatabasenøglerne er indstillet af **til 0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Bruger du Windows Server 2012 R2 eller Windows Server 2016?

Du kan nu køre Microsoft Defender Antivirus i passiv tilstand Windows Server 2012 R2 og 2016 ved hjælp af ovenstående metode. Du kan finde flere oplysninger [under Indstillinger for installation af Microsoft Defender til slutpunkt](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Konfigurer Defender til Slutpunkt

Dette trin i overførselsprocessen omfatter konfiguration Microsoft Defender Antivirus for dine slutpunkter. Vi anbefaler, at du bruger Intune; Kan du dog bruge en af de metoder, der er angivet i følgende tabel:
<br/><br/>

|Metode|Hvad kan du gøre?|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **Bemærk**! Intune er nu en del af Microsoft Endpoint Manager.|1. Gå [til Microsoft Endpoint Manager Administration,](https://go.microsoft.com/fwlink/?linkid=2109431) og log på.<br/><br/>2. Vælg **Enheders** \> **konfigurationsprofiler**, og vælg derefter den profiltype, du vil konfigurere. Hvis du endnu ikke har oprettet en profiltype for Enhedsbegrænsninger, eller hvis du vil oprette en ny, skal du se Konfigurer indstillinger for enhedsbegrænsning [i Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. Vælg **Egenskaber**, og vælg derefter **Konfigurationsindstillinger: Rediger**<br/><br/>4. **Udvid Microsoft Defender Antivirus**.<br/><br/>5. **Aktivér skybaseret leveringsbeskyttelse**.<br/><br/>6. På **rullelisten Spørg brugere før eksempelindsendelse** skal du vælge **Send alle eksempler automatisk**.<br/><br/>7. I **rullelisten Registrer potentielt uønskede programmer** skal du **vælge Aktivér** eller **Overse**.<br/><br/>8. Vælg **Gennemse + gem**, og vælg derefter **Gem**. <br/><br/> **Tip**: Du kan finde flere oplysninger om Intune-enhedsprofiler, herunder hvordan du opretter og konfigurerer deres indstillinger, [under Hvad Microsoft Intune enhedsprofiler?](/intune/device-profiles).|
|Microsoft Endpoint Configuration Manager|Se [Opret og installér antimalwarepolitikker for at Endpoint Protection i Konfigurationsstyring](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Når du opretter og konfigurerer dine antimalwarepolitikker, skal du sørge for [](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) at gennemse indstillingerne for beskyttelse i realtid og aktivere [blokering ved første syn](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|Kontrolpanel i Windows|Følg vejledningen her: [Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows). (Du får muligvis *vist Windows Defender Antivirus* i *stedet for Microsoft Defender Antivirus* i nogle versioner Windows.)|
|[Avanceret Gruppepolitik administration](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> eller <br/><br/> [Gruppepolitik administrationskonsol](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Gå til **Computerkonfiguration Administrative** \> **skabeloner** \> **Windows komponenter** \> **Microsoft Defender Antivirus**.<br/><br/>2. Se efter en politik, der **hedder Slå Microsoft Defender Antivirus**.<br/><br/>3. Vælg Rediger **politikindstilling**, og sørg for, at politikken er deaktiveret. Denne handling Microsoft Defender Antivirus. <br/>(Du får muligvis *vist Windows Defender Antivirus* i *stedet for Microsoft Defender Antivirus* i nogle versioner Windows.)|

> [!TIP]
> Du kan implementere politikkerne, før organisationens enheder er onboardet.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Føj Microsoft Defender til slutpunkt til udeladelseslisten for din eksisterende løsning

Dette trin i konfigurationsprocessen indebærer at føje Defender for Endpoint til udeladelseslisten for din eksisterende løsning til slutpunktsbeskyttelse og andre sikkerhedsprodukter, som din organisation bruger.

> [!TIP]
> Hvis du vil have hjælp til at konfigurere udeladelse, skal du se din løsningsudbyders dokumentation.

De specifikke undtagelser, der skal konfigureres, afhænger af, hvilken version af Windows dine slutpunkter eller enheder kører, og er angivet i følgende tabel.
<br/><br/>

| OPERATIVSYSTEM |Udeladelser |
|:--|:--|
|Windows 11 <br/><br/>Windows 10, [version 1803](/windows/release-health/status-windows-10-1803) eller nyere (se [Windows 10 udgivelsesoplysninger](/windows/release-health/release-information))<br/><br/>Windows 10 version 1703 eller 1709 med [KB4493441](https://support.microsoft.com/help/4493441) installeret <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>Desuden er følgende undtagelser Windows server 2012 R2 og 2016, der kører den moderne, samlede løsning, påkrævet efter opdatering af Sense Slutpunktsregistrering og -svar-komponenten med [KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac):<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**BEMÆRK**: Overvågning af midlertidige værtsfiler 6\45 kan være forskellige nummererede undermapper.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Føj din eksisterende løsning til udeladelseslisten for Microsoft Defender Antivirus

I dette trin af konfigurationsprocessen skal du føje din eksisterende løsning til Microsoft Defender Antivirus udeladelseslisten. Du kan vælge mellem flere forskellige metoder for at føje dine Microsoft Defender Antivirus, sådan som det er angivet i følgende tabel:
<br/><br/>

|Metode|Hvad kan du gøre?|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **Bemærk**! Intune er nu en del af Microsoft Endpoint Manager.|1. Gå [til Microsoft Endpoint Manager Administration,](https://go.microsoft.com/fwlink/?linkid=2109431) og log på.<br/><br/>2. Vælg **Enheders** \> **konfigurationsprofiler**, og vælg derefter den profil, du vil konfigurere.<br/><br/>3. Under **Administrer** skal du vælge **Egenskaber**.<br/><br/>4. Vælg **Konfigurationsindstillinger: Rediger**.<br/><br/>5. **Udvid Microsoft Defender Antivirus**, og udvid **derefter Microsoft Defender Antivirus Udeladelse.**<br/><br/>6. Angiv de filer og mapper, udvidelser og processer, der skal udelukkes Microsoft Defender Antivirus scanninger. Du kan finde reference [under Microsoft Defender Antivirus udeladelse.](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions)<br/><br/>7. Vælg **Gennemse + gem**, og vælg derefter **Gem**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. Ved [Konfigurationsstyring](/mem/configmgr/core/servers/manage/admin-console) du gå til **Politikker** \> for **Endpoint Protection** \> og overholdelse af angivne standarder og derefter vælge den **politik, du** vil ændre.<br/><br/>2. Angiv udeladelsesindstillinger for filer og mapper, udvidelser og processer, der skal udelukkes Microsoft Defender Antivirus scanninger.|
|[Gruppepolitik-objekt](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. På Gruppepolitik-administrationscomputer skal du åbne [Gruppepolitik Management Console](https://technet.microsoft.com/library/cc731212.aspx), højreklikke på det Gruppepolitik-objekt, du vil konfigurere, og derefter vælge **Rediger**.<br/><br/>2. I Gruppepolitik **Administration skal** du gå til **Computerkonfiguration og** vælge **Administrative skabeloner**.<br/><br/>3. Udvid træet for **at Windows komponenter \> Microsoft Defender Antivirus udeladelse\>.** (Du får muligvis *vist Windows Defender Antivirus* i *stedet for Microsoft Defender Antivirus* i nogle versioner Windows.)<br/><br/>4. Dobbeltklik på indstillingen **Stiude udeladelse** , og tilføj udeladelseserne.<br/><br/>5. Angiv indstillingen til **Aktiveret**.<br/><br/>6. Under **sektionen Indstillinger** skal du **vælge Vis...**.<br/><br/>7. Angiv hver mappe på sin egen linje under **kolonnen Værdinavn** . Hvis du angiver en fil, skal du sørge for at angive en fuldt kvalificeret sti til filen, herunder drevbogstavet, mappestien, filnavnet og filtypenavnet. Angiv **0** i **kolonnen** Værdi.<br/><br/>8. Vælg **OK**.<br/><br/>9. Dobbeltklik på indstillingen **Udeladelse af udvidelse** , og tilføj udeladelseerne.<br/><br/>10. Angiv indstillingen til **Aktiveret**.<br/><br/>11. Under **sektionen Indstillinger** skal du **vælge Vis...**.<br/><br/>12. Angiv hvert filtypenavn på sin egen linje under **kolonnen Værdinavn** . Angiv **0** i **kolonnen** Værdi.<br/><br/>13. Vælg **OK**.|
|Lokalt gruppepolitikobjekt|1. På slutpunktet eller enheden skal du åbne Editor Gruppepolitik lokal.<br/><br/>2. Gå til **Administrative skabeloner til** \> **computerkonfiguration** \> **Windows komponenter** \> **Microsoft Defender Antivirus** \> **udeladelse.** (Du får muligvis *vist Windows Defender Antivirus* i *stedet for Microsoft Defender Antivirus* i nogle versioner Windows.)<br/><br/>3. Angiv dine sti- og procesudetagelser.|
|Registreringsdatabasenøgle|1. Eksportér følgende registreringsdatabasenøgle: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Importér registreringsdatabasenøglen. Her er to eksempler:<br/>- Lokal sti: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>- Netværksshare: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Vær opmærksom på følgende punkter vedrørende udeladelse

Når du [føjer udeladelse til Microsoft Defender Antivirus scanninger](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus), skal du tilføje sti- og procesude udeladelse.

Husk følgende punkter:

- *Stiudelse udelader* bestemte filer, og uanset hvad disse filer har adgang til.
- *Procesudetagelser* udelukker det, som en proces rører ved, men udelukker ikke selve processen.
- Opliste dine procesudetagelser ved hjælp af deres fulde sti og ikke kun efter deres navn. Metoden kun med navne er mindre sikker.
- Hvis du oplister hver eksekverbar (.exe) som både en stiudeladelse og en procesudeladelse, udelades processen, og hvad den rører ved.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Konfigurer dine enhedsgrupper, enhedssamlinger og organisationsenheder

Enhedsgrupper, enhedssamlinger og organisationsenheder gør det muligt for dit sikkerhedsteam at administrere og tildele sikkerhedspolitikker effektivt. I følgende tabel beskrives hver af disse grupper, og hvordan de konfigureres. Din organisation bruger muligvis ikke alle tre samlingstyper.
<br/><br/>

|Samlingstype|Hvad kan du gøre?|
|---|---|
|[Enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups) (tidligere kaldet *maskingrupper*) gør det muligt for dit sikkerhedsteam at konfigurere sikkerhedsegenskaber som f.eks. automatisk undersøgelse og afhjælpning. <br/><br/> Enhedsgrupper er også nyttige til at tildele adgang til disse enheder, så dit sikkerhedsteam kan løse problemer, hvis det er nødvendigt. <br/><br/> Enhedsgrupper oprettes i portalen, Mens angrebene blev registreret og stoppet, blev beskeder, f.eks. en "startadgangsbesked", udløst og vist i [Microsoft 365 Defender portal](/microsoft-365/security/defender/microsoft-365-defender).|1. Gå til Microsoft 365 Defender portal (<https://security.microsoft.com>).<br/><br/>2. I **navigationsruden** til venstre skal du **vælge Indstillinger** \> **tilladelsesgrupper** \> **for**\> slutpunkter på enheden.<br/><br/>3. Vælg **+ Tilføj enhedsgruppe**.<br/><br/>4. Angiv et navn og en beskrivelse af enhedsgruppen.<br/><br/>5. Vælg en **indstilling på** listen Automatiseringsniveau. (Vi anbefaler **Fuld – afhjulpet trusler automatisk**.) Du kan få mere at vide om de forskellige automatiseringsniveauer [under Hvordan trusler afhjælpes](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Angiv betingelser for en matchende regel for at afgøre, hvilke enheder der tilhører gruppen af enheder. Du kan f.eks. vælge et domæne, os-versioner eller endda bruge [enhedsmærker](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. På fanen **Brugeradgang skal** du angive roller, der skal have adgang til de enheder, der er inkluderet i gruppen af enheder.<br/><br/>8. Vælg **Udført**.|
|[Grupper af enheder](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) gør det muligt for sikkerhedsteamet at administrere programmer, installere overholdelsesindstillinger eller installere softwareopdateringer på enhederne i organisationen. <br/><br/> Enhedssamlinger oprettes ved hjælp af [Konfigurationsstyring](/mem/configmgr/).|Følg trinnene i [Opret en samling](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Med organisationsenheder](/azure/active-directory-domain-services/create-ou) kan du gruppere objekter logisk, f.eks. brugerkonti, tjenestekonti eller computerkonti. <br/><br/> Du kan derefter tildele administratorer til bestemte organisationsenheder og anvende gruppepolitik til at gennemtvinge målrettede konfigurationsindstillinger. <br/><br/> Organisationsenheder er defineret i [Azure Active Directory Domain Services](/azure/active-directory-domain-services).|Følg trinnene i Oprette [en organisationsenhed på et Azure Active Directory domænetjenesters administrerede domæne](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har færdiggjort konfigurationsfasen for [skiftet til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Fortsæt til Fase 3: Onboard to Defender til slutpunkt](switch-to-mde-phase-3.md)
