---
title: Begrænsninger for indholdssøgning og Core eDiscovery i overholdelsescenteret
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om de begrænsninger, der gælder for indholdssøgning og kerne eDiscovery-funktioner i Microsoft 365 Overholdelsescenter.
ms.openlocfilehash: ad72dfa1d599a908a56b3b6530433ccb5ed23df4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715944"
---
# <a name="limits-for-ediscovery-search"></a>Begrænsninger for eDiscovery-søgning

Der anvendes forskellige begrænsninger for eDiscovery-søgeværktøjer i Microsoft 365 Overholdelsescenter. Dette omfatter søgninger, der køres  på siden Indholdssøgning og søgninger, der er knyttet til en eDiscovery-sag på **den centrale eDiscovery-side**. Disse begrænsninger hjælper med at opretholde tilstand og kvalitet af tjenester, der leveres til organisationer. Der er også begrænsninger relateret til indeksering af mails i Exchange Online til søgning. Du kan ikke ændre begrænsningerne for eDiscovery-søgninger eller mailindeksering, men du skal være opmærksom på dem, så du kan tage højde for disse begrænsninger, når du planlægger, kører og foretager fejlfinding af eDiscovery-søgninger.

Du kan finde begrænsninger for Advanced eDiscovery i [Begrænsninger i Advanced eDiscovery](limits-ediscovery20.md)

## <a name="search-limits"></a>Søgebegrænsninger

I følgende tabel vises søgebegrænsningerne, når du bruger værktøjet til indholdssøgning i Microsoft 365 Overholdelsescenter og for søgninger, der er knyttet til en grundlæggende eDiscovery-sag.

<br>

****

|Beskrivelse af grænse|Grænse|
|---|---|
|Det maksimale antal postkasser eller websteder, der kan søges i i en enkelt søgning|Ingen grænse <sup>1</sup>|
|Det maksimale antal søgninger, der kan køre på samme tid i organisationen.|30|
|Det maksimale antal søgninger i hele organisationen, der kan køres på samme tid.|3|
|Det maksimale antal søgninger, som en enkelt bruger kan starte på samme tid. Denne grænse rammes højst sandsynligt, når brugeren forsøger at starte flere søgninger ved hjælp af kommandoen **Get-ComplianceSearch \|Start-ComplianceSearch** i Security & Compliance Center PowerShell.|10|
|Det maksimale antal elementer pr. brugerpostkasse, der vises på eksempelsiden, når du får vist resultater fra indholdssøgningen.|100|
|Det maksimale antal elementer, der findes i alle brugerpostkasser, som muligvis kan vises på eksempelsiden, når søgeresultaterne vises. De nyeste elementer vises.|1.000 <sup>2</sup>|
|Det maksimale antal brugerpostkasser, der kan vises eksempler for søgeresultater. Hvis der er mere end 1000 postkasser, der indeholder indhold, der svarer til søgeforespørgslen, vil kun de øverste 1000 postkasser med de fleste søgeresultater være tilgængelige til forhåndsvisning.|1,000|
|Det maksimale antal elementer, der findes på SharePoint og OneDrive for Business, der vises på eksempelsiden, når søgeresultaterne vises. De nyeste elementer vises.|200|
|Det maksimale antal websteder (i SharePoint og OneDrive for Business), der kan gennemses for søgeresultater. Hvis der er mere end 200 websteder i alt, der indeholder indhold, der svarer til søgeforespørgslen, vil kun de øverste 200 websteder med de fleste søgeresultater være tilgængelige til forhåndsvisning.|200|
|Det maksimale antal elementer pr. postkasse med offentlig mappe, der vises på eksempelsiden, når du får vist resultater fra indholdssøgningen.|100|
|Det maksimale antal elementer, der findes i alle postkasser i offentlige mapper, der vises på eksempelsiden, når indholdssøgningsresultater vises.|200|
|Det maksimale antal postkasser i offentlige mapper, der kan vises i søgeresultaterne. Hvis der er mere end 500 postkasser i offentlige mapper, der indeholder indhold, der svarer til søgeforespørgslen, vil kun de øverste 500 postkasser i den offentlige mappe med de fleste søgeresultater være tilgængelige til forhåndsvisning.|500|
|Den maksimale størrelse på et element, der kan vises på eksempelsiden.|10.000.000 byte (ca. 9,5 MB)|
|Det maksimale antal tegn for søgeforespørgslen (herunder operatorer og betingelser) for en søgning. <p> **Bemærk!** Denne grænse træder i kraft, når forespørgslen er udvidet og indeholder tegn fra nøgleordsforespørgslen, eventuelle filtre for søgetilladelser, der anvendes til brugeren, og URL-adresserne for alle placeringer. Det betyder, at forespørgslen udvides i forhold til hver af nøgleordene. Hvis en søgeforespørgsel f.eks. indeholder 15 nøgleord og yderligere parametre og betingelser, udvides forespørgslen 15 gange, hver med de andre parametre og betingelser i forespørgslen. Så selvom antallet af tegn i søgeforespørgslen kan være under grænsen, er det den udvidede forespørgsel, der kan bidrage til at overskride denne grænse.|**Postkasser:** 10.000. <p> **Websteder:** 4.000, når der søges på alle websteder eller 2.000, når der søges på op til 20 websteder. <sup>3</sup>|
|Det maksimale antal varianter, der returneres, når du bruger et jokertegn med præfiks til at søge efter et nøjagtigt udtryk i en søgeforespørgsel, eller når du bruger et præfiks med jokertegn og operatoren **NEAR** Boolean.|10.000 <sup>4</sup>|
|Det mindste antal alfategn for præfiks jokertegn; f.eks `time*`. , `one*`eller `set*`.|3|
|Det maksimale antal postkasser i en søgning, som du kan slette elementer i ved at udføre en "søgning og sletning"-handling (ved hjælp af kommandoen **New-ComplianceSearchAction -Tøm** ). Hvis den søgning, du udfører en tømningshandling for, har flere kildepostkasser end denne grænse, mislykkes handlingen for at fjerne. Du kan finde flere oplysninger om søgning og [tømning i Søg efter og slet mails i organisationen](search-for-and-delete-messages-in-your-organization.md).|50,000|
|Det maksimale antal placeringer i en søgning, som du kan eksportere elementer fra. Hvis søgningen, som du eksporterer, har flere placeringer end denne grænse, mislykkes eksporten. Få mere at vide under [Eksportér resultater fra indholdssøgning](export-search-results.md).|100,000|

