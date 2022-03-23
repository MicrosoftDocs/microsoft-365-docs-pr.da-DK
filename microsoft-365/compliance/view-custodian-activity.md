---
title: Vis overvågningsaktivitet for ansvarlig
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug værktøjet Advanced eDiscovery til at få nem adgang til og søge efter aktiviteter for y-brugere i din sag.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: d0ea6e94bd48c055cac23d8a96477e036369dd5c
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63587515"
---
# <a name="view-custodian-audit-activity"></a>Vis overvågningsaktivitet for ansvarlig

Har du brug for at finde ud af, om en bruger har set et bestemt dokument eller fjernet et element fra sin postkasse? Advanced eDiscovery nu integreret med det eksisterende søgeværktøj til overvågningslogfiler i Microsoft 365 Overholdelsescenter. Ved hjælp af denne integrerede oplevelse kan du bruge værktøjet Advanced eDiscovery, der viser, hvordan du undersøges, ved nemt at få adgang til og søge efter aktivitet for søgere i din sag.

## <a name="get-permissions"></a>Få tilladelser

Du skal have tildelt rollen View-Only overvågningslogfiler eller overvågningslogfiler i en Exchange Online at søge i overvågningsloggen. Disse roller tildeles som standard rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Hvis du vil give en bruger mulighed for at søge i Advanced eDiscovery-overvågningsloggen med det mindste niveau af rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only-overvågningslogfiler eller Overvågningslogs og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan finde flere oplysninger i Administrere rollegrupper i Exchange Online.

> [!IMPORTANT]
> Hvis du tildeler en bruger rollen View-Only-overvågningslogfiler eller Overvågningslogfiler på siden Tilladelser i Microsoft 365 Overholdelsescenter, kan de ikke søge i overvågningsloggen. Du skal tildele tilladelserne i Exchange Online. Dette skyldes, at den underliggende cmdlet, der bruges til at søge i overvågningsloggen, er en Exchange Online cmdlet.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>Trin 1: Søg i overvågningsloggen efter aktiviteter, der er udført af en seer

1. Gå til **eDiscovery > Advanced eDiscovery** og åbn sagen.
  
2. Klik på **fanen** Kilder.
  
3. På siden **YP'er** skal du vælge en yndet på listen, og derefter skal du klikke på Vis aktivitet, der er underholds **af,** på pop op-siden.

    Søgesiden For øvriske aktiviteter vises. Bemærk, at den vismand, du valgte i det forrige trin **, vises i** rullelisten 1. Du kan vælge forskellige øvriskere i rullelisten, men du kan kun søge efter aktiviteter for én af de ydst øvriske på én gang.

    ![Søgesiden For y-y-2-2-aktiviteter.](../media/AeDCustodianActivities1.png)
   
4. Konfigurer følgende søgekriterier:
      
   1. **Aktiviteter** – Klik på rullelisten for at få vist de aktiviteter, du kan søge efter. Når du har kørt søgningen, vises kun overvågningsposterne for de markerede aktiviteter. Hvis du **vælger Vis resultater for alle aktiviteter, vises** resultaterne for alle aktiviteter, der udføres af den kontrol, der opfylder de andre søgekriterier.

      ![Liste over aktiviteter.](../media/CustodianActivityAudit.PNG)
      
   1. **Startdato og Slutdato – Vælg en** dato og et tidsinterval for at få vist de hændelser, der er opstået inden for den pågældende periode. De seneste syv dage er valgt som standard. Dato og klokkeslæt vises i formatet UTC (Coordinated Universal Time). Det maksimale datointerval, du kan angive, er et år.
      
   1. **Esplikere** – Klik i dette felt, og vælg derefter en bestemt fremviser, der skal vises søgeresultater for. Overvågningsposter for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater.
      
5. Klik på ![Knappen Søg.](../media/SearchButton.PNG)  for at køre søgningen ved hjælp af dine søgekriterier. Søgeresultaterne indlæses, og efter et øjeblik vises de under Resultater på søgesiden Aktiviteter, der er ved at blive gennemsøgt af søgeresultaterne. 

## <a name="step-2-view-the-audit-log-search-results"></a>Trin 2: Få vist søgeresultaterne fra overvågningsloggen

Resultaterne af en søgning i overvågningsloggen vises under Resultater på siden Overvågningslog, der er ved at blive overvåget. Maksimalt 5.000 (nyeste) hændelser vises i intervaller på 150 hændelser. Hvis du vil have vist flere hændelser, kan du bruge rullepanelet i ruden Resultater, eller du kan trykke på Skift+End for at få vist de næste 150 hændelser.

Resultaterne indeholder følgende oplysninger om hver hændelse, der returneres af søgningen.
- **Dato**: Dato og klokkeslæt (i UTC-format), da hændelsen indtraf.

- **IP-adresse**: IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.

- **Bruger**: Den bruger (eller tjenestekonto), der udførte den handling, der udløste hændelsen.

- **Aktivitet**: Den aktivitet, der er udført af brugeren. Denne værdi svarer til de aktiviteter, du har valgt på rullelisten Aktiviteter. For en hændelse fra Exchange for administrator er værdien i denne kolonne en Exchange cmdlet.

- **Element**: Det objekt, der blev oprettet eller ændret som et resultat af den tilsvarende aktivitet. For eksempel den fil, der blev vist eller ændret, eller den brugerkonto, der blev opdateret. Ikke alle aktiviteter har en værdi i denne kolonne.

- **Detalje**: Flere oplysninger om en aktivitet. Igen har ikke alle aktiviteter en værdi.

## <a name="step-3-filter-the-search-results"></a>Trin 3: Filtrer søgeresultaterne

Ud over sortering kan du også filtrere resultaterne af en søgning i overvågningsloggen. Dette kan hjælpe dig med hurtigt at filtrere resultaterne for en bestemt bruger eller aktivitet. 

Sådan filtrerer du resultaterne:

 1. Opret og kør en søgning i overvågningsloggen.
  
2. Når resultaterne vises, skal du klikke på **Filtrer resultater**.
 
3. Felterne nøgleord vises under hver kolonneoverskrift.
  
4. Klik på et af felterne under en kolonneoverskrift, og skriv et ord eller udtryk, afhængigt af den kolonne, du filtrerer på. Resultaterne justeres dynamisk for at vise de hændelser, der passer til filteret.
  
5. Hvis du vil rydde et filter, skal **du klikke på X** i filterfeltet eller blot klikke **på Skjul filtrering**.

## <a name="export-the-search-results-to-a-file"></a>Eksportér søgeresultaterne til en fil

Du kan eksportere resultaterne af en søgning i overvågningsloggen til en fil med kommaseparerede værdier (CSV) på din lokale computer. Du kan åbne denne fil i Microsoft Excel og bruge funktioner som f.eks søgning, sortering, filtrering og opdeling af en enkelt kolonne (der indeholder celler med flere værdier) i flere kolonner.

1. Kør en søgning i overvågningsloggen, og revidere søgekriterierne, indtil du har de ønskede resultater.
  
2. Klik på Eksportér resultater, og vælg en af følgende indstillinger:

    - **Gem indlæste resultater:** Vælg denne indstilling, hvis du kun vil eksportere de poster, der vises under **Resultater** på siden med søgning i **overvågningsloggen med ydsmand.** DEN CSV-fil, der downloades, indeholder de samme kolonner (og data), der vises på siden (Dato, Bruger, Aktivitet, Element og Detaljer). En ekstra kolonne (med titlen **Mere**) er inkluderet i CSV-filen, der indeholder flere oplysninger fra overvågningslogposten. Da du eksporterer de samme resultater, som er indlæst (og kan vises) på siden Søgning i overvågningslog, eksporteres der maksimalt 5.000 poster.
        
    - **Hent alle resultater:** Vælg denne indstilling for at eksportere alle de poster fra overvågningsloggen, der opfylder søgekriterierne. Hvis der er tale om et stort sæt søgeresultater, skal du vælge denne indstilling for at hente alle poster fra overvågningsloggen ud over de 5.000 resultater, der kan vises på siden  med søgning i overvågningsloggen, hvor der vises oplysninger om overvågningsloggen. Denne indstilling downloader rådataene fra overvågningsloggen til en CSV-fil og indeholder yderligere oplysninger fra overvågningslogposten i en kolonne med navnet AuditData. Det kan tage længere tid at hente filen, hvis du vælger denne eksportindstilling, da filen kan være meget større end den, der downloades, hvis du vælger den anden indstilling.
    
      > [!IMPORTANT]
      > Du kan hente maksimalt 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis der downloades 50.000 poster til CSV-filen, kan du sandsynligvis antage, at mere end 50.000 hændelser opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et datointerval for at reducere antallet af poster i overvågningsloggen. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.
        

3. Når du har valgt en eksportindstilling, vises der en meddelelse nederst i vinduet, der beder dig om at åbne CSV-filen, gemme den i mappen Overførsler eller gemme den i en bestemt mappe

Du kan finde flere oplysninger om visning, filtrering eller eksport af søgeresultater fra overvågningsloggen [i Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
