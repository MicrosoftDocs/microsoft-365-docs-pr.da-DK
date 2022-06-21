---
title: Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter
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
ms.openlocfilehash: c0fdf84ec4883921a8e12b2a0638be66a393f725
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185497"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter

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
> - Microsoft Defender Antivirus fås også på Windows Server 2012 R2, når den onboardes ved hjælp af den [moderne, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - På Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), som administreres via Microsoft Endpoint Configuration Manager.
> - Windows Defender tilbydes også til [forbrugerenheder på Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), selvom Windows Defender ikke leverer administration på virksomhedsniveau.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Antivirusbeskyttelse uden Defender for Endpoint

I dette afsnit beskrives det, hvad der sker, når du bruger Microsoft Defender Antivirus sammen med ikke-Microsoft-antivirus-/antimalwareprodukter på slutpunkter, der ikke er onboardet til Defender for Endpoint. 

> [!NOTE]
> Generelt kører Microsoft Defender Antivirus ikke i passiv tilstand på enheder, der ikke er onboardet til Defender for Endpoint.

I følgende tabel opsummeres det, hvad du kan forvente:

|Windows version|Primær antivirus-/antimalwareløsning|Microsoft Defender Antivirus tilstand|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Microsoft Defender Antivirus|Aktiv tilstand|
|Windows 10 <br/> Windows 11|En ikke-Microsoft-antivirus-/antimalwareløsning|Deaktiveret tilstand (sker automatisk)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 eller nyere <br/> Windows Server 2016 <br/> Windows Server 2012 R2 |Microsoft Defender Antivirus|Aktiv tilstand|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 eller nyere <br/> Windows Server 2016 |En ikke-Microsoft-antivirus-/antimalwareløsning|Deaktiveret (indstillet manuelt) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Hvis du kører et antivirusprogram, der ikke er fra Microsoft, på Windows Server, kan du fjerne Microsoft Defender Antivirus for at forhindre konflikt. Hvis enheden er onboardet til Microsoft Defender for Endpoint, kan du bruge Microsoft Defender Antivirus i passiv tilstand (se nedenfor).

> [!TIP]
> På Windows Server 2016 kan du muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender Antivirus og ikke-Microsoft-antivirus-/antimalwareløsninger

> [!NOTE]
> Generelt kan Microsoft Defender Antivirus kun angives til passiv tilstand på slutpunkter, der er onboardet til Defender for Endpoint.

Om Microsoft Defender Antivirus kører i aktiv tilstand, passiv tilstand eller deaktiveres, afhænger af flere faktorer, f.eks.:

- Hvilken version af Windows der er installeret på et slutpunkt
- Om Microsoft Defender Antivirus er den primære antivirus-/antimalwareløsning på slutpunktet
- Angiver, om slutpunktet er onboardet til Defender for Endpoint

I følgende tabel opsummeres tilstanden for Microsoft Defender Antivirus i flere scenarier. 

| Windows version   | Antivirus-/antimalwareløsning  | Onboardet til <br/> Defender for Endpoint? | Microsoft Defender Antivirus tilstand     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Microsoft Defender Antivirus | Ja  | Aktiv tilstand | 
| Windows 10 <br/> Windows 11 | Microsoft Defender Antivirus | Nej   | Aktiv tilstand |
| Windows 10 <br/> Windows 11  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja  | Passiv tilstand (automatisk) |
| Windows 10 <br/> Windows 11  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej   | Deaktiveret tilstand (automatisk)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 eller nyere  | Microsoft Defender Antivirus  | Ja |         Aktiv tilstand  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 eller nyere   | Microsoft Defender Antivirus | Nej  | Aktiv tilstand |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja  | Microsoft Defender Antivirus skal angives til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej  | Microsoft Defender Antivirus skal deaktiveres (manuelt) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Microsoft Defender Antivirus | Ja | Aktiv tilstand |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft Defender Antivirus | Nej | Aktiv tilstand |
| Windows Server 2016 <br/> Windows Server 2012 R2  | En ikke-Microsoft-antivirus-/antimalwareløsning | Ja | Microsoft Defender Antivirus skal angives til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | En ikke-Microsoft-antivirus-/antimalwareløsning | Nej | Microsoft Defender Antivirus skal deaktiveres (manuelt) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) På Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 eller Windows Server 2012 R2 går Microsoft Defender Antivirus ikke automatisk i passiv tilstand, når du installerer et antivirusprodukt, der ikke er fra Microsoft. I disse tilfælde skal du angive Microsoft Defender Antivirus til passiv tilstand for at forhindre problemer, der skyldes, at flere antivirusprogrammer er installeret på en server. Du kan angive Microsoft Defender Antivirus til passiv tilstand ved hjælp af PowerShell, Gruppepolitik eller en registreringsdatabasenøgle. 

