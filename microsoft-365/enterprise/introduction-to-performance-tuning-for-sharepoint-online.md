---
title: Introduktion til justering af ydeevnen for SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel forklares det, hvilke specifikke aspekter du skal overveje, når du designer sider for at opnå den bedste ydeevne i SharePoint Online.
ms.openlocfilehash: b31696766d3201b6677bf0c63108fad72c3ed49d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100737"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduktion til justering af ydeevnen for SharePoint Online

I denne artikel forklares det, hvilke specifikke aspekter du skal overveje, når du designer sider for at opnå den bedste ydeevne i SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>SharePoint onlinemålepunkter

Følgende brede målepunkter for SharePoint Online leverer data om ydeevnen i den virkelige verden:
  
- Hvor hurtige sider indlæses
    
- Hvor mange rundture der kræves pr. side
    
- Problemer med tjenesten
    
- Andre ting, der forårsager forringelse af ydeevnen
    
### <a name="conclusions-reached-because-of-the-data"></a>Konklusioner, der er nået på grund af dataene

Dataene fortæller os:
  
- De fleste af siderne klarer sig godt på SharePoint Online.
    
- Ikke-tilpassede sider indlæses hurtigt.
    
- OneDrive for Business, teamwebsteder og systemsider, f.eks. _layouts osv., indlæses hurtigt.
    
- Den langsomste 1 % af SharePoint Online-sider tager mere end 5.000 millisekunder at indlæse.
    
En enkel benchmarktest, du kan bruge, er at måle ydeevnen ved at sammenligne indlæsningstiden på din egen portal med indlæsningstiden for den OneDrive for Business startside, da den bruger få brugerdefinerede funktioner. Dette vil ofte være det første trin Support beder dig om at fuldføre, når du foretager fejlfinding af problemer med netværkets ydeevne.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Brug en standardbrugerkonto, når du kontrollerer ydeevnen

En administrator af en gruppe af websteder, ejeren af webstedet, editoren eller bidragyderen tilhører andre sikkerhedsgrupper, har flere tilladelser og har derfor ekstra elementer, der SharePoint indlæses på en side.
  
Dette gælder for SharePoint i det lokale miljø og SharePoint Online, men i et scenarie i det lokale miljø bliver forskellene ikke så nemme at bemærke som i SharePoint Online.
  
Hvis du vil evaluere, hvordan en side vil fungere korrekt for brugerne, skal du bruge en standardbrugerkonto for at undgå at indlæse kontrolelementerne til oprettelse og ekstra trafik, der er relateret til sikkerhedsgrupper.
  
## <a name="connection-categories-for-performance-tuning"></a>Forbindelseskategorier til justering af ydeevnen

Du kan kategorisere forbindelserne mellem serveren og brugeren i tre hovedkomponenter. Overvej disse, når du designer SharePoint Online-sider for at få indsigt i indlæsningstider.
  
- **Server** De servere, som Microsoft hoster i datacentre.
    
- **Netværk** Microsoft-netværket, internettet og dit lokale netværk mellem datacenteret og dine brugere.
    
- **Browser** Hvor siden er indlæst.
    
Inden for disse tre forbindelser er der typisk fem årsager, der forårsager 95 % af de langsomme sider. Hver af disse årsager beskrives i denne artikel:
  
- Navigationsproblemer
    
- Opløftet indhold
    
- Store filer
    
- Mange anmodninger til serveren
    
- Behandling af webdele
    
### <a name="server-connection"></a>Serverforbindelse

Mange af de problemer, der påvirker ydeevnen med SharePoint i det lokale miljø, gælder også for SharePoint Online.
  
Som du ville forvente, har du langt mere kontrol over, hvordan servere klarer sig med SharePoint i det lokale miljø. Med SharePoint Online er tingene lidt anderledes. Jo mere arbejde en server udfører, jo længere tid tager det at gengive en side. Med SharePoint er de største syndere i denne henseende komplekse sider med flere webdele.
  
SharePoint Server i det lokale miljø
  
![Skærmbillede af serveren i det lokale miljø.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Skærmbillede af serveren online.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Med SharePoint Online kan visse sideanmodninger faktisk ende med at kalde flere servere. Du kan ende med en matrix af anmodninger mellem servere for en individuel anmodning. Disse interaktioner er dyre ud fra et sideindlæsningsperspektiv og vil gøre tingene langsomme.
  
Eksempler på disse server til server-interaktioner er:
  
- Web til SQL-servere
    
- Web til programservere
    
Den anden ting, der kan gøre serverinteraktioner langsommere, er, at cachen går glip af noget. I modsætning til SharePoint i det lokale miljø er der en lille chance for, at du rammer den samme server for en side, du tidligere har besøgt. Dette gør cachelagring af objekter forældet.
  
### <a name="network-connection"></a>Netværksforbindelse

Med SharePoint i det lokale miljø, der ikke bruger et WAN, kan du bruge en hurtig forbindelse mellem datacenter og slutbrugere. Generelt er det nemt at administrere fra et netværksperspektiv.
  
Med SharePoint Online er der et par flere faktorer, du skal overveje, f.eks.:
  
- Microsoft-netværket
    
- Internettet
    
- Internetudbyderen
    
Uanset hvilken version af SharePoint (og hvilket netværk) du bruger, omfatter ting, der normalt medfører, at netværket er optaget, følgende:
  
- Stor nyttedata
    
- Mange filer
    
- Stor fysisk afstand til serveren
    
En funktion, du kan bruge i SharePoint Online, er Microsoft CDN (Content Delivery Network). Et CDN er grundlæggende en distribueret samling af servere, der er installeret på tværs af flere datacentre. Med en CDN kan indhold på sider hostes på en server tæt på klienten, selvom klienten er langt væk fra den oprindelige SharePoint Server. Microsoft vil fremover bruge dette til at gemme lokale forekomster af sider, der ikke kan tilpasses, f.eks. startsiden for SharePoint Online-administrator. Du kan få flere oplysninger om CDN'er under [Netværk til levering af indhold](content-delivery-networks.md).
  
Noget, du skal være opmærksom på, men måske ikke være i stand til at gøre meget ved, er forbindelseshastigheden for din internetudbyder. Et simpelt værktøj til test af hastighed fortæller dig forbindelseshastigheden.
  
### <a name="browser-connection"></a>Browserforbindelse

Der er et par faktorer, du skal overveje i forbindelse med webbrowsere fra et ydeevneperspektiv.
  
Besøg af komplekse sider vil påvirke ydeevnen. De fleste browsere har kun en lille cache (ca. 90 MB), mens den gennemsnitlige webside typisk er omkring 1,6 MB. Det tager ikke lang tid at vænne sig til det.
  
Båndbredde kan også være et problem. Hvis en bruger f.eks. ser videoer i en anden session, påvirker dette ydeevnen af din SharePoint side. Selvom du ikke kan forhindre brugere i at streame medier, kan du styre, hvordan en side indlæses for brugerne.
  
Se følgende artikler om forskellige teknikker til tilpasning af SharePoint onlinesider og andre bedste fremgangsmåder for at hjælpe dig med at opnå optimal ydeevne.
  
- [Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md)
    
- [Billedoptimering til SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Udskyd indlæsning af billeder og JavaScript i SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minification og bundling i SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Brug af webdelen Indholdssøgning i stedet for webdelen indholdsforespørgsel til at forbedre ydeevnen i SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Kapacitetsplanlægning og indlæsningstest i SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnosticering af problemer med ydeevnen med SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Brug af objektcachen med SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Sådan gør du: Undgå at blive begrænset eller blokeret i SharePoint Online](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