> [!NOTE]
> <sup>1</sup> Selvom du kan søge i et ubegrænset antal postkasser i en enkelt søgning, kan du kun downloade de eksporterede søgeresultater fra maksimalt 100.000 postkasser ved hjælp af eDiscovery-eksportværktøjet i Microsoft 365 Overholdelsescenter.
>
> <sup>2</sup> Formålet med eksempelsiden er at vise en begrænset stikprøve af resultaterne. Selv ved store søgninger med tusindvis af resultater kan antallet af elementer, der vises på eksempelsiden, og ofte være meget mindre end den maksimalt mulige værdi på 1000. Hvis du vil se de komplette søgeresultater, skal du eksportere resultaterne.
>
> <sup>3</sup> Når du SharePoint og OneDrive for Business en placering, tælles tegnene i URL-adresserne for de websteder, der søges efter, med i denne grænse.
>
> <sup>4</sup> Ved forespørgsler, der ikke er udtryk (en nøgleordsværdi, der ikke bruger dobbelte anførselstegn), bruger vi et særligt præfiksindeks. Dette fortæller os, at et ord forekommer i et dokument, men ikke der, hvor det forekommer i dokumentet. For at udføre en sætningsforespørgsel (en nøgleordsværdi med dobbelte anførselstegn) skal vi sammenligne placeringen i dokumentet med ordene i udtrykket. Det betyder, at vi ikke kan bruge præfiksindekset for udtryksforespørgsler. I dette tilfælde udvider vi forespørgslen internt med alle mulige ord, som præfikset udvides til; f.eks `"time*"` . kan udvide til `"time OR timer OR times OR timex OR timeboxed OR ..."`. 10.000 er det maksimale antal varianter, som ordet kan udvides til, ikke antallet af dokumenter, der matcher forespørgslen. Der er ingen øvre grænse for udtryk, der ikke er udtryk.