**Metode til registreringsdatabasenøgle**

  Du kan angive Microsoft Defender Antivirus til passiv tilstand ved at angive følgende registreringsdatabasenøgle:
- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Navn: `ForceDefenderPassiveMode`
- Type: `REG_DWORD`
- Værdi: `1`

**GPO-metode**

1. Åbn Gruppepolitik Administrationseditor > **Computerkonfiguration** > **Administrative skabeloner** >  **Windows komponenter** >  **Microsoft Defender Antivirus**.

2. Vælg **Slå Microsoft Defender Antivirus fra**.

3.  Angiv gruppepolitikobjektet til **Aktiveret**.

Du kan få vist din beskyttelsesstatus i PowerShell ved hjælp af kommandoen [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) og nøglen `AMRunningMode`. Her er et eksempel på, hvordan outputtet ser ud:

```
PS C:\Users\contoso> Get-MpComputerStatus


AMEngineVersion                  : 0.0.0.0
AMProductVersion                 : 4.18.2205.4
AMRunningMode                    : Not running
AMServiceEnabled                 : False
AMServiceVersion                 : 0.0.0.0
AntispywareEnabled               : False
AntispywareSignatureAge          : 4294967295
AntispywareSignatureLastUpdated  :
AntispywareSignatureVersion      : 0.0.0.0
AntivirusEnabled                 : False
AntivirusSignatureAge            : 4294967295
AntivirusSignatureLastUpdated    :
AntivirusSignatureVersion        : 0.0.0.0
BehaviorMonitorEnabled           : False
ComputerID                       : 5CF99D95-BF09-4B2E-9911-8E01C55642E5
ComputerState                    : 0
DefenderSignaturesOutOfDate      : False
DeviceControlDefaultEnforcement  : N/A
DeviceControlPoliciesLastUpdated : 01/01/1601 00:00:00
DeviceControlState               : N/A
FullScanAge                      : 4294967295
FullScanEndTime                  :
FullScanOverdue                  : False
FullScanRequired                 : False
FullScanSignatureVersion         :
FullScanStartTime                :
IoavProtectionEnabled            : False
IsTamperProtected                : False
IsVirtualMachine                 : True
LastFullScanSource               : 0
LastQuickScanSource              : 0
NISEnabled                       : False
NISEngineVersion                 : 0.0.0.0
NISSignatureAge                  : 4294967295
NISSignatureLastUpdated          :
NISSignatureVersion              : 0.0.0.0
OnAccessProtectionEnabled        : False
ProductStatus                    : 1
QuickScanAge                     : 4294967295
QuickScanEndTime                 :
QuickScanOverdue                 : False
QuickScanSignatureVersion        :
QuickScanStartTime               :
RealTimeProtectionEnabled        : False
RealTimeScanDirection            : 0
RebootRequired                   : False
TamperProtectionSource           : Signatures
TDTMode                          : N/A
TDTStatus                        : N/A
TDTTelemetry                     : N/A
TroubleShootingDailyMaxQuota     :
TroubleShootingDailyQuotaLeft    :
TroubleShootingEndTime           :
TroubleShootingExpirationLeft    :
TroubleShootingMode              :
TroubleShootingModeSource        :
TroubleShootingQuotaResetTime    :
TroubleShootingStartTime         :
PSComputerName                   :
```

I det foregående eksempel kører **Defender-status ikke**.

 > [!NOTE]
 > Hvis passiv tilstand skal fungere på slutpunkter, der kører Windows Server 2016 og Windows Server 2012 R2, skal disse slutpunkter onboardes med den moderne, samlede løsning, der er beskrevet i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) På Windows Server 2016 Windows Server 2012 R2, Windows Server version 1803 eller nyere, Windows Server 2019 og Windows Server 2022, hvis du bruger et antivirusprodukt, der ikke er Microsoft, på et slutpunkt, der *ikke* er onboardet til Microsoft Defender for Endpoint, skal du deaktivere/fjerne Microsoft Defender Antivirus manuelt for at forhindre problemer, der skyldes, at flere antivirusprogrammer er installeret på en server.

> [!TIP]
> På Windows Server 2016 kan du muligvis se *Windows Defender Antivirus* i stedet for *Microsoft Defender Antivirus*.

