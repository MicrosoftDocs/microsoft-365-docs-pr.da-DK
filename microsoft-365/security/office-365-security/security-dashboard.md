---
title: Oversigt over sikkerhedsdashboard
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Brug det nye sikkerhedsdashboard til at gennemse Office 365 Threat Protection Status og få vist og reagere på sikkerhedsbeskeder.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: defda5c112cf29cb944b502f442cf0e721a32676
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971732"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Sikkerhedsdashboard i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Grundlæggende funktioner, og hvordan du åbner et sikkerhedsdashboard

Security & Compliance Center på <https://protection.office.com> gør det muligt for din organisation at administrere databeskyttelse og overholdelse af angivne standarder. Hvis du har de nødvendige tilladelser, giver sikkerhedsdashboardet dig mulighed for at gennemse din Trusselsbeskyttelsesstatus samt få vist og reagere på sikkerhedsbeskeder.

Se videoen for at få et overblik, og læs derefter denne artikel for at få mere at vide.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

Afhængigt af hvad din organisations abonnement omfatter, indeholder sikkerhedsdashboardet flere widgets, f.eks. Threat Management Summary, Threat Protection Status, Global Weekly Threat Detections, Malware og meget mere, som beskrevet i følgende afsnit.

Hvis du vil have vist sikkerhedsdashboardet i Security & Compliance Center, skal du gå til **Dashboard** til **trusselsstyring**\>. Hvis du vil gå direkte til sikkerhedsdashboardet, skal du bruge <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> Du skal være global administrator, sikkerhedsadministrator eller sikkerhedslæser for at få vist sikkerhedsdashboardet. Nogle widgets kræver yderligere tilladelser for at få vist. Du kan få mere at vide [under Tilladelser i Security & Compliance Center](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>Oversigt over trusselsstyring

Widgetten Threat Management Summary fortæller dig hurtigt, hvordan din organisation var beskyttet mod trusler i løbet af de seneste syv (7) dage.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="Widgetten Security Dashboard – Oversigt over trusselsstyring" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

De oplysninger, du får vist i Oversigten over trusselsadministration, afhænger af, hvad dit abonnement omfatter. I følgende tabel beskrives, hvilke oplysninger der er inkluderet for Office 365 E3 og Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Malwaremeddelelser er blokeret<br>Phishing-meddelelser er blokeret<br>Meddelelser, der er rapporteret af brugere<br><br><br><br>|Malwaremeddelelser er blokeret<br>Phishing-meddelelser er blokeret<br>Meddelelser, der er rapporteret af brugere<br>Nuldags malware er blokeret<br>Der blev fundet avancerede phishing-meddelelser<br>Ondsindede URL-adresser er blokeret|

Hvis du vil have vist eller få adgang til widgetten Threat Management Summary, skal du have tilladelser til at få vist Defender for Office 365 rapporter. Du kan få mere at vide under [Hvilke tilladelser er nødvendige for at få vist de Defender for Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Status for trusselsbeskyttelse

Widgetten Threat Protection Status viser effektiviteten af trusselsbeskyttelse med en trendende og detaljeret visning af phish og malware.

:::image type="content" source="../../media/tpswidget.png" alt-text="Widgetten Status for trusselsbeskyttelse" lightbox="../../media/tpswidget.png":::

Detaljerne afhænger af, om dit Microsoft 365-abonnement omfatter [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) med eller uden [Microsoft Defender for Office 365](defender-for-office-365.md).

|Hvis dit abonnement indeholder...|Du får vist disse oplysninger|
|---|---|
|EOP, men ikke Microsoft Defender for Office 365|Skadelig mail, der blev registreret og blokeret af EOP.<p> Se [Rapport over status for trusselsbeskyttelse (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Microsoft Defender for Office 365|Skadeligt indhold og skadelig mail, der er registreret og blokeret af EOP og Defender for Office 365 <p> Samlet antal entydige mails med skadeligt indhold, der er blokeret af antimalwareprogrammet, [automatisk tømninger på nul timer](zero-hour-auto-purge.md) og Defender for Office 365 funktioner (herunder [Pengeskab links](safe-links.md), [Pengeskab vedhæftede filer](safe-attachments.md) og [anti-phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) . <p> Se [Statusrapport for trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report).|

Hvis du vil have vist eller få adgang til widgetten Threat Protection Status, skal du have tilladelser til at få vist Defender for Office 365 rapporter. Du kan få mere at vide under [Hvilke tilladelser er der brug for for at få vist de Defender for Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Globale ugentlige trusselsregistreringer

Widgetten Global Weekly Threat Detections viser, hvor mange trusler der blev registreret i mails i løbet af de seneste syv (7) dage.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="Widgetten Global Weekly Threat Detections" lightbox="../../media/globalweeklythreatdetections.png":::

Målepunkterne beregnes som beskrevet i følgende tabel:

|Metriske|Sådan beregnes den|
|---|---|
|Scannede meddelelser|Antallet af scannede mails ganget med antallet af modtagere|
|Truslerne er stoppet|Antallet af mails, der er identificeret som indeholder malware, ganget med antallet af modtagere|
|Blokeret af [Defender for Office 365](defender-for-office-365.md)|Antal blokerede mails med Defender for Office 365 ganget med antallet af modtagere|
|Fjernet efter levering|Antal meddelelser, der er fjernet med [automatisk fjernelse på nul timer (ZAP)](zero-hour-auto-purge.md) ganget med antallet af modtagere|

## <a name="malware"></a>Malware

Malwarewidgets viser oplysninger om malwaretendenser og malwarefamilietyper i løbet af de seneste syv (7) dage.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="Malware tendenser og familie typer" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Insights

Insights ikke kun behandler vigtige problemer, du skal gennemgå, de indeholder også anbefalinger og handlinger, du skal overveje.

:::image type="content" source="../../media/smartinsights.png" alt-text="Smart indsigt" lightbox="../../media/smartinsights.png":::

Du kan f.eks. se, at phishing-mails leveres, fordi nogle brugere har deaktiveret deres indstillinger for uønsket mail. Hvis du vil vide mere om, hvordan indsigt fungerer, skal du se [Rapporter og indsigt i Security & Compliance Center](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Trusselsundersøgelse og -svar

Hvis organisationens abonnement omfatter [Microsoft Defender for Office 365 Plan 2](office-365-ti.md), indeholder dit sikkerhedsdashboard et afsnit, der indeholder avancerede værktøjer til undersøgelse af trusler og svar. Disse værktøjer omfatter [automatiserede undersøgelses- og svarfunktioner](automated-investigation-response-office.md). Automatiseret undersøgelse og svar kan være nyttig i scenarier som f.eks. [hurtig håndtering af kompromitterede brugerkonti](address-compromised-users-quickly.md).

Du kan få mere at vide under [Kom i gang med at bruge automatiseret undersøgelse og svar (AIR) i Office 365](office-365-air.md).

## <a name="trends"></a>Tendenser

Nederst i sikkerhedsdashboardet findes afsnittet **Tendenser** , der opsummerer mailflowtendenser for din organisation. Rapporter indeholder oplysninger om mail, der er kategoriseret som spam, malware, phishingforsøg og god mail. Klik på et felt for at få vist mere detaljerede oplysninger i rapporten.

:::image type="content" source="../../media/trends.png" alt-text="Afsnittet Tendenser, der opsummerer mailflowtendenser for organisationen" lightbox="../../media/trends.png":::

Og hvis din organisations abonnement omfatter [Defender for Office 365 Plan 2](office-365-ti.md), har du også en rapport over **vigtige beskeder om administration af trusler for nylig** i dette afsnit, der gør det muligt for dit sikkerhedsteam at få vist og reagere på sikkerhedsbeskeder med høj prioritet.

Hvis du vil have vist eller få adgang til widgetten Sendt og Modtaget mail, skal du have tilladelse til at få vist Defender for Office 365 rapporter. Du kan få mere at vide under [Hvilke tilladelser er nødvendige for at få vist de Defender for Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

Hvis du vil have vist eller få adgang til widgetten Recent Threat Management Alerts, skal du have tilladelse til at få vist beskeder. Du kan få mere at vide under [RBAC-tilladelser, der kræves for at få vist beskeder](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>Relaterede artikler

[Få vist mailsikkerhedsrapporter i Security & Compliance Center](view-email-security-reports.md)

[Få vist rapporter for Microsoft Defender for Office 365](view-reports-for-mdo.md)

[Defender for Office 365](defender-for-office-365.md)

[Office 365 Trusselsundersøgelse og -svar](office-365-ti.md)
