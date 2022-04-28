---
title: Brug af objektcachen med SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: I denne artikel forklares forskellen mellem at bruge objektcachen i SharePoint Server 2013 i det lokale miljø og SharePoint Online.
ms.openlocfilehash: db0a150927bc3a2078d4dc0ca7491471b7973f2d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077783"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Brug af objektcachen med SharePoint Online

I denne artikel forklares forskellen mellem at bruge objektcachen i SharePoint Server 2013 i det lokale miljø og SharePoint Online.
  
Der er betydelige negative konsekvenser ved at være afhængig af objektcachen i SharePoint Online-udrulning. Alle afhængigheder af objektcachen i SharePoint Online vil reducere pålideligheden af din side. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Sådan fungerer objektcachen SharePoint Online og SharePoint Server 2013

Når SharePoint Server 2013 hostes i det lokale miljø, har kunden private frontendwebservere, der hoster objektcachen. Det betyder, at cachen er dedikeret til én kunde og kun er begrænset af, hvor meget hukommelse der er tilgængelig og allokeret til objektcachen. Da der kun serveres én kunde i scenariet i det lokale miljø, får frontendwebserverne typisk brugere, der foretager anmodninger til de samme websteder igen og igen. Det betyder, at cachen bliver fuld hurtigt og forbliver fuld af resultaterne af listeforespørgslen og SharePoint objekter, som dine brugere anmoder om regelmæssigt.
  
![Viser trafik og belastning på frontendwebservere i det lokale miljø.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Det betyder, at indlæsningstiden for siden forbedres, anden gang en bruger besøger en side. Efter mindst fire belastninger af den samme side cachelagres siden på alle frontendwebserverne.
  
I modsætning hertil er der i SharePoint Online mange flere servere, men også mange flere websteder. Hver bruger kan oprette forbindelse til en anden frontendwebserver, der ikke har cachen udfyldt. Eller måske udfyldes cachen for en server, men den næste bruger af frontendwebserveren anmoder om en side fra et andet websted. Eller selvom den næste bruger anmoder om den samme side som ved deres forrige besøg, er vedkommende belastningsafbalanceret på en anden frontendwebserver, der ikke har den pågældende side i cachen. I dette sidste tilfælde hjælper cachelagring slet ikke brugerne.
  
I følgende figur repræsenterer hver prik en side, som en bruger anmoder om, og hvor den cachelagres. Forskellige farver repræsenterer forskellige kunder, der bruger SaaS-infrastrukturen delt.
  
![Viser resultaterne af cachelagring af objekter i SharePoint Online.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Som du kan se fra diagrammet, er chancerne for, at en given bruger rammer en server med den cachelagrede version af deres side, slank. På grund af det store dataoverførselshastighed og det faktum, at serverne deles mellem mange websteder, varer cachen ikke længe, da der kun er så meget plads til cachelagring tilgængelig.
  
Af alle disse årsager er det ikke en effektiv måde at sikre en god brugeroplevelse og indlæsningstider for sider på i SharePoint Online, hvis brugerne får cachelagrede objekter.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Hvis vi ikke kan stole på objektcachen for at forbedre ydeevnen i SharePoint Online, hvad bruger vi så i stedet?

Da du ikke skal være afhængig af cachelagring i SharePoint Online, skal du evaluere alternative designmetoder for SharePoint tilpasninger, der bruger objektcachen. Det betyder, at du skal bruge metoder til problemer med ydeevnen, som ikke er afhængige af cachelagring af objekter for at opnå gode resultater for brugerne. Dette er beskrevet i nogle af de andre artikler i denne serie og omfatter:
  
- [Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minification og bundling i SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Udskyd indlæsning af billeder og JavaScript i SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    