---
title: Installér Microsoft Defender til slutpunkt på Android med Microsoft Intune
description: Beskrivelse af, hvordan du installerer Microsoft Defender til slutpunkt på Android med Microsoft Intune
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, installation, deploy, uninstallation,
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
ms.openlocfilehash: 380e2ecb9ee8df7eb066eef600f796685215662f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63595837"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Installér Microsoft Defender til slutpunkt på Android med Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Få mere at vide om, hvordan du installerer Defender til Slutpunkt på Android Intune-firmaportal enheder, der er tilmeldt. Du kan finde flere oplysninger om registrering af enheder i Intune under [Tilmeld din enhed](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Defender til Slutpunkt på Android er nu tilgængelig på [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Du kan oprette forbindelse til Google Play fra Intune for at installere Defender for Endpoint-appen på tværs af enhedsadministrator- og Android Enterprise-registreringstilstande.
>
> Opdateringer af appen sker automatisk via Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Installér på enheder, der er tilmeldt Enhedsadministrator

**Installér Defender til slutpunkt på Android på Intune-firmaportal – enheder, der er tilmeldt af enhedsadministratoren**

Få mere at vide om, hvordan du installerer Defender til Slutpunkt på Android Intune-firmaportal – enheder, der er tilmeldt enhedsadministrator.

### <a name="add-as-android-store-app"></a>Tilføj som Android Store-app

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå til **Apps Android-apps** \>  \> **Tilføj \> Android Store-app** og vælge **Vælg**.

   :::image type="content" alt-text="Billede af Microsoft Endpoint Manager Administration tilføje Android Store-programmet." source="images/mda-addandroidstoreapp.png" lightbox="images/mda-addandroidstoreapp.png":::

2. På siden **Tilføj app** og i sektionen *Appoplysninger skal* du skrive:

   - **Name**
   - **Beskrivelse**
   - **Publisher** Microsoft.
   - **App Store-URL-adresse** https://play.google.com/store/apps/details?id=com.microsoft.scmx som (Defender til Endpoint-appen Google Play Store URL-adresse)

   Andre felter er valgfri. Vælg **Næste**.

   :::image type="content" alt-text="Billede af Microsoft Endpoint Manager Administration tilføje appoplysninger." source="images/mda-addappinfo.png" lightbox="images/mda-addappinfo.png":::

3. I sektionen *Opgaver skal* du gå til sektionen **Påkrævet** og vælge **Tilføj gruppe.** Du kan derefter vælge den eller de brugergrupper, du vil målrette Defender til Slutpunkt på Android-appen. Vælg **Vælg** og derefter **Næste**.

    > [!NOTE]
    > Den valgte brugergruppe skal bestå af tilmeldte Intune-brugere.
    >
    > :::image type="content" alt-text="Billede af Microsoft Endpoint Manager valgte brugergrupper i Administration." source="images/363bf30f7d69a94db578e8af0ddd044b.png" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. I sektionen **Gennemse+Opret skal** du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**.

    Efter et øjeblik blev Defender for Endpoint-appen oprettet, og der blev vist en meddelelse i øverste højre hjørne på siden.

    :::image type="content" alt-text="Billede af Microsoft Endpoint Manager administration af Defender for Endpoint-appen." source="images/86cbe56f88bb6e93e9c63303397fc24f.png" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. På siden med appoplysninger, der vises, skal du i sektionen **Skærm** vælge Installationsstatus for enhed for at bekræfte, at installationen af enheden er fuldført.

    :::image type="content" alt-text="Billede af Microsoft Endpoint Manager installation af Administration." source="images/513cf5d59eaaef5d2b5bc122715b5844.png" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Fuldfør onboarding, og kontrollér status

1. Når Defender til Slutpunkt på Android er blevet installeret på enheden, kan du se appikonet.

    ![Ikon på mobilenhed.](images/7cf9311ad676ec5142002a4d0c2323ca.jpg)

2. Tryk på appikonet Microsoft Defender for Endpoint, og følg instruktionerne på skærmen for at fuldføre onboarding-appen. Oplysningerne omfatter slutbrugeraccept af Android-tilladelser, der kræves af Defender til Slutpunkt på Android.

