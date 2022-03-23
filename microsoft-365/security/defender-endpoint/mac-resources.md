---
title: Ressourcer til Microsoft Defender til Slutpunkt på Mac
description: Ressourcer til Microsoft Defender til slutpunkt på Mac, herunder hvordan du fjerner det, hvordan du indsamler diagnostiske logfiler, CLI-kommandoer og kendte problemer med produktet.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, uninstallation, intune,propf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 5c8580e1bc0869f28da1b23a813bba9d2f3c612e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592057"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>Ressourcer til Microsoft Defender til Slutpunkt på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>Indsamling af diagnostiske oplysninger

Hvis du kan genskabe et problem, kan du øge logføringsniveauet, køre systemet i et stykke tid og gendanne logføringsniveauet til standardindstillingen.

1. Forøg logføringsniveauet:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Genskab problemet

3. Kør `sudo mdatp diagnostic create` for at sikkerhedskopiere Microsoft Defender for Endpoint-logfilerne. Filerne gemmes i et .zip arkiv. Denne kommando udskriver også filstien til sikkerhedskopieringen, når handlingen lykkes.

   > [!TIP]
   > Diagnosticeringslogfiler gemmes som standard i `/Library/Application Support/Microsoft/Defender/wdavdiag/`. Hvis du vil ændre den mappe, hvor diagnostiske logfiler gemmes, `--path [directory]` skal du overføre til kommandoen nedenfor og `[directory]` erstatte den med den ønskede mappe.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. Gendanne logføringsniveau:

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>Problemer med logføring af installation

Hvis der opstår en fejl under installationen, rapporterer installationsprogrammet kun en generel fejl.

Den detaljerede logfil gemmes i `/Library/Logs/Microsoft/mdatp/install.log`. Hvis du oplever problemer under installationen, kan du sende os denne fil, så vi kan hjælpe med at diagnosticere årsagen.

## <a name="uninstalling"></a>Fjernelse

Der er flere måder at fjerne Microsoft Defender til Endpoint på macOS. Bemærk, at mens centralt administreret afinstallation er tilgængelig på SYLF, er den endnu ikke tilgængelig for Microsoft Intune.

### <a name="interactive-uninstallation"></a>Interaktiv fjernelse

- Åbn **Finder > Programmer**. Højreklik på **Microsoft Defender for Slutpunkt for at flytte > til Papirkurv**.

### <a name="supported-output-types"></a>Understøttede outputtyper

Understøtter outputtyperne tabel- og JSON-format. For hver kommando er der en standardoutputfunktion. Du kan ændre outputtet i dit foretrukne outputformat ved hjælp af følgende kommandoer:

`-output json`

`-output table`

### <a name="from-the-command-line"></a>Fra kommandolinjen

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>Konfiguration fra kommandolinjen

Vigtige opgaver, f.eks. kontrol af produktindstillinger og udløsning af scanninger efter behov, kan udføres fra kommandolinjen:

|Gruppe|Scenarie|Kommando|
|---|---|---|
|Konfiguration|Slå beskyttelse i realtid til/fra|`mdatp config real-time-protection --value [enabled/disabled]`|
|Konfiguration|Slå skybeskyttelse til/fra|`mdatp config cloud --value [enabled/disabled]`|
|Konfiguration|Slå produktdiagnosticering til/fra|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|Konfiguration|Slå automatisk indsendelse af eksempler til/fra|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|Konfiguration|Føje et trusselsnavn til listen over tilladte|`mdatp threat allowed add --name [threat-name]`|
|Konfiguration|Fjerne et trusselsnavn fra listen over tilladte|`mdatp threat allowed remove --name [threat-name]`|
|Konfiguration|Liste over alle tilladte trusselsnavne|`mdatp threat allowed list`|
|Konfiguration|Slå PUA-beskyttelse til|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|Konfiguration|Slå PUA-beskyttelse fra|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|Konfiguration|Slå overvågningstilstand til for PUA-beskyttelse|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|Konfiguration|Slå passiv antivirustilstand til/fra|`mdatp config passive-mode --value [enabled/disabled]`|
|Konfiguration|Konfigurere grad af parallelitet for on-demand-scanninger|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Konfiguration|Aktivere/deaktivere scanninger efter sikkerhedsintelligensopdateringer|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Konfiguration|Slå arkivscanning til/fra (kun scanninger efter behov)|`mdatp config scan-archives --value [enabled/disabled]`|
|Diagnosticering|Ændre logniveauet|`mdatp log level set --level [error/warning/info/verbose]`|
|Diagnosticering|Opret diagnostiske logfiler|`mdatp diagnostic create --path [directory]`|
|Tilstand|Kontrollér produktets tilstand|`mdatp health`|
|Tilstand|Kontrollér, om der er en spefic-produktattribut|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|Beskyttelse|Scan en sti|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Beskyttelse|Udføre en hurtig scanning|`mdatp scan quick`|
|Beskyttelse|Udføre en fuld scanning|`mdatp scan full`|
|Beskyttelse|Annuller en løbende scanning efter behov|`mdatp scan cancel`|
|Beskyttelse|Anmod om en sikkerhedsintelligensopdatering|`mdatp definitions update`|
|Slutpunktsregistrering og -svar|Angiv/fjern kode, kun GRUPPE understøttet|`mdatp edr tag set --name GROUP --value [name]`|
|Slutpunktsregistrering og -svar|Fjern gruppemærke fra enhed|`mdatp edr tag remove --tag-name [name]`|
|Slutpunktsregistrering og -svar|Tilføj gruppe-id|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>Sådan aktiveres autofuldførelse

For at aktivere autofuldførelse i Bash skal du køre følgende kommando og genstarte Terminal-sessionen:

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

Sådan aktiveres autofuldførelse i zsh:

- Kontrollér, om autofuldførelse er aktiveret på din enhed:

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- Hvis den foregående kommando ikke frembringer nogen output, kan du aktivere autofuldførelse ved hjælp af følgende kommando:

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- Kør følgende kommandoer for at aktivere autofuldførelse for Microsoft Defender til slutpunkt på macOS, og genstart Terminal-sessionen:

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>Client Microsoft Defender for Endpoint quarantine directory

`/Library/Application Support/Microsoft/Defender/quarantine/` indeholder de filer, der er sat i karantæne af `mdatp`. Filerne er navngivet efter trusselssporings-id'et. De aktuelle sporings-id'er vises med `mdatp threat list`.

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Oplysninger om Microsoft Defender til Endpoint-portalen

[Slutpunktsregistrering og -svar funktioner til macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801) nu er kommet, viser Microsoft Defender for Endpoint-bloggen detaljerede anvisninger for, hvad du kan forvente i Microsoft Defender til Endpoint Security Center.
