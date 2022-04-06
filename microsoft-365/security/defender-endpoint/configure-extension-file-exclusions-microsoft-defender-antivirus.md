---
title: Konfigurere og validere udeladelse baseret på udvidelse, navn eller placering
description: Udelad filer Microsoft Defender Antivirus alle scanninger baseret på deres filtypenavn, filnavn eller placering.
keywords: udeladelse, filer, filtypenavn, filtype, mappenavn, filnavn, scanninger
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.date: 02/27/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: da5add0e1f37a813e6962accbc391be6efba1cb1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472985"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Konfigurere og validere udeladelse baseret på filtypenavn og mappeplacering

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Du kan definere undtagelser for Microsoft Defender Antivirus, der gælder for planlagte scanninger[, scanninger](schedule-antivirus-scans.md) efter [](run-scan-microsoft-defender-antivirus.md)behov og altid [on-on, beskyttelse og overvågning i realtid](configure-real-time-protection-microsoft-defender-antivirus.md). **Generelt skal du ikke anvende udeladelse**. Hvis du har brug for at anvende udeladelse, kan du vælge mellem flere forskellige typer:

- Udeladelse baseret på filtypenavne og mappeplaceringer (beskrevet i denne artikel)
- [Udeladelse af filer, der åbnes af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Microsoft Defender Antivirus undtagelser gælder ikke for andre Microsoft Defender for Endpoint, herunder slutpunktsregistrering og -svar [( Slutpunktsregistrering og -svar)](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response), [ASR-regler (Attack Surface Reduction)](/microsoft-365/security/defender-endpoint/attack-surface-reduction) og [kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders). Filer, som du udelader ved hjælp af de metoder, der er beskrevet i denne artikel, kan stadig Slutpunktsregistrering og -svar vigtige beskeder og andre registreringer.
> Hvis du vil udelade filer bredt, skal du føje dem til Microsoft Defender for Endpoint [brugerdefinerede indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators).

## <a name="before-you-begin"></a>Inden du går i gang...

Se En [Anbefalinger definition af udeladelseslister, før](configure-exclusions-microsoft-defender-antivirus.md) du definerer dine udeladelseslister.

## <a name="exclusion-lists"></a>Udeladelseslister

Hvis du vil udelade bestemte filer Microsoft Defender Antivirus scanninger, skal du ændre dine udeladelseslister. Microsoft Defender Antivirus indeholder mange automatiske udeladelsesforanstaltninger, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier og -situationer.

> [!NOTE]
> Undtagelser gælder også for potentielt uønskede appregistreringer.
>
> Automatisk udeladelse gælder kun for Windows Server 2016 og nyere. Disse undtagelser er ikke synlige i Windows Sikkerhed-appen og i PowerShell.

I følgende tabel vises nogle eksempler på udeladelse baseret på filtypenavn og mappeplacering. 
<br/><br/>

|Udeladelse|Eksempler|Udeladelsesliste|
|---|---|---|
|Enhver fil med et bestemt filtypenavn|Alle filer med det angivne filtypenavn, hvor som helst på computeren. <p> Gyldig syntaks: `.test` og `test`|Udeladelse af udvidelse|
|En fil under en bestemt mappe|Alle filer under `c:\test\sample` mappen|Udeladelse af filer og mapper|
|En bestemt fil i en bestemt mappe|Kun filen `c:\sample\sample.test`|Udeladelse af filer og mapper|
|En bestemt proces|Den eksekverbare fil `c:\test\process.exe`|Udeladelse af filer og mapper|

## <a name="characteristics-of-exclusion-lists"></a>Karakteristika ved udeladelseslister

- Mappeudetagelser gælder for alle filer og mapper under den pågældende mappe, medmindre undermappen er et genparspunkt. Undermapper til genopsparing af point skal udelades separat.
- Filtypenavne gælder for alle filnavne med det definerede filtypenavn, hvis der ikke er defineret en sti eller mappe.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Vigtige noter om udeladelse baseret på filtypenavne og mappeplaceringer

- Hvis du bruger jokertegn, f.eks. stjernen (\*), ændres fortolkningen af udeladelsesreglerne. Se afsnittet [Brug jokertegn](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) i filnavnet og mappestien eller udeladelseslister for filtypenavnet for at få vigtige oplysninger om, hvordan jokertegn fungerer.

- Du må ikke udelade tilknyttede netværksdrev. Angiv den faktiske netværkssti.

- Mapper, der er omoprettede punkter, der er oprettet, efter Microsoft Defender Antivirus-tjenesten starter, og som er føjet til udeladelseslisten, medtages ikke. Genstart tjenesten (ved at genstarte Windows), så nye genparspunkter genkendes som et gyldigt udelukkelsesmål.

- Udeladelse gælder [for planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [on-demand-scanninger](run-scan-microsoft-defender-antivirus.md) og [](configure-real-time-protection-microsoft-defender-antivirus.md)beskyttelse i realtid, men ikke på tværs af Defender til slutpunkt. Hvis du vil definere udeladelse på tværs af Defender til Slutpunkt, skal du bruge [brugerdefinerede indikatorer](manage-indicators.md).

- Lokale ændringer af listerne (af brugere med administratorrettigheder, herunder ændringer foretaget med PowerShell og WMI) sammenflettes som standard med listerne som defineret (og installeret) af Gruppepolitik, Configuration Manager eller Intune. Listerne Gruppepolitik rangfølges, når der opstår konflikter. Desuden kan ændringer i udeladelseslisten, der Gruppepolitik ændringer i Gruppepolitik, ses [i Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md).

- Hvis du vil tillade lokale ændringer at tilsidesætte administrerede installationsindstillinger, skal [du konfigurere, hvordan lokalt og globalt definerede udeladelseslister flettes](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Konfigurer listen over udeladelses undtagelser baseret på mappenavn eller filtypenavn

Du kan vælge mellem flere forskellige metoder til at definere undtagelser for Microsoft Defender Antivirus.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug Intune til at konfigurere udeladelse af filnavn, mappe eller filtypenavn

Se følgende artikler:

- [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure)
- [Microsoft Defender Antivirus indstillinger for enhedsbegrænsning for Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug Configuration Manager til at konfigurere udeladelse af filnavn, mappe eller filtypenavn

Se [Sådan oprettes og installeres antimalwarepolitikker: Udeladelsesindstillinger](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) for at få mere at vide om konfiguration Microsoft Endpoint Manager (aktuel forgrening).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Brug Gruppepolitik til at konfigurere udeladelse af mapper eller filtypenavn

> [!NOTE]
> Hvis du angiver en fuldt kvalificeret sti til en fil, er det kun den pågældende fil, der udelades. Hvis en mappe er defineret i udelukkelsen, udelades alle filer og undermapper under den pågældende mappe.

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I Gruppepolitik **skal du gå** til **Computerkonfiguration og** vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **udeladelse.**

4. Åbn indstillingen **For undtagelser til** sti til redigering, og tilføj dine udeladelsesindstillinger.
    1. Angiv indstillingen til **Aktiveret**.
    2. Under sektionen **Indstillinger** skal du vælge **Vis**.
    3. Angiv hver mappe på sin egen linje under **kolonnen Værdinavn** .
    4. Hvis du angiver en fil, skal du sikre dig, at du angiver en fuldt kvalificeret sti til filen, herunder drevbogstavet, mappestien, filnavnet og filtypenavnet. 
    5. Angiv **0** i **kolonnen** Værdi.

5. Vælg **OK**.

6. Åbn indstillingen **Udeladelse af udvidelse** for at redigere, og tilføj dine udeladelsesindstillinger.
    1. Angiv indstillingen til **Aktiveret**.
    2. Under sektionen **Indstillinger** skal du vælge **Vis**.
    3. Angiv hvert filtypenavn på sin egen linje under **kolonnen Værdinavn** .
    4. Angiv **0** i **kolonnen** Værdi.

7. Vælg **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug PowerShell-cmdlet'er til at konfigurere udeladelse af filnavn, mappe eller filtypenavn

Brug af PowerShell til at tilføje eller fjerne udeladelse af filer, der er baseret på filtypenavnet, placeringen eller filnavnet kræver brug af en kombination af tre cmdlet'er og den relevante parameter for udeladelseslisten. Cmdlet'erne er alle i [Defender-modulet](/powershell/module/defender/).

Formatet for cmdletterne er som følger:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

I følgende tabel vises de cmdlet'er, som du kan bruge i den `<cmdlet>` del af PowerShell-cmdlet'en:

<br/><br/>

|Konfigurationshandling|PowerShell-cmdlet|
|:---|:---|
|Oprette eller overskrive listen|`Set-MpPreference`|
|Føj til listen|`Add-MpPreference`|
|Fjern element fra listen|`Remove-MpPreference`|

I følgende tabel vises værdier, som du kan bruge i den del `<exclusion list>` af PowerShell-cmdlet'en:

<br/><br/>

|Udeladelsestype|PowerShell-parameter|
|---|---|
|Alle filer med et bestemt filtypenavn|`-ExclusionExtension`|
|Alle filer under en mappe (herunder filer i undermapper) eller en bestemt fil|`-ExclusionPath`|

> [!IMPORTANT]
> Hvis du har oprettet en liste, vil brug `Set-MpPreference` af `Add-MpPreference``Set-MpPreference` cmdlet'en, enten med eller , overskrive den eksisterende liste.

Følgende kodestykke medfører f.eks., at Microsoft Defender Antivirus alle filer med filtypenavnet udelades`.test`:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug Windows WMI (Management Instrumentation) til at konfigurere udeladelse af filnavn, mappe eller filtypenavn

Brug [metoderne Indstil, Tilføj og Fjern for MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
ExclusionExtension
ExclusionPath
```

Brug **af Set**, **Add** og **Remove** svarer til deres modparter i PowerShell: `Set-MpPreference`, `Add-MpPreference`og `Remove-MpPreference`.

> [!TIP]
> Du kan finde flere oplysninger [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug appen Windows Sikkerhed til at konfigurere udeladelse af filnavn, mappe eller filtypenavn

Se [Tilføj udeladelse i appen Windows Sikkerhed for at få](microsoft-defender-security-center-antivirus.md) vejledning.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Brug jokertegn i filnavnet og mappestien eller udeladelseslisterne for filtypenavnet

Du kan bruge `*`stjerne, `?`spørgsmålstegn eller miljøvariabler ( `%ALLUSERSPROFILE%`f.eks. ) som jokertegn, når du definerer elementer i udeladelseslisten for filnavnet eller mappestien. Den måde, hvorpå disse jokertegn fortolkes, er forskellig fra deres sædvanlige brug i andre apps og sprog. Sørg for at læse dette afsnit for at forstå deres specifikke begrænsninger.

> [!IMPORTANT]
> Der er vigtige begrænsninger og brugsscenarier for disse jokertegn:
>
> - Anvendelse af miljøvariabler er begrænset til maskinvariabler og dem, der gælder for processer, der kører som en NT AUTHORITY\SYSTEM-konto.
> - Du kan kun bruge op til seks jokertegn pr. post.
> - Du kan ikke bruge et jokertegn i stedet for et drevbogstav.
> - En stjerne i en `*` mappeudeudelse står for en enkelt mappe. Brug flere forekomster af `\*\` til at angive flere indlejrede mapper med uspecificeret navne.
> - Aktuelt understøtter Microsoft Endpoint Configuration Manager ikke jokertegn (f.eks. `*` eller `?`).
    
I følgende tabel beskrives det, hvordan jokertegnene kan bruges, og der er nogle eksempler.

<br/><br/>

|Jokertegn|Eksempler|
|---|---|
|`*` (stjerne) <p> I **forbindelse** med medtagelse af filnavn og filtypenavn erstatter stjernen et vilkårligt antal tegn og gælder kun for filer i den sidste mappe, der er defineret i argumentet. <p> I **mappeudetagelser** erstatter stjernen en enkelt mappe. Brug flere `*` med mappe skråstreger `\` til at angive flere indlejrede mapper. Når du har matcher antallet af jokertegn og navngivne mapper, medtages alle undermapper også.|`C:\MyData\*.txt` omfatter `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` omfatter en hvilken som helst `C:\somepath\Archives\Data` fil i og dens undermapper og `C:\somepath\Authorized\Data` dens undermapper <p> `C:\Serv\*\*\Backup` omfatter en hvilken som helst fil `C:\Serv\Primary\Denied\Backup` i og dens undermapper `C:\Serv\Secondary\Allowed\Backup` og undermapper|
|`?` (spørgsmålstegn)  <p> Ved **medtagelse af filnavn og** filtypenavn erstatter spørgsmålstegnet et enkelt tegn og gælder kun for filer i den sidste mappe, der er defineret i argumentet. <p> I **mappeudetagelser** erstatter spørgsmålstegnet et enkelt tegn i et mappenavn. Når du har matcher antallet af jokertegn og navngivne mapper, medtages alle undermapper også.|`C:\MyData\my?.zip` omfatter `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` omfatter en hvilken som helst fil `C:\somepath\P\Data` i og dens undermapper  <p> `C:\somepath\test0?\Data` ville medtage en hvilken som helst fil `C:\somepath\test01\Data` i og dens undermapper|
|Miljøvariabler <p> Den definerede variabel udfyldes som en sti, når udelukkelsen evalueres.|`%ALLUSERSPROFILE%\CustomLogFiles` ville omfatte `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Hvis du blander et argument til udeladelse af en fil med et argument til udeladelse af en mappe, stopper reglerne ved filargumentet match i den matchede mappe og søger ikke efter filmatches i nogen undermapper.
>
> Du kan f.eks. udelade alle filer, der starter med "dato" i mapperne `c:\data\final\marked` og ved `c:\data\review\marked` hjælp af argumentet regel `c:\data\*\marked\date*`.
>
> Dette argument svarer dog ikke til nogen filer i undermapper under `c:\data\final\marked` eller `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Variabler for systemmiljø

Følgende tabel viser og beskriver miljøvariablerne for systemkontoen.

<br/><br/>

|Denne systemmiljøvariabel...|Omdirigerer til dette|
|---|---|
|`%APPDATA%`|`C:\Users\UserName.DomainName\AppData\Roaming`|
|`%APPDATA%\Microsoft\Internet Explorer\Quick Launch`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch`|
|`%APPDATA%\Microsoft\Windows\Start Menu`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu`|
|`%APPDATA%\Microsoft\Windows\Start Menu\Programs`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`|
|`%LOCALAPPDATA%`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%ProgramData%`|`C:\ProgramData`|
|`%ProgramFiles%`|`C:\Program Files`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles%\Windows Sidebar\Gadgets`|`C:\Program Files\Windows Sidebar\Gadgets`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles(x86)%`|`C:\Program Files (x86)`|
|`%ProgramFiles(x86)%\Common Files`|`C:\Program Files (x86)\Common Files`|
|`%SystemDrive%`|`C:`|
|`%SystemDrive%\Program Files`|`C:\Program Files`|
|`%SystemDrive%\Program Files (x86)`|`C:\Program Files (x86)`|
|`%SystemDrive%\Users`|`C:\Users`|
|`%SystemDrive%\Users\Public`|`C:\Users\Public`|
|`%SystemRoot%`|`C:\Windows`|
|`%windir%`|`C:\Windows`|
|`%windir%\Fonts`|`C:\Windows\Fonts`|
|`%windir%\Resources`|`C:\Windows\Resources`|
|`%windir%\resources\0409`|`C:\Windows\resources\0409`|
|`%windir%\system32`|`C:\Windows\System32`|
|`%ALLUSERSPROFILE%`|`C:\ProgramData`|
|`%ALLUSERSPROFILE%\Application Data`|`C:\ProgramData\Application Data`|
|`%ALLUSERSPROFILE%\Documents`|`C:\ProgramData\Documents`|
|`%ALLUSERSPROFILE%\Documents\My Music\Sample Music`|`C:\ProgramData\Documents\My Music\Sample Music`|
|`%ALLUSERSPROFILE%\Documents\My Music`|`C:\ProgramData\Documents\My Music`|
|`%ALLUSERSPROFILE%\Documents\My Pictures`|`C:\ProgramData\Documents\My Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Pictures\Sample Pictures`|`C:\ProgramData\Documents\My Pictures\Sample Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Videos`|`C:\ProgramData\Documents\My Videos`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\DeviceMetadataStore`|`C:\ProgramData\Microsoft\Windows\DeviceMetadataStore`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\GameExplorer`|`C:\ProgramData\Microsoft\Windows\GameExplorer`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Ringtones`|`C:\ProgramData\Microsoft\Windows\Ringtones`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu`|`C:\ProgramData\Microsoft\Windows\Start Menu`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Templates`|`C:\ProgramData\Microsoft\Windows\Templates`|
|`%ALLUSERSPROFILE%\Start Menu`|`C:\ProgramData\Start Menu`|
|`%ALLUSERSPROFILE%\Start Menu\Programs`| `C:\ProgramData\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Templates`|`C:\ProgramData\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\ConnectedSearch\Templates`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\ConnectedSearch\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\History`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\History`|
|`%PUBLIC%`|`C:\Users\Public`|
|`%PUBLIC%\AccountPictures`|`C:\Users\Public\AccountPictures`|
|`%PUBLIC%\Desktop`|`C:\Users\Public\Desktop`|
|`%PUBLIC%\Documents`|`C:\Users\Public\Documents`|
|`%PUBLIC%\Downloads`|`C:\Users\Public\Downloads`|
|`%PUBLIC%\Music\Sample Music`|`C:\Users\Public\Music\Sample Music`|
|`%PUBLIC%\Music\Sample Playlists`|`C:\Users\Public\Music\Sample Playlists`|
|`%PUBLIC%\Pictures\Sample Pictures`|`C:\Users\Public\Pictures\Sample Pictures`|
|`%PUBLIC%\RecordedTV.library-ms`|`C:\Users\Public\RecordedTV.library-ms`|
|`%PUBLIC%\Videos`|`C:\Users\Public\Videos`|
|`%PUBLIC%\Videos\Sample Videos`|`C:\Users\Public\Videos\Sample Videos`|
|`%USERPROFILE%`|`C:\Users\UserName`|
|`%USERPROFILE%\AppData\Local`|`C:\Users\UserName\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Users\UserName\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Users\UserName\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>Gennemse listen over udeladelses undtagelser

Du kan hente elementerne på udeladelseslisten ved hjælp af en af følgende metoder:

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- MpCmdRun
- PowerShell
- [Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Udeladelseslisten over ændringer, Gruppepolitik **har,** vises på listerne [i Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md).
>
> De ændringer, der Windows Sikkerhed i **appen, vises ikke** på Gruppepolitik lister.

Hvis du bruger PowerShell, kan du hente listen på to måder:

- Hent status for alle Microsoft Defender Antivirus indstillinger. Hver liste vises på separate linjer, men elementerne på hver liste kombineres til den samme linje.
- Skriv status for alle indstillinger til en variabel, og brug variablen til kun at kalde den specifikke liste, du er interesseret i. Hver brug af `Add-MpPreference` skrives på en ny linje.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider udeladelseslisten ved hjælp af MpCmdRun

Hvis du vil kontrollere udeladelse af det [dedikerede kommandolinjeværktøj mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), skal du bruge følgende kommando:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Kontrol af udeladelse med MpCmdRun kræver Microsoft Defender Antivirus CAMP version 4.18.2111-5.0 (udgivet i december 2021) eller nyere.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Gennemse listen over udeladelsesindstillinger sammen med alle Microsoft Defender Antivirus ved hjælp af PowerShell

Brug følgende cmdlet:

```PowerShell
Get-MpPreference
```

I følgende eksempel er elementerne på listen `ExclusionExtension` fremhævet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="PowerShell-output til Get-MpPreference" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Hent en bestemt udeladelsesliste ved hjælp af PowerShell

Brug følgende kodestykke (angiv hver linje som en separat kommando); **erstat WDAVprefs** med det navn, du vil navngive variablen:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

I følgende eksempel er listen opdelt i nye linjer for hver brug af `Add-MpPreference` cmdlet'en:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="PowerShell-output, der kun viser posterne på udeladelseslisten" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Få mere at vide under [Brug PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus[- og Defender Antivirus-cmdlet'er](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider udeladelseslister med EICAR-testfilen

Du kan validere, at dine udeladelseslister fungerer ved at bruge PowerShell `Invoke-WebRequest` med enten cmdlet'en eller .NET WebClient-klassen for at hente en testfil.

I det følgende PowerShell-kodestykke skal du erstatte `test.txt` med en fil, der overholder dine udeladelsesregler. Hvis du f.eks. har udeladt udvidelsen `.testing` , skal du erstatte `test.txt` med `test.testing`. Hvis du tester en sti, skal du sikre dig, at du kører cmdlet'en inden for den pågældende sti.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Hvis Microsoft Defender Antivirus rapporter om malware, fungerer reglen ikke. Hvis der ikke er nogen rapport om malware, og den downloadede fil findes, fungerer udelukkelsen. Du kan åbne filen for at bekræfte, at indholdet er det samme som det, der beskrives på [webstedet for EICAR-testfilen](http://www.eicar.org/86-0-Intended-use.html).

Du kan også bruge følgende PowerShell-kode, der kalder .NET WebClient-klassen for at downloade testfilen `Invoke-WebRequest` – som med cmdlet'en; `c:\test.txt` erstat med en fil, der overholder den regel, du validerer:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Hvis du ikke har internetadgang, kan du oprette din egen EICAR-testfil ved at skrive EICAR-strengen til en ny tekstfil med følgende PowerShell-kommando:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Du kan også kopiere strengen til en tom tekstfil og forsøge at gemme den med filnavnet eller i den mappe, du forsøger at udelade.

## <a name="see-also"></a>Se også

- [Konfigurere og validere udeladelse i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse af filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl at undgå, når du definerer udeladelse](common-exclusion-mistakes-microsoft-defender-antivirus.md)
