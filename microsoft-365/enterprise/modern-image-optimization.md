---
title: Optimer billeder på SharePoint moderne webstedssider online
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
description: Få mere at vide om, hvordan du bruger værktøjerne i SharePoint Online til at optimere billeder SharePoint moderne webstedssider online.
ms.openlocfilehash: 85280dfc903c56c89308c50fa94979fd98b2003c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590993"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optimer billeder på SharePoint moderne webstedssider online

Denne artikel hjælper dig med at forstå, hvordan du optimerer billeder SharePoint moderne webstedssider online.

Du kan finde oplysninger om optimering af billeder i klassiske publiceringswebsteder [i Billedoptimering SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Du kan finde flere oplysninger om SharePoint online moderne portaler i [Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Brug Sidediagnosticering til SharePoint til at analysere billedoptimering

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer et SharePoint websted med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om store billeder i ruden _Diagnosticeringstest_.

Mulige resultater omfatter:

- **Handling påkrævet** (rød): Siden indeholder **et eller flere billeder** , der er større end 300KB
- **Ingen handling påkrævet** (grøn): Siden indeholder ingen billeder, der er større end 300KB

Hvis det **registrerede resultat Store billeder** vises i sektionen **Opmærksomhed påkrævet** i resultaterne, kan du klikke på resultatet for at få vist flere detaljer.

![Resultater fra værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Løse problemer med store billeder

Hvis en side indeholder billeder, der er større end 300.000, skal du vælge resultatet Store billeder for at se, hvilke billeder der er for store. I moderne SharePoint Online-sider leveres gengivelser af billeder automatisk og størrelse afhængigt af størrelsen på browservinduet og opløsningen på klientskærmen. Du bør altid optimere billeder til webbrug, før du uploader til SharePoint Online. Meget store billeder reduceres automatisk i størrelse og opløsning, hvilket kan medføre uventede gengivelsesegenskaber.

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