---
title: Konfigurer en connector til arkivering af CellTrust-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere CellTrust-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: aedb91f75884cc8bac2e6ff05e65af274a1ca332
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317156"
---
# <a name="set-up-a-connector-to-archive-celltrust-data"></a>Konfigurer en connector til arkivering af CellTrust-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra CellTrust-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [CellTrust-connector](https://globanet.com/celltrust/), der henter elementer fra tredjepartsdatakilden og importerer disse elementer til Microsoft 365. Connectoren konverterer indholdet af SMS meddelelser fra CellTrust-konti til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når CellTrust-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en CellTrust-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-celltrust-data"></a>Oversigt over arkivering af CellTrust-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere CellTrust-data i Microsoft 365.

![Arkivering af arbejdsproces for CellTrust-data.](../media/CellTrustConnectorWorkflow.png)

1. Din organisation arbejder sammen med CellTrust om at konfigurere et CellTrust-websted.

2. En gang hver 24 timer kopieres CellTrust-elementer til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af en meddelelse til et mailformat.

3. Den CellTrust-connector, du opretter i overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Den automatiske brugertilknytning som connector importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for det, der er beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **CellTrust** i brugerpostkasserne, og meddelelseselementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle CellTrust-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter CellTrust-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-celltrust-connector"></a>Trin 1: Konfigurer CellTrust-connectoren

Det første trin er at få adgang til **dataconnectorerne på overholdelsesportalen** og oprette en connector til CellTrust-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** \> **CellTrust**.

2. Klik på **Tilføj connector** på siden **CellTrust-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-celltrust-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer CellTrust-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere CellTrust-connectoren på Veritas Merge1-webstedet. Du kan få mere at vide om, hvordan du konfigurerer CellTrust-connectoren, i [Brugervejledningen til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20CellTrust%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre den connector, der er konfigureret i overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Tilknyt cellTrust-brugere til Microsoft 365 brugere**. CellTrust-elementerne indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-celltrust-connector"></a>Trin 4: Overvåg CellTrust-connectoren

Når du har oprettet CellTrust-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **CellTrust-connectoren** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.