---
title: Konfigurer scanningsindstillinger for Microsoft Defender Antivirus
description: Du kan konfigurere Microsoft Defender AV til at scanne filer til maillagring, sikkerhedskopiering eller genfortolkning, netværksfiler og arkiverede filer (f.eks. .zip filer).
keywords: avancerede scanninger, scanning, mail, arkiv, zip, rar, arkiv, genfortolkning scanning
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.date: 12/03/2021
ms.collection: M365-security-compliance
ms.topic: how-to
ms.openlocfilehash: 5060a05e485db18f8276ecd2ec592ea3873a83b2
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419918"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Konfigurer scanningsindstillinger for Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows 

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Brug Microsoft Intune til at konfigurere scanningsindstillinger

Du kan få flere oplysninger [under Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) og [Microsoft Defender Antivirus indstillinger for enhedsbegrænsning for Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Brug Microsoft Endpoint Manager til at konfigurere scanningsindstillinger

Du kan finde oplysninger om konfiguration af Microsoft Endpoint Manager (aktuel forgrening) under [Sådan opretter og installerer du antimalwarepolitikker: Scanningsindstillinger](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Brug Gruppepolitik til at konfigurere scanningsindstillinger

> [!TIP]
> Download Gruppepolitik Reference-regneark, som viser politikindstillingerne for computer- og brugerkonfigurationer, der er inkluderet i de administrative skabelonfiler, der leveres med til Windows. Du kan konfigurere referer til regnearket, når du redigerer Gruppepolitik Objekter. <br/><br/> Her er de nyeste versioner:
> - [Gruppepolitik Indstillinger referenceregneark til Windows 10 maj 2020-opdatering (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Gruppepolitik Indstillinger referenceregneark til Windows 11 oktober 2021-opdatering (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **redigeringseditoren til Gruppepolitik** skal du gå til **Computerkonfiguration** og klikke på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus**, og vælg derefter en placering (se [Indstillinger og placeringer](#settings-and-locations) i denne artikel).

5. Rediger politikobjektet.

6. Klik på **OK**, og gentag for andre indstillinger.

### <a name="settings-and-locations"></a>Indstillinger og placeringer

|Politikelement og placering|Standardindstilling (hvis den ikke er konfigureret)|PowerShell-parameter `Set-MpPreference` eller WMI-egenskab for `MSFT_MpPreference` klassen|
|---|---|---|
|Mailscanning <p> **Skan** \> **Slå mailscanning til**<p>Se [Begrænsninger for scanning af mail](#email-scanning-limitations) (i denne artikel)|Deaktiveret|`-DisableEmailScanning`|
| Scriptscanning | Aktiveret  | Denne politikindstilling giver dig mulighed for at konfigurere scriptscanning. Hvis du aktiverer eller ikke konfigurerer denne indstilling, aktiveres scriptscanning. <p>Se [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Scan [genfortolkningspunkter](/windows/win32/fileio/reparse-points) <p> **Skan** \> **Slå scanning af genfortolkningspunkt til**|Deaktiveret|Ikke tilgængelig <p>Se [Genfortolkningspunkter](/windows/win32/fileio/reparse-points)|
|Scan tilknyttede netværksdrev <p> **Skan** \> **Kør fuld scanning på tilknyttede netværksdrev**|Deaktiveret|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Scan arkivfiler (f.eks. .zip eller .rar filer). <p> **Skan** \> **Scan arkivfiler**|Aktiveret|`-DisableArchiveScanning` <p>[Listen over udeladelser af filtypenavne](configure-extension-file-exclusions-microsoft-defender-antivirus.md) har forrang for denne indstilling.|
|Scan filer på netværket <p> **Skan** \> **Scan netværksfiler**|Deaktiveret|`-DisableScanningNetworkFiles`|
|Scan pakkede eksekverbare filer <p> **Skan** \> **Scan pakkede eksekverbare filer**|Aktiveret|Ikke tilgængelig|
|Scan kun flytbare drev under komplette scanninger <p> **Skan** \> **Scan flytbare drev**|Deaktiveret|`-DisableRemovableDriveScanning`|
|Angiv det niveau af undermapper i en arkivmappe, der skal scannes <p>**Skan** \> **Angiv den maksimale dybde til scanning af arkivfiler**|0|Ikke tilgængelig|
|Angiv den maksimale CPU-belastning (som en procentdel) under en scanning. <p> **Skan** \> **Angiv den maksimale procentdel af CPU-udnyttelse under en scanning**|50|`-ScanAvgCPULoadFactor` <p>**BEMÆRK**! Den maksimale CPU-belastning er ikke en hård grænse, men er en vejledning i, at scanningsprogrammet ikke overskrider maksimumgrænsen i gennemsnit. Manuel kørsel af scanninger ignorerer denne indstilling og kører uden NOGEN CPU-grænser.|
|Angiv den maksimale størrelse (i kilobyte) af arkivfiler, der skal scannes. <p> **Skan** \> **Angiv den maksimale størrelse på de arkivfiler, der skal scannes**|Ingen grænse|Ikke tilgængelig <p>Standardværdien 0 anvender ingen grænse|
|Konfigurer lav CPU-prioritet for planlagte scanninger <p> **Skan** \> **Konfigurer lav CPU-prioritet for planlagte scanninger**|Deaktiveret|Ikke tilgængelig|

> [!NOTE]
> Hvis beskyttelse i realtid er slået til, scannes filer, før de tilgås og udføres. Scanningsområdet omfatter alle filer, herunder filer på tilsluttede flytbare medier, f.eks. USB-drev. Hvis enheden, der udfører scanningen, har beskyttelse i realtid eller on-access-beskyttelse slået til, omfatter scanningen også netværksshares.

## <a name="use-powershell-to-configure-scanning-options"></a>Brug PowerShell til at konfigurere scanningsindstillinger

Du kan få flere oplysninger om, hvordan du bruger PowerShell sammen med Microsoft Defender Antivirus, under

- [Administrer Microsoft Defender Antivirus med PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Brug WMI til at konfigurere scanningsindstillinger

Se [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Begrænsninger for scanning af mail

Mailscanning gør det muligt at scanne mailfiler, der bruges af Outlook og andre mailklienter under on-demand og planlagte scanninger. Integrerede objekter i mails (f.eks. vedhæftede filer og arkiverede filer) scannes også. Følgende filformattyper kan scannes og afhjælpes:

- DBX
- MBX
- MIME

PST-filer, der bruges af Outlook 2003 eller ældre (hvor arkivtypen er angivet til ikke-unicode), scannes også, men Microsoft Defender Antivirus kan ikke afhjælpe trusler, der registreres i PST-filer.

Hvis Microsoft Defender Antivirus registrerer en trussel i en mail, viser den dig følgende oplysninger, der kan hjælpe dig med at identificere den kompromitterede mail, så du kan afhjælpe truslen manuelt:

- Mailemne
- Navn på vedhæftet fil

## <a name="scanning-mapped-network-drives"></a>Scanner tilknyttede netværksdrev

På et operativsystem er det kun de netværksdrev, der er tilknyttet på systemniveau, der scannes. Tilknyttede netværksdrev på brugerniveau scannes ikke. Tilknyttede netværksdrev på brugerniveau er dem, som en bruger tilknytter manuelt i sin session og bruger deres egne legitimationsoplysninger.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Tilpas, start og gennemse resultaterne af Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Konfigurer og kør scanninger efter behov Microsoft Defender Antivirus](run-scan-microsoft-defender-antivirus.md)
- [Konfigurer planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
