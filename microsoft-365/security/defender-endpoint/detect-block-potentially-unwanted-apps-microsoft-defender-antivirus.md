---
title: Bloker potentielt uønskede programmer med Microsoft Defender Antivirus
description: Aktivér den potentielt uønskede pua-antivirusfunktion for at blokere uønsket software, f.eks. adware.
keywords: pua, enable, uønsket software, uønskede apps, adware, browserværktøjslinje, registrere, blokere, Microsoft Defender Antivirus
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: mimilone, julih
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: defccd8d570ec54cd033dcf7fbe29df8254661c8
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717752"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Find og bloker potentielt uønskede programmer

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Potentielt uønskede programmer (PUA) er en kategori af software, der kan få din maskine til at køre langsomt, vise uventede annoncer eller i værste fald installere anden software, der kan være uventet eller uønsket. PUA betragtes ikke som en virus, malware eller anden type trussel, men den kan udføre handlinger på slutpunkter, der påvirker slutpunktets ydeevne eller brug negativt. Udtrykket *PUA* kan også henvise til et program, der har et dårligt ry, som vurderet af Microsoft Defender for Endpoint, på grund af visse former for uønsket adfærd.

Her er nogle eksempler:

- **Reklamesoftware** , der viser reklamer eller kampagner, herunder software, der indsætter reklamer på websider.
- **Bundling-software** , der tilbyder at installere anden software, der ikke er digitalt signeret af den samme enhed. Også software, der tilbyder at installere anden software, der kvalificeres som PUA.
- **Undvigelsessoftware** , der aktivt forsøger at undgå opdagelse af sikkerhedsprodukter, herunder software, der opfører sig anderledes i tilstedeværelse af sikkerhedsprodukter.

> [!TIP]
> Hvis du vil have flere eksempler og en diskussion af de kriterier, vi bruger til at mærke programmer med særlig opmærksomhed fra sikkerhedsfunktioner, skal du se [Sådan identificerer Microsoft malware og potentielt uønskede programmer](/windows/security/threat-protection/intelligence/criteria).

Potentielt uønskede programmer kan øge risikoen for, at dit netværk bliver inficeret med faktisk malware, gøre malwareinfektioner sværere at identificere eller spilde it-ressourcer i at rense dem op. PUA-beskyttelse understøttes på Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016. I Windows 10 (version 2004 og nyere) blokerer Microsoft Defender Antivirus apps, der som standard betragtes som PUA for Enterprise-enheder (E5).

## <a name="microsoft-edge"></a>Microsoft Edge

