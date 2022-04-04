---
title: Enhedsprofil i Microsoft 365 sikkerhedsportal
description: Få vist risiko- og eksponeringsniveauer for en enhed i organisationen. Analysér tidligere og nuværende trusler, og beskyt enheden med de seneste opdateringer.
keywords: sikkerhed, malware, Microsoft 365, M365, Microsoft 365 Defender, security center, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity, enhedsside, enhedsprofil, maskinside, maskinprofil
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
ms.author: v-maave
author: martyav
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: eec3881d2fdb53bc03e4e730fecaf6f1c78c98c7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755865"
---
# <a name="device-profile-page"></a>Siden Enhedsprofil

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Sikkerhedsportalen Microsoft 365 dig enhedsprofilsider, så du hurtigt kan vurdere tilstand og status for enheder på dit netværk.

> [!IMPORTANT]
> Enhedsprofilsiden kan se en smule anderledes ud, afhængigt af om enheden er tilmeldt Microsoft Defender til Slutpunkt, Microsoft Defender til identitet eller begge dele.

Hvis enheden er tilmeldt Microsoft Defender til slutpunkt, kan du også bruge enhedens profilside til at udføre nogle almindelige sikkerhedsopgaver.

## <a name="navigating-the-device-profile-page"></a>Navigering på enhedens profilside

Profilsiden er opdelt i flere brede sektioner.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-overall.png" alt-text="Siden Enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-overall.png":::

Sidepanelet (1) viser grundlæggende oplysninger om enheden.

Hovedindholdsområdet (2) indeholder faner, du kan skifte mellem for at få vist forskellige typer oplysninger om enheden.

Hvis enheden er tilmeldt Microsoft Defender til slutpunkt, får du også vist en liste over svarhandlinger (3). Svarhandlinger giver dig mulighed for at udføre almindelige sikkerhedsrelaterede opgaver.

## <a name="sidebar"></a>Sidepanel

Sidepanelet ud for hovedindholdsområdet på enhedens profilside.

:::image type="content" source="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png" alt-text="Fanen Sidepanel for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/azure-atp-only-device-sidebar.png":::

Sidepanelet viser enhedens fulde navn og eksponeringsniveau. Den indeholder også nogle vigtige grundlæggende oplysninger i små underafsnit, som kan åbnes eller lukkes, f.eks.:

* **Mærker** – Alle Microsoft Defender til slutpunkter, Microsoft Defender til identitet eller brugerdefinerede mærker, der er knyttet til enheden. Mærker fra Microsoft Defender for Identity kan ikke redigeres.
* **Sikkerhedsoplysninger** – Åbn hændelser og aktive beskeder. Enheder, der er tilmeldt Microsoft Defender til Slutpunkt, viser også eksponeringsniveau og risikoniveau.

> [!TIP]
> Eksponeringsniveauet relaterer til, hvor meget enheden overholder sikkerhedsanbefalinger, mens risikoniveauet beregnes ud fra en række faktorer, herunder typerne og alvorsgraderne for aktive beskeder.

