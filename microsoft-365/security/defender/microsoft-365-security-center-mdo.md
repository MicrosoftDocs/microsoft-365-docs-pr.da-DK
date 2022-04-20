---
title: Microsoft Defender for Office 365 i Microsoft 365 Defender
description: Få mere at vide om ændringer fra Security & Compliance Center til Microsoft 365 Defender.
keywords: Microsoft 365 sikkerhed, Introduktion til Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, enkelt glasrude, ny sikkerhedsportal, ny forsvarer sikkerhedsportal
ms.date: 02/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.prod: m365-security
ms.technology: m365d
ms.openlocfilehash: 84fed53ec1f12ebe7e52d0b789dc9db57360cf4f
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945555"
---
# <a name="microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Microsoft Defender for Office 365 i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

## <a name="quick-reference"></a>Hurtig reference

I nedenstående tabel vises ændringerne i navigationen mellem Security & Compliance Center og Microsoft 365 Defender.

<br>

****

|[Security & Compliance Center](https://protection.office.com)|[Microsoft 365 Defender](https://security.microsoft.com)|[Microsoft Purview-overholdelsesportal](https://compliance.microsoft.com/homepage)|[Exchange Administration](https://admin.exchange.microsoft.com)|
|---|---|---|---|
|Beskeder|<ul><li>[Politikker for beskeder](https://security.microsoft.com/alertpolicies)</li><li>[Hændelser & beskeder](https://security.microsoft.com/alerts)</li></ul>|[Siden Beskeder](https://compliance.microsoft.com/homepage)||
|Klassificering||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Forebyggelse af datatab||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Datastyring||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Informationsstyring||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Trusselsstyring|[Mail & samarbejde](https://security.microsoft.com/homepage)|||
|Tilladelser|[Tilladelser & roller](https://security.microsoft.com/emailandcollabpermissions)|Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Mailflow|||Se [Exchange Administration](https://admin.exchange.microsoft.com/#/)|
|Beskyttelse af personlige data||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Søg|[Revision](https://security.microsoft.com/auditlogsearch?viewid=Async%20Search)|Søg (indholdssøgning)||
|Rapporter|[Rapport](https://security.microsoft.com/emailandcollabreport)|||
|Service assurance||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|Tilsyn||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|eDiscovery||Se [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/homepage)||
|||||

[Microsoft 365 Defender](./microsoft-365-defender.md) at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> kombinerer sikkerhedsfunktioner fra eksisterende Microsoft-sikkerhedsportaler, herunder Security & Compliance Center. Dette forbedrede center hjælper sikkerhedsteams med at beskytte deres organisation mod trusler mere effektivt og effektivt.

Hvis du har kendskab til Security & Compliance Center (protection.office.com), beskrives nogle af ændringerne og forbedringerne i Microsoft 365 Defender i denne artikel.

Få mere at vide om fordelene: [Oversigt over Microsoft 365 Defender](microsoft-365-defender.md)

Hvis du leder efter elementer, der er relateret til overholdelse af angivne standarder, skal du besøge <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>.

## <a name="new-and-improved-capabilities"></a>Nye og forbedrede funktioner

Den venstre navigationslinje eller værktøjslinjen Hurtig start vil se bekendt ud. Der er dog nogle nye og opdaterede elementer i denne Defender for Cloud.

Med den samlede Microsoft 365 Defender løsning kan du sy trusselssignalerne sammen og bestemme det fulde omfang og den fulde indvirkning af truslen, og hvordan den i øjeblikket påvirker organisationen.

:::image type="content" source="../../media/M365-defender-converge-experience.png" alt-text="Den Microsoft 365 Defender konvergerede oplevelse" lightbox="../../media/M365-defender-converge-experience.png":::

Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer.

:::image type="content" source="../../media/Defender-for-O365.png" alt-text="Portalen Defender for Office 365" lightbox="../../media/Defender-for-O365.png":::

### <a name="incidents-and-alerts"></a>Hændelser og beskeder

Samler administration af hændelser og beskeder på tværs af dine mails, enheder og identiteter. Beskeder er nu tilgængelige under noden Undersøgelse og hjælper med at give et bredere overblik over et angreb. Beskedsiden giver fuld kontekst til beskeden ved at kombinere angrebssignaler for at oprette en detaljeret historie. Tidligere var beskeder specifikke for forskellige arbejdsbelastninger. En ny samlet oplevelse samler nu en ensartet visning af beskeder på tværs af arbejdsbelastninger. Du kan hurtigt triage, undersøge og udføre effektive handlinger.

- [Få mere at vide om undersøgelser](incidents-overview.md)
- [Få mere at vide om administration af beskeder](/windows/security/threat-protection/microsoft-defender-atp/review-alerts)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Værktøjslinjen Hurtig start af beskeder og handlinger på portalen Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Jagt

Søg proaktivt efter trusler, malware og skadelig aktivitet på tværs af dine slutpunkter, Office 365 postkasser og meget mere ved hjælp af [avancerede jagtforespørgsler](advanced-hunting-overview.md). Disse effektive forespørgsler kan bruges til at finde og gennemse trusselsindikatorer og enheder for både kendte og potentielle trusler.

[Brugerdefinerede registreringsregler](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) kan bygges fra avancerede jagtforespørgsler for at hjælpe dig med proaktivt at holde øje med hændelser, der kan være tegn på brudaktivitet og forkert konfigurerede enheder.

Her er et [eksempel på avanceret jagt](advanced-hunting-example.md) i Microsoft Defender for Office 365.

### <a name="action-center"></a>Handlingscenter

I Løsningscenter kan du se de undersøgelser, der er oprettet af automatiserede undersøgelses- og svarfunktioner. Denne automatiserede selvhelbredende Microsoft 365 Defender kan hjælpe sikkerhedsteams ved automatisk at reagere på bestemte hændelser.

Få mere at vide om [Løsningscenter](m365d-action-center.md).

#### <a name="threat-analytics"></a>Threat Analytics

Få trusselsintelligens fra ekspertforskere i Microsoft-sikkerhed. Threat Analytics hjælper sikkerhedsteams med at være mere effektive, når de står over for nye trusler. Threat Analytics indeholder:

- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365. Dette er ud over de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.
- Visning af hændelser relateret til truslerne.
- Forbedret oplevelse til hurtigt at identificere og bruge handlingsvenlige oplysninger i rapporterne.

Du kan få adgang til Threat-analyser enten fra navigationslinjen øverst til venstre i Microsoft 365 Defender eller fra et dedikeret dashboardkort, der viser de største trusler for din organisation.

Få mere at vide om, hvordan [du sporer og reagerer på nye trusler med trusselsanalyser](./threat-analytics.md).

### <a name="email--collaboration"></a>Mail & samarbejde

Spor og undersøg trusler mod dine brugeres mail, spor kampagner m.m. Hvis du har brugt Security & Compliance Center, kender du dette.

:::image type="content" source="../../media/converge-3-email-and-collab-new.png" alt-text="Menuen Hurtig start for Mail & Collab (eller MSDO) i navigationsruden til venstre på Microsoft 365 Defender-portalen" lightbox="../../media/converge-3-email-and-collab-new.png":::

#### <a name="email-entity-page"></a>Mailobjektside

Siden [Mailobjekt](../office-365-security/mdo-email-entity-page.md) *samler* mailoplysninger, der tidligere var blevet punktoprettet på tværs af forskellige sider eller visninger. Undersøgelse af mail for trusler og tendenser *er centraliseret*. Sidehovedoplysninger og eksempelvisning af mails er tilgængelige via den samme mailside sammen med andre nyttige mailrelaterede oplysninger. På samme måde kan du finde detonationsstatus for vedhæftede filer eller URL-adresser på en fane på samme side. Enhedssiden Mail giver administratorer og sikkerhedsteams mulighed for at forstå en mailtrussel og dens status hurtigt og derefter handle hurtigt og fastlægge håndteringen hurtigt.

### <a name="access-and-reports"></a>Adgang og rapporter

Få vist rapporter, rediger dine indstillinger, og rediger brugerroller.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Menuen Hurtig start til Microsoft 365 Defender tilladelser og rapportering i venstre navigationsrude på Microsoft 365 Defender-portalen" lightbox="../../media/converge-4-access-and-reporting-new.png":::

> [!NOTE]
> DomainKeys Identificeret mail (DKIM) sikrer, at destinationens mailsystemer har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.
> For Defender for Office 365 brugere kan du nu *administrere og rotere* DKIM-nøgler via Microsoft 365 Defender: <https://security.microsoft.com/threatpolicy>eller navigere til sektionen **Politik & regler** \> **Trusselspolitikker** \> \> **Afsnittet** \> **Regler DKIM**.
>
> Du kan få flere oplysninger under [Brug DKIM til at validere udgående mails, der er sendt fra dit brugerdefinerede domæne](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email).

## <a name="whats-changed"></a>Hvad er ændret

Denne tabel er en hurtig reference til Threat Management, hvor der er sket ændringer mellem Security & Compliance Center og portalen Microsoft 365 Defender. Klik på linkene for at læse mere om disse områder.

<br>

****

|Område|Beskrivelse af ændring|
|---|---|
|[Undersøgelse](../office-365-security/office-365-air.md#changes-are-coming-soon-in-your-microsoft-365-defender-portal)|Samler AIR-funktioner i [Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) og [Defender for Endpoint](../defender-endpoint/automated-investigations.md). Med disse opdateringer og forbedringer kan dit team for sikkerhedshandlinger få vist oplysninger om automatiserede undersøgelser og afhjælpningshandlinger på tværs af din mail, samarbejdsindhold, brugerkonti og enheder på ét sted.|
|[Beskedkø](../../compliance/alert-policies.md)|Pop op-vinduet **Vis beskeder** i Security & Compliance Center indeholder nu links til Microsoft 365 Defender. Klik på linket **Åbn beskedside**, og Microsoft 365 Defender åbnes. Du kan få adgang til siden **Vis beskeder** ved at klikke på en hvilken som helst Office 365 besked i køen Beskeder.|
|[Træning i simulering af angreb](../office-365-security/attack-simulation-training-insights.md)|Brug oplæring af angrebssimulering til at køre realistiske angrebsscenarier i din organisation. Disse simulerede angreb kan hjælpe med at oplære din arbejdsstyrke, før et reelt angreb påvirker din organisation. Oplæring af angrebssimulering omfatter flere muligheder, forbedrede rapporter og forbedrede træningsflows, der gør det nemmere at levere og administrere dine angrebssimulerings- og træningsscenarier.|
|

Ingen ændringer af disse områder:

- [Explorer](../office-365-security/threat-explorer.md)
- [Politikker & regler](../../compliance/alert-policies.md)
- [Kampagne](../office-365-security/campaigns.md)
- [Indlæg](../office-365-security/admin-submission.md)
- [Vurder](./m365d-action-center.md)
- [Trusselssporing](../office-365-security/threat-trackers.md)

Du kan også se afsnittet **Relaterede oplysninger** nederst i denne artikel.

> [!IMPORTANT]
> På <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> kombineres sikkerhedsfunktionerne i <https://securitycenter.windows.com>og <https://protection.office.com>. Det, du ser, afhænger dog af dit abonnement. Hvis du kun har Microsoft Defender for Office 365 Plan 1 eller 2, f.eks. som separate abonnementer, kan du ikke se funktioner omkring Sikkerhed for Slutpunkter og Defender for Office Plan 1-kunder kan ikke se elementer som Threat Analytics.

> [!TIP]
> Alle funktioner i Exchange Online Protection (EOP) medtages i Microsoft 365 Defender, da EOP er et kerneelement i Defender for Office 365.

## <a name="microsoft-365-defender-home-page"></a>Microsoft 365 Defender startside

På startsiden for portalen vises vigtige oversigtsoplysninger om sikkerhedsstatus for dit Microsoft 365 miljø.

Ved hjælp af **rundvisningen** kan du få en hurtig rundvisning i Slutpunkt eller Mail & samarbejdssider. Bemærk, at det, du ser her, afhænger af, om du har licens til Defender for Office 365 og/eller Defender for Endpoint.

Inkluderet er også et link til Security & Compliance Center til sammenligning. Det sidste link er siden **Nyheder** , der beskriver de seneste opdateringer.

## <a name="related-information"></a>Relaterede oplysninger

- [Omdirigerer Security & Compliance Center til Microsoft 365 Defender](microsoft-365-security-mdo-redirection.md)
- [Løsningscenter](./m365d-action-center.md)
- [Mailbeskeder & samarbejde](../../compliance/alert-policies.md#default-alert-policies)
- [Regler for brugerdefineret registrering](/microsoft-365/security/defender-endpoint/custom-detection-rules)
- [Opret en simulering af phishingangreb](../office-365-security/attack-simulation-training.md) , og [opret en nyttedata til oplæring af dine personer](../office-365-security/attack-simulation-training-payloads.md)
