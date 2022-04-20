---
title: Brug KQL-editoren til at oprette søgeforespørgsler
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
description: Du kan bruge KQL-editoren til at konfigurere eDiscovery-søgeforespørgsler i Indholdssøgning, eDiscovery (Standard) og eDiscovery (Premium).
ms.openlocfilehash: cbd7adb02c926477fd81568ed950ebd16110c79b
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993792"
---
# <a name="use-the-kql-editor-to-build-search-queries"></a>Brug KQL-editoren til at oprette søgeforespørgsler

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Den nye KQL-forespørgselsoplevelse i Microsoft 365 søgning i eDiscovery-værktøjer giver feedback og vejledning, når du opretter søgeforespørgsler i Indholdssøgning, Microsoft Purview eDiscovery (Standard) og eDiscovery (Premium). Når du skriver forespørgsler i editoren, giver den automatisk fuldførelse af understøttede egenskaber og betingelser, der kan søges i, og indeholder lister over understøttede værdier for standardegenskaber og -betingelser. Hvis du f.eks. angiver mailegenskaben `kind` i din forespørgsel, viser editoren en liste over understøttede værdier, som du kan vælge. KQL-editoren viser også potentielle forespørgselsfejl i realtid, som du kan løse, før du kører søgningen. Det bedste af det hele er, at du kan indsætte komplekse forespørgsler direkte i editoren uden at skulle oprette forespørgsler manuelt ved hjælp af nøgleords- og betingelseskortene i standardbetingelsesgeneratoren.
  
Her er de vigtigste fordele ved at bruge KQL-editoren:

- Indeholder vejledning og hjælper dig med at oprette søgeforespørgsler fra bunden.

- Gør det muligt hurtigt at indsætte lange, komplekse forespørgsler direkte i editoren. Hvis du f.eks. modtager en kompleks forespørgsel fra modsatrettede råd, kan du indsætte det i KQL-editoren i stedet for at skulle bruge betingelsesgeneratoren.

- Identificerer hurtigt potentielle fejl og viser tip om, hvordan du kan løse problemer.

KQL-editoren er også tilgængelig, når du opretter forespørgselsbaserede ventepositioner i eDiscovery (Standard) og eDiscovery (Premium).

## <a name="displaying-the-kql-editor"></a>Visning af KQL-editoren

Når du opretter eller redigerer en eDiscovery-søgning, er indstillingen til at få vist og bruge KQL-editoren placeret på siden **Betingelser** i guiden Til søgning eller samlinger.

### <a name="kql-editor-in-content-search-and-ediscovery-standard"></a>KQL-editor i indholdssøgning og eDiscovery (Standard)

![KQL-editor i indholdssøgning og eDiscovery (Standard)](../media/KQLEditorCore.png)

### <a name="kql-editor-in-ediscovery-premium"></a>KQL-editor i eDiscovery (Premium)

![KQL-editor i eDiscovery (Premium)](../media/KQLEditorAdvanced.png)

## <a name="using-the-kql-editor"></a>Brug af KQL-editoren

Følgende afsnit viser eksempler på, hvordan KQL-editoren giver forslag og registrerer potentielle fejl.

### <a name="autocompletion-of-search-properties-and-operators"></a>Autofuldførelse af søgeegenskaber og operatorer

Når du begynder at skrive en søgeforespørgsel i KQL-editoren, viser editoren foreslået automatisk fuldførelse af understøttede søgeegenskaber (også kaldet *egenskabsbegrænsninger*), som du kan vælge. Du skal skrive mindst to tegn for at få vist en liste over understøttede egenskaber, der starter med disse to tegn. Følgende skærmbillede viser f.eks. de foreslåede søgeegenskaber, der starter med `Se`.

![KQL-editor foreslår understøttede egenskaber](../media/KQLEditorAutoCompleteProperties.png)

Derudover foreslår editoren også en liste over understøttede operatorer (f.eks. `:`, `=` og `<>`), når du skriver et komplet egenskabsnavn. Følgende skærmbillede viser f.eks. de foreslåede operatorer for egenskaben `Date` .

![KQL-editor foreslår operatorer](../media/KQLEditorOperatorSuggestions.png)

Du kan finde flere oplysninger om de understøttede søgeegenskaber og -operatorer under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

### <a name="property-value-suggestions"></a>Forslag til egenskabsværdi

KQL-editoren indeholder forslag til mulige værdier for nogle egenskaber. Følgende skærmbillede viser f.eks. de foreslåede værdier for `Kind` egenskaben.

![KQL-editor foreslår værdier for nogle egenskaber](../media/KQLEditorValueSuggestions.png)

Editoren foreslår også en liste over brugere (i UPN-format), når du skriver egenskaber for mailmodtagere, f.eks`From`. , `To``Recipients` og `Participants`.

![KQL-editor foreslår brugere til egenskaber for modtagermail](../media/KQLEditorRecipientSuggestions.png)

### <a name="detection-of-potential-errors"></a>Registrering af potentielle fejl

KQL-editoren registrerer potentielle fejl i søgeforespørgsler og giver et tip om, hvad der forårsager fejlen, for at hjælpe dig med at løse fejlen. Editoren angiver også en potentiel fejl, når en egenskab ikke har en tilsvarende handling eller værdi. Potentielle fejl i forespørgslen er fremhævet med rød tekst, og forklaringer og mulige rettelser til fejlen vises i rullemenuen **Potentielle fejl** . Hvis du f.eks. indsatte følgende forespørgsel i KQL-editoren, ville der blive registreret fire potentielle fejl.

![Fejlregistrering i KQL-editor](../media/KQLEditorErrorDetection.png)

I dette tilfælde kan du bruge de potentielle fejltip til at foretage fejlfinding og løse forespørgslen.

## <a name="more-information"></a>Flere oplysninger

- Du kan skifte mellem betingelsesgeneratoren og KQL-editoren. Hvis du f.eks. bruger betingelsesgeneratoren til at konfigurere en forespørgsel ved hjælp af feltet Nøgleord og flere betingelseskort, kan du få vist den resulterende forespørgsel i KQL-editoren. Men hvis du opretter en kompleks forespørgsel (med nøgleord og betingelser) i KQL-editoren, vises den resulterende forespørgsel kun i feltet Nøgleord, når du får den vist i betingelsesgeneratoren.

- Hvis du indsætter en kompleks forespørgsel i KQL-editoren, registrerer editoren potentielle fejl og foreslår mulige løsninger til løsning af fejl.
