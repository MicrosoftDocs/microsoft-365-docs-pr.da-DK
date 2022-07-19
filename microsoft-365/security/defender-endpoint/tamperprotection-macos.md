---
title: Beskyt macOS-sikkerhedsindstillinger med beskyttelse mod manipulation
description: Brug beskyttelse mod ændring for at forhindre, at skadelige apps ændrer vigtige sikkerhedsindstillinger for macOS.
keywords: macos, manipulationsbeskyttelse, sikkerhedsindstillinger, malware
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 45a30d02992d3128ab1520c24927fb43c1180cf8
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66858948"
---
# <a name="protect-macos-security-settings-with-tamper-protection"></a>Beskyt macOS-sikkerhedsindstillinger med beskyttelse mod manipulation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]


Ændringsbeskyttelse i macOS hjælper med at forhindre uønskede ændringer af sikkerhedsindstillingerne i at blive foretaget af uautoriserede brugere. Manipulationsbeskyttelse hjælper med at forhindre uautoriseret fjernelse af Microsoft Defender for Endpoint på macOS. Denne funktion hjælper også vigtige sikkerhedsfiler, processer og konfigurationsindstillinger med at blive ændret.

Du kan angive ændringsbeskyttelse i følgende tilstande:

|Emne|Beskrivelse|
|---|---|
|Deaktiveret|Manipulationsbeskyttelse er helt slået fra (dette er standardtilstanden efter installation)|
|Revision|Manipulationshandlinger logføres, men blokeres ikke|
|Bloker|Ændringsbeskyttelse er slået til, manipulationshandlinger blokeres|

Når beskyttelse mod ændring er indstillet til overvågning eller blokeringstilstand, kan du forvente følgende resultater:

**Overvågningstilstand**:

- Handlinger til fjernelse af Defender for Endpoint Agent logføres (overvåges)
- Redigering/ændring af Defender for Endpoint-filer logføres (overvåges)
- Oprettelse af nye filer under Defender for Endpoint-placering logføres (overvåges)
- Sletning af Defender for Endpoint-filer logføres (overvåges)
- Omdøbning af Defender for Endpoint-filer logføres (overvåges)

**Bloktilstand**:

- Handlinger til fjernelse af Defender for Endpoint Agent er blokeret
- Redigering/ændring af Defender for Endpoint-filer er blokeret
- Oprettelse af nye filer under Defender for Endpoint-placering er blokeret
- Sletning af Defender for Endpoint-filer er blokeret
- Omdøbning af Defender for Endpoint-filer er blokeret
- Kommandoer til at stoppe agenten mislykkes

Her er et eksempel på en systemmeddelelse som svar på en blokeret handling:

![Billede af handling, der er blokeret](images/operation-blocked.png)

Du kan konfigurere beskyttelsestilstanden for manipulation ved at angive tilstandsnavnet som håndhævelsesniveau.

> [!NOTE]
>
> - Tilstandsændringen gælder med det samme.
> - Hvis du brugte JAMF under den indledende konfiguration, skal du også opdatere konfigurationen ved hjælp af JAMF.

## <a name="before-you-begin"></a>Før du begynder

- Understøttede macOS-versioner: Monterey (12), Big Sur (11), Catalina (10.15+).
- Minimumversion kræves for Defender for Endpoint: 101.70.19.
- Du skal være på en ikke-produktionsopdateringskanal ([enten prøveversion eller beta](/deployoffice/office-insider/deploy/microsoft-autoupdate)), mens funktionen Tamper Protection er en prøveversion. Hvis du er på en produktionskanal, ignoreres den konfigurerede beskyttelsestilstand for manipulation.

**Stærkt anbefalede indstillinger:**

- System Integrity Protection (SIP) er aktiveret. Du kan få flere oplysninger under [Deaktivering og aktivering af systemintegritetsbeskyttelse](https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection).
- Brug et MDM-værktøj (Mobile Device Management) til at konfigurere Microsoft Defender for Endpoint.

## <a name="configure-tamper-protection-on-macos-devices"></a>Konfigurer beskyttelse mod manipulation på macOS-enheder

Der er flere måder, du kan konfigurere beskyttelse mod manipulation på:

