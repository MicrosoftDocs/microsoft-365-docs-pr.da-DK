---
title: Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server omfatter automatisk udeladelse baseret på serverrolle. Du kan også tilføje brugerdefinerede udeladelser.
keywords: udeladelse, server, automatisk udeladelse, automatisk, brugerdefineret, scanninger, Microsoft Defender Antivirus
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
ms.date: 02/04/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 442172afc9caf5dbd2af8c91cda531494fabd05d
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63606492"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Microsoft Defender Antivirus på Windows Server 2016 og Windows Server 2019 automatisk dig i visse undtagelser som defineret af din angivne serverrolle. Disse udeladelseslister vises ikke på de standard udeladelseslister, der vises [i Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md).

Ud over automatisk udeladelse af serverroller kan du tilføje eller fjerne brugerdefinerede udeladelser. Det gør du ved at læse følgende artikler:
- [Konfigurere og validere udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse af filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>Et par point at huske på

Husk følgende vigtige punkter:

- Brugerdefinerede udeladelser tilsidesætter automatiske udeladelser.
- Automatisk udeladelse gælder kun for scanning i realtid (RTP). Automatiske udeladelser bliver ikke imødekommet under en fuld, hurtig eller on-demand-scanning.
- Brugerdefinerede og dublerede udeladelseskonflikter er ikke modstridende med automatiske udeladelser.
- Microsoft Defender Antivirus bruger DISM-værktøjerne (Deployment Image Servicing and Management) til at bestemme, hvilke roller der er installeret på computeren.
- Windows Server 2012 R2 ikke har en Microsoft Defender Antivirus som en funktion, der kan installeres. Når du onboarder disse servere til Defender til Slutpunkt, skal du installere Windows Defender Antivirus, og standard udeladelse af operativsystemfiler anvendes. Udeladelse af serverroller (som angivet nedenfor) gælder dog ikke automatisk, og du bør konfigurere disse undtagelser efter behov. Du kan få mere at [vide Windows onboard Windows serverne til Microsoft Defender for Endpoint-tjenesten](configure-server-endpoints.md).

Denne artikel indeholder en oversigt over udeladelse af Microsoft Defender Antivirus på Windows Server 2016 eller nyere.

Da Microsoft Defender Antivirus er indbygget i Windows Server 2016 og nyere, sker udeladelse af operativsystemfiler og serverroller automatisk. Du kan dog definere brugerdefinerede undtagelser. Du kan også fravælge automatisk udeladelse, hvis det er nødvendigt.

Denne artikel indeholder følgende afsnit:

<br/><br/>

|Sektion|Beskrivelse|
|---|---|
|[Automatisk udeladelse på Windows Server 2016 eller nyere](#automatic-exclusions-on-windows-server-2016-or-later)|Beskriver de to vigtigste typer automatiske udeladelse og indeholder en detaljeret liste over automatiske udeladelsestyper|
|[Framelde dig automatiske udeladelse](#opting-out-of-automatic-exclusions)|Omfatter vigtige overvejelser og procedurer, der beskriver, hvordan du fravælger automatiske udeladelser|
|[Definition af brugerdefinerede udeladelses undtagelser](#defining-custom-exclusions)|Indeholder links til trinvise oplysninger til at definere brugerdefinerede udeladelser|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>Automatisk udeladelse på Windows Server 2016 eller nyere

På Windows Server 2016 eller nyere, bør du ikke behøver at definere følgende undtagelser:

- Operativsystemfiler
- Serverroller og alle filer, der tilføjes via serverroller

Da Microsoft Defender Antivirus er indbygget, kræver det ikke undtagelser for operativsystemfiler på Windows Server 2016 eller nyere. Når du kører Windows Server 2016 eller nyere og installerer en rolle, inkluderer Microsoft Defender Antivirus desuden automatiske udeladelser for serverrollen og alle filer, der tilføjes, når du installerer rollen.

Udeladelse af operativsystem og udeladelse af serverroller vises ikke på de standard udeladelseslister, der vises [i Windows Sikkerhed app](microsoft-defender-security-center-antivirus.md).

> [!NOTE]
> Automatisk udeladelse for serverroller og operativsystemfiler gælder ikke for Windows Server 2012. Automatisk udeladelse kan gælde, hvis dine servere, Windows Server 2012 R2 er onboardet til Defender til Slutpunkt. (Se [Onboard Windows-servere til Microsoft Defender for Endpoint-tjenesten](configure-server-endpoints.md)).


### <a name="the-list-of-automatic-exclusions"></a>Listen over automatiske udeladelse

De følgende afsnit indeholder udeladelsestyper, der leveres med automatisk udeladelse af filstier og filtyper.

#### <a name="default-exclusions-for-all-roles"></a>Standard udeladelse for alle roller

I dette afsnit vises standard udeladelsesindstillingerne for alle roller i Windows Server 2016, Windows Server 2019 og Windows Server 2022.

> [!NOTE]
> Standardplaceringerne kan være forskellige fra dem, der er angivet i denne artikel.

##### <a name="windows-tempedb-files"></a>Windows "temp.edb"-filer

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows opdater filer eller automatiske opdateringsfiler

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

##### <a name="file-replication-service-frs-exclusions"></a>Udeladelse af Filreplikeringstjeneste (FRS)

- Filer i arbejdsmappen File Replication Service (FRS). Arbejdsmappen FRS er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- FRS-databaselogfiler. Logfilmappen for FRS-databasen er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- Mappen til opsætning af FRS. Mappen til opsætning er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- Mappen for forudinstallering af FRS. Denne mappe er angivet af mappen `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- Distributed File System Replication (DFSR)-databasen og arbejdsmapper. Disse mapper er angivet af registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > For brugerdefinerede placeringer skal du [se Frameld automatisk udeladelse](#opting-out-of-automatic-exclusions).

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

##### <a name="process-exclusions"></a>Procesudetagelser

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Hyper-V-udeladelse

I følgende tabel vises udeladelse af filtyper, mappeude udeladelse og procesudetagelser, der leveres automatisk, når du installerer Hyper-V-rollen.

<br><br/>

|Udeladelsestype|Specifikke oplysninger|
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


#### <a name="active-directory-exclusions"></a>Active Directory-udeladelse

I dette afsnit vises de udeladelsestegn, der leveres automatisk, når du Active Directory-domæneservices (AD DS).

##### <a name="ntds-database-files"></a>NTDS-databasefiler

Databasefilerne er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>Den AD DS transaktionslogfiler

Transaktionslogfilerne er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>Arbejdsmappen NTDS

Denne mappe er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>Procesudetagelser for AD DS og AD DS relaterede supportfiler

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>Udeladelse af DHCP-server

I dette afsnit vises udeladelserne, der leveres automatisk, når du installerer DHCP-serverrollen. Placeringerne af DHCP-serveren er angivet af parametrene *DatabasePath*, *DhcpLogFilePath* og *BackupDatabasePath* i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>Udeladelse af DNS Server

I dette afsnit vises de fil- og mappeudetagelser og de procesudetagelser, der leveres automatisk, når du installerer DNS Server-rollen.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>Fil- og mappeude udeladelse for DNS Server-rollen

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>Procesudetagelser for DNS Server-rollen

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>Fil- Storage og tjenesteude udeladelse

I dette afsnit vises de fil- og mappeude udeladelsestegn, der leveres automatisk, når du installerer rollen Filer og Storage-tjenester. De undtagelser, der er angivet nedenfor, inkluderer ikke udeladelse for klyngerollen.

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>Udeladelse af Print Server

I dette afsnit vises udeladelse af filtyper, mappeudetagelser og de procesudetagelser, der leveres automatisk, når du installerer printserverrollen.

##### <a name="file-type-exclusions"></a>Udeladelse af filtyper

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>Udeladelse af mapper

Denne mappe er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>Procesudetagelser

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>Udeladelse af webserver

I dette afsnit finder du en oversigt over mappeudetagelser og de procesudetagelser, der leveres automatisk, når du installerer Web Server-rollen.

##### <a name="folder-exclusions"></a>Udeladelse af mapper

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>Procesudetagelser

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>De deaktiverer scanning af filer i mappen Sysvol\Sysvol eller mappen SYSVOL_DFSR\Sysvol

Den aktuelle placering af mappen `Sysvol\Sysvol` og `SYSVOL_DFSR\Sysvol` alle undermapper er filsystemets genparse destination for replikeringssætroden. Mapperne `Sysvol\Sysvol` `SYSVOL_DFSR\Sysvol` og disse bruger som standard følgende placeringer:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

Der refereres til stien til den `SYSVOL` aktive i øjeblikket aktive del af NETLOGON-delingen og kan bestemmes af værdien SysVol i følgende undernøgle: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

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

#### <a name="windows-server-update-services-exclusions"></a>Windows Server Update Services udeladelse

I dette afsnit vises de mappeudetagelser, der leveres automatisk, når du installerer Windows Server Update Services (WSUS). WSUS-mappen er angivet i registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>Framelde dig automatiske udeladelse

I Windows Server 2016 og nyere udelader de foruddefinerede udeladelsesindstillinger, der leveres af Sikkerhedsintelligens-opdateringer, kun standardstierne for en rolle eller funktion. Hvis du har installeret en rolle eller funktion i en brugerdefineret sti, eller hvis du manuelt vil styre udeladelsessættet, skal du sørge for at fravælge de automatiske udeladelsesindstillinger, der leveres i Sikkerhedsintelligens-opdateringer. Men husk på, at de undtagelser, der leveres automatisk, er optimeret til Windows Server 2016 og nyere. Se En [Anbefalinger definition af udeladelseslister, før](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) du definerer dine udeladelseslister.

> [!WARNING]
> Frameld automatisk udeladelse kan have en negativ effekt på ydeevnen eller medføre beskadigelse af data. Udeladelserne, der leveres automatisk, er optimeret til Windows Server 2016, Windows Server 2019 og Windows Server 2022-roller.

Da foruddefinerede undtagelser kun udelader standardstier **, skal** du tilføje udeladelse manuelt, hvis du flytter NTDS- og SYSVOL-mapper til et andet drev eller en anden sti end den oprindelige sti. Se [Konfigurer listen over udeladelses undtagelser baseret på mappenavn eller filtypenavn](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

Du kan deaktivere listerne over automatiske udeladelse med Gruppepolitik, PowerShell-cmdlet'er og WMI.

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>Brug Gruppepolitik til at deaktivere listen til automatisk udeladelse Windows Server 2016, Windows Server 2019 og Windows Server 2022

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

2. På fanen **Gruppepolitik skal du** gå **til Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **udeladelse.**

4. Dobbeltklik på Slå **automatisk udeladelse fra**, og angiv indstillingen til **Aktiveret**. Vælg derefter **OK**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>Brug PowerShell-cmdlet'er til at deaktivere listen til automatisk udeladelse på Windows Server

Brug følgende cmdlet'er:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

Du kan få mere at vide i følgende ressourcer:

- [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [Brug PowerShell med Microsoft Defender Antivirus](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>Brug Windows (WMI) til at deaktivere listen over automatiske udeladelser Windows Server

Brug **metoden Angiv** for [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) til følgende egenskaber:

```WMI
DisableAutoExclusions
```

Se følgende for at få flere oplysninger og tilladte parametre:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>Definition af brugerdefinerede udeladelses undtagelser

Hvis det er nødvendigt, kan du tilføje eller fjerne brugerdefinerede udeladelser. Det gør du i følgende artikler:

- [Konfigurere og validere udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse af filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>Se også

- [Konfigurere og validere udeladelse for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse baseret på filnavn, filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere og validere udeladelse af filer, der er åbnet af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [Almindelige fejl at undgå, når du definerer udeladelse](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
