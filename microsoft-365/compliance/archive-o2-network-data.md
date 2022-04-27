---
title: Konfigurer en connector til arkivering af O2-netværksdata i Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere SMS- og MMS-data fra O2-mobilnetværket i Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 525420c3c838cdab677c08f07910bd709b774715
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077524"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Konfigurer en connector til arkivering af O2-netværksdata

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en TeleMessage-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere sms-beskeder og taleopkald fra O2-mobilnetværket. Når du har konfigureret en connector, opretter den forbindelse til organisationens O2-netværk én gang om dagen og importerer sms- og taleopkald til postkasser i Microsoft 365.

Når sms-beskeder og taleopkald er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, Content Search og Microsoft 365 opbevaringspolitikker, på O2 Network-data. Du kan f.eks. søge i O2 Network-sms-beskeder og taleopkald ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder O2 Network-data, til en tilsynsførende i et eDiscovery-tilfælde (Premium). Hvis du bruger en O2 Network-connector til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-o2-network-data"></a>Oversigt over arkivering af O2-netværksdata

I følgende oversigt forklares processen med at bruge en connector til at arkivere O2-netværksdata i Microsoft 365.

![O2 Netværksarkiveringsarbejdsproces.](../media/O2NetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og O2 om at konfigurere en O2-netværksconnector. Du kan få flere oplysninger under [O2 Network Archiver](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Hver 24. time kopieres sms-beskeder og taleopkald fra organisationens O2-netværk til telemeddelelseswebstedet.

3. Den O2 Network-connector, du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører SMS-meddelelser og taleopkald fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet af sms-beskeder og taleopkald til et mailformat.

4. Connectoren importerer mobilkommunikationselementerne til bestemte brugeres postkasse. Der oprettes en ny mappe med navnet **O2 SMS og Voice Network Archiver** i en bestemt brugers postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle sms-beskeder og taleopkald indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i meddelelsen.

   Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og tilsvarende Microsoft 365 mailadresse for brugere i din organisation. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, kigger connectoren først på den brugerdefinerede tilknytningsfil for hvert O2-element. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers mobiltelefonnummer, bruger connectoren værdierne i egenskaben mailadresse for det element, den forsøger at importere. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller i egenskaben for mailadressen for O2-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de implementeringstrin, der kræves for at arkivere O2-netværksdata, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette en connector i Overholdelsescenter.

- Bestil [O2-netværksarkivtjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) , og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Få din O2 Network-konto og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne for TeleMessage og bestille tjenesten til arkivering af meddelelser fra O2.

- Registrer alle brugere, der kræver O2 SMS- og Voice Network-arkivering, på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365 konto.

- Dine medarbejdere skal have virksomhedsejede og virksomhedsansvarende mobiltelefoner på O2-mobilnetværket. Arkivering af meddelelser i Microsoft 365 er ikke tilgængelig for medarbejderejede eller BYOD-enheder (Bring Your Own Devices).

- Den bruger, der opretter en O2-netværksconnector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-an-o2-network-connector"></a>Opret en O2-netværksconnector

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette en O2 Network-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til telemeddelelseswebstedet og overføre sms-beskeder og taleopkald til de tilsvarende postkassefelter for brugeren i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **Dataconnectors** \> **O2 Network**.

2. Klik på **Tilføj connector** på siden med produktbeskrivelsen til **O2-netværket**

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