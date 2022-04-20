---
title: Konfigurer en connector til arkivering af Verizon Network-data i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere SMS- og MMS-data fra Verizon Network i Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 5df1adad87c9995caeed4e090a7db0e7fbdf7566
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936967"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Konfigurer en connector til arkivering af Verizon Network-data

Brug TeleMessage-connectoren på Microsoft Purview-overholdelsesportalen til at importere og arkivere sms-data (Short Messaging Service) og MMS-data (Multimedia Messaging Service) fra Verizon Network. Når du har konfigureret en connector, opretter den forbindelse til din organisations Verizon Network én gang om dagen og importerer SMS- og MMS-data til postkasser i Microsoft 365.

Når Verizon Network-connectordata er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner som Litigation Hold, Content Search og Microsoft 365 opbevaringspolitikker på Verizon-data. Du kan f.eks. søge i Verizon SMS- og MMS-meddelelser ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder Verizon Network-data, til en tilsynsførende i en Microsoft Purview eDiscovery-sag (Premium). Brug af en Verizon Network-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-verizon-network-data"></a>Oversigt over arkivering af Verizon Network-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Verizon Network-data i Microsoft 365.

![Verizon Network-arkiveringsarbejdsproces.](../media/VerizonNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og Verizon om at konfigurere en Verizon Network-connector. Du kan få flere oplysninger under [Verizon Network Archiver](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. En gang hver 24 timer kopieres SMS- og MMS-meddelelser fra din organisations Verizon Network til TeleMessage-webstedet.

3. Verizon Network-connectoren, som du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører SMS- og MMS-meddelelserne fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet af sms- og mms-meddelelser til et mailformat.

4. Connectoren importerer mobilkommunikationselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet **Verizon SMS/MMS Network Archiver** i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle SMS- og MMS-meddelelser indeholder denne egenskab, som udfyldes med mailadressen på hver enkelt deltager i meddelelsen.

   Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også implementere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og tilsvarende Microsoft 365 mailadresse for brugere i din organisation. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, kigger connectoren først på brugerdefineret tilknytningsfil for hvert Verizon-element. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers mobiltelefonnummer, bruger connectoren værdierne i egenskaben mailadresse for det element, den forsøger at importere. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller i egenskaben for mailadressen for Verizon-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de trin til implementering, der kræves for at arkivere Verizon Network-data, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette en connector i overholdelsescenteret.

- Bestil [Verizon Network Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Få din Verizon Network-konto og fakturering kontaktoplysninger, så du kan udfylde TeleMessage onboarding formularer og bestille meddelelsen arkivering tjeneste fra Verizon.

- Registrer alle brugere, der kræver Verizon SMS- og MMS-arkivering, på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365 konto.

- Dine medarbejdere skal have virksomhedsejede og virksomhedsansvarende mobiltelefoner på Verizon-mobilnetværket. Arkivering af meddelelser i Microsoft 365 er ikke tilgængelig for BYOD-enheder (Employee-owned) eller Bring Your Own Devices (Bring Your Own Devices).

- Den bruger, der opretter en Verizon Network-connector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-verizon-network-connector"></a>Opret en Verizon Network-connector

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette Verizon Network-connectoren på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til telemeddelelseswebstedet og overføre SMS- og MMS-meddelelser til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik derefter på **DataconnectorsVerizon** >  **Network**.

2. På siden med produktbeskrivelsen til **Verizon Network** skal du klikke på **Tilføj connector**

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. På siden **Log på TeleMessage** under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.
  
   - **Brugernavn:** Dit TeleMessage-brugernavn.

   - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når connectoren er oprettet, kan du lukke pop op-vinduet og gå til næste side.

6. Aktivér automatisk **brugertilknytning på siden Brugertilknytning** , og klik på **Næste**. Hvis du har brug for brugerdefineret tilknytning, skal du overføre en CSV-fil og klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til fanen Forbindelser på siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.