---
title: Fejlfinding af problemer med ydeevnen
description: Foretag fejlfinding af højt CPU-forbrug i forbindelse med tjenesten til beskyttelse i realtid i Microsoft Defender for Endpoint.
keywords: fejlfinding, ydeevne, høj CPU-udnyttelse, højt CPU-forbrug, fejl, rettelse, opdateringsoverholdelse, oms, skærm, rapport, Microsoft Defender Antivirus
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
ms.openlocfilehash: dd89a2cf6d6a8cd355258376b93ca12c37ad501f
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788672"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Fejlfinding af problemer med ydeevnen i forbindelse med beskyttelse i realtid


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Hvis dit system har et højt CPU-forbrug eller ydeevneproblemer, der er relateret til beskyttelsestjenesten i realtid i Microsoft Defender for Endpoint, kan du indsende en anmodning til Microsoft Support. Følg trinnene i [Indsaml Microsoft Defender Antivirus diagnosticeringsdata](collect-diagnostic-data.md).

Som administrator kan du også selv foretage fejlfinding af disse problemer.

Først kan det være en god idé at kontrollere, om problemet skyldes en anden software. Læs [Spørg forhandleren om antivirusudeladelser](#check-with-vendor-for-antivirus-exclusions).

Ellers kan du identificere, hvilken software der er relateret til det identificerede problem med ydeevnen, ved at følge trinnene i [Analysér Microsoft-beskyttelsesloggen](#analyze-the-microsoft-protection-log).

Du kan også angive yderligere logge til din indsendelse til Microsoft Support ved at følge trinnene i:

- [Hent proceslogge ved hjælp af Procesovervågning](#capture-process-logs-using-process-monitor)
- [Hent ydelseslogge ved hjælp af Windows Ydeevneoptager](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Kontakt forhandleren for at få antivirusudeladelser

Hvis du nemt kan identificere den software, der påvirker systemets ydeevne, skal du gå til softwareleverandørens videnbase eller supportcenter. Søg, hvis de har anbefalinger om antivirusudeladelser. Hvis leverandørens websted ikke har dem, kan du åbne en supportanmodning sammen med vedkommende og bede vedkommende om at publicere en.

Vi anbefaler, at softwareleverandører følger de forskellige retningslinjer i [Partnering med branchen for at minimere falske positiver](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). Leverandøren kan indsende sin software via [Microsoft Sikkerhedsviden-portalen](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>Analysér Microsoft Protection Log

I **MPLog-xxxxxxxx-xxxxxx.log** kan du finde oplysninger om den anslåede påvirkning af ydeevnen for kørsel af software som *EstimatedImpact*:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Feltnavn|Beskrivelse|
|---|---|
|ProcessImageName|Behandl billednavn|
|TotalTime|Den samlede varighed i millisekunder, der er brugt på scanninger af filer, som denne proces bruger|
|Tælle|Antallet af scannede filer, som denne proces tilgås|
|Maks. tid|Varigheden i millisekunder i den længstvarende enkelte scanning af en fil, der tilgås af denne proces|
|MaxTimeFile|Stien til den fil, der blev åbnet af denne proces, hvor den længste scanning af `MaxTime` varigheden blev registreret|
|Anslået effekt|Den procentdel af tid, der er brugt på scanninger af filer, som denne proces tilgås, ud af den periode, hvor denne proces oplevede scanningsaktivitet|
|

Hvis påvirkningen af ydeevnen er høj, kan du prøve at føje processen til sti-/procesudeladelser ved at følge trinnene i [Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger](collect-diagnostic-data.md).

Hvis det forrige trin ikke løser problemet, kan du indsamle flere oplysninger via [Procesovervågning](#capture-process-logs-using-process-monitor) eller [Windows Performance Recorder](#capture-performance-logs-using-windows-performance-recorder) i følgende afsnit.

## <a name="capture-process-logs-using-process-monitor"></a>Hent proceslogge ved hjælp af Procesovervågning

Procesovervågning (ProcMon) er et avanceret overvågningsværktøj, der kan vise processer i realtid. Du kan bruge dette til at registrere problemet med ydeevnen, efterhånden som det opstår.

1. Download [Process Monitor v3.60](/sysinternals/downloads/procmon) til en mappe som `C:\temp`.

2. Sådan fjernes filens webmærke:
    1. Højreklik **ProcessMonitor.zip** , og vælg **Egenskaber**.
    1. Søg efter *Sikkerhed* under fanen *Generelt*.
    1. Markér afkrydsningsfeltet ud for **Fjern blokering**.
    1. Vælg **Anvend**.

    :::image type="content" source="images/procmon-motw.png" alt-text="Siden Fjern MOTW" lightbox="images/procmon-motw.png":::

3. Pak filen ud, `C:\temp` så mappestien bliver `C:\temp\ProcessMonitor`.

4. Kopiér **ProcMon.exe** til den Windows klient eller Windows server, du foretager fejlfinding af.

5. Før du kører ProcMon, skal du kontrollere, at alle andre programmer, der ikke er relateret til problemet med højt CPU-forbrug, er lukket. Hvis du gør dette, minimeres antallet af processer, der skal kontrolleres.

6. Du kan starte ProcMon på to måder.
    1. Højreklik på **ProcMon.exe** , og vælg **Kør som administrator**.

        Da logføring starter automatisk, skal du vælge forstørrelsesglasikonet for at stoppe den aktuelle optagelse eller bruge tastaturgenvejen **Ctrl+E**.

        :::image type="content" source="images/procmon-magglass.png" alt-text="Ikonet for forstørrelsesglasset" lightbox="images/procmon-magglass.png":::

        Hvis du vil kontrollere, at du har stoppet hentningen, skal du kontrollere, om forstørrelsesglasikonet nu vises med et rødt X.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="Den røde skråstreg" lightbox="images/procmon-magglass-stop.png":::

        Derefter skal du vælge viskelæderikonet for at rydde den tidligere hentning.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="Ikonet Ryd" lightbox="images/procmon-eraser-clear.png":::

        Eller brug tastaturgenvejen **Ctrl+X**.

    2. Den anden måde er at køre **kommandolinjen** som administrator og derefter køre fra stien Procesovervågning:

       :::image type="content" source="images/cmd-procmon.png" alt-text="Cmd-procedure" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > Gør vinduet ProcMon så lille som muligt, når du henter data, så du nemt kan starte og stoppe sporingen.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="Den side, der viser en minimer Procmon" lightbox="images/procmon-minimize.png":::

7. Når du har fulgt en af procedurerne i trin 6, får du derefter vist en indstilling for angivelse af filtre. Vælg **OK**. Du kan altid filtrere resultaterne, når hentningen er fuldført.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="Den side, hvor System Exclude vælges som procesnavn til filtrering" lightbox="images/procmon-filter-options.png":::

8. Hvis du vil starte hentningen, skal du vælge forstørrelsesglasikonet igen.

9. Genskab problemet.

    > [!TIP]
    > Vent på, at problemet gengives fuldt ud, og notér derefter tidsstemplet, da sporingen startede.

10. Når du har to til fire minutters procesaktivitet under den høje CPU-forbrugstilstand, skal du stoppe hentningen ved at vælge forstørrelsesglasikonet.

11. Hvis du vil gemme hentningen med et entydigt navn og med .pml-formatet, skal du vælge **Filer** og derefter vælge **Gem...**. Sørg for at vælge alternativknapperne **Alle hændelser** og **PML (Native Process Monitor Format).**

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="Siden Med indstillinger for lagring" lightbox="images/procmon-savesettings1.png":::

12. Hvis du vil have bedre sporing, skal du ændre standardstien fra `C:\temp\ProcessMonitor\LogFile.PML` til `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` hvor:
    - `%ComputerName%` er enhedsnavnet
    - `MMDDYEAR` er måned, dag og år
    - `Repro_of_issue` er navnet på det problem, du forsøger at genskabe

    > [!TIP]
    > Hvis du har et fungerende system, kan det være en god idé at få en eksempellog til sammenligning.

13. Zip .pml-filen, og send den til Microsoft Support.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Hent ydelseslogge ved hjælp af Windows Ydeevneoptager

Du kan bruge Windows WPR (Performance Recorder) til at inkludere yderligere oplysninger i din indsendelse til Microsoft Support. WPR er et effektivt optagelsesværktøj, der opretter Event Tracing til Windows optagelser.

WPR er en del af Windows Assessment and Deployment Kit (Windows ADK) og kan downloades fra [Download og installere Windows ADK](/windows-hardware/get-started/adk-install). Du kan også downloade den som en del af Windows 10 Software Development Kit på [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

Du kan bruge WPR-brugergrænsefladen ved at følge trinnene i [Hent ydelseslogge ved hjælp af brugergrænsefladen for WPR](#capture-performance-logs-using-the-wpr-ui).

Du kan også bruge kommandolinjeværktøjet *wpr.exe*, som er tilgængeligt i Windows 8 og nyere versioner, ved at følge trinnene i [Registrer ydelseslogge ved hjælp af kommandolinjegrænsefladen for WPR](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>Hent ydelseslogge ved hjælp af WPR-brugergrænsefladen

> [!TIP]
> Hvis flere enheder oplever dette problem, skal du bruge den, der har mest RAM.

1. Download og installér WPR.

2. Højreklik *under Windows Kits* **Windows Performance Recorder**.

   :::image type="content" source="images/wpr-01.png" alt-text="Menuen Start" lightbox="images/wpr-01.png":::

    Vælg **Mere**. Vælg **Kør som administrator**.

3. Når dialogboksen Brugerkontokontrol vises, skal du vælge **Ja**.

   :::image type="content" source="images/wpt-yes.png" alt-text="UAC-siden" lightbox="images/wpt-yes.png":::

4. Download derefter [Microsoft Defender for Endpoint analyseprofilen](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp), og gem som `MDAV.wprp` i en mappe som .`C:\temp`

5. Vælg **Flere indstillinger** i dialogboksen WPR.

   :::image type="content" source="images/wpr-03.png" alt-text="Den side, hvor du kan vælge flere indstillinger" lightbox="images/wpr-03.png":::


6. Vælg **Tilføj profiler...** , og gå til stien `MDAV.wprp` til filen.

7. Derefter får du vist en ny profil, der er angivet under *Brugerdefinerede målinger* med navnet *Microsoft Defender for Endpoint analyse* under den.

   :::image type="content" source="images/wpr-infile.png" alt-text="Filen i" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > Hvis din Windows Server har 64 GB RAM eller mere, skal du bruge den brugerdefinerede måling `Microsoft Defender for Endpoint analysis for large servers` i stedet for `Microsoft Defender for Endpoint analysis`. Ellers kan dit system forbruge en stor mængde hukommelse eller buffere, der ikke er sideopdelt, hvilket kan medføre ustabile systemer. Du kan vælge, hvilke profiler der skal tilføjes, ved at udvide **Ressourceanalyse**.
    Denne brugerdefinerede profil giver den nødvendige kontekst til dybdegående ydeevneanalyse.

8. Sådan bruger du den brugerdefinerede måling Microsoft Defender for Endpoint detaljeret analyseprofil i brugergrænsefladen for WPR:

    1. Sørg for, at der ikke er valgt nogen profiler under grupperne *Første niveau*, *Ressourceanalyse* og *Scenarieanalyse* .
    2. Vælg **Brugerdefinerede målinger**.
    3. Vælg **Microsoft Defender for Endpoint analyse**.
    4. Vælg **Detaljeret** under *detaljeniveau* .
    5. Vælg **Fil** eller **hukommelse** under Logføringstilstand.

    > [!IMPORTANT]
    > Du skal vælge *Fil* for at bruge fillogføringstilstanden, hvis problemet med ydeevnen kan genskabes direkte af brugeren. De fleste problemer falder ind under denne kategori. Men hvis brugeren ikke direkte kan genskabe problemet, men nemt kan bemærke det, når problemet opstår, skal brugeren vælge *Hukommelse* for at bruge hukommelseslogføringstilstanden. Dette sikrer, at sporingsloggen ikke oppuste overdrevent på grund af den lange kørselstid.

9. Nu er du klar til at indsamle data. Afslut alle de programmer, der ikke er relevante for at gengive problemet med ydeevnen. Du kan vælge **Skjul indstillinger** for at holde pladsen optaget af WPR-vinduet.

   :::image type="content" source="images/wpr-08.png" alt-text="Skjul indstillinger" lightbox="images/wpr-08.png":::

    > [!TIP]
    > Prøv at starte sporingen heltalssekunder. For eksempel 01:30:00. Det gør det nemmere at analysere dataene. Prøv også at holde styr på tidsstemplet for præcis, hvornår problemet genskabes.

10. Vælg **Start**.

    :::image type="content" source="images/wpr-09.png" alt-text="Siden Optag systemoplysninger" lightbox="images/wpr-09.png":::

11. Genskab problemet.

    > [!TIP]
    > Bevar dataindsamlingen på højst fem minutter. To til tre minutter er et godt interval, da der indsamles mange data.

12. Vælg **Gem**.

    :::image type="content" source="images/wpr-10.png" alt-text="Indstillingen Gem" lightbox="images/wpr-10.png":::

13. Udfyld **Type i en detaljeret beskrivelse af problemet:** med oplysninger om problemet, og hvordan du genskabede problemet.

    :::image type="content" source="images/wpr-12.png" alt-text="Den rude, du udfylder" lightbox="images/wpr-12.png":::

    1. Vælg **Filnavn:** for at bestemme, hvor sporingsfilen skal gemmes. Som standard gemmes den i `%user%\Documents\WPR Files\`.
    1. Vælg **Gem**.

14. Vent, mens sporingen flettes.

    :::image type="content" source="images/wpr-13.png" alt-text="WPR-indsamlingen af generel sporing" lightbox="images/wpr-13.png":::

15. Når sporingen er gemt, skal du vælge **Åbn mappe**.

    :::image type="content" source="images/wpr-14.png" alt-text="Den side, der viser meddelelsen om, at WPR-sporing er blevet gemt" lightbox="images/wpr-14.png":::

    Medtag både filen og mappen i din indsendelse til Microsoft Support.

    :::image type="content" source="images/wpr-15.png" alt-text="Oplysningerne om filen og mappen" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>Hent ydelseslogge ved hjælp af kommandolinjegrænsefladen for WPR

Kommandolinjeværktøjet *wpr.exe* er en del af operativsystemet, der starter med Windows 8. Sådan indsamler du en WPR-sporing ved hjælp af kommandolinjeværktøjet wpr.exe:

1. Download **[Microsoft Defender for Endpoint analyseprofil](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** for ydeevnesporinger til en fil, der er navngivet `MDAV.wprp` i en lokal mappe, f.eks`C:\traces`. .

2. Højreklik på ikonet **Menuen Start,** og vælg **Windows PowerShell (administrator)** eller **kommandoprompt (administrator)** for at åbne et kommandopromptvindue for administratorer.

3. Når dialogboksen Brugerkontokontrol vises, skal du vælge **Ja**.

4. Kør følgende kommando i prompten med administratorrettigheder for at starte en Microsoft Defender for Endpoint ydeevnesporing:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Hvis din Windows Server har 64 GB eller RAM eller mere, skal du bruge henholdsvis profiler `WDForLargeServers.Light` og `WDForLargeServers.Verbose` i stedet for profiler `WD.Light` og `WD.Verbose`. Ellers kan dit system forbruge en stor mængde hukommelse eller buffere, der ikke er sideopdelt, hvilket kan medføre ustabile systemer.

5. Genskab problemet.

    > [!TIP]
    > Bevar dataindsamlingen til højst fem minutter. Afhængigt af scenariet er to til tre minutter et godt interval, da der indsamles mange data.

6. Kør følgende kommando ved prompten med administratorrettigheder for at stoppe sporingen af ydeevnen, og sørg for at angive oplysninger om problemet, og hvordan du har reproduceret problemet:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. Vent, indtil sporingen er flettet.

8. Medtag både filen og mappen i din indsendelse til Microsoft Support.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Indsaml Microsoft Defender Antivirus diagnosticeringsdata](collect-diagnostic-data.md)
- [Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md)
