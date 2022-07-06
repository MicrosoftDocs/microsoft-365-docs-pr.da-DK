---
title: Eksportér søgeresultater for indhold
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Eksportér søgeresultaterne fra en indholdssøgning i Microsoft Purview-compliance-portal til en lokal computer. Mailresultater eksporteres som PST-filer. Indhold fra SharePoint og OneDrive for Business websteder eksporteres som oprindelige Office-dokumenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a73120b697441255e6ac53c5bd371d56931d8644
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641576"
---
# <a name="export-content-search-results"></a>Eksportér søgeresultater for indhold

Når en indholdssøgning er blevet kørt, kan du eksportere søgeresultaterne til en lokal computer. Når du eksporterer mailresultater, downloades de til din computer som PST-filer. Når du eksporterer indhold fra SharePoint og OneDrive for Business websteder, eksporteres der kopier af oprindelige Office-dokumenter. Der er andre dokumenter og rapporter, der er inkluderet i de eksporterede søgeresultater.
  
Eksport af resultaterne af en indholdssøgning omfatter forberedelse af resultaterne og derefter download af dem til en lokal computer. Disse trin til eksport af søgeresultater gælder også for eksport af resultaterne af en søgning, der er knyttet til Microsoft Purview eDiscovery (Standard)-sager.
  
## <a name="before-you-export-search-results"></a>Før du eksporterer søgeresultater

- Hvis du vil eksportere søgeresultater, skal du have tildelt rollen Eksportstyring i Microsoft Purview-compliance-portal. Denne rolle tildeles til den indbyggede rollegruppe eDiscovery Manager. Den er ikke som standard tildelt rollegruppen Organisationsadministration. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Den computer, du bruger til at eksportere søgeresultaterne, skal opfylde følgende systemkrav:
  
  - Seneste version af Windows (32-bit eller 64-bit)
  
  - Microsoft .NET Framework 4.7 eller nyere
  
