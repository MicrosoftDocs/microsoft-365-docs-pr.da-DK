---
title: Delvist indekserede elementer i Indholdssøgning og andre eDiscovery-værktøjer
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
description: Få mere at vide om unindexed elementer i Exchange og SharePoint, som du kan medtage i en eDiscovery-søgning, som du kører i Microsoft 365 Overholdelsescenter.
ms.openlocfilehash: b1adfaab1008cdfa9e7893273feaba38a71e85ac
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63589540"
---
# <a name="partially-indexed-items-in-ediscovery"></a>Delvist indekserede elementer i eDiscovery

En eDiscovery-søgning, som du kører fra Microsoft 365 Overholdelsescenter, medtager automatisk delvist indekserede elementer i de anslåede søgeresultater, når du kører en søgning. Delvist indekserede elementer er Exchange postkasseelementer og dokumenter på SharePoint og OneDrive for Business websteder, som af en eller anden grund ikke blev indekseret helt til søgning. I Exchange indeholder et delvist indekseret element typisk en fil (af en filtype, der ikke kan indekseres), som er vedhæftet en mail. Her er nogle andre årsager til, at elementer ikke kan indekseres til søgning og returneres som delvist indekserede elementer, når du kører en eDiscovery-søgning:
  
- Filtypen er ukendt eller understøttes ikke til indeksering.

- Meddelelser har en vedhæftet fil, der ikke kan åbnes, f.eks. billedfiler. dette er den mest almindelige årsag til delvist indekserede mailelementer.

- Filtypen understøttes til indeksering, men der opstod en indekseringsfejl for en bestemt fil.

- For mange filer vedhæftet en mail.

- En fil, der er vedhæftet en mail, er for stor.

- En fil er krypteret med ikke-Microsoft-teknologier.

- En fil er beskyttet med adgangskode.

> [!NOTE]
> De fleste organisationer har mindre end 1 % indhold efter volumen og mindre end 12 % efter størrelse, der er delvist indekseret. Årsagen til forskellen mellem mængde og størrelse er, at større filer har en større sandsynlighed for at indeholde indhold, der ikke kan indekseres fuldstændigt.
  
Ved juridiske undersøgelser kan det være nødvendigt, at din organisation gennemser delvist indekserede elementer. Du kan også angive, om du vil medtage delvist indekserede elementer, når du eksporterer søgeresultater til en lokal computer, eller når du forbereder resultaterne til analyse med Advanced eDiscovery. Få mere at vide under [Undersøgelse af delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Filtyper, der ikke er indekseret til søgning

Visse filtyper, f.eks. bitmap- eller MP3-filer, indeholder ikke indhold, der kan indekseres. Derfor udfører søgeindekseringsserverne i Exchange og SharePoint ikke fuld tekstindeksering på disse filtyper. Disse filtyper betragtes som ikke-understøttede filtyper. Der er også filtyper, hvor indeksering af hele teksten er blevet deaktiveret, enten som standard eller af en administrator. Ikke-understøttede og deaktiverede filtyper er mærket elementer, der ikke understøttes i indholdssøgninger. Som nævnt tidligere kan delvist indekserede elementer medtages i sættet af søgeresultater, når du kører en søgning, eksportere søgeresultaterne til en lokal computer eller forberede søgeresultaterne til Advanced eDiscovery.
  
Hvis du vil se en liste over understøttede og deaktiverede filformater, skal du se følgende emner:
  
-  -  Exchange [Filformater indekseret af Exchange Search](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

-  -  Exchange [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

-  -  SharePoint [Default gennemsøgte filtypenavne og fortolkede filtyper i SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Meddelelser og dokumenter med delvist indekserede filtyper kan returneres i søgeresultater

Ikke alle mails med delvist indekserede vedhæftede filer eller delvist indekserede dokumenter SharePoint automatisk som et delvist indekseret element. Det skyldes, at andre meddelelses- eller dokumentegenskaber, f.eks. egenskaben Emne i mails  og egenskaberne Titel eller Forfatter for dokumenter, indekseres og kan søges i.  For eksempel returnerer en søgning efter nøgleordet "finansiel" elementer med en delvist indekseret vedhæftet fil, hvis det pågældende nøgleord vises i emnet for en mail eller i filnavnet eller titlen på et dokument. Men hvis nøgleordet kun vises i brødteksten i filen, returneres meddelelsen eller dokumentet som et delvist indekseret element.
  
På samme måde medtages meddelelser med delvist indekserede vedhæftede filer og dokumenter af en delvist indekseret filtype i søgeresultaterne, når andre meddelelser eller dokumentegenskaber, som er indekseret og søgbare, matcher søgekriterierne. Meddelelsesegenskaber, der er indekseret til søgning, omfatter sendte og modtagne datoer, afsender og modtager, filnavnet på en vedhæftet fil og tekst i meddelelsesteksten. Dokumentegenskaber, der er indekseret til søgning, omfatter oprettede og ændrede datoer. Så selvom en vedhæftet fil i en meddelelse kan være et delvist indekseret element, medtages meddelelsen i de almindelige søgeresultater, hvis værdien af andre meddelelses- eller dokumentegenskaber svarer til søgekriterierne.
  
Hvis du vil have en liste over mail- og dokumentegenskaber, som du kan søge efter ved hjælp af eDiscovery-værktøjer i Microsoft 365 Overholdelsescenter, skal du se Nøgleordsforespørgsler og søgebetingelser [for eDiscovery](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Hvis et postkasseelement flyttes fra en mappe, der er indekseret til en mappe, der ikke er indekseret, angives et flag for at indeksere elementet, og elementet fjernes fra indekset og kan ikke søges i. Hvis det samme element senere flyttes tilbage til en mappe, der er indekseret, nulstilles flaget ikke. Det betyder, at elementet forbliver unindexed og ikke søgbart.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Delvist indekserede elementer, der er inkluderet i søgeresultaterne

Din organisation kan være nødvendig for at identificere og udføre yderligere analyse af delvist indekserede elementer for at bestemme, hvad de er, hvad de indeholder, og om de er relevante for en bestemt undersøgelse. Som beskrevet tidligere medtages de delvist indekserede elementer på de indholdsplaceringer, der søges automatisk i, med de anslåede søgeresultater. Du har mulighed for at medtage disse delvist indekserede elementer, når du eksporterer søgeresultater eller forbereder søgeresultaterne til Advanced eDiscovery.
  
Vær opmærksom på følgende vedrørende delvist indekserede elementer:
  
- Når du kører en eDiscovery-søgning, vises det samlede antal og størrelsen af delvist indekserede Exchange-elementer (der returneres af søgeforespørgslen) i søgestatistikken på pop op-siden og navngivet elementer, der ikke er indekseret **.** Statistik om delvist indekserede elementer, der vises på pop op-siden, inkluderer ikke delvist indekserede elementer på SharePoint websteder eller OneDrive konti.

- Hvis den søgning, du eksporterer resultater fra, var en søgning på bestemte placeringer med indhold eller alle placeringer med indhold i organisationen, eksporteres kun de uindsiderede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Med andre ord, hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, så eksporteres elementer, der ikke er inddæmt i den pågældende postkasse eller websted, ikke. Dette skyldes, at eksport af delvist indekserede elementer fra mange placeringer i organisationen kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og hente søgeresultaterne.

    Hvis du vil eksportere delvist indekserede elementer fra alle indholdsplaceringer til en søgning, skal du konfigurere søgningen til at returnere alle elementer (ved at fjerne eventuelle nøgleord fra søgeforespørgslen) og derefter kun eksportere delvist indekserede elementer, når du eksporterer søgeresultaterne (ved at klikke på Kun elementer, der har et ukendt **format,** er krypteret eller ikke er indekseret af andre årsager under **Outputindstillinger**).

- Hvis du vælger at medtage alle postkasseelementer i søgeresultaterne, eller hvis en søgeforespørgsel ikke angiver nogen nøgleord eller kun angiver et datoområde, bliver delvist indekserede elementer muligvis ikke kopieret til den PST-fil, der indeholder de delvist indekserede elementer. Dette skyldes, at alle elementer, herunder eventuelle delvist indekserede elementer, automatisk medtages i de almindelige søgeresultater.

- Delvist indekserede elementer kan ikke vises. Du skal eksportere søgeresultaterne for at få vist delvist indekserede elementer, der returneres af søgningen.

   Når du eksporterer søgeresultater og medtager delvist indekserede elementer i eksporten, eksporteres delvist indekserede elementer fra SharePoint-elementer desuden til en mappe med navnet **Unwlwlable**. Når du eksporterer delvist indekserede Exchange-elementer, eksporteres de forskelligt afhængigt af, om de delvist indekserede elementer matcher søgeforespørgslen og konfigurationen af eksportindstillingerne. 

- Følgende tabel viser eksportfunktionsmåden for indekserede og delvist indekserede elementer, og om hver af dem er inkluderet i de forskellige eksportkonfigurationsindstillinger.

  |**Eksportér konfiguration**|**Indekserede elementer, der svarer til søgeforespørgsel**|**Delvist indekserede elementer, der svarer til søgeforespørgslen**|**Delvist indekserede elementer, der ikke svarer til søgeforespørgslen**|
  |:-----|:-----|:-----|:-----|
  |Eksportér kun indekserede elementer  <br/> |Eksporteret<br/> |Eksporteret (inkluderet i de indekserede elementer, der eksporteres)<br/>  |Ikke eksporteret <br/>|
  |Eksportér kun delvist indekserede elementer  <br/> |Ikke eksporteret  <br/> |Eksporteret (som delvist indekserede elementer)<br/> |Eksporteret (som delvist indekserede elementer)|
  |Eksportere indekserede og delvist indekserede elementer  <br/> |Eksporteret<br/> |Eksporteret (inkluderet i de indekserede elementer, der eksporteres)<br/>  |Eksporteret (som delvist indekserede elementer)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Løsning til at bruge et datoområde til at udelukke delvist indekserede elementer

I Indholdssøgning og Core eDiscovery kan du ikke bruge et datointerval til at udelukke delvist indekserede elementer fra at blive returneret af en søgeforespørgsel. Med andre ord medtages delvist indekserede elementer, der ligger uden for et datoområde, stadig som delvist indekserede elementer i søgestatistikken, og når du eksporterer delvist indekserede elementer. I Advanced eDiscovery kan du udelade delvist indekserede elementer ved hjælp af et datoområde i en søgeforespørgsel.

Som en midlertidig løsning på denne begrænsning anbefaler vi følgende procedure.

1. Opret og kør en søgning ved hjælp af en søgeforespørgsel, der opfylder dine krav og returnerer de ønskede resultater.

2. Eksportér resultaterne af søgningen fra trin 1, men medtag ikke delvist indekserede elementer i eksporten. For at gøre dette skal du vælge indstillingen Alle elementer, undtagen dem, der har ukendt format, er krypteret **eller ikke** er indekseret af andre årsager til eksport. <sup>1</sup>

   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

3. Opret og kør en anden søgning, der bruger den samme søgeforespørgsel (og søger på de samme placeringer), som du brugte i trin 1. Tilføj følgende delsætning til den oprindelige forespørgsel ved hjælp af **operatoren AND** :

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   Hvis du tilføjer denne delsætning, returneres delvist indekserede elementer, der svarer til den oprindelige søgeforespørgsel, og som falder inden for et bestemt datointerval. <sup>2</sup>

4. Eksportér resultaterne af søgningen fra trin 3, og denne gang medtager delvist indekserede elementer i eksporten. For at gøre dette skal du markere indstillingen Alle elementer, herunder dem, der har ukendt format, er krypteret **eller ikke** blev indekseret af andre årsager til eksport.

   > [!NOTE]
   > <sup>1</sup> Outputtet fra trin 2 resulterer i, at indekserede elementer kun eksporteres.<br/>
   > <sup>2 Den betingelse</sup> , der blev brugt i trin 3, identificerer kun elementer med indekseringsfejl, der falder inden for det angivne datointerval. Den returnerer ikke nogen elementer, der er indekseret fuldt ud. Det betyder, at de elementer, der eksporteres på trin 4, kun inkluderer ikke-xede elementer, der falder inden for datointervallet. Eksporten indeholder ikke indekserede elementer. Som resultat indeholder den kombinerede output fra trin 2 og trin 4 alle indekserede og indekserede elementer, der falder inden for det angivne datointerval.

Brug den anden søgning, du oprettede på trin 3, og den tilsvarende eksport til at få vist og opnå forståelse for de delvist indekserede elementer, der svarer til din oprindelige søgeforespørgsel. Eksporten fra den anden søgning omfatter også alle delvist indekserede elementer, der er blevet eksporteret, så du kan gennemse dem, hvis det er nødvendigt.

> [!TIP]
> I den forrige procedure kan du eksportere de faktiske søgeresultater eller kun eksportere en rapport.

## <a name="indexing-limits-for-messages"></a>Indekseringsgrænser for meddelelser

I følgende tabel beskrives de indekseringsgrænser, der kan medføre, at en mail returneres som et delvist indekseret element i en eDiscovery-søgning i Microsoft 365.
  
Du kan finde en liste over indekseringsgrænser for SharePoint i [Søgebegrænsninger for SharePoint Online](/sharepoint/search-limits).
  
|**Indekseringsgrænse**|**Maksimumværdi**|**Beskrivelse**|
|:-----|:-----|:-----|
|Maksimale størrelse på vedhæftede filer (undtagen Excel filer)  <br/> |150 MB  <br/> |Den maksimale størrelse på en vedhæftet fil i en mail, der kan fortolkes til indeksering. Vedhæftede filer, der grænser denne grænse, kan ikke fortolkes til indeksering, og meddelelsen med den vedhæftede fil markeres som delvist indekseret.  <br/><br/> **Bemærk!** Fortolkning er den proces, hvor indekseringstjenesten udtrækker tekst fra den vedhæftede fil, fjerner unødvendige tegn som tegnsætningstegn og mellemrum og derefter opdeler teksten i ord (i en proces kaldet tokenisering), som derefter gemmes i indekset.           |
|Maksimumstørrelse på Excel filer  <br/> |4 MB  <br/> |Den maksimale størrelse på Excel fil, der er placeret på et websted eller vedhæftet en mail, og som stadig kan fortolkes til indeksering. Enhver Excel fil, der grænser denne grænse, kan ikke fortolkes, og filen eller mailen med den vedhæftede fil markeres som ikke-identificeret.  <br/> |
|Maksimale antal vedhæftede filer  <br/> |250  <br/> |Det maksimale antal filer, der er vedhæftet en mail, som stadig kan fortolkes til indeksering. Hvis en meddelelse indeholder mere end 250 vedhæftede filer, bliver de første 250 vedhæftede filer fortolket og indekseret, og meddelelsen markeres som delvist indekseret, fordi den havde flere vedhæftede filer, som ikke blev fortolket.  <br/> |
|Maksimal dybde for vedhæftede filer  <br/> |30  <br/> |Det maksimale antal indlejrede vedhæftede filer, der fortolkes. Hvis en mail f.eks. har en anden meddelelse vedhæftet til sig, og den vedhæftede meddelelse har et vedhæftet Word-dokument, indekseres Word-dokumentet og den vedhæftede meddelelse. Denne funktionsmåde fortsætter for op til 30 indlejrede vedhæftede filer.  <br/> |
|Maksimale antal vedhæftede billeder  <br/> |0  <br/> |Et billede, der er vedhæftet en mail, ignoreres af parseren og indekseres ikke.  <br/> |
|Maksimal tid, der bruges på fortolkning af et element  <br/> |30 sekunder  <br/> |Der bliver maksimalt brugt 30 sekunder på fortolkning af et element til indeksering. Hvis fortolkningstiden overstiger 30 sekunder, markeres elementet som delvist indekseret.  <br/> |
|Maksimalt parseroutput  <br/> |2 millioner tegn  <br/> |Den maksimale mængde tekstoutput fra parseren, der er indekseret. Hvis parseren f.eks. udtrækker 8 millioner tegn fra et dokument, er det kun de første 2 millioner tegn, der indekseres.  <br/> |
|Maksimalt antal anmærkningstokens  <br/> |2 millioner  <br/> |Når en mail er indekseret, anmærkes hvert ord med forskellige behandlingsinstruktioner, der angiver, hvordan ordet skal indekseres. Hvert sæt af behandlingsinstruktioner kaldes et anmærkningstoken. For at bevare kvaliteten af tjenesten i Office 365 er der en begrænsning på to millioner anmærkningstokens for en mail.  <br/> |
|Maksimal brødtekststørrelse i indeks  <br/> |67 millioner tegn  <br/> |Det samlede antal tegn i brødteksten i en mail og dens vedhæftede filer. Når en mail er indekseret, sammenfejes al tekst i meddelelsens brødtekst og alle vedhæftede filer i en enkelt streng. Den maksimale størrelse for denne streng, der er indekseret, er 67 millioner tegn.  <br/> |
|Maksimalt antal unikke tokens i brødteksten  <br/> |1 million  <br/> |Som tidligere nævnt er tokens resultatet af at udtrække tekst fra indholdet, fjerne tegnsætning og mellemrum og derefter inddele den i ord (kaldet tokens), der er gemt i indekset. Sætningen indeholder f.eks  `"cat, mouse, bird, dog, dog"` . fem tokens. Men kun 4 af disse er unikke tokens. Der er en begrænsning på én million entydige tokens pr. mail, som hjælper med at forhindre, at indekset bliver for stort med tilfældige tokens.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Flere oplysninger om delvist indekserede elementer

- Da meddelelses- og dokumentegenskaber og deres metadata er indekseret, kan en søgning med nøgleord som tidligere nævnt returnere resultater, hvis det pågældende nøgleord vises i de indekserede metadata. Men den samme søgning efter nøgleord returnerer muligvis ikke det samme element, hvis nøgleordet kun vises i indholdet af et element med en filtype, der ikke understøttes. I dette tilfælde ville elementet blive returneret som et delvist indekseret element.

- Hvis et delvist indekseret element er medtaget i søgeresultaterne, fordi det matcher søgeforespørgselskriterierne, medtages det ikke som et delvist indekseret element i den anslåede søgestatistik. Den medtages heller ikke i delvist indekserede elementer, når du eksporterer søgeresultater.

- Selvom en filtype understøttes til indeksering og er indekseret, kan der være indekserings- eller søgefejl, der medfører, at en fil returneres som et delvist indekseret element. Det kan f.eks. være delvist vellykket at søge i en stor Excel-fil (fordi de første 4 MB er indekseret), men det mislykkes derefter, fordi filstørrelsesgrænsen overskrides. I dette tilfælde er det muligt, at den samme fil returneres med søgeresultaterne og som et delvist indekseret element.

- Filer, der er krypteret [](encryption.md) med Microsoft-krypteringsteknologier og er vedhæftet en mail, der opfylder kriterierne for en søgning, kan gennemses og dekrypteres, når de eksporteres. På nuværende tidspunkt er filer, der er krypteret med Microsoft-krypteringsteknologier (og gemt i SharePoint eller OneDrive for Business), delvist indekseret.

- Mails, der er krypteret med S/MIME, er delvist indekseret. Dette omfatter krypterede meddelelser med eller uden vedhæftede filer.

- Mails, der er beskyttet ved hjælp af Azure Rights Management, indekseres og medtages i søgeresultaterne, hvis de svarer til søgeforespørgslen. Rettighedsbeskyttede mails dekrypteres og kan gennemses og eksporteres. Denne funktion kræver, at du er tildelt rollen RMS Dekrypter, som som standard er tildelt rollegruppen eDiscover Manager.

- Hvis du opretter en forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, sættes alle delvist indekserede elementer i venteposition. Dette omfatter delvist indekserede elementer, der ikke opfylder søgeforespørgslens kriterier for venteposition. Du kan finde flere oplysninger om oprettelse af forespørgselsbaserede eDiscovery-ventepositioner [i Opret en eDiscovery-venteposition](create-ediscovery-holds.md).

## <a name="see-also"></a>Se også

[Undersøgelse af delvist indekserede elementer i eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)
