---
title: Opret og administrer eDiscovery-sager (Premium) i Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives det, hvordan du opretter og administrerer Microsoft Purview eDiscovery-sager (Premium). Det første trin er at oprette en sag og begynde at bruge funktioner og funktionalitet i eDiscovery (Premium).
ms.openlocfilehash: fb14c5ce7f1ffca6216e8d592c5cc1c7ff2802ce
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946413"
---
# <a name="create-and-manage-an-ediscovery-premium-case"></a>Opret og administrer en eDiscovery-sag (Premium)

Når du har konfigureret Microsoft Purview eDiscovery (Premium) og [tildelt tilladelser til eDiscovery-ledere](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) i din organisation, der skal administrere sager, er det næste trin at oprette og administrere en sag.

Denne artikel indeholder også en overordnet oversigt over, hvordan du bruger sager til at administrere eDiscovery-arbejdsprocessen (Premium) for en juridisk sag eller andre typer undersøgelser.

## <a name="create-a-case"></a>Opret en sag

Udfør følgende trin for at oprette en sag og tilføje medlemmer. Den bruger, der opretter sagen, tilføjes automatisk som medlem. Medlemmer af sagen kan få adgang til sagen på Microsoft Purview-overholdelsesportalen og udføre eDiscovery-opgaver (Premium).

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> , og log på med legitimationsoplysningerne for den brugerkonto, der er tildelt eDiscovery-tilladelser. Medlemmer af rollegruppen Organisationsadministration kan også oprette eDiscovery-sager (Premium).

2. Klik på **Vis alle** i navigationsruden til venstre på overholdelsesportalen, vælg derefter **eDiscoveryAdvanced** > , og vælg derefter <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">fanen **Sager**</a>.

3. Vælg **Opret en sag**.

4. På siden **Ny eDiscovery-sag** skal du give sagen et navn (obligatorisk), og derefter skrive et valgfrit sagsnummer og en valgfri beskrivelse. Sagsnavnet skal være entydigt i din organisation.

5. Klik på **Gem** for at oprette sagen.

   Den nye sag oprettes, og fanen **Indstillinger** i den nye sag vises.

6. Klik på **Vælg** i feltet **Adgang & tilladelser** under fanen **Indstillinger**.

7. På pop op-vinduet **Administrer denne sag** under **Administrer medlemmer** skal du klikke på **Tilføj** for at føje medlemmer til sagen.

8. På listen over personer skal du markere afkrydsningsfeltet ud for navnene på de personer, du vil føje til sagen. Som tidligere forklaret skal du sørge for, at de personer, du føjer til sagen, er tildelt de relevante eDiscovery-tilladelser.

9. Når du har valgt de personer, der skal tilføjes som medlemmer af sagen, skal du klikke på **Tilføj**.

10. Klik på **Gem** på siden **Administrer denne sag** for at gemme den nye liste over sagsmedlemmer.

11. Klik på fanen **Hjem** for at gå til startsiden for sagen.

## <a name="manage-the-workflow"></a>Administrer arbejdsprocessen

Her er en grundlæggende arbejdsproces, der passer til [almindelige eDiscovery-fremgangsmåder](advanced-ediscovery-edrm.md), så du kan komme i gang med at bruge eDiscovery (Premium). I hvert af disse trin fremhæver vi også nogle udvidede funktioner i eDiscovery (Premium), som du kan udforske.

![eDiscovery-arbejdsproces (Premium).](../media/AeDWorkflow.png)

1. **[Føj tilsynsførende](add-custodians-to-case.md) og [ikke-frihedsberøvende datakilder](non-custodial-data-sources.md) til sagen**. Det første trin efter at have oprettet en sag er at tilføje tilsynsførende. En *varetægtsfængslet* er en person, der har administrativ kontrol over et dokument eller en elektronisk fil, som kan være relevant for sagen. Du kan også tilføje datakilder, der ikke er knyttet til en bestemt bruger, men som kan være relevante for sagen.

   Her er nogle ting, der sker (eller som du kan gøre), når du føjer tilsynsførende til en sag:

   - Data i forældremyndighedens Exchange postkasse, OneDrive konto og eventuelle Microsoft Teams eller Yammer grupper, som vogteren er medlem af, kan "markeres" som frihedsberøvende data i tilfælde.
  
   - Forældremyndighedens data genindekseres (af en proces, der kaldes *Avanceret indeksering*). Dette hjælper med at optimere søgningen efter den i næste trin.
  
   - Du kan placere en venteposition på data fra tilsynsførende. Dette bevarer data, der kan være relevante for sagen under undersøgelsen.
  
   - Du kan knytte andre datakilder til en tilsynsførende (du kan f.eks. knytte et SharePoint websted eller en Microsoft 365 gruppe til en tilsynsførende), så disse data kan omlægges, sættes i venteposition og søges på samme måde som dataene i forældremyndighedens postkasse eller OneDrive konto.

   - Du kan bruge [arbejdsprocessen for kommunikation](managing-custodian-communications.md) i eDiscovery (Premium) til at sende en meddelelse om juridisk venteposition til tilsynsførende.