- Du skal bruge Microsoft Edge<sup>1</sup> til at køre eDiscovery-eksportværktøjet. Brug af Internet Explorer 11 til at eksportere søgeresultater understøttes ikke længere<sup>2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Som følge af de seneste ændringer af Microsoft Edge er ClickOnce-understøttelse ikke længere aktiveret som standard. Du kan finde en vejledning i, hvordan du aktiverer ClickOnce-understøttelse i Edge, under [Brug eDiscovery-eksportværktøjet i Microsoft Edge](configure-edge-to-export-search-results.md). Desuden producerer Microsoft ikke udvidelser eller tilføjelsesprogrammer fra tredjepart til ClickOnce-programmer. Eksport af søgeresultater ved hjælp af en browser, der ikke understøttes, med udvidelser eller tilføjelsesprogrammer fra tredjepart understøttes ikke.
  >
  > <sup>2</sup> Fra august 2021 understøtter Microsoft 365-apps og -tjenester ikke længere Internet Explorer 11 (IE11), og brugerne kan have en forringet oplevelse eller ikke kunne oprette forbindelse til disse apps og tjenester. Disse apps og tjenester udfases i løbet af de kommende uger og måneder for at sikre en problemfri ophør af support. Hver app og tjeneste udfases efter uafhængige tidsplaner. Du kan få flere oplysninger i dette [blogindlæg](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Det eDiscovery-eksportværktøj, du bruger i trin 2 til at downloade søgeresultater, understøtter ikke automatisering (ved hjælp af et script eller ved at køre cmdlet'er). Vi anbefaler på det kraftigste, at du ikke automatiserer forberedelsesprocessen i trin 1 eller downloadprocessen i trin 2. Hvis du automatiserer en af disse processer, yder Microsoft Support ikke hjælp, hvis du støder på problemer.

- Vi anbefaler, at du downloader søgeresultater til en lokal computer. Hvis du vil undgå, at din virksomheds firewall eller proxyinfrastruktur forårsager problemer, når du downloader søgeresultater, kan du overveje at downloade søgeresultater til et virtuelt skrivebord uden for netværket. Dette kan reducere timeouts, der opstår i Azure-dataforbindelser, når der eksporteres et stort antal filer. Du kan få flere oplysninger om virtuelle skriveborde under [Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop).

- Hvis du vil forbedre ydeevnen, når du downloader søgeresultater, kan du overveje at opdele søgninger, der returnerer et stort sæt resultater, i mindre søgninger. Du kan f.eks. bruge datointervaller i søgeforespørgsler til at returnere et mindre sæt resultater, der kan downloades hurtigere.
  
- Når du eksporterer søgeresultater, gemmes dataene midlertidigt på en Azure Storage-placering i Microsoft-cloudmiljøet, før de downloades til din lokale computer. Sørg for, at din organisation kan oprette forbindelse til slutpunktet i Azure, som er **\*.blob.core.windows.net** (jokertegnet repræsenterer et entydigt id for din eksport). Søgeresultaterne slettes fra Azure Storage-placeringen to uger efter, at de er oprettet. 
  
- Hvis din organisation bruger en proxyserver til at kommunikere med internettet, skal du definere proxyserverindstillingerne på den computer, du bruger til at eksportere søgeresultaterne (så eksportværktøjet kan godkendes af proxyserveren). Det gør du ved at åbne  *filenmachine.config*  på den placering, der svarer til din version af Windows. 
  
  - **32-bit:** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64-bit:** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Føj følgende linjer til  *denmachine.config*  fil et sted mellem mærkerne  `<configuration>` og  `</configuration>` . Sørg for at erstatte  `ProxyServer` og  `Port` med de korrekte værdier for din organisation, `proxy01.contoso.com:80`f.eks. . 
  
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

- Hvis resultaterne af en søgning er ældre end 7 dage, og du sender et eksportjob, vises der en fejlmeddelelse, hvor du bliver bedt om at køre søgningen igen for at opdatere søgeresultaterne. Hvis det sker, skal du annullere eksporten, køre søgningen igen og derefter starte eksporten igen.

## <a name="step-1-prepare-search-results-for-export"></a>Trin 1: Forbered søgeresultater til eksport

Det første trin er at forberede søgeresultaterne til eksport. Når du forbereder resultater, uploades de til en Microsoft-leveret Azure Storage-placering i Microsoft-cloudmiljøet. Indhold fra postkasser og websteder uploades med en maksimal hastighed på 2 GB pr. time.
  
1. Vælg den indholdssøgning, du vil eksportere resultater fra, på overholdelsesportalen.
  
2. Klik på **Eksportér resultater** i menuen **Handlinger** nederst på pop op-siden.

   ![Indstillingen Eksportér resultater i menuen Handlinger.](../media/ActionMenuExportResults.png)

   Pop op-vinduet **Eksportér resultater** vises. De eksportindstillinger, der er tilgængelige til eksport af indhold, afhænger af, om søgeresultaterne er placeret i postkasser eller på websteder eller en kombination af begge.

3. Vælg en af følgende indstillinger under **Outputindstillinger**:
  
   ![Eksportér outputindstillinger.](../media/ExportOutputOptions.png)

    - **Alle elementer, bortset fra elementer, der har et ukendt format, krypteres eller er ikke indekseret af andre årsager**. Denne indstilling eksporterer kun indekserede elementer.
  
    - **Alle elementer, herunder elementer, der har et ukendt format, krypteres eller er ikke indekseret af andre årsager**. Denne indstilling eksporterer indekserede og ikke-indekserede elementer.
  
    - **Kun elementer, der har et ukendt format, krypteres eller ikke er indekseret af andre årsager**. Denne indstilling eksporterer kun ikke-indekserede elementer.

      Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af, hvordan delvist indekserede elementer eksporteres. Du kan finde flere oplysninger om delvist indekserede elementer [under Delvist indekserede elementer i Indholdssøgning](partially-indexed-items-in-content-search.md).

4. Vælg en af følgende indstillinger under **Eksportér Exchange-indhold som**:
  
   ![Exchange-indstillinger.](../media/ExchangeExportOptions.png)

    - **Én PST-fil for hver postkasse**: Eksporterer én PST-fil for hver brugerpostkasse, der indeholder søgeresultater. Alle resultater fra brugerens arkivpostkasse er inkluderet i den samme PST-fil. Denne indstilling genskaber postkassens mappestruktur fra kildepostkassen.
  
    - **Én PST-fil, der indeholder alle meddelelser**: Eksporterer en enkelt PST-fil (med navnet *Exchange.pst*), der indeholder søgeresultaterne fra alle kildepostkasser, der er inkluderet i søgningen. Denne indstilling genskaber mappestrukturen for postkassen for hver meddelelse.
  
    - **Én PST-fil, der indeholder alle meddelelser i en enkelt mappe**: Eksporterer søgeresultater til en enkelt PST-fil, hvor alle meddelelser er placeret i en enkelt mappe på øverste niveau. Denne indstilling gør det muligt for korrekturlæsere at gennemse elementer i kronologisk rækkefølge (elementer sorteres efter afsendelsesdato) uden at skulle navigere i den oprindelige postkassemappestruktur for hvert element.
  
    - **Individuelle meddelelser**: Eksporterer søgeresultater som individuelle mails i formatet .msg. Hvis du vælger denne indstilling, eksporteres søgeresultater via mail til en mappe i filsystemet. Mappestien til individuelle meddelelser er den samme som den, der bruges, hvis du eksporterede resultaterne til en PST-fil.
  
5. Konfigurer følgende yderligere indstillinger:

   ![Konfigurer andre eksportindstillinger.](../media/OtherExportOptions.png)

   1. Markér afkrydsningsfeltet **Aktivér deduplikering for Exchange-indhold for** at udelade dublerede meddelelser.
  
      Hvis du vælger denne indstilling, eksporteres der kun én kopi af en meddelelse, selvom der findes flere kopier af den samme meddelelse i de postkasser, der blev søgt i. Rapporten med eksportresultater (som er en fil med navnet Results.csv) indeholder en række for hver kopi af en dubletmeddelelse, så du kan identificere de postkasser (eller offentlige mapper), der indeholder en kopi af den dublerede meddelelse. Du kan finde flere oplysninger om deduplikering, og hvordan dubletter identificeres, [under De-duplikering i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).
  
   2. Markér afkrydsningsfeltet **Medtag versioner til SharePoint-filer for** at eksportere alle versioner af SharePoint-dokumenter. Denne indstilling vises kun, hvis søgeindholdskilderne omfatter SharePoint eller OneDrive for Business websteder.
  
   3. Vælg **Eksportér filer i en zip-komprimeret mappe. Medtager kun individuelle meddelelser og SharePoint-dokumenter** til eksport af søgeresultater til komprimerede mapper. Denne indstilling vises kun, når du vælger at eksportere Exchange-elementer som individuelle meddelelser, og når søgeresultaterne omfatter SharePoint- eller OneDrive-dokumenter. Denne indstilling bruges primært til at omgå grænsen på 260 tegn i windows-filnavne, når elementer eksporteres. Se "Filnavne på eksporterede elementer" i afsnittet [Flere oplysninger](#more-information) .
   > [!IMPORTANT]
   > Eksport af filer i en zip-komprimeret mappe øger eksporttiden.
  
6. Klik på **Eksportér** for at starte eksportprocessen. Søgeresultaterne er forberedt til download, hvilket betyder, at de indsamles fra de oprindelige indholdsplaceringer og derefter uploades til en Azure Storage-placering i Microsoft-cloudmiljøet. Dette kan tage flere minutter.

Se næste afsnit for at få instruktioner til at downloade de eksporterede søgeresultater.
  
## <a name="step-2-download-the-search-results"></a>Trin 2: Download søgeresultaterne

Det næste trin er at downloade søgeresultaterne fra Azure Storage-placeringen til din lokale computer.

> [!NOTE]
> De eksporterede søgeresultater skal hentes inden for 14 dage, efter at du har oprettet eksportjobbet i trin 1.
  
1. På siden **Indholdssøgning** i overholdelsesportalen skal du vælge fanen **Eksporter**
  
   Du skal muligvis klikke på **Opdater** for at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportjob har samme navn som den tilsvarende søgning med **_Export** føjet til søgenavnet.
  
2. Vælg det eksportjob, du oprettede i trin 1.

3. Klik på **Kopiér til Udklipsholder** på pop op-siden under **Eksportér nøgle**. Du kan bruge denne nøgle i trin 6 til at downloade søgeresultaterne.
  
   > [!IMPORTANT]
   > Da alle kan installere og starte eDiscovery-eksportværktøjet og derefter bruge denne nøgle til at downloade søgeresultaterne, skal du sørge for at træffe forholdsregler for at beskytte denne nøgle på samme måde, som du ville beskytte adgangskoder eller andre sikkerhedsrelaterede oplysninger.

4. Klik på **Download resultater** øverst på pop op-siden.

5. Hvis du bliver bedt om at installere **eDiscovery-eksportværktøjet**, skal du klikke på **Installér**.

6. Gør følgende i **eDiscovery-eksportværktøjet**:

   ![eDiscovery-eksportværktøj.](../media/eDiscoveryExportTool.png)

   1. Indsæt den eksportnøgle, du kopierede, i trin 3 i det relevante felt.
  
   2. Klik på **Gennemse** for at angive den placering, hvor du vil downloade søgeresultatfilerne.
  
      > [!IMPORTANT]
      >  På grund af høj netværksaktivitet under download bør du kun downloade søgeresultater til en placering på et internt drev på din lokale computer. Følg disse retningslinjer for at få den bedste downloadoplevelse: <br/>
      >- Download ikke søgeresultater til en UNC-sti, et tilknyttet netværksdrev, et eksternt USB-drev eller en synkroniseret OneDrive for Business konto.<br/>
      >- Deaktiver antivirusscanning for den mappe, du downloader søgeresultatet til.<br/>
      >- Download søgeresultater til forskellige mapper for samtidige downloadjob.

7. Klik på **Start** for at hente søgeresultaterne til computeren.
  
    **EDiscovery-eksportværktøjet** viser statusoplysninger om eksportprocessen, herunder et estimat af antallet (og størrelsen) af de resterende elementer, der skal downloades. Når eksporten er fuldført, kan du få adgang til filerne på den placering, hvor de blev downloadet.

## <a name="more-information"></a>Flere oplysninger

Her er flere oplysninger om eksport af søgeresultater.
  
[Eksportgrænser](#export-limits)
  
[Eksportér rapporter](#export-reports)
  
[Eksport af delvist indekserede elementer](#exporting-partially-indexed-items)

[Eksport af individuelle meddelelser eller PST-filer](#exporting-individual-messages-or-pst-files)

[Dekrypterer RMS-beskyttede mails og krypterede vedhæftede filer](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Filnavne på eksporterede elementer](#filenames-of-exported-items)  
  
[Diverse](#miscellaneous)
  
### <a name="export-limits"></a>Eksportgrænser

Du kan finde oplysninger om grænser, når du eksporterer indholdssøgeresultater, i afsnittet "Eksportgrænser" i [Grænser for indholdssøgning](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Eksportér rapporter
  
- Når du eksporterer søgeresultater, medtages følgende rapporter ud over søgeresultaterne.
  
  - **Eksportér oversigt** Et Excel-dokument, der indeholder en oversigt over eksporten. Dette omfatter oplysninger som f.eks. antallet af indholdskilder, der blev søgt efter, de anslåede og downloadede størrelser af søgeresultaterne og det anslåede og downloadede antal elementer, der blev eksporteret.
  
  - **Manifestere** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der er inkluderet i søgeresultaterne.
  
  - **Resultater** Et Excel-dokument, der indeholder oplysninger om hvert element, der downloades som et søgeresultat. I forbindelse med mail indeholder resultatloggen oplysninger om hver meddelelse, herunder:
  
    - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).
  
    - Den dato, hvor meddelelsen blev sendt eller modtaget.

    - Emnelinjen fra meddelelsen.

    - Afsenderen og modtagerne af meddelelsen.

    - Angiver, om meddelelsen er en dubletmeddelelse, hvis du har aktiveret indstillingen deduplikering, når du eksporterer søgeresultaterne. Duplikerede meddelelser har en værdi i kolonnen **Dupliker til element** , der identificerer meddelelsen som en dublet. Værdien i kolonnen **Dupliker til element** indeholder elementidentiteten for den meddelelse, der blev eksporteret. Du kan finde flere oplysninger [under De-duplikering i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

      For dokumenter fra SharePoint- og OneDrive for Business-websteder indeholder resultatloggen oplysninger om hvert dokument, herunder:

      - DOKUMENTETs URL-adresse.

      - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.

      - Den dato, hvor dokumentet senest blev ændret.

      - Navnet på dokumentet (som findes i kolonnen Emne i resultatloggen).

  - **Ikke-indekserede elementer** Et Excel-dokument, der indeholder oplysninger om alle delvist indekserede elementer, der medtages i søgeresultaterne. Hvis du ikke medtager delvist indekserede elementer, når du genererer rapporten med søgeresultater, downloades denne rapport stadig, men den er tom.

  - **Fejl og advarsler** Indeholder fejl og advarsler for filer, der opstod under eksporten. Se kolonnen Fejldetaljer for at få oplysninger, der er specifikke for hver enkelt fejl eller advarsel.

  - **Elementer, der er sprunget over** Når du eksporterer søgeresultater fra SharePoint og OneDrive for Business websteder, indeholder eksporten normalt en rapport over elementer (SkippedItems.csv). De elementer, der citeres i denne rapport, er typisk elementer, der ikke downloades, f.eks. en mappe eller et dokumentsæt. Det er tilsigtet ikke at eksportere disse typer elementer. For andre elementer, der blev sprunget over, viser feltet 'Fejltype' og 'Fejldetaljer' i rapporten over elementer, hvorfor elementet blev sprunget over og ikke blev downloadet med de andre søgeresultater.

  - **Trace.log** Indeholder detaljerede logføringsoplysninger om eksportprocessen og kan hjælpe med at afdække problemer under eksporten. Hvis du åbner en anmodning med Microsoft Support om et problem, der er relateret til eksport af søgeresultater, kan du blive bedt om at angive denne sporingslogfil.
  
    > [!NOTE]
    > Du kan blot eksportere disse dokumenter uden at skulle eksportere de faktiske søgeresultater. Se [Eksportér en indholdssøgningsrapport](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Eksport af delvist indekserede elementer
  
- Hvis du eksporterer postkasseelementer fra en indholdssøgning, der returnerer alle postkasseelementer i søgeresultaterne (fordi ingen nøgleord er inkluderet i søgeforespørgslen), kopieres delvist indekserede elementer ikke til den PST-fil, der indeholder de ikke-indekserede elementer. Det skyldes, at alle elementer, herunder eventuelle delvist indekserede elementer, automatisk medtages i de almindelige søgeresultater. Det betyder, at delvist indekserede elementer medtages i en PST-fil (eller som individuelle meddelelser), der indeholder de andre indekserede elementer.

    Hvis du eksporterer både de indekserede og delvist indekserede elementer, eller hvis du kun eksporterer de indekserede elementer fra en indholdssøgning, der returnerer alle elementer, hentes det samme antal elementer. Dette sker, selvom de anslåede søgeresultater for indholdssøgningen (der vises i søgestatistikken på overholdelsesportalen) stadig indeholder et separat estimat for antallet af delvist indekserede elementer. Lad os f.eks. sige, at estimatet for en søgning, der indeholder alle elementer (ingen nøgleord i søgeforespørgslen), viser, at der blev fundet 1.000 elementer, og at der også blev fundet 200 delvist indekserede elementer. I dette tilfælde indeholder de 1.000 elementer de delvist indekserede elementer, fordi søgningen returnerer alle elementer. Med andre ord er der 1.000 elementer i alt, der returneres af søgningen, og ikke 1.200 elementer (som du måske forventer). Hvis du eksporterer resultaterne af denne søgning og vælger at eksportere indekserede og delvist indekserede elementer (eller kun eksportere delvist indekserede elementer), hentes der 1.000 elementer. Det skyldes igen, at delvist indekserede elementer er inkluderet i de almindelige (indekserede) resultater, når du bruger en tom søgeforespørgsel til at returnere alle elementer. Hvis du i dette eksempel vælger kun at eksportere delvist indekserede elementer, er det kun de 200 ikke-indekserede elementer, der downloades.

    Bemærk også, at i det forrige eksempel (når du eksporterer indekserede og delvist indekserede elementer, eller du kun eksporterer indekserede elementer), viser rapporten **Eksportoversigt** , der er inkluderet i de eksporterede søgeresultater, 1.000 elementer anslået elementer og 1.000 hentede elementer af de samme årsager som tidligere beskrevet. 

- Hvis den søgning, du eksporterer resultater fra, var en søgning efter bestemte indholdsplaceringer eller alle indholdsplaceringer i din organisation, eksporteres kun de delvise elementer fra indholdsplaceringer, der indeholder elementer, der opfylder søgekriterierne. Det vil sige, at hvis der ikke findes nogen søgeresultater i en postkasse eller et websted, eksporteres alle delvist indekserede elementer i den pågældende postkasse eller det pågældende websted ikke. Årsagen til dette er, at eksport af delvist indekserede elementer fra mange placeringer i organisationen kan øge sandsynligheden for eksportfejl og øge den tid, det tager at eksportere og downloade søgeresultaterne.

    Hvis du vil eksportere delvist indekserede elementer fra alle indholdsplaceringer for en søgning, skal du konfigurere søgningen til at returnere alle elementer (ved at fjerne eventuelle nøgleord fra søgeforespørgslen) og derefter kun eksportere delvist indekserede elementer, når du eksporterer søgeresultaterne.

    ![Brug den tredje eksportindstilling til kun at eksportere ikke-indekserede elementer.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- Når du eksporterer søgeresultater fra SharePoint eller OneDrive for Business websteder, afhænger muligheden for at eksportere ikke-indekserede elementer også af den eksportindstilling, du vælger, og om et websted, der blev søgt efter, indeholder et indekseret element, der svarer til søgekriterierne. Hvis du f.eks. søger på bestemte SharePoint- eller OneDrive for Business websteder, og der ikke findes nogen søgeresultater, eksporteres ingen ikke-indekserede elementer fra disse websteder, hvis du vælger den anden eksportmulighed for at eksportere både indekserede og ikke-indekserede elementer. Hvis et indekseret element fra et websted stemmer overens med søgekriterierne, eksporteres alle ikke-indekserede elementer fra dette websted, når du eksporterer både indekserede og ikke-indekserede elementer. I følgende illustration beskrives eksportindstillingerne baseret på, om et websted indeholder et indekseret element, der opfylder søgekriterierne.

    ![Vælg eksportindstillingen, afhængigt af om et websted indeholder et indekseret element, der opfylder søgekriterierne.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Det er kun indekserede elementer, der opfylder søgekriterierne, der eksporteres. Der eksporteres ingen delvist indekserede elementer.

    b. Hvis ingen indekserede elementer fra et websted opfylder søgekriterierne, eksporteres der ikke delvist indekserede elementer fra det samme websted. Hvis indekserede elementer fra et websted returneres i søgeresultaterne, eksporteres de delvist indekserede elementer fra det pågældende websted. Det er med andre ord kun de delvist indekserede elementer fra websteder, der indeholder elementer, der opfylder søgekriterierne, der eksporteres.

    c. Alle delvist indekserede elementer fra alle websteder i søgningen eksporteres, uanset om et websted indeholder elementer, der opfylder søgekriterierne.

    Hvis du vælger at eksportere delvist indekserede elementer, eksporteres delvist indekserede postkasseelementer i en separat PST-fil, uanset hvilken indstilling du vælger under **Eksportér Exchange-indhold som**.

- Hvis der returneres delvist indekserede elementer i søgeresultaterne (fordi andre egenskaber for delvist indekserede elementer opfylder søgekriterierne), eksporteres de delvist indekserede elementer med de almindelige søgeresultater. Så hvis du vælger at eksportere både indekserede elementer og delvist indekserede elementer (ved at vælge indstillingen **Alle elementer, herunder elementer, der har et ukendt format, krypteres eller ikke er indekseret af andre årsager eksportmulighed** ), vises de delvist indekserede elementer, der eksporteres med de almindelige resultater, i Results.csv rapport. De vil ikke blive opført i Unindexed items.csv-rapporten.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Eksport af individuelle meddelelser eller PST-filer
  
- Hvis filnavnet på en meddelelse overskrider den maksimale tegngrænse for Windows, afkortes filnavnet. Men navnet på den oprindelige filsti vises i Manifest og ResultsLog.
  
- Som tidligere forklaret eksporteres mailsøgeresultater til en mappe i filsystemet. Mappestien til individuelle meddelelser replikerer mappestien i brugerens postkasse. For en søgning med navnet "ContosoCase101" vil meddelelser i en brugers indbakke f.eks. være placeret i mappestien  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`.

- Hvis du vælger at eksportere mails i én PST-fil, der indeholder alle meddelelser i en enkelt mappe, medtages mappen **Slettet post** og mappen **Søgemapper** på øverste niveau i PST-mappen. Disse mapper er tomme.

- Som tidligere angivet skal du eksportere søgeresultater for mails som individuelle meddelelser for at dekryptere RMS-beskyttede meddelelser, når de eksporteres. Krypterede meddelelser forbliver krypterede, hvis du eksporterer søgeresultater for mails som en PST-fil.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>Dekrypterer RMS-beskyttede mails og krypterede vedhæftede filer

Alle rettighedsbeskyttede (RMS-beskyttede) mails, der er inkluderet i resultaterne af en indholdssøgning, dekrypteres, når du eksporterer dem. Derudover dekrypteres alle filer, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) og er knyttet til en mail, der er inkluderet i søgeresultaterne, også, når de eksporteres. Denne dekrypteringsfunktion er som standard aktiveret for medlemmer af rollegruppen eDiscovery Manager. Det skyldes, at rollen RMS Decrypt management som standard er tildelt denne rollegruppe. Vær opmærksom på følgende ting, når du eksporterer krypterede mails og vedhæftede filer:
  
- Som tidligere forklaret skal du eksportere søgeresultaterne som individuelle meddelelser for at dekryptere RMS-beskyttede meddelelser, når du eksporterer dem. Hvis du eksporterer søgeresultater til en PST-fil, forbliver RMS-beskyttede meddelelser krypterede.

- Meddelelser, der dekrypteres, identificeres i **ResultsLog-rapporten** . Denne rapport indeholder en kolonne med navnet **Decode Status**, og en værdi af **Decoded** i denne kolonne identificerer de meddelelser, der blev dekrypteret.

- Ud over at dekryptere vedhæftede filer, når du eksporterer søgeresultater, kan du også få vist den dekrypterede fil, når du får vist søgeresultaterne. Du kan kun få vist den rettighedsbeskyttede mailmeddelelse, når du har eksporteret den.

- På nuværende tidspunkt omfatter dekrypteringsfunktionen, når du eksporterer søgeresultater, ikke krypteret indhold fra SharePoint og OneDrive for Business websteder. Der ydes dog snart support til dokumenter, der er krypteret med Microsofts krypteringsteknologier og gemt i SharePoint Online og OneDrive for Business.

- Hvis du har brug for at forhindre nogen i at dekryptere RMS-beskyttende meddelelser og krypterede vedhæftede filer, skal du oprette en brugerdefineret rollegruppe (ved at kopiere den indbyggede rollegruppe eDiscovery Manager) og derefter fjerne rollen RMS Dekrypter administration fra den brugerdefinerede rollegruppe. Tilføj derefter den person, du ikke vil dekryptere meddelelser som medlem af den brugerdefinerede rollegruppe.
  
### <a name="filenames-of-exported-items"></a>Filnavne på eksporterede elementer
  
- Der er en grænse på 260 tegn (pålagt af operativsystemet) for det fulde stinavn for mails og webstedsdokumenter, der eksporteres til din lokale computer. Det fulde stinavn for eksporterede elementer omfatter elementets oprindelige placering og mappeplaceringen på den lokale computer, hvor søgeresultaterne downloades til. Hvis du f.eks. angiver, at søgeresultaterne skal downloades til i værktøjet eDiscovery-eksport  `C:\Users\Admin\Desktop\SearchResults` , vil det fulde stinavn for et downloadet mailelement være  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`.

- Hvis grænsen på 260 tegn overskrides, afkortes det fulde stinavn for et element på baggrund af følgende:

  - Hvis det fulde stinavn er længere end 260 tegn, forkortes filnavnet for at komme under grænsen. Bemærk, at det afkortede filnavn (undtagen filtypenavnet) ikke er mindre end otte tegn.

  - Hvis det fulde stinavn stadig er for langt, efter filnavnet er blevet forkortet, flyttes elementet fra den aktuelle placering til den overordnede mappe. Hvis stinavnet stadig er for langt, gentages processen: Forkort filnavnet, og flyt om nødvendigt igen til den overordnede mappe. Denne proces gentages, indtil det fulde stinavn er under grænsen på 260 tegn.

  - Hvis der allerede findes et afkortet fulde stinavn, føjes der et versionsnummer til slutningen af filnavnet. f.eks. `statusmessage(2).msg`.

    Hvis du vil afhjælpe dette problem, kan du overveje at downloade søgeresultater til en placering med et kort stinavn. Hvis du f.eks. henter søgeresultater til en mappe med navnet  `C:\Results` , føjes der færre tegn til stinavnene på eksporterede elementer end at hente dem til en mappe med navnet  `C:\Users\Admin\Desktop\Results`.

- Når du eksporterer webstedsdokumenter, er det også muligt, at et dokuments oprindelige filnavn ændres. Dette sker specifikt for dokumenter, der er blevet slettet fra et SharePoint- eller OneDrive for Business websted, der er sat i venteposition. Når et dokument på et websted, der er i venteposition, slettes, flyttes det slettede dokument automatisk til biblioteket bevarelsesposition for webstedet (som blev oprettet, da webstedet blev sat i venteposition). Når det slettede dokument flyttes til biblioteket bevarelsesposition, føjes et tilfældigt genereret og entydigt id til dokumentets oprindelige filnavn. Hvis filnavnet for et dokument f.eks. er  `FY2017Budget.xlsx` , og dokumentet senere slettes og flyttes til biblioteket bevarelsesposition, ændres filnavnet på det dokument, der flyttes til biblioteket Bevarelses venteposition, til f.eks  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`. . Hvis et dokument i biblioteket bevarelsesventeposition svarer til forespørgslen i en indholdssøgning, og du eksporterer resultaterne af søgningen, har den eksporterede fil det ændrede filnavn. i dette eksempel vil filnavnet på det eksporterede dokument være  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`.

    Når et dokument på et websted, der er i venteposition, ændres (og versionsstyring for dokumentbiblioteket på webstedet er aktiveret), oprettes der automatisk en kopi af filen i biblioteket bevarelses venteposition. I dette tilfælde føjes et tilfældigt genereret og entydigt id også til filnavnet på det dokument, der er kopieret til biblioteket Bevarelse af venteposition.

    Årsagen til, at filnavne på dokumenter, der flyttes eller kopieres til biblioteket for bevarelse af venteposition, er for at forhindre modstridende filnavne. Du kan finde flere oplysninger om, hvordan du placerer en venteposition på websteder og biblioteket Bevarelsesventeposition, under [Oversigt over lokal venteposition i SharePoint Server 2016](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95).

### <a name="miscellaneous"></a>Diverse
  
- Når du downloader søgeresultater ved hjælp af eDiscovery-eksportværktøjet, er det muligt, at du får vist følgende fejl: `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` Dette er en forbigående fejl, som typisk forekommer på Azure Storage-placeringen. Du kan løse problemet ved at prøve at [hente søgeresultaterne](#step-2-download-the-search-results) igen, hvilket genstarter eDiscovery-eksportværktøjet.

- Alle søgeresultater og eksportrapporter er inkluderet i en mappe, der har samme navn som indholdssøgningen. De mails, der blev eksporteret, er placeret i en mappe med navnet **Exchange**. Dokumenter er placeret i en mappe med navnet **SharePoint**.

- Filsystemets metadata for dokumenter på SharePoint- og OneDrive for Business-websteder vedligeholdes, når dokumenter eksporteres til din lokale computer. Det betyder, at dokumentegenskaber, f.eks. oprettede og senest ændrede datoer, ikke ændres, når dokumenter eksporteres.

- Hvis søgeresultaterne indeholder et listeelement fra SharePoint, der svarer til søgeforespørgslen, eksporteres alle rækker på listen ud over det element, der svarer til søgeforespørgslen og eventuelle vedhæftede filer på listen. Årsagen til denne funktionsmåde er at angive en kontekst for listeelementer, der returneres i søgeresultaterne. De ekstra listeelementer og vedhæftede filer kan medføre, at antallet af eksporterede elementer er anderledes end det oprindelige estimat af søgeresultater.
