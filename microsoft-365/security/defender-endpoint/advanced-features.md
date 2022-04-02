---
title: Konfigurer avancerede funktioner i Microsoft Defender for Endpoint
description: Aktivér avancerede funktioner som f.eks bloker filer i Microsoft Defender for Endpoint.
keywords: avancerede funktioner, indstillinger, bloker fil, automatisk undersøgelse, automatisk løsning, skype, microsoft defender for identity, Office 365, Azure Information Protection, intune
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
ms.openlocfilehash: 94e5b18ab1090f6fb76cb7734e90411b93b444e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465437"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Konfigurer avancerede funktioner i Defender til Slutpunkt

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Afhængigt af de Microsoft-sikkerhedsprodukter, du bruger, kan du have adgang til nogle avancerede funktioner, som du kan integrere Defender for Endpoint med.

## <a name="enable-advanced-features"></a>Aktivér avancerede funktioner

1. I **navigationsruden** skal du **vælge Indstillinger** \> Avancerede **slutpunkter-funktioner**\>.
2. Vælg den avancerede funktion, du vil konfigurere, og skift **mellem Til og** **Fra**.
3. Klik **på Gem indstillinger**.

Brug følgende avancerede funktioner til at blive bedre beskyttet mod potentielt skadelige filer og få bedre indsigt under sikkerhedsundersøgelse.

## <a name="automated-investigation"></a>Automatiseret undersøgelse

Slå denne funktion til for at drage fordel af funktionerne til automatisk undersøgelse og afhjælpning af tjenesten. Få mere at vide under [Automatiseret undersøgelse](automated-investigations.md).

## <a name="live-response"></a>Livesvar

> [!NOTE]
> Livesvar kræver **automatisk undersøgelse** for at være slået til, før du kan aktivere det i afsnittet avancerede indstillinger på Microsoft Defender for Endpoint-portalen.

Slå denne funktion til, så brugere med de relevante tilladelser kan starte en direkte svarsession på enheder.

Du kan finde flere oplysninger om rolletildelinger [i Oprette og administrere roller](user-roles.md).

## <a name="live-response-for-servers"></a>Live-svar til servere

Slå denne funktion til, så brugere med de relevante tilladelser kan starte en direkte svarsession på servere.

