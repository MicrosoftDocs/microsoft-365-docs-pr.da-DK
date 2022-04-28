---
title: Optimer billeder på SharePoint online moderne webstedssider
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
description: Få mere at vide om, hvordan du bruger de værktøjer, der er inkluderet i SharePoint Online, til at optimere billeder på SharePoint online moderne webstedssider.
ms.openlocfilehash: 102555e25e48af19432a26e6e2a0cb17c78044b3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093827"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>Optimer billeder på SharePoint online moderne webstedssider

Denne artikel hjælper dig med at forstå, hvordan du optimerer billeder på SharePoint online moderne webstedssider.

Du kan finde oplysninger om optimering af billeder på klassiske udgivelseswebsteder under [Billedoptimering for SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>Du kan få flere oplysninger om ydeevnen i SharePoint moderne onlineportaler [under Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>Brug sidediagnosticering til SharePoint værktøj til at analysere billedoptimering

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer et SharePoint moderne websted med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om store billeder i ruden _Diagnosticeringstest_.

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Siden indeholder **et eller flere** billeder på over 300 KB i størrelse
- **Der kræves ingen handling** (grøn): Siden indeholder ingen billeder over 300 KB i størrelse

Hvis resultatet **Store billeder registreret** vises i sektionen **Opmærksomhed kræves** i resultaterne, kan du klikke på resultatet for at få vist flere oplysninger.

![Resultater af værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>Løs problemer med store billeder

Hvis en side indeholder billeder på over 300 KB, skal du vælge resultatet **Store billeder registreret** for at se, hvilke billeder der er for store. På moderne SharePoint Online-sider leveres gengivelser af billeder automatisk, og størrelsen afhænger af størrelsen af browservinduet og løsningen på klientovervågningen. Du bør altid optimere billeder til brug på internettet, før du uploader til SharePoint Online. Meget store billeder reduceres automatisk i størrelse og opløsning, hvilket kan resultere i uventede gengivelsesegenskaber.

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