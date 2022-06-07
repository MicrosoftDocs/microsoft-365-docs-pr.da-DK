---
title: Enhedsprofil i Microsoft 365-sikkerhedsportal
description: Få vist risiko- og eksponeringsniveauer for en enhed i din organisation. Analysér tidligere og nuværende trusler, og beskyt enheden med de nyeste opdateringer.
keywords: sikkerhed, malware, Microsoft 365, M365, Microsoft 365 Defender, sikkerhedscenter, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity, enhedsside, enhedsprofil, computerside, maskinprofil
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: dansimp
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 962ec0c5ed6b7d6934678678be9a57ebcbaabc55
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923428"
---
# <a name="device-profile-page"></a>Enhedsprofilside

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Microsoft 365-sikkerhedsportalen giver dig enhedsprofilsider, så du hurtigt kan vurdere tilstanden og status for enheder på netværket.

> [!IMPORTANT]
> Enhedens profilside kan se lidt anderledes ud, afhængigt af om enheden er tilmeldt Microsoft Defender for Endpoint, Microsoft Defender for Identity eller begge dele.

Hvis enheden er tilmeldt Microsoft Defender for Endpoint, kan du også bruge enhedens profilside til at udføre nogle almindelige sikkerhedsopgaver.

## <a name="navigating-the-device-profile-page"></a>Navigering på enhedens profilside

Profilsiden er opdelt i flere brede afsnit.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="Profilsiden Enhed på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

Margenteksten (1) viser de grundlæggende oplysninger om enheden.

Hovedindholdsområdet (2) indeholder faner, som du kan skifte mellem for at få vist forskellige typer oplysninger om enheden.

Hvis enheden er tilmeldt Microsoft Defender for Endpoint, får du også vist en liste over svarhandlinger (3). Svarhandlinger giver dig mulighed for at udføre almindelige sikkerhedsrelaterede opgaver.

## <a name="sidebar"></a>Side

Ud for hovedindholdsområdet på enhedens profilside er margenteksten.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="Fanen Margentekst for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

Margenteksten viser enhedens fulde navn og eksponeringsniveau. Den indeholder også nogle vigtige grundlæggende oplysninger i små undersektioner, som kan slås til eller fra, f.eks.:

* **Tags** – alle Microsoft Defender for Endpoint, Microsoft Defender for Identity eller brugerdefinerede mærker, der er knyttet til enheden. Mærker fra Microsoft Defender for Identity kan ikke redigeres.
* **Sikkerhedsoplysninger** – åbne hændelser og aktive beskeder. Enheder, der er tilmeldt Microsoft Defender for Endpoint, viser også eksponeringsniveau og risikoniveau.

> [!TIP]
> Eksponeringsniveauet er relateret til, hvor meget enheden overholder sikkerhedsanbefalinger, mens risikoniveauet beregnes på baggrund af en række faktorer, herunder typerne og alvorsgraden af aktive beskeder.

