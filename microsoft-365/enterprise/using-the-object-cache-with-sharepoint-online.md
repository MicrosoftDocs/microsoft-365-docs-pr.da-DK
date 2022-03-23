---
title: Brug af objektcachen med SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel forklares forskellen mellem at bruge objektcachen i SharePoint Server 2013 lokalt og SharePoint Online.
ms.openlocfilehash: c763ebb1603ade7fdc98f7728fb03697c5e7425c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591412"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Brug af objektcachen med SharePoint Online

I denne artikel forklares forskellen mellem at bruge objektcachen i SharePoint Server 2013 lokalt og SharePoint Online.
  
Der er en betydelig negativ indvirkning ved at være afhængig af objektcachen i SharePoint Online-installation. Enhver afhængighed af objektcachen i SharePoint Online vil reducere pålideligheden af din side. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Sådan fungerer SharePoint Online og SharePoint Server 2013-objektcachen

Når SharePoint Server 2013 er hostet i det lokale miljø, har kunden private front end-webservere, der er vært for objektcachen. Det betyder, at cachen er dedikeret til én kunde og kun er begrænset af, hvor meget hukommelse der er tilgængelig og tildelt til objektcachen. Da kun én kunde betjenes i det lokale scenarie, har front end webserverne typisk brugere, der foretager anmodninger til de samme websteder igen og igen. Det betyder, at cachen hurtigt bliver fuld og forbliver fuld af listeforespørgselsresultaterne og SharePoint, som dine brugere anmoder om regelmæssigt.
  
![Viser trafik og belastning på lokale front end-webservere.](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Derfor forbedres indlæsningstiden på siden anden gang, en bruger besøger den. Når du har mindst fire indlæst den samme side, cachelagres siden på alle front end-webservere.
  
I modsætning hertil er der SharePoint Online mange flere servere, men også mange flere websteder. Hver bruger kan oprette forbindelse til en anden front end-webserver, som ikke har udfyldt cachen. Eller måske bliver cachen udfyldt for en server, men den næste bruger på front end webserveren anmoder om en side fra et andet websted. Eller selvom den næste bruger anmoder om den samme side som ved deres forrige besøg, bliver de indlæsningsbalanceret til en anden front end webserver, der ikke har den pågældende side i cachen. I dette sidste tilfælde hjælper cachelagring slet ikke brugerne.
  
I følgende figur repræsenterer hver prik en side, som en bruger anmoder om, og hvor den cachelagres. Forskellige farver repræsenterer forskellige kunder, der gør delt brug af SaaS-infrastruktur.
  
![Viser resultaterne af objektcaching i SharePoint Online.](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Som du kan se i diagrammet, er chancen for, at en given bruger rammer en server med den cachelagrede version af deres side meget lille. På grund af den store overførselshastighed og den kendsgerning, at serverne deles mellem mange websteder, varer cachen desuden ikke længe, da der kun er så meget plads til cachelagring tilgængelig.
  
Af alle disse årsager er det ikke en effektiv måde at sikre en god brugeroplevelse og sideindlæsningstider i cachelagrede objekter på i SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Hvis vi ikke kan stole på, at objektcachen forbedrer ydeevnen i SharePoint Online, hvad bruger vi så i stedet?

Da du ikke bør regne med cachelagring i SharePoint Online, bør du evaluere alternative designmetoder for SharePoint, der bruger objektcachen. Det betyder, at du skal bruge metoder til problemer med ydeevnen, som ikke er afhængige af cachelagring af objekter for at opnå gode resultater for brugerne. Dette er beskrevet i nogle af de andre artikler i denne serie og omfatter:
  
- [Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minification og bundtning i SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Forsinke indlæsning af billeder og JavaScript i SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    