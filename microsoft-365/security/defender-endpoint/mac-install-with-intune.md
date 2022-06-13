---
title: Intune-baseret udrulning til Microsoft Defender for Endpoint på Mac
description: Installér Microsoft Defender for Endpoint på Mac ved hjælp af Microsoft Intune.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, installere, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 4c2c1f7c11c57ca45411b74023807077f73ba8bf
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044100"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Intune-baseret udrulning for Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I dette emne beskrives det, hvordan du installerer Microsoft Defender for Endpoint på macOS via Intune. En vellykket installation kræver fuldførelse af alle følgende trin:

1. [Download onboardingpakken](#download-the-onboarding-package)
1. [Konfiguration af klientenhed](#client-device-setup)
1. [Godkend systemudvidelser](#approve-system-extensions)
1. [Opret profiler til systemkonfiguration](#create-system-configuration-profiles)
1. [Udgiv program](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, kan du se [de primære Microsoft Defender for Endpoint på macOS side](microsoft-defender-endpoint-mac.md) for at få en beskrivelse af forudsætninger og systemkrav til den aktuelle softwareversion.

## <a name="overview"></a>Oversigt

I følgende tabel opsummeres de trin, du skal udføre for at udrulle og administrere Microsoft Defender for Endpoint på Macs via Intune. Du kan finde mere detaljerede trin nedenfor.

<br>

****

|Trin|Eksempelfilnavne|BundleIdentifier|
|---|---|---|
|[Download onboardingpakken](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Godkend systemudvidelse for Microsoft Defender for Endpoint](#approve-system-extensions)|MDATP_SysExt.xml|NIELSEN|
|[Godkend kerneudvidelse for Microsoft Defender for Endpoint](#download-the-onboarding-package)|MDATP_KExt.xml|NIELSEN|
|[Giv fuld diskadgang til Microsoft Defender for Endpoint](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Politik for netværksudvidelse](#network-filter)|MDATP_NetExt.xml|NIELSEN|
|[Konfigurer Microsoft Automatiske opdateringer (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[konfigurationsindstillinger for Microsoft Defender for Endpoint](mac-preferences.md#intune-full-profile) <p> **Bemærk:** Hvis du planlægger at køre en tredjeparts-AV for macOS, skal du angive `passiveMode` til `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Konfigurer meddelelser om Microsoft Defender for Endpoint og MS Automatiske opdateringer (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 eller com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakkerne fra Microsoft 365 Defender portalen:

1. I Microsoft 365 Defender portal skal du gå til **Indstillinger** \> **Onboarding** af **enhedshåndtering** \> **for slutpunkter**\>.

2. Angiv operativsystemet til **macOS** og installationsmetoden til **Mobile Enhedshåndtering/Microsoft Intune**.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Siden Onboarding-indstillinger" lightbox="images/macos-install-with-intune.png":::

3. Vælg **Download onboarding-pakke**. Gem den som _WindowsDefenderATPOnboardingPackage.zip_ i den samme mappe.

4. Udpak indholdet af den .zip fil:

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

## <a name="create-system-configuration-profiles"></a>Opret profiler til systemkonfiguration

Det næste trin er at oprette systemkonfigurationsprofiler, som Microsoft Defender for Endpoint har brug for.
Åbn **Enhedskonfigurationsprofiler** i [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/)\>.

### <a name="onboarding-blob"></a>Onboarding-blob

Denne profil indeholder licensoplysninger om Microsoft Defender for Endpoint. Uden denne profil rapporterer Microsoft Defender for Endpoint, at den ikke er givet i licens.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **Platform**= **macOS**, **Profiltypeskabeloner**=. **Skabelonnavn**= **Brugerdefineret**. Klik på **Opret**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Siden Til oprettelse af brugerdefineret konfigurationsprofil" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Vælg et navn til profilen, f.eks. "Defender for Cloud eller Endpoint onboarding for macOS". Klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Feltet Navn på brugerdefineret konfigurationsprofil" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Vælg et navn til konfigurationsprofilnavnet, f.eks. "Defender for Endpoint onboarding for macOS".
1. Vælg en [udrulningskanal](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Vælg intune/WindowsDefenderATPOnboarding.xml, som du udtrækkede fra onboardingpakken ovenfor som konfigurationsprofilfil.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Import af en konfiguration fra en fil til brugerdefineret konfigurationsprofil" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. Klik på **Næste**.
1. Tildel enheder under fanen **Tildeling** . Klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Den brugerdefinerede konfigurationsprofil – tildeling" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Gennemse og **opret**.
1. Åbn **Enhedskonfigurationsprofiler**\>. Du kan se din oprettede profil der.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Fuldførelse af den brugerdefinerede konfigurationsprofil" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Godkend systemudvidelser

Denne profil er nødvendig for macOS 10.15 (Catalina) eller nyere. Den ignoreres på ældre macOS.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **Platform**= **macOS**, **Profiltypeskabeloner**=. **Skabelonnavn**= **Udvidelser**. Klik på **Opret**.
1. Under fanen **Grundlæggende** skal du give denne nye profil et navn.
1. Under fanen **Konfigurationsindstillinger** skal du udvide **Systemudvidelser** tilføje følgende poster i afsnittet **Tilladte systemudvidelser** :

    |Bundt-id|Team-id|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Indstillingerne for systemets udvidelse" lightbox="images/mac-system-extension-intune2.png":::

1. Under fanen **Tildelinger** skal du tildele denne profil til **Alle brugere & Alle enheder**.
1. Gennemse og opret denne konfigurationsprofil.

### <a name="kernel-extensions"></a>Kerneudvidelser

Denne profil er nødvendig for macOS 10.15 (Catalina) eller ældre. Den ignoreres i nyere macOS.

> [!CAUTION]
> Apple Silicon-enheder (M1) understøtter ikke KEXT. Installationen af en konfigurationsprofil, der består af KEXT-politikker, mislykkes på disse enheder.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **Platform**= **macOS**, **Profiltypeskabeloner**=. **Skabelonnavn**= **Udvidelser**. Klik på **Opret**.
1. Under fanen **Grundlæggende** skal du give denne nye profil et navn.
1. På fanen **Konfigurationsindstillinger** skal du udvide **Kerneudvidelser**.
1. Angiv **Team-id** til **UBF8T346G9,** og klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-kernel-extension-intune2.png" alt-text="Tilladte team-id'er for kerneudvidelser." lightbox="images/mac-kernel-extension-intune2.png":::

1. Under fanen **Tildelinger** skal du tildele denne profil til **Alle brugere & Alle enheder**.
1. Gennemse og opret denne konfigurationsprofil.

### <a name="full-disk-access"></a>Fuld diskadgang

   > [!CAUTION]
   > macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til visse placeringer på disken (f.eks. dokumenter, downloads, desktop osv.) uden eksplicit samtykke. Hvis dette samtykke ikke er til stede, er Microsoft Defender for Endpoint ikke i stand til fuldt ud at beskytte din enhed.
   >
   > Denne konfigurationsprofil giver fuld diskadgang til Microsoft Defender for Endpoint. Hvis du tidligere har konfigureret Microsoft Defender for Endpoint via Intune, anbefaler vi, at du opdaterer installationen med denne konfigurationsprofil.

Download [**fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) fra [vores GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg instruktionerne for [Onboarding-blob](#onboarding-blob) ovenfor ved hjælp af "Defender for Endpoint Full Disk Access" som profilnavn og downloadet **fulldisk.mobileconfig** som konfigurationsprofilnavn.

### <a name="network-filter"></a>Netværksfilter

Som en del af slutpunktsregistrerings- og svarfunktionerne Microsoft Defender for Endpoint på macOS undersøger sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

Download [**netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) fra [vores GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg instruktionerne for [Onboarding-blob](#onboarding-blob) ovenfor ved hjælp af "Defender for Endpoint Network Filter" som profilnavn og **downloadet netfilter.mobileconfig** som konfigurationsprofilnavn.

### <a name="notifications"></a>Meddelelser

Denne profil bruges til at tillade, at Microsoft Defender for Endpoint på macOS og Microsoft Automatiske opdateringer får vist meddelelser i brugergrænsefladen på macOS 10.15 (Catalina) eller nyere.

Download [**notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) fra [vores GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg instruktionerne for [Onboarding-blob](#onboarding-blob) ovenfor ved hjælp af "Defender for Endpoint Notifications" som profilnavn og **downloadet notif.mobileconfig** som konfigurationsprofilnavn.

### <a name="view-status"></a>Vis status

Når de Intune ændringer overføres til de tilmeldte enheder, kan du se dem på listen under **Overvåg** \> **enhedsstatus**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Visningen af enhedens status" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Udgiv program

Dette trin gør det muligt at udrulle Microsoft Defender for Endpoint på tilmeldte maskiner.

1. Åbn **Apps** [i Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/).

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Programmets oversigtsside" lightbox="images/mdatp-8-app-before.png":::

1. Vælg Efter platform > macOS > Tilføj.
1. Vælg **Apptype**= **macOS** klik på **Vælg**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Den specifikke programtype" lightbox="images/mdatp-9-app-type.png":::

1. Bevar standardværdier, og klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Siden med programegenskaber" lightbox="images/mdatp-10-properties.png":::

1. Tilføj tildelinger, og klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Siden med oplysninger om Intune tildelinger" lightbox="images/mdatp-11-assignments.png":::

1. Gennemse og **opret**.
1. Du kan besøge **Apps** \> **Efter platform** \> **macOS** for at se det på listen over alle programmer.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Siden programlister" lightbox="images/mdatp-12-applications.png":::

Du kan få flere oplysninger under [Føj Microsoft Defender for Endpoint til macOS enheder ved hjælp af Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Du skal oprette alle de påkrævede konfigurationsprofiler og pushe dem til alle maskiner, som forklaret ovenfor.

## <a name="client-device-setup"></a>Konfiguration af klientenhed

Du behøver ikke nogen særlig klargøring til en Mac-enhed ud over en [standardinstallation Firmaportal](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Bekræft enhedshåndtering.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Siden Bekræft enhedshåndtering" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    Vælg **Åbn systemindstillinger**, find **Administrationsprofil** på listen, og vælg **Godkend...**. Din administrationsprofil vises som **Bekræftet**:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Profilsiden Administration" lightbox="images/mdatp-4-managementprofile.png":::

2. Vælg **Fortsæt** , og fuldfør tilmeldingen.

   Du kan nu tilmelde flere enheder. Du kan også tilmelde dem senere, når du er færdig med at klargøre systemkonfiguration og programpakker.

3. I Intune skal du åbne **Administrer** \> **enheder** \> **Alle enheder**. Her kan du se din enhed blandt dem, der er angivet:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Siden Alle enheder" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>Bekræft klientenhedstilstand

1. Når konfigurationsprofilerne er installeret på dine enheder, skal du åbne **Profiler for systemindstillinger** \> på din Mac-enhed.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Siden Systemindstillinger" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Siden Profiler for systemindstillinger" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Kontrollér, at følgende konfigurationsprofiler findes og er installeret. **Administrationsprofilen** skal være den Intune systemprofil. _Wdav-config_ og _wdav-kext_ er systemkonfigurationsprofiler, der blev tilføjet i Intune:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Siden Profiler" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. Du bør også se ikonet Microsoft Defender for Endpoint i øverste højre hjørne:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Ikonet for Microsoft Defender for Endpoint på statuslinjen" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Fejlfinding

Problem: Der blev ikke fundet en licens.

Løsning: Følg trinnene ovenfor for at oprette en enhedsprofil ved hjælp af WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Logføring af installationsproblemer

Du kan finde flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl, under [Logføring af installationsproblemer](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Uninstallation

Se [Fjernelse for](mac-resources.md#uninstalling) at få oplysninger om, hvordan du fjerner Microsoft Defender for Endpoint på macOS fra klientenheder.
