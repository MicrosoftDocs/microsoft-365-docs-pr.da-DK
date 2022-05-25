---
title: Appbaseret installation af Microsoft Defender for Endpoint på iOS
ms.reviewer: ''
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på iOS ved hjælp af en app
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, app, installation, installere, afinstallation, intune
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
ms.openlocfilehash: 4a81f125f9f32a5b4bdafd6d4656699fa17caa82
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669964"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>Udrul Microsoft Defender for Endpoint på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

I dette emne beskrives, hvordan du installerer Defender for Endpoint på iOS på Intune-firmaportal tilmeldte enheder. Du kan få flere oplysninger om Intune enhedsregistrering under [Tilmeld iOS-/iPadOS-enheder i Intune](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at du har adgang til [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

- Sørg for, at iOS-tilmelding er udført for dine brugere. Brugerne skal have tildelt en Licens til Defender for Endpoint for at kunne bruge Defender for Endpoint på iOS. Se [Tildel licenser til brugere for at](/azure/active-directory/users-groups-roles/licensing-groups-assign) få oplysninger om, hvordan du tildeler licenser.

> [!NOTE]
> Microsoft Defender for Endpoint på iOS er tilgængelig i [Apple App Store](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>Installationstrin

Installer Defender for Endpoint på iOS via Intune-firmaportal.

### <a name="add-ios-store-app"></a>Tilføj iOS Store-app

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Apps** -> **iOS/iPadOS** -> **Tilføj** -> **iOS Store-app** og klikke på **Vælg**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-1.png" alt-text="Fanen Tilføj programmer i Microsoft Endpoint Manager Administration Center" lightbox="images/ios-deploy-1.png":::

1. Klik på **Søg i App Store** på siden **Tilføj app**, og skriv **Microsoft Defender for Endpoint** i søgelinjen. Klik på *Microsoft Defender for Endpoint* i afsnittet søgeresultater, og klik på **Vælg**.

1. Vælg **iOS 11.0** som minimumoperativsystemet. Gennemse de øvrige oplysninger om appen, og klik på **Næste**.

1. I afsnittet **Tildelinger** skal du gå til sektionen **Påkrævet** og vælge **Tilføj gruppe**. Du kan derefter vælge den eller de brugergrupper, du vil målrette mod Defender for Endpoint på iOS-appen. Klik på **Vælg** og derefter **på Næste**.

    > [!NOTE]
    > Den valgte brugergruppe skal bestå af Intune tilmeldte brugere.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-2.png" alt-text="Fanen Tilføj gruppe i Microsoft Endpoint Manager Administration Center" lightbox="images/ios-deploy-2.png":::

1. I afsnittet *Gennemse + Opret* skal du kontrollere, at alle de angivne oplysninger er korrekte, og derefter vælge **Opret**. Om et øjeblik skal Defender for Endpoint-appen oprettes, og der vises en meddelelse i øverste højre hjørne af siden.

1. På den side med appoplysninger, der vises, skal du i afsnittet **Overvåg** vælge **Status for enhedsinstallation** for at kontrollere, at enhedsinstallationen er fuldført.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-3.png" alt-text="Statussiden for enhedsinstallation" lightbox="images/ios-deploy-3.png":::

## <a name="complete-deployment-for-supervised-devices"></a>Fuldfør udrulning for overvågede enheder

Microsoft Defender for Endpoint på iOS-appen har specialiseret sig i overvågede iOS-/iPadOS-enheder på grund af de øgede administrationsfunktioner, der leveres af platformen på disse typer enheder. Den kan også levere webbeskyttelse **uden at konfigurere en lokal VPN-forbindelse på enheden**. Dette giver slutbrugerne en problemfri oplevelse, mens de stadig er beskyttet mod phishing og andre webbaserede angreb.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurer overvåget tilstand via Intune

Konfigurer derefter overvåget tilstand for Defender for Endpoint-app via en App Configuration politik.

   > [!NOTE]
   > Denne appkonfigurationspolitik for overvågede enheder gælder kun for administrerede enheder og bør målrettes til ALLE administrerede iOS-enheder som bedste praksis.

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **Apps** \> **Appkonfigurationspolitikker** \> **Tilføj**. Vælg **Administrerede enheder**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager Administration Center4.](images/ios-deploy-4.png)

1. På siden *Opret appkonfigurationspolitik* skal du angive følgende oplysninger:
    - Politiknavn
    - Platform: Vælg iOS/iPadOS
    - Målrettet app: Vælg **Microsoft Defender for Endpoint** på listen

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager Administration Center5.](images/ios-deploy-5.png)

1. På det næste skærmbillede skal du vælge **Brug konfigurationsdesigner** som format. Angiv følgende egenskab:
    - Konfigurationsnøgle: issupervised
    - Værditype: Streng
    - Konfigurationsværdi: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager Administration Center6.](images/ios-deploy-6.png)

