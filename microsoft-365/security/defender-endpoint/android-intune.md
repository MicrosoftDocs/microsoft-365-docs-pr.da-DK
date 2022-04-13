---
title: Installér Microsoft Defender for Endpoint på Android med Microsoft Intune
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på Android med Microsoft Intune
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, installation, installere, afinstallation,
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
ms.openlocfilehash: 461664cc72486a49e5b7bd9be44235559409adff
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825235"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Installér Microsoft Defender for Endpoint på Android med Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Få mere at vide om, hvordan du installerer Defender for Endpoint på Android på Intune-firmaportal tilmeldte enheder. Du kan få flere oplysninger om Intune enhedsregistrering under [Tilmeld din enhed](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Defender for Endpoint på Android er nu tilgængelig i [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Du kan oprette forbindelse til Google Play fra Intune for at installere Defender for Endpoint-appen på tværs af enhedsadministrator- og Android Enterprise-tilmeldingstilstande.
>
> Opdateringer til appen opdateres automatisk via Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Installér på de enheder, der er tilmeldt af enhedsadministratoren

**Installér Defender for Endpoint på Android på Intune-firmaportal – Enheder, der er tilmeldt af enhedsadministratoren**

Få mere at vide om, hvordan du installerer Defender for Endpoint på Android på Intune-firmaportal – enheder, der er tilmeldt af enhedsadministratoren.

### <a name="add-as-android-store-app"></a>Tilføj som Android Store-app

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Apps** \> **Android-apps** \> **Tilføj \> Android Store-app** og vælge **Vælg**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Ruden Tilføj Android Store-program på Microsoft Endpoint Manager Administrationsportal"  lightbox="images/mda-addandroidstoreapp.png":::

2. På siden **Tilføj app** og i afsnittet *Appoplysninger* skal du skrive:

   - **Name**
   - **Beskrivelse**
   - **Publisher** som Microsoft.
   - **URL-adresse til App Store** som https://play.google.com/store/apps/details?id=com.microsoft.scmx (URL-adresse til Defender for Endpoint-app i Google Play Store)

   Andre felter er valgfri. Vælg **Næste**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Siden Tilføj app, der viser oplysninger om programmets udgiver og URL-adresse på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mda-addappinfo.png":::

3. I afsnittet *Tildelinger* skal du gå til sektionen **Påkrævet** og vælge **Tilføj gruppe.** Du kan derefter vælge den eller de brugergrupper, du vil målrette mod Defender for Endpoint på Android-appen. Vælg **Vælg** og derefter **Næste**.

    > [!NOTE]
    > Den valgte brugergruppe skal bestå af Intune tilmeldte brugere.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Ruden Tilføj gruppe på siden Tilføj app på Microsoft Endpoint Manager Administrationsportal" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. I afsnittet **Gennemse+Opret** skal du kontrollere, at alle de angivne oplysninger er korrekte, og derefter vælge **Opret**.

    Om et øjeblik oprettes Defender for Endpoint-appen, og der vises en meddelelse i øverste højre hjørne af siden.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Ruden programstatus på Microsoft Endpoint Manager Administrationsportal" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. På den side med appoplysninger, der vises, skal du i afsnittet **Overvåg** vælge **Status for enhedsinstallation** for at kontrollere, at enhedsinstallationen er fuldført.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Siden Status for installation af enhed på Microsoft Defender 365-portalen" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Fuldfør onboarding, og kontrollér status

1. Når Defender for Endpoint på Android er installeret på enheden, får du vist appikonet.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Ikonet Microsoft Defender ATP angivet i ruden Søg" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Tryk på ikonet Microsoft Defender for Endpoint app, og følg vejledningen på skærmen for at fuldføre onboarding af appen. Oplysningerne omfatter slutbrugeraccept af Android-tilladelser, der kræves af Defender for Endpoint på Android.

3. Ved vellykket onboarding vises enheden på listen Enheder på Microsoft 365 Defender-portalen.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="En enhed på Microsoft Defender for Endpoint-portalen"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Installér på tilmeldte Android Enterprise-enheder

Defender for Endpoint på Android understøtter Android Enterprise-tilmeldte enheder.

Du kan få flere oplysninger om de tilmeldingsindstillinger, der understøttes af Intune, under [Tilmeldingsindstillinger](/mem/intune/enrollment/android-enroll).

**I øjeblikket understøttes personligt ejede enheder med arbejdsprofil og virksomhedsejede fuldt administrerede brugerenhedsregistreringer til installation.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Tilføj Microsoft Defender for Endpoint på Android som en Administreret Google Play-app

