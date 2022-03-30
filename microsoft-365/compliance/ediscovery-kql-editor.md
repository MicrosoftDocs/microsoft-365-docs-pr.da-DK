---
title: Brug KQL-editoren til at opbygge søgeforespørgsler
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Du kan bruge KQL-editoren til at konfigurere eDiscovery-søgeforespørgsler i Indholdssøgning, Grundlæggende eDiscovery og Advanced eDiscovery.
ms.openlocfilehash: 6c553a20116eba478961b606f30fa7af8c4c322e
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/07/2021
ms.locfileid: "63598500"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Brug KQL-editoren til at opbygge søgeforespørgsler

Den nye KQL-forespørgselsoplevelse i søgning efter Microsoft 365 eDiscovery-værktøjer giver feedback og vejledning, når du opbygger søgeforespørgsler i Indholdssøgning, Kerne eDiscovery og Advanced eDiscovery. Når du skriver forespørgsler i editoren, giver den autofuldførelse af understøttede søgbare egenskaber og betingelser og indeholder lister over understøttede værdier til standardegenskaber og -betingelser. Hvis du f.eks. angiver mailegenskaben `kind` i din forespørgsel, viser editoren en liste over understøttede værdier, som du kan vælge. KQL-editoren viser også potentielle forespørgselsfejl i realtid, som du kan rette, før du kører søgningen. Det bedste er, at du kan indsætte komplekse forespørgsler direkte i editoren uden at skulle oprette forespørgsler manuelt ved hjælp af nøgleord og betingelseskort i standardkonstruatoren.
  
Her er de vigtigste fordele ved at bruge KQL-editoren:

- Giver vejledning og hjælper dig med at opbygge søgeforespørgsler fra bunden.

- Gør det hurtigt at indsætte lange og komplekse forespørgsler direkte i editoren. Hvis du f.eks. modtager en kompleks forespørgsel fra en modstridende advokat, kan du indsætte den i KQL-editoren i stedet for at skulle bruge betingelsesgeneratoren.

- Identificerer hurtigt potentielle fejl og viser tip om, hvordan du løser problemerne.

KQL-editoren er også tilgængelig, når du opretter forespørgselsbaserede indholdsbaserede indhold i Core eDiscovery og Advanced eDiscovery.

## <a name="displaying-the-kql-editor"></a>Visning af KQL-editoren

Når du opretter eller redigerer en eDiscovery-søgning, findes muligheden for at få vist og bruge KQL-editoren på siden Betingelser i guiden til søgning eller samlinger.

### <a name="kql-editor-in-content-search-and-core-ediscovery"></a>KQL-editor i Indholdssøgning og Core eDiscovery

![KQL-editor i Indholdssøgning og Core eDiscovery](../media/KQLEditorCore.png)

### <a name="kql-editor-in-advanced-ediscovery"></a>KQL-editor i Advanced eDiscovery

![KQL-editor i Advanced eDiscovery](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Brug af KQL-editoren

De følgende afsnit viser eksempler på, hvordan KQL-editoren kommer med forslag og registrerer potentielle fejl.

### <a name="autocompletion-of-search-properties-and-operators"></a>Autofuldførelse af søgeegenskaber og operatorer

Når du begynder at skrive en søgeforespørgsel i KQL-editoren, viser editoren foreslåede autofuldførelse af understøttede søgeegenskaber (også kaldet egenskabsbegrænsninger), som du kan vælge. Du skal skrive mindst to tegn for at få vist en liste over understøttede egenskaber, der starter med disse to tegn. Følgende skærmbillede viser f.eks. de foreslåede søgeegenskaber, der begynder med `Se`.

![KQL-editoren foreslår understøttede egenskaber](../media/KQLEditorAutoCompleteProperties.png)

Desuden giver editoren også en liste over understøttede operatorer (`:`f.eks. , `<>``=` og ), når du skriver et komplet egenskabsnavn. Følgende skærmbillede viser f.eks. de foreslåede operatorer for `Date` egenskaben.

![KQL-editor foreslår operatorer](../media/KQLEditorOperatorSuggestions.png)

Du kan finde flere oplysninger om de understøttede søgeegenskaber og operatorer under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Forslag til egenskabsværdi

KQL-editoren giver forslag til mulige værdier af nogle egenskaber. Følgende skærmbillede viser f.eks. de foreslåede værdier for `Kind` egenskaben.

![KQL-editoren foreslår værdier til nogle egenskaber](../media/KQLEditorValueSuggestions.png)

Editoren foreslår også en liste over brugere (i UPN-format), når du skriver egenskaber for mailmodtagere, f.eks `From`. , `To`og `Recipients` `Participants`.

![KQL-editor foreslår brugere til egenskaber for modtagermail](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Registrering af potentielle fejl

KQL-editoren registrerer potentielle fejl i søgeforespørgsler og giver en ide om, hvad der forårsager fejlen for at hjælpe dig med at løse fejlen. Editoren angiver også en potentiel fejl, når en egenskab ikke har en tilsvarende handling eller værdi. Potentielle fejl i forespørgslen er fremhævet med rød tekst, og forklaringer og mulige løsninger til fejlen vises i rullelisten med Potentielle fejl. Hvis du f.eks. har indsat følgende forespørgsel i KQL-editoren, registreres fire potentielle fejl.

![Registrering af fejl i KQL-editor](../media/KQLEditorErrorDetection.png)

I dette tilfælde kan du bruge de potentielle fejltip til at foretage fejlfinding og løse forespørgslen.

## <a name="more-information"></a>Flere oplysninger

- Du kan skifte mellem betingelsesgeneratoren og KQL-editoren. Hvis du f.eks. bruger betingelsesgeneratoren til at konfigurere en forespørgsel ved hjælp af feltet Nøgleord og flere betingelseskort, kan du få vist den resulterende forespørgsel i KQL-editoren. Men hvis du opretter en kompleks forespørgsel (med nøgleord og betingelser) i KQL-editoren, vises den resulterende forespørgsel kun i feltet Nøgleord, når du får den vist i betingelsesgeneratoren.

- Hvis du indsætter en kompleks forespørgsel i KQL-editoren, registrerer editoren potentielle fejl og foreslår mulige løsninger for at løse fejl.
