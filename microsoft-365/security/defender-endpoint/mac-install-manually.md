---
title: Manuel installation af Microsoft Defender til Endpoint på macOS
description: Installer Microsoft Defender til Slutpunkt på macOS manuelt fra kommandolinjen.
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1fce7aa103de9fb90cafa88a286cbf33bc753456
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592640"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Manuel installation af Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

I dette emne beskrives det, hvordan du installerer Microsoft Defender til Endpoint på macOS manuelt. En vellykket installation kræver, at alle følgende trin er gennemført:

- [Download installations- og onboardingpakker](#download-installation-and-onboarding-packages)
- [Programinstallation (macOS 10.15)](#application-installation-macos-1015)
- [Programinstallation (macOS 11 og nyere versioner)](#application-installation-macos-11-and-newer-versions)
- [Klientkonfiguration](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du se microsoft [Defender for Endpoint på macOS-hovedsiden](microsoft-defender-endpoint-mac.md) for en beskrivelse af forudsætningerne og systemkravene for den aktuelle softwareversion.

## <a name="download-installation-and-onboarding-packages"></a>Download installations- og onboardingpakker

Download installations- og onboardingpakkerne fra Microsoft 365 Defender portal:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du gå **til Indstillinger > slutpunkter > administration af > onboarding**.
2. I sektion 1 på siden skal du indstille operativsystemet til **macOS og** installationsmetode til **lokalt script**.
3. I sektion 2 på siden skal du vælge **Download installationspakke**. Gem den som wdav.pkg til en lokal mappe.
4. I sektion 2 på siden skal du vælge **Download onboardingpakke**. Gem den som WindowsDefenderATPOnboardingPackage.zip i den samme mappe.

    ![Microsoft 365 Defender portalskærm.](images/portal-onboarding-macos.png)

5. I en kommandoprompt skal du bekræfte, at du har de to filer.

## <a name="application-installation-macos-1015"></a>Programinstallation (macOS 10.15)

Du skal have administratorrettigheder på enheden for at fuldføre denne proces.

1. Gå til den downloadede wdav.pkg i Finder, og åbn den.

    ![Skærmbillede af installation af app1.](images/mdatp-28-appinstall.png)

2. Vælg **Fortsæt**, enig med licensvilkårene, og angiv adgangskoden, når du bliver bedt om det.

    ![Skærmbillede af installation af app2.](images/mdatp-29-appinstalllogin.png)

   > [!IMPORTANT]
   > Du bliver bedt om at tillade, at en driver fra Microsoft bliver installeret (enten "Systemudvidelse blokeret" eller "Installation er sat i venteposition" eller begge dele. Driveren skal være installeret.

   ![Skærmbillede af installation af app3.](images/mdatp-30-systemextension.png)

3. Vælg **Åbn sikkerhedsindstillinger, eller** **åbn Systemindstillinger, > sikkerhedsoplysninger & beskyttelse af personlige oplysninger**. Vælg **Tillad**:

    ![Skærmbillede af vinduet Sikkerhed og beskyttelse af personlige oplysninger.](images/mdatp-31-securityprivacysettings.png)

   Installationen fortsætter.

   > [!CAUTION]
   > Hvis du ikke vælger **Tillad**, fortsætter installationen efter 5 minutter. Microsoft Defender til slutpunkt indlæses, men nogle funktioner, f.eks beskyttelse i realtid, deaktiveres. Se [Fejlfinding af problemer med kerneudvidelse](mac-support-kext.md) for at få oplysninger om, hvordan du løser dette.

> [!NOTE]
> macOS anmoder muligvis om at genstarte enheden ved den første installation af Microsoft Defender til slutpunkt. Beskyttelse i realtid er ikke tilgængelig, før enheden genstartes.

## <a name="application-installation-macos-11-and-newer-versions"></a>Programinstallation (macOS 11 og nyere versioner)

Du skal have administratorrettigheder på enheden for at fuldføre denne proces.

1. Gå til den downloadede wdav.pkg i Finder, og åbn den.

    ![Skærmbillede af installation af app4.](images/monterey-install-1.png)

2. Vælg **Fortsæt**, enig med licensvilkårene, og angiv adgangskoden, når du bliver bedt om det.

3. Når installationen er slut, bliver du promoveret til at godkende de systemudvidelser, der bruges af produktet. Vælg **Åbn sikkerhedsindstillinger**.

    ![Godkendelse af systemudvidelse.](images/monterey-install-2.png)

4. Vælg **Tillad & vinduet** Sikkerhed og **beskyttelse af personlige oplysninger**.

    ![Sikkerhedsindstillinger for systemudvidelse1.](images/monterey-install-3.png)

5. Gentag trin 3 & 4 for alle systemudvidelser, der distribueres med Microsoft Defender til slutpunkt på Mac.

6. Som en del af egenskaberne Slutpunktsregistrering og Svar undersøger Microsoft Defender til slutpunkt på Mac socket-trafik og rapporterer disse oplysninger til Microsoft 365 Defender portalen. Når du bliver bedt om at give Microsoft Defender for Endpoint-tilladelser til at filtrere netværkstrafik, skal du vælge **Tillad**.

    ![Sikkerhedsindstillinger for systemudvidelse2.](images/monterey-install-4.png)

7. Åbn **Systemindstillinger Sikkerhed** \> **&** beskyttelse af personlige oplysninger, og gå til  fanen Beskyttelse af personlige oplysninger. Giv fuld **diskadgangstilladelse** til **Microsoft Defender** **og Microsoft Defenders Endpoint Security Extension**.

    ![Fuld diskadgang.](images/monterey-install-5.png)

## <a name="client-configuration"></a>Klientkonfiguration

1. Kopiér wdav.pkg MicrosoftDefenderATPOnboardingMacOs.py til den enhed, hvor du installerer Microsoft Defender til Slutpunkt på macOS.

    Klientenheden er ikke knyttet til org_id. Bemærk, at *org_id* er tom.

    ```bash
    mdatp health --field org_id
    ```

2. Kør Python-scriptet for at installere konfigurationsfilen:

    ```bash
    /usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py
    ```

3. Kontrollér, at enheden nu er knyttet til organisationen, og rapporter et gyldigt organisations-id:

    ```bash
    mdatp health --field org_id
    ```

    Efter installationen får du vist Microsoft Defender-ikonet på macOS-statuslinjen i øverste højre hjørne.

    > [!div class="mx-imgBorder"]
    > ![Skærmbillede af Microsoft Defender-ikon på statuslinjen.](images/mdatp-icon-bar.png)

## <a name="how-to-allow-full-disk-access"></a>Sådan tillader du fuld diskadgang

> [!CAUTION]
> macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til bestemte placeringer på disken (f.eks Dokumenter, Overførsler, Skrivebord osv.) uden udtrykkeligt samtykke. I fravær af dette samtykke kan Microsoft Defender til Slutpunkt ikke fuldt ud beskytte din enhed.

1. Hvis du vil give samtykke, skal **du åbne Sikkerhedsindstillinger** \> **& fuld** \> **diskadgang til beskyttelse** \> **af personlige oplysninger**. Klik på låseikonet for at foretage ændringer (nederst i dialogboksen). Vælg Microsoft Defender som slutpunkt.

2. Kør en test til registrering af lyd/lyd for at bekræfte, at enheden er korrekt onboardet og rapporterer til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    1. Sørg for, at beskyttelse i realtid er aktiveret (angivet med et resultat på 1 fra at køre følgende kommando):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Åbn et Terminal-vindue. Kopiér og udfør følgende kommando:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Filen skulle være sat i karantæne af Defender for Endpoint på Mac. Brug følgende kommando til at få vist en liste over alle registrerede trusler:

        ```bash
        mdatp threat list
        ```

3. Kør en Slutpunktsregistrering og -svar-registreringstest for at bekræfte, at enheden er korrekt onboardet og rapporterer til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

   1. I din browser, f.Microsoft Edge til Mac eller Safari.

   1. Download MDATP MacOS-DIY.zip fra, og https://aka.ms/mdatpmacosdiy udtræk.

      Du bliver muligvis bedt om at gøre følgende:

      > Vil du tillade downloads på "mdatpclientanalyzer.blob.core.windows.net"?<br/>
      > Du kan ændre, hvilke websteder der kan hente filer under Indstillinger for websteder.

4. Klik **på Tillad**.

5. Åbn **Downloads**.

6. Du bør se **MDATP MacOS DIY**.

   > [!TIP]
   > Hvis du dobbeltklikker, får du vist følgende meddelelse:
   >
   > > **"MDATP MacOS DIY" kan ikke åbnes, fordi udvikleren ikke kan bekræfte.**<br/>
   > > macOS kan ikke bekræfte, at denne app er fri for malware.<br/>
   > > **\[Flyt til Annuller for papirkurv\]** **\[\]**

7. Klik på **Annuller**.

8. Højreklik på **MDATP MacOS DIY**, og klik derefter på **Åbn**.

    Systemet bør vise følgende meddelelse:

    > **macOS kan ikke bekræfte udvikleren af MDATP MacOS DIY. Er du sikker på, at du vil åbne den?**<br/>
    > Ved at åbne denne app tilsidesætter du systemsikkerhed, som kan udsætte din computer og personlige oplysninger for malware, der kan skade din Mac eller forringe dine personlige oplysninger.

9. Klik **på Åbn**.

    Systemet bør vise følgende meddelelse:

    > Microsoft Defender til Slutpunkt – macOS Slutpunktsregistrering og -svar DIY-testfil<br/>
    > Tilsvarende besked vil være tilgængelig i MDATP-portalen.

10. Klik **på Åbn**.

    Efter et par minutter bør en besked med navnet "macOS Slutpunktsregistrering og -svar Testbesked" hæves.

11. Gå til Microsoft 365 Defender portal (https://security.microsoft.com/).

12. Gå til beskedkøen.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="Eksempel på en macOS-Slutpunktsregistrering og -svar, der viser alvorsgrad, kategori, registreringskilde og en skjult menu med handlinger.":::

    Kig på oplysningerne om beskeden og tidslinjen for enheden, og udfør de regelmæssige undersøgelsestrin.

## <a name="logging-installation-issues"></a>Problemer med logføring af installation

Se [Problemer med logføring](mac-resources.md#logging-installation-issues) af installation for at få flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl.

## <a name="uninstallation"></a>Fjernelse af installation

Se [Afinstallering](mac-resources.md#uninstalling) for at få mere at vide om, hvordan du fjerner Microsoft Defender til Endpoint på macOS fra klientenheder.
