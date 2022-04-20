---
title: Søg efter indhold
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
description: Brug eDiscovery-værktøjet til indholdssøgning på Microsoft Purview-overholdelsesportalen til hurtigt at finde mails i Exchange postkasser, dokumenter på SharePoint websteder og på OneDrive placeringer samt chatsamtaler i Skype for Business.
ms.openlocfilehash: 4efe2f4b4735005c10fd59e618bb6ecc8be51ec0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993638"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Søg efter indhold ved hjælp af indholdssøgeværktøjet

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug indholdssøgeværktøjet på Microsoft Purview-overholdelsesportalen til hurtigt at finde mails i Exchange postkasser, dokumenter på SharePoint websteder og på OneDrive placeringer samt chatsamtaler i Skype for Business. Du kan bruge værktøjet til indholdssøgning til at søge efter mail, dokumenter og chatsamtaler i samarbejdsværktøjer, f.eks. Microsoft Teams og Microsoft 365-grupper.
  
## <a name="search-for-content"></a>Søg efter indhold

Det første trin er at begynde at bruge indholdssøgeværktøjet til at vælge indholdsplaceringer, hvor der skal søges efter og konfigureres en nøgleordsforespørgsel for at søge efter bestemte elementer. Du kan også bare lade forespørgslen være tom og returnere alle elementer på målplaceringerne.
  
- [Opret og kør](content-search.md) en indholdssøgning

- [Opret søgeforespørgsler, og brug betingelser](keyword-queries-and-search-conditions.md) til at indsnævre din søgning

- [Funktionsreference](content-search-reference.md) til indholdssøgning

- [Konfigurer filtrering af søgetilladelser](permissions-filtering-for-content-search.md) , så en eDiscovery-administrator kun kan søge i undersæt af postkasser eller websteder i din organisation

- [Søg i skybaserede postkasser](search-cloud-based-mailboxes-for-on-premises-users.md) efter brugere i det lokale miljø i Microsoft 365

- [Få vist nøgleordsstatistik](view-keyword-statistics-for-content-search.md) for resultaterne af en søgning, og afgræns derefter forespørgslen, hvis det er nødvendigt

- [Søg efter tredjepartsdata](use-content-search-to-search-third-party-data-that-was-imported.md), som din organisation har importeret til Microsoft 365

- [Bevar Bcc-modtagere](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) , så du kan søge efter dem

## <a name="perform-actions-on-content-you-find"></a>Udfør handlinger på det indhold, du finder

Når du har kørt en søgning og afgrænset den efter behov, er det næste trin at gøre noget med de resultater, der returneres af søgningen. Du kan eksportere og downloade resultaterne til din lokale computer eller i tilfælde af et mailangreb på din organisation, kan du slette resultaterne af en søgning fra brugerpostkasser.
  
- [Eksportér resultaterne af en indholdssøgning](export-search-results.md) , og download dem til din lokale computer

- [Søg efter og slet mails](search-for-and-delete-messages-in-your-organization.md), f.eks. meddelelser, der indholder en virus, farlige vedhæftede filer eller phishingmeddelelser

- [Eksportér en rapport](export-a-content-search-report.md) om resultaterne af en indholdssøgning uden at eksportere de faktiske resultater

## <a name="learn-more-about-content-search"></a>Få mere at vide om indholdssøgning

Indholdssøgning er nem at bruge, men det er også et effektivt værktøj. Bag kulisserne foregår der meget. Jo mere du ved om den og forstår dens funktionsmåde og dens begrænsninger, jo mere vellykket vil du bruge den til din organisations søge- og undersøgelsesbehov. Få mere at vide om:
  
- [Grænser for indholdssøgning](limits-for-content-search.md), f.eks. det maksimale antal søgninger, du kan køre på én gang, og det maksimale antal indholdsplaceringer, du kan inkludere i en enkelt søgning

- [Anslåede og faktiske søgeresultater](differences-between-estimated-and-actual-ediscovery-search-results.md) og årsagerne til, at der kan være forskelle mellem dem, når du eksporterer og downloader søgeresultater

- [Delvist indekserede elementer i Exchange og SharePoint](partially-indexed-items-in-content-search.md), og hvordan de medtages eller udelades, når du eksporterer og downloader søgeresultater

- [Undersøg delvist indekserede elementer](investigating-partially-indexed-items-in-ediscovery.md) , og fastlæg din organisations eksponering over for dem

- [Deduplikering i søgeresultater](de-duplication-in-ediscovery-search-results.md) , som du kan aktivere, når du eksporterer mails, der er resultatet af en søgning

## <a name="use-scripts-for-advanced-scenarios"></a>Brug scripts til avancerede scenarier

Nogle gange skal du udføre mere avancerede, komplekse og gentagne søgeopgaver for indhold. I disse tilfælde er det nemmere og hurtigere at bruge kommandoer i Security & Compliance Center PowerShell. For at gøre det nemmere har vi oprettet en række PowerShell-scripts til Security & Compliance Center for at hjælpe dig med at fuldføre opgaver, der er relateret til søgning i komplekst indhold.

- [Søg i bestemte postkasser og webstedsmapper](use-content-search-for-targeted-collections.md) (kaldet en  *målrettet* samling), når du er sikker på, at elementer, der svarer til en sag, er placeret i den pågældende mappe

- [Søg i postkassen og OneDrive placering](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) efter en liste over brugere

- [Opret, rapportér om og slet flere søgninger](create-report-on-and-delete-multiple-content-searches.md) for hurtigt og effektivt at identificere og slette søgedata

- [Klon en indholdssøgning](clone-a-content-search.md) , og sammenlign hurtigt resultaterne af forskellige nøgleordssøgningsforespørgsler, der kører på de samme indholdsplaceringer. eller brug scriptet til at spare tid ved ikke at skulle angive et stort antal indholdsplaceringer igen, når du opretter en ny søgning
