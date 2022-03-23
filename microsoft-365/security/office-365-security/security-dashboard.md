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
description: Brug det nye Sikkerhedsdashboard til at Office 365 status for trusselsbeskyttelse og få vist og handle på sikkerhedsadvarsler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 977fc897ecee859648fb1097e573cd0a8289768e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589144"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Sikkerhedsdashboard i Sikkerheds- & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Grundlæggende funktioner, og hvordan du åbner Sikkerhedsdashboard

Security & Compliance Center hos giver din organisation mulighed for at <https://protection.office.com> administrere databeskyttelse og overholdelse af data. Hvis du har de nødvendige tilladelser, giver Sikkerhedsdashboard dig mulighed for at gennemse din status for trusselsbeskyttelse samt få vist og reagere på sikkerhedsadvarsler.

Se videoen for at få et overblik, og læs derefter denne artikel for at få mere at vide.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

Afhængigt af hvad din organisations abonnement omfatter, indeholder Sikkerhedsdashboard flere widgets, f.eks. Oversigt over trusselsadministration, Status for trusselsbeskyttelse, globale ugentlige trusselsregistreringer, malware og meget mere, som beskrevet i de følgende afsnit.

Hvis du vil have vist Sikkerhedsdashboard i Security & Compliance Center, skal du gå til **Dashboard til trusselsadministration**\>. For at gå direkte til dashboardet Sikkerhed skal du bruge <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> Du skal være global administrator, sikkerhedsadministrator eller sikkerhedslæser for at få vist dashboardet Sikkerhed. Nogle widgets kræver yderligere tilladelser for at få vist. Du kan få mere at [vide under Tilladelser i Security & Compliance Center](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>Oversigt over trusselsadministration

Widgetten Oversigt over trusselsadministration fortæller dig hurtigt, hvordan organisationen var beskyttet mod trusler i løbet af de seneste syv (7) dage.

![Sikkerhedsdashboard – Widget med oversigt over trusselsadministration.](../../media/SecDash-ThreatMgmtSummary.png)

De oplysninger, du får vist i Threat Management Summary, afhænger af, hvad dit abonnement indeholder. I følgende tabel beskrives, hvilke oplysninger der er medtaget for Office 365 E3 og Office 365 E5.

<br>

****

|Office 365 E3|Office 365 E5|
|---|---|
|Malwaremeddelelser blokeret<br>Blokerede phishingmeddelelser<br>Meddelelser rapporteret af brugere<br><br><br><br>|Malwaremeddelelser blokeret<br>Blokerede phishingmeddelelser<br>Meddelelser rapporteret af brugere<br>Malware blokeret på nul dage<br>Avancerede phishingmeddelelser registreres<br>Skadelige URL-adresser blokeret|
|

For at få vist eller få adgang til widgetten Threat Management Summary skal du have tilladelse til at få vist Defender Office 365 rapporter. Du kan få mere at [vide under Hvilke tilladelser er nødvendige for at få vist Defender Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Status for trusselsbeskyttelse

Statuswidget'en Threat Protection viser effektiviteten af trusselsbeskyttelse med en tendens og detaljeret visning af phish og malware.

![Widget med status for trusselsbeskyttelse.](../../media/tpswidget.png)

Oplysningerne afhænger af, om dit Microsoft 365 -[abonnement Exchange Online Protection](exchange-online-protection-overview.md) (EOP) med eller uden [Microsoft Defender Office 365](defender-for-office-365.md).

<br>

****

|Hvis dit abonnement omfatter...|Du får vist disse oplysninger|
|---|---|
|EOP, men ikke Microsoft Defender til Office 365|Ondsindede mails, der blev registreret og blokeret af EOP.<p> Se [Statusrapport over trusselsbeskyttelse (EOP)](view-email-security-reports.md#threat-protection-status-report).|
|Microsoft Defender til Office 365|Skadeligt indhold og skadelig mail registreret og blokeret af EOP og Defender for Office 365 <p> Samlet antal unikke mails med skadeligt indhold blokeret af antimalwareprogrammet, automatisk tømning uden time og Defender til [Office 365-funktioner](zero-hour-auto-purge.md) (herunder [Pengeskab Links](safe-links.md), [Pengeskab](safe-attachments.md) vedhæftede filer og [antiphishing i Defender til Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> Se [Statusrapport over trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report).|
|

For at få vist eller få adgang til widget'en Status for Trusselsbeskyttelse skal du have tilladelse til at få vist Defender Office 365 rapporter. Du kan få mere at vide [under Hvilke tilladelser er nødvendige for at få vist Defender til Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Globale ugentlige trusselsregistreringer

Widget'en Globale ugentlige trusselsregistreringer viser, hvor mange trusler der blev registreret i mails i løbet af de seneste syv (7) dage.

![Global widget med ugentlige trusselsregistreringer.](../../media/globalweeklythreatdetections.png)

Metrikværdierne beregnes som beskrevet i følgende tabel:

<br>

****

|Metrisk|Sådan beregnes det|
|---|---|
|Meddelelser scannet|Antal scannede mails ganget med antallet af modtagere|
|Trusler er stoppet|Antal mails, der er identificeret som indeholdende malware ganget med antallet af modtagere|
|Blokeret [af Defender for Office 365](defender-for-office-365.md)|Antal mails, der er blokeret af Defender Office 365 ganget med antallet af modtagere|
|Fjernet efter levering|Antal meddelelser, der er [blevet fjernet med automatisk tømning uden time (ZAP)](zero-hour-auto-purge.md) ganget med antallet af modtagere|
|

## <a name="malware"></a>Malware

Malwarewidgets viser detaljer om malwaretendenser og malwarefamilietyper i løbet af de seneste syv (7) dage.

![Malwaretendenser og familietyper.](../../media/malwarewidgetatpe5.png)

## <a name="insights"></a>Insights

Insights er ikke kun surface key-problemer, du skal gennemgå, de indeholder også anbefalinger og handlinger, du bør overveje.

![Smart indsigt.](../../media/smartinsights.png)

Du kan f.eks. se, at phishing-mails leveres, fordi nogle brugere har deaktiveret deres indstillinger for uønsket mail. Hvis du vil have mere at vide om, hvordan indsigt [fungerer, skal du se Rapporter og indsigt & Security & Compliance Center](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Trusselsundersøgelse og -svar

Hvis din organisations abonnement omfatter [Microsoft Defender til Office 365 Plan 2](office-365-ti.md), har dit Sikkerhedsdashboard et afsnit, der indeholder avancerede værktøjer til trusselsundersøgelse og svar. Disse værktøjer omfatter [automatiserede undersøgelses- og svarmuligheder](automated-investigation-response-office.md). Automatiseret undersøgelse og svar kan være nyttigt i scenarier som [adressering af kompromitterede brugerkonti hurtigt](address-compromised-users-quickly.md).

Du kan få mere at vide [under Kom i gang med at bruge Automatiseret undersøgelse og svar (AIR) Office 365](office-365-air.md).

## <a name="trends"></a>Tendenser

Nederst i sikkerhedsdashboardet findes sektionen **Trends** , som opsummerer tendenser i mailflowet for organisationen. Rapporter indeholder oplysninger om mails, der er kategoriseret som spam, malware, phishingforsøg og gode mails. Klik på et felt for at få vist mere detaljerede oplysninger i rapporten.

![Afsnittet Tendenser opsummerer tendenser i mailflow for organisationen.](../../media/trends.png)

Og hvis din organisations abonnement omfatter [Defender for Office 365 Plan 2](office-365-ti.md), får du også en rapport om den seneste **trusselsadministration** i dette afsnit, der gør det muligt for dit sikkerhedsteam at få vist og handle på sikkerhedsadvarsler med høj prioritet.

Hvis du vil have vist eller have adgang til widgetten Sendt og Modtaget mail, skal du have tilladelse til at få vist Defender Office 365 rapporter. Du kan få mere at [vide under Hvilke tilladelser er nødvendige for at få vist Defender Office 365 rapporter?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

For at få vist eller få adgang til widget'en Seneste threat management Alerts skal du have tilladelse til at få vist beskeder. Du kan få mere at vide under [RBAC-tilladelser, der kræves for at få vist vigtige beskeder](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>Relaterede artikler

[Få vist mailsikkerhedsrapporter i Security & Compliance Center](view-email-security-reports.md)

[Få vist rapporter for Microsoft Defender for Office 365](view-reports-for-mdo.md)

[Defender til Office 365](defender-for-office-365.md)

[Office 365 trusselsundersøgelse og -svar](office-365-ti.md)
