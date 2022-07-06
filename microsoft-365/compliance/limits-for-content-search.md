---
title: Grænser for indholdssøgning og eDiscovery (Standard) i Overholdelsescenter
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 78fe3147-1979-4c41-83bb-aeccf244368d
description: Få mere at vide om de grænser, der gælder for funktionerne til indholdssøgning og eDiscovery (Standard) i Microsoft Purview-compliance-portal.
ms.openlocfilehash: 79078818ca3975dcbfee0ce72b93f1c3d6039802
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629525"
---
# <a name="limits-for-ediscovery-search"></a>Grænser for eDiscovery-søgning

Der anvendes forskellige grænser for eDiscovery-søgeværktøjer i Microsoft Purview-compliance-portal. Dette omfatter søgninger, der kører på **indholdssøgesiden**, og søgninger, der er knyttet til en eDiscovery-sag på siden **eDiscovery (Standard).** Disse grænser hjælper med at opretholde sundhed og kvalitet af tjenester, der leveres til organisationer. Der er også grænser for indeksering af mails i Exchange Online til søgning. Du kan ikke ændre grænserne for eDiscovery-søgninger eller mailindeksering, men du skal være opmærksom på dem, så du kan tage disse begrænsninger i betragtning, når du planlægger, kører og foretager fejlfinding af eDiscovery-søgninger.

Du kan finde begrænsninger, der er relateret til værktøjet Microsoft Purview eDiscovery (Premium), [under Grænser i eDiscovery (Premium)](limits-ediscovery20.md)

## <a name="search-limits"></a>Søgegrænser

I følgende tabel vises søgegrænserne, når du bruger værktøjet til indholdssøgning på overholdelsesportalen og efter søgninger, der er knyttet til en Microsoft Purview eDiscovery (Standard)-sag.

<br>

****

