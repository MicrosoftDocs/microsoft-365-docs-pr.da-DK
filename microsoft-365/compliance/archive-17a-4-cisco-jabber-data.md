---
title: Konfigurer en connector til arkivering af Cisco Jabber-data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 Cisco Jabber DataParser-connector til at importere og arkivere Cisco Jabber-data i Microsoft 365.
ms.openlocfilehash: 3e7bcd9a85293d1516da8070fa39e2545d4fbc22
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319954"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>Konfigurer en connector til arkivering af Cisco Jabber-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug [Cisco Jabber DataParser](https://www.17a-4.com/jabber-dataparser/) fra 17a-4 LLC til at importere og arkivere data fra Cisco Jabber til brugerpostkasser i din Microsoft 365 organisation. DataParser indeholder en Cisco Jabber-connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. Cisco Jabber DataParser-connectoren konverterer Cisco Jabber-data til et mailmeddelelsesformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når Cisco Jabber-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og overholdelse af kommunikation. Brug af en Cisco Jabber-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Oversigt over arkivering af Cisco Jabber-data

I følgende oversigt forklares processen med at bruge en dataconnector til at arkivere Cisco Jabber-data i Microsoft 365.

![Arkiveringsarbejdsproces for Cisco Jabber-data fra 17a-4.](../media/CiscoJabberDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere Cisco Jabber DataParser.

2. Cisco Jabber-elementer indsamles regelmæssigt af DataParser. DataParser konverterer også indholdet af en meddelelse til et mailformat.

3. Cisco Jabber DataParser-connectoren, som du opretter i Microsoft Purview-compliance-portal opretter forbindelse til DataParser og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber DataParser** i brugerpostkasserne, og Cisco Jabber-elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Cisco Jabber-elementer indeholder denne egenskab, som udfyldes med mailadressen på hver deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en DataParser-konto til Microsoft-connectors. For at gøre dette skal du kontakte [17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter Cisco Jabber DataParser-connectoren i Trin 1 (og fuldfører den i trin 3), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-a-cisco-jabber-dataparser-connector"></a>Trin 1: Konfigurer en Cisco Jabber DataParser-connector

Det første trin er at få adgang til siden Dataconnectors på overholdelsesportalen og oprette en 17a-4-connector til Cisco Jabber-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsCisco** >  **Jabber DataParser**.

2. Klik på **Tilføj connector** på siden Cisco **Jabber DataParser-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i cisco Jabber DataParser-forbindelsesguiden.

## <a name="step-2-configure-the-cisco-jabber-dataparser-connector"></a>Trin 2: Konfigurer Cisco Jabber DataParser-connectoren

Arbejd med 17a-4-support for at konfigurere Cisco Jabber DataParser-connectoren.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

Cisco Jabber DataParser-connectoren knytter automatisk brugere til deres Microsoft 365 mailadresser, før de importerer data til Microsoft 365.

## <a name="step-4-monitor-the-cisco-jabber-dataparser-connector"></a>Trin 4: Overvåg Cisco Jabber DataParser-connectoren

Når du har oprettet en Cisco Jabber DataParser-connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter cisco Jabber DataParser-connectoren, som du oprettede, for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
