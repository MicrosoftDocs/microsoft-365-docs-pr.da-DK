---
title: Brug af webdelen Indholdssøgning i stedet for webdelen indholdsforespørgsel til at forbedre ydeevnen i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du øger ydeevnen ved at erstatte webdelen indholdsforespørgsel med webdelen Indholdssøgning i SharePoint Server 2013 og SharePoint Online.
ms.openlocfilehash: 4c8a97d24320d5380eccc089737947df9b1a0d0b
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139491"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Brug af webdelen Indholdssøgning i stedet for webdelen indholdsforespørgsel til at forbedre ydeevnen i SharePoint Online

I denne artikel beskrives det, hvordan du øger ydeevnen ved at erstatte webdelen indholdsforespørgsel med webdelen indholdssøgning i SharePoint Server 2013 og SharePoint Online.
  
En af de mest effektive nye funktioner i SharePoint Server 2013 og SharePoint Online er webdelen Til indholdssøgning (CSWP). Denne webdel bruger søgeindekset til hurtigt at hente resultater, som vises for brugeren. Brug webdelen indholdssøgning i stedet for CQWP (Indholdsforespørgsel) på dine sider for at forbedre ydeevnen for dine brugere.
  
Hvis du bruger en webdel til indholdssøgning via en webdel til indholdsforespørgsel, vil det næsten altid resultere i en bedre ydeevne for sideindlæsning på SharePoint Online. Der er lidt ekstra konfiguration for at få den rigtige forespørgsel, men belønningerne er forbedret ydeevne og gladere brugere.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Sammenligning af den ydeevne, du får ved at bruge webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel

Følgende eksempler viser de relative ydeevnegevinster, du kan få, når du bruger en webdel til indholdssøgning i stedet for en webdel til indholdsforespørgsel. Effekterne er mere indlysende med en kompleks webstedsstruktur og brede indholdsforespørgsler.
  
Dette eksempelwebsted har følgende egenskaber:
  
- 8 niveauer af underordnede websteder.
    
- Lister, der bruger en brugerdefineret "frugt"-indholdstype.
    
- I webdelen er indholdsforespørgslen bred og returnerer alle elementer med indholdstypen "frugt".
    
- I eksemplet bruges der kun 50 elementer på tværs af de 8 websteder. Effekterne vil blive endnu mere udtalt for websteder med mere indhold.
    
Her er et skærmbillede af resultaterne af webdelen indholdsforespørgsel.
  
![Grafik, der viser indholdsforespørgsel for webdelen.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
I Internet Explorer skal du bruge fanen **Netværk** i F12-udviklerværktøjerne til at se nærmere på svarheaderen. På følgende skærmbillede er værdien for **SPRequestDuration** for denne sideindlæsning 924 millisekunder. 
  
![Skærmbillede, der viser anmodningens varighed på 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** angiver den mængde arbejde, der udføres på serveren for at forberede siden. Hvis du skifter indhold efter forespørgsel webdele med indhold efter søgning, webdele reduceres den tid, det tager at gengive siden, dramatisk. En side med en tilsvarende webdel til indholdssøgning, der returnerer det samme antal resultater, har derimod en **SPRequestDuration-værdi** på 106 millisekunder som vist på dette skærmbillede: 
  
![Skærmbillede, der viser anmodningsvarigheden på 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Tilføjelse af en webdel til indholdssøgning i SharePoint Online

Tilføjelse af en webdel til indholdssøgning svarer til en almindelig webdel til indholdsforespørgslen. Se afsnittet *"Tilføj en webdel til indholdssøgning"* i [Konfigurer en webdel til indholdssøgning i SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Oprettelse af den rigtige søgeforespørgsel til webdelen indholdssøgning

Når du har tilføjet en webdel til indholdssøgning, kan du tilpasse søgningen og returnere de ønskede elementer. Du kan finde detaljerede instruktioner til, hvordan du gør dette, i afsnittet *"Vis indhold ved at konfigurere en avanceret forespørgsel i en webdel til indholdssøgning"* i [Konfigurer en webdel til indholdssøgning i SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Værktøj til oprettelse og test af forespørgsler

Hvis du vil have et værktøj til at oprette og teste komplekse forespørgsler, skal du se [søgeforespørgselsværktøjet](https://github.com/pnp/PnP-Tools/tree/master/Solutions/SharePoint.Search.QueryTool#download-the-tool).
  

