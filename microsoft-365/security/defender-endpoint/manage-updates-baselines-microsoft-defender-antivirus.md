---
title: Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer
description: Administrer, hvordan Microsoft Defender Antivirus modtager beskyttelse og produktopdateringer.
keywords: opdateringer, grundlinjer for sikkerhed, beskyttelse, planlæg opdateringer, gennemtving opdateringer, mobilopdateringer, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.date: 03/16/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: c6454704c6cabfd5136eeec565c3c57dca044250
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63592363"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer

**Gælder for:**
- [Microsoft Defender for Endpoint Plans 1 og 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Det Microsoft Defender Antivirus at holde dig opdateret for at sikre, at dine enheder har den nyeste teknologi og de nyeste funktioner, der er nødvendige for at beskytte dig mod nye malware- og angrebsteknikker. Sørg for at opdatere din antivirusbeskyttelse, også selvom Microsoft Defender Antivirus kører i [passiv tilstand](microsoft-defender-antivirus-compatibility.md). Der findes to typer opdateringer, der er relateret Microsoft Defender Antivirus holde dem opdateret:

- Sikkerhedsintelligensopdateringer
- Produktopdateringer

> [!TIP]
> Hvis du vil se det nyeste program, den nyeste platform og signaturdatoen, skal du gå til Sikkerhedsintelligens-opdateringer [til Microsoft Defender Antivirus og anden Microsoft-antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Sikkerhedsintelligensopdateringer

Microsoft Defender Antivirus anvender skybaseret beskyttelse (også kaldet Microsoft Advanced [Protection-tjenesten](cloud-protection-microsoft-defender-antivirus.md) eller MAPS) og downloader jævnligt dynamiske sikkerhedsintelligensopdateringer for at yde yderligere beskyttelse. Disse dynamiske opdateringer kommer ikke i stedet for almindelige sikkerhedsintelligensopdateringer via sikkerhedsintelligensopdateringen KB2267602.

> [!NOTE]
> Der udgives opdateringer under følgende KBs:
> - Microsoft Defender Antivirus: KB2267602
> - System Center Endpoint Protection: KB2461484

Beskyttelse, der leveres i skyen, er altid aktiveret og kræver en aktiv forbindelse til internettet for at fungere. Sikkerhedsintelligensopdateringer sker på en planlagt kadence (kan konfigureres via politik). Få mere at vide under [Brug Microsoft cloud-provided protection i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

Du kan finde en liste over de seneste sikkerhedsintelligensopdateringer under [Sikkerhedsintelligens-opdateringer til Microsoft Defender Antivirus og anden Microsoft-antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Programopdateringer er inkluderet i sikkerhedsintelligensopdateringer og frigives ved månedlige kadencer.

## <a name="product-updates"></a>Produktopdateringer

Microsoft Defender Antivirus kræver [månedlige opdateringer (KB4052623),](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) også kaldet *platformopdateringer*.

Du kan administrere fordelingen af opdateringer ved hjælp af en af følgende metoder:

- [Windows serveropdateringstjeneste (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- Den sædvanlige metode, du bruger til at installere Microsoft Windows opdateringer til slutpunkter i dit netværk.

Du kan få mere at [vide under Administrere kilder til Microsoft Defender Antivirus opdateringer til beskyttelse](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Månedlige opdateringer frigives i faser, hvilket resulterer i flere pakker, der er synlige i dine [Window Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - I denne artikel vises ændringer, der er inkluderet i den brede udgivelseskanal. [Se den nyeste brede kanaludgivelse her](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Du kan få mere at vide om processen til gradvis udrulning, og hvis du vil have mere at vide om den næste version, skal du se Administrer den gradvise [implementeringsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
> - Du kan få mere at vide om [sikkerhedsintelligensopdateringer under Sikkerhedsintelligens-opdateringer Microsoft Defender Antivirus og anden Microsoft-antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Hvis du leder efter en liste over Microsoft Defender-processer, kan du downloade **[projektmappen mde-URLs](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)** og derefter vælge **regnearket Microsoft Defender Processes** . Projektmappen mde-URL-adresser viser også de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til, som beskrevet i Aktivér adgang til [Microsoft Defender for Endpoint-tjenestens URL-adresser på proxyserveren](configure-proxy-internet.md).

## <a name="monthly-platform-and-engine-versions"></a>Månedlig platform og programversioner

Du kan finde oplysninger om, hvordan du opdaterer eller installerer platformsopdateringen, [under Opdatering Windows Defender antimalwareplatformen](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Alle vores opdateringer indeholder

- Forbedring af ydeevnen
- Forbedringer af tjenestebarhed
- Integrationsforbedringer (Cloud, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Februar-2022 (platform: 4.18.2202.4 | Program: 1.1.19000.8)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.361.14.0**<br/>
&ensp;Udgivet: **14. marts 2022**<br/>
&ensp;Platform: **4.18.2202.4**<br/>
&ensp;Program: **1.1.19000.8**<br/>
&ensp;Supportfase: **Sikkerheds- og kritiske opdateringer**<br/>

Engine-version: 1.1.19000.8 <br/>
Sikkerhedsintelligens-opdateringsversion: 1.361.14.0 <br/>

### <a name="whats-new"></a>Nyheder

- Registrerings- og funktionsmådeovervågningslogik er blevet forbedret
- Vi har rettet registreringer af falsk positiv, der udløser reduktion af angrebsoverfladen
- Vi har tilføjet en rettelse, der giver bedre pålidelighed Slutpunktsregistrering og -svar vigtige beskeder om registrering af jagt og avanceret registrering af jagt
- Defender understøtter ikke længere brugerdefinerede meddelelser ved toast pop op-vindue. Ændret gruppepolitikobjekt/Intune/SCCM og dokumenter for at afspejle denne ændring.
- Forbedringer til at registrere både oplysninger og kopi af filer, der er skrevet til flytbart lager. Du kan få mere at vide under Flytbare eller flytbare lagermedier i [Microsoft Defender Storage Endpoint Device Control](device-control-removable-storage-access-control.md).
- Vi har forbedret trafikoutput, når tjenesten SmartScreen ikke er tilgængelig 
- Forbedringer af forbindelsesmuligheder for kunder, der bruger proxyer med godkendelseskrav
- Vi har rettet en fejl i forbindelse med opdatering af VDI-enhed for fildeling på netværket 
- Slutpunktsregistrering og -svar bloktilstand understøtter nu detaljeret enhedsmål med nye indholds adresser. Se [Slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand](edr-in-block-mode.md).

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details><details>
<summary>Januar-2022 (platform: 4.18.2201.10 | Program: 1.1.18900.2)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.357.8.0**<br/>
&ensp;Udgivet: **9. februar 2022**<br/>
&ensp;Platform: **4.18.2201.10**<br/>
&ensp;Program: **1.1.18900.2**<br/>
&ensp;Supportfase: **Sikkerheds- og kritiske opdateringer**<br/>

Engine-version: 1.1.18900.2 <br/>
Sikkerhedsintelligens opdateringsversion: 1.357.8.0 <br/>

### <a name="whats-new"></a>Nyheder

- Forbedringer af funktionsmådeovervågning i filtreringsydeevnen
- Hardening til TrustedInstaller
- Forbedringer til beskyttelse af tæmme
- Erstattet med `ScanScheduleTime` ny `ScanScheduleOffest` cmdlet i [Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik konfigurerer antallet af minutter efter midnat til at udføre en planlagt scanning.
- Vi har `-ServiceHealthReportInterval` tilføjet indstillingen [til Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik konfigurerer tidsintervallet (i minutter) til at udføre en planlagt scanning.
- Vi har `AllowSwitchToAsyncInspection` tilføjet indstillingen [til Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik aktiverer en optimering af ydeevnen, der giver mulighed for synkroniseret kontrollerede netværksflows, så du kan skifte til en synkroniseringsinspektion, når de er blevet kontrolleret og valideret.
- Performance Analyzer v2-opdateringer: Understøttelse af Remote PowerShell og PowerShell 7.x er tilføjet. Se [Ydeevneanalyse for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md).
- Vi har rettet en potentiel dubletpakkefejl Microsoft Defender Antivirus netværksinspektionssystemdriveren.

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details><details>
<summary>November-2021 (platform: 4.18.2111.5 | Program: 1.1.18800.4)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.355.2.0**<br/>
&ensp;Udgivet: **9. december 2021**<br/>
&ensp;Platform: **4.18.2111.5**<br/>
&ensp;Program: **1.1.18800.4**<br/>
&ensp;Supportfase: **Sikkerheds- og kritiske opdateringer**<br/>

Programversion: 1.1.18800.4 Sikkerhedsintelligens-opdateringsversion: 1.355.2.0

### <a name="whats-new"></a>Nyheder

- Forbedret effektivitet i CPU-brug for visse krævende scenarier på Exchange servere
- Nye statusfelter for enhedskontrol er blevet tilføjet Get-MpComputerStatus i Defender PowerShell-modulet. Du kan finde flere oplysninger [i Microsoft Defender til enhedsstyring på slutpunkter Flytbart Storage Access Control](device-control-removable-storage-access-control.md).
- Vi har rettet en fejl, `SharedSignatureRoot` hvor værdien ikke kunne fjernes, når den blev indstillet med PowerShell
- Vi har rettet en fejl [, hvor](prevent-changes-to-security-settings-with-tamper-protection.md) beskyttelse mod rettelse ikke blev aktiveret, selvom Microsoft Defender til slutpunkt angav, at beskyttelse med rettelse var slået til
- Vi har tilføjet understøttelse og fejlrettelser til ydeevneanalyse til Microsoft Defender Antivirus værktøj. Du kan finde flere oplysninger [i Ydeevneanalyse for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md).   
   - PowerShell ISE-support tilføjet til `New-MpPerformanceRecording`
   - Vi har rettet fejl for `Get-MpPerformanceReport -TopFilesPerProcess`
   - Vi har rettet lækage af optagelsessessioner `New-MpPerformanceRecording` ved brug i PowerShell 7.x, fjernsessioner og PowerShell ISE


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Tidligere versionsopdateringer: Kun teknisk opgraderingssupport

Når en ny pakkeversion udgives, reduceres support til de to tidligere versioner kun til teknisk support. Versioner, der er ældre end dem, der er angivet i dette afsnit, og som kun er med teknisk opgraderingssupport.<br/><br/>

<details>
<summary> Oktober-2021 (platform: 4.18.2110.6 | Program: 1.1.18700.4)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.353.3.0**<br/>
&ensp;Udgivet: **28. oktober 2021**<br/>
&ensp;Platform: **4.18.2110.6**<br/>
&ensp;Program: **1.1.18700.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

Engine version: 1.1.18700.4 Security intelligence update version: 1.353.3.0

### <a name="whats-new"></a>Nyheder

- Forbedringer af FTP-netværkstrafikkens dækning (File Transfer Protocol)
- Rettelse, der reducerer Microsoft Defender CPU-brugen Exchange Server kører på Windows Server 2016
- Løs problemer med afbrydelser af scanningen
- Løsning til beskeder ved blokerede forsøg på rettelse, der ikke vises i Sikkerhedscenter
- Forbedringer af fleksibiliteten i Microsoft Defender Service

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> September-2021 (platform: 4.18.2109.6 | Program: 1.1.18600.4)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.351.7.0**<br/>
&ensp;Udgivet: **7. oktober 2021**<br/>
&ensp;Platform: **4.18.2109.6**<br/>
&ensp;Program: **1.1.18600.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

Engine version: 1.1.18600.4 Security intelligence update version: 1.351.7.0

### <a name="whats-new"></a>Nyheder
- Ny forsinkelsesring til Microsoft Defender Antivirus program- og platformopdateringer. Enheder, der tilmelder sig denne ring, modtager opdateringer med en 48-timers forsinkelse. Den nye forsinkelsesring foreslås kun til kritiske miljøer. Se [Administrer den gradvise implementeringsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
- Forbedringer af den gradvise implementeringsproces for opdateringer til Microsoft Defender

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> August-2021 (platform: 4.18.2108.7 | Program: 1.1.18500.10)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.349.22.0**<br/>
&ensp;Udgivet: **2. september 2021**<br/>
&ensp;Platform: **4.18.2108.7**<br/>
&ensp;Program: **1.1.18500.10**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af funktionsmådeovervågningsprogrammet
- Udgivet [ny ydeevneanalyse til Microsoft Defender Antivirus](tune-performance-defender-antivirus.md)
- Microsoft Defender Antivirus mod at indlæse skadelige URL-adresser
- Microsoft Defender Antivirus mod TrustedInstaller-bypasset
- Udvidelse af meddelelser om filændringer, så de inkluderer flere data Human-Operated ransomware (HumOR)

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Juli-2021 (platform: 4.18.2107.4 | Program: 1.1.18400.4)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.345.13.0**<br/>
&ensp;Udgivet: **5. august 2021**<br/>
&ensp;Platform: **4.18.2107.4**<br/>
&ensp;Program: **1.1.18400.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Understøttelse af enhedsstyring tilføjet til Windows bærbare enheder
- PuA-beskyttelse (potentielt uønskede programmer) er slået til som standard for forbrugere (Se [Potentielt uønskede apps blokeres som standard](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Planlagte scanninger for Gruppepolitik objekt-administrerede systemer overholder brugerens konfigurerede scanningstid
- Forbedringer af funktionsmådeovervågningsprogrammet

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer

<br/>
</details><details>
<summary> Juni-2021 (platform: 4.18.2106.5 | Program: 1.1.18300.4)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.343.17.0**<br/>
&ensp;Udgivet: **28. juni 2021**<br/>
&ensp;Platform: **4.18.2106.5**<br/>
&ensp;Program: **1.1.18300.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Nye kontrolelementer til administration af den gradvise implementering af Microsoft Defender-opdateringer. Se [Administrer den gradvise implementeringsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
- Forbedring af funktionsmådeovervågningsprogrammet
- Forbedringer af udrulningen af antimalwaredefinitioner
- Udvidede netværkshændelsesinspektioner i Extended Edge

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Maj-2021 (platform: 4.18.2105.4 | Program: 1.1.18200.4)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.341.8.0**<br/>
&ensp;Udgivet: **3. juni 2021**<br/>
&ensp;Platform: **4.18.2105.4**<br/>
&ensp;Program: **1.1.18200.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af [funktionsmådeovervågning](client-behavioral-blocking.md)
- Vi har [rettet filtreringsfunktionen](network-protection.md) for netværksbeskyttelsesbeskeder

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> April-2021 (platform: 4.18.2104.14 | Program: 1.1.18100.5)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.337.2.0**<br/>
&ensp;Udgivet: **26. april 2021**  (Engine: 1.1.18100.6 udgivet 5. maj 2021)<br/>
&ensp;Platform: **4.18.2104.14**<br/>
&ensp;Program: **1.1.18100.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Overvågningslogik for mere funktionsmåde
- Forbedret registrering af nøglelogføring i kernetilstand
- Nye kontrolelementer er blevet tilføjet for at administrere den gradvise implementering af [opdateringer til Microsoft Defender](manage-gradual-rollout.md)


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Marts-2021 (platform: 4.18.2103.7 | Program: 1.1.18000.5)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.335.36.0**<br/>
&ensp;Udgivet: **2. april 2021**<br/>
&ensp;Platform: **4.18.2103.7**<br/>
&ensp;Program: **1.1.18000.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedring af funktionsmådeovervågningsprogrammet
- Udvidede afhjælpninger af netværkets brute-force-angreb
- Flere mislykkede tæmmelse af forsøg på hændelsesgenerering, [når Tamper Protection](prevent-changes-to-security-settings-with-tamper-protection.md) er aktiveret

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Februar-2021 (platform: 4.18.2102.3 | Program: 1.1.17900.7)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.333.7.0**<br/>
&ensp;Udgivet: **9. marts 2021**<br/>
&ensp;Platform: **4.18.2102.3**<br/>
&ensp;Program: **1.1.17900.7**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret tjenestegendannelse [via beskyttelse mod rettelse](prevent-changes-to-security-settings-with-tamper-protection.md)
- Udvid omfanget af beskyttelse mod tæmme

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Januar-2021 (platform: 4.18.2101.9 | Program: 1.1.17800.5)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.327.1854.0**<br/>
&ensp;Udgivet: **2. februar 2021**<br/>
&ensp;Platform: **4.18.2101.9**<br/>
&ensp;Program: **1.1.17800.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedringer af Shellcode exploit Detection
- Øget synlighed for forsøg på at stjæle legitimationsoplysninger
- Forbedringer af antitamperingsfunktioner i Microsoft Defender Antivirus tjenester
- Forbedret understøttelse af ARM x64-emulering
- Rettelse: Slutpunktsregistrering og -svar meddelelse om blokering forbliver i trusselsoversigten, efter beskyttelse i realtid udførte indledende registrering

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> November-2020 (platform: 4.18.2011.6 | Program: 1.1.17700.4)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.327.1854.0**<br/>
&ensp;Udgivet: **3. december 2020**<br/>
&ensp;Platform: **4.18.2011.6**<br/>
&ensp;Program: **1.1.17700.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret [status for SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) understøtter logføring

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Oktober-2020 (platform: 4.18.2010.7 | Program: 1.1.17600.5)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.327.7.0**<br/>
&ensp;Udgivet: **29. oktober 2020**<br/>
&ensp;Platform: **4.18.2010.7**<br/>
&ensp;Program: **1.1.17600.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Nye beskrivelser af kategorier over særlige trusler
- Forbedrede emuleringsfunktioner
- Forbedrede egenskaber for tilladelse/blokering af værtsadresser
- Ny indstilling i Defender CSP til Ignorer fletning af lokale brugerudetagelser

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer
<br/>
</details><details>
<summary> September-2020 (platform: 4.18.2009.7 | Program: 1.1.17500.4)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.325.10.0**<br/>
&ensp;Udgivet: **1. oktober 2020**<br/>
&ensp;Platform: **4.18.2009.7**<br/>
&ensp;Program: **1.1.17500.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Administratortilladelser er nødvendige for at gendanne filer i karantæne
- XML-formaterede hændelser understøttes nu
- CSP-understøttelse til ignorering af udeladelsesfletninger
- Nye administrationsgrænseflader til:
   - UDP-inspektion
   - Netværksbeskyttelse på Server 2019
   - Udeladelse af IP-adresse for netværksbeskyttelse
- Forbedret synlighed i TPM-målinger
- Forbedret Office scanning af VBA-moduler

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer
<br/>
</details>
<details>
<summary> August-2020 (platform: 4.18.2008.9 | Program: 1.1.17400.5)</summary>

&ensp;Opdateringsversion af **sikkerhedsintelligens: 1.323.9.0**<br/>
&ensp;Udgivet: **27. august 2020**<br/>
&ensp;Platform: **4.18.2008.9**<br/>
&ensp;Program: **1.1.17400.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Tilføj flere telemetrihændelser
- Forbedret telemetri for scanningshændelser
- Forbedret funktionsmådeovervågning for hukommelsesscanninger
- Forbedret scanning af makrostrømme
- Føjet `AMRunningMode` til Get-MpComputerStatus PowerShell-cmdlet
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) ignoreres. Microsoft Defender Antivirus automatisk deaktiverer sig selv, når det registrerer et andet antivirusprogram.


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Juli-2020 (platform: 4.18.2007.8 | Program: 1.1.17300.4)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.321.30.0**<br/>
&ensp;Udgivet: **28. juli 2020**<br/>
&ensp;Platform: **4.18.2007.8**<br/>
&ensp;Program: **1.1.17300.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret telemetri til BITS
- Forbedret validering af signeringscertifikat til Authenticode-kode

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Juni-2020 (platform: 4.18.2006.10 | Program: 1.1.17200.2)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.319.20.0**<br/>
&ensp;Udgivet: **22. juni 2020**<br/>
&ensp;Platform: **4.18.2006.10**<br/>
&ensp;Program: **1.1.17200.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Mulighed for at angive [placeringen af supportlogfilerne](./collect-diagnostic-data.md)
- Spring den aggressive scanning over i passiv tilstand.
- Tillad, at Defender opdaterer på forbrugsafsluttede forbindelser
- Fast justering af ydeevnen, når cachelagring er deaktiveret
- Rettet registreringsdatabaseforespørgsel
- Vi har rettet scannings randomisering i ADMX

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Maj-2020 (platform: 4.18.2005.4 | Program: 1.1.17100.2)</summary>

&ensp;Sikkerhedsintelligens **opdateringsversion: 1.317.20.0**<br/>
&ensp;Udgivet: **26. maj 2020**<br/>
&ensp;Platform: **4.18.2005.4**<br/>
&ensp;Program: **1.1.17100.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret logføring af scanningshændelser
- Forbedret håndtering af nedbrud i brugertilstand.
- Hændelsessporing tilføjet til beskyttelse af Tamper
- Rettet INDSENDELSE AF AMSI-eksempel
- Vi har rettet blokering af AMSI-skyen
- Sikkerhedsopdateringslog er rettet

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> April-2020 (platform: 4.18.2004.6 | Program: 1.1.17000.2)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.315.12.0**<br/>
&ensp;Udgivet: **30. april 2020**<br/>
&ensp;Platform: **4.18.2004.6**<br/>
&ensp;Program: **1.1.17000.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af WDfilter
- Føj flere begivenhedsdata, der kan handles på, til hændelser til registrering af reduktion af angrebsoverfladen
- Rettede versionsoplysninger i diagnostiske data og WMI
- En forkert platformversion i brugergrænsefladen er blevet rettet efter platformsopdatering
- Dynamic URL Intel for Fileless Threat Protection
- UEFI-scanningsfunktionalitet
- Udvide logføring for opdateringer

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Marts-2020 (platform: 4.18.2003.8 | Program: 1.1.16900.2)</summary>

&ensp;Sikkerhedsintelligens-opdateringsversion: **1.313.8.0**<br/>
&ensp;Udgivet: **24. marts 2020**<br/>
&ensp;Platform: **4.18.2003.8**<br/>
&ensp;Program: **1.1.16900.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- CPU-begrænsningsindstilling føjet til [MpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Forbedre diagnosticeringsfunktionaliteten
- reducere timeout for sikkerhedsintelligens (5 min)
- Udvid intern LOGfunktion for AMSI-program
- Få bedre meddelelser om procesblokering

### <a name="known-issues"></a>Kendte problemer
[**Rettet**] Microsoft Defender Antivirus springer filer over, når du kører en scanning.

<br/>
</details>

<details>

<summary> Februar-2020 (platform: - | Program: 1.1.16800.2)</summary>


&ensp;Sikkerhedsintelligens-opdateringsversion: **1.311.4.0**<br/>
&ensp;Udgivet: **25. februar 2020**<br/>
&ensp;Platform/klient: **-**<br/>
&ensp;Program: **1.1.16800.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Januar-2020 (platform: 4.18.2001.10 | Program: 1.1.16700.2)</summary>


Sikkerhedsintelligens-opdateringsversion: **1.309.32.0**<br/>
Udgivet: **30. januar 2020**<br/>
Platform/klient: **4.18.2001.10**<br/>
Program: **1.1.16700.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Rettet BSOD på WS2016 med Exchange
- Supportplatformopdateringer, når TMP omdirigeres til netværksstien
- Platform- og programversioner føjes til [WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- udvide signatureopdateringen til passiv [tilstand](./microsoft-defender-antivirus-compatibility.md)
- Rettelse 4.18.1911.3 hænger

### <a name="known-issues"></a>Kendte problemer

[**Rettet**] Enheder, der bruger moderne [standbytilstand](/windows-hardware/design/device-experiences/modern-standby), kan opleve at de hænger sammen med Windows Defender, der resulterer i et hul med beskyttelse.  Påvirkede maskiner ser ud til, at kunden ikke har opdateret til den nyeste antimalwareplatform.
<br/>
> [!IMPORTANT]
> Denne opdatering er:
> - skal bruges af RS1-enheder, der kører en lavere version af platformen, til at understøtte SHA2;
> - har et genstartflag til systemer, der har problemer med hængende;
> - udgives igen i april 2020 og vil ikke blive overskrevet af nyere opdateringer for at bevare fremtidig tilgængelighed;
> - kategoriseres som en opdatering på grund af genstartskravet; og
> - tilbydes kun med Windows [Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> November-2019 (platform: 4.18.1911.3 | Engine: 1.1.16600.7)</summary>

Sikkerhedsintelligens **opdateringsversion: 1.307.13.0**<br/>
Udgivet: **7. december 2019**<br/>
Platform: **4.18.1911.3**<br/>
Program: **1.1.17000.7**<br/>
Supportfase: **Ingen support**<br/>

### <a name="whats-new"></a>Nyheder

- Vi har rettet mpCmdRun-sporingsniveau
- Rettede oplysninger om WDFilter-version
- Forbedring af meddelelser (PUA)
- tilføje MRT-logfiler for at understøtte filer

### <a name="known-issues"></a>Kendte problemer
Når denne opdatering er installeret, skal enheden bruge jumppakken 4.18.2001.10 for at kunne opdatere til den nyeste platformversion.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>Microsoft Defender Antivirus-platform

Platform- og programopdateringer leveres ved en månedlig kadence. Hold dig opdateret med de nyeste platformsopdateringer for at få fuld support. Vores supportstruktur er dynamisk og udvikles i to faser afhængigt af tilgængeligheden af den nyeste platformversion:

- **Serviceringsfase for sikkerheds-** og vigtige opdateringer – Når du kører den nyeste platformversion, vil du være berettiget til at modtage både sikkerheds- og vigtige opdateringer til platformen for malware.

- **Fase for teknisk support (kun)** – Når en ny platformversion er udgivet, reduceres support til ældre versioner (N-2) kun til teknisk support. Platformversioner, der er ældre end N-2, understøttes ikke længere.*

\*Teknisk support vil fortsat være medtaget i forbindelse med opgraderinger fra Windows 10-udgivelsesversionen (se Platformversion, der følger med [Windows 10-udgivelser](#platform-version-included-with-windows-10-releases)) til den nyeste platformversion.

I løbet af den tekniske supportfase (kun) vil kommercielt rimelige supporthændelser blive leveret via Microsoft kundeservice & Support og Microsofts administrerede supporttilbud (f.eks. Premier Support). Hvis en supporthændelse kræver eskalering til udvikling for yderligere vejledning, kræver en ikke-sikkerhedsrelateret opdatering eller kræver en sikkerhedsopdatering, bliver kunder bedt om at opgradere til den nyeste platformversion eller en mellemliggende opdatering (*).

> [!NOTE]
> Hvis du installerer Microsoft Defender Antivirus Platform Update manuelt, eller hvis du bruger et script eller et produkt, der ikke er fra Microsoft-administration, til at installere Microsoft Defender Antivirus Platform Update, skal du sørge for, at versionen `4.18.2001.10` er installeret fra [Microsoft Update-kataloget](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10), før den nyeste version af Platform Update (N-2) er installeret.

### <a name="platform-version-included-with-windows-10-releases"></a>Platformversion, der følger med Windows 10 udgivelser

Tabellen nedenfor indeholder de Microsoft Defender Antivirus og programversioner, der leveres med de seneste Windows 10 udgivelser:<br/><br/>

|Windows 10 udgivelse  |Platformversion  |Engine-version |Supportfase |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Teknisk opgraderingssupport (kun) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Teknisk opgraderingssupport (kun) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Teknisk opgraderingssupport (kun) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Teknisk opgraderingssupport (kun) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Teknisk opgraderingssupport (kun) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Teknisk opgraderingssupport (kun) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Teknisk opgraderingssupport (kun) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Teknisk opgraderingssupport (kun) |

Du Windows 10 oplysninger om [livscyklussen i Windows oplysninger om livscyklus](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Opdateringer til Deployment Image Servicing and Management (DISM)

Vi anbefaler, at du opdaterer dine Windows 10-versioner (Enterprise-, Pro- og Home-versioner), Windows Server 2019, Windows Server 2022 og Windows Server 2016 OS-installationsbilleder med de seneste opdateringer til antivirus og antimalware. Når dine billeder af operativsystemet er opdateret, undgår du et hul i beskyttelsen.

Du kan finde flere oplysninger [i Microsoft Defender-opdatering Windows billeder af installation af operativsystemet](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20220305.1</summary>

&ensp;Pakkeversion: **20220305.1**<br/>
&ensp;Platformversion: **4.18.2201.10**<br/>
&ensp;Engine-version: **1.1.18900.3**<br/>
&ensp;Signaturversion: **1.359.1405.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen

<br/>
</details><details>
<summary>20220203.1</summary>

&ensp;Pakkeversion: **20220203.1**<br/>
&ensp;Platformversion: **4.18.2111.5**<br/>
&ensp;Engine-version: **1.1.18900.2**<br/>
&ensp;Signaturversion: **1.357.32.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>20220105.1</summary>

&ensp;Pakkeversion: **20220105.1**<br/>
&ensp;Platformversion: **4.18.2111.5**<br/>
&ensp;Engine-version: **1.1.18800.4**<br/>
&ensp;Signaturversion: **1.355.1482.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2112.01</summary>

&ensp;Pakkeversion: **1.1.2112.01**<br/>
&ensp;Platformversion: **4.18.2110.6**<br/>
&ensp;Engine-version: **1.1.18700.4**<br/>
&ensp;Signaturversion: **1.353.2283.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2111.02</summary>

&ensp;Pakkeversion: **1.1.2111.02**<br/>
&ensp;Platformversion: **4.18.2110.6**<br/>
&ensp;Engine-version: **1.1.18700.4**<br/>
&ensp;Signaturversion: **1.353.613.0**<br/>

### <a name="fixes"></a>Rettelser
- Et problem med lokalisering af filer er blevet rettet

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Pakkeversion: **1.1.2110.01**<br/>
&ensp;Platformversion: **4.18.2109.6**<br/>
&ensp;Engine-version: **1.1.18500.10**<br/>
&ensp;Signaturversion: **1.349.2103.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2109.01</summary>

&ensp;Pakkeversion: **1.1.2109.01**<br/>
&ensp;Platformversion: **4.18.2107.4**<br/>
&ensp;Engine-version: **1.1.18400.5**<br/>
&ensp;Signaturversion: **1.347.891.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2108.01</summary>

&ensp;Pakkeversion: **1.1.2108.01**<br/>
&ensp;Platformversion: **4.18.2107.4**<br/>
&ensp;Engine-version: **1.1.18300.4**<br/>
&ensp;Signaturversion: **1.343.2244.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2107.02</summary>

&ensp;Pakkeversion: **1.1.2107.02**<br/>
&ensp;Platformversion: **4.18.2105.5**<br/>
&ensp;Engine-version: **1.1.18300.4**<br/>
&ensp;Signaturversion: **1.343.658.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2106.01</summary>

&ensp;Pakkeversion: **1.1.2106.01**<br/>
&ensp;Platformversion: **4.18.2104.14**<br/>
&ensp;Engine-version: **1.1.18100.6**<br/>
&ensp;Signaturversion: **1.339.1923.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2105.01</summary>

&ensp;Pakkeversion: **1.1.2105.01**<br/>
&ensp;Platformversion: **4.18.2103.7**<br/>
&ensp;Engine-version: **1.1.18100.6**<br/>
&ensp;Signaturversion: **1.339.42.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2104.01</summary>

&ensp;Pakkeversion: **1.1.2104.01**<br/>
&ensp;Platformversion: **4.18.2102.4**<br/>
&ensp;Engine-version: **1.1.18000.5**<br/>
&ensp;Signaturversion: **1.335.232.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2103.01</summary>

&ensp;Pakkeversion: **1.1.2103.01**<br/>
&ensp;Platformversion: **4.18.2101.9**<br/>
&ensp;Engine-version: **1.1.17800.5**<br/>
&ensp;Signaturversion: **1.331.2302.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2102.03</summary>

&ensp;Pakkeversion: **1.1.2102.03**<br/>
&ensp;Platformversion: **4.18.2011.6**<br/>
&ensp;Engine-version: **1.1.17800.5**<br/>
&ensp;Signaturversion: **1.331.174.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2101.02</summary>

&ensp;Pakkeversion: **1.1.2101.02**<br/>
&ensp;Platformversion: **4.18.2011.6**<br/>
&ensp;Engine-version: **1.1.17700.4**<br/>
&ensp;Signaturversion: **1.329.1796.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2012.01</summary>

&ensp;Pakkeversion: **1.1.2012.01**<br/>
&ensp;Platformversion: **4.18.2010.7**<br/>
&ensp;Engine-version: **1.1.17600.5**<br/>
&ensp;Signaturversion: **1.327.1991.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2011.02</summary>

&ensp;Pakkeversion: **1.1.2011.02**<br/>
&ensp;Platformversion: **4.18.2010.7**<br/>
&ensp;Engine-version: **1.1.17600.5**<br/>
&ensp;Signaturversion: **1.327.658.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Opdaterede Microsoft Defender Antivirus signaturer
<br/>
</details><details>
<summary>1.1.2011.01</summary>

&ensp;Pakkeversion: **1.1.2011.01**<br/>
&ensp;Platformversion: **4.18.2009.7**<br/>
&ensp;Engine-version: **1.1.17600.5**<br/>
&ensp;Signaturversion: **1.327.344.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2009.10</summary>

&ensp;Pakkeversion: **1.1.2011.01**<br/>
&ensp;Platformversion: **4.18.2008.9**<br/>
&ensp;Engine-version: **1.1.17400.5**<br/>
&ensp;Signaturversion: **1.327.2216.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Vi har tilføjet understøttelse Windows 10 RS1 eller nyere os-installationsbilleder.
<br/>
</details>

## <a name="more-resources"></a>Flere ressourcer

| Artikel | Beskrivelse  |
|:---|:---|
|[Opdatering af Microsoft Defender Windows billeder af installation af operativsystem](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Gennemse antimalwareopdateringspakker for dine WIM- og VHD-filer (OS-installationsbilleder). Få Microsoft Defender Antivirus opdateringer til Windows 10 (Enterprise-, Pro- og Home-versioner), Windows Server 2019, Windows Server 2022 og Windows Server 2016-installationsbilleder.  |
|[Administrer, hvordan sikkerhedsopdateringer hentes og anvendes](manage-protection-updates-microsoft-defender-antivirus.md) | Beskyttelsesopdateringer kan leveres via mange kilder. |
|[Administrer, hvornår sikkerhedsopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Du kan planlægge, hvornår sikkerhedsopdateringer skal downloades. |
|[Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Hvis et slutpunkt går glip af en opdatering eller planlagt scanning, kan du gennemtvinge en opdatering eller scanning, næste gang en bruger logger på. |
|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md) | Du kan indstille sikkerhedsopdateringer, der skal downloades ved start eller efter visse skybaserede beskyttelseshændelser. |
|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Du kan angive indstillinger, f.eks. om opdateringer skal forekomme på batteristrøm, der er særligt nyttige for mobilenheder og virtuelle computere. |
| [Opdatering af Microsoft Defender til slutpunkt til Slutpunktsregistrering og -svar sensor](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Du kan opdatere den Slutpunktsregistrering og -svar sensor (MsSense.exe), der er inkluderet i den nye samlede Løsningspakke til Microsoft Defender til slutpunkter, der blev udgivet i 2021.   |
