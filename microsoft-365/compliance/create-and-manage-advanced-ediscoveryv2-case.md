---
title: Opret og administrer Advanced eDiscovery i Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
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
description: Denne artikel beskriver, hvordan du opretter og administrerer Advanced eDiscovery sager. Det første trin er at oprette en sag og begynde at bruge Advanced eDiscovery funktioner og funktionalitet.
ms.openlocfilehash: f647421dcaba3d50f1cb8b7a6b1e58a792f23403
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63602968"
---
# <a name="create-and-manage-an-advanced-ediscovery-case"></a>Oprette og administrere en Advanced eDiscovery sag

Når du har konfigureret Advanced eDiscovery og tildelt [tilladelser til eDiscovery-ledere](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions) i din organisation, der vil administrere sager, er næste trin at oprette og administrere en sag.

Denne artikel indeholder også en detaljeret oversigt over brugen af sager til at administrere Advanced eDiscovery for en juridisk sag eller andre typer undersøgelser.

## <a name="create-a-case"></a>Opret en sag

Udfør følgende trin for at oprette en sag og tilføje medlemmer. Den bruger, der opretter sagen, tilføjes automatisk som medlem. Medlemmer af sagen kan få adgang til sagen i Microsoft 365 Overholdelsescenter udføre Advanced eDiscovery opgaver.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for den brugerkonto, der har fået tildelt eDiscovery-tilladelser. Medlemmer af rollegruppen Organisationsadministration kan også oprette Advanced eDiscovery sager.

2. Klik på Vis Microsoft 365 Overholdelsescenter navigationsruden i venstre navigationsrude **, og** vælg **derefter eDiscoveryAdvanced** > , og vælg derefter <a href="https://go.microsoft.com/fwlink/p/?linkid=2173764" target="_blank">**fanen** Sager</a>.

3. Vælg **Opret en sag**.

4. På pop **op-siden Ny eDiscovery-sag** skal du give sagen et navn (påkrævet) og derefter skrive et valgfrit sagsnummer og en beskrivelse. Casenavnet skal være entydigt i din organisation.

5. Klik **på Gem** for at oprette sagen.

   Den nye sag oprettes, **og Indstillinger** i den nye sag vises.

6. Klik på **& under** fanen Tilladelser **Indstillinger** Access **.**

7. Klik på **Tilføj under Administrer** medlemmer på pop **op-siden Administrer** denne sag **for** at føje medlemmer til sagen.

8. Markér afkrydsningsfeltet ud for navnene på de personer, du vil føje til sagen, på listen over personer. Som beskrevet tidligere skal du sørge for, at de personer, du føjer til sagen, har fået tildelt de relevante eDiscovery-tilladelser.

9. Når du har valgt de personer, der skal tilføjes som medlemmer af sagen, skal du klikke på **Tilføj**.

10. På pop **op-siden Administrer denne** sag skal du klikke på **Gem for** at gemme den nye liste over sagsmedlemmer.

11. Klik på **fanen** Hjem for at gå til startsiden for en sag.

## <a name="manage-the-workflow"></a>Administrere arbejdsprocessen

Her er en grundlæggende arbejdsproces, der Advanced eDiscovery i overensstemmelse med almindelige [eDiscovery-praksisser](advanced-ediscovery-edrm.md), for at komme i gang med at Advanced eDiscovery praksis. I hvert af disse trin fremhæver vi også nogle udvidede funktioner, Advanced eDiscovery, som du kan udforske.

![Advanced eDiscovery arbejdsproces.](../media/AeDWorkflow.png)

1. **[Føj ydsere](add-custodians-to-case.md) [og ikke-registrerede datakilder](non-custodial-data-sources.md) til sagen**. Det første trin efter oprettelsen af en sag er at tilføje øverere. En *kontaktperson er* en person, der har administrativ kontrol over et dokument eller en elektronisk fil, der kan være relevant for sagen. Desuden kan du tilføje datakilder, der ikke er knyttet til en bestemt bruger, men som kan være relevante for sagen.

   Her er nogle ting, der sker (eller som du kan gøre), når du føjer ydsere til en sag:

   - Data i den registreredes Exchange-postkasse, OneDrive-konto og eventuelle Microsoft Teams- eller Yammer-grupper, som den person, der skal have hjælp, er medlem af, kan i sagen "markeres" som oplysninger om, hvem der er til ansvar.
  
   - Opbevaringsdataene bliver genindført (ved hjælp af en proces kaldet *Avanceret indeksering*). Dette er med til at optimere søgningen efter det i næste trin.
  
   - Du kan placere venteposition på data for det person, der er skal være skal have arbejde, i venteposition. Dette bevarer data, der kan være relevante for sagen under undersøgelsen.
  
   - Du kan knytte andre datakilder til en assistent, der er tilknyttet (f.eks. kan du knytte et SharePoint-websted eller Microsoft 365-gruppe til en tilknyttet person), så disse data kan blive genindført, sat i venteposition og søget på samme måde som dataene i regnskabsmedarbejderens postkasse eller OneDrive-konto.

   - Du kan bruge [kommunikationsarbejdsprocessen i en](managing-custodian-communications.md) Advanced eDiscovery sende meddelelse om retslig venteposition til personer, der er i venteposition.

2. **[Indsamle relevant indhold fra datakilder](create-draft-collection.md)**. Når du har føjet ledende kilder og ikke-registrerede datakilder til en sag, skal du bruge det indbyggede samlingsværktøj til at søge efter indhold, der kan være relevant for sagen, i disse datakilder. Du bruger nøgleord, egenskaber og betingelser til at [](building-search-queries.md) opbygge søgeforespørgsler, der returnerer søgeresultater med de data, der er mest sandsynlige for sagen. Du kan også:

   - Få [vist samlingsstatistik](collection-statistics-reports.md) , som kan hjælpe dig med at indskrænke en samling for at indsnævre resultaterne.

   - Få vist et eksempel på samlingen for hurtigt at bekræfte, om de relevante data findes.

   - Revidere en forespørgsel og køre samlingen igen.

3. **[Bekræfte samlingen i et gennemsynssæt](commit-draft-collection.md)**. Når du har konfigureret og bekræftet, at en søgning returnerer de ønskede data, er næste trin at føje søgeresultaterne til et korrektursæt. Når du føjer data til et korrektursæt, kopieres elementer fra deres oprindelige placering til en sikker placering, Azure Storage placering. Dataene indekseres igen for at optimere dem til grundige og hurtige søgninger, når du gennemser og analyserer elementer i korrektursættet. Desuden kan du også tilføje [ikke-Office 365 i et korrektursæt](load-non-office-365-data-into-a-review-set.md).

   Der er også en særlig type korrektursæt, som du kan føje data til, kaldet et *samtalegennemsynssæt*. Disse typer anmeldelser giver samtaleovertrædelsesmuligheder, som kan genoprettes, gennemgås og eksporteres samtaler med tråde som dem i Microsoft Teams. Du kan finde flere [oplysninger i Gennemse samtaler i Advanced eDiscovery](conversation-review-sets.md).

4. **Gennemse og analysér data i et gennemsynssæt**. Nu, hvor dataene er i et gennemsynssæt, kan du bruge en lang række værktøjer og funktioner til at få vist og analysere sagsdataene med det formål at reducere datasættet til det, der er mest relevant for den sag, du undersøger. Her er en liste over nogle værktøjer og egenskaber, som du kan bruge under denne proces.

   - [Få vist dokumenter](view-documents-in-review-set.md). Dette omfatter visning af metadataene for hvert dokument i et korrektursæt og visning af dokumentet i dets oprindelige version eller tekstversion.

   - [Opret forespørgsler og filtre](review-set-search.md). Du opretter søgeforespørgsler ved hjælp af forskellige søgekriterier (herunder muligheden for at søge i alle filens [metadataegenskaber](document-metadata-fields-in-advanced-ediscovery.md) for yderligere at indskrænke og cullere sagsdataene til det, der er mest relevant for sagen. Du kan også bruge gennemsynssætfiltre til hurtigt at anvende andre betingelser på resultaterne af en søgeforespørgsel for yderligere at indskrænke disse resultater. 

   - [Opret og brug mærker](tagging-documents.md). Du kan anvende mærker på dokumenter i et korrektursæt for at identificere, hvad der svarer (eller ikke svarer til sagen), og derefter bruge disse mærker, når du opretter søgeforespørgsler for at medtage eller udelade de mærkede dokumenter. Du kan også mærke for at bestemme, hvilke dokumenter der skal eksporteres.

   - [Anmærke og redigere dokumenter](view-documents-in-review-set.md#annotate-view). Du kan bruge anmærkningsværktøjet i en gennemgang til at anmærke dokumenter og redigere indhold i dokumenter som et arbejdsprodukt. Vi genererer en PDF-version af et kommenteret eller redigeret dokument under gennemsyn for at reducere risikoen for at eksportere den oprindelige version af dokumentet, der ikke er redigeret.

   - [Analysere sagsdata](analyzing-data-in-review-set.md). Analysefunktionaliteten i Advanced eDiscovery effektiv. Når du har kørt analyser af dataene i et gennemsynssæt, udfører vi analyser som f.eks. nær registrering af dubletter, mailtrådning og temaer, som kan hjælpe med at reducere mængden af dokumenter, du skal gennemse. Vi genererer også en Analytics-rapport, der opsummerer resultatet af kørende analyser. Som tidligere beskrevet kører kørende analyser også [registreringsmodellen for advokatklientens rettigheder](attorney-privilege-detection.md#use-the-attorney-client-privilege-detection-model).

5. **Eksportere og downloade sagsdata**. Det sidste trin efter indsamling, gennemgang og analyse af sagsdata er at eksportere dem ud af Advanced eDiscovery til ekstern gennemgang eller til gennemgang af personer uden for undersøgelsesteamet. Eksport af data er en totrinsproces. Det første trin er at [eksportere data ud](export-documents-from-review-set.md) af korrektursættet og kopiere dem til en anden Azure Storage placering (en, der leveres af Microsoft, eller en, der administreres af din organisation). Derefter skal du Azure Storage Stifinder [til at](download-export-jobs.md) hente dataene til en lokal computer. Ud over de eksporterede datafiler indeholder pakkens indhold også en eksportrapport, en oversigtsrapport og en fejlrapport.

## <a name="advanced-ediscovery-architecture"></a>Advanced eDiscovery arkitektur

Her er et arkitekturdiagram, der viser Advanced eDiscovery end-to-end-arbejdsprocessen i et enkelt geomiljø og i et multi-geo-miljø, og det slutpunkt-til-ende-dataflow, der er justeret med [Electronic Discovery-referencemodellen](overview-ediscovery-20.md#advanced-ediscovery-alignment-with-the-electronic-discovery-reference-model).

[![Modelplakat: Advanced eDiscovery arkitektur i Microsoft 365.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Få vist som et billede](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Download som en PDF-fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Download som Visio fil](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)
