---
title: Skift størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 10/12/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 04e9de2d-765b-457b-a98a-d0f60bfb13f2
description: Du kan ændre standardstørrelsen for PST-filer, der downloades til din computer, når du eksporterer eDiscovery-søgeresultater.
ms.openlocfilehash: 135c83f734e0687c8d477ab434d0aa539224f39a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100825"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Skift størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du bruger værktøjet eDiscovery-eksport til at eksportere mailresultaterne af en eDiscovery-søgning fra de forskellige Microsoft eDiscovery-værktøjer, er standardstørrelsen på en PST-fil, der kan eksporteres, 10 GB. Hvis du vil ændre denne standardstørrelse, kan du redigere Windows-registreringsdatabasen på den computer, du bruger til at eksportere søgeresultaterne. En af grundene til dette er, at en PST-fil kan være på flytbare medier, en dvd, en cd eller et USB-drev. 
  
> [!NOTE]
> Værktøjet eDiscovery-eksport bruges til at eksportere søgeresultaterne, når du bruger søgeværktøjet Indhold på Microsoft Purview-overholdelsesportalen.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Opret en indstilling i registreringsdatabasen for at ændre størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater

Udfør følgende procedure på den computer, du vil bruge til at eksportere resultaterne af en eDiscovery-søgning.
  
1. Luk værktøjet til eDiscovery-eksport, hvis det er åbent. 
    
2. Gem følgende tekst i en Window-registreringsdatabasefil ved hjælp af et filnavnssuffiks af .reg. f.eks. PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    I ovenstående eksempel er værdien  `PstSizeLimitInBytes` indstillet til 1.073.741.824 byte eller ca. 1 GB. Her er nogle andre eksempelværdier for  `PstSizeLimitInBytes` indstillingen. 
    
    |**Størrelse i GB (ca.)**|**Størrelse i byte**|
    |:-----|:-----|
    |0,7 GB (700 MB)  <br/> |751619277  <br/> |
    |2 GB  <br/> |2147483648  <br/> |
    |4 GB  <br/> |4294967296  <br/> |
    |8 GB  <br/> |8589934592  <br/> |
   
3. Ret værdien `PstSizeLimitInBytes` til den ønskede maksimumstørrelse for en PST-fil, når du eksporterer søgeresultater, og gem derefter filen. 
    
4. I Windows Explorer skal du klikke eller dobbeltklikke på den .reg-fil, du oprettede i de forrige trin.
    
5. Klik på **Ja** i vinduet Bruger Access Control for at lade registreringseditoren foretage ændringen. 
    
6. Klik på **Ja**, når du bliver bedt om at fortsætte.
    
    Der vises en meddelelse i Registreringseditor om, at indstillingen blev føjet til registreringsdatabasen.
    
7. Du kan gentage trin 3-6 for at ændre værdien for indstillingen i  `PstSizeLimitInBytes` registreringsdatabasen. 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Ofte stillede spørgsmål om ændring af standardstørrelsen for PST-filer, når du eksporterer eDiscovery-søgeresultater

 **Hvorfor er standardstørrelsen 10 GB?**
  
Standardstørrelsen på 10 GB var baseret på kundefeedback. 10 GB er en god balance mellem den optimale indholdsmængde i en enkelt PST og med en mindste chance for beskadigelse af filer.
  
 **Skal jeg øge eller mindske standardstørrelsen for PST-filer?**
  
Kunderne har en tendens til at reducere størrelsesgrænsen, så søgeresultaterne kan være på flytbare medier, som de fysisk kan sende til andre placeringer i deres organisation. Vi anbefaler ikke, at du øger standardstørrelsen, fordi PST-filer, der er større end 10 GB, kan have problemer med beskadigelse.
  
 **Hvilken computer skal jeg gøre det på?**
  
Du skal ændre indstillingen i registreringsdatabasen på en hvilken som helst lokal computer, som du kører værktøjet eDiscovery Export på.
  
 **Når jeg har ændret denne indstilling, skal jeg så genstarte computeren?**
  
Nej, du behøver ikke at genstarte computeren. Men hvis eDiscovery-eksportværktøjet kører, skal du lukke det og genstarte det, når du har ændret denne indstilling.
  
 **Redigeres en eksisterende registreringsdatabasenøgle, eller oprettes der en ny nøgle?**
  
Der oprettes en ny registreringsdatabasenøgle, første gang du kører den .reg-fil, du oprettede i denne procedure. Derefter redigeres indstillingen, hver gang du ændrer, og kører .reg-redigeringsfilen igen.
