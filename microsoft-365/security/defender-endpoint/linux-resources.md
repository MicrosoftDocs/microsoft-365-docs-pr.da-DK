---
title: Microsoft Defender for Endpoint på Linux-ressourcer
ms.reviewer: ''
description: Beskriver ressourcer til Microsoft Defender for Endpoint på Linux, herunder hvordan du fjerner det, hvordan du indsamler diagnosticeringslogge, kommandolinjegrænsefladekommandoer og kendte problemer med produktet.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, uninstallation, dukke, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0971933f1099192b1cb8b7a844793f264ef2aa15
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949475"
---
# <a name="resources"></a>Ressourcer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Indsaml diagnosticeringsoplysninger

Hvis du kan genskabe et problem, skal du først øge logføringsniveauet, køre systemet i et stykke tid og derefter gendanne logføringsniveauet til standardniveauet.

1. Forøg logføringsniveauet:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Genskab problemet.

3. Kør følgende kommando for at sikkerhedskopiere Defender for slutpunktets logge. Filerne gemmes i et .zip arkiv.

   ```bash
   sudo mdatp diagnostic create
   ```

    Denne kommando udskriver også filstien til sikkerhedskopien, når handlingen er fuldført:

   ```Output
   Diagnostic file created: <path to file>
   ```

4. Gendan logføringsniveau:

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>Problemer med loginstallation

Hvis der opstår en fejl under installationen, rapporterer installationsprogrammet kun en generel fejl.

Den detaljerede log gemmes i `/var/log/microsoft/mdatp/install.log`.
Hvis du oplever problemer under installationen, kan du sende os denne fil, så vi kan hjælpe med at diagnosticere årsagen.

## <a name="uninstall"></a>Afinstallere

Der er flere måder at fjerne Defender for Endpoint på Linux på. Hvis du bruger et konfigurationsværktøj, f.eks. Puppet, skal du følge vejledningen til fjernelse af pakken for konfigurationsværktøjet.

### <a name="manual-uninstallation"></a>Manuel fjernelse

- `sudo yum remove mdatp` til RHEL og varianter(CentOS og Oracle Linux).
- `sudo zypper remove mdatp` for SLES og varianter.
- `sudo apt-get purge mdatp` til Ubuntu- og Debian-systemer.

## <a name="configure-from-the-command-line"></a>Konfigurer fra kommandolinjen

Vigtige opgaver, f.eks. styring af produktindstillinger og udløsning af scanninger efter behov, kan udføres fra kommandolinjen.

### <a name="global-options"></a>Globale indstillinger

Kommandolinjeværktøjet skriver som standard resultatet i et format, der kan læses af mennesker. Derudover understøtter værktøjet også output af resultatet som JSON, hvilket er nyttigt i automatiseringsscenarier. Hvis du vil ændre outputtet til JSON, skal du overføre `--output json` til en af nedenstående kommandoer.

### <a name="supported-commands"></a>Understøttede kommandoer

I følgende tabel vises kommandoer til nogle af de mest almindelige scenarier. Kør `mdatp help` fra Terminal for at få vist en komplet liste over understøttede kommandoer.

<br>

****

|Gruppe|Scenario|Kommando|
|---|---|---|
|Konfiguration|Slå beskyttelse i realtid til/fra|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Konfiguration|Slå overvågning af funktionsmåde til/fra|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Konfiguration|Slå skybeskyttelse til/fra|`mdatp config cloud --value [enabled\|disabled]`|
|Konfiguration|Slå produktdiagnosticering til/fra|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Konfiguration|Slå automatisk eksempelafsendelse til/fra|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Konfiguration|Slå AV-passiv tilstand til/fra|`mdatp config passive-mode --value [enabled\|disabled]`|
|Konfiguration|Tilføj/fjern en antivirusudeladelse for et filtypenavn|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Konfiguration|Tilføj/fjern en antivirusudeladelse for en fil|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Konfiguration|Tilføj/fjern en antivirusudeladelse for en mappe|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Konfiguration|Tilføj/fjern en antivirusudeladelse for en proces|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Konfiguration|Vis alle antivirusudeladelser|`mdatp exclusion list`|
|Konfiguration|Føj et trusselsnavn til listen over tilladte|`mdatp threat allowed add --name [threat-name]`|
|Konfiguration|Fjern et trusselsnavn fra listen over tilladte|`mdatp threat allowed remove --name [threat-name]`|
|Konfiguration|Vis alle tilladte trusselsnavne|`mdatp threat allowed list`|
|Konfiguration|Slå PUA-beskyttelse til|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Konfiguration|Deaktiver PUA-beskyttelse|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Konfiguration|Slå overvågningstilstand til for PUA-beskyttelse|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Konfiguration|Konfigurer graden af parallelitet for scanninger efter behov|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Konfiguration|Slå scanninger til/fra efter sikkerhedsintelligensopdateringer|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Konfiguration|Slå arkivscanning til/fra (kun efter behov)|`mdatp config scan-archives --value [enabled/disabled]`|
|Konfiguration|Slå beregning af filhash til/fra|`mdatp config enable-file-hash-computation --value [enabled/disabled]`|
|Diagnostik|Skift logniveau|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Diagnostik|Generér diagnosticeringslogge|`mdatp diagnostic create --path [directory]`|
|Sundhed|Kontrollér produktets tilstand|`mdatp health`|
|Beskyttelse|Scan en sti|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Beskyttelse|Foretage en hurtig scanning|`mdatp scan quick`|
|Beskyttelse|Foretage en fuld scanning|`mdatp scan full`|
|Beskyttelse|Annuller en igangværende scanning efter behov|`mdatp scan cancel`|
|Beskyttelse|Anmod om en sikkerhedsintelligensopdatering|`mdatp definitions update`|
|Beskyttelsesoversigt|Udskriv historikken for fuld beskyttelse|`mdatp threat list`|
|Beskyttelsesoversigt|Få detaljer om trusler|`mdatp threat get --id [threat-id]`|
|Karantænestyring|Vis alle filer, der er sat i karantæne|`mdatp threat quarantine list`|
|Karantænestyring|Fjern alle filer fra karantænen|`mdatp threat quarantine remove-all`|
|Karantænestyring|Tilføj en fil, der er registreret som en trussel mod karantænen|`mdatp threat quarantine add --id [threat-id]`|
|Karantænestyring|Fjern en fil, der er registreret som en trussel, fra karantænen|`mdatp threat quarantine remove --id [threat-id]`|
|Karantænestyring|Gendan en fil fra karantænen|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|Registrering af slutpunkt og svar|Angiv tidlig eksempelvisning (bruges ikke)|`mdatp edr early-preview [enable|disable]`|
|Registrering af slutpunkt og svar|Angiv gruppe-id|`mdatp edr group-ids --group-id [group-id]`|
|Registrering af slutpunkt og svar|Angiv/fjern kode. Understøttes kun `GROUP`|`mdatp edr tag set --name GROUP --value [tag]`|
|Registrering af slutpunkt og svar|Listeudeladelser (rod)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
