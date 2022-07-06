---
title: Konfigurer en 17a-4 DataParser-connector til arkivering af FX Connect-data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 FX Connect DataParser-connector til at importere og arkivere FX Connect-data i Microsoft 365.
ms.openlocfilehash: 99e9a34bff72861102a1097aad21e2b4c3c84391
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640736"
---
# <a name="set-up-a-connector-to-archive-data-from-fx-connect"></a>Konfigurer en connector til arkivering af data fra FX Connect

Brug [FX Connect DataParser](https://www.17a-4.com/dataparser-roadmap/) fra 17a-4 LLC til at importere og arkivere data fra FX Opret forbindelse til brugerpostkasser i din Microsoft 365-organisation. DataParser indeholder en FX Connect-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. FX Connect DataParser-connectoren konverterer FX Connect-data til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når FX Connect-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Hvis du bruger en FX Connect-connector til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-fx-connect-data"></a>Oversigt over arkivering af FX Connect-data

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere FX Connect-data i Microsoft 365.

![Arkivering af arbejdsproces for FX Connect-data fra 17a-4.](../media/FXConnectDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere FX Connect DataParser.

2. FX Connect-elementer indsamles regelmæssigt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Fx Connect DataParser-connectoren, som du opretter i Microsoft Purview-compliance-portal opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **FX Connect DataParser** i brugerpostkasserne, og FX Connect-elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle FX Connect-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter FX Connect DataParser-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-a-fx-connect-dataparser-connector"></a>Trin 1: Konfigurer en FX Connect DataParser-connector

Det første trin er at få adgang til siden Dataconnectors på overholdelsesportalen og oprette en 17a-4-connector til FX Connect-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Dataconnectors** > **FX Connect DataParser**.

2. Klik på **Tilføj connector** på siden **FX Connect DataParser-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden OPRET forbindelse til FX Connect DataParser.

## <a name="step-2-configure-the-fx-connect-dataparser-connector"></a>Trin 2: Konfigurer FX Connect DataParser-connectoren

Arbejd med 17a-4-understøttelse for at konfigurere FX Connect DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

FX Connect DataParser-connectoren knytter automatisk brugere til deres Microsoft 365-mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-fx-connect-dataparser-connector"></a>Trin 4: Overvåg FX Connect DataParser-connectoren

Når du har oprettet en FX Connect DataParser-connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter den FX Connect DataParser-connector, du oprettede, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
