---
title: Analysér data i et korrektursæt i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om de værktøjer, der er tilgængelige til at organisere dokumentsæt, når du analyserer Advanced eDiscovery store og små bogstaver.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 829e6e6441403cf5a934e81a1a437f65d2de3db3
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588702"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analysér data i et korrektursæt i Advanced eDiscovery

Når antallet af indsamlede dokumenter er stort, kan det være svært at gennemse dem alle. Advanced eDiscovery indeholder en række værktøjer til analyse af dokumenterne for at reducere mængden af dokumenter, der skal gennemses uden tab af oplysninger, og for at hjælpe dig med at organisere dokumenterne på en sammenhængende måde. Hvis du vil vide mere om disse funktioner, skal du se:

- [Nær registrering af dubletter](near-duplicate-detection-in-advanced-ediscovery.md)

- [Mailtrådning](email-threading-in-advanced-ediscovery.md)

- [Temaer](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Kør analyser for et gennemsynssæt

Sådan analyserer du data i et korrektursæt:

1. Konfigurer analyseindstillinger for din sag. Få mere at vide under [Konfigurer indstillinger for søgning og analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Åbn det korrektursæt, du vil analysere.

3. Klik **på AnalyticsRun-dokument** >  **& mailanalyse**.

   ![Vælg Kør & og mailanalyse fra rullelisten Analytics](..\media\RunAnalytics1.png)

Du kan se status for analysen under **fanen Jobs** for sagen.

 Når analysen er fuldført, kan du få vist analyserapporten, køre forespørgsler i dit korrektursæt på output fra analysen (se Forespørgsel i dit korrektursæt [, og](review-set-search.md) se relaterede dokumenter for et bestemt dokument (se Gennemse [data](reviewing-data-in-review-set.md) i korrektursæt.

## <a name="using-the-for-review-filter-query"></a>Brug af filterforespørgslen Til gennemsyn

Når du har kørt analyser for korrektursættet, kan du bruge en automatisk genereret filterforespørgsel (kaldet Til gennemsyn), der filtrerer din anmeldelse *for* at udelukke im chat, duplikerede eller ikke-inkluderende elementer. Dette giver dig kun de elementer, der er repræsentative, entydige og inkluderende i korrektursættet.

Hvis du vil **anvende filterforespørgslen**  Til gennemsyn på et korrektursæt, skal du vælge rullelisten Gemte filterforespørgsler og derefter **vælge AutoGen] Til gennemsyn.\[**

![Vælg Til gennemsyn på rullelisten Gemte filterforespørgsler](..\media\ForReviewFilterQuery1.png)

Her er syntaksen for **filterforespørgslen** Til gennemsyn:

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

Følgende liste beskriver resultatet af filterforespørgslen med hensyn til, hvilket indhold der vises, når du anvender den på korrektursættet.

- **Mail**. Viser elementer, der er markeret som **Inkluderende** **eller InklusiveMinus**. Et inkluderende element er den endelige meddelelse i en mailtråd. Den indeholder alt tidligere indhold i mailtråden. Et inkluderende minus indeholder en eller flere vedhæftede filer, der er knyttet til den specifikke meddelelse i mailtråden. En korrekturlæser kan bruge den inkluderende minusværdi til at bestemme, hvilke bestemte meddelelser i mailtråden der har tilknyttede vedhæftede filer.

- **Vedhæftede filer**. Filtrerer dublerede vedhæftede filer ud i det samme mailsæt. Kun vedhæftede filer, der er entydige i en mailtråd, vises.

- **Dokumenter og andre**. Filtrerer dublerede dokumenter fra. Det er kun de dokumenter, der er entydige i korrektursættet, der vises.

- **Teams samtaler**. Alle Teams (Yammer samtaler i korrektursættet) vises.

Du kan finde flere oplysninger om inkluderende typer og dokumentets [entydighed under Mailtrådning Advanced eDiscovery](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> Under det offentlige eksempel på [](advanced-ediscovery-new-case-format.md) det nye caseformat i Advanced eDiscovery returnerede filterforespørgslen Til gennemsyn ikke Teams- eller Yammer-samtaler for korrektursæt (i tilfælde, der bruger det store sagsformat), som blev oprettet før 4. november 2021. Dette problem er løst. Det betyder, at hvis du genanvender  forespørgslen Til gennemsyn på et korrektursæt i en sag, der bruger store bogstaver, vises der muligvis flere elementer, der svarer til filterforespørgslen, fordi alle Teams- eller Yammer-samtaler er inkluderet.

## <a name="analytics-report"></a>Analyserapport

Sådan får du vist analyserapporten for et korrektursæt:

1. Åbn korrektursættet.

2. Klik **på** **AnalyticsShow-rapporter** > .

Rapporten **Analytics** indeholder syv komponenter fra analysen:

- **Målgruppe:** Antallet af mails, vedhæftede filer og løse dokumenter, der findes i korrektursættet.

- **Dokumenter (undtagen vedhæftede filer):** Antallet af løse dokumenter, der er pivoter, entydige nær dubletter af en pivot eller en nøjagtig kopi af et andet dokument.

- **Mails:** Antallet af mails, der er markeret som inkluderende, inklusive kopi, inklusive minus eller ingen af ovenstående.

- **Vedhæftede filer:** Antallet af vedhæftede filer i mails, der er entydige eller dubletter af en anden vedhæftet fil i gennemsynssættet.

- **Nummerer dokumenter efter filtype:** Antallet af filer, der er identificeret med filtypenavn.

- **Dokumenter efter kilde:** En oversigt over indhold ud fra den oprindelige datakilde.

- **Dokumenter aggregeret efter proces:** En oversigt over indhold efter gennemsyn af indstillede processer. 
