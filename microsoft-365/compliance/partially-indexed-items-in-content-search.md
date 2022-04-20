---
title: Delvist indekserede elementer i indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnindexedItemsLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: d1691de4-ca0d-446f-a0d0-373a4fc8487b
description: Få mere at vide om ikke-indekserede elementer i Exchange og SharePoint, som du kan inkludere i en eDiscovery-søgning, som du kører på Microsoft Purview-overholdelsesportalen.
ms.openlocfilehash: 3e4f9521151755f97f3ad4b824c763f3ab5d807f
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64932039"
---
# <a name="partially-indexed-items-in-ediscovery"></a>Delvist indekserede elementer i eDiscovery

En Microsoft Purview eDiscovery-søgning, som du kører fra Microsoft Purview-overholdelsesportalen, inkluderer automatisk delvist indekserede elementer i de anslåede søgeresultater, når du kører en søgning. Delvist indekserede elementer er Exchange postkasseelementer og dokumenter på SharePoint og OneDrive for Business websteder, der af en eller anden grund ikke er fuldt indekseret til søgning. I Exchange indeholder et delvist indekseret element typisk en fil (af en filtype, der ikke kan indekseres), som er knyttet til en mail. Her er nogle andre årsager til, at elementer ikke kan indekseres til søgning og returneres som delvist indekserede elementer, når du kører en eDiscovery-søgning:
  
- Filtypen kan ikke genkendes eller understøttes ikke til indeksering.

- Meddelelser har en vedhæftet fil, der ikke kan åbnes, f.eks. billedfiler. dette er den mest almindelige årsag til delvist indekserede mailelementer.

- Filtypen understøttes til indeksering, men der opstod en indekseringsfejl for en bestemt fil.

- Der er knyttet for mange filer til en mail.

- En fil, der er knyttet til en mail, er for stor.

- En fil krypteres med ikke-Microsoft-teknologier.

- En fil er beskyttet med adgangskode.

> [!NOTE]
> De fleste organisationer har mindre end 1 % indhold efter volumen og mindre end 12 % efter størrelse, der er delvist indekseret. Årsagen til forskellen mellem volumen og størrelse er, at større filer har en højere sandsynlighed for at indeholde indhold, der ikke kan indekseres fuldstændigt.
  
