---
title: Konfigurer tidligere versioner i Advanced eDiscovery
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
description: Brug tidligere versioner i Advanced eDiscovery til at indsamle indhold fra alle versioner af dokumenter, der er gemt i SharePoint og OneDrive.
ms.openlocfilehash: 5ecbb9c9216482223ce756aed5742e25a3b851a1
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593628"
---
# <a name="set-up-historical-versions-in-advanced-ediscovery-preview"></a>Konfigurer tidligere versioner i Advanced eDiscovery (forhåndsvisning)

Funktionen tidligere versioner i Advanced eDiscovery gør det muligt for eDiscovery-ledere i organisationen at søge efter og indsamle indhold fra alle versioner af dokumenter, der er gemt i SharePoint Online og OneDrive for Business. Derefter kan du føje indholdet til et gennemsynssæt til analyse og gennemgang. På den måde kan du finde og gennemse indhold fra en bestemt version af et dokument, som kan være relevant for en sag eller undersøgelse, også selvom den nyeste version af det samme dokument ikke indeholder de relevante oplysninger.

For at understøtte funktionaliteten for historiske versioner Advanced eDiscovery, SharePoint administratorer aktivere versionshistorik for websteder i deres organisation. Når brugerne derefter redigerer dokumenter i SharePoint eller OneDrive, oprettes der implicitte regelmæssige versioner, når dokumentet gemmes (eller gemmes automatisk). SharePoint giver mulighed for sporing af den aktivitet, der udføres SharePoint elementer (herunder dokumenter, begivenheder og opgaver). Denne versionsfunktion efterlader en revisionslog, der kan levere beviser i juridiske undersøgelser. Disse ældre versioner af et dokument er tilgængelige for organisationen, som muligvis skal dele sådanne versioner, der har følsomt eller relevant indhold under retsregistrering i en juridisk sag.

Når en eDiscovery-administrator aktiverer historiske versioner for organisationen og derefter aktiverer den for bestemte SharePoint-websteder, gennemsøger SharePoint-indholds pushtjenesten alle overordnede og underordnede versioner af dokumenter på de aktiverede websteder og sender derefter disse versioner til indeksering. Når gennemsøgnings- og indekseringsprocessen er fuldført, er dokumenter og deres versioner tilgængelige for eDiscovery-søgning. Så længe der kan opnås adgang til en bestemt version (via versionshistorik), vil den pågældende version kunne findes i en Advanced eDiscovery søgning på en samling.

## <a name="set-up-historical-versions"></a>Konfigurer ældre versioner

Hvis du vil aktivere tidligere versioner i Advanced eDiscovery, skal din organisation aktivere det og derefter aktivere bestemte websteder, så alle versioner af dokumenter, der er gemt på disse websteder, indekseres til søgning. Før du konfigurerer Advanced eDiscovery for historiske versioner, skal du aktivere understøttelse af versionshistorik i SharePoint.

### <a name="step-1-turn-on-versioning-in-sharepoint"></a>Trin 1: Slå versionsversioner til i SharePoint

Det første trin er at slå versionsering til i SharePoint Online, så alle versioner af et dokument bevares. Du kan finde en vejledning [under SharePoint](/microsoft-365/community/versioning-basics-best-practices).

### <a name="step-2-turn-on-historical-versions"></a>Trin 2: Slå tidligere versioner til

Næste trin er at slå historiske versioner til i Advanced eDiscovery. Hvis du vil aktivere historiske versioner for din organisation, skal en person være global administrator eller eDiscovery-administrator (medlem af undergruppen eDiscovery-administrator i rollegruppen eDiscovery-leder). Når historiske versioner er slået til, gælder det for hele organisationen.

> [!IMPORTANT]
> Når du har aktiveret tidligere versioner, kan du ikke deaktivere den under den offentlige prøveversion. Du kan deaktivere den, når der er udgivet historiske versioner for at sikre generel tilgængelighed.

