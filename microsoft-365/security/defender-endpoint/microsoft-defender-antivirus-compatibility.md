---
title: Microsoft Defender Antivirus-kompatibilitet med andre sikkerhedsprodukter
description: Få mere at vide om Microsoft Defender Antivirus med andre sikkerhedsprodukter og operativsystemer.
keywords: windows defender, defender for endpoint, next-generation, antivirus, kompatibilitet, passiv tilstand
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: d3b6cee3212ea7d98782a9e073343321c31c8990
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750314"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Antivirus-kompatibilitet med andre sikkerhedsprodukter

**Gælder for:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platforme**
- Windows

Microsoft Defender Antivirus installeres automatisk på slutpunkter, der kører følgende versioner af Windows:

- Windows 10 eller nyere
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 eller nyere
- Windows Server 2016

Hvad sker der, når der bruges en anden ikke-Microsoft-antivirus-/antimalwareløsning? Kan du køre Microsoft Defender Antivirus sammen med et andet antivirusprogram? Svarene afhænger af flere faktorer, f.eks. dit operativsystem, og om du bruger [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) sammen med din antivirusbeskyttelse.

I denne artikel beskrives det, hvad der sker med Microsoft Defender Antivirus og en ikke-Microsoft-antivirus-/antimalwareløsning med og uden Defender for Endpoint.

> [!IMPORTANT]
> - Microsoft Defender Antivirus er tilgængelig på enheder, der kører Windows 10 og 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 eller nyere og Windows Server 2016. 
> - Microsoft Defender Antivirus er også tilgængelig på Windows Server 2012 R2, når de onboardes ved hjælp af den [moderne, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - På Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), som administreres via Microsoft Endpoint Configuration Manager.
> - Windows Defender tilbydes også til [forbrugerenheder på Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), selvom Windows Defender ikke leverer administration på virksomhedsniveau.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Antivirusbeskyttelse uden Defender for Endpoint

I dette afsnit beskrives det, hvad der sker, når du bruger Microsoft Defender Antivirus sammen med ikke-Microsoft-antivirus-/antimalwareprodukter på slutpunkter, der ikke er onboardet til Defender for Endpoint. 

> [!NOTE]
> Microsoft Defender Antivirus kører generelt ikke i passiv tilstand på enheder, der ikke er onboardet til Defender for Endpoint.

I følgende tabel opsummeres det, hvad du kan forvente:

|Windows-version|Primær antivirus-/antimalwareløsning|Microsoft Defender Antivirus-tilstand|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Microsoft Defender Antivirus|Aktiv tilstand|
|Windows 10 <br/> Windows 11|En ikke-Microsoft-antivirus-/antimalwareløsning|Deaktiveret tilstand (sker automatisk)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 eller nyere <br/> Windows Server 2016 <br/> Windows Server 2012 R2 |Microsoft Defender Antivirus|Aktiv tilstand|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 eller nyere <br/> Windows Server 2016 |En ikke-Microsoft-antivirus-/antimalwareløsning|Deaktiveret (indstillet manuelt) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Hvis du kører et antivirusprogram, der ikke er fra Microsoft, på Windows Server, kan du fjerne Microsoft Defender Antivirus for at forhindre konflikt. Hvis enheden er onboardet til Microsoft Defender for Endpoint, kan du bruge Microsoft Defender Antivirus i passiv tilstand (se nedenfor).

> [!TIP]
> På Windows Server 2016 kan du muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender Antivirus- og ikke-Microsoft-antivirus-/antimalwareløsninger

> [!NOTE]
> Microsoft Defender Antivirus kan generelt kun angives til passiv tilstand på slutpunkter, der er onboardet til Defender for Endpoint.

Om Microsoft Defender Antivirus kører i aktiv tilstand, passiv tilstand eller deaktiveres, afhænger af flere faktorer, f.eks.:

- Hvilken version af Windows der er installeret på et slutpunkt
- Om Microsoft Defender Antivirus er den primære antivirus-/antimalwareløsning på slutpunktet
- Angiver, om slutpunktet er onboardet til Defender for Endpoint

I følgende tabel opsummeres tilstanden for Microsoft Defender Antivirus i flere scenarier. 

