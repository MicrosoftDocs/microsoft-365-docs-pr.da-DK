---
title: Konfigurer en connector til arkivering af Jive-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere Jive-data fra Veritas i Microsoft 365. Med denne connector kan du arkivere tredjepartsdata i Microsoft 365, så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 2ad2d709a9257a1b14e50603240e8a3674c88d1a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624659"
---
# <a name="set-up-a-connector-to-archive-jive-data"></a>Konfigurer en connector til arkivering af Jive-data

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra samarbejdsplatformen til brugerpostkasser i din Microsoft 365-organisation. Veritas leverer en [Jive-connector](https://globanet.com/jive/) , der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og derefter importere disse elementer til Microsoft 365. Connectoren konverterer indhold som mails, chats og vedhæftede filer fra en brugers Jive-konto til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Jive-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Jive-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-jive-data"></a>Oversigt over arkivering af Jive-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Jive-dataene i Microsoft 365.

![Arkivering af arbejdsproces for Jive-data.](../media/JiveConnectorWorkflow.png)

1. Din organisation arbejder sammen med Jive om at konfigurere et Jive-websted.

2. En gang hver 24 timer kopieres varer fra Jive til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af Jive-elementer til et mailmeddelelsesformat.

3. Den Jive-connector, du opretter i overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører indholdet til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en ny undermappe i mappen Indbakke med navnet **Jive** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle Jive-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter Jive-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen DataConnector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-jive-connector"></a>Trin 1: Konfigurer Jive-connectoren

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til Jive-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** > **Jive**.

2. Klik på **Tilføj connector** på siden Med produktbeskrivelse for **Jive**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-jive-connector"></a>Trin 2: Konfigurer Jive-connectoren

Det andet trin er at konfigurere Jive-connectoren på Merge1-webstedet. Du kan finde oplysninger om, hvordan du konfigurerer Jive-connectoren, i [Brugervejledningen til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Jive%20User%20Guide.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge nedenstående trin:

1. Aktivér automatisk brugertilknytning på siden **Knyt Jive-brugere til Microsoft 365-brugere** . Jive-elementerne indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365-bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-jive-connector"></a>Trin 4: Overvåg Jive-connectoren

Når du har oprettet Jive-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **Jive-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.