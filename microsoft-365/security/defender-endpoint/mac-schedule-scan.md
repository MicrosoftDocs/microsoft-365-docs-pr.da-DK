---
title: Sådan planlægger du scanninger med Microsoft Defender til Endpoint på macOS
description: Få mere at vide om, hvordan du planlægger en automatisk scanningstid for Microsoft Defender til Endpoint i macOS for bedre at beskytte din organisations aktiver.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, scanninger, antivirus
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
ms.openlocfilehash: 629db5fc343d100913d631f59a680fc9160713ed
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592350"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Planlæg scanninger med Microsoft Defender til Slutpunkt på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Selvom du når som helst kan starte en trusselsscanning med Microsoft Defender til slutpunkt, kan din virksomhed drage fordel af planlagte eller timede scanninger. Du kan f.eks. planlægge en scanning til at køre i begyndelsen af hver arbejdsdag eller uge. 

## <a name="schedule-a-scan-with-launchd"></a>Planlæg en scanning med *start*

Du kan oprette en scanningsplan ved hjælp af *launchd* daemon på en macOS-enhed.

Du kan finde flere oplysninger om *.plist-filformatet* , der bruges her, i Om oplysninger om [egenskabslistefiler](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) på det officielle Apple-udviklerwebsted.

### <a name="schedule-a-quick-scan"></a>Planlæg en hurtig scanning

Følgende kode viser det skema, du skal bruge til at planlægge en hurtig scanning. 

1. Åbn en teksteditor, og brug dette eksempel som vejledning til din egen planlagte scanningsfil.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Gem filen som *com.microsoft.wdav.schedquickscan.plist*.

### <a name="schedule-a-full-scan"></a>Planlæg en fuld scanning

1. Åbn en teksteditor, og brug dette eksempel til en komplet scanning.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedfullscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan full</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>50</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Gem filen som *com.microsoft.wdav.schedfullscan.plist*.
 
### <a name="load-your-file"></a>Indlæs din fil

1. Åbn **Terminal**.
2. Angiv følgende kommandoer for at indlæse filen:

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. Din planlagte scanning kører på den dato, det klokkeslæt og den hyppighed, du har angivet på din p-liste. I de forrige eksempler kører scanningen kl. 02:50 hver fredag. 

    - Værdien `Weekday` af bruger `StartCalendarInterval` et heltal til at angive den femte dag i ugen eller fredag. Mellem 0 og 7 er 7, der repræsenterer søndag.
    - Værdien `Day` af anvender `StartCalendarInterval` et heltal til at angive den tredje dag i måneden. Området er mellem 1 og 31.
    - Værdien `Hour` af anvender `StartCalendarInterval` et heltal til at angive den anden time på dagen. Intervallet er mellem 0 og 24.
    Værdien `Minute` af bruger `StartCalendarInterval` et heltal til at angive 50 minutter i timen. Intervallet er mellem 0 og 59.
    
    
 > [!IMPORTANT]
 > Agenter, der *er udført med start* , kører ikke på det planlagte tidspunkt, mens enheden sov. De kører i stedet, når enheden genoptager fra slumretilstand.
 >
 > Hvis enheden er deaktiveret, kører scanningen ved næste planlagte scanningstid.

## <a name="schedule-a-scan-with-intune"></a>Planlæg en scanning med Intune

Du kan også planlægge scanninger med Microsoft Intune. Det [runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) shell-script, der er tilgængeligt på [Scripts til Microsoft Defender for Endpoint](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) , bevares, når enheden genoptager fra slumretilstand. 

Se [Brug shell-scripts på macOS-enheder i Intune](/mem/intune/apps/macos-shell-scripts) for at få mere detaljerede oplysninger om, hvordan du bruger dette script i din virksomhed.
