---
title: Konfigurer Microsoft Defender for Endpoint i iOS-funktioner
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint i iOS-funktioner.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, configure, features, ios
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
ms.openlocfilehash: c52fac7c5680d8e5f814098410dc2e1993328d2f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476901"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>Konfigurer Microsoft Defender for Endpoint i iOS-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender til Slutpunkt på iOS ville bruge et VPN for at levere webbeskyttelsesfunktionen. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Betinget adgang med Defender til slutpunkt på iOS

Microsoft Defender for Endpoint på iOS sammen med Microsoft Intune og Azure Active Directory gør det muligt at håndhæve politikker for enhedsoverholdelse og Betinget adgang baseret på enhedens risikoscore. Defender til slutpunkt er en MTD-løsning (Mobile Threat Defense), som du kan implementere for at anvende denne funktion via Intune.

Du kan finde flere oplysninger om, hvordan du konfigurerer Betinget adgang med Defender til Slutpunkt på iOS, under [Defender for Endpoint og Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Registrering af jailbreak af Microsoft Defender for Endpoint

Microsoft Defender for Endpoint har mulighed for at registrere ikke-administrerede og administrerede enheder, der er jailbroken. Hvis en enhed registreres at være jailbroken, rapporteres en besked om høj risiko til **Microsoft 365 Defender-portalen**, og hvis Betinget adgang er konfigureret baseret på risikoscore for enheder, vil enheden blive blokeret fra at få adgang til virksomhedens data.

## <a name="web-protection-and-vpn"></a>Webbeskyttelse og VPN

Defender til Slutpunkt på iOS omfatter og aktiverer som standard funktionen til webbeskyttelse. [Webbeskyttelse hjælper](web-protection-overview.md) dig med at beskytte enheder mod webtrusler og beskytte brugere mod phishingangreb. Bemærk, at antiphishing og brugerdefinerede indikatorer (URL-adresser og IP-adresser) understøttes som en del af WebBeskyttelse. Filtrering af webindhold understøttes i øjeblikket ikke på iOS.

Defender til Slutpunkt på iOS bruger et VPN for at levere denne funktion. Bemærk, at dette er et lokalt VPN, og i modsætning til traditionelt VPN sendes netværkstrafik ikke uden for enheden.

Mens den er aktiveret som standard, kan der være nogle tilfælde, hvor du er nødt til at deaktivere VPN. For eksempel vil du køre nogle apps, der ikke fungerer, når et VPN er konfigureret. I sådanne tilfælde kan du vælge at deaktivere VPN fra appen på enheden ved at følge nedenstående trin:

1. På din iOS-enhed skal du åbne **Indstillinger**, klikke eller trykke **på Generelt** og derefter **VPN**.
1. Klik eller tryk på knappen "i" for at Microsoft Defender for Endpoint.
1. Slå VPN **fra Forbind On Demand for** at deaktivere VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Til/fra-knappen til VPN-konfigurationsindstillingen Forbind on-demand" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Webbeskyttelse er ikke tilgængelig, når VPN er deaktiveret. Hvis du vil genaktivere Web Protection, skal Microsoft Defender for Endpoint-appen på enheden og klikke eller trykke **på Start VPN**.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Sameksistens af flere VPN-profiler

Apple iOS understøtter ikke flere VPN for hele enheden for at være aktive samtidigt. Selvom flere VPN-profiler kan findes på enheden, kan kun ét VPN være aktivt ad gangen.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Konfigurer Microsoft Defender for Endpoint risikosignal i appbeskyttelsespolitik (MAM)

Microsoft Defender for Endpoint kan konfigureres til at sende trusselssignaler, der skal bruges i Politikker for appbeskyttelse (APP, også kaldet MAM) på iOS/iPadOS. Med denne funktion kan du også bruge Microsoft Defender for Endpoint til at beskytte adgang til virksomhedens data fra enheder, der ikke er tilmeldt.

Trin til konfiguration af politikker for appbeskyttelse med Microsoft Defender for Endpoint er som nedenfor:

1. Konfigurer forbindelsen fra din Microsoft Endpoint Manager til Microsoft Defender for Endpoint. I [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) Administration skal du gå til **Lejeradministrationsforbindelser**  \> og tokens \> **Microsoft Defender for Endpoint** (under På tværs af platforme) eller **Endpoint Security** \> **Microsoft Defender for Endpoint** (under Installation) og slå til/fra-knappen til under **Politik for beskyttelse af apps Indstillinger til iOS**.
1. Vælg Gem. Du bør få vist **Forbindelsesstatus** er nu angivet til **Aktiveret**.
1. Opret politik for beskyttelse af apps: Når konfigurationen af Microsoft Defender for Endpoint-forbindelsen er fuldført, skal du gå til **Apps** \> **Appbeskyttelse-politikker** (under Politik) for at oprette en ny politik eller opdatere en eksisterende.
1. Vælg de indstillinger for **platform, apps, databeskyttelse og adgangskrav** , din organisation kræver til din politik.
1. Under **Betingelser for betinget** \> **startenhed** finder du indstillingen **Maks. tilladt trusselsniveau for enheden**. Dette skal konfigureres til enten Lav, Mellem, Høj eller Sikret. De handlinger, der er tilgængelige for dig, **er Bloker adgang** **eller Slet data**. Du får muligvis vist en informationsdialogboks for at sikre, at forbindelsen er konfigureret, før denne indstilling træder i kraft. Hvis forbindelsen allerede er konfigureret, kan du ignorere denne dialogboks.
1. Afslut med Opgaver, og gem din politik.

Du kan finde flere oplysninger om MAM eller beskyttelsespolitik for apps [under Indstillinger for beskyttelsespolitik for iOS-apps](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Implementering af Microsoft Defender for Endpoint til MAM eller på enheder, der ikke er tilmeldt

Microsoft Defender for Endpoint på iOS aktiverer scenariet for appbeskyttelsespolitik og er tilgængelig i Apple App Store.

Slutbrugere skal installere den nyeste version af appen direkte fra Apple App Store.

## <a name="privacy-controls"></a>Kontrolelementer til beskyttelse af personlige oplysninger

> [!IMPORTANT]
> Kontrolelementer til beskyttelse af Microsoft Defender for Endpoint på iOS fås i forhåndsvisning. Følgende oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

### <a name="configure-privacy-in-phish-alert-report"></a>Konfigurere beskyttelse af personlige oplysninger i rapport over phish-besked

Kunder kan nu aktivere kontrol af beskyttelse af personlige oplysninger for den phish-rapport, der sendes Microsoft Defender for Endpoint i iOS. Dette sikrer, at domænenavnet ikke sendes som en del af phish-beskeden, når et phish-websted registreres og blokeres af Microsoft Defender for Endpoint.

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger og ikke indsamle domænenavnet som en del af rapporten om phish-besked.

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå **til Konfigurationspolitikker** **for** AppsAppAddManaged-enheder > . >  > 
1. Giv politikken et navn, **Platform > iOS/iPadOS**, vælg profiltypen.
1. Vælg **Microsoft Defender for Endpoint** destinationappen.
1. På Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeURLInReport** som nøgle- og værditype som **boolesk**
   - Hvis du vil aktivere beskyttelse af personlige oplysninger og ikke indsamle domænenavnet, skal du angive værdien som `true` og tildele denne politik til brugerne. Denne værdi er som standard angivet til `false`.
   - For brugere med tastesæt som `true`, indeholder phish-beskeden ikke oplysninger om domænenavnet, når et skadeligt websted registreres og blokeres af Defender til slutpunkt.
1. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrol af enhedsoverholdelse eller betinget adgang.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Konfigurer overholdelsespolitik for jailbroken-enheder

For at beskytte virksomhedens data mod adgang på jailbroken iOS-enheder anbefaler vi, at du konfigurerer følgende politik for overholdelse af regler og standarder Intune.

> [!NOTE]
> Registrering af jailbreak er en funktion, der leveres af Microsoft Defender for Endpoint på iOS. Vi anbefaler dog, at du konfigurerer denne politik som et ekstra lag af forsvar mod jailbreak-scenarier.

Følg trinnene nedenfor for at oprette en politik for overholdelse af regler og standarder mod jailbroken-enheder.

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **Politikker for overholdelse** ->  **af** **enhederOprette** ->  politik. Vælg "iOS/iPadOS" som platform, og klik på **Opret**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-policy.png" alt-text="Fanen Opret politik" lightbox="images/ios-jb-policy.png":::

2. Angiv et navn på politikken, f.eks. "Politik for overholdelse af regler og standarder for Jailbreak".
3. På siden med indstillinger for overholdelse af regler og standarder skal **du klikke for** at udvide sektionen Enhedstilstand og **klikke på Bloker** for **Jailbroken-enheder** .

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-settings.png" alt-text="Fanen Indstillinger for overholdelse af regler og standarder" lightbox="images/ios-jb-settings.png":::

4. I sektionen **Handlinger for manglende overholdelse skal** du vælge handlingerne i henhold til dine krav og vælge **Næste**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-actions.png" alt-text="Fanen Handlinger for manglende overholdelse" lightbox="images/ios-jb-actions.png":::

5. I sektionen **Opgaver skal** du vælge de brugergrupper, du vil medtage for denne politik, og derefter vælge **Næste**.
6. I sektionen **Gennemse+Opret skal** du kontrollere, at alle indtastede oplysninger er korrekte og derefter vælge **Opret**.

## <a name="configure-custom-indicators"></a>Konfigurere brugerdefinerede indikatorer

Defender til Slutpunkt på iOS giver administratorer mulighed for også at konfigurere brugerdefinerede indikatorer på iOS-enheder. Du kan finde flere oplysninger om, hvordan du konfigurerer brugerdefinerede indikatorer, [under Administrere indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Defender til Slutpunkt på iOS understøtter kun oprettelse af brugerdefinerede indikatorer for IP-adresser og URL-adresser/domæner.

## <a name="configure-option-to-send-in-app-feedback"></a>Konfigurere indstillingen til at sende feedback i appen 

Kunder har nu mulighed for at konfigurere muligheden for at sende feedbackdata til Microsoft i Defender for Endpoint-appen. Feedbackdata hjælper Microsoft med at forbedre produkter og foretage fejlfinding af problemer.

> [!NOTE]
> For skykunder i det amerikanske offentlige er indsamling af feedback **som standard** deaktiveret. 

Brug følgende trin til at konfigurere indstillingen til at sende feedbackdata til Microsoft:

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå **til Konfigurationspolitikker** **for** AppsAppAddManaged-enheder > . >  > 
1. Giv politikken et navn, **Platform > iOS/iPadOS**, vælg profiltypen.
1. Vælg **Microsoft Defender for Endpoint** destinationappen.
1. På Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderSendFeedback** som nøglen og værditypen som **boolesk**
   - Hvis du vil fjerne slutbrugernes mulighed for at give feedback, skal du angive værdien som og `false` tildele denne politik til brugerne. Denne værdi er som standard angivet til `true`. For kunder inden for det amerikanske offentlige myndigheder er standardværdien angivet til "falsk".
   - For brugere `true`med tastesæt som , er der mulighed for at sende feedbackdata til Microsoft i appen (Menu > Hjælp & feedback > Send feedback til Microsoft)
1. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.


## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder udgives som pålidelige websteder for at få dine personlige eller økonomiske oplysninger. Gå til [siden Giv feedback om netværksbeskyttelse](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , hvis du vil rapportere et websted, der kunne være et phishingwebsted.