## <a name="search-times"></a>Søgetider

Microsoft indsamler oplysninger om ydeevnen for søgninger, der køres af alle organisationer. Selvom kompleksiteten af søgeforespørgslen kan påvirke søgetider, er den største faktor, der påvirker, hvor lang tid søgninger tager, antallet af postkasser, der søges i. Selvom Microsoft ikke leverer en serviceaftale for søgetider, viser følgende tabel gennemsnitlige søgetider for søgning i samlinger baseret på antallet af postkasser, der er inkluderet i søgningen.

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

I følgende tabel vises begrænsningerne, når resultaterne af en indholdssøgning eksporteres. Disse begrænsninger gælder også, når du eksporterer indhold fra en Core eDiscovery-sag.

<br>

****

|Beskrivelse af grænse|Grænse|
|---|---|
|Maksimale mængde data, der kan eksporteres, fra en enkelt søgning  <p> **Bemærk!** Hvis søgeresultaterne er større end 2 TB, skal du overveje at bruge datointervaller eller andre typer filtre for at mindske den samlede størrelse af søgeresultaterne.|2 TB|
|Maksimalt kan en organisation eksportere på en enkelt dag <p> **Bemærk!** Denne grænse nulstilles dagligt kl. 12:00 UTC|2 TB|
|Maksimalt antal samtidige eksporter, der kan køres samtidigt i din organisation <p> **Bemærk!** Kørsel af **en rapport tæller** kun eksport med i de samlede samtidige eksporter for organisationen. Hvis tre brugere udfører 3 eksporter hver, kan der kun udføres én anden eksport. Uanset om det er eksport af en rapport eller søgeresultater, kan der ikke udføres andre eksporter, før den ene er fuldført.|10|
|Maksimumeksporter En enkelt bruger kan køre ad gangen|3|
|Maksimale antal postkasser til søgeresultater, der kan downloades ved hjælp af eDiscovery-eksportværktøjet|100,000|
|Maksimumstørrelse på PST-fil, der kan eksporteres <p> **Bemærk!** Hvis søgeresultaterne fra en brugers postkasse er større end 10 GB, eksporteres søgeresultaterne for postkassen i to (eller flere) separate PST-filer. Hvis du vælger at eksportere alle søgeresultater i en enkelt PST-fil, overser PST-filen til flere PST-filer, hvis den samlede størrelse af søgeresultaterne er større end 10 GB. Hvis du vil ændre denne standardstørrelse, kan du redigere registreringsdatabasen Windows på den computer, du bruger til at eksportere søgeresultaterne. Se [Skift størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater](change-the-size-of-pst-files-when-exporting-results.md). Søgeresultaterne fra en bestemt postkasse opdeles ikke mellem flere PST-filer, medmindre indholdet af en enkelt postkasse er mere end 10 GB. Hvis du vælger at eksportere søgeresultaterne i én PST-fil, der indeholder alle meddelelser i en enkelt mappe, og søgeresultaterne er større end 10 GB, organiseres elementerne stadig i kronologisk rækkefølge, så de oversøges i flere PST-filer baseret på den sendte dato.|10 GB|
|Bedøm, hvor søgeresultaterne fra postkasser og websteder uploades til en Microsoft-leveret placering Azure Storage placering.|Maksimalt 2 GB pr. time|

## <a name="indexing-limits-for-email-messages"></a>Indekseringsgrænser for mails

I følgende tabel beskrives de indekseringsgrænser, der kan medføre, at en mail returneres som et ikke-indekseret element eller et delvist indekseret element i resultaterne af en indholdssøgning.

<br>

****