2. **[Indsaml relevant indhold fra datakilder](create-draft-collection.md)**. Når du har føjet tilsynsførende og ikke-frihedsberøvende datakilder til en sag, kan du bruge det indbyggede indsamlingsværktøj til at søge i disse datakilder efter indhold, der kan være relevant for sagen. Du kan bruge nøgleord, egenskaber og betingelser til at [oprette søgeforespørgsler](building-search-queries.md) , der returnerer søgeresultater med de data, der er mest relevante for sagen. Du kan også:

   - Få vist [statistik for samlinger](collection-statistics-reports.md) , der kan hjælpe dig med at afgrænse en samling for at indsnævre resultaterne.

   - Få vist et eksempel på samlingen for hurtigt at kontrollere, om de relevante data findes.

   - Rediger en forespørgsel, og kør samlingen igen.

3. **[Send samling til et korrektursæt](commit-draft-collection.md)**. Når du har konfigureret og bekræftet, at en søgning returnerer de ønskede data, er det næste trin at føje søgeresultaterne til et korrektursæt. Når du føjer data til et korrektursæt, kopieres elementer fra deres oprindelige placering til en sikker Azure Storage placering. Dataene indekseres igen for at optimere dem til grundige og hurtige søgninger, når du gennemser og analyserer elementer i korrektursættet. Du kan også [føje data, der ikke er Office 365, til et korrektursæt](load-non-office-365-data-into-a-review-set.md).

   Der er også en særlig type korrektursæt, som du kan føje data til, kaldet et *samtalegennemsynssæt*. Disse typer korrektursæt indeholder funktioner til genopbygning af samtaler, så du kan rekonstruere, gennemse og eksportere gevindsamtaler som dem i Microsoft Teams. Du kan finde flere oplysninger [under Gennemse samtaler i eDiscovery (Premium)](conversation-review-sets.md).

4. **Gennemse og analysér data i et korrektursæt**. Nu, hvor dataene er i et gennemgangssæt, kan du bruge en lang række værktøjer og funktioner til at få vist og analysere sagsdataene med det formål at reducere datasættet til det, der er mest relevant for den sag, du undersøger. Her er en liste over nogle værktøjer og egenskaber, som du kan bruge under denne proces.

   - [Vis dokumenter](view-documents-in-review-set.md). Dette omfatter visning af metadataene for hvert dokument i et gennemsynssæt og visning af dokumentet i den oprindelige version eller tekstversion.

   - [Opret forespørgsler og filtre](review-set-search.md). Du kan oprette søgeforespørgsler ved hjælp af forskellige søgekriterier (herunder muligheden for at søge i alle [egenskaber for filmetadata](document-metadata-fields-in-advanced-ediscovery.md) for yderligere at tilpasse og fjerne sagsdataene i forhold til det, der er mest relevant for sagen. Du kan også bruge filtre, der er angivet til gennemsyn, til hurtigt at anvende andre betingelser på resultaterne af en søgeforespørgsel for at finjustere disse resultater yderligere. 

   - [Opret og brug mærker](tagging-documents.md). Du kan anvende mærker på dokumenter i et korrektursæt for at identificere, hvilke der er dynamiske (eller ikke reagerer på sagen), og derefter bruge disse mærker, når du opretter søgeforespørgsler, til at inkludere eller udelade de mærkede dokumenter. Du kan også mærke for at bestemme, hvilke dokumenter der skal eksporteres.

   - [Anmærk og optegn dokumenter](view-documents-in-review-set.md#annotate-view). Du kan bruge anmærkningsværktøjet i en korrektur til at anmærke dokumenter og redigere indhold i dokumenter som arbejdsprodukt. Vi genererer en PDF-version af et anmærket eller redigeret dokument under gennemgangen for at reducere risikoen for at eksportere den ikke-redigerede oprindelige version af dokumentet.

   - [Analysér sagsdata](analyzing-data-in-review-set.md). Analysefunktionen i eDiscovery (Premium) er effektiv. Når du har kørt analyser af dataene i gennemgangssættet, udfører vi analyser, f.eks. næsten registrering af dubletter, mailtråde og temaer, der kan hjælpe med at reducere mængden af dokumenter, du skal gennemse. Vi genererer også en analyserapport, der opsummerer resultatet af at køre analyse. Som tidligere forklaret kører kørsel af analyser også [modellen til registrering af rettighedsregistrering for advokatklienter](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Eksportér og download sagsdata**. Et sidste trin efter indsamling, gennemgang og analyse af sagsdata er at eksportere dem ud af eDiscovery (Premium) til ekstern gennemgang eller til gennemsyn af personer uden for undersøgelsesteamet. Eksport af data er en proces med to trin. Det første trin er at [eksportere](export-documents-from-review-set.md) data ud af korrektursættet og kopiere dem til en anden Azure Storage placering (en, der leveres af Microsoft eller en, der administreres af din organisation). Derefter kan du bruge Azure Storage Explorer til at [downloade](download-export-jobs.md) dataene til en lokal computer. Ud over de eksporterede datafiler indeholder indeholder den også en eksportrapport, en oversigtsrapport og en fejlrapport.

## <a name="ediscovery-premium-architecture"></a>eDiscovery-arkitektur (Premium)

Her er et arkitekturdiagram, der viser eDiscovery-arbejdsprocessen (Premium) i et enkelt geomiljø og i et multi-geo-miljø samt dataflowet fra slutpunkt til slutpunkt, der er justeret i forhold til [modellen for reference til elektronisk registrering](overview-ediscovery-20.md#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model).

[![Modelplakat: eDiscovery-arkitektur (Premium) i Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Vis som et billede](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Download som en PDF-fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Download som en Visio-fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
