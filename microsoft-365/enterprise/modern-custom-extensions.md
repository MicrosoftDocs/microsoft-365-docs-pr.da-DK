---
title: Optimer brugerdefinerede udvidelser på SharePoint moderne webstedssider
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Få mere at vide om, hvordan du optimerer ydelsen af brugerdefinerede udvidelser SharePoint moderne webstedssider online.
ms.openlocfilehash: 6493f140a1335b5439707fed94372760ac6fab50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591381"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a>Optimer brugerdefineret udvidelsesydeevne SharePoint moderne webstedssider

I denne artikel kan du få hjælp til at forstå, hvordan du kan afgøre, hvordan brugerdefinerede udvidelser påvirker brugerens opfattede ventetid, og hvordan du kan løse almindelige problemer.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a>Brug Sidediagnosticering til SharePoint til at analysere brugerdefinerede udvidelser

Sidediagnosticering til værktøjet SharePoint er en browserudvidelse til den nye Microsoft Edge –https://www.microsoft.com/edge) og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske publiceringswebstedssider. Værktøjet indeholder en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et defineret sæt kriterier for ydeevne. Hvis du vil installere og få mere at vide om værktøjet Sidediagnosticering til SharePoint, skal du gå til Brug værktøjet [Sidediagnosticering til SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>Værktøjet Sidediagnosticering fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Når du analyserer en SharePoint-webstedsside med værktøjet Sidediagnosticering til SharePoint, kan du se oplysninger om brugerdefinerede udvidelser, der overskrider metrikværdien for den oprindelige plan i Udvidelser påvirker indlæsningstiden  og/eller det anvendte for mange  udvidelser i ruden Diagnosticeringstest  

Mulige resultater omfatter:

- **Handling påkrævet** (rød): Enhver _brugerdefineret_ udvidelse, der tager længere tid **end et** sekund at indlæse. Samlet indlæsningstid som vist i testresultater er opdelt efter modulindlæsning og init. Hvis der er for mange udvidelser på en side, kan de desuden påvirke sideindlæsningstiden, og dette fremhæves, hvis  der bruges syv eller flere udvidelser på siden.
- **Forbedringsmuligheder** (gul) Hvis  der bruges fem eller flere udvidelser, fremhæves de i dette afsnit som en advarsel, indtil der bruges syv eller flere, som derefter fremhæves som Påkrævet opmærksomhed.
- **Ingen handling påkrævet** (grøn): Ingen udvidelse tager længere tid end et sekund at indlæse.

Hvis en udvidelse påvirker sideindlæsningstiden, eller der er for mange udvidelser på siden, vises resultatet i sektionen **Handling** , der er påkrævet i resultaterne. Klik på resultatet for at få vist detaljer om, hvilken udvidelse der indlæses langsomt, eller for mange udvidelser er blevet fremhævet. Fremtidige opdateringer til Sidediagnosticering til SharePoint kan omfatte opdateringer til analyseregler, så sørg for, at du altid har den nyeste version af værktøjet.

