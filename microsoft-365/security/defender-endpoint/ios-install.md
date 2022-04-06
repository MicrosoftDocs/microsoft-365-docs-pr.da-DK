---
title: Appbaseret installation til Microsoft Defender for Endpoint på iOS
ms.reviewer: ''
description: Beskrivelse af, hvordan du installerer Microsoft Defender for Endpoint iOS ved hjælp af en app
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, app, installation, deploy, uninstallation, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 239d16bdbdb3fd7770061a91d77a3f190cfb8f4a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476175"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>Installér Microsoft Defender for Endpoint på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

I dette emne beskrives udrulning af Defender til Slutpunkt på iOS Intune-firmaportal-tilmeldte enheder. Du kan finde flere Intune om registrering af enheder under [Tilmeld iOS-/iPadOS-enheder Intune](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at du [har adgang til Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

- Sørg for, at iOS-tilmelding er udført for dine brugere. Brugere skal have en Defender for Endpoint-licens tildelt for at kunne bruge Defender for Endpoint på iOS. Se Tildel [licenser til brugere for at](/azure/active-directory/users-groups-roles/licensing-groups-assign) få en vejledning i at tildele licenser.

> [!NOTE]
> Microsoft Defender for Endpoint på iOS er tilgængelig i [Apple App Store](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>Installationstrin

Installér Defender til Slutpunkt på iOS via Intune-firmaportal.

### <a name="add-ios-store-app"></a>Tilføj iOS Store-app

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå til **AppsiOS** -> **/iPadOSAddiOS** ->  ->  **store app** og klikke på **Vælg**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-1.png" alt-text="Fanen Tilføj programmer i Microsoft Endpoint Manager Administration" lightbox="images/ios-deploy-1.png":::

1. På siden **Tilføj app** skal du klikke **på Søg i App Store** og **Microsoft Defender for Endpoint** i søgelinjen. I sektionen med søgeresultater skal du klikke på klik *Microsoft Defender for Endpoint* på **Vælg**.

1. Vælg **iOS 11.0** som Minimum-operativsystem. Gennemgå resten af oplysningerne om appen, og klik på **Næste**.

1. I sektionen **Opgaver skal** du gå til sektionen **Påkrævet** og vælge **Tilføj gruppe**. Du kan derefter vælge den eller de brugergrupper, som du gerne vil målrette Defender for Endpoint på iOS-appen. Klik **på Vælg** og derefter **på Næste**.

    > [!NOTE]
    > Den valgte brugergruppe skal bestå af Intune tilmeldte brugere.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-2.png" alt-text="Fanen Tilføj gruppe i Microsoft Endpoint Manager Administration" lightbox="images/ios-deploy-2.png":::

1. I sektionen *Gennemse + Opret skal* du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**. Om et øjeblik bør appen Defender til slutpunkt oprettes, og der bør blive vist en meddelelse i øverste højre hjørne på siden.

1. På siden med appoplysninger, der vises, skal du i sektionen **Skærm** vælge Installationsstatus for enhed for at bekræfte, at installationen af enheden er fuldført.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-3.png" alt-text="Statussiden for installation af enhed" lightbox="images/ios-deploy-3.png":::

## <a name="complete-deployment-for-supervised-devices"></a>Komplet udrulning af overvågede enheder

Data Microsoft Defender for Endpoint iOS-appen har særlige muligheder for at overvåge iOS/iPadOS-enheder under forudsætning af de øgede administrationsfunktioner, der leveres af platformen for disse typer enheder. Det kan også levere Web Protection **uden at konfigurere et lokalt VPN på enheden**. Dette giver slutbrugerne en problemfri oplevelse, mens de stadig er beskyttet mod phishing og andre webbaserede angreb.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurer overvåget tilstand via Intune

Dernæst skal du konfigurere den overvågede tilstand for Defender for Endpoint-appen via App Configuration politik.

   > [!NOTE]
   > Denne politik for appkonfiguration til overvågede enheder gælder kun for administrerede enheder og bør målrettes alle administrerede iOS-enheder som en bedste fremgangsmåde.

1. Log på administration Microsoft Endpoint Manager [, og gå til](https://go.microsoft.com/fwlink/?linkid=2109431) Politikker for konfiguration **af appsapps** \>  \> **Tilføj**. Vælg **Administrerede enheder**.

    > [!div class="mx-imgBorder"]
    > ![Billede Microsoft Endpoint Manager Administration4.](images/ios-deploy-4.png)

1. Angiv *følgende oplysninger på siden Opret* politik for appkonfiguration:
    - Politiknavn
    - Platform: Vælg iOS/iPadOS
    - Målrettet app: **Microsoft Defender for Endpoint** på listen

    > [!div class="mx-imgBorder"]
    > ![Billede Microsoft Endpoint Manager Administration5.](images/ios-deploy-5.png)

1. På næste skærmbillede skal du vælge **Brug konfigurationsdesigner** som format. Angiv følgende egenskab:
    - Konfigurationsnøgle: udstedt
    - Værditype: Streng
    - Konfigurationsværdi: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![Billede Microsoft Endpoint Manager Administration6.](images/ios-deploy-6.png)

1. Vælg **Næste for** at åbne **siden Områdemærker** . Områdemærker er valgfri. Vælg **Næste for** at fortsætte.

1. På siden **Opgaver skal** du vælge de grupper, der skal modtage denne profil. I dette scenarie er det den bedste fremgangsmåde at målrette **alle enheder**. Du kan finde flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Når du installerer i brugergrupper, skal en bruger logge på en enhed, før politikken anvendes.

   Klik på **Næste**.

1. På siden **Gennemse + Opret** skal du vælge Opret, når du er **færdig**. Den nye profil vises på listen over konfigurationsprofiler.

1. Derefter skal du implementere en brugerdefineret profil på overvågede iOS-enheder. Dette er med henblik på at forbedre antiphishing-egenskaberne. Følg nedenstående trin:

    - Hent konfigurationsprofilen fra [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - Gå til **DevicesiOS** -> **/iPadOSKonfigurationsprofilerOpret** ->  ->  **profil**

    > [!div class="mx-imgBorder"]
    > ![Billede Microsoft Endpoint Manager Administration7.](images/ios-deploy-7.png)
    
    - Angiv et navn på profilen. Når du bliver bedt om at importere en Konfigurationsprofil-fil, skal du vælge den, der er hentet fra det forrige trin.
    - I sektionen **Tildeling** skal du vælge den enhedsgruppe, du vil anvende denne profil på. Som bedste fremgangsmåde bør dette anvendes på alle administrerede iOS-enheder. Vælg **Næste**.
    - På siden **Gennemse + Opret** skal du vælge Opret, når du er **færdig**. Den nye profil vises på listen over konfigurationsprofiler.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>Automatisk onboarding af VPN-profil (Forenklet onboarding)

For enheder, der ikke er under opsyn, bruges et VPN for at levere funktionen Webbeskyttelse. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.

>[!NOTE]
>For overvågede enheder er et VPN ikke nødvendigt for at kunne bruge Web Protection og kræver, at administratorer konfigurerer en konfigurationsprofil på overvågede enheder. Hvis du vil konfigurere for overvågede enheder, skal du følge trinnene i [sektionen Komplet installation til overvågede](#complete-deployment-for-supervised-devices) enheder.

Administratorer kan konfigurere automatisk konfiguration af VPN-profilen. Dette vil automatisk konfigurere Defender for Endpoint VPN-profilen uden at have brugeren til at gøre det under onboarding. 

Dette trin forenkler onboardingprocessen ved at konfigurere VPN-profilen. Hvis du vil have en onboardingoplevelse uden touch eller lyd, skal du se næste afsnit: [Onboard med nul-touch](#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview).

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **EnhedskonfigurationsprofilerOprette** ->  ->  **profil**.
1. Vælg **Platform** som **iOS/iPadOS** og **Profiltype** som **VPN**. Klik **på Opret**.
1. Skriv et navn til profilen, og klik på **Næste**.
1. Vælg **Custom VPN** for Connection Type, og i **sektionen Base VPN** skal du skrive følgende:
    - Forbindelsesnavn = Microsoft Defender for Endpoint
    - VPN-serveradresse = 127.0.0.1
    - Godkendelsesmetode = "Brugernavn og adgangskode"
    - SplitIng = Disable
    - VPN-id = com.microsoft.scmx
    - I nøgleværdiparrene skal du indtaste nøglen **AutoOnboard** og angive værdien til **Sand**.
    - Type af automatisk VPN = On-demand VPN
    - Klik **på Tilføj** **regler efter behov,** og vælg Jeg vil gøre følgende **= Opret VPN**, **jeg vil begrænse til = Alle domæner**.

    :::image type="content" source="images/ios-deploy-8.png" alt-text="Fanen Konfiguration af VPN-profil" lightbox="images/ios-deploy-8.png":::

1. Klik på Næste, og tildel profilen til målrettede brugere.
1. I sektionen *Gennemse + Opret skal* du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview"></a>Onboarding med nulto touch af Microsoft Defender for Endpoint (prøveversion)

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

> [!NOTE]
> Nul-touch kan ikke konfigureres på iOS-enheder, der er tilmeldt uden brugeraffinitet (enheder med mindre bruger eller delte enheder).

Administratorer kan konfigurere Microsoft Defender for Endpoint at installere og aktivere uovervåget. I dette flow opretter administratoren en installationsprofil, og brugeren underrettes blot om installationen. Defender til Slutpunkt installeres automatisk, uden at brugeren behøver at åbne appen. Følg trinnene nedenfor for at konfigurere installation af Defender til slutpunkt på tilmeldte iOS-enheder uden berøring eller automatisk installation:

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **EnhedskonfigurationsprofilerOprette** >  >  **profil**.
1. Vælg **Platform** som **iOS/iPadOS** og **Profiltype** som **VPN**. Vælg **Opret**.
1. Skriv et navn til profilen, og vælg **Næste**.
1. Vælg **Custom VPN** for Connection Type, og i **sektionen Base VPN** skal du skrive følgende:
    - Forbindelsesnavn = Microsoft Defender for Endpoint
    - VPN-serveradresse = 127.0.0.1
    - Godkendelsesmetode = "Brugernavn og adgangskode"
    - SplitIng = Disable
    - VPN-id = com.microsoft.scmx
    - I parrene med nøgleværdier skal du indtaste **nøglen SilentOnboard** og angive værdien til **Sand**.
    - Type af automatisk VPN = On-demand VPN
    - Vælg **Add** for **On Demand Rules,** og vælg **I want to do the following = Establish VPN**, **I want to restrict to = All domains**.

    :::image type="content" source="images/ios-deploy-9.png" alt-text="Siden Konfiguration af VPN-profil" lightbox="images/ios-deploy-9.png":::

1. Vælg **Næste** , og tildel profilen til målrettede brugere.
1. I sektionen *Gennemse + Opret skal* du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**.

Når ovenstående konfiguration er udført og synkroniseret med enheden, udføres følgende handlinger på de(e) målrettede iOS-enheder:
    - Microsoft Defender for Endpoint installeres og automatisk onboardes, og enheden kan ses i Defender for Endpoint-portalen.
    - Der sendes en meddelelse om beskeden om brugeren til brugerenheden.
    - Webbeskyttelse og andre funktioner aktiveres.

   > [!NOTE]
   > For overvågede enheder, selvom en VPN-profil ikke er påkrævet, kan administratorer stadig konfigurere Zero-touch onboarding ved at konfigurere VPN-profilen for Defender til Slutpunkt via Intune. VPN-profilen installeres på enheden, men vil kun være til stede på enheden som en pass-through-profil og kan slettes efter den indledende onboarding.

## <a name="complete-onboarding-and-check-status"></a>Fuldfør onboarding, og kontrollér status

1. Når Defender til Slutpunkt på iOS er blevet installeret på enheden, kan du se appikonet.

    :::image type="content" source="images/41627a709700c324849bf7e13510c516.png" alt-text="En beskrivelse af en smartphone genereres automatisk" lightbox="images/41627a709700c324849bf7e13510c516.png":::

2. Tryk på appikonet Defender for Endpoint (MSDefender), og følg instruktionerne på skærmen for at fuldføre onboardingtrinnene. Oplysningerne omfatter slutbrugeraccept af iOS-tilladelser, der kræves af Defender for Endpoint på iOS.

3. Når onboarding er gennemført, vises enheden på listen Enheder i Microsoft 365 Defender portal.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/device-inventory-screen.png" alt-text="Lagersiden for enhed" lightbox="images/device-inventory-screen.png":::

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>Konfigurere Microsoft Defender for Endpoint til overvåget tilstand

Data Microsoft Defender for Endpoint iOS-appen har særlige muligheder for at overvåge iOS/iPadOS-enheder under forudsætning af de øgede administrationsfunktioner, der leveres af platformen for disse typer enheder. For at udnytte disse funktioner skal Defender til Slutpunkt-appen vide, om en enhed er i overvåget tilstand.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurer overvåget tilstand via Intune

Intune gør det muligt at konfigurere Defender til iOS-appen via en App Configuration politik.

   > [!NOTE]
   > Denne politik for appkonfiguration til overvågede enheder gælder kun for administrerede enheder og skal målrettes for alle administrerede iOS-enheder som en bedste fremgangsmåde.

1. Log på administration Microsoft Endpoint Manager [, og gå til](https://go.microsoft.com/fwlink/?linkid=2109431) Politikker for konfiguration **af appsapps** \>  \> **Tilføj**. Klik på **Administrerede enheder**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-4.png" alt-text="Indstillingen Administrerede enheder" lightbox="images/ios-deploy-4.png":::

1. Angiv *følgende oplysninger på siden Opret* politik for appkonfiguration:
    - Politiknavn
    - Platform: Vælg iOS/iPadOS
    - Målrettet app: **Microsoft Defender for Endpoint** på listen

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-5.png" alt-text="De grundlæggende felter for konfigurationspolitikken for programmet" lightbox="images/ios-deploy-5.png":::

1. På næste skærmbillede skal du vælge **Brug konfigurationsdesigner** som format. Angiv følgende egenskab:
    - Konfigurationsnøgle: udstedt
    - Værditype: Streng
    - Konfigurationsværdi: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-6.png" alt-text="Den side, hvorfra du kan vælge formatet for indstillingerne for politikkonfigurationen" lightbox="images/ios-deploy-6.png":::

1. Klik **på Næste** for at åbne **siden Områdemærker** . Områdemærker er valgfri. Klik **på Næste** for at fortsætte.

1. På siden **Opgaver skal** du vælge de grupper, der skal modtage denne profil. I dette scenarie er det den bedste fremgangsmåde at målrette **alle enheder**. Du kan finde flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Når du installerer i brugergrupper, skal en bruger logge på en enhed, før politikken anvendes.

   Klik på **Næste**.

1. På siden **Gennemse + Opret** skal du vælge Opret, når du er **færdig**. Den nye profil vises på listen over konfigurationsprofiler.

## <a name="next-steps"></a>Næste trin

- [Konfigurer politik for appbeskyttelse til at medtage Defender til slutpunkt-risikosignaler (MAM)](ios-install-unmanaged.md)
- [Konfigurer Defender til Slutpunkt på iOS-funktioner](ios-configure-features.md)
