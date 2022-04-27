---
title: Prøv en indholdssøgning igen for at løse en fejl i indholdsplaceringen
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Under en undersøgelse kan du bruge knappen Prøv igen for at løse indholdssøgninger, der har fejl i indholdsplaceringen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5345b346e8c66f6983d67081839248e4c66be7d8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090423"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Prøv en indholdssøgning igen for at løse en fejl i indholdsplaceringen

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du bruger indholdssøgning i Security and Compliance Center til at søge i et stort antal postkasser, kan du få søgefejl, der svarer til fejlen:

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Disse fejl (med fejlkoder for CS001-002, CS003-002, CS008-009, CS012-002 og andre fejl i formularen CS0XX-0XX) angiver, at indholdssøgningen ikke kunne søge efter bestemte indholdsplaceringer. I dette eksempel blev der ikke søgt i to postkasser. Disse fejl vises på pop op-siden med statusoplysninger i indholdssøgningen.

## <a name="cause-of-content-location-errors"></a>Årsag til fejl i placering af indhold

Når du søger i et stort antal postkasser, distribueres søgningen på tværs af tusindvis af servere i et Microsoft-datacenter. På et hvilket som helst tidspunkt kan bestemte servere være i genstartstilstand eller i gang med at mislykkes i forbindelse med redundante kopier. I begge tilfælde får indholdssøgningens anmodning om at hente data timeout. I det forrige eksempel var fejlene for de postkasser, der mislykkedes, resultatet af timeout for søgning.

## <a name="resolving-content-location-errors"></a>Løsning af fejl i indholdsplacering

Genstart af søgningen vil ofte resultere i lignende fejl på forskellige servere. I stedet for at genstarte søgningen skal du klikke på knappen **Prøv igen** , der vises øverst på siden med søgeresultater.

![Klik på knappen Prøv igen for at løse fejl i indholdsplaceringen.](../media/retrycontentsearch3.png)

Dette medfører, at søgningen kun forsøges igen for de postkasser, der mislykkedes. Når du prøver søgningen igen, bevares de andre resultater, der blev returneret.

## <a name="tips-to-avoid-content-location-errors"></a>Tips for at undgå fejl i indholdsplacering

Her er nogle yderligere årsager til fejl i placering af indhold og nogle tip, der kan hjælpe dig med at undgå dem, når du søger i et stort antal postkasser.

- Den postkasse, der søges i, kan være optaget på grund af brugeraktivitet. I dette tilfælde kan søgetjenesten begrænse sig selv for at forhindre, at postkassen bliver utilgængelig. Du kan undgå dette ved at prøve at køre søgninger uden for arbejdstiden.

- Søgeforespørgslen henter muligvis for meget indhold fra postkassen. Hvis det er muligt, kan du prøve at indsnævre omfanget af søgningen ved hjælp af nøgleord, datointervaller og søgebetingelser.

- Der er for mange nøgleord eller nøgleordsudtryk, når du opretter en søgeforespørgsel ved hjælp af [listen over nøgleord](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Når du kører en søgeforespørgsel, der bruger nøgleordslisten, kører tjenesten i bund og grund en separat søgning efter hver række på nøgleordslisten, så der kan genereres statistikker. Hvis du bruger listen over nøgleord i søgeforespørgsler, skal du minimere antallet af rækker på nøgleordslisten eller opdele talnøgleordene i mindre lister og oprette en anden søgning efter hver nøgleordsliste.

  > [!NOTE]
  > For at hjælpe med at reducere problemer, der skyldes store nøgleordslister, er du nu begrænset til maksimalt 20 rækker på nøgleordslisten i en søgeforespørgsel.

- Der udføres for mange søgninger i den samme postkasse på samme tid. Hvis det er muligt, kan du prøve at køre én søgning ad gangen i en hvilken som helst postkasse.

- Søger i for mange postkasser i en enkelt søgning. Sandsynligheden for fejl i placering af indhold øges, når der søges i et stort antal postkasser. Hvis det er muligt, kan du prøve at køre flere søgninger, så hver søgning indeholder et undersæt af postkasser i din organisation.

- Den påkrævede vedligeholdelse udføres på postkassen. Selvom denne årsag sandsynligvis forekommer sjældent, skal du vente lidt, efter at du har modtaget fejlen for indholdsplaceringen, og derefter prøve søgningen igen.
