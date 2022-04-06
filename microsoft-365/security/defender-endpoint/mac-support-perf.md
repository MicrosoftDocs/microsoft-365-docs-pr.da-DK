---
title: Fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på macOS
description: Fejlfinding af problemer med ydeevnen Microsoft Defender for Endpoint på macOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, ydeevne
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e83400e444d4c8c733bea5552a31954bb019e358
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474041"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dette emne indeholder nogle generelle trin, der kan bruges til at indskrænke problemer med ydeevnen, der er relateret Microsoft Defender for Endpoint på macOS.

Beskyttelse i realtid (RTP) er en funktion i Microsoft Defender for Endpoint i macOS, der løbende overvåger og beskytter din enhed mod trusler. Den består af fil- og procesovervågning og anden heuristics.

Afhængigt af de programmer, du kører, og dine enhedsegenskaber kan du opleve underoptimal ydeevne, når du kører Microsoft Defender for Endpoint på macOS. Især programmer eller systemprocesser, der får adgang til mange ressourcer over en kort periode, kan føre til problemer med ydeevnen Microsoft Defender for Endpoint på macOS.

Følgende trin kan bruges til at foretage fejlfinding af og afhjælpe disse problemer:

1. Deaktiver beskyttelse i realtid ved hjælp af en af følgende metoder, og se, om ydeevnen forbedres. Denne fremgangsmåde hjælper med at indskrænke, Microsoft Defender for Endpoint på macOS bidrager til problemer med ydeevnen.

      Hvis din enhed ikke administreres af din organisation, kan beskyttelse i realtid deaktiveres ved hjælp af en af følgende indstillinger:

    - Fra brugergrænsefladen. Åbn Microsoft Defender for Endpoint i macOS, og gå til **Administrer indstillinger**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Siden Administrer beskyttelse i realtid" lightbox="images/mdatp-36-rtp.png":::
      

    - Fra terminalen. Af sikkerhedsmæssige årsager kræver denne handling udvidelse.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Hvis din enhed administreres af din organisation, kan beskyttelse i realtid deaktiveres af din administrator ved hjælp af vejledningen i Angiv indstillinger [for Microsoft Defender for Endpoint på macOS](mac-preferences.md).

      Hvis ydelsesproblemet fortsætter, mens beskyttelse i realtid er slået fra, kan problemets oprindelse være slutpunktsregistrering og -svar komponenten. I dette tilfælde skal du kontakte kundesupport for yderligere instruktioner og afhjælpning.

2. Åbn Finder, og naviger **til Programmer** \> **.** Åbn **Aktivitetsovervågning** , og analysér, hvilke programmer der bruger ressourcerne på systemet. Typiske eksempler omfatter softwareopdatering og compilere.

3. For at finde de programmer, der udløser de fleste scanninger, kan du bruge statistik i realtid, der er indsamlet af Defender til Slutpunkt på Mac.

      > [!NOTE]
      > Denne funktion er tilgængelig i version 100.90.70 eller nyere.
      Denne funktion er aktiveret som standard på **Doghem og** **InsiderFast-kanaler** . Hvis du bruger en anden opdateringskanal, kan denne funktion aktiveres fra kommandolinjen:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Denne funktion kræver beskyttelse i realtid for at blive aktiveret. Kør følgende kommando for at kontrollere status for beskyttelse i realtid:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Kontrollér, **at real_time_protection_enabled** er sandt. Ellers skal du køre følgende kommando for at aktivere den:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      For at indsamle aktuel statistik skal du køre:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > Ved **hjælp af --output json** (bemærk den dobbelte bindestreg) sikrer du, at outputformatet er klar til fortolkning.
      Outputtet for denne kommando viser alle processer og deres tilknyttede scanningsaktivitet.

4. På dit Mac-system skal du downloade python parserprøven high_cpu_parser.py ved hjælp af kommandoen:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Outputtet for denne kommando skal ligne følgende:

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.
    mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in
    0s
    ```

5. Skriv derefter følgende kommandoer:

      ```bash
        chmod +x high_cpu_parser.py
      ```

      ```bash
        cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
      ```

      Outputtet fra ovenstående er en liste over de vigtigste bidragydere til problemer med ydeevnen. Den første kolonne er procesidentifikatoren (PID), den anden kolonne er te procesnavn, og den sidste kolonne er antallet af scannede filer, sorteret efter virkning.

      Eksempelvis vil outputtet for kommandoen være noget i den følgende stand:

      ```output
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

      Hvis du vil forbedre ydeevnen for Defender til slutpunkt på Mac, skal du finde den med det højeste tal under den scannede række Af filer i alt og tilføje en udeladelse for den. Få mere at vide under [Konfigurer og valider udeladelse af Defender for Endpoint på Linux](linux-exclusions.md).

      > [!NOTE]
      > Programmet lagrer statistik i hukommelsen og holder kun styr på filaktivitet, siden det blev startet, og beskyttelse i realtid blev aktiveret. Processer, der blev startet før eller i perioder, hvor beskyttelse i realtid var slået fra, tælles ikke. Desuden tælles kun hændelser, der udløste scanninger, med.
      >
6. Konfigurer Microsoft Defender for Endpoint på macOS med undtagelser for de processer eller diskplaceringer, der bidrager til problemer med ydeevnen, og genaktiver beskyttelse i realtid.

     Se [Konfigurer og valider udeladelse for Microsoft Defender for Endpoint på macOS](mac-exclusions.md), hvis du vil have mere at vide.