|Beskrivelse af grænse|Grænse|
|---|---|
|Det maksimale antal postkasser eller websteder, der kan søges i i en enkelt søgning|Ingen grænse <sup>1</sup>|
|Det maksimale antal søgninger, der kan køre på samme tid i din organisation.|30|
|Det maksimale antal søgninger i hele organisationen, der kan køres på samme tid.|3|
|Det maksimale antal søgninger, som en enkelt bruger kan starte på samme tid. Denne grænse er sandsynligvis nået, når brugeren forsøger at starte flere søgninger ved hjælp af kommandoen **Get-ComplianceSearch \|Start-ComplianceSearch** i Security & Compliance PowerShell.|10|
|Det maksimale antal elementer pr. brugerpostkasse, der vises på eksempelsiden, når der vises resultater for indholdssøgning.|100|
|Det maksimale antal elementer, der findes i alle brugerpostkasser, som muligvis kan vises på eksempelsiden, når søgeresultaterne vises. De nyeste elementer vises.|1.000 <sup>2</sup>|
|Det maksimale antal brugerpostkasser, der kan gennemses for søgeresultater. Hvis der er mere end 1.000 postkasser, der indeholder indhold, der svarer til søgeforespørgslen, er det højst de øverste 1000 postkasser med de fleste søgeresultater, der er tilgængelige som prøveversion.|1,000|
|Det maksimale antal elementer, der findes på SharePoint og OneDrive for Business websteder, der vises på eksempelsiden, når søgeresultaterne vises. De nyeste elementer vises.|200|
|Det maksimale antal websteder (i SharePoint og OneDrive for Business), der kan gennemses for søgeresultater. Hvis der er mere end 200 websteder i alt, der indeholder indhold, der svarer til søgeforespørgslen, er det kun de øverste 200 websteder med flest søgeresultater, der er tilgængelige som prøveversion.|200|
|Det maksimale antal elementer pr. postkasse med offentlige mapper, der vises på eksempelsiden, når der vises resultater for indholdssøgning.|100|
|Det maksimale antal elementer, der blev fundet i alle offentlige mappepostkasser, som vises på eksempelsiden, når du får vist indholdssøgeresultater.|200|
|Det maksimale antal offentlige mappepostkasser, der kan vises i søgeresultaterne. Hvis der er mere end 500 postkasser med offentlige mapper, der indeholder indhold, der svarer til søgeforespørgslen, er det kun de øverste 500 postkasser med offentlige mapper med de fleste søgeresultater, der er tilgængelige som prøveversion.|500|
|Den maksimale størrelse af et element, der kan vises på eksempelsiden.|10.000.000 byte (ca. 9,5 MB)|
|Det maksimale antal tegn for søgeforespørgslen (herunder operatorer og betingelser) for en søgning. <p> **Bemærk:** Denne grænse træder i kraft, når forespørgslen er udvidet og indeholder tegn fra nøgleordsforespørgslen, eventuelle søgetilladelser filtre, der er anvendt på brugeren, og URL-adresserne for alle webstedsplaceringer. Det betyder, at forespørgslen udvides i forhold til hvert af nøgleordene. Hvis en søgeforespørgsel f.eks. har 15 nøgleord og yderligere parametre og betingelser, udvides forespørgslen 15 gange, hver med de andre parametre og betingelser i forespørgslen. Så selvom antallet af tegn i søgeforespørgslen kan være under grænsen, er det den udvidede forespørgsel, der kan bidrage til at overskride denne grænse.|**Postkasser:** 10.000. <p> **Websteder:** 4.000, når du søger på alle websteder eller 2.000, når du søger på op til 20 websteder. <sup>3</sup>|
|Det maksimale antal varianter, der returneres, når der bruges et præfiks jokertegn til at søge efter et nøjagtigt udtryk i en søgeforespørgsel, eller når du bruger et præfiks jokertegn og den **booleske operator NEAR** .|10.000 <sup>4</sup>|
|Det mindste antal alfategn for præfiks jokertegn. f.eks. `time*`, `one*`eller `set*`.|3|
|Det maksimale antal postkasser i en søgning, som du kan slette elementer i ved at udføre en "søg og fjern"-handling (ved hjælp af kommandoen **New-ComplianceSearchAction -Purge** ). Hvis der er flere kildepostkasser end denne grænse for den søgning, du foretager en tømninger af, mislykkes. Du kan finde flere oplysninger om søgning og tømning under [Søg efter og slet mails i din organisation](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Det maksimale antal placeringer i en søgning, som du kan eksportere elementer fra. Hvis den søgning, du eksporterer, har flere placeringer end denne grænse, mislykkes eksporten. Du kan finde flere oplysninger under [Eksportér resultater af indholdssøgning](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Selvom du kan søge i et ubegrænset antal postkasser i en enkelt søgning, kan du kun downloade de eksporterede søgeresultater fra maksimalt 100.000 postkasser ved hjælp af eDiscovery-eksportværktøjet på overholdelsesportalen.
>
> <sup>2</sup> Hensigten med eksempelsiden er at vise et begrænset eksempel på resultaterne. Selv for massive søgninger med tusindvis af resultater kan antallet af elementer, der vises på eksempelsiden, og det vil ofte være meget mindre end den maksimalt mulige værdi på 1000. Hvis du vil se de komplette søgeresultater, skal du eksportere resultaterne.
>
> <sup>3</sup> Når du søger i SharePoint og OneDrive for Business placeringer, tælles tegnene i URL-adresserne på de websteder, der søges efter, i forhold til denne grænse.
>
> <sup>4</sup> Til forespørgsler, der ikke er udtryk (en nøgleordsværdi, der ikke bruger dobbelte anførselstegn), bruger vi et særligt præfiksindeks. Dette fortæller os, at der forekommer et ord i et dokument, men ikke der, hvor det forekommer i dokumentet. Hvis du vil udføre en udtryksforespørgsel (en nøgleordsværdi med dobbelte anførselstegn), skal vi sammenligne placeringen i dokumentet med ordene i udtrykket. Det betyder, at vi ikke kan bruge præfiksindekset til udtryksforespørgsler. I dette tilfælde udvider vi forespørgslen internt med alle de mulige ord, som præfikset udvides til. kan f.eks `"time*"` . udvides til `"time OR timer OR times OR timex OR timeboxed OR ..."`. 10.000 er det maksimale antal varianter, ordet kan udvides til, ikke antallet af dokumenter, der svarer til forespørgslen. Der er ingen øvre grænse for ord, der ikke er udtryk.

## <a name="search-times"></a>Søgetider

Microsoft indsamler oplysninger om ydeevnen for søgninger, der køres af alle organisationer. Selvom kompleksiteten af søgeforespørgslen kan påvirke søgetiderne, er den største faktor, der påvirker, hvor lang tid det tager at søge, antallet af postkasser, der søges i. Selvom Microsoft ikke leverer en serviceniveauaftale for søgetider, vises de gennemsnitlige søgetider for samlingssøgninger i følgende tabel baseret på antallet af postkasser, der er inkluderet i søgningen.

<br>

****

|Antal postkasser|Gennemsnitlig søgetid|
|---|---|
|100|30 sekunder|
|1,000|45 sekunder|
|10,000|4 minutter|
|25,000|10 minutter|
|50,000|20 minutter|
|100,000|25 minutter|

## <a name="export-limits"></a>Eksportgrænser

I følgende tabel vises grænserne, når du eksporterer resultaterne af en indholdssøgning. Disse grænser gælder også, når du eksporterer indhold fra en eDiscovery-sag (Standard).

<br>

****

|Beskrivelse af grænse|Grænse|
|---|---|
|Den maksimale mængde data, der kan eksporteres, fra en enkelt søgning  <p> **Bemærk:** Hvis søgeresultaterne er større end 2 TB, kan du overveje at bruge datointervaller eller andre typer filtre til at reducere den samlede størrelse af søgeresultaterne.|2 TB|
|Det maksimale antal dage, en organisation kan eksportere <p> **Bemærk:** Denne grænse nulstilles dagligt kl. 12:00 UTC|2 TB|
|Det maksimale antal samtidige eksporter, der kan udføres på samme tid i organisationen <p> **Bemærk:** Kørsel af en **Eksport af rapport tæller kun** i forhold til den samlede samtidige eksport for din organisation. Hvis tre brugere udfører tre eksporter hver, kan der kun udføres én anden eksport. Uanset om den eksporterer en rapport eller søgeresultaterne, kan der ikke udføres andre eksporter, før en af dem er fuldført.|10|
|Det maksimale antal eksporter, som en enkelt bruger kan køre på en gang|3|
|Maksimalt antal postkasser til søgeresultater, der kan downloades ved hjælp af eDiscovery-eksportværktøjet|100,000|
|Maksimal størrelse på PST-fil, der kan eksporteres <p> **Bemærk:** Hvis søgeresultaterne fra en brugers postkasse er større end 10 GB, eksporteres søgeresultaterne for postkassen i to (eller flere) separate PST-filer. Hvis du vælger at eksportere alle søgeresultater i en enkelt PST-fil, vil PST-filen blive overført til flere PST-filer, hvis den samlede størrelse af søgeresultaterne er større end 10 GB. Hvis du vil ændre denne standardstørrelse, kan du redigere Windows-registreringsdatabasen på den computer, du bruger til at eksportere søgeresultaterne. Se [Skift størrelsen af PST-filer, når du eksporterer eDiscovery-søgeresultater](change-the-size-of-pst-files-when-exporting-results.md). Søgeresultaterne fra en bestemt postkasse opdeles ikke mellem flere PST-filer, medmindre indholdet fra en enkelt postkasse er mere end 10 GB. Hvis du vælger at eksportere søgeresultaterne i én PST-fil for , der indeholder alle meddelelser i en enkelt mappe, og søgeresultaterne er større end 10 GB, er elementerne stadig organiseret i kronologisk rækkefølge, så de vil blive overført til yderligere PST-filer baseret på afsendelsesdatoen.|10 GB|
|Bedøm, med hvilken søgeresultater fra postkasser og websteder uploades til en Microsoft-leveret Azure Storage-placering.|Maksimalt 2 GB pr. time|

## <a name="indexing-limits-for-email-messages"></a>Indekseringsgrænser for mails

I følgende tabel beskrives de indekseringsgrænser, der kan resultere i, at en mail returneres som et ikke-indekseret element eller et delvist indekseret element i resultaterne af en indholdssøgning.

<br>

****

|Indekseringsgrænse|Maksimumværdi|Beskrivelse|
|---|---|---|
|Maksimal størrelse på vedhæftede filer|150 MB|Den maksimale størrelse af en vedhæftet fil, der fortolkes til indeksering. Alle vedhæftede filer, der er større end denne grænse, fortolkes ikke til indeksering, og meddelelsen med den vedhæftede fil markeres som delvist indekseret. <p> **Bemærk:** Fortolkning er den proces, hvor indekseringstjenesten udtrækker tekst fra den vedhæftede fil, fjerner unødvendige tegn som tegnsætning og mellemrum og derefter opdeler teksten i ord (i en proces kaldet tokenisering), der derefter gemmes i indekset.|
|Maksimalt antal vedhæftede filer|250|Det maksimale antal filer, der er knyttet til en mail, som skal fortolkes til indeksering. Hvis en meddelelse indeholder mere end 250 vedhæftede filer, fortolkes og indekseres de første 250 vedhæftede filer, og meddelelsen markeres som delvist indekseret, fordi der var flere vedhæftede filer, der ikke blev fortolket.|
|Maksimal dybde på vedhæftede filer|30|Det maksimale antal indlejrede vedhæftede filer, der fortolkes. Hvis en mail f.eks. har en anden meddelelse vedhæftet, og den vedhæftede meddelelse har et vedhæftet Word-dokument, indekseres Word-dokumentet og den vedhæftede meddelelse. Denne funktionsmåde fortsætter i op til 30 indlejrede vedhæftede filer.|
|Maksimalt antal vedhæftede billeder|0|Et billede, der er knyttet til en mail, springes over af fortolkeren og er ikke indekseret.|
|Den maksimale tid, der er brugt på at fortolke et element|30 sekunder|Der bruges maksimalt 30 sekunder på at fortolke et element til indeksering. Hvis fortolkningstiden overstiger 30 sekunder, markeres elementet som delvist indekseret.|
|Maksimalt parseroutput|2 millioner tegn|Den maksimale mængde tekstoutput fra den parser, der er indekseret. Hvis fortolkeren f.eks. udtrækkede 8 millioner tegn fra et dokument, indekseres kun de første 2 millioner tegn.|
|Maksimalt antal anmærkningstokens|2 millioner|Når en mail indekseres, anmærkes hvert ord med forskellige behandlingsinstruktioner, der angiver, hvordan ordet skal indekseres. Hvert sæt behandlingsinstruktioner kaldes et anmærkningstoken. For at opretholde kvaliteten af tjenesten i Office 365 er der en grænse på 2 millioner anmærkningstokens for en mail.|
|Maksimal brødtekststørrelse i indekset|67 millioner tegn|Det samlede antal tegn i brødteksten i en mail og alle dens vedhæftede filer. Når en mail indekseres, sammenkædes al tekst i meddelelsens brødtekst og i alle vedhæftede filer til en enkelt streng. Den maksimale størrelse på denne streng, der indekseres, er 67 millioner tegn.|
|Maksimalt antal entydige tokens i brødteksten|1 million|Som tidligere forklaret er tokens resultatet af at udtrække tekst fra indhold, fjerne tegnsætning og mellemrum og derefter opdele det i ord (kaldet tokens), der er gemt i indekset. Sætningen `"cat, mouse, bird, dog, dog"` indeholder f.eks. 5 tokens. Men kun fire af disse er unikke tokens. Der er en grænse på 1 million entydige tokens pr. mail, hvilket hjælper med at forhindre, at indekset bliver for stort med tilfældige tokens.|
|||

## <a name="more-information"></a>Flere oplysninger

Der er yderligere grænser, der er relateret til forskellige aspekter af søgning efter indhold, f.eks. indholdsindeksering. Du kan få flere oplysninger om disse grænser i følgende emner:

- [Delvist indekserede elementer i indholdssøgning](partially-indexed-items-in-content-search.md)

- [Undersøger delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)

- [Søgegrænser for SharePoint Online](/sharepoint/search-limits)

Du kan finde oplysninger om indholdssøgninger i:

- [Indholdssøgning i Microsoft 365](content-search.md)

- [Søg efter indhold i en eDiscovery-sag (Standard)](search-for-content-in-core-ediscovery.md)

- [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)

Hvis du vil se sagsgrænser, der er relateret til eDiscovery (Standard) og eDiscovery (Premium), skal du se:

- [Grænser i eDiscovery (Standard)](limits-core-ediscovery.md)

- [Grænser i eDiscovery (Premium)](limits-ediscovery20.md)
