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
description: Brug eDiscovery-sager på Microsoft Purview-overholdelsesportalen til at administrere organisationens juridiske undersøgelse.
ms.openlocfilehash: 28dead35cce2102cfd826fa1505cdd620e4a1b25
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999778"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>Administrer juridiske undersøgelser i Microsoft 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Organisationer har mange grunde til at reagere på en sag, der involverer bestemte direktører eller andre medarbejdere i organisationen. Dette kan omfatte hurtigt at finde og gemme yderligere undersøgelsesspecifikke oplysninger i mail, dokumenter, chatsamtaler og andre indholdsplaceringer, der bruges af personer i deres daglige arbejdsopgaver. Du kan udføre disse og mange andre lignende aktiviteter ved hjælp af eDiscovery-sagsværktøjerne i Security and Compliance Center.
  
**Vil du gerne vide, hvordan Microsoft administrerer sine eDiscovery-undersøgelser?** Her er et [teknisk whitepaper](https://go.microsoft.com/fwlink/?linkid=852161) , som du kan downloade, og som forklarer, hvordan vi bruger de samme søge- og undersøgelsesværktøjer til at administrere vores interne eDiscovery-arbejdsproces.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>Administrer juridiske undersøgelser med eDiscovery-sager

Med eDiscovery-sager kan du styre, hvem der kan oprette, få adgang til og administrere eDiscovery-sager i din organisation. Brug sager til at tilføje medlemmer og styre, hvilke typer handlinger de kan udføre, placere en venteposition på indholdsplaceringer, der er relevante for en juridisk sag, og bruge værktøjet Indholdssøgning til at søge efter indhold, der kan reagere på din sag. Derefter kan du også eksportere og downloade disse resultater til yderligere undersøgelse af eksterne korrekturlæsere.
  
- [Administrer din eDiscovery-arbejdsproces](./get-started-core-ediscovery.md) ved at oprette og bruge eDiscovery-sager til alle juridiske undersøgelser, din organisation skal foretage.

- [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md) til at styre, hvem der kan oprette og administrere eDiscovery-sager i din organisation.

- [Konfigurer overholdelsesgrænser](set-up-compliance-boundaries.md) for at styre de brugerindholdsplaceringer, som eDiscovery-ledere kan søge efter.

- [Søg efter indhold](search-for-content.md) i din organisation.

### <a name="use-scripts-for-advanced-scenarios"></a>Brug scripts til avancerede scenarier

Ligesom i det forrige afsnit, der viste scripts til indholdssøgningsscenarier, har vi også oprettet nogle PowerShell-scripts til Security & Compliance Center for at hjælpe dig med at administrere eDiscovery-sager.
  
- [Opret en eDiscovery-ventepositionsrapport](create-a-report-on-holds-in-ediscovery-cases.md) , der indeholder oplysninger om alle ventepositioner, der er knyttet til eDiscovery-sager i din organisation.

- [Føj postkasser og OneDrive placeringer](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) for en liste over brugere til eDiscovery-venteposition.
  
## <a name="manage-legal-investigations-with-the-ediscovery-premium-solution-in-microsoft-365"></a>Administrer juridiske undersøgelser med eDiscovery-løsningen (Premium) i Microsoft 365

Microsoft Purview eDiscovery-løsningen (Premium) i Microsoft 365 bygger på de eksisterende eDiscovery- og analysefunktioner i Office 365. Denne nye løsning, *der kaldes eDiscovery (Premium),* indeholder en komplette arbejdsproces, hvor du kan bevare, indsamle, gennemse, analysere og eksportere indhold, der reagerer på din organisations interne og eksterne undersøgelser. Det giver også juridiske teams mulighed for at administrere hele arbejdsprocessen for meddelelse om juridisk venteposition for at kommunikere med tilsynsførende, der er involveret i en sag.

eDiscovery (Premium) kræver et E5-abonnement til din Microsoft 365 eller Office 365 organisation. Du kan finde flere oplysninger om licenser under [Konfigurer eDiscovery (Premium)](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

Her er et hurtigt overblik over den indbyggede arbejdsproces i eDiscovery (Premium). Du kan finde flere oplysninger under [Administrer arbejdsprocessen for eDiscovery (Premium).](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)

- [Opret en sag](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) for at komme i gang.

- [Administrer vogtere](managing-custodians.md) ved at føje dem til en sag og placere indhold i deres postkasse, OneDrive konto og Microsoft Teams, de er medlemmer af.

- [Administrer kommunikation](managing-custodian-communications.md) med tilsynsførende ved at automatisere meddelelsesprocessen for juridisk venteposition.

- [Indeksér data om forældremyndigheden](processing-data-for-case.md) , og ret indekseringsfejl, så du effektivt kan indsamle data til dine undersøgelser.

- [Indsaml data](collecting-data-for-ediscovery.md) for en sag, og [føj dem til et gennemsynssæt](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) med henblik på yderligere undersøgelse.

- [Få vist](view-documents-in-review-set.md) dokumenter, [forespørg om](review-set-search.md) data, og [mærk](tagging-documents.md) elementer i et korrektursæt.

- [Analysér sagsdata](analyzing-data-in-review-set.md) med avancerede analyseværktøjer.

- [Eksportér sagsdata](exporting-data-ediscover20.md) til gennemsyn af eksterne rådgivere.

- [Administrer langvarige job](managing-jobs-ediscovery20.md) i eDiscovery (Premium).