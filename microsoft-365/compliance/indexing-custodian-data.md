---
title: Avanceret indeksering af data fra tilsynsførende
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
description: Når en tilsynsførende føjes til en eDiscovery-sag (Premium), behandles alt indhold, der anses for delvist indekseret, for at gøre det fuldt søgbart.
ms.openlocfilehash: 3c6f0079f87dbc4711fed7d776204c287d5b5865
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64931974"
---
# <a name="advanced-indexing-of-custodian-data"></a>Avanceret indeksering af data fra tilsynsførende

Når en tilsynsførende føjes til en eDiscovery-sag (Premium), genindekseres alt indhold, der blev betragtet som delvist indekseret eller havde indekseringsfejl. Denne genindekseringsproces kaldes *avanceret indeksering*. Der er mange årsager til, at indholdet er delvist indekseret eller har indekseringsfejl. Dette omfatter billedfiler eller tilstedeværelsen af billeder i en fil, filtyper, der ikke understøttes, eller indekseringsgrænser for filstørrelse. For SharePoint filer kører avanceret indeksering kun på elementer, der er markeret som delvist indekserede, eller som har indekseringsfejl. I Exchange markeres mails, der har vedhæftede billedfiler, ikke som delvist indekserede eller med indekseringsfejl. Det betyder, at disse filer ikke genindekseres af den avancerede indekseringsproces.

Hvis du vil vide mere om behandling af support og delvist indekserede elementer, skal du se:

- [Understøttede filtyper i eDiscovery (Premium)](supported-filetypes-ediscovery20.md)

- [Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md)

- [Filformater, der er indekseret af Exchange Search](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [Standardfilnavneudvidelser og fortolkede filtyper i SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>Visning af avancerede indekseringsresultater

Når den avancerede indekseringsproces er fuldført, kan du få en forståelse af, hvor effektiv oparbejdningen er.  I visningen Avancerede indekseringsresultater under fanen **Behandling** for en sag viser grafen antallet af elementer, der er føjet til *hybridindekset*.  Hybridindekset er det steder, hvor eDiscovery (Premium) gemmer det genbehandlede indhold.

Denne visning indeholder også antallet af elementer, der kræver afhjælpning, og en anden graf over fejl efter filtype. Du kan finde flere oplysninger under:

- [Fejlafhjælpning under behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [Afhjælpning af fejl med et enkelt element](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>Opdaterer det avancerede indeks for tilsynsførende

Når en tilsynsførende føjes til en eDiscovery-sag (Premium), genbehandles alle delvist indekserede elementer. Men efterhånden som tiden går, kan der føjes flere delvist indekserede elementer til en brugers postkasse eller OneDrive konto.  Hvis det er nødvendigt, kan du opdatere indekset for en bestemt tilsynsførende. Du kan finde flere oplysninger [under Administrer vogtere i en eDiscovery-sag (Premium).](manage-new-custodians.md#reindex-custodian-data) Du kan også opdatere indekset for alle tilsynsførende i en sag ved at klikke på **indekset Opdater** under fanen **Behandling** .

> [!NOTE]
> Opdatering af tilsynsførende indekser er en langvarig proces. Det anbefales, at du ikke opdaterer indeks mere end én gang om dagen i et tilfælde.
