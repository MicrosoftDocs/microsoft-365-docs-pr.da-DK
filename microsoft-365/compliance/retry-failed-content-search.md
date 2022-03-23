---
title: Prøv en indholdssøgning igen for at løse en indholdsplaceringsfejl
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: ''
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Under en undersøgelse kan du bruge knappen Prøv igen til at løse problemer med indholdssøgninger, der har fejl med indholdsplaceringen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3c433dfa6bf842f1d62350e3b518177d1bdca6d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587942"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Prøv en indholdssøgning igen for at løse en indholdsplaceringsfejl

Når du bruger Indholdssøgning i Sikkerheds- og overholdelsescenteret til at søge i et stort antal postkasser, får du muligvis søgefejl, der ligner fejlen:

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Disse fejl (med fejlkoderne CS001-002, CS003-002, CS008-009, CS012-002 og andre fejl i formularen CS0XX-0XX) angiver, at Indholdssøgning ikke kunne søge i bestemte indholdsplaceringer; I dette eksempel blev der ikke søgt i to postkasser. Disse fejl vises på pop op-siden med statusoplysninger i Indholdssøgning.

## <a name="cause-of-content-location-errors"></a>Årsag til fejl i indholdsplacering

Når du søger i et stort antal postkasser, fordeles søgningen på tværs af tusindvis af servere i et Microsoft-datacenter. På et hvilket som helst tidspunkt kan bestemte servere være i genstartstilstand eller i gang med mislykkes over til redundante kopier. I et af disse tilfælde får indholdssøgningens anmodning om at hente data time out. I det forrige eksempel var fejlene for de postkasser, der mislykkedes, resultatet af, at søgningen ikke var tidsindstilling.

## <a name="resolving-content-location-errors"></a>Løs problemer med indholdsplaceringen

Hvis du genstarter søgningen, medfører det ofte lignende fejl på forskellige servere. I stedet for at genstarte søgningen skal du **klikke på knappen** Prøv igen, der vises øverst på siden med søgeresultater.

![Klik på knappen Prøv igen for at løse problemer med placering af indhold.](../media/retrycontentsearch3.png)

Dette medfører, at søgningen kun forsøges igen for de postkasser, der mislykkedes. Når du forsøger søgningen igen, bevares de andre resultater, der blev returneret.

## <a name="tips-to-avoid-content-location-errors"></a>Tips for at undgå fejl i indholdsplaceringen

Her er nogle flere årsager til fejl på indholdsplaceringen og nogle tip, der kan hjælpe dig med at undgå dem, når du søger i et stort antal postkasser.

- Den postkasse, der søges i, kan være optaget på grund af brugeraktivitet. I dette tilfælde begrænser søgetjenesten muligvis sig selv for at forhindre postkassen i at blive utilgængelig. Du kan undgå dette ved at køre søgninger uden for arbejdstiden.

- Søgeforespørgslen henter muligvis for meget indhold fra postkassen. Hvis det er muligt, kan du prøve at begrænse omfanget af søgningen ved hjælp af nøgleord, datointervaller og søgebetingelser.

- For mange nøgleord eller nøgleordsudtryk, når du opretter en søgeforespørgsel ved hjælp af [listen med nøgleord](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Når du kører en søgeforespørgsel, der bruger listen med nøgleord, kører tjenesten i bund og grund en separat søgning for hver række på listen med nøgleord, så der kan genereres statistik. Hvis du bruger listen med nøgleord i søgeforespørgsler, skal du minimere antallet af rækker på listen over nøgleord eller opdele antallet af nøgleord i mindre lister og oprette en anden søgning efter hver nøgleordsliste.

  > [!NOTE]
  > For at reducere problemer, der skyldes lister med store nøgleord, er du nu begrænset til maksimalt 20 rækker på listen med nøgleord i en søgeforespørgsel.

- Der udføres for mange søgninger på den samme postkasse på samme tid. Hvis det er muligt, kan du prøve at køre én søgning ad gangen på en vilkårlig postkasse.

- Søgning for mange postkasser i en enkelt søgning. Sandsynligheden for fejl på indholdsplaceringen øges, når du søger i et stort antal postkasser. Hvis det er muligt, kan du prøve at køre flere søgninger, så hver søgning indeholder et undersæt af postkasser i organisationen.

- Der udføres påkrævet vedligeholdelse på postkassen. Selvom denne årsag sandsynligvis forekommer sjældent, skal du vente lidt, efter du har modtaget fejlen for indholdsplaceringen, og derefter prøve søgningen igen.