Den [nye Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea), som er Chromium-baseret, blokerer potentielt uønskede programoverførsler og tilknyttede ressource-URL-adresser. Denne funktion leveres via [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Aktivér PUA-beskyttelse i Chromium-baseret Microsoft Edge

Selvom potentielt uønsket programbeskyttelse i Microsoft Edge (Chromium-baseret version 80.0.361.50) er slået fra som standard, kan den nemt aktiveres fra browseren.

1. I edge-browseren skal du vælge ellipsen og derefter vælge **Indstillinger**.

2. Vælg **Beskyttelse af personlige oplysninger, søgning og tjenester**.

3. Under afsnittet **Sikkerhed** skal du aktivere **Bloker potentielt uønskede apps**.

> [!TIP]
> Hvis du kører Microsoft Edge (Chromium-baseret), kan du sikkert udforske funktionen URL-blokering i PUA-beskyttelse ved at teste den på en af vores [Microsoft Defender SmartScreen-demosider](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Bloker URL-adresser med Microsoft Defender SmartScreen

I Chromium-baseret Edge, hvor PUA-beskyttelse er slået til, beskytter Microsoft Defender SmartScreen dig mod URL-adresser, der er tilknyttet PUA.

Sikkerhedsadministratorer kan [konfigurere](/DeployEdge/configure-microsoft-edge) , hvordan Microsoft Edge og Microsoft Defender SmartScreen arbejder sammen for at beskytte grupper af brugere mod PUA-tilknyttede URL-adresser. Der findes flere [gruppepolitikindstillinger](/DeployEdge/microsoft-edge-policies#smartscreen-settings) eksplicit for Microsoft Defender SmartScreen, herunder [en til blokering af PUA](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). Desuden kan administratorer [konfigurere Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) som helhed ved hjælp af gruppepolitikindstillinger til at slå Microsoft Defender SmartScreen til eller fra.

Selvom Microsoft Defender for Endpoint har sin egen blokliste baseret på et datasæt, der administreres af Microsoft, kan du tilpasse denne liste baseret på din egen trusselsintelligens. Hvis du [opretter og administrerer indikatorer](manage-indicators.md) på Microsoft Defender for Endpoint-portalen, respekterer Microsoft Defender SmartScreen de nye indstillinger.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Microsoft Defender Antivirus- og PUA-beskyttelse

Den potentielt uønskede funktion til programbeskyttelse i Microsoft Defender Antivirus kan registrere og blokere PUA på slutpunkter i dit netværk.

> [!NOTE]
> Denne funktion er tilgængelig i Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016.

Microsoft Defender Antivirus blokerer registrerede PUA-filer og forsøg på at downloade, flytte, køre eller installere dem. Blokerede PUA-filer flyttes derefter til karantæne. Når der registreres en PUA-fil på et slutpunkt, sender Microsoft Defender Antivirus en meddelelse til brugeren ([medmindre meddelelser er blevet deaktiveret](configure-notifications-microsoft-defender-antivirus.md) i samme format som andre trusselsregistreringer. Meddelelsen er på forhånd med `PUA:` for at angive dens indhold.

Meddelelsen vises på den sædvanlige [karantæneliste i Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Konfigurer PUA-beskyttelse i Microsoft Defender Antivirus

Du kan aktivere PUA-beskyttelse med [Microsoft Intune](/mem/intune/protect/device-protect), [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) eller via [PowerShell-cmdlet'er](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Du kan også bruge PUA-beskyttelse i overvågningstilstand til at registrere potentielt uønskede programmer uden at blokere dem. Registreringerne registreres i Windows-hændelsesloggen.

PUA-beskyttelse i overvågningstilstand er nyttig, hvis din virksomhed udfører en intern kontrol af softwaresikkerhedsoverholdelse, og du gerne vil undgå falske positiver.

### <a name="use-intune-to-configure-pua-protection"></a>Brug Intune til at konfigurere PUA-beskyttelse

Se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) og [Microsoft Defender Antivirus indstillinger for enhedsbegrænsning for Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) for at få flere oplysninger.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>Brug Configuration Manager til at konfigurere PUA-beskyttelse

PUA-beskyttelse er som standard aktiveret i Microsoft Endpoint Manager (Aktuel gren).

Se [Sådan opretter og installerer du antimalwarepolitikker: Indstillinger for planlagte scanninger for at](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) få oplysninger om konfiguration af Microsoft Endpoint Manager (aktuel gren).

I forbindelse med System Center 2012 Configuration Manager skal du se [Sådan installerer du potentielt uønsket politik for programbeskyttelse for Endpoint Protection i Configuration Manager](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> PUA-hændelser, der er blokeret af Microsoft Defender Antivirus, rapporteres i Windows-Logbog og ikke i Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>Brug Gruppepolitik til at konfigurere PUA-beskyttelse

1. Download og installér [administrative skabeloner (.admx) til Windows 11 oktober 2021-opdatering (21H2)](https://www.microsoft.com/download/details.aspx?id=103507)

2. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Vælg det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

4. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

5. Udvid træet til **Windows-komponenter** \> **Microsoft Defender Antivirus**.

6. Dobbeltklik på **Konfigurer registrering for potentielt uønskede programmer**.

7. Vælg **Aktiveret** for at aktivere PUA-beskyttelse.

8. Under **Indstillinger** skal du vælge **Bloker** for at blokere potentielt uønskede programmer eller vælge **Overvågningstilstand** for at teste, hvordan indstillingen fungerer i dit miljø. Vælg **OK**.

9. Udrul dit Gruppepolitik objekt, som du normalt gør.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Brug PowerShell-cmdlet'er til at konfigurere PUA-beskyttelse

#### <a name="to-enable-pua-protection"></a>Sådan aktiverer du PUA-beskyttelse

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Angivelse af værdien for denne cmdlet til at `Enabled` aktivere funktionen, hvis den er blevet deaktiveret.

#### <a name="to-set-pua-protection-to-audit-mode"></a>Sådan angiver du PUA-beskyttelse til overvågningstilstand

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Når du angiver en indstilling `AuditMode` , registreres pua'er uden at blokere dem.

#### <a name="to-disable-pua-protection"></a>Sådan deaktiverer du PUA-beskyttelse

Vi anbefaler, at PUA-beskyttelse er slået til. Du kan dog slå den fra ved hjælp af følgende cmdlet:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Hvis du angiver værdien for denne cmdlet for at `Disabled` slå funktionen fra, hvis den er blevet aktiveret.

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) - og [Defender Antivirus-cmdlet'er](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>Få vist PUA-hændelser ved hjælp af PowerShell

PUA-hændelser rapporteres i Windows-Logbog, men ikke i Microsoft Endpoint Manager eller i Intune. Du kan også bruge cmdlet'en `Get-MpThreat` til at få vist trusler, som Microsoft Defender Antivirus har håndteret. Her er et eksempel:

```console
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## <a name="get-email-notifications-about-pua-detections"></a>Få mailmeddelelser om PUA-registreringer

Du kan slå mailmeddelelser til for at modtage mail om PUA-registreringer.

Se [Fejlfinding af hændelses-id'er for at](troubleshoot-microsoft-defender-antivirus.md) få oplysninger om visning af Microsoft Defender Antivirus-hændelser. PUA-hændelser registreres under hændelses-id **1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>Se PUA-begivenheder ved hjælp af avanceret jagt

Hvis du bruger [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), kan du bruge en avanceret jagtforespørgsel til at få vist PUA-hændelser. Her er et eksempel på en forespørgsel:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Du kan få mere at vide om avanceret jagt under [Proaktiv jagt efter trusler med avanceret jagt](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Udelad filer fra PUA-beskyttelse

Nogle gange blokeres en fil fejlagtigt af PUA-beskyttelse, eller en funktion i en PUA er påkrævet for at fuldføre en opgave. I disse tilfælde kan en fil føjes til en udeladelsesliste.

Du kan få flere oplysninger under [Konfigurer og valider udeladelser baseret på filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

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

- [Næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
