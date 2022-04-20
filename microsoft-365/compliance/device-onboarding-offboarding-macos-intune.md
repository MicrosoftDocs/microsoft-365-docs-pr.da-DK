---
title: Onboarde og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Microsoft Intune
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Få mere at vide om, hvordan du onboarder og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Microsoft Intune
ms.openlocfilehash: 99a407b2b0c8d6a506cd138078b3f35cf9e5a232
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952968"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>Onboarde og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Intune

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge Intune til at integrere macOS-enheder i Microsoft Purview-løsninger.

> [!IMPORTANT]
> Brug denne fremgangsmåde, hvis du ***ikke*** har installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at dine [macOS-enheder er onboardet i Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) og er tilmeldt [Firmaportal-appen](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Sørg for, at du har adgang til [Microsoft Endpoint Manager center](https://endpoint.microsoft.com/#home).
- Dette understøtter macOS-version Catalina 10.15 og nyere.
- Opret de brugergrupper, du vil tildele konfigurationsopdateringerne til.
- Installér v95+ Edge-browseren på dine macOS-enheder 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Onboarde macOS-enheder i Microsoft Purview-løsninger ved hjælp af Microsoft Intune

Onboarding af en macOS-enhed i overholdelsesløsninger er en seksfaset proces.

1. [Opret systemkonfigurationsprofiler](#create-system-configuration-profiles)
1. [Hent onboardingpakken til enheden](#get-the-device-onboarding-package)
1. [Udrul onboardingpakken](#deploy-the-onboarding-package)
1. [Aktivér systemudvidelse](#enable-system-extension)
1. [Hent installationspakken](#get-the-installation-package)
1. [Installer installationspakken](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Opret systemkonfigurationsprofiler

1. Du skal bruge disse filer til denne procedure.

|fil, der er nødvendig for |Kilde |
|---------|---------|
|Onboarding-pakke    |downloadet fra **onboardingpakken til overholdelsesportalen**, *filnavnDeviceComplianceOnboarding.xml* |
|Tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Netværks filer| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Systemudvidelser |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE-indstillinger     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|MAU-indstillinger|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Installationspakke     |downloadet fra **installationspakken** til overholdelsesportalen, filnavn *\*wdav.pkg*\* |

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvist eller i [en enkelt kombineret fil](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - systemudvidelser
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten downloade den kombinerede fil igen eller den enkelte opdaterede fil enkeltvist.

<!--2. Copy this code and save it in a file named `com.microsoft.autoupdate2.xml`.

```xml
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
-->

2. Åbn **profilerne Microsoft Endpoint Manager** **centerDevicesConfiguration** >  > .

1. Vælg: **Opret profil** 

1. Vælge:
    1. **Platform = macOS**
    1. **Profiltype = skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *. AccessibilityformacOS* i dette eksempel. Vælg **Næste**.

1. Vælg den **accessibility.mobileconfig-fil** , du downloadede i trin 1, som konfigurationsprofilfil.

1. Vælg **næste**

1. Under fanen **Tildelinger** skal du tilføje den gruppe, du vil installere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

1. Gentag trin 3-11 for at oprette profiler for:
    1. **fulldisk.mobileconfig-fil**
    1. **com.microsoft.autoupdate2.xml** fil
    1. MDE-indstillinger **com.microsoft.wdav.xml** fil
        1. set Antivirusprogram `passive mode` = `true` eller `false`. Bruges `true`kun, hvis der installeres DLP. Brug `false` eller tildel ikke en værdi, hvis du installerer DLP og Microsoft Defender for Endpoint (MDE).
    1. **netfilter.mobileconfig**
 
1. Åbn **DevicesConfiguration-profiler** > . Du kan se dine oprettede profiler der.

1. På siden **Konfigurationsprofiler** skal du vælge den profil, du lige har oprettet, i dette eksempel *AccessibilityformacOS* og vælge **Enhedsstatus** for at få vist en liste over enheder og installationsstatussen for konfigurationsprofilen.

### <a name="get-the-device-onboarding-package"></a>Hent onboardingpakken til enheden

1. I **Compliance Center** skal **du åbne Indstillinger** >  **Device Onboarding** og vælge **Onboarding**.
 
1. Vælg **macOS** **for Vælg operativsystem for at starte onboardingprocessen**.
 
1. Vælg **Mobil Enhedshåndtering/Microsoft Intune** som **installationsmetode**.
 
1. Vælg **Download onboarding-pakke**. Dette indeholder onboardingkoden i *filenDeviceComplianceOnboarding.xml* .

### <a name="deploy-the-onboarding-package"></a>Udrul onboardingpakken

1. Åbn **profilerne Microsoft Endpoint Manager** **centerDevicesConfiguration** >  > .

1. Vælg: **Opret profil**. 

1. Vælge:
    1. **Platform = macOS**
    1. **Profiltype = skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *. OnboardingPackage* i dette eksempel. Vælg **Næste**.

1. Vælg den *DeviceComplianceOnboarding.xml* fil som konfigurationsprofilfil.

1. Vælg **næste**

1. Under fanen **Tildelinger** skal du tilføje den gruppe, du vil installere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

### <a name="enable-system-extension"></a>Aktivér systemudvidelse

1. I **Microsoft Endpoint Manager skal** du vælge **Opret profil** under **Konfigurationsprofiler**

1. Vælge:
    1. **Platform = macOS**
    1. **Profiltype = skabeloner**
    1. **Skabelonnavn = Udvidelser**

1. Vælg **Opret**

1. Under fanen **Grundlæggende** skal du give denne nye profil et navn.

1. Under fanen **Konfigurationsindstillinger** skal du udvide **Systemudvidelser**.

1. Angiv disse værdier under **Bundt-id** og **Team-id**

|Bundt-id  |Team-id  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. Under fanen **Tildelinger** skal du tilføje den gruppe, du vil installere disse konfigurationer i, og vælge **Næste**.

1. Vælg **Næste** for at installere konfigurationen.

### <a name="get-the-installation-package"></a>Hent installationspakken

1. I **Compliance Center** skal **du åbne Indstillinger** >  **Device Onboarding** og vælge **Onboarding**.
 
1. **Vælg macOS for Vælg operativsystem for at starte onboardingprocessen** 
 
1. Vælg **Mobile Enhedshåndtering/Microsoft Intune** for **installationsmetode**
 
1. Vælg **Download installationspakke**. Dette giver dig filen *wdav.pkg* .

> [!IMPORTANT]
> Før du kan installere *wdav.pkg.* pakke via Intune, skal den omformateres ved hjælp af *Intune App Wrapping Tools til Mac* til *formatet wdav.pkg.intunemac*.
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Installer Microsoft DLP-installationspakken

1. Følg procedurerne i [Sådan tilføjer du macOS LOB-apps (line-of-business) for at Microsoft Intune](/mem/intune/apps/lob-apps-macos) til at konvertere *wdav.pkg-filen* til det korrekte format og udrulle den via Intune.

## <a name="offboard-macos-devices-using-intune"></a>MacOS-enheder uden for bord ved hjælp af Intune

> [!NOTE]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

2. I **Microsoft Endpoint Manager center** skal du åbne **DevicesConfiguration-profiler** > . Du kan se dine oprettede profiler der.

1. På siden **Konfigurationsprofiler** skal du vælge profilen *wdav.pkg.intunemac* .

1. Vælg **Enhedsstatus** for at få vist en liste over enheder og installationsstatus for konfigurationsprofilen

1. Åbn **egenskaber** og **tildelinger**

1. Fjern gruppen fra tildelingen. Dette fjerner *wdav.pkg.intunemac-pakken* og fjerner macOS-enheden fra Overholdelsesløsninger.