3. Når onboarding er gennemført, vises enheden på listen Enheder i Microsoft 365 Defender portal.

    :::image type="content" alt-text="Billede af enhed i Defender til Endpoint-portalen." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Installér på Android Enterprise-enheder, der er tilmeldt

Defender til Slutpunkt på Android understøtter enheder, der er tilmeldt Android Enterprise.

Du kan finde flere oplysninger om de indstillinger for tilmelding, der understøttes af Intune, [under Registreringsindstillinger](/mem/intune/enrollment/android-enroll).

**I øjeblikket understøttes personligt ejet enheder med arbejdsprofil og virksomhedsejede fuldt administrerede tilmeldinger til brugerenheder til udrulning.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Tilføj Microsoft Defender til slutpunkt på Android som en administreret Google Play-app

Følg trinnene nedenfor for at tilføje Microsoft Defender for Endpoint-appen i din administrerede Google Play.

1. I [Microsoft Endpoint Manager administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå til **Apps** \> **Android-apps Tilføj** \> **og** vælge **Administreret Google Play-app**.

    :::image type="content" alt-text="Billede af Microsoft Endpoint Manager administreret Google Play." source="images/579ff59f31f599414cedf63051628b2e.png" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. På din administrerede Google Play-side, der indlæses efterfølgende, skal du gå til søgefeltet og skrive `Microsoft Defender`. Søgningen skal vise appen Microsoft Defender til slutpunkt i din administrerede Google Play. Klik på appen Microsoft Defender til slutpunkt fra søgeresultaterne for apps.

    ![Billede af Microsoft Endpoint Manager Administration App-søgning.](images/0f79cb37900b57c3e2bb0effad1c19cb.png)

3. På siden med appbeskrivelsen, der vises næste gang, bør du kunne se appoplysninger på Defender til slutpunkt. Gennemse oplysningerne på siden, og vælg derefter **Godkend**.

    > [!div class="mx-imgBorder"]
    > ![Et skærmbillede af en administreret Google Play.](images/07e6d4119f265037e3b80a20a73b856f.png)

4. Du får vist de tilladelser, som Defender for Endpoint får for at få det til at fungere. Gennemse dem, og vælg derefter **Godkend**.

    ![Et skærmbillede af godkendelsesappen Defender til Endpoint Preview.](images/206b3d954f06cc58b3466fb7a0bd9f74.png)

5. Du får vist siden med indstillinger for godkendelse. Siden bekræfter din indstilling til at håndtere nye apptilladelser, som Defender til Slutpunkt på Android muligvis spørger. Gennemse valgmulighederne, og vælg din foretrukne indstilling. Vælg **Udført**.

    Administreret Google Play vælger som standard Bevar **godkendt, når appen anmoder om nye tilladelser**.

    > [!div class="mx-imgBorder"]
    > ![Billede af fanen Meddelelser.](images/ffecfdda1c4df14148f1526c22cc0236.png)

6. Når du har foretaget den valgte håndtering af tilladelser, skal du **vælge Synkroniser** for at synkronisere Microsoft Defender til slutpunkt med listen over apps.

    > [!div class="mx-imgBorder"]
    > ![Billede af synkroniseringsside.](images/34e6b9a0dae125d085c84593140180ed.png)

7. Synkroniseringen fuldføres om et par minutter.

    :::image type="content" alt-text="Billede af Android-appen." source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Vælg knappen **Opdater** på Android-appskærmen, og Microsoft Defender til slutpunkt skal være synlige på listen over apps.

    :::image type="content" alt-text="Billede af listen over Android-apps." source="images/fa4ac18a6333335db3775630b8e6b353.png" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Defender til Slutpunkt understøtter appkonfigurationspolitikker for administrerede enheder via Intune. Denne funktion kan anvendes til automatisk at angive relevante Android-tilladelser, så slutbrugeren ikke behøver at acceptere disse tilladelser.

    1. På siden **Apps** skal du gå til **Politik > politikker for appkonfiguration > Tilføj > administrerede enheder**.

       :::image type="content" alt-text="Billede af Microsoft Endpoint Manager Android-administrerede enheder." source="images/android-mem.png":::

    1. Angiv følgende **oplysninger på siden Opret** politik for appkonfiguration:

        - Navn: Microsoft Defender til slutpunkt.
        - Vælg **Android Enterprise** som platform.
        - Vælg **kun Arbejdsprofil** som Profiltype.
        - Klik **på Vælg app**, vælg **Microsoft Defender ATP**, vælg **OK** og derefter **Næste**.

        :::image type="content" alt-text="Billede af siden opret politik for appkonfiguration." source="images/android-create-app.png" lightbox="images/android-create-app.png":::

    1. På siden **Indstillinger** skal du gå til sektionen Tilladelser og klikke på Tilføj for at få vist listen over understøttede tilladelser. I sektionen Tilføj tilladelser skal du vælge følgende tilladelser:

       - Eksternt lager (læst)
       - Eksternt lager (skriv)

       Vælg derefter **OK**.

       :::image type="content" alt-text="Billede af android-konfigurationspolitik for apps." source="images/android-create-app-config.png" lightbox="images/android-create-app-config.png":::

    1. Du bør nu kunne se både de tilladelser, der er angivet, og nu kan du automatisk begge dele ved at vælge automatisk under  rullelisten Tilladelsestilstand og derefter vælge **Næste**.

       :::image type="content" alt-text="Billede af automatisk oprettelsespolitik for appkonfiguration i Android." source="images/android-auto-grant.png" lightbox="images/android-auto-grant.png":::

    1. På siden **Opgaver skal** du vælge den brugergruppe, som denne appkonfigurationspolitik ville blive tildelt til. Klik **på Vælg grupper, der** skal medtages, og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er som regel den samme gruppe, som du skal tildele Microsoft Defender til Endpoint Android-appen.

       :::image type="content" alt-text="Billede af politikken opret appkonfiguration." source="images/android-select-group.png" lightbox="images/android-select-group.png":::

    1. På siden **Gennemse + Opret** , som vises herefter, skal du gennemse alle oplysningerne og derefter vælge **Opret**.

        Appkonfigurationspolitikken for Defender til Slutpunkt, hvor der automatisk tildeles lagerpladstilladelse, er nu tildelt den valgte brugergruppe.

        > [!div class="mx-imgBorder"]
        > ![Billede af android review create app config policy.](images/android-review-create.png)

10. Vælg **Microsoft Defender ATP-appen** på listen \> **Egenskabstildelinger** \>  \> **Rediger**.

    :::image type="content" alt-text="Billede af listen over apps." source="images/mda-properties.png" lightbox="images/mda-properties.png":::

11. Tildele appen som en *påkrævet* app til en brugergruppe. Den installeres automatisk i *arbejdsprofilen* under den næste synkronisering af enheden via Firmaportal app. Denne opgave kan udføres ved at gå til sektionen *Påkrævet* Tilføj \> **gruppe,** vælge brugergruppen og klikke på **Vælg**.

    > [!div class="mx-imgBorder"]
    > ![Billede af siden Rediger program.](images/ea06643280075f16265a596fb9a96042.png)

12. På siden **Rediger program** skal du gennemse alle de oplysninger, der blev angivet ovenfor. Vælg derefter **Gennemse + Gem og** derefter **Gem igen** for at starte opgaven.

### <a name="auto-setup-of-always-on-vpn"></a>Automatisk konfiguration af ALWAYS-on VPN

Defender til Slutpunkt understøtter politikker for enhedskonfiguration for administrerede enheder via Intune. Denne funktion kan anvendes til automatisk konfiguration af **Always-on VPN** på Enheder, der er tilmeldt Android Enterprise, så slutbrugeren ikke behøver at konfigurere VPN-tjenesten under onboarding.

1. På **Enheder skal** du vælge **Konfigurationsprofiler** \> **Opret profilplatform** \>  \> **til Android Enterprise**

   Vælg **Enhedsbegrænsninger** under et af følgende baseret på din enhedsregistreringstype:
   - **Fuldt administreret, dedikeret og Corporate-Owned arbejdsprofil**
   - **Personligt ejet arbejdsprofil**

   Vælg **Opret**.

   :::image type="content" alt-text="Billede af konfigurationsprofil for enheder Opret." source="images/1autosetupofvpn.png":::

2. **Konfigurationsprofil Indstillinger** Angiv **et navn** og **en Beskrivelse for** entydigt at identificere konfigurationsprofilen.

   :::image type="content" alt-text="Billede af enheders konfigurationsprofilNavn og Beskrivelse." source="images/2autosetupofvpn.png":::

3. Vælg **Forbindelse,** og konfigurer VPN:

   - **Aktivér VPN altid på**

     Konfigurer en VPN-klient i arbejdsprofilen for automatisk at oprette forbindelse til og genoprette forbindelsen til VPN, når det er muligt. Der kan kun konfigureres én VPN-klient til VPN altid på en given enhed, så sørg for, at der ikke er installeret mere end én altid på VPN-politik på en enkelt enhed.

   - Vælg **Brugerdefineret** i rullelisten VPN-klient

     Custom VPN in this case is Defender for Endpoint VPN which is used to provide the Web Protection feature.

     > [!NOTE]
     > Microsoft Defender til Slutpunkt-appen skal installeres på brugerens enhed for at kunne fungere automatisk konfiguration af dette VPN.

   - Angiv **pakke-id'et** for Microsoft Defender for Endpoint-appen i Google Play Butik. For Defender-appens URL-adresse <https://play.google.com/store/apps/details?id=com.microsoft.scmx>er **pakke-id'et com.microsoft.scmx**

   - **Låst tilstand** Ikke konfigureret (standard)

     ![Billede af enheders konfigurationsprofil aktiverer Always-on VPN.](images/3autosetupofvpn.png)
      :::image type="content" alt-text="Billede af enheders konfigurationsprofil aktiverer Always-on VPN." source="images/3autosetupofvpn.png":::

4. **Opgave**

   På siden **Opgaver skal** du vælge den brugergruppe, som denne appkonfigurationspolitik ville blive tildelt til. Vælg **Vælg grupper,** der skal medtages og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er som regel den samme gruppe, som du skal tildele Microsoft Defender til Endpoint Android-appen.

   ![Billede af enheders konfigurationsprofilTildeling.](images/4autosetupofvpn.png)

5. På siden **Gennemse + Opret** , som vises herefter, skal du gennemse alle oplysningerne og derefter vælge **Opret**.
Enhedskonfigurationsprofilen er nu tildelt den valgte brugergruppe.

   ![Billede af enheders konfigurationsprofil Gennemse og Opret.](images/5autosetupofvpn.png)

## <a name="check-status-and-complete-onboarding"></a>Kontrollér status og fuldfør onboarding

1. Bekræft installationsstatussen for Microsoft Defender til slutpunkt på Android ved at klikke på Status **for installation af enhed**. Kontrollér, at enheden vises her.

    > [!div class="mx-imgBorder"]
    > ![Billede af installationsstatus for enhed.](images/900c0197aa59f9b7abd762ab2b32e80c.png)

2. På enheden kan du validere onboardingstatus ved at gå til **arbejdsprofilen**. Bekræft, at Defender til slutpunkt er tilgængelig, og at du er tilmeldt de **personligt ejet enheder med arbejdsprofil**. Hvis du er tilmeldt en virksomhedsejet **,** fuldt administreret brugerenhed, har du en enkelt profil på enheden, hvor du kan bekræfte, at Defender til slutpunkt er tilgængelig.

    ![Billede af app på mobilenhed.](images/c2e647fc8fa31c4f2349c76f2497bc0e.png)

3. Når appen er installeret, skal du åbne appen og acceptere tilladelserne, og derefter skulle onboardingen være gennemført.

    ![Billede af mobilenhed med Microsoft Defender til endpoint-appen](images/MDE_new.png)

4. På dette tidspunkt er enheden blevet onboardet på Defender til Slutpunkt på Android. Du kan bekræfte dette på [Microsoft 365 Defender-portalen](https://security.microsoft.com) ved at gå til **siden Lager over** enheder.

    :::image type="content" alt-text="Billede af Microsoft Defender til Endpoint-portalen." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender til slutpunkt på Android](microsoft-defender-endpoint-android.md)
- [Konfigurer Microsoft Defender til slutpunkt på Android-funktioner](android-configure.md)