I forbindelse med juridiske undersøgelser kan din organisation blive bedt om at gennemse delvist indekserede elementer. Du kan også angive, om delvist indekserede elementer skal medtages, når du eksporterer søgeresultater til en lokal computer, eller når du forbereder resultaterne til analyse med eDiscovery (Premium). Du kan finde flere oplysninger [under Undersøgelse af delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Filtyper, der ikke er indekseret til søgning

Visse filtyper, f.eks. bitmapfiler eller MP3-filer, indeholder ikke indhold, der kan indekseres. Derfor udfører søgeindekseringsserverne i Exchange og SharePoint ikke fuldtekstindeksering på disse filtyper. Disse filtyper anses for at være filtyper, der ikke understøttes. Der er også filtyper, hvor fuldtekstindeksering er deaktiveret, enten som standard eller af en administrator. Ikke-understøttede og deaktiverede filtyper er mærket som ikke-indekserede elementer i indholdssøgninger. Som tidligere nævnt kan delvist indekserede elementer medtages i sættet af søgeresultater, når du kører en søgning, eksporterer søgeresultaterne til en lokal computer eller forbereder søgeresultater til eDiscovery (Premium).
  
Du kan se en liste over understøttede og deaktiverede filformater i følgende emner:
  
-  -  Exchange [File-formater, der er indekseret af Exchange Search](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

-  -  Exchange [Hent-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

-  -  SharePoint [Standard-gennemsøgte filtypenavne og fortolkede filtyper i SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Meddelelser og dokumenter med delvist indekserede filtyper kan returneres i søgeresultater

Det er ikke alle mails med en delvist indekseret vedhæftet fil eller alle delvist indekserede SharePoint dokument, der returneres automatisk som et delvist indekseret element. Det skyldes, at andre meddelelses- eller dokumentegenskaber, f.eks. egenskaben **Emne** i mails og egenskaberne **Titel** eller **Forfatter** for dokumenter, indekseres og kan søges i. En nøgleordssøgning efter "økonomisk" returnerer f.eks. elementer med en delvist indekseret vedhæftet fil, hvis nøgleordet vises i emnet i en mail eller i filnavnet eller titlen på et dokument. Men hvis nøgleordet kun vises i filens brødtekst, returneres meddelelsen eller dokumentet som et delvist indekseret element.
  
På samme måde medtages meddelelser med delvist indekserede vedhæftede filer og dokumenter af en delvist indekseret filtype i søgeresultaterne, når andre meddelelses- eller dokumentegenskaber, der er indekserede og søgbare, stemmer overens med søgekriterierne. Meddelelsesegenskaber, der er indekseret til søgning, omfatter datoer for afsendelse og modtagelse, afsender og modtager, filnavnet på en vedhæftet fil og tekst i meddelelsens brødtekst. Dokumentegenskaber, der er indekseret til søgning, omfatter oprettelses- og ændringsdatoer. Selvom en vedhæftet meddelelse kan være et delvist indekseret element, medtages meddelelsen i de almindelige søgeresultater, hvis værdien af andre meddelelses- eller dokumentegenskaber stemmer overens med søgekriterierne.
  
Du kan finde en liste over mail- og dokumentegenskaber, som du kan søge efter ved hjælp af eDiscovery-værktøjer på overholdelsesportalen, under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Hvis et postkasseelement flyttes fra en mappe, der er indekseret til en mappe, der ikke er indekseret, angives et flag til unindex-elementet, og elementet fjernes fra indekset og kan ikke søges i. Hvis det samme element senere flyttes tilbage til en mappe, der er indekseret, nulstilles flaget ikke. Det betyder, at elementet forbliver ikke-indekseret og ikke kan søges i.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Delvist indekserede elementer, der er inkluderet i søgeresultaterne

Din organisation skal muligvis identificere og udføre yderligere analyser af delvist indekserede elementer for at bestemme, hvad de er, hvad de indeholder, og om de er relevante for en bestemt undersøgelse. Som tidligere forklaret medtages de delvist indekserede elementer på de indholdsplaceringer, der søges efter, automatisk med de anslåede søgeresultater. Du har mulighed for at medtage disse delvist indekserede elementer, når du eksporterer søgeresultater eller forbereder søgeresultaterne til eDiscovery (Premium).
  
Vær opmærksom på følgende i forbindelse med delvist indekserede elementer:
  
- Når du kører en eDiscovery-søgning, vises det samlede antal og den samlede størrelse af delvist indekserede Exchange elementer (returneret af søgeforespørgslen) i søgestatistikken på pop op-siden og navngives som **ikke-indekserede elementer**. Statistikker over delvist indekserede elementer, der vises på pop op-siden, omfatter ikke delvist indekserede elementer på SharePoint websteder eller OneDrive konti.

- Hvis den søgning, du eksporterer resultater fra, var en søgning efter bestemte indholdsplaceringer eller alle indholdsplaceringer i din organisation, eksporteres kun de ikke-indekserede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Det vil sige, at hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, eksporteres alle ikke-indekserede elementer i den pågældende postkasse eller det pågældende websted ikke. Årsagen til dette er, at eksport af delvist indekserede elementer fra mange placeringer i organisationen kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og downloade søgeresultaterne.

    Hvis du vil eksportere delvist indekserede elementer fra alle indholdssteder for en søgning, skal du konfigurere søgningen til at returnere alle elementer (ved at fjerne eventuelle nøgleord fra søgeforespørgslen) og derefter kun eksportere delvist indekserede elementer, når du eksporterer søgeresultaterne (ved at klikke på **Kun elementer, der har et ukendt format, krypteres eller ikke er indekseret af andre årsager** under **Outputindstillinger**).

- Hvis du vælger at medtage alle postkasseelementer i søgeresultaterne, eller hvis en søgeforespørgsel ikke angiver nogen nøgleord eller kun angiver et datointerval, kopieres delvist indekserede elementer muligvis ikke til den PST-fil, der indeholder de delvist indekserede elementer. Det skyldes, at alle elementer, herunder eventuelle delvist indekserede elementer, automatisk medtages i de almindelige søgeresultater.

- Delvist indekserede elementer kan ikke vises. Du skal eksportere søgeresultaterne for at få vist delvist indekserede elementer, der returneres af søgningen.

   Når du eksporterer søgeresultater og medtager delvist indekserede elementer i eksporten, eksporteres der desuden delvist indekserede elementer fra SharePoint elementer til en mappe med navnet **Uncrawlable**. Når du eksporterer delvist indekserede Exchange elementer, eksporteres de forskelligt, afhængigt af om de delvist indekserede elementer svarede til søgeforespørgslen og konfigurationen af eksportindstillingerne. 

- I følgende tabel vises eksportfunktionsmåden for indekserede og delvist indekserede elementer, og om de hver især er inkluderet i de forskellige konfigurationsindstillinger for eksport.

  |**Eksportkonfiguration**|**Indekserede elementer, der svarer til søgeforespørgslen**|**Delvist indekserede elementer, der svarer til søgeforespørgslen**|**Delvist indekserede elementer, der ikke stemmer overens med søgeforespørgslen**|
  |:-----|:-----|:-----|:-----|
  |Eksportér kun indekserede elementer  <br/> |Eksporteret<br/> |Eksporteret (inkluderet i de indekserede elementer, der eksporteres)<br/>  |Ikke eksporteret <br/>|
  |Eksportér kun delvist indekserede elementer  <br/> |Ikke eksporteret  <br/> |Eksporteret (som delvist indekserede elementer)<br/> |Eksporteret (som delvist indekserede elementer)|
  |Eksportér indekserede og delvist indekserede elementer  <br/> |Eksporteret<br/> |Eksporteret (inkluderet i de indekserede elementer, der eksporteres)<br/>  |Eksporteret (som delvist indekserede elementer)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Løsning på brug af et datointerval til at udelade delvist indekserede elementer

I Indholdssøgning og Microsoft Purview eDiscovery (Standard) kan du ikke bruge et datointerval til at udelade delvist indekserede elementer fra at blive returneret af en søgeforespørgsel. Med andre ord medtages delvist indekserede elementer, der ligger uden for et datointerval, stadig som delvist indekserede elementer i søgestatistikken, og når du eksporterer delvist indekserede elementer. I eDiscovery (Premium) kan du udelade delvist indekserede elementer ved hjælp af et datointerval i en søgeforespørgsel.

Som en løsning på denne begrænsning anbefaler vi følgende procedure.

1. Opret og kør en søgning ved hjælp af en søgeforespørgsel, der opfylder dine krav og returnerer de ønskede resultater.

2. Eksportér resultaterne af søgningen fra trin 1, men medtag ikke delvist indekserede elementer i eksporten. Det gør du ved at vælge indstillingen **Alle elementer, bortset fra dem, der har et ukendt format, er krypteret eller ikke er indekseret af andre årsager** . <sup>1</sup>

   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

3. Opret og kør endnu en søgning, der bruger den samme søgeforespørgsel (og søger på de samme placeringer), som du brugte i trin 1. Føj følgende delsætning til den oprindelige forespørgsel ved hjælp af operatoren **AND** :

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   Hvis du tilføjer denne delsætning, returneres delvist indekserede elementer, der svarer til den oprindelige søgeforespørgsel, og som falder inden for et bestemt datointerval. <sup>2</sup>

4. Eksportér resultaterne af søgningen fra trin 3, og medtag denne gang delvist indekserede elementer i eksporten. Hvis du vil gøre dette, skal du vælge indstillingen **Alle elementer, herunder dem, der har et ukendt format, er krypteret eller ikke er indekseret af andre årsager** .

   > [!NOTE]
   > <sup>1</sup> Resultatet af trin 2 resulterer kun i eksport af indekserede elementer.<br/>
   > <sup>2</sup> Betingelsen, der bruges i trin 3, identificerer kun elementer med indekseringsfejl, der falder inden for det angivne datointerval. Den returnerer ikke nogen elementer, der er fuldt indekserede. Det betyder, at de elementer, der eksporteres i trin 4, kun indeholder ikke-indekserede elementer, der falder inden for datointervallet. Eksporten indeholder ikke indekserede elementer. Resultatet er, at det kombinerede output for trin 2 og trin 4 indeholder alle indekserede og ikke-indekserede elementer, der falder inden for det angivne datointerval.

Brug den anden søgning, du oprettede i trin 3, og den tilsvarende eksport til at få vist og få forståelse for de delvist indekserede elementer, der svarer til din oprindelige søgeforespørgsel. Eksporten fra den anden søgning omfatter også alle delvist indekserede elementer, der blev eksporteret, så du kan gennemse dem, hvis det er nødvendigt.

> [!TIP]
> I den forrige procedure kan du eksportere de faktiske søgeresultater eller kun eksportere en rapport.

## <a name="indexing-limits-for-messages"></a>Indekseringsgrænser for meddelelser

I følgende tabel beskrives de indekseringsgrænser, der kan resultere i, at en mail returneres som et delvist indekseret element i en eDiscovery-søgning i Microsoft 365.
  
Du kan finde en liste over indekseringsgrænser for SharePoint dokumenter under [Søgegrænser for SharePoint Online](/sharepoint/search-limits).
  
|**Indekseringsgrænse**|**Maksimumværdi**|**Beskrivelse**|
|:-----|:-----|:-----|
|Maksimal størrelse på vedhæftede filer (undtagen Excel filer)  <br/> |150 MB  <br/> |Den maksimale størrelse af en vedhæftet fil, der fortolkes til indeksering. Alle vedhæftede filer, der er større end denne grænse, fortolkes ikke til indeksering, og meddelelsen med den vedhæftede fil markeres som delvist indekseret.  <br/><br/> **Bemærk:** Fortolkning er den proces, hvor indekseringstjenesten udtrækker tekst fra den vedhæftede fil, fjerner unødvendige tegn som tegnsætning og mellemrum og derefter opdeler teksten i ord (i en proces kaldet tokenisering), der derefter gemmes i indekset.           |
|Maksimal størrelse på Excel filer  <br/> |4 MB  <br/> |Den maksimale størrelse på en Excel fil, der er placeret på et websted eller knyttet til en mail, som skal analyseres til indeksering. Alle Excel filer, der er større end denne grænse, fortolkes ikke, og filen eller mailen med den vedhæftede fil markeres som ikke-indekseret.  <br/> |
|Maksimalt antal vedhæftede filer  <br/> |250  <br/> |Det maksimale antal filer, der er knyttet til en mail, som skal fortolkes til indeksering. Hvis en meddelelse indeholder mere end 250 vedhæftede filer, fortolkes og indekseres de første 250 vedhæftede filer, og meddelelsen markeres som delvist indekseret, fordi der var flere vedhæftede filer, der ikke blev fortolket.  <br/> |
|Maksimal dybde på vedhæftede filer  <br/> |30  <br/> |Det maksimale antal indlejrede vedhæftede filer, der fortolkes. Hvis en mail f.eks. har en anden meddelelse vedhæftet, og den vedhæftede meddelelse har et vedhæftet Word-dokument, indekseres Word-dokumentet og den vedhæftede meddelelse. Denne funktionsmåde fortsætter i op til 30 indlejrede vedhæftede filer.  <br/> |
|Maksimalt antal vedhæftede billeder  <br/> |0  <br/> |Et billede, der er knyttet til en mail, springes over af fortolkeren og er ikke indekseret.  <br/> |
|Den maksimale tid, der er brugt på at fortolke et element  <br/> |30 sekunder  <br/> |Der bruges maksimalt 30 sekunder på at fortolke et element til indeksering. Hvis fortolkningstiden overstiger 30 sekunder, markeres elementet som delvist indekseret.  <br/> |
|Maksimalt parseroutput  <br/> |2 millioner tegn  <br/> |Den maksimale mængde tekstoutput fra den parser, der er indekseret. Hvis fortolkeren f.eks. udtrækkede 8 millioner tegn fra et dokument, indekseres kun de første 2 millioner tegn.  <br/> |
|Maksimalt antal anmærkningstokens  <br/> |2 millioner  <br/> |Når en mail indekseres, anmærkes hvert ord med forskellige behandlingsinstruktioner, der angiver, hvordan ordet skal indekseres. Hvert sæt behandlingsinstruktioner kaldes et anmærkningstoken. For at opretholde kvaliteten af tjenesten i Office 365 er der en grænse på 2 millioner anmærkningstokens for en mail.  <br/> |
|Maksimal brødtekststørrelse i indekset  <br/> |67 millioner tegn  <br/> |Det samlede antal tegn i brødteksten i en mail og alle dens vedhæftede filer. Når en mail indekseres, sammenkædes al tekst i meddelelsens brødtekst og i alle vedhæftede filer til en enkelt streng. Den maksimale størrelse på denne streng, der indekseres, er 67 millioner tegn.  <br/> |
|Maksimalt antal entydige tokens i brødteksten  <br/> |1 million  <br/> |Som tidligere forklaret er tokens resultatet af at udtrække tekst fra indhold, fjerne tegnsætning og mellemrum og derefter opdele det i ord (kaldet tokens), der er gemt i indekset. Sætningen  `"cat, mouse, bird, dog, dog"` indeholder f.eks. 5 tokens. Men kun fire af disse er unikke tokens. Der er en grænse på 1 million entydige tokens pr. mail, hvilket hjælper med at forhindre, at indekset bliver for stort med tilfældige tokens.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Flere oplysninger om delvist indekserede elementer

- Da egenskaber for meddelelser og dokumenter og deres metadata er indekseret, kan en nøgleordssøgning returnere resultater, hvis nøgleordet vises i de indekserede metadata. Den samme nøgleordssøgning returnerer muligvis ikke det samme element, hvis nøgleordet kun vises i indholdet af et element med en filtype, der ikke understøttes. I dette tilfælde returneres elementet som et delvist indekseret element.

- Hvis et delvist indekseret element medtages i søgeresultaterne, fordi det opfylder søgeforespørgselskriterierne, medtages det ikke som et delvist indekseret element i den anslåede søgestatistik. Den medtages heller ikke i delvist indekserede elementer, når du eksporterer søgeresultater.

- Selvom en filtype understøttes til indeksering og er indekseret, kan der være indekserings- eller søgefejl, der medfører, at en fil returneres som et delvist indekseret element. Det kan f.eks. være en delvis succes at søge i en stor Excel fil (fordi de første 4 MB indekseres), men det mislykkes derefter, fordi grænsen for filstørrelsen er overskredet. I dette tilfælde er det muligt, at den samme fil returneres sammen med søgeresultaterne og som et delvist indekseret element.

- Filer, der er krypteret med [Microsoft-krypteringsteknologier](encryption.md) og er knyttet til en mail, der opfylder kriterierne i en søgning, kan gennemses og dekrypteres, når der eksporteres. På nuværende tidspunkt indekseres filer, der er krypteret med Microsofts krypteringsteknologier (og gemt i SharePoint eller OneDrive for Business), delvist.

- Mails, der er krypteret med S/MIME, indekseres delvist. Dette omfatter krypterede meddelelser med eller uden vedhæftede filer.

- Mails, der er beskyttet ved hjælp af Azure Rights Management, indekseres og medtages i søgeresultaterne, hvis de stemmer overens med søgeforespørgslen. Rettighedsbeskyttede mails dekrypteres og kan gennemses og eksporteres. Denne funktionalitet kræver, at du er tildelt rollen RMS Decrypt, som som standard er tildelt til rollegruppen eDiscover Manager.

- Hvis du opretter en forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, sættes alle delvist indekserede elementer i venteposition. Dette omfatter delvist indekserede elementer, der ikke stemmer overens med søgeforespørgselskriterierne for ventepositionen. Du kan finde flere oplysninger om oprettelse af forespørgselsbaserede eDiscovery-ventepositioner under [Opret en eDiscovery-venteposition](create-ediscovery-holds.md).

## <a name="see-also"></a>Se også

[Undersøger delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)