1. Vælg **Næste** for at åbne siden **Områdekoder** . Områdekoder er valgfri. Vælg **Næste** for at fortsætte.

1. På siden **Tildelinger** skal du vælge de grupper, der skal modtage denne profil. I dette scenarie er det bedste praksis at målrette alle **enheder**. Du kan få flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Når der udrulles til brugergrupper, skal en bruger logge på en enhed, før politikken gælder.

   Klik på **Næste**.

1. På siden **Gennemse + opret** skal du vælge **Opret**, når du er færdig. Den nye profil vises på listen over konfigurationsprofiler.

1. Derefter skal du installere en brugerdefineret profil på overvågede iOS-enheder. Dette er til forbedrede funktioner til anti-phishing. Følg nedenstående trin:

    - Download konfigurationsprofilen fra [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - Gå til **Enheder** -> **iOS/iPadOS-konfigurationsprofiler** ->  -> **Opret profil**

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager Administration Center7.](images/ios-deploy-7.png)
    
    - Angiv et navn på profilen. Når du bliver bedt om at importere en konfigurationsprofilfil, skal du vælge den fil, der er downloadet fra det forrige trin.
    - I afsnittet **Tildeling** skal du vælge den enhedsgruppe, du vil anvende denne profil på. Dette bør som bedste praksis anvendes på alle administrerede iOS-enheder. Vælg **Næste**.
    - På siden **Gennemse + opret** skal du vælge **Opret**, når du er færdig. Den nye profil vises på listen over konfigurationsprofiler.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>Automatisk onboarding af VPN-profil (forenklet onboarding)

For enheder, der ikke er overvåget, bruges der en VPN-forbindelse til at levere funktionen Webbeskyttelse. Dette er ikke en almindelig VPN- og er en lokal/selv-løkke-VPN, der ikke tager trafik uden for enheden.

