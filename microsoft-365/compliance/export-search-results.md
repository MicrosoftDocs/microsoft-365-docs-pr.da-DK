---
title: Eksportér resultater fra indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ed48d448-3714-4c42-85f5-10f75f6a4278
description: Eksportér søgeresultaterne fra en indholdssøgning i Microsoft 365 Overholdelsescenter til en lokal computer. Mailresultater eksporteres som PST-filer. Indhold fra SharePoint og OneDrive for Business eksporteres som oprindelige Office dokumenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 22f66333a5fa2c5b570b564276c626fa0b41f83d
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63589135"
---
# <a name="export-content-search-results"></a>Eksportér resultater fra indholdssøgning

Når en indholdssøgning er kørt, kan du eksportere søgeresultaterne til en lokal computer. Når du eksporterer mailresultater, hentes de til din computer som PST-filer. Når du eksporterer indhold SharePoint og OneDrive for Business websteder, eksporteres kopier Office oprindelige dokumenter. Der er andre dokumenter og rapporter inkluderet i de eksporterede søgeresultater.
  
Hvis du eksporterer resultaterne af en indholdssøgning, skal du forberede resultaterne og derefter hente dem til en lokal computer. Disse trin til at eksportere søgeresultater gælder også for eksport af resultaterne af en søgning, der er knyttet til centrale eDiscovery-sager.
  
## <a name="before-you-export-search-results"></a>Før du eksporterer søgeresultater

- Hvis du vil eksportere søgeresultater, skal du have tildelt administrationsrollen Eksport i Microsoft 365 Overholdelsescenter. Denne rolle tildeles den indbyggede rollegruppe eDiscovery Manager. Den tildeles ikke som standard til rollegruppen Organisationsadministration. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Den computer, du bruger til at eksportere søgeresultaterne, skal opfylde følgende systemkrav:
  
  - Nyeste version af Windows (32-bit eller 64-bit)
  
  - Microsoft .NET Framework 4.7 eller nyere
  