| Windows-version   | Antivirus-/antimalwareløsning  | Onboardet til <br/> Defender for Endpoint? | Microsoft Defender Antivirus-tilstand     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Microsoft Defender Antivirus | Ja  | Aktiv tilstand | 
| Windows 10 <br/> Windows 11 | Microsoft Defender Antivirus | Nej   | Aktiv tilstand |
| Windows 10 <br/> Windows 11  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja  | Passiv tilstand (automatisk) |
| Windows 10 <br/> Windows 11  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej   | Deaktiveret tilstand (automatisk)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 eller nyere  | Microsoft Defender Antivirus  | Ja |         Aktiv tilstand  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 eller nyere   | Microsoft Defender Antivirus | Nej  | Aktiv tilstand |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja  | Microsoft Defender Antivirus skal være indstillet til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej  | Microsoft Defender Antivirus skal være deaktiveret (manuelt) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Microsoft Defender Antivirus | Ja | Aktiv tilstand |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft Defender Antivirus | Nej | Aktiv tilstand |
| Windows Server 2016 <br/> Windows Server 2012 R2  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja | Microsoft Defender Antivirus skal være indstillet til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej | Microsoft Defender Antivirus skal være deaktiveret (manuelt) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) På Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 eller Windows Server 2012 R2 går Microsoft Defender Antivirus ikke automatisk i passiv tilstand, når du installerer et antivirusprodukt, der ikke er fra Microsoft. I disse tilfælde skal du indstille Microsoft Defender Antivirus til passiv tilstand for at forhindre problemer, der skyldes, at flere antivirusprogrammer er installeret på en server. Du kan angive Microsoft Defender Antivirus til passiv tilstand ved hjælp af en registreringsdatabasenøgle på følgende måde:
- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Navn: `ForceDefenderPassiveMode`
- Type: `REG_DWORD`
- Værdi: `1`

 > [!NOTE]
 > Hvis passiv tilstand skal fungere på slutpunkter, der kører Windows Server 2016 og Windows Server 2012 R2, skal disse slutpunkter onboardes med den moderne, samlede løsning, der er beskrevet i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) På Windows Server 2016, Windows Server 2012 R2, Windows Server version 1803 eller nyere, Windows Server 2019 og Windows Server 2022, hvis du bruger et antivirusprodukt, der ikke er fra Microsoft, på et slutpunkt, der *ikke* er onboardet til Microsoft Defender for Endpoint, skal du deaktivere/fjerne Microsoft Defender Antivirus manuelt for at forhindre problemer, der skyldes, at flere antivirusprodukter er installeret på en server.

> [!TIP]
> På Windows Server 2016 kan du muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus*.

Defender for Endpoint indeholder funktioner, der yderligere udvider den antivirusbeskyttelse, der er installeret på dit slutpunkt. Du kan drage fordel af at køre Microsoft Defender Antivirus sammen med en anden antivirusløsning.

[EDR (Endpoint Detection and Response) i blokeringstilstand](edr-in-block-mode.md) giver f.eks. ekstra beskyttelse mod skadelige artefakter, selvom Microsoft Defender Antivirus ikke er det primære antivirusprodukt. Sådanne funktioner kræver, at Microsoft Defender Antivirus installeres og kører i passiv tilstand eller aktiv tilstand.

## <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Krav til Microsoft Defender Antivirus om at køre i passiv tilstand

Slutpunkter skal opfylde følgende krav, før Microsoft Defender Antivirus kan køre i passiv tilstand:

- Operativsystem: Windows 10 eller nyere; Windows Server 2022, Windows Server 2019 eller Windows Server, version 1803 eller nyere
- Microsoft Defender Antivirus skal installeres
- Et andet antivirus-/antimalwareprodukt, der ikke er fra Microsoft, skal installeres og bruges som den primære antivirusløsning
- Slutpunkter skal være onboardet til Defender for Endpoint

