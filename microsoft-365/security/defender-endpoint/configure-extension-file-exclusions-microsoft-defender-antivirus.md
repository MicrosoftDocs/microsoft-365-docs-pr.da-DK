---
title: Konfigurer og valider udeladelser baseret på filtypenavn, navn eller placering
description: Udelad filer fra Microsoft Defender Antivirus scanninger baseret på filtypenavnet, filnavnet eller placeringen.
keywords: udeladelser, filer, filtypenavn, filtype, mappenavn, filnavn, scanninger
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 864d67aeaa84713b1b2126b017fadacd0e43dc7a
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622992"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>Konfigurer og valider udeladelser baseret på filtypenavn og mappeplacering

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan definere udeladelser for Microsoft Defender Antivirus, der gælder for [planlagte scanninger](schedule-antivirus-scans.md), [efter behovsscanninger](run-scan-microsoft-defender-antivirus.md) og [altid aktiveret beskyttelse og overvågning i realtid](configure-real-time-protection-microsoft-defender-antivirus.md). **Generelt skal du ikke anvende undtagelser**. Hvis du har brug for at anvende undtagelser, kan du vælge mellem flere forskellige typer:

- Undtagelser baseret på filtypenavne og mappeplaceringer (beskrevet i denne artikel)
- [Udeladelser for filer, der åbnes af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> Microsoft Defender Antivirus undtagelser gælder ikke for andre Microsoft Defender for Endpoint funktioner, f.eks[. regler for reduktion af angrebsoverflader og](/microsoft-365/security/defender-endpoint/attack-surface-reduction) [kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders). Filer, som du udelader ved hjælp af de metoder, der er beskrevet i denne artikel, kan stadig udløse Slutpunktsregistrering og -svar beskeder og andre registreringer.
> Hvis du vil udelade filer bredt, skal du føje dem til Microsoft Defender for Endpoint [brugerdefinerede indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators).

## <a name="before-you-begin"></a>Før du begynder

Se [Anbefalinger for at definere udeladelser, før du definerer dine udeladelseslister](configure-exclusions-microsoft-defender-antivirus.md).

## <a name="exclusion-lists"></a>Lister over udeladelser

Hvis du vil udelade visse filer fra Microsoft Defender Antivirus scanninger, skal du ændre dine udeladelseslister. Microsoft Defender Antivirus omfatter mange automatiske undtagelser, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier og -situationer.

> [!NOTE]
> Undtagelser gælder også for potentielt uønskede apps(PUA)-registreringer.
>
> Automatiske udeladelser gælder kun for Windows Server 2016 og nyere. Disse udeladelser er ikke synlige i appen Windows Sikkerhed og i PowerShell.

I følgende tabel vises nogle eksempler på undtagelser, der er baseret på filtypenavnet og mappeplaceringen.

|Udelukkelse|Eksempler|Udeladelsesliste|
|---|---|---|
|Alle filer med et bestemt filtypenavn|Alle filer med den angivne udvidelse, hvor som helst på maskinen. <p> Gyldig syntaks: `.test` og `test`|Undtagelser for filtypenavne|
|Alle filer under en bestemt mappe|Alle filer under mappen `c:\test\sample`|Fil- og mappeudeladelser|
|En bestemt fil i en bestemt mappe|Kun filen `c:\sample\sample.test`|Fil- og mappeudeladelser|
|En bestemt proces|Den eksekverbare fil `c:\test\process.exe`|Fil- og mappeudeladelser|

## <a name="characteristics-of-exclusion-lists"></a>Egenskaber for udeladelseslister

- Mappeudeladelser gælder for alle filer og mapper under den pågældende mappe, medmindre undermappen er et genfortolkningspunkt. Undermapper til genfortolkning af punkt skal udelades separat.
- Filtypenavne gælder for alle filnavne med det definerede filtypenavn, hvis der ikke er defineret en sti eller mappe.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>Vigtige noter om undtagelser baseret på filtypenavne og mappeplaceringer

- Hvis du bruger jokertegn, f.eks. stjernen (\*), ændres den måde, som udeladelsesreglerne fortolkes på. Se afsnittet [Brug jokertegn i filnavnet og mappestien eller liste over udeladelser af filtypenavne](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) for at få vigtige oplysninger om, hvordan jokertegn fungerer.

- Undlad at udelade tilknyttede netværksdrev. Angiv den faktiske netværkssti.

- Mapper, der er genfortolkningspunkter, som oprettes, når tjenesten Microsoft Defender Antivirus starter, og som er føjet til listen over undtagelser, medtages ikke. Genstart tjenesten (ved at genstarte Windows), så nye genfortolkningspunkter genkendes som en gyldig destination for udeladelse.

- Undtagelser gælder for [planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [efter behovsscanninger](run-scan-microsoft-defender-antivirus.md) og [beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md), men ikke på tværs af Defender for Endpoint. Hvis du vil definere udeladelser på tværs af Defender for Endpoint, skal du bruge [brugerdefinerede indikatorer](manage-indicators.md).

- Lokale ændringer, der foretages af listerne (af brugere med administratorrettigheder, herunder ændringer foretaget med PowerShell og WMI), flettes som standard med listerne som defineret (og installeret) af Gruppepolitik, Configuration Manager eller Intune. De Gruppepolitik lister har forrang, når der er konflikter. Desuden er ændringer af listen over udeladelser, der er foretaget med Gruppepolitik, synlige i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

- Hvis du vil tillade, at lokale ændringer tilsidesætter administrerede installationsindstillinger, [skal du konfigurere, hvordan lister over lokalt og globalt definerede udeladelser flettes](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>Konfigurer listen over udeladelser baseret på mappenavn eller filtypenavn

Du kan vælge mellem flere metoder til at definere udeladelser for Microsoft Defender Antivirus.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug Intune til at konfigurere undtagelser for filnavn, mappe eller filtypenavn

Se følgende artikler:

- [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure)
- [Microsoft Defender Antivirus indstillinger for enhedsbegrænsning for Windows 10 i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug Configuration Manager til at konfigurere undtagelser for filnavn, mappe eller filtypenavn

Se [Sådan opretter og installerer du antimalwarepolitikker: Indstillinger for udeladelse for at](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) få oplysninger om konfiguration af Microsoft Endpoint Manager (aktuel forgrening).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>Brug Gruppepolitik til at konfigurere udeladelser for mapper eller filtypenavne

> [!NOTE]
> Hvis du angiver en fuldt kvalificeret sti til en fil, er det kun den pågældende fil, der udelades. Hvis der er defineret en mappe i udeladelsesmappen, udelades alle filer og undermapper under den pågældende mappe.

1. Åbn [administrationskonsollen Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **Gruppepolitik Management Editor** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Windows Defender Antivirus** \> **Udeladelser**.

4. Åbn indstillingen **Stiudeladelser** til redigering, og tilføj dine udeladelser.
    1. Angiv indstillingen til **Aktiveret**.
    2. Under afsnittet **Indstillinger** skal du vælge **Vis**.
    3. Angiv hver mappe på sin egen linje under kolonnen **Værdinavn** .
    4. Hvis du angiver en fil, skal du sørge for at angive en fuldt gyldig sti til filen, herunder drevbogstavet, mappestien, filnavnet og filtypenavnet.
    5. Angiv **0** i kolonnen **Værdi** .

5. Vælg **OK**.

6. Åbn indstillingen **Filtypenavneudeladelser** til redigering, og tilføj dine udeladelser.
    1. Angiv indstillingen til **Aktiveret**.
    2. Under afsnittet **Indstillinger** skal du vælge **Vis**.
    3. Angiv hvert filtypenavn på sin egen linje under kolonnen **Værdinavn** .
    4. Angiv **0** i kolonnen **Værdi** .

7. Vælg **OK**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug PowerShell-cmdlet'er til at konfigurere undtagelser for filnavn, mappe eller filtypenavn

Brug af PowerShell til at tilføje eller fjerne udeladelser for filer, der er baseret på filtypenavnet, placeringen eller filnavnet, kræver brug af en kombination af tre cmdlet'er og den relevante parameter for udeladelseslisten. Cmdlet'erne er alle i [Defender-modulet](/powershell/module/defender/).

Formatet for cmdlet'erne er som følger:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

I følgende tabel vises de cmdlet'er, du kan bruge i delen `<cmdlet>` af PowerShell-cmdlet'en:

|Konfigurationshandling|PowerShell-cmdlet|
|:---|:---|
|Opret eller overskriv listen|`Set-MpPreference`|
|Føj til listen|`Add-MpPreference`|
|Fjern element fra listen|`Remove-MpPreference`|

I følgende tabel vises de værdier, du kan bruge i delen `<exclusion list>` af PowerShell-cmdlet'en:

|Udeladelsestype|PowerShell-parameter|
|---|---|
|Alle filer med et angivet filtypenavn|`-ExclusionExtension`|
|Alle filer under en mappe (herunder filer i undermapper) eller en bestemt fil|`-ExclusionPath`|

> [!IMPORTANT]
> Hvis du har oprettet en liste, enten med `Set-MpPreference` eller `Add-MpPreference`, overskrives den eksisterende liste ved hjælp af `Set-MpPreference` cmdlet'en igen.

Følgende kodestykke vil f.eks. medføre, at Microsoft Defender Antivirus scanninger udelader alle filer med filtypenavnet`.test`:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug WMI (Windows Management Instrumentation) til at konfigurere udeladelser for filnavn, mappe eller filtypenavn

Brug [metoderne Set, Add og Remove for klassen MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) for følgende egenskaber:

```WMI
ExclusionExtension
ExclusionPath
```

Brug af **Set**, **Add** og **Remove** svarer til deres kolleger i PowerShell: `Set-MpPreference`, `Add-MpPreference`og `Remove-MpPreference`.

> [!TIP]
> Du kan få flere oplysninger [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>Brug appen Windows Sikkerhed til at konfigurere undtagelser for filnavn, mappe eller filtypenavn

Se [Tilføj udeladelser i appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md) for at få en vejledning.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Brug jokertegn i filnavnet og mappestien eller udvidelsesudeladelseslisterne

Du kan bruge stjernen `*`, spørgsmålstegnet `?`eller miljøvariabler (f.eks. `%ALLUSERSPROFILE%`) som jokertegn, når du definerer elementer på listen over undtagelser for filnavnet eller mappestien. Den måde, hvorpå disse jokertegn fortolkes, adskiller sig fra deres normale brug i andre apps og sprog. Sørg for at læse dette afsnit for at forstå deres specifikke begrænsninger.

> [!IMPORTANT]
> Der er vigtige begrænsninger og forbrugsscenarier for disse jokertegn:
>
> - Brug af miljøvariabler er begrænset til computervariabler og dem, der gælder for processer, der kører som en NT AUTHORITY\SYSTEM-konto.
> - Du kan højst bruge seks jokertegn pr. post.
> - Du kan ikke bruge et jokertegn i stedet for et drevbogstav.
> - En stjerne `*` i en mappeudeladelse står på plads for en enkelt mappe. Brug flere forekomster af `\*\` til at angive flere indlejrede mapper med uspecificerede navne.
> - I øjeblikket understøtter Microsoft Endpoint Configuration Manager ikke jokertegn (f.eks. `*` eller `?`).
    
I følgende tabel beskrives, hvordan jokertegnene kan bruges, og der vises nogle eksempler.

<br/><br/>

|Wildcard|Eksempler|
|---|---|
|`*` (stjerne) <p> I **medtagelser af filnavn og filtypenavn** erstatter stjernen et vilkårligt antal tegn og gælder kun for filer i den sidste mappe, der er defineret i argumentet. <p> I **mappeudeladelser** erstatter stjernen en enkelt mappe. Brug flere `*` med mappestreger `\` til at angive flere indlejrede mapper. Når antallet af jokertegn og navngivne mapper er matchet, medtages alle undermapper også.|`C:\MyData\*.txt` Omfatter `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` inkluderer alle filer i `C:\somepath\Archives\Data` og dens undermapper og `C:\somepath\Authorized\Data` dens undermapper <p> `C:\Serv\*\*\Backup` inkluderer alle filer i `C:\Serv\Primary\Denied\Backup` og dens undermapper og `C:\Serv\Secondary\Allowed\Backup` dens undermapper|
|`?` (spørgsmålstegn)  <p> I **medtagelser af filnavn og filtypenavn** erstatter spørgsmålstegnet et enkelt tegn og gælder kun for filer i den sidste mappe, der er defineret i argumentet. <p> I **mappeudeladelser** erstatter spørgsmålstegnet et enkelt tegn i et mappenavn. Når antallet af jokertegn og navngivne mapper er matchet, medtages alle undermapper også.|`C:\MyData\my?.zip` Omfatter `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` inkluderer alle filer i `C:\somepath\P\Data` og dens undermapper  <p> `C:\somepath\test0?\Data` indeholder alle filer i `C:\somepath\test01\Data` og dens undermapper|
|Miljøvariabler <p> Den definerede variabel udfyldes som en sti, når udeladelse evalueres.|`%ALLUSERSPROFILE%\CustomLogFiles` omfatter `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> Hvis du blander et argument for filudeladelse med et mappeudeladelsesargument, stopper reglerne ved filargumentet i den tilsvarende mappe og søger ikke efter filforekomster i nogen undermapper.
>
> Du kan f.eks. udelade alle filer, der starter med "dato" i mapperne `c:\data\final\marked` og `c:\data\review\marked` ved hjælp af regelargumentet `c:\data\*\marked\date*`.
>
> Dette argument stemmer dog ikke overens med nogen filer i undermapper under `c:\data\final\marked` eller `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>Systemmiljøvariabler

I følgende tabel vises og beskrives miljøvariabler for systemkontoen.

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

## <a name="review-the-list-of-exclusions"></a>Gennemse listen over udeladelser

Du kan hente elementerne på listen over undtagelser ved hjælp af en af følgende metoder:

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- [MpCmdRun](command-line-arguments-microsoft-defender-antivirus.md)
- [PowerShell](/powershell/module/defender)
- [Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> Ændringer af listen over udeladelser, der er foretaget med Gruppepolitik **, vises** på listerne i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).
>
> Ændringer, der er foretaget i Windows Sikkerhed-appen, **vises ikke** på Gruppepolitik-listerne.

Hvis du bruger PowerShell, kan du hente listen på to måder:

- Hent status for alle Microsoft Defender Antivirus indstillinger. Hver liste vises på separate linjer, men elementerne på hver liste kombineres til den samme linje.
- Skriv status for alle indstillinger til en variabel, og brug denne variabel til kun at kalde den bestemte liste, du er interesseret i. Hver brug af skrives `Add-MpPreference` til en ny linje.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>Valider listen over undtagelser ved hjælp af MpCmdRun

Hvis du vil kontrollere udeladelser med det dedikerede [kommandolinjeværktøj mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md), skal du bruge følgende kommando:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> Kontrol af udeladelser med MpCmdRun kræver Microsoft Defender Antivirus CAMP version 4.18.2111-5.0 (udgivet i december 2021) eller nyere.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>Gennemse listen over undtagelser sammen med alle andre indstillinger for Microsoft Defender Antivirus ved hjælp af PowerShell

Brug følgende cmdlet:

```PowerShell
Get-MpPreference
```

I følgende eksempel er elementerne på `ExclusionExtension` listen fremhævet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="PowerShell-output til Get-MpPreference" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>Hent en bestemt liste over udeladelser ved hjælp af PowerShell

Brug følgende kodestykke (angiv hver linje som en separat kommando). erstat **WDAVprefs** med den etiket, du vil navngive variablen:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

I følgende eksempel opdeles listen i nye linjer for hver brug af cmdlet'en `Add-MpPreference` :

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="PowerShell-output, der kun viser posterne på listen over undtagelser" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

Du kan få flere oplysninger under [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)- og [Defender Antivirus-cmdlet'er](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider udeladelseslister med EICAR-testfilen

Du kan validere, at dine udeladelseslister fungerer ved hjælp af PowerShell med enten `Invoke-WebRequest` cmdlet'en eller .NET WebClient-klassen til at downloade en testfil.

I følgende PowerShell-kodestykke skal du erstatte `test.txt` med en fil, der overholder dine udelukkelsesregler. Hvis du f.eks. har udeladt filtypenavnet `.testing` , skal du erstatte `test.txt` med `test.testing`. Hvis du tester en sti, skal du sikre dig, at du kører cmdlet'en i den pågældende sti.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

Hvis Microsoft Defender Antivirus rapporterer malware, fungerer reglen ikke. Hvis der ikke er nogen rapport over malware, og den downloadede fil findes, fungerer udelukkelsen. Du kan åbne filen for at bekræfte, at indholdet er det samme som det, der er beskrevet på [webstedet for EICAR-testfilen](http://www.eicar.org/86-0-Intended-use.html).

Du kan også bruge følgende PowerShell-kode, der kalder klassen .NET WebClient for at downloade testfilen – ligesom med cmdlet'en `Invoke-WebRequest` . Erstat `c:\test.txt` med en fil, der overholder den regel, du validerer:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

Hvis du ikke har internetadgang, kan du oprette din egen EICAR-testfil ved at skrive EICAR-strengen til en ny tekstfil med følgende PowerShell-kommando:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

Du kan også kopiere strengen til en tom tekstfil og forsøge at gemme den med filnavnet eller i den mappe, du forsøger at udelade.

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

- [Konfigurer og valider udeladelser i Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl, der skal undgås, når du definerer udeladelser](common-exclusion-mistakes-microsoft-defender-antivirus.md)
