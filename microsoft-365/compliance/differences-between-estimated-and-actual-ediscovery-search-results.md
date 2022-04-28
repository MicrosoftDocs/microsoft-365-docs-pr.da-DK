---
title: Anslåede og faktiske eDiscovery-søgeresultater
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Forstå, hvorfor anslåede og faktiske søgeresultater kan variere i søgninger, der køres med eDiscovery-værktøjer i Office 365.
ms.openlocfilehash: 694d850d568aee4965530317f9bbc9f95727338c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092773"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Forskelle mellem anslåede og faktiske eDiscovery-søgeresultater

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denne artikel gælder for søgninger, som du kan køre ved hjælp af et af følgende Microsoft 365 eDiscovery-værktøjer: 

- Indholdssøgning
- eDiscovery (Standard)

Når du kører en eDiscovery-søgning, returnerer det værktøj, du bruger, et estimat over antallet af elementer (og deres samlede størrelse), der svarer til søgekriterierne. Når du f.eks. kører en søgning på Microsoft Purview-overholdelsesportalen, vises de anslåede søgeresultater på pop op-siden for den valgte søgning.
  
![Estimat over resultater, der vises på søgevinduet.](../media/EstimatedSearchResults1.png)
  
Dette er det samme estimat af den samlede størrelse og antallet af elementer, der vises i eDiscovery-eksportværktøjet, når du eksporterer resultater til en lokal computer og i rapporten Eksportoversigt, der downloades sammen med søgeresultaterne.
  
**Anslåede resultater i eDiscovery-eksportværktøjet**

