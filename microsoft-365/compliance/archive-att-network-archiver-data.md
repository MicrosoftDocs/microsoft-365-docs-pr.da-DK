---
title: Konfigurer en connector til arkivering af AT&T SMS/MMS Network-data
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere SMS- og MMS-data fra AT&T Mobile Network. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft Purview, så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 1e7c3b1de79d4777beec22b0b1a5506fc8bccf6a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625869"
---
# <a name="set-up-a-connector-to-archive-att-smsmms-data"></a>Konfigurer en connector til arkivering af AT&T SMS/MMS-data

Brug en TeleMessage-connector i Microsoft Purview-compliance-portal til at importere og arkivere SMS- og MMS-data fra AT&T Mobile Network. Når du har konfigureret en connector, opretter den forbindelse til organisationens AT&T Network én gang om dagen og importerer SMS- og MMS-data til postkasser i Microsoft Purview.

Når SMS- og MMS-meddelelser er gemt i brugerpostkasser, kan du anvende Microsoft 365 Purview-funktioner, f.eks. litigation hold, content search og Microsoft 365 retention policies, på AT&T Network-data. Du kan f.eks. søge i AT&T Network-data ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder AT&T Network-connectordataene, til en tilsynsførende i en eDiscovery-sag (Premium). Hvis du bruger en AT&T Network-connector til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-att-network-data"></a>Oversigt over arkivering af AT&T Network-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere AT&T Network-data i Microsoft 365.

![ATT Netværksarkiveringsarbejdsproces.](../media/ATTNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en AT&T Network-connector. Du kan få flere oplysninger under [AT&T Network Archiver](https://www.telemessage.com/office365-activation-for-atnt-network-archiver/).

2. I realtid kopieres SMS- og MMS-meddelelser fra organisationens AT&T Network til telemeddelelseswebstedet.

3. Den AT&T Network-connector, du opretter i overholdelsesportalen, opretter forbindelse til telemeddelelseswebstedet hver dag og overfører SMS- og MMS-meddelelserne fra de forrige 24 timer til en sikker Azure Storage-placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet af sms- og mms-meddelelser til et mailformat.

4. Connectoren importerer mobilkommunikationselementerne til bestemte brugeres postkasse. Der oprettes en ny mappe med navnet **AT&T SMS/MMS Network Archiver** i brugerens postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle SMS- og MMS-meddelelser indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager i meddelelsen.
 
   Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og den tilsvarende Microsoft 365-mailadresse for brugere i din organisation. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, kigger connectoren først på den brugerdefinerede tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til et mobiltelefonnummer, bruger connectoren værdierne i egenskaben mailadresse for det element, den forsøger at importere. Hvis connectoren ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller i mailadresseegenskaben for mailelementet, importeres elementet ikke.

## <a name="before-you-begin"></a>Før du begynder

Nogle af de implementeringstrin, der kræves for at arkivere AT&T Network-data, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette connectoren i Overholdelsescenter.

- Bestil [mobilarkiveringstjenesten fra TeleMessage,](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Få dine AT&T-konto- og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne for TeleMessage og bestille tjenesten til arkivering af meddelelser fra AT&T.

- Registrer alle brugere, der kræver AT&T SMS/MMS Network-arkivering på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Dine medarbejdere skal have virksomhedsejede og virksomhedsansvarende mobiltelefoner på AT&T-mobilnetværket. Arkivering af meddelelser i Microsoft 365 er ikke tilgængelig for medarbejderejede eller BYOD-enheder (Bring Your Own Devices).

- Den bruger, der opretter en AT&T Network-connector, skal tildeles rollen DataConnector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen og derfor ikke er omfattet af Microsoft Purview- og databeskyttelsesforpligtelserne. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-att-network-connector"></a>Opret en AT&T Network-connector

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette en AT&T Network-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til telemeddelelseswebstedet og overføre SMS- og MMS-meddelelser til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** \ **AT&T Network**.

2. På produktbeskrivelsessiden **AT&T Network** skal du klikke på **Tilføj connector**

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
