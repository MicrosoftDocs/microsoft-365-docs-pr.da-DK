---
title: Analysér data i et korrektursæt i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.assetid: ''
description: Få mere at vide om de værktøjer, der er tilgængelige til at organisere dokumentgrupper, når du analyserer en Microsoft Purview eDiscovery-sag (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: af34a790881cad2af5d278cf187b963f0aa58146
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099823"
---
# <a name="analyze-data-in-a-review-set-in-ediscovery-premium"></a>Analysér data i et korrektursæt i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når antallet af indsamlede dokumenter er stort, kan det være svært at gennemse dem alle. Microsoft Purview eDiscovery (Premium) indeholder en række værktøjer til at analysere dokumenterne for at reducere mængden af dokumenter, der skal gennemses uden tab af oplysninger, og til at hjælpe dig med at organisere dokumenterne på en sammenhængende måde. Du kan få mere at vide om disse funktioner under:

- [Registrering af næsten dubletter](near-duplicate-detection-in-advanced-ediscovery.md)

- [Mailtrådning](email-threading-in-advanced-ediscovery.md)

- [Temaer](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Kør analyse for et korrektursæt

Sådan analyserer du data i et korrektursæt:

1. Konfigurer analyseindstillinger for din sag. Du kan finde flere oplysninger under [Konfigurer søge- og analyseindstillinger](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Åbn det korrektursæt, du vil analysere.

3. Klik på **AnalyticsRun** >  **dokument & mailanalyse**.

   ![Vælg Kør dokument & mailanalyse på rullelisten Analytics](..\media\RunAnalytics1.png)

Du kan kontrollere status for analysen under fanen **Job** i sagen.

 Når analysen er fuldført, kan du få vist analyserapporten, køre forespørgsler i dit korrektursæt på output fra analysen (se [Forespørgsel i dit korrektursæt](review-set-search.md), og se relaterede dokumenter i et givet dokument (se [Gennemse data i korrektursæt](reviewing-data-in-review-set.md).

## <a name="using-the-for-review-filter-query"></a>Brug af filterforespørgslen Til gennemsyn

Når du har kørt analyser for korrektursættet, kan du bruge en automatisk genereret filterforespørgsel (kaldet *Til gennemsyn*), der filtrerer din anmeldelse for at udelade immaterielle, dublerede eller ikke-inkluderende elementer. Dette efterlader dig kun de elementer, der er repræsentative, unikke og inkluderende i korrektursættet.

Hvis du vil anvende filterforespørgslen **til gennemsyn** på et korrektursæt, skal du vælge rullelisten **Gemte filterforespørgsler** og derefter vælge **\[AutoGen] til gennemsyn**.

![Vælg Til gennemsyn på rullelisten Gemte filterforespørgsler](..\media\ForReviewFilterQuery1.png)

Her er syntaksen for filterforespørgslen **til gennemsyn** :

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

På følgende liste beskrives resultatet af filterforespørgslen med hensyn til, hvilket indhold der vises, når du har anvendt det i korrektursættet.

- **Mail**. Viser elementer, der er markeret som **Inclusive** eller **InclusiveMinus**. Et inkluderende element er den endelige meddelelse i en mailtråd. Den indeholder alt tidligere indhold i mailtråden. Et inkluderende minus det indeholder en eller flere vedhæftede filer, der er knyttet til den specifikke meddelelse i mailtråden. En korrekturlæser kan bruge minusværdien inklusive til at bestemme, hvilke bestemte meddelelser i mailtråden der har tilknyttede vedhæftede filer.

- **Vedhæftede filer**. Filtrerer dublerede vedhæftede filer i det samme mailsæt fra. Det er kun vedhæftede filer, der er entydige i en mailtråd, der vises.

- **Dokumenter og andet**. Filtrerer dublerede dokumenter fra. Det er kun dokumenter, der er entydige i korrektursættet, der vises.

- **Teams samtaler**. Alle Teams (og Yammer) samtaler i korrektursættet vises.

Du kan finde flere oplysninger om inkluderende typer og dokumentets entydighed [under Mailtrådning i eDiscovery (Premium)](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> I den offentlige prøveversion af [det nye sagsformat](advanced-ediscovery-new-case-format.md) i eDiscovery (Premium) returnerede filterforespørgslen til **gennemsyn** ikke Teams eller Yammer samtaler til korrektursæt (i tilfælde, hvor store sager bruges) oprettet før den 4. november 2021. Problemet er løst. Det betyder, at hvis du anvender forespørgslen **Til gennemsyn** igen på et korrektursæt i et tilfælde, der bruger store og små bogstaver, kan flere elementer, der stemmer overens med filterforespørgslen, blive vist, fordi alle Teams eller Yammer samtaler er inkluderet.

## <a name="analytics-report"></a>Analyserapport

Sådan får du vist analyserapporten for et gennemsynssæt:

1. Åbn korrektursættet.

2. Klik på **AnalyticsShowrapporter** > .

**Analyserapporten** indeholder syv komponenter fra analysen:

- **Målpopulation:** Antallet af mails, vedhæftede filer og løse dokumenter, der blev fundet i korrektursættet.

- **Dokumenter (undtagen vedhæftede filer):** Antallet af løse dokumenter, der er pivots, entydige nær dubletter af en pivot eller en nøjagtig dublet af et andet dokument.

- **E-mails:** Antallet af mails, der er markeret som inklusive, inklusive kopi, inklusive minus, eller ingen af ovenstående.

- **Vedhæftede filer:** Antallet af vedhæftede filer i mails, der er entydige eller dubletter af en anden vedhæftet fil i korrektursættet.

- **Nummerer dokumenter efter filtype:** Antallet af filer, der er identificeret af filtypenavnet.

- **Dokumenter efter kilde:** En oversigt over indhold fra den oprindelige datakilde.

- **Dokumenter, der er samlet efter proces:** En oversigt over indhold ved at gennemse sæt processer. 
