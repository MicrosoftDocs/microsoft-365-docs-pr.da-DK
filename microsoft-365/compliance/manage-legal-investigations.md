---
title: Administrer juridiske undersøgelser i Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: Brug eDiscovery-sager i Microsoft 365 Overholdelsescenter til at administrere din organisations juridiske undersøgelse.
ms.openlocfilehash: fc4e89645ef1912c33ab89ec190c87dc9c8a8965
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588935"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Administrer juridiske undersøgelser i Microsoft 365

Organisationer har mange grunde til at besvare en juridisk sag med visse ledere eller andre medarbejdere i organisationen. Dette kan omfatte hurtigt at finde og bevare til yderligere undersøgelse-specifikke oplysninger i mails, dokumenter, chatsamtaler og andre indholdsplaceringer, der bruges af personer i deres daglige arbejdsopgaver. Du kan udføre disse og mange andre lignende aktiviteter ved hjælp af eDiscovery-sagsværktøjerne i Security and Compliance Center.
  
**Vil du vide, hvordan Microsoft administrerer sine eDiscovery-undersøgelser?** Here's a [technical white paper you](https://go.microsoft.com/fwlink/?linkid=852161) can download that explains how we use the same search and investigation tools to manage our internal eDiscovery workflow.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Administrer juridiske undersøgelser med eDiscovery-sager

Med eDiscovery-sager kan du styre, hvem der kan oprette, få adgang til og administrere eDiscovery-sager i din organisation. Use cases to add members and control what types of actions they can perform, placer a hold on content locations relevant to a legal case, and use the Content Search tool to search the locations on hold for content that might be responsive to your case. Derefter kan du også eksportere og hente disse resultater, så eksterne korrekturlæsere kan undersøge dem yderligere.
  
- [Administrer din eDiscovery-arbejdsproces](./get-started-core-ediscovery.md) ved at oprette og bruge eDiscovery-sager til enhver juridisk undersøgelse, som din organisation skal foretage.

- [Tildel eDiscovery-tilladelser for](assign-ediscovery-permissions.md) at styre, hvem der kan oprette og administrere eDiscovery-sager i din organisation.

- [Konfigurer overholdelsesgrænser til](set-up-compliance-boundaries.md) at styre de placeringer af indhold, som eDiscovery-ledere kan søge efter.

- [Søg efter indhold](search-for-content.md) i din organisation.

### <a name="use-scripts-for-advanced-scenarios"></a>Bruge scripts til avancerede scenarier

Ligesom i det forrige afsnit, der opliste scripts til scenarier med indholdssøgning, har vi også oprettet nogle Security & Compliance Center PowerShell-scripts, der kan hjælpe dig med at administrere eDiscovery-sager.
  
- [Opret en rapport om eDiscovery-venteposition,](create-a-report-on-holds-in-ediscovery-cases.md) der indeholder oplysninger om alle ventepositioner, der er knyttet til eDiscovery-sager i din organisation.

- [Tilføj postkasser og OneDrive for en](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) liste over brugere til en eDiscovery-venteposition.
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>Administrer retsundersøgelser med den Advanced eDiscovery løsning på Microsoft 365

Løsningen Advanced eDiscovery i Microsoft 365 bygger på de eksisterende eDiscovery- og analyseegenskaber i Office 365. Denne nye løsning, kaldet *Advanced eDiscovery*, giver en ende-til-en-arbejdsproces til at bevare, indsamle, gennemse, analysere og eksportere indhold, der er dynamiske på din organisations interne og eksterne undersøgelser. Det giver også juridiske teams mulighed for at administrere hele arbejdsprocessen for meddelelser om retsligt hold, så de kan kommunikere med personer, der er involveret i en sag.

Advanced eDiscovery kræver et E5-abonnement til din Microsoft 365 eller Office 365 organisation. Du kan finde flere oplysninger om licenser [under Konfigurer Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Her er en hurtig oversigt over den indbyggede arbejdsproces i Advanced eDiscovery. Du kan finde flere oplysninger [i Advanced eDiscovery arbejdsprocessen](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow).

- [Opret en sag for](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) at komme i gang.

- [Administrer familiemedlemmer ved](managing-custodians.md) at føje dem til en sag og sætte indhold i retslig venteposition i deres postkasse, OneDrive-konto og Microsoft Teams, som de er medlem af.

- [Administrer kommunikation](managing-custodian-communications.md) med overensstemmelsesmedarbejdere ved at automatisere meddelelsesprocessen for retslig venteposition.

- [Indeksering af data, der](processing-data-for-case.md) kan håndteres, og ret indekseringsfejl, så du effektivt kan indsamle data til dine undersøgelser.

- [Indsaml data](collecting-data-for-ediscovery.md) for en sag, [og føj den til et revisionssæt](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) til yderligere undersøgelse.

- [Få](view-documents-in-review-set.md) vist dokumenter, [forespørgselsdata](review-set-search.md) og [mærke](tagging-documents.md) elementer i et korrektursæt.

- [Analysér sagsdata](analyzing-data-in-review-set.md) med avancerede analyseværktøjer.

- [Eksportér sagsdata](exporting-data-ediscover20.md) til gennemgang af en ekstern advokat.

- [Administrer langsigtede job i](managing-jobs-ediscovery20.md) Advanced eDiscovery.