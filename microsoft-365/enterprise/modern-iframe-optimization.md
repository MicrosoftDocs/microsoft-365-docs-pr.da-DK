---
title: Optimer iFrames i SharePoint Online moderne og klassiske udgivelseswebstedssider
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du optimerer ydeevnen for iFrames på SharePoint Online moderne og klassiske udgivelseswebstedssider.
ms.openlocfilehash: 0e8710b76d20388ba3514b32fe598e982a7a9561
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100693"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optimer iFrames i SharePoint Online moderne og klassiske udgivelseswebstedssider

iFrames kan være nyttigt til visning af avanceret indhold, f.eks. videoer eller andre medier. Da iFrames indlæser en separat side på den SharePoint webstedsside, kan indhold, der indlæses i iFrame, indeholde store billeder, videoer eller andre elementer, der kan bidrage til den overordnede sideindlæsningstid, og som du ikke kan styre på siden. Denne artikel hjælper dig med at forstå, hvordan iFrames på dine sider påvirker brugerens opfattede ventetid, og hvordan almindelige problemer afhjælpes.

>[!NOTE]
>Du kan finde flere oplysninger om ydeevnen på SharePoint moderne onlinewebsteder [under Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>Brug sidediagnosticering til SharePoint til at analysere webdele ved hjælp af iFrames

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint webstedsside med værktøjet Sidediagnosticering for SharePoint, kan du se oplysninger om webdele, der indeholder iFrames, i ruden _Diagnosticeringstest_. Den grundlæggende metrikværdi er den samme for moderne og klassiske sider.

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Siden indeholder **tre eller flere** webdele, der bruger iFrames
- **Muligheder for forbedring** (gul): Siden indeholder **en eller to** webdele ved hjælp af iFrames
- **Der kræves ingen handling** (grøn): Siden indeholder ingen webdele, der bruger iFrames

Hvis de **webdele, der bruger det registrerede resultat iFrames** , vises i afsnittet **Forbedringsmuligheder** eller **Opmærksomhed kræves)** i resultaterne, kan du klikke på resultatet for at se de webdele, der indeholder iFrames.

![Resultater af værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>Løs problemer med ydeevnen af iFrame

Brug de **webdele, der bruger iFrames, der registreres** , resulterer i værktøjet Sidediagnosticering til at bestemme, hvilke webdele der indeholder iFrames, og som kan bidrage til langsomme indlæsningstider for sider.

iFrames er i sagens natur langsomme, fordi de indlæser en separat ekstern side, herunder alt tilknyttet indhold, f.eks. javascript, CSS og framework-elementer, hvilket potentielt øger belastningerne på webstedssiden med en faktor på to eller flere.

Følg vejledningen nedenfor for at sikre optimal brug af iFrames.

- Når det er muligt, kan du bruge billeder i stedet for iFrames, hvis prøveversionen er lille til at begynde med eller ikke-interaktiv.
- Hvis iFrames skal bruges, skal du minimere antallet og/eller flytte dem ud af visningsporten.
- Integrerede Office-filer, f.eks. Word, Excel og PowerPoint, er interaktive, men indlæses langsomt. Billedminiaturer med et link til hele dokumentet fungerer ofte bedre.
- Integrerede YouTube-videoer og Twitter-feeds har en tendens til at fungere bedre i iFrames, men brug disse former for integreringer fornuftigt.
- Isolerede webdele er en rimelig undtagelse, men minimerer deres antal og placering i visningsporten.
- Hvis en iFrame er placeret uden for visningsporten, kan du overveje at bruge en _IntersectionObserver_ til at forsinke gengivelsen af iFrame, indtil den vises.

Før du foretager sideændringer for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter din revision for at se, om det nye resultat er inden for grundlinjestandarden, og kontrollér indlæsningstiden for den nye side for at se, om der var en forbedring.

![Resultater for sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, f.eks. netværksbelastning, klokkeslæt på dagen og andre midlertidige forhold. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at beregne gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Juster SharePoint onlineydeevne](tune-sharepoint-online-performance.md)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)

[Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)