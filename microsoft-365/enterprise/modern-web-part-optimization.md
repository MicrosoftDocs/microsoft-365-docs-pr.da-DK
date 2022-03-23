---
title: Optimer ydeevnen for webdele på SharePoint moderne webstedssider
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: Få mere at vide om, hvordan du bruger Sidediagnosticering til at optimere ydeevnen af webdele SharePoint moderne webstedssider online.
ms.openlocfilehash: 15b15e56a1c490cab86f225c5784d8bb9adcb36e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590571"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>Optimer ydeevnen for webdele på SharePoint moderne webstedssider

SharePoint online moderne webstedssider indeholder webdele, der kan bidrage til den samlede sideindlæsningstider. Denne artikel hjælper dig med at forstå, hvordan du bestemmer, hvordan webdele på dine sider påvirker brugerens opfattede ventetid, og hvordan du kan løse almindelige problemer.

> [!NOTE]
> Du kan finde flere oplysninger om SharePoint online moderne portaler i [Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Brug Sidediagnosticering til SharePoint til at analysere webdele

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

> [!NOTE]
> Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint-webstedsside med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om webdele, der overskrider metrikværdien for den  oprindelige plan i webdelene påvirker sideindlæsningstiden i  ruden Diagnosticeringstest.

Mulige resultater omfatter:

- **Handling påkrævet** (rød):  Enhver brugerdefineret webdel, der er synlig i visningsporten (den synlige skærmdel på siden, som indlæses først), som  tager længere end to sekunder at indlæse. Eventuelle _brugerdefinerede_ webdele uden for visningsporten, som tager mere end **fire** sekunder at indlæse. Samlet indlæsningstid vises i testresultater og er opdelt efter modulbelastning, doven belastning, init og gengiv.
- **Forbedringsmuligheder** (gul): Elementer, der kan påvirke sideindlæsningstiden, vises i dette afsnit og skal gennemses og overvåges. Dette kan omfatte "out of the box" (OOTB) Microsoft-webdele. Resultater for eventuelle Microsoft-webdele, der vises i dette afsnit, rapporteres automatisk til Microsoft, **så der kræves ingen handling**. Du bør kun logge en supportbillet til undersøgelse, hvis du oplever meget langsom ydeevne på siden, og alle **Microsoft-webdele** på siden vises i resultaterne i sektionen **Forbedrede muligheder.** Bemærk, at en fremtidig Sidediagnosticering til SharePoint vil opdele resultaterne yderligere baseret på den specifikke konfiguration af Microsoft-webdelen.
- **Ingen handling påkrævet** (grøn): Ingen webdel tager længere tid end **to sekunder** at returnere data.

Hvis **webdele** påvirker sideindlæsningstiden, vises enten i sektionen Påkrævede  oplysninger eller Forbedringsmuligheder i resultaterne, skal du klikke på resultatet for at få vist detaljer om, hvilke webdele der indlæses langsomt. Fremtidige opdateringer til Sidediagnosticering til SharePoint kan omfatte opdateringer til analyseregler, så sørg for, at du altid har den nyeste version af værktøjet.

![Resultater fra værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-web-part.png)

De oplysninger, der er tilgængelige i resultaterne, omfatter:

- **Udført af** viser, om webdelen er brugerdefineret eller Microsoft OOTB.
- **Navn og id** viser identifikationsoplysninger, der kan hjælpe dig med at finde webdelen på siden.
- **Total** viser den samlede tid, som webdelen må bruge til at modulindlæse, initialisere og gengive. Det er den samlede relative tid, som webdelen tager at gengive på siden fra start til slut.
- **Indlæsning af** moduler viser den tid, det tager at downloade, evaluere og indlæse udvidelser JavaScript- og CSS-filer. Derefter starter programmet Init-processen.
- **Lazy Load** viser tiden for udskudt indlæsning af webdele, der ikke kan ses i hoveddelen af siden. Der er visse betingelser, hvor der er for mange webdele til at gengive, og de er i kø til at gengive for at minimere sideindlæsningstiden.
- **Init** viser den tid, det tager for webdelen at initialisere dataene.

  Det er et asynkront opkald, og inittid er beregningen af tid for funktionen onInit, når det returnerede løfte bliver løst.

- **Gengiv** viser den tid, det tager at gengive brugergrænsefladen (brugergrænsefladen), når modulindlæsningen og Init er fuldført.

  Det er JavaScript-eksekveringstiden, der skal bruges til at indsætte DOM i dokumentet (side).
  Gengivelse af asynkrone ressourcer, f.eks. billeder, kan tage ekstra tid at fuldføre.

Disse oplysninger kan bruges til at hjælpe designere og udviklere med at foretage fejlfinding af problemer. Disse oplysninger skal leveres til dit design- og udviklingsteam.

## <a name="remediate-web-part-performance-issues"></a>Løse problemer med webdelens ydeevne

Følg vejledningen i dette afsnit for at identificere og løse problemer med ydeevnen for webdele, der er angivet i webdelene, påvirker **sideindlæsningstidsresultaterne** .

Der er tre kategorier af mulige årsager til dårlig ydeevne for webdelen. Brug oplysningerne nedenfor til at afgøre, hvilke problemer der gælder for scenariet, og afhjælpe dem.

- Størrelse og afhængighed af webdelsscript
  - Optimer det indledende script, der gengiver hovedlinjescenariet _kun for visningstilstand_.
  - Flyt de mindre hyppige scenarier og redigeringstilstandskode (f.eks. egenskabsruden) for at adskille dele ved hjælp af _import()-_ sætningen.
  - Gennemse afhængigheder af _package.json-filen_ for at fjerne alle dødt kode helt. Flyt kun eventuelle test/buildafhængigheder til devDependencies.
  - Brug af Office 365 CDN til optimal statisk ressourceoverførsel. Offentlige CDN er at foretrække for _js/css-filer_. Du kan finde flere oplysninger Office 365 CDN brug af Office 365 Content Delivery Network [(CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Genbrug frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx). Få mere at vide under [Oversigt over SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Sørg for, at du bruger den nyeste version af SharePoint Framework, og opgrader til nye versioner, efterhånden som de bliver tilgængelige.
- Dataindhentning/cachelagring
  - Hvis webdelen er afhængig af ekstra serveropkald til at hente data til visning, skal du sikre dig, at disse server-API'er er hurtige og/eller implementere cachelagring på klientsiden (f.eks. ved hjælp af _localStorage_ eller _IndexedDB_ til større sæt).
  - Hvis der kræves flere opkald for at gengive vigtige data, kan du overveje at batche på serveren eller andre metoder til at konsolidere anmodninger til et enkelt opkald.
  - Alternativt kan du, hvis nogle dataelementer kræver en langsommere API, men ikke er kritiske for den indledende gengivelse, afkoble dem til et separat opkald, der udføres, når vigtige data gengives.
  - Hvis flere dele bruger de samme data, skal du bruge et fælles datalag for at undgå dublerede opkald.
- Gengivelsestid
  - Alle mediekilder som f.eks. billeder og videoer skal være tilpasset til begrænsningerne for beholderen, enheden og/eller netværket for at undgå at downloade unødvendige store aktiver. Du kan finde flere oplysninger om [indholdsafhængigheder under Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Undgå API-opkald, der forårsager omflow og komplekse CSS-regler eller komplicerede animationer. Få mere at vide under [Minimer browserombrydning](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Undgå at bruge sammenkædede opgaver, der kører længe. I stedet kan du opdele opgaver, der kører længe, i separate køer. Få mere at vide under [Optimer JavaScript-udførelse](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Reserver tilsvarende plads til asynkron gengivelse af medier eller visuelle elementer for at undgå springede rammer og hakkende (også kaldet _jank_).
  - Hvis en bestemt browser ikke understøtter en funktion, der bruges i gengivelse, kan du enten indlæse en polyfyld eller udelade kørende afhængig kode. Hvis funktionen ikke er kritisk, kan du skaffe dig af med ressourcer som f.eks. hændelsesbehandlere for at undgå hukommelseslækager.

Før du foretager siderevisioner for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter ændringen for at se, om det nye resultat er inden for den oprindelige standard, og kontrollér den nye sideindlæsningstid for at se, om der er sket en forbedring.

![Resultater af sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, som f.eks. netværksbelastning, tidspunkt på dagen og andre midlertidige betingelser. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at finde gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Finjustere ydeevnen SharePoint Online](tune-sharepoint-online-performance.md)

[Finjustere ydeevnen Office 365 finjustere ydeevnen](tune-microsoft-365-performance.md)

[Ydeevnen i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Netværk, der kan levere indhold](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
