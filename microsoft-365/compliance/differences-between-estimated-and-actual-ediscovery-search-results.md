---
title: Forskelle mellem anslåede og faktiske eDiscovery-søgeresultater
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Forstå, hvorfor anslåede og faktiske søgeresultater kan variere i søgninger, der køres med eDiscovery-værktøjer Office 365.
ms.openlocfilehash: e9dd47f8f2485fe31044cf52ae8e04e65eeaac60
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63587480"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Forskelle mellem anslåede og faktiske eDiscovery-søgeresultater

Dette emne gælder for søgninger, som du kan køre ved hjælp af en af følgende Microsoft 365 eDiscovery-værktøjer: 

- Indholdssøgning
- Core eDiscovery

Når du kører en eDiscovery-søgning, returnerer det værktøj, du bruger, et skøn over antallet af elementer (og deres samlede størrelse), der svarer til søgekriterierne. Når du f.eks. kører en søgning i Microsoft 365 Overholdelsescenter, vises de anslåede søgeresultater på pop op-siden for den valgte søgning.
  
![Esstim af resultater, der vises på siden med pop op-sider til søgning.](../media/EstimatedSearchResults1.png)
  
Dette er det samme skøn over den samlede størrelse og antallet af elementer, der vises i eDiscovery-eksportværktøjet, når du eksporterer resultater til en lokal computer, og i rapporten Eksportoversigt, der er downloadet sammen med søgeresultaterne.
  
**Anslåede resultater i værktøjet eDiscovery-eksport**

