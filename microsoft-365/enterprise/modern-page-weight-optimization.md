---
title: Optimer sidetykkelse på SharePoint moderne webstedssider online
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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: Lær at bruge værktøjet Sidediagnosticering til at optimere sidetykkelse på SharePoint moderne webstedssider online.
ms.openlocfilehash: 2c7221befc89fd0385b3e96a31fc7721f012628d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589718"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>Optimer sidetykkelse på SharePoint moderne webstedssider online

SharePoint Online indeholder serialiseret kode, der kræves for at gengive sidens sideindhold, herunder billeder, tekst, objekter i indholdsområdet under navigation/kommandolinjer og anden HTML-kode, der danner rammerne for siden. Sidetykkelse er en måling af denne HTML-kode og bør være begrænset for at sikre optimale sideindlæsningstider.

I denne artikel kan du få hjælp til at forstå, hvordan du kan reducere sidetykkelsen på dine moderne webstedssider.

>[!NOTE]
>Du kan finde flere oplysninger om SharePoint online moderne portaler i [Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>Brug Sidediagnosticering til SharePoint til at analysere sidetykkelse

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint-webstedsside med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om siden under **500KB-resultatet** af ruden Diagnosticeringstest. Resultatet vises med grønt, hvis sidetykkelsen er under den oprindelige værdi, og rød, hvis sidetykkelsen overskrider den oprindelige værdi.

Mulige resultater omfatter:

- **Handling påkrævet** (rød): Sidetykkelse overstiger 500KB
- **Ingen handling påkrævet** (grøn): Sidetykkelse er under 500KB

Hvis **Sidetykkelse under 500.000** KR.-resultatet  vises i sektionen Påkrævet opmærksomhed, kan du klikke på resultatet for at få flere oplysninger.

![Anmodninger om at SharePoint resultater.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>Løse problemer med sidetykkelse

Hvis sidetykkelsen overstiger 500.000 TB, kan du forbedre den samlede sideindlæsningstid ved at reducere antallet af webdele og begrænse sideindhold til en passende grad.

Generelle retningslinjer for reduktion af sidetykkelse omfatter:

- Begræns sideindholdet til et rimeligt beløb, og brug flere sider til relateret indhold.
- Minimer brugen af webdele, der har store egenskabstasker.
- Brug ikke-interaktive opskkumuleringsvisninger, når det er muligt.
- Optimer billedstørrelser ved at tilpasse billederne korrekt ved hjælp af komprimerede billedformater og sikre, at de downloades fra en CDN.

Du kan finde yderligere vejledning til at begrænse sidetykkelsen i følgende artikel:

- [Optimer ydeevnen for sider i SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

Før du foretager siderevisioner for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter ændringen for at se, om det nye resultat er inden for den oprindelige standard, og kontrollér den nye sideindlæsningstid for at se, om der er sket en forbedring.

![Resultater af sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, som f.eks. netværksbelastning, tidspunkt på dagen og andre midlertidige betingelser. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at finde gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Finjustere ydeevnen SharePoint Online](tune-sharepoint-online-performance.md)

[Finjustere ydeevnen Office 365 finjustere ydeevnen](tune-microsoft-365-performance.md)

[Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Netværk, der kan levere indhold](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)