|Indekseringsgrænse|Maksimumværdi|Beskrivelse|
|---|---|---|
|Maksimumstørrelse for vedhæftede filer|150 MB|Den maksimale størrelse på en vedhæftet fil i en mail, der kan fortolkes til indeksering. Vedhæftede filer, der grænser denne grænse, kan ikke fortolkes til indeksering, og meddelelsen med den vedhæftede fil markeres som delvist indekseret. <p> **Bemærk!** Fortolkning er den proces, hvor indekseringstjenesten udtrækker tekst fra den vedhæftede fil, fjerner unødvendige tegn som tegnsætningstegn og mellemrum og derefter opdeler teksten i ord (i en proces kaldet tokenisering), som derefter gemmes i indekset.|
|Maksimale antal vedhæftede filer|250|Det maksimale antal filer, der er vedhæftet en mail, som stadig kan fortolkes til indeksering. Hvis en meddelelse indeholder mere end 250 vedhæftede filer, bliver de første 250 vedhæftede filer fortolket og indekseret, og meddelelsen markeres som delvist indekseret, fordi den havde flere vedhæftede filer, som ikke blev fortolket.|
|Maksimal dybde for vedhæftede filer|30|Det maksimale antal indlejrede vedhæftede filer, der fortolkes. Hvis en mail f.eks. har en anden meddelelse vedhæftet til sig, og den vedhæftede meddelelse har et vedhæftet Word-dokument, indekseres Word-dokumentet og den vedhæftede meddelelse. Denne funktionsmåde fortsætter for op til 30 indlejrede vedhæftede filer.|
|Maksimale antal vedhæftede billeder|0|Et billede, der er vedhæftet en mail, ignoreres af parseren og indekseres ikke.|
|Maksimal tid, der bruges på fortolkning af et element|30 sekunder|Der bliver maksimalt brugt 30 sekunder på fortolkning af et element til indeksering. Hvis fortolkningstiden overstiger 30 sekunder, markeres elementet som delvist indekseret.|
|Maksimalt parseroutput|2 millioner tegn|Den maksimale mængde tekstoutput fra parseren, der er indekseret. Hvis parseren f.eks. udtrækker 8 millioner tegn fra et dokument, er det kun de første 2 millioner tegn, der indekseres.|
|Maksimalt antal anmærkningstokens|2 millioner|Når en mail er indekseret, anmærkes hvert ord med forskellige behandlingsinstruktioner, der angiver, hvordan ordet skal indekseres. Hvert sæt af behandlingsinstruktioner kaldes et anmærkningstoken. For at bevare kvaliteten af tjenesten i Office 365 er der en begrænsning på to millioner anmærkningstokens for en mail.|
|Maksimal brødtekststørrelse i indeks|67 millioner tegn|Det samlede antal tegn i brødteksten i en mail og dens vedhæftede filer. Når en mail er indekseret, sammenfejes al tekst i meddelelsens brødtekst og alle vedhæftede filer i en enkelt streng. Den maksimale størrelse for denne streng, der er indekseret, er 67 millioner tegn.|
|Maksimalt antal unikke tokens i brødteksten|1 million|Som tidligere nævnt er tokens resultatet af at udtrække tekst fra indholdet, fjerne tegnsætning og mellemrum og derefter inddele den i ord (kaldet tokens), der er gemt i indekset. Sætningen indeholder f.eks `"cat, mouse, bird, dog, dog"` . fem tokens. Men kun 4 af disse er unikke tokens. Der er en begrænsning på én million entydige tokens pr. mail, som hjælper med at forhindre, at indekset bliver for stort med tilfældige tokens.|
|||

## <a name="more-information"></a>Flere oplysninger

Der er yderligere begrænsninger, der er relateret til forskellige aspekter af søgning efter indhold, f.eks. indeksering af indhold. Du kan finde flere oplysninger om disse begrænsninger i følgende emner:

- [Delvist indekserede elementer i indholdssøgning](partially-indexed-items-in-content-search.md)

- [Undersøgelse af delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)

- [Søgebegrænsninger for SharePoint Online](/sharepoint/search-limits)

Du kan finde oplysninger om indholdssøgninger i:

- [Indholdssøgning i Microsoft 365](content-search.md)

- [Søge efter indhold i en core eDiscovery-sag](search-for-content-in-core-ediscovery.md)

- [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)

Du kan finde oplysninger om sagsbegrænsninger relateret til Core eDiscovery Advanced eDiscovery, under:

- [Begrænsninger i Core eDiscovery](limits-core-ediscovery.md)

- [Begrænsninger i Advanced eDiscovery](limits-ediscovery20.md)
