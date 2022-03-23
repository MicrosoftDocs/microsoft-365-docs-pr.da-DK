---
title: Eksportere en rapport for indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: I stedet for at eksportere de faktiske resultater af en indholdssøgning Microsoft 365 Overholdelsescenter, kan du eksportere en rapport med søgeresultater. Rapporten indeholder en oversigt over søgeresultaterne og et dokument med detaljerede oplysninger om hvert element, der skal eksporteres.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d06cc712e8c81304bbd11a9c93f35e48d279a36e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63587902"
---
# <a name="export-a-content-search-report"></a>Eksportere en rapport for indholdssøgning

I stedet for at eksportere hele sættet af søgeresultater fra en indholdssøgning i Microsoft 365 Overholdelsescenter (eller fra en søgning, der er knyttet til en Core eDiscovery-sag), kan du eksportere de samme rapporter, der genereres, når du eksporterer de faktiske søgeresultater.
  
Når du eksporterer en rapport, downloades rapportfilerne til en mappe på din lokale computer, som har samme navn som Indholdssøgning, men som er føjet til *_ReportsOnly*. Hvis f.eks. Indholdssøgning hedder  *ContosoCase0815*, hentes rapporten til en mappe med *navnet ContosoCase0815_ReportsOnly*. Hvis du vil se en liste over dokumenter, der er inkluderet i rapporten, skal [du se Hvad er inkluderet i rapporten](#whats-included-in-the-report).

## <a name="before-you-export-a-search-report"></a>Før du eksporterer en søgerapport

- Hvis du vil eksportere en søgerapport, skal du have tildelt administrationsrollen til overholdelsessøgning i Microsoft 365 Overholdelsescenter. Denne rolle tildeles som standard til de indbyggede rollegrupper eDiscovery Manager og Organisationsadministration. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Når du eksporterer en rapport, gemmes dataene midlertidigt på en placering Azure Storage Microsoft-skyen, før de downloades til din lokale computer. Sørg for, at organisationen kan oprette forbindelse til slutpunktet i Azure, **\*som er .blob.core.windows.net** (jokertegnet repræsenterer et entydig identifier for eksporten). Dataene om søgeresultaterne slettes fra placeringen Azure Storage, to uger efter de er blevet oprettet.

- Den computer, du bruger til at eksportere søgerapporten, skal opfylde følgende systemkrav:
  
  - Nyeste version af Windows (32-bit eller 64-bit)
  
  - Microsoft .NET Framework 4.7 eller nyere
  
- Du skal bruge Microsoft Edge <sup>1 til</sup> at køre eDiscovery-eksportværktøjet. Brug af Internet Explorer 11 til at eksportere søgeresultater understøttes ikke <sup>længere2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Som følge af de seneste ændringer af Microsoft Edge er ClickOnce support ikke længere aktiveret som standard. Du kan finde en vejledning til ClickOnce support i Edge under Brug [eDiscovery-eksportværktøjet i Microsoft Edge](configure-edge-to-export-search-results.md). Desuden fremstiller Microsoft ikke udvidelser eller tilføjelsesprogrammer fra tredjeparter til ClickOnce programmer. Eksport af søgeresultater ved hjælp af en ikke-understøttet browser med tredjepartsudvidelser eller tilføjelser understøttes ikke.
  > 
  > <sup>2</sup> Fra august 2021 understøtter Microsoft 365-apps og -tjenester ikke længere Internet Explorer 11 (IE11), og brugerne kan opleve en forringet oplevelse eller ikke kan oprette forbindelse til disse apps og tjenester. Disse apps og tjenester udfases i løbet af de kommende uger og måneder for at sikre en problemfri ophør af supporten. Hver app og tjeneste bliver udfaset efter uafhængige tidsplaner. Du kan finde flere oplysninger i dette [blogindlæg](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Hvis den anslåede samlede størrelse af de resultater, der returneres af en søgning, overstiger 2 TB, mislykkes eksport af rapporterne. Hvis du vil eksportere rapporterne uden problemer, skal du prøve at begrænse omfanget og køre søgningen igen, så den anslåede størrelse af resultaterne er mindre end 2 TB.

- Hvis resultaterne af en søgning er ældre end 7 dage, og du sender et eksportrapportjob, vises der en fejlmeddelelse, som beder dig om at køre søgningen igen for at opdatere søgeresultaterne. Hvis dette sker, skal du annullere eksporten, køre søgningen igen og derefter starte eksporten igen.

- Eksport af søgerapporter tæller med i det maksimale antal eksporter, der kører på samme tid, og det maksimale antal eksporter, som en enkelt bruger kan køre. Du kan finde flere oplysninger om eksportgrænser under [Eksportér resultater fra indholdssøgning](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>Trin 1: Generere rapporten til eksport

Det første trin er at forberede rapporten til overførsel til eksport til din computer. Når du eksporterer rapporten, uploades rapportdokumenterne til et Azure Storage i Microsoft-skyen.
  
1. I Microsoft 365 Overholdelsescenter skal du vælge den indholdssøgning, du vil eksportere rapporten fra.
  
2. Klik **på Eksportér** rapport i menuen Handlinger nederst på siden med pop op-vinduet **med søgninger**.

   ![Indstillingen Eksportér rapport i menuen Handlinger.](../media/ActionMenuExportReport.png)

   Pop **op-siden** Eksportér rapport vises. De eksportrapportindstillinger, der er tilgængelige til at eksportere oplysninger om søgningen, afhænger af, om søgeresultaterne er placeret i postkasser eller websteder eller en kombination af begge dele.
  
3. Vælg **en af** følgende indstillinger under Outputindstillinger:
  
   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

    - **Alle elementer, undtagen dem, der har ukendt format, krypteres eller blev ikke indekseret af andre årsager**. Denne indstilling eksporterer kun oplysninger om indekserede elementer.
  
    - **Alle elementer, herunder elementer, der har ukendt format, er krypteret eller ikke blev indekseret af andre årsager**. Denne indstilling eksporterer oplysninger om indekserede og indekserede elementer.
  
    - **Det er kun elementer, der har et ukendt format, der krypteres eller ikke er indekseret af andre årsager**. Denne indstilling eksporterer kun oplysninger om ikke-xede elementer.

4. Konfigurer indstillingen **Aktivér duplikering for Exchange indhold**.
  
   - Hvis du vælger denne indstilling, medtages antallet af dublerede meddelelser (før duplikering og efter duplikering) i eksportoversigtsrapporten. Desuden medtages der kun én kopi af meddelelsen i den manifest.xml fil. Men rapporten med eksportresultater indeholder en række for hver kopi af en dubletmeddelelse, så du kan identificere de postkasser, der indeholder en kopi af den duplikerede meddelelse. Du kan finde flere oplysninger om de eksporterede [rapporter under Hvad indeholder rapporten](#whats-included-in-the-report).

   - Hvis du ikke vælger denne indstilling, indeholder eksportrapporterne oplysninger om alle meddelelser, der returneres af søgningen, herunder dubletter.

     Du kan finde flere oplysninger om afplikering, og hvordan duplikerede elementer identificeres, under [Afplikning i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

5. Klik **på Generér rapport**.

   Søgerapporterne er klar til at blive downloadet, hvilket betyder, at rapportdokumenterne uploades til Azure Storage placering i Microsoft-skyen. Dette kan tage flere minutter.

Se næste afsnit for at få vejledning i at downloade de eksporterede søgerapporter.
  
## <a name="step-2-download-the-report"></a>Trin 2: Download rapporten

Næste trin er at hente rapporten fra området Azure Storage til din lokale computer.

> [!NOTE]
> Den eksporterede søgerapport skal downloades inden for 14 dage, efter at du oprettede rapporten i trin 1.

1. På siden **Indholdssøgning** i Microsoft 365 Overholdelsescenter du vælge **fanen Eksporter**
  
   Du skal muligvis klikke på Opdater **for** at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportér rapportjob har samme navn som den tilsvarende søgning **_ReportsOnly** er føjet til navnet på søgningen.
  
2. Vælg det eksportjob, du oprettede i trin 1.

3. Klik på **Kopiér til** Udklipsholder på **pop op-siden** **Eksportér rapport under Eksportér**. Du kan bruge denne nøgle i trin 6 til at downloade søgeresultaterne.
  
   > [!IMPORTANT]
   > Da alle kan installere og starte værktøjet eDiscovery-eksport og derefter bruge denne nøgle til at downloade søgerapporten, skal du sørge for at træffe forholdsregler for at beskytte denne nøgle på samme måde, som du beskytter adgangskoder eller andre sikkerhedsrelaterede oplysninger.

4. Klik på Hent resultater øverst på pop **op-siden**.

5. Hvis du bliver bedt om at installere **eDiscovery-eksportværktøjet, skal** du klikke på **Installér**.

6. I **eDiscovery-eksportværktøjet** skal du gøre følgende:

   ![eDiscovery-eksportværktøj.](../media/eDiscoveryExportTool.png)

   1. Indsæt den eksportnøgle, du kopierede i trin 3, i det relevante felt.
  
   2. Klik **på** Gennemse for at angive den placering, hvor du vil hente søgerapportfilerne.

7. Klik **på Start** for at hente søgeresultaterne til din computer.
  
    Værktøjet **til eDiscovery-eksport** viser statusoplysninger om eksportprocessen, herunder et skøn over antallet (og størrelsen) af de resterende elementer, der skal downloades. Når eksporten er fuldført, kan du få adgang til filerne på den placering, hvor de blev downloadet.
  
## <a name="whats-included-in-the-report"></a>Hvad er inkluderet i rapporten

Når du opretter og eksporterer en rapport om resultaterne af en indholdssøgning, hentes følgende dokumenter:
  
- **Eksportoversigt:** Et Excel dokument, der indeholder en oversigt over eksporten. Dette omfatter oplysninger som f.eks. antallet af indholdskilder, der blev søgt på, antallet af søgeresultater fra hver indholdsplacering, det anslåede antal elementer, det faktiske antal elementer, der skal eksporteres, og den anslåede og faktiske størrelse af elementer, der skal eksporteres.

   Hvis du medtager ikke-identificerede elementer, når du eksporterer rapporten, medtages antallet af ikke-xede elementer i det samlede antal anslåede søgeresultater og i det samlede antal downloadede søgeresultater (hvis du eksporterer søgeresultaterne), som er angivet i eksportoversigtsrapporten. Med andre ord er det samlede antal elementer, der skal downloades, lig med det samlede antal anslåede resultater og det samlede antal elementer uden side om side.
  
- **Manifest:** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der medtages i søgeresultaterne. Hvis du har aktiveret indstillingen duplikering, medtages dublerede meddelelser ikke i manifestfilen.

- **Resultater:** Et Excel dokument, der indeholder en række med oplysninger om hvert indekseret element, der skal eksporteres med søgeresultaterne. For mails indeholder resultatloggen oplysninger om hver meddelelse, herunder: 

  - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).

  - Den dato, hvor meddelelsen blev sendt eller modtaget.

  - Emnelinjen i meddelelsen.

  - Afsenderen og modtagerne af meddelelsen.

  For dokumenter fra SharePoint og OneDrive for Business indeholder resultatloggen oplysninger om hvert dokument, herunder:

  - Dokumentets URL-adresse.

  - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.

  - Den dato, hvor dokumentet sidst blev ændret.

  - Navnet på dokumentet (som er placeret i kolonnen Emne i resultatloggen).

  > [!NOTE]
  > Antallet af rækker i resultatrapporten  skal være lig med det samlede antal søgeresultater minus det samlede antal elementer, der er angivet i rapporten **Unindexed Items**.
  
- **Trace.log:** En sporingslog, der indeholder detaljerede logføringsoplysninger om eksportprocessen og kan hjælpe med at afdække problemer under eksporten. Hvis du åbner en billet hos Microsoft Support om et problem i forbindelse med eksport af søgerapporter, kan du blive bedt om at angive denne sporingslog.

- **Uindsiddedede elementer:** Et Excel dokument, der indeholder oplysninger om eventuelle enkeltblinde elementer, der er inkluderet i søgeresultaterne. Hvis du ikke medtager ikke-indkluderede elementer, når du genererer rapporten med søgeresultater, hentes denne rapport stadig, men den vil være tom.
