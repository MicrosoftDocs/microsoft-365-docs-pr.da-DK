---
title: SharePoint begrænsninger for moderne portalwebsteder på internettet
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
description: Få mere at vide om anbefalinger af ydeevnen for moderne websteder i SharePoint Online, f.eks. begrænsning af opkald SharePoint og eksterne slutpunkter.
ms.openlocfilehash: 6d09af30f5bdc8866b44047771060ced86362565
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590590"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint begrænsninger for moderne portalwebsteder på internettet

Denne artikel indeholder anbefalinger til ydeevne for moderne portalwebsteder i SharePoint Online. Brug retningslinjerne i denne artikel til at optimere ydeevnen for moderne portalwebsteder og undgå almindelige problemer med ydeevnen.

## <a name="performance-considerations-for-modern-portal-sites"></a>Overvejelser om ydeevnen for moderne portalwebsteder

Ud fra optimering af ydeevnen er der et par karakteristika, der gør moderne portalwebsteder entydige. Den vigtigste forskel mellem samarbejde og portalwebsteder i SharePoint Online er skala. Portalwebsteder forventes generelt at betjene flere sidevisninger til et større antal brugere end samarbejdswebsteder, og de vil sandsynligvis indeholde mere statisk indhold og færre redigerbare ressourcer. Desuden adskiller arkitekturen for moderne websteder sig fra klassiske websteder på den måde, at det meste af den behandling, der er involveret i gengivelse af sider og eksekveringskode, foregår på klienten i stedet for på serveren.

Optimering af ydeevnen for moderne portalwebsteder er primært fokuseret på et par overordnede målsætninger:

- Reducer den samlede størrelse af komponenterne på hver side på webstedet
- Aflæs hosting af almindelige statiske filer, f.eks. billeder, typografiark og scripts, for at CDN
- Begræns opkald SharePoint og eksterne slutpunkter til det, der er nødvendigt
- Undgå dublerede anmodninger om det samme indhold

Mange af retningslinjerne i denne artikel fokuserer på minimering og optimering af opkald SharePoint Online. Gentagne opkald, hver gang en side indlæses, påvirker ydeevnen for brugerne, da oplysningerne hentes fra tjenesten hver gang, selvom de ikke er blevet ændret. Derfor kan anmodninger om at SharePoint kategoriseres enten som opkald, der er almindelige for alle brugere, eller opkald, der kræves for hver enkelt bruger. Resultaterne fra disse to opkaldskategorier bør cachelagres for at optimere brugeroplevelsen.

>[!NOTE]
>Brug [Sidediagnosticering til SharePoint som](./page-diagnostics-for-spo.md) et udgangspunkt til at analysere specifikke målepunkter for ydeevnen på SharePoint onlinewebstedssider.

## <a name="modern-portal-site-limits-and-recommendations"></a>Moderne portalwebstedsgrænser og anbefalinger

|**Grænse**|**Maksimal anbefalet værdi**|**Bemærkninger**|
|:-----|:-----|:-----|:-----|
|Sider og nyhedselementer  <br/> |5.000 pr. websted  <br/> |Vi anbefaler, at antallet af sider og nyhedselementer på et moderne portalwebsted begrænses til under 5.000.  <br/> |
|Webdele på en side  <br/> |20 pr. side  <br/> |Vi anbefaler, at du bruger 20 eller færre webdele pr. side, herunder både out of the box Microsoft-webdele og brugerdefinerede webdele. <br/> Få mere at vide under [Optimer webdelsydeevne SharePoint moderne webstedssider online](modern-web-part-optimization.md).  <br/> |
|Dynamiske webdele på en side  <br/> |4 pr. side  <br/> |Dynamiske webdele, der gør en eller flere forespørgsler til en SharePoint at hente de nyeste data, bør være begrænset til 4 pr. side. _Webdelen_ Nyheder er et eksempel på en dynamisk webdel. <br/> Få mere at vide under [Optimer webdelsydeevne SharePoint moderne webstedssider online](modern-web-part-optimization.md).    <br/> |
|Sikkerhedsgrupper  <br/> |20 pr. websted  <br/> |Antallet af sikkerhedsgrupper påvirker omfanget af mange forespørgsler på moderne portalwebsteder. Vi anbefaler, at du begrænser antallet af sikkerhedsgrupper til så lille et sæt som muligt med højst 20 pr. websted.  <br/> |
|Elementer i webstedsnavigation  <br/> |100 pr. websted  <br/> |Vi anbefaler, at du føjer færre end 100 elementer til webstedsnavigation, og at du gør brug af kontrolelementer til direkte navigation.  <br/> Få mere at vide under [Optimer sidetykkelse på SharePoint moderne webstedssider online](modern-page-weight-optimization.md). <br/> |
|Maksimal billedstørrelse  <br/> |300 kb pr. billede  <br/> |Vi anbefaler at begrænse størrelsen af billeder til 300kb eller mindre og bruge en CDN til at hoste billeder, typografiark og scripts. <br/>Få mere at vide under [Optimer billeder på SharePoint Online-moderne](modern-image-optimization.md) webstedssider og [Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Brugere med redigeringsrettigheder  <br/> |200 brugere pr. websted  <br/> |SharePoint portalwebsteder er optimeret til visning og forbrug af indhold. Redigeringstilladelser på en portal bør være begrænset til en begrænset gruppe af brugere, fordi redigeringstilladelser downloader yderligere kontrolelementer og derfor vil køre langsommere for disse brugere. Et stort antal brugere med redigeringstilladelser vil derfor påvirke den samlede oplevelse. <br/> |
|Tredjeparts iFrames  <br/> |2 pr. side  <br/> |iFrames er uforudsigelige langsomme, fordi de indlæser en separat ekstern side, der indeholder alt tilknyttet indhold som javascript, CSS og frameworkelementer. Hvis du skal bruge iFrames, skal du begrænse deres tal til 2 eller færre pr. side.<br/> Få mere at vide under [Optimer iFrames i SharePoint moderne og klassiske sider på onlinepubliceringswebstedet](modern-iframe-optimization.md). <br/> |
|Opkald til UPA-tjenesten  <br/> |1 pr. bruger pr. time  <br/> |Vi anbefaler, at du ikke _foretager opkald pr_ . anmodning til UPA-tjenesten (Brugerprofilprogram). [Microsoft-Graph API](/graph/call-api) og [PageContext](/javascript/api/sp-page-context/pagecontext) kan bruges til at forespørge efter brugeroplysninger.  <br/> Hvis et UPA-serviceopkald er nødvendigt, skal du foretage et enkelt opkald, når det er nødvendigt, og derefter cachelagre oplysningerne til senere brug i samme session. |
|Opkald til taksonomitjenesten  <br/> |5 pr. bruger pr. time  <br/> |Vi anbefaler, at du ikke _foretager opkald_ pr. anmodning til taksonomitjenesten. Hvis taksonomitjenesteopkald er nødvendige, kan du cachelagre oplysningerne, så de kan genbruges i samme session. <br/> Få mere at vide under [Optimer sideopkald på SharePoint moderne og klassiske publiceringswebstedssider](modern-page-call-optimization.md) online. <br/> |

## <a name="related-topics"></a>Relaterede emner

[Oprettelse af en sund SharePoint portal](/sharepoint/portal-health)

[Finjustere ydeevnen SharePoint Online](tune-sharepoint-online-performance.md)

[Finjustere ydeevnen Office 365 finjustere ydeevnen](tune-microsoft-365-performance.md)

[SharePoint onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Retningslinjer for ydeevne for SharePoint Online-portaler](/sharepoint/dev/solution-guidance/portal-performance)
