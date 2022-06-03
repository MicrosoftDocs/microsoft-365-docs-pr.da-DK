---
title: Fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på Linux
description: Foretag fejlfinding af problemer med ydeevnen i Microsoft Defender for Endpoint på Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, ydeevne
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
ms.openlocfilehash: 3452f36068facc92885047184f7e00828f569cbc
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873000"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Dette dokument indeholder instruktioner om, hvordan du begrænser ydeevneproblemer, der er relateret til Defender for Endpoint på Linux, ved hjælp af de tilgængelige diagnosticeringsværktøjer for at kunne forstå og afhjælpe den eksisterende ressourcemangel og de processer, der gør systemet til sådanne situationer. Problemer med ydeevnen skyldes hovedsageligt flaskehalse i et eller flere delsystemer til hardware, afhængigt af ressourceudnyttelsens profil i systemet. Nogle gange er programmer følsomme over for disk-I/O-ressourcer og kan have brug for mere CPU-kapacitet, og nogle gange er nogle konfigurationer ikke bæredygtige, og de kan udløse for mange nye processer og åbne for mange filbeskrivelser.

Afhængigt af de programmer, du kører, og dine enhedsegenskaber, kan du opleve en ikke-optimal ydeevne, når du kører Defender for Endpoint på Linux. Især programmer eller systemprocesser, der har adgang til mange ressourcer, f.eks. CPU, disk og hukommelse over et kort tidsrum, kan medføre problemer med ydeevnen i Defender for Endpoint på Linux.

> [!WARNING]
> Før du starter, **skal du sørge for, at andre sikkerhedsprodukter ikke kører på enheden i øjeblikket**. Flere sikkerhedsprodukter kan være i konflikt med og påvirke værtens ydeevne.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>Fejlfinding af problemer med ydeevnen ved hjælp af statistik for beskyttelse i realtid

**Gælder for:**
- Kun problemer med ydeevnen, der er relateret til AV

Realtidsbeskyttelse (RTP) er en funktion i Defender for Endpoint på Linux, der løbende overvåger og beskytter din enhed mod trusler. Den består af fil- og procesovervågning og andre heuristik.

Følgende trin kan bruges til at foretage fejlfinding og afhjælpe disse problemer:

1. Deaktiver beskyttelse i realtid ved hjælp af en af følgende metoder, og se, om ydeevnen forbedres. Denne fremgangsmåde hjælper med at indsnævre, om Defender for Endpoint på Linux bidrager til problemerne med ydeevnen.

    Hvis enheden ikke administreres af din organisation, kan beskyttelse i realtid deaktiveres fra kommandolinjen:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    Hvis enheden administreres af din organisation, kan beskyttelse i realtid deaktiveres af administratoren ved hjælp af vejledningen i [Angiv indstillinger for Defender for Endpoint på Linux](linux-preferences.md).

    > [!NOTE]
    > Hvis problemet med ydeevnen fortsætter, mens beskyttelse i realtid er slået fra, kan problemet skyldes komponenten slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). I dette tilfælde skal du følge trinnene i afsnittet **Foretag fejlfinding af problemer med ydeevnen ved hjælp af Microsoft Defender for Endpoint Klientanalyse** i denne artikel.

2. Hvis du vil finde de programmer, der udløser flest scanninger, kan du bruge statistikker i realtid, der indsamles af Defender for Endpoint på Linux.

    > [!NOTE]
    > Denne funktion er tilgængelig i version 100.90.70 eller nyere.

    Denne funktion er som standard aktiveret på kanalerne `Dogfood` og `InsiderFast` . Hvis du bruger en anden opdateringskanal, kan denne funktion aktiveres fra kommandolinjen:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    Denne funktion kræver, at beskyttelse i realtid er aktiveret. Kør følgende kommando for at kontrollere status for beskyttelse i realtid:

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

    Hvis du vil indsamle aktuelle statistikker, skal du køre:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > Brug ```--output json``` (bemærk dobbelt tankestregen) sikrer, at outputformatet er klar til fortolkning.

    Outputtet af denne kommando viser alle processer og deres tilknyttede scanningsaktivitet.

3. Download Python-eksempelparser **high_cpu_parser.py** på dit Linux-system ved hjælp af kommandoen:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Outputtet af denne kommando skal ligne følgende:


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

      Ovenstående output er en liste over de største bidragydere til problemer med ydeevnen. Den første kolonne er proces-id'et (PID), den anden kolonne er procesnavnet, og den sidste kolonne er antallet af scannede filer sorteret efter indvirkning.
    Outputtet af kommandoen vil f.eks. være noget i stil med nedenstående: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool    1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd     407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Hvis du vil forbedre ydeevnen for Defender for Endpoint på Linux, skal du finde den med det højeste tal under `Total files scanned` rækken og tilføje en udeladelse for den. Du kan finde flere oplysninger under [Konfigurer og valider udeladelser for Defender for Endpoint på Linux](linux-exclusions.md).

    > [!NOTE]
    > Programmet gemmer statistikker i hukommelsen og holder kun styr på filaktivitet, siden det blev startet, og beskyttelse i realtid blev aktiveret. Processer, der blev startet før eller i perioder, hvor beskyttelse i realtid var slået fra, tælles ikke med. Derudover tælles kun hændelser, der udløste scanninger.

