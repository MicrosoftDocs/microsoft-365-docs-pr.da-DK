---
title: Deaktiver rapporter, når du eksporterer resultater af indholdssøgning
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Rediger Windows-registreringsdatabasen på din lokale computer for at deaktivere rapporter, når du eksporterer resultaterne af en indholdssøgning fra Microsoft Purview-compliance-portal.
ms.openlocfilehash: 55a5405d516b0bf3daaca5970a25794b468a5119
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636177"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Deaktiver rapporter, når du eksporterer resultater af indholdssøgning

Når du bruger værktøjet eDiscovery-eksport til at eksportere resultaterne af en indholdssøgning i Microsoft Purview-compliance-portal, opretter og eksporterer værktøjet automatisk to rapporter, der indeholder yderligere oplysninger om det eksporterede indhold. Disse rapporter er Results.csv-filen og Manifest.xml-filen .Se afsnittet [Ofte stillede spørgsmål om deaktivering af eksportrapporter](#frequently-asked-questions-about-disabling-export-reports) i dette emne for at få detaljerede beskrivelser af disse rapporter). Da disse filer kan være meget store, kan du fremskynde downloadtiden og spare diskplads ved at forhindre, at disse filer eksporteres. Det kan du gøre ved at ændre Windows-registreringsdatabasen på den computer, du bruger til at eksportere søgeresultaterne. Hvis du vil medtage rapporterne på et senere tidspunkt, kan du redigere indstillingen i registreringsdatabasen. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Opret indstillinger i registreringsdatabasen for at deaktivere eksportrapporterne

Udfør følgende procedure på den computer, du vil bruge til at eksportere resultaterne til en indholdssøgning.
  
1. Luk værktøjet til eDiscovery-eksport, hvis det er åbent.
    
2. Udfør et eller begge af følgende trin, afhængigt af hvilken eksportrapport du vil deaktivere.
    
    - **Results.csv**
    
      Gem følgende tekst i en Windows-registreringsdatabasefil ved hjælp af et filnavnssuffiks af .reg. f.eks. DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Gem følgende tekst i en Windows-registreringsdatabasefil ved hjælp af et filnavnssuffiks af .reg. f.eks. DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. I Windows Stifinder skal du klikke eller dobbeltklikke på den .reg-fil, du oprettede i de forrige trin.
    
4. Klik på **Ja** i vinduet Bruger Access Control for at lade registreringseditoren foretage ændringen. 
    
5. Klik på **Ja**, når du bliver bedt om at fortsætte.
    
    Der vises en meddelelse i Registreringseditor om, at indstillingen blev føjet til registreringsdatabasen.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Rediger indstillinger i registreringsdatabasen for at aktivere eksportrapporterne igen

Hvis du har deaktiveret Results.csv og Manifest.xml rapporter ved at oprette .reg-filerne i den forrige procedure, kan du redigere disse filer for at aktivere en rapport igen, så den eksporteres med søgeresultaterne. Udfør igen følgende procedure på den computer, du vil bruge til at eksportere resultaterne til en indholdssøgning.
  
1. Luk værktøjet til eDiscovery-eksport, hvis det er åbent.
    
2. Rediger en eller begge af de .reg-redigeringsfiler, du oprettede i den forrige procedure.
    
    - **Results.csv**
    
        Åbn filen DisableResultsCsv.reg i Notesblok, skift værdien  `False` til  `True`, og gem derefter filen. Når du f.eks. har redigeret filen, ser den sådan ud:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Åbn filen DisableManifestXml.reg i Notesblok, ret værdien  `False` til  `True`, og gem derefter filen. Når du f.eks. har redigeret filen, ser den sådan ud:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. I Windows Stifinder skal du klikke eller dobbeltklikke på en .reg-fil, som du redigerede i det forrige trin.
    
4. Klik på **Ja** i vinduet Bruger Access Control for at lade registreringseditoren foretage ændringen. 
    
5. Klik på **Ja**, når du bliver bedt om at fortsætte.
    
    Der vises en meddelelse i Registreringseditor om, at indstillingen blev føjet til registreringsdatabasen.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Ofte stillede spørgsmål om deaktivering af eksportrapporter

 **Hvad er rapporterne Results.csv og Manifest.xml?**
  
Filerne Results.csv og Manifest.xml indeholder flere oplysninger om det indhold, der blev eksporteret.
  
- **Results.csv** Et Excel-dokument, der indeholder oplysninger om hvert element, der downloades som et søgeresultat. I forbindelse med mail indeholder resultatloggen oplysninger om hver meddelelse, herunder: 
    
  - Placeringen af meddelelsen i kildepostkassen (herunder om meddelelsen er i den primære postkasse eller arkivpostkassen).
    
  - Den dato, hvor meddelelsen blev sendt eller modtaget.
    
  - Emnelinjen fra meddelelsen.
    
  - Afsenderen og modtagerne af meddelelsen.
    
  - Angiver, om meddelelsen er en dubletmeddelelse, hvis du har aktiveret deduplikering, da du eksporterede søgeresultaterne. Duplikerede meddelelser har en værdi i kolonnen **Overordnet ItemId** , der identificerer meddelelsen som en dublet. Værdien i kolonnen **Overordnet ItemId** er den samme som værdien i kolonnen **Item DocumentId** i den meddelelse, der blev eksporteret. 
    
    For dokumenter fra SharePoint- og OneDrive for Business-websteder indeholder resultatloggen oplysninger om hvert dokument, herunder:
    
  - DOKUMENTETs URL-adresse.
    
  - URL-adressen for den gruppe af websteder, hvor dokumentet er placeret.
    
  - Den dato, hvor dokumentet senest blev ændret.
    
  - Navnet på dokumentet (som findes i kolonnen Emne i resultatloggen).
    
- **Manifest.xml** En manifestfil (i XML-format), der indeholder oplysninger om hvert element, der er inkluderet i søgeresultaterne. Oplysningerne i denne rapport er de samme som den Results.csv rapport, men de er i det format, der er angivet i EDRM (Electronic Discovery Reference Model). Du kan få flere oplysninger om EDRM ved at gå til [https://www.edrm.net](https://www.edrm.net).
    
 **Hvornår skal jeg deaktivere eksport af disse rapporter?**
  
Det afhænger af dine specifikke behov. Mange organisationer kræver ikke yderligere oplysninger om søgeresultater og har ikke brug for disse rapporter.
  
 **Hvilken computer skal jeg gøre det på?**
  
 Du skal ændre indstillingen i registreringsdatabasen på en hvilken som helst lokal computer, som du kører værktøjet eDiscovery Export på. 
  
 **Når jeg har ændret denne indstilling, skal jeg så genstarte computeren?**
  
Nej, du behøver ikke at genstarte computeren. Men hvis eDiscovery-eksportværktøjet kører, skal du lukke det og derefter genstarte det, når du har ændret indstillingen i registreringsdatabasen.
  
 **Redigeres en eksisterende registreringsdatabasenøgle, eller oprettes der en ny nøgle?**
  
Der oprettes en ny registreringsdatabasenøgle, første gang du kører den .reg-fil, du oprettede i proceduren i dette emne. Derefter redigeres indstillingen, hver gang du ændrer, og kører .reg-redigeringsfilen igen.
