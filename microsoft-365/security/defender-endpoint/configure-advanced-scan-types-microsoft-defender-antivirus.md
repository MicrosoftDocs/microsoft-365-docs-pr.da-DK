---
title: Konfigurer scanningsindstillinger for Microsoft Defender Antivirus
description: Du kan konfigurere Microsoft Defender AV til at scanne maillagringsfiler, sikkerhedskopierings- eller genparsepunkter, netværksfiler og arkiverede filer (f.eks. .zip filer).
keywords: avancerede scanninger, scanning, mail, arkiv, zip, arkiv, arkiv, genparse scanning
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
ms.openlocfilehash: 2527a558d474fecaab813963dc38a9e76aa89d5c
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2021
ms.locfileid: "63595879"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Konfigurere Microsoft Defender Antivirus indstillinger for scanning

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Brug Microsoft Intune til at konfigurere scanningsindstillinger

Du kan finde flere oplysninger [under Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) og Microsoft Defender Antivirus indstillinger for enhedsbegrænsning [for Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Brug Microsoft Endpoint Manager til at konfigurere scanningsindstillinger

Hvis du vil have mere at vide Microsoft Endpoint Manager (aktuel gren), skal du se Sådan oprettes og [installeres antimalwarepolitikker: Indstillinger for scanning](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Brug Gruppepolitik til at konfigurere scanningsindstillinger

> [!TIP]
> Download oversigtsarket Gruppepolitik, som viser politikindstillingerne for computer- og brugerkonfigurationer, der er inkluderet i de administrative skabelonfiler, der leveres sammen med til Windows. Du kan konfigurere henvis til regnearket, når du redigerer Gruppepolitik objekter. <br/><br/> Her er de seneste versioner:
> - [Gruppepolitik Indstillinger til regneark til Windows 10 maj 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Gruppepolitik Indstillinger oversigtsark til Windows 11. oktober 2021 Opdatering (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I menuen **Gruppepolitik skal du** gå til **Computerkonfiguration og** klikke på **Administrative skabeloner**.

4. Udvid træet for **Windows flere** \> **Microsoft Defender Antivirus**, og vælg derefter en placering ([se Indstillinger og placeringer](#settings-and-locations) i denne artikel).

5. Redigere politikobjektet.

6. Klik **på OK**, og gentag for eventuelle andre indstillinger.

### <a name="settings-and-locations"></a>Indstillinger og placeringer

|Politikelement og placering|Standardindstilling (hvis den ikke er konfigureret)|PowerShell-parameter `Set-MpPreference` eller WMI-egenskab for `MSFT_MpPreference` klasse|
|---|---|---|
|Scanning af mail <p> **Scan** \> **Aktivere scanning af e-mails**<p>Se [Begrænsninger for scanning af mail](#email-scanning-limitations) (i denne artikel)|Deaktiveret|`-DisableEmailScanning`|
| Scriptscanning | Aktiveret  | Denne politikindstilling gør det muligt at konfigurere scriptscanning. Hvis du aktiverer eller ikke konfigurerer denne indstilling, aktiveres scriptscanning. <p>Se [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Scan [reparse point](/windows/win32/fileio/reparse-points) <p> **Scan** \> **Slå scanning af genparse point til**|Deaktiveret|Ikke tilgængelig <p>Se [Reparse points](/windows/win32/fileio/reparse-points)|
|Scanning tilknyttede netværksdrev <p> **Scan** \> **Kør fuld scanning på tilknyttede netværksdrev**|Deaktiveret|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Scan arkivfiler (f.eks. .zip eller .rar filer). <p> **Scan** \> **Scan arkivfiler**|Aktiveret|`-DisableArchiveScanning` <p>[Udeladelseslisten for](configure-extension-file-exclusions-microsoft-defender-antivirus.md) udvidelser tilsidesætter denne indstilling.|
|Scan filer på netværket <p> **Scan** \> **Scan netværksfiler**|Deaktiveret|`-DisableScanningNetworkFiles`|
|Scanne eksekverbare eksekverbare værdier <p> **Scan** \> **Scanne eksekverbare eksekverbare værdier**|Aktiveret|Ikke tilgængelig|
|Scan kun flytbare drev under fulde scanninger <p> **Scan** \> **Scan flytbare drev**|Deaktiveret|`-DisableRemovableDriveScanning`|
|Angive det niveau af undermapper i en arkivmappe, der skal scannes <p>**Scan** \> **Angiv den maksimale dybde for scanningsarkivfiler**|0|Ikke tilgængelig|
|Angiv den maksimale CPU-indlæsning (som en procentdel) under en scanning. <p> **Scan** \> **Angiv den maksimale procentdel af CPU-udnyttelse under en scanning**|50|`-ScanAvgCPULoadFactor` <p>**BEMÆRK**: Den maksimale CPU-belastning er ikke en hård grænse, men er en vejledning til scanningsprogrammet, så det ikke overskrider maksimumværdien i gennemsnit. Hvis du kører scanninger manuelt, ignoreres denne indstilling, og de køres uden CPU-begrænsninger.|
|Angiv den maksimale størrelse (i kilobyte) af arkivfiler, der skal scannes. <p> **Scan** \> **Angiv den maksimale størrelse på arkivfiler, der skal scannes**|Ingen grænse|Ikke tilgængelig <p>Standardværdien 0 anvender ingen grænse|
|Konfigurere lav CPU-prioritet for planlagte scanninger <p> **Scan** \> **Konfigurere lav CPU-prioritet for planlagte scanninger**|Deaktiveret|Ikke tilgængelig|

> [!NOTE]
> Hvis beskyttelse i realtid er aktiveret, scannes filer, før de åbnes og udføres. Scanningsomfanget omfatter alle filer, herunder filer påmonterede flytbare medier, f.eks. USB-drev. Hvis den enhed, der udfører scanningen, har beskyttelse i realtid eller beskyttelse mod adgang slået til, omfatter scanningen også netværksshares.

## <a name="use-powershell-to-configure-scanning-options"></a>Brug PowerShell til at konfigurere scanningsindstillinger

Du kan finde flere oplysninger om, hvordan du bruger PowerShell Microsoft Defender Antivirus, under

- [Administrer Microsoft Defender Antivirus med PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Brug WMI til at konfigurere scanningsindstillinger

Se [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>Begrænsninger for scanning af mail

Scanning af mails muliggør scanning af mailfiler, der Outlook og andre mailklienter under on-demand og planlagte scanninger. Integrerede objekter i mails (f.eks. vedhæftede filer og arkiverede filer) scannes også. Følgende filtyper kan scannes og afhjælpes:

- DBX
- MBX
- MIME

PST-filer, der bruges af Outlook 2003 eller ældre (hvor arkivtypen er angivet til ikke-unicode), scannes også, men Microsoft Defender Antivirus kan ikke løse trusler, der registreres i PST-filer.

Hvis Microsoft Defender Antivirus registrerer en trussel i en mail, viser den dig følgende oplysninger, der kan hjælpe dig med at identificere den kompromitterede mail, så du kan løse truslerne manuelt:

- Mailens emne
- Navn på vedhæftet fil

## <a name="scanning-mapped-network-drives"></a>Scanning af tilknyttede netværksdrev

På et hvilket som helst operativsystem scannes kun de netværksdrev, der er tilknyttet på systemniveau. Tilknyttede netværksdrev på brugerniveau scannes ikke. Brugerniveau tilknyttede netværksdrev er dem, som en bruger tilknytter i sin session manuelt og ved hjælp af sine egne legitimationsoplysninger.

## <a name="see-also"></a>Se også

- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Konfigurere og køre on-demand-Microsoft Defender Antivirus scanninger](run-scan-microsoft-defender-antivirus.md)
- [Konfigurere planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
