---
title: Konfigurer en 17a-4 DataParser-connector til arkivering af FX-Forbind data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 FX-Forbind DataParser-connector til at importere og arkivere FX-Forbind data i Microsoft 365.
ms.openlocfilehash: 6317657228c00a4dbb6c73d5211b13f4c4d2c790
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940791"
---
# <a name="set-up-a-connector-to-archive-data-from-fx-connect"></a>Konfigurer en connector til arkivering af data fra FX-Forbind

Brug [FX-Forbind DataParser](https://www.17a-4.com/dataparser-roadmap/) fra 17a-4 LLC til at importere og arkivere data fra FX-Forbind til brugerpostkasser i din Microsoft 365 organisation. DataParser indeholder en FX-Forbind-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. FX Forbind DataParser-connectoren konverterer FX Forbind data til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når FX-Forbind data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en FX-Forbind-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-fx-connect-data"></a>Oversigt over arkivering af FX Forbind data

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere FX-Forbind data i Microsoft 365.

![Arkivering af arbejdsproces for FX-Forbind data fra 17a-4.](../media/FXConnectDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere FX-Forbind DataParser.

2. Fx Forbind varer indsamles jævnligt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Fx-Forbind DataParser-connectoren, som du opretter på Microsoft Purview-overholdelsesportalen, opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **FX Forbind DataParser** i brugerpostkasserne, og elementerne i FX-Forbind importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle FX-Forbind-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter FX-Forbind DataParser-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-a-fx-connect-dataparser-connector"></a>Trin 1: Konfigurer en FX Forbind DataParser-connector

Det første trin er at få adgang til siden Dataconnectors på overholdelsesportalen og oprette en 17a-4-connector til FX-Forbind data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsFX** >  **Forbind DataParser**.

2. Klik på **Tilføj connector** **på siden MED Forbind DataParser-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden FX Forbind DataParser-forbindelse.

## <a name="step-2-configure-the-fx-connect-dataparser-connector"></a>Trin 2: Konfigurer FX Forbind DataParser-connectoren

Arbejd med 17a-4-understøttelse for at konfigurere FX-Forbind DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

FX Forbind DataParser-connectoren knytter automatisk brugere til deres Microsoft 365 mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-fx-connect-dataparser-connector"></a>Trin 4: Overvåg FX-Forbind DataParser-connectoren

Når du har oprettet en FX-Forbind DataParser-connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter den FX-Forbind DataParser-connector, du har oprettet, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