Defender for Endpoint indeholder funktioner, der yderligere udvider den antivirusbeskyttelse, der er installeret på dit slutpunkt. Du kan drage fordel af at køre Microsoft Defender Antivirus sammen med en anden antivirusløsning.

[Registrering af slutpunkter og svar (Slutpunktsregistrering og -svar) i blokeringstilstand](edr-in-block-mode.md) giver f.eks. yderligere beskyttelse mod skadelige artefakter, selvom Microsoft Defender Antivirus ikke er det primære antivirusprodukt. Disse funktioner kræver, at Microsoft Defender Antivirus installeres og kører i passiv tilstand eller aktiv tilstand.

## <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Krav til, at Microsoft Defender Antivirus skal køre i passiv tilstand

Slutpunkter skal opfylde følgende krav, før Microsoft Defender Antivirus kan køre i passiv tilstand:

- Operativsystem: Windows 10 eller nyere; Windows Server 2022, Windows Server 2019 eller Windows Server, version 1803 eller nyere
- Microsoft Defender Antivirus skal installeres
- Et andet antivirus-/antimalwareprodukt, der ikke er fra Microsoft, skal installeres og bruges som den primære antivirusløsning
- Slutpunkter skal være onboardet til Defender for Endpoint

> [!IMPORTANT]
> - Microsoft Defender Antivirus er kun tilgængelig på enheder, der kører Windows 10 og 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 og Windows Server 2012 R2.
> - I Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), som administreres via Microsoft Endpoint Configuration Manager.
> - Windows Defender tilbydes også til [forbrugerenheder på Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), selvom Windows Defender ikke leverer administration på virksomhedsniveau.

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Sådan påvirker Microsoft Defender Antivirus Funktionen Defender for Endpoint

Defender for Endpoint påvirker, om Microsoft Defender Antivirus kan køre i passiv tilstand. Og tilstanden for Microsoft Defender Antivirus kan påvirke visse funktioner i Defender for Endpoint. Beskyttelse i realtid fungerer f.eks., når Microsoft Defender Antivirus er i aktiv eller passiv tilstand, men ikke når Microsoft Defender Antivirus er deaktiveret eller fjernet.

> [!IMPORTANT]
> - Tabellen i dette afsnit opsummerer de funktioner og funktioner, der fungerer aktivt eller ej, afhængigt af om Microsoft Defender Antivirus er i aktiv tilstand, passiv tilstand eller deaktiveret/fjernet. Denne tabel er udviklet til kun at være til orientering.   
> - **Deaktiver ikke funktioner**, f.eks. beskyttelse i realtid, skybaseret beskyttelse eller begrænset periodisk scanning, hvis du bruger Microsoft Defender Antivirus i passiv tilstand, eller hvis du bruger [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md), som arbejder bag kulisserne for at registrere og afhjælpe skadelige artefakter, der blev registreret efter sikkerhedsbrud.