![Resultater af sideindlæsningstid.](../media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

De oplysninger, der er tilgængelige i resultaterne, omfatter:

- **Navn og id viser** identifikationsoplysninger, der kan hjælpe dig med at finde udvidelsen på siden
- **Total** viser den samlede tid for udvidelsen til at modulindlæse og initialisere. Det er den samlede relative tid, som udvidelsen bruger på at blive udført på siden fra start til slut.
- **Indlæsning af** moduler viser den tid, det tager at downloade, evaluere og indlæse udvidelser JavaScript- og CSS-filer. Derefter starter programmet Init-processen.
- **Init** viser den tid, det tager at initialisere dataene for udvidelsen.

  Det er et asynkront opkald, og inittid er beregningen af tid for funktionen onInit, når det returnerede løfte bliver løst.

Disse oplysninger kan bruges til at hjælpe designere og udviklere med at foretage fejlfinding af problemer. Disse oplysninger skal leveres til dit design- og udviklingsteam.

## <a name="overview-of-extensions"></a>Oversigt over udvidelser

SharePoint Framework (SPFx) Udvidelser kan bruges til at udvide SharePoint brugeroplevelsen. Med SharePoint Framework-udvidelser kan du tilpasse flere facetter af SharePoint, herunder meddelelsesområder, værktøjslinjer og listedatavisninger.

Udvidelser kan have en dårlig indflydelse på ydeevnen for en SharePoint, da det også tager CPU- og netværksressourcer at udføre det nødvendige arbejde.

Der findes fire typer udvidelser:

- **Programtilpassere** føjer scripts til siden og får adgang til velkendte PLADSholdere for HTML-elementer og udvider dem med brugerdefinerede gengivelser.
- **Felttilpassere** giver ændrede visninger til data for felter i en liste.
- **Kommandosæt** udvider SharePoint til at tilføje nye handlinger og indeholder kode på klientsiden, som du kan bruge til at implementere funktionsmåder.
- **Søgeforespørgselsmodifikator (kun eksempel)** aktiveres, lige før søgeforespørgslen udføres.

## <a name="remediate-extension-performance-issues"></a>Løse problemer med ydeevnen for udvidelser

Følg vejledningen i dette afsnit for at identificere og løse problemer med ydeevnen for udvidelser, der er angivet i Udvidelser, **påvirker resultaterne af sideindlæsningstiden** .

>[!NOTE]
>Programtilpassere kan udføres i de tidlige faser under livscyklussen for en side, og det kan påvirke ydeevnen for andre udvidelser på siden.

Overvågningsresultatet i sidediagnosticeringsværktøjet viser to trin i udførelsen af et filtypenavn for at hjælpe med at identificere den potentielle påvirkning af ydeevnen.

- **Modulbelastning** er, hvor lang tid det tager at indlæse udvidelsen, hvilket påvirkes af størrelsen af en udvidelse, så det er en god ide kun at samle de nødvendige biblioteker i udvidelsen og også vælge lette biblioteker.
- **Init** er initialiseringstiden for udvidelsen og udvidelsesudviklere bør overveje, om udvidelsen udfører unødvendigt arbejde eller udfører for mange kommandoer under initialiseringen.

Sideforfattere kan også bruge overvågningsresultatet for at se, om en side har for mange udvidelser, da for mange udvidelser vil påvirke en sides ydeevne negativt.

- **Udvidelsesstørrelse og -afhængigheder**
  - Brug af Office 365 CDN til optimal statisk ressourceoverførsel. Offentlige CDN er at foretrække for _js/css-filer_. Du kan finde flere oplysninger Office 365 CDN brug af Office 365 Content Delivery Network [(CDN) med SharePoint Online](use-microsoft-365-cdn-with-spo.md).
  - Genbrug frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx). Få mere at vide under [Oversigt over SharePoint Framework](/sharepoint/dev/spfx/sharepoint-framework-overview).
  - Sørg for, at du bruger den nyeste version af SharePoint Framework, og opgrader til nye versioner, efterhånden som de bliver tilgængelige.
- **Dataindhentning/cachelagring**
  - Hvis udvidelsen er afhængig af ekstra serveropkald til at hente data til visning, skal du sikre dig, at disse server-API'er er hurtige og/eller implementere cachelagring på klientsiden (f.eks. ved hjælp af _localStorage_ eller _IndexDB_ til større sæt).
  - Hvis der kræves flere opkald for at gengive vigtige data, kan du overveje at batche på serveren eller andre metoder til at konsolidere anmodninger til et enkelt opkald.
  - Alternativt kan du, hvis nogle dataelementer kræver en langsommere API, men ikke er kritiske for den indledende gengivelse, afkoble dem til et separat opkald, der udføres, når vigtige data gengives.
  - Hvis flere dele bruger de samme data, skal du bruge et fælles datalag for at undgå dublerede opkald.
- **Gengivelsestid**
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