---
title: Fejlfinding af problemer med ydeevnen
description: Fejlfinding af højt CPU-forbrug relateret til beskyttelse i realtid i Microsoft Defender til slutpunkt.
keywords: fejlfinding, ydeevne, høj CPU-udnyttelse, højt CPU-forbrug, fejl, rettelse, overholdelse af regler og standarder, oms, skærm, rapport, Microsoft Defender Antivirus
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
ms.date: 10/19/2021
audience: ITPro
ms.topic: troubleshooting
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 1dfe480f36d99acfdc9dcb36e63d2eed4f22054a
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63595899"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Fejlfinding af problemer med ydeevnen i forbindelse med beskyttelse i realtid


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis dit system har problemer med høj CPU-brug eller ydeevne relateret til beskyttelse i realtid i Microsoft Defender til slutpunkt, kan du sende en anmodning til Microsoft-support. Følg trinnene i [Indsaml Microsoft Defender Antivirus diagnostiske data](collect-diagnostic-data.md).

Som administrator kan du også selv foretage fejlfinding af disse problemer.

Først skal du kontrollere, om problemet skyldes en anden software. Læs [Kontakt leverandøren for at få undtagelser til antivirus.](#check-with-vendor-for-antivirus-exclusions)

Ellers kan du identificere, hvilken software der er relateret til det identificerede ydelsesproblem, ved at følge trinnene i [Analysér Microsoft Protection-logfilen](#analyze-the-microsoft-protection-log).

Du kan også angive yderligere logfiler til din indsendelse til Microsoft support ved at følge trinnene i:

- [Registrere proceslogfiler ved hjælp af Procesovervågning](#capture-process-logs-using-process-monitor)
- [Registrere ydeevnelogger ved hjælp Windows Performance Recorder](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Kontakt leverandøren for at få undtagelser til antivirus

Hvis du uden videre kan identificere den software, der påvirker systemets ydeevne, skal du gå til softwareleverandørens videnbase eller supportcenter. Søg, hvis de har anbefalinger om antivirus udelukkelser. Hvis leverandørens websted ikke har dem, kan du åbne en supportbillet med dem og bede dem om at publicere en.

Vi anbefaler, at softwareleverandører følger de forskellige retningslinjer i [Samarbejde med branchen for at minimere falske positive](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). Leverandøren kan indsende deres software via [Microsoft Sikkerhedsviden portalen](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>Analysér Microsoft Protection-logfilen

I **MPLog-xxxxxxxx-xxxxxx.log** kan du finde oplysninger om den anslåede ydeevnepåvirkning for at køre software som *EstimatedImpact*:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Feltnavn|Beskrivelse|
|---|---|
|ProcessImageName|Navn på procesbillede|
|TotalTime|Den akkumulerede varighed i millisekunder, der bruges i scanninger af filer, der tilgås af denne proces|
|Antal|Antallet af scannede filer, der blev åbnet via denne proces|
|MaxTime|Varigheden i millisekunder i den længste enkelte scanning af en fil, der tilgås af denne proces|
|MaxTimeFile|Stien til den fil, der blev åbnet ved denne proces, hvor den længste varighedsscanning `MaxTime` blev registreret|
|EstimatedImpact|Den procentdel af tiden, der er brugt i scanninger til filer, der tilgås via denne proces, ud af den periode, hvor denne proces oplevede scanningsaktivitet|
|

Hvis påvirkningen af ydeevnen er stor, kan du prøve at føje processen til sti-/procesudetagelserne ved at følge trinnene i Konfigurere og validere udeladelse [for Microsoft Defender Antivirus scanninger](collect-diagnostic-data.md).

Hvis det forrige trin ikke løser problemet, kan du indsamle flere oplysninger via Procesovervågning eller [](#capture-process-logs-using-process-monitor) [Windows Performance Recorder](#capture-performance-logs-using-windows-performance-recorder) i de følgende afsnit.

## <a name="capture-process-logs-using-process-monitor"></a>Registrere proceslogfiler ved hjælp af Procesovervågning

Process Monitor (ProcMon) er et avanceret overvågningsværktøj, der kan vise processer i realtid. Du kan bruge dette til at registrere ydelsesproblemet, efterhånden som det forekommer.

1. Download [Process Monitor v3.60](/sysinternals/downloads/procmon) til en mappe som f.eks `C:\temp`. .

2. Sådan fjerner du filens mærke på internettet:
    1. Højreklik på listen **ProcessMonitor.zip** vælg **Egenskaber**.
    1. Under fanen *Generelt* skal du se efter *Sikkerhed*.
    1. Markér afkrydsningsfeltet ud for **Fjern blokering**.
    1. Vælg **Anvend**.

    ![Fjern MOTW.](images/procmon-motw.png)

3. Udpakke filen, så `C:\temp` mappestien bliver `C:\temp\ProcessMonitor`.

4. **KopiérProcMon.exe** til den Windows klient Windows den server, du foretager fejlfinding af.

5. Før du kører ProcMon, skal du sørge for, at alle andre programmer, der ikke er relateret til problemet med høj CPU-brug, er lukket. Dette minimerer antallet af processer, der skal kontrolleres.

6. Du kan starte ProcMon på to måder.
    1. Højreklik på listen **ProcMon.exe** vælg **Kør som administrator**.

        Da logføring starter automatisk, skal du vælge forstørrelsesglasikonet for at stoppe det aktuelle skærmklip eller bruge **tastaturgenvejen Ctrl+E**.

        ![Forstørrelsesglasikon.](images/procmon-magglass.png)

        Kontrollér, om forstørrelsesglasikonet nu vises med et rødt X, for at bekræfte, at du har stoppet denne optagelse.

        ![rød skråstreg.](images/procmon-magglass-stop.png)

        Vælg derefter viskelæderikonet for at rydde den tidligere optagelse.

        ![ryd ikon.](images/procmon-eraser-clear.png)

        Eller brug tastaturgenvejen **Ctrl+X**.

    2. Den anden måde er at køre **kommandolinjen som** administrator og derefter køre fra stien Procesovervågning:

        ![cmd procmon.](images/cmd-procmon.png)

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > Gør vinduet ProcMon så lille som muligt, når du henter data, så du nemt kan starte og stoppe sporingen.
        >
        > ![Minimer Procmon.](images/procmon-minimize.png)

7. Når du har fulgt en af procedurerne i trin 6, får du derefter vist en indstilling til at angive filtre. Vælg **OK**. Du kan altid filtrere resultaterne, når du er færdig med skærmbilledet.

    ![Filtrering af procesnavn er Systemudeluk.](images/procmon-filter-options.png)

8. Hvis du vil starte hentningerne, skal du vælge forstørrelsesglasikonet igen.

9. Genskab problemet.

    > [!TIP]
    > Vent på, at problemet gengives fuldstændigt, og noter dig tidsstemplet, da sporingen startede.

10. Når du har to til fire minutters procesaktivitet under den høje CPU-brugsbetingelse, kan du stoppe opfangningen ved at vælge forstørrelsesglasikonet.

11. Hvis du vil gemme et billede med et entydigt navn og med .pml-formatet, skal **du vælge Filer** og derefter **vælge Gem...**. Sørg for at vælge alternativknapperne **Alle hændelser** og **PML -format (Native Process Monitor Format).**

    ![gemme indstillinger.](images/procmon-savesettings1.png)

12. Du kan forbedre sporingen ved at ændre standardstien fra `C:\temp\ProcessMonitor\LogFile.PML` sted `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` til sted:
    - `%ComputerName%` er enhedsnavnet
    - `MMDDYEAR` er måned, dag og år
    - `Repro_of_issue` er navnet på det problem, du forsøger at genskabe

    > [!TIP]
    > Hvis du har et fungerende system, kan det være en god ide at få en eksempellog, der kan sammenlignes.

13. Zip .pml-filen, og send den til Microsoft support.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Registrere ydeevnelogger ved hjælp Windows Performance Recorder

Du kan bruge Windows (WPR) til at medtage yderligere oplysninger i din indsendelse til Microsoft support. WPR er et effektivt optagelsesværktøj, der opretter Hændelsessporing Windows optagelser.

WPR er en del af Windows Assessment and Deployment Kit (Windows ADK) og kan downloades fra Download og installere [Windows ADK](/windows-hardware/get-started/adk-install). Du kan også downloade den som en del af Windows 10 Software Development Kit [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

Du kan bruge WPR-brugergrænsefladen ved at følge trinnene i [Registrere ydeevnelogfiler ved hjælp af WPR-brugergrænsefladen](#capture-performance-logs-using-the-wpr-ui).

Du kan også bruge kommandolinjeværktøjet *tilwpr.exe*, der er tilgængeligt i Windows 8 og nyere versioner ved at følge trinnene i Registrere ydeevnelogfiler ved hjælp af [WPR CLI](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>Registrere ydeevnelogfiler ved hjælp af WPR-brugergrænsefladen

> [!TIP]
> Hvis flere enheder oplever dette problem, skal du bruge den, der har mest RAM.

1. Download og installér WPR.

2. Under *Windows-pakker* skal du højreklikke **Windows Performance Recorder**.

    ![menuen Start.](images/wpr-01.png)

    Vælg **Flere**. Vælg **Kør som administrator**.

3. Når dialogboksen Kontrol af brugerkonti vises, skal du vælge **Ja**.

    ![UAC.](images/wpt-yes.png)

4. Derefter skal du downloade [analyseprofilen microsoft Defender for Endpoint](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) og gemme som `MDAV.wprp` i en mappe som f.eks `C:\temp`. .

5. I dialogboksen WPR skal du vælge **Flere indstillinger**.

    ![Vælg flere indstillinger.](images/wpr-03.png)

6. Vælg **Tilføj profiler ...** og gå til stien til `MDAV.wprp` filen.

7. Derefter bør du kunne se et nyt profilsæt under *Brugerdefinerede mål* med navnet *Microsoft Defender til slutpunktsanalyse* nedenunder.

    ![i filen.](images/wpr-infile.png)

    > [!WARNING]
    > Hvis din Windows Server har 64 GB RAM eller mere, skal du bruge det brugerdefinerede mål `Microsoft Defender for Endpoint analysis for large servers` i stedet for `Microsoft Defender for Endpoint analysis`. Ellers kan systemet forbruge en stor mængde ikke-sidet puljehukommelse eller buffere, hvilket kan føre til systemne ustabil. Du kan vælge, hvilke profiler der skal tilføjes, ved at **udvide Ressourceanalyse**.
    Denne brugerdefinerede profil giver den nødvendige kontekst til dybdegående ydeevneanalyse.

8. Sådan bruges den brugerdefinerede måling Microsoft Defender til slutpunkt detaljeret analyseprofil i WPR-brugergrænsefladen:

    1. Sørg for, at der ikke er valgt nogen profiler under *grupperne Triage* på første niveau, *Ressourceanalyse* *og Scenarieanalyse* .
    2. Vælg **Brugerdefinerede mål**.
    3. Vælg **Microsoft Defender til slutpunktsanalyse**.
    4. Vælg **Detaljeret** under *Detaljeniveau* .
    5. Vælg **Filer eller** **Hukommelse** under Logføringstilstand.

    > [!IMPORTANT]
    > Du skal vælge *Filer* for at bruge fillogføringstilstand, hvis ydelsesproblemet kan genskabes direkte af brugeren. De fleste problemer falder inden for denne kategori. Men hvis brugeren ikke kan genskabe problemet direkte, men nemt kan lægge mærke til det, når problemet opstår, skal brugeren vælge  Hukommelse for at bruge hukommelseslogføringstilstanden. Dette sikrer, at sporingsloggen ikke vil fylde for meget på grund af den lange kørselstid.

9. Nu er du klar til at indsamle data. Afslut alle de programmer, der ikke er relevante for at genskabe ydelsesproblemet. Du kan vælge **Skjul indstillinger** for at holde pladsen optaget af WPR-vinduet lille.

    ![Skjul indstillinger.](images/wpr-08.png)

    > [!TIP]
    > Prøv at starte sporingen ved et helt antal sekunder. Eksempel: 01:30:00. Dette gør det nemmere at analysere dataene. Prøv også at holde styr på tidsstemplet på netop det tidspunkt, hvor problemet genskabes.

10. Vælg **Start**.

    ![Vælg starten af sporingen.](images/wpr-09.png)

11. Genskab problemet.

    > [!TIP]
    > Hold dataindsamlingen på højst fem minutter. To til tre minutter er et godt område, da der indsamles mange data.

12. Vælg **Gem**.

    ![Vælg Gem.](images/wpr-10.png)

13. Udfyld Skriv **en detaljeret beskrivelse af problemet: med oplysninger** om problemet, og hvordan du har genskabet problemet.

    ![Udfyld detaljer.](images/wpr-12.png)

    1. Vælg **Filnavn: for** at bestemme, hvor din sporingsfil skal gemmes. Som standard gemmes den på `%user%\Documents\WPR Files\`.
    1. Vælg **Gem**.

14. Vent, mens sporingen flettes.

    ![WPR indsamler generel sporing.](images/wpr-13.png)

15. Når sporingen er gemt, skal du **vælge Åbn mappe**.

    ![WPR-sporing gemt.](images/wpr-14.png)

    Medtag både filen og mappen i din indsendelse til Microsoft Support.

    ![Fil og mappe.](images/wpr-15.png)

### <a name="capture-performance-logs-using-the-wpr-cli"></a>Registrere ydeevnelogfiler ved hjælp af WPR CLI

Kommandolinjeværktøjet til *wpr.exe* er en del af operativsystemet, der starter Windows 8. Sådan indsamler du en WPR-sporing ved hjælp af kommandolinjeværktøjet wpr.exe:

1. Download **[Microsoft Defender for Endpoint-analyseprofilen](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** for ydeevnespor til en fil, der er navngivet `MDAV.wprp` i en lokal mappe, f.eks `C:\traces`. .

2. Højreklik på ikonet **for menuen Start**, og vælg **Windows PowerShell (administrator)** eller Kommandoprompt **(administrator)** for at åbne et vindue med en administratorkommandoprompt.

3. Når dialogboksen Kontrol af brugerkonti vises, skal du vælge **Ja**.

4. Ved den hævede prompt skal du køre følgende kommando for at starte en Microsoft Defender for Endpoint-ydeevnesporing:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Hvis din Windows Server har 64 GB eller RAM eller mere, `WDForLargeServers.Light` `WDForLargeServers.Verbose` skal du bruge profiler og i `WD.Light` stedet for `WD.Verbose`profiler og , henholdsvis. Ellers kan systemet forbruge en stor mængde ikke-sidet puljehukommelse eller buffere, hvilket kan føre til systemne ustabil.

5. Genskab problemet.

    > [!TIP]
    > Opsæt dataindsamlingen til højst fem minutter. Afhængigt af scenariet er to til tre minutter et godt område, da der indsamles mange data.

6. Ved den hævede prompt skal du køre følgende kommando for at stoppe ydeevnesporingen og sørge for at angive oplysninger om problemet, og hvordan du genskabede problemet:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. Vent, indtil sporingen flettes.

8. Medtag både filen og mappen i din indsendelse til Microsoft support.

## <a name="see-also"></a>Se også

- [Indsaml Microsoft Defender Antivirus diagnostiske data](collect-diagnostic-data.md)
- [Konfigurere og validere udeladelse for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
