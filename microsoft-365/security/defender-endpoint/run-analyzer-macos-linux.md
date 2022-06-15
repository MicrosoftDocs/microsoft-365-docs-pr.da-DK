---
title: Kør klientanalysen på macOS eller Linux
description: Få mere at vide om, hvordan du kører Microsoft Defender for Endpoint-klientanalysen på macOS eller Linux
keywords: klientanalyse, fejlfinding af sensor, analyse, mdeanalyzer, macos, linux, mdeanalyzer
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: a4dd7193bed1a22e3b88e6bc9201f5a15ddcd9eb
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090448"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Kør klientanalysen på macOS og Linux


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Kørsel af analysefunktionen via ET GUI-scenarie

1. Download værktøjet [XMDE-klientanalyse](https://aka.ms/XMDEClientAnalyzer) til den macOS- eller Linux-maskine, du skal undersøge.

   > [!NOTE]
   > Den aktuelle SHA256-hash for 'XMDEClientAnalyzer.zip', der downloades fra ovenstående link, er: 'AFD674A149F139E80F1AE90E36814DAAC08AAD9E8B0DA20CB1D3FA33B9D0D1AD'.

2. Udpak indholdet af XMDEClientAnalyzer.zip på maskinen.

3. Åbn en terminalsession, skift mappe til den udtrukne placering, og kør:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Hvis scriptet ikke har tilladelse til at udføre på Linux, skal du først køre:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Kørsel af analysefunktionen ved hjælp af en terminal eller et SSH-scenarie

Åbn en terminal eller SSH på den relevante computer, og kør følgende kommandoer:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Kør som ikke-rodanvendelse for at installere de påkrævede pip- og lxml-komponenter: `./mde_support_tool.sh`

4. Sådan indsamles den faktiske diagnosticeringspakke, og resultatarkivfilen køres igen som rod: `./mde_support_tool.sh -d`

> [!NOTE]
> - For Linux kræver analysefunktionen 'lxml' for at producere resultatoutputtet. Hvis den ikke er installeret, forsøger analysefunktionen at hente den fra det officielle lager til Python-pakker nedenfor: <https://pypi.org/search/?q=lxml>
> 
> - Desuden kræver værktøjet i øjeblikket, at Python version 3 eller nyere er installeret.
>
> - Hvis du kører på en computer, der ikke kan bruge Python 3 eller hente lxml-komponenten, kan du downloade en binær version af analysefunktionen, der ikke har nogen af kravene: [Binær XMDE-klientanalyse](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Hvis enheden er bag en proxy, kan du blot overføre proxyserveren som en miljøvariabel til mde_support_tool.sh-scriptet. For eksempel: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Eksempel:

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="Kommandolinjeeksempel" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

Yderligere hjælp til syntaks:

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

## <a name="result-package-contents-on-macos-and-linux"></a>Resultatpakkeindhold på macOS og Linux

- report.html

  Beskrivelse: Den primære HTML-outputfil, der indeholder de resultater og den vejledning, som analysescriptet, der kører på computeren, kan producere.

- mde_diagnostic.zip

  Beskrivelse: Samme diagnosticeringsoutput, der genereres, når der køres *oprettelse af mdatp-diagnosticering* på begge [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  Eller

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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
