---
title: Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server indeholder automatiske udeladelser baseret på serverrolle. Du kan også tilføje brugerdefinerede udeladelser.
keywords: udeladelser, server, automatisk udeladelse, automatisk, brugerdefineret, scanninger, Microsoft Defender Antivirus
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 890be814be75c303aa42feb5cb7a16cb4f5c3bd9
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320634"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Antivirus på Windows Server 2016 og Windows Server 2019 tilmelder dig automatisk i visse undtagelser, som defineret af din angivne serverrolle. Disse udeladelser vises ikke på de standardlister over udeladelser, der vises i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

Ud over serverrolledefinerede automatiske udeladelser kan du tilføje eller fjerne brugerdefinerede udeladelser. Det gør du ved at læse disse artikler:
- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Et par punkter, du skal være opmærksom på

- Brugerdefinerede udeladelser har forrang frem for automatiske udeladelser.
- Automatiske undtagelser gælder kun for [RTP-scanning (real-time protection).](configure-protection-features-microsoft-defender-antivirus.md) 
- Automatiske udeladelser anvendes ikke under en [fuld, hurtig eller on-demand-scanning](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).
- Brugerdefinerede og duplikerede udeladelser er ikke i konflikt med automatiske udeladelser.
- Microsoft Defender Antivirus bruger DISM-værktøjer (Deployment Image Servicing and Management) til at bestemme, hvilke roller der er installeret på computeren.
- Relevante undtagelser skal angives for software, der ikke er inkluderet i operativsystemet.
- Windows Server 2012 R2 har ikke Microsoft Defender Antivirus som en installerbar funktion. Når du onboarder disse servere til Defender for Endpoint, installerer du Windows Defender Antivirus, og der anvendes standardudeladelser for operativsystemfiler. Udeladelser for serverroller (som angivet nedenfor) gælder dog ikke automatisk, og du skal konfigurere disse udeladelser efter behov. Du kan få mere at vide under [Onboard Windows servere til tjenesten Microsoft Defender for Endpoint](configure-server-endpoints.md).

Denne artikel indeholder en oversigt over undtagelser for Microsoft Defender Antivirus på Windows Server 2016 eller nyere.

Da Microsoft Defender Antivirus er indbygget i Windows Server 2016 og nyere, sker udeladelser for operativsystemfiler og serverroller automatisk. Du kan dog definere brugerdefinerede udeladelser. Du kan også fravælge automatiske undtagelser, hvis det er nødvendigt.

Denne artikel indeholder følgende afsnit:

|Afsnit|Beskrivelse|
|---|---|
|[Automatiske udeladelser på Windows Server 2016 eller nyere](#automatic-exclusions-on-windows-server-2016-or-later)|Beskriver de to primære typer automatiske udeladelser og indeholder en detaljeret liste over automatiske udeladelser|
|[Fravalg af automatiske udeladelser](#opting-out-of-automatic-exclusions)|Indeholder vigtige overvejelser og procedurer, der beskriver, hvordan du fravælger automatiske undtagelser|
|[Definition af brugerdefinerede udeladelser](#defining-custom-exclusions)|Indeholder links til oplysninger om, hvordan du definerer brugerdefinerede udeladelser|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Automatiske udeladelser på Windows Server 2016 eller nyere

På Windows Server 2016 eller nyere skal du ikke definere følgende undtagelser:

- Operativsystemfiler
- Serverroller og eventuelle filer, der tilføjes via serverroller

Da Microsoft Defender Antivirus er indbygget, kræver det ikke undtagelser for operativsystemfiler på Windows Server 2016 eller nyere. Når du kører Windows Server 2016 eller nyere og installerer en rolle, indeholder Microsoft Defender Antivirus desuden automatiske udeladelser for serverrollen og eventuelle filer, der tilføjes under installationen af rollen.

Udeladelser fra operativsystemet og udeladelser af serverroller vises ikke på de standardlister over undtagelser, der vises i [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Automatiske udeladelser for serverroller og operativsystemfiler gælder ikke for Windows Server 2012. Automatiske udeladelser kan gælde, hvis dine servere, der kører Windows Server 2012 R2, er onboardet til Defender for Endpoint. (Se [Onboard Windows-servere til Microsoft Defender for Endpoint-tjenesten](configure-server-endpoints.md)).


### <a name="the-list-of-automatic-exclusions"></a>Listen over automatiske udeladelser

De følgende afsnit indeholder de udeladelser, der leveres med filstier og filtyper til automatiske udeladelser.

#### <a name="default-exclusions-for-all-roles"></a>Standardudeladelser for alle roller

I dette afsnit vises standardudeladelser for alle roller i Windows Server 2016, Windows Server 2019 og Windows Server 2022.

> [!IMPORTANT]
> - Standardplaceringer kan være anderledes end de placeringer, der er beskrevet i denne artikel.
> - Hvis du vil angive udeladelser for software, der ikke er inkluderet som en Windows funktion eller serverrolle, skal du se softwareproducentens dokumentation.

##### <a name="windows-tempedb-files"></a>Windows filer af typen "temp.edb"

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows Update filer eller filer med automatisk opdatering

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>Windows Sikkerhed filer

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>Gruppepolitik filer

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>WINS-filer

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>Frs-udeladelser (File Replication Service)

- Filer i frs-arbejdsmappen (File Replication Service). FRS-arbejdsmappen er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- FRS-databaselogfiler. Mappen med FRS-databaselogfilen er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Den midlertidige FRS-mappe. Den midlertidige mappe er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Frs-forudinstallationsmappen. Denne mappe er angivet i mappen `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- DFSR-databasen (Distributed File System Replication) og arbejdsmapper. Disse mapper er angivet af registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > Hvis du vil se brugerdefinerede placeringer, skal [du se Fravalg af automatiske udeladelser](#opting-out-of-automatic-exclusions).

  - `%systemdrive%\System Volume Information\DFSR\$db_normal$`
  - `%systemdrive%\System Volume Information\DFSR\FileIDTable_*`
  - `%systemdrive%\System Volume Information\DFSR\SimilarityTable_*`
  - `%systemdrive%\System Volume Information\DFSR\*.XML`
  - `%systemdrive%\System Volume Information\DFSR\$db_dirty$`
  - `%systemdrive%\System Volume Information\DFSR\$db_clean$`
  - `%systemdrive%\System Volume Information\DFSR\$db_lostl$`
  - `%systemdrive%\System Volume Information\DFSR\Dfsr.db`
  - `%systemdrive%\System Volume Information\DFSR\*.frx`
  - `%systemdrive%\System Volume Information\DFSR\*.log`
  - `%systemdrive%\System Volume Information\DFSR\Fsr*.jrs`
  - `%systemdrive%\System Volume Information\DFSR\Tmp.edb`

##### <a name="process-exclusions"></a>Behandl udeladelser

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Hyper-V-udeladelser

I følgende tabel vises de filtypeudeladelser, mappeudeladelser og procesudeladelser, der leveres automatisk, når du installerer Hyper-V-rollen.

|Udeladelsestype|Detaljerne|
|---|---|
|Filtyper|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|Mapper|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|Processer|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

##### <a name="sysvol-files"></a>SYSVOL-filer

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


#### <a name="active-directory-exclusions"></a>Active Directory-udeladelser

I dette afsnit vises de udeladelser, der leveres automatisk, når du installerer Active Directory-domæneservices (AD DS).

##### <a name="ntds-database-files"></a>NTDS-databasefiler

Databasefilerne er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>AD DS-transaktionslogfilerne

Transaktionslogfilerne er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>NTDS-arbejdsmappen

Denne mappe er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Behandl udeladelser for AD DS- og AD DS-relaterede supportfiler

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>DHCP-serverudeladelser

I dette afsnit vises de udeladelser, der leveres automatisk, når du installerer DHCP-serverrollen. DHCP-serverfilplaceringerne angives af parametrene *DatabasePath*, *DhcpLogFilePath* og *BackupDatabasePath* i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Udeladelser fra DNS-server

I dette afsnit vises de fil- og mappeudeladelser og de procesudeladelser, der leveres automatisk, når du installerer DNS-serverrollen.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Fil- og mappeudeladelser for DNS-serverrollen

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Behandl udeladelser for DNS-serverrollen

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Fil- og Storage Services-udeladelser

I dette afsnit vises de fil- og mappeudeladelser, der leveres automatisk, når du installerer rollen Filer og Storage Tjenester. De undtagelser, der er angivet nedenfor, omfatter ikke udeladelser for klyngerollen.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Udskrivningsserverudeladelser

I dette afsnit vises de filtypeudeladelser, mappeudeladelser og procesudeladelser, der leveres automatisk, når du installerer rollen Udskriftsserver.

##### <a name="file-type-exclusions"></a>Undtagelser for filtype

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Mappeudeladelser

Denne mappe er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Behandl udeladelser

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Webserverudeladelser

I dette afsnit vises de mappeudeladelser og procesudeladelser, der leveres automatisk, når du installerer rollen Webserver.

##### <a name="folder-exclusions"></a>Mappeudeladelser

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>Behandl udeladelser

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>Deaktiver scanning af filer i mappen Sysvol\Sysvol eller mappen SYSVOL_DFSR\Sysvol

Den aktuelle placering af `Sysvol\Sysvol` mappen eller `SYSVOL_DFSR\Sysvol` og alle undermapperne er filsystemets genfortolkningsmål for replikasætroden. Mapperne `Sysvol\Sysvol` og `SYSVOL_DFSR\Sysvol` bruger som standard følgende placeringer:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Der refereres til stien til det aktive `SYSVOL` i øjeblikket af NETLOGON-sharet og kan bestemmes af værdien SysVol i følgende undernøgle: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

Udelad følgende filer fra denne mappe og alle dens undermapper:

- `*.adm`
- `*.admx`
- `*.adml`
- `Registry.pol`
- `Registry.tmp`
- `*.aas`
- `*.inf`
- `Scripts.ini`
- `*.ins`
- `Oscfilter.ini`

#### <a name="windows-server-update-services-exclusions"></a>Windows Server Update Services undtagelser

I dette afsnit vises de mappeudeladelser, der leveres automatisk, når du installerer rollen Windows Server Update Services (WSUS). Mappen WSUS er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Fravalg af automatiske udeladelser

I Windows Server 2016 og nyere udelukker de foruddefinerede udeladelser, der leveres af opdateringer til Security Intelligence, kun standardstierne for en rolle eller funktion. Hvis du har installeret en rolle eller funktion i en brugerdefineret sti, eller du vil styre sættet af udeladelser manuelt, skal du sørge for at fravælge de automatiske udeladelser, der leveres i Opdateringer til Security Intelligence. Men vær opmærksom på, at de undtagelser, der leveres automatisk, er optimeret til Windows Server 2016 og nyere. Se [Anbefalinger for at definere udeladelser, før du definerer dine udeladelseslister](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

> [!WARNING]
> Hvis du fravalger automatiske undtagelser, kan det påvirke ydeevnen negativt eller medføre beskadigelse af data. De undtagelser, der leveres automatisk, er optimeret til Windows Server 2016, Windows Server 2019 og Windows Server 2022-roller.

Da foruddefinerede udeladelser kun **udelader standardstier**, skal du tilføje udeladelser manuelt, hvis du flytter NTDS- og SYSVOL-mapper til et andet drev eller en anden sti end *den oprindelige sti*. Se [Konfigurer listen over undtagelser baseret på mappenavn eller filtypenavn](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Du kan deaktivere de automatiske udeladelseslister med Gruppepolitik, PowerShell-cmdlet'er og WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Brug Gruppepolitik til at deaktivere listen over automatisk udeladelser på Windows Server 2016, Windows Server 2019 og Windows Server 2022

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

2. I **Gruppepolitik Administrationseditor** skal du gå til **Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Udeladelser**.

4. Dobbeltklik på **Slå Automatisk udeladelse fra**, og angiv indstillingen til **Aktiveret**. Vælg derefter **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Brug PowerShell-cmdlet'er til at deaktivere listen over automatiske udeladelser på Windows Server

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Du kan få mere at vide i følgende ressourcer:

- [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Brug PowerShell sammen med Microsoft Defender Antivirus](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Brug WMI (Windows Management Instruction) til at deaktivere listen med automatiske udeladelser på Windows Server

Brug metoden **Set** for klassen [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) til følgende egenskaber:

```WMI
DisableAutoExclusions
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Definition af brugerdefinerede udeladelser

Hvis det er nødvendigt, kan du tilføje eller fjerne brugerdefinerede udeladelser. Det gør du ved at se følgende artikler:

- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

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

- [Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer og valider udeladelser for filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl, der skal undgås, når du definerer udeladelser](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Tilpas, start og gennemse resultaterne af Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
