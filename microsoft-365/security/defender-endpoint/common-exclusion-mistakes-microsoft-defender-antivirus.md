---
title: Almindelige fejl at undgå, når du definerer udeladelse
description: Undgå almindelige fejl, når du definerer udeladelse for Microsoft Defender Antivirus scanninger.
keywords: udeladelse, filer, filtypenavn, filtype, mappenavn, filnavn, scanninger
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
ms.date: 10/19/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 73234fd929406da475455baf21fbbf463216c660
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63599355"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>Almindelige fejl at undgå, når du definerer udeladelse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan definere en udeladelsesliste for elementer, du ikke vil Microsoft Defender Antivirus at scanne. Sådanne udeladte elementer kan indeholde trusler, der gør din enhed sårbar. I denne artikel beskrives en almindelig fejl, du bør undgå, når du definerer udeladelse.

Før du definerer dine [udeladelseslister, skal Anbefalinger oplysninger om definition af udeladelse](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>Udelade bestemte elementer, der er tillid til

Visse filer, filtyper, mapper eller processer bør ikke udelukkes fra scanning, selvom du har tillid til, at de ikke er skadelige.

Du må ikke definere udeladelse for mappeplaceringer, filtypenavne og processer, der er angivet i de følgende afsnit:
- Mappeplaceringer
- Filtypenavne
- Processer

### <a name="folder-locations"></a>Mappeplaceringer

Generelt kan du ikke definere udeladelse for følgende mappeplaceringer:

`%systemdrive%`

`C:`

`C:\`

`C:\*`

`%ProgramFiles%\Java`

`C:\Program Files\Java`

`%ProgramFiles%\Contoso\`

`C:\Program Files\Contoso\`

`%ProgramFiles(x86)%\Contoso\`

`C:\Program Files (x86)\Contoso\`

`C:\Temp`

`C:\Temp\`

`C:\Temp\*`

`C:\Users\`

`C:\Users\*`

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**Bemærk følgende undtagelse for SharePoint**: Udelad, `C:\Users\ServiceAccount\AppData\Local\Temp` når du bruger [antivirusbeskyttelse på filniveau i SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**Bemærk følgende undtagelse for SharePoint**: Udelad, `C:\Users\Default\AppData\Local\Temp` når du bruger [antivirusbeskyttelse på filniveau i SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`%Windir%\Prefetch`

`C:\Windows\Prefetch`

`C:\Windows\Prefetch\`

`C:\Windows\Prefetch\*`

`%Windir%\System32\Spool`

`C:\Windows\System32\Spool`

`C:\Windows\System32\CatRoot2`
`%Windir%\Temp`

`C:\Windows\Temp`

`C:\Windows\Temp\`

`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Linux- og macOS-platforme

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>Filtypenavne

Generelt kan du ikke definere udeladelse for følgende filtypenavne:

`.7z`

`.bat`

`.bin`

`.cab`

`.cmd`

`.com`

`.cpl`

`.dll`

`.exe`

`.fla`

`.gif`

`.gz`

`.hta`

`.inf`

`.java`

`.jar`

`.job`

`.jpeg`

`.jpg`

`.js`

`.ko`

`.ko.gz`

`.msi`

`.ocx`

`.png`

`.ps1`

`.py`

`.rar`

`.reg`

`.scr`

`.sys`

`.tar`

`.tmp`

`.url`

`.vbe`

`.vbs`

`.wsf`

`.zip`

### <a name="processes"></a>Processer

Generelt kan du ikke definere udeladelse for følgende processer:

`AcroRd32.exe`

`bitsadmin.exe`

`excel.exe`

`iexplore.exe`

`java.exe`

`outlook.exe`

`psexec.exe`

`powerpnt.exe`

`powershell.exe`

`schtasks.exe`

`svchost.exe`

`wmic.exe`

`winword.exe`

`wuauclt.exe`

`addinprocess.exe`

`addinprocess32.exe`

`addinutil.exe`

`bash.exe`

`bginfo.exe`

`cdb.exe`

`csi.exe`

`dbghost.exe`

`dbgsvc.exe`

`dnx.exe`

`dotnet.exe`

`fsi.exe`

`fsiAnyCpu.exe`

`kd.exe`

`ntkd.exe`

`lxssmanager.dll`

`msbuild.exe`

`mshta.exe`

`ntsd.exe`

`rcsi.exe`

`system.management.automation.dll`

`windbg.exe`

#### <a name="linux-and-macos-platforms"></a>Linux- og macOS-platforme

`bash`

`sh`

`python` og `python3`

`java`

`zsh`

> [!NOTE]
> Du kan vælge at udelade filtyper, `.gif`f.eks. , `.jpg`, `.png` `.jpeg`eller hvis dit miljø har en moderne, opdateret software med en streng opdateringspolitik for at håndtere eventuelle sårbarheder.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>Kun bruge filnavnet på udeladelseslisten

Malware kan have samme navn som navnet på en fil, du har tillid til, og som du vil udelukke fra scanning. For at undgå at scanne potentielt malware skal du derfor bruge en fuldt kvalificeret sti til den fil, du vil udelukke, i stedet for kun at bruge filnavnet. Hvis du f.eks. vil udelukke fra `Filename.exe` scanning, skal du bruge hele stien til filen, f.eks `C:\program files\contoso\Filename.exe`. .

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>Brug af en enkelt udeladelsesliste til flere serverarbejdsbelastninger

Brug ikke en enkelt udeladelsesliste til at definere udeladelse for flere serverarbejdsbelastninger. Opdele udeladelseslisterne for forskellige program- eller tjenestearbejdsbelastninger i flere udeladelseslister. Udeladelseslisten for din arbejdsbelastning for IIS-serveren skal f.eks. være forskellig fra udeladelseslisten for din SQL Server arbejdsbelastning.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>Brug af forkerte miljøvariabler som jokertegn i filnavnet og mappestien eller udeladelseslisterne for filtypenavne

Microsoft Defender Antivirus tjeneste kører i systemkontekst ved hjælp af LocalSystem-kontoen, hvilket betyder, at den henter oplysninger fra systemmiljøvariablen og ikke fra brugermiljøvariablen. Brug af miljøvariabler som et jokertegn i udeladelseslister er begrænset til systemvariabler og dem, der gælder for processer, der kører som en NT AUTHORITY\SYSTEM-konto. Brug derfor ikke brugermiljøvariabler som jokertegn, når du tilføjer Microsoft Defender Antivirus og procesudetagelser. Se tabellen under [Systemmiljøvariabler](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) for at få en komplet liste over systemmiljøvariabler.

Se [Brug jokertegn i filnavnet](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) og mappestien eller udeladelseslisterne for filtypenavnet for at få oplysninger om, hvordan du bruger jokertegn på udeladelseslister.