> [!IMPORTANT]
> - Microsoft Defender Antivirus er kun tilgængelig på enheder, der kører Windows 10 og 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 og Windows Server 2012 R2.
> - I Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), som administreres via Microsoft Endpoint Configuration Manager.
> - Windows Defender tilbydes også til [forbrugerenheder på Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), selvom Windows Defender ikke leverer administration på virksomhedsniveau.

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Sådan påvirker Microsoft Defender Antivirus Defender for Endpoint-funktionaliteten

Defender for Endpoint påvirker, om Microsoft Defender Antivirus kan køre i passiv tilstand. Og tilstanden for Microsoft Defender Antivirus kan påvirke visse funktioner i Defender for Endpoint. Beskyttelse i realtid fungerer f.eks. når Microsoft Defender Antivirus er i aktiv eller passiv tilstand, men ikke når Microsoft Defender Antivirus er deaktiveret eller fjernet.

> [!IMPORTANT]
> - Tabellen i dette afsnit opsummerer de funktioner og funktioner, der fungerer aktivt eller ej, afhængigt af om Microsoft Defender Antivirus er i aktiv tilstand, passiv tilstand eller deaktiveret/fjernet. Denne tabel er udviklet til kun at være til orientering.   
> - **Deaktiver ikke funktioner**, f.eks. beskyttelse i realtid, skybaseret beskyttelse eller begrænset periodisk scanning, hvis du bruger Microsoft Defender Antivirus i passiv tilstand, eller hvis du bruger [EDR i bloktilstand](edr-in-block-mode.md), som arbejder bag kulisserne for at registrere og afhjælpe skadelige artefakter, der blev registreret efter sikkerhedsbrud.

