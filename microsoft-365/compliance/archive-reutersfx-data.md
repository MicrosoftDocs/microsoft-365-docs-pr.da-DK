---
title: Konfigurer en connector til arkivering af Reuters FX-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere Reuters FX-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: d7566691ea4030d852aa4075a8bfe7088e71bf62
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320144"
---
# <a name="set-up-a-connector-to-archive-reuters-fx-data"></a>Konfigurer en connector til arkivering af Reuters FX-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra Reuters FX-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en [Reuters FX-connector](https://globanet.com/reuters-fx/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (regelmæssigt) og derefter importere disse elementer til Microsoft 365. Connectoren konverterer valutakurserne og FX-kurserne fra Reuters FX-kontoen til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Reuters FX-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af en Reuters FX-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-reuters-fx-data"></a>Oversigt over arkivering af Reuters FX-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Reuters FX-data i Microsoft 365.

![Arkivering af arbejdsproces for Reuters FX-data.](../media/ReutersFXConnectorWorkflow.png)

1. Din organisation arbejder sammen med Reuters FX om at konfigurere et Reuters FX-websted.

2. En gang hver 24 timer kopieres Reuters FX-varer til Veritas Merge1-webstedet. Connectoren konverterer også elementerne til et mailformat.

3. Den Reuters FX-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører indholdet til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer elementerne til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Reuters FX** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Reuters FX-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://globanet.com/contact-us). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter Reuters FX-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-reuters-fx-connector"></a>Trin 1: Konfigurer Reuters FX-connectoren

Det første trin er at få adgang til siden **Dataconnectors** i Microsoft 365 og oprette en connector til Reuters FX-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsReuters** >  **FX**.

2. Klik på **Tilføj connector** på siden **Reuters FX-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-reuters-fx-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Reuters FX-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere Reuters FX-connectoren på Veritas Merge1-webstedet. Du kan få oplysninger om konfiguration af Reuters [FX-connectoren i Brugervejledningen til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20FX%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge nedenstående trin:

1. Aktivér automatisk brugertilknytning på siden **Tilknyt Reuters FX-brugere til Microsoft 365 brugere**.

   Reuters FX-elementer indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-reuters-fx-connector"></a>Trin 4: Overvåg Reuters FX-connectoren

Når du har oprettet Fx-connectoren Reuters, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **FX-connectoren Reuters** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.