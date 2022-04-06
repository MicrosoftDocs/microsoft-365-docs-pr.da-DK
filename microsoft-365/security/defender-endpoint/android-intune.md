---
title: Installer Microsoft Defender for Endpoint på Android med Microsoft Intune
description: Beskrivelse af, hvordan du installerer Microsoft Defender for Endpoint på Android med Microsoft Intune
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
ms.openlocfilehash: aab50764a13a671cdeb10902744456dcbc1cb48f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471401"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>Installer Microsoft Defender for Endpoint på Android med Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Få mere at vide om, hvordan du installerer Defender til Slutpunkt på Android Intune-firmaportal enheder, der er tilmeldt. Du kan finde flere Intune om registrering af enheder under [Tilmeld din enhed](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **Defender til Slutpunkt på Android er nu tilgængelig på [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> Du kan oprette forbindelse til Google Play fra Intune at installere Defender for Endpoint-appen på tværs af enhedsadministrator- og Android Enterprise-registreringstilstande.
>
> Opdateringer af appen sker automatisk via Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>Installér på enheder, der er tilmeldt Enhedsadministrator

**Installér Defender til slutpunkt på Android på Intune-firmaportal – enheder, der er tilmeldt af enhedsadministratoren**

Få mere at vide om, hvordan du installerer Defender til Slutpunkt på Android Intune-firmaportal – enheder, der er tilmeldt enhedsadministrator.

### <a name="add-as-android-store-app"></a>Tilføj som Android Store-app

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå til **Apps Android-apps** \>  \> **Tilføj \> Android Store-app** og vælge **Vælg**.

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="Appen Tilføj Android Store applikationsrude på Microsoft Endpoint Manager Administration"  lightbox="images/mda-addandroidstoreapp.png":::

2. På siden **Tilføj app** og i sektionen *Appoplysninger skal* du skrive:

   - **Name**
   - **Beskrivelse**
   - **Publisher** Microsoft.
   - **App Store-URL-adresse** https://play.google.com/store/apps/details?id=com.microsoft.scmx som (Defender til Endpoint-appen Google Play Store URL-adresse)

   Andre felter er valgfri. Vælg **Næste**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="Siden Tilføj app, der viser programmets udgiver- og URL-oplysninger i Microsoft Endpoint Manager Administration" lightbox="images/mda-addappinfo.png":::

3. I sektionen *Opgaver skal* du gå til sektionen **Påkrævet** og vælge **Tilføj gruppe.** Du kan derefter vælge den eller de brugergrupper, du vil målrette Defender til Slutpunkt på Android-appen. Vælg **Vælg** og derefter **Næste**.

    > [!NOTE]
    > Den valgte brugergruppe skal bestå af Intune tilmeldte brugere.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="Ruden Tilføj gruppe på siden Tilføj app Microsoft Endpoint Manager portalen Administration" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. I sektionen **Gennemse+Opret skal** du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**.

    Efter et øjeblik blev Defender for Endpoint-appen oprettet, og der blev vist en meddelelse i øverste højre hjørne på siden.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="Ruden Programstatus på Microsoft Endpoint Manager Administration" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. På siden med appoplysninger, der vises, skal du i sektionen **Skærm** vælge Installationsstatus for enhed for at bekræfte, at installationen af enheden er fuldført.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="Statussiden for installation af enhed i Microsoft Defender 365-portalen" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>Fuldfør onboarding, og kontrollér status

1. Når Defender til Slutpunkt på Android er blevet installeret på enheden, kan du se appikonet.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="Microsoft Defender ATP-ikonet, der vises i søgeruden" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. Tryk på Microsoft Defender for Endpoint-appikonet, og følg instruktionerne på skærmen for at fuldføre onboarding af appen. Oplysningerne omfatter slutbrugeraccept af Android-tilladelser, der kræves af Defender til Slutpunkt på Android.

3. Når onboarding er gennemført, vises enheden på listen Enheder i Microsoft 365 Defender portal.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="En enhed i Microsoft Defender for Endpoint portalen"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>Installér på Android Enterprise-enheder, der er tilmeldt

Defender til Slutpunkt på Android understøtter enheder, der er tilmeldt Android Enterprise.

Du kan finde flere oplysninger om de registreringsindstillinger, der understøttes Intune, under [Registreringsindstillinger](/mem/intune/enrollment/android-enroll).

**I øjeblikket understøttes personligt ejet enheder med arbejdsprofil og virksomhedsejede fuldt administrerede tilmeldinger til brugerenheder til udrulning.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>Tilføj Microsoft Defender for Endpoint på Android som en administreret Google Play-app

Følg trinnene nedenfor for at tilføje Microsoft Defender for Endpoint app i din administrerede Google Play.

