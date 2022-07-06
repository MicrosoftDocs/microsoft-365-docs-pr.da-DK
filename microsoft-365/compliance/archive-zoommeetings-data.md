---
title: Konfigurer en connector til arkivering af Zoom-mødedata i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra Veritas Zoom-møder til Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 3a2d63071ba29baa40c8d7a656e7e7437f9348bd
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631353"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Konfigurer en connector til arkivering af Zoom-mødedata

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra Zoom Meetings til brugerpostkasser i din Microsoft 365-organisation. Veritas indeholder en [Zoom Meetings-connector](https://globanet.com/zoom/) , der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Connectoren konverterer indholdet af møderne (herunder chats, optagede filer og metadata) fra kontoen Zoommøder til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når dataene for Zoom-møder er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner som f.eks. proceshold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Zoom Meetings-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Oversigt over arkivering af zoommødedata

I følgende oversigt forklares processen med at bruge en connector til at arkivere Zoom-møder-data i Microsoft 365.

![Zoom arbejdsprocessen for arkivering af møder.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Din organisation arbejder sammen med Zoom-møder om at konfigurere et Zoom-mødewebsted.

2. En gang hver 24 timer kopieres mødeelementer fra Zoom-møder til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af møderne til et mailmeddelelsesformat.

3. Zoom Meetings-connectoren, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1 hver dag og overfører mødemeddelelserne til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede mødeelementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* og automatisk brugertilknytning, som beskrevet i trin 3. Der oprettes en ny undermappe i mappen Indbakke med navnet **Zoom-møder** i brugerpostkasser, og mødeelementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Hvert mødeelement indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i mødet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Hent brugernavnet og adgangskoden til din organisations Zoom Business- eller Zoom Enterprise-konto. Du skal logge på denne konto i Trin 2, når du konfigurerer connectoren Zoom møder.

- Opret følgende programmer på [Zoom Marketplace](https://marketplace.zoom.us):

  - OAuth-program

  - JWT-program

  Når du har oprettet disse programmer, genererer Zoom-platformen et sæt entydige legitimationsoplysninger, der bruges til at generere tokens. Disse tokens bruges til at godkende connectoren, når den opretter forbindelse til din Zoom-konto og kopierer elementer til Flet1-webstedet. Du skal bruge disse tokens, når du konfigurerer Zoom-connectoren i trin 2.

  Du kan finde en trinvis vejledning til, hvordan du opretter OAuth- og JWT-programmer, i [Brugervejledningen Til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- Den bruger, der opretter connectoren Zoom møder i trin 1 (og fuldfører den i trin 3), skal tildeles rollen DataConnector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Trin 1: Konfigurer connectoren Zoom møder

Det første trin er at få adgang til **dataconnectors på overholdelsesportalen** og oprette en Zoom Meetings-connector.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** > **Zoom-møder**.

2. Klik på **Tilføj connector** på produktbeskrivelsessiden **Zoom møder**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Trin 2: Konfigurer connectoren Zoom møder

Det andet trin er at konfigurere connectoren Zoom møder på Flet1-webstedet. Du kan få flere oplysninger om, hvordan du konfigurerer zoommøder-connectoren på Veritas [Merge1-webstedet, i Brugervejledning til fletning1 af tredjepartsconnectorer](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

1. Aktivér automatisk brugertilknytning på siden **Knyt eksterne brugere til Microsoft 365-brugere** .

   Zoommødeelementer omfatter en egenskab kaldet *Mail* , der indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365-bruger, importeres elementerne til den pågældende brugers postkasse

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Trin 4: Overvåg connectoren Zoom møder

Når du har oprettet connectoren Zoom møder, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter connectoren **Zoom møder** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.

- Hvis connectoren Zoom-møder skal fungere, skal du aktivere optagelser, når du konfigurerer Zoom møder.