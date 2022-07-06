---
title: Vis overvågningsaktivitet for ansvarlig
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Brug værktøjet eDiscovery (Premium) Custodian Management til nemt at få adgang til og søge efter tilsynsførende i din sag.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 3ead391eee7fc35a66a0d9472278ee75878de4df
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626991"
---
# <a name="view-custodian-audit-activity"></a>Vis overvågningsaktivitet for ansvarlig

Har du brug for at finde ud af, om en bruger fik vist et bestemt dokument eller fjernede et element fra sin postkasse? Microsoft Purview eDiscovery (Premium) er nu integreret med det eksisterende søgeværktøj til overvågningslog i Microsoft Purview-compliance-portal. Ved hjælp af denne integrerede oplevelse kan du bruge værktøjet eDiscovery (Premium) Custodian Management til at lette din undersøgelse ved nemt at få adgang til og søge efter tilsynsførende i din sag.

## <a name="get-permissions"></a>Hent tilladelser

Du skal have tildelt rollen View-Only overvågningslogge eller overvågningslogge i Exchange Online for at søge i overvågningsloggen. Disse roller tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden Tilladelser i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Hvis du vil give en bruger mulighed for at søge i eDiscovery-overvågningsloggen (Premium) med minimumsniveauet for rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only Overvågningslogge eller Overvågningslogge og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan få flere oplysninger under Administrer rollegrupper i Exchange Online.

> [!IMPORTANT]
> Hvis du tildeler en bruger rollen View-Only overvågningslogfiler eller overvågningslogfiler på siden Tilladelser på overholdelsesportalen, kan vedkommende ikke søge i overvågningsloggen. Du skal tildele tilladelserne i Exchange Online. Det skyldes, at den underliggende cmdlet, der bruges til at søge i overvågningsloggen, er en Exchange Online-cmdlet.

## <a name="step-1-search-the-audit-log-for-activities-performed-by-a-custodian"></a>Trin 1: Søg i overvågningsloggen efter aktiviteter, der udføres af en tilsynsførende

1. Gå til  **eDiscovery > eDiscovery (Premium),** og åbn sagen.
  
2. Klik på fanen **Kilder** .
  
3. Vælg en tilsynsførende på listen på siden **Tilsynsførende** , og klik derefter på **Vis tilsynsførende aktivitet** på pop op-siden.

    Søgesiden Tilsynsførende aktiviteter vises. Bemærk, at den tilsynsførende, du valgte i det forrige trin, vises på rullelisten **Tilsynsførende** . Du kan vælge forskellige tilsynsførende på rullelisten, men du kan kun søge efter aktiviteter for én tilsynsførende ad gangen.

    ![Søgeside for tilsynsførende aktiviteter.](../media/AeDCustodianActivities1.png)
   
4. Konfigurer følgende søgekriterier:
      
   1. **Aktiviteter** – Klik på rullelisten for at få vist de aktiviteter, du kan søge efter. Når du har kørt søgningen, er det kun overvågningsposterne for de valgte aktiviteter, der vises. Hvis du vælger **Vis resultater for alle aktiviteter** , vises resultaterne for alle de aktiviteter, der udføres af den tilsynsførende, og som stemmer overens med de andre søgekriterier.

      ![Liste over aktiviteter.](../media/CustodianActivityAudit.PNG)
      
   1. **Startdato og Slutdato** – Vælg et dato- og klokkeslætsinterval for at få vist de hændelser, der opstod inden for den pågældende periode. De seneste syv dage er valgt som standard. Dato og klokkeslæt vises i UTC-format (Coordinated Universal Time). Det maksimale datointerval, du kan angive, er ét år.
      
   1. **Tilsynsførende** – Klik i dette felt, og vælg derefter en bestemt tilsynsførende, der skal vises søgeresultater for. Overvågningsposter for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater.
      
5. Klik ![Søgeknap.](../media/SearchButton.PNG)  for at køre søgningen ved hjælp af dine søgekriterier. Søgeresultaterne indlæses, og efter et øjeblik vises de under Resultater på søgesiden Forældremyndighedens aktiviteter. 

## <a name="step-2-view-the-audit-log-search-results"></a>Trin 2: Få vist søgeresultaterne i overvågningsloggen

Resultaterne af en søgning i overvågningsloggen vises under Resultater på siden Overvågningslog for tilsynsførende. Der vises maksimalt 5.000 (nyeste) hændelser i intervaller af 150 hændelser. Hvis du vil have vist flere hændelser, kan du bruge rullepanelet i ruden Resultater, eller du kan trykke på Skift + End for at få vist de næste 150 hændelser.

