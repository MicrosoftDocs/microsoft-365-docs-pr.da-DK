---
title: Skift til Microsoft Defender for Endpoint – installation
description: Skift til Defender for Endpoint. Gennemse konfigurationsprocessen, som omfatter installation af Microsoft Defender Antivirus.
keywords: overførsel, Microsoft Defender for Endpoint, antivirus, passiv tilstand, konfigurationsproces
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
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 7f22d5d1162e01afe737e6e3f25450cc22e25c76
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695720"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>Skift til Microsoft Defender for Endpoint - fase 2: Konfiguration

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![Fase 1: Forbered.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[Fase 1: Forbered](switch-to-mde-phase-1.md)|![Fase 2: Konfigurer.](images/phase-diagrams/setup.png#lightbox)<br/>Fase 2: Konfigurer|[![Fase 3: Onboard3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Fase 3: Onboard](switch-to-mde-phase-3.md)|
|---|---|---|
||*Du er her!*||

**Velkommen til konfigurationsfasen for [skift til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**. Denne fase omfatter følgende trin:

1. [Geninstaller/aktivér Microsoft Defender Antivirus på dine slutpunkter](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [Konfigurer Defender for Slutpunkt](#configure-defender-for-endpoint).
3. [Føj Defender for Endpoint til listen over undtagelser for din eksisterende løsning](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [Føj din eksisterende løsning til listen over undtagelser for Microsoft Defender Antivirus](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [Konfigurer dine enhedsgrupper, enhedssamlinger og organisationsenheder](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>Geninstaller/aktivér Microsoft Defender Antivirus på dine slutpunkter

På visse versioner af Windows blev Microsoft Defender Antivirus sandsynligvis fjernet eller deaktiveret, da din ikke-Microsoft antivirus-/antimalware-løsning blev installeret. Når slutpunkter, der kører Windows, føjes til Defender for Endpoint, kan Microsoft Defender Antivirus køre i passiv tilstand sammen med en ikke-Microsoft-antivirusløsning. Du kan få mere at vide under [Antivirusbeskyttelse med Defender for Endpoint](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

Når du skifter til Defender for Endpoint, skal du muligvis udføre visse trin for at geninstallere eller aktivere Microsoft Defender Antivirus. I følgende tabel beskrives det, hvad du skal gøre på dine Windows-klienter og -servere.

|Slutpunktstype|Sådan gør du|
|---|---|
|Windows-klienter (f.eks. slutpunkter, der kører Windows 10 og Windows 11)|Generelt behøver du ikke at foretage dig noget for Windows-klienter (medmindre Microsoft Defender Antivirus er fjernet). Generelt skal Microsoft Defender Antivirus stadig installeres, men er sandsynligvis deaktiveret på dette tidspunkt i overførselsprocessen. <br/><br/> Når der er installeret en ikke-Microsoft-antivirus-/antimalwareløsning, og klienterne endnu ikke er onboardet til Defender for Endpoint, deaktiveres Microsoft Defender Antivirus automatisk. Når klientslutpunkterne senere er onboardet til Defender for Endpoint, går Microsoft Defender Antivirus i passiv tilstand, hvis disse slutpunkter kører en antivirusløsning, der ikke er Fra Microsoft. <br/><br/> Hvis den ikke-Microsoft-antivirusløsning fjernes, skifter Microsoft Defender Antivirus automatisk til aktiv tilstand.|
|Windows-servere|På Windows Server skal du geninstallere Microsoft Defender Antivirus og indstille den til passiv tilstand manuelt. På Windows-servere kan Microsoft Defender Antivirus ikke køre sammen med den ikke-Microsoft-antivirusløsning, når der er installeret et antivirusprogram eller et antimalwareprogram, der ikke er Microsoft. I disse tilfælde er Microsoft Defender Antivirus deaktiveret eller fjernet manuelt. <br/><br/> Hvis du vil geninstallere eller aktivere Microsoft Defender Antivirus på Windows Server, skal du udføre følgende opgaver: <br/>- [Geninstaller Microsoft Defender Antivirus på Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [Geninstaller Microsoft Defender Antivirus på Windows Server, version 1803 eller nyere](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [Angiv Microsoft Defender Antivirus til passiv tilstand på Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>Hvis du støder på problemer med at geninstallere eller aktivere Microsoft Defender Antivirus på Windows Server, skal du se [Fejlfinding: Microsoft Defender Antivirus fjernes på Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> Hvis du vil vide mere om tilstande for Microsoft Defender Antivirus med antivirusbeskyttelse, der ikke er fra Microsoft, skal du se [Microsoft Defender Antivirus-kompatibilitet](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>Genaktiver Microsoft Defender Antivirus på Windows Server 2016

Du kan bruge [Command-Line Utility til beskyttelse af skadelig software](command-line-arguments-microsoft-defender-antivirus.md) til at genaktivere Microsoft Defender Antivirus på Windows Server 2016.

1. Åbn Kommandoprompt som lokal administrator på serveren.

2. Kør følgende kommando: `MpCmdRun.exe -wdenable`

3. Genstart enheden.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>Genaktiver Microsoft Defender Antivirus på Windows Server, version 1803 eller nyere

> [!IMPORTANT]
> Følgende procedure gælder kun for slutpunkter eller enheder, der kører følgende versioner af Windows:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Server, version 1803 (kun kernetilstand)

1. Åbn Windows PowerShell som lokal administrator på serveren.

2. Kør følgende PowerShell-cmdlet'er:

   ```powershell
   # For Windows Server 2016
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Gui
   
   # For Windows Server 2019 and Windows Server 2022
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

   Når du bruger DISM-kommandoen i en opgavesekvens, der kører PowerShell, er følgende sti til cmd.exe påkrævet.
   Eksempel:

   ```powershell
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. Genstart enheden.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>Angiv Microsoft Defender Antivirus til passiv tilstand på Windows Server

> [!TIP]
> Du kan nu køre Microsoft Defender Antivirus i passiv tilstand på Windows Server 2012 R2 og 2016. Du kan få flere oplysninger under [Indstillinger for installation af Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. Åbn Registreringseditor, og naviger derefter til `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. Rediger (eller opret) en DWORD-post med navnet **ForceDefenderPassiveMode**, og angiv følgende indstillinger:

   - Angiv DWORD-værdien til **1**.

   - Under **Base** skal du vælge **Hexadecimal**.

> [!NOTE]
> Når du har onboardet til Defender for Endpoint, skal du muligvis angive Microsoft Defender Antivirus til passiv tilstand på Windows Server. Hvis du vil validere, at passiv tilstand er angivet som forventet, skal du søge efter **Event 5007** i registreringsdatabasenøglen **Microsoft-Windows-Windows Defender Operational** (placeret på `C:\Windows\System32\winevt\Logs`) og bekræfte, at registreringsdatabasenøglerne **ForceDefenderPassiveMode** eller **PassiveMode** er angivet til **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Bruger du Windows Server 2012 R2 eller Windows Server 2016?

Du kan nu køre Microsoft Defender Antivirus i passiv tilstand på Windows Server 2012 R2 og 2016 ved hjælp af ovenstående metode. Du kan få flere oplysninger under [Indstillinger for installation af Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>Konfigurer Defender for Slutpunkt

Dette trin i overførselsprocessen omfatter konfiguration af Microsoft Defender Antivirus til dine slutpunkter. Vi anbefaler, at du bruger Intune, men du kan bruge en af de metoder, der er angivet i følgende tabel:

|Metode|Sådan gør du|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **BEMÆRK**! Intune er nu en del af Microsoft Endpoint Manager.|1. Gå til [Microsoft Endpoint Manager Administration,](https://go.microsoft.com/fwlink/?linkid=2109431) og log på.<br/><br/>2. Vælg **Enhedskonfigurationsprofiler**\>, og vælg derefter den profiltype, du vil konfigurere. Hvis du endnu ikke har oprettet en profiltype for **enhedsbegrænsninger**, eller hvis du vil oprette en ny, skal du se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. Vælg **Egenskaber**, og vælg derefter **Konfigurationsindstillinger: Rediger**<br/><br/>4. Udvid **Microsoft Defender Antivirus**.<br/><br/>5. Aktivér **skybaseret beskyttelse**.<br/><br/>6. På rullelisten **Spørg brugere før eksempelindsendelse** skal du vælge **Send alle eksempler automatisk**.<br/><br/>7. På rullelisten **Registrer potentielt uønskede programmer** skal du vælge **Aktivér** eller **Overvåg**.<br/><br/>8. Vælg **Gennemse + Gem**, og vælg derefter **Gem**. <br/><br/> **Tip**: Du kan få flere oplysninger om Intune enhedsprofiler, herunder hvordan du opretter og konfigurerer deres indstillinger, under [Hvad er Microsoft Intune enhedsprofiler?](/intune/device-profiles).|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr)|Se [Opret og installer antimalwarepolitikker for Endpoint Protection i Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> Når du opretter og konfigurerer dine antimalwarepolitikker, skal du sørge for at gennemse [beskyttelsesindstillinger i realtid](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) og [aktivere blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|Kontrolpanel i Windows|Følg vejledningen her: [Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows) til. (Du kan muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus* i nogle versioner af Windows).|
|[Administration af avancerede Gruppepolitik](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> Eller <br/><br/> [administrationskonsol til Gruppepolitik](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. Gå til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows-komponenter** \> **Microsoft Defender Antivirus**.<br/><br/>2. Søg efter en politik, der kaldes **Slå Microsoft Defender Antivirus fra**.<br/><br/>3. Vælg **Rediger politikindstilling**, og sørg for, at politikken er deaktiveret. Denne handling aktiverer Microsoft Defender Antivirus. <br/>(Du kan muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus* i nogle versioner af Windows).|

> [!TIP]
> Du kan installere politikkerne, før organisationens enheder onboardes.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>Føj Microsoft Defender for Endpoint til listen over undtagelser for din eksisterende løsning

Dette trin i konfigurationsprocessen omfatter tilføjelse af Defender for Endpoint til listen over undtagelser for din eksisterende løsning til beskyttelse af slutpunkter og andre sikkerhedsprodukter, som din organisation bruger.

> [!TIP]
> Du kan få hjælp til at konfigurere udeladelser i dokumentationen til din løsningsudbyder.

De specifikke undtagelser, der skal konfigureres, afhænger af, hvilken version af Windows dine slutpunkter eller enheder kører, og de er angivet i følgende tabel.

| Operativsystem |Udeladelser |
|:--|:--|
|[Windows 11](/windows/whats-new/windows-11-overview) <br/><br/>Windows 10 [version 1803](/lifecycle/announcements/windows-server-1803-end-of-servicing) eller nyere (se [Windows 10 udgivelsesoplysninger](/windows/release-health/release-information))<br/><br/>Windows 10, version 1703 eller 1709 med [KB4493441](https://support.microsoft.com/help/4493441) installeret <br/><br/> [Windows Server 2022](/windows/release-health/status-windows-server-2022)<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server, version 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\DataCollection`<br/><br/> Derudover kræves følgende undtagelser på Windows Server 2012 R2 og 2016, der kører den moderne, samlede løsning, efter at du har opdateret Sense EDR-komponenten ved hjælp af [KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac):<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe`|
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**BEMÆRK**! Overvågning af midlertidige værtsfiler 6\45 kan være forskellige nummererede undermapper.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>Føj din eksisterende løsning til listen over undtagelser for Microsoft Defender Antivirus

I dette trin i konfigurationsprocessen føjer du din eksisterende løsning til microsoft Defender Antivirus-udeladelseslisten. Du kan vælge mellem flere metoder til at føje dine undtagelser til Microsoft Defender Antivirus, som vist i følgende tabel: 

|Metode|Sådan gør du|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **BEMÆRK**! Intune er nu en del af Microsoft Endpoint Manager.|1. Gå til [Microsoft Endpoint Manager Administration,](https://go.microsoft.com/fwlink/?linkid=2109431) og log på.<br/><br/>2. Vælg **Enhedskonfigurationsprofiler**\>, og vælg derefter den profil, du vil konfigurere.<br/><br/>3. Vælg **Egenskaber** under **Administrer**.<br/><br/>4. Vælg **Konfigurationsindstillinger: Rediger**.<br/><br/>5. Udvid **Microsoft Defender Antivirus**, og udvid derefter **Microsoft Defender Antivirus Exclusions**.<br/><br/>6. Angiv de filer og mapper, udvidelser og processer, der skal udelukkes fra Microsoft Defender Antivirus-scanninger. Du kan se en reference under [Microsoft Defender Antivirus-udeladelser](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. Vælg **Gennemse + Gem**, og vælg derefter **Gem**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. Ved hjælp af [Configuration Manager-konsollen](/mem/configmgr/core/servers/manage/admin-console) skal du gå til **Assets and Compliance** \> **Endpoint Protection** \> **Antimalware Policies** og derefter vælge den politik, du vil ændre.<br/><br/>2. Angiv indstillinger for udeladelse for filer og mapper, udvidelser og processer, der skal udelades fra Microsoft Defender Antivirus-scanninger.|
|[Gruppepolitik objekt](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. Åbn [administrationskonsollen Gruppepolitik](https://technet.microsoft.com/library/cc731212.aspx) på din Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.<br/><br/>2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.<br/><br/>3. Udvid træet til **Windows-komponenter \> Microsoft Defender Antivirus \> Exclusions**. (Du kan muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus* i nogle versioner af Windows).<br/><br/>4. Dobbeltklik på indstillingen **Stiudeladelser,** og tilføj udeladelser.<br/><br/>5. Angiv indstillingen til **Aktiveret**.<br/><br/>6. Under afsnittet **Indstillinger** skal du vælge **Vis...**.<br/><br/>7. Angiv hver mappe på sin egen linje under kolonnen **Værdinavn** . Hvis du angiver en fil, skal du sørge for at angive en fuldt gyldig sti til filen, herunder drevbogstavet, mappestien, filnavnet og filtypenavnet. Angiv **0** i kolonnen **Værdi** .<br/><br/>8. Vælg **OK**.<br/><br/>9. Dobbeltklik på indstillingen **Udeladelser for filtypenavne,** og tilføj undtagelserne.<br/><br/>10. Angiv indstillingen til **Aktiveret**.<br/><br/>11. Under afsnittet **Indstillinger** skal du vælge **Vis...**.<br/><br/>12. Angiv hvert filtypenavn på sin egen linje under kolonnen **Værdinavn** . Angiv **0** i kolonnen **Værdi** .<br/><br/>13. Vælg **OK**.|
|Lokalt gruppepolitikobjekt|1. Åbn editoren Lokal Gruppepolitik på slutpunktet eller enheden.<br/><br/>2. Gå til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows-komponenter** \> **Microsoft Defender Antivirus** \> **Exclusions**. (Du kan muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus* i nogle versioner af Windows).<br/><br/>3. Angiv stien og procesudeladelser.|
|Registreringsdatabasenøgle|1. Eksportér følgende registreringsdatabasenøgle: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. Importér registreringsdatabasenøglen. Her er to eksempler:<br/>- Lokal sti: `regedit.exe /s c:\temp\MDAV_Exclusion.reg`<br/>- Netværksshare: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>Vær opmærksom på følgende punkter om undtagelser

Når du [føjer udeladelser til Microsoft Defender Antivirus-scanninger](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus), skal du tilføje sti- og procesudeladelser.

Vær opmærksom på følgende punkter:

- *Udeladelser af stier* udelukker bestemte filer, og hvad disse filer end har adgang til.
- *Procesudeladelser* udelukker, uanset hvad en proces rører, men udelukker ikke selve processen.
- Angiv dine procesudeladelser ved hjælp af deres fulde sti og ikke kun efter deres navn. (Metoden kun navn er mindre sikker).
- Hvis du angiver hver eksekverbar (.exe) som både en stiudeladelse og en procesudeladelse, udelades processen og det, den indeholder.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>Konfigurer dine enhedsgrupper, enhedssamlinger og organisationsenheder

Enhedsgrupper, enhedssamlinger og organisationsenheder gør det muligt for dit sikkerhedsteam at administrere og tildele sikkerhedspolitikker effektivt og effektivt. I følgende tabel beskrives hver af disse grupper, og hvordan du konfigurerer dem. Din organisation bruger muligvis ikke alle tre samlingstyper.

|Samlingstype|Sådan gør du|
|---|---|
|[Enhedsgrupper](/microsoft-365/security/defender-endpoint/machine-groups) (tidligere kaldet *computergrupper*) gør det muligt for dit team af sikkerhedshandlinger at konfigurere sikkerhedsfunktioner, f.eks. automatiseret undersøgelse og afhjælpning. <br/><br/> Enhedsgrupper er også nyttige til at tildele adgang til disse enheder, så dit team af sikkerhedshandlinger kan udføre afhjælpningshandlinger, hvis det er nødvendigt. <br/><br/> Enhedsgrupper oprettes i , mens angrebet blev registreret og stoppet, blev beskeder, f.eks. en "indledende adgangsbesked", udløst og vist på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender).|1. Gå til Microsoft 365 Defender-portalen (<https://security.microsoft.com>).<br/><br/>2. Vælg **Indstillinger** \> **Slutpunkter** \>  \> **Enhedsgrupper** i navigationsruden til venstre.<br/><br/>3. Vælg **+ Tilføj enhedsgruppe**.<br/><br/>4. Angiv et navn og en beskrivelse til enhedsgruppen.<br/><br/>5. Vælg en indstilling **på listen Automatiseringsniveau** . (Vi anbefaler **Fuld – afhjælp trusler automatisk**). Du kan få mere at vide om de forskellige automatiseringsniveauer under [Sådan afhjælpes trusler](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. Angiv betingelser for en matchende regel for at bestemme, hvilke enheder der tilhører enhedsgruppen. Du kan f.eks. vælge et domæne, os-versioner eller endda bruge [enhedskoder](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. Under fanen **Brugeradgang** skal du angive roller, der skal have adgang til de enheder, der er inkluderet i enhedsgruppen.<br/><br/>8. Vælg **Udført**.|
|[Enhedssamlinger](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) gør det muligt for dit team af sikkerhedshandlinger at administrere programmer, installere indstillinger for overholdelse af angivne standarder eller installere softwareopdateringer på enhederne i din organisation. <br/><br/> Enhedssamlinger oprettes ved hjælp af [Configuration Manager](/mem/configmgr/).|Følg trinnene i [Opret en samling](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[Organisatoriske enheder](/azure/active-directory-domain-services/create-ou) gør det muligt for dig at gruppere objekter logisk, f.eks. brugerkonti, tjenestekonti eller computerkonti. <br/><br/> Du kan derefter tildele administratorer til bestemte organisationsenheder og anvende gruppepolitik til at gennemtvinge målrettede konfigurationsindstillinger. <br/><br/> Organisatoriske enheder defineres i [Azure Active Directory-domæneservices](/azure/active-directory-domain-services).|Følg trinnene i [Opret en organisationsenhed i et Azure Active Directory-domæneservices administreret domæne](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført installationsfasen for [at skifte til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Fortsæt til fase 3: Onboard til Defender for Endpoint](switch-to-mde-phase-3.md)