| Beskyttelse | Microsoft Defender Antivirus <br/>(*Aktiv tilstand*) | Microsoft Defender Antivirus <br/>(*Passiv tilstand*) | Microsoft Defender Antivirus <br/>(*Deaktiveret eller fjernet*) | [EDR i bloktilstand](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [Beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) | Ja | Se note <sup>[[4](#fn4)]</sup> | Nej | Nej | 
| [Skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) | Ja | Nej  | Nej | Nej | 
| [Netværksbeskyttelse](network-protection.md)  | Ja | Nej | Nej | Nej | 
| [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md)  | Ja | Nej | Nej  | Nej | 
| [Begrænset tilgængelighed af periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md) | Nej | Nej | Ja | Nej | 
| [Oplysninger om filscanning og registrering](review-scan-results-microsoft-defender-antivirus.md) | Ja | Ja<sup>[[5](#fn5)]</sup> | Nej | Ja | 
| [Trusselsafhjælpning](configure-remediation-microsoft-defender-antivirus.md) | Ja | Se note <sup>[[6](#fn6)]</sup> | Nej | Ja | 
| [Opdateringer til sikkerhedsintelligens](manage-updates-baselines-microsoft-defender-antivirus.md) | Ja | Ja <sup>[[7](#fn7)]</sup> | Nej | Ja <sup>[[7](#fn7)]</sup> | 
| [Forebyggelse af datatab](../../compliance/endpoint-dlp-learn-about.md) | Ja | Ja | Nej | Nej |
| [Styret mappeadgang](controlled-folders.md) | Ja |Nej | Nej | Nej |
| [Filtrering af webindhold](web-content-filtering.md) | Ja | Se note <sup>[[8](#fn8)]</sup> | Nej | Nej |
| [Enhedsstyring](device-control-report.md) | Ja | Ja | Nej | Nej |
| [PUA-beskyttelse](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Ja | Nej | Nej | Nej |

(<a id="fn4">4</a>) Når Microsoft Defender Antivirus er i passiv tilstand, giver beskyttelse i realtid ikke nogen blokering eller håndhævelse, selvom den er aktiveret og i passiv tilstand.

(<a id="fn5">5</a>) Når Microsoft Defender Antivirus er i passiv tilstand, er scanninger ikke planlagt.

(<a id="fn6">6</a>) Når Microsoft Defender Antivirus er i passiv tilstand, afhjælpes trusler ikke. Trusler kan dog afhjælpes ved [at registrere og reagere på slutpunkter (Slutpunktsregistrering og -svar) i bloktilstand](edr-in-block-mode.md). I dette tilfælde kan du få vist beskeder, der viser Microsoft Defender Antivirus som en kilde, også selvom Microsoft Defender Antivirus er i passiv tilstand.

(<a id="fn7">7</a>) Opdateringsrytmen for sikkerhedsintelligens styres kun af Windows Update indstillinger. Defender-specifikke indstillinger for opdateringsplaner (dagligt/ugentligt på bestemt tidspunkt, intervalbaserede) fungerer kun, når Microsoft Defender Antivirus er i aktiv tilstand. De ignoreres i passiv tilstand.

(<a id="fn8">8</a>) Når Microsoft Defender Antivirus er i passiv tilstand, fungerer filtrering af webindhold kun med Microsoft Edge browser. 

> [!NOTE]
> [Beskyttelse mod datatab for slutpunkter](/microsoft-365/compliance/endpoint-dlp-learn-about) fungerer fortsat normalt, når Microsoft Defender Antivirus er i enten aktiv eller passiv tilstand.

## <a name="important-notes"></a>Vigtige noter

- Deaktiver, stop eller rediger ikke nogen af de tilknyttede tjenester, der bruges af Microsoft Defender Antivirus, Defender for Endpoint eller Windows Sikkerhed-appen. Denne anbefaling omfatter *tjenesterne wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* eller *MsMpEng* . Manuel ændring af disse tjenester kan medføre alvorlig ustabilitet på dine enheder og kan gøre dit netværk sårbart. Deaktivering, standsning eller ændring af disse tjenester kan også medføre problemer, når du bruger antivirusløsninger, der ikke er Fra Microsoft, og hvordan deres oplysninger vises i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

- I Defender for Endpoint skal du slå Slutpunktsregistrering og -svar til i blokeringstilstand, selvom Microsoft Defender Antivirus ikke er din primære antivirusløsning. Slutpunktsregistrering og -svar i bloktilstand registrerer og afhjælper skadelige elementer, der findes på enheden (efter sikkerhedsbrud). Du kan få mere at vide under [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Sådan bekræfter du tilstanden for Microsoft Defender Antivirus

Du kan bruge en af flere metoder til at bekræfte tilstanden af Microsoft Defender Antivirus, som beskrevet i følgende tabel:

 | Metode | Procedure | 
 |:---|:---| 
 | Windows Sikkerhed app | <ol><li>Åbn appen Windows Sikkerhed på en Windows enhed.</li><li>Vælg **Virus- og trusselsbeskyttelse**.</li><li>Under **Who beskytter mig?** vælg **Administrer udbydere**.</li><li>På siden **Sikkerhedsudbydere** under **Antivirus** kan du se, **at Microsoft Defender Antivirus er slået til**.</li></ol> | 
 | Jobliste | <ol><li>Åbn appen Jobliste på en Windows enhed.</li><li>Vælg fanen **Detaljer** .</li><li>Søg efter **MsMpEng.exe** på listen.</li></ol> | 
 | Windows PowerShell <br/> (For at bekræfte, at Microsoft Defender Antivirus kører) | <ol><li>Åbn Windows PowerShell på en Windows enhed. </li><li>Kør følgende PowerShell-cmdlet: `Get-Process`.</li><li>Gennemse resultaterne. Du bør kunne se **MsMpEng.exe**, om Microsoft Defender Antivirus er aktiveret.</li></ol> | 
 | Windows PowerShell <br/>(For at bekræfte, at antivirusbeskyttelse er på plads) |  Du kan bruge [PowerShell-cmdlet'en Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).<ol><li>Åbn Windows PowerShell på en Windows enhed.</li><li>Kør følgende PowerShell-cmdlet:<br/>`Get-MpComputerStatus | select AMRunningMode`.</li><li>Gennemse resultaterne. Du bør kunne se enten **Normal**, **Passiv** eller **Slutpunktsregistrering og -svar Blokeringstilstand**, hvis Microsoft Defender Antivirus er aktiveret på slutpunktet. </li></ol> | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Flere oplysninger om Microsoft Defender Antivirus stater

I tabellen i dette afsnit beskrives forskellige tilstande, som du kan se med Microsoft Defender Antivirus.

 |  Staten  |  Hvad sker der  | 
 |:---|:---| 
 |  Aktiv tilstand  |  I aktiv tilstand bruges Microsoft Defender Antivirus som antivirusappen på computeren. Indstillinger, der konfigureres ved hjælp af Configuration Manager, Gruppepolitik, Microsoft Intune eller andre administrationsprodukter, gælder. Filer scannes, trusler afhjælpes, og registreringsoplysninger rapporteres i dit konfigurationsværktøj (f.eks. Configuration Manager eller Microsoft Defender Antivirus-appen på selve slutpunktet).  | 
 |  Passiv tilstand eller Slutpunktsregistrering og -svar bloktilstand |  I passiv tilstand bruges Microsoft Defender Antivirus ikke som antivirusapp, og trusler afhjælpes *ikke* af Microsoft Defender Antivirus. <p>Trusler kan dog afhjælpes ved [at registrere og reagere på slutpunkter (Slutpunktsregistrering og -svar) i blokeringstilstand](edr-in-block-mode.md), når de kører i Slutpunktsregistrering og -svar Bloktilstand. <p> Filer scannes af Slutpunktsregistrering og -svar, og der leveres rapporter om trusselsregistreringer, der deles med Defender for Endpoint-tjenesten. Du får muligvis vist beskeder, der viser Microsoft Defender Antivirus som en kilde, selvom Microsoft Defender Antivirus er i passiv tilstand. <p> Når Microsoft Defender Antivirus er i passiv tilstand, kan du stadig [administrere opdateringer for Microsoft Defender Antivirus](manage-updates-baselines-microsoft-defender-antivirus.md), men du kan ikke flytte Microsoft Defender Antivirus  i aktiv tilstand, hvis dine enheder har et antivirusprogram, der ikke er fra Microsoft, og som yder beskyttelse i realtid mod malware. <p> Hvis du vil opnå optimal sikkerhedslagseffekt for forsvar og registrering, skal du sørge for at få dine antivirus- og antimalwareopdateringer, selvom Microsoft Defender Antivirus kører i passiv tilstand. Se [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md). <p> Bemærk, at passiv tilstand kun understøttes på Windows Server 2012 R2 & 2016, når maskinen er onboardet ved hjælp af den [moderne, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  Deaktiveret eller fjernet  |  Når Microsoft Defender Antivirus er deaktiveret eller fjernet, bruges den ikke som antivirusapp. Filer scannes ikke, og trusler afhjælpes ikke. <p> Det anbefales ikke generelt at deaktivere eller fjerne Microsoft Defender Antivirus. Hvis det er muligt, skal du bevare Microsoft Defender Antivirus i passiv tilstand, hvis du bruger en ikke-Microsoft-antimalware-/antivirusløsning. <p> I tilfælde, hvor Microsoft Defender Antivirus deaktiveres automatisk, kan det aktiveres igen automatisk, hvis det antivirus-/antimalwareprodukt, der ikke er Fra Microsoft, udløber eller på anden måde stopper med at yde beskyttelse i realtid mod virus, malware eller andre trusler. Den automatiske genaktivering af Microsoft Defender Antivirus hjælper med at sikre, at antivirusbeskyttelsen bevares på dine slutpunkter. <p> Du kan også bruge [begrænset periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md), som fungerer sammen med Microsoft Defender Antivirus-programmet til jævnligt at kontrollere, om der er trusler, hvis du bruger en antivirusapp, der ikke er fra Microsoft.  | 

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus på Windows klienter](microsoft-defender-antivirus-in-windows-10.md)
- [EDR i bloktilstand](edr-in-block-mode.md)
- [Få mere at vide om forebyggelse af datatab ved slutpunkt](/microsoft-365/compliance/endpoint-dlp-learn-about)
