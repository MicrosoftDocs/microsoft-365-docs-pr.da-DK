---
title: Eksportér en indholdssøgningsrapport
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
description: I stedet for at eksportere de faktiske resultater af en indholdssøgning på Microsoft Purview-overholdelsesportalen kan du eksportere en rapport med søgeresultater. Rapporten indeholder en oversigt over søgeresultaterne og et dokument med detaljerede oplysninger om hvert element, der skal eksporteres.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6ac46944ab454271358168c95a7df94d606e0ec5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944827"
---
# <a name="export-a-content-search-report"></a>Eksportér en indholdssøgningsrapport

I stedet for at eksportere det fulde sæt søgeresultater fra en indholdssøgning på Microsoft Purview-overholdelsesportalen (eller fra en søgning, der er knyttet til en Microsoft Purview eDiscovery(Standard)-sag), kan du eksportere de samme rapporter, der genereres, når du eksporterer de faktiske søgeresultater.
  
Når du eksporterer en rapport, downloades rapportfilerne til en mappe på din lokale computer, der har samme navn som indholdssøgningen, men som tilføjes med *_ReportsOnly*. Hvis indholdssøgningen f.eks. hedder  *ContosoCase0815*, downloades rapporten til en mappe med navnet *ContosoCase0815_ReportsOnly*. Du kan se en liste over dokumenter, der er inkluderet i rapporten, under [Hvad er inkluderet i rapporten](#whats-included-in-the-report).

## <a name="before-you-export-a-search-report"></a>Før du eksporterer en søgerapport

- Hvis du vil eksportere en søgerapport, skal du have tildelt rollen Styring af overholdelsessøgning på overholdelsesportalen. Denne rolle er som standard tildelt de indbyggede rollegrupper eDiscovery Manager og Organization Management. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Når du eksporterer en rapport, gemmes dataene midlertidigt på en Azure Storage placering i Microsofts cloud, før de downloades til din lokale computer. Sørg for, at din organisation kan oprette forbindelse til slutpunktet i Azure, som er **\*.blob.core.windows.net** (jokertegnet repræsenterer et entydigt id for din eksport). Søgeresultaterne slettes fra Azure Storage placering to uger efter, at de er oprettet.

- Den computer, du bruger til at eksportere søgerapporten, skal opfylde følgende systemkrav:
  
  - Seneste version af Windows (32-bit eller 64-bit)
  
  - Microsoft .NET Framework 4.7 eller nyere
  
- Du skal bruge Microsoft Edge <sup>1</sup> til at køre eDiscovery-eksportværktøjet. Brug af Internet Explorer 11 til at eksportere søgeresultater understøttes ikke <sup>længere2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Som følge af de seneste ændringer af Microsoft Edge er understøttelse af ClickOnce ikke længere aktiveret som standard. Du kan finde oplysninger om, hvordan du aktiverer understøttelse af ClickOnce i Edge, under [Brug eDiscovery-eksportværktøjet i Microsoft Edge](configure-edge-to-export-search-results.md). Desuden producerer Microsoft ikke udvidelser eller tilføjelsesprogrammer fra tredjepart til ClickOnce programmer. Eksport af søgeresultater ved hjælp af en browser, der ikke understøttes, med udvidelser eller tilføjelsesprogrammer fra tredjepart understøttes ikke.
  > 
  > <sup>2</sup> Fra august 2021 understøtter Microsoft 365 apps og tjenester ikke længere Internet Explorer 11 (IE11), og brugerne kan have en forringet oplevelse eller ikke kunne oprette forbindelse til disse apps og tjenester. Disse apps og tjenester udfases i løbet af de kommende uger og måneder for at sikre en problemfri ophør af support. Hver app og tjeneste udfases efter uafhængige tidsplaner. Du kan få flere oplysninger i dette [blogindlæg](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Hvis den anslåede samlede størrelse af de resultater, der returneres af søgningen, overstiger 2 TB, mislykkes eksporten af rapporterne. Hvis du vil eksportere rapporterne, skal du forsøge at indsnævre omfanget og køre søgningen igen, så den anslåede størrelse af resultaterne er mindre end 2 TB.

- Hvis resultaterne af en søgning er ældre end 7 dage, og du sender et eksportrapportjob, vises der en fejlmeddelelse, hvor du bliver bedt om at køre søgningen igen for at opdatere søgeresultaterne. Hvis det sker, skal du annullere eksporten, køre søgningen igen og derefter starte eksporten igen.

- Eksport af søgerapporter tæller i forhold til det maksimale antal eksporter, der kører på samme tid, og det maksimale antal eksporter, som en enkelt bruger kan køre. Du kan finde flere oplysninger om eksportgrænser under [Eksportér søgeresultater for indhold](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>Trin 1: Generér rapporten til eksport

Det første trin er at forberede rapporten til download til din computereksport. Når du eksporterer rapporten, uploades rapportdokumenterne til et Azure Storage område i Microsoft-cloudmiljøet.
  
1. Vælg den indholdssøgning, du vil eksportere rapporten fra, på overholdelsesportalen.
  
2. Klik på **Eksportér rapport** i menuen **Handlinger** nederst på siden med søgevinduet.

   ![Indstillingen Eksportér rapport i menuen Handlinger.](../media/ActionMenuExportReport.png)

   Pop op-siden **Eksportér rapport** vises. De eksportrapportindstillinger, der er tilgængelige til eksport af oplysninger om søgningen, afhænger af, om søgeresultaterne er placeret i postkasser eller på websteder eller en kombination af begge.
  
3. Vælg en af følgende indstillinger under **Outputindstillinger**:
  
   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

    - **Alle elementer, bortset fra elementer, der har et ukendt format, krypteres eller er ikke indekseret af andre årsager**. Denne indstilling eksporterer kun oplysninger om indekserede elementer.
  
    - **Alle elementer, herunder elementer, der har et ukendt format, krypteres eller er ikke indekseret af andre årsager**. Denne indstilling eksporterer oplysninger om indekserede og ikke-indekserede elementer.
  
    - **Kun elementer, der har et ukendt format, krypteres eller ikke er indekseret af andre årsager**. Denne indstilling eksporterer kun oplysninger om ikke-indekserede elementer.

4. Konfigurer indstillingen **Aktivér deduplikering for Exchange indhold**.
  
   - Hvis du vælger denne indstilling, medtages antallet af dublerede meddelelser (før deduplikering og efter deduplikering) i rapporten med eksportoversigten. Desuden medtages kun én kopi af en meddelelse i filen manifest.xml. Men rapporten med eksportresultater indeholder en række for hver kopi af en dubletmeddelelse, så du kan identificere de postkasser, der indeholder en kopi af den dublerede meddelelse. Du kan få flere oplysninger om de eksporterede rapporter under [Hvad er inkluderet i rapporten](#whats-included-in-the-report).

   - Hvis du ikke vælger denne indstilling, indeholder eksportrapporterne oplysninger om alle meddelelser, der returneres af søgningen, herunder dubletter.

     Du kan finde flere oplysninger om deduplikering, og hvordan dubletter identificeres, [under De-duplikering i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

5. Klik på **Generér rapport**.

   Søgerapporterne er forberedt til download, hvilket betyder, at rapportdokumenterne uploades til en Azure Storage placering i Microsoft-cloudmiljøet. Dette kan tage flere minutter.

Se næste afsnit for at få oplysninger om, hvordan du downloader de eksporterede søgerapporter.
  
## <a name="step-2-download-the-report"></a>Trin 2: Download rapporten

Det næste trin er at downloade rapporten fra området Azure Storage til din lokale computer.

> [!NOTE]
> Den eksporterede søgerapport skal downloades inden for 14 dage, efter at du oprettede rapporten i trin 1.

1. På siden **Indholdssøgning** i overholdelsesportalen skal du vælge fanen **Eksporter**
  
   Du skal muligvis klikke på **Opdater** for at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportér rapportjob har samme navn som den tilsvarende søgning med **_ReportsOnly** føjet til søgenavnet.
  
2. Vælg det eksportjob, du oprettede i trin 1.

3. Klik på **Kopiér til Udklipsholder** på siden **Eksportér rapport** under **Eksportnøgle**. Du kan bruge denne nøgle i trin 6 til at downloade søgeresultaterne.
  
   > [!IMPORTANT]
   > Da alle kan installere og starte eDiscovery-eksportværktøjet og derefter bruge denne nøgle til at downloade søgerapporten, skal du sørge for at beskytte denne nøgle på samme måde, som du ville beskytte adgangskoder eller andre sikkerhedsrelaterede oplysninger.

4. Klik på **Download resultater** øverst på pop op-siden.

5. Hvis du bliver bedt om at installere **eDiscovery-eksportværktøjet**, skal du klikke på **Installér**.

6. Gør følgende i **eDiscovery-eksportværktøjet**:

   ![eDiscovery-eksportværktøj.](../media/eDiscoveryExportTool.png)

   1. Indsæt den eksportnøgle, du kopierede, i trin 3 i det relevante felt.
  
   2. Klik på **Gennemse** for at angive den placering, hvor du vil downloade søgerapportfilerne.

7. Klik på **Start** for at hente søgeresultaterne til computeren.
  
    **EDiscovery-eksportværktøjet** viser statusoplysninger om eksportprocessen, herunder et estimat af antallet (og størrelsen) af de resterende elementer, der skal downloades. Når eksporten er fuldført, kan du få adgang til filerne på den placering, hvor de blev downloadet.
  
## <a name="whats-included-in-the-report"></a>Det, der er inkluderet i rapporten

Når du genererer og eksporterer en rapport om resultaterne af en indholdssøgning, downloades følgende dokumenter:
  
- **Eksportoversigt:** Et Excel dokument, der indeholder en oversigt over eksporten. Dette omfatter oplysninger som f.eks. antallet af indholdskilder, der blev søgt efter, antallet af søgeresultater fra hver indholdsplacering, det anslåede antal elementer, det faktiske antal elementer, der ville blive eksporteret, og den anslåede og faktiske størrelse af elementer, der ville blive eksporteret.

   Hvis du medtager ikke-indekserede elementer, når du eksporterer rapporten, medtages antallet af ikke-indekserede elementer i det samlede antal anslåede søgeresultater og i det samlede antal downloadede søgeresultater (hvis du eksporterer søgeresultaterne), som er angivet i rapporten med eksportoversigten. Det samlede antal elementer, der downloades, er med andre ord lig med det samlede antal anslåede resultater og det samlede antal ikke-indekserede elementer.
  
- **Manifestere:** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der er inkluderet i søgeresultaterne. Hvis du har aktiveret indstillingen deduplikering, medtages dublerede meddelelser ikke i manifestfilen.

- **Resultater:** Et Excel dokument, der indeholder en række med oplysninger om hvert indekseret element, der eksporteres med søgeresultaterne. I forbindelse med mail indeholder resultatloggen oplysninger om hver meddelelse, herunder: 

  - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).

  - Den dato, hvor meddelelsen blev sendt eller modtaget.

  - Emnelinjen fra meddelelsen.

  - Afsenderen og modtagerne af meddelelsen.

  For dokumenter fra SharePoint og OneDrive for Business websteder indeholder resultatloggen oplysninger om hvert dokument, herunder:

  - DOKUMENTETs URL-adresse.

  - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.

  - Den dato, hvor dokumentet senest blev ændret.

  - Navnet på dokumentet (som findes i kolonnen Emne i resultatloggen).

  > [!NOTE]
  > Antallet af rækker **i resultatrapporten** skal være lig med det samlede antal søgeresultater minus det samlede antal elementer, der er angivet i rapporten **Unindexed Items** .
  
- **Trace.log:** En sporingslog, der indeholder detaljerede logføringsoplysninger om eksportprocessen, og som kan hjælpe med at afdække problemer under eksporten. Hvis du åbner en anmodning med Microsoft Support om et problem, der er relateret til eksport af søgerapporter, kan du blive bedt om at angive denne sporingslogfil.

- **Ikke-indekserede elementer:** Et Excel dokument, der indeholder oplysninger om alle ikke-indekserede elementer, der er inkluderet i søgeresultaterne. Hvis du ikke medtager ikke-indekserede elementer, når du genererer rapporten med søgeresultater, downloades denne rapport stadig, men den er tom.
