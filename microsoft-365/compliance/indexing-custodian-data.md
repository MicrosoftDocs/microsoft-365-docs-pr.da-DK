---
title: Avanceret indeksering af data for oversigter
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
description: Når en inficeringsmand føjes til en Advanced eDiscovery sag, behandles alt indhold, der blev betragtet som delvist indekseret, for at gøre det fuldt søgbart.
ms.openlocfilehash: 1c43f55f399f69d58e05c073e688170d53480b42
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2021
ms.locfileid: "63588691"
---
# <a name="advanced-indexing-of-custodian-data"></a>Avanceret indeksering af data for oversigter

Når en hjælper føjes til en Advanced eDiscovery sag, bliver alt indhold, der blev betragtet som delvist indekseret eller havde indekseringsfejl, genindført. Denne indekseringsproces kaldes *Avanceret indeksering*. Der er mange årsager til, at indholdet er delvist indekseret eller har indekseringsfejl. Dette omfatter billedfiler eller tilstedeværelsen af billeder i en fil, ikke-understøttede filtyper eller begrænsninger for indeksering af filstørrelse. For SharePoint filer kører Avanceret indeksering kun på elementer, der er markeret som delvist indekserede, eller som har indekseringsfejl. I Exchange er de mails, der har vedhæftede billeder, ikke markeret som delvist indekserede eller med indekseringsfejl. Det betyder, at disse filer ikke bliver indekseret igen af avanceret indekseringsproces.

Hvis du vil have mere at vide om behandling af support og delvist indekserede elementer, skal du se:

- [Understøttede filtyper i Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md)

- [Filformater, der er indekseret Exchange Søg](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Standard for gennemsøgte filtypenavne og fortolkede filtyper i SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Vise avancerede indekseringsresultater

Når avanceret indeksering er fuldført, kan du få en forståelse af effektiviteten af genbehandling.  I visningen Avancerede indekseringsresultater på fanen **Behandler** for en sag viser grafen antallet af elementer, der er føjet til *hybridindekset*.  Hybridindekset er det sted Advanced eDiscovery lagrer det genbehandlede indhold.

Denne visning indeholder også det antal elementer, der kræver afhjælpning, og en anden graf over fejl efter filtype. Du kan finde flere oplysninger under:

- [Fejl der afhjælpes ved behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Afhjælpning af fejl i et enkelt element](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Opdatering af avanceret indeks for brugere, der skal opdateres

Når en leder føjes til en Advanced eDiscovery sag, bliver alle delvist indekserede elementer genbehandlet. Men efterhånden som tiden går, kan mere delvist indekserede elementer føjes til en brugers postkasse eller OneDrive konto.  Hvis det er nødvendigt, kan du opdatere indekset for en specifik opbevaringsmand. Du kan få mere at vide [under Administrer Advanced eDiscovery en sag](manage-new-custodians.md#reindex-custodian-data). Du kan også opdatere indekset for alle y-2-4-2016-2016 ved at klikke på indekset Opdater **på fanen** Behandler.

> [!NOTE]
> Opdatering af indeks over øvriske fejl er en lang løbende proces. Det anbefales, at du ikke opdaterer indeks mere end én gang om dagen i en sag.
