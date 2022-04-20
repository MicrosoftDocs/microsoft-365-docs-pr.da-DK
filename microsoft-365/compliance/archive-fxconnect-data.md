---
title: Konfigurer en connector til arkivering af FX-Forbind data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra Veritas FX-Forbind i Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 79d4dca6c71f6654db7294d55761275d8b758727
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946720"
---
# <a name="set-up-a-connector-to-archive-fx-connect-data"></a>Konfigurer en connector til arkivering af FX-Forbind data

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra FX Forbind samarbejdsplatformen til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [FX Forbind-connector](https://globanet.com/fx-connect/), der er konfigureret til at registrere FX-Forbind elementer og importere disse elementer til Microsoft 365. Connectoren konverterer indholdet fra FX-Forbind, f.eks. handler, meddelelser og andre oplysninger fra organisationens FX-Forbind-konto, til et mailmeddelelsesformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når FX-Forbind data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en FX-Forbind-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-fx-connect-data"></a>Oversigt over arkivering af FX Forbind data

I følgende oversigt forklares det, hvordan du bruger en connector til at arkivere oplysningerne om FX-Forbind i Microsoft 365.

![Arkivering af arbejdsproces for FX-Forbind-data.](../media/FXConnectConnectorWorkflow.png)

1. Din organisation arbejder sammen med FX-Forbind om at konfigurere et FX-Forbind websted.

2. En gang hver 24 timer kopieres varer fra FX Forbind konti til Veritas Merge1-webstedet. Connectoren konverterer også FX-Forbind-elementer til et mailformat.

3. Den FX-Forbind-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører FX-Forbind-elementer til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **FX Forbind** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle FX-Forbind-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors.  Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter FX-Forbind-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-fx-connect-connector"></a>Trin 1: Konfigurer FX-Forbind-connectoren

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til FX Forbind data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsFX** >  **Forbind**.

2. På siden **MED Forbind** produktbeskrivelse skal du klikke på **Tilføj connector**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-fx-connect-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer FX Forbind-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere FX-Forbind-connectoren på Flet1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer FX-Forbind-connectoren, i [Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20FX%20Connect%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Tilknyt FX-Forbind brugere, der skal Microsoft 365 brugere**. FX-Forbind-elementerne indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-fx-connect-connector"></a>Trin 4: Overvåg FX-Forbind-connectoren

Når du har oprettet FX-Forbind-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **fx-Forbind-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.