1. I [Microsoft Endpoint Manager administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå til **Apps** \> **Android-apps Tilføj** \> **og** vælge **Administreret Google Play-app**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="Ruden til tilføjelse af program i Microsoft Endpoint Manager Administration" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. På din administrerede Google Play-side, der indlæses efterfølgende, skal du gå til søgefeltet og skrive `Microsoft Defender`. Søgningen skal vise Microsoft Defender for Endpoint i din administrerede Google Play. Klik på Microsoft Defender for Endpoint fra søgeresultatet apps.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="Siden Administreret Google Play Microsoft Endpoint Manager administrationscenterets portal" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. På siden med appbeskrivelsen, der vises næste gang, bør du kunne se appoplysninger på Defender til slutpunkt. Gennemse oplysningerne på siden, og vælg derefter **Godkend**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="Siden for administreret Google Play i Microsoft Endpoint Manager administrationscenter" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. Du får vist de tilladelser, som Defender for Endpoint får for at få det til at fungere. Gennemse dem, og vælg derefter **Godkend**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="Siden til godkendelse af tilladelser i Microsoft Defender 365-portalen" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. Du får vist siden med indstillinger for godkendelse. Siden bekræfter din indstilling til at håndtere nye apptilladelser, som Defender til Slutpunkt på Android muligvis spørger. Gennemse valgmulighederne, og vælg din foretrukne indstilling. Vælg **Udført**.

    Administreret Google Play vælger som standard Bevar **godkendt, når appen anmoder om nye tilladelser**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" Siden til konfiguration af godkendelsesindstillinger på Microsoft Defender 365-portalen" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. Når der er foretaget valg for håndtering af tilladelser, skal du **vælge Synkroniser** for Microsoft Defender for Endpoint synkronisere med din appliste.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="Ruden Synkroniser i Microsoft Defender 365-portalen" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. Synkroniseringen fuldføres om et par minutter.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="Statusruden for programsynkronisering på siden med Android-apps i Microsoft Defender 365-portalen"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. Vælg knappen **Opdater** på Android-appskærmen, og Microsoft Defender for Endpoint skal kunne ses på listen over apps.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="Den side, der viser det synkroniserede program" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. Defender til Slutpunkt understøtter appkonfigurationspolitikker for administrerede enheder via Intune. Denne funktion kan anvendes til automatisk at angive relevante Android-tilladelser, så slutbrugeren ikke behøver at acceptere disse tilladelser.

    1. På siden **Apps** skal du gå til **Politik > politikker for appkonfiguration > Tilføj > administrerede enheder**.

       :::image type="content" source="images/android-mem.png" alt-text="Ruden Politikker for appkonfiguration på Microsoft Endpoint Manager Administrationsportal" lightbox="images/android-mem.png":::

    1. Angiv følgende **oplysninger på siden Opret** politik for appkonfiguration:

        - Navn: Microsoft Defender for Endpoint.
        - Vælg **Android Enterprise** som platform.
        - Vælg **kun Arbejdsprofil** som Profiltype.
        - Klik **på Vælg app**, vælg **Microsoft Defender ATP**, vælg **OK** og derefter **Næste**.

        :::image type="content" source="images/android-create-app.png" alt-text=" Detaljeruden tilknyttet app" lightbox="images/android-create-app.png":::

    1. På siden **Indstillinger** skal du gå til sektionen Tilladelser og klikke på Tilføj for at få vist listen over understøttede tilladelser. I sektionen Tilføj tilladelser skal du vælge følgende tilladelser:

       - Eksternt lager (læst)
       - Eksternt lager (skriv)

       Vælg derefter **OK**.

       :::image type="content" source="images/android-create-app-config.png" alt-text="Ruden Tilføj tilladelser" lightbox="images/android-create-app-config.png":::

    1. Du bør nu kunne se både de tilladelser, der er angivet, og nu kan du automatisk begge dele ved at vælge automatisk under  rullelisten Tilladelsestilstand og derefter vælge **Næste**.

       :::image type="content" source="images/android-auto-grant.png" alt-text="Ruden Tilladelsestilstand" lightbox="images/android-auto-grant.png":::

    1. På siden **Opgaver skal** du vælge den brugergruppe, som denne appkonfigurationspolitik ville blive tildelt til. Klik **på Vælg grupper, der** skal medtages, og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er som regel den samme gruppe, som du tildeler Microsoft Defender for Endpoint Android-app.

       :::image type="content" source="images/android-select-group.png" alt-text="Ruden Valgte grupper" lightbox="images/android-select-group.png":::

    1. På siden **Gennemse + Opret** , som vises herefter, skal du gennemse alle oplysningerne og derefter vælge **Opret**.

        Appkonfigurationspolitikken for Defender til Slutpunkt, hvor der automatisk tildeles lagerpladstilladelse, er nu tildelt den valgte brugergruppe.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="Fanen Gennemse + Opret på siden Opret politik for appkonfiguration" lightbox="images/android-review-create.png":::

10. Vælg **Microsoft Defender ATP-appen** på listen \> **Egenskabstildelinger** \>  \> **Rediger**.

   :::image type="content" source="images/mda-properties.png" alt-text="Indstillingen Rediger på siden Egenskaber" lightbox="images/mda-properties.png":::

11. Tildele appen som en *påkrævet* app til en brugergruppe. Den installeres automatisk i *arbejdsprofilen* under den næste synkronisering af enheden via Firmaportal app. Denne opgave kan udføres ved at gå til sektionen *Påkrævet* Tilføj \> **gruppe,** vælge brugergruppen og klikke på **Vælg**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="Siden Rediger program" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. På siden **Rediger program** skal du gennemse alle de oplysninger, der blev angivet ovenfor. Vælg derefter **Gennemse + Gem og** derefter **Gem igen** for at starte opgaven.

### <a name="auto-setup-of-always-on-vpn"></a>Automatisk konfiguration af ALWAYS-on VPN

Defender til Slutpunkt understøtter politikker for enhedskonfiguration for administrerede enheder via Intune. Denne funktion kan anvendes til automatisk konfiguration af **Always-on VPN** på Enheder, der er tilmeldt Android Enterprise, så slutbrugeren ikke behøver at konfigurere VPN-tjenesten under onboarding.

1. På **Enheder skal** du vælge **Konfigurationsprofiler** \> **Opret profilplatform** \>  \> **til Android Enterprise**

   Vælg **Enhedsbegrænsninger** under et af følgende baseret på din enhedsregistreringstype:
   - **Fuldt administreret, dedikeret og Corporate-Owned arbejdsprofil**
   - **Personligt ejet arbejdsprofil**

   Vælg **Opret**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="Menupunktet Konfigurationsprofiler i ruden Politik" lightbox="images/1autosetupofvpn.png":::

2. **Konfigurationsprofil Indstillinger** Angiv **et navn** og **en Beskrivelse for** entydigt at identificere konfigurationsprofilen.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="Felterne Navn og Beskrivelse på enheders konfigurationsprofil i ruden Grundlæggende" lightbox="images/2autosetupofvpn.png":::

3. Vælg **Forbindelse,** og konfigurer VPN:

   - **Aktivér VPN altid på**

     Konfigurer en VPN-klient i arbejdsprofilen for automatisk at oprette forbindelse til og genoprette forbindelsen til VPN, når det er muligt. Der kan kun konfigureres én VPN-klient til VPN altid på en given enhed, så sørg for, at der ikke er installeret mere end én altid på VPN-politik på en enkelt enhed.

   - Vælg **Brugerdefineret** i rullelisten VPN-klient

     Custom VPN in this case is Defender for Endpoint VPN which is used to provide the Web Protection feature.

     > [!NOTE]
     > Microsoft Defender for Endpoint-appen skal være installeret på brugerens enhed for at kunne fungere med automatisk konfiguration af dette VPN.

   - Angiv **pakke-id'et** for Microsoft Defender for Endpoint i Google Play Butik. For Defender-appens URL-adresse <https://play.google.com/store/apps/details?id=com.microsoft.scmx>er **pakke-id'et com.microsoft.scmx**

   - **Låst tilstand** Ikke konfigureret (standard)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="Ruden Forbindelse under fanen Konfigurationsindstillinger" lightbox="images/3autosetupofvpn.png":::

4. **Opgave**

   På siden **Opgaver skal** du vælge den brugergruppe, som denne appkonfigurationspolitik ville blive tildelt til. Vælg **Vælg grupper,** der skal medtages og vælg den relevante gruppe, og vælg derefter **Næste**. Den gruppe, der vælges her, er som regel den samme gruppe, som du tildeler Microsoft Defender for Endpoint Android-app.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="Ruden Enhedskonfigurationsprofil i Enhedsbegrænsninger" lightbox="images/4autosetupofvpn.png":::

5. På siden **Gennemse + Opret** , som vises herefter, skal du gennemse alle oplysningerne og derefter vælge **Opret**.
Enhedskonfigurationsprofilen er nu tildelt den valgte brugergruppe.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="En enheders konfigurationsprofil 's klargøring til Gennemsyn + opret" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>Kontrollér status og fuldfør onboarding

1. Bekræft installationsstatussen for Microsoft Defender for Endpoint på Android ved at klikke på **Installationsstatus for enhed**. Kontrollér, at enheden vises her.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="Statusruden for installation af enhed" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. På enheden kan du validere onboardingstatus ved at gå til **arbejdsprofilen**. Bekræft, at Defender til slutpunkt er tilgængelig, og at du er tilmeldt de **personligt ejet enheder med arbejdsprofil**. Hvis du er tilmeldt en virksomhedsejet **,** fuldt administreret brugerenhed, har du en enkelt profil på enheden, hvor du kan bekræfte, at Defender til slutpunkt er tilgængelig.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="Visningsruden for programmet" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. Når appen er installeret, skal du åbne appen og acceptere tilladelserne, og derefter skulle onboardingen være gennemført.

    :::image type="content" source="images/MDE_new.png" alt-text="Th display of a Microsoft Defender for Endpoint application on a mobile device" lightbox="images/MDE_new.png":::

4. På dette tidspunkt er enheden blevet onboardet på Defender til Slutpunkt på Android. Du kan bekræfte dette på [Microsoft 365 Defender-portalen](https://security.microsoft.com) ved at gå til **siden Lager over** enheder.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="Den Microsoft Defender for Endpoint portal" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Konfigurer Microsoft Defender for Endpoint på Android-funktioner](android-configure.md)