| Beskyttelse | Microsoft Defender Antivirus <br/>(*Aktiv tilstand*) | Microsoft Defender Antivirus <br/>(*Passiv tilstand*) | Microsoft Defender Antivirus <br/>(*Deaktiveret eller fjernet*) | [EDR i bloktilstand](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) | Ja | Se note <sup>[[4](#fn4)]</sup> | Nej | Nej | 
| [Skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) | Ja | Nej  | Nej | Nej | 
| [Netværksbeskyttelse](network-protection.md)  | Ja | Nej | Nej | Nej | 
| [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md)  | Ja | Nej | Nej  | Nej | 
| [Begrænset tilgængelighed af periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md) | Nej | Nej | Ja | Nej | 
| [Oplysninger om filscanning og registrering](review-scan-results-microsoft-defender-antivirus.md) | Ja | Ja <sup>[[5](#fn5)]</sup> | Nej | Ja | 
| [Trusselsafhjælpning](configure-remediation-microsoft-defender-antivirus.md) | Ja | Se note <sup>[[6](#fn6)]</sup> | Nej | Ja | 
| [Opdateringer til sikkerhedsintelligens](manage-updates-baselines-microsoft-defender-antivirus.md) | Ja | Ja <sup>[[7](#fn7)]</sup> | Nej | Ja <sup>[[7](#fn7)]</sup> | 
| [Forebyggelse af datatab](../../compliance/endpoint-dlp-learn-about.md) | Ja | Ja | Nej | Nej |
| [Styret mappeadgang](controlled-folders.md) | Ja |Nej | Nej | Nej |
| [Filtrering af webindhold](web-content-filtering.md) | Ja | Se note <sup>[[8](#fn8)]</sup> | Nej | Nej |
| [Enhedsstyring](device-control-report.md) | Ja | Ja | Nej | Nej |
| [PUA-beskyttelse](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Ja | Nej | Nej | Nej |

(<a id="fn4">4</a>) Når Microsoft Defender Antivirus er i passiv tilstand, giver beskyttelse i realtid ikke nogen blokering eller håndhævelse, selvom den er aktiveret og i passiv tilstand.

(<a id="fn5">5</a>) Når Microsoft Defender Antivirus er i passiv tilstand, er scanninger ikke planlagt.

(<a id="fn6">6</a>) Når Microsoft Defender Antivirus er i passiv tilstand, afhjælper den ikke trusler. Trusler kan dog afhjælpes ved hjælp af [EDR (Endpoint Detection and Response) i bloktilstand](edr-in-block-mode.md). I dette tilfælde kan du få vist beskeder, der viser Microsoft Defender Antivirus som en kilde, selvom Microsoft Defender Antivirus er i passiv tilstand.

(<a id="fn7">7</a>) Opdateringsrytmen for sikkerhedsintelligens styres kun af Windows Update indstillinger. Defender-specifikke indstillinger for opdateringsplaner (dagligt/ugentligt på bestemt tidspunkt, intervalbaserede) fungerer kun, når Microsoft Defender Antivirus er i aktiv tilstand. De ignoreres i passiv tilstand.

(<a id="fn8">8</a>) Når Microsoft Defender Antivirus er i passiv tilstand, fungerer filtrering af webindhold kun med Microsoft Edge-browseren. 

> [!IMPORTANT]
> - [Beskyttelse mod datatab for slutpunkter](/microsoft-365/compliance/endpoint-dlp-learn-about) fungerer fortsat normalt, når Microsoft Defender Antivirus er i enten aktiv eller passiv tilstand.
>
> - Deaktiver, stop eller rediger ikke nogen af de tilknyttede tjenester, der bruges af Microsoft Defender Antivirus, Defender for Endpoint eller Windows Sikkerhed-appen. Denne anbefaling omfatter *tjenesterne wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* eller *MsMpEng* . Manuel ændring af disse tjenester kan medføre alvorlig ustabilitet på dine enheder og kan gøre dit netværk sårbart. Deaktivering, standsning eller ændring af disse tjenester kan også medføre problemer, når du bruger antivirusløsninger, der ikke er Fra Microsoft, og hvordan deres oplysninger vises i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).
>
> - I Defender for Endpoint kan du slå EDR til i blokeringstilstand, selvom Microsoft Defender Antivirus ikke er din primære antivirusløsning. EDR i blokeringstilstand registrerer og afhjælper skadelige elementer, der findes på enheden (efter sikkerhedsbrud). Du kan få mere at vide [under EDR i bloktilstand](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Sådan bekræfter du tilstanden for Microsoft Defender Antivirus

Du kan bruge en af flere metoder til at bekræfte tilstanden af Microsoft Defender Antivirus:

### <a name="use-the-windows-security-app"></a>Brug appen Windows Sikkerhed

1. Åbn appen Windows Sikkerhed på en Windows-enhed.

2. Vælg **Virus- og trusselsbeskyttelse**.

3. Under **Hvem beskytter mig?** skal du vælge **Administrer udbydere**.

4. På siden **Sikkerhedsudbydere** under **Antivirus** kan du se, at **Microsoft Defender Antivirus er slået til**.

### <a name="use-task-manager"></a>Brug Jobliste

1. Åbn appen Jobliste på en Windows-enhed.

2. Vælg fanen **Detaljer** .

3. Søg efter **MsMpEng.exe** på listen.

### <a name="use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running"></a>Brug Windows PowerShell til at bekræfte, at Microsoft Defender Antivirus kører

> [!NOTE]
> Brug kun denne procedure til at bekræfte, om Microsoft Defender Antirivus kører på et slutpunkt.

1. Åbn Windows PowerShell på en Windows-enhed. 

2. Kør følgende PowerShell-cmdlet: `Get-Process`.

3. Gennemse resultaterne. Du bør kunne se **MsMpEng.exe** , om Microsoft Defender Antivirus er aktiveret.

### <a name="use-windows-powershell-to-confirm-that-antivirus-protection-is-running"></a>Brug Windows PowerShell til at bekræfte, at antivirusbeskyttelsen kører

> [!NOTE]
> Brug kun denne procedure til at bekræfte, om antivirusbeskyttelse er aktiveret på et slutpunkt.

1. Åbn Windows PowerShell på en Windows-enhed.

2. Kør følgende PowerShell-cmdlet: `Get-MpComputerStatus | select AMRunningMode`.

3. Gennemse resultaterne. Du bør kunne se **Normal**, **Passiv** eller **EDR-blokeringstilstand** , hvis antivirusbeskyttelse er aktiveret på slutpunktet. 

> [!NOTE]
> Bemærk, at denne procedure kun bruges til at bekræfte, om antivirusbeskyttelse er aktiveret på et slutpunkt.

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Flere oplysninger om tilstande for Microsoft Defender Antivirus

I følgende afsnit beskrives det, hvad du kan forvente, når Microsoft Defender Antivirus er:

- [I aktiv tilstand](#active-mode)
- [I passiv tilstand, eller når EDR i bloktilstand er slået til](#passive-mode-or-edr-block-mode)
- [Deaktiveret eller fjernet](#disabled-or-uninstalled)

### <a name="active-mode"></a>Aktiv tilstand

I aktiv tilstand bruges Microsoft Defender Antivirus som antivirusappen på computeren. Indstillinger, der konfigureres ved hjælp af Configuration Manager, Gruppepolitik, Microsoft Intune eller andre administrationsprodukter, gælder. Filer scannes, trusler afhjælpes, og registreringsoplysninger rapporteres i dit konfigurationsværktøj (f.eks. i Microsoft Endpoint Manager Administration eller Microsoft Defender Antivirus-appen på slutpunktet).  

### <a name="passive-mode-or-edr-block-mode"></a>Passiv tilstand eller EDR-blokeringstilstand

I passiv tilstand bruges Microsoft Defender Antivirus ikke som antivirusapp, og trusler afhjælpes *ikke* af Microsoft Defender Antivirus. Trusler kan dog afhjælpes ved hjælp af [EDR (Endpoint Detection and Response) i bloktilstand](edr-in-block-mode.md). Filer scannes af EDR, og rapporter leveres til trusselsregistreringer, der deles med Defender for Endpoint-tjenesten. Du får muligvis vist beskeder, der viser Microsoft Defender Antivirus som en kilde, selvom Microsoft Defender Antivirus er i passiv tilstand. 

Når Microsoft Defender Antivirus er i passiv tilstand, kan du stadig [administrere opdateringer til Microsoft Defender Antivirus](manage-updates-baselines-microsoft-defender-antivirus.md). Du kan dog ikke flytte Microsoft Defender Antivirus til aktiv tilstand, hvis dine enheder har et antivirusprogram, der ikke er fra Microsoft, og som yder beskyttelse mod malware i realtid.

**Sørg for at hente dine antivirus- og antimalwareopdateringer, selvom Microsoft Defender Antivirus kører i passiv tilstand**. Se [Administrer Opdateringer til Microsoft Defender Antivirus, og anvend grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).<br/><br/>Bemærk, at passiv tilstand kun understøttes på Windows Server 2012 R2 & 2016, når maskinen er onboardet ved hjælp af den [moderne, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints). 

### <a name="disabled-or-uninstalled"></a>Deaktiveret eller fjernet

Når Microsoft Defender Antivirus er deaktiveret eller fjernet, bruges den ikke som antivirusapp. Filer scannes ikke, og trusler afhjælpes ikke. Det anbefales ikke generelt at deaktivere eller fjerne Microsoft Defender Antivirus. Hvis det er muligt, skal du holde Microsoft Defender Antivirus i passiv tilstand, hvis du bruger en ikke-Microsoft-antimalware-/antivirusløsning.

I de tilfælde, hvor Microsoft Defender Antivirus deaktiveres automatisk, kan det aktiveres igen automatisk, hvis det ikke-Microsoft-antivirus-/antimalwareprodukt udløber, fjernes eller på anden måde stopper med at yde beskyttelse i realtid mod virus, malware eller andre trusler. Den automatiske genaktivering af Microsoft Defender Antivirus hjælper med at sikre, at antivirusbeskyttelsen vedligeholdes på dine slutpunkter.

Du kan også bruge [begrænset periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md), som fungerer sammen med Microsoft Defender Antivirus-programmet til jævnligt at kontrollere, om der er trusler, hvis du bruger en antivirusapp, der ikke er fra Microsoft.  | 

## <a name="what-about-non-windows-devices"></a>Hvad med ikke-Windows-enheder?

 Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:

- [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
- [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
- [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
- [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
- [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
- [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus på Windows-klienter](microsoft-defender-antivirus-in-windows-10.md)
- [EDR i bloktilstand](edr-in-block-mode.md)
- [Få mere at vide om forebyggelse af datatab ved slutpunkt](/microsoft-365/compliance/endpoint-dlp-learn-about)
