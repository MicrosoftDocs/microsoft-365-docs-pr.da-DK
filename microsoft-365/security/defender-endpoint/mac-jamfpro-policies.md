---
title: Konfigurer politikkerne for Microsoft Defender for Endpoint macOS i Syltef Pro
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender for Endpoint macOS-politikker i Syltef Pro
keywords: politikker, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6e3a31343468b79ff1117a60eca6a87825562778
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466742"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Konfigurer politikkerne for Microsoft Defender for Endpoint macOS i Syltef Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Defender til Slutpunkt på Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne side fører dig gennem de trin, du skal bruge til at konfigurere macOS-politikker i Sylf-Pro.

Du skal gøre følgende:

1. [Få Microsoft Defender for Endpoint-onboardingpakken](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Opret en konfigurationsprofil i Jamf-Pro ved hjælp af onboardingpakken](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Konfigurere Microsoft Defender for Endpoint indstillinger](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Konfigurere Microsoft Defender for Endpoint for meddelelser](#step-4-configure-notifications-settings)
5. [Konfigurere Microsoft Automatiske opdateringer (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Giv fuld diskadgang til Microsoft Defender for Endpoint](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Godkend kernel-udvidelse til Microsoft Defender for Endpoint](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Godkend systemudvidelser til Microsoft Defender for Endpoint](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Konfigurere netværksudvidelse](#step-9-configure-network-extension)
10. [Planlæg scanninger med Microsoft Defender for Endpoint på macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Installer Microsoft Defender for Endpoint på macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Trin 1: Hent Microsoft Defender for Endpoint-onboardingpakken

1. I [Microsoft 365 Defender](https://security.microsoft.com) skal du gå **til Indstillinger > slutpunkter > onboarding**.

2. Vælg macOS som operativsystem og mobile Enhedshåndtering/Microsoft Intune som installationsmetode.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Den Indstillinger side i Microsoft Defender Security Center" lightbox="images/onboarding-macos.png":::

3. Vælg **Download onboardingpakke** (WindowsDefenderATPOnboardingPackage.zip).

4. Udtræk `WindowsDefenderATPOnboardingPackage.zip`.

5. Kopiér filen til din foretrukne placering. F.eks. `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Trin 2: Opret en konfigurationsprofil i Syltef Pro ved hjælp af onboardingpakken

1. Find filen fra `WindowsDefenderATPOnboarding.plist` den forrige sektion.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="Den Windows Defender ATP-onboardingfil" lightbox="images/plist-onboarding-file.png":::

2. Log på Syltef Pro, naviger **til** **ComputersConfiguration** >  Profiles, og vælg **Ny**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Den side, hvor du opretter en ny Sylte Pro dashboard" lightbox="images/jamf-pro-configure-profile.png":::

3. Angiv følgende oplysninger:

   **Generelt**:

   - Navn: MDE-onboarding til macOS
   - Beskrivelse: MDE Slutpunktsregistrering og -svar onboarding til macOS
   - Kategori: Ingen
   - Distributionsmetode: Installer automatisk
   - Niveau: Computerniveau

4.  Gå til siden **Program & Brugerdefineret Indstillinger**, og **vælg Upload** >  **Add**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Den konfigurering af app og brugerdefinerede indstillinger" lightbox="images/jamfpro-mac-profile.png":::

5. Vælg **Upload fil (PLIST-fil), og** angiv derefter følgende **i Præferencedomæne**: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="The sylfpro plist upload file" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Overfør filegenskabslistefil" lightbox="images/jamfpro-plist-file.png":::

6. Vælg **Åbn** , og vælg onboardingfilen.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Onboardingfilen" lightbox="images/jamfpro-plist-file-onboard.png":::

7. Vælg **Upload**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Den uploadende plist-fil" lightbox="images/jamfpro-upload-plist.png":::

8. Vælg **fanen** Omfang.

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Fanen Omfang" lightbox="images/jamfpro-scope-tab.png":::

9. Vælg destinationscomputerne.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Destinationscomputerne" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Målene" lightbox="images/jamfpro-targets.png":::

10. Vælg **Gem**.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Installation af destinationscomputere" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Valget af destinationscomputere" lightbox="images/jamfpro-target-selected.png":::

11. Vælg **Udført**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Computerne i en målgruppe" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Listen over konfigurationsprofiler" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Trin 3: Konfigurer Microsoft Defender for Endpoint indstillinger

Du kan enten bruge SYLF Pro GUI til at redigere individuelle indstillinger for Microsoft Defender for Endpoint-konfigurationen eller bruge den ældre metode ved at oprette en konfigurations-Plist i en teksteditor og uploade den til SYLF Pro.

Bemærk, at du skal bruge nøjagtigt `com.microsoft.wdav` som **præferencedomænet**, da Microsoft Defender for Endpoint kun bruger dette navn og til `com.microsoft.wdav.ext` at indlæse dets administrerede indstillinger!

Versionen `com.microsoft.wdav.ext` kan bruges i sjældne tilfælde, når du foretrækker at bruge GUI-metoden, men også har brug for at konfigurere en indstilling, der endnu ikke er blevet føjet til skemaet.

### <a name="gui-method"></a>GUI-metode

1. Download schema.json-fil [fra Defenders lager GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) gemme den i en lokal fil:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Opret en ny konfigurationsprofil under Computere > Konfigurationsprofiler, og angiv følgende oplysninger på **fanen** Generelt:

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="En ny profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Navn: MDATP MDAV-konfigurationsindstillinger
    - Beskrivelse:\<blank\>
    - Kategori: Ingen (standard)
    - Niveau: Computerniveau (standard)
    - Distributionsmetode: Installer automatisk (standard)

3. Rul ned til **fanen & Brugerdefineret Indstillinger**, vælg Eksterne **programmer, klik** på Tilføj, og brug Brugerdefineret skema som  kilde for at bruge det præferencedomæne.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Tilføj brugerdefineret skema" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Angiv `com.microsoft.wdav` som præferencedomæne, klik på **Tilføj skema,** og klik Upload **filen** schema.json, der blev downloadet på trin 1. Klik på **Gem**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="Upload skema" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Du kan se alle understøttede Microsoft Defender for Endpoint konfigurationsindstillinger nedenfor under **Præferencedomæneegenskaber**. Klik **på Tilføj/fjern egenskaber** for at vælge de indstillinger, du vil administrere, og klik på **OK for** at gemme ændringerne. (Indstillinger ikke er markeret, vil det ikke blive medtaget i den administrerede konfiguration, og slutbrugeren vil kunne konfigurere disse indstillinger på sin maskine.

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="De valgte administrerede indstillinger" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Skift værdierne i indstillingerne til de ønskede værdier. Du kan klikke på **Flere oplysninger for** at få dokumentation til en bestemt indstilling. (Du kan klikke på **Forhåndsvisning af Plist** for at undersøge, hvordan konfigurations-plist kommer til at se ud. Klik **på Formulareditor** for at vende tilbage til den visuelle editor).

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Den side, hvor du ændrer indstillingernes værdier" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Vælg **fanen** Omfang.

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Konfigurationens profilområde" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. Vælg **Contosos computergruppe**.

9. Vælg **Tilføj**, og vælg derefter **Gem**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Den side, hvor du kan tilføje konfigurationsindstillingerne" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Den side, hvor du kan gemme konfigurationsindstillingerne" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Den side, hvor du fuldfører konfigurationsindstillingerne" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Microsoft Defender for Endpoint tilføjer nye indstillinger over tid. Disse nye indstillinger føjes til skemaet, og en ny version publiceres i Github.
Det eneste, du skal gøre **for at få** opdateringer, er at downloade et opdateret skema, redigere eksisterende konfigurationsprofil og Redigere skema på fanen **& Brugerdefineret Indstillinger**.

### <a name="legacy-method"></a>Ældre metode

1. Brug følgende Microsoft Defender for Endpoint konfigurationsindstillinger:

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

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Den side, der viser en ny profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-konfigurationsindstillinger
    - Beskrivelse:\<blank\>
    - Kategori: Ingen (standard)
    - Distributionsmetode: Installer automatisk(standard)
    - Niveau: Computerniveau(standard)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="MdATP MDAV-konfigurationsindstillinger" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. I **Program & Brugerdefineret Indstillinger** du vælge **Konfigurer**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Programmet og brugerdefinerede indstillinger" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. Vælg **Upload Fil (PLIST-fil)**.

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Plist-fil med konfigurationsindstillinger" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. I **Preferences Domain** skal du angive `com.microsoft.wdav`, og derefter **Upload PLIST-fil**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Præferencedomænet for konfigurationsindstillinger" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. Vælg **Vælg fil**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Prompten om at vælge plist-filen" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. Vælg **MDATP_MDAV_configuration_settings.plist**, og vælg derefter **Åbn**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Konfigurationsindstillingerne for mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. Vælg **Upload**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Upload af konfigurationsindstillingen" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Prompten om at overføre det billede, der er relateret til konfigurationsindstillingerne" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Hvis du har uploadet Intune fil, får du vist følgende fejlmeddelelse:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Prompten om at overføre intune-filen, der er relateret til konfigurationsindstillingerne" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. Vælg **Gem**.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Muligheden for at gemme det billede, der er relateret til konfigurationsindstillingerne" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Filen uploades.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Den uploadede fil, der er relateret til konfigurationsindstillingerne" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Siden konfigurationsindstillinger" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Vælg **fanen** Omfang.

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Omfanget af konfigurationsindstillingerne" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. Vælg **Contosos computergruppe**.

15. Vælg **Tilføj**, og vælg derefter **Gem**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Konfigurationsindstillingerne tilføjerav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Meddelelse om konfigurationsindstillinger" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

    ![Billede af konfigurationsindstillinger, der konfigurerer profilbillede.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Konfigurationsprofilens indstillinger" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

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

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Den nye macOS-konfigurationsprofilside" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - Tabulatormeddelelser **, klik** på Tilføj, og angiv følgende værdier:
        - **Bundle-id**: `com.microsoft.wdav.tray`
        - **Vigtige beskeder: Klik** på **Deaktiver**
        - **Meddelelser**: Klik på **Aktivér**
        - **Type af bannerbesked**: Vælg **Medtag** **og Midlertidig** *(standard)*
        - **Meddelelser på låseskærmen**: Klik på **Skjul**
        - **Meddelelser i Meddelelsescenter**: Klik på **Vis**
        - **Badge-appikon**: Klik på **Vis**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="Meddelelsesbakken med konfigurationsindstillinger mdatpmdav" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - Fanen **Meddelelser**, klik **på** Tilføj en gang mere, rul ned **til siden Nye Indstillinger**
        - **Bundle-id**: `com.microsoft.autoupdate2`
        - Konfigurer resten af indstillingerne til de samme værdier som ovenfor

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Konfigurationsindstillinger mdatpmdav meddelelser mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Bemærk, at du nu har to "tabeller" med meddelelseskonfigurationer, en til **Bundle-id: com.microsoft.wdav.tray** og en anden til **Bundle-id: com.microsoft.autoupdate2**. Selvom du kan konfigurere beskedindstillinger i henhold til dine krav, skal pakke-sms'er være præcis det samme som beskrevet  før, og Inkluder **skal være til** for **meddelelser**.

3. Vælg fanen **Omfang** , og vælg derefter **Tilføj**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Den side, hvor du kan tilføje værdier for konfigurationsindstillingerne" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. Vælg **Contosos computergruppe**.

5. Vælg **Tilføj**, og vælg derefter **Gem**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Den side, hvor du kan gemme værdier for konfigurationsindstillingerne for contoso-computergruppen" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Den side, der viser meddelelsen om fuldførelse af konfigurationsindstillingerne" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. Vælg **Udført**. Du får vist den nye **Konfiguration-profil**.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="De fuldførte konfigurationsindstillinger" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Trin 5: Konfigurer Microsoft Automatiske opdateringer (MAU)

1. Brug følgende Microsoft Defender for Endpoint konfigurationsindstillinger:

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

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Konfigurationsindstillingerne" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV MAU-indstillinger
    - Beskrivelse: Microsoft Automatiske opdateringer-indstillinger for MDATP til macOS
    - Kategori: Ingen (standard)
    - Distributionsmetode: Installer automatisk(standard)
    - Niveau: Computerniveau(standard)

5. I **Program & Brugerdefineret Indstillinger** du vælge **Konfigurer**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Konfigurationsindstillingsprogrammet og brugerdefinerede indstillinger" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. Vælg **Upload Fil (PLIST-fil)**.

7. I **Preference Domain skal** du angive: `com.microsoft.autoupdate2`og derefter **Upload PLIST-fil**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Præferencedomæne for konfigurationsindstilling" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. Vælg **Vælg fil**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Prompten om at vælge filen vedrørende konfigurationsindstillingen" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. Vælg **MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Indstillingerne for mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. Vælg **Upload**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Upload af filen vedrørende konfigurationsindstillingen" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Den side, der viser uploadindstillingen for filen vedrørende konfigurationsindstillingen" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. Vælg **Gem**.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Den side, der viser lagringsindstillingen for filen vedrørende konfigurationsindstillingen" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Vælg **fanen** Omfang.

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Fanen Omfang for konfigurationsindstillingerne" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. Vælg **Tilføj**.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Muligheden for at tilføje installationsmål" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Den side, hvor du føjer flere værdier til konfigurationsindstillingerne" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Den side, hvor du kan føje flere værdier til konfigurationsindstillingerne" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. Vælg **Udført**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Meddelelse om fuldførelse af konfigurationsindstillingerne" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Trin 6: Giv fuld diskadgang til Microsoft Defender for Endpoint

1. I Syltef-Pro dashboard skal du vælge **Konfigurationsprofiler**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Den profil, som indstillingerne skal konfigureres for" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. Vælg **+ Ny**.

3. Angiv følgende oplysninger:

    **Generel**
    - Navn: MDATP MDAV – giv fuld diskadgang til Slutpunktsregistrering og -svar og AV
    - Beskrivelse: På macOS Catalina eller nyere har den nye politikkontrolelement Indstillinger for beskyttelse af personlige oplysninger
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Konfigurationsindstillingen generelt" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. I Konfigurer **Politikkontrol for indstillinger for beskyttelse af personlige oplysninger** skal du **vælge Konfigurer**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Politikkontrolelementet for konfigurationen af beskyttelse af personlige oplysninger" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. Angiv **følgende oplysninger i Politikkontrolelement** for indstillinger for beskyttelse af personlige oplysninger:

    - Identifikator: `com.microsoft.wdav`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Detaljer om politikkontrol for konfigurationsindstillingen for beskyttelse af personlige oplysninger" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. Vælg **+ Tilføj**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Konfigurationsindstillingen tilføjer systempolitik for alle filer" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - Under App eller tjeneste: Angiv til **SystemPolicyAllFiles**

    - Under "adgang": Angiv til **Tillad**

7. Vælg **Gem** (ikke den nederste højre).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Lagringshandlingen for konfigurationsindstillingen" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. Klik på `+` tegnet ud for **Appadgang for** at tilføje en ny post.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Lagringshandlingen, der vedrører konfigurationsindstillingen" lightbox="images/tcc-add-entry.png":::

9. Angiv følgende oplysninger:

    - Identifikator: `com.microsoft.wdav.epsext`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Vælg **+ Tilføj**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Konfigurationsindstillingen tcc epsext" lightbox="images/tcc-epsext-entry.png":::

    - Under App eller tjeneste: Angiv til **SystemPolicyAllFiles**

    - Under "adgang": Angiv til **Tillad**

11. Vælg **Gem** (ikke den nederste højre).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="Den anden forekomst af konfigurationsindstilling tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. Vælg **fanen** Omfang.

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Den side, der viser omfanget af konfigurationsindstillingen" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. Vælg **+ Tilføj**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Den side, der viser konfigurationsindstillingen" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. Vælg **Computergrupper** > under **Gruppenavn** > **du vælge Contosos Computergruppe**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Konfigurationsindstillingen contoso-computergruppe" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. Vælg **Tilføj**.

16. Vælg **Gem**.

17. Vælg **Udført**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Konfigurationsindstillingen contoso machine-group" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Illustrationen med konfigurationsindstillinger" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Alternativt kan du downloade [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Installation af brugerdefinerede konfigurationsprofiler ved hjælp af [Sylf-Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Trin 7: Godkend kernel-udvidelse til Microsoft Defender for Endpoint

> [!CAUTION]
> Apple Silicon-enheder (M1) understøtter ikke KEXT. Installation af en konfigurationsprofil bestående af KEXT-politikker mislykkes på disse enheder.

1. I **Konfigurationsprofiler skal** du vælge **+ Ny**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Beskrivelse af det sociale medie, der genereres automatisk" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-kerneudvidelse
    - Beskrivelse: MDATP-kerneudvidelse (kext)
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Konfigurationsindstillingerne mdatpmdav-kerne" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. I **Konfigurer godkendte kerneludvidelser skal** du vælge **Konfigurer**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Den side, der viser de godkendte konfigurationsindstillinger for kerneudvidelser" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. I **Godkendte kerneludvidelser** Angiv følgende oplysninger:

    - Visningsnavn: Microsoft Corp.
    - Team-id: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Ruden Godkendte kerneudvidelser" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Vælg **fanen** Omfang.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Fanen Omfang for konfigurationen" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Vælg **+ Tilføj**.

7. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

8. Vælg **+ Tilføj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Den side, hvor du definerer yderligere værdier for konfigurationsindstillingerne" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Vælg **Gem**.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="MDATP MDAV-kerneludvidelsen" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. Vælg **Udført**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Detaljesiden konfigurationsprofiler" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Du kan også downloade [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Implementere brugerdefinerede konfigurationsprofiler ved hjælp af [Syltef Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Trin 8: Godkend systemudvidelser til Microsoft Defender for Endpoint

1. I **Konfigurationsprofiler skal** du vælge **+ Ny**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Beskrivelsen af det automatisk oprettede sociale medieindlæg" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Angiv følgende oplysninger:

    **Generel**

    - Navn: MDATP MDAV-systemudvidelser
    - Beskrivelse: MDATP-systemudvidelser
    - Kategori: Ingen
    - Distributionsmetode: Installer automatisk
    - Niveau: Computerniveau

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Konfigurationsindstillingerne skal være en ny profil" lightbox="images/sysext-new-profile.png":::

3. Vælg **Konfigurer i Systemudvidelser**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Ruden med indstillingen Konfigurer for systemudvidelserne" lightbox="images/sysext-configure.png":::

4. I **Systemudvidelser** skal du angive følgende oplysninger:

   - Visningsnavn: Microsoft Corp. Systemudvidelser
   - Systemudvidelsestyper: Tilladte systemudvidelser
   - Team-id: UBF8T346G9
   - Tilladte systemudvidelser:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="Ruden med MDATP MDAV-systemudvidelser" lightbox="images/sysext-configure2.png":::

5. Vælg **fanen** Omfang.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Valgruden Destinationscomputere" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Vælg **+ Tilføj**.

7. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

8. Vælg **+ Tilføj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Ruden Ny macOS-konfigurationsprofil" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Vælg **Gem**.

   :::image type="content" source="images/sysext-scope.png" alt-text="Visning af indstillinger vedrørende MDATP MDAV-systemudvidelser" lightbox="images/sysext-scope.png":::

10. Vælg **Udført**.

    :::image type="content" source="images/sysext-final.png" alt-text="Konfigurationsindstillingerne sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>Trin 9: Konfigurer netværksudvidelse

Som en del af egenskaberne slutpunktsregistrering og svar undersøger Microsoft Defender for Endpoint på macOS sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender portal. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

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

        :::image type="content" source="images/netext-create-profile.png" alt-text="Konfigurationsindstillingen mdatpmdav" lightbox="images/netext-create-profile.png":::

3. Vælg **fanen** Omfang.

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Fanen til konfigurationsindstillinger" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. Vælg **+ Tilføj**.

5. Vælg **Computergrupper** > under **gruppenavn** > **du vælge Contosos computergruppe**.

6. Vælg **+ Tilføj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Konfigurationsindstillinger adim" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. Vælg **Gem**.

   :::image type="content" source="images/netext-scope.png" alt-text="Ruden Indholdsfilter" lightbox="images/netext-scope.png":::

8. Vælg **Udført**.

   :::image type="content" source="images/netext-final.png" alt-text="Konfigurationsindstillingerne netext - final" lightbox="images/netext-final.png":::

Alternativt kan du downloade [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) og uploade den til SYLF-konfigurationsprofiler som beskrevet i Installation af brugerdefinerede konfigurationsprofiler ved hjælp af [Sylf-Pro| Metode 2: Upload konfigurationsprofil til Syltef Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Trin 10: Planlæg scanninger med Microsoft Defender for Endpoint på macOS

Følg vejledningen på [Planlæg scanninger med Microsoft Defender for Endpoint på macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Trin 11: Installer Microsoft Defender for Endpoint på macOS

1. Gå til det sted, hvor du gemte `wdav.pkg`.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Stifinder wdav-pakken" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. Omdøb den til `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Stifinder1 wdavmdm-pakken" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Åbn Syltef-Pro dashboard.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Konfigurationsindstillingerne forpropperfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Vælg din computer, og klik på tandhjulsikonet øverst, og vælg **derefter Computeradministration**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Konfigurationsindstillingerne – computeradministration" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. I **Pakker skal** du vælge **+ Ny**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Beskrivelse af fugle for en automatisk oprettet pakke" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. Angiv **følgende oplysninger** i Ny pakke:

    **Fanen Generelt**
    - Visningsnavn: Lad det være tomt lige nu. Fordi den nulstilles, når du vælger din pkg.
    - Kategori: Ingen (standard)
    - Filnavn: Vælg fil

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Fanen Generelt for konfigurationsindstillinger" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Åbn filen, og peg på den eller `wdav.pkg` `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Computerskærmen viser beskrivelsen af en automatisk genereret pakke" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. Vælg **Åbn**. Angiv Det **viste navn til** **Microsoft Defender Advanced Threat Protection, og Microsoft Defender Antivirus**.

    **Manifestfil** er ikke påkrævet. Microsoft Defender for Endpoint fungerer uden manifestfil.

    **Fanen Indstillinger**: Bevar standardværdier.

    **Fanen Begrænsninger**: Bevar standardværdier.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Fanen begrænsning for konfigurationsindstillingerne" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. Vælg **Gem**. Pakken uploades til Sylf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Uploadprocessen for konfigurationsindstillinger for pakken, der er relateret til konfigurationsindstillingerne" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Det kan tage et par minutter, før pakken er tilgængelig til installation.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="En forekomst af overførsel af pakken til konfigurationsindstillinger" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. Gå til **siden** Politikker.

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Politikker for konfigurationsindstillinger" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Vælg **+ Ny** for at oprette en ny politik.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Den nye politik for konfigurationsindstillinger" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. Angiv **følgende** oplysninger generelt:

    - Visningsnavn: MDATP Onboarding Contoso 200329 v100.86.92 eller nyere

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Konfigurationsindstillinger – MDATP-onboard" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. Vælg **Tilbagevendende indtjekning**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Den tilbagevendende indtjekning af konfigurationsindstillingerne" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. Vælg **Gem**.

14. Vælg **Pakker> Konfigurer**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Muligheden for at konfigurere pakker" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Vælg knappen **Tilføj** ud for **Microsoft Defender Advanced Threat Protection, og Microsoft Defender Antivirus**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="Muligheden for at tilføje flere indstillinger til MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. Vælg **Gem**.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Lagringsindstillingen for konfigurationsindstillingerne" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Vælg **fanen** Omfang.

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Fanen Omfang, der er relateret til konfigurationsindstillingerne" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Vælg destinationscomputerne.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Muligheden for at tilføje computergrupper" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Omfang**

    Vælg **Tilføj**.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Konfigurationsindstillingerne - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Konfigurationsindstillingerne - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Selvbetjening**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Fanen Selvbetjening for konfigurationsindstillinger" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. Vælg **Udført**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="Contoso-onboardingstatus med mulighed for at fuldføre den" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="Siden Politikker" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
