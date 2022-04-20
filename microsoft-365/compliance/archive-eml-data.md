---
title: Konfigurer en connector til arkivering af EML-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere EML-data fra Veritas i Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 9ba4cc4772e93b85e856bb68850ba682352e9f5f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993529"
---
# <a name="set-up-a-connector-to-archive-eml-data"></a>Konfigurer en connector til arkivering af EML-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere EML-data til brugerpostkasser i din Microsoft 365 organisation. EML er filtypenavnet for en mail, der er gemt i en fil. Connectoren konverterer indholdet af et element fra kildeformatet til et mailformat og importerer derefter elementet til en brugerpostkasse.

Når EML-meddelelser er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery og opbevaringspolitikker og opbevaringsmærkater. Brug af en EML-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-eml-data"></a>Oversigt over arkivering af EML-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere EML-data i Microsoft 365.

![Arkivering af arbejdsproces for EML-data.](../media/EMLConnectorWorkflow.png)

1. Din organisation arbejder sammen med EML-kilden om at konfigurere et EML-websted.

2. En gang hver 24 timer kopieres indholdselementer fra EML-kilden til Veritas Merge1-webstedet. Under denne proces konverteres indholdet af en EML-fil til et mailformat.

3. Den EML-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede meddelelseselementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytningsproces, der er beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Under denne proces oprettes en undermappe i mappen Indbakke med navnet **EMLis** i brugerpostkasserne, og EML-elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Hver meddelelse indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i indholdselementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter EML-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-an-eml-connector"></a>Trin 1: Konfigurer en EML-connector

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til EML-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsEML** > .

2. Klik på **Tilføj connector** på siden **med beskrivelsen af EML-produktet**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-eml-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer EML-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere EML-connectoren på Veritas Merge1-webstedet. Du kan få oplysninger om konfiguration af [EML-connectoren i Brugervejledningen til Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20EML%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Knyt eksterne brugere til Microsoft 365 brugere**. EML-kildeelementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres EML-elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-eml-connector"></a>Trin 4: Overvåg EML-connectoren

Når du har oprettet EML-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **EML-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.