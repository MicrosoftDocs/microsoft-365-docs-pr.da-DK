---
title: Fejlfinding af problemer med ydeevnen for Microsoft Defender til slutpunkt på Linux
description: Fejlfinding af problemer med ydeevnen i Microsoft Defender til slutpunkt på Linux.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, ydeevne
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 14424f0cdff908fc641d6de1c22d25546473cc13
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592017"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Fejlfinding af problemer med ydeevnen for Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Dette dokument indeholder instruktioner om, hvordan du indsnævrer problemer med ydeevnen i forbindelse med Defender til slutpunkt på Linux ved hjælp af de tilgængelige diagnosticeringsværktøjer for at kunne forstå og afhjælpe den eksisterende ressource mangler og de processer, der gør systemet i sådanne situationer. Problemer med ydeevnen skyldes hovedsageligt flaskehalse i et eller flere hardwaresystemsystemer afhængigt af profilen for ressourceforbruget i systemet. Nogle gange er programmer følsomme over for disk-I/O-ressourcer og har måske brug for mere CPU-kapacitet, og nogle gange er nogle konfigurationer ikke dynamiske, og de kan udløse for mange nye processer og åbne for mange filbeskrivelser.

Afhængigt af de programmer, du kører, og dine enhedsegenskaber kan du opleve en underoptimal ydeevne, når du kører Defender til Slutpunkt på Linux. Især kan programmer eller systemprocesser, der får adgang til mange ressourcer som CPU, disk og hukommelse over en kort periode, føre til problemer med ydeevnen i Defender til slutpunkt på Linux.

> [!WARNING]
> Før du starter, **skal du sørge for, at andre sikkerhedsprodukter ikke kører på enheden i øjeblikket**. Flere sikkerhedsprodukter kan skabe konflikt og påvirke værtsydeevnen.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Fejlfinding af problemer med ydeevnen ved hjælp af statistik for beskyttelse i realtid

**Gælder for:**
- Kun ydelsesproblemer relateret til AV

Beskyttelse i realtid (RTP) er en funktion i Defender til slutpunkt på Linux, som løbende overvåger og beskytter din enhed mod trusler. Den består af fil- og procesovervågning og anden heuristics.

Følgende trin kan bruges til at foretage fejlfinding af og afhjælpe disse problemer:

1. Deaktiver beskyttelse i realtid ved hjælp af en af følgende metoder, og se, om ydeevnen forbedres. Denne fremgangsmåde hjælper med at indskrænke, om Defender til slutpunkt på Linux bidrager til problemer med ydeevnen.

    Hvis din enhed ikke administreres af din organisation, kan beskyttelse i realtid deaktiveres fra kommandolinjen:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Hvis din enhed administreres af din organisation, kan beskyttelse i realtid deaktiveres af din administrator ved hjælp af instruktionerne i Angiv indstillinger [for Defender for Endpoint på Linux](linux-preferences.md).

    > [!NOTE]
    > Hvis ydelsesproblemet fortsætter, mens beskyttelse i realtid er slået fra, kan problemets oprindelse være den slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar)-komponent. I dette tilfælde skal du følge trinnene fra afsnittet Fejlfinding af problemer med ydeevnen ved hjælp **af Microsoft Defender til Endpoint Client Analyzer** i denne artikel.

2. For at finde de programmer, der udløser de fleste scanninger, kan du bruge realtidsstatistik, der er indsamlet af Defender til Slutpunkt på Linux.

    > [!NOTE]
    > Denne funktion er tilgængelig i version 100.90.70 eller nyere.

    Denne funktion er som standard aktiveret på kanalerne `Dogfood` og `InsiderFast` i kanalerne. Hvis du bruger en anden opdateringskanal, kan denne funktion aktiveres fra kommandolinjen:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Denne funktion kræver beskyttelse i realtid for at blive aktiveret. Kør følgende kommando for at kontrollere status for beskyttelse i realtid:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    Kontrollér, at posten `real_time_protection_enabled` er `true`. Ellers skal du køre følgende kommando for at aktivere den:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    For at indsamle aktuel statistik skal du køre:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Ved ```--output json``` at bruge (bemærk den dobbelte streg) sikrer du, at outputformatet er klar til fortolkning.

    Outputtet for denne kommando viser alle processer og deres tilknyttede scanningsaktivitet.

3. På dit Linux-system kan du downloade eksempel på Python parser **high_cpu_parser.py** ved hjælp af kommandoen:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Outputtet for denne kommando skal ligne følgende:


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. Skriv derefter følgende kommandoer:

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      Outputtet fra ovenstående er en liste over de vigtigste bidragydere til problemer med ydeevnen. Den første kolonne er proces-id'et (PID), den anden kolonne er procesnavnet, og den sidste kolonne er antallet af scannede filer, sorteret efter virkning.
    Eksempelvis vil outputtet for kommandoen være noget i den følgende stand: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool     1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd    407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Hvis du vil forbedre ydeevnen for Defender til slutpunkt på Linux, skal du finde den, der har det højeste tal under `Total files scanned` rækken, og tilføje en udeladelse for den. Få mere at vide under [Konfigurer og valider udeladelse af Defender for Endpoint på Linux](linux-exclusions.md).

    > [!NOTE]
    > Programmet lagrer statistik i hukommelsen og holder kun styr på filaktivitet, siden det blev startet, og beskyttelse i realtid blev aktiveret. Processer, der blev startet før eller i perioder, hvor beskyttelse i realtid var slået fra, tælles ikke. Desuden tælles kun hændelser, der udløste scanninger, med.