Følg nedenstående trin for at føje Microsoft Defender for Endpoint app til din administrerede Google Play.

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Apps** \> **Android-apps** \> **Tilføj** og vælge **Administreret Google Play-app**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Ruden til tilføjelse af programmer på Microsoft Endpoint Manager Administrationsportal" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. På din administrerede Google Play-side, der indlæses efterfølgende, skal du gå til søgefeltet og angive `Microsoft Defender`. Din søgning skal vise appen Microsoft Defender for Endpoint i administreret Google Play. Klik på appen Microsoft Defender for Endpoint fra søgeresultatet Apps.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Siden Administreret Google Play på Microsoft Endpoint Manager Administrationsportal" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. På siden Med appbeskrivelse, der vises derefter, kan du se appdetaljer om Defender for Endpoint. Gennemse oplysningerne på siden, og vælg derefter **Godkend**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Siden Administreret Google Play på Microsoft Endpoint Manager Administrationsportal" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Du får vist de tilladelser, som Defender for Endpoint får til at fungere. Gennemse dem, og vælg derefter **Godkend**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Siden til godkendelse af tilladelser på Microsoft Defender 365-portalen" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Du får vist siden Godkendelsesindstillinger. Siden bekræfter, at du foretrækker at håndtere nye apptilladelser, som Defender for Endpoint muligvis spørger om på Android. Gennemse valgmulighederne, og vælg din foretrukne indstilling. Vælg **Udført**.

    Administreret Google Play vælger som standard **Bevar godkendelse, når appen anmoder om nye tilladelser**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Siden konfiguration af godkendelsesindstillinger på microsoft Defender 365-portalen" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. Når de tilladelser, der håndterer valget, er foretaget, skal du vælge **Synkroniser** for at synkronisere Microsoft Defender for Endpoint til listen over apps.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Ruden Synkroniser på Microsoft Defender 365-portalen" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Synkroniseringen fuldføres om et par minutter.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Statusruden for programsynkronisering på siden Android-apps på Microsoft Defender 365-portalen"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Vælg knappen **Opdater** på skærmen Android-apps, hvorefter Microsoft Defender for Endpoint skal være synlig på listen over apps.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Den side, der viser det synkroniserede program" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Defender for Endpoint understøtter appkonfigurationspolitikker for administrerede enheder via Intune. Denne funktion kan udnyttes til at vælge forskellige konfigurationer til Defender.

    1. På siden **Apps** skal du gå til **Politik > Appkonfigurationspolitikker > Tilføj > Administrerede enheder**.

       :::image type="content" source="images/android-mem.png" alt-text="Ruden Appkonfigurationspolitikker på Microsoft Endpoint Manager Administrationsportal" lightbox="images/android-mem.png":::

    1. Angiv følgende oplysninger på siden **Opret appkonfigurationspolitik** :

        - Navn: Microsoft Defender for Endpoint.
        - Vælg **Android Enterprise** som platform.
        - Vælg **kun arbejdsprofil** som profiltype.
        - Klik på **Vælg app**, vælg **Microsoft Defender ATP**, vælg **OK** og derefter **Næste**.

        :::image type="content" source="images/android-create-app.png" alt-text=" Ruden Tilknyttede appoplysninger" lightbox="images/android-create-app.png":::

    1. På siden **Indstillinger** skal du gå til afsnittet **Konfigurationsindstillinger** og vælge **"Brug konfigurationsdesigner"** i konfigurationsindstillingsformat. 

       :::image type="content" alt-text="Billede af konfigurationspolitikken for oprettelse af app til Android." source="images/configurationformat.png" lightbox="images/configurationformat.png":::

    1. Klik på **Tilføj** for at få vist en liste over understøttede konfigurationer. Vælg den påkrævede konfiguration, og klik på **OK**.

       :::image type="content" alt-text="Billede af valg af konfigurationspolitikker til Android." source="images/selectconfigurations.png" lightbox="images/selectconfigurations.png":::


    1. Du bør kunne se alle de valgte konfigurationer på listen. Du kan ændre konfigurationsværdien efter behov og derefter vælge **Næste**.
        
        :::image type="content" alt-text="Billede af valgte konfigurationspolitikker." source="images/listedconfigurations.png" lightbox="images/listedconfigurations.png":::
       

    1. På siden **Tildelinger** skal du vælge den brugergruppe, som denne appkonfigurationspolitik skal tildeles til. Klik på **Vælg de grupper, der skal medtages** , og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er normalt den samme gruppe, som du tildeler Microsoft Defender for Endpoint Android-app.

       :::image type="content" source="images/android-select-group.png" alt-text="Ruden Valgte grupper" lightbox="images/android-select-group.png":::

    1. Gennemse **+ opret** på den næste side, gennemse alle oplysningerne, og vælg derefter **Opret**.

        Appkonfigurationspolitikken for Defender for Endpoint, der automatisk giver lagertilladelsen, er nu tildelt den valgte brugergruppe.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Fanen Gennemse + opret på siden Opret appkonfigurationspolitik" lightbox="images/android-review-create.png":::

10. Vælg **Microsoft Defender ATP-app** på listen \> **Egenskaber** \> **Tildelinger** \> **Rediger**.

   :::image type="content" source="images/mda-properties.png" alt-text="Indstillingen Rediger på siden Egenskaber" lightbox="images/mda-properties.png":::