Resultaterne indeholder følgende oplysninger om hver hændelse, der returneres af søgningen.
- **Dato**: Dato og klokkeslæt (i UTC-format), da hændelsen fandt sted.

- **IP-adresse**: IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.

- **Bruger**: Den bruger (eller tjenestekonto), der udførte den handling, der udløste hændelsen.

- **Aktivitet**: Den aktivitet, der udføres af brugeren. Denne værdi svarer til de aktiviteter, du har valgt på rullelisten Aktiviteter. For en hændelse fra Exchange-administratorens overvågningslog er værdien i denne kolonne en Exchange-cmdlet.

- **Element**: Det objekt, der blev oprettet eller ændret som følge af den tilsvarende aktivitet. Det kan f.eks. være den fil, der blev vist eller ændret, eller den brugerkonto, der blev opdateret. Ikke alle aktiviteter har en værdi i denne kolonne.

- **Detalje**: Flere oplysninger om en aktivitet. Det er ikke alle aktiviteter, der har en værdi.

## <a name="step-3-filter-the-search-results"></a>Trin 3: Filtrer søgeresultaterne

Ud over sortering kan du også filtrere resultaterne af en søgning i overvågningsloggen. Dette kan hjælpe dig med hurtigt at filtrere resultaterne for en bestemt bruger eller aktivitet. 

Sådan filtrerer du resultaterne:

 1. Opret og kør en søgning i overvågningsloggen.
  
2. Når resultaterne vises, skal du klikke på **Filtrer resultater**.
 
3. Nøgleordsfelter vises under hver kolonneoverskrift.
  
4. Klik på et af boksene under en kolonneoverskrift, og skriv et ord eller et udtryk, afhængigt af den kolonne du filtrerer efter. Resultaterne justeres dynamisk for at vise de hændelser, der stemmer overens med dit filter.
  
5. Hvis du vil rydde et filter, skal du klikke på **X** i filterfeltet eller blot klikke på **Skjul filtrering**.

## <a name="export-the-search-results-to-a-file"></a>Eksportér søgeresultaterne til en fil

Du kan eksportere resultaterne af en søgning i overvågningsloggen til en fil med kommaseparerede værdier (CSV) på din lokale computer. Du kan åbne denne fil i Microsoft Excel og bruge funktioner som f.eks. søgning, sortering, filtrering og opdeling af en enkelt kolonne (der indeholder celler med flere værdier) i flere kolonner.

1. Kør en søgning i overvågningsloggen, og rediger derefter søgekriterierne, indtil du har de ønskede resultater.
  
2. Klik på Eksportér resultater, og vælg en af følgende indstillinger:

    - **Gem indlæste resultater:** Vælg denne indstilling, hvis du kun vil eksportere de poster, der vises under **Resultater** på **søgesiden Tilsynsførende overvågningslog** . Den CSV-fil, der downloades, indeholder de samme kolonner (og data), der vises på siden (Dato, Bruger, Aktivitet, Element og Detaljer). En ekstra kolonne (med titlen **Mere**) er inkluderet i CSV-filen, der indeholder flere oplysninger fra posten i overvågningsloggen. Da du eksporterer de samme resultater, som indlæses (og kan ses) på søgesiden Overvågningslog, eksporteres der maksimalt 5.000 poster.
        
    - **Download alle resultater:** Vælg denne indstilling for at eksportere alle poster fra overvågningsloggen, der opfylder søgekriterierne. I forbindelse med et stort sæt søgeresultater skal du vælge denne indstilling for at downloade alle poster fra overvågningsloggen ud over de 5.000 resultater, der kan vises på søgesiden **Overvågning af overvågningslog** . Denne indstilling henter rådata fra overvågningsloggen til en CSV-fil og indeholder yderligere oplysninger fra posten i overvågningsloggen i en kolonne med navnet AuditData. Det kan tage længere tid at downloade filen, hvis du vælger denne eksportindstilling, fordi filen kan være meget større end den, der downloades, hvis du vælger den anden indstilling.
    
      > [!IMPORTANT]
      > Du kan maksimalt downloade 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis 50.000 poster downloades til CSV-filen, kan du sandsynligvis antage, at der er mere end 50.000 hændelser, der opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et datointerval til at reducere antallet af overvågningslogposter. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.
        

3. Når du har valgt en eksportindstilling, vises der en meddelelse nederst i vinduet, hvor du bliver bedt om at åbne CSV-filen, gemme den i mappen Overførsler eller gemme den i en bestemt mappe

Du kan finde flere oplysninger om visning, filtrering eller eksport af søgeresultater i overvågningsloggen under [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
