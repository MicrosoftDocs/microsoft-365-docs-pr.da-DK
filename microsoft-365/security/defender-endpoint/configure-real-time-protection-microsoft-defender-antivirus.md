---
title: Aktivere og Microsoft Defender Antivirus egenskaber for beskyttelse
description: Aktivér og konfigurer Microsoft Defender Antivirus funktioner til beskyttelse i realtid, f.eks. overvågning af funktionsmåder, heuristics og maskinlæring
keywords: antivirus, beskyttelse i realtid, rtp, maskinlæring, overvågning af adfærd, heuristics
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
ms.openlocfilehash: 9af87907c476b637ddc484bbb3357b143219107e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473205"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse i Gruppepolitik


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Altid on-beskyttelse består af beskyttelse i realtid, overvågning af funktionsmåder og heuristics til at identificere malware baseret på kendte mistænkelige og skadelige aktiviteter.

Disse aktiviteter omfatter hændelser, f.eks. processer, der foretager usædvanlige ændringer af eksisterende filer, ændring eller oprettelse af automatiske registreringsdatabasenøgler og startplaceringer (også kaldet automatisk startende udvidelsespunkter eller ASEP'er) og andre ændringer af filsystemet eller filstrukturen.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Aktivér og konfigurer altid-on-beskyttelse i Gruppepolitik

Du kan bruge **Lokal Gruppepolitik Editor** til at aktivere og konfigurere Microsoft Defender Antivirus indstillingerne for altid on-on-beskyttelse.

Sådan aktiveres og konfigureres altid-on-beskyttelse:

1. Åbn **Editor Gruppepolitik lokal tekst** som følger:

    1. Skriv **gpedit** Windows 11 Windows 10 søgefeltet i søgefeltet på proceslinjen.

    2. Under **Bedste match skal** du vælge **Rediger gruppepolitik for** at **starte Lokal Gruppepolitik Editor**.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Søgeresultatet for GPEdit-proceslinjen i Kontrolpanelet" lightbox="images/gpedit-search.png":::

2. I venstre rude i **Editor til Gruppepolitik lokal konfiguration** skal du udvide træet til Administrative skabeloner for **computerkonfiguration** \> \> **Windows Komponenter** \> **Microsoft Defender Antivirus**.

3. Konfigurer Microsoft Defender Antivirus for antimalwaretjeneste.

   I **detaljeruden Microsoft Defender Antivirus** til højre skal du dobbeltklikke på Tillad **antimalwaretjeneste** at starte med normal prioritet, og indstil den til **Aktiveret**.

   Vælg derefter **OK**.

4. Konfigurer Microsoft Defender Antivirus indstillinger for beskyttelsespolitik i realtid på følgende måde:

    1. I **ruden Microsoft Defender Antivirus** detaljer skal du **dobbeltklikke på Beskyttelse i realtid**. Du kan også vælge **Microsoft Defender Antivirus** realtidsbeskyttelse i venstre **rude**.

    2. I **detaljeruden Beskyttelse i** realtid til højre skal du dobbeltklikke på politikindstillingen som angivet i Indstillinger for beskyttelsespolitik i [realtid (senere](#real-time-protection-policy-settings) i denne artikel).

    3. Konfigurer indstillingen efter behov, og vælg **OK**.

    4. Gentag de forrige trin for hver indstilling i tabellen.

5. Konfigurer politikindstillingen Microsoft Defender Antivirus scanning på følgende måde:

    1. Vælg **scan Microsoft Defender Antivirus** i venstre rude i **opgavetræet**.
    
   2. I **detaljeruden** Scanning til højre skal du dobbeltklikke på **Aktivér heuristics** og indstille den til **Aktiveret**. 

   3. Vælg **OK**.

6. Luk **Lokal Gruppepolitik Editor**.

### <a name="real-time-protection-policy-settings"></a>Indstillinger for beskyttelsespolitik i realtid

|Indstilling|Standardindstilling|
|---|---|
|Aktiver overvågning af funktionsmåder <p> Antivirusprogrammet overvåger filprocesser, ændringer i filer og registreringsdatabasen og andre hændelser på dine slutpunkter for mistænkelig og kendt ondsindet aktivitet.|Aktiveret|
|Scan alle downloadede filer og vedhæftede filer <p> Downloadede filer og vedhæftede filer scannes automatisk. Denne scanning fungerer ud over det Windows Defender SmartScreen-filter, som scanner filer før og under overførslen.|Aktiveret|
|Overvåg fil- og programaktivitet på din computer <p> Programprogrammet Microsoft Defender Antivirus notere eventuelle filændringer (filskrivninger, f.eks. flytninger, kopier eller ændringer) og generel programaktivitet (programmer, der åbnes eller kører, og som medfører, at andre programmer kører).|Aktiveret|
|Slå rå meddelelser om lydstyrke til <p> Oplysninger om rå volumenskrivninger analyseres ved hjælp af overvågning af funktionsmåder.|Aktiveret|
|Slå processcanning til, når beskyttelse i realtid er aktiveret <p> Du kan uafhængigt aktivere Microsoft Defender Antivirus til at scanne kører processer for mistænkelige ændringer eller funktionsmåder. Dette er nyttigt, hvis du midlertidigt har deaktiveret beskyttelse i realtid og automatisk vil scanne processer, der startede, da den var deaktiveret.|Aktiveret|
|Definer den maksimale størrelse på downloadede filer og vedhæftede filer, der skal scannes <p> Du kan definere størrelsen i kilobyte.|Aktiveret|
|Konfigurere tilsidesættelse af lokale indstillinger for at aktivere overvågning af funktionsmåder <p> Konfigurer en lokal tilsidesættelse for konfigurationen af overvågning af funktionsmåder. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres den lokale indstilling frem for Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, Gruppepolitik en prioritet over indstillingen for den lokale indstilling.|Aktiveret|
|Konfigurere tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer <p> Konfigurer en lokal tilsidesættelse for konfiguration af scanning for alle downloadede filer og vedhæftede filer. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres den lokale indstilling frem for Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, Gruppepolitik en prioritet over indstillingen for den lokale indstilling.|Aktiveret|
|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af fil- og programaktivitet på computeren <p> Konfigurer en lokal tilsidesættelse for konfigurationen af overvågning for fil- og programaktivitet på computeren. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres den lokale indstilling frem for Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, Gruppepolitik en prioritet over indstillingen for den lokale indstilling.|Aktiveret|
|Konfigurer tilsidesættelse af lokale indstillinger for at aktivere beskyttelse i realtid <p> Konfigurer en lokal tilsidesættelse for konfigurationen for at aktivere beskyttelse i realtid. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres den lokale indstilling frem for Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, Gruppepolitik en prioritet over indstillingen for den lokale indstilling.|Aktiveret|
|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af indgående og udgående filaktivitet <p> Konfigurer en lokal tilsidesættelse for konfigurationen af overvågning af indgående og udgående filaktivitet. Denne indstilling kan kun angives af Gruppepolitik. Hvis du aktiverer denne indstilling, prioriteres den lokale indstilling frem for Gruppepolitik. Hvis du deaktiverer eller ikke konfigurerer denne indstilling, Gruppepolitik en prioritet over indstillingen for den lokale indstilling.|Aktiveret|
|Konfigurere overvågning af indgående og udgående fil- og programaktivitet <p> Angiv, om overvågning skal udføres på indgående, udgående, begge eller ingen retning. Denne handling er relevant for Windows Server-installationer, hvor du har defineret bestemte servere eller serverroller, der kun ser store mængder filændringer i én retning, og du vil forbedre netværkets ydeevne. Fuldt opdaterede slutpunkter (og servere) på et netværk vil kun få mindre indflydelse på ydeevnen uanset antallet eller retningen af filændringer.|Aktiveret (begge retninger)|

## <a name="disable-real-time-protection-in-group-policy"></a>Deaktiver beskyttelse i realtid i Gruppepolitik

> [!WARNING]
> Deaktivering af beskyttelse i realtid reducerer beskyttelsen på dine slutpunkter markant og anbefales ikke.

Den primære funktion til beskyttelse i realtid er aktiveret som standard, men du kan deaktivere den ved hjælp af **lokal Gruppepolitik Editor**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Sådan deaktiverer du beskyttelse i realtid i gruppepolitik

1. Åbn **Lokal Gruppepolitik Editor**.

   1. Skriv **gpedit** Windows 11 Windows 10 søgefeltet i søgefeltet på proceslinjen.
   2. Under **Bedste match skal** du vælge **Rediger gruppepolitik for** at **starte Lokal Gruppepolitik Editor**.

2. I venstre rude i  **Local Gruppepolitik Editor** skal du udvide træet til Administrative skabeloner til **computerkonfiguration** \> \> **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **Beskyttelse i realtid**.

3. I **detaljeruden Beskyttelse i realtid** til højre skal du dobbeltklikke på **Slå beskyttelse i realtid fra**.

4. I vinduet **Deaktiver beskyttelse i realtid skal** du angive indstillingen til **Aktiveret**.
   
5. skal **du vælge OK**.

6. Luk **Lokal Gruppepolitik Editor**.

## <a name="see-also"></a>Se også

- [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
