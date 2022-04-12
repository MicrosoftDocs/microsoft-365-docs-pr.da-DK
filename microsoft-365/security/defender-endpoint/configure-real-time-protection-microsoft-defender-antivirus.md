---
title: Aktivér og konfigurer funktioner til Microsoft Defender Antivirus beskyttelse
description: Aktivér og konfigurer Microsoft Defender Antivirus beskyttelsesfunktioner i realtid, f.eks. overvågning af funktionsmåde, heuristik og maskinel indlæring
keywords: antivirus, beskyttelse i realtid, rtp, maskinel indlæring, adfærdsovervågning, heuristik
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 10/22/2021
manager: dansimp
ms.custom: nextgen
ms.collection: M365-security-compliance
ms.openlocfilehash: 744aaa887bfbfafd29b9e3bedb8dc49791b43137
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790168"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Aktivér og konfigurer Microsoft Defender Antivirus altid-aktive beskyttelse i Gruppepolitik

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Always-on protection består af beskyttelse i realtid, overvågning af adfærd og heuristik til at identificere malware baseret på kendte mistænkelige og ondsindede aktiviteter.

Disse aktiviteter omfatter hændelser, f.eks. processer, der foretager usædvanlige ændringer af eksisterende filer, ændring eller oprettelse af automatiske startregistreringsdatabasenøgler og startplaceringer (også kendt som udvidelsespunkter for automatisk start eller ASEP'er) og andre ændringer af filsystemet eller filstrukturen.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Aktivér og konfigurer altid aktiveret beskyttelse i Gruppepolitik

Du kan bruge **Lokal Gruppepolitik Editor** til at aktivere og konfigurere Microsoft Defender Antivirus beskyttelsesindstillinger, der altid er aktiveret.

Sådan aktiveres og konfigureres always-on-beskyttelse:

1. Åbn **Editor til lokale Gruppepolitik** på følgende måde:

    1. Skriv **gpedit** i søgefeltet Windows 10 eller Windows 11 proceslinjen.

    2. Under **Bedste match** skal du vælge **Rediger gruppepolitik** for at starte **Lokal Gruppepolitik Editor**.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Søgeresultatet på proceslinjen GPEdit i Kontrolpanel" lightbox="images/gpedit-search.png":::

2. I venstre rude i **Editor til lokal Gruppepolitik** skal du udvide træet til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Komponenter** \> **Microsoft Defender Antivirus**.

3. Konfigurer politikindstillingen Microsoft Defender Antivirus antimalwaretjeneste.

   Dobbeltklik på **Tillad, at antimalwaretjenesten starter med normal prioritet** i ruden **med Microsoft Defender Antivirus** detaljer til højre, og angiv den til **Aktiveret**.

   Vælg derefter **OK**.

4. Konfigurer indstillingerne for Microsoft Defender Antivirus beskyttelsespolitik i realtid på følgende måde:

    1. Dobbeltklik på **Beskyttelse i realtid** i ruden **med Microsoft Defender Antivirus** detaljer. Du kan også vælge **Beskyttelse i realtid** i **træet Microsoft Defender Antivirus** til venstre.

    2. Dobbeltklik på politikindstillingen i ruden **Beskyttelse** i realtid til højre som angivet i [Indstillinger for beskyttelsespolitik i realtid](#real-time-protection-policy-settings) (senere i denne artikel).

    3. Konfigurer indstillingen efter behov, og vælg **OK**.

    4. Gentag de forrige trin for hver indstilling i tabellen.

5. Konfigurer politikindstillingen Microsoft Defender Antivirus scanning på følgende måde:

    1. Vælg **Scan** **i Microsoft Defender Antivirus** træ til venstre.
    
   2. Dobbeltklik på **Slå heuristik** til i ruden **Scan** details til højre, og angiv den til **Enabled**. 

   3. Vælg **OK**.

6. Luk **Editor til lokal Gruppepolitik**.

### <a name="real-time-protection-policy-settings"></a>Indstillinger for beskyttelsespolitik i realtid

|Indstilling|Standardindstillingen|
|---|---|
|Slå overvågning af funktionsmåde til <p> Antivirusprogrammet overvåger filprocesser, ændringer i filer og registreringsdatabasen og andre hændelser på dine slutpunkter for mistænkelig og kendt skadelig aktivitet.|Aktiveret|
|Scan alle downloadede filer og vedhæftede filer <p> Downloadede filer og vedhæftede filer scannes automatisk. Denne scanning fungerer ud over det Windows Defender SmartScreen-filter, der scanner filer før og under download.|Aktiveret|
|Overvåg fil- og programaktivitet på computeren <p> Det Microsoft Defender Antivirus program noterer sig eventuelle filændringer (filskrivninger, f.eks. flytninger, kopier eller ændringer) og generel programaktivitet (programmer, der åbnes eller kører, og som medfører, at andre programmer kører).|Aktiveret|
|Slå rå meddelelser om skrivning af diskenhed til <p> Oplysninger om rå diskenhedsskrivninger analyseres af overvågning af funktionsmåde.|Aktiveret|
|Slå processcanning til, når beskyttelse i realtid er aktiveret <p> Du kan uafhængigt aktivere Microsoft Defender Antivirus-programmet for at scanne kørende processer for mistænkelige ændringer eller funktionsmåder. Dette er nyttigt, hvis du har deaktiveret beskyttelse i realtid midlertidigt og vil scanne processer, der startede, mens de blev deaktiveret, automatisk.|Aktiveret|
|Definer den maksimale størrelse af downloadede filer og vedhæftede filer, der skal scannes <p> Du kan definere størrelsen i kilobyte.|Aktiveret|
|Konfigurer tilsidesættelse af lokal indstilling for aktivering af overvågning af funktionsmåde <p> Konfigurer en lokal tilsidesættelse af konfigurationen af overvågning af funktionsmåde. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres indstillingen for lokale indstillinger over Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, har Gruppepolitik højere prioritet end indstillingen for lokale indstillinger.|Aktiveret|
|Konfigurer tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer <p> Konfigurer en lokal tilsidesættelse af konfigurationen af scanning for alle downloadede filer og vedhæftede filer. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres indstillingen for lokale indstillinger over Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, har Gruppepolitik højere prioritet end indstillingen for lokale indstillinger.|Aktiveret|
|Konfigurer tilsidesættelse af lokal indstilling for overvågning af fil- og programaktivitet på computeren <p> Konfigurer en lokal tilsidesættelse af konfigurationen af overvågning for fil- og programaktivitet på computeren. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres indstillingen for lokale indstillinger over Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, har Gruppepolitik højere prioritet end indstillingen for lokale indstillinger.|Aktiveret|
|Konfigurer tilsidesættelse af lokal indstilling for at aktivere beskyttelse i realtid <p> Konfigurer en lokal tilsidesættelse af konfigurationen for at aktivere beskyttelse i realtid. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres indstillingen for lokale indstillinger over Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, har Gruppepolitik højere prioritet end indstillingen for lokale indstillinger.|Aktiveret|
|Konfigurer tilsidesættelse af lokal indstilling for overvågning for indgående og udgående filaktivitet <p> Konfigurer en lokal tilsidesættelse af konfigurationen af overvågning for indgående og udgående filaktivitet. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres indstillingen for lokale indstillinger over Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, har Gruppepolitik højere prioritet end indstillingen for lokale indstillinger.|Aktiveret|
|Konfigurer overvågning for indgående og udgående fil- og programaktivitet <p> Angiv, om overvågning skal finde sted på indgående, udgående, begge eller ingen af retninger. Denne handling er relevant for Windows Server-installationer, hvor du har defineret bestemte servere eller serverroller, der kun ser store mængder filændringer i én retning, og du vil forbedre netværkets ydeevne. Fuldt opdaterede slutpunkter (og servere) på et netværk vil kun få ringe indvirkning på ydeevnen, uanset antallet eller retningen af filændringer.|Aktiveret (begge retninger)|

## <a name="disable-real-time-protection-in-group-policy"></a>Deaktiver beskyttelse i realtid i Gruppepolitik

> [!WARNING]
> Hvis du deaktiverer beskyttelse i realtid, reduceres beskyttelsen på dine slutpunkter drastisk, og det anbefales ikke.

Den primære funktion til beskyttelse i realtid er aktiveret som standard, men du kan deaktivere den ved hjælp af **Lokal Gruppepolitik Editor**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Sådan deaktiverer du beskyttelse i realtid i gruppepolitik

1. Åbn **Editor til lokal Gruppepolitik**.

   1. Skriv **gpedit** i søgefeltet Windows 10 eller Windows 11 proceslinjen.
   2. Under **Bedste match** skal du vælge **Rediger gruppepolitik** for at starte **Lokal Gruppepolitik Editor**.

2. I venstre rude i **Lokal Gruppepolitik Editor** skal du udvide træet til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **Beskyttelse i realtid**.

3. Dobbeltklik på **Slå beskyttelse i realtid fra** i ruden Med oplysninger om **beskyttelse** i realtid til højre.

4. I vinduet **Slå beskyttelse i realtid** fra skal du angive indstillingen til **Aktiveret**.
   
5. vælg **OK**.

6. Luk **Editor til lokal Gruppepolitik**.

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

- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
