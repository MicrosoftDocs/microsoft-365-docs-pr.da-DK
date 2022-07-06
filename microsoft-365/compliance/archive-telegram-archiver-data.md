---
title: Konfigurer en connector til arkivering af Telegram-kommunikationsdata i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere Telegram-kommunikationsdata i Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: f611893db7415c2218c61f560063c8a08a319c93
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635715"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Konfigurer en connector til arkivering af Telegram-kommunikationsdata

Brug connectoren TeleMessage i Microsoft Purview-compliance-portal til at importere og arkivere Telegram-chats, vedhæftede filer, filer og slettede meddelelser og opkald. Når du har konfigureret en connector, opretter den forbindelse til din organisations TeleMessage-konto og importerer medarbejdernes mobilkommunikation ved hjælp af Telegram Archiver til postkasser i Microsoft 365.

Når Telegram Archiver-connectordata er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, Indholdssøgning og Microsoft 365-opbevaringspolitikker, til Telegram-kommunikationsdata. Du kan f.eks. søge i Telegram-kommunikation ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder connectordataene for Telegram Archiver, til en tilsynsførende i en eDiscovery-sag (Premium). Brug af en Telegram Archiver-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde reglerne for virksomhedsstyring og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-telegram-communications-data"></a>Oversigt over arkivering af telegramkommunikationsdata

I følgende oversigt forklares processen med at bruge en connector til at arkivere Telegram-kommunikationsdata i Microsoft 365.

![Telegram kommunikation arkivering arbejdsproces.](../media/TelegramConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en Telegram Archiver-connector. Du kan få flere oplysninger under [Aktivering af TeleMessage Telegram Archiver til Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. I realtid kopieres din organisations Telegram-data til TeleMessage-webstedet.

3. Telegram Archiver-connectoren, som du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mailmeddelelserne fra de forrige 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

4. Connectoren importerer mobilkommunikationselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet TelegramArkiver i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle mails indeholder denne egenskab, som udfyldes med mailadressen for hver deltager i mailen.

> Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365-postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger connectoren brugerens mailadresseegenskab for mailelementet. Hvis connectoren ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede *tilknytningsfil eller brugerens mailadresseegenskab* for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Bestil [Telegram-arkiveringstjenesten fra TeleMessage,](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Registrer alle brugere, der kræver telegramarkivering, på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Installér Telegram Archiver-appen på dine medarbejderes mobiltelefoner, og aktivér den. Telegram Archiver-appen giver dem mulighed for at kommunikere og chatte med andre Telegram-brugere.

- Den bruger, der opretter en Telegram Archiver-connector i trin 3, skal tildeles rollen Data Connector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-telegram-archiver-connector"></a>Opret en Telegram Archiver-connector

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette Connectoren Telegram Archiver på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overfører Telegram-kommunikationsdata til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Dataconnectors** > T **elegram Archiver**.

2. Klik på **Tilføj connector** på produktbeskrivelsessiden **Telegramarkiv**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. På siden **Log på TeleMessage** under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

    - **Brugernavn:** Dit TeleMessage-brugernavn.

    - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når connectoren er oprettet, kan du lukke pop op-vinduet og gå til næste side.

6. Aktivér automatisk brugertilknytning på siden **Brugertilknytning** . Hvis du vil aktivere brugerdefineret tilknytning, skal du uploade en CSV-fil, der indeholder brugertilknytningsoplysningerne, og derefter klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til fanen Forbindelser på siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
