---
title: Konfigurer Microsoft Defender til Slutpunkt på macOS-politikker i Jamf Pro
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender til Slutpunkt på macOS-politikker i Jamf Pro
keywords: politikker, microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 23420223102eafeab7783f7b81ac60c06670626c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592012"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Konfigurer Microsoft Defender til Slutpunkt på macOS-politikker i Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Defender til Slutpunkt på Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne side fører dig gennem de trin, du skal bruge til at konfigurere macOS-politikker i Sylf-Pro.

Du skal gøre følgende:

1. [Hent onboardingpakken til Microsoft Defender til Slutpunkt](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Opret en konfigurationsprofil i Jamf-Pro ved hjælp af onboardingpakken](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Konfigurer Microsoft Defender til slutpunktsindstillinger](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Konfigurer meddelelsesindstillinger for Microsoft Defender til Slutpunkt](#step-4-configure-notifications-settings)
5. [Konfigurere Microsoft Automatiske opdateringer (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Giv fuld diskadgang til Microsoft Defender til Slutpunkt](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Godkend kernel-udvidelse til Microsoft Defender til slutpunkt](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Godkend systemudvidelser til Microsoft Defender til Slutpunkt](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Konfigurere netværksudvidelse](#step-9-configure-network-extension)
10. [Planlæg scanninger med Microsoft Defender til Slutpunkt på macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Installer Microsoft Defender til Slutpunkt på macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Trin 1: Hent onboardingpakken til Microsoft Defender til Slutpunkt

1. I [Microsoft 365 Defender](https://security.microsoft.com) skal du gå **til Indstillinger > slutpunkter > onboarding**.

2. Vælg macOS som operativsystem og administration af mobilenheder/Microsoft Intune som installationsmetode.

    ![Billede af Microsoft 365 Defender portal.](images/onboarding-macos.png)

3. Vælg **Download onboardingpakke** (WindowsDefenderATPOnboardingPackage.zip).

4. Udtræk `WindowsDefenderATPOnboardingPackage.zip`.

5. Kopiér filen til din foretrukne placering. F.eks. `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Trin 2: Opret en konfigurationsprofil i Syltef Pro ved hjælp af onboardingpakken

1. Find filen fra `WindowsDefenderATPOnboarding.plist` den forrige sektion.

   ![Billede af WindowsDefenderATPOnboarding-fil.](images/plist-onboarding-file.png)

2. Log på Syltef Pro, naviger **til** **ComputersConfiguration** >  Profiles, og vælg **Ny**.

    ![Billede af oprettelse af en ny Sylte Pro dashboard.](images/jamf-pro-configure-profile.png)

3. Angiv følgende oplysninger:

   **Generelt**:

   - Navn: MDE-onboarding til macOS
   - Beskrivelse: MDE Slutpunktsregistrering og -svar onboarding til macOS
   - Kategori: Ingen
   - Distributionsmetode: Installer automatisk
   - Niveau: Computerniveau

4.  Gå til siden **Program & Brugerdefineret Indstillinger**, og **vælg Upload** >  **Add**.

    ![Billede af konfiguration af app og brugerdefinerede indstillinger.](images/jamfpro-mac-profile.png)

5. Vælg **Upload fil (PLIST-fil), og** angiv derefter følgende **i Præferencedomæne**: `com.microsoft.wdav.atp`.

    ![Billede af papirspentpro plist-uploadfil.](images/jamfpro-plist-upload.png)

    ![Billede af listefil for overførsel af filegenskab.](images/jamfpro-plist-file.png)

6. Vælg **Åbn** , og vælg onboardingfilen.

    ![Billede af onboardingfil.](images/jamfpro-plist-file-onboard.png)

7. Vælg **Upload**.

    ![Billede af overførsel af plist-fil.](images/jamfpro-upload-plist.png)

8. Vælg **fanen** Omfang.

    ![Billede af fanen Omfang.](images/jamfpro-scope-tab.png)

9. Vælg destinationscomputerne.

    ![Billede af destinationscomputere.](images/jamfpro-target-computer.png)

    ![Billede af mål.](images/jamfpro-targets.png)

10. Vælg **Gem**.

    ![Billede af destinationscomputere for installation.](images/jamfpro-deployment-target.png)

    ![Billede af valgte destinationscomputere.](images/jamfpro-target-selected.png)

11. Vælg **Udført**.

    ![Billede af destinationscomputere.](images/jamfpro-target-group.png)

    ![Liste over konfigurationsprofiler.](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Trin 3: Konfigurer Indstillinger for Microsoft Defender til slutpunkt

Du kan enten bruge SYLEF Pro GUI til at redigere individuelle indstillinger for Microsoft Defender til slutpunktskonfigurationen eller bruge den ældre metode ved at oprette en konfigurations-Plist i en teksteditor og uploade den til SYLF-Pro.

Bemærk, at du skal bruge nøjagtigt `com.microsoft.wdav` som **preferencedomænet**, så bruger Microsoft Defender kun dette navn og indlæser `com.microsoft.wdav.ext` dets administrerede indstillinger!

Versionen `com.microsoft.wdav.ext` kan bruges i sjældne tilfælde, når du foretrækker at bruge GUI-metoden, men også har brug for at konfigurere en indstilling, der endnu ikke er blevet føjet til skemaet.

### <a name="gui-method"></a>GUI-metode

1. Download schema.json-fil [fra Defenders lager GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) gemme den i en lokal fil:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Opret en ny konfigurationsprofil under Computere > Konfigurationsprofiler, og angiv følgende oplysninger på **fanen** Generelt:

    ![Ny profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

    - Navn: MDATP MDAV-konfigurationsindstillinger
    - Beskrivelse:\<blank\>
    - Kategori: Ingen (standard)
    - Niveau: Computerniveau (standard)
    - Distributionsmetode: Installer automatisk (standard)

3. Rul ned til **fanen & Brugerdefineret Indstillinger**, vælg Eksterne **programmer, klik** på Tilføj, og brug Brugerdefineret skema som  kilde for at bruge det præferencedomæne.

    ![Tilføj brugerdefineret skema.](images/4137189bc3204bb09eed3aabc41afd78.png)

4. Angiv `com.microsoft.wdav` som præferencedomæne, klik på **Tilføj skema,** og klik Upload **filen** schema.json, der blev downloadet på trin 1. Klik på **Gem**.

    ![Upload skema.](images/a6f9f556037c42fabcfdcb1b697244cf.png)

5. Du kan se alle understøttede konfigurationsindstillinger for Microsoft Defender til Slutpunkt nedenfor under **Præferencedomæneegenskaber**. Klik **på Tilføj/fjern egenskaber** for at vælge de indstillinger, du vil administrere, og klik på **OK for** at gemme ændringerne. (Indstillinger ikke er markeret, vil det ikke blive medtaget i den administrerede konfiguration, og slutbrugeren vil kunne konfigurere disse indstillinger på sin maskine.

    ![Vælg administrerede indstillinger.](images/817b3b760d11467abe9bdd519513f54f.png)

6. Skift værdierne i indstillingerne til de ønskede værdier. Du kan klikke på **Flere oplysninger for** at få dokumentation til en bestemt indstilling. (Du kan klikke på **Forhåndsvisning af Plist** for at undersøge, hvordan konfigurations-plist kommer til at se ud. Klik **på Formulareditor** for at vende tilbage til den visuelle editor).

    ![Rediger indstillingers værdier.](images/a14a79efd5c041bb8974cb5b12b3a9b6.png)

7. Vælg **fanen** Omfang.

    ![Konfigurationsprofilens omfang.](images/9fc17529e5577eefd773c658ec576a7d.png)

8. Vælg **Contosos computergruppe**.

9. Vælg **Tilføj**, og vælg derefter **Gem**.

    ![Konfigurationsindstillinger – tilføj.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Konfigurationsindstillinger – gem.](images/6f093e42856753a3955cab7ee14f12d9.png)

10. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

    ![Konfigurationsindstillinger – udført.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

Microsoft Defender til Slutpunkt tilføjer nye indstillinger over tid. Disse nye indstillinger føjes til skemaet, og en ny version publiceres i Github.
Det eneste, du skal gøre **for at få** opdateringer, er at downloade et opdateret skema, redigere eksisterende konfigurationsprofil og Redigere skema på fanen **& Brugerdefineret Indstillinger**.

### <a name="legacy-method"></a>Ældre metode

1. Brug følgende konfigurationsindstillinger for Microsoft Defender til slutpunkt:

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Ikke slået til som standard, hvis du planlægger at køre en tredjeparts AV til macOS, skal du indstille den til `true`.

    - udeladelse
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - udeladelseMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR er på prøve, og hvis du gennemgår en koncepttest, skal du fjerne den, især hvis du tester EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - mærker
    - hideStatusMenuIcon

     Du kan få mere at vide [under Egenskabsliste for fuld konfigurationsprofil for SYLF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. Gem filen som `MDATP_MDAV_configuration_settings.plist`.

3. I Syltef-Pro dashboard skal du **åbne Computere** og deres **konfigurationsprofiler**. Klik **på** Ny, og skift **til fanen** Generelt.

    ![Ny profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-konfigurationsindstillinger
    - Beskrivelse:\<blank\>
    - Kategori: Ingen (standard)
    - Distributionsmetode: Installer automatisk(standard)
    - Niveau: Computerniveau(standard)

    ![Billede af MDATP MDAV-konfigurationsindstillinger.](images/3160906404bc5a2edf84d1d015894e3b.png)

5. I **Program & Brugerdefineret Indstillinger** du vælge **Konfigurer**.

    ![Billede af app og brugerdefinerede indstillinger.](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. Vælg **Upload Fil (PLIST-fil)**.

    ![Billede af plist-fil med konfigurationsindstillinger.](images/6f85269276b2278eca4bce84f935f87b.png)

7. I **Preferences Domain** skal du angive `com.microsoft.wdav`, og derefter **Upload PLIST-fil**.

    ![Billede af indstillingsindstillingsdomænet for konfiguration.](images/db15f147dd959e872a044184711d7d46.png)

8. Vælg **Vælg fil**.

    ![Billede af konfigurationsindstillinger vælg fil.](images/526e978761fc571cca06907da7b01fd6.png)

9. Vælg **MDATP_MDAV_configuration_settings.plist**, og vælg derefter **Åbn**.

    ![Billede af mdatpmdav-konfigurationsindstillinger.](images/98acea3750113b8dbab334296e833003.png)

10. Vælg **Upload**.

    ![Billede af overførsel af konfigurationsindstilling.](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![Billede af overførselsbillede af konfigurationsindstillinger.](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    > [!NOTE]
    > Hvis du overfører Intune-filen, får du vist følgende fejlmeddelelse:
    >
    >![Billede af intune-filoverførsel af konfigurationsindstillinger.](images/8e69f867664668796a3b2904896f0436.png)

11. Vælg **Gem**.

    ![Billede af konfigurationsindstillinger Gem billede.](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. Filen uploades.

    ![Billede af billede af filen med konfigurationsindstillinger, der er overført.](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![Billede af filen med konfigurationsindstillinger, der er overført.](images/a422e57fe8d45689227e784443e51bd1.png)

13. Vælg **fanen** Omfang.

    ![Billede af omfanget af konfigurationsindstillinger.](images/9fc17529e5577eefd773c658ec576a7d.png)

14. Vælg **Contosos computergruppe**.

15. Vælg **Tilføj**, og vælg derefter **Gem**.

    ![Billede af konfigurationsindstillinger addav.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Billede af konfigurationsindstillinger gem Tilføj.](images/6f093e42856753a3955cab7ee14f12d9.png)

16. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

    ![Billede af konfigurationsindstillinger, der konfigurerer profilbillede.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

## <a name="step-4-configure-notifications-settings"></a>Trin 4: Konfigurer indstillinger for meddelelser

Disse trin er gældende for macOS 10.15 (Catalina) eller nyere.

1. I Syltef-Pro dashboard skal du **vælge Computere** og derefter **Konfigurationsprofiler**.

2. Klik **på** Ny, og angiv følgende oplysninger for **Indstillinger**:

    - Fane **Generelt**:
        - **Navn**: MDATP MDAV-meddelelsesindstillinger
        - **Beskrivelse**: macOS 10.15 (Catalina) eller nyere
        - **Kategori**: Ingen *(standard)*
        - **Distributionsmetode**: Installer automatisk *(standard)*
        - **Niveau**: Computerniveau *(standard)*

        ![Billede af ny macOS-konfigurationsprofilskærm.](images/c9820a5ff84aaf21635c04a23a97ca93.png)

    - Tabulatormeddelelser **, klik** på Tilføj, og angiv følgende værdier:
        - **Bundle-id**: `com.microsoft.wdav.tray`
        - **Vigtige beskeder: Klik** på **Deaktiver**
        - **Meddelelser**: Klik på **Aktivér**
        - **Type af bannerbesked**: Vælg **Medtag** **og Midlertidig** *(standard)*
        - **Meddelelser på låseskærmen**: Klik på **Skjul**
        - **Meddelelser i Meddelelsescenter**: Klik på **Vis**
        - **Badge-appikon**: Klik på **Vis**

        ![Billede af konfigurationsindstillinger mdatpmdav-meddelelsesbakken.](images/7f9138053dbcbf928e5182ee7b295ebe.png)

    - Fanen **Meddelelser**, klik **på** Tilføj en gang mere, rul ned **til siden Nye Indstillinger**
        - **Bundle-id**: `com.microsoft.autoupdate2`
        - Konfigurer resten af indstillingerne til de samme værdier som ovenfor

        ![Billede af konfigurationsindstillinger mdatpmdav notifications mau.](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)

        Bemærk, at du nu har to "tabeller" med meddelelseskonfigurationer, en til **Bundle-id: com.microsoft.wdav.tray** og en anden til **Bundle-id: com.microsoft.autoupdate2**. Selvom du kan konfigurere beskedindstillinger i henhold til dine krav, skal pakke-sms'er være præcis det samme som beskrevet  før, og Inkluder **skal være til** for **meddelelser**.

3. Vælg fanen **Omfang** , og vælg derefter **Tilføj**.

    ![Billede af tilføjelsesprogrammet for konfigurationsindstillinger.](images/441aa2ecd36abadcdd8aed03556080b5.png)

4. Vælg **Contosos computergruppe**.

5. Vælg **Tilføj**, og vælg derefter **Gem**.

    ![Billede af konfigurationsindstillinger, som contoso machine grp gemmer.](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    ![Billede af konfigurationsindstillinger, der tilføjes Gem.](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

6. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

    ![Billede af konfigurationsindstillingen udført img.](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Trin 5: Konfigurer Microsoft Automatiske opdateringer (MAU)

1. Brug følgende konfigurationsindstillinger for Microsoft Defender til slutpunkt:

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
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

2. Gem den som `MDATP_MDAV_MAU_settings.plist`.

3. I Syltef-Pro skal du vælge **Generelt**.

    ![Billede af konfigurationsindstilling af det generelle billede.](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV MAU-indstillinger
    - Beskrivelse: Microsoft Automatiske opdateringer-indstillinger for MDATP til macOS
    - Kategori: Ingen (standard)
    - Distributionsmetode: Installer automatisk(standard)
    - Niveau: Computerniveau(standard)

5. I **Program & Brugerdefineret Indstillinger** du vælge **Konfigurer**.

    ![Billede af konfigurationsindstillingsapp og brugerdefinerede indstillinger.](images/1f72e9c15eaafcabf1504397e99be311.png)

6. Vælg **Upload Fil (PLIST-fil)**.

    ![Billede af konfigurationsindstillings-plist.](images/1213872db5833aa8be535da57653219f.png)

7. I **Preference Domain skal** du angive: `com.microsoft.autoupdate2`og derefter **Upload PLIST-fil**.

    ![Billede af konfigurationsindstilling for domæne.](images/1213872db5833aa8be535da57653219f.png)

8. Vælg **Vælg fil**.

    ![Billede af konfigurationsindstillingen choosefile.](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. Vælg **MDATP_MDAV_MAU_settings.plist**.

    ![Billede af konfigurationsindstilling mdatpmdavmau-indstillinger.](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. Vælg **Upload**.
    ![Billede af konfigurationskonfiguration, der afbildes.](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![Billede af konfiguration, der konfigurererlimre.](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. Vælg **Gem**.

    ![Billede af saveimg-konfigurationsindstilling.](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. Vælg **fanen** Omfang.

     ![Billede af konfigurationsindstillingens omfangstabulering.](images/10ab98358b2d602f3f67618735fa82fb.png)

13. Vælg **Tilføj**.

    ![Billede af konfigurationsindstillingen addimg1.](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![Billede af konfigurationsindstillingen addimg2.](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![Billede af konfigurationsindstillingen addimg3.](images/321ba245f14743c1d5d51c15e99deecc.png)

14. Vælg **Udført**.

    ![Billede af konfigurationsindstillingen doneimage.](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Trin 6: Giv fuld diskadgang til Microsoft Defender til slutpunkt

1. I Syltef-Pro dashboard skal du vælge **Konfigurationsprofiler**.

    ![Billede af konfigurationsindstillingskonfigurationsprofil.](images/264493cd01e62c7085659d6fdc26dc91.png)

2. Vælg **+ Ny**.

3. Angiv følgende oplysninger:

    **Generel**
    - Navn: MDATP MDAV – giv fuld diskadgang til Slutpunktsregistrering og -svar og AV
    - Beskrivelse: På macOS Catalina eller nyere har den nye politikkontrolelement Indstillinger for beskyttelse af personlige oplysninger
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    ![Billede af konfigurationsindstilling generelt.](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. I Konfigurer **Politikkontrol for indstillinger for beskyttelse af personlige oplysninger** skal du **vælge Konfigurer**.

    ![Billede af politikkontrolelement for konfiguration.](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. Angiv **følgende oplysninger i Politikkontrolelement** for indstillinger for beskyttelse af personlige oplysninger:

    - Identifikator: `com.microsoft.wdav`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    ![Billede af detaljer om indstilling af indstilling for politik for beskyttelse af personlige oplysninger.](images/22cb439de958101c0a12f3038f905b27.png)

6. Vælg **+ Tilføj**.

    ![Billede af konfigurationsindstilling tilføj systempolitik for alle filer.](images/bd93e78b74c2660a0541af4690dd9485.png)

    - Under App eller tjeneste: Angiv til **SystemPolicyAllFiles**

    - Under "adgang": Angiv til **Tillad**

7. Vælg **Gem** (ikke den nederste højre).

    ![Billede af konfigurationsindstillingen gemmer billeder.](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. Klik på `+` tegnet ud for **Appadgang for** at tilføje en ny post.

    ![Billede af konfigurationsindstilling af appadgang.](images/tcc-add-entry.png)

9. Angiv følgende oplysninger:

    - Identifikator: `com.microsoft.wdav.epsext`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Vælg **+ Tilføj**.

    ![Billede af konfigurationsindstillingen tcc epsext.](images/tcc-epsext-entry.png)

    - Under App eller tjeneste: Angiv til **SystemPolicyAllFiles**

    - Under "adgang": Angiv til **Tillad**

11. Vælg **Gem** (ikke den nederste højre).

    ![Billede af konfigurationsindstillingen tcc epsext image2.](images/tcc-epsext-entry2.png)

12. Vælg **fanen** Omfang.

    ![Billede af konfigurationsindstillingens omfang.](images/2c49b16cd112729b3719724f581e6882.png)

13. Vælg **+ Tilføj**.

    ![Billede af tilføjelsesprogrammet Konfigurationsindstillinger.](images/57cef926d1b9260fb74a5f460cee887a.png)

14. Vælg **Computergrupper** > under **Gruppenavn** > **du vælge Contosos Computergruppe**.

    ![Billede af konfigurationsindstillingen contoso machinegrp.](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. Vælg **Tilføj**.

16. Vælg **Gem**.

17. Vælg **Udført**.

    ![Billede af konfigurationsindstillings donimg.](images/809cef630281b64b8f07f20913b0039b.png)

    ![Billede af konfigurationsindstillingen donimg2.](images/6c8b406ee224335a8c65d06953dc756e.png)

Alternativt kan du downloade [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Installation af brugerdefinerede konfigurationsprofiler ved hjælp af [Sylf-Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Trin 7: Godkend kernel-udvidelse til Microsoft Defender til slutpunkt

> [!CAUTION]
> Apple Silicon-enheder (M1) understøtter ikke KEXT. Installation af en konfigurationsprofil bestående af KEXT-politikker mislykkes på disse enheder.

1. I **Konfigurationsprofiler skal** du vælge **+ Ny**.

    ![Et skærmbillede af et indlæg til et socialt medie, der genereres automatisk.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-kerneudvidelse
    - Beskrivelse: MDATP-kerneudvidelse (kext)
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    ![Billede af konfigurationsindstillinger mdatpmdav-kerne.](images/24e290f5fc309932cf41f3a280d22c14.png)

3. I **Konfigurer godkendte kerneludvidelser skal** du vælge **Konfigurer**.

    ![Billede af godkendt kerne ext i konfigurationsindstillinger.](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

4. I **Godkendte kerneludvidelser** Angiv følgende oplysninger:

    - Visningsnavn: Microsoft Corp.
    - Team-id: UBF8T346G9

    ![Billede af kerneudvidelsen til konfigurationsindstillinger for appr.](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. Vælg **fanen** Omfang.

    ![Billede af fanen Konfigurationsindstillingers omfang img.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Vælg **+ Tilføj**.

7. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

8. Vælg **+ Tilføj**.

    ![Billede af konfigurationsindstillinger tilføjer billeder.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Vælg **Gem**.

    ![Billede af saveimag for konfigurationsindstillinger.](images/0add8019b85a453b47fa5c402c72761b.png)

10. Vælg **Udført**.

    ![Billede af konfigurationsindstillinger doneimag.](images/1c9bd3f68db20b80193dac18f33c22d0.png)

Du kan også downloade [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Implementere brugerdefinerede konfigurationsprofiler ved hjælp af [Syltef Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Trin 8: Godkend systemudvidelser for Microsoft Defender til slutpunkt

1. I **Konfigurationsprofiler skal** du vælge **+ Ny**.

    ![Et skærmbillede af et indlæg til et socialt medie, der genereres automatisk.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-systemudvidelser
    - Beskrivelse: MDATP-systemudvidelser
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    ![Billede af configuration settings sysext new prof.](images/sysext-new-profile.png)

3. Vælg **Konfigurer i Systemudvidelser**.

   ![Billede af konfigurationsindstillinger sysext config.](images/sysext-configure.png)

4. I **Systemudvidelser** skal du angive følgende oplysninger:

   - Visningsnavn: Microsoft Corp. Systemudvidelser
   - Systemudvidelsestyper: Tilladte systemudvidelser
   - Team-id: UBF8T346G9
   - Tilladte systemudvidelser:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![Billede af konfigurationsindstillinger sysextconfig2.](images/sysext-configure2.png)

5. Vælg **fanen** Omfang.

    ![Billede af omfang for konfigurationsindstillinger.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Vælg **+ Tilføj**.

7. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

8. Vælg **+ Tilføj**.

   ![Billede af tilføjelsesprogrammet Konfigurationsindstillinger.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Vælg **Gem**.

   ![Billede af konfigurationsindstillingers sysext scope.](images/sysext-scope.png)

10. Vælg **Udført**.

    ![Billede af konfigurationsindstillinger sysext-final.](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>Trin 9: Konfigurer netværksudvidelse

Som en del af egenskaberne Slutpunktsregistrering og Svar undersøger Microsoft Defender til slutpunkt på macOS sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

Disse trin er gældende for macOS 10.15 (Catalina) eller nyere.

1. I Syltef-Pro dashboard skal du **vælge Computere** og derefter **Konfigurationsprofiler**.

2. Klik **på** Ny, og angiv følgende oplysninger for **Indstillinger**:

    - Fane **Generelt**:
        - **Navn**: Microsoft Defender Network Extension
        - **Beskrivelse**: macOS 10.15 (Catalina) eller nyere
        - **Kategori**: Ingen *(standard)*
        - **Distributionsmetode**: Installer automatisk *(standard)*
        - **Niveau**: Computerniveau *(standard)*

    - **Faneindholdsfilter**:
        - **Filternavn**: Microsoft Defender-indholdsfilter
        - **Identifikator**: `com.microsoft.wdav`
        - Lad **tjenesteadresse**, **organisation**, **brugernavn**, **adgangskode, certifikat** **være tomt** (**Medtag** *er ikke* valgt)
        - **Filterrækkefølge**: Inspektion
        - **Socket Filter**: `com.microsoft.wdav.netext`
        - **Socket Filter Angivet krav**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Lad **netværksfilterfelterne** være tomme (**Medtag** *er ikke* markeret)

        Bemærk, **at de** nøjagtige **værdier for Id** , Socket **Filter og Socket Filter** angivne krav som angivet ovenfor.

        ![Billede af konfigurationsindstilling mdatpmdav.](images/netext-create-profile.png)
        
 > [!NOTE]
 > Syltef understøtter indbyggede indstillinger for indholdsfiltre, som kan indstilles direkte via brugergrænsefladen.

3. Vælg **fanen** Omfang.

   ![Billede af fanen konfigurationsindstillinger.](images/0df36fc308ba569db204ee32db3fb40a.png)

4. Vælg **+ Tilføj**.

5. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

6. Vælg **+ Tilføj**.

    ![Billede af konfigurationsindstillinger adim.](images/0dde8a4c41110dbc398c485433a81359.png)

7. Vælg **Gem**.

    ![Billede af konfigurationsindstillinger savimg netextscop.](images/netext-scope.png)

8. Vælg **Udført**.

    ![Billede af konfigurationsindstillinger netextfinal.](images/netext-final.png)

Alternativt kan du downloade [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Installation af brugerdefinerede konfigurationsprofiler ved hjælp af [Sylf-Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Trin 10: Planlæg scanninger med Microsoft Defender til slutpunkt på macOS

Følg vejledningen på [Planlæg scanninger med Microsoft Defender for Endpoint på macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Trin 11: Installer Microsoft Defender til Endpoint på macOS

1. Gå til det sted, hvor du gemte `wdav.pkg`.

    ![Billede af Stifinder wdav pkg.](images/8dde76b5463047423f8637c86b05c29d.png)

2. Omdøb den til `wdav_MDM_Contoso_200329.pkg`.

    ![Billede af stifinder1 wdavmdmpkg.](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. Åbn Syltef-Pro dashboard.

    ![Billede af configuration settings sylfpro.](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. Vælg din computer, og klik på tandhjulsikonet øverst, og vælg **derefter Computeradministration**.

    ![Billede af konfigurationsindstillinger compmgmt.](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. I **Pakker skal** du vælge **+ Ny**.
    ![Et billede, der indeholder beskrivelsen af fuglen, genereres automatisk som pakke ny.](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. Angiv **følgende oplysninger** i Ny pakke:

    **Fanen Generelt**
    - Visningsnavn: Lad det være tomt lige nu. Fordi den nulstilles, når du vælger din pkg.
    - Kategori: Ingen (standard)
    - Filnavn: Vælg fil

    ![Billede af fanen Konfigurationsindstillinger generelt.](images/21de3658bf58b1b767a17358a3f06341.png)

    Åbn filen, og peg på den eller `wdav.pkg` `wdav_MDM_Contoso_200329.pkg`.

    ![Et skærmbillede af en computerskærm Beskrivelse genereres automatisk.](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. Vælg **Åbn**. Angiv Det **viste navn til** **Microsoft Defender Advanced Threat Protection, og Microsoft Defender Antivirus**.

    **Manifestfil** er ikke påkrævet. Microsoft Defender til slutpunkt fungerer uden manifestfil.

    **Fanen Indstillinger**: Bevar standardværdier.

    **Fanen Begrænsninger**: Bevar standardværdier.

     ![Billede af fanen for begrænsning af konfigurationsindstillinger.](images/56dac54634d13b2d3948ab50e8d3ef21.png)

8. Vælg **Gem**. Pakken uploades til Sylf Pro.

   ![Billede af configuration settings pack upl sylf pro.](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   Det kan tage et par minutter, før pakken er tilgængelig til installation.

   ![Billede af upl for konfigurationsindstillinger.](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. Gå til **siden** Politikker.

    ![Billede af konfigurationsindstillinger.](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. Vælg **+ Ny** for at oprette en ny politik.

    ![Billede af ny politik for konfigurationsindstillinger.](images/847b70e54ed04787e415f5180414b310.png)


11. Angiv **følgende** oplysninger generelt:

    - Visningsnavn: MDATP Onboarding Contoso 200329 v100.86.92 eller nyere

    ![Billede af konfigurationsindstillingermdatponboard.](images/625ba6d19e8597f05e4907298a454d28.png)

12. Vælg **Tilbagevendende indtjekning**.

    ![Billede af konfigurationsindstillinger gentager indtjekning.](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

13. Vælg **Gem**.

14. Vælg **Pakker> Konfigurer**.

    ![Billede af konfigurationsindstillingspakken til konfiguration.](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. Vælg knappen **Tilføj** ud for **Microsoft Defender Advanced Threat Protection, og Microsoft Defender Antivirus**.

    ![Billede af konfigurationsindstillinger MDATP og MDA add.](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. Vælg **Gem**.

    ![Billede af konfigurationsindstillingersavimg.](images/9d6e5386e652e00715ff348af72671c6.png)

17. Vælg **fanen** Omfang.

    ![Billede af configuration settings scptab.](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. Vælg destinationscomputerne.

    ![Billede af konfigurationsindstillinger tgtcomp.](images/6eda18a64a660fa149575454e54e7156.png)

    **Omfang**

    Vælg **Tilføj**.

    ![Billede af konfigurationsindstillinger ad1img.](images/1c08d097829863778d562c10c5f92b67.png)

    ![Billede af konfigurationsindstillinger ad2img.](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **Selvbetjening**

    ![Billede af selvbetjening for konfigurationsindstillinger.](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. Vælg **Udført**.

    ![Billede af konfigurationsindstillinger, do1img.](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![Billede af konfigurationsindstillinger, do2img.](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)
