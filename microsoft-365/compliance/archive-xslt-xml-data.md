---
title: Konfigurer en connector til arkivering af XSLT/XML-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere XSLT/XML-data fra Veritas i Microsoft 365. Med denne connector kan du arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 450294107ce9ef7d138a60e4fcc5de47bce47ef1
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319390"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>Konfigurer en connector til arkivering af XSLT/XML-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-compliance-portal til at importere og arkivere data fra websidekilden til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en [XSLT/XML-connector](https://globanet.com/xslt-xml), der gør det muligt hurtigt at udvikle filer, der er oprettet ved hjælp af XSLT (Extensible Style sheet Language Transformations), til at transformere XML-filer til andre filformater (f.eks. HTML eller tekst), der kan importeres til Microsoft 365. Connectoren konverterer indholdet af et element fra XSLT/XML-kilden til et mailformat og importerer derefter det konverterede element til Microsoft 365 postkasser.

Når XSLT/XML-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview funktioner som f.eks. litigation hold, eDiscovery og opbevaringspolitikker og opbevaringsmærkater. Brug af en XSLT/XML-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-xsltxml-data"></a>Oversigt over arkivering af XSLT/XML-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere XSLT-/XML-kildedata i Microsoft 365.

![Arkivering af arbejdsproces for XSLT/XML-data.](../media/XSLT-XMLConnectorWorkflow.png)

1. Din organisation arbejder sammen med XSLT/XML-kilden om at konfigurere et XSLT/XML-websted.

2. En gang hver 24 timer kopieres chatbeskeder fra XSLT/XML-kilden til Veritas Merge1-webstedet. Connectoren konverterer også indholdet til et mailformat.

3. Den XSLT/XML-connector, du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede meddelelseselementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning, som beskrevet i trin 3. Der oprettes en ny undermappe i mappen Indbakke med navnet **XSLT/XML** i brugerpostkasserne, og meddelelseselementerne importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Hver meddelelse indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i meddelelsen.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Den bruger, der opretter XSLT/XML-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af forpligtelserne til Microsoft Purview og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-an-xsltxml-connector"></a>Trin 1: Konfigurer en XSLT/XML-connector

Det første trin er at få adgang til **dataconnectors på overholdelsesportalen** og oprette en connector til XSLT/XML-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsXSLT** > **/XML**.

2. Klik på **Tilføj ny connector** på siden **XSLT/XML-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-an-xsltxml-connector"></a>Trin 2: Konfigurer en XSLT/XML-connector

Det andet trin er at konfigurere XSLT/XML-connectoren på Flet1-webstedet. Du kan få mere at vide om, hvordan du konfigurerer XSLT/XML-connectoren på Veritas [Merge1-webstedet, i Brugervejledning til connectors fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

1. Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge nedenstående trin:

2. Aktivér automatisk brugertilknytning på siden **Tilknyt XSLT/XML-brugere til Microsoft 365 brugere**. XSLT/XML-elementerne indeholder en egenskab med navnet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

3. Klik på **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-xsltxml-connector"></a>Trin 4: Overvåg XSLT/XML-connectoren

Når du har oprettet XSLT/XML-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **XSLT/XML-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.