11. Tildel appen som en *påkrævet* app til en brugergruppe. Den installeres automatisk i *arbejdsprofilen* under den næste synkronisering af enheden via Firmaportal app. Denne tildeling kan udføres ved at navigere til sektionen \> *Påkrævet* **Tilføj gruppe,** vælge brugergruppen og klikke på **Vælg**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Siden Rediger program" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. Gennemse alle de oplysninger, der er angivet ovenfor, på siden **Rediger program** . Vælg derefter **Gennemse + Gem** , og **gem** igen for at påbegynde tildelingen.

### <a name="auto-setup-of-always-on-vpn"></a>Automatisk konfiguration af Always-on VPN

Defender for Endpoint understøtter politikker for enhedskonfiguration for administrerede enheder via Intune. Denne funktion kan udnyttes til **automatisk konfiguration af Always-on VPN på Android Enterprise-tilmeldte** enheder, så slutbrugeren ikke behøver at konfigurere VPN-tjenesten under onboarding.

1. På **enheder** skal du vælge **Konfigurationsprofiler** \> **Opret profilplatform** \>  \> **Android Enterprise**

   Vælg **Enhedsbegrænsninger** under en af følgende, afhængigt af din tilmeldingstype for enheden:
   - **Fuldt administreret, dedikeret og Corporate-Owned arbejdsprofil**
   - **Personligt ejet arbejdsprofil**

   Vælg **Opret**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="Menupunktet Konfigurationsprofiler i ruden Politik" lightbox="images/1autosetupofvpn.png":::

2. **Konfiguration Indstillinger** Angiv et **navn** og en **beskrivelse** for entydigt at identificere konfigurationsprofilen.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Felterne Navn og Beskrivelse for enhedskonfigurationsprofilen i ruden Grundlæggende" lightbox="images/2autosetupofvpn.png":::

3. Vælg **Forbindelse,** og konfigurer VPN:

   - Aktivér **Always-on VPN**

     Konfigurer en VPN-klient i arbejdsprofilen for automatisk at oprette forbindelse til og genoprette forbindelsen til VPN, når det er muligt. Der kan kun konfigureres én VPN-klient for VPN, der altid er tændt, på en given enhed, så sørg for ikke at have mere end én VPN-politik, der altid er aktiveret, installeret på en enkelt enhed.

   - Vælg **Brugerdefineret** på rullelisten VPN-klient

     Brugerdefineret VPN er i dette tilfælde Defender for Endpoint VPN, som bruges til at levere webbeskyttelsesfunktionen.

     > [!NOTE]
     > Microsoft Defender for Endpoint app skal være installeret på brugerens enhed, for at denne VPN kan fungere automatisk.

   - Angiv **pakke-id for** appen Microsoft Defender for Endpoint i Google Play Butik. Pakke-id'et er **com.microsoft.scmx** for URL-adressen til Defender-appen <https://play.google.com/store/apps/details?id=com.microsoft.scmx>

   - **Låsningstilstand** Ikke konfigureret (standard)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Ruden Forbindelse under fanen Konfigurationsindstillinger" lightbox="images/3autosetupofvpn.png":::

4. **Tildeling**

   På siden **Tildelinger** skal du vælge den brugergruppe, som denne appkonfigurationspolitik skal tildeles til. Vælg **Vælg de grupper** , der skal medtages, og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er normalt den samme gruppe, som du tildeler Microsoft Defender for Endpoint Android-app.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Ruden Tildeling af enhedskonfigurationsprofil i Enhedsbegrænsninger" lightbox="images/4autosetupofvpn.png":::

5. Gennemse **+ opret** på den næste side, gennemse alle oplysningerne, og vælg derefter **Opret**.
Enhedskonfigurationsprofilen er nu tildelt den valgte brugergruppe.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="Klargøring af en enhedskonfigurationsprofil til gennemsyn og oprettelse" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Kontrollér status og komplet onboarding

1. Bekræft installationsstatus for Microsoft Defender for Endpoint på Android ved at klikke på Status for **enhedsinstallation**. Kontrollér, at enheden vises her.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Statusruden for enhedsinstallation" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. På enheden kan du validere onboardingstatussen ved at gå til **arbejdsprofilen**. Bekræft, at Defender for Endpoint er tilgængelig, og at du er tilmeldt de **personligt ejede enheder med arbejdsprofilen**. Hvis du er tilmeldt en **virksomhedsejet, fuldt administreret brugerenhed**, har du en enkelt profil på enheden, hvor du kan bekræfte, at Defender for Endpoint er tilgængelig.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Visningsruden for programmet" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Når appen er installeret, skal du åbne appen og acceptere tilladelserne, hvorefter onboarding lykkes.

    :::image type="content" source="images/MDE_new.png" alt-text="Visning af et Microsoft Defender for Endpoint program på en mobilenhed" lightbox="images/MDE_new.png":::

4. På dette tidspunkt er enheden onboardet til Defender for Endpoint på Android. Du kan bekræfte dette på [Microsoft 365 Defender portalen](https://security.microsoft.com) ved at gå til siden **Enhedslager**.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Portalen Microsoft Defender for Endpoint" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Konfigurer Microsoft Defender for Endpoint på Android-funktioner](android-configure.md)