>[!NOTE]
>For overvågede enheder kræves der ikke VPN til webbeskyttelsesfunktioner, og administratorer skal konfigurere en konfigurationsprofil på overvågede enheder. Hvis du vil konfigurere for overvågede enheder, skal du følge trinnene i afsnittet [Fuldfør udrulning for overvågede enheder](#complete-deployment-for-supervised-devices) .

Administratorer kan konfigurere automatisk konfiguration af VPN-profilen. Dette konfigurerer automatisk Defender for Endpoint VPN-profilen, uden at brugeren skal gøre det under onboarding. 

Dette trin forenkler onboardingprocessen ved at konfigurere VPN-profilen. Hvis du vil have en oplevelse uden berøring eller lydløs onboarding, skal du se næste afsnit: [Zero-touch onboard](#zero-touch-onboarding-of-microsoft-defender-for-endpoint).

1. I [Administration af Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Enhedskonfigurationsprofiler** ->  ->  **Opret profil**.
1. Vælg **Platform** som **iOS/iPadOS** og **Profiltype** som **VPN**. Klik på **Opret**.
1. Skriv et navn til profilen, og klik på **Næste**.
1. Vælg **Brugerdefineret VPN** som forbindelsestype, og angiv følgende i afsnittet **Basis-VPN** :
    - Forbindelsesnavn = Microsoft Defender for Endpoint
    - VPN-serveradresse = 127.0.0.1
    - Auth-metode = "Brugernavn og adgangskode"
    - Opdel tunnelføring = Deaktiver
    - VPN-id = com.microsoft.scmx
    - I nøgleværdipar skal du angive nøglen **AutoOnboard** og angive værdien til **Sand**.
    - Type af automatisk VPN = On-demand VPN
    - Vælg **Tilføj** for **Regler efter behov,** og vælg **Jeg vil gøre følgende = Forbind VPN**, **jeg vil begrænse til = Alle domæner**.

    :::image type="content" source="images/ios-deploy-8.png" alt-text="Fanen Konfigurationsindstillinger for VPN-profil" lightbox="images/ios-deploy-8.png":::

1. Klik på Næste, og tildel profilen til målrettede brugere.
1. I afsnittet *Gennemse + Opret* skal du kontrollere, at alle de angivne oplysninger er korrekte, og derefter vælge **Opret**.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint"></a>Onboarding uden berøring af Microsoft Defender for Endpoint



> [!NOTE]
> Zero-touch kan ikke konfigureres på iOS-enheder, der er tilmeldt uden brugertilhør (brugerfri enheder eller delte enheder).

Administratorer kan konfigurere Microsoft Defender for Endpoint til at installere og aktivere uovervåget. I dette flow opretter administratoren en installationsprofil, og brugeren får ganske enkelt besked om installationen. Defender for Endpoint installeres automatisk, uden at brugeren skal åbne appen. Følg nedenstående trin for at konfigurere zero-touch eller uovervåget installation af Defender for Endpoint på tilmeldte iOS-enheder:

1. I [Administration af Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Enhedskonfigurationsprofiler** >  >  **Opret profil**.
1. Vælg **Platform** som **iOS/iPadOS** og **Profiltype** som **VPN**. Vælg **Opret**.
1. Skriv et navn til profilen, og vælg **Næste**.
1. Vælg **Brugerdefineret VPN** som forbindelsestype, og angiv følgende i afsnittet **Basis-VPN** :
    - Forbindelsesnavn = Microsoft Defender for Endpoint
    - VPN-serveradresse = 127.0.0.1
    - Auth-metode = "Brugernavn og adgangskode"
    - Opdel tunnelføring = Deaktiver
    - VPN-id = com.microsoft.scmx
    - I nøgleværdipar skal du angive nøglen **SilentOnboard** og angive værdien til **True**.
    - Type af automatisk VPN = On-demand VPN
    - Vælg **Tilføj** for **Regler efter behov,** og vælg **Jeg vil gøre følgende = Forbind VPN**, **jeg vil begrænse til = Alle domæner**.

    :::image type="content" source="images/ios-deploy-9.png" alt-text="Siden Konfiguration af VPN-profil" lightbox="images/ios-deploy-9.png":::

1. Vælg **Næste** , og tildel profilen til målrettede brugere.
1. I afsnittet *Gennemse + Opret* skal du kontrollere, at alle de angivne oplysninger er korrekte, og derefter vælge **Opret**.

Når ovenstående konfiguration er fuldført og synkroniseret med enheden, udføres følgende handlinger på de målrettede iOS-enheder:
    - Microsoft Defender for Endpoint installeres og onboardes uovervåget, og enheden kan ses på Defender for Endpoint-portalen.
    - Der sendes en foreløbig meddelelse til brugerenheden.
    - Webbeskyttelse og andre funktioner aktiveres.

   > [!NOTE]
   > Selvom der ikke kræves en VPN-profil for overvågede enheder, kan administratorer stadig konfigurere onboarding uden berøring ved at konfigurere Defender for Endpoint VPN-profilen via Intune. VPN-profilen installeres på enheden, men vil kun være til stede på enheden som en pass-through-profil og kan slettes efter den indledende onboarding.

## <a name="complete-onboarding-and-check-status"></a>Fuldfør onboarding, og kontrollér status

1. Når Defender for Endpoint på iOS er installeret på enheden, får du vist appikonet.

    :::image type="content" source="images/41627a709700c324849bf7e13510c516.png" alt-text="Der genereres automatisk en beskrivelse af en smartphone" lightbox="images/41627a709700c324849bf7e13510c516.png":::

2. Tryk på ikonet for Appen Defender for Endpoint (MSDefender), og følg vejledningen på skærmen for at fuldføre onboardingtrinnene. Oplysningerne omfatter slutbrugeraccept af iOS-tilladelser, der kræves af Defender for Endpoint på iOS.

3. Ved vellykket onboarding vises enheden på listen Enheder på Microsoft 365 Defender-portalen.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/device-inventory-screen.png" alt-text="Siden Enhedslager" lightbox="images/device-inventory-screen.png":::

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>Konfigurer Microsoft Defender for Endpoint til overvåget tilstand

Microsoft Defender for Endpoint på iOS-appen har specialiseret sig i overvågede iOS-/iPadOS-enheder på grund af de øgede administrationsfunktioner, der leveres af platformen på disse typer enheder. Hvis du vil udnytte disse funktioner, skal Defender for Endpoint-appen vide, om en enhed er i overvåget tilstand.

### <a name="configure-supervised-mode-via-intune"></a>Konfigurer overvåget tilstand via Intune

Intune giver dig mulighed for at konfigurere Defender til iOS-appen via en App Configuration politik.

   > [!NOTE]
   > Denne appkonfigurationspolitik for overvågede enheder gælder kun for administrerede enheder og bør målrettes til alle administrerede iOS-enheder som bedste praksis.

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **Apps** \> **Appkonfigurationspolitikker** \> **Tilføj**. Klik på **Administrerede enheder**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-4.png" alt-text="Indstillingen Administrerede enheder" lightbox="images/ios-deploy-4.png":::

1. På siden *Opret appkonfigurationspolitik* skal du angive følgende oplysninger:
    - Politiknavn
    - Platform: Vælg iOS/iPadOS
    - Målrettet app: Vælg **Microsoft Defender for Endpoint** på listen

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-5.png" alt-text="De grundlæggende felter for konfigurationspolitikken for programmet" lightbox="images/ios-deploy-5.png":::

1. På det næste skærmbillede skal du vælge **Brug konfigurationsdesigner** som format. Angiv følgende egenskab:
    - Konfigurationsnøgle: issupervised
    - Værditype: Streng
    - Konfigurationsværdi: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-6.png" alt-text="Den side, hvorfra du kan vælge formatet for indstillingerne for politikkonfigurationen" lightbox="images/ios-deploy-6.png":::

1. Klik på **Næste** for at åbne siden **Områdekoder** . Områdekoder er valgfri. Klik på **Næste** for at fortsætte.

1. På siden **Tildelinger** skal du vælge de grupper, der skal modtage denne profil. I dette scenarie er det bedste praksis at målrette alle **enheder**. Du kan få flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Når der udrulles til brugergrupper, skal en bruger logge på en enhed, før politikken gælder.

   Klik på **Næste**.

1. På siden **Gennemse + opret** skal du vælge **Opret**, når du er færdig. Den nye profil vises på listen over konfigurationsprofiler.

## <a name="next-steps"></a>Næste trin

- [Konfigurer beskyttelsespolitikken for apps, så den omfatter Defender for Endpoint-risikosignaler (MAM)](ios-install-unmanaged.md)
- [Konfigurer Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
