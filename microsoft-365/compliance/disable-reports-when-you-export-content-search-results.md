---
title: Deaktiver rapporter, når du eksporterer resultater fra indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: c9b0ff0c-282b-4a44-b43f-cfc5b96557f9
ms.custom:
- seo-marvel-apr2020
description: Rediger registreringsdatabasen Windows din lokale computer for at deaktivere rapporter, når du eksporterer resultaterne af en indholdssøgning fra Microsoft 365 Overholdelsescenter.
ms.openlocfilehash: bafdab1586b28239ddba7cf251704111731f2239
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587883"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Deaktiver rapporter, når du eksporterer resultater fra indholdssøgning

Når du bruger værktøjet eDiscovery-eksport til at eksportere resultaterne af en indholdssøgning i Microsoft 365 Overholdelsescenter, opretter og eksporterer værktøjet automatisk to rapporter, der indeholder yderligere oplysninger om det eksporterede indhold. Disse rapporter er den Results.csv-fil og Manifest.xml-filen (se afsnittet Ofte stillede spørgsmål om [](#frequently-asked-questions-about-disabling-export-reports) deaktivering af eksportrapporter i dette emne for at få detaljerede beskrivelser af disse rapporter). Da disse filer kan være meget store, kan du øge downloadtiden og spare diskplads ved at forhindre disse filer i at blive eksporteret. Det kan du gøre ved at ændre Windows registreringsdatabasen på den computer, du bruger til at eksportere søgeresultaterne. Hvis du vil medtage rapporterne på et senere tidspunkt, kan du redigere indstillingen i registreringsdatabasen. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Opret indstillinger for registreringsdatabasen for at deaktivere eksportrapporter

Udfør følgende procedure på den computer, du skal bruge til at eksportere resultaterne af en indholdssøgning.
  
1. Luk eDiscovery-eksportværktøjet, hvis det er åbent.
    
2. Udfør en eller begge af følgende trin, afhængigt af hvilken eksportrapport du vil deaktivere.
    
    - **Results.csv**
    
      Gem følgende tekst i en Windows-fil i registreringsdatabasen ved hjælp af et filnavnsuffiks af .reg, f.eks. DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Gem følgende tekst i en Windows-registreringsdatabasefil ved hjælp af et filnavnsuffiks af .reg, f.eks. DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. I Windows stifinder skal du klikke eller dobbeltklikke på den .reg-fil, du oprettede i de forrige trin.
    
4. I vinduet Brugeradgangskontrol skal du klikke på **Ja** for at lade registreringseditoren foretage ændringen. 
    
5. Klik på Ja, når du bliver bedt om **at fortsætte**.
    
    Registreringseditoren viser en meddelelse, der fortæller, at indstillingen blev føjet til registreringsdatabasen.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Rediger indstillinger i registreringsdatabasen for at genaktivere eksportrapporter

Hvis du har deaktiveret rapporterne om Results.csv og Manifest.xml ved at oprette .reg-filerne i den forrige procedure, kan du redigere disse filer for at genaktivere en rapport, så den eksporteres med søgeresultaterne. Udfør igen følgende procedure på den computer, du vil bruge til at eksportere resultaterne af en indholdssøgning.
  
1. Luk eDiscovery-eksportværktøjet, hvis det er åbent.
    
2. Rediger en eller begge af de .reg-redigeringsfiler, du oprettede i den forrige procedure.
    
    - **Results.csv**
    
        Åbn filen DisableResultsCsv.reg i Notesblok, rediger værdien `False` til `True`, og gem derefter filen. Når du f.eks. har redigeret filen, ser den sådan ud:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Åbn filen DisableManifestXml.reg i Notesblok, rediger værdien `False` til `True`, og gem derefter filen. Når du f.eks. har redigeret filen, ser den sådan ud:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. I Windows Stifinder skal du klikke eller dobbeltklikke på en .reg-fil, som du redigerede i forrige trin.
    
4. I vinduet Brugeradgangskontrol skal du klikke på **Ja** for at lade registreringseditoren foretage ændringen. 
    
5. Klik på Ja, når du bliver bedt om **at fortsætte**.
    
    Registreringseditoren viser en meddelelse, der fortæller, at indstillingen blev føjet til registreringsdatabasen.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Ofte stillede spørgsmål om deaktivering af eksportrapporter

 **Hvad er rapporterne Results.csv og Manifest.xml?**
  
Indholdsfilerne Results.csv og Manifest.xml indeholder yderligere oplysninger om det indhold, der blev eksporteret.
  
- **Results.csv** Et Excel dokument, der indeholder oplysninger om hvert element, der downloades som et søgeresultat. For mails indeholder resultatloggen oplysninger om hver meddelelse, herunder: 
    
  - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).
    
  - Den dato, hvor meddelelsen blev sendt eller modtaget.
    
  - Emnelinjen i meddelelsen.
    
  - Afsenderen og modtagerne af meddelelsen.
    
  - Om meddelelsen er en dubletmeddelelse, hvis du har aktiveret duplikering, når søgeresultaterne eksporteres. Dublerede meddelelser har en værdi i **kolonnen Overordnet element-id** , der identificerer meddelelsen som en dublet. Værdien i kolonnen **Overordnet element-id** er den samme som værdien i kolonnen **Item DocumentId** i den meddelelse, der blev eksporteret. 
    
    For dokumenter fra SharePoint og OneDrive for Business indeholder resultatloggen oplysninger om hvert dokument, herunder:
    
  - Dokumentets URL-adresse.
    
  - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.
    
  - Den dato, hvor dokumentet sidst blev ændret.
    
  - Navnet på dokumentet (som er placeret i kolonnen Emne i resultatloggen).
    
- **Manifest.xml** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der medtages i søgeresultaterne. Oplysningerne i denne rapport er de samme som Results.csv rapporten, men den er i det format, der er angivet af Electronic Discovery Reference Model (EDRM). Du kan finde flere oplysninger om EDRM ved at gå til [https://www.edrm.net](https://www.edrm.net).
    
 **Hvornår skal jeg deaktivere eksport af disse rapporter?**
  
Det afhænger af dine specifikke behov. Mange organisationer kræver ikke yderligere oplysninger om søgeresultater og har ikke brug for disse rapporter.
  
 **Hvilken computer skal jeg gøre dette på?**
  
 Du skal ændre indstillingen i registreringsdatabasen på en hvilken som helst lokal computer, som du kører værktøjet eDiscovery-eksport på. 
  
 **Når jeg har ændret denne indstilling, skal jeg så genstarte computeren?**
  
Nej, du behøver ikke at genstarte computeren. Men hvis værktøjet eDiscovery-eksport kører, skal du lukke det og genstarte det, når du har ændret indstillingen i registreringsdatabasen.
  
 **Bliver en eksisterende registreringsdatabasenøgle redigeret, eller oprettes en ny nøgle?**
  
Der oprettes en ny registreringsdatabasenøgle, første gang du kører den .reg-fil, du oprettede i proceduren i dette emne. Indstillingen redigeres derefter, hver gang du ændrer og kører .reg-redigeringsfilen igen.