- [Manuel konfiguration](#manual-configuration)
- [JAMF](#jamf)
- [Intune](#intune)

### <a name="before-you-begin"></a>Før du begynder

Kontrollér, at "tamper_protection" er angivet til "disabled" eller "audit" for at overvåge tilstandsændringen.
Sørg også for, at "release_ring" ikke rapporterer "Produktion".

```bash
mdatp health
```

```console
healthy                                     : true
health_issues                               : []
licensed                                    : true
engine_version                              : "1.1.19300.3"
app_version                                 : "101.70.19"
org_id                                      : "..."
log_level                                   : "info"
machine_guid                                : "..."
release_ring                                : "InsiderFast"
product_expiration                          : Dec 29, 2022 at 09:48:37 PM
cloud_enabled                               : true
cloud_automatic_sample_submission_consent   : "safe"
cloud_diagnostic_enabled                    : false
passive_mode_enabled                        : false
real_time_protection_enabled                : true
real_time_protection_available              : true
real_time_protection_subsystem              : "endpoint_security_extension"
network_events_subsystem                    : "network_filter_extension"
device_control_enforcement_level            : "audit"
tamper_protection                           : "audit"
automatic_definition_update_enabled         : true
definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
definitions_updated_minutes_ago             : 5
definitions_version                         : "1.369.896.0"
definitions_status                          : "up_to_date"
edr_early_preview_enabled                   : "disabled"
edr_device_tags                             : []
edr_group_ids                               : ""
edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
edr_machine_id                              : "..."
conflicting_applications                    : []
network_protection_status                   : "stopped"
data_loss_prevention_status                 : "disabled"
full_disk_access_enabled                    : true
```

### <a name="manual-configuration"></a>Manuel konfiguration

1. Brug følgende kommando:

   ```console
   sudo mdatp config tamper-protection enforcement-level --value block
   ```

   ![Billede af manuel konfigurationskommando](images/manual-config-cmd.png)

   > [!NOTE]
   > Hvis du bruger manuel konfiguration til at aktivere manipulationsbeskyttelse, kan du også deaktivere ændringsbeskyttelse manuelt når som helst. Du kan f.eks. tilbagekalde fuld diskadgang fra Defender i Systemindstillinger manuelt. Du skal bruge MDM i stedet for manuel konfiguration for at forhindre en lokal administrator i at gøre det.

2. Kontrollér resultatet.

  ```bash
  mdatp health
  ```

  ```console
  healthy                                     : true
  health_issues                               : []
  licensed                                    : true
  engine_version                              : "1.1.19300.3"
  app_version                                 : "101.70.19"
  org_id                                      : "..."
  log_level                                   : "info"
  machine_guid                                : "..."
  release_ring                                : "InsiderFast"
  product_expiration                          : Dec 29, 2022 at 09:48:37 PM
  cloud_enabled                               : true
  cloud_automatic_sample_submission_consent   : "safe"
  cloud_diagnostic_enabled                    : false
  passive_mode_enabled                        : false
  real_time_protection_enabled                : true
  real_time_protection_available              : true
  real_time_protection_subsystem              : "endpoint_security_extension"
  network_events_subsystem                    : "network_filter_extension"
  device_control_enforcement_level            : "audit"
  tamper_protection                           : "block"
  automatic_definition_update_enabled         : true
  definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
  definitions_updated_minutes_ago             : 5
  definitions_version                         : "1.369.896.0"
  definitions_status                          : "up_to_date"
  edr_early_preview_enabled                   : "disabled"
  edr_device_tags                             : []
  edr_group_ids                               : ""
  edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
  edr_machine_id                              : "..."
  conflicting_applications                    : []
  network_protection_status                   : "stopped"
  data_loss_prevention_status                 : "disabled"
  full_disk_access_enabled                    : true
  ```

Bemærk, at "tamper_protection" nu er angivet til "blok".

### <a name="jamf"></a>JAMF

Konfigurer beskyttelsestilstand for ændring i Microsoft Defender for Endpoint [konfigurationsprofil](mac-jamfpro-policies.md) ved at tilføje følgende indstillinger:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>block</string>
    </dict>
  </dict>
</plist>
```

> [!NOTE]
> Hvis du allerede har en konfigurationsprofil til Microsoft Defender for Endpoint skal du *føje* indstillinger til den. Du behøver ikke at oprette endnu en konfigurationsprofil.

### <a name="intune"></a>Intune

Følg det dokumenterede Intune profileksempel for at konfigurere ændringsbeskyttelse via Intune. Du kan få flere oplysninger under [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md).

Tilføj følgende konfiguration i din Intune profil:

> [!NOTE]
> Hvis du vil Intune konfiguration, kan du oprette en ny profilkonfigurationsfil for at tilføje konfigurationen af Beskyttelse af Tamper, eller du kan føje disse parametre til den eksisterende.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>block</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Kontrollér beskyttelsesstatus for ændring ved at køre følgende kommando:

`mdatp health --field tamper_protection`

Resultatet viser "blok", hvis beskyttelse mod ændring er slået til:

![Billede af manipulationsbeskyttelse i bloktilstand](images/tp-block-mode.png)

Du kan også køre fuld `mdatp health` og søge efter "tamper_protection" i outputtet

## <a name="verify-tamper-protection-preventive-capabilities"></a>Kontrollér forebyggende funktioner til beskyttelse af manipulation

Du kan bekræfte, at manipulationsbeskyttelse er aktiveret på forskellige måder.

### <a name="verify-block-mode"></a>Kontrollér bloktilstand

Der sendes en ændringsadvarsel på Microsoft 365 Defender-portalen

![Billede af manipulationsadvarsel, der er opstået på Microsoft 365 Defender-portalen](images/tampering-sensor-portal.png)

### <a name="verify-block-mode-and-audit-modes"></a>Kontrollér bloktilstand og overvågningstilstande

- Når du bruger Avanceret jagt, får du vist manipulationsbeskeder
- Ændringshændelser kan findes i logfilerne for den lokale enhed: `sudo grep -F '[{tamperProtection}]' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log`

![Billede af ændringsbeskyttelseslog](images/tamper-protection-log.png)

### <a name="diy-scenarios"></a>GØR-det-selv-scenarier

- Når manipulationsbeskyttelse er angivet til "blok", kan du forsøge at fjerne Defender for Endpoint på forskellige måder. Du kan f.eks. trække appfeltet til papirkurven eller fjerne beskyttelse mod manipulation ved hjælp af kommandolinjen.
- Prøv at stoppe Defender for Endpoint-processen (kill).
- Prøv at slette, omdøbe, redigere, flytte Defender for Endpoint-filer (svarende til, hvad en ondsindet bruger ville gøre), f.eks.:

  - /Applications/Microsoft Defender ATP.app/
  - /Library/LaunchDaemons/com.microsoft.fresno.plist
  - /Library/LaunchDaemons/com.microsoft.fresno.uninstall.plist
  - /Library/LaunchAgents/com.microsoft.wdav.tray.plist
  - /Library/Managed Preferences/com.microsoft.wdav.ext.plist
  - /Library/Managed Preferences/mdatp_managed.json
  - /Library/Managed Preferences/com.microsoft.wdav.atp.plist
  - /Library/Managed Preferences/com.microsoft.wdav.atp.offboarding.plist
  - /usr/local/bin/mdatp

## <a name="turning-off-tamper-protection"></a>Deaktiver beskyttelse mod manipulation

Du kan slå manipulationsbeskyttelse fra ved hjælp af en af følgende metoder.

### <a name="manual-configuration"></a>Manuel konfiguration

Brug følgende kommando:

```console
sudo mdatp config tamper-protection enforcement-level - -value disabled
```

## <a name="jamf"></a>JAMF
Skift værdien `enforcementLevel` til "disabled" i din konfigurationsprofil, og send den til computeren:

```console
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>disabled</string>
    </dict>
  </dict>
</plist>

```

### <a name="intune"></a>Intune
Tilføj følgende konfiguration i din Intune profil:

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>disabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="troubleshooting-configuration-issues"></a>Fejlfinding af konfigurationsproblemer

### <a name="issue-tamper-protection-is-reported-as-disabled"></a>Problem: Ændringsbeskyttelse rapporteres som deaktiveret

Hvis kørsel af kommandoen `mdatp health` rapporterer, at beskyttelse mod manipulation er deaktiveret, selvom du har aktiveret den, og der er gået mere end en time siden onboarding, kan du kontrollere, om du har den rigtige konfiguration, ved at køre følgende kommando:

```console
$ sudo grep -F '\[{tamperProtection}\]: Feature state:' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log | tail -n 1


```

Tilstanden skal være "block" (eller "audit"). Hvis det ikke er det, har du ikke angivet beskyttelsestilstanden for manipulation, hverken via `mdatp config` kommando eller via Intune.
