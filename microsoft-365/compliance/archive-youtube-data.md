---
title: Konfigurer en connector til arkivering af YouTube-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere YouTube-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridiske ventepositioner, eDiscovery- og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 20343411a77210845bfad22e34dfcada6f8ca9b9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759451"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>Konfigurer en connector til arkivering af YouTube-data

Brug en Veritas-connector i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra YouTube til brugerpostkasser i din Microsoft 365 organisation. Veritas indeholder en connector, der er konfigureret til at hente elementer fra en tredjepartsdatakilde og importere disse elementer til Microsoft 365. Connectoren konverterer indhold som f.eks. chats, vedhæftede filer, opgaver, noter og indlæg fra YouTube til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når YouTube-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 funktioner til overholdelse af angivne standarder, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en YouTube-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-youtube-data"></a>Oversigt over arkivering af YouTube-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere YouTube-dataene i Microsoft 365.

![Arkivering af arbejdsproces for YouTube-data.](../media/YouTubeConnectorWorkflow.png)

1. Din organisation arbejder sammen med YouTube om at konfigurere et YouTube-websted.

2. En gang hver 24 timer kopieres YouTube-varer til Veritas Merge1-webstedet. Connectoren konverterer også YouTube-elementer til et mailformat.

3. Den YouTube-connector, du opretter i Microsoft 365 Overholdelsescenter opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører YouTube-indholdet til en sikker Azure Storage placering i Microsofts cloud.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **YouTube** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle YouTube-elementer indeholder denne ejendom, som udfyldes med mailadressen på hver enkelt deltager i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Opret en Flet1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://www.veritas.com/form/requestacall/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Opret et YouTube-program for at hente data fra din YouTube-konto. Du kan finde en trinvis vejledning i, hvordan du opretter programmet, under [Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

- Den bruger, der opretter YouTube-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors** i Microsoft 365 Overholdelsescenter. Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>Trin 1: Konfigurer YouTube-connectoren

Det første trin er at få adgang til siden **Dataconnectors** i Microsoft 365 Overholdelsescenter og oprette en connector til YouTube-data.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsYouTube** > .

2. På siden med beskrivelsen af **YouTube-produktet** skal du klikke på **Tilføj connector**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer YouTube på Veritas Merge1-webstedet

Det andet trin er at konfigurere YouTube-connectoren på Veritas Merge1-webstedet. Du kan få oplysninger om, hvordan du konfigurerer YouTube-connectoren, i [Brugervejledning til Merge1-tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

Når du klikker på **Gem & Udfør,** vises siden **Brugertilknytning** i connectorguiden i Microsoft 365 Overholdelsescenter.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Map YouTube-brugere til Microsoft 365 brugere**. YouTube-elementerne omfatter en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-youtube-connector"></a>Trin 4: Overvåg YouTube-connectoren

Når du har oprettet YouTube-connectoren, kan du få vist connectorstatussen i Microsoft 365 Overholdelsescenter.

1. Gå til , <https://compliance.microsoft.com/> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **YouTube-connectoren** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