5. Konfigurer Microsoft Defender til Slutpunkt på Linux med undtagelser for de processer eller diskplaceringer, der bidrager til problemer med ydeevnen, og genaktiver beskyttelse i realtid.

    Du kan finde flere oplysninger under [Konfigurer og valider udeladelser for Microsoft Defender for Endpoint på Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Fejlfinding af problemer med ydeevnen ved hjælp af Microsoft Defender til Endpoint Client Analyzer

**Gælder for:**
- Problemer med ydeevnen for alle tilgængelige Defender til slutpunktskomponenter såsom AV og Slutpunktsregistrering og -svar  

Microsoft Defender for Endpoint Client Analyzer (MDECA) kan indsamle sporinger, logfiler og diagnostiske oplysninger for at foretage fejlfinding af problemer med ydeevnen på [onboardede](/microsoft-365/security/defender-endpoint/onboard-configure) enheder på Linux.

> [!NOTE]
> Værktøjet Microsoft Defender for Endpoint Client Analyzer bruges regelmæssigt af Microsofts kundesupporttjenester (CSS) til at indsamle oplysninger som f.eks. (men ikke begrænset til) IP-adresser, pc-navne, der kan hjælpe med at foretage fejlfinding af problemer med Microsoft Defender til Slutpunkt. Du kan finde flere oplysninger om vores erklæring om beskyttelse af personlige oplysninger [i Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Krav

- Klientanalysen kan køre på understøttede distributions af [Linux](microsoft-defender-endpoint-linux.md#system-requirements) , enten før eller efter onboarding til Microsoft Defender til slutpunkt.
- Download klientanalyse til Linux fra den nyeste prøveversion, der kan downloades her: <https://aka.ms/XMDEClientAnalyzer>
- Hvis din enhed er bag en proxy, kan du blot overføre proxyserveren som en miljøvariabel til scriptet mde_support_tool.sh. For eksempel: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Kør klientanalysen på Linux

Åbn en terminal eller SSH på den relevante computer, og kør følgende kommandoer:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Kør som ikke-rodbaseret brug for at installere påkrævede rør og lxml-komponenter: `./mde_support_tool.sh`
6. For at indsamle den faktiske diagnosticeringspakke og generere resultatarkivfilen skal du køre igen som rod: `./mde_support_tool.sh -d` Eksempel:

   ![Eksempel på kommandolinje.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Analyseanalysen kræver 'lxml' for at producere resultatet. Hvis det ikke er installeret, forsøger analyseator at hente det fra det officielle lager til python-pakker nedenfor: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Desuden kræver værktøjet i øjeblikket, at Python version 3 eller nyere er installeret.
>
> - Hvis du kører på en computer, der ikke kan bruge Python 3 eller hente lxml-komponenten, kan du downloade en binær baseret version af analyseprogrammet, der ikke har nogen af kravene: [Binær XMDE-klientanalyse](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Yderligere hjælp til syntaks:

**-h** \# Hjælp<br>
\# Vis Hjælp-meddelelse

**ydeevne** \# Ydeevne<br>
\# Indsamler omfattende sporing til analyse af et ydelsesproblem, der kan genskabes efter behov. Bruges `--length=<seconds>` til at angive varigheden af benchmarken.

**-o** \# Output<br>
\# Angiv destinationsstien for resultatfilen

**-nz** \# No-Zip<br>
\# Hvis den er indstillet, oprettes der en mappe i stedet for en resulterende arkivfil

**-f** \# Gennemtving<br>
\# Overskrive, hvis der allerede findes output i destinationsstien

### <a name="result-package-contents"></a>Indhold af resultatpakke

- report.html

  Beskrivelse: Den primære HTML-outputfil, der indeholder de fund og den vejledning, som analysescriptet kører på computeren, kan producere.

- mde_diagnostic.zip

  Beskrivelse: Samme diagnostiske output, der genereres, når du *kører mdatp Diagnostic Create* på [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Beskrivelse: XML-output, der genereres under kørsel og bruges til at opbygge HTML-rapportfilen.

- Processes_information.txt

  Beskrivelse: indeholder oplysningerne om de kørende microsoft Defender for Endpoint-relaterede processer på systemet.

- Log.txt

  Beskrivelse: indeholder de samme logfiler, der er skrevet på skærmen under dataindsamlingen.

- Health.txt

  Beskrivelse: Det samme grundlæggende tilstandsoutput, der vises, når du *kører kommandoen mdatp-tilstand* .

- Events.xml

  Beskrivelse: Yderligere XML-fil, der bruges af analysefilen, når HTML-rapporten opbygges.

- Auditd_info.txt

  Beskrivelse: Detaljer om overvåget tjeneste og relaterede komponenter til [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events) OS

- perf_benchmark.tar.gz

  Beskrivelse: Ydeevnetestrapporterne. Du får kun vist dette, hvis du bruger performanceparameteren.

> [!NOTE]
> Hvis problemet med ydeevnen bevares efter at have fulgt ovenstående trin, skal du kontakte kundesupport for yderligere vejledning og afhjælpning.



## <a name="see-also"></a>Se også

- [Undersøg agentens tilstandsproblemer](health-status.md)
