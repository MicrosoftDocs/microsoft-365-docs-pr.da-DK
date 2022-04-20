---
title: Konfigurer en connector til arkivering af Red tail Speak-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere Red tail Speak-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 46b9646fee78fa0589a9af41db35cf79a71e508f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994562"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Konfigurer en connector til arkivering af Redtail Speak-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Redtail Speak til brugerpostkasser i din Microsoft 365 organisation. Veritas giver dig en [Redtail Speak-connector](https://globanet.com/redtail/) , der er konfigureret til at hente elementer fra din organisations SFTP-server, hvor varerne modtages fra Redtail. Connectoren konverterer indholdet fra Redtail Speak til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Redtail Speak-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en Redtail Speak-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Oversigt over arkivering af Redtail Speak-dataene

I følgende oversigt forklares processen med at bruge en connector til at arkivere Redtail Speak-dataene i Microsoft 365.

![Arkivering af arbejdsproces for Redtail Speak-data.](../media/RedtailSpeakConnectorWorkflow.png)

1. Din organisation arbejder med Redtail Speak for at konfigurere en SMTP-gateway, hvor meddelelser videresendes fra Redtail Speak til organisationens SFTP-server dagligt.

2. En gang hver 24 timer kopieres Redtail Speak-genstandene til Veritas Merge1-webstedet. Connectoren konverterer også Redtail Speak-elementerne til et mailformat.

3. Redtail Speak-connectoren, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører meddelelserne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede Redtail *Speak-elementer* til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben Mail for den automatiske brugertilknytning, som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Redtail Speak** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Redtail Speak-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- I trin 2 skal du angive din organisations SFTP-server. Dette trin er nødvendigt, så Veritas Merge1 kan kontakte det for at indsamle Redtail Speak-data via SFTP.

- Den bruger, der opretter connectoren Redtail Speak Importer i Trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>Trin 1: Konfigurer Redtail Speak-connectoren

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til Redtail Speak-dataene.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) , og vælg **Dataconnectors** &gt; **Redtail Speak**.

2. Vælg **Tilføj ny connector** på siden med produktbeskrivelsen **til Redtail Speak**.

3. På siden **Vilkår for tjeneste** skal du vælge **Acceptér**.

4. Angiv et entydigt navn, der identificerer connectoren, og vælg derefter **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Redtail Speak-connectoren på Veritas Merge1-webstedet

Det andet trin er at konfigurere Redtail Speak-connectoren på Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer Redtail [Speak-connectoren, i Brugervejledningen til Merge1-tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

Når du har valgt **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Map Redtail Speak-brugere til Microsoft 365 brugere**. Redtail Speak-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Vælg **Næste**, gennemse dine indstillinger, og gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>Trin 4: Overvåg Redtail Speak-connectoren

Når du har oprettet Redtail Speak-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) , og vælg **Dataconnectors** i venstre navigationsrude.

2. Vælg fanen **Forbindelser,** og vælg derefter connectoren **Redtail Speak** for at få vist pop op-siden. På denne side vises egenskaber og oplysninger om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du vælge linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.