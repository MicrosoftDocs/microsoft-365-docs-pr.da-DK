---
title: Konfigurer en connector til at arkivere Slack eDiscovery-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra Veritas Slack eDiscovery til Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: e48bd25b5f444ce17eba08677f5bd1c1171af1ff
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637743"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Konfigurer en connector til arkivering af Slack eDiscovery-data

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere tredjepartsdata fra sociale medier, chat- og dokumentsamarbejdesplatforme til postkasser i din Microsoft 365-organisation. Veritas leverer en [Slack-connector](https://globanet.com/slack/) , der er konfigureret til at hente elementer fra tredjepartsdatakilden (regelmæssigt) og derefter importere disse elementer til Microsoft 365. Slack henter meddelelser og filer fra Slack-API'en og konverterer dem til et mailmeddelelsesformat og importerer derefter elementet til brugerpostkasser.

Når Slack eDiscovery-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Slack-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Oversigt over arkivering af Slack eDiscovery-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Slack-oplysningerne i Microsoft 365.

![Slack-arkiveringsarbejdsproces.](../media/SlackConnectorWorkflow.png)

1. Din organisation arbejder sammen med Slack om at konfigurere et Slack-websted.

2. En gang hver 24 timer kopieres chatbeskeder fra Slack eDiscovery til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af en chatmeddelelse til et mailformat.

3. Den Slack eDiscovery-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører chatbeskederne til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede chatbeskedelementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* og automatisk brugertilknytning, som beskrevet i trin 3. Der oprettes en ny undermappe i mappen Indbakke med navnet **Slack eDiscovery** i brugerpostkasserne, og chatmeddelelseselementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle chatbeskeder indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i chatmeddelelsen.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Hent brugernavnet og adgangskoden til din organisations Slack-virksomhedskonto. Du skal logge på denne konto i trin 2, når du konfigurerer Slack.

- Den bruger, der opretter Slack eDiscovery-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>Trin 1: Konfigurer Slack eDiscovery-connectoren

Det første trin er at få adgang til siden **Dataconnectors på overholdelsesportalen** og oprette en connector til Slack-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** > **Slack eDiscovery**.

2. Klik på **Tilføj connector** på siden **Slack eDiscovery-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-slack-ediscovery"></a>Trin 2: Konfigurer Slack eDiscovery

Det andet trin er at konfigurere Slack eDiscovery-connectoren på Flet1-webstedet. Du kan finde flere oplysninger om, hvordan du konfigurerer Slack eDiscovery-connectoren på Veritas [Merge1-webstedet, i Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

1. Aktivér automatisk brugertilknytning på siden **Knyt eksterne brugere til Microsoft 365-brugere** .

   Slack eDiscovery-elementer omfatter en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365-bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Trin 4: Overvåg Slack eDiscovery-connectoren

Når du har oprettet Slack eDiscovery-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **slack-eDiscovery-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.