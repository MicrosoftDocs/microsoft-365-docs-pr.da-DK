---
title: Brug af webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel til at forbedre ydeevnen SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Lær at øge ydeevnen ved at erstatte webdelen Indholdsforespørgsel med webdelen Indholdssøgning i SharePoint Server 2013 og SharePoint Online.
ms.openlocfilehash: d41983a5771e42d357ae4d2adb5864e2a74fdd57
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594273"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Brug af webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel til at forbedre ydeevnen SharePoint Online

I denne artikel beskrives det, hvordan du kan øge ydeevnen ved at erstatte webdelen Indholdsforespørgsel med webdelen Indholdssøgning i SharePoint Server 2013 og SharePoint Online.
  
En af de mest effektive nye funktioner i SharePoint Server 2013 og SharePoint Online er webdelen Indholdssøgning (CSWP). Denne webdel bruger søgeindekset til hurtigt at hente resultater, der vises for brugeren. Brug webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel (CQWP) på dine sider til at forbedre ydeevnen for dine brugere.
  
Brug af webdelen Indholdssøgning frem for webdelen Indholdsforespørgsel vil næsten altid give betydeligt bedre sideindlæsningsydeevne SharePoint online. Der er en smule yderligere konfiguration for at få den rigtige forespørgsel, men gevinsten er forbedret ydeevne og mere tilfredse brugere.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Sammenligning af den ydeevne, du opnår ved at bruge webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel

Følgende eksempler viser den relative effektivitet, du opnår, når du bruger en webdel til indholdssøgning i stedet for en webdel til indholdsforespørgsel. Virkningerne er mere tydelige med en kompleks webstedsstruktur og meget brede indholdsforespørgsler.
  
Dette eksempelwebsted har følgende egenskaber:
  
- 8 niveauer af underordnede websteder.
    
- Lister med en brugerdefineret "frugt"-indholdstype.
    
- I webdelen er indholdsforespørgslen bred og returnerer alle elementer med indholdstypen "frugt".
    
- I eksemplet bruges kun 50 elementer på tværs af 8 websteder. Virkningerne vil være endnu mere udtale for websteder med mere indhold.
    
Her er et skærmbillede af resultaterne af webdelen Indholdsforespørgsel.
  
![Grafik, der viser indholdsforespørgsel for webdel.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
I Internet Explorer skal du bruge **fanen Netværk** i F12-udviklerværktøjerne til at se nærmere på detaljerne for svaroverskriften. I følgende skærmbillede indlæses værdien for **SPRequestDuration** for denne side på 924 millisekunder. 
  
![Skærmbillede med varighed af anmodning på 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** angiver den mængde arbejde, der er udført på serveren for at forberede siden. Hvis du skifter indhold efter webdele indhold med indhold fra webdele reduceres den tid, det tager at gengive siden, dramatisk. I modsætning hertil har en side med en tilsvarende webdel Indholdssøgning, der returnerer det samme antal resultater, en **værdi for SPRequestDuration** på 106 millisekunder, som vist i dette skærmbillede: 
  
![Skærmbillede med varighed af anmodning på 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Tilføje en webdel til indholdssøgning i SharePoint Online

At tilføje en webdel til indholdssøgning minder meget om en almindelig webdel til indholdsforespørgsel. Se afsnittet *"Tilføje en webdel til indholdssøgning"* [i Konfigurere en webdel til indholdssøgning SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Oprette den rigtige søgeforespørgsel til din webdel til indholdssøgning

Når du har tilføjet en webdel til indholdssøgning, kan du afgrænse søgningen og returnere de ønskede elementer. Hvis du vil have detaljeret vejledning til at gøre dette, skal du se afsnittet "Vis indhold ved at konfigurere en avanceret forespørgsel i en webdel til indholdssøgning *"* i Konfigurere en webdel til indholdssøgning [i SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Forespørgselsopbygning og testværktøj

Du kan finde et værktøj til at opbygge og teste komplekse forespørgsler i [søgeforespørgselsværktøjet](https://sp2013searchtool.codeplex.com/) på Codeplex. 
  

