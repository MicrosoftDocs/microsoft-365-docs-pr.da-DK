---
title: Konfigurer en connector til Webex-Teams data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra Veritas' Webex-Teams-connector i Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 775c09b1c2526367d9794ce41fe4f90f010f1bde
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320656"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Konfigurer en connector til arkivering af Webex-Teams data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra Webex-Teams til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [Webex Teams-connector](https://globanet.com/webex-teams/), der er konfigureret til at registrere Webex-Teams kommunikationselementer og importere dem til Microsoft 365. Connectoren konverterer indhold fra Webex-Teams, f.eks. 1:1-chats, gruppesamtaler, kanalsamtaler og vedhæftede filer fra din organisations Webex-Teams-konto, til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Webex-Teams data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. proceshold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Webex Teams-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-webex-teams-data"></a>Oversigt over arkivering af Webex-Teams data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Webex Teams data i Microsoft 365.

![Arkivering af arbejdsproces for Webex Teams data.](../media/WebexTeamsConnectorWorkflow.png)

1. Din organisation arbejder sammen med Webex-Teams om at konfigurere et Webex-Teams websted.

2. En gang hver 24 timer kopieres Webex Teams varer til Veritas Merge1-webstedet. Connectoren konverterer også Webex-Teams elementer til et mailformat.

3. Den Webex-Teams-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1 hver dag og overfører Webex-Teams-elementer til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Webex Teams** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle Webex-Teams-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Opret et program på [https://developer.webex.com/](https://developer.webex.com) for at hente data fra din Webex-Teams-konto. Du kan finde en trinvis vejledning i, hvordan du opretter programmet, under [Brugervejledning til fletning1 af tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Når du opretter dette program, genererer Webex-platformen et sæt entydige legitimationsoplysninger. Disse legitimationsoplysninger bruges i trin 2, når du konfigurerer Webex Teams-connectoren på webstedet Global Merge1.

- Den bruger, der opretter Webex Teams-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Trin 1: Konfigurer Webex Teams-connectoren

Det første trin er at få adgang til **dataconnectors** og konfigurere [Webex Teams-connectoren](https://globanet.com/webex-teams/).

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsWebex** >  **Teams**.

2. Klik på **Tilføj connector** på siden **Webex Teams** produktbeskrivelse.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Webex Teams-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere Webex Teams-connectoren på Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer Webex-Teams-connectoren, i [Brugervejledningen Til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Kortwebex Teams brugere, der skal Microsoft 365 brugere**. Webex-Teams-elementerne omfatter en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Trin 4: Overvåg Webex-Teams-connectoren

Når du har oprettet Webex-Teams-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **webex-Teams-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.