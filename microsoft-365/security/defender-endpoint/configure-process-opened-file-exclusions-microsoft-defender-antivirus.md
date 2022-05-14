---
title: Konfigurer udeladelser for filer, der er åbnet af bestemte processer
description: Du kan udelade filer fra scanninger, hvis de er blevet åbnet af en bestemt proces.
keywords: Microsoft Defender Antivirus, proces, udeladelse, filer, scanninger
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 6faca5dde477908010f4426ff9009f383b63c58c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418604"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Konfigurer udeladelser for filer, der er åbnet af processer


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows 

Du kan udelade filer, der er blevet åbnet af bestemte processer, fra Microsoft Defender Antivirus scanninger. Se [Anbefalinger for at definere udeladelser, før du definerer dine udeladelseslister](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

I denne artikel beskrives det, hvordan du konfigurerer lister over undtagelser.

## <a name="examples-of-exclusions"></a>Eksempler på udeladelser

<br/><br/>

|Udelukkelse|Eksempel|
|---|---|
|Alle filer på computeren, der åbnes af en proces med et bestemt filnavn|Hvis du angiver `test.exe` , udelades filer, der er åbnet af: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Alle filer på computeren, der åbnes af en proces under en bestemt mappe|Hvis du angiver `c:\test\sample\*` , udelades filer, der er åbnet af: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Alle filer på computeren, der åbnes af en bestemt proces i en bestemt mappe|Hvis du angiver `c:\test\process.exe` , udelades filer, der kun er åbnet af `c:\test\process.exe`|

Når du føjer en proces til listen over procesudeladelser, scanner Microsoft Defender Antivirus ikke filer, der er åbnet af den pågældende proces, uanset hvor filerne er placeret. Selve processen scannes dog, medmindre den også er føjet til [filudeladelseslisten](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Undtagelserne gælder kun [for realtidsbeskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md). De gælder ikke for planlagte scanninger eller scanninger efter behov.

Ændringer, der er foretaget med Gruppepolitik af udeladelseslisterne **, vises** på listerne i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md). Ændringer, der er foretaget i Windows Sikkerhed app **, vises dog ikke** på de Gruppepolitik lister.

Du kan tilføje, fjerne og gennemse listerne for udeladelser i Gruppepolitik, Microsoft Endpoint Configuration Manager, Microsoft Intune og med Windows Sikkerhed-appen, og du kan bruge jokertegn til yderligere at tilpasse listerne.

Du kan også bruge PowerShell-cmdlet'er og WMI til at konfigurere udeladelseslisterne, herunder gennemse dine lister.

Lokale ændringer af listerne (af brugere med administratorrettigheder, ændringer foretaget med PowerShell og WMI) flettes som standard med listerne som defineret (og installeret) af Gruppepolitik, Configuration Manager eller Intune. De Gruppepolitik lister har forrang i tilfælde af konflikter.

Du kan [konfigurere, hvordan lister over undtagelser, der er defineret lokalt og globalt, flettes](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) , så lokale ændringer kan tilsidesætte administrerede udrulningsindstillinger.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Konfigurer listen over udeladelser for filer, der er åbnet af angivne processer

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Microsoft Intune til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

Se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) og [Microsoft Defender Antivirus indstillinger for enhedsbegrænsning for at få Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) for at få flere oplysninger.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Microsoft Endpoint Manager til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

Se [Sådan opretter og installerer du antimalwarepolitikker: Indstillinger for udeladelse for at](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) få oplysninger om konfiguration af Microsoft Endpoint Manager (aktuel forgrening).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Gruppepolitik til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. I **redigeringseditoren til Gruppepolitik** skal du gå til **Computerkonfiguration** og klikke på **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter \> Microsoft Defender Antivirus \> Udeladelser**.

4. Dobbeltklik på **Behandl udeladelser,** og tilføj udeladelser:
    1. Angiv indstillingen til **Aktiveret**.
    2. Under afsnittet **Indstillinger** skal du klikke på **Vis...**.
    3. Angiv hver proces på sin egen linje under kolonnen **Værdinavn** . Se eksempeltabellen for de forskellige typer procesudeladelser. Angiv **0** i kolonnen **Værdi** for alle processer.

5. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug PowerShell-cmdlet'er til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

