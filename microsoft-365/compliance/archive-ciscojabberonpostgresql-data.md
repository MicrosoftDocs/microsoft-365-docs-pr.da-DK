---
title: Konfigurer en connector for at arkivere Cisco Jabber på PostgreSQL-data i Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan du konfigurerer og bruger en connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Cisco Jabber på PostgreSQL for at Microsoft 365.
ms.openlocfilehash: 2e573bcc6c39e9188ec09f05190c124bd904ef98
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996322"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>Konfigurer en connector til arkivering af Cisco Jabber på PostgreSQL-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Cisco Jabber-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [Cisco Jabber på PostgreSQL-connector](https://www.veritas.com/insights/merge1/jabber), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Connectoren konverterer indholdet, f.eks. meddelelser, chats og delt indhold fra Cisco Jabber på PostgreSQL, til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Cisco Jabber på PostgreSQL-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner som f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en Cisco Jabber på PostgreSQL-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>Oversigt over arkivering af Cisco Jabber på PostgreSQL-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Cisco Jabber på PostgreSQL-data i Microsoft 365.

![Arkivering af arbejdsproces for Cisco Jabber på PostgreSQL-data.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Din organisation arbejder sammen med Cisco Jabber på PostgreSQL om at konfigurere et Cisco Jabber på PostgreSQL-webstedet.

2. En gang hver 24 timer kopieres Cisco Jabber på PostgreSQL-elementer til Veritas Merge1-webstedet. Connectoren konverterer også Cisco Jabber på PostgreSQL-elementer til et mailformat.

3. Cisco Jabber på PostgreSQL-connector, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører Jabber-indholdet til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber på PostgreSQL** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle Jabber-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-connectors. For at gøre dette skal du kontakte [Veritas Kundesupport](https://www.veritas.com/content/support/en_US). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter Cisco Jabber på PostgreSQL-connectoren i Trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>Trin 1: Konfigurer Cisco Jabber på PostgreSQL-connector

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til Jabber-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Dataconnectors** &gt; **Cisco Jabber på PostgreSQL**.

2. Klik på **Tilføj connector** **på siden Cisco Jabber på PostgreSQL-produktbeskrivelsen**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Cisco Jabber på PostgreSQL på Veritas Merge1 site

Det andet trin er at konfigurere Cisco Jabber på PostgreSQL-connectoren på Veritas Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer Cisco Jabber på PostgreSQL-connectoren, i [Brugervejledning til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning **på siden Map Cisco Jabber på PostgreSQL-brugere til Microsoft 365 brugere**. Cisco Jabber på PostgreSQL-elementer omfatter en egenskab kaldet *Email*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>Trin 4: Overvåg Cisco Jabber på PostgreSQL-connectoren

Når du har oprettet Cisco Jabber på PostgreSQL-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **Cisco Jabber på PostgreSQL-connectoren** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