* **Enhedsoplysninger** – Domæne, operativsystem, tidsstempel for, hvornår enheden blev set første gang, IP-adresser og ressourcer. Enheder, der er tilmeldt Microsoft Defender til Slutpunkt, viser også tilstandstilstanden. Enheder, der er tilmeldt Microsoft Defender for Identity, viser SAM-navn og et tidsstempel for, hvornår enheden blev oprettet.
* **Netværksaktivitet** – Tidsstempler for første gang og sidste gang enheden blev set på netværket.
* **Katalogdata** (kun for enheder, der er tilmeldt *Microsoft Defender for Identity*) – [UAC-flag](/windows/security/identity-protection/user-account-control/user-account-control-overview) , [SPN'er](/windows/win32/ad/service-principal-names) og gruppemedlemskaber.

## <a name="response-actions"></a>Svarhandlinger

Svarhandlinger giver en hurtig måde at beskytte dig mod og analysere trusler på.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-long-action-bar.png" alt-text="Handlingslinjen for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-long-action-bar.png":::

> [!IMPORTANT]
> * [Svarhandlinger](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) er kun tilgængelige, hvis enheden er tilmeldt Microsoft Defender til slutpunkt.
> * Enheder, der er tilmeldt Microsoft Defender til Slutpunkt, kan vise forskellige antal svarhandlinger baseret på enhedens operativsystem og versionsnummer.

Handlinger, der er tilgængelige på enhedsprofilsiden, omfatter:

* **Administrer mærker** – opdaterer brugerdefinerede mærker, du har anvendt på denne enhed.
* **Isoler** enhed – isolerer enheden fra organisationens netværk, mens du holder den forbundet til Microsoft Defender til slutpunktet. Du kan vælge at tillade Outlook, Teams og Skype for Business kører, mens enheden er isoleret, til kommunikationsformål.
* **Handlingscenter** – Få vist status for sendte handlinger. Kun tilgængelig, hvis der allerede er valgt en anden handling.
* **Begræns eksekvering** af apps – Forhindrer programmer, der ikke er signeret af Microsoft, i at køre.
* **Kør antivirusscanning** – opdateringer Windows Defender Antivirus definitioner og kører straks en antivirusscanning. Vælg mellem Hurtig scanning eller Fuld scanning.
* **Indsamle undersøgelsespakke** – indsamler oplysninger om enheden. Når undersøgelsen er afsluttet, kan du downloade den.
* **Initier direkte svarsession** – Indlæser en fjern shell på [enheden til dybdegående sikkerhedsundersøgelse](/microsoft-365/security/defender-endpoint/live-response).
* **Initier automatiseret** [undersøgelse – undersøger og afhjælper automatisk trusler](../office-365-security/office-365-air.md). Selvom du manuelt kan udløse automatiserede undersøgelser, der skal køres fra denne [side, udløser](../../compliance/alert-policies.md#default-alert-policies) visse beskedpolitikker automatisk undersøgelser selv.
* **Handlingscenter** – Viser oplysninger om svarhandlinger, der i øjeblikket kører.

## <a name="tabs-section"></a>Sektionen Faner

Enhedsprofilfanerne giver dig mulighed for at skifte gennem en oversigt over sikkerhedsoplysninger om enheden og tabeller, der indeholder en liste over beskeder.

Enheder, der er tilmeldt Microsoft Defender til Slutpunkt, vil også vise faner, der har en tidslinje, en liste med sikkerhedsanbefalinger, et softwarelager, en liste over opdagede sårbarheder og manglende KBs (sikkerhedsopdateringer).

### <a name="overview-tab"></a>Fanen Oversigt

Standardfanen er **Oversigt**. Den giver et hurtigt overblik over den vigtigste sikkerhed på enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-overview.png" alt-text="Fanen Oversigt for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-overview.png":::

Her kan du få et hurtigt overblik over enhedens aktive beskeder og eventuelle brugere, der er logget på i øjeblikket.

Hvis enheden er tilmeldt Microsoft Defender til slutpunkt, kan du også se enhedens risikoniveau og eventuelle tilgængelige data om sikkerhedsvurderinger. Sikkerhedsvurderingerne beskriver enhedens eksponeringsniveau, kommer med sikkerhedsanbefalinger og viser påvirket software og opdagede sårbarheder.

### <a name="alerts-tab"></a>Fanen Beskeder

Fanen **Vigtige beskeder** indeholder en liste over beskeder, der er blevet hævet på enheden, fra både Microsoft Defender for Identity og Microsoft Defender til slutpunkt.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-alerts.png" alt-text="Fanen Beskeder for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-alerts.png":::

Du kan tilpasse antallet af viste elementer, samt hvilke kolonner der vises for hvert element. Standardfunktionsmåden er at angive tredive elementer pr. side.

Kolonnerne under denne fane indeholder oplysninger om alvoren af den trussel, der udløste beskeden, samt status, undersøgelsestilstand og hvem beskeden er tildelt.

Kolonnen *berørte enheder henviser* til den enhed (enhed), hvis profil du aktuelt får vist, samt alle andre enheder i dit netværk, der er påvirket.

Når du vælger et element på denne liste, åbnes en pop op-meddelelse, der indeholder endnu flere oplysninger om den markerede besked.

Denne liste kan filtreres efter alvorsgrad, status, eller hvem beskeden er tildelt til.

### <a name="timeline-tab"></a>Fanen Tidslinje

Fanen **Tidslinje** indeholder et interaktivt kronologisk diagram over alle hændelser, der er hævet på enheden. Ved at flytte det fremhævede område i diagrammet til venstre eller højre kan du se begivenheder over forskellige tidsperioder. Du kan også vælge et brugerdefineret datointerval fra rullemenuen mellem det interaktive diagram og listen over begivenheder.

Under diagrammet er der en liste over begivenheder for det valgte datointerval.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-timeline.png" alt-text="Fanen Tidslinje for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-timeline.png":::

Antallet af viste elementer og kolonnerne på listen kan begge tilpasses. Standardkolonnerne viser tidspunktet for begivenheden, den aktive bruger, handlingstypen, enheder (processer) og yderligere oplysninger om begivenheden.

Når du vælger et element på denne liste, åbnes en pop op-meddelelse, der viser et diagram over hændelsesenheder, der viser de overordnede og underordnede processer, der er involveret i begivenheden.

Listen kan filtreres efter den specifikke type hændelse. For eksempel hændelser i registreringsdatabasen eller Smart Screen-hændelser.

Listen kan også eksporteres til en CSV-fil til download. Selvom filen ikke er begrænset af antallet af hændelser, er det maksimale tidsinterval, du kan vælge at eksportere, syv dage.

### <a name="security-recommendations-tab"></a>Fanen Sikkerhedsanbefalinger

Fanen **Sikkerhedsanbefalinger** viser de handlinger, du kan udføre for at beskytte enheden. Når du vælger et element på denne liste, åbnes der et pop op-pop-op-element, hvor du kan få en vejledning i, hvordan du anvender det.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png" alt-text="Fanen sikkerhedsanbefalinger for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-security-recs.png":::

Som med de forrige faner kan antallet af elementer, der vises pr. side, samt hvilke kolonner der er synlige, tilpasses.

Standardvisningen indeholder kolonner, der beskriver de sikkerhedsrelaterede problemer, den tilknyttede trussel, den relaterede komponent eller software, der påvirkes af truslen, og meget mere. Elementer kan filtreres efter anbefalingens status.

### <a name="software-inventory"></a>Lager over software

Fanen **Softwarelager viser** software, der er installeret på enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png" alt-text="Fanen Softwarelager for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-software-inventory.png":::

Standardvisningen viser softwareleverandøren, det installerede versionsnummer, antallet af kendte softwareudviklere, trusselsindsigt, produktkode og mærker. Antallet af viste elementer, og hvilke kolonner der vises, kan begge tilpasses.

Når du vælger et element på denne liste, åbnes et pop op-vindue med flere oplysninger om den valgte software samt sti- og tidsstemplet for sidste gang, softwaren blev fundet.

Denne liste kan filtreres efter produktkode.

### <a name="discovered-vulnerabilities-tab"></a>Fane med opdagede sårbarheder

Fanen **Opdagede** sårbarheder viser en liste over almindelige sårbarheder og udnyttelser (CVEs), der kan påvirke enheden.

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png" alt-text="Fanen Opdagede sårbarheder for enhedsprofilen i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-discovered-vulnerabilities.png":::

Standardvisningen viser CVE'ens alvorlighed, sikkerhedsrisikosscore (COMMON Vulnerability Score – CVS), den software, der er relateret til CVE'en, hvornår CVE'en blev offentliggjort, hvornår CVE'en sidst blev opdateret, samt trusler knyttet til CVE'en.

Som med de forrige faner kan antallet af viste elementer, og hvilke kolonner der er synlige, tilpasses.

Når du vælger et element på denne liste, åbnes en pop op-pop-op, der beskriver CVE'et.

### <a name="missing-kbs"></a>Manglende KBs

Under **fanen Manglende KBs** vises eventuelle Microsoft-opdateringer, der endnu ikke er anvendt på enheden. De pågældende "KBs" er Knowledge [Base-artikler,](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query) der beskriver disse opdateringer; [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

:::image type="content" source="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG" alt-text="Fanen Manglende KBs for enhedsprofil i Microsoft 365 Defender portal" lightbox="../../media/mtp-device-profile/hybrid-device-tab-missing-kbs.PNG":::

Standardvisningen viser opslagsordet med opdateringer, operativsystemversion, berørte produkter, adresserede CV'er, KB-nummer og mærker.

Antallet af elementer, der vises pr. side, og hvilke kolonner der vises, kan tilpasses.

Når du vælger et element, åbnes der en pop op-pop-op-pop-op, der linker til opdateringen.

## <a name="related-topics"></a>Relaterede emner

* [Microsoft 365 Defender oversigt](microsoft-365-defender.md)
* [Slå Microsoft 365 Defender](m365d-enable.md)
* [Undersøg enheder på enheder ved hjælp af direkte svar](../defender-endpoint/live-response.md)
* [Automatiseret undersøgelse og svar (AIR) i Office 365](../office-365-security/office-365-air.md)
