---
title: Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer
description: Administrer, hvordan Microsoft Defender Antivirus modtager beskyttelse og produktopdateringer.
keywords: opdateringer, grundlæggende sikkerhedsopdateringer, beskyttelse, tidsplanopdateringer, tving opdateringer, mobilopdateringer, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr, mkaminska
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 6822f736cae73d7d4654f8b4310e0e397cffa677
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077481"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-apply-baselines"></a>Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer

> [!IMPORTANT]
> Kunder, der anvendte opdateringen til Microsoft Defender-programmet fra marts 2022 (**1.1.19100.5**), kan have oplevet høj ressourceudnyttelse (CPU og/eller hukommelse). Microsoft har udgivet en opdatering (**1.1.19200.5**), der løser de fejl, der blev introduceret i den tidligere version. Kunder anbefales at opdatere til denne nye motor build af Antivirus Engine (**1.1.19200.5**). Hvis du vil sikre, at eventuelle problemer med ydeevnen er fuldt løst, anbefales det at genstarte maskiner efter anvendelse af opdatering. Se [Månedlige platform- og programversioner](#monthly-platform-and-engine-versions) (i denne artikel).

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1 og 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Det er vigtigt at holde Microsoft Defender Antivirus opdateret for at sikre, at dine enheder har den nyeste teknologi og de funktioner, der er nødvendige for at beskytte mod ny malware og angrebsteknikker. Sørg for at opdatere antivirusbeskyttelsen, selvom Microsoft Defender Antivirus kører i [passiv tilstand](microsoft-defender-antivirus-compatibility.md). Der er to typer opdateringer, der er relateret til at holde Microsoft Defender Antivirus opdateret:

- [Opdateringer til sikkerhedsintelligens](#security-intelligence-updates)
- [Produktopdateringer](#product-updates)

> [!TIP]
> Hvis du vil se den mest aktuelle program-, platform- og signaturdato, skal du gå [til Sikkerhedsintelligensopdateringer til Microsoft Defender Antivirus og andre Microsoft-antimalwareprogrammer](https://www.microsoft.com/en-us/wdsi/defenderupdates)

## <a name="security-intelligence-updates"></a>Opdateringer til sikkerhedsintelligens

Microsoft Defender Antivirus bruger [skybaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md) (også kaldet Microsoft Advanced Protection Service eller MAPS) og downloader jævnligt dynamiske opdateringer til sikkerhedsintelligens for at yde yderligere beskyttelse. Disse dynamiske opdateringer træder ikke i stedet for regelmæssige opdateringer af sikkerhedsintelligens via KB2267602.

> [!NOTE]
> Opdateringer udgives under følgende KB:
> - Microsoft Defender Antivirus: KB2267602
> - System Center Endpoint Protection: KB2461484

Skybaseret beskyttelse er altid aktiveret og kræver en aktiv forbindelse til internettet for at fungere. Sikkerhedsintelligensopdateringer sker efter en planlagt rytme (kan konfigureres via politik). Du kan få flere oplysninger under [Brug microsoft cloudbaseret beskyttelse i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

Du kan se en liste over de seneste opdateringer til [sikkerhedsintelligens under Opdateringer til sikkerhedsintelligens for Microsoft Defender Antivirus og andet Microsoft-antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).

Programopdateringer er inkluderet i opdateringer til sikkerhedsintelligens og udgives månedligt.

## <a name="product-updates"></a>Produktopdateringer

Microsoft Defender Antivirus kræver [månedlige opdateringer (KB4052623),](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform) der kaldes *platformopdateringer*.

Du kan administrere distributionen af opdateringer via en af følgende metoder:

- [Windows Server Update Service (WSUS)](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/sum/understand/software-updates-introduction)
- Den sædvanlige metode, du bruger til at installere Microsoft og Windows opdateringer til slutpunkter på dit netværk.

Du kan få flere oplysninger under [Administrer kilderne til Microsoft Defender Antivirus beskyttelsesopdateringer](/mem/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

> [!NOTE]
> - Månedlige opdateringer udgives i faser, hvilket resulterer i flere pakker, der er synlige i dit [Vindue Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).
> - Denne artikel indeholder en liste over ændringer, der er inkluderet i den brede udgivelseskanal. [Se den seneste brede kanalversion her](https://www.microsoft.com/security/encyclopedia/adlpackages.aspx?action=info).
> - Hvis du vil vide mere om processen for gradvis udrulning og se flere oplysninger om den næste version, skal du se [Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
> - Hvis du vil vide mere om opdateringer til sikkerhedsintelligens, skal du se [Opdateringer til sikkerhedsintelligens for Microsoft Defender Antivirus og andet Microsoft-antimalware](https://www.microsoft.com/en-us/wdsi/defenderupdates).
> - Hvis du leder efter en liste over Microsoft **[Defender-processer, skal du downloade projektmappen med mde-URL-adresser](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)** og derefter vælge regnearket **Microsoft Defender-processer** . Projektmappen med mde-URL-adresser viser også de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til, som beskrevet i [Aktivér adgang til Microsoft Defender for Endpoint tjeneste-URL-adresser på proxyserveren](configure-proxy-internet.md).

## <a name="monthly-platform-and-engine-versions"></a>Månedlige platform- og programversioner

Du kan få oplysninger om, hvordan du opdaterer eller installerer platformsopdateringen, under [Opdatering til Windows Defender antimalwareplatform](https://support.microsoft.com/help/4052623/update-for-windows-defender-antimalware-platform).

Alle vores opdateringer indeholder

- Forbedringer af ydeevnen
- Forbedringer af tjenestens anvendelighed
- Forbedringer af integration (Cloud, [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender))
<br/><br/>
<details>
<summary>Marts-2022-OPDATERING (platform: 4.18.2203.5 | Motor: 1.1.19200.5)</summary>

*Kunder, der anvendte opdateringen til Microsoft Defender-programmet fra marts 2022 (**1.1.19100.5**), kan have oplevet høj ressourceudnyttelse (CPU og/eller hukommelse). Microsoft har udgivet en opdatering (**1.1.19200.5**), der løser de fejl, der blev introduceret i den tidligere version. Kunder anbefales at opdatere til denne nye motor build af Antivirus Engine (**1.1.19200.5**). Hvis du vil sikre, at eventuelle problemer med ydeevnen er fuldt løst, anbefales det at genstarte maskiner efter anvendelse af opdatering.*

&ensp;Version af sikkerhedsintelligensopdatering: **1.363.817.0**<br/>
&ensp;Udgivet: **22. april 2022**<br/>
&ensp;Platform: **4.18.2203.5**<br/>
&ensp;Motor: **1.1.19200.5**<br/>
&ensp;Supportfase: **Sikkerhedsopdateringer og vigtige opdateringer**<br/>

Programversion: 1.1.19200.5 <br/>
Version af sikkerhedsintelligensopdatering: 1.363.817.0<br/>

### <a name="whats-new"></a>Nyheder

- Løser problemer med høj ressourceudnyttelse (CPU og/eller hukommelse), der er relateret til opdateringen af Microsoft Defender-programmet fra marts 2022 (1.1.19100.5)

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details><details>
<summary>Marts-2022 (platform: 4.18.2203.5 | Motor: 1.1.19100.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.361.1449.0**<br/>
&ensp;Udgivet: **7. april 2022**<br/>
&ensp;Platform: **4.18.2203.5**<br/>
&ensp;Motor: **1.1.19100.5**<br/>
&ensp;Supportfase: **Sikkerhedsopdateringer og vigtige opdateringer**<br/>

Programversion: 1.1.19100.5 <br/>
Version af sikkerhedsintelligensopdatering: 1.361.1449.0<br/>

### <a name="whats-new"></a>Nyheder

- Tilføjet rettelse til en [regel for reduktion af angrebsoverfladen](attack-surface-reduction.md), der blokerede et Outlook-tilføjelsesprogram 
- Tilføjet rettelse af problemer med ydeevnen for [overvågning af funktionsmåde](configure-protection-features-microsoft-defender-antivirus.md) , der er relateret til korte liveprocesser 
- Tilføjet rettelse af [AMSI-udeladelse](/windows/win32/amsi/antimalware-scan-interface-portal) 
- Forbedrede funktioner til [beskyttelse af manipulation](prevent-changes-to-security-settings-with-tamper-protection.md) 
- Der er tilføjet en rettelse til [beskyttelse i realtid](configure-protection-features-microsoft-defender-antivirus.md) , der deaktiveres i nogle tilfælde, når du bruger `SharedSignaturesPath` config (du kan finde flere oplysninger om `SharedSignaturesPath` parameteren under [Set-MpPreference](/powershell/module/defender/set-mppreference))

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details><details>
<summary>Februar-2022 (platform: 4.18.2202.4 | Motor: 1.1.19000.8)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.361.14.0**<br/>
&ensp;Udgivet: **14. marts 2022**<br/>
&ensp;Platform: **4.18.2202.4**<br/>
&ensp;Motor: **1.1.19000.8**<br/>
&ensp;Supportfase: **Sikkerhedsopdateringer og vigtige opdateringer**<br/>

Programversion: 1.1.19000.8 <br/>
Version af sikkerhedsintelligensopdatering: 1.361.14.0 <br/>

### <a name="whats-new"></a>Nyheder

- Forbedringer af registrerings- og funktionsovervågningslogik
- Faste registreringer af falsk positiv udløsende angrebsoverfladereduktion
- Tilføjet rettelse, der resulterer i bedre pålidelighed af beskeder om Slutpunktsregistrering og -svar og avanceret registrering af jagt
- Defender understøtter ikke længere brugerdefinerede meddelelser på toast-pop op-meddelelser. Ændret gruppepolitikobjekt/Intune/SCCM og dokumenter for at afspejle denne ændring.
- Forbedringer til hentning af både oplysninger og kopiering af filer, der er skrevet til et flytbart lager. Du kan få mere at vide [under Microsoft Defender for Endpoint Flytbare Storage Access Control flytbare lagermedier Microsoft Defender for Endpoint](device-control-removable-storage-access-control.md).
- Forbedret trafikoutput, når SmartScreen-tjenesten ikke er tilgængelig 
- Forbedringer af forbindelsen for kunder, der bruger proxyer med godkendelseskrav
- Fast fejl ved opdatering af VDI-enhed for netværksfilshares 
- Slutpunktsregistrering og -svar i bloktilstand understøtter nu detaljeret enhedsmålretning med nye CSP'er. Se [Registrering af slutpunkt og svar (Slutpunktsregistrering og -svar) i blokeringstilstand](edr-in-block-mode.md).

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details><details>
<summary>Januar-2022 (platform: 4.18.2201.10 | Motor: 1.1.18900.2)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.357.8.0**<br/>
&ensp;Udgivet: **9. februar 2022**<br/>
&ensp;Platform: **4.18.2201.10**<br/>
&ensp;Motor: **1.1.18900.2**<br/>
&ensp;Supportfase: **Sikkerhedsopdateringer og vigtige opdateringer**<br/>

Programversion: 1.1.18900.2 <br/>
Version af sikkerhedsintelligensopdatering: 1.357.8.0 <br/>

### <a name="whats-new"></a>Nyheder

- Forbedringer af adfærdsovervågning i filtreringsydeevnen
- Hærdning til TrustedInstaller
- Forbedringer af beskyttelse mod ændring
- Erstattet `ScanScheduleTime` med ny `ScanScheduleOffest` cmdlet i [Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik konfigurerer antallet af minutter efter midnat for at udføre en planlagt scanning.
- Indstillingen er `-ServiceHealthReportInterval` føjet til [Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik konfigurerer tidsintervallet (i minutter) til at udføre en planlagt scanning.
- Indstillingen er `AllowSwitchToAsyncInspection` føjet til [Set-MpPreference](/powershell/module/defender/set-mppreference). Denne politik muliggør en optimering af ydeevnen, der tillader synkront inspicerede netværksflows, at skifte til asynkron inspektion, når de er blevet kontrolleret og valideret.
- Effektivitetsanalyse v2-opdateringer: Understøttelse af Remote PowerShell og PowerShell 7.x er tilføjet. Se [Effektivitetsanalyse for at få Microsoft Defender Antivirus](tune-performance-defender-antivirus.md).
- Løste en potentiel duplikeret pakkefejl i Microsoft Defender Antivirus driver til netværksinspektionssystemet.

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer

<br/><br/>
</details>


### <a name="previous-version-updates-technical-upgrade-support-only"></a>Tidligere versionsopdateringer: Kun teknisk opgraderingssupport

Når en ny pakkeversion er udgivet, reduceres understøttelsen af de to tidligere versioner til kun teknisk support. Versioner, der er ældre end dem, der er angivet i dette afsnit, og som kun er beregnet til teknisk opgraderingssupport.<br/><br/>

<details>
<summary>November-2021 (platform: 4.18.2111.5 | Motor: 1.1.18800.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.355.2.0**<br/>
&ensp;Udgivet: **9. december 2021**<br/>
&ensp;Platform: **4.18.2111.5**<br/>
&ensp;Motor: **1.1.18800.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

Programversion: 1.1.18800.4 Opdateringsversion af sikkerhedsintelligens: 1.355.2.0

### <a name="whats-new"></a>Nyheder

- Forbedret cpu-forbrugseffektivitet i visse intensive scenarier på Exchange servere
- Der er tilføjet nye statusfelter for enhedskontrol under Get-MpComputerStatus i Defender PowerShell-modulet. Du kan få flere oplysninger [under Microsoft Defender for Endpoint Flytbare Storage Access Control til enhedshåndtering](device-control-removable-storage-access-control.md).
- Løste fejl, hvor `SharedSignatureRoot` værdien ikke kunne fjernes, når den er angivet med PowerShell
- Fast fejl, hvor [manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md) ikke blev aktiveret, selvom Microsoft Defender for Endpoint indikerede, at manipulationsbeskyttelse var slået til
- Tilføjet understøttelse og fejlrettelser til effektivitetsanalyse for Microsoft Defender Antivirus værktøj. Du kan få flere oplysninger under [Effektivitetsanalyse for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md).   
   - PowerShell ISE-understøttelse tilføjet til `New-MpPerformanceRecording`
   - Løste fejlfejl for `Get-MpPerformanceReport -TopFilesPerProcess`
   - Fast ydeevne for sessionsfejl ved optagelse af session, når du bruger `New-MpPerformanceRecording` i PowerShell 7.x, fjernsessioner og PowerShell ISE


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Oktober-2021 (platform: 4.18.2110.6 | Motor: 1.1.18700.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.353.3.0**<br/>
&ensp;Udgivet: **28. oktober 2021**<br/>
&ensp;Platform: **4.18.2110.6**<br/>
&ensp;Motor: **1.1.18700.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

Programversion: 1.1.18700.4 Opdateringsversion af sikkerhedsintelligens: 1.353.3.0

### <a name="whats-new"></a>Nyheder

- Forbedringer af FTP-netværkstrafik (File Transfer Protocol)
- Rettelse for at reducere Microsoft Defender CPU-forbruget i Exchange Server, der kører på Windows Server 2016
- Rettelse til scanningsafbrydelser
- Rettelse af beskeder om blokerede manipulationsforsøg, der ikke vises i Security Center
- Forbedringer af robusthed i Microsoft Defender-tjenesten

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> September-2021 (platform: 4.18.2109.6 | Motor: 1.1.18600.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.351.7.0**<br/>
&ensp;Udgivet: **7. oktober 2021**<br/>
&ensp;Platform: **4.18.2109.6**<br/>
&ensp;Motor: **1.1.18600.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

Programversion: 1.1.18600.4 Opdateringsversion af sikkerhedsintelligens: 1.351.7.0

### <a name="whats-new"></a>Nyheder
- Ny forsinkelsesring til Microsoft Defender Antivirus program- og platformopdateringer. Enheder, der tilmelder sig denne ring, modtager opdateringer med en forsinkelse på 48 timer. Den nye forsinkelsesring foreslås kun for kritiske miljøer. Se [Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
- Forbedringer af gradvis udrulningsproces for Microsoft Defender-opdatering

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> August-2021 (platform: 4.18.2108.7 | Motor: 1.1.18500.10)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.349.22.0**<br/>
&ensp;Udgivet: **2. september 2021**<br/>
&ensp;Platform: **4.18.2108.7**<br/>
&ensp;Motor: **1.1.18500.10**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af funktionsovervågningsprogrammet
- Udgivet ny [effektivitetsanalyse til Microsoft Defender Antivirus](tune-performance-defender-antivirus.md)
- Microsoft Defender Antivirus hærdet mod indlæsning af skadelige DLL'er
- Microsoft Defender Antivirus hærdet mod TrustedInstaller-bypass
- Udvidelse af meddelelser om filændring til at omfatte flere data til Human-Operated Ransomware (HumOR)

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Juli-2021 (platform: 4.18.2107.4 | Motor: 1.1.18400.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.345.13.0**<br/>
&ensp;Udgivet: **5. august 2021**<br/>
&ensp;Platform: **4.18.2107.4**<br/>
&ensp;Motor: **1.1.18400.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Understøttelse af enhedskontrol tilføjet for Windows bærbare enheder
- Beskyttelse af potentielt uønskede programmer (PUA) er som standard slået til for forbrugere (se [Potentielt uønskede apps blokeres som standard](https://support.microsoft.com/windows/potentially-unwanted-apps-will-be-blocked-by-default-b9f53cb9-7f1e-40bb-8c6b-a17e0ab6289e))
- Planlagte scanninger for Gruppepolitik objektadministrerede systemer overholder den brugerkonfigurerede scanningstid
- Forbedringer af funktionsovervågningsprogrammet

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer

<br/>
</details><details>
<summary> Juni 2021 (platform: 4.18.2106.5 | Motor: 1.1.18300.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.343.17.0**<br/>
&ensp;Udgivet: **28. juni 2021**<br/>
&ensp;Platform: **4.18.2106.5**<br/>
&ensp;Motor: **1.1.18300.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Nye kontrolelementer til administration af den gradvise udrulningsproces for Microsoft Defender-opdateringer. Se [Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer](manage-gradual-rollout.md).
- Forbedring af funktionsovervågningsprogrammet
- Forbedringer af udrulningen af antimalwaredefinitioner
- Inspektioner af udvidede Edge-netværkshændelser

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Maj-2021 (platform: 4.18.2105.4 | Motor: 1.1.18200.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.341.8.0**<br/>
&ensp;Udgivet: **3. juni 2021**<br/>
&ensp;Platform: **4.18.2105.4**<br/>
&ensp;Motor: **1.1.18200.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af [overvågning af funktionsmåde](client-behavioral-blocking.md)
- Funktion til filtrering af meddelelser [om netværksbeskyttelse](network-protection.md)

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> April-2021 (platform: 4.18.2104.14 | Motor: 1.1.18100.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.337.2.0**<br/>
&ensp;Udgivet: **26. april 2021**  (program: 1.1.18100.6 udgivet 5. maj 2021)<br/>
&ensp;Platform: **4.18.2104.14**<br/>
&ensp;Motor: **1.1.18100.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Mere logik til overvågning af funktionsmåde
- Forbedret registrering af nøglelogger for kernetilstand
- Tilføjede nye kontrolelementer til administration af den gradvise udrulningsproces for [Microsoft Defender-opdateringer](manage-gradual-rollout.md)


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Marts-2021 (platform: 4.18.2103.7 | Motor: 1.1.18000.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.335.36.0**<br/>
&ensp;Udgivet: **2. april 2021**<br/>
&ensp;Platform: **4.18.2103.7**<br/>
&ensp;Motor: **1.1.18000.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedring af funktionsovervågningsprogrammet
- Udvidede angrebsmitigeringer på netværk med gennemtvingning
- Oprettelse af flere mislykkede forsøgshændelser, når [Tamper Protection](prevent-changes-to-security-settings-with-tamper-protection.md) er aktiveret

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Februar-2021 (platform: 4.18.2102.3 | Motor: 1.1.17900.7)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.333.7.0**<br/>
&ensp;Udgivet: **9. marts 2021**<br/>
&ensp;Platform: **4.18.2102.3**<br/>
&ensp;Motor: **1.1.17900.7**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret tjenestegendannelse via [ændringsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md)
- Udvid beskyttelsesomfanget for ændring

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Januar-2021 (platform: 4.18.2101.9 | Motor: 1.1.17800.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.327.1854.0**<br/>
&ensp;Udgivet: **2. februar 2021**<br/>
&ensp;Platform: **4.18.2101.9**<br/>
&ensp;Motor: **1.1.17800.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedringer af Shellcode-registrering af udnyttelse
- Øget synlighed for forsøg på at stjæle legitimationsoplysninger
- Forbedringer af antitamperingsfunktioner i Microsoft Defender Antivirus-tjenester
- Forbedret understøttelse af ARM x64-emulering
- Løsning: Slutpunktsregistrering og -svar blokmeddelelse forbliver i trusselshistorikken, efter at beskyttelsen i realtid har udført indledende registrering

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> November-2020 (platform: 4.18.2011.6 | Motor: 1.1.17700.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.327.1854.0**<br/>
&ensp;Udgivet: **3. december 2020**<br/>
&ensp;Platform: **4.18.2011.6**<br/>
&ensp;Motor: **1.1.17700.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret logføring af [SmartScreen-status](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details><details>
<summary> Oktober-2020 (platform: 4.18.2010.7 | Motor: 1.1.17600.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.327.7.0**<br/>
&ensp;Udgivet: **29. oktober 2020**<br/>
&ensp;Platform: **4.18.2010.7**<br/>
&ensp;Motor: **1.1.17600.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Nye beskrivelser af særlige trusselskategorier
- Forbedrede emuleringsfunktioner
- Forbedrede egenskaber for tillade/blokerede værtsadresser
- Ny indstilling i Defender CSP til Ignorer fletning af lokale brugerudeladelser

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer
<br/>
</details><details>
<summary> September-2020 (platform: 4.18.2009.7 | Motor: 1.1.17500.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.325.10.0**<br/>
&ensp;Udgivet: **1. oktober 2020**<br/>
&ensp;Platform: **4.18.2009.7**<br/>
&ensp;Motor: **1.1.17500.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Der kræves administratortilladelser for at gendanne filer i karantæne
- XML-formaterede hændelser understøttes nu
- Understøttelse af CSP til at ignorere udeladelsesfletninger
- Nye administrationsgrænseflader til:
   - UDP-inspektion
   - Netværksbeskyttelse på Server 2019
   - Udeladelser af IP-adresser i forbindelse med Netværksbeskyttelse
- Forbedret synlighed i TPM-målinger
- Forbedret scanning af VBA-modulet Office

### <a name="known-issues"></a>Kendte problemer

Ingen kendte problemer
<br/>
</details>
<details>
<summary> August-2020 (platform: 4.18.2008.9 | Motor: 1.1.17400.5)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.323.9.0**<br/>
&ensp;Udgivet: **27. august 2020**<br/>
&ensp;Platform: **4.18.2008.9**<br/>
&ensp;Motor: **1.1.17400.5**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Tilføj flere telemetrihændelser
- Forbedret scanningshændelsestelemetri
- Forbedret overvågning af funktionsmåde for hukommelsesscanninger
- Forbedret scanning af makrostrømme
- Føjet `AMRunningMode` til Get-MpComputerStatus PowerShell-cmdlet
- [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) ignoreres. Microsoft Defender Antivirus automatisk slår sig selv fra, når det registrerer et andet antivirusprogram.


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Juli-2020 (platform: 4.18.2007.8 | Motor: 1.1.17300.4)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.321.30.0**<br/>
&ensp;Udgivet: **28. juli 2020**<br/>
&ensp;Platform: **4.18.2007.8**<br/>
&ensp;Motor: **1.1.17300.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret telemetri for BITS
- Forbedret validering af authenticode-kodesigneringscertifikat

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Juni-2020 (platform: 4.18.2006.10 | Motor: 1.1.17200.2)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.319.20.0**<br/>
&ensp;Udgivet: **22. juni 2020**<br/>
&ensp;Platform: **4.18.2006.10**<br/>
&ensp;Motor: **1.1.17200.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Mulighed for at angive [placeringen af supportlogfilerne](./collect-diagnostic-data.md)
- Springer aggressiv catchup-scanning over i passiv tilstand.
- Tillad, at Defender opdateres på forbindelser efter forbrug
- Justering af fast ydeevne, når cachelagring er deaktiveret
- Fast forespørgsel i registreringsdatabasen
- Fast scantime-randomisering i ADMX

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Maj-2020 (platform: 4.18.2005.4 | Motor: 1.1.17100.2)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.317.20.0**<br/>
&ensp;Udgivet: **26. maj 2020**<br/>
&ensp;Platform: **4.18.2005.4**<br/>
&ensp;Motor: **1.1.17100.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Forbedret logføring for scanningshændelser
- Forbedret håndtering af nedbrud i brugertilstand.
- Tilføjet hændelsessporing til beskyttelse mod manipulation
- Fast indsendelse af AMSI-eksempel
- Fast AMSI-skyblokering
- Log over installation af faste sikkerhedsopdatering

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> April-2020 (platform: 4.18.2004.6 | Motor: 1.1.17000.2)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.315.12.0**<br/>
&ensp;Udgivet: **30. april 2020**<br/>
&ensp;Platform: **4.18.2004.6**<br/>
&ensp;Motor: **1.1.17000.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder
- Forbedringer af WDfilter
- Føj flere handlingsbare hændelsesdata til registreringshændelser for reduktion af angrebsoverfladen
- Oplysninger om fast version i diagnosticeringsdata og WMI
- Fast forkert platformversion i brugergrænsefladen efter platformsopdatering
- Dynamisk URL-adresse intel for Filløs trusselsbeskyttelse
- UEFI-scanningsfunktionalitet
- Udvid logføring for opdateringer

### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Marts-2020 (platform: 4.18.2003.8 | Motor: 1.1.16900.2)</summary>

&ensp;Version af sikkerhedsintelligensopdatering: **1.313.8.0**<br/>
&ensp;Udgivet: **24. marts 2020**<br/>
&ensp;Platform: **4.18.2003.8**<br/>
&ensp;Motor: **1.1.16900.4**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Indstillingen CPU-begrænsning er føjet til [MpCmdRun](./command-line-arguments-microsoft-defender-antivirus.md)
- Gør diagnosticeringsfunktionen bedre
- reducer timeout for sikkerhedsintelligens (5 min.)
- Udvid den interne logfunktion i AMSI-programmet
- Gør meddelelse bedre i forbindelse med procesblokering

### <a name="known-issues"></a>Kendte problemer
[**Fast**] Microsoft Defender Antivirus springer filer over, når du kører en scanning.

<br/>
</details>

<details>

<summary> Februar-2020 (platform: – | Motor: 1.1.16800.2)</summary>


&ensp;Version af sikkerhedsintelligensopdatering: **1.311.4.0**<br/>
&ensp;Udgivet: **25. februar 2020**<br/>
&ensp;Platform/klient: **-**<br/>
&ensp;Motor: **1.1.16800.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder


### <a name="known-issues"></a>Kendte problemer
Ingen kendte problemer
<br/>
</details>

<details>
<summary> Januar-2020 (platform: 4.18.2001.10 | Motor: 1.1.16700.2)</summary>


Version af sikkerhedsintelligensopdatering: **1.309.32.0**<br/>
Udgivet: **30. januar 2020**<br/>
Platform/klient: **4.18.2001.10**<br/>
Motor: **1.1.16700.2**<br/>
&ensp;Supportfase: **Teknisk opgraderingssupport (kun)**<br/>

### <a name="whats-new"></a>Nyheder

- Fast BSOD på WS2016 med Exchange
- Supportplatformsopdateringer, når TMP omdirigeres til netværksstien
- Platform- og programversioner føjes til [WDSI](https://www.microsoft.com/en-us/wdsi/defenderupdates) <!-- The preceding URL must include "/en-us" -->
- udvid opdatering af nødsignatur til [passiv tilstand](./microsoft-defender-antivirus-compatibility.md)
- Rettelse 4.18.1911.3 hænger

### <a name="known-issues"></a>Kendte problemer

[**Faste**] enheder, der bruger [moderne standbytilstand](/windows-hardware/design/device-experiences/modern-standby), kan opleve et stop sammen med den Windows Defender filterdriver, der resulterer i et hul i beskyttelsen.  Berørte maskiner ser ud til, at kunden ikke har opdateret til den nyeste antimalwareplatform.
<br/>
> [!IMPORTANT]
> Denne opdatering er:
> - kræves af RS1-enheder, der kører en lavere version af platformen for at understøtte SHA2
> - har et genstartsflag for systemer, der har hængende problemer;
> - udgives igen i april 2020 og erstattes ikke af nyere opdateringer for at sikre, at de bliver tilgængelige i fremtiden.
> - er kategoriseret som en opdatering på grund af kravet om genstart. Og
> - tilbydes kun med [Windows Update](https://support.microsoft.com/help/4027667/windows-10-update).
<br/>
</details>

<details>
<summary> November-2019 (platform: 4.18.1911.3 | Motor: 1.1.16600.7)</summary>

Version af sikkerhedsintelligensopdatering: **1.307.13.0**<br/>
Udgivet: **7. december 2019**<br/>
Platform: **4.18.1911.3**<br/>
Motor: **1.1.17000.7**<br/>
Supportfase: **Ingen support**<br/>

### <a name="whats-new"></a>Nyheder

- Fast sporingsniveau for MpCmdRun
- Oplysninger om fast version af WDFilter
- Gør meddelelser bedre (PUA)
- føj MRT-logge til supportfiler

### <a name="known-issues"></a>Kendte problemer
Når denne opdatering er installeret, skal enheden bruge jumppakken 4.18.2001.10 for at kunne opdatere til den nyeste platformversion.
<br/>
</details>


## <a name="microsoft-defender-antivirus-platform-support"></a>understøttelse af Microsoft Defender Antivirus platform

Platform- og programopdateringer leveres på en månedlig kadence. Hvis du vil have fuld support, skal du holde dig opdateret med de nyeste platformopdateringer. Vores supportstruktur er dynamisk og udvikler sig til to faser afhængigt af tilgængeligheden af den nyeste platformversion:

- **Servicefase for vigtige opdateringer og sikkerhedsopdateringer** – Når du kører den nyeste platformversion, er du berettiget til at modtage både sikkerhedsopdateringer og vigtige opdateringer til platformen til antimalware.

- **Fasen Teknisk support (kun)** – Når en ny platformversion udgives, reduceres understøttelsen af ældre versioner (N-2) til kun teknisk support. Platformversioner, der er ældre end N-2, understøttes ikke længere.*

\*Der ydes fortsat teknisk support til opgraderinger fra Windows 10 version (se [Platformversion, der følger med Windows 10 versioner](#platform-version-included-with-windows-10-releases)) til den nyeste platformversion.

Under fasen med teknisk support (kun) leveres kommercielt rimelige supporthændelser via Microsoft Customer Service & Support og Microsofts administrerede supporttilbud (f.eks. Premier Support). Hvis en supporthændelse kræver eskalering til udvikling for yderligere vejledning, kræver en ikke-sikkerhedsrelateret opdatering eller kræver en sikkerhedsopdatering, bliver kunderne bedt om at opgradere til den nyeste platformversion eller en mellemliggende opdatering (*).

> [!NOTE]
> Hvis du installerer Microsoft Defender Antivirus platformsopdatering manuelt, eller hvis du bruger et script eller et ikke-Microsoft-administrationsprodukt til at installere Microsoft Defender Antivirus Platform Update, skal du sørge for, at versionen `4.18.2001.10` er installeret fra [Microsoft Update-kataloget](https://www.catalog.update.microsoft.com/Search.aspx?q=4.18.2001.10), før den nyeste version af Platform Update (N-2) er installeret.

### <a name="platform-version-included-with-windows-10-releases"></a>Platformversion, der er inkluderet i Windows 10 udgivelser

Nedenstående tabel indeholder de Microsoft Defender Antivirus platform- og programversioner, der leveres med de nyeste Windows 10 versioner:<br/><br/>

|Windows 10 version  |Platformversion  |Programversion |Supportfase |
|:---|:---|:---|:---|
|2004 (20H1/20H2) |4.18.1909.6 |1.1.17000.2 | Teknisk opgraderingssupport (kun) |
|1909 (19H2) |4.18.1902.5 |1.1.16700.3 | Teknisk opgraderingssupport (kun) |
|1903 (19H1) |4.18.1902.5 |1.1.15600.4 | Teknisk opgraderingssupport (kun) |
|1809 (RS5) |4.18.1807.18075 |1.1.15000.2 | Teknisk opgraderingssupport (kun) |
|1803 (RS4) |4.13.17134.1 |1.1.14600.4 | Teknisk opgraderingssupport (kun) |
|1709 (RS3) |4.12.16299.15 |1.1.14104.0 | Teknisk opgraderingssupport (kun) |
|1703 (RS2) |4.11.15603.2 |1.1.13504.0 | Teknisk opgraderingssupport (kun) |
|1607 (RS1) |4.10.14393.3683 |1.1.12805.0 | Teknisk opgraderingssupport (kun) |

Du kan få Windows 10 udgivelsesoplysninger i [faktaarket for Windows livscyklus](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

## <a name="updates-for-deployment-image-servicing-and-management-dism"></a>Opdateringer til DISM (Deployment Image Servicing and Management)

Vi anbefaler, at du opdaterer dine Windows 10 (Enterprise-, Pro- og Home-udgaver), Windows Server 2019, Windows Server 2022 og Windows Server 2016 OS-installationsafbildninger med de nyeste antivirus- og antimalwareopdateringer. Hvis du holder afbildningerne af operativsystemet opdateret, undgår du et hul i beskyttelsen.

Du kan få flere oplysninger under [Microsoft Defender-opdatering til Windows afbildninger af operativsystemet](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images).

<details>
<summary>20220321.1</summary>

&ensp;Pakkeversion: **20220321.1**<br/>
&ensp;Platformversion: **4.18.2202.4**<br/>
&ensp;Programversion: **1.1.19000.8**<br/>
&ensp;Signaturversion: **1.351.337.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Ingen

<br/>
</details><details>
<summary>20220305.1</summary>

&ensp;Pakkeversion: **20220305.1**<br/>
&ensp;Platformversion: **4.18.2201.10**<br/>
&ensp;Programversion: **1.1.18900.3**<br/>
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
&ensp;Programversion: **1.1.18900.2**<br/>
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
&ensp;Programversion: **1.1.18800.4**<br/>
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
&ensp;Programversion: **1.1.18700.4**<br/>
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
&ensp;Programversion: **1.1.18700.4**<br/>
&ensp;Signaturversion: **1.353.613.0**<br/>

### <a name="fixes"></a>Rettelser
- Løste et problem, der vedrører lokaliseringsfiler

### <a name="additional-information"></a>Flere oplysninger:
- Ingen
<br/>
</details><details>
<summary>1.1.2110.01</summary>

&ensp;Pakkeversion: **1.1.2110.01**<br/>
&ensp;Platformversion: **4.18.2109.6**<br/>
&ensp;Programversion: **1.1.18500.10**<br/>
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
&ensp;Programversion: **1.1.18400.5**<br/>
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
&ensp;Programversion: **1.1.18300.4**<br/>
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
&ensp;Programversion: **1.1.18300.4**<br/>
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
&ensp;Programversion: **1.1.18100.6**<br/>
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
&ensp;Programversion: **1.1.18100.6**<br/>
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
&ensp;Programversion: **1.1.18000.5**<br/>
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
&ensp;Programversion: **1.1.17800.5**<br/>
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
&ensp;Programversion: **1.1.17800.5**<br/>
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
&ensp;Motorversion: **1.1.17700.4**<br/>
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
&ensp;Programversion: **1.1.17600.5**<br/>
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
&ensp;Programversion: **1.1.17600.5**<br/>
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
&ensp;Programversion: **1.1.17600.5**<br/>
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
&ensp;Programversion: **1.1.17400.5**<br/>
&ensp;Signaturversion: **1.327.2216.0**<br/>

### <a name="fixes"></a>Rettelser
- Ingen

### <a name="additional-information"></a>Flere oplysninger:
- Tilføjede understøttelse af Windows 10 RS1- eller nyere operativsysteminstallationsafbildninger.
<br/>
</details>

## <a name="more-resources"></a>Flere ressourcer

| Artikel | Beskrivelse  |
|:---|:---|
|[Microsoft Defender-opdatering til installationsafbildninger af Windows operativsystem](https://support.microsoft.com/help/4568292/defender-update-for-windows-operating-system-installation-images)  | Gennemse antimalware-opdateringspakker for dine afbildninger af operativsystemet (WIM- og VHD-filer). Hent Microsoft Defender Antivirus opdateringer til Windows 10 (Enterprise-, Pro- og Home-udgaver), Windows Server 2019, Windows Server 2022 og installationsafbildninger af Windows Server 2016.  |
|[Administrer, hvordan beskyttelsesopdateringer downloades og anvendes](manage-protection-updates-microsoft-defender-antivirus.md) | Beskyttelsesopdateringer kan leveres via mange kilder. |
|[Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md) | Du kan planlægge, hvornår beskyttelsesopdateringer skal downloades. |
|[Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md) | Hvis et slutpunkt går glip af en opdatering eller planlagt scanning, kan du gennemtvinge en opdatering eller scanning, næste gang en bruger logger på. |
|[Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md) | Du kan angive, at beskyttelsesopdateringer skal downloades ved start eller efter visse skybaserede beskyttelseshændelser. |
|[Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)| Du kan angive indstillinger, f.eks. om opdateringer skal forekomme på batteristrøm, som især er nyttige til mobilenheder og virtuelle maskiner. |
| [Microsoft Defender for Endpoint opdatering til Slutpunktsregistrering og -svar sensor](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) | Du kan opdatere den Slutpunktsregistrering og -svar sensor (MsSense.exe), der er inkluderet i den nye Microsoft Defender for Endpoint samlede løsningspakke, der blev udgivet i 2021.   |

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
