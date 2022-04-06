---
title: Installér opdateringer til Microsoft Defender for Endpoint på Mac
description: Styr opdateringer til Microsoft Defender for Endpoint på Mac i virksomhedsmiljøer.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, opdateringer, installér
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
ms.openlocfilehash: 0b9ddf9693a242b3b8c466cfa1616b62c5eb73b9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469289"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Installér opdateringer til Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner.

Hvis du Microsoft Defender for Endpoint opdateringer på macOS, bruges et program med navnet Microsoft AutoUpdate (MAU). Som standard søger MAU automatisk efter opdateringer dagligt, men du kan ændre det til ugentligt, månedligt eller manuelt.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Hvis du beslutter dig for at installere opdateringer ved hjælp af dine softwaredistributionsværktøjer, skal du konfigurere MAU til manuelt at søge efter softwareopdateringer. Du kan installere indstillinger for at konfigurere, hvordan og hvornår MAU søger efter opdateringer til Mac-computere i organisationen.

## <a name="use-msupdate"></a>Brug msupdate

MAU indeholder et kommandolinjeværktøj kaldet *msupdate*, som er udviklet til it-administratorer, så de har mere præcis kontrol over, hvornår der anvendes opdateringer. Du kan finde en vejledning til, hvordan du bruger dette værktøj[, Office til Mac ved hjælp af msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

I MAU er programidentifikatoren for Microsoft Defender for Endpoint på macOS *WDAV00*. For at downloade og installere de seneste opdateringer til Microsoft Defender for Endpoint på macOS skal du udføre følgende kommando fra et Terminal-vindue:

```dos
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Angiv indstillinger for Microsoft Automatiske opdateringer

I dette afsnit beskrives de mest almindelige indstillinger, der kan bruges til at konfigurere MAU. Disse indstillinger kan installeres som en konfigurationsprofil via den administrationskonsol, din virksomhed bruger. Et eksempel på en konfigurationsprofil vises i de følgende afsnit.

### <a name="set-the-channel-name"></a>Angiv kanalnavnet

Kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes via MAU. Enheder i `Beta` kan prøve nye funktioner før enheder i `Preview` og `Current`.

Kanalen `Current` indeholder den mest stabile version af produktet.

> [!IMPORTANT]
> Før version 4.29 af Microsoft Automatiske opdateringer havde kanaler forskellige navne:
>
> - `Beta` blev navngivet `InsiderFast` (Insider Fast)
> - `Preview` blev navngivet `External` (Insider Slow)
> - `Current` blev navngivet `Production`

> [!TIP]
> For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer visse enheder i virksomheden til eller `Beta` `Preview`.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|ChannelName|
|**Datatype**|String|
|**Mulige værdier**|Beta <p> Eksempel <p> Aktuel|
|||

> [!WARNING]
> Denne indstilling ændrer kanalen for alle programmer, der opdateres via Microsoft Automatiske opdateringer. Hvis du kun vil ændre kanalen for Microsoft Defender for Endpoint i macOS, skal du udføre følgende kommando efter at have erstattet `[channel-name]` med den ønskede kanal:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Angiv hyppigheden for opdateringskontrol

Rediger, hvor ofte MAU søger efter opdateringer.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|UpdateCheckFrequency|
|**Datatype**|Heltal|
|**Standardværdi**|720 (minutter)|
|**Kommenter**|Denne værdi er angivet i minutter.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>Ændre måden MAU interagerer med opdateringer på

Rediger, hvordan MAU søger efter opdateringer.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|HowToCheck|
|**Datatype**|String|
|**Mulige værdier**|Manuel <p> AutomaticCheck <p> AutomaticDownload|
|**Kommenter**|Bemærk, at AutomaticDownload automatisk downloader og installerer automatisk, hvis det er muligt.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Ændre, om knappen "Søg efter opdateringer" er aktiveret

Rediger, om lokale brugere skal kunne klikke på indstillingen "Søg efter opdateringer" i brugergrænsefladen Microsoft Automatiske opdateringer.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|EnableCheckForUpdatesButton|
|**Datatype**|Boolesk |
|**Mulige værdier**|Sand (standard) <p> Falsk|
|||

### <a name="disable-insider-checkbox"></a>Afkrydsningsfeltet Deaktiver Insider

Indstillet til sand for at gøre "Deltag Office Insider Program..." ikke tilgængeligt/nedtonet for brugere.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|DisableInsiderCheckbox|
|**Datatype**|Boolesk |
|**Mulige værdier**|Falsk (standard) <p> Sand|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Begræns den telemetri, der sendes fra MAU

Indstillet til falsk for at sende minimale heartbeat-data, ingen anvendelse af programmet og ingen miljødetaljer.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|SendAllTelemetryEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|Sand (standard) <p> Falsk|
|||

## <a name="example-configuration-profile"></a>Eksempel på konfigurationsprofil

Følgende konfigurationsprofil bruges til at:

- Placer enheden i produktionskanalen
- Hent og installér opdateringer automatisk
- Aktivér knappen "Søg efter opdateringer" i brugergrænsefladen
- Tillad brugere på enheden at tilmelde sig Insider-kanalerne

> [!WARNING]
> Nedenstående konfiguration er en eksempelkonfiguration og bør ikke bruges i produktion uden korrekt gennemgang af indstillinger og skræddersy af konfigurationer.

> [!TIP]
> For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer visse enheder i virksomheden til eller `Beta` `Preview`.

### <a name="jamf"></a>JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>ChannelName</key>
    <string>Production</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
</dict>
</plist>
```

### <a name="intune"></a>Intune

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
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
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```

Hvis du vil konfigurere MAU, kan du installere denne konfigurationsprofil fra det administrationsværktøj, din virksomhed bruger:

- Fra SYLF skal du uploade denne konfigurationsprofil og angive Præferencedomænet *til com.microsoft.autoupdate2*.
- Fra Intune skal du uploade denne konfigurationsprofil og angive navnet på den brugerdefinerede konfigurationsprofil *til com.microsoft.autoupdate2*.

## <a name="resources"></a>Ressourcer

- [msupdate-reference](/deployoffice/mac/update-office-for-mac-using-msupdate)