5. Konfigurer Microsoft Defender for Endpoint på Linux med udeladelser for de processer eller diskplaceringer, der bidrager til problemer med ydeevnen, og genaktiver beskyttelse i realtid.

    Du kan finde flere oplysninger under [Konfigurer og valider udeladelser for Microsoft Defender for Endpoint på Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>Foretag fejlfinding af problemer med ydeevnen ved hjælp af Microsoft Defender for Endpoint Klientanalyse

**Gælder for:**
- Problemer med ydeevnen for alle tilgængelige Defender for Slutpunkt-komponenter, f.eks. AV og Slutpunktsregistrering og -svar  

MDECA (Microsoft Defender for Endpoint Client Analyzer) kan indsamle sporings-, logge- og diagnosticeringsoplysninger for at foretage fejlfinding af problemer med ydeevnen på [onboardede enheder](/microsoft-365/security/defender-endpoint/onboard-configure) på Linux.

> [!NOTE]
> Værktøjet Microsoft Defender for Endpoint Client Analyzer bruges jævnligt af Microsoft Customer Support Services (CSS) til at indsamle oplysninger, f.eks. (men ikke begrænset til) IP-adresser, pc-navne, der kan hjælpe med fejlfinding af problemer, du kan opleve med Microsoft Defender for Endpoint. Du kan få flere oplysninger om vores erklæring om beskyttelse [af personlige oplysninger under Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>Krav

- Klientanalysen kan køre på understøttede distros af [Linux](microsoft-defender-endpoint-linux.md#system-requirements) enten før eller efter onboarding til Microsoft Defender for Endpoint.
- Download klientanalysen til Linux fra den seneste prøveversion, der kan downloades her: <https://aka.ms/XMDEClientAnalyzer>
- Hvis enheden er bag en proxy, kan du blot overføre proxyserveren som en miljøvariabel til mde_support_tool.sh-scriptet. For eksempel: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>Kør klientanalysen på Linux

Åbn en terminal eller SSH på den relevante computer, og kør følgende kommandoer:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. Kør som ikke-rodanvendelse for at installere de påkrævede pip- og lxml-komponenter: `./mde_support_tool.sh`
6. Sådan indsamles den faktiske diagnosticeringspakke, og resultatarkivfilen køres igen som rod: `./mde_support_tool.sh -d` Eksempel:

   ![Billede af eksempel på kommandolinje.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - Analysen kræver 'lxml' for at producere resultatoutputtet. Hvis den ikke er installeret, forsøger analysefunktionen at hente den fra det officielle lager til Python-pakker nedenfor: <https://pypi.org/search/?q=lxml>
> 
> - Desuden kræver værktøjet i øjeblikket, at Python version 3 eller nyere er installeret.
>
> - Hvis du kører på en computer, der ikke kan bruge Python 3 eller hente lxml-komponenten, kan du downloade en binær version af analysefunktionen, der ikke har nogen af kravene: [Binær XMDE-klientanalyse](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>Yderligere hjælp til syntaks:

**-h** \# Hjælp<br>
\# Vis Hjælp-meddelelse

**Ydeevne** \# Ydeevne<br>
\# Indsamler omfattende sporing til analyse af et problem med ydeevnen, der kan genskabes efter behov. Bruges `--length=<seconds>` til at angive varigheden af benchmarket.

**-o** \# Output<br>
\# Angiv destinationsstien til resultatfilen

**-nz** \# No-Zip<br>
\# Hvis den er angivet, oprettes der en mappe i stedet for en arkivfil, der oprettes.

**-f** \# Kraft<br>
\# Overskriv, hvis der allerede findes output i destinationsstien

### <a name="result-package-contents"></a>Indhold af resultatpakke

- report.html

  Beskrivelse: Den primære HTML-outputfil, der indeholder de resultater og den vejledning, som analysescriptet, der kører på computeren, kan producere.

- mde_diagnostic.zip

  Beskrivelse: Samme diagnosticeringsoutput, der genereres, når der køres *oprettelse af mdatp-diagnosticering* på [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Beskrivelse: XML-output, der genereres under kørsel, og som bruges til at oprette HTML-rapportfilen.

- Processes_information.txt

  Beskrivelse: Indeholder oplysninger om de kørende Microsoft Defender for Endpoint relaterede processer på systemet.

- Log.txt

  Beskrivelse: Indeholder de samme logmeddelelser, der er skrevet på skærmen under dataindsamlingen.

- Health.txt

  Beskrivelse: Det samme grundlæggende tilstandsoutput, der vises, når du kører *mdatp-tilstandskommandoen* .

- Events.xml

  Beskrivelse: Yderligere XML-fil, der bruges af analysefunktionen, når HTML-rapporten bygges.

- Audited_info.txt

  Beskrivelse: oplysninger om overvåget tjeneste og relaterede komponenter til [Linux](/microsoft-365/security/defender-endpoint/linux-resources) OS

- perf_benchmark.tar.gz

  Beskrivelse: Testrapporter for ydeevne. Du kan kun se dette, hvis du bruger parameteren performance.

> [!NOTE]
> Hvis ydeevnen fortsætter, når du har fulgt ovenstående trin, skal du kontakte kundesupport for at få yderligere instruktioner og afhjælpning.



## <a name="see-also"></a>Se også

- [Undersøg agentens tilstandsproblemer](health-status.md)
