---
title: Almindelige fejl, der skal undgås, når du definerer udeladelser
description: Undgå almindelige fejl, når du definerer udeladelser for Microsoft Defender Antivirus scanninger.
keywords: udeladelser, filer, filtypenavn, filtype, mappenavn, filnavn, scanninger
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 06/16/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 99d59c2027d3b34ad5c9c19444a51dd08cc22276
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128652"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Almindelige fejl, der skal undgås, når du definerer udeladelser

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender for Endpoint Plan 1
- Microsoft Defender Antivirus 

**Platforme**

- Windows
- macOS
- Linux

> [!IMPORTANT]
> **Tilføj undtagelser med forsigtighed**. Undtagelser for Microsoft Defender Antivirus scanninger reducerer beskyttelsesniveauet for enheder.

Du kan definere en udeladelsesliste for elementer, som du ikke vil scanne Microsoft Defender Antivirus. Udeladte elementer kan dog indeholde trusler, der gør din enhed sårbar. I denne artikel beskrives nogle almindelige fejl, som du bør undgå, når du definerer udeladelser.

Før du definerer dine lister over udeladelser, [skal du se Anbefalinger for at definere udeladelser](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Udeladelse af visse elementer, der er tillid til

Visse filer, filtyper, mapper eller processer bør ikke udelukkes fra scanning, selvom du har tillid til, at de ikke er skadelige.

Definer ikke udeladelser for mappeplaceringer, filtypenavne og processer, der er angivet i følgende afsnit:

- [Mappeplaceringer](#folder-locations)
- [Filtypenavne](#file-extensions)
- [Processer](#processes)

### <a name="folder-locations"></a>Mappeplaceringer

> [!IMPORTANT]
> Visse mapper bør ikke udelukkes fra scanninger, fordi de ender med at blive mapper, hvor ondsindede filer kan blive droppet.

Generelt skal du ikke definere udeladelser for følgende mappeplaceringer:

- `%systemdrive%`
- `C:`, `C:\`eller `C:\*`
- `%ProgramFiles%\Java` Eller `C:\Program Files\Java`
- `%ProgramFiles%\Contoso\`, `C:\Program Files\Contoso\`, `%ProgramFiles(x86)%\Contoso\`eller `C:\Program Files (x86)\Contoso\`
- `C:\Temp`, `C:\Temp\`eller `C:\Temp\*`
- `C:\Users\` Eller `C:\Users\*`
- `C:\Users\<UserProfileName>\AppData\Local\Temp\` eller `C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`. **Bemærk følgende vigtige undtagelser for SharePoint**: **Udelad** `C:\Users\ServiceAccount\AppData\Local\Temp` eller `C:\Users\Default\AppData\Local\Temp` brug [antivirusbeskyttelse på filniveau i SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).
- `%Windir%\Prefetch`, `C:\Windows\Prefetch`, `C:\Windows\Prefetch\`eller `C:\Windows\Prefetch\*`
- `%Windir%\System32\Spool` Eller `C:\Windows\System32\Spool`
- `C:\Windows\System32\CatRoot2`
- `%Windir%\Temp`, `C:\Windows\Temp`, `C:\Windows\Temp\`eller `C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Linux- og macOS platforme

Generelt skal du ikke definere udeladelser for følgende mappeplaceringer:

- `/`
- `/bin` Eller `/sbin`
- `/usr/lib`

### <a name="file-extensions"></a>Filtypenavne

> [!IMPORTANT]
> Visse filtypenavne bør ikke udelades, fordi de kan være filtyper, der bruges i et angreb.

Generelt skal du ikke definere undtagelser for følgende filtypenavne:

- `.7z`
- `.bat`
- `.bin`
- `.cab`
- `.cmd`
- `.com`
- `.cpl`
- `.dll`
- `.exe`
- `.fla`
- `.gif`
- `.gz`
- `.hta`
- `.inf`
- `.java`
- `.jar`
- `.job`
- `.jpeg`
- `.jpg`
- `.js`
- `.ko` Eller `.ko.gz`
- `.msi`
- `.ocx`
- `.png`
- `.ps1`
- `.py`
- `.rar`
- `.reg`
- `.scr`
- `.sys`
- `.tar`
- `.tmp`
- `.url`
- `.vbe`
- `.vbs`
- `.wsf`
- `.zip`

### <a name="processes"></a>Processer

> [!IMPORTANT]
> Visse processer bør ikke udelukkes, fordi de bliver brugt under angreb.

Generelt skal du ikke definere undtagelser for følgende processer:

- `AcroRd32.exe`
- `addinprocess.exe`
- `addinprocess32.exe`
- `addinutil.exe`
- `bash.exe`
- `bginfo.exe`
- `bitsadmin.exe`
- `cdb.exe`
- `csi.exe`
- `dbghost.exe`
- `dbgsvc.exe`
- `dnx.exe`
- `dotnet.exe`
- `excel.exe`
- `fsi.exe`
- `fsiAnyCpu.exe`
- `iexplore.exe`
- `java.exe`
- `kd.exe`
- `lxssmanager.dll`
- `msbuild.exe`
- `mshta.exe`
- `ntkd.exe`
- `ntsd.exe`
- `outlook.exe`
- `psexec.exe`
- `powerpnt.exe`
- `powershell.exe`
- `rcsi.exe`
- `svchost.exe`
- `schtasks.exe`
- `system.management.automation.dll`
- `windbg.exe`
- `winword.exe`
- `wmic.exe`
- `wuauclt.exe`

> [!NOTE]
> Du kan vælge at udelade filtyper, f.eks `.gif`. , `.jpg`, `.jpeg`, eller `.png` hvis dit miljø har en moderne, opdateret software med en streng opdateringspolitik til håndtering af eventuelle sikkerhedsrisici.

#### <a name="linux-and-macos-platforms"></a>Linux- og macOS platforme

Generelt skal du ikke definere undtagelser for følgende processer:

- `bash`
- `java`
- `python` Og `python3`
- `sh`
- `zsh`

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Brug kun filnavnet på listen over undtagelser

Malware kan have samme navn som den fil, du har tillid til, og som du vil udelukke fra scanning. For at undgå at udelukke potentiel malware fra scanning skal du derfor bruge en fuldt kvalificeret sti til den fil, du vil udelade, i stedet for kun at bruge filnavnet. Hvis du f.eks. vil udelade `Filename.exe` fra scanning, skal du bruge hele stien til filen, f.eks `C:\program files\contoso\Filename.exe`. .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Brug af en enkelt udeladelsesliste til arbejdsbelastninger på flere servere

Brug ikke en enkelt udeladelsesliste til at definere udeladelser for flere serverarbejdsbelastninger. Opdel udeladelser for forskellige program- eller tjenestearbejdsbelastninger i flere udeladelseslister. Listen over undtagelser for IIS Server-arbejdsbelastningen skal f.eks. være forskellig fra listen over undtagelser for din SQL Server arbejdsbelastning.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Brug af forkerte miljøvariabler som jokertegn i filnavnet og mappestien eller udvidelsesudeladelseslisterne

Microsoft Defender Antivirus Tjeneste kører i systemkontekst ved hjælp af LocalSystem-kontoen, hvilket betyder, at den henter oplysninger fra systemmiljøvariablen og ikke fra brugermiljøvariablen. Brugen af miljøvariabler som jokertegn på udeladelseslister er begrænset til systemvariabler og dem, der gælder for processer, der kører som en NT AUTHORITY\SYSTEM-konto. Brug derfor ikke variabler i brugermiljøet som jokertegn, når du tilføjer Microsoft Defender Antivirus mappe og procesudeladelser. Se tabellen under [Systemmiljøvariabler](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) for at få en komplet liste over systemmiljøvariabler.

Se [Brug jokertegn på filnavns- og mappestien eller i lister over undtagelser for filtypenavne](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) for at få oplysninger om, hvordan du bruger jokertegn på udeladelseslister.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
