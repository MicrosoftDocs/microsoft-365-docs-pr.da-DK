---
title: Opbygge søgeforespørgsler i Advanced eDiscovery
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
description: Brug nøgleord og betingelser til at indsnævre omfanget af søgningen, når du søger efter data ved hjælp Advanced eDiscovery i Microsoft 365.
ms.openlocfilehash: 8ad708b9733dd7d96f1025f116a31a92d757afd2
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63587280"
---
# <a name="build-search-queries-for-collections-in-advanced-ediscovery"></a>Opbygge søgeforespørgsler til samlinger i Advanced eDiscovery

Når du konfigurerer søgeforespørgslen[](collections-overview.md), når du opretter en samling i en Advanced eDiscovery-sag, kan du bruge nøgleord til at finde bestemt indhold og betingelser for at begrænse omfanget af søgningen til at returnere de elementer, der er mest relevante for din juridiske undersøgelse.

![Brug nøgleord og betingelser til at indsnævre resultaterne af en søgning.](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>Nøgleordssøgninger

Skriv en nøgleordsforespørgsel **i feltet** Nøgleord i søgeforespørgslen. Du kan angive nøgleord, egenskaber for mails, f.eks. datoerne sendt og modtaget, eller dokumentegenskaber, f.eks. filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. **OG**, **ELLER**, **IKKE** og **I NÆRHEDEN**. Du kan også søge efter følsomme oplysninger (f.eks. cpr-numre) i dokumenter i SharePoint og OneDrive (ikke i mails) eller søge efter dokumenter, der er blevet delt eksternt. Hvis du lader feltet **Nøgleord** være tomt, vises alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne.

## <a name="keyword-list"></a>Listen Nøgleord

Alternativt kan du markere afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord eller nøgleord i hver række. Nøgleordene i hver række forbindes af en logisk operator (der er repræsenteret som *c:s* i søgeforespørgslens syntaks), der i funktionalitet svarer til **ELLER-operatoren** i den søgeforespørgsel, der oprettes. Det betyder, at elementer, der indeholder et vilkårligt nøgleord i en række, findes i søgeresultaterne. Du kan tilføje op til 180 rækker på listen over nøgleord Advanced eDiscovery søgeforespørgsler.

![Brug listen med nøgleord til at få statistik for hvert nøgleord i forespørgslen.](../media/KeywordListSearch.png)

Hvorfor bruge listen over nøgleord? Du kan få vist statistik, der viser, hvor mange elementer der svarer til hvert nøgleord på listen over nøgleord. Dette kan hjælpe dig med hurtigt at identificere de nøgleord, der er mest (og mindst) effektive. Du kan også bruge et nøgleord (omgivet af parenteser) i en række på listen over nøgleord. Du kan finde flere oplysninger om søgestatistik i [Indsamling af statistik og rapporter](collection-statistics-reports.md)

## <a name="conditions"></a>Betingelser

Du kan tilføje søgebetingelser for at begrænse omfanget af en søgning og returnere et mere elegant sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med den nøgleordsforespørgsel, der er angivet i nøgleordsfeltet af en logisk operator (der er repræsenteret som *c:c* i syntaksen for søgeforespørgslen), der svarer til funktionaliteten for **operatoren OG** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser, der skal medtages i søgeresultaterne. Det er sådan, betingelser kan hjælpe dig med at indsnævre dine resultater. Hvis du vil have en liste over og en beskrivelse af betingelser, du kan bruge i en søgeforespørgsel, skal du se afsnittet "Søgebetingelser" i [Nøgleordsforespørgsler og søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).
