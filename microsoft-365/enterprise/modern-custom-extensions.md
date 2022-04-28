---
title: Optimer brugerdefinerede udvidelser på SharePoint online moderne webstedssider
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Få mere at vide om, hvordan du optimerer ydeevnen for brugerdefinerede udvidelser på SharePoint online moderne webstedssider.
ms.openlocfilehash: a31b6e68227d433359537b9655d68c63b5893cce
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093849"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>Optimer ydeevnen for brugerdefinerede udvidelser på SharePoint online moderne webstedssider

Denne artikel hjælper dig med at forstå, hvordan brugerdefinerede udvidelser påvirker ventetid, og hvordan almindelige problemer afhjælpes.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Brug værktøjet Sidediagnosticering til SharePoint til at analysere brugerdefinerede udvidelser

Værktøjet Sidediagnosticering til SharePoint er en browserudvidelse til det nye Microsoft Edge (https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både SharePoint moderne portal online og klassiske sider til udgivelse af websteder. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et defineret sæt ydeevnekriterier. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå [til Brug værktøjet Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint webstedsside med værktøjet Sidediagnosticering for SharePoint, kan du se oplysninger om brugerdefinerede udvidelser, der overstiger den oprindelige metrikværdi i **udvidelserne, påvirker indlæsningstiden**, og/eller resultatet **for for mange anvendte udvidelser** i ruden _Diagnosticeringstests_ 

Mulige resultater omfatter:

- **Opmærksomhed kræves** (rød): Enhver _brugerdefineret_ udvidelse, der tager længere tid end **et** sekund at indlæse. Den samlede indlæsningstid, som vises i testresultaterne, opdeles efter modulindlæsning og init. Hvis der er for mange udvidelser på en side, kan de desuden påvirke indlæsningstiden for siden, og dette fremhæves, hvis der bruges **syv** eller flere udvidelser på siden.
- **Forbedringsmuligheder** (gul) Hvis **der bruges fem** eller flere udvidelser, fremhæves de i dette afsnit som en advarsel, indtil der bruges syv eller flere, som derefter fremhæves som Påkrævet opmærksomhed.
- **Der kræves ingen handling** (grøn): Det tager ikke længere end et sekund at indlæse en udvidelse.

Hvis en udvidelse påvirker indlæsningstiden for siden, eller der er for mange udvidelser på siden, vises resultatet i sektionen **Opmærksomhed påkrævede** i resultaterne. Klik på resultatet for at se detaljer om, hvilken udvidelse der indlæses langsomt, eller for mange udvidelser er blevet fremhævet. Fremtidige opdateringer af sidediagnosticering til SharePoint værktøj kan indeholde opdateringer til analyseregler, så sørg for, at du altid har den nyeste version af værktøjet.

![Resultater for sideindlæsningstid.](../media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

De oplysninger, der er tilgængelige i resultaterne, omfatter:

- **Navn og id** viser identificerende oplysninger, der kan hjælpe dig med at finde udvidelsen på siden
- **Total** viser den samlede tid for udvidelsen til modulindlæsning og -initialisering. Det er den samlede relative tid, det tager for udvidelsen at udføre på siden, fra start til slut.
- **Modulindlæsning** viser den tid, det tager at downloade, evaluere og indlæse udvidelserne JavaScript- og CSS-filer. Derefter starter den Init-processen.
- **Init** viser den tid, det tager for udvidelsen at initialisere dataene.

  Det er et asynkront kald, og init time er beregningen af tiden for funktionen onInit, når det returnerede løfte er løst.

Disse oplysninger er beregnet til at hjælpe designere og udviklere med at foretage fejlfinding af problemer. Disse oplysninger skal gives til dit design- og udviklingsteam.

## <a name="overview-of-extensions"></a>Oversigt over udvidelser

SharePoint Framework (SPFx) Udvidelser kan bruges til at udvide den SharePoint brugeroplevelse. Med SharePoint Framework-udvidelser kan du tilpasse flere facetter af den SharePoint oplevelse, herunder meddelelsesområder, værktøjslinjer og listedatavisninger.

Udvidelser kan have en dårlig indflydelse på ydeevnen af en SharePoint side, da det også kræver CPU- og netværksressourcer at udføre det påkrævede arbejde.

Der er fire typer udvidelser:

- **Programtilpassere** føjer scripts til siden og får adgang til velkendte pladsholdere for HTML-elementer og udvider dem med brugerdefinerede gengivelser.
- **Felttilpassere** leverer ændrede visninger til data for felter på en liste.
- **Kommandosæt** udvider SharePoint kommandooverflader for at tilføje nye handlinger og leverer kode på klientsiden, som du kan bruge til at implementere funktionsmåder.
- **Ændring af søgeforespørgsel (kun prøveversion)** aktiveres, lige før søgeforespørgslen udføres.

## <a name="remediate-extension-performance-issues"></a>Løs problemer med udvidelsesydeevne

Følg vejledningen i dette afsnit for at identificere og afhjælpe problemer med ydeevnen med de udvidelser, der er angivet i **Udvidelser påvirker sideindlæsningstidsresultater** .

>[!NOTE]
>Programtilpassere kan udføres i den tidlige fase i en sides livscyklus, og det kan påvirke ydeevnen af andre udvidelser på siden.

Overvågningsresultaterne i Sidediagnosticeringsværktøj viser to faser i udførelsen af en udvidelse for at hjælpe med at identificere den potentielle påvirkning af ydeevnen.

- **Modulbelastningen** er, hvor lang tid det tager at indlæse udvidelsen, hvilket påvirkes af størrelsen på en udvidelse, så det er en god idé kun at bundte de nødvendige biblioteker i udvidelsen og også vælge lysere biblioteker.
- **Init** er initialiseringstiden for udvidelsen, og udvidelsesudviklere bør overveje, om udvidelsen udfører unødvendigt arbejde eller udfører for mange kommandoer i initialiseringsfasen.

Sideforfattere kan også bruge overvågningsresultatet til at se, om en side har for mange udvidelser, da for mange udvidelser vil påvirke en sides ydeevne negativt.

- **Udvidelsesstørrelse og afhængigheder**
  - Brug af Office 365 CDN er påkrævet til optimal download af statiske ressourcer. Offentlige CDN er at foretrække for _js/css-filer_. Du kan få flere oplysninger om brug af Office 365 CDN under [Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Genbrug strukturer som _React_ og _Fabric-import_, der kommer som en del af SharePoint Framework (SPFx). Du kan få flere oplysninger under [Oversigt over SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Sørg for, at du bruger den nyeste version af SharePoint Framework, og opgrader til nye versioner, efterhånden som de bliver tilgængelige.
- **Datahentning/cachelagring**
  - Hvis udvidelsen er afhængig af ekstra serverkald for at hente data til visning, skal du sikre, at disse server-API'er er hurtige og/eller implementere cachelagring på klientsiden (f.eks. brug af _localStorage_ eller _IndexDB_ til større sæt).
  - Hvis der kræves flere kald for at gengive vigtige data, kan du overveje batching på serveren eller andre metoder til konsolidering af anmodninger til et enkelt kald.
  - Hvis nogle dataelementer kræver en langsommere API, men ikke er kritiske for den indledende gengivelse, kan du også afkoble disse til et separat kald, der udføres, når vigtige data gengives.
  - Hvis flere dele bruger de samme data, kan du bruge et fælles datalag for at undgå dublerede kald.
- **Gengivelsestid**
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