* **Enhedsdetaljer** – Domæne, OPERATIVSYSTEM, tidsstempel for, hvornår enheden blev set første gang, IP-adresser og ressourcer. Enheder, der er tilmeldt Microsoft Defender for Endpoint, viser også tilstandstilstand. Enheder, der er tilmeldt Microsoft Defender for Identity, viser SAM-navn og et tidsstempel for, hvornår enheden første gang blev oprettet.
* **Netværksaktivitet** – Tidsstempler for første gang og sidste gang, enheden blev set på netværket.
* **Mappedata** (*kun for enheder, der er tilmeldt Microsoft Defender for Identity*) – [UAC-flag](/windows/security/identity-protection/user-account-control/user-account-control-overview) , [SPN'er](/windows/win32/ad/service-principal-names) og gruppemedlemskaber.

## <a name="response-actions"></a>Svarhandlinger

Svarhandlinger giver en hurtig måde at forsvare sig mod og analysere trusler på.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="Handlingslinjen for enhedsprofilen på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * [Svarhandlinger](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) er kun tilgængelige, hvis enheden er tilmeldt Microsoft Defender for Endpoint.
> * Enheder, der er tilmeldt Microsoft Defender for Endpoint, kan vise forskellige antal svarhandlinger baseret på enhedens operativsystem og versionsnummer.

Handlinger, der er tilgængelige på enhedens profilside, omfatter:

* **Administrer mærker** – opdaterer brugerdefinerede mærker, du har anvendt på denne enhed.
* **Isoler enhed** – Isolerer enheden fra organisationens netværk, samtidig med at den har forbindelse til Microsoft Defender for Endpoint. Du kan vælge at tillade, at Outlook, Teams og Skype for Business kører, mens enheden er isoleret, til kommunikationsformål.
* **Løsningscenter** – få vist status for sendte handlinger. Kun tilgængelig, hvis der allerede er valgt en anden handling.
* **Begræns udførelse af apps** – Forhindrer, at programmer, der ikke er signeret af Microsoft, kører.
* **Kør antivirusscanning** – opdaterer Windows Defender Antivirus-definitioner og kører straks en antivirusscanning. Vælg mellem Hurtig scanning eller Fuld scanning.
* **Indsaml undersøgelsespakke** – indsamler oplysninger om enheden. Når undersøgelsen er fuldført, kan du downloade den.
* **Start live-svarsession** – Indlæser en ekstern shell på enheden til [dybdegående sikkerhedsundersøgelser](/microsoft-365/security/defender-endpoint/live-response).
* **Start en automatiseret undersøgelse** – [undersøger og afhjælper automatisk trusler](../office-365-security/office-365-air.md). Selvom du manuelt kan udløse automatiserede undersøgelser, så de kan køre fra denne side, udløser [visse beskedpolitikker](../../compliance/alert-policies.md#default-alert-policies) automatisk undersøgelser på egen hånd.
* **Løsningscenter** – viser oplysninger om eventuelle svarhandlinger, der kører i øjeblikket.

## <a name="tabs-section"></a>Fanesektion

Under fanerne for enhedsprofilen kan du skifte mellem en oversigt over sikkerhedsoplysninger om enheden og tabeller, der indeholder en liste over beskeder.

De enheder, der er tilmeldt Microsoft Defender for Endpoint, viser også faner, der indeholder en tidslinje, en liste over sikkerhedsanbefalinger, en softwareoversigt, en liste over registrerede sikkerhedsrisici og manglende KB (sikkerhedsopdateringer).

### <a name="overview-tab"></a>Fanen Oversigt

Standardfanen er **Oversigt**. Det giver et hurtigt kig på den vigtigste sikkerheds kendsgerning om enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="Fanen Oversigt for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

Her kan du få et hurtigt kig på enhedens aktive beskeder og eventuelle brugere, der i øjeblikket er logget på.

Hvis enheden er tilmeldt Microsoft Defender for Endpoint, kan du også se enhedens risikoniveau og eventuelle tilgængelige data om sikkerhedsvurderinger. Sikkerhedsvurderingerne beskriver enhedens eksponeringsniveau, giver sikkerhedsanbefalinger og viser påvirket software og registrerede sikkerhedsrisici.

### <a name="alerts-tab"></a>Fanen Beskeder

Fanen **Beskeder** indeholder en liste over beskeder, der er blevet udløst på enheden, fra både Microsoft Defender for Identity og Microsoft Defender for Endpoint.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="Fanen Beskeder for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

Du kan tilpasse antallet af elementer, der vises, samt hvilke kolonner der vises for hvert element. Standardfunktionsmåden er at vise tredive elementer pr. side.

Kolonnerne under denne fane indeholder oplysninger om alvorsgraden af den trussel, der udløste beskeden, samt status, undersøgelsestilstand, og hvem beskeden er blevet tildelt til.

Kolonnen *påvirkede enheder* refererer til den enhed (enhed), hvis profil du får vist i øjeblikket, samt alle andre enheder i netværket, der påvirkes.

Hvis du vælger et element på denne liste, åbnes et pop op-vindue, der indeholder endnu flere oplysninger om den valgte besked.

Denne liste kan filtreres efter alvorsgrad, status, eller hvem beskeden er tildelt til.

### <a name="timeline-tab"></a>Fanen Tidslinje

Fanen **Tidslinje** indeholder et interaktivt kronologisk diagram over alle hændelser, der udløses på enheden. Ved at flytte det fremhævede område i diagrammet til venstre eller højre kan du få vist hændelser over forskellige tidsperioder. Du kan også vælge et brugerdefineret datointerval i rullemenuen mellem det interaktive diagram og listen over hændelser.

Under diagrammet vises en liste over hændelser for det valgte datointerval.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="Fanen Tidslinje for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

Det antal elementer, der vises, og kolonnerne på listen kan begge tilpasses. I standardkolonnerne vises hændelsestidspunktet, den aktive bruger, handlingstype, enheder (processer) og yderligere oplysninger om hændelsen.

Hvis du vælger et element på denne liste, åbnes et pop op-vindue med grafen Hændelsesenheder, der viser de overordnede og underordnede processer, der er involveret i hændelsen.

Listen kan filtreres efter den specifikke type hændelse. f.eks. hændelser i registreringsdatabasen eller smartskærmhændelser.

Listen kan også eksporteres til en CSV-fil til download. Selvom filen ikke er begrænset af antallet af hændelser, er det maksimale tidsinterval, du kan vælge at eksportere, syv dage.

### <a name="security-recommendations-tab"></a>Fanen Sikkerhedsanbefalinger

Under fanen **Sikkerhedsanbefalinger** vises de handlinger, du kan udføre for at beskytte enheden. Hvis du vælger et element på denne liste, åbnes et pop op-vindue, hvor du kan få instruktioner i, hvordan du anvender anbefalingen.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="Fanen Sikkerhedsanbefalinger for enhedsprofilen på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

Som med de forrige faner kan antallet af elementer, der vises pr. side, samt hvilke kolonner der er synlige, tilpasses.

Standardvisningen indeholder kolonner, der beskriver de sikkerhedsmæssige svagheder, der er blevet håndteret, den tilknyttede trussel, den relaterede komponent eller software, der er berørt af truslen, og meget mere. Elementer kan filtreres efter anbefalingens status.

### <a name="software-inventory"></a>Softwarelager

Under fanen **Software inventory (Software inventory)** vises software, der er installeret på enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="Fanen Softwarelager for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

I standardvisningen vises softwareleverandøren, det installerede versionsnummer, antallet af kendte softwaresvagheder, trusselsindsigt, produktkode og tags. Det antal elementer, der vises, og hvilke kolonner der vises, kan begge tilpasses.

Hvis du vælger et element på denne liste, åbnes et pop op-vindue, der indeholder flere oplysninger om den valgte software samt stien og tidsstemplet for sidste gang, softwaren blev fundet.

Denne liste kan filtreres efter produktkode.

### <a name="discovered-vulnerabilities-tab"></a>Fanen Fundne sikkerhedsrisici

Under fanen **Fundne sikkerhedsrisici** kan du se en liste over alle almindelige sikkerhedsrisici og udnyttelser (CVEs), der kan påvirke enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="Fanen Fundne sikkerhedsrisici for enhedsprofilen på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

Standardvisningen viser alvorsgraden af CVE, CVS (Common Vulnerability Score), den software, der er relateret til CVE, da CVE'en blev publiceret, da CVE'en sidst blev opdateret, og trusler, der er knyttet til CVE'et.

Som med de forrige faner kan antallet af viste elementer, og hvilke kolonner der er synlige, tilpasses.

Hvis du vælger et element på denne liste, åbnes der et pop op-vindue, der beskriver CVE'et.

### <a name="missing-kbs"></a>Manglende KB

Fanen **Manglende KB** viser alle Microsoft-opdateringer, der endnu ikke er anvendt på enheden. De pågældende "nøgletal" er [vidensbaseartikler](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) , der beskriver disse opdateringer. f.eks. [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="Fanen Manglende KB for enhedsprofil på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

Standardvisningen viser den bulletin, der indeholder opdateringerne, operativsystemversionen, de berørte produkter, adresserede CV'er, KB-nummeret og mærkerne.

Det antal elementer, der vises pr. side, og hvilke kolonner der vises, kan tilpasses.

Når du vælger et element, åbnes et pop op-vindue, der er sammenkædet med opdateringen.

## <a name="related-topics"></a>Relaterede emner

* [Oversigt over Microsoft 365 Defender-portalen](microsoft-365-defender.md)
* [Slå Microsoft 365 Defender til](m365d-enable.md)
* [Undersøg enheder på enheder ved hjælp af direkte svar](../defender-endpoint/live-response.md)
* [Automatiseret undersøgelse og svar (AIR) i Office 365](../office-365-security/office-365-air.md)
