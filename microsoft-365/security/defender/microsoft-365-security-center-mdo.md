---
title: Microsoft Defender for Office 365 i Microsoft 365 Defender
description: Få mere at vide om ændringer fra Security & Compliance Center til Microsoft 365 Defender.
keywords: 'Microsoft 365 sikkerhed: Introduktion til Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, enkelt rude med glas, ny sikkerhedsportal, ny defender sikkerhedsportal'
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
ms.openlocfilehash: a42805ea9b803818bd538e24a3fa626a00dac348
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499831"
---
# <a name="microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Microsoft Defender for Office 365 i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

## <a name="quick-reference"></a>Oversigtsreference

Tabellen nedenfor viser ændringerne i navigationen mellem Security & Compliance Center og Microsoft 365 Defender.

<br>

****

|[Security & Compliance Center](https://protection.office.com)|[Microsoft 365 Defender](https://security.microsoft.com)|[Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)|[Exchange Administration](https://admin.exchange.microsoft.com)|
|---|---|---|---|
|Beskeder|<ul><li>[Beskedpolitikker](https://security.microsoft.com/alertpolicies)</li><li>[Hændelser & beskeder](https://security.microsoft.com/alerts)</li></ul>|[Siden Beskeder](https://compliance.microsoft.com/homepage)||
|Klassificering||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Forebyggelse af datatab||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Datastyring||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Styring af oplysninger||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Administration af trusler|[Samarbejde & mail](https://security.microsoft.com/homepage)|||
|Tilladelser|[Tilladelser & roller](https://security.microsoft.com/emailandcollabpermissions)|Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Mailflow|||Se [Exchange Administration](https://admin.exchange.microsoft.com/#/)|
|Beskyttelse af personlige data||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Søg|[Overvågning](https://security.microsoft.com/auditlogsearch?viewid=Async%20Search)|Søg (indholdssøgning)||
|Rapporter|[Rapport](https://security.microsoft.com/emailandcollabreport)|||
|Tjenestesikring||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|Overvågning||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|eDiscovery||Se [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/homepage)||
|||||

[Microsoft 365 Defender](./microsoft-365-defender.md) at kombinerer <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> sikkerhedsegenskaber fra eksisterende Microsoft-sikkerhedsportaler, herunder Security & Compliance Center. Dette forbedrede center hjælper sikkerhedsteams med at beskytte deres organisation mod trusler mere effektivt.

Hvis du er bekendt med Security & Compliance Center (protection.office.com), beskrives nogle af ændringerne og forbedringerne i Microsoft 365 Defender.

Få mere at vide om fordelene: [Oversigt over Microsoft 365 Defender](microsoft-365-defender.md)

Hvis du leder efter kompatibilitetsrelaterede elementer, kan du gå <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">til Microsoft 365 Overholdelsescenter</a>.

## <a name="new-and-improved-capabilities"></a>Nye og forbedrede funktioner

Den venstre navigationslinje eller værktøjslinjen Hurtig start ser bekendt ud. Der er dog nogle nye og opdaterede elementer i denne Defender for Cloud.

Med den samlede Microsoft 365 Defender-løsning kan du sammensætte trusselssignalerne og fastslå det fulde omfang og den fulde virkning af truslen, og hvordan den i øjeblikket påvirker organisationen.

:::image type="content" source="../../media/M365-defender-converge-experience.png" alt-text="Den Microsoft 365 Defender konvergerende oplevelse" lightbox="../../media/M365-defender-converge-experience.png":::

Defender for Office 365 beskytter organisationen mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer.

:::image type="content" source="../../media/Defender-for-O365.png" alt-text="Den Defender for Office 365 portal" lightbox="../../media/Defender-for-O365.png":::

### <a name="incidents-and-alerts"></a>Hændelser og beskeder

Samler hændelses- og beskedstyring på tværs af dine mails, enheder og identiteter. Beskeder er nu tilgængelige under undersøgelsesnoden og er med til at give et bredere overblik over et angreb. Beskedsiden giver fuld kontekst til beskeden ved at kombinere angrebslys for at opbygge en detaljeret historie. Tidligere var beskeder specifikke for forskellige arbejdsbelastninger. En ny, samlet oplevelse samler nu en ensartet visning af beskeder på tværs af arbejdsbelastninger. Du kan hurtigt undersøge, undersøge og reagere effektivt.

- [Få mere at vide om undersøgelser](incidents-overview.md)
- [Få mere at vide om administration af beskeder](/windows/security/threat-protection/microsoft-defender-atp/review-alerts)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Startlinjen Beskeder og handlinger i Microsoft 365 Defender portal" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>På jagt

Søg proaktivt efter trusler, malware og ondsindet aktivitet på tværs af dine slutpunkter, Office 365 postkasser og meget mere ved hjælp af avancerede [forespørgselsforespørgsler](advanced-hunting-overview.md). Disse effektive forespørgsler kan bruges til at finde og gennemse trusselsindikatorer og enheder for både kendte og potentielle trusler.

[Brugerdefinerede registreringsregler](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) kan oprettes ud fra avancerede forespørgselsforespørgsler, der kan hjælpe dig med proaktivt at holde øje med begivenheder, der kan være til hjælp ved brudaktivitet og forkert konfigurerede enheder.

Her er et [eksempel på avanceret Microsoft Defender for Office 365](advanced-hunting-example.md).

### <a name="action-center"></a>Handlingscenter

Handlingscenter viser dig de undersøgelser, der er oprettet af automatiseret undersøgelse og svarmuligheder. Denne automatiserede, selvkørende kalender Microsoft 365 Defender hjælpe sikkerhedsteams ved automatisk at svare på bestemte begivenheder.

Få mere at vide [om Handlingscenter](m365d-action-center.md).

#### <a name="threat-analytics"></a>Threat Analytics

Få trusselsintelligens fra ekspert Microsoft-sikkerhedseksperter. Threat Analytics hjælper sikkerhedsteams med at være mere effektive, når de oplever nye trusler. Threat Analytics omfatter:

- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365. Dette er i tillæg til de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.
- Visning af hændelser relateret til truslerne.
- Forbedret oplevelse til hurtigt at identificere og bruge brugbare oplysninger i rapporterne.

Du kan få adgang til Threat Analytics enten fra den øverste venstre navigationslinje i Microsoft 365 Defender eller fra et dedikeret dashboardkort, der viser de vigtigste trusler for organisationen.

Få mere at vide om, [hvordan du kan spore og reagere på nye trusler med trusselsanalyse](./threat-analytics.md).

### <a name="email--collaboration"></a>Mail & samarbejde

Spor og undersøg trusler til dine brugeres mail, spor kampagner og meget mere. Hvis du har brugt Sikkerheds- & Compliance Center, er dette velkendt.

:::image type="content" source="../../media/converge-3-email-and-collab-new.png" alt-text="Menuen Hurtig start for mail & Collab (eller MSDO) i venstre navigationsrude på Microsoft 365 Defender-portalen" lightbox="../../media/converge-3-email-and-collab-new.png":::

#### <a name="email-entity-page"></a>Siden Mailenhed

Siden [Mailenhed samler](../office-365-security/mdo-email-entity-page.md) *mailoplysninger* , der var blevet spredt på tværs af forskellige sider eller visninger tidligere. Det er centraliseret at undersøge mails for trusler *og tendenser*. Oplysninger om sidehoved og maileksempel er tilgængelige via den samme mailside sammen med andre nyttige mailrelaterede oplysninger. På samme måde kan detonationsstatus for skadelige vedhæftede filer eller URL-adresser findes på en fane på samme side. Siden Mailenhed giver administratorer og sikkerhedsteams mulighed for at forstå en mailtrussel og dens status hurtigt og derefter reagere hurtigt på håndteringen.

### <a name="access-and-reports"></a>Access og rapporter

Få vist rapporter, rediger dine indstillinger, og rediger brugerroller.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Menuen Hurtig start til Microsoft 365 Defender adgang til og rapportering i venstre navigationsrude på Microsoft 365 Defender Navigationsportal" lightbox="../../media/converge-4-access-and-reporting-new.png":::

> [!NOTE]
> DomainKeys Identified Mail (DKIM) sikrer, at destinationsmailsystemerne har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.
> For Defender for Office 365 brugere kan du nu administrere  og *rotere DKIM-nøgler* via Microsoft 365 Defender: <https://security.microsoft.com/threatpolicy>, eller gå til Politik **&** \> \> \> regler For Trusselspolitikker **afsnit** \> **DKIM**.
>
> Få mere at vide under [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email).

## <a name="whats-changed"></a>Hvad er der ændret

Denne tabel er en hurtig reference til trusselsstyring, hvor der er sket en ændring mellem Security & Compliance Center og Microsoft 365 Defender portalen. Klik på linkene for at læse mere om disse områder.

<br>

****

|Område|Beskrivelse af ændring|
|---|---|
|[Undersøgelse](../office-365-security/office-365-air.md#changes-are-coming-soon-in-your-microsoft-365-defender-portal)|Samler AIR-funktioner i [Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) [og Defender til slutpunkt](../defender-endpoint/automated-investigations.md). Med disse opdateringer og forbedringer kan dit sikkerhedsteam få vist oplysninger om automatiserede undersøgelser og afhjælpningshandlinger på tværs af din mail, dit samarbejdsindhold, dine brugerkonti og enheder, alt sammen på ét sted.|
|[Beskedkø](../../compliance/alert-policies.md)|Pop **op-ruden** Vis beskeder i sikkerheds- & Overholdelsescenter indeholder nu links til Microsoft 365 Defender. Klik på linket **Åbn påmindelsesside**, og Microsoft 365 Defender åbnes. Du kan få adgang **til siden Vis beskeder** ved at klikke på en Office 365 i køen Vigtige beskeder.|
|[Kursus i angrebssimulering](../office-365-security/attack-simulation-training-insights.md)|Brug kursus i angrebssimulering til at køre realistiske angrebsscenarier i din organisation. Disse simulerede angreb kan hjælpe med at oplære dine medarbejdere, før et rigtigt angreb påvirker din organisation. Angrebssimulering omfatter flere indstillinger, forbedrede rapporter og forbedrede træningsflows for at gøre dine angrebssimulering og kursusscenarier nemmere at levere og administrere.|
|

Ingen ændringer af disse områder:

- [Stifinder](../office-365-security/threat-explorer.md)
- [Politikker & regler](../../compliance/alert-policies.md)
- [Kampagne](../office-365-security/campaigns.md)
- [Indsendelser](../office-365-security/admin-submission.md)
- [Gennemse](./m365d-action-center.md)
- [Threat Tracker](../office-365-security/threat-trackers.md)

Du kan også **se afsnittet** Relaterede oplysninger nederst i denne artikel.

> [!IMPORTANT]
> I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender kombineres</a> sikkerhedsfunktioner i <https://securitycenter.windows.com>, og <https://protection.office.com>. Men det, du ser, afhænger af dit abonnement. Hvis du kun har Microsoft Defender for Office 365 Plan 1 eller 2, kan du f.eks. ikke se egenskaberne omkring Sikkerhed for slutpunkter og Defender til Office Plan 1-kunder kan ikke se elementer som Threat Analytics.

> [!TIP]
> Alle Exchange Online Protection (EOP) inkluderes i Microsoft 365 Defender, da EOP er et centralt element i Defender for Office 365.

## <a name="microsoft-365-defender-home-page"></a>Microsoft 365 Defender startside

Startsiden for portalen viser vigtige oversigtsoplysninger om sikkerhedsstatus for dit Microsoft 365 miljø.

Med **Guidet rundvisning** kan du få en hurtig rundvisning i slutpunkter eller mailsider & samarbejdssider. Bemærk, at det, du ser her, afhænger af, om du har licens til Defender for Office 365 og/eller Defender til slutpunkt.

Der medfølger også et link til Security & Compliance Center til sammenligning. Det sidste link er **til siden Nyheder,** der beskriver de seneste opdateringer.

## <a name="related-information"></a>Relaterede oplysninger

- [Omdirigering af Security & Compliance Center til Microsoft 365 Defender](microsoft-365-security-mdo-redirection.md)
- [Handlingscenter](./m365d-action-center.md)
- [Beskeder & mailsamarbejde](../../compliance/alert-policies.md#default-alert-policies)
- [Brugerdefinerede registreringsregler](/microsoft-365/security/defender-endpoint/custom-detection-rules)
- [Opret en simulering af phishingangreb](../office-365-security/attack-simulation-training.md)[, og opret en nyttelast til uddannelse af dine personer](../office-365-security/attack-simulation-training-payloads.md)
