---
title: Kør klientanalyse på macOS eller Linux
description: Få mere at vide om, hvordan du kører Microsoft Defender for Endpoint Client Analyzer på macOS eller Linux
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
ms.openlocfilehash: bbd4100466fbfef75363848bc5b89bbb9a769265
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63600944"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>Kør klientanalyse på macOS og Linux


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Kørsel af analyseanalyse gennem scenariet GUI

1. Download [værktøjet XMDE Client Analyzer på](https://aka.ms/XMDEClientAnalyzer) den macOS- eller Linux-computer, du skal undersøge.

   > [!NOTE]
   > Den aktuelle SHA256-hash for "XMDEClientAnalyzer.zip", som downloades fra ovenstående link, er: 'B95E2E21D5A93E0AC88BA401ACB20E5F721727B409D4186147C8D17468185583'.

2. Udtræk indholdet XMDEClientAnalyzer.zip på maskinen.

3. Åbn en terminalsession, skift mappe til den udtrukne placering, og kør:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Hvis scriptet på Linux ikke har tilladelse til at udføre, skal du først køre:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Kørsel af analysatoren ved hjælp af en terminal eller et SSH-scenarie

Åbn en terminal eller SSH på den relevante computer, og kør følgende kommandoer:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Kør som ikke-rodbaseret brug for at installere påkrævede rør og lxml-komponenter: `./mde_support_tool.sh`

4. Hvis du vil indsamle den faktiske diagnosticeringspakke og generere resultatarkivfilen, skal du køre igen som rod: `./mde_support_tool.sh -d`

> [!NOTE]
> - Til Linux kræver analyseeren 'lxml' for at producere resultatet. Hvis det ikke er installeret, forsøger analyseator at hente det fra det officielle lager til python-pakker nedenfor: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Desuden kræver værktøjet i øjeblikket, at Python version 3 eller nyere er installeret.
>
> - Hvis du kører på en computer, der ikke kan bruge Python 3 eller hente lxml-komponenten, kan du downloade en binær baseret version af analyseprogrammet, der ikke har nogen af kravene: [Binær XMDE-klientanalyse](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Hvis din enhed er bag en proxy, kan du blot overføre proxyserveren som en miljøvariabel til scriptet mde_support_tool.sh. For eksempel: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Eksempel:

![Eksempel på kommandolinje.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

Yderligere hjælp til syntaks:

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

## <a name="result-package-contents-on-macos-and-linux"></a>Resultatpakkeindhold på macOS og Linux

- report.html

  Beskrivelse: Den primære HTML-outputfil, der indeholder de fund og den vejledning, som analysescriptet kører på computeren, kan producere.

- mde_diagnostic.zip

  Beskrivelse: Samme diagnostiske output, der genereres, når du *kører mdatp Diagnostic Create* på enten [macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  eller

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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
