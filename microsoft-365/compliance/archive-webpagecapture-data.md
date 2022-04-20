---
title: Konfigurer en connector til arkivering af websidedata i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere websidehentningsdata fra Veritas i Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 549af03a794c132bc11901618a60185722f24907
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935033"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Konfigurer en connector til arkivering af websidedata

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra websider til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [Webside Capture-connector](https://globanet.com/webpage-capture) , der registrerer bestemte websider (og eventuelle links på disse sider) på et bestemt websted eller et helt domæne. Connectoren konverterer websideindholdet til et PDF-, PNG- eller brugerdefineret filformat og vedhæfter derefter de konverterede filer til en mail og importerer derefter disse mailelementer til brugerpostkasser i Microsoft 365.

Når websideindhold er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery og opbevaringspolitikker og opbevaringsmærkater. Brug af en Connector til hentning af websider til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-webpage-data"></a>Oversigt over arkivering af websidedata

I følgende oversigt forklares processen med at bruge en connector til at arkivere websideindhold i Microsoft 365.

![Arkivering af arbejdsproces for websidedata.](../media/WebPageCaptureConnectorWorkflow.png)

1. Din organisation arbejder sammen med websidekilden om at konfigurere et websted til hentning af webside.

2. En gang hver 24 timer kopieres elementer fra websiden til Veritas Merge1-webstedet. Connectoren konverterer også og vedhæfter indholdet af en webside til en mail.

3. Den Webside Capture-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører websideelementerne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede websideelementer til bestemte brugeres postkasser ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Websidehentning** i brugerpostkasserne, og websideelementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle websideelementer indeholder denne egenskab, som udfyldes med de mailadresser, der angives, når du konfigurerer connectoren Websidehentning i [trin 2](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Du skal arbejde med Veritas-understøttelse for at konfigurere et brugerdefineret filformat til at konvertere websideelementerne til. Du kan få flere oplysninger i [brugervejledningen til Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- Den bruger, der opretter connectoren Websidehentning i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Trin 1: Konfigurer connectoren Websidehentning

Det første trin er at få adgang til **dataconnectorerne** og oprette en connector til kildedata for websiden.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsWebpage** >  **Capture**.

2. Klik på **Tilføj connector** på siden **Websidehentning** af produktbeskrivelse.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer webside-capture-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere Webside Capture-connectoren på Veritas Merge1-webstedet. Du kan få mere at vide om, hvordan du konfigurerer connectoren Websidehentning, i [Brugervejledning til Merge1-tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge nedenstående trin:

1. Aktivér automatisk brugertilknytning på siden **Registrer webside for brugere, der skal Microsoft 365 brugere**. Elementerne i Websidehentning indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Trin 4: Overvåg connectoren Websidehentning

Når du har oprettet connectoren Websidehentning, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter connectoren **Websidehentning** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.