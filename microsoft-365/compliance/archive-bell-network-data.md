---
title: Konfigurer en connector til arkivering af Bell SMS/MMS Network-data
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere SMS- og MMS-data fra Bell Network. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: dc23e3788958270712bab493cd0364a80a0377f9
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992782"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Konfigurer en connector til arkivering af Bell Network-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en TeleMessage-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere SMS-meddelelser (Short Messaging Service) og MMS-meddelelser (Multimedia Messaging Service) fra Bell Network. Når du har konfigureret en connector, opretter den forbindelse til din organisations Bell Network én gang om dagen og importerer SMS- og MMS-meddelelser til postkasser i Microsoft 365.

Når SMS- og MMS-meddelelserne er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, Content Search og Microsoft 365 opbevaringspolitikker, på Bell Network-data. Du kan f.eks. søge i Bell Network SMS/MMS ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder Bell Network-connectordataene, til en tilsynsførende i en eDiscovery-sag (Premium). Brug af en Bell Network-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-bell-network-data"></a>Oversigt over arkivering af Bell Network-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Bell Network-data i Microsoft 365.

![Bell Network-arkiveringsarbejdsproces.](../media/BellNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og Bell om at konfigurere en Bell Network-connector. Du kan få flere oplysninger under [Bell Network Archiver](https://www.telemessage.com/office365-activation-for-bell-network-archiver).

2. I realtid kopieres sms- og mms-beskeder fra din organisations klokkenetværk til telemeddelelseswebstedet.

3. Bell Network-connectoren, som du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører SMS- og MMS-meddelelserne fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet af sms- og mms-meddelelser til et mailformat.

4. Connectoren importerer mobilkommunikationselementerne til bestemte brugeres postkasse. Der oprettes en ny mappe med navnet **Bell SMS/MMS Network Archiver** i en bestemt brugers postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle SMS- og MMS-meddelelser indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager i meddelelsen.

   Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og tilsvarende Microsoft 365 mailadresse for brugere i din organisation. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, kigger connectoren først på den brugerdefinerede tilknytningsfil for hvert Bell Network-element. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers mobiltelefonnummer, bruger connectoren værdierne i egenskaben mailadresse for det element, den forsøger at importere. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller i mailadresseegenskaben for Bell Network-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de trin til implementering, der kræves for at arkivere Bell Network-data, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette en connector i Overholdelsescenter.

- Bestil [klokkenetværksarkivtjenesten fra TeleMessage,](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Få din Bell Network-konto og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne for TeleMessage og bestille arkiveringstjenesten for meddelelser fra Bell.

- Registrer alle brugere, der kræver Bell SMS/MMS Network-arkivering på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365 konto.

- Dine medarbejdere skal have virksomhedsejede og virksomhedsansvarende mobiltelefoner på Bells mobilnetværk. Arkivering af meddelelser i Microsoft 365 er ikke tilgængelig for medarbejderejede eller BYOD-enheder (Bring Your Own Devices).

- Den bruger, der opretter en Bell Network-connector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-bell-network-connector"></a>Opret en Bell Network-connector

Det sidste trin er at oprette en Bell Network-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til telemeddelelseswebstedet og overføre SMS/MMS-meddelelser til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik derefter på **DataconnectorsBell** >  **SMS/MMS Network Archiver**.

2. Klik på **Tilføj connector** på siden med produktbeskrivelsen til **Bell Network**

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. På siden **Log på TeleMessage** under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

   - **Brugernavn:** Dit TeleMessage-brugernavn.

   - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når connectoren er oprettet, kan du lukke pop op-vinduet og gå til næste side.

6. Aktivér automatisk brugertilknytning på siden **Brugertilknytning** . Hvis du vil aktivere brugerdefineret tilknytning, skal du uploade en CSV-fil, der indeholder brugertilknytningsoplysningerne, og derefter klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til fanen **Forbindelser** på siden **Dataconnectors** i Overholdelsescenter for at se status for importprocessen for den nye connector.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
