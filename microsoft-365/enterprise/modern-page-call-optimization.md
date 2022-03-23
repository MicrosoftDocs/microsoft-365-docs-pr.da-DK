---
title: Optimer sideopkald i SharePoint moderne og klassiske publiceringswebstedssider
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
description: Få mere at vide om, hvordan du optimerer moderne og klassiske sider på SharePoint Online ved at begrænse antallet af opkald til SharePoint Online-tjenestens slutpunkter.
ms.openlocfilehash: 298e928f339d82f472f73e22998b8762461cc209
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591614"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optimer sideopkald i SharePoint moderne og klassiske publiceringswebstedssider

Begge SharePoint Online-moderne og klassiske publiceringswebsteder indeholder links, der indlæser data fra (eller ringer til) SharePoint-funktioner og CDN'er. Jo flere opkald, der foretages af en side, jo længere tid tager det at indlæse siden. Dette kaldes slutbrugerens **opfattede ventetid eller** **EUPL**.

Denne artikel hjælper dig med at forstå, hvordan du bestemmer antallet og effekten af opkald til eksterne slutpunkter fra dine moderne og klassiske publiceringswebstedssider, og hvordan du begrænser deres effekt på slutbrugerens opfattede ventetid.

>[!NOTE]
>Du kan finde flere oplysninger om SharePoint online moderne portaler i [Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Brug Sidediagnosticering til SharePoint til at analysere sideopkald

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint-webstedsside med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om eksterne opkald i ruden Anmodninger om **SharePoint** i ruden _Diagnosticeringstest_. Linjen vises med grønt, hvis webstedssiden indeholder færre end det oprindelige antal opkald og rød, hvis siden overskrider det oprindelige nummer. Det oprindelige tal er forskelligt for moderne og klassiske sider, fordi klassiske webstedssider bruger HTTP1.1, og moderne sider bruger HTTP2.0:

- Moderne webstedssider må højst indeholde **25** opkald
- Klassiske udgivelsessider må højst indeholde **6** opkald

Mulige resultater omfatter:

- **Handling påkrævet** (rød): Siden overskrider det oprindelige antal opkald
- **Ingen handling påkrævet** (grøn): Siden indeholder færre end det oprindelige antal opkald

Hvis resultatet **anmodninger om SharePoint** vises i sektionen Kræver opmærksomhed, kan  du klikke på resultatet for at få flere oplysninger, herunder det samlede antal opkald på siden og en liste over URL-adresserne.

![Anmodninger om at SharePoint resultater.](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Løse problemer med ydeevnen i forbindelse med for mange opkald på en side

Hvis en side indeholder for mange opkald, kan du bruge listen over URL-adresser i Resultaterne af Anmodninger til **SharePoint** til at afgøre, om der er gentagede opkald, opkald, der skal batches, eller opkald, der returnerer data, der skal cachelagres.

**Batching af REST-opkald** kan hjælpe dig med at reducere den faste ydeevne. Du kan finde flere oplysninger om batching af API-opkald [under Foretage batchanmodninger med REST-API'er](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

**Hvis du bruger en cache** til at gemme resultaterne af et API-opkald, kan det forbedre ydeevnen for en varm anmodning ved at give klienten tilladelse til at bruge de cachelagrede data i stedet for at foretage et ekstra opkald til hver efterfølgende sideindlæsning. Der er flere måder at gribe denne løsning an på, afhængigt af virksomhedskravet. Typisk, hvis dataene vil være de samme for alle brugere, er brug af en cachelagringstjeneste på mellemniveau som [_Azure Redis-cache_](https://azure.microsoft.com/services/cache/) en god mulighed for at reducere API-trafik betydeligt mod et websted, da brugerne vil anmode om data fra cachelagringstjenesten i stedet for direkte fra SPO. De eneste SPO-opkald, der er nødvendige, er at opdatere cachen på det midterste niveau. Hvis dataene vil fluktuere på individuel brugerbasis, kan det være bedst at implementere en klientsidecache, f.eks. LocalStorage eller endda en cookie. Dette vil stadig reducere opkaldsmængde ved at fjerne efterfølgende anmodninger fra den samme bruger i cachevarigheden, men det vil være mindre effektivt end en dedikeret cachelagringstjeneste. PnP gør det muligt at bruge LocalStorage med kun meget lidt yderligere udvikling påkrævet.

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