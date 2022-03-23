---
title: Søge efter indhold
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
description: Brug værktøjet eDiscovery til indholdssøgning i Microsoft 365 Overholdelsescenter til hurtigt at finde mails i Exchange-postkasser, dokumenter på SharePoint-websteder og OneDrive-placeringer og chatsamtaler i Skype for Business.
ms.openlocfilehash: 21e07f09c21bbf0196b6ba113b82ec3030aada32
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587313"
---
# <a name="search-for-content-using-the-content-search-tool"></a>Søge efter indhold ved hjælp af værktøjet Indholdssøgning

Brug værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter til hurtigt at finde mails i Exchange-postkasser, dokumenter på SharePoint-websteder og OneDrive-placeringer og chatsamtaler i Skype for Business. Du kan bruge værktøjet til indholdssøgning til at søge efter mails, dokumenter og chatsamtaler i samarbejdsværktøjer som f.eks Microsoft Teams og Microsoft 365 Grupper.
  
## <a name="search-for-content"></a>Søge efter indhold

Det første trin er at begynde at bruge værktøjet Indholdssøgning til at vælge indholdsplaceringer til søgning og konfiguration af en nøgleordsforespørgsel til at søge efter bestemte elementer. Eller du kan bare lade forespørgslen være tom og returnere alle elementer på destinationsplaceringerne.
  
- [Oprette og køre en](content-search.md) indholdssøgning

- [Opbygge søgeforespørgsler og bruge betingelser til](keyword-queries-and-search-conditions.md) at indsnævre din søgning

- [Funktionsreference](content-search-reference.md) til indholdssøgning

- [Konfigurer filtrering af søgetilladelser,](permissions-filtering-for-content-search.md) så en eDiscovery-leder kun kan søge i undersæt af postkasser eller websteder i din organisation

- [Søg i skybaserede postkasser](search-cloud-based-mailboxes-for-on-premises-users.md) efter lokale brugere i Microsoft 365

- [Få vist nøgleordsstatistik](view-keyword-statistics-for-content-search.md) for resultaterne af en søgning, og indskrænp derefter forespørgslen, hvis det er nødvendigt

- [Søg efter tredjepartsdata,](use-content-search-to-search-third-party-data-that-was-imported.md) som organisationen har importeret til Microsoft 365

- [Bevar Bcc-modtagere](/exchange/policy-and-compliance/holds/preserve-bcc-recipients-and-group-members) , så du kan søge efter dem

## <a name="perform-actions-on-content-you-find"></a>Udføre handlinger for indhold, du finder

Når du har kørt en søgning og afgrænset den efter behov, er næste trin at gøre noget med de resultater, der returneres af søgningen. Du kan eksportere og hente resultaterne til din lokale computer, eller i tilfælde af mailangreb på din organisation, kan du slette resultaterne af en søgning fra brugerpostkasser.
  
- [Eksportere resultaterne af en indholdssøgning](export-search-results.md) og hente dem til din lokale computer

- [Søge efter og slette mails, f.eks](search-for-and-delete-messages-in-your-organization.md). meddelelser, der indeholder virus, skadelige vedhæftede filer eller phishingmeddelelser

- [Eksportere en rapport](export-a-content-search-report.md) om resultaterne af en indholdssøgning uden at eksportere de faktiske resultater

## <a name="learn-more-about-content-search"></a>Få mere at vide om indholdssøgning

Indholdssøgning er nem at bruge, men det er også et effektivt værktøj. Der sker meget bag kulisserne. Jo mere du ved om det og forstår dets funktionsmåde og begrænsninger, jo mere vellykket kommer det til at bruge det til din organisations behov for søgning og undersøgelse. Få mere at vide om:
  
- [Begrænsninger for indholdssøgning](limits-for-content-search.md), f.eks. det maksimale antal søgninger, du kan køre ad gangen, og det maksimale antal indholdsplaceringer, du kan medtage i en enkelt søgning

- [Anslåede og faktiske søgeresultater](differences-between-estimated-and-actual-ediscovery-search-results.md) samt årsagerne til, at der kan være forskelle mellem dem, når du eksporterer og downloader søgeresultater

- [Delvist indekserede elementer i Exchange og SharePoint](partially-indexed-items-in-content-search.md), og hvordan du medtager eller udelader dem, når du eksporterer og downloader søgeresultater

- [Undersøg delvist indekserede elementer](investigating-partially-indexed-items-in-ediscovery.md) og afgør, om din organisation er eksponeret for dem

- [Dupliker i søgeresultater,](de-duplication-in-ediscovery-search-results.md) som du kan aktivere, når du eksporterer mails, som er resultaterne af en søgning

## <a name="use-scripts-for-advanced-scenarios"></a>Bruge scripts til avancerede scenarier

Nogle gange skal du udføre mere avancerede, komplekse og gentagne indholdssøgningsopgaver. I disse tilfælde er det nemmere og hurtigere at bruge kommandoer i Security & Compliance Center PowerShell. For at gøre dette nemmere har vi oprettet en række Security & Compliance Center PowerShell-scripts, der kan hjælpe dig med at udføre komplekse indholdssøgningsrelaterede opgaver.

- [Søg i specifikke postkasser og webstedsmapper](use-content-search-for-targeted-collections.md) (kaldet en målrettet samling), når du er sikker på, at elementer, der reagerer på en sag, findes i den pågældende mappe 

- [Søg i postkassen og OneDrive efter](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md) en liste over brugere

- [Opret, rapportér om og slet flere søgninger for hurtigt](create-report-on-and-delete-multiple-content-searches.md) og effektivt at identificere og slette søgedata

- [Klon en indholdssøgning](clone-a-content-search.md) , og sammenlign hurtigt resultaterne af forskellige søgeordsforespørgsler på de samme indholdsplaceringer; eller brug scriptet for at spare tid ved ikke at skulle angive et stort antal indholdsplaceringer igen, når du opretter en ny søgning
