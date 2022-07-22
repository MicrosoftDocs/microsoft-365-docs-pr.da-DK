---
title: Foretag fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på macOS
description: Foretag fejlfinding af problemer med ydeevnen i Microsoft Defender for Endpoint på macOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, performance
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
ms.openlocfilehash: 7c60a61ca1a0a1179abd27c0f6d59970a0c09866
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969530"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Foretag fejlfinding af problemer med ydeevnen for Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dette emne indeholder nogle generelle trin, der kan bruges til at indsnævre problemer med ydeevnen, der er relateret til Microsoft Defender for Endpoint på macOS.

Realtidsbeskyttelse (RTP) er en funktion i Microsoft Defender for Endpoint på macOS, der konstant overvåger og beskytter din enhed mod trusler. Den består af fil- og procesovervågning og andre heuristik.

Afhængigt af de programmer, du kører, og dine enhedsegenskaber, kan du opleve en ikke-optimal ydeevne, når du kører Microsoft Defender for Endpoint på macOS. Især programmer eller systemprocesser, der har adgang til mange ressourcer over et kort tidsrum, kan føre til problemer med ydeevnen i Microsoft Defender for Endpoint på macOS.

Følgende trin kan bruges til at foretage fejlfinding og afhjælpe disse problemer:

1. Deaktiver beskyttelse i realtid ved hjælp af en af følgende metoder, og se, om ydeevnen forbedres. Denne fremgangsmåde hjælper med at indsnævre, om Microsoft Defender for Endpoint på macOS bidrager til problemerne med ydeevnen.

      Hvis enheden ikke administreres af din organisation, kan beskyttelse i realtid deaktiveres ved hjælp af en af følgende muligheder:

    - Fra brugergrænsefladen. Åbn Microsoft Defender for Endpoint på macOS, og naviger til **Administrer indstillinger**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Siden Administrer beskyttelse i realtid" lightbox="images/mdatp-36-rtp.png":::
      

    - Fra terminalen. Af sikkerhedsmæssige årsager kræver denne handling udvidede rettigheder.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Hvis enheden administreres af din organisation, kan beskyttelse i realtid deaktiveres af administratoren ved hjælp af vejledningen i [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md).

      Hvis problemet med ydeevnen fortsætter, mens beskyttelse i realtid er slået fra, kan problemets oprindelse være slutpunktsregistrerings- og svarkomponenten. I dette tilfælde skal du kontakte kundesupport for at få yderligere instruktioner og afhjælpning.

2. Åbn Finder, og naviger til **programmer** \> **.** Åbn **Aktivitetsovervågning** , og analysér, hvilke programmer der bruger ressourcerne på systemet. Typiske eksempler omfatter softwareopdaterings- og compilere.

3. Hvis du vil finde de programmer, der udløser flest scanninger, kan du bruge statistikker i realtid, der indsamles af Defender for Endpoint på Mac.

      > [!NOTE]
      > Denne funktion er tilgængelig i version 100.90.70 eller nyere.
      Denne funktion er som standard aktiveret på kanalerne **Dogfood** og **InsiderFast** . Hvis du bruger en anden opdateringskanal, kan denne funktion aktiveres fra kommandolinjen:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Denne funktion kræver, at beskyttelse i realtid er aktiveret. Kør følgende kommando for at kontrollere status for beskyttelse i realtid:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Kontrollér, at den **real_time_protection_enabled** er sand. Ellers skal du køre følgende kommando for at aktivere den:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      Hvis du vil indsamle aktuelle statistikker, skal du køre:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > Brug af **--output-json** (bemærk dobbelt tankestregen) sikrer, at outputformatet er klar til fortolkning.
      Outputtet af denne kommando viser alle processer og deres tilknyttede scanningsaktivitet.

4. Download Python-eksempelparser high_cpu_parser.py på dit Mac-system ved hjælp af kommandoen:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Outputtet af denne kommando skal ligne følgende:

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

      Ovenstående output er en liste over de største bidragydere til problemer med ydeevnen. Den første kolonne er proces-id'et (PID), den anden kolonne er procesnavnet, og den sidste kolonne er antallet af scannede filer sorteret efter indvirkning.

      Outputtet af kommandoen vil f.eks. være noget i stil med nedenstående:

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

      Hvis du vil forbedre ydeevnen for Defender for Endpoint på Mac, skal du finde den med det højeste tal under rækken Filer i alt scannet og tilføje en udeladelse for den. Du kan finde flere oplysninger under [Konfigurer og valider udeladelser for Defender for Endpoint på macOS](mac-exclusions.md).

      > [!NOTE]
      > Programmet gemmer statistikker i hukommelsen og holder kun styr på filaktivitet, siden det blev startet, og beskyttelse i realtid blev aktiveret. Processer, der blev startet før eller i perioder, hvor beskyttelse i realtid var slået fra, tælles ikke med. Derudover tælles kun hændelser, der udløste scanninger.
      >
6. Konfigurer Microsoft Defender for Endpoint på macOS med udeladelser for de processer eller diskplaceringer, der bidrager til problemerne med ydeevnen, og genaktiver beskyttelse i realtid.

     Se [Konfigurer og valider udeladelser for Microsoft Defender for Endpoint på macOS](mac-exclusions.md) for at få flere oplysninger.