Brug af PowerShell til at tilføje eller fjerne udeladelser for filer, der er blevet åbnet af processer, kræver brug af en kombination af tre cmdlet'er med `-ExclusionProcess` parameteren . Cmdlet'erne er alle i [Defender-modulet](/powershell/module/defender/).

Formatet for cmdlet'erne er:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Følgende er tilladt som \<cmdlet\>:

<br/><br/>

|Konfigurationshandling|PowerShell-cmdlet|
|---|---|
|Opret eller overskriv listen|`Set-MpPreference`|
|Føj til listen|`Add-MpPreference`|
|Fjern elementer fra listen|`Remove-MpPreference`|

> [!IMPORTANT]
> Hvis du har oprettet en liste, enten med `Set-MpPreference` eller `Add-MpPreference`, overskrives den eksisterende liste ved hjælp af `Set-MpPreference` cmdlet'en igen.

Følgende kodestykke vil f.eks. medføre, at Microsoft Defender AV-scanninger udelukker alle filer, der åbnes af den angivne proces:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Du kan få flere oplysninger om, hvordan du bruger PowerShell sammen med Microsoft Defender Antivirus, under Administrer antivirus med PowerShell-cmdlet'er og [Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug WMI (Windows Management Instruction) til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

Brug [metoderne **Set**, **Add** og **Remove** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) for følgende egenskaber:

```WMI
ExclusionProcess
```

Brugen af **Set**, **Add** og **Remove** svarer til deres kolleger i PowerShell: `Set-MpPreference`, `Add-MpPreference`og `Remove-MpPreference`.

Du kan få flere oplysninger og tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug appen Windows Sikkerhed til at udelade filer, der er blevet åbnet af angivne processer, fra scanninger

Se [Tilføj udeladelser i appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md) for at få en vejledning.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Brug jokertegn på listen over procesudeladelser

Brugen af jokertegn på listen over procesudeladelser adskiller sig fra brugen af dem på andre lister over undtagelser.

Du kan især ikke bruge spørgsmålstegnet (`?`) jokertegn, og stjerne jokertegnet (`*`) kan kun bruges i slutningen af en fuldstændig sti. Du kan stadig bruge miljøvariabler (f.eks. `%ALLUSERSPROFILE%`) som jokertegn, når du definerer elementer på listen over procesudeladelser.

I følgende tabel beskrives det, hvordan jokertegnene kan bruges på listen over procesudeladelser:

<br/><br/>

|Wildcard|Eksempel på brug|Eksempler på forekomster|
|---|---|---|
|`*` (stjerne) <p> Erstatter et vilkårligt antal tegn|`C:\MyData\*`|En hvilken som helst fil, der er åbnet af `C:\MyData\file.exe`|
|Miljøvariabler <p> Den definerede variabel udfyldes som en sti, når udeladelse evalueres|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|En hvilken som helst fil, der er åbnet af `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Gennemse listen over udeladelser

Du kan hente elementerne på listen over undtagelser med MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), [Intune](/intune/device-restrictions-configure) eller [appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md).

Hvis du bruger PowerShell, kan du hente listen på to måder:

- Hent status for alle Microsoft Defender Antivirus indstillinger. Hver af listerne vises på separate linjer, men elementerne på hver liste kombineres til den samme linje.
- Skriv status for alle indstillinger til en variabel, og brug denne variabel til kun at kalde den bestemte liste, du er interesseret i. Hver brug af skrives `Add-MpPreference` til en ny linje.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider listen over undtagelser ved hjælp af MpCmdRun

Hvis du vil kontrollere udeladelser med det dedikerede [kommandolinjeværktøj mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), skal du bruge følgende kommando:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Kontrol af udeladelser med MpCmdRun kræver Microsoft Defender Antivirus CAMP version 4.18.1812.3 (udgivet i december 2018) eller nyere.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Gennemse listen over undtagelser sammen med alle andre indstillinger for Microsoft Defender Antivirus ved hjælp af PowerShell

Brug følgende cmdlet:

```PowerShell
Get-MpPreference
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) og [Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Hent en bestemt liste over udeladelser ved hjælp af PowerShell

Brug følgende kodestykke (angiv hver linje som en separat kommando). erstat **WDAVprefs** med den etiket, du vil navngive variablen:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Se [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) og [Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender) for at få flere oplysninger om, hvordan du bruger PowerShell med Microsoft Defender Antivirus.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl, der skal undgås, når du definerer udeladelser](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Tilpas, start og gennemse resultaterne af Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
