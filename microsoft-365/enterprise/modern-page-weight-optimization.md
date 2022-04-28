---
title: Optimer sidetykkelsen på SharePoint online moderne webstedssider
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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: Få mere at vide om, hvordan du bruger værktøjet Sidediagnosticering til at optimere sidevægten på SharePoint online moderne webstedssider.
ms.openlocfilehash: 01a1976972983cccf3e93006e395f789d5882eff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101199"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>Optimer sidetykkelsen på SharePoint online moderne webstedssider

SharePoint Online moderne webstedssider indeholder serialiseret kode, der kræves for at gengive sidens indhold, herunder billeder, tekst, objekter i indholdsområdet under navigations-/kommandolinjer og anden HTML-kode, der udgør sidens struktur. Sidevægt er en måling af denne HTML-kode og bør begrænses for at sikre optimale indlæsningstider for siden.

Denne artikel hjælper dig med at forstå, hvordan du reducerer sidevægten på dine moderne webstedssider.

>[!NOTE]
>Du kan få flere oplysninger om ydeevnen i SharePoint moderne onlineportaler [under Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>Brug sidediagnosticering til SharePoint til at analysere sidevægt

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint webstedsside med værktøjet Sidediagnosticering for SharePoint, kan du se oplysninger om siden i **sidevægten under 500 KB** resultatet af ruden _Diagnosticeringstest_. Resultatet vises med grønt, hvis sidetykkelsen er under grundlinjens værdi, og rød, hvis sidevægten overstiger den oprindelige værdi.

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Sidevægten overstiger 500 KB
- **Der kræves ingen handling** (grøn): Sidevægten er under 500 KB

Hvis **sidetykkelsen under 500 KB** vises i afsnittet **Opmærksomhed påkrævet** , kan du klikke på resultatet for at få flere oplysninger.

![Anmodninger om SharePoint resultater.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>Løs problemer med sidevægt

Hvis sidevægten overstiger 500 KB, kan du forbedre den samlede indlæsningstid for sider ved at reducere antallet af webdele og begrænse sideindhold til en passende grad.

Generel vejledning i reduktion af sidevægt omfatter:

- Begræns sideindholdet til et rimeligt beløb, og brug flere sider til relateret indhold.
- Minimer brugen af webdele, der har store egenskabsbeholdere.
- Brug ikke-interaktive aggregerede visninger, når det er muligt.
- Optimer billedstørrelser ved at tilpasse størrelsen på billeder korrekt ved hjælp af komprimerede billedformater og sikre, at de downloades fra en CDN.

Du kan finde yderligere vejledning i at begrænse sidevægt i følgende artikel:

- [Optimer sidens ydeevne i SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

Før du foretager sideændringer for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter din revision for at se, om det nye resultat er inden for grundlinjestandarden, og kontrollér indlæsningstiden for den nye side for at se, om der var en forbedring.

![Resultater for sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, f.eks. netværksbelastning, klokkeslæt på dagen og andre midlertidige forhold. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at beregne gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Juster SharePoint onlineydeevne](tune-sharepoint-online-performance.md)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)

[Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Content Delivery Networks](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)