---
title: Bloker potentielt uønskede programmer med Microsoft Defender Antivirus
description: Aktivér den potentielt uønskede antivirusfunktion (PUA) for at blokere uønsket software som f.eks. virus.
keywords: pua, aktivér, uønsket software, uønskede apps, browserværktøjslinje, registrer, bloker, Microsoft Defender Antivirus
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
ms.date: 10/18/2021
ms.collection: m365-security-compliance
ms.openlocfilehash: b193279f9891badc78e639776a57a366a0fa8109
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63593831"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>Find og bloker potentielt uønskede programmer

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

Potentielt uønskede programmer er en kategori af software, der kan få din computer til at køre langsomt, vise uventede reklamer eller i værst mulige tilfælde installere anden software, der kan være uventet eller uønsket. PUA betragtes ikke som en virus, malware eller en anden type trussel, men den kan udføre handlinger på slutpunkter, der påvirker slutpunktets ydeevne eller brug negativt. Ordet *PUA kan* også referere til et program, der har et dårligt ry, som vurderet af Microsoft Defender til slutpunkt på grund af visse typer uønsket adfærd.

Her er nogle eksempler:

- **Reklamesoftware** , der viser reklamer eller kampagner, herunder software, der indsætter reklamer på websider.
- **Bundtning af software** , der tilbyder installation af anden software, som ikke er digitalt signeret af den samme enhed. Samt software, der tilbyder installation af anden software, der er kvalificeret til PUA.
- **Software, der** aktivt forsøger at undgå registrering af sikkerhedsprodukter, herunder software, der opfører sig anderledes i tilstedeværelse af sikkerhedsprodukter.

> [!TIP]
> Du kan finde flere eksempler og en diskussion af de kriterier, vi bruger til at mærke programmer for at få særlig opmærksomhed fra sikkerhedsfunktioner, under Sådan identificerer [Microsoft malware og potentielt uønskede programmer](/windows/security/threat-protection/intelligence/criteria).

Potentielt uønskede programmer kan øge risikoen for, at dit netværk bliver inficeret med faktisk malware, gøre malwareinficering sværere at identificere eller spilde it-ressourcer på at rydde dem op. PUA-beskyttelse understøttes Windows 10 Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016. I Windows 10 (version 2004 og nyere) blokerer Microsoft Defender Antivirus apps, der betragtes som PUA til Enterprise-enheder (E5) som standard.

## <a name="microsoft-edge"></a>Microsoft Edge

