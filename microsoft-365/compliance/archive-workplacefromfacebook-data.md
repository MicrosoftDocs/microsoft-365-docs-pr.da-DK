---
title: Konfigurer en connector for at arkivere Arbejdsplads fra Facebook-data i Microsoft 365
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
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra Workplace fra Facebook, som er arkiveret på Veritas' Merge1-websted, i Microsoft 365. Konfiguration af en connector kræver, at du arbejder med Veritas Denne connector giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk venteposition, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 0dbd1bfaeea6a42db03793941b1fea894ee391b5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001450"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Konfigurer en connector til arkivering af arbejdsplads fra Facebook-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector i Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Arbejdsplads fra Facebook til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [arbejdsplads fra Facebook-connector](https://globanet.com/workplace/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Connectoren konverterer indholdet, f.eks. chats, vedhæftede filer, indlæg og videoer fra Arbejdsplads, til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når data på arbejdspladsen er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater og kommunikation med overholdelse af angivne standarder. Brug af Workplace fra Facebook-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Oversigt over arkivering af arbejdsplads fra Facebook-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere arbejdspladsdata i Microsoft 365.

![Arkivering af arbejdsproces for arbejdsplads fra Facebook-data.](../media/WorkplaceConnectorWorkflow.png)

1. Din organisation arbejder sammen med Workplace fra Facebook om at konfigurere et websted på arbejdspladsen.

2. En gang hver 24 timer kopieres elementer fra Workplace til Veritas Merge1-webstedet. Connectoren konverterer også indholdet af disse elementer til et mailmeddelelsesformat.

3. Workplace fra Facebook-connectoren, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1 hver dag og overfører arbejdspladselementerne til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i trin 3. Der oprettes en undermappe i mappen Indbakke med navnet **Workplace fra Facebook** , og elementerne på arbejdspladsen importeres til den pågældende mappe. Connectoren gør dette ved hjælp af værdien af egenskaben *Mail* . Alle elementer på arbejdspladsen indeholder denne egenskab, som udfyldes med mailadressen på alle chat- eller postdeltagere.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-connectors. Hvis du vil oprette denne konto, skal du kontakte [Veritas-kundesupport](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Opret en brugerdefineret integration på https://my.workplace.com/work/admin/apps/ for at hente data fra Workplace via API'er med henblik på overholdelse af angivne standarder og eDiscovery.

   Når du opretter integrationen, genererer Workplace-platformen et sæt entydige legitimationsoplysninger, der bruges til at generere tokens, der bruges til godkendelse. Disse tokens bruges i guiden Konfiguration af Workplace fra Facebook-connector i Trin 2. Du kan finde en trinvis vejledning i, hvordan du opretter programmerne, i [Brugervejledningen Flet1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- Den bruger, der opretter workplace fra Facebook-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>Trin 1: Konfigurer arbejdsplads fra Facebook-connector

Det første trin er at få adgang til siden **Dataconnectors på overholdelsesportalen** og oprette en connector til workplace-data.

1. Gå til, [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsArbejdsplads** >  **fra Facebook**.

2. Klik på **Tilføj connector** på siden **Arbejdsplads fra Facebook-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer arbejdsplads fra Facebook-connector på Veritas Merge1-webstedet

Det andet trin er at konfigurere Workplace fra Facebook-connectoren på Merge1-webstedet. Du kan få mere at vide om, hvordan du konfigurerer Workplace fra [Facebook-connectoren, i Brugervejledning til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

Når du har klikket på **Gem & Udfør**, vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Knyt eksterne brugere til Microsoft 365 brugere**. Elementer på arbejdspladsen omfatter en egenskab med navnet *Mail* , der indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>Trin 4: Overvåg arbejdspladsen fra Facebook-connector

Når du har oprettet Workplace fra Facebook-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **Workplace fra Facebook-connectoren** for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.