Du kan finde flere oplysninger om rolletildelinger [i Oprette og administrere roller](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Direkte svar usigneret scriptudførelse

Ved at aktivere denne funktion kan du køre usignerede scripts i en direkte svarsession.

## <a name="always-remediate-pua"></a>Afhjælpe altid PUA

Potentielt uønskede programmer (PUA) er en kategori af software, der kan få din computer til at køre langsomt, vise uventede reklamer eller i værst, installere anden software, som kan være uventet eller uønsket.

Slå denne funktion til, så potentielt uønskede programmer (PUA) afhjælpes på alle enheder i din lejer, også selvom PUA-beskyttelse ikke er konfigureret på enhederne. Denne aktivering af funktionen hjælper med at beskytte brugere mod utilsigtet at installere uønskede programmer på deres enhed. Når afhjælpning er slået fra, afhænger det af enhedskonfigurationen.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Begræns korrelation til inden for grupper af enheder med omfang

Denne konfiguration kan bruges til scenarier, hvor lokale SOC-handlinger kun vil begrænse korrelationer for påmindelser til enhedsgrupper, de har adgang til. Hvis du slår denne indstilling til, betragtes en hændelse, der består af beskeder om, at grupper på tværs af enheder ikke længere betragtes som en enkelt hændelse. Den lokale SOC kan derefter handle på hændelsen, fordi de har adgang til en af de involverede enhedsgrupper. Global SOC vil dog se flere forskellige hændelser efter enhedsgruppe i stedet for én hændelse. Vi anbefaler ikke, at du slår denne indstilling til, medmindre du gør det for at se fordelene ved korrelation mellem hændelser i hele organisationen.

> [!NOTE]
> Ændring af denne indstilling påvirker kun fremtidige korrelationer.

## <a name="enable-edr-in-block-mode"></a>Aktivér Slutpunktsregistrering og -svar i bloktilstand

Slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand beskytter mod skadelige artefakter, selv når Microsoft Defender Antivirus kører i passiv tilstand. Når denne indstilling er slået Slutpunktsregistrering og -svar bloktilstand, blokeres skadelige artefakter eller adfærd, der registreres på en enhed. Slutpunktsregistrering og -svar i bloktilstand fungerer i baggrunden for at afhjælpe skadelige artefakter, der registreres efter brud.

## <a name="autoresolve-remediated-alerts"></a>Autoopbevaring af løste beskeder

For lejere, der er oprettet på eller efter Windows 10, version 1809, konfigureres den automatiske undersøgelses- og afhjælpningsfunktion som standard til at løse beskeder, hvor status for automatiserede analyseresultat er "Ingen trusler fundet" eller "Afhjælpet". Hvis du ikke vil have besked løst automatisk, skal du deaktivere funktionen manuelt.

> [!TIP]
> For lejere, der er oprettet før den version, skal du manuelt slå denne funktion til på siden [Avancerede](https://security.microsoft.com//preferences2/integration) funktioner.

> [!NOTE]
>
> - Resultatet af den automatiske løsningshandling kan påvirke beregningen på risikoniveau for enheden, som er baseret på de aktive beskeder, der findes på en enhed.
> - Hvis en analytiker for sikkerhedshandlinger manuelt angiver status for en besked til "I gang" eller "Løst", overskriver funktionen til automatisk løsning den ikke.

## <a name="allow-or-block-file"></a>Tillad eller bloker fil

Blokering er kun tilgængelig, hvis din organisation opfylder disse krav:

- bruger Microsoft Defender Antivirus som den aktive antimalwareløsning, og
- Den skybaserede beskyttelsesfunktion er aktiveret

Denne funktion gør det muligt at blokere potentielt skadelige filer i dit netværk. Blokering af en fil vil forhindre den i at blive læst, skrevet eller udført på enheder i organisationen.

Sådan slår **du Tillad eller bloker** filer til:

1. I navigationsruden skal du **vælge Indstillinger** \> **Generelle avancerede funktioner** \>  \> **Tillad eller** \> **bloker fil**.

1. Skift mellem **Til og** **Fra**.
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Skærmbilledet Slutpunkter" lightbox="../../media/alloworblockfile.png":::

1. Vælg **Gem** indstillinger nederst på siden.

Når du har deaktiveret denne funktion, [kan du blokere](respond-file-alerts.md#allow-or-block-file) filer via **fanen Tilføj** indikator på en fils profilside.

## <a name="custom-network-indicators"></a>Brugerdefinerede netværksindikatorer

Hvis du slår denne funktion til, kan du oprette indikatorer for IP-adresser, domæner eller URL-adresser, som afgør, om de bliver tilladt eller blokeret baseret på din liste over brugerdefinerede indikatore.

For at bruge denne funktion skal enhederne køre Windows 10 version 1709 eller nyere eller Windows 11. De skal også have netværksbeskyttelse i blokeringstilstand og version 4.18.1906.3 eller nyere af antimalwareplatformen under [KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Få mere at vide under [Administrer indikatorer](manage-indicators.md).

> [!NOTE]
> Netværksbeskyttelse udnytter omdømmetjenester, der behandler anmodninger på placeringer, der kan være uden for den placering, du har valgt for din Defender til slutpunktsdata.

## <a name="tamper-protection"></a>Beskyttelse mod tæmmer
Under nogle typer cyberangreb forsøger dårlige angreb at deaktivere sikkerhedsfunktioner, f.eks. antivirusbeskyttelse, på dine computere. Dårlige venner, som f.eks. vil deaktivere dine sikkerhedsfunktioner for at få nemmere adgang til dine data, installere malware eller på anden måde udnytte dine data, identiteter og enheder.

Beskyttelse mod manipulation låser Microsoft Defender Antivirus og forhindrer dine sikkerhedsindstillinger i at blive ændret via apps og metoder.

Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus og skybaseret beskyttelse er aktiveret. Få mere at vide under [Brug næste generations teknologier i Microsoft Defender Antivirus gennem skybaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md).

Hold tæmmebeskyttelse slået til for at forhindre uønskede ændringer af din sikkerhedsløsning og dens vigtige funktioner.

## <a name="show-user-details"></a>Vis brugeroplysninger

Slå denne funktion til, så du kan se brugeroplysninger gemt i Azure Active Directory. Detaljer omfatter en brugers billede, navn, titel og afdelingsoplysninger, når du undersøger enheder af brugerkonti. Du kan finde oplysninger om brugerkontoen i følgende visninger:

- Dashboard for sikkerhedshandlinger
- Beskedkø
- Siden Enhedsoplysninger

Få mere at vide under [Undersøg en brugerkonto](investigate-user.md).

## <a name="skype-for-business-integration"></a>Skype for Business integration

Ved at aktivere Skype for Business integration får du mulighed for at kommunikere med brugere ved hjælp Skype for Business, mail eller telefon. Denne aktivering kan være praktisk, når du har brug for at kommunikere med brugeren og reducere risici.

> [!NOTE]
> Når en enhed isoleres fra netværket, er der en pop op-vindue, hvor du kan vælge at aktivere Outlook- og Skype-kommunikation, som tillader kommunikation til brugeren, mens de er koblet fra netværket. Denne indstilling gælder for Skype og Outlook, når enhederne er i isolationstilstand.

## <a name="microsoft-defender-for-identity-integration"></a>Microsoft Defender for Identity integration

Integration med Microsoft Defender for Identity giver dig mulighed for at pivote direkte ind i et andet Microsoft Identity-sikkerhedsprodukt. Microsoft Defender for Identity øger en undersøgelse med mere viden om en mistænkelig kompromitteret konto og relaterede ressourcer. Ved at aktivere denne funktion kan du forbedre den enhedsbaserede undersøgelsesfunktion ved at pivotere på tværs af netværket fra et identifikationspunkt.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Threat Intelligence-forbindelse

Denne funktion er kun tilgængelig, hvis du har et aktivt Office 365 E5 eller tilføjelsesprogrammet Threat Intelligence. Du kan finde flere oplysninger Office 365 Enterprise siden med E5-produkter.

Når du slår denne funktion til, vil du kunne inkorporere data fra Microsoft Defender for Office 365 til Microsoft 365 Defender for at udføre en omfattende sikkerhedsundersøgelse på tværs af Office 365 postkasser og Windows enheder.

> [!NOTE]
> Du skal have den relevante licens for at aktivere denne funktion.

Hvis du vil modtage kontekstafhængig enhedsintegration i Office 365 Threat Intelligence, skal du aktivere indstillingerne for Defender for Endpoint i dashboardet Security & Compliance. Du kan få mere at vide [under Trusselsundersøgelse og -svar](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft-trusselseksperter – Målrettede angrebsmeddelelser

Ud af de to Microsoft Threat Expert-komponenter er målrettet angrebsmeddelelse generelt tilgængelig. Eksperter-on-demand-funktionaliteten er stadig i forhåndsvisning. Du kan kun bruge eksperter-on-demand-funktionen, hvis du har anvendt til forhåndsvisning, og dit program er blevet godkendt. Du kan modtage beskeder om målrettede angreb fra Microsoft-trusselseksperter via dashboardet for påmindelser på din Defender for Endpoint-portal og via mail, hvis du konfigurerer det.

> [!NOTE]
> Funktionen Microsoft-trusselseksperter i Defender til slutpunkt er tilgængelig med en E5-licens til [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Hvis du aktiverer denne indstilling, videresendes Defender til Slutpunkt-signaler for Microsoft Defender for Cloud Apps give en dybere indsigt i brugen af skybaserede programmer. Videresendte data gemmes og behandles på samme placering som dine Defender til skyapps-data.

> [!NOTE]
> Denne funktion vil være tilgængelig med en E5-licens til [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) på enheder, der kører Windows 10, version 1709 (OS Build 16299.1085 med [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (OS Build 17134.704 med [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809  (OS-build 17763.379 med [KB4489899](https://support.microsoft.com/help/4489899)), nyere versioner Windows 10 versioner eller Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Aktivere Microsoft Defender for Endpoint integration fra Microsoft Defender for Identity portalen

Hvis du vil modtage kontekstafhængig enhedsintegration i Microsoft Defender for Identity, skal du også aktivere funktionen i Microsoft Defender for Identity portal.

1. Log på portalen [Microsoft Defender for Identity med](https://portal.atp.azure.com/) en global administrator- eller sikkerhedsadministratorrolle.

2. Klik **på Opret din forekomst**.

3. Slå indstillingen Integration til Til **, og** klik på **Gem**.

Når du har fuldført integrationstrinnene på begge portaler, vil du kunne se relevante beskeder på siden enhedsdetaljer eller brugeroplysninger.

## <a name="web-content-filtering"></a>Filtrering af webindhold

Bloker adgang til websteder, der indeholder uønsket indhold, og spor webaktivitet på tværs af alle domæner. Opret en politik for filtrering af webindhold for at angive, hvilke [kategorier af webindhold du vil blokere](https://security.microsoft.com/preferences2/web_content_filtering_policy). Sørg for, at du har netværksbeskyttelse i bloktilstand, når du installerer [Microsoft Defender for Endpoint grundlinje for sikkerhed](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-compliance-center"></a>Del slutpunktsbeskeder med Microsoft Compliance Center

Videresender sikkerhedsadvarsler om slutpunkter og deres status til Microsoft Compliance Center, så du kan forbedre politikker for insider-risikostyring med advarsler og afhjælpe interne risici, før de skader. Videresendte data behandles og gemmes på den samme placering som dine Office 365 data.

Når du har [konfigureret](/microsoft-365/compliance/insider-risk-management-settings#indicators) indikatorer for overtrædelse af sikkerhedspolitik i indstillingerne for insider-risikostyring, deles Defender for Endpoint-beskeder med Insider Risk Management for de relevante brugere.

## <a name="microsoft-intune-connection"></a>Microsoft Intune forbindelse

Defender til Slutpunkt kan integreres med Microsoft Intune [at](/intune/what-is-intune) [aktivere risikobaseret betinget adgang på enheden](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Når du [har aktiveret denne](configure-conditional-access.md) funktion, vil du kunne dele defender for endpoint-enhedsoplysninger med andre Intune forbedre håndhævelsen af politikken.

> [!IMPORTANT]
> Du skal aktivere integration på både Intune Defender for Endpoint for at bruge denne funktion. Du kan finde flere oplysninger om specifikke trin [i Konfigurer betinget adgang i Defender til slutpunkt](configure-conditional-access.md).

Denne funktion er kun tilgængelig, hvis du har følgende forudsætninger:

- En licenseret lejer til Enterprise Mobility + Security E3 og Windows E5 (eller Microsoft 365 Enterprise E5)
- Et aktivt Microsoft Intune med Intune-administrerede Windows enheder[, som Azure AD er forbundet med](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Politik for betinget adgang

Når du Intune integration, Intune automatisk en klassisk politik for betinget adgang (CA). Denne klassiske nøglecenterpolitik er en forudsætning for at kunne konfigurere statusrapporter til Intune. Den bør ikke slettes.

> [!NOTE]
> Den klassiske nøglecenterpolitik, der oprettes Intune, adskiller sig fra moderne politikker for [Betinget adgang](/azure/active-directory/conditional-access/overview/), som bruges til at konfigurere slutpunkter.

## <a name="device-discovery"></a>Enhedsregistrering

Hjælper dig med at finde ikke-administrerede enheder, der har forbindelse til virksomhedens netværk, uden behov for ekstra enheder eller besværlige procesændringer. Ved hjælp af onboardede enheder kan du finde ikke-administrerede enheder i dit netværk og vurdere sårbarheder og risici. Du kan få mere at vide under [Enhedsregistrering](device-discovery.md).

> [!NOTE]
> Du kan altid anvende filtre for at udelukke enheder, der ikke er administrerede, fra listen over enheders lager. Du kan også bruge kolonnen onboardingstatus på API-forespørgsler til at frafiltrere enheder, der ikke er administrerede.

## <a name="preview-features"></a>Visningsfunktioner

Få mere at vide om de nye funktioner i prøveversionen af Defender for Endpoint. Prøv kommende funktioner ved at slå forhåndsvisningsoplevelsen til.

Du har adgang til kommende funktioner, som du kan give feedback på for at forbedre den samlede oplevelse, før funktioner er alment tilgængelige.

## <a name="download-quarantined-files"></a>Download filer, der er sat i karantæne

Sikkerhedskopiere filer, der er sat i karantæne, på en sikker og kompatibel placering, så de kan downloades direkte fra karantæne. Knappen **Download fil** vil altid være tilgængelig på filsiden. Denne indstilling er som standard slået til. [Få mere at vide om krav](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>Relaterede emner

- [Opdater indstillinger for dataopbevaring](data-retention-settings.md)
- [Konfigurere beskeder](configure-email-notifications.md)
