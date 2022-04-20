---
title: Konfigurer historiske versioner i eDiscovery (Premium)
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
description: Brug historiske versioner i eDiscovery (Premium) til at indsamle indhold fra alle versioner af dokumenter, der er gemt i SharePoint og OneDrive.
ms.openlocfilehash: e73429744958698f275d33b52cc50805c274ef13
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943079"
---
# <a name="set-up-historical-versions-in-ediscovery-premium-preview"></a>Konfigurer historiske versioner i eDiscovery (Premium) (prøveversion)

Funktionen historiske versioner i eDiscovery (Premium) gør det muligt for eDiscovery-ledere i din organisation at søge efter og indsamle indhold fra alle versioner af dokumenter, der er gemt i SharePoint Online og OneDrive for Business. Derefter kan du føje dette indhold til et anmeldelsessæt til analyse og gennemgang. Dette hjælper dig med at finde og gennemse indhold fra en bestemt version af et dokument, der kan være relevant for en sag eller undersøgelse, også selvom den seneste version af det samme dokument ikke indeholder de relevante oplysninger.

Hvis SharePoint administratorer vil understøtte funktionen til historiske versioner i eDiscovery (Premium), skal de aktivere versionering for websteder i deres organisation. Når brugerne derefter ændrer dokumenter i SharePoint eller OneDrive, oprettes der implicitte almindelige versioner, når dokumentet gemmes (eller gemmes automatisk). SharePoint versioner gør det muligt at spore den aktivitet, der udføres på SharePoint elementer (herunder dokumenter, hændelser og opgaver). Denne versionsstyringsfunktion efterlader et revisionsspor, der kan levere beviser i juridiske undersøgelser. Disse ældre versioner af et dokument er tilgængelige for organisationen, som kan blive bedt om at dele sådanne versioner, der har følsomt eller relevant indhold under en retskendelse i en juridisk sag.

Når en eDiscovery-administrator aktiverer historiske versioner for organisationen og derefter aktiverer den for bestemte SharePoint websteder, gennemsøger den SharePoint indholds-pushtjeneste alle overordnede og underordnede versioner af dokumenter på de aktiverede websteder og sender derefter disse versioner til indeksering. Når gennemsøgnings- og indekseringsprocessen er fuldført, er dokumenter og deres versioner tilgængelige til eDiscovery-søgning. Så længe der er adgang til en bestemt version (efter versionshistorik), kan du finde denne version i en eDiscovery-samlingssøgning (Premium).

## <a name="set-up-historical-versions"></a>Konfigurer historiske versioner

Hvis du vil aktivere historiske versioner i eDiscovery (Premium), skal din organisation aktivere den og derefter aktivere bestemte websteder, så alle versioner af dokumenter, der er gemt på disse websteder, indekseres til søgning. Før du konfigurerer eDiscovery (Premium) for historiske versioner, skal du aktivere understøttelse af versioner i SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Trin 1: Aktivér versionering i SharePoint

