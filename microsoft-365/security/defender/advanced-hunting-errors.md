---
title: Håndter fejl i avanceret Microsoft 365 Defender
description: Forstå de fejl, der vises, når du bruger avanceret jagt
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skema, kusto, timeout, ressourcer, fejl, ukendt fejl, grænser, kvote, parameter, tildeling
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 8bd7d4b5191ff88fe2bd958c87e930b91f64dd5e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63593563"
---
# <a name="handle-advanced-hunting-errors"></a>Håndter avancerede jagtfejl

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt


Avanceret jagt viser fejl, der informeres ved syntaksfejl, og når forespørgsler rammer [foruddefinerede kvoter og forbrugsparametre](advanced-hunting-limits.md). Se tabellen nedenfor for at få tip til, hvordan du løser eller undgår fejl.

| Fejltype | Årsag | Løsning | Eksempler på fejlmeddelelser |
|--|--|--|--|
| Syntaksfejl | Forespørgslen indeholder ukendt navne, herunder referencer til ikke-eksisterende operatorer, kolonner, funktioner eller tabeller. | Sørg for, at [referencer til Kusto-operatorer og -](/azure/data-explorer/kusto/query/) funktioner er korrekte. Kontrollér [skemaet](advanced-hunting-schema-tables.md) for de korrekte avancerede jagtkolonner, funktioner og tabeller. Omslut variable strenge i anførselstegn, så de genkendes. Mens du skriver dine forespørgsler, kan du bruge forslagene til autofuldførelse fra IntelliSense. | `A recognition error occurred.` |
| Semantiske fejl | Mens forespørgslen bruger gyldige operator-, kolonne-, funktions- eller tabelnavne, er der fejl i dens struktur og resulterende logik. I nogle tilfælde identificerer avanceret jagt den specifikke operator, der forårsagede fejlen. | Kontrollér for fejl i strukturen i forespørgslen. Se [Kusto-dokumentationen](/azure/data-explorer/kusto/query/) for vejledning. Mens du skriver dine forespørgsler, kan du bruge forslagene til autofuldførelse fra IntelliSense. |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| Timeouts | En forespørgsel kan kun køres inden for [en begrænset periode, før der er tid.](advanced-hunting-limits.md) Denne fejl kan forekomme oftere, når du kører komplekse forespørgsler. | [Optimere forespørgslen](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| CPU-begrænsning | Forespørgsler i samme lejer har overskredet DE [CPU-ressourcer, der](advanced-hunting-limits.md) er tildelt baseret på lejerstørrelse. | Tjenesten kontrollerer CPU-ressourceforbruget hvert 15. minut og dagligt og viser advarsler, når brugen overstiger 10 % af den tildelte kvote. Hvis du når 100 % brug, blokerer tjenesten forespørgsler indtil efter den næste daglige eller 15-minutters cyklus. [Optimer dine forespørgsler for at undgå at ramme CPU-kvoter](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| Resultatstørrelsesgrænsen er overskredet  | Den samlede størrelse af resultatsættet for forespørgslen har overskredet den maksimale størrelse. Denne fejl kan opstå, hvis resultatsættet er så stort, at afkortning ved grænsen på 10.000 poster ikke kan reducere det til en acceptabel størrelse. Resultater, der har flere kolonner med indhold, der kan tilpasses, vil mere sandsynligt blive påvirket af denne fejl. | [Optimere forespørgslen](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| Unødvendigt ressourceforbrug | Forespørgslen har brugt store mængder ressourcer og er blevet stoppet i at fuldføre. I nogle tilfælde identificerer avanceret jagt den specifikke operator, der ikke blev optimeret. | [Optimere forespørgslen](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| Ukendte fejl | Forespørgslen mislykkedes på grund af en ukendt årsag. | Prøv at køre forespørgslen igen. Kontakt Microsoft via portalen, hvis forespørgsler fortsat returnerer ukendte fejl. | `An unexpected error occurred during query execution. Please try again in a few minutes.`



## <a name="related-topics"></a>Relaterede emner
- [Avancerede bedste fremgangsmåder på jagt](advanced-hunting-best-practices.md)
- [Kvoter og brugsparametre](advanced-hunting-limits.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Oversigt over Kusto-forespørgselssprog](/azure/data-explorer/kusto/query/)