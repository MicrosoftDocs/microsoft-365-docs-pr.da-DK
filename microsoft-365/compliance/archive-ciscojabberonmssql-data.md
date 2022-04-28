---
title: Konfigurer en connector til arkivering af Cisco Jabber på MS SQL data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere Cisco Jabber på MS SQL data fra Veritas i Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: ef9586c0e860db727bea53651d70777e7c606498
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099779"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Konfigurer en connector til arkivering af Cisco Jabber på MS SQL-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Cisco Jabber-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en [Cisco Jabber-connector](https://globanet.com/jabber/), der er konfigureret til at hente elementer fra Jabbers MS-SQL Database, f.eks. 1:1 chatbeskeder og gruppechats, og derefter importere disse elementer til Microsoft 365. Connectoren henter data fra Cisco Jabbers MS-SQL Database, behandler dem, og konverterer indholdet fra en brugers Cisco Jabber-konto til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Cisco Jabber-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Cisco Jabber-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Oversigt over arkivering af Cisco Jabber-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Cisco Jabber på MS-SQL data i Microsoft 365.

![Arkivering af arbejdsproces for Cisco Jabber-data.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Din organisation arbejder sammen med Cisco om at konfigurere en Cisco Jabber på MS-SQL Database.

2. En gang hver 24 timer kopieres Cisco Jabber-elementer fra MS SQL Database til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af chatbeskeder til et mailformat.

3. Cisco Jabber-connectoren, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører elementerne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Den automatiske brugertilknytning som connector importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for det, der er beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber på MS SQL** i brugerpostkasserne, og meddelelseselementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Cisco Jabber-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver deltager.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Konfigurer en MS-SQL Database til at hente Jabber-elementer fra, før du opretter connectoren i trin 1. Du skal angive forbindelsesindstillingerne for MS-SQL Database, når du konfigurerer Cisco Jabber-connectoren i Trin 2. Du kan få flere oplysninger i [brugervejledningen til Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- Den bruger, der opretter Cisco Jabber-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Trin 1: Konfigurer Cisco Jabber på MS SQL-connector

Det første trin er at få adgang til **dataconnectors på overholdelsesportalen** og oprette en connector til Cisco Jabber på MS SQL data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/)og klik derefter på **Data connectorsCisco** >  **Jabber på MS SQL**.

2. Klik på **Tilføj connector** **på siden Cisco Jabber på MS SQL** produktbeskrivelse.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Cisco Jabber på MS SQL connector på Veritas Merge1-webstedet

Det andet trin er at konfigurere Cisco Jabber på MS SQL connector på Veritas Merge1 site. Du kan få oplysninger om, hvordan du konfigurerer Cisco Jabber på MS SQL connector, i [Brugervejledning til Flette1 tredjepartsconnectorer](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre den connector, der er konfigureret i overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning **på siden Map Cisco Jabber på MS SQL brugere til Microsoft 365 brugere**. Cisco Jabber på MS SQL elementer omfatter en egenskab kaldet *Email*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Trin 4: Overvåg Cisco Jabber-connectoren

Når du har oprettet Cisco Jabber på MS SQL-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Connectorer,** og vælg derefter **Cisco Jabber på MS SQL** connector for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
