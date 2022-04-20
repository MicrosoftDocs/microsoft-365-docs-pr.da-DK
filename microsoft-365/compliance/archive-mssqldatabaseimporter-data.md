---
title: Konfigurer en connector til arkivering af data fra MICROSOFT SQL Database
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra MS SQL Database. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: d1c33a57fbbf9fba5a097b0affbb7e5fcea21a55
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937207"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>Konfigurer en connector til arkivering af data fra MICROSOFT SQL Database

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra MS SQL Database til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en MS SQL Database Importer-connector, der er konfigureret til at hente elementer fra en database ved hjælp af en XML-konfigurationsfil og importere disse elementer til Microsoft 365. Connectoren konverterer indhold fra MS SQL Database til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når indhold fra MS SQL Database gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en MS SQL Database-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-the-ms-sql-data"></a>Oversigt over arkivering af MS SQL-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere MS-SQL data i Microsoft 365.

![Arkivering af arbejdsproces for MS SQL-data.](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Din organisation arbejder sammen med en MS SQL Database-udbyder om at konfigurere et MS SQL Database-websted.

2. Hver 24. time kopieres MS SQL Database elementer til Veritas Merge1-webstedet. Connectoren konverterer også dette indhold til et mailformat.

3. Den MS SQL Database Importér-connector, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede MS SQL Database-elementer til bestemte brugeres postkasser ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **MS SQL Database Importér** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle elementer fra MS-SQL Database indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter MS SQL Database-importconnectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>Trin 1: Konfigurer MS SQL Database Importer-connectoren

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til MS SQL Database.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik derefter på **DataconnectorsMS** >  **SQL Database Importer**.

2. Klik på **Tilføj ny connector** på siden **MED SQL DATABASE-importprogrambeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer MS SQL Database Importer-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere MS SQL Database Importer-connectoren på Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer MS SQL Database-importprogrammet, i [Brugervejledningen til connectors fra tredjepart, Flet1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning **på siden Tilknyt MS-SQL Database importbrugere til Microsoft 365 brugere**. MS SQL Database-elementerne indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>Trin 4: Overvåg MS SQL Database Importer-connectoren

Når du har oprettet MS SQL Database Importer-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **connectoren MS SQL Database** **Importér** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.