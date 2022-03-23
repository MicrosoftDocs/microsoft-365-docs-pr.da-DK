---
title: Konfigurere udeladelse af filer, der er åbnet af bestemte processer
description: Du kan udelukke filer fra scanninger, hvis de har været åbnet af en bestemt proces.
keywords: Microsoft Defender Antivirus, proces, udelukkelse, filer, scanninger
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
ms.openlocfilehash: 034ad1312497652554c9a59d51ba18f6bddc9d83
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63593206"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>Konfigurere udeladelse af filer, der er åbnet af processer


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan udelade filer, der er blevet åbnet af bestemte processer, Microsoft Defender Antivirus scanninger. Se En [Anbefalinger definition af udeladelseslister, før](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) du definerer dine udeladelseslister.

I denne artikel beskrives det, hvordan du kan konfigurere udeladelseslister.

## <a name="examples-of-exclusions"></a>Eksempler på udeladelse

<br/><br/>

|Udeladelse|Eksempel|
|---|---|
|En hvilken som helst fil på den computer, der åbnes af en proces med et bestemt filnavn|Angivelse `test.exe` af, om filer, der er åbnet ved hjælp af: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Enhver fil på den computer, der åbnes af en proces under en bestemt mappe|Angivelse `c:\test\sample\*` af, om filer, der er åbnet ved hjælp af: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Enhver fil på den computer, der åbnes af en bestemt proces i en bestemt mappe|Angivelse vil `c:\test\process.exe` udelukke filer, der kun åbnes af `c:\test\process.exe`|

Når du føjer en proces til listen over udeladelse af proces, scanner Microsoft Defender Antivirus ikke filer, der er åbnet af denne proces, uanset hvor filerne er placeret. Selve processen scannes dog, medmindre den også er blevet føjet til listen til [udeladelse af filer](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Undtagelserne gælder kun for [beskyttelse og overvågning i realtid, der altid er i realtid](configure-real-time-protection-microsoft-defender-antivirus.md). De gælder ikke for planlagte scanninger eller scanninger efter behov.

Ændringer, der Gruppepolitik med **udeladelseslisterne, vises** på listerne [i Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md). De ændringer, der er foretaget Windows Sikkerhed appen **, vises dog ikke** på Gruppepolitik lister.

Du kan tilføje, fjerne og gennemse listerne over udeladelser i Gruppepolitik, Microsoft Endpoint Configuration Manager, Microsoft Intune og med Windows Sikkerhed-appen, og du kan bruge jokertegn til yderligere at tilpasse listerne.

Du kan også bruge PowerShell-cmdlet'er og WMI til at konfigurere udeladelseslisterne, herunder gennemsyn af dine lister.

Lokale ændringer af listerne (af brugere med administratorrettigheder; ændringer, der er foretaget med PowerShell og WMI) flettes som standard med listerne som defineret (og installeret) af Gruppepolitik, Konfigurationsstyring eller Intune. De Gruppepolitik lister har forrang i tilfælde af konflikter.

Du kan [konfigurere, hvordan lokalt og globalt definerede udeladelseslister flettes](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) for at tillade, at lokale ændringer tilsidesætter administrerede installationsindstillinger.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Konfigurere listen over udeladelse af filer, der åbnes af angivne processer

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Microsoft Intune til at udelukke filer, der har været åbnet af angivne processer, fra scanninger

Se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure) Microsoft Defender Antivirus [indstillinger for enhedsbegrænsning for at Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) for at få mere at vide.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Microsoft Endpoint Manager til at udelukke filer, der har været åbnet af angivne processer, fra scanninger

Se [Sådan oprettes og installeres antimalwarepolitikker: Udeladelsesindstillinger](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) for at få mere at vide om konfiguration Microsoft Endpoint Manager (aktuel forgrening).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Gruppepolitik til at udelukke filer, der har været åbnet af angivne processer, fra scanninger

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I menuen **Gruppepolitik skal du** gå til **Computerkonfiguration og** klikke på **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter \> Microsoft Defender Antivirus \> udeladelse.**

4. Dobbeltklik på **Procesude udeladelse,** og tilføj udeladelserne:
    1. Angiv indstillingen til **Aktiveret**.
    2. Under sektionen **Indstillinger** skal du klikke **på Vis...**.
    3. Angiv hver proces på sin egen linje under **kolonnen Værdinavn** . Se eksempeltabellen for de forskellige typer procesudetagelser. Angiv **0** i **kolonnen Værdi** for alle processer.

5. Klik på **OK**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug PowerShell-cmdlet'er til at udelukke filer, der har været åbnet af angivne processer, fra scanninger

