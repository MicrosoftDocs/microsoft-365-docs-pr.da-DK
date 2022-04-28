---
title: Optimer webdelens ydeevne på SharePoint online moderne webstedssider
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du bruger Sidediagnosticering til at optimere ydeevnen af webdele på SharePoint Online moderne webstedssider.
ms.openlocfilehash: 543ee889831d08b2b465c077cc391a653fa0b9a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093344"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a>Optimer webdelens ydeevne på SharePoint online moderne webstedssider

SharePoint Online moderne webstedssider indeholder webdele, der kan bidrage til den samlede sideindlæsningstid. Denne artikel hjælper dig med at forstå, hvordan webdele på dine sider påvirker brugerens opfattede ventetid, og hvordan almindelige problemer afhjælpes.

> [!NOTE]
> Du kan få flere oplysninger om ydeevnen i SharePoint moderne onlineportaler [under Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a>Brug sidediagnosticering til SharePoint til at analysere webdele

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

> [!NOTE]
> Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint webstedsside med sidediagnosticering for SharePoint værktøj, kan du se oplysninger om webdele, der overstiger den grundlæggende metrikværdi i **webdelene, påvirker sideindlæsningstiden** i ruden _Diagnosticeringstest_.

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Enhver _brugerdefineret_ webdel, der er synlig i visningsporten (skærm synlig del af siden, som indlæses først), der tager længere tid end **to** sekunder at indlæse. Alle _brugerdefinerede_ webdele uden for visningsporten, der tager mere end **fire** sekunder at indlæse. Den samlede indlæsningstid vises i testresultater og opdeles efter modulbelastning, doven belastning, init og gengivelse.
- **Muligheder for forbedring** (gul): Elementer, der kan påvirke indlæsningstiden for sider, vises i dette afsnit og bør gennemses og overvåges. Dette kan omfatte Microsoft-webdele ("out of the box" (OOTB). Resultater for alle Microsoft-webdele, der vises i dette afsnit, rapporteres automatisk til Microsoft, så **der kræves ingen handling**. Du bør kun logge en supportanmodning til undersøgelse, hvis du oplever meget langsom ydeevne på siden, og **alle Microsoft-webdele** på siden vises i resultaterne i afsnittet **Forbedringsmuligheder** . Bemærk, at en fremtidig sidediagnosticering til SharePoint værktøjsopdatering yderligere opdeler resultaterne baseret på den specifikke konfiguration af Microsoft-webdelen.
- **Der kræves ingen handling** (grøn): Ingen webdel tager mere end **to** sekunder at returnere data.

Hvis **webdelene påvirker sideindlæsningstiden** , vises i afsnittet **Opmærksomhed påkrævede** eller **Forbedringsmuligheder** i resultaterne, skal du klikke på resultatet for at få vist oplysninger om, hvilke webdele der indlæses langsomt. Fremtidige opdateringer af sidediagnosticering til SharePoint værktøj kan indeholde opdateringer til analyseregler, så sørg for, at du altid har den nyeste version af værktøjet.

![Resultater af værktøjet Sidediagnosticering.](../media/modern-portal-optimization/pagediag-web-part.png)

De oplysninger, der er tilgængelige i resultaterne, omfatter:

- **Oprettet af** viser, om webdelen er brugerdefineret eller Microsoft OOTB.
- **Navn og id** viser identificerende oplysninger, der kan hjælpe dig med at finde webdelen på siden.
- **Total** viser den samlede tid, som webdelen har til at indlæse, initialisere og gengive webdelen. Det er den samlede relative tid, det tager for webdelen at gengive på siden, fra start til slut.
- **Modulindlæsning** viser den tid, det tager at downloade, evaluere og indlæse udvidelserne JavaScript- og CSS-filer. Derefter starter den Init-processen.
- **Udskudt belastning** viser tiden for udskudt indlæsning af webdele, der ikke ses i hovedsektionen på siden. Der er visse betingelser, hvor der er for mange webdele til at gengive, og de sættes i kø for at gengive for at minimere indlæsningstiden for siden.
- **Init** viser den tid, det tager for webdelen at initialisere dataene.

  Det er et asynkront kald, og init time er beregningen af tiden for funktionen onInit, når det returnerede løfte er løst.

- **Gengiv** viser den tid, det tager at gengive brugergrænsefladen (brugergrænsefladen), når modulbelastningen og Init er fuldført.

  Det er JavaScript-udførelsestiden, hvor DOM skal indsættes i dokumentet (siden).
  Gengivelse af asynkrone ressourcer, f.eks. billeder, kan tage ekstra tid at fuldføre.

Disse oplysninger er beregnet til at hjælpe designere og udviklere med at foretage fejlfinding af problemer. Disse oplysninger skal gives til dit design- og udviklingsteam.

## <a name="remediate-web-part-performance-issues"></a>Løs problemer med webdelens ydeevne

Følg vejledningen i dette afsnit for at identificere og afhjælpe problemer med ydeevnen for de webdele, der er angivet i **webdelene, påvirker sideindlæsningstidsresultater** .

Der er tre kategorier af mulige årsager til dårlig webdelsydeevne. Brug oplysningerne nedenfor til at bestemme, hvilke problemer der gælder for dit scenarie, og løs dem.

- Størrelse og afhængigheder for webdelsscript
  - Optimer det indledende script, der kun gengiver hovedlinjescenariet for _visningstilstand_.
  - Flyt de mindre hyppige scenarier, og rediger tilstandskoden (f.eks. egenskabsruden) for at adskille segmenter ved hjælp af _import()-_ sætningen.
  - Gennemse afhængigheder af _filen package.json_ for helt at fjerne eventuel død kode. Flyt kun alle test-/buildafhængigheder til devDependencies.
  - Brug af Office 365 CDN er påkrævet til optimal download af statiske ressourcer. Offentlige CDN er at foretrække for _js/css-filer_. Du kan få flere oplysninger om brug af Office 365 CDN under [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Genbrug strukturer som _React_ og _Fabric-import_, der kommer som en del af SharePoint Framework (SPFx). Du kan få flere oplysninger under [Oversigt over SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Sørg for, at du bruger den nyeste version af SharePoint Framework, og opgrader til nye versioner, efterhånden som de bliver tilgængelige.
- Datahentning/cachelagring
  - Hvis webdelen er afhængig af ekstra serverkald for at hente data til visning, skal du sikre, at disse server-API'er er hurtige og/eller implementere cachelagring på klientsiden (f.eks. ved hjælp af _localStorage_ eller _IndexedDB_ til større sæt).
  - Hvis der kræves flere kald for at gengive vigtige data, kan du overveje batching på serveren eller andre metoder til konsolidering af anmodninger til et enkelt kald.
  - Hvis nogle dataelementer kræver en langsommere API, men ikke er kritiske for den indledende gengivelse, kan du også afkoble disse til et separat kald, der udføres, når vigtige data gengives.
  - Hvis flere dele bruger de samme data, kan du bruge et fælles datalag for at undgå dublerede kald.
- Gengivelsestid
  - Alle mediekilder som billeder og videoer skal tilpasses grænserne for objektbeholderen, enheden og/eller netværket for at undgå at downloade unødvendige store aktiver. Du kan få flere oplysninger om indholdsafhængigheder under [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Undgå API-kald, der medfører re-flow, komplekse CSS-regler eller komplicerede animationer. Du kan få flere oplysninger under [Minimering af browserombrydning](https://developers.google.com/speed/docs/insights/browser-reflow).
  - Undgå at bruge sammenkædede langvarige opgaver. Opdel i stedet langvarige opgaver i separate køer. Du kan få flere oplysninger under [Optimer JavaScript-udførelse](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).
  - Reserver tilsvarende plads til asynkront gengivelse af medier eller visuelle elementer for at undgå oversprungne rammer og stammen (også kendt som _jank_).
  - Hvis en bestemt browser ikke understøtter en funktion, der bruges til gengivelse, skal du enten indlæse en polyfill eller udelade kørsel af afhængig kode. Hvis funktionen ikke er kritisk, skal du fjerne ressourcer, f.eks. hændelseshandlere, for at undgå hukommelsesfejl.

Før du foretager sideændringer for at løse problemer med ydeevnen, skal du notere sideindlæsningstiden i analyseresultaterne. Kør værktøjet igen efter din revision for at se, om det nye resultat er inden for grundlinjestandarden, og kontrollér indlæsningstiden for den nye side for at se, om der var en forbedring.

![Resultater for sideindlæsningstid.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>Sideindlæsningstiden kan variere afhængigt af en række faktorer, f.eks. netværksbelastning, klokkeslæt på dagen og andre midlertidige forhold. Du bør teste indlæsningstiden for siden et par gange før og efter at have foretaget ændringer for at hjælpe dig med at beregne gennemsnittet af resultaterne.

## <a name="related-topics"></a>Relaterede emner

[Juster SharePoint onlineydeevne](tune-sharepoint-online-performance.md)

[Juster Office 365 ydeevne](tune-microsoft-365-performance.md)

[Ydeevne i den moderne SharePoint oplevelse](/sharepoint/modern-experience-performance)

[Content Delivery Networks](content-delivery-networks.md)

[Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md)