![Anslåede resultater i værktøjet eDiscovery-eksport.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Anslåede resultater i rapporten Eksportoversigt**

![Anslåede søgeresultater er inkluderet i rapporten Eksportoversigt.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Men som du vil bemærke på det forrige skærmbillede af rapporten Eksportoversigt, er størrelsen og antallet af faktiske søgeresultater, der downloades, forskellig fra størrelsen og antallet af anslåede søgeresultater.
  
![Forskel mellem estimerede og downloadede søgeresultater.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Her er nogle årsager til disse forskelle:
  
- **Den måde, resultaterne anslås på**. Et estimat af søgeresultaterne er netop det, et estimat (og ikke et faktisk antal) af de elementer, der opfylder søgeforespørgselskriterierne. Hvis du vil kompilere estimatet for Exchange elementer, anmodes der om en liste over de meddelelses-id'er, der opfylder søgekriterierne, fra den Exchange database af det eDiscovery-værktøj, du bruger. Men når du eksporterer søgeresultaterne, kører søgningen igen, og de faktiske meddelelser hentes fra den Exchange database. Disse forskelle kan derfor skyldes, hvordan det anslåede antal elementer og det faktiske antal elementer bestemmes.

- **Ændringer, der sker mellem tidspunktet for vurdering og eksport af søgeresultater**. Når du eksporterer søgeresultater, genstartes søgningen for at indsamle de nyeste elementer i søgeindekset, der opfylder søgekriterierne. Det er muligt, at der blev oprettet, sendt eller modtaget flere elementer, der opfylder søgekriterierne i tiden mellem det tidspunkt, hvor de anslåede søgeresultater blev indsamlet, og hvornår søgeresultaterne blev eksporteret. Det er også muligt, at elementer, der var i søgeindekset, da søgeresultaterne blev anslået, ikke længere findes, fordi de blev fjernet fra indholdsplaceringen, før søgeresultaterne eksporteres. En måde at afhjælpe dette problem på er ved at angive et datointerval for en eDiscovery-søgning. En anden måde er at placere en venteposition på indholdsplaceringer, så elementer bevares og ikke kan fjernes.

   Her er andre problemer, der kan medføre forskelle mellem anslåede og eksporterede søgeresultater:

  - Stigning i elementer, når du bruger en datoforespørgsel. Dette skyldes typisk følgende to ting:

  - Hold versioner i SharePoint. Hvis et dokument slettes fra et websted, der er i venteposition, og dokumentversionsstyring er aktiveret, bevares alle versioner af det slettede dokument.

  - Kalenderemner. Acceptér og afvis meddelelser og tilbagevendende møder fortsætter automatisk med at oprette nye elementer i baggrunden med gamle datoer.

  - Med ventepositioner kan der være tilfælde, hvor det samme element bevares i en brugers primære postkasse og i deres arkivpostkasse. Dette kan ske, når en bruger manuelt flytter et element til sit arkiv.

  - Selvom det er sjældent, selv når der anvendes venteposition, kan vedligeholdelsen af indbyggede kalenderelementer (som ikke kan redigeres af brugeren, men er inkluderet i mange søgeresultater) blive fjernet fra tid til anden. Denne periodiske fjernelse af kalenderelementer medfører, at der eksporteres færre elementer.

- **Ikke-indekserede elementer**. Elementer, der ikke er indekseret til søgning, kan medføre forskelle mellem anslåede og faktiske søgeresultater. Du kan inkludere ikke-indekserede elementer, når du eksporterer søgeresultaterne. Hvis du medtager ikke-indekserede elementer, når du eksporterer søgeresultater, kan der være flere elementer, der eksporteres. Dette vil medføre en forskel mellem de anslåede og eksporterede søgeresultater.

    Når du bruger indholdssøgeværktøjet, har du mulighed for at inkludere ikke-indekserede elementer, når du eksporterer søgeresultater. Antallet af ikke-indekserede elementer, der returneres af søgningen, vises på pop op-siden sammen med de andre anslåede søgeresultater. Alle ikke-indekserede elementer medtages også i den samlede størrelse af de anslåede søgeresultater. Når du eksporterer søgeresultater, har du mulighed for at inkludere ikke-indekserede elementer. Den måde, du konfigurerer disse indstillinger på, kan resultere i forskelle mellem estimerede og faktiske søgeresultater, der downloades.

- **Eksport af resultaterne af en indholdssøgning, der indeholder alle indholdsplaceringer**. Hvis den søgning, du eksporterer resultater fra, var en søgning efter alle indholdsplaceringer i din organisation, eksporteres kun de ikke-indekserede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Det vil sige, at hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, eksporteres alle ikke-indekserede elementer i den pågældende postkasse eller det pågældende websted ikke. Ikke-indekserede elementer fra alle indholdsplaceringer (også dem, der ikke indeholder elementer, der svarer til søgeforespørgslen) medtages i de anslåede søgeresultater.

    Hvis den søgning, du eksporterer resultater fra, indeholder bestemte indholdsplaceringer, eksporteres ikke-indekserede elementer fra alle de indholdsplaceringer, der er angivet i søgningen, også, hvis søgningen ikke er udelukket af søgekriterierne. I dette tilfælde skal det anslåede antal ikke-indekserede elementer og antallet af ikke-indekserede elementer, der eksporteres, være det samme.

    Årsagen til ikke at eksportere ikke-indekserede elementer fra alle placeringer i organisationen er, at det kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og downloade søgeresultaterne.

- **Ikke-indekserede elementer i SharePoint og OneDrive ikke inkluderet i søgeestimaterne**. Ikke-indekserede elementer fra SharePoint websteder og OneDrive for Business konti medtages ikke i de anslåede søgeresultater. Det skyldes, at det SharePoint indeks ikke indeholder data for ikke-indekserede elementer. Det er kun ikke-indekserede elementer fra postkasser, der medtages i søgeestimaterne. Men hvis du medtager ikke-indekserede elementer, når du eksporterer søgeresultater, medtages ikke-indekserede elementer i SharePoint og OneDrive, hvilket øger antallet af elementer, der faktisk eksporteres. Dette resulterer i forskelle mellem de anslåede resultater (som ikke omfatter ikke-indekserede elementer på SharePoint og OneDrive websteder) og de faktiske elementer, der downloades. Reglen om eksport af ikke-indekserede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne, gælder stadig i denne situation.

- **Dokumentversioner i SharePoint og OneDrive**. Når du søger på SharePoint websteder og OneDrive konti, medtages der ikke flere versioner af et dokument i antallet af anslåede søgeresultater. Men du har mulighed for at inkludere alle dokumentversioner, når du eksporterer søgeresultaterne. Hvis du medtager dokumentversioner, når du eksporterer søgeresultater, øges det faktiske antal (og den samlede størrelse) af de eksporterede elementer.

- **SharePoint mapper**. Hvis mapper i SharePoint stemmer overens med en søgeforespørgsel, f.eks. søgning efter dato, indeholder søgeestimatet en optælling af disse mapper med det senest ændrede datointerval (men ikke elementerne i disse mapper). Når du eksporterer søgeresultaterne, eksporteres elementerne i mappen, men den faktiske mappe eksporteres ikke. Resultatet er, at antallet af eksporterede elementer vil være større end antallet af anslåede søgeresultater. Hvis en mappe er tom, reduceres antallet af eksporterede faktiske søgeresultater med ét element, fordi den faktiske mappe ikke eksporteres.

   > [!NOTE]
   > Når du kører en forespørgselsbaseret søgning, kan du udelade SharePoint mapper ved at føje følgende betingelse til forespørgslen: `NOT(ContentType:folder)`.

- **SharePoint lister**. Hvis navnet på en SharePoint liste svarer til en søgeforespørgsel, indeholder søgeestimatet et antal af alle elementerne på listen. Når du eksporterer søgeresultaterne, eksporteres listen (og listeelementerne) som en enkelt CSV-fil. Dette reducerer det faktiske antal elementer, der faktisk eksporteres. Hvis listen indeholder vedhæftede filer, eksporteres de vedhæftede filer som separate dokumenter, hvilket også øger antallet af eksporterede elementer.

   > [!NOTE]
   > Når du kører en forespørgselsbaseret søgning, kan du udelade SharePoint lister ved at føje følgende betingelse til forespørgslen: `NOT(ContentType:list)`.

- **Rå filformater i forhold til eksporterede filformater**. For Exchange elementer beregnes den anslåede størrelse af søgeresultaterne ved hjælp af de rå Exchange meddelelsesstørrelser. Mails eksporteres dog i en PST-fil eller som individuelle meddelelser (som er formateret som EML-filer). Begge disse eksportindstillinger bruger et andet filformat end rå Exchange meddelelser, hvilket medfører, at den samlede eksporterede filstørrelse er forskellig fra den anslåede filstørrelse.

- **Deduplikering af Exchange elementer under eksport**. For Exchange elementer reducerer deduplikering antallet af elementer, der eksporteres. Du har mulighed for at duplikere søgeresultaterne, når du eksporterer dem. For Exchange meddelelser betyder det, at der kun eksporteres en enkelt forekomst af en meddelelse, selvom meddelelsen kan findes i flere postkasser. De anslåede søgeresultater omfatter alle forekomster af en meddelelse. Så hvis du vælger indstillingen deduplikering, når du eksporterer søgeresultater, kan det faktiske antal elementer, der eksporteres, være betydeligt mindre end det anslåede antal elementer.

Rapporten med søgeresultater (Results.csv fil) indeholder en post for hver dubletmeddelelse og identificerer kildepostkassen, hvor der findes en dubletmeddelelse. Dette hjælper dig med at identificere alle postkasser, der indeholder en dubletmeddelelse.

> [!NOTE]
> Hvis du ikke vælger indstillingen **Medtag elementer, der er krypteret eller har et ukendt format** , når du eksporterer søgeresultater eller blot downloader rapporterne, downloades indeksfejlrapporterne, men de har ingen poster. Det betyder ikke, at der ikke er nogen indekseringsfejl. Det betyder bare, at ikke-indekserede elementer ikke blev inkluderet i eksporten.