Den [nye Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea), som er Chromium, blokerer potentielt uønskede programoverførsler og tilknyttede ressource-URL-adresser. Denne funktion leveres via [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>Aktivér PUA-beskyttelse i Chromium-baseret Microsoft Edge

Selvom potentielt uønsket programbeskyttelse i Microsoft Edge (Chromium-baseret version 80.0.361.50) er slået fra som standard, kan det nemt slås til fra i browseren.

1. I Edge-browseren skal du vælge ellipserne og derefter vælge **Indstillinger**.

2. Vælg **Beskyttelse af personlige oplysninger, søgning og tjenester**.

3. Under sektionen **Sikkerhed** skal du slå **Bloker potentielt uønskede apps til**.

> [!TIP]
> Hvis du kører Microsoft Edge (Chromium-baseret), kan du roligt udforske funktionen til blokering af webadresser i PUA-beskyttelse ved at teste den på en af [vores Microsoft Defender SmartScreen demosider](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>Bloker URL-adresser med Microsoft Defender SmartScreen

I Chromium-baseret Edge med PUA-beskyttelse slået til beskytter Microsoft Defender SmartScreen dig mod PUA-tilknyttede URL-adresser.

Sikkerhedsadministratorer kan [konfigurere,](/DeployEdge/configure-microsoft-edge) hvordan Microsoft Edge og Microsoft Defender SmartScreen arbejder sammen for at beskytte grupper af brugere mod PUA-tilknyttede URL-adresser. Der er flere [gruppepolitikindstillinger](/DeployEdge/microsoft-edge-policies#smartscreen-settings) eksplicit for de Microsoft Defender SmartScreen, herunder [én til blokering af PUA](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). Desuden kan administratorer [konfigurere Microsoft Defender SmartScreen som](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) en helhed ved hjælp af indstillinger for gruppepolitik til at slå Microsoft Defender SmartScreen til eller fra.

Selvom Microsoft Defender til Slutpunkt har sin egen blokeringsliste, der er baseret på et datasæt, der administreres af Microsoft, kan du tilpasse denne liste ud fra din egen trusselsintelligens. Hvis du [opretter og administrerer](manage-indicators.md) indikatorer i Microsoft Defender for Endpoint-portalen, Microsoft Defender SmartScreen de nye indstillinger.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>Microsoft Defender Antivirus og PUA-beskyttelse

Den potentielt uønskede pua-beskyttelsesfunktion i Microsoft Defender Antivirus kan registrere og blokere PUA på slutpunkter i dit netværk.

> [!NOTE]
> Denne funktion er tilgængelig i Windows 10, Windows 11, Windows Server 2019, Windows Server 2022 og Windows Server 2016.

Microsoft Defender Antivirus detekterede PUA-filer og eventuelle forsøg på at downloade, flytte, køre eller installere dem. Blokerede PUA-filer flyttes derefter til karantæne. Når der registreres en PUA-fil på et slutpunkt, sender Microsoft Defender Antivirus en meddelelse til [brugeren (medmindre](configure-notifications-microsoft-defender-antivirus.md) meddelelser er blevet deaktiveret i samme format som andre trusselsregistreringer. Meddelelsen åbnes med det samme for at `PUA:` angive dens indhold.

Meddelelsen vises på den sædvanlige [karantæneliste i Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>Konfigurer PUA-beskyttelse i Microsoft Defender Antivirus

Du kan aktivere PUA-beskyttelse [med Microsoft Intune](/mem/intune/protect/device-protect), [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection), [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) eller via [PowerShell-cmdlet'er](/powershell/module/defender/?preserve-view=true&view=win10-ps).

Du kan også bruge PUA-beskyttelse i overvågningstilstand til at registrere potentielt uønskede programmer uden at blokere dem. Registreringerne registreres i Windows hændelsesloggen.

> [!TIP]
> Besøg webstedet for demoen Microsoft Defender for Endpoint [demo.wd.microsoft.com](https://demo.wd.microsoft.com/Page/UrlRep) at bekræfte, at funktionen virker, og se den i aktion.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

PUA-beskyttelse i overvågningstilstand er nyttigt, hvis din virksomhed udfører en intern kontrol af overholdelse af softwaresikkerhed, og du gerne vil undgå falske positive.

### <a name="use-intune-to-configure-pua-protection"></a>Brug Intune til at konfigurere PUA-beskyttelse

Se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) Microsoft Defender Antivirus [indstillinger for enhedsbegrænsning for at Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) for at få mere at vide.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>Brug Konfigurationsstyring til at konfigurere PUA-beskyttelse

PUA-beskyttelse er aktiveret som standard i Microsoft Endpoint Manager (Aktuel forgrening).

Se [Sådan oprettes og installeres antimalwarepolitikker: Planlagte scanningsindstillinger](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) for at få mere at vide om konfiguration Microsoft Endpoint Manager (Aktuel forgrening).

For System Center 2012 Konfigurationsstyring du se Sådan installerer du en politik for potentielt uønsket programbeskyttelse til [Endpoint Protection i Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> PUA-hændelser, der blokeres Microsoft Defender Antivirus, rapporteres i Windows og ikke i Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>Brug Gruppepolitik til at konfigurere PUA-beskyttelse

1. Download og [installér administrative skabeloner (.admx) Windows 10 for oktober 2020 Update (20H2)](https://www.microsoft.com/download/details.aspx?id=102157)

2. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. Vælg det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

4. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

5. Udvid træet for **at Windows flere** \> **Microsoft Defender Antivirus**.

6. Dobbeltklik på Konfigurer **registrering for potentielt uønskede programmer**.

7. Vælg **Aktiveret** for at aktivere PUA-beskyttelse.

8. Under **Indstillinger** skal du **vælge Bloker** for at blokere potentielt uønskede programmer **eller vælge** Overvågningstilstand for at teste, hvordan indstillingen virker i dit miljø. Vælg **OK**.

9. Installér dit Gruppepolitik objekt, som du normalt gør.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>Brug PowerShell-cmdlet'er til at konfigurere PUA-beskyttelse

#### <a name="to-enable-pua-protection"></a>Sådan aktiveres PUA-beskyttelse

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

Indstilling af værdien for denne cmdlet til aktiverer `Enabled` funktionen, hvis den er blevet deaktiveret.

#### <a name="to-set-pua-protection-to-audit-mode"></a>Sådan indstilles PUA-beskyttelse til overvågningstilstand

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

Indstilling `AuditMode` registrerer PPA'er uden at blokere dem.

#### <a name="to-disable-pua-protection"></a>Sådan deaktiveres PUA-beskyttelse

Vi anbefaler, at du holder PUA-beskyttelse slået til. Du kan dog deaktivere den ved at bruge følgende cmdlet:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

Indstilling af værdien for denne cmdlet til deaktiverer `Disabled` funktionen, hvis den er blevet aktiveret.

Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>Få vist PUA-hændelser ved hjælp af PowerShell

PUA-hændelser rapporteres i Windows, men ikke i Microsoft Endpoint Manager eller i Intune. Du kan også bruge `Get-MpThreat` cmdlet'en til at få vist trusler, som Microsoft Defender Antivirus håndteres. Her er et eksempel:

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

## <a name="get-email-notifications-about-pua-detections"></a>Få mailbeskeder om PUA-registreringer

Du kan aktivere mailbeskeder til for at modtage mails om PUA-registreringer.

Se [Fejlfinding af hændelses-cd'er](troubleshoot-microsoft-defender-antivirus.md) for at få mere at vide om visning Microsoft Defender Antivirus begivenheder. PUA-hændelser registreres under hændelses-id **1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>Få vist PUA-begivenheder ved hjælp af avanceret jagt

Hvis du bruger [Microsoft Defender til slutpunkt, kan du bruge](microsoft-defender-endpoint.md) en avanceret forespørgsel til at få vist PUA-hændelser. Her er en eksempelforespørgsel:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

Du kan få mere at vide om avanceret [jagt under Proaktivt på jagt efter trusler med avanceret jagt](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>Udelad filer fra PUA-beskyttelse

Nogle gange blokeres en fil forkert af PUA-beskyttelse, eller en funktion i en PUA kræves for at fuldføre en opgave. I disse tilfælde kan en fil føjes til en udeladelsesliste.

Få mere at vide under [Konfigurer og valider udeladelse baseret på filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Se også

- [Næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
