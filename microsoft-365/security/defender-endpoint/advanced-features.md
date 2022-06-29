---
title: Konfigurer avancerede funktioner i Microsoft Defender for Endpoint
description: Aktivér avancerede funktioner, f.eks. bloker filer i Microsoft Defender for Endpoint.
keywords: avancerede funktioner, indstillinger, blokere fil, automatiseret undersøgelse, automatisk løsning, skype, microsoft defender for identity, office 365, azure information protection, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d9824a738468f14ebfc7cd7bdc3c612c21a0e43c
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493103"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Konfigurer avancerede funktioner i Defender for Endpoint

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Afhængigt af de Microsoft-sikkerhedsprodukter, du bruger, kan nogle avancerede funktioner være tilgængelige, så du kan integrere Defender for Endpoint med.

## <a name="enable-advanced-features"></a>Aktivér avancerede funktioner

1. Vælg **Indstillinger** \> **Slutpunkter** \> **Avancerede funktioner** i navigationsruden.
2. Vælg den avancerede funktion, du vil konfigurere, og skift mellem **Til** og **Fra**.
3. Klik på **Gem indstillinger**.

Brug følgende avancerede funktioner til at blive bedre beskyttet mod potentielt skadelige filer og få bedre indsigt under sikkerhedsundersøgelser.

## <a name="automated-investigation"></a>Automatiseret undersøgelse

Slå denne funktion til for at drage fordel af tjenestens automatiserede undersøgelses- og afhjælpningsfunktioner. Du kan få flere oplysninger under [Automatiseret undersøgelse](automated-investigations.md).

## <a name="live-response"></a>Live-svar

> [!NOTE]
> Direkte svar kræver **, at Automatiseret undersøgelse** er slået til, før du kan aktivere den i afsnittet avancerede indstillinger på Microsoft Defender for Endpoint-portalen.

Slå denne funktion til, så brugere med de relevante tilladelser kan starte en live-svarsession på enheder.

Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

## <a name="live-response-for-servers"></a>Live-svar til servere

Slå denne funktion til, så brugere med de relevante tilladelser kan starte en live-svarsession på servere.

Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Udførelse af direkte svar uden fortegn

Hvis du aktiverer denne funktion, kan du køre usignerede scripts i en live-svarsession.

## <a name="always-remediate-pua"></a>Afhjælp altid PUA

Potentielt uønskede programmer (PUA) er en kategori af software, der kan få din maskine til at køre langsomt, vise uventede annoncer eller i værste fald installere anden software, hvilket kan være uventet eller uønsket.

Slå denne funktion til, så potentielt uønskede programmer (PUA) afhjælpes på alle enheder i din lejer, selvom PUA-beskyttelse ikke er konfigureret på enhederne. Denne aktivering af funktionen hjælper med at beskytte brugerne mod utilsigtet installation af uønskede programmer på deres enhed. Når den er slået fra, afhænger afhjælpning af enhedskonfigurationen.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Begræns korrelation til inden for bestemte enhedsgrupper

Denne konfiguration kan bruges til scenarier, hvor lokale SOC-handlinger kun vil begrænse beskedkorrelationen til enhedsgrupper, som de har adgang til. Ved at aktivere denne indstilling vil en hændelse, der består af beskeder, som grupper på tværs af enheder ikke længere betragtes som en enkelt hændelse. Den lokale SOC kan derefter udføre handlinger på hændelsen, fordi de har adgang til en af de involverede enhedsgrupper. Global SOC kan dog se flere forskellige hændelser efter enhedsgruppe i stedet for én hændelse. Vi anbefaler ikke, at du aktiverer denne indstilling, medmindre det opvejer fordelene ved hændelseskorrelation på tværs af hele organisationen.

> [!NOTE]
> Ændring af denne indstilling påvirker kun fremtidige beskeders korrelation.

## <a name="enable-edr-in-block-mode"></a>Aktivér EDR i bloktilstand

EDR (Endpoint Detection and Response) i blokeringstilstand giver beskyttelse mod skadelige artefakter, selv når Microsoft Defender Antivirus kører i passiv tilstand. Når EDR er slået til, blokerer EDR i bloktilstand skadelige artefakter eller funktionsmåder, der registreres på en enhed. EDR i bloktilstand arbejder bag kulisserne for at afhjælpe skadelige artefakter, der registreres efter sikkerhedsbrud.

