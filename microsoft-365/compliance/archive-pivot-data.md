---
title: Konfigurer en connector til at arkivere pivotdata i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere pivotdata fra Veritas i Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 45916fa4a107ec40c0f95c2be9ded85643f6ea23
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099295"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Konfigurer en connector til arkivering af pivotdata

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Pivot-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en [Pivot-connector](https://globanet.com/pivot/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (regelmæssigt) og derefter importere disse elementer til Microsoft 365. Pivot er en chatplatform, der muliggør samarbejde med deltagere på det finansielle marked. Connectoren konverterer elementer som f.eks. chatbeskeder fra en brugers pivotkonti til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når pivotdata er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation venteposition, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikationsoverholdelse. Brug af en Pivot-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-pivot-data"></a>Oversigt over arkivering af pivotdata

I følgende oversigt forklares processen med at bruge en connector til at arkivere pivotdataene i Microsoft 365.

![Arkivering af arbejdsproces for pivotdata.](../media/PivotConnectorWorkflow.png)

1. Din organisation arbejder sammen med Pivot om at konfigurere et pivotkildewebsted.

2. En gang hver 24. time kopieres pivotelementer til Veritas Merge1-webstedet. Connectoren konverterer også pivotelementerne til et mailformat.

3. Den Pivot-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører pivotelementerne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer pivotelementerne til bestemte brugeres postkasser ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Pivot** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Hvert pivotelement indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter pivotconnectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-pivot-connector"></a>Trin 1: Konfigurer pivotconnectoren

Det første trin er at få adgang til siden **Dataconnectors** i Microsoft Compliance Center og oprette en connector til pivotdata.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsPivot** > .

2. Klik på **Tilføj connector** på siden **Med pivotproduktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-pivot-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Pivot-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere Pivot-connectoren på Flet1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer Pivot-connectoren på Veritas [Merge1-webstedet, i Brugervejledning til fletning1 af tredjepartsconnectorer](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen i Microsoft 356 Compliance Center, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Tilknyt pivotbrugere til Microsoft 365 brugere**. Pivotelementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-pivot-connector"></a>Trin 4: Overvåg Pivot-connectoren

Når du har oprettet pivotconnectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **pivotconnectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.