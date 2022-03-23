---
title: Optimer iFrames på sider med moderne og klassisk publiceringswebsted i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Få mere at vide om, hvordan du optimerer ydeevnen af iFrames i SharePoint Online – moderne og klassiske publiceringswebstedssider.
ms.openlocfilehash: e38dd3922444228cdf54c8ef306fbbd9eafb81c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591615"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optimer iFrames på sider med moderne og klassisk publiceringswebsted i SharePoint Online

iFrames kan være nyttige til eksempelvisning af RTF-indhold som videoer eller andre medier. Men fordi iFrames indlæser en separat side på SharePoint-webstedssiden, kan indhold, der indlæses i iFrame, indeholde store billeder, videoer eller andre elementer, der kan bidrage til den samlede sideindlæsningstider, og som du ikke kan styre på siden. Denne artikel hjælper dig med at forstå, hvordan du bestemmer, hvordan iFrames på dine sider påvirker brugerens opfattede ventetid, og hvordan du kan løse almindelige problemer.

>[!NOTE]
>Du kan finde flere oplysninger om ydeevnen i moderne websteder i SharePoint Online under [Ydeevne i den moderne SharePoint-oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>Brug Værktøjet Sidediagnosticering til SharePoint til at analysere webdele ved hjælp af iFrames

Sidediagnosticering til SharePoint-værktøjet er en browserudvidelse til de nye Microsoft Edge- oghttps://www.microsoft.com/edge) Chrome-browsere, der analyserer både moderne portal og klassiske sider på publiceringswebstedet i SharePoint Online. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om Værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug [sidediagnosticeringsværktøjet til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint-systemside.

Når du analyserer en SharePoint-webstedsside med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om webdele, der indeholder iFrames, i ruden _Diagnosticeringstest_ . Metrikværdien for grundlinjer er den samme for moderne og klassiske sider.

Mulige resultater omfatter:

- **Handling påkrævet** (rød): Siden indeholder tre **eller flere webdele** ved hjælp af iFrames
- **Forbedringsmuligheder** (gul): Siden indeholder én **eller to webdele** ved hjælp af iFrames
- **Ingen handling påkrævet** (grøn): Siden indeholder ingen webdele, der bruger iFrames

Hvis de webdele, der bruger **iFrames, registreres** i enten  sektionen Forbedringsmuligheder eller Handling påkrævet **)** i resultaterne, kan du klikke på resultatet for at se de webdele, der indeholder iFrames.

![Resultater fra værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>Løse problemer med ydeevnen i iFrame

Brug **webdelene, der bruger iFrames** , resulterer i værktøjet Sidediagnosticering til at bestemme, hvilke webdele der indeholder iFrames, og det kan bidrage til langsomme sideindlæsningstider.

iFrames er indbygget langsom, fordi de indlæser en separat ekstern side, herunder alt tilknyttet indhold som javascript, CSS og frameworkelementer, hvilket potentielt øger pladsen på webstedssiden med en faktor på to eller flere.

Følg vejledningen nedenfor for at sikre optimal brug af iFrames.

- Når det er muligt, skal du bruge billeder i stedet for iFrames, hvis eksemplet er lille til at starte med eller ikke-interaktivt.
- Hvis der skal bruges iFrames, skal du minimere antallet og/eller flytte dem ud af visningsporten.
- Integrerede Office-filer som Word, Excel og PowerPoint er interaktive, men er langsomme at indlæse. Billedminiaturer med et link til hele dokumentet vil ofte fungere bedre.
- Integrerede YouTube-videoer og Twitter-feeds har en tendens til at fungere bedre i iFrames, men brug disse typer af integreringer med omovervejethed.
- Isolerede webdele er en rimelig undtagelse, men minimer deres antal og placering i visningsporten.
- Hvis en iFrame er placeret uden for visningsporten, skal du overveje at bruge en _IntersectionObserver_ til at forsinke gengivelsen af iFrame, indtil den kommer ind i visningen.

Før du foretager siderevisioner for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter ændringen for at se, om det nye resultat er inden for den oprindelige standard, og kontrollér den nye sideindlæsningstid for at se, om der er sket en forbedring.

![Resultater af sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, som f.eks. netværksbelastning, tidspunkt på dagen og andre midlertidige betingelser. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at finde gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Finjustere ydeevnen i SharePoint Online](tune-sharepoint-online-performance.md)

[Finjustere ydeevnen i Office 365](tune-microsoft-365-performance.md)

[Ydeevne i den moderne SharePoint-oplevelse](/sharepoint/modern-experience-performance)