Det første trin er at aktivere versionering i SharePoint Online, så alle versioner af et dokument bevares. Du kan finde instruktioner [under Versionering i SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>Trin 2: Slå historiske versioner til

Det næste trin er at aktivere historiske versioner i eDiscovery (Premium). Hvis du vil aktivere historiske versioner for din organisation, skal en person være global administrator eller eDiscovery-administrator (medlem af undergruppen eDiscovery-administrator i rollegruppen eDiscovery Manager). Når historiske versioner er slået til, gælder det for hele organisationen.

> [!IMPORTANT]
> Når du har slået historiske versioner til, kan du ikke slå dem fra i den offentlige prøveversion. Du kan slå den fra, når historiske versioner er blevet offentligt tilgængelige.

1. Gå til [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) på Microsoft Purview-overholdelsesportalen, og klik derefter på **indstillinger for eDiscovery (Premium).**

   ![Vælg indstillinger for eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen **Historiske versioner (prøveversion)** og derefter skifte **lejerkontrolelementet Historiske versioner** til til.

   ![Slå til/fra-knappen til for at aktivere historiske versioner](..\media\HistoricalVersions2.png)

   Der vises en advarsel om, at du ikke kan slå historiske versioner fra. Som tidligere nævnt kan du ikke deaktivere historiske versioner, før funktionen er offentligt tilgængelig.

3. Klik på **Ja** for at aktivere historiske versioner.

### <a name="step-3-activate-sharepoint-sites"></a>Trin 3: Aktivér SharePoint websteder

Når du har slået historiske versioner til for din organisation, er det sidste trin at aktivere SharePoint websteder for at understøtte historiske versioner. Når du aktiverer et websted (ved at føje det til en liste over websteder under fanen **Historiske versioner** ), gennemsøges webstedet igen, og alle versioner af dokumenter, der er gemt på det pågældende websted, indekseres til søgning.

> [!NOTE]
> Der er en grænse på 100 webstedsaktiveringer pr. organisation under den offentlige prøveversion af historiske versioner. En aktivering tælles i forhold til denne grænse, når du aktiverer eller deaktiverer et websted for historiske versioner. Hvis du aktiverer flere websteder, tælles hvert websted som en enkelt aktivering. Det samlede antal aktiveringer vises under fanen **Historiske versioner** .

1. På fanen **Historiske versioner** på siden eDiscovery (Premium) **Indstillinger** skal du klikke på **Aktivér** for at aktivere websteder for historiske versioner.

   ![Klik på Aktivér for at aktivere websteder for historiske versioner](..\media\HistoricalVersions3.png)  

   Der vises en pop op-side, der indeholder en liste over alle SharePoint websteder i din organisation.

2. Vælg et websted, der skal aktiveres, og klik derefter på **Aktivér** for at aktivere det for historiske versioner. Du kan bruge søgefeltet til at søge efter et bestemt websted.

   Der vises en advarsel, hvor der står, at dokumentversioner på webstedet vil blive indekseret, og at indekseringsprocessen vil tage et stykke tid, før versionerne er klar til søgning. Advarslen angiver også, at du ikke kan deaktivere historiske versioner for det valgte websted i 30 dage.

3. Klik på **Ja** for at aktivere webstedet for historiske versioner.

   ![Det aktiverede websted og antallet af aktiveringer af webstedet vises](..\media\HistoricalVersions4.png)  

   Webstedet føjes til listen over aktiverede websteder. Tælleren, der viser antallet af aktiveringer af webstedet, opdateres også.

4. Gentag de forrige trin for hvert websted, du vil aktivere for historiske versioner.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvordan adskiller historiske versioner sig fra at have mulighed for at "indsamle alle versioner", når du sender en kladdesamling til et korrektursæt?**

I øjeblikket er det kun den nyeste version af dokumenter, der indekseres til søgning. Det betyder, at når du kører en kladdesamling, er det kun de nyeste versioner af dokumenter, der søges i. Hvis et dokument stemmer overens med nøgleordsforespørgslen for samlingen, returneres det i resultaterne af samlingen. Men hvis den nyeste version af et dokument ikke svarer til en søgeforespørgsel, returneres dokumentet ikke hændelse, hvis ældre versioner af dokumentet indeholder nøgleordet. For at afhjælpe denne situation giver eDiscovery (Premium) dig mulighed for at indsamle alle versioner af dokumentet, når du [sender en samling til et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Det betyder, at alle ældre versioner, der kan indeholde nøgleordet, føjes til korrektursættet.

Historiske versioner er forskellige og mere effektive end "indsamling af alle versioner", fordi når du aktiverer et websted, indekseres alle versioner af et dokument (og ikke kun den sidste version) til søgning. Resultatet er, at hvis en ældre version af et dokument indeholder et nøgleord, der svarer til søgeforespørgslen, returneres det af samlingen.

**Når historiske versioner er aktiveret for et websted, påvirker det så webstedets ydeevne?**

Nej. Når historiske versioner er aktiveret for et websted, vil webstedets ydeevne være den samme, som den var, før webstedet blev aktiveret. De gennemsøgnings- og indekseringsprocesser, der udføres på webstedet, når det er aktiveret, sker langsommere og udføres uden for spidsbelastningstider. Aktivering af historiske versioner for et websted starter en backfill-proces, der finder alle versioner af dokumenter på webstedet og derefter sender disse versioner til indekset. Afhængigt af antallet af dokumentversioner for webstedet kan denne backfill-proces påvirke tjenestetilstanden. Vi har mindsket denne potentielle indvirkning på følgende måder:

- Vi gør det bedste for at behandle disse versioner uden for spidsbelastningstider.

- Vi behandler dokumentversioner i vores kø med laveste prioritet, hvilket gør det muligt at delegere de fleste tjenesteressourcer til brugerændringer.

**Hvor længe skal jeg vente, når et websted er aktiveret, indtil alle historiske versioner af dokumenter på det pågældende websted er indekseret og tilgængelige til eDiscovery-søgning?**

Baseret på antallet af dokumenter for et websted og det gennemsnitlige antal versioner pr. dokument forsøger vi at estimere det samlede antal filer pr. websted. Baseret på dette er et estimat af, hvor lang tid det kan tage at indeksere, som følger:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Den halve dag tilføjes som buffer, da indeksering af versioner på webstedet er optimeret til at køre uden for spidsbelastningstider.

Hvis det samlede antal dokumenter og alle versioner for et websted f.eks. er 150.000, tager det mindst to dage at behandle webstedet for historiske versioner:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Hvorfor anbefales det ikke at aktivere eller deaktivere websteder for historiske versioner ofte?**

Når du deaktiverer et tidligere aktiveret websted, udløses en oprydningsproces. Det tager tid at fuldføre denne proces. Hvis det samme websted aktiveres igen, skal backfill-processen til genfyldning af webstedet køre igen. Både oprydnings- og backfill-processerne er tids- og ressourcekrævende. Derfor anbefaler vi, at du nøje overvejer og planlægger, hvilke websteder du vil aktivere for historiske versioner, så du kan undgå gentagne gange at aktivere og deaktivere historiske versioner for et websted.
