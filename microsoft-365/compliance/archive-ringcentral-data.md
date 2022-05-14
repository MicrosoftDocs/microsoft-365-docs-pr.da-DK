---
title: Konfigurer en connector til arkivering af RingCentral-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere RingCentral-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridiske ventepositioner, eDiscovery- og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 097aa739e28387c09f608ac6fa40c23f13158dbd
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417144"
---
# <a name="set-up-a-connector-to-archive-ringcentral-data"></a>Konfigurer en connector til arkivering af RingCentral-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra RingCentral-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas indeholder en [RingCentral-connector](https://www.veritas.com/insights/merge1/ringcentral), der er konfigureret til at hente elementer fra tredjepartsdatakilden og importere disse elementer til Microsoft 365. Connectoren konverterer indhold som f.eks. chats, vedhæftede filer, opgaver, noter og meddelelser fra RingCentral til et mailformat og importerer derefter disse elementer til brugerpostkasserne i Microsoft 365.

Når RingCentral-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en RingCentral-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-ringcentral-data"></a>Oversigt over arkivering af RingCentral-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere RingCentral-dataene i Microsoft 365.

![Arkivering af arbejdsproces for RingCentral-data.](../media/RingCentralConnectorWorkflow.png)

1. Din organisation arbejder sammen med RingCentral om at konfigurere et RingCentral-websted.

2. En gang hver 24 timer kopieres RingCentral-varer til Veritas Merge1-webstedet. Connectoren konverterer også RingCentral-elementer til et mailformat.

3. Den RingCentral-connector, du opretter i overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører RingCentral-indholdet til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **RingCentral** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle RingCentral-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en Flet1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/form/requestacall/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Opret et RingCentral-program til at hente data fra din RingCentral-konto. Du kan finde en trinvis vejledning i, hvordan du opretter programmet, under [Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

- Den bruger, der opretter RingCentral-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-ringcentral-connector"></a>Trin 1: Konfigurer RingCentral-connectoren

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til RingCentral-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsRingCentral** > .

2. Klik på **Tilføj connector** på siden **Med produktbeskrivelse til RingCentral**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-ringcentral-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer RingCentral på Veritas Merge1 site

Det andet trin er at konfigurere RingCentral-connectoren på Veritas Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer RingCentral-connectoren, i [Brugervejledningen til Merge1-tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

Når du klikker på **Gem & Udfør,** vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Map RingCentral-brugere til Microsoft 365 brugere**. RingCentral-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-ringcentral-connector"></a>Trin 4: Overvåg RingCentral-connectoren

Når du har oprettet RingCentral-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **RingCentral-connectoren** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