## <a name="autoresolve-remediated-alerts"></a>Automatisk løsningsbeskeder

For lejere, der er oprettet på eller efter Windows 10, version 1809, er den automatiserede undersøgelses- og afhjælpningsfunktion som standard konfigureret til at løse beskeder, hvor den automatiserede resultatstatus for analysen er "Der blev ikke fundet trusler" eller "Afhjælpning". Hvis du ikke vil have beskederne løst automatisk, skal du slå funktionen fra manuelt.

> [!TIP]
> For lejere, der er oprettet før denne version, skal du slå denne funktion til manuelt fra siden [Avancerede funktioner](https://security.microsoft.com//preferences2/integration) .

> [!NOTE]
>
> - Resultatet af handlingen til automatisk løsning kan påvirke beregningen af enhedens risikoniveau, som er baseret på de aktive beskeder, der findes på en enhed.
> - Hvis en sikkerhedsanalytiker manuelt angiver status for en besked til "I gang" eller "Løst", overskriver funktionen til automatisk løsning ikke den.

## <a name="allow-or-block-file"></a>Tillad eller bloker fil

Blokering er kun tilgængelig, hvis din organisation opfylder disse krav:

- Bruger Microsoft Defender Antivirus som den aktive antimalwareløsning, og
- Den skybaserede beskyttelsesfunktion er aktiveret

Denne funktion giver dig mulighed for at blokere potentielt skadelige filer på netværket. Blokering af en fil forhindrer den i at blive læst, skrevet eller udført på enheder i din organisation.

Sådan slår du **Tillad eller bloker** filer til:

1. I navigationsruden skal du vælge **Indstillinger** \> **Slutpunkter** \> **Generelle** \> **avancerede funktioner** \> **Tillad eller bloker fil**.

1. Slå **indstillingen til og** **fra.**
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Skærmbilledet Slutpunkter" lightbox="../../media/alloworblockfile.png":::

1. Vælg **Gem indstillinger** nederst på siden.

Når du har aktiveret denne funktion, kan du [blokere filer](respond-file-alerts.md#allow-or-block-file) via fanen **Tilføj indikator** på en fils profilside.

## <a name="custom-network-indicators"></a>Brugerdefinerede netværksindikatorer

Når du aktiverer denne funktion, kan du oprette indikatorer for IP-adresser, domæner eller URL-adresser, der bestemmer, om de er tilladt eller blokeret, baseret på din brugerdefinerede indikatorliste.

Hvis du vil bruge denne funktion, skal enheder køre Windows 10 version 1709 eller nyere eller Windows 11. De skal også have netværksbeskyttelse i bloktilstand og version 4.18.1906.3 eller nyere af antimalwareplatformen, se [KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Du kan få flere oplysninger under [Administrer indikatorer](manage-indicators.md).

> [!NOTE]
> Netværksbeskyttelse udnytter omdømmetjenester, der behandler anmodninger på placeringer, der kan være uden for den placering, du har valgt til dine Defender for Endpoint-data.

## <a name="tamper-protection"></a>Ændringsbeskyttelse
Under nogle former for cyberangreb forsøger dårlige aktører at deaktivere sikkerhedsfunktioner, f.eks. antivirusbeskyttelse, på dine maskiner. Dårlige aktører vil gerne deaktivere dine sikkerhedsfunktioner for at få lettere adgang til dine data, installere malware eller på anden måde udnytte dine data, identitet og enheder.

Manipulationsbeskyttelse låser i bund og grund Microsoft Defender Antivirus og forhindrer, at dine sikkerhedsindstillinger ændres via apps og metoder.

Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus, og cloudbaseret beskyttelse er aktiveret. Du kan finde flere oplysninger [under Brug næste generations teknologier i Microsoft Defender Antivirus via cloudbaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md).

Hold beskyttelse mod manipulation slået til for at forhindre uønskede ændringer af din sikkerhedsløsning og dens vigtige funktioner.

## <a name="show-user-details"></a>Vis brugeroplysninger

Aktivér denne funktion, så du kan se brugeroplysninger, der er gemt i Azure Active Directory. Oplysningerne omfatter oplysninger om en brugers billede, navn, titel og afdeling, når der undersøges brugerkontoobjekter. Du kan finde brugerkontooplysninger i følgende visninger:

- Dashboard til sikkerhedshandlinger
- Beskedkø
- Side med enhedsdetaljer

Du kan få flere oplysninger under [Undersøg en brugerkonto](investigate-user.md).

## <a name="skype-for-business-integration"></a>Skype for Business integration

Aktivering af Skype for Business integration giver dig mulighed for at kommunikere med brugere ved hjælp af Skype for Business, mail eller telefon. Denne aktivering kan være praktisk, når du har brug for at kommunikere med brugeren og afhjælpe risici.

> [!NOTE]
> Når en enhed isoleres fra netværket, er der et pop op-vindue, hvor du kan vælge at aktivere Outlook- og Skype-kommunikation, som tillader kommunikation til brugeren, mens brugeren ikke har forbindelse til netværket. Denne indstilling gælder for Skype- og Outlook-kommunikation, når enheder er i isolationstilstand.

## <a name="microsoft-defender-for-identity-integration"></a>Microsoft Defender for Identity integration

Integrationen med Microsoft Defender for Identity giver dig mulighed for at pivotere direkte til et andet Microsoft Identity-sikkerhedsprodukt. Microsoft Defender for Identity øger en undersøgelse med mere indsigt i en formodet kompromitteret konto og relaterede ressourcer. Når du aktiverer denne funktion, kan du forbedre den enhedsbaserede undersøgelsesfunktion ved at pivotere på tværs af netværket fra et identificerbart synspunkt.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Threat Intelligence-forbindelse

Denne funktion er kun tilgængelig, hvis du har en aktiv Office 365 E5 eller tilføjelsesprogrammet Threat Intelligence. Du kan få flere oplysninger på produktsiden Office 365 Enterprise E5.

Når du aktiverer denne funktion, kan du inkorporere data fra Microsoft Defender for Office 365 i Microsoft 365 Defender for at udføre en omfattende sikkerhedsundersøgelse på tværs af Office 365 postkasser og Windows-enheder.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

Hvis du vil modtage kontekstafhængig enhedsintegration i Office 365 Threat Intelligence, skal du aktivere indstillingerne for Defender for Endpoint på dashboardet Sikkerhed & Overholdelse. Du kan få flere oplysninger under [Trusselsundersøgelse og -svar](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft-trusselseksperter – målrettede angrebsmeddelelser

Ud af de to Microsoft Threat Expert-komponenter er meddelelsen om målrettede angreb offentligt tilgængelig. Eksperter efter behov-funktionalitet findes stadig som prøveversion. Du kan kun bruge funktionaliteten eksperter efter behov, hvis du har ansøgt om forhåndsvisning, og dit program er blevet godkendt. Du kan modtage målrettede angrebsmeddelelser fra Microsoft-trusselseksperter via beskeddashboardet for Defender for Endpoint-portalen og via mail, hvis du konfigurerer det.

> [!NOTE]
> Funktionen Microsoft-trusselseksperter i Defender for Endpoint er tilgængelig med en E5-licens til [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Hvis du aktiverer denne indstilling, videresendes Defender for Endpoint-signaler for at Microsoft Defender for Cloud Apps for at give en bedre indsigt i brugen af cloudprogrammer. Videresendte data gemmes og behandles på samme placering som dine Defender for Cloud Apps-data.

> [!NOTE]
> Denne funktion er tilgængelig med en E5-licens til [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) på enheder, der kører Windows 10, version 1709 (OS Build 16299.1085 med [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (OS Build 17134.704 med [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809  (OS Build 17763.379 med [KB4489899](https://support.microsoft.com/help/4489899)), nyere Windows 10 versioner eller Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Aktivér integration af Microsoft Defender for Endpoint fra Microsoft Defender for Identity-portalen

Hvis du vil modtage kontekstafhængig enhedsintegration i Microsoft Defender for Identity, skal du også aktivere funktionen på Microsoft Defender for Identity-portalen.

1. Log på [Microsoft Defender for Identity-portalen](https://portal.atp.azure.com/) med rollen Global administrator eller Sikkerhedsadministrator.

2. Klik på **Opret din forekomst**.

3. Slå indstillingen Integration til **Til** , og klik på **Gem**.

Når du har fuldført integrationstrinnene på begge portaler, kan du se relevante beskeder på siden med enhedsoplysninger eller brugeroplysninger.

## <a name="web-content-filtering"></a>Filtrering af webindhold

Bloker adgang til websteder, der indeholder uønsket indhold, og spor webaktivitet på tværs af alle domæner. Hvis du vil angive de webindholdskategorier, du vil blokere, skal du oprette en [politik for filtrering af webindhold](https://security.microsoft.com/preferences2/web_content_filtering_policy). Sørg for, at du har netværksbeskyttelse i blokeringstilstand, når [du installerer Microsoft Defender for Endpoint grundlæggende sikkerhedsindstilling](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-purview-compliance-portal"></a>Del slutpunktbeskeder med Microsoft Purview-compliance-portal

Videresender sikkerhedsbeskeder for slutpunkter og deres triagestatus til Microsoft Purview-compliance-portal, så du kan forbedre politikker for styring af insiderrisiko med beskeder og afhjælpe interne risici, før de forårsager skade. Videresendte data behandles og gemmes på samme placering som dine Office 365 data.

Når du har konfigureret [indikatorerne for overtrædelse af sikkerhedspolitik](/microsoft-365/compliance/insider-risk-management-settings#indicators) i indstillingerne for styring af insiderrisiko, deles Defender for Endpoint-beskeder med styring af insiderrisiko for relevante brugere.

## <a name="authenticated-telemetry"></a>Godkendt telemetri

Du kan **slå** godkendt telemetri til for at forhindre spoofing af telemetri i dit dashboard.

## <a name="microsoft-intune-connection"></a>Microsoft Intune forbindelse

Defender for Endpoint kan integreres med [Microsoft Intune](/intune/what-is-intune) for at [aktivere enhedsrisikobaseret betinget adgang](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Når du [aktiverer denne funktion](configure-conditional-access.md), kan du dele Defender for Endpoint-enhedsoplysninger med Intune, hvilket forbedrer håndhævelsen af politikker.

> [!IMPORTANT]
> Du skal aktivere integrationen på både Intune og Defender for Endpoint for at kunne bruge denne funktion. Du kan finde flere oplysninger om bestemte trin under [Konfigurer betinget adgang i Defender for Endpoint](configure-conditional-access.md).

Denne funktion er kun tilgængelig, hvis du har følgende forudsætninger:

- En licenseret lejer til Enterprise Mobility + Security E3 og Windows E5 (eller Microsoft 365 Enterprise E5)
- Et aktivt Microsoft Intune miljø, hvor Intune administrerede Windows-enheder [Azure AD tilsluttet](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Politik for betinget adgang

Når du aktiverer Intune integration, opretter Intune automatisk en klassisk ca-politik (Conditional Access). Denne klassiske nøglecenterpolitik er en forudsætning for at konfigurere statusrapporter til Intune. Den bør ikke slettes.

> [!NOTE]
> Den klassiske nøglecenterpolitik, der oprettes af Intune, adskiller sig fra moderne [politikker for betinget adgang](/azure/active-directory/conditional-access/overview/), som bruges til at konfigurere slutpunkter.

## <a name="device-discovery"></a>Enhedssøgning

Hjælper dig med at finde ikke-administrerede enheder, der er tilsluttet virksomhedens netværk, uden at der er behov for ekstra apparater eller besværlige procesændringer. Ved hjælp af onboardede enheder kan du finde ikke-administrerede enheder i dit netværk og vurdere sikkerhedsrisici og risici. Du kan finde flere oplysninger under [Enhedsregistrering](device-discovery.md).

> [!NOTE]
> Du kan altid anvende filtre for at udelade ikke-administrerede enheder fra enhedslagerlisten. Du kan også bruge kolonnen med onboardingstatus i API-forespørgsler til at filtrere ikke-administrerede enheder fra.

## <a name="preview-features"></a>Visningsfunktioner

Få mere at vide om nye funktioner i prøveversionen af Defender for Endpoint. Prøv kommende funktioner ved at aktivere prøveversionsoplevelsen.

Du har adgang til kommende funktioner, som du kan give feedback på for at hjælpe med at forbedre den overordnede oplevelse, før funktioner bliver offentligt tilgængelige.

## <a name="download-quarantined-files"></a>Download filer, der er sat i karantæne

Sikkerhedskopiér filer, der er sat i karantæne, på en sikker og kompatibel placering, så de kan downloades direkte fra karantæne. Knappen **Download fil** vil altid være tilgængelig på filsiden. Denne indstilling er som standard slået til. [Få mere at vide om krav](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>Relaterede emner

- [Opdater indstillinger for dataopbevaring](data-retention-settings.md)
- [Konfigurer beskedmeddelelser](configure-email-notifications.md)
