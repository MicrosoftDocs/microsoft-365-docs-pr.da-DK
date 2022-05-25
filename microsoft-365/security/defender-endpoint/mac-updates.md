---
title: Installer opdateringer til Microsoft Defender for Endpoint på Mac
description: Kontrollér opdateringer til Microsoft Defender for Endpoint på Mac i virksomhedsmiljøer.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, updates, deploy
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
ms.openlocfilehash: 4612c7ca68ab0b55fa2a2f28821cb5baef6ff6e9
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669336"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>Installer opdateringer til Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner.

Hvis du vil opdatere Microsoft Defender for Endpoint på macOS, bruges et program med navnet Microsoft Automatiske opdateringer (MAU). MAU søger som standard automatisk efter opdateringer dagligt, men du kan ændre dette til ugentligt, månedligt eller manuelt.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="MAU" lightbox="images/MDATP-34-MAU.png":::

Hvis du beslutter at installere opdateringer ved hjælp af dine softwaredistributionsværktøjer, skal du konfigurere MAU til manuelt at søge efter softwareopdateringer. Du kan udrulle indstillinger for at konfigurere, hvordan og hvornår MAU søger efter opdateringer til Macs i din organisation.

## <a name="use-msupdate"></a>Brug msupdate

MAU indeholder et kommandolinjeværktøj, *der kaldes msupdate*, som er udviklet til it-administratorer, så de har mere præcis kontrol over, hvornår der anvendes opdateringer. Du kan finde instruktioner til, hvordan du bruger dette værktøj, i [Opdater Office til Mac ved hjælp af msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

I MAU er program-id'et for Microsoft Defender for Endpoint på macOS *WDAV00*. Hvis du vil hente og installere de nyeste opdateringer til Microsoft Defender for Endpoint på macOS, skal du udføre følgende kommando fra et terminalvindue:

```dos
cd /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app/Contents/MacOS
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>Angiv indstillinger for Microsoft Automatiske opdateringer

I dette afsnit beskrives de mest almindelige indstillinger, der kan bruges til at konfigurere MAU. Disse indstillinger kan installeres som en konfigurationsprofil via den administrationskonsol, som din virksomhed bruger. Der vises et eksempel på en konfigurationsprofil i følgende afsnit.

### <a name="set-the-channel-name"></a>Angiv kanalnavnet

Kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes via MAU. Enheder i `Beta` kan afprøve nye funktioner, før enheder i `Preview` og `Current`.

Kanalen `Current` indeholder den mest stabile version af produktet.

> [!IMPORTANT]
> Før Microsoft Automatiske opdateringer version 4.29 havde kanaler forskellige navne:
>
> - `Beta` blev navngivet `InsiderFast` (Insider Fast)
> - `Preview` blev navngivet `External` (Insider Slow)
> - `Current` blev navngivet `Production`

> [!TIP]
> Hvis du vil have forhåndsvist nye funktioner og give tidlig feedback, anbefales det, at du konfigurerer nogle enheder i virksomheden til `Beta` eller `Preview`.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|ChannelName|
|**Datatype**|String|
|**Mulige værdier**|Beta <p> Preview <p> Nuværende|
|||

> [!WARNING]
> Denne indstilling ændrer kanalen for alle programmer, der opdateres via Microsoft Automatiske opdateringer. Hvis du kun vil ændre kanalen for Microsoft Defender for Endpoint på macOS, skal du udføre følgende kommando, når du har erstattet `[channel-name]` med den ønskede kanal:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>Angiv hyppigheden for opdateringskontrol

Rediger, hvor ofte MAU søger efter opdateringer.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|UpdateCheckFrequency|
|**Datatype**|Heltal|
|**Standardværdien**|720 (minutter)|
|**Kommenter**|Denne værdi er angivet i minutter.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>Rediger, hvordan MAU interagerer med opdateringer

Rediger, hvordan MAU søger efter opdateringer.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|HowToCheck|
|**Datatype**|String|
|**Mulige værdier**|Manuel <p> Automatisk kontrol <p> Automatiskdownload|
|**Kommenter**|Bemærk, at AutomaticDownload downloader og installerer uovervåget, hvis det er muligt.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>Rediger, om knappen "Søg efter opdateringer" er aktiveret

Rediger, om lokale brugere skal kunne klikke på indstillingen "Søg efter opdateringer" i brugergrænsefladen i Microsoft Automatiske opdateringer.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|EnableCheckForUpdatesButton|
|**Datatype**|Boolesk |
|**Mulige værdier**|Sand (standard) <p> Falsk|
|||

### <a name="disable-insider-checkbox"></a>Deaktiver Insider-afkrydsningsfelt

Angiv til true for at gøre "Join the Office Insider Program..." ikke er tilgængeligt/nedtonet for brugerne.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|DisableInsiderCheckbox|
|**Datatype**|Boolesk |
|**Mulige værdier**|Falsk (standard) <p> Sandt|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>Begræns den telemetri, der sendes fra MAU

Indstillet til falsk for at sende minimal impulsdata, ingen programanvendelse og ingen miljøoplysninger.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.autoupdate2`|
|**Tast**|SendAllTelemetryEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|Sand (standard) <p> Falsk|
|||

## <a name="example-configuration-profile"></a>Eksempel på konfigurationsprofil

Følgende konfigurationsprofil bruges til at:

- Placer enheden i produktionskanalen
- Download og installér automatisk opdateringer
- Aktivér knappen "Søg efter opdateringer" i brugergrænsefladen
- Tillad brugere på enheden at tilmelde sig Insider-kanalerne

> [!WARNING]
> Nedenstående konfiguration er et eksempel på konfiguration og bør ikke bruges i produktion uden korrekt gennemgang af indstillinger og skræddersy af konfigurationer.

> [!TIP]
> Hvis du vil have forhåndsvist nye funktioner og give tidlig feedback, anbefales det, at du konfigurerer nogle enheder i virksomheden til `Beta` eller `Preview`.

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

Hvis du vil konfigurere MAU, kan du installere denne konfigurationsprofil fra det administrationsværktøj, som din virksomhed bruger:

- Fra JAMF skal du uploade denne konfigurationsprofil og angive præferencedomænet til *com.microsoft.autoupdate2*.
- Fra Intune skal du uploade denne konfigurationsprofil og angive navnet på den brugerdefinerede konfigurationsprofil til *com.microsoft.autoupdate2*.

## <a name="resources"></a>Ressourcer

- [msupdate-reference](/deployoffice/mac/update-office-for-mac-using-msupdate)
