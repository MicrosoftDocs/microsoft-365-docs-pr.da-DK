---
title: Manuel installation af Microsoft Defender for Endpoint på macOS
description: Installér Microsoft Defender for Endpoint manuelt på macOS fra kommandolinjen.
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4c2bf6cef9e2d2d7413cff9aa4a8ed110ae72edf
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129260"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Manuel installation af Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

I dette emne beskrives det, hvordan du installerer Microsoft Defender for Endpoint på macOS manuelt. En vellykket installation kræver fuldførelse af alle følgende trin:

- [Download installations- og onboardingpakker](#download-installation-and-onboarding-packages)
- [Programinstallation (macOS 10.15)](#application-installation-macos-1015)
- [Programinstallation (macOS 11 og nyere versioner)](#application-installation-macos-11-and-newer-versions)
- [Klientkonfiguration](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, kan du se [de primære Microsoft Defender for Endpoint på macOS-siden](microsoft-defender-endpoint-mac.md) for at få en beskrivelse af forudsætninger og systemkrav til den aktuelle softwareversion.

## <a name="download-installation-and-onboarding-packages"></a>Download installations- og onboardingpakker

Download installations- og onboardingpakkerne fra Microsoft 365 Defender portalen:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal du gå til **Indstillinger > Slutpunkter > Enhedshåndtering > Onboarding**.
2. I afsnit 1 på siden skal du angive operativsystemet til **macOS** og installationsmetoden til **Lokalt script**.
3. I afsnit 2 på siden skal du vælge **Download installationspakke**. Gem den som wdav.pkg i en lokal mappe.
4. I afsnit 2 på siden skal du vælge **Download onboarding-pakke**. Gem den som WindowsDefenderATPOnboardingPackage.zip i den samme mappe.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="Mulighederne for at downloade installations- og onboardingpakker" lightbox="images/portal-onboarding-macos.png":::

5. Kontrollér, at du har de to filer, fra en kommandoprompt.

## <a name="application-installation-macos-1015"></a>Programinstallation (macOS 10.15)

Hvis du vil fuldføre denne proces, skal du have administratorrettigheder på enheden.

1. Naviger til den downloadede wdav.pkg i Finder, og åbn den.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="Installationen af programmet" lightbox="images/mdatp-28-appinstall.png":::

2. Vælg **Fortsæt**, acceptér licensvilkårene, og angiv adgangskoden, når du bliver bedt om det.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="Programinstallationen" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > Du bliver bedt om at tillade, at en driver fra Microsoft installeres (enten "System Extension Blocked" eller "Installation er i venteposition" eller begge dele. Driveren skal have tilladelse til at blive installeret.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="Programmets installation" lightbox="images/mdatp-30-systemextension.png":::

3. Vælg **Åbn sikkerhedsindstillinger** eller **Åbn systemindstillinger > Sikkerhed & Beskyttelse af personlige oplysninger**. Vælg **Tillad**:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="Vinduet Sikkerhed og beskyttelse af personlige oplysninger" lightbox="images/mdatp-31-securityprivacysettings.png":::

   Installationen fortsætter.

   > [!CAUTION]
   > Hvis du ikke vælger **Tillad**, fortsætter installationen efter 5 minutter. Microsoft Defender for Endpoint indlæses, men nogle funktioner, f.eks. beskyttelse i realtid, deaktiveres. Se [Fejlfinding af problemer med kerneudvidelser](mac-support-kext.md) for at få oplysninger om, hvordan du løser dette.

> [!NOTE]
> macOS kan anmode om at genstarte enheden ved den første installation af Microsoft Defender for Endpoint. Beskyttelse i realtid vil ikke være tilgængelig, før enheden genstartes.

## <a name="application-installation-macos-11-and-newer-versions"></a>Programinstallation (macOS 11 og nyere versioner)

Hvis du vil fuldføre denne proces, skal du have administratorrettigheder på enheden.

1. Naviger til den downloadede wdav.pkg i Finder, og åbn den.

   :::image type="content" source="images/monterey-install-1.png" alt-text="Installationsprocessen for programmet" lightbox="images/monterey-install-1.png":::

2. Vælg **Fortsæt**, acceptér licensvilkårene, og angiv adgangskoden, når du bliver bedt om det.

3. Når installationsprocessen er afsluttet, bliver du forfremmet for at godkende de systemudvidelser, der bruges af produktet. Vælg **Åbn sikkerhedsindstillinger**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="Godkendelse af systemudvidelse" lightbox="images/monterey-install-2.png":::

4. Vælg **Tillad** **i vinduet Sikkerhed & Beskyttelse af personlige oplysninger**.

   :::image type="content" source="images/monterey-install-3.png" alt-text="Sikkerhedsindstillingerne for systemudvidelse1" lightbox="images/monterey-install-3.png":::

5. Gentag trin 3 & 4 for alle systemudvidelser, der er distribueret med Microsoft Defender for Endpoint på Mac.

6. Som en del af slutpunktsregistrerings- og svarfunktionerne undersøger Microsoft Defender for Endpoint på Mac sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Når du bliver bedt om at tildele Microsoft Defender for Endpoint tilladelser til at filtrere netværkstrafik, skal du vælge **Tillad**.

   :::image type="content" source="images/monterey-install-4.png" alt-text="Sikkerhedsindstillingerne for systemudvidelse2" lightbox="images/monterey-install-4.png":::

7. Åbn **Systemindstillinger** \> **Sikkerhed & Beskyttelse af personlige oplysninger** , og gå til fanen **Beskyttelse af personlige oplysninger** . Tildel **fuld adgang til disken** til **Microsoft Defender** og **Microsoft Defenders Endpoint Security Extension**.

   :::image type="content" source="images/monterey-install-5.png" alt-text="Fuld diskadgang" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>Klientkonfiguration

1. Kopiér wdav.pkg og MicrosoftDefenderATPOnboardingMacOs.sh til den enhed, hvor du installerer Microsoft Defender for Endpoint på macOS.

    Klientenheden er ikke knyttet til org_id. Bemærk, at attributten *org_id* er tom.

    ```bash
    mdatp health --field org_id
    ```

2. Kør Bash-scriptet for at installere konfigurationsfilen:

    ```bash
    bash MicrosoftDefenderATPOnboardingMacOs.sh
    ```

3. Kontrollér, at enheden nu er knyttet til din organisation, og rapporterer et gyldigt organisations-id:

    ```bash
    mdatp health --field org_id
    ```

    Efter installationen kan du se Microsoft Defender-ikonet på macOS-statuslinjen i øverste højre hjørne.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Ikonet Microsoft Defender på statuslinjen" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>Sådan tillader du fuld diskadgang

> [!CAUTION]
> macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til visse placeringer på disken (f.eks. dokumenter, downloads, desktop osv.) uden eksplicit samtykke. Hvis dette samtykke ikke er til stede, er Microsoft Defender for Endpoint ikke i stand til fuldt ud at beskytte din enhed.

1. Hvis du vil give samtykke, skal du åbne **Systemindstillinger** \> **Sikkerhed & Beskyttelse af personlige oplysninger** \>  \> **Fuld diskadgang**. Klik på låseikonet for at foretage ændringer (nederst i dialogboksen). Vælg Microsoft Defender for Endpoint.

2. Kør en av-registreringstest for at bekræfte, at enheden er onboardet korrekt, og rapportering til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    1. Sørg for, at beskyttelse i realtid er aktiveret (angivet af et resultat på 1 fra kørsel af følgende kommando):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Åbn et terminalvindue. Kopiér og udfør følgende kommando:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Filen skulle være blevet sat i karantæne af Defender for Endpoint på Mac. Brug følgende kommando til at få vist alle registrerede trusler:

        ```bash
        mdatp threat list
        ```

3. Kør en Slutpunktsregistrering og -svar registreringstest for at bekræfte, at enheden er onboardet korrekt, og at den rapporterer til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

   1. I din browser, f.eks. Microsoft Edge til Mac eller Safari.

   1. Download MDATP MacOS-DIY.zip fra https://aka.ms/mdatpmacosdiy og udtræk.

      Du bliver muligvis bedt om følgende:

      > Vil du tillade downloads på "mdatpclientanalyzer.blob.core.windows.net"?<br/>
      > Du kan ændre, hvilke websteder der kan downloade filer under Indstillinger for websteder.

4. Klik på **Tillad**.

5. Åbn **Downloads**.

6. Du bør kunne se **MDATP MacOS DIY**.

   > [!TIP]
   > Hvis du dobbeltklikker, får du vist følgende meddelelse:
   >
   > > **"MDATP MacOS DIY" kan ikke åbnes, fordi udvikleren ikke kan bekræfte.**<br/>
   > > macOS kan ikke bekræfte, at denne app er fri for malware.<br/>
   > > **\[Flyt til Annuller papirkurv\]** **\[\]**

7. Klik på **Annuller**.

8. Højreklik på **MDATP MacOS DIY**, og klik derefter på **Åbn**.

    Systemet skal vise følgende meddelelse:

    > **macOS kan ikke bekræfte udvikleren af MDATP MacOS DIY. Er du sikker på, at du vil åbne den?**<br/>
    > Når du åbner denne app, tilsidesætter du systemsikkerheden, hvilket kan udsætte computeren og personlige oplysninger for malware, der kan skade din Mac eller kompromittere dine personlige oplysninger.

9. Klik på **Åbn**.

    Systemet skal vise følgende meddelelse:

    > Microsoft Defender for Endpoint – macOS Slutpunktsregistrering og -svar diy-testfil<br/>
    > Den tilsvarende besked vil være tilgængelig på MDATP-portalen.

10. Klik på **Åbn**.

    I løbet af et par minutter skal der udløses en besked med navnet "macOS Slutpunktsregistrering og -svar Test Alert".

11. Gå til Microsoft 365 Defender portal (https://security.microsoft.com/).

12. Gå til beskedkøen.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="En macOS-Slutpunktsregistrering og -svar testadvarsel, der viser alvorsgrad, kategori, registreringskilde og en skjult menu med handlinger" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    Se oplysningerne om beskeden og enhedens tidslinje, og udfør de almindelige undersøgelsestrin.

## <a name="logging-installation-issues"></a>Logføring af installationsproblemer

Se [Logføring af installationsproblemer](mac-resources.md#logging-installation-issues) for at få flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl.

## <a name="uninstallation"></a>Uninstallation

Se [Fjernelse](mac-resources.md#uninstalling) for at få oplysninger om, hvordan du fjerner Microsoft Defender for Endpoint på macOS fra klientenheder.
