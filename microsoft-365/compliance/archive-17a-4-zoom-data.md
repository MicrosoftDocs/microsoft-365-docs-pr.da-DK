---
title: Konfigurer en connector for at arkivere Zoom-data i Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 Zoom DataParser-connector til at importere og arkivere Zoom-data i Microsoft 365.
ms.openlocfilehash: b5168ae4a62e5a519ca911dffea932edd8a0a2ab
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65316760"
---
# <a name="set-up-a-connector-to-archive-zoom-data"></a>Konfigurer en connector til arkivering af Zoom-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug [Zoom DataParser](https://www.17a-4.com/dataparser/) fra 17a-4 LLC til at importere og arkivere data fra Zoom-platformen til brugerpostkasser i din Microsoft 365 organisation. DataParser indeholder en Zoom-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. Connectoren Zoom DataParser konverterer Zoom-data til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når Zoom-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation venteposition, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikationsoverholdelse. Brug af en Zoom-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-zoom-data"></a>Oversigt over arkivering af zoomdata

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere Zoom-data i Microsoft 365.

![Arkivering af arbejdsproces for zoomdata fra 17a-4.](../media/ZoomDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere Zoom DataParser.

2. Zoomelementer indsamles regelmæssigt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Den Zoom DataParser-connector, du opretter i Microsoft Purview-compliance-portal opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **Zoom DataParser** i brugerpostkasserne, og Zoom-elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Zoom-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter connectoren Zoom DataParser i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-a-zoom-dataparser-connector"></a>Trin 1: Konfigurer en Zoom DataParser-connector

Det første trin er at få adgang til siden Dataconnectors på overholdelsesportalen og oprette en 17a-4-connector til Zoom-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsZoom** >  **DataParser**.

2. Klik på **Tilføj connector** på siden **Zoom DataParser-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og udfør trinnene i guiden Zoom DataParser-forbindelse.

## <a name="step-2-configure-the-zoom-dataparser-connector"></a>Trin 2: Konfigurer connectoren Zoom DataParser

Arbejd med understøttelse af 17a-4 for at konfigurere Zoom DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

Connectoren Zoom DataParser knytter automatisk brugerne til deres Microsoft 365 mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-zoom-dataparser-connector"></a>Trin 4: Overvåg connectoren Zoom DataParser

Når du har oprettet en Zoom DataParser-connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter connectoren Zoom DataParser, som du oprettede, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
