---
title: Intune-baseret installation til Microsoft Defender til Slutpunkt på Mac
description: Installér Microsoft Defender til slutpunkt på Mac ved hjælp Microsoft Intune.
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
ms.openlocfilehash: 4979ee5f3953ced1073779fdcabb7eb361d4911a
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63591887"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Intune-baseret installation til Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I dette emne beskrives det, hvordan du installerer Microsoft Defender til Endpoint på macOS via Intune. En vellykket installation kræver, at alle følgende trin er gennemført:

1. [Download onboardingpakken](#download-the-onboarding-package)
1. [Konfiguration af klientenhed](#client-device-setup)
1. [Godkend systemudvidelser](#approve-system-extensions)
1. [Opret systemkonfigurationsprofiler](#create-system-configuration-profiles)
1. [Publicer program](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du se microsoft [Defender for Endpoint på macOS-hovedsiden](microsoft-defender-endpoint-mac.md) for en beskrivelse af forudsætningerne og systemkravene for den aktuelle softwareversion.

## <a name="overview"></a>Oversigt

Følgende tabel opsummerer de trin, du skal bruge for at installere og administrere Microsoft Defender til Slutpunkt på Macs via Intune. Mere detaljerede trin er tilgængelige nedenfor.

<br>

****

|Trin|Eksempel på filnavne|BundleIdentifier|
|---|---|---|
|[Download onboardingpakken](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Godkend systemudvidelse til Microsoft Defender til slutpunkt](#approve-system-extensions)|MDATP_SysExt.xml|I/T|
|[Godkend kerneludvidelse til Microsoft Defender til slutpunkt](#download-the-onboarding-package)|MDATP_KExt.xml|I/T|
|[Giv fuld diskadgang til Microsoft Defender til Slutpunkt](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Politik for netværksudvidelse](#network-filter)|MDATP_NetExt.xml|I/T|
|[Konfigurere Microsoft Automatiske opdateringer (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[Konfigurationsindstillinger for Microsoft Defender til Slutpunkt](mac-preferences.md#intune-full-profile) <p> **Bemærk!** Hvis du planlægger at køre en tredjeparts AV til macOS, skal du indstille den `passiveMode` til `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Konfigurer Microsoft Defender til slutpunkts- og MS AutoUpdate-meddelelser (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 eller com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakkerne fra Microsoft 365 Defender portal:

1. I Microsoft 365 Defender, skal du gå **til Indstillinger** \> **slutpunkter onboarding** \> **til** \> **enhedshåndtering**.

2. Indstil operativsystemet til **macOS** og installationsmetoden til **Administration af mobilenheder/Microsoft Intune**.

    ![Skærmbillede af indstillinger for onboarding.](images/macos-install-with-intune.png)

3. Vælg **Download onboarding pakke**. Gem den som _WindowsDefenderATPOnboardingPackage.zip_ i den samme mappe.

4. Udtræk indholdet af .zip fil:

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

## <a name="create-system-configuration-profiles"></a>Opret systemkonfigurationsprofiler

Det næste trin er at oprette systemkonfigurationsprofiler, som skal bruges af Microsoft Defender til slutpunkt.
I administration [Microsoft Endpoint Manager skal du åbne](https://endpoint.microsoft.com/) **Enheders** \> **konfigurationsprofiler**.

### <a name="onboarding-blob"></a>Onboarding-blob

Denne profil indeholder licensoplysninger for Microsoft Defender til slutpunkt. Uden denne profil vil Microsoft Defender til slutpunkt rapportere, at den ikke er licenseret.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **PlatformmacOS**=, **ProfiltypeTemplates**=. **Skabelonnavn**= **Brugerdefineret**. Klik **på Opret**.

    > [!div class="mx-imgBorder"]
    > ![Oprettelse af brugerdefineret konfigurationsprofil.](images/mdatp-6-systemconfigurationprofiles-1.png)

1. Vælg et navn til profilen, f.eks. "Defender til cloud- eller slutpunkt-onboarding til macOS". Klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Brugerdefineret konfigurationsprofil – navn.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. Vælg et navn til konfigurationsprofilnavnet, f.eks. "Defender til slutpunkt-onboarding til macOS".
1. Vælg en [installationskanal](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Vælg intune/WindowsDefenderATPOnboarding.xml, du udtrækkede fra onboardingpakken ovenfor som konfigurationsprofilfil.

    > [!div class="mx-imgBorder"]
    > ![Importere en konfiguration fra en fil til brugerdefineret konfigurationsprofil.](images/mdatp-6-systemconfigurationprofiles.png)

1. Klik på **Næste**.
1. Tildel enheder under **fanen Opgave** . Klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Brugerdefineret konfigurationsprofil – tildeling.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. Gennemse og **opret**.
1. Åbn **Enheder** \> **Konfigurationsprofiler**, du kan se din oprettede profil der.

    > [!div class="mx-imgBorder"]
    > ![Brugerdefineret konfigurationsprofil – udført.](images/mdatp-6-systemconfigurationprofiles-3.png)

### <a name="approve-system-extensions"></a>Godkend systemudvidelser

Denne profil er nødvendig til macOS 10.15 (Catalina) eller nyere. Den ignoreres på ældre macOS.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **PlatformmacOS**=, **ProfiltypeTemplates**=. **Skabelonnavn**= **Udvidelser**. Klik **på Opret**.
1. Giv **denne nye** profil et navn under fanen Grundlæggende.
1. På fanen **Konfigurationsindstillinger** skal du udvide **Systemudvidelser** og tilføje følgende poster i afsnittet **Tilladte systemudvidelser** :

    |Bundle-id|Team-id|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > ![Indstillinger for systemudvidelse.](images/mac-system-extension-intune2.png)

1. I fanen **Opgaver skal** du tildele denne profil til **Alle brugere & Alle enheder**.
1. Gennemse og opret denne konfigurationsprofil.

### <a name="kernel-extensions"></a>Kerneudvidelser

Denne profil er nødvendig til macOS 10.15 (Catalina) eller ældre. Den ignoreres på nyere macOS.

> [!CAUTION]
> Apple Silicon-enheder (M1) understøtter ikke KEXT. Installation af en konfigurationsprofil bestående af KEXT-politikker mislykkes på disse enheder.

1. Vælg **Opret profil** under **Konfigurationsprofiler**.
1. Vælg **PlatformmacOS**=, **ProfiltypeTemplates**=. **Skabelonnavn**= **Udvidelser**. Klik **på Opret**.
1. Giv **denne nye** profil et navn under fanen Grundlæggende.
1. På fanen **Konfigurationsindstillinger** skal du udvide **Kerneudvidelser**.
1. **Indstil Team-id** **til UBF8T346G9**, og klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Indstillinger for kerneletudvidelse.](images/mac-kernel-extension-intune2.png)

1. I fanen **Opgaver skal** du tildele denne profil til **Alle brugere & Alle enheder**.
1. Gennemse og opret denne konfigurationsprofil.

### <a name="full-disk-access"></a>Fuld diskadgang

   > [!CAUTION]
   > macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til bestemte placeringer på disken (f.eks Dokumenter, Overførsler, Skrivebord osv.) uden udtrykkeligt samtykke. I fravær af dette samtykke kan Microsoft Defender til Slutpunkt ikke fuldt ud beskytte din enhed.
   >
   > Denne konfigurationsprofil giver fuld diskadgang til Microsoft Defender til slutpunkt. Hvis du tidligere har konfigureret Microsoft Defender til slutpunkt via Intune, anbefaler vi, at du opdaterer installationen med denne konfigurationsprofil.

Download [**fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) [fra GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg vejledningen for [Onboarding blob](#onboarding-blob) ovenfra ved hjælp af "Defender for Full Disk Access" som profilnavn, og download **fulldisk.mobileconfig** som Konfigurationsprofilnavn.

### <a name="network-filter"></a>Netværksfilter

Som en del af egenskaberne Slutpunktsregistrering og Svar undersøger Microsoft Defender til slutpunkt på macOS sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

Download [**netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) [fra GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg vejledningen for [Onboarding blob](#onboarding-blob) ovenfra ved hjælp af "Defender for Endpoint Network Filter" som profilnavn, og downloaded **netfilter.mobileconfig** som Konfigurationsprofilnavn.

### <a name="notifications"></a>Meddelelser

Denne profil bruges til at tillade, at Microsoft Defender til slutpunkt på macOS og Microsoft Automatiske opdateringer viser meddelelser i brugergrænsefladen på macOS 10.15 (Catalina) eller nyere.

Download [**notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) [fra GitHub lager](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Følg vejledningen for [Onboarding blob](#onboarding-blob) ovenfra ved hjælp af "Defender for Endpoint Notifications" som profilnavn, og downloaded **notif.mobileconfig** som Konfigurationsprofilnavn.

### <a name="view-status"></a>Vis status

Når intune-ændringerne er overført til de tilmeldte enheder, kan du se dem angivet under Status **for** \> **skærmenhed**:

> [!div class="mx-imgBorder"]
> ![Visning af enhedsstatus under Skærm.](images/mdatp-7-devicestatusblade.png)

## <a name="publish-application"></a>Publicer program

Dette trin gør det muligt at udrulle Microsoft Defender til slutpunkt på tilmeldte computere.

1. I [Microsoft Endpoint Manager Administration skal](https://endpoint.microsoft.com/) du åbne **Apps**.

    > [!div class="mx-imgBorder"]
    > ![Klar til at oprette programmet.](images/mdatp-8-app-before.png)

1. Vælg Efter platform > macOS > Tilføj.
1. Vælg **ApptypemacOS**=, og klik på **Vælg**.

    > [!div class="mx-imgBorder"]
    > ![Angiv programtype.](images/mdatp-9-app-type.png)

1. Bevar standardværdierne, og klik **på Næste**.

    > [!div class="mx-imgBorder"]
    > ![Programegenskaber.](images/mdatp-10-properties.png)

1. Tilføj opgaver, og klik på **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Skærmbillede med oplysninger om Intune-opgaver.](images/mdatp-11-assignments.png)

1. Gennemse og **opret**.
1. Du kan besøge **Apps** \> **efter platform** \> **macOS** for at se det på listen over alle programmer.

    > [!div class="mx-imgBorder"]
    > ![Listen Programmer.](images/mdatp-12-applications.png)

Få mere at vide under [Føj Microsoft Defender til Endpoint til macOS-enheder, der bruger Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > Du skal oprette alle de påkrævede konfigurationsprofiler og skubbe dem til alle maskiner, som beskrevet ovenfor.

## <a name="client-device-setup"></a>Konfiguration af klientenhed

Du behøver ikke nogen særlig klargøring til en Mac-enhed ud over Firmaportal [installation](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Bekræft administration af enheder.

    > [!div class="mx-imgBorder"]
    > ![Bekræft skærmbillede af enhedshåndtering.](images/mdatp-3-confirmdevicemgmt.png)

    Vælg **Åbn systemindstillinger**, **find Administrationsprofil** på listen, og vælg **Godkend...**. Din administrationsprofil blev vist som **bekræftet**:

    ![Skærmbillede af administrationsprofil.](images/mdatp-4-managementprofile.png)

2. Vælg **Fortsæt** , og fuldfør tilmeldingen.

   Du kan nu tilmelde flere enheder. Du kan også tilmelde dem senere, når du er færdig med klargøring af systemkonfiguration og programpakker.

3. I Intune skal du åbne **Administrer** \> **enheder på** \> **alle enheder**. Her kan du se din enhed blandt de viste:

   > [!div class="mx-imgBorder"]
   > ![Skærmbillede af Tilføj enheder.](images/mdatp-5-alldevices.png)

## <a name="verify-client-device-state"></a>Bekræft klientenhedstilstand

1. Når konfigurationsprofiler er installeret på dine enheder, skal du åbne **Systemindstillinger-profiler** \> på din Mac-enhed.

    > [!div class="mx-imgBorder"]
    > ![Skærmbillede af Systemindstillinger.](images/mdatp-13-systempreferences.png)

    ![Skærmbillede af Profil for systemindstillinger.](images/mdatp-14-systempreferencesprofiles.png)

2. Kontrollér, at følgende konfigurationsprofiler er til stede og installeret. **Administrationsprofilen** skal være Intune-systemprofilen. _Wdav-config og_ _wdav-kext_ er systemkonfigurationsprofiler, der blev tilføjet i Intune:

    ![Skærmbillede af profiler.](images/mdatp-15-managementprofileconfig.png)

3. Du bør også kunne se ikonet Microsoft Defender til slutpunkt i øverste højre hjørne:

    > [!div class="mx-imgBorder"]
    > ![Skærmbillede af Microsoft Defender for Slutpunkt på statuslinjen.](images/mdatp-icon-bar.png)

## <a name="troubleshooting"></a>Fejlfinding

Problem: Der blev ikke fundet nogen licens.

Løsning: Følg trinnene ovenfor for at oprette en enhedsprofil ved hjælp WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Problemer med logføring af installation

Du kan finde flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl, under Problemer [med logføring af installation](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Fjernelse af installation

Se [Afinstallering](mac-resources.md#uninstalling) for at få mere at vide om, hvordan du fjerner Microsoft Defender til Endpoint på macOS fra klientenheder.