- Du skal bruge Microsoft Edge <sup>1 til</sup> at køre eDiscovery-eksportværktøjet. Brug af Internet Explorer 11 til at eksportere søgeresultater understøttes ikke <sup>længere2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Som følge af de seneste ændringer af Microsoft Edge er ClickOnce support ikke længere aktiveret som standard. Du kan finde en vejledning til ClickOnce support i Edge under Brug [eDiscovery-eksportværktøjet i Microsoft Edge](configure-edge-to-export-search-results.md). Desuden fremstiller Microsoft ikke udvidelser eller tilføjelsesprogrammer fra tredjeparter til ClickOnce programmer. Eksport af søgeresultater ved hjælp af en ikke-understøttet browser med tredjepartsudvidelser eller tilføjelser understøttes ikke.
  >
  > <sup>2</sup> Fra august 2021 understøtter Microsoft 365-apps og -tjenester ikke længere Internet Explorer 11 (IE11), og brugerne kan opleve en forringet oplevelse eller ikke kan oprette forbindelse til disse apps og tjenester. Disse apps og tjenester udfases i løbet af de kommende uger og måneder for at sikre en problemfri ophør af supporten. Hver app og tjeneste bliver udfaset efter uafhængige tidsplaner. Du kan finde flere oplysninger i dette [blogindlæg](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Det eDiscovery-eksportværktøj, som du bruger i trin 2 til at hente søgeresultater, understøtter ikke automatisering (ved hjælp af et script eller kørsel af cmdlet'er). Vi anbefaler kraftigt, at du ikke automatiserer forberedelsesprocessen i trin 1 eller downloadprocessen i trin 2. Hvis du automatiserer en af disse processer, yder Microsoft Support ikke hjælp, hvis du løber ind i problemer.

- Vi anbefaler, at du downloader søgeresultater til en lokal computer. For at eliminere virksomhedens firewall eller proxyinfrastruktur i at forårsage problemer, når du henter søgeresultater, kan du overveje at hente søgeresultater til en virtuel skrivebord uden for dit netværk. Dette kan reducere timeouts, der opstår i Azure-dataforbindelser, når et stort antal filer eksporteres. Du kan finde flere oplysninger om virtuelle skriveborde [i Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop).

- Hvis du vil forbedre ydeevnen, når du downloader søgeresultater, skal du overveje at inddele de søgninger, der returnerer et stort sæt resultater, i mindre søgninger. Du kan f.eks. bruge datointervaller i søgeforespørgsler til at returnere et mindre sæt resultater, der kan downloades hurtigere.
  
- Når du eksporterer søgeresultater, gemmes dataene midlertidigt på en Microsoft-leveret placering Azure Storage Microsoft-skyen, før de downloades til din lokale computer. Sørg for, at organisationen kan oprette forbindelse til slutpunktet i Azure, **\*som er .blob.core.windows.net** (jokertegnet repræsenterer et entydig identifier for eksporten). Dataene om søgeresultaterne slettes fra placeringen Azure Storage, to uger efter de er blevet oprettet. 
  
- Hvis din organisation bruger en proxyserver til at kommunikere med internettet, skal du definere indstillingerne for proxyserveren på den computer, du bruger til at eksportere søgeresultaterne (så eksportværktøjet kan godkendes af din proxyserver). Det gør du ved at *machine.config* filen på den placering, der svarer til din version Windows. 
  
  - **32-bit:** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64-bit:** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Føj følgende linjer til filen  *machine.config*  et sted mellem mærkerne  `<configuration>`  `</configuration>` . Sørg for at erstatte  `ProxyServer` og  `Port` med de korrekte værdier for organisationen, f.eks. `proxy01.contoso.com:80`. 
  
    ```xml
    <system.net>
       <defaultProxy enabled="true" useDefaultCredentials="true">
         <proxy proxyaddress="https://ProxyServer :Port " 
                usesystemdefault="False" 
                bypassonlocal="True" 
                autoDetect="False" />
       </defaultProxy>
    </system.net>
    ```

- Hvis resultaterne af en søgning er ældre end 7 dage, og du sender et eksportjob, vises der en fejlmeddelelse, som beder dig om at køre søgningen igen for at opdatere søgeresultaterne. Hvis dette sker, skal du annullere eksporten, køre søgningen igen og derefter starte eksporten igen.

## <a name="step-1-prepare-search-results-for-export"></a>Trin 1: Forbered søgeresultaterne til eksport

Det første trin er at forberede søgeresultaterne til eksport. Når du forbereder resultater, overføres de til en Microsoft-leveret placering Azure Storage i Microsoft-skyen. Indhold fra postkasser og websteder uploades til en maksimal hastighed på 2 GB pr. time.
  
1. I Microsoft 365 Overholdelsescenter skal du vælge den indholdssøgning, du vil eksportere resultater fra.
  
2. Klik på **Eksportér** resultater i menuen Handlinger nederst på pop **op-siden**.

   ![Indstillingen Eksportér resultater i menuen Handlinger.](../media/ActionMenuExportResults.png)

   Pop **op-siden** Eksportér resultater vises. De eksportindstillinger, der er tilgængelige til at eksportere indhold, afhænger af, om søgeresultaterne er placeret i postkasser eller websteder eller en kombination af begge dele.

3. Vælg **en af** følgende indstillinger under Outputindstillinger:
  
   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

    - **Alle elementer, undtagen dem, der har ukendt format, krypteres eller blev ikke indekseret af andre årsager**. Denne indstilling eksporterer kun indekserede elementer.
  
    - **Alle elementer, herunder elementer, der har ukendt format, er krypteret eller ikke blev indekseret af andre årsager**. Denne indstilling eksporterer indekserede og indekserede elementer.
  
    - **Det er kun elementer, der har et ukendt format, der krypteres eller ikke er indekseret af andre årsager**. Denne indstilling eksporterer kun enkelt x-elementer.

      Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af, hvordan delvist indekserede elementer eksporteres. Du kan finde flere oplysninger om delvist indekserede elementer under [Delvist indekserede elementer i Indholdssøgning](partially-indexed-items-in-content-search.md).

4. Vælg **en Exchange af følgende** indstillinger under Eksportér indhold som:
  
   ![Exchange indstillinger.](../media/ExchangeExportOptions.png)

    - **Én PST-fil for hver postkasse**: Eksporterer én PST-fil for hver brugerpostkasse, der indeholder søgeresultater. Alle resultater fra brugerens arkivpostkasse er inkluderet i den samme PST-fil. Denne indstilling gengiver postkassemappestrukturen fra kildepostkassen.
  
    - **En PST-fil**, der indeholder alle meddelelser: Eksporterer en enkelt PST-fil (kaldet *Exchange.pst*), der indeholder søgeresultater fra alle kildepostkasser, som medtages i søgningen. Denne indstilling gengiver postkassemappestrukturen for hver meddelelse.
  
    - **En PST-fil**, der indeholder alle meddelelser i en enkelt mappe: Eksporterer søgeresultater til en enkelt PST-fil, hvor alle meddelelser er placeret i en enkelt mappe på øverste niveau. Denne indstilling giver korrekturlæsere mulighed for at gennemse elementer i kronologisk rækkefølge (elementerne er sorteret efter sendt dato), uden at de behøver at navigere i den oprindelige postkassemappestruktur for hvert element.
  
    - **Individuelle meddelelser**: Eksporterer søgeresultater som individuelle mails ved hjælp af formatet .msg. Hvis du vælger denne indstilling, eksporteres søgeresultaterne via mail til en mappe i filsystemet. Mappestien til individuelle meddelelser er den samme som den, der bruges, hvis du eksporterede resultaterne til en PST-fil.
  
5. Konfigurer følgende yderligere indstillinger:

   ![Konfigurere andre eksportindstillinger.](../media/OtherExportOptions.png)

   1. Markér **afkrydsningsfeltet Aktivér duplikering af Exchange for** at udelukke dublerede meddelelser.
  
      Hvis du vælger denne indstilling, eksporteres der kun én kopi af en meddelelse, selvom der findes flere kopier af den samme meddelelse i de postkasser, der blev søgt i. Eksportér resultatrapporten (som er en fil med navnet Results.csv) indeholder en række for hver kopi af en dubletmeddelelse, så du kan identificere de postkasser (eller offentlige mapper), der indeholder en kopi af den duplikerede meddelelse. Du kan finde flere oplysninger om afplikering, og hvordan duplikerede elementer identificeres, under [Afplikning i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).
  
   2. Markér **afkrydsningsfeltet Medtag versioner SharePoint filer** for at eksportere alle versioner af SharePoint dokumenter. Denne indstilling vises kun, hvis indholdskilderne for søgningen omfatter SharePoint eller OneDrive for Business websteder.
  
   3. Vælg **Eksportér filer i en komprimeret (zippet) mappe. Omfatter kun individuelle meddelelser SharePoint dokumenter** for at eksportere søgeresultater til komprimerede mapper. Denne indstilling vises kun, når du vælger at Exchange elementer som individuelle meddelelser, og når søgeresultaterne indeholder SharePoint eller OneDrive dokumenter. Denne indstilling bruges primært til at arbejde omkring grænsen på 260 tegn i Windows, når elementer eksporteres. Se "Filnavne for eksporterede elementer" i [sektionen Flere](#more-information) oplysninger.
   > [!IMPORTANT]
   > Eksport af filer i en komprimeret (ZIP-komprimeret) mappe øger eksporttider.
  
6. Klik **på Eksportér** for at starte eksporten. Søgeresultaterne klargjort til at blive downloadet, hvilket betyder, at de indsamles fra de oprindelige placeringer af indhold og derefter overføres til Azure Storage placering i Microsoft-skyen. Dette kan tage flere minutter.

Se næste afsnit for at få vejledning i at downloade de eksporterede søgeresultater.
  
## <a name="step-2-download-the-search-results"></a>Trin 2: Download søgeresultaterne

Næste trin er at hente søgeresultaterne fra placeringen Azure Storage din lokale computer.

> [!NOTE]
> De eksporterede søgeresultater skal downloades inden for 14 dage, efter at du har oprettet eksportjobbet i trin 1.
  
1. På siden **Indholdssøgning** i Microsoft 365 Overholdelsescenter du vælge **fanen Eksporter**
  
   Du skal muligvis klikke på Opdater **for** at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportjob har samme navn som den tilsvarende søgning **, _Export** er føjet til søgenavnet.
  
2. Vælg det eksportjob, du oprettede i trin 1.

3. Klik på Kopiér til **Udklipsholder** under **Eksportér på pop op-siden**. Du kan bruge denne nøgle i trin 6 til at downloade søgeresultaterne.
  
   > [!IMPORTANT]
   > Da alle kan installere og starte værktøjet eDiscovery-eksport og derefter bruge denne nøgle til at downloade søgeresultaterne, skal du sørge for at træffe forholdsregler for at beskytte denne nøgle på samme måde, som du beskytter adgangskoder eller andre sikkerhedsrelaterede oplysninger.

4. Klik på Hent resultater øverst på pop **op-siden**.

5. Hvis du bliver bedt om at installere **eDiscovery-eksportværktøjet, skal** du klikke på **Installér**.

6. I **eDiscovery-eksportværktøjet** skal du gøre følgende:

   ![eDiscovery-eksportværktøj.](../media/eDiscoveryExportTool.png)

   1. Indsæt den eksportnøgle, du kopierede i trin 3, i det relevante felt.
  
   2. Klik **på** Gennemse for at angive den placering, hvor du vil hente filerne med søgeresultatet.
  
      > [!IMPORTANT]
      >  På grund af høj netværksaktivitet under overførslen bør du kun downloade søgeresultaterne til en placering på et internt drev på din lokale computer. Du får den bedste downloadoplevelse ved at følge disse retningslinjer: <br/>
      >- Download ikke søgeresultater til en UNC-sti, et tilknyttet netværksdrev, et eksternt USB-drev eller en synkroniseret OneDrive for Business konto.<br/>
      >- Deaktiver antivirusscanning for den mappe, du downloader søgeresultatet til.<br/>
      >- Download søgeresultater til forskellige mapper til samtidige downloadjobs.

7. Klik **på Start** for at hente søgeresultaterne til din computer.
  
    Værktøjet **til eDiscovery-eksport** viser statusoplysninger om eksportprocessen, herunder et skøn over antallet (og størrelsen) af de resterende elementer, der skal downloades. Når eksporten er fuldført, kan du få adgang til filerne på den placering, hvor de blev downloadet.

## <a name="more-information"></a>Flere oplysninger

Her er flere oplysninger om eksport af søgeresultater.
  
[Eksportgrænser](#export-limits)
  
[Eksportér rapporter](#export-reports)
  
[Eksportere delvist indekserede elementer](#exporting-partially-indexed-items)

[Eksport af individuelle meddelelser eller PST-filer](#exporting-individual-messages-or-pst-files)

[Dekryptering af RMS-beskyttede mails og krypterede vedhæftede filer](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Filnavne for eksporterede elementer](#filenames-of-exported-items)  
  
[Diverse bestemmelser](#miscellaneous)
  
### <a name="export-limits"></a>Eksportgrænser

Du kan finde oplysninger om begrænsninger ved eksport af indholdssøgning i afsnittet "Eksportgrænser" i [Begrænsninger for indholdssøgning](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Eksportér rapporter
  
- Når du eksporterer søgeresultater, medtages følgende rapporter ud over søgeresultaterne.
  
  - **Eksportoversigt** Et Excel dokument, der indeholder en oversigt over eksporten. Dette omfatter oplysninger som f.eks. antallet af indholdskilder, der blev søgt, de anslåede og downloadede størrelser af søgeresultaterne samt det anslåede og downloadede antal elementer, der blev eksporteret.
  
  - **Manifest** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der medtages i søgeresultaterne.
  
  - **Resultater** Et Excel dokument, der indeholder oplysninger om hvert element, der downloades som et søgeresultat. For mails indeholder resultatloggen oplysninger om hver meddelelse, herunder:
  
    - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).
  
    - Den dato, hvor meddelelsen blev sendt eller modtaget.

    - Emnelinjen i meddelelsen.

    - Afsenderen og modtagerne af meddelelsen.

    - Om meddelelsen er en dubletmeddelelse, hvis du har aktiveret indstillingen Dupliker, når du eksporterer søgeresultaterne. Dublerede meddelelser har en værdi i kolonnen **Dupliker til** element, der identificerer meddelelsen som en dublet. Værdien i kolonnen **Dupliker til element** indeholder elementidentiteten for den meddelelse, der blev eksporteret. Du kan finde flere oplysninger i [Afplikering i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

      For dokumenter fra SharePoint og OneDrive for Business indeholder resultatloggen oplysninger om hvert dokument, herunder:

      - Dokumentets URL-adresse.

      - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.

      - Den dato, hvor dokumentet sidst blev ændret.

      - Navnet på dokumentet (som er placeret i kolonnen Emne i resultatloggen).

  - **Unindexed Items** Et Excel dokument, der indeholder oplysninger om eventuelle delvist indekserede elementer, der medtages i søgeresultaterne. Hvis du ikke medtager delvist indekserede elementer, når du genererer rapporten med søgeresultater, hentes denne rapport stadig, men den vil være tom.

  - **Fejl og advarsler** Indeholder fejl og advarsler om filer, der er opstået under eksporten. Se kolonnen Fejldetaljer for at få oplysninger, der er specifikke for hver enkelt fejl eller advarsel.

  - **Elementer, der er sprunget over** Når du eksporterer søgeresultater fra SharePoint og OneDrive for Business, vil eksporten som regel indeholde en rapport over ignorerede elementer (SkippedItems.csv). De elementer, der er citeret i denne rapport, er typisk elementer, der ikke hentes, f.eks. en mappe eller et dokumentsæt. Det er tils designes, at disse typer elementer ikke eksporteres. For andre elementer, der blev sprunget over, viser feltet "Fejltype" og "Fejldetaljer" i rapporten over ignorerede elementer årsagen til, at elementet blev sprunget over og ikke er hentet med de andre søgeresultater.

  - **Trace.log Indeholder** detaljerede logføringsoplysninger om eksportprocessen og kan hjælpe med at afdække problemer under eksporten. Hvis du åbner en billet hos Microsoft Support om et problem, der er relateret til eksport af søgeresultater, kan du blive bedt om at angive denne sporingslog.
  
    > [!NOTE]
    > Du kan blot eksportere disse dokumenter uden at skulle eksportere de faktiske søgeresultater. Se [Eksportere en rapport for indholdssøgning](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Eksportere delvist indekserede elementer
  
- Hvis du eksporterer postkasseelementer fra en indholdssøgning, der returnerer alle postkasseelementer i søgeresultaterne (fordi der ikke medtages nogen nøgleord i søgeforespørgslen), kopieres delvist indekserede elementer ikke til den PST-fil, der indeholder de indekserede elementer. Dette skyldes, at alle elementer, herunder eventuelle delvist indekserede elementer, automatisk medtages i de almindelige søgeresultater. Det betyder, at delvist indekserede elementer medtages i en PST-fil (eller som individuelle meddelelser), der indeholder de andre indekserede elementer.

    Hvis du eksporterer både de indekserede og delvist indekserede elementer, eller hvis du kun eksporterer de indekserede elementer fra en indholdssøgning, der returnerer alle elementer, hentes det samme antal elementer. Dette sker, selvom de anslåede søgeresultater for indholdssøgningen (vises i søgestatistikken i Microsoft 365 Overholdelsescenter) stadig indeholder et separat estimat for antallet af delvist indekserede elementer. Lad os f.eks. sige, at estimatet for en søgning, der indeholder alle elementer (ingen nøgleord i søgeforespørgslen), viser, at der blev fundet 1.000 elementer, og at der også blev fundet 200 delvist indekserede elementer. I dette tilfælde indeholder de 1.000 elementer de delvist indekserede elementer, fordi søgningen returnerer alle elementer. Med andre ord er der 1.000 elementer i alt, der returneres af søgningen, og ikke 1.200 elementer (som du måske forventer). Hvis du eksporterer resultaterne af denne søgning og vælger at eksportere indekserede og delvist indekserede elementer (eller kun eksportere delvist indekserede elementer), hentes der 1.000 elementer. Dette skyldes igen, at delvist indekserede elementer er inkluderet i de almindelige (indekserede) resultater, når du bruger en tom søgeforespørgsel til at returnere alle elementer. Hvis du i dette eksempel vælger kun at eksportere delvist indekserede elementer, hentes kun de 200 indekserede elementer.

    Bemærk også, at i det forrige eksempel (når du eksporterer indekserede og delvist indekserede elementer, eller du kun eksporterer  indekserede elementer), ville rapporten Eksportoversigt, der følger med de eksporterede søgeresultater, vise 1.000 elementer anslåede elementer og 1.000 downloadede elementer af samme årsager som tidligere beskrevet. 

- Hvis den søgning, du eksporterer resultater fra, var en søgning på bestemte placeringer med indhold eller alle placeringer med indhold i organisationen, eksporteres kun de dele af elementerne fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Med andre ord, hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, så eksporteres elementer, der er delvist indekseret i den pågældende postkasse eller websted, ikke. Dette skyldes, at eksport af delvist indekserede elementer fra mange placeringer i organisationen kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og hente søgeresultaterne.

    Hvis du vil eksportere delvist indekserede elementer fra alle indholdsplaceringer til en søgning, skal du konfigurere søgningen til at returnere alle elementer (ved at fjerne eventuelle nøgleord fra søgeforespørgslen) og derefter kun eksportere delvist indekserede elementer, når du eksporterer søgeresultaterne.

    ![Brug den tredje eksportindstilling til kun at eksportere enkeltelementer.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Når du eksporterer søgeresultater fra SharePoint- eller OneDrive for Business-websteder, afhænger muligheden for at eksportere indekserede elementer også af den eksportindstilling, du vælger, og om et websted, der blev søgt på, indeholder et indekseret element, der svarer til søgekriterierne. Hvis du f.eks. søger efter bestemte SharePoint- eller OneDrive for Business-websteder, og der ikke findes nogen søgeresultater, eksporteres ingen indekserede elementer fra disse websteder, hvis du vælger den anden eksportindstilling til at eksportere både indekserede og indekserede elementer. Hvis et indekseret element fra et websted opfylder søgekriterierne, eksporteres alle indekserede elementer fra det pågældende websted, når du eksporterer både indekserede og indekserede elementer. Følgende illustration beskriver eksportindstillingerne baseret på, om et websted indeholder et indekseret element, der svarer til søgekriterierne.

    ![Vælg eksportindstillingen baseret på, om et websted indeholder et indekseret element, der svarer til søgekriterierne.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Det er kun indekserede elementer, der opfylder søgekriterierne, der eksporteres. Der eksporteres ingen delvist indekserede elementer.

    b. Hvis ingen indekserede elementer fra et websted opfylder søgekriterierne, eksporteres delvist indekserede elementer fra det samme websted ikke. Hvis indekserede elementer fra et websted returneres i søgeresultaterne, så eksporteres de delvist indekserede elementer fra webstedet. Med andre ord eksporteres kun de delvist indekserede elementer fra websteder, der indeholder elementer, der opfylder søgekriterierne.

    c. Alle delvist indekserede elementer fra alle websteder i søgningen eksporteres, uanset om et websted indeholder elementer, der opfylder søgekriterierne.

    Hvis du vælger at eksportere delvist indekserede elementer, eksporteres delvist indekserede postkasseelementer i en separat PST-fil, uanset hvilken indstilling du vælger under **Eksportér Exchange som**.

- Hvis delvist indekserede elementer returneres i søgeresultaterne (fordi andre egenskaber for delvist indekserede elementer matcher søgekriterierne), så eksporteres de delvist indekserede med de almindelige søgeresultater. Så hvis du vælger at eksportere både indekserede elementer og delvist indekserede elementer (ved at vælge alle elementer, herunder dem, der har ukendt **format,** er krypterede eller ikke blev indekseret af andre årsager til eksportindstillingen), vil de delvist indekserede elementer, der er eksporteret med almindelige resultater, blive vist i Results.csv-rapporten. De vil ikke blive vist i rapporten Unindexed items.csv rapport.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Eksport af individuelle meddelelser eller PST-filer
  
- Hvis navnet på filstien for en meddelelse overskrider den maksimale tegngrænse for Windows, afkortes filnavnet på stien. Men navnet på den oprindelige filsti vises i Manifest og ResultsLog.
  
- Som beskrevet tidligere eksporteres søgeresultaterne fra mails til en mappe i filsystemet. Mappestien til individuelle meddelelser kopierede mappestien i brugerens postkasse. I en søgning med navnet "ContosoCase101" blev meddelelser i en brugers indbakke f.eks. placeret i mappestien  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`.

- Hvis du vælger at eksportere mails i én PST-fil, der indeholder alle meddelelser i en enkelt mappe, medtages mappen Slettet post og  en søgemappe på det øverste niveau i PST-mappen. Disse mapper er tomme.

- Som tidligere nævnt skal du eksportere søgeresultater fra mails som individuelle meddelelser for at dekryptere RMS-beskyttede meddelelser, når de eksporteres. Krypterede meddelelser forbliver krypterede, hvis du eksporterer søgeresultaterne fra mails som en PST-fil.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Dekryptering af RMS-beskyttede mails og krypterede vedhæftede filer

Alle rettighedsbeskyttede mails (RMS-beskyttede), der medtages i resultaterne af en indholdssøgning, bliver dekrypteret, når du eksporterer dem. Desuden vil alle filer, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) og er vedhæftet en mail, som er inkluderet i søgeresultaterne, også blive dekrypteret, når den eksporteres. Denne dekrypteringsfunktion er aktiveret som standard for medlemmer af rollegruppen eDiscovery Manager. Dette skyldes, at administrationsrollen RMS Dekrypter tildeles denne rollegruppe som standard. Husk følgende, når du eksporterer krypterede mails og vedhæftede filer:
  
- Som tidligere nævnt skal du eksportere søgeresultaterne som individuelle meddelelser for at dekryptere RMS-beskyttede meddelelser, når du eksporterer dem. Hvis du eksporterer søgeresultater til en PST-fil, forbliver RMS-beskyttede meddelelser krypteret.

- Meddelelser, der er dekrypteret, identificeres i **ResultsLog-rapporten** . Denne rapport indeholder en kolonne med navnet **Afkod status**, og en  værdi af Afkodet i denne kolonne identificerer de meddelelser, der blev dekrypteret.

- Ud over at dekryptere vedhæftede filer, når du eksporterer søgeresultater, kan du også se en forhåndsvisning af den dekrypterede fil, når du får vist søgeresultaterne. Du kan kun se den rettighedsbeskyttede mail, når du har eksporteret den.

- På nuværende tidspunkt omfatter dekrypteringsfunktionen, når du eksporterer søgeresultater, ikke krypteret indhold SharePoint og OneDrive for Business websteder. Men understøttelse kommer snart til dokumenter, der er krypteret med Microsoft-krypteringsteknologier og gemt i SharePoint Online og OneDrive for Business.

- Hvis du vil forhindre nogen i at dekryptere RMS-beskytte meddelelser og krypterede vedhæftede filer, skal du oprette en brugerdefineret rollegruppe (ved at kopiere den indbyggede rollegruppe eDiscovery Manager) og derefter fjerne administrationsrollen RMS Dekrypter fra den brugerdefinerede rollegruppe. Tilføj derefter den person, du ikke vil dekryptere meddelelser fra, som medlem af den brugerdefinerede rollegruppe.
  
### <a name="filenames-of-exported-items"></a>Filnavne for eksporterede elementer
  
- Der er en grænse på 260 tegn (som er indført af operativsystemet) for det fulde stinavn for mails og webstedsdokumenter, der er eksporteret til din lokale computer. Det fulde stinavn for eksporterede elementer omfatter elementets oprindelige placering og mappeplaceringen på den lokale computer, hvor søgeresultaterne hentes til. Hvis du f.eks  `C:\Users\Admin\Desktop\SearchResults` . angiver, at søgeresultaterne skal downloades til eDiscovery-eksportværktøjet, så vil det fulde stinavn for et downloadet mailelement være  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`.

- Hvis grænsen på 260 tegn overskrides, afkortes det fulde stinavn for et element på følgende måde:

  - Hvis navnet på den fulde sti er længere end 260 tegn, bliver filnavnet afkortet, så det kommer under grænsen. Bemærk, at det afkortede filnavn (undtagen filtypenavnet) ikke er mindre end otte tegn.

  - Hvis navnet på den fulde sti stadig er for langt efter afkortning af filnavnet, flyttes elementet fra den aktuelle placering til den overordnede mappe. Hvis stinavnet stadig er for langt, gentages processen: afkort filnavnet, og flyt om nødvendigt igen til den overordnede mappe. Denne proces gentages, indtil det fulde stinavn er under grænsen på 260 tegn.

  - Hvis der allerede findes et afkortet fuldt stinavn, tilføjes der et versionsnummer i slutningen af filnavnet. f.eks. `statusmessage(2).msg`.

    For at afhjælpe dette problem skal du overveje at downloade søgeresultater til en placering med et kort stinavn; Hvis du f.eks.  `C:\Results` hentede søgeresultater til en mappe, der blev navngivet, blev der føjet færre tegn til stinavnene på eksporterede elementer end at hente dem til en mappe med navnet  `C:\Users\Admin\Desktop\Results`.

- Når du eksporterer webstedsdokumenter, er det også muligt, at det oprindelige filnavn på et dokument ændres. Dette sker specifikt for dokumenter, der er blevet slettet fra en SharePoint eller OneDrive for Business websted, der er blevet sat i venteposition. Når et dokument på et websted, der er sat i venteposition, slettes det slettede dokument automatisk til biblioteket til opbevaring af dokumenter for webstedet (som blev oprettet, da det blev sat i venteposition). Når det slettede dokument flyttes til biblioteket til opbevaring af dokumenter, føjes et tilfældigt genereret og entydigt id til det oprindelige filnavn for dokumentet. Hvis f.eks. filnavnet for  `FY2017Budget.xlsx` et dokument er, og dokumentet senere slettes og flyttes til biblioteket til opbevaring af dokumenter, ændres filnavnet på det dokument, der flyttes til biblioteket til opbevaring af dokumenter, til noget i lignende stand  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`. Hvis et dokument i biblioteket til opbevaring af dokumenter svarer til forespørgslen fra en indholdssøgning, og du eksporterer resultaterne af søgningen, har den eksporterede fil det ændrede filnavn. I dette eksempel vil filnavnet for det eksporterede dokument være  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`.

    Når et dokument på et websted, der er sat i venteposition, ændres (og versionsdeling for dokumentbiblioteket på webstedet er aktiveret), oprettes der automatisk en kopi af filen i biblioteket til opbevaring af dokumenter. I dette tilfælde føjes et tilfældigt genereret og entydigt id også til filnavnet på det dokument, der kopieres til biblioteket til opbevaring af dokumenter.

    Filnavnene på dokumenter, der flyttes eller kopieres til biblioteket til opbevaring af dokumenter, er fordi filnavne, der er i konflikt med hinanden, forhindres. Du kan finde flere oplysninger om at sætte en venteposition på websteder og biblioteket til opbevaring af dokumenter i Oversigt over direkte [venteposition SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Diverse bestemmelser
  
- Når du henter søgeresultater ved hjælp af eDiscovery-eksportværktøjet, er det muligt, at du modtager følgende fejlmeddelelse: `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` Dette er en midlertidig fejl, der typisk opstår i Azure Storage placering. Du kan løse dette problem ved igen [at downloade søgeresultaterne](#step-2-download-the-search-results), hvilket genstarter eDiscovery-eksportværktøjet.

- Alle søgeresultater og eksportrapporter er inkluderet i en mappe, der har samme navn som indholdssøgningen. De mails, der blev eksporteret, findes i en mappe med **navnet Exchange**. Dokumenter er placeret i en mappe med **navnet SharePoint**.

- Filsystemmetadata for dokumenter på SharePoint og OneDrive for Business websted bevares, når dokumenter eksporteres til din lokale computer. Det betyder, at dokumentegenskaber som f.eks. oprettede og datoer for seneste ændring ikke ændres, når dokumenter eksporteres.

- Hvis søgeresultaterne indeholder et listeelement fra SharePoint, der svarer til søgeforespørgslen, eksporteres alle rækker på listen ud over det element, der svarer til søgeforespørgslen, og eventuelle vedhæftede filer på listen. Årsagen til denne funktionsmåde er at angive en kontekst for listeelementer, der returneres i søgeresultaterne. De ekstra listeelementer og vedhæftede filer kan medføre, at antallet af eksporterede elementer er anderledes end det oprindelige skøn over søgeresultater.
