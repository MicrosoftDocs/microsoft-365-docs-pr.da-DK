---
title: Ændre størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Du kan ændre standardstørrelsen af PST-filer, der downloades til din computer, når du eksporterer eDiscovery-søgeresultater.
ms.openlocfilehash: b0376a423827df855af83375ddfae0e9803fd933
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587892"
---
# <a name="change-the-size-of-pst-files-when-exporting-ediscovery-search-results"></a>Ændre størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater

Når du bruger værktøjet eDiscovery-eksport til at eksportere mailresultater fra en eDiscovery-søgning fra de forskellige Microsoft eDiscovery-værktøjer, er standardstørrelsen for en PST-fil, der kan eksporteres, 10 GB. Hvis du vil ændre denne standardstørrelse, kan du redigere registreringsdatabasen Windows på den computer, du bruger til at eksportere søgeresultaterne. En grund til at gøre dette er, at en PST-fil kan være på flytbare medier, f.eks. en dvd, en kompakt disk eller et USB-drev. 
  
> [!NOTE]
> Værktøjet eDiscovery-eksport bruges til at eksportere søgeresultaterne, når du bruger værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter.
  
## <a name="create-a-registry-setting-to-change-the-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Opret en indstilling i registreringsdatabasen for at ændre størrelsen på PST-filer, når du eksporterer eDiscovery-søgeresultater

Udfør følgende procedure på den computer, som du skal bruge til at eksportere resultaterne af en eDiscovery-søgning.
  
1. Luk eDiscovery-eksportværktøjet, hvis det er åbent. 
    
2. Gem følgende tekst i en Windows-registreringsdatabasefil ved hjælp af et filnavnsuffiks af .reg; f.eks. PstExportSize.reg. 
    
    ```text
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
    "PstSizeLimitInBytes"="1073741824"
    ```

    I eksemplet ovenfor er  `PstSizeLimitInBytes` værdien angivet til 1.073.741.824 byte eller ca. 1 GB. Her er nogle andre eksempelværdier for  `PstSizeLimitInBytes` indstillingen. 
    
    |**Størrelse i GB (ca.**|**Størrelse i byte**|
    |:-----|:-----|
    |0,7 GB (700 MB)  <br/> |751619277  <br/> |
    |2 GB  <br/> |2147483648  <br/> |
    |4 GB  <br/> |4294967296  <br/> |
    |8 GB  <br/> |8589934592  <br/> |
   
3. Rediger værdien `PstSizeLimitInBytes` til den ønskede maksimale størrelse på en PST-fil, når du eksporterer søgeresultater, og gem derefter filen. 
    
4. I Windows stifinder skal du klikke eller dobbeltklikke på den .reg-fil, du oprettede i de forrige trin.
    
5. I vinduet Brugeradgangskontrol skal du klikke på **Ja** for at lade registreringseditoren foretage ændringen. 
    
6. Klik på Ja, når du bliver bedt om **at fortsætte**.
    
    Registreringseditoren viser en meddelelse, der fortæller, at indstillingen blev føjet til registreringsdatabasen.
    
7. Du kan gentage trin 3-6 for at ændre værdien for indstillingen i registreringsdatabasen  `PstSizeLimitInBytes` . 
  
## <a name="frequently-asked-questions-about-changing-the-default-size-of-pst-files-when-you-export-ediscovery-search-results"></a>Ofte stillede spørgsmål om ændring af standardstørrelsen af PST-filer, når du eksporterer eDiscovery-søgeresultater

 **Hvorfor er standardstørrelsen 10 GB?**
  
Standardstørrelsen på 10 GB var baseret på kundefeedback. 10 GB er en god balance mellem den optimale mængde indhold i en enkelt PST og med mindst mulig mulighed for beskadigelse af filen.
  
 **Skal jeg øge eller mindske standardstørrelsen af PST-filer?**
  
Kunder har en tendens til at mindske størrelsesgrænsen, så søgeresultaterne kan være på flytbare medier, som de fysisk kan sende til andre steder i organisationen. Vi anbefaler ikke, at du øger standardstørrelsen, da PST-filer, der er større end 10 GB, kan have problemer med beskadigelse.
  
 **Hvilken computer skal jeg gøre dette på?**
  
Du skal ændre indstillingen i registreringsdatabasen på en hvilken som helst lokal computer, som du kører værktøjet eDiscovery-eksport på.
  
 **Når jeg har ændret denne indstilling, skal jeg så genstarte computeren?**
  
Nej, du behøver ikke at genstarte computeren. Men hvis værktøjet eDiscovery-eksport kører, skal du lukke det og genstarte det, når du har ændret denne indstilling.
  
 **Bliver en eksisterende registreringsdatabasenøgle redigeret, eller oprettes en ny nøgle?**
  
Der oprettes en ny registreringsdatabasenøgle, første gang du kører den .reg-fil, du oprettede i denne procedure. Indstillingen redigeres derefter, hver gang du ændrer og kører .reg-redigeringsfilen igen.