1. I Microsoft 365 Overholdelsescenter skal du gå til [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **Advanced eDiscovery indstillinger**.

   ![Vælg Advanced eDiscovery indstillinger](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge fanen Historiske versioner (forhåndsvisning **)** og derefter slå lejerkontrolelementet  Historiske versioner til til.

   ![Slå til/fra-knappen til for at aktivere tidligere versioner](..\media\HistoricalVersions2.png)

   Der vises en advarsel, der fortæller dig, at du ikke kan deaktivere tidligere versioner. Som tidligere nævnt kan du ikke deaktivere tidligere versioner, før funktionen frigives til generel tilgængelighed.

3. Klik **på Ja** for at aktivere tidligere versioner.

### <a name="step-3-activate-sharepoint-sites"></a>Trin 3: Aktivér SharePoint websteder

Når du har aktiveret tidligere versioner for organisationen, er det sidste trin at aktivere SharePoint til understøttelse af tidligere versioner. Når du aktiverer et websted (ved at føje det til en liste over websteder under  fanen Historiske versioner), genaktiveres webstedet, og alle versioner af dokumenter, der er gemt på webstedet, indekseres til søgning.

> [!NOTE]
> Der er en grænse på 100 webstedsaktiveringer pr. organisation under den offentlige prøveversion af historiske versioner. En aktivering tæller med i denne grænse, når du aktiverer eller deaktiverer et websted i tidligere versioner. Hvis du aktiverer flere websteder, tælles hvert websted som en enkelt aktivering. Det samlede antal aktiveringer vises under fanen **Historiske** versioner.

1. På fanen **Historiske versioner på** siden Advanced eDiscovery **Indstillinger** skal du klikke på **Aktivér for** at aktivere websteder for historiske versioner.

   ![Klik på Aktivér for at aktivere websteder for tidligere versioner](..\media\HistoricalVersions3.png)  

   Der vises en pop op-side med en liste over alle SharePoint websteder i organisationen.

2. Vælg et websted, du vil aktivere, og klik derefter **på Aktivér** for at aktivere det i tidligere versioner. Du kan bruge søgefeltet til at søge efter et bestemt websted.

   Der vises en advarsel, hvor der står, at dokumentversionerne på webstedet indekseres, og indekseringsprocessen tager et stykke tid, før versionerne er klar til søgning. Advarslen siger også, at du ikke kan deaktivere tidligere versioner for det valgte websted i 30 dage.

3. Klik **på Ja** for at aktivere webstedet for historiske versioner.

   ![Det aktiverede websted og antallet af webstedsaktiveringerne vises](..\media\HistoricalVersions4.png)  

   Webstedet føjes til listen over aktiverede websteder. Tælleren, der viser antallet af webstedsaktivering, opdateres også.

4. Gentag de forrige trin for hvert websted, du vil aktivere for tidligere versioner.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvordan er tidligere versioner anderledes end muligheden for at "indsamle alle versioner", når du har bekræftet en kladdesamling i et korrektursæt?**

I øjeblikket er det kun den seneste version af dokumenter, der indekseres til søgning. Det betyder, at når du kører en kladdesamling, søges der kun i de seneste versioner af dokumenter. Hvis et dokument svarer til nøgleordsforespørgslen for samlingen, returneres den i samlingens resultater. Men hvis den nyeste version af et dokument ikke stemmer overens med en søgeforespørgsel, returneres dokumentet ikke, hvis ældre versioner af dokumentet indeholder nøgleordet. For at afhjælpe denne situation Advanced eDiscovery du mulighed for at indsamle alle versioner af dokumentet, når du har bekræftet en samling [i et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set). Det betyder, at alle ældre versioner, der kan indeholde nøgleordet, føjes til korrektursættet.

Historiske versioner er forskellige og mere effektive end "indsamling af alle versioner", fordi når du aktiverer et websted, indekseres alle versioner af et dokument (og ikke kun den sidste version) til søgning. Resultatet er, at hvis en ældre version af et dokument indeholder et nøgleord, der svarer til søgeforespørgslen, så returneres det af samlingen.

**Når historiske versioner er aktiveret for et websted, påvirker det så webstedets ydeevne?**

Nej. Når tidligere versioner er aktiveret for et websted, vil ydeevnen for webstedet være den samme, som før webstedet blev aktiveret. De gennemsøgnings- og indekseringsprocesser, der udføres på webstedet, efter det er aktiveret, sker med en langsommere hastighed og udføres på tidspunkter uden spidsbelastning. Aktivering af historiske versioner for et websted starter en efterfyldningsproces, som finder alle versioner af dokumenter på webstedet og derefter sender disse versioner til indekset. Afhængigt af antallet af dokumentversioner for webstedet kan denne efterfyldningsproces påvirke tjenestetjenestens tilstand. Vi har mindsket denne potentielle indvirkning på følgende måder:

- Vi gør den bedste indsats for at behandle disse versioner på tidspunkter uden spidsbelastning.

- Vi behandler dokumentversioner i vores lavprioritetskøer, hvilket giver de fleste tjenesteressourcer mulighed for at uddelegere til brugerændringer.

**Hvor længe skal jeg vente, efter at et websted er aktiveret, indtil alle historiske versioner af dokumenter på webstedet alle er indekseret og tilgængelige for eDiscovery-søgning?**

Baseret på antallet af dokumenter for et websted og det gennemsnitlige antal versioner pr. dokument forsøger vi at anslå det samlede antal filer pr. websted. Baseret på dette er et skøn over, hvor lang tid det kan tage at indeksere, som følger:

`Number of versions / (Processing rate of 100,000 files per day ) + .5 days = Total number of days to process a site`

Halvdag tilføjes som en buffer, da indeksering af versioner på webstedet er optimeret til at køre i tidspunkter uden spidsbelastning.

Hvis f.eks. det samlede antal dokumenter og alle versioner for et websted er 150.000, tager det mindst to dage at behandle webstedet i tidligere versioner:

`150,000 files/100,000 files per day + .5 days = 2 days`

**Hvorfor anbefales det ikke ofte at aktivere eller deaktivere websteder for tidligere versioner?**

Når du deaktiverer et tidligere aktiveret websted, udløses en oprydningsproces. Denne proces tager tid at fuldføre. Hvis det samme websted aktiveres igen, skal efterfyldningsprocessen for at genindfylde webstedet køres igen. Både oprydnings- og efterfyldningsprocesserne er tids- og ressourcekrævende. Vi anbefaler derfor, at du nøje overvejer og planlægger, hvilke websteder du vil aktivere til historisk version, så du kan undgå gentagne gange at aktivere og deaktivere historiske versioner for et websted.
