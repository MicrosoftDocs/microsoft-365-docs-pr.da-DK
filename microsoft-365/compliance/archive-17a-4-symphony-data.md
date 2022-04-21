---
title: Konfigurer en Symfoni DataParser-connector til arkivering af data i Microsoft 365
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
ms.collection: M365-security-compliance
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 Symfoni DataParser-connector til at importere og arkivere symfonidata i Microsoft 365.
ms.openlocfilehash: f783e5f9f405223493e43e7b9966be50c2e58f10
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996608"
---
# <a name="set-up-a-connector-to-archive-data-from-symphony"></a>Konfigurer en connector til arkivering af data fra Symfoni

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug [symfonidataparser](https://www.17a-4.com/Symphony-dataparser/) fra 17a-4 LLC til at importere og arkivere symfonikommunikationsdata til brugerpostkasser i din Microsoft 365 organisation. DataParser indeholder en Symfoni-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. Connectoren Symfoni DataParser konverterer symfonidata til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når Symfoni-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikationsoverholdelse. Brug af en Symfoni-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-symphony-data"></a>Oversigt over arkivering af symfonidata

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere Symfoni-data i Microsoft 365.

![Arkivering af arbejdsproces for symfonidata fra 17a-4.](../media/SymphonyDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere SymfonidataParser.

2. Symfonielementer indsamles jævnligt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Den Symfoni DataParser-connector, du opretter på Microsoft Purview-overholdelsesportalen, opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **SymfonidataParser** i brugerpostkasserne, og symfonielementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Hvert symfonielement indeholder denne egenskab, som udfyldes med mailadressen på hver deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter connectoren SymfoniDataParser i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-a-symphony-dataparser-connector"></a>Trin 1: Konfigurer en Symfoni DataParser-connector

Det første trin er at få adgang til siden Dataconnectors på overholdelsesportalen og oprette en 17a-4-connector til Symfoni-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsSymfoni** >  DataParser.

2. Klik på **Tilføj connector** på produktbeskrivelsessiden **SymfonidataParser**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden SymfonidataParser-forbindelse.

## <a name="step-2-configure-the-symphony-dataparser-connector"></a>Trin 2: Konfigurer Connectoren Symfoni DataParser

Arbejd med 17a-4 Support for at konfigurere Symfoni DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

Connectoren Symfoni DataParser knytter automatisk brugere til deres Microsoft 365 mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-symphony-dataparser-connector"></a>Trin 4: Overvåg Symfoni DataParser-connectoren

Når du har oprettet en Symfoni DataParser-connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter connectoren SymfonidataParser, som du har oprettet, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
