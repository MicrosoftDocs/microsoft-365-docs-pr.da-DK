---
title: SharePoint Grænser for moderne portalwebsted online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om anbefalinger til ydeevnen for moderne websteder i SharePoint Online, f.eks. begrænsning af kald til SharePoint og eksterne slutpunkter.
ms.openlocfilehash: a0163cd808ce3eb25da8d1c94fb27ed9d238d75a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091143"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint Grænser for moderne portalwebsted online

Denne artikel indeholder anbefalinger til ydeevnen for moderne portalwebsteder i SharePoint Online. Brug retningslinjerne i denne artikel til at optimere ydeevnen af moderne portalwebsteder og undgå almindelige problemer med ydeevnen.

## <a name="performance-considerations-for-modern-portal-sites"></a>Overvejelser i forbindelse med ydeevnen for moderne portalwebsteder

Hvad angår optimering af ydeevnen, er der et par egenskaber, der gør moderne portalwebsteder unikke. Den vigtigste forskel mellem samarbejde og portalwebsteder i SharePoint Online er skalering. Portalwebsteder forventes generelt at levere flere sidevisninger til et større antal brugere end samarbejdswebsteder og vil sandsynligvis indeholde mere statisk indhold og færre redigerbare ressourcer. Desuden adskiller arkitekturen for moderne websteder sig fra klassiske websteder, idet de fleste af de behandlingshandlinger, der er involveret i gengivelse af sider og udførelse af kode, finder sted på klienten i stedet for på serveren.

Optimering af ydeevnen for moderne portalwebsteder fokuserer primært på nogle få overordnede målsætninger:

- Reducer den samlede størrelse af komponenterne på hver webstedsside
- Aflastning af hosting af almindelige statiske filer, f.eks. billeder, typografiark og scripts, til CDN
- Begræns kald til SharePoint og eksterne slutpunkter til det, der er nødvendigt
- Undgå dubletanmodninger for det samme indhold

Mange af retningslinjerne i denne artikel fokuserer på at minimere og optimere kald til SharePoint Online. Hvis du foretager gentagne kald, hver gang en side indlæses, påvirker det brugernes ydeevne, da oplysningerne hentes fra tjenesten hver gang, selvom de ikke er blevet ændret. Anmodninger om SharePoint kan derfor kategoriseres enten som kald, der er fælles for alle brugere, eller kald, der kræves for hver enkelt bruger. Resultater fra disse to opkaldskategorier skal cachelagres for at optimere brugeroplevelsen.

>[!NOTE]
>Brug [værktøjet Sidediagnosticering til SharePoint](./page-diagnostics-for-spo.md) som udgangspunkt for at analysere specifikke målepunkter for ydeevne på SharePoint onlinewebstedssider.

## <a name="modern-portal-site-limits-and-recommendations"></a>Moderne portalwebstedsgrænser og -anbefalinger

|**Grænse**|**Maksimum anbefalede værdi**|**Bemærkninger**|
|:-----|:-----|:-----|:-----|
|Sider og nyhedselementer  <br/> |5.000 pr. websted  <br/> |Vi anbefaler, at du begrænser antallet af sider og nyhedselementer på et moderne portalwebsted til under 5.000.  <br/> |
|Webdele på en side  <br/> |20 pr. side  <br/> |Vi anbefaler, at du bruger 20 eller færre webdele pr. side i alt, herunder både Microsoft-webdele og brugerdefinerede webdele, der er indbyggede. <br/> Du kan få flere oplysninger under [Optimer webdelens ydeevne på SharePoint online moderne webstedssider](modern-web-part-optimization.md).  <br/> |
|Dynamiske webdele på en side  <br/> |4 pr. side  <br/> |Dynamiske webdele, der foretager en eller flere forespørgsler for at SharePoint hente de nyeste data, skal begrænses til 4 pr. side. Webdelen _Nyheder_ er et eksempel på en dynamisk webdel. <br/> Du kan få flere oplysninger under [Optimer webdelens ydeevne på SharePoint online moderne webstedssider](modern-web-part-optimization.md).    <br/> |
|Sikkerhedsgrupper  <br/> |20 pr. websted  <br/> |Antallet af sikkerhedsgrupper påvirker omfanget af mange forespørgsler på moderne portalwebsteder. Vi anbefaler, at du begrænser antallet af sikkerhedsgrupper til så små et sæt som muligt med højst 20 pr. websted.  <br/> |
|Elementer i webstedsnavigation  <br/> |100 pr. websted  <br/> |Vi anbefaler, at du føjer færre end 100 elementer til webstedsnavigationen, og at du bruger køreklare navigationskontrolelementer.  <br/> Du kan få flere oplysninger under [Optimer sidevægt på SharePoint online moderne webstedssider](modern-page-weight-optimization.md). <br/> |
|Maksimal billedstørrelse  <br/> |300 KB pr. billede  <br/> |Vi anbefaler, at du begrænser størrelsen på billeder til 300 kb eller mindre og bruger en CDN til at hoste billeder, typografiark og scripts. <br/>Du kan få flere oplysninger [under Optimer billeder på de moderne webstedssider SharePoint Online](modern-image-optimization.md) og [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md).  <br/> |
|Brugere med redigeringsrettigheder  <br/> |200 brugere pr. websted  <br/> |SharePoint portalwebsteder er optimeret til visning og brug af indhold. Redigeringstilladelser på en portal skal være begrænset til en begrænset gruppe af brugere, fordi redigeringstilladelser henter yderligere kontrolelementer og derfor fungerer langsommere for disse brugere. Et stort antal brugere med redigeringstilladelser vil derfor påvirke den overordnede oplevelse. <br/> |
|IFrames fra tredjepart  <br/> |2 pr. side  <br/> |iFrames er uforudsigelige langsomme, fordi de indlæser en separat ekstern side, herunder alt tilknyttet indhold, f.eks. javascript, CSS og framework-elementer. Hvis du skal bruge iFrames, skal du begrænse deres antal til 2 eller færre pr. side.<br/> Du kan få flere oplysninger [under Optimer iFrames i SharePoint Online moderne og klassiske udgivelseswebstedssider](modern-iframe-optimization.md). <br/> |
|Opkald til UPA-tjenesten  <br/> |1 pr. bruger pr. time  <br/> |Vi anbefaler, at du ikke foretager opkald _pr. anmodning_ til UPA-tjenesten (Brugerprofilprogram). [Microsoft Graph API](/graph/call-api) og [PageContext](/javascript/api/sp-page-context/pagecontext) kan bruges til at forespørge om brugeroplysninger.  <br/> Hvis et UPA-tjenesteopkald er nødvendigt, skal du foretage et enkelt opkald, når det er nødvendigt, og derefter cachelagre oplysningerne til genbrug i den samme session. |
|Kald til taksonomitjenesten  <br/> |5 pr. bruger pr. time  <br/> |Vi anbefaler, at du ikke foretager opkald _pr. anmodning_ til taksonomitjenesten. Hvis taksonomitjenestekald er nødvendige, skal du cachelagre oplysningerne til genbrug i den samme session. <br/> Du kan få flere oplysninger [under Optimer sidekald i SharePoint Online moderne og klassiske udgivelseswebstedssider](modern-page-call-optimization.md). <br/> |

## <a name="related-topics"></a>Relaterede emner

[Oprettelse af en sund SharePoint-portal](/sharepoint/portal-health)

[Juster SharePoint onlineydeevne](tune-sharepoint-online-performance.md)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)

[SharePoint Online-grænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Vejledning til ydeevne for SharePoint Online-portaler](/sharepoint/dev/solution-guidance/portal-performance)
