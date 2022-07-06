---
title: Konfigurer en connector for at arkivere Skype for Business data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra Skype for Business til Microsoft 365.
ms.openlocfilehash: 4301519561c75d4c76cdd47b7adae544f5170585
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632856"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Konfigurer en connector til arkivering af Skype for Business data

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra den Skype for Business platform til brugerpostkasser i din Microsoft 365-organisation. Veritas leverer en [Skype for Business](https://www.veritas.com/en/au/insights/merge1/skype-for-business) connector, der er konfigureret til at hente elementer fra tredjepartsdatakilden (regelmæssigt) og importere disse elementer til Microsoft 365. Connectoren konverterer indholdet, f.eks. meddelelser mellem brugere, vedvarende chats og mødemeddelelser fra Skype for Business til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Skype for Business data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Hvis du bruger en Skype for Business-connector til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-skype-for-business-data"></a>Oversigt over arkivering af Skype for Business data

I følgende oversigt forklares processen med at bruge en connector til at arkivere de Skype for Business data i Microsoft 365.

![Arkivering af arbejdsproces for Skype for Business data.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Din organisation arbejder sammen med Skype for Business om at konfigurere et Skype for Business websted.

2. En gang hver 24 timer kopieres Skype for Business varer til Veritas Merge1-webstedet. Connectoren konverterer også Skype for Business elementer til et mailformat.

3. Den Skype for Business connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører det Skype for Business indhold til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Skype for Business** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Hvert Skype for Business element indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en Flet1-konto til Microsoft-connectors. For at gøre dette skal du kontakte [Veritas Kundesupport](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter den Skype for Business connector i trin 1 (og fuldfører den i trin 3), skal tildeles rollen DataConnector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>Trin 1: Konfigurer Skype for Business-connectoren

Det første trin er at få adgang til siden **Dataconnectors på overholdelsesportalen** og oprette en connector til Skype for Business data.

1. Gå til <https://compliance.microsoft.com> , og klik på **Dataconnectors** >  **Skype for Business**.

2. Klik på **Tilføj connector** på siden **Skype for Business** produktbeskrivelse.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Skype for Business på Veritas Merge1-webstedet

Det andet trin er at konfigurere Skype for Business connector på Veritas Merge1 site. Du kan få mere at vide om, hvordan du konfigurerer Skype for Business connector, i [Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Knyt Skype for Business brugere til Microsoft 365-brugere**. De Skype for Business elementer omfatter en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365-bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>Trin 4: Overvåg den Skype for Business connector

Når du har oprettet Skype for Business connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg **derefter Skype for Business connector** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
