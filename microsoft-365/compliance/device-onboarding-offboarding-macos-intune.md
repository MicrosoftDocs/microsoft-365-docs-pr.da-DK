---
title: Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp Microsoft Intune (preview)
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
description: Lær at onboarde og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp Microsoft Intune (preview)
ms.openlocfilehash: 5f8dd27490992e15d53dfc10311ce7b23b99683a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596930"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview"></a>Onboard and offboard macOS devices into Microsoft 365 Compliance solutions using Intune (preview)

Du kan bruge Intune til at onboarde macOS-enheder Microsoft 365 løsninger til overholdelse af regler og standarder.

> [!IMPORTANT]
> Brug denne fremgangsmåde, hvis ***du ikke har*** Installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, [at dine macOS-enheder er onboardet i Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) og er tilmeldt [Firmaportal app](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Sørg for, at du har adgang [til Microsoft Endpoint Manager center](https://endpoint.microsoft.com/#home).
- Dette understøtter macOS version Catalina 10.15 og nyere.
- Opret de brugergrupper, du vil tildele konfigurationsopdateringerne til.
- Installér browseren v95+ Edge på dine macOS-enheder 


## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Onboard macOS-enheder i Microsoft 365 Compliance-løsninger ved hjælp Microsoft Intune

Onboarding af en macOS-enhed i løsninger til overholdelse af regler og standarder er en seksfaset proces.

1. [Opret systemkonfigurationsprofiler](#create-system-configuration-profiles)
1. [Hent onboardingpakken til enheden](#get-the-device-onboarding-package)
1. [Installer onboardingpakken](#deploy-the-onboarding-package)
1. [Aktivér systemudvidelse](#enable-system-extension)
1. [Hent installationspakken](#get-the-installation-package)
1. [Installér installationspakken](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>Opret systemkonfigurationsprofiler

1. Du skal bruge disse filer til denne procedure.

|fil, der skal bruges til |kilde |
|---------|---------|
|Onboardingpakke    |downloadet fra **onboardingpakken til overholdelsesportalen**, *DeviceComplianceOnboarding.xml* |
|tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Netværks filer| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|Systemudvidelser |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE-indstilling     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|MAU-indstilling|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|Installationspakke     |downloadet fra installationspakken **til overholdelsesportalen**, *filnavnet\* wdav.pkg*\* |

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvis eller i [en enkelt kombineret fil,](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - systemudvidelser
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten hente den kombinerede fil igen eller den enkelt opdaterede fil enkeltvis.

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

2. Åbn **Microsoft Endpoint Manager** **CenterKonfigurationsprofiler** >  > .

1. Vælg: **Opret profil** 

1. Vælg:
    1. **Platform = macOS**
    1. **Profiltype = Skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *. AccessibilityformacOS* i dette eksempel. Vælg **Næste**.

1. Vælg den **accessibility.mobileconfig-fil** , du hentede i trin 1, som konfigurationsprofilfil.

1. Vælg **Næste**

1. På fanen **Opgaver skal** du tilføje den gruppe, du vil implementere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

1. Gentag trin 3-11 for at oprette profiler for:
    1. **fulldisk.mobileconfig-fil**
    1. **com.microsoft.autoupdate2.xml** fil
    1. **MDE-indstillingercom.microsoft.wdav.xml** fil
        1. angiv Antivirusprogram `passive mode` = `true` eller `false`. Brug `true`, hvis du kun installerer DLP. Brug `false` eller tildel ikke en værdi, hvis du installerer DLP og Microsoft Defender for Endpoint (MDE).
    1. **netfilter.mobileconfig**
 
1. Åbn **EnhederKonfigurationsprofiler** > , bør du kunne se dine oprettede profiler der.

1. På siden **Konfigurationsprofiler** skal du vælge den profil, du lige har oprettet, i dette eksempel *AccessibilityformacOS* og vælge Enhedsstatus for at få vist en liste over enheder og installationsstatus for konfigurationsprofilen.

### <a name="get-the-device-onboarding-package"></a>Hent onboardingpakken til enheden

1. I **Overholdelsescenter** skal **du** **Indstillinger-onboarding** >  og vælge **Onboarding**.
 
1. Ud **for Vælg operativsystem for at starte onboardingprocessen skal** du vælge **macOS**.
 
1. **Udrulningsmetode** **skal du vælge Administration/Microsoft Intune**.
 
1. Vælg **Download onboarding pakke**. Denne indeholder onboardingkoden *iDeviceComplianceOnboarding.xmlfil* .

### <a name="deploy-the-onboarding-package"></a>Installer onboardingpakken

1. Åbn **Microsoft Endpoint Manager** **CenterKonfigurationsprofiler** >  > .

1. Vælg: **Opret profil**. 

1. Vælg:
    1. **Platform = macOS**
    1. **Profiltype = Skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *OnboardingPackage* i dette eksempel. Vælg **Næste**.

1. Vælg *DeviceComplianceOnboarding.xmlsom* konfigurationsprofilfil.

1. Vælg **Næste**

1. På fanen **Opgaver skal** du tilføje den gruppe, du vil implementere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

### <a name="enable-system-extension"></a>Aktivér systemudvidelse

1. Vælg Opret **profil Microsoft Endpoint Manager** **konfigurationsprofiler** i **søgecenteret**

1. Vælg:
    1. **Platform = macOS**
    1. **Profiltype = Skabeloner**
    1. **Skabelonnavn = Udvidelser**

1. Vælg **Opret**

1. Giv **den nye** profil et navn under fanen Grundlæggende.

1. På fanen **Konfigurationsindstillinger** skal du udvide **Systemudvidelser**.

1. Angiv **disse værdier under Bundle-id** og **Team-id**

|Bundle-id  |Team-id  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. På fanen **Opgaver skal** du tilføje den gruppe, du vil implementere disse konfigurationer i, og vælge **Næste**.

1. Vælg **Næste** for at installere konfigurationen.

### <a name="get-the-installation-package"></a>Hent installationspakken

1. I **Overholdelsescenter** skal **du** **Indstillinger-onboarding** >  og vælge **Onboarding**.
 
1. Vælg macOS **for at vælge operativsystem for at starte** **onboardingprocessen**
 
1. **Udrulningsmetode** **vælger Administration/Microsoft Intune**
 
1. Vælg **Download installationspakke**. Dette giver dig *filen wdav.pkg* .

> [!IMPORTANT]
> Før du kan installere *wdav.pkg.* pakke via Intune, skal den omformateres ved hjælp af *Intune App Wrapping Tools til Mac* i *wdav.pkg.intunemac-formatet* .
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>Installér Microsoft DLP-installationspakken

1. Følg fremgangsmåden i Sådan tilføjer du [macOS LOB-apps (line of business)](/mem/intune/apps/lob-apps-macos) for at Microsoft Intune for at konvertere *wdav.pkg-filen* til det korrekte format og udrulle den via Intune.

## <a name="offboard-macos-devices-using-intune"></a>Offboard macOS-enheder ved hjælp af Intune

> [!NOTE]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

2. I **Microsoft Endpoint Manager center** skal du **åbne** **EnhederKonfigurationsprofiler** > , hvor du bør kunne se dine oprettede profiler.

1. På siden **Konfigurationsprofiler** skal du vælge *wdav.pkg.intunemac-profilen* .

1. Vælg **Enhedsstatus** for at få vist en liste over enheder og installationsstatus for konfigurationsprofilen

1. Åbn **Egenskaber** **og Opgaver**

1. Fjern gruppen fra opgaven. Dette fjerner *wdav.pkg.intunemac-pakken* og offboardet på macOS-enheden fra Compliance Solutions.
