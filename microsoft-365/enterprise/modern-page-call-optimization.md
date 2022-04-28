---
title: Optimer sidekald på SharePoint Online moderne og klassiske udgivelseswebstedssider
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
description: Få mere at vide om, hvordan du optimerer moderne og klassiske udgivelseswebstedssider i SharePoint Online ved at begrænse antallet af kald til SharePoint Online-tjenesteslutpunkter.
ms.openlocfilehash: 7636e1cf2dfac6dc7fea4158f1f22a7336d6485e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101221"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>Optimer sidekald på SharePoint Online moderne og klassiske udgivelseswebstedssider

Både SharePoint Online moderne og klassiske udgivelseswebsteder indeholder links, der indlæser data fra (eller foretager kald til) SharePoint funktioner og CDN'er. Jo flere opkald en side foretager, jo længere tid tager det at indlæse siden. Dette kaldes **slutbrugerens opfattelse af ventetid** eller **EUPL**.

Denne artikel hjælper dig med at forstå, hvordan du kan bestemme antallet og virkningen af kald til eksterne slutpunkter fra dine moderne og klassiske udgivelseswebstedssider, og hvordan du begrænser deres effekt på ventetider, som slutbrugeren opfatter.

>[!NOTE]
>Du kan få flere oplysninger om ydeevnen i SharePoint moderne onlineportaler [under Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a>Brug værktøjet Sidediagnosticering til SharePoint til at analysere sidekald

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint webstedsside med værktøjet Sidediagnosticering for SharePoint, kan du se oplysninger om eksterne opkald i **anmodningerne om SharePoint** resultere i ruden _Diagnosticeringstest_. Linjen vises med grønt, hvis webstedssiden indeholder færre end det oprindelige antal opkald, og rød, hvis siden overskrider det oprindelige tal. Det oprindelige tal er forskelligt for moderne og klassiske sider, fordi klassiske webstedssider bruger HTTP1.1, og moderne sider bruger HTTP2.0:

- Moderne webstedssider må ikke indeholde mere end **25** opkald
- Klassiske udgivelsessider må ikke indeholde mere end **6** opkald

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Siden overskrider det oprindelige antal opkald
- **Der kræves ingen handling** (grøn): Siden indeholder færre end det oprindelige antal kald

Hvis resultatet **Anmodninger om SharePoint** vises i afsnittet **Opmærksomhed kræves**, kan du klikke på resultatet for at få flere oplysninger, herunder det samlede antal kald på siden og en liste over URL-adresserne.

![Anmodninger om SharePoint resultater.](../media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a>Løs problemer med ydeevnen, der er relateret til for mange kald på en side

Hvis en side indeholder for mange kald, kan du bruge listen over URL-adresser i **anmodningerne om at SharePoint** resultater til at afgøre, om der er gentagne kald, kald, der skal batches, eller kald, der returnerer data, der skal cachelagres.

**Batching af REST-kald** kan hjælpe med at reducere ydeevnen. Du kan få flere oplysninger om batching af API-kald under [Foretag batchanmodninger med REST API'erne](/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).

**Hvis du bruger en cache** til at gemme resultaterne af et API-kald, kan det forbedre ydeevnen af en varm anmodning ved at tillade klienten at bruge de cachelagrede data i stedet for at foretage et ekstra kald for hver efterfølgende sideindlæsning. Der er flere måder at nærme sig denne løsning på, afhængigt af forretningskravet. Hvis dataene vil være ens for alle brugere, er det typisk en god mulighed at reducere API-trafik i forhold til et websted ved hjælp af en cachelagringstjeneste på mellemniveau som [_Azure Redis-cachen_](https://azure.microsoft.com/services/cache/), da brugerne anmoder om dataene fra cachelagringstjenesten i stedet for direkte fra SPO. Det eneste SPO-kald, der kræves, er at opdatere cachen på det midterste niveau. Hvis dataene varierer på individuel brugerbasis, kan det være bedst at implementere en cache på klientsiden, f.eks. LocalStorage eller endda en cookie. Dette vil stadig reducere opkaldsmængderne ved at fjerne efterfølgende anmodninger fra den samme bruger i cachens varighed, men det vil være mindre effektivt end en dedikeret cachelagringstjeneste. PnP giver dig mulighed for at bruge LocalStorage med lidt yderligere udvikling påkrævet.

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