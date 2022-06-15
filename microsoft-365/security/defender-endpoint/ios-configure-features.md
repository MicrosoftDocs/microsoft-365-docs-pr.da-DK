---
title: Konfigurer Microsoft Defender for Endpoint på iOS-funktioner
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på iOS-funktioner.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, konfigurer, funktioner, ios
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
ms.openlocfilehash: 8defbb5d1a72afd13110d3c76a4770e40ac1c469
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089253"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>Konfigurer Microsoft Defender for Endpoint på iOS-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender for Endpoint på iOS ville bruge en VPN-forbindelse til at levere webbeskyttelsesfunktionen. Dette er ikke en almindelig VPN- og er en lokal/selv-løkke-VPN, der ikke tager trafik uden for enheden.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>Betinget adgang med Defender for Endpoint på iOS

Microsoft Defender for Endpoint på iOS sammen med Microsoft Intune og Azure Active Directory gør det muligt at gennemtvinge enhedsoverholdelse og politikker for betinget adgang baseret på enhedens risikoscore. Defender for Endpoint er en MTD-løsning (Mobile Threat Defense), som du kan udrulle for at udnytte denne funktionalitet via Intune.

Du kan finde flere oplysninger om, hvordan du konfigurerer betinget adgang med Defender for Endpoint på iOS, under [Defender for Endpoint og Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Registrering af jailbreak af Microsoft Defender for Endpoint

Microsoft Defender for Endpoint har mulighed for at registrere ikke-administrerede og administrerede enheder, der er jailbroken. Hvis det registreres, at en enhed er jailbroken, rapporteres der en advarsel om **høj** risiko til Microsoft 365 Defender-portalen, og hvis Betinget adgang er konfigureret på baggrund af enhedens risikoscore, blokeres enheden fra at få adgang til firmadata.

## <a name="web-protection-and-vpn"></a>Webbeskyttelse og VPN

Som standard inkluderer og aktiverer Defender for Endpoint på iOS webbeskyttelsesfunktionen. [Webbeskyttelse](web-protection-overview.md) hjælper med at beskytte enheder mod webtrusler og beskytte brugerne mod phishingangreb. Bemærk, at anti-phishing og brugerdefinerede indikatorer (URL-adresser og IP-adresser) understøttes som en del af Web Protection. Filtrering af webindhold understøttes i øjeblikket ikke på iOS.

Defender for Endpoint på iOS bruger en VPN-forbindelse til at levere denne funktion. Bemærk, at dette er en lokal VPN, og i modsætning til traditionel VPN sendes netværkstrafik ikke uden for enheden.

Selvom indstillingen er aktiveret som standard, kan der være nogle tilfælde, der kræver, at du deaktiverer VPN. Du vil f.eks. køre nogle apps, der ikke fungerer, når en VPN er konfigureret. I sådanne tilfælde kan du vælge at deaktivere VPN fra appen på enheden ved at følge nedenstående trin:

1. Åbn appen **Indstillinger** på din iOS-enhed, klik eller tryk på **Generelt** og derefter **VPN**.

2. Klik eller tryk på knappen "i" for Microsoft Defender for Endpoint.

3. Slå **Forbind On Demand** fra for at deaktivere VPN. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="Til/fra-knappen for INDSTILLINGEN VPN-konfiguration Forbind efter behov" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Webbeskyttelse vil ikke være tilgængelig, når VPN er deaktiveret. Hvis du vil aktivere Web Protection igen, skal du åbne appen Microsoft Defender for Endpoint på enheden og klikke eller trykke på **Start VPN**.

## <a name="configure-network-protection"></a>Konfigurer netværksbeskyttelse
>[!NOTE] 
>Netværksbeskyttelse på Microsoft Defender for Endpoint er nu en offentlig prøveversion. Følgende oplysninger relaterer til en foreløbig udgivelse af produktet, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Netværksbeskyttelse i Microsoft Defender for slutpunkt er aktiveret som standard. Administratorer kan bruge følgende trin til at konfigurere MAM-understøttelse af Netværksbeskyttelse på iOS-enheder.

1. I Microsoft Endpoint Manager Administration skal du gå til Apps > konfigurationspolitikker for apps. Opret en ny appkonfigurationspolitik.
   :::image type="content" source="images/addiosconfig.png" alt-text="Tilføj konfigurationspolitik." lightbox="images/addiosconfig.png":::
   
2. Angiv et navn og en beskrivelse for entydigt at identificere politikken. Klik derefter på 'Vælg offentlige apps', og vælg 'Microsoft Defender' for Platform iOS/IPadOS :::image type="content" source="images/nameiosconfig.png" alt-text="Navngiv konfigurationen." lightbox="images/nameiosconfig.png":::
   
3. På Indstillinger side skal du tilføje 'DefenderNetworkProtectionEnable' som nøglen og værdien som 'false' for at deaktivere Network Protection. (Netværksbeskyttelse er aktiveret som standard) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Tilføj konfigurationsværdi." lightbox="images/addiosconfigvalue.png":::
   
4. I forbindelse med andre konfigurationer, der er relateret til Netværksbeskyttelse, skal du tilføje følgende nøgler og den relevante tilsvarende værdi.

    |Tast| Standard (true-enable, false-disable)|Beskrivelse|
    |---|---|---|
    |DefenderEndUserTrustFlowEnable| Falsk | Giv brugere tilladelse til at have tillid til netværk og certifikater|
    |DefenderNetworkProtectionAutoRemediation| Sandt |Denne indstilling bruges af it-administratoren til at aktivere eller deaktivere de afhjælpningsbeskeder, der sendes, når en bruger udfører afhjælpningsaktiviteter, f.eks. at skifte til et sikrere WIFI-adgangspunkter eller slette mistænkelige certifikater, der er registreret af Defender|
    |DefenderNetworkProtectionBeskyttelse af personlige oplysninger| Sandt |Denne indstilling administreres af it-administratoren for at aktivere eller deaktivere beskyttelse af personlige oplysninger i netværksbeskyttelse|
  
5. I afsnittet Tildelinger kan administratoren vælge grupper af brugere, der skal medtages og udelades fra politikken.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Tildel konfiguration." lightbox="images/assigniosconfig.png":::
   
6. Gennemse og opret konfigurationspolitikken.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Sam eksistens af flere VPN-profiler

Apple iOS understøtter ikke, at flere VPN'er for hele enheden er aktive samtidig. Selvom der kan være flere VPN-profiler på enheden, kan kun én VPN-forbindelse være aktiv ad gangen.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Konfigurer Microsoft Defender for Endpoint risikosignal i MAM (App Protection Policy)

Microsoft Defender for Endpoint kan konfigureres til at sende trusselssignaler, der skal bruges i App Protection Policies (APP, også kendt som MAM) på iOS/iPadOS. Med denne funktion kan du bruge Microsoft Defender for Endpoint til også at beskytte adgang til virksomhedsdata fra fra tilmeldte enheder.

Trinnene til konfiguration af politikker for appbeskyttelse med Microsoft Defender for Endpoint er nedenfor:

1. Konfigurer forbindelsen fra din Microsoft Endpoint Manager lejer til Microsoft Defender for Endpoint. I [Administration af Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Lejeradministrationsconnectors** \> **og tokens** \> **Microsoft Defender for Endpoint** (under Sikkerhed på tværs af platforme) eller **Slutpunktssikkerhed** \> **Microsoft Defender for Endpoint** (under Konfiguration) og slå til/fra-knappen under **Beskyttelsespolitik for apps Indstillinger til iOS**.

2. Vælg Gem. Du bør se **, at Forbindelsesstatus** nu er angivet til **Aktiveret**.

3. Opret beskyttelsespolitik for apps: Når konfigurationen af din Microsoft Defender for Endpoint connector er fuldført, skal du gå til **Apps** \> **Appbeskyttelse politikker** (under Politik) for at oprette en ny politik eller opdatere en eksisterende.

4. Vælg platformen, **Apps, Databeskyttelse, Adgangskravindstillinger** , som din organisation kræver til din politik.

5. Under **Betingelser for betinget start** \> **af enhed** finder du indstillingen **Maks. tilladte niveau for enhedstrusler**. Dette skal konfigureres til enten Low, Medium, High eller Secured. De handlinger, der er tilgængelige for dig, er **Bloker adgang** eller **Slet data**. Du får muligvis vist en dialogboks med oplysninger for at sikre, at din connector er konfigureret, før denne indstilling træder i kraft. Hvis din connector allerede er konfigureret, kan du ignorere denne dialogboks.

6. Afslut med Tildelinger, og gem politikken.

Du kan finde flere oplysninger om MAM- eller appbeskyttelsespolitik under [Indstillinger for beskyttelsespolitik for iOS-apps](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Udrulning af Microsoft Defender for Endpoint til MAM eller på ikke-tilmeldte enheder

Microsoft Defender for Endpoint på iOS aktiverer scenariet appbeskyttelsespolitik og er tilgængelig i Apple App Store. Slutbrugere skal installere den nyeste version af appen direkte fra Apple App Store.

## <a name="privacy-controls"></a>Kontrolelementer til beskyttelse af personlige oplysninger

> [!IMPORTANT]
> Kontrolelementer til beskyttelse af personlige oplysninger for Microsoft Defender for Endpoint på iOS fås som prøveversion. Følgende oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

### <a name="configure-privacy-in-phish-alert-report"></a>Konfigurer beskyttelse af personlige oplysninger i rapport over phish-beskeder

Kunder kan nu aktivere kontrol af beskyttelse af personlige oplysninger for den phishrapport, der sendes af Microsoft Defender for Endpoint på iOS. Dette vil sikre, at domænenavnet ikke sendes som en del af phish-beskeden, når et phish-websted registreres og blokeres af Microsoft Defender for Endpoint.

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger og ikke indsamle domænenavnet som en del af phish-beskedrapporten.

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **Apps** > **Appkonfigurationspolitikker** > **Tilføj** > **administrerede enheder**.

2. Giv politikken et navn, **Platform > iOS/iPadOS**, vælg profiltypen.

3. Vælg **Microsoft Defender for Endpoint** som destinationsapp.

4. På Indstillinger side skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeURLInReport** som nøgle- og værditype som **boolesk**.

   - Hvis du vil aktivere beskyttelse af personlige oplysninger og ikke indsamle domænenavnet, skal du angive værdien som `true` og tildele denne politik til brugerne. Denne værdi er som standard angivet til `false`.

   - For brugere med nøgle angivet som `true`indeholder phishbeskeden ikke oplysninger om domænenavne, hver gang der registreres og blokeres et skadeligt websted af Defender for Endpoint.

5. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrollen af enhedens overholdelse eller betinget adgang.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Konfigurer politik for overholdelse af regler og standarder for jailbrokenenheder

For at beskytte virksomhedens data mod at blive adgang til på jailbroken iOS-enheder anbefaler vi, at du konfigurerer følgende politik for overholdelse af angivne standarder på Intune.

> [!NOTE]
> Registrering af jailbreak er en funktion, der leveres af Microsoft Defender for Endpoint på iOS. Vi anbefaler dog, at du konfigurerer denne politik som et ekstra forsvarslag mod jailbreak-scenarier.

Følg nedenstående trin for at oprette en politik for overholdelse af angivne standarder for jailbrokenenheder.

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Politikker for overholdelse af angivne standarder** ->  for **enheder** -> **Opret politik**. Vælg "iOS/iPadOS" som platform, og klik på **Opret**.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="Fanen Opret politik" lightbox="images/ios-jb-policy.png":::

1. Angiv et navn på politikken, f.eks. "Politik for overholdelse af regler og standarder for jailbreak".

1. På siden med indstillinger for overholdelse skal du klikke for at udvide sektionen **Enhedstilstand** og klikke på feltet **Bloker** for **jailbrokenenheder** .

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Fanen Indstillinger for overholdelse" lightbox="images/ios-jb-settings.png":::

1. I afsnittet **Handlinger for manglende overholdelse** skal du vælge handlingerne i henhold til dine krav og vælge **Næste**.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Fanen Handlinger for manglende overholdelse" lightbox="images/ios-jb-actions.png":::

1. I afsnittet **Tildelinger** skal du vælge de brugergrupper, du vil medtage for denne politik, og derefter vælge **Næste**.

1. I afsnittet **Gennemse+Opret** skal du kontrollere, at alle de angivne oplysninger er korrekte, og derefter vælge **Opret**.

## <a name="configure-custom-indicators"></a>Konfigurer brugerdefinerede indikatorer

Defender for Endpoint på iOS giver administratorer mulighed for også at konfigurere brugerdefinerede indikatorer på iOS-enheder. Du kan få mere at vide om, hvordan du konfigurerer brugerdefinerede indikatorer, under [Administrer indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> Defender for Endpoint på iOS understøtter kun oprettelse af brugerdefinerede indikatorer for IP-adresser og URL-adresser/domæner.

## <a name="configure-option-to-send-in-app-feedback"></a>Konfigurer muligheden for at sende feedback i appen 

Kunder har nu mulighed for at konfigurere muligheden for at sende feedbackdata til Microsoft i Defender for Endpoint-appen. Feedbackdata hjælper Microsoft med at forbedre produkter og foretage fejlfinding af problemer.

> [!NOTE]
> For cloudkunder i US Government er indsamling af feedbackdata **deaktiveret** som standard. 

Brug følgende trin til at konfigurere indstillingen for at sende feedbackdata til Microsoft:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **Apps** > **Appkonfigurationspolitikker** > **Tilføj** > **administrerede enheder**.

1. Giv politikken et navn, **Platform > iOS/iPadOS**, vælg profiltypen.

1. Vælg **Microsoft Defender for Endpoint** som destinationsapp.

1. På Indstillinger side skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderSendFeedback** som nøgle- og værditypen som **boolesk**.
   
   - Hvis du vil fjerne slutbrugernes mulighed for at give feedback, skal du angive værdien som `false` og tildele denne politik til brugere. Denne værdi er som standard angivet til `true`. For US Government-kunder er standardværdien angivet til 'falsk'.
   
   - For brugere med nøglesæt som `true`er der mulighed for at sende feedbackdata til Microsoft i appen (Menu > Hjælp & Feedback > Send feedback til Microsoft)

1. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder repræsenterer pålidelige websteder med det formål at indhente dine personlige eller økonomiske oplysninger. Besøg siden [Giv feedback om netværksbeskyttelse](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , hvis du vil rapportere et websted, der kan være et phishingwebsted.
