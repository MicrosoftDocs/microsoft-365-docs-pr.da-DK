---
title: Opret søgeforespørgsler i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: Brug nøgleord og betingelser til at indsnævre omfanget af søgningen, når der søges efter data ved hjælp af eDiscovery (Premium) i Microsoft 365.
ms.openlocfilehash: cceac6974bacb066201120ac4972393f2323353c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995002"
---
# <a name="build-search-queries-for-collections-in-ediscovery-premium"></a>Opret søgeforespørgsler for samlinger i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du konfigurerer søgeforespørgslen, når du opretter en [samling](collections-overview.md) i en eDiscovery-sag (Premium), kan du bruge nøgleord til at finde bestemt indhold og betingelser for at begrænse omfanget af søgningen for at returnere elementer, der er mest relevante for din juridiske undersøgelse.

![Brug nøgleord og betingelser til at indsnævre resultaterne af en søgning.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Nøgleordssøgninger

Skriv en **nøgleordsforespørgsel** i feltet Nøgleord i søgeforespørgslen. Du kan angive nøgleord, egenskaber for mailmeddelelser, f.eks. datoer for afsendelse og modtagelse, eller dokumentegenskaber, f.eks. filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks **. AND**, **OR**, **NOT** og **NEAR**. Du kan også søge efter følsomme oplysninger (f.eks. cpr-numre) i dokumenter i SharePoint og OneDrive (ikke i mails) eller søge efter dokumenter, der er blevet delt eksternt. Hvis du lader feltet **Nøgleord** være tomt, findes alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne.

## <a name="keyword-list"></a>Nøgleordsliste

Du kan også markere afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord eller nøgleordsudtryk i hver række. Nøgleordene i hver række er forbundet med en logisk operator (der *repræsenteres som c:s i søgeforespørgslens* syntaks), der har samme funktionalitet som operatoren **OR** i den søgeforespørgsel, der oprettes. Det betyder, at elementer, der indeholder nøgleord i en vilkårlig række, findes i søgeresultaterne. Du kan tilføje op til 180 rækker på nøgleordslisten i eDiscovery(Premium)-søgeforespørgsler.

![Brug nøgleordslisten til at få statistikker om hvert nøgleord i forespørgslen.](../media/KeywordListSearch.png)

Hvorfor bruge nøgleordslisten? Du kan få statistikker, der viser, hvor mange elementer der matcher hvert nøgleord på nøgleordslisten. Dette kan hjælpe dig med hurtigt at identificere de nøgleord, der er de mest (og mindst) effektive. Du kan også bruge et nøgleordsudtryk (omgivet af parenteser) i en række på listen over nøgleord. Du kan finde flere oplysninger om søgestatistik under [Indsamlingsstatistik og -rapporter](collection-statistics-reports.md)

## <a name="conditions"></a>Betingelser

Du kan tilføje søgebetingelser for at indsnævre omfanget af en søgning og returnere et mere raffineret sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med den nøgleordsforespørgsel, der er angivet i nøgleordsfeltet, af en logisk operator (der repræsenteres som *c:c* i søgeforespørgslens syntaks), der har samme funktionalitet som **OPERATOREN AND** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser for at blive inkluderet i søgeresultaterne. Sådan hjælper betingelser med at indsnævre dine resultater. Du kan finde en liste over og en beskrivelse af de betingelser, du kan bruge i en søgeforespørgsel, i afsnittet "Søgebetingelser" i [Nøgleordsforespørgsler og søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).