![Anslåede resultater i værktøjet eDiscovery-eksport.](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Anslåede resultater i rapporten Eksportoversigt**

![Anslåede søgeresultater medtages i rapporten Eksportoversigt.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Men som du vil bemærke på det forrige skærmbillede af rapporten Eksportoversigt, er størrelsen og antallet af faktiske søgeresultater, der downloades, anderledes end størrelsen og antallet af anslåede søgeresultater.
  
![Forskellen mellem estimerede og downloadede søgeresultater.](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Her er nogle årsager til disse forskelle:
  
- **Den måde, resultater estimeres på**. Et estimat af søgeresultaterne er blot det, et estimat (og ikke et faktisk antal) af de elementer, der opfylder søgeforespørgslens kriterier. For at samle estimatet på Exchange-elementer, anmodes der om en liste over de meddelelses-cd'er, der opfylder søgekriterierne, fra Exchange-databasen af det eDiscovery-værktøj, du bruger. Men når du eksporterer søgeresultaterne, køres søgningen igen, og de faktiske meddelelser hentes fra Exchange database. Disse forskelle kan derfor skyldes, hvordan det anslåede antal elementer og det faktiske antal elementer bestemmes.

- **Ændringer, der sker mellem tidspunktet, hvor estimering og eksport af søgeresultater**. Når du eksporterer søgeresultater, genstartes søgningen for at indsamle de seneste elementer i søgeindekset, der opfylder søgekriterierne. Det er muligt, at der er yderligere elementer, der er oprettet, sendt eller modtaget, som opfylder søgekriterierne i tiden mellem tidspunktet, hvor de anslåede søgeresultater blev indsamlet, og hvornår søgeresultaterne blev eksporteret. Det er også muligt, at elementer, der var i søgeindekset, da søgeresultaterne blev anslået, ikke længere er der, fordi de blev slettet fra indholdsplaceringen, før søgeresultaterne eksporteres. En måde at afhjælpe dette problem på er at angive et datointerval for en eDiscovery-søgning. En anden måde er at placere en venteposition på indholdsplaceringer, så elementer bevares og ikke kan slettes. 

   Selvom det er sjældent, selv når der anvendes venteposition, kan vedligeholdelse af indbyggede kalenderelementer (som ikke kan redigeres af brugeren, men medtages i mange søgeresultater) blive fjernet fra tid til anden. Denne periodiske fjernelse af kalenderelementer resulterer i færre eksporterede elementer.

- **Uindsiddedede elementer**. Elementer, der ikke er identificeret til søgning, kan medføre forskelle mellem anslåede og faktiske søgeresultater. Du kan medtage ikke-indkluderede elementer, når du eksporterer søgeresultaterne. Hvis du medtager ikke-indkluderede elementer, når du eksporterer søgeresultater, kan der være flere eksporterede elementer. Dette vil medføre en forskel mellem de estimerede og eksporterede søgeresultater.

    Når du bruger værktøjet Indholdssøgning, har du mulighed for at medtage elementer, der ikke er identificerede, når du eksporterer søgeresultater. Antallet af ikke-xede elementer, der returneres af søgningen, er angivet på pop op-siden sammen med de andre anslåede søgeresultater. Eventuelle elementer, der ikke er identificeret, medtages også i den samlede størrelse af de anslåede søgeresultater. Når du eksporterer søgeresultater, har du mulighed for at medtage eller ikke-indkluderede elementer. Konfigurationen af disse indstillinger kan medføre forskelle mellem anslåede og faktiske søgeresultater, der downloades.

- **Eksport af resultaterne af en indholdssøgning, der omfatter alle indholdsplaceringer**. Hvis den søgning, du eksporterer resultater fra, var en søgning på alle indholdsplaceringer i organisationen, eksporteres kun de uindsiderede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Med andre ord, hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, så eksporteres elementer, der ikke er inddæmt i den pågældende postkasse eller websted, ikke. Elementer, der ikke er identificeret, fra alle placeringer med indhold (selv dem, der ikke indeholder elementer, der svarer til søgeforespørgslen) medtages dog i de anslåede søgeresultater.

    Alternativt kan du, hvis den søgning, du eksporterer resultater fra inkluderede bestemte indholdsplaceringer, eksporteres ikke-markerede elementer (der ikke er udeladt af søgekriterierne) fra alle de indholdsplaceringer, der er angivet i søgningen. I dette tilfælde skal det anslåede antal ikke-xede elementer og antallet af eksporterede elementer, der ikke erxed, være det samme.

    Årsagen til, at ikke-eksporterede elementer fra alle placeringer i organisationen er, at det kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og hente søgeresultaterne.

- **Unindexed elementer i SharePoint og OneDrive ikke medtaget i de anslåede søgninger**. Unindexed items from SharePoint sites and OneDrive for Business accounts aren't included in the estimated search results. Dette skyldes, SharePoint indeks ikke indeholder data for indekserede elementer. Det er kun elementer fra postkasser, der ikke er identificeret, der medtages i de anslåede søgninger. Men hvis du medtager ikke-indkluderede elementer, når du eksporterer søgeresultater, medtages uindsiderede elementer i SharePoint og OneDrive, hvilket øger antallet af elementer, der faktisk eksporteres. Dette medfører forskelle mellem de anslåede resultater (som ikke omfatter ikke-indkluderede elementer i SharePoint- OneDrive websteder) og de faktiske elementer, der downloades. Reglen om kun at eksportere ikke-identificerede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne, gælder stadig i denne situation.

- **Dokumentversioner i SharePoint og OneDrive**. Når du SharePoint på websteder OneDrive konti, medtages flere versioner af et dokument ikke i antallet af anslåede søgeresultater. Men du har mulighed for at medtage alle dokumentversioner, når du eksporterer søgeresultaterne. Hvis du medtager dokumentversioner, når du eksporterer søgeresultater, øges det faktiske antal (og den samlede størrelse) af de eksporterede elementer.

- **SharePoint mapper**. Hvis navnet på mapper i SharePoint svarer til en søgeforespørgsel, indeholder søgeestimaet en optælling af disse mapper (men ikke elementerne i disse mapper). Når du eksporterer søgeresultaterne, eksporteres elementerne i mappen, men den faktiske mappe eksporteres ikke. Resultatet er, at antallet af eksporterede elementer vil være mere end antallet af anslåede søgeresultater. Hvis en mappe er tom, reduceres antallet af faktiske eksporterede søgeresultater med ét element, fordi den faktiske mappe ikke eksporteres.

   > [!NOTE]
   > Når du kører en forespørgselsbaseret søgning, kan du SharePoint mapper ved at føje følgende betingelse til forespørgslen: `NOT(ContentType:folder)`.

- **SharePoint lister**. Hvis navnet på en liste SharePoint en søgeforespørgsel, vil søgeesestimen indeholde en optælling af alle elementerne på listen. Når du eksporterer søgeresultaterne, eksporteres listen (og listeelementerne) som en enkelt CSV-fil. Dette vil reducere det faktiske antal elementer, der faktisk er eksporteret. Hvis listen indeholder vedhæftede filer, eksporteres de vedhæftede filer som separate dokumenter, hvilket også øger antallet af eksporterede elementer.

- **Rå filformater kontra eksporterede filformater**. For Exchange elementer beregnes den anslåede størrelse af søgeresultaterne ved hjælp af den rå Exchange i meddelelsesstørrelser. Mails eksporteres dog i en PST-fil eller som individuelle meddelelser (der er formateret som EML-filer). Begge disse eksportindstillinger bruger et andet filformat end rå Exchange meddelelser, hvilket medfører, at den samlede eksporterede filstørrelse er forskellig fra den anslåede filstørrelse.

- **Afplikering af Exchange elementer under eksporten**. For Exchange af dublerede elementer reducerer duplikering antallet af eksporterede elementer. Du har mulighed for at fjerne duplikerede søgeresultaterne, når du eksporterer dem. For Exchange meddelelser betyder det, at der kun eksporteres en enkelt forekomst af en meddelelse, selvom den pågældende meddelelse kan findes i flere postkasser. De estimerede søgeresultater omfatter alle forekomster af en meddelelse. Så hvis du vælger indstillingen af duplikering, når du eksporterer søgeresultater, kan det faktiske antal elementer, der eksporteres, være væsentligt mindre end det anslåede antal elementer.

Rapporten over søgeresultater (Results.csv fil) indeholder en post for hver dubletmeddelelse og identificerer den kildepostkasse, hvor en dubletmeddelelse er placeret. Dette hjælper dig med at identificere alle postkasser, der indeholder en dubletmeddelelse.

> [!NOTE]
> Hvis du ikke vælger indstillingen Inkluder elementer, der er krypteret eller har en ukendt **format** , når du eksporterer søgeresultater eller blot downloader rapporterne, downloades indeksfejlrapporterne, men de har ingen poster. Dette betyder ikke, at der ikke er nogen indeksfejl. Det betyder blot, at enkeltinddeede elementer ikke blev medtaget i eksporten.
