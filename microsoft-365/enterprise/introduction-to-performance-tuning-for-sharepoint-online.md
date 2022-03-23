---
title: Introduktion til justering af ydeevnen for SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: I denne artikel forklares det, hvilke specifikke aspekter du skal overveje, når du designer sider for at opnå den bedste SharePoint Online.
ms.openlocfilehash: deabb059e2121743b35d5519e4b8684a08dd28b4
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63590596"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduktion til justering af ydeevnen for SharePoint Online

I denne artikel forklares det, hvilke specifikke aspekter du skal overveje, når du designer sider for at opnå den bedste SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>SharePoint Online-målepunkter

Følgende generelle målepunkter for SharePoint Online indeholder virkelige data om ydeevne:
  
- Sådan indlæses sider hurtigt
    
- Hvor mange ture påkrævet pr. side
    
- Problemer med tjenesten
    
- Andre ting, der kan medføre forringet ydeevne
    
### <a name="conclusions-reached-because-of-the-data"></a>Konklusioner på baggrund af dataene

Dataene fortæller os:
  
- De fleste af siderne fungerer godt på SharePoint Online.
    
- Sider, der ikke er tilpassede, indlæses hurtigt.
    
- OneDrive for Business, teamwebsteder og systemsider, f._layouts. osv., indlæses alle hurtigt.
    
- De mest langsomme 1 % SharePoint onlinesider tager mere end 5.000 millisekunder at indlæse.
    
En simpel test, du kan bruge til at måle ydeevnen, er at sammenligne indlæsningstiden for din egen portal med indlæsningstiden for OneDrive for Business-startsiden, da den kun bruger få tilpassede funktioner. Dette vil ofte være det første trin, support vil bede dig om at udføre ved fejlfinding af problemer med netværkets ydeevne.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Brug en standardbrugerkonto, når du kontrollerer ydeevnen

En administrator for gruppen af websteder, webstedsejer, redaktør eller bidragyder tilhører en anden sikkerhedsgruppe, har flere tilladelser og har derfor ekstra elementer, SharePoint indlæses på en side.
  
Dette gælder for SharePoint lokalt miljø og SharePoint Online, men i et lokalt scenarie er forskellene ikke så lette at bemærke som i SharePoint Online.
  
For at foretage en korrekt evaluering af, hvordan en side vil fungere for brugerne, skal du bruge en standardbrugerkonto for at undgå at indlæse oprettelseskontrolelementerne og ekstra trafik, der er relateret til sikkerhedsgrupper.
  
## <a name="connection-categories-for-performance-tuning"></a>Forbindelseskategorier til justering af ydeevnen

Du kan kategorisere forbindelserne mellem serveren og brugeren i tre hovedkomponenter. Overvej disse, når du designer SharePoint onlinesider for at få indsigt i indlæsningstider.
  
- **Server** De servere, Microsoft er vært for i datacentre.
    
- **Netværk** Microsoft-netværket, internettet og dit lokale netværk mellem datacenteret og dine brugere.
    
- **Browser** Hvor siden indlæses.
    
Inden for disse tre forbindelser er der typisk fem årsager til 95 % af alle langsomme sider. Hver af disse årsager diskuteres i denne artikel:
  
- Navigationsproblemer
    
- Opsnulning af indhold
    
- Store filer
    
- Mange anmodninger til serveren
    
- Behandling af webdele
    
### <a name="server-connection"></a>Serverforbindelse

Mange af de problemer, der påvirker ydeevnen SharePoint lokalt miljø, gælder også for SharePoint Online.
  
Som man ville forvente, har du langt mere kontrol over, hvordan servere klarer sig med lokale SharePoint. Med SharePoint Online er tingene lidt anderledes. Jo mere arbejde en server skal udføre, jo længere tid tager det at gengive en side. Med SharePoint er de største gerningsmanden i denne forbindelse komplekse sider med flere webdele.
  
SharePoint lokal server
  
![Skærmbillede af lokal server.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Skærmbillede af server, der er online.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Med SharePoint Online kan visse sideanmodninger faktisk ende med at kalde flere servere. Du kan ende med en matrix af anmodninger mellem servere for en enkelt anmodning. Disse interaktioner er dyre set i forhold til sideindlæsning og gør det hele langsomt.
  
Eksempler på disse server til server-interaktioner er:
  
- Web til SQL-servere
    
- Web til programservere
    
Det andet, der kan gøre serverinteraktion langsommere, er cache overser. I modsætning til lokale SharePoint er der meget lille risiko for, at du kommer til at gå til den samme server for en side, du har besøgt tidligere. Dette gør cachelagring af objekter overflødig.
  
### <a name="network-connection"></a>Netværksforbindelse

Med lokale SharePoint der ikke gør brug af et WAN, kan du bruge en højhastighedsforbindelse mellem datacenter og slutbrugere. Generelt er det nemt at administrere set fra et netværksperspektiv.
  
Med SharePoint Online er der flere faktorer, du skal overveje, f.eks.:
  
- Microsoft-netværket
    
- Internettet
    
- Internetudbyderen
    
Uanset hvilken version af SharePoint (og hvilket netværk), du bruger, vil de ting, der typisk medfører, at netværket er optaget, omfatte:
  
- Stor nyttedata
    
- Mange filer
    
- Stor fysisk afstand til serveren
    
En af de funktioner, du kan bruge SharePoint Online, er Microsoft CDN (Content Delivery Network). En CDN er reelt en distribueret samling af servere, der er installeret på tværs af flere datacentre. Med en CDN indhold på sider kan hostes på en server tæt på klienten, selvom klienten er langt væk fra den oprindelige SharePoint Server. Microsoft bruger dette mere i fremtiden til at gemme lokale forekomster af sider, der ikke kan tilpasses, f.eks. startsiden SharePoint Online-administrator. Du kan finde flere oplysninger om CDN'er under [Netværk, der kan levere indhold](content-delivery-networks.md).
  
Noget, du skal være opmærksom på, men muligvis ikke kan gøre meget ved, er din internetudbyders forbindelseshastighed. Et simpelt værktøj til test af hastighed fortæller dig forbindelseshastigheden.
  
### <a name="browser-connection"></a>Browserforbindelse

Der er et par faktorer, du skal overveje i forbindelse med webbrowsere set fra et ydeevneperspektiv.
  
Besøg på komplekse sider vil påvirke ydeevnen. De fleste browsere har kun en lille cache (omkring 90 MB), mens den gennemsnitlige webside typisk er omkring 1,6 MB. Det tager ikke lang tid at blive brugt op.
  
Båndbredden kan også være et problem. Hvis en bruger f.eks. kan se videoer i en anden session, påvirker det ydeevnen i SharePoint session. Du kan ikke forhindre brugere i at streame medier, men du kan styre, hvordan en side indlæses for brugere.
  
Se følgende artikler for at finde forskellige SharePoint tilpasningsteknikker til onlinesider og andre bedste fremgangsmåder, der kan hjælpe dig med at opnå optimal ydeevne.
  
- [Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md)
    
- [Billedoptimering til SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Forsinke indlæsning af billeder og JavaScript i SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minification og bundtning i SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Brug af webdelen Indholdssøgning i stedet for webdelen Indholdsforespørgsel til at forbedre ydeevnen SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Kapacitetsplanlægning og indlæsningstest i SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnosticering af problemer med ydeevnen for SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Brug af objektcachen med SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Sådan gør du: Undgå at blive begrænser eller blokeret i SharePoint Online](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
