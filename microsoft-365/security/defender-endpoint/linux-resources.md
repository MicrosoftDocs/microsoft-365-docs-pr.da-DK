---
title: Microsoft Defender til slutpunkt på Linux-ressourcer
ms.reviewer: ''
description: Beskriver ressourcer til Microsoft Defender til slutpunkt på Linux, herunder hvordan du fjerner det, hvordan du indsamler diagnostiske logfiler, CLI-kommandoer og kendte problemer med produktet.
keywords: microsoft, defender, Microsoft Defender til slutpunkt, linux, installation, deploy, uninstallation, defender, ansible, linux, redhat, ubuntu, defender, sles, suse, centos
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
ms.openlocfilehash: a32c8c91350218da619de18e0b1b398a93bf7fda
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591863"
---
# <a name="resources"></a>Ressourcer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Indsamle diagnostiske oplysninger

Hvis du kan genskabe et problem, skal du først øge logføringsniveauet, køre systemet i et stykke tid og derefter gendanne logføringsniveauet til standardværdien.

1. Forøg logføringsniveauet:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Genskab problemet.

3. Kør følgende kommando for at sikkerhedskopiere Defender for Endpoints logfiler. Filerne gemmes i et .zip arkiv.

   ```bash
   sudo mdatp diagnostic create
   ```

    Denne kommando udskriver også filstien til sikkerhedskopieringen, når handlingen lykkes:

   ```Output
   Diagnostic file created: <path to file>
   ```

4. Gendanne logføringsniveau:

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>Problemer med installation af logfil

Hvis der opstår en fejl under installationen, rapporterer installationsprogrammet kun en generel fejl.

Den detaljerede logfil gemmes i `/var/log/microsoft/mdatp/install.log`.
Hvis du oplever problemer under installationen, kan du sende os denne fil, så vi kan hjælpe med at diagnosticere årsagen.

## <a name="uninstall"></a>Fjern

Der er flere måder at fjerne Defender for Endpoint på Linux på. Hvis du bruger et konfigurationsværktøj som f.eks. Pak, skal du følge instruktionerne til fjernelse af pakken for konfigurationsværktøjet.

### <a name="manual-uninstallation"></a>Manuel fjernelse

- `sudo yum remove mdatp` for RHEL og varianter (CentOS og Oracle Linux).
- `sudo zypper remove mdatp` for SLES og varianter.
- `sudo apt-get purge mdatp` til Ubuntu- og Systems- og Ink- systemer.

## <a name="configure-from-the-command-line"></a>Konfigurere fra kommandolinjen

Vigtige opgaver, f.eks. kontrol af produktindstillinger og udløsning af scanninger efter behov, kan udføres fra kommandolinjen.

### <a name="global-options"></a>Globale indstillinger

Som standard viser kommandolinjeværktøjet resultatet i læsbart format. Desuden understøtter værktøjet også output af resultatet som JSON, hvilket er nyttigt til automatiseringsscenarier. Hvis du vil ændre outputtet til JSON, skal `--output json` du overføre til en af nedenstående kommandoer.

### <a name="supported-commands"></a>Understøttede kommandoer

I følgende tabel vises kommandoer for nogle af de mest almindelige scenarier. Kør `mdatp help` fra Terminalen for at få vist en komplet liste over understøttede kommandoer.

<br>

****

|Gruppe|Scenarie|Kommando|
|---|---|---|
|Konfiguration|Slå beskyttelse i realtid til/fra|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Konfiguration|Aktivere/deaktivere overvågning af funktionsmåder|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Konfiguration|Slå skybeskyttelse til/fra|`mdatp config cloud --value [enabled\|disabled]`|
|Konfiguration|Slå produktdiagnosticering til/fra|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Konfiguration|Slå automatisk indsendelse af eksempler til/fra|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Konfiguration|Slå AV-passiv tilstand til/fra|`mdatp config passive-mode --value [enabled\|disabled]`|
|Konfiguration|Tilføj/fjern en antivirusudelse for et filtypenavn|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Konfiguration|Tilføj/fjern en antivirusudelse for en fil|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Konfiguration|Tilføj/fjern en antivirusudelse for en mappe|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Konfiguration|Tilføje/fjerne en antivirusudelse for en proces|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Konfiguration|Vis alle antivirusude udeladelse|`mdatp exclusion list`|
|Konfiguration|Føje et trusselsnavn til listen over tilladte|`mdatp threat allowed add --name [threat-name]`|
|Konfiguration|Fjerne et trusselsnavn fra listen over tilladte|`mdatp threat allowed remove --name [threat-name]`|
|Konfiguration|Liste over alle tilladte trusselsnavne|`mdatp threat allowed list`|
|Konfiguration|Slå PUA-beskyttelse til|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Konfiguration|Slå PUA-beskyttelse fra|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Konfiguration|Slå overvågningstilstand til for PUA-beskyttelse|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Konfiguration|Konfigurere grad af parallelitet for on-demand-scanninger|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Konfiguration|Aktivere/deaktivere scanninger efter sikkerhedsintelligensopdateringer|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Konfiguration|Slå arkivscanning til/fra (kun scanninger efter behov)|`mdatp config scan-archives --value [enabled/disabled]`|
|Diagnosticering|Ændre logniveauet|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Diagnosticering|Opret diagnostiske logfiler|`mdatp diagnostic create --path [directory]`|
|Tilstand|Kontrollér produktets tilstand|`mdatp health`|
|Beskyttelse|Scan en sti|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Beskyttelse|Udføre en hurtig scanning|`mdatp scan quick`|
|Beskyttelse|Udføre en fuld scanning|`mdatp scan full`|
|Beskyttelse|Annuller en løbende scanning efter behov|`mdatp scan cancel`|
|Beskyttelse|Anmod om en sikkerhedsintelligensopdatering|`mdatp definitions update`|
|Historik for beskyttelse|Udskriv den fulde historik for beskyttelse|`mdatp threat list`|
|Historik for beskyttelse|Få oplysninger om trusler|`mdatp threat get --id [threat-id]`|
|Administration af karantæne|Vis alle filer, der er sat i karantæne|`mdatp threat quarantine list`|
|Administration af karantæne|Fjern alle filer fra karantæne|`mdatp threat quarantine remove-all`|
|Administration af karantæne|Tilføj en fil, der er registreret som en trussel mod karantæne|`mdatp threat quarantine add --id [threat-id]`|
|Administration af karantæne|Fjerne en fil, der er registreret som en trussel fra karantæne|`mdatp threat quarantine remove --id [threat-id]`|
|Administration af karantæne|Gendan en fil fra karantæne|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|Registrering af slutpunkt og svar|Angiv tidlig forhåndsvisning (ubrugt)|`mdatp edr early-preview [enable|disable]`|
|Registrering af slutpunkt og svar|Indstil gruppe-id|`mdatp edr group-ids --group-id [group-id]`|
|Registrering af slutpunkt og svar|Angiv/fjern mærke, understøttes `GROUP` kun|`mdatp edr tag set --name GROUP --value [tag]`|
|Registrering af slutpunkt og svar|Listeudetagelser (rod)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