Brug af PowerShell til at tilføje eller fjerne udeladelse af filer, der har været åbnet af processer, kræver brug af en kombination af tre cmdlet'er med `-ExclusionProcess` parameteren. Cmdlet'erne er alle i [Defender-modulet](/powershell/module/defender/).

Formatet for cmdletterne er:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Følgende er tilladt som \<cmdlet\>:

<br/><br/>

|Konfigurationshandling|PowerShell-cmdlet|
|---|---|
|Oprette eller overskrive listen|`Set-MpPreference`|
|Føj til listen|`Add-MpPreference`|
|Fjern elementer fra listen|`Remove-MpPreference`|

> [!IMPORTANT]
> Hvis du har oprettet en liste, vil brug `Set-MpPreference` af `Add-MpPreference``Set-MpPreference` cmdlet'en, enten med eller , overskrive den eksisterende liste.

Det følgende kodestykke ville f.eks. få Microsoft Defender AV-scanninger til at udelukke enhver fil, der åbnes af den angivne proces:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

Du kan finde flere oplysninger om, hvordan du bruger PowerShell Microsoft Defender Antivirus, under Administrer antivirus med [PowerShell-cmdlet'er og Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug Windows management instruction (WMI) til at udelukke filer, der har været åbnet af angivne processer fra scanninger

Brug [**metoderne** **Indstil**, Tilføj **og** Fjern for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ExclusionProcess
```

Brug af **Set**, **Add** og **Remove svarer** til deres modparter i PowerShell: `Set-MpPreference`, `Add-MpPreference`og `Remove-MpPreference`.

Du kan finde flere oplysninger og tilladte parametre [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Brug appen Windows Sikkerhed til at udelukke filer, der har været åbnet af angivne processer, fra scanninger

Se [Tilføj udeladelse i appen Windows Sikkerhed for at få](microsoft-defender-security-center-antivirus.md) vejledning.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>Brug jokertegn på listen over udeladelse af proces

Brugen af jokertegn på listen over udeladelse af proces er anderledes end brugen af dem på andre udeladelseslister.

Du kan især ikke bruge jokertegnet spørgsmålstegn (`?`), og jokertegnet stjerne (`*`) kan kun bruges i slutningen af en komplet sti. Du kan stadig bruge miljøvariabler (f.eks `%ALLUSERSPROFILE%`. ) som jokertegn, når du definerer elementer på listen over udeladelse af proces.

I følgende tabel beskrives det, hvordan jokertegnene kan bruges på listen over udeladelse af proces:

<br/><br/>

|Jokertegn|Eksempel på brug|Eksempel på match|
|---|---|---|
|`*` (stjerne) <p> Erstatter et vilkårligt antal tegn|`C:\MyData\*`|Enhver fil, der åbnes af `C:\MyData\file.exe`|
|Miljøvariabler <p> Den definerede variabel udfyldes som en sti, når udelukkelsen evalueres|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Enhver fil, der åbnes af `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Gennemse listen over udeladelses undtagelser

Du kan hente elementerne på udeladelseslisten med MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings), [Intune](/intune/device-restrictions-configure) [eller Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md).

Hvis du bruger PowerShell, kan du hente listen på to måder:

- Hent status for alle Microsoft Defender Antivirus indstillinger. Hver af listerne vises på separate linjer, men elementerne på hver liste kombineres til den samme linje.
- Skriv status for alle indstillinger til en variabel, og brug variablen til kun at kalde den specifikke liste, du er interesseret i. Hver brug af `Add-MpPreference` skrives på en ny linje.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider udeladelseslisten ved hjælp af MpCmdRun

Hvis du vil kontrollere udeladelse af det [dedikerede kommandolinjeværktøj mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), skal du bruge følgende kommando:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Kontrol af udeladelse med MpCmdRun kræver Microsoft Defender Antivirus CAMP version 4.18.1812.3 (udgivet i december 2018) eller nyere.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Gennemse listen over udeladelsesindstillinger sammen med alle Microsoft Defender Antivirus ved hjælp af PowerShell

Brug følgende cmdlet:

```PowerShell
Get-MpPreference
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- [Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Hent en bestemt udeladelsesliste ved hjælp af PowerShell

Brug følgende kodestykke (angiv hver linje som en separat kommando); **erstat WDAVprefs** med det navn, du vil navngive variablen:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

Se [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus- [Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender) for at få mere at vide om, hvordan du bruger PowerShell Microsoft Defender Antivirus.

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl at undgå, når du definerer udeladelse](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
