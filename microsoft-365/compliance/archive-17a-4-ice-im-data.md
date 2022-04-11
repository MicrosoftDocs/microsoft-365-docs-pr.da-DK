---
title: Konfigurer en connector til arkivering af ICE Forbind Chat-data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 ICE Forbind Chat DataParser-connector til at importere og arkivere ICE Forbind Chat-data i Microsoft 365.
ms.openlocfilehash: d300c3e3e5b9064a0844bf8069e0eaac174825e9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761787"
---
# <a name="set-up-a-connector-to-archive-ice-connect-chat-data"></a>Konfigurer en connector til arkivering af ICE Forbind Chat-data

Brug [ICE DataParser](https://www.17a-4.com/ice-dataparser/) fra 17a-4 LLC til at importere og arkivere data fra ICE Forbind Chat til brugerpostkasser i din Microsoft 365 organisation. DataParser indeholder en ICE Chat-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. ICE DataParser-connectoren konverterer ICE Forbind Chat-data til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når ICE Forbind Chat-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 funktioner til overholdelse af angivne standarder, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater samt kommunikation med overholdelse af angivne standarder. Brug af en ICE DataParser-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-ice-chat-data"></a>Oversigt over arkivering af ICE Chat-data

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere ICE Forbind Chat-data i Microsoft 365.

![Arkivering af arbejdsproces for ICE Forbind Chat-data fra 17a-4.](../media/ICEChatDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere ICE-dataparser.

2. Ice Forbind Chat-elementer indsamles jævnligt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Den ICE DataParser-connector, du opretter i Microsoft 365 Overholdelsescenter opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **ICE DataParser** i brugerpostkasserne, og ICE Forbind Chat-elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle ICE Forbind Chat-elementer indeholder denne ejendom, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter ICE DataParser-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors** i Microsoft 365 Overholdelsescenter. Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsoft 365 forpligtelser til overholdelse af angivne standarder og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-an-ice-dataparser-connector"></a>Trin 1: Konfigurer en ICE DataParser-connector

Det første trin er at få adgang til siden Dataconnectors i Microsoft 365 Overholdelsescenter og oprette en 17a-4-connector til ICE Forbind Chat-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Data connectorsICE** >  **DataParser**.

2. Klik på **Tilføj connector** på siden **ICE DataParser-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden ICE DataParser-forbindelse.

## <a name="step-2-configure-the-ice-dataparser-connector"></a>Trin 2: Konfigurer ICE DataParser-connectoren

Arbejd med understøttelse af 17a-4 for at konfigurere ICE DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

ICE DataParser-connectoren knytter automatisk brugere til deres Microsoft 365 mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-ice-dataparser-connector"></a>Trin 4: Overvåg ICE DataParser-connectoren

Når du har oprettet en ICE DataParser-connector, kan du få vist connectorstatussen i Microsoft 365 Overholdelsescenter.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter den ICE DataParser-connector, du oprettede, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
