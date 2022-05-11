---
title: Konfigurer en connector til at arkivere tekstseparerede data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere tekstseparerede data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 8758bd92d78663d4a494ca920ee222d5668f733b
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318696"
---
# <a name="set-up-a-connector-to-archive-text-delimited-data"></a>Konfigurer en connector til at arkivere tekstseparerede data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere tekstseparerede data til brugerpostkasser i din Microsoft 365 organisation. Veritas indeholder en [tekstsepareret connector](https://globanet.com/text-delimited), der er konfigureret til at hente elementer fra en datakilde fra tredjepart (regelmæssigt) og importere disse elementer til Microsoft 365. Connectoren konverterer indhold fra den tekstseparerede datakilde til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når tekstafgrænsede data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation hold, eDiscovery og opbevaringspolitikker og opbevaringsmærkater. Brug af en tekstsepareret dataconnector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-the-text-delimited-data"></a>Oversigt over arkivering af de tekstseparerede data

I følgende oversigt forklares processen med at bruge en connector til at arkivere tekstseparerede kildeoplysninger i Microsoft 365.

![Arkivering af arbejdsproces for tekstseparerede data.](../media/TextDelimitedConnectorWorkflow.png)

1. Din organisation arbejder sammen med den tekstseparerede kilde om at konfigurere et tekstsepareret websted.

2. En gang hver 24 timer kopieres chatbeskeder fra den tekstseparerede kilde til Veritas Merge1-webstedet. Connectoren konverterer også indholdet til et mailformat.

3. Den tekstseparerede connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede meddelelseselementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i trin 3. Der oprettes en ny undermappe i mappen Indbakke med navnet **Tekstsepareret** i brugerpostkasserne, og meddelelseselementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Hver meddelelse indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter den tekstseparerede connector i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-text-delimited-connector"></a>Trin 1: Konfigurer den tekstseparerede forbindelse

Det første trin er at få adgang til siden **Dataconnectors på overholdelsesportalen** og oprette en connector til tekstseparerede data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsText-Delimited** > .

2. Klik på **Tilføj forbindelse** på siden med **en tekstsepareret** produktbeskrivelse.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-text-delimited-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer den tekstseparerede connector på Veritas Merge1-webstedet

Det andet trin er at konfigurere den tekstseparerede connector på Flet1-webstedet. Du kan få oplysninger om konfiguration af den tekstseparerede connector på Veritas [Merge1-webstedet under Brugervejledning til connectors fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20text-delimited%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Knyt eksterne brugere til Microsoft 365 brugere**. De tekstseparerede kildeelementer indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-text-delimited-connector"></a>Trin 4: Overvåg den tekstseparerede forbindelse

Når du har oprettet den tekstseparerede connector, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter den **tekstseparerede** forbindelse for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.