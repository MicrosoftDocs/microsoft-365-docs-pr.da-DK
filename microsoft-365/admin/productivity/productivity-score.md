---
title: Microsoft Productivity Score
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
description: Få mere at vide om, hvordan Microsoft Produktivitetsscore afspejler målinger af personer og teknologi og sammenligner dem med organisationer af lignende størrelse.
ms.openlocfilehash: 24a84c3780ec3787b76f78acbe9c0c109a27c639
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589381"
---
# <a name="microsoft-productivity-score"></a>Microsoft Productivity Score 

Produktivitetsscore understøtter rejsen til digital transformation med indsigt i, hvordan din organisation bruger Microsoft 365 og de teknologioplevelser, der understøtter den. Organisationens resultat afspejler måleenheder for personer og teknologi og kan sammenlignes med benchmarks fra organisationer, der ligner dine.

Den omfatter:

- **Målepunkter,** der kan hjælpe dig med at se, hvor du er på din digitale transformationsrejse.
- **Insights om** dataene, så du lettere kan identificere muligheder for at forbedre produktiviteten og tilfredsheden i organisationen.
- **Anbefalede handlinger**, du kan udføre for at hjælpe organisationen med at bruge Microsoft 365 produkter effektivt.

Vi leverer målepunkter, viden og anbefalinger på to områder: 

- **Personers oplevelser:** Kvantificerer, hvordan organisationen arbejder ved Microsoft 365 kategorier som f.eks. indholdsamarbejde, mobilitet, kommunikation, møder og teamwork.  

    For hver af de nævnte kategorier kigger vi på offentlig forskning for at identificere nogle bedste fremgangsmåder og tilknyttede fordele i form af organisatorisk effektivitet. For example, Forrester research has shown that when people collaborate and share content in the cloud (instead of emailing attachments), they can save up to 100 minutes a week. Desuden sætter vi tal på brugen af disse bedste fremgangsmåder i din organisation for at hjælpe dig med at se, hvor du er på din digitale transformationsrejse. 

- **Teknologioplevelser:** Din organisation afhænger af pålidelig og højtydende teknologi samt effektiv brug af Microsoft 365. [Slutpunktsanalyse hjælper](https://aka.ms/endpointanalytics) dig med at forstå, hvordan organisationen kan påvirkes af problemer med ydeevne og sundhed med din hardware og software. Tilstand for Microsoft 365-apps hjælper dig med at forstå, om enhederne i din organisation kører Microsoft 365 apps på anbefalede kanaler.

## <a name="before-you-begin"></a>Før du begynder

Se [Hvad er Endpoint Analytics for at](/mem/analytics/overview) få en oversigt og forudsætninger for detaljer. Du kan få mere at vide Microsoft 365 om netværksforbindelsesindsigt ved at [læse oversigten over netværksforbindelsen](../../enterprise/microsoft-365-networking-overview.md).

For at få personoplevelser til data skal du have et Microsoft 365 til virksomheder eller Office 365 til enterprise-abonnement. For slutpunktsanalysedata for din lejer skal du føje Microsoft Intune til dit abonnement. Intune hjælper med at beskytte din organisations data ved at administrere enheder og apps. Når du har Intune, kan du aktivere slutpunktsanalyser i Intune-oplevelsen. Du kan få mere at Microsoft Intune oplysninger i [Microsoft Intune dokumentationen](/mem/intune/). 

> [!NOTE]
> Det er ikke påkrævet en licens til Workplace Analytics for at få funktionerne til Produktivitetsscore.

Produktivitetsscore er kun tilgængeligt i Microsoft 365 Administration og kan kun benyttes af it-fagfolk, der har en af følgende roller:  

- Global administrator
- Exchange administratorer
- SharePoint administrator
- Skype for Business administrator
- Teams administrator
- Global læser
- Rapportlæser
- Læser til oversigt over brugsrapporter

> [!NOTE]
> Kun en it-fagperson med rollen global administrator kan tilmelde sig eller tilmelde sig en lejer for Produktivitetsscore.

Den rollebaserede adgangskontrolmodel for Productivity Score hjælper organisationer med yderligere digitale transformationsindsatser med Microsoft 365 ved at give fleksibilitet til at tildele roller til it-fagfolk i en organisation.

Microsoft er forpligtet til at beskytte enkeltpersoners personlige oplysninger. Dette [dokument til](privacy.md)  beskyttelse af personlige oplysninger forklarer de kontrolelementer, vi giver dig som din organisations it-administrator, for at sikre, at der kan handles på oplysningerne, uden at der gårs på kompromis med den tillid, du placerer i Microsoft.

Du kan få adgang til oplevelsen fra Microsoft 365 Administration under **ReportsProductivity** >  Score.
  
## <a name="how-the-score-is-calculated"></a>Sådan beregnes scoren

Din Produktivitetsscore er baseret på de kombinerede kategorier for personer og teknologioplevelser. Hver kategori vægtes lige med 100 point i alt. Det højest mulige produktivitetsresultat er 800.

### <a name="score-categories"></a>Scorekategorier 

- Kommunikation (100 point)
- Møder (100 point)
- Indholdsamarbejde (100 point)
- Teamwork (100 point)
- Mobilitet (100 punkter)
- Slutpunktsanalyse (100 point)
- Netværksforbindelse (100 punkter)
- Microsoft 365 Apps tilstand (100 point)
- **Samlet muligt = 800 point**
 
I hver scorekategori sætter vi tal på nøgleindikatorerne for, hvordan organisationen bruger Microsoft 365 sin rejse mod digital transformation. Vi giver dig 28- og 180-dagsvisninger af de vigtigste aktiviteter. Vi leverer også understøttende målepunkter, der ikke er en del af scoreberegningen, men som er vigtige for at hjælpe dig med at identificere den underliggende forbrugsstatistik og konfigurationer, som du kan håndtere.

### <a name="products-included-in-productivity-score"></a>Produkter inkluderet i Produktivitetsscore 

Produktivitetsscore omfatter data fra Exchange, SharePoint, OneDrive, Teams, Word, Excel, PowerPoint, OneNote, Outlook, Yammer og Skype.

Organisationens resultat opdateres dagligt og afspejler brugerhandlinger, der er fuldført i de sidste 28 (herunder den aktuelle dag).

## <a name="interpreting-your-organizations-productivity-score"></a>Fortolkning af din organisations produktivitetsscore 

Startsiden for Productivity Score viser din organisations samlede score og scorehistorik samt det primære indsigt for hver kategori.

:::image type="content" source="../../media/prodscore-landing.png" alt-text="Siden Produktivitetsscore i Rapporter.":::

**Din organisations resultat vises** som en procentværdi og i point. Du kan se dine point i tælleren og de maksimalt mulige point i nævneren.

**Peer-benchmarks** giver dig mulighed for at sammenligne din organisations resultat med organisationer som din. Peer-benchmarken for kategorierne for personers oplevelser beregnes som gennemsnittet af målinger inden for et sæt lignende organisationer. Sættet af organisationer består af organisationer i dit område med et lignende antal licenserede brugere, typer af licenser, branche og leje med Microsoft 365.

> [!NOTE]
> Microsoft bruger interne data til at bestemme den branche, som en organisation har tilknytning til. Lejere under en overordnet organisation tilknyttes den samme branche som den overordnede organisation. Organisationer kan ikke få vist eller redigere branchetilknytninger.

Slutpunktsanalyse-peer-benchmarken omfatter mål for enhedens startydeevne og anbefalede softwarekonfiguration baseret på samlede medianværdier på tværs af alle lejere.

For netværksforbindelsen er den anbefalede benchmark 80 punkter.

Sektionen **Opdeling af** pointtal indeholder en oversigt over din produktivitetsscore med benchmarks for personer og teknologioplevelsesområder.

Scorehistorikken viser, hvordan scoren i hver kategori har ændret sig inden for de seneste seks måneder.

People **experiences and** **Technology experiences areas** contain the primary insights for the categories in those areas. Du kan vælge hver kategori for at få en dybere indsigt.

## <a name="category-details-pages"></a>Sider med kategoridetaljer

Hver side med kategoridetaljer viser den primære indsigt og understøttende målepunkter samt relaterede undersøgelser og handlinger, du kan udføre for at fremme ændringer i organisationen. Forskning understøtter vigtigheden og logisk bag den primære indsigt for hver kategori. Læs [Forrester-rapporten for at få flere oplysninger](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2PBrb).

Detaljesiderne er:
- [Samarbejde om indhold – personers oplevelser](content-collaboration.md)
- [Kommunikation – oplevelser med mennesker](communication.md)
- [Møder – oplevelser med mennesker](meetings.md)
- [Mobilitet – personers oplevelser](mobility.md)
- [Teamwork – oplevelser med mennesker](teamwork.md)
- [Microsoft 365 Apps tilstand – teknologioplevelser](apps-health.md)
- [Endpoint Analytics](/mem/analytics/productivity-score)

## <a name="business-continuity-special-report"></a>Særlige rapport om forretningskontinuitet

Rapporten Virksomhedskontinuitet er en tidsbegrænset Workplace Intelligence-rapport, der er tilgængelig for alle Microsoft 365-kunder, så de kan hjælpe dem med at vejlede deres organisationer i denne udfordrende tid.  

Denne rapport hjælper organisationer med at forstå: 

- Hvordan samarbejde og kommunikation påvirkes af skiftet til fjernarbejde. 

- Påvirkningen af balancen mellem arbejdsliv og privatliv, efterhånden som folk tilpasser sig arbejdet hjemmefra. 

- Uanset om fjernmøder understøtter effektiv beslutningstagning.

[Få mere at vide om rapporten Om forretningskontinuitet](/Workplace-Analytics/tutorials/bcrps)

[Få mere at vide om Microsoft Graph](/graph/)

> [!NOTE]
> Brugerne har også mulighed for at få produktivitetsindsigt fra [MyAnalytics-dashboardet](/workplace-analytics/myanalytics/use/dashboard-2).


## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Del dine tanker om Produktivitetsscore og dine idéer til, hvordan du kan forbedre det. Brug **Feedback-sektionerne** i produktet, og/eller kontakt produktivitetsscore-teamet prodscorefeedback@microsoft.com.

## <a name="related-content"></a>Relateret indhold

[Overvåg Microsoft 365 aktivitet ved hjælp af rapporter](../../admin/activity-reports/activity-reports.md) (artikel)\
[Aktivér Microsoft 365 forbrugsanalyse](../../admin/usage-analytics/enable-usage-analytics.md) (artikel)\
[Oversigt over Microsoft 365 Administration](Oversigt over Microsoft 365 Administration](.. /admin-overview/admin-center-overview.md) (video)