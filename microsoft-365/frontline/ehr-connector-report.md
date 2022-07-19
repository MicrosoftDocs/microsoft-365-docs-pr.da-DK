---
title: Microsoft Teams EHR-connector Virtuelle Aftaler rapport
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: Få mere at vide om, hvordan du bruger Teams EHR-connectoren Virtuelle Aftaler rapport i Microsoft Teams Administration for at få en oversigt over EHR-integreret brug af virtuelle aftaler i din organisation.
ms.openlocfilehash: 6ec3423df4b6cd094bd2cab07e44c06923ec58bf
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859067"
---
# <a name="microsoft-teams-ehr-connector-virtual-appointments-report"></a>Microsoft Teams EHR-connector Virtuelle Aftaler rapport

Ehr-connectoren (Electronic Health Record) til Microsoft Teams Virtuelle Aftaler rapport i Microsoft Teams Administration giver dig en hurtig og nem måde at få vist Teams EHR-integreret brug af virtuelle aftaler på i din organisation.

Hvis du vil have vist rapporten, skal du være global administrator, Teams-administrator, Global læser eller Rapportlæser.

## <a name="view-the-report"></a>Få vist rapporten

Der er to måder at få adgang til og få vist rapporten på i Teams Administration.

- Via [brugskortet for EHR-connectoren](#the-ehr-connector-usage-card) på dashboardet
- Direkte ved at vælge [**EHR-connector Virtuelle Aftaler**](#the-teams-ehr-connector-virtual-appointments-report) i **Analytics &-rapporter** > **Forbrugsrapporter**

### <a name="the-ehr-connector-usage-card"></a>Brugskortet for EHR-connectoren

I venstre navigationsrude i Microsoft Teams Administration skal du vælge **Dashboard** og derefter gå til **EHR-connectoren Virtuelle Aftaler** kortet.

Her får du et hurtigt overblik over Teams EHR-integreret virtuel aftaleaktivitet pr. måned, herunder fuldførte aftaler, resterende allokering, og om du har overskredet den månedlige grænse (afhængigt af den licens, du har).

:::image type="content" source="media/ehr-connector-report-card.png" alt-text="Skærmbillede af brugskortet for EHR-connectoren på Dashboard i Teams Administration." lightbox="media/ehr-connector-report-card.png":::

Vælg **Vis detaljer** for at få vist rapportdetaljer. Hvis du vil købe flere licenser, skal du vælge **Køb mere**.

### <a name="the-teams-ehr-connector-virtual-appointments-report"></a>Teams EHR-connectoren Virtuelle Aftaler rapporten

1. I venstre navigationsrude i Teams Administration skal du gå til **Analytics & rapporter** > **Forbrugsrapporter**.
1. Under fanen **Vis rapporter** skal du vælge **EHR-connector Virtuelle Aftaler** og et datointerval. Vælg derefter **Kør rapport**.

    :::image type="content" source="media/ehr-connector-report.png" alt-text="Skærmbillede af Teams EHR-connectoren Virtuelle Aftaler rapporten i Teams Administration." lightbox="media/ehr-connector-report.png":::

#### <a name="interpret-the-report"></a>Fortolkning af rapporten

|Billedforklaring |Beskrivelse  |
|--------|-------------|
|**1**   |Hver rapport viser datoen for, hvornår rapporten blev genereret, og det valgte datointerval.|
|**2**   |Tabellen indeholder detaljerede oplysninger om hver aftale, der fandt sted i løbet af det valgte datointerval. Vær opmærksom på, at du ikke kan se poster for aftaler, hvor enten en medarbejder eller patient ikke tilmeldte sig. <ul><li>**Starttidspunkt (UTC)** er den dato og det klokkeslæt, hvor både en medarbejder og deltager er i aftalen.  </li> <li>**Varighed** er tidsforskellen mellem starttidspunktet, og hvornår den sidste person forlader aftalen.</li> <li>**Primær** er navnet på mødearrangøren. <li>**Primær mailadresse** er mødearrangørens mailadresse.</li> <li> **Afdelingen** er afdelingsoplysningerne for aftalen. Hvis oplysningerne ikke vises korrekt, skal du kontakte dit EHR-supportteam. Hvis du vil integrere med Epic, skal du sørge for, at ```&departmentId=%PERFDEPID;;; ; ;;NONE;%``` er en del af udbyderintegrationsposten. </li></li> <li>**Ledsagere** er det samlede antal medarbejdere og deltagere i aftalen.</li> <li>**Inden for grænsen** angiver, om aftalen er inden for allokeringsgrænsen. </li> </ul> |
|**3**   |Du kan eksportere rapporten til en CSV-fil til offlineanalyse. Vælg **Eksportér til Excel** for at downloade rapporten. |
|**4**   |Vælg **Filter** for at filtrere visningen med rapportdetaljer. |
|**5**   |Vælg **Fuld skærm** for at få vist rapporten i fuldskærmsvisning. |
|**6**   |Vælg **Rediger kolonner** for at tilføje eller fjerne kolonner i tabellen |

> [!NOTE]
> Hvis du vil have mere at vide om teams EHR-integrerede virtuelle aftaler, skal du se [Brugsrapport for virtuelle besøg](virtual-visits-usage-report.md). Med forbrugsrapporten virtuelle besøg kan du få vist vigtige målepunkter, f.eks. samlede aftaler, ventetid for lobby, aftalevarighed og ingen visninger. Brug disse oplysninger til at få indsigt i brugstendenser for at hjælpe dig med at optimere virtuelle aftaler for at levere bedre forretningsresultater.

## <a name="related-articles"></a>Relaterede artikler

- [Virtuelle aftaler med Teams – integration i Cerner EHR](ehr-admin-cerner.md)
- [Virtuelle aftaler med Teams – integration i Epic EHR](ehr-admin-epic.md) 
