---
title: Konfigurer en connector til arkivering af WhatsApp-data i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere WhatsApp-data i Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: d48e4108fdf89023d3b41d9c1ff6a31e0148b17d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094047"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>Konfigurer en connector til arkivering af WhatsApp-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug TeleMessage-connectoren på Microsoft Purview-overholdelsesportalen til at importere og arkivere WhatsApp-opkald, chats, vedhæftede filer, filer og slettede meddelelser. Når du har konfigureret en connector, oprettes der forbindelse til din organisations TeleMessage-konto én gang om dagen, og medarbejdernes mobilkommunikation importeres ved hjælp af TeleMessage WhatsApp Telefon Archiver eller TeleMessage WhatsApp Cloud Archiver til postkasser i Microsoft 365.

Når WhatsApp-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, Content Search og Microsoft 365 opbevaringspolitikker, på WhatsApp-data. Du kan f.eks. søge i WhatsApp-meddelelser ved hjælp af Indholdssøgning eller knytte den postkasse, der indeholder WhatsApp-meddelelser, til en tilsynsførende i en eDiscovery-sag (Premium). Brug af en WhatsApp-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-whatsapp-data"></a>Oversigt over arkivering af WhatsApp-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere WhatsApp-data i Microsoft 365.

![WhatsApp-arkiveringsarbejdsproces.](../media/WhatsAppConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en WhatsApp Archiver-connector. Du kan få flere oplysninger under [WhatsApp Archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. I realtid kopieres organisationens WhatsApp-data til TeleMessage-webstedet.

3. Den WhatsApp-connector, du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører WhatsApp-data fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet WhatsApp-data til et mailmeddelelsesformat.

4. Connectoren importerer WhatsApp-data til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet **WhatsApp Archiver** i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren udfører denne tilknytning ved hjælp af værdien af egenskaben *For brugerens mailadresse* . Alle WhatsApp-meddelelser indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i meddelelsen.

   Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også implementere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og tilsvarende Microsoft 365 mailadresse for brugere i din organisation. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, kigger connectoren først på brugerdefineret tilknytningsfil for hvert WhatsApp-element. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers mobiltelefonnummer, bruger connectoren værdierne i egenskaben mailadresse for det element, den forsøger at importere. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller i egenskaben mailadresse for WhatsApp-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de implementeringstrin, der kræves for at arkivere WhatsApp-kommunikationsdata, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette connectoren i Overholdelsescenter.

- Bestil [WhatsApp Archiver-tjenesten fra TeleMessage,](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren i Overholdelsescenter.

- Registrer alle brugere, der kræver WhatsApp-arkivering, på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365 konto.

- Installér appen TeleMessage [WhatsApp Telefon Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) på dine medarbejderes mobiltelefoner, og aktivér den. Alternativt kan du installere de almindelige WhatsApp- eller WhatsApp Business-apps på dine medarbejderes mobiltelefoner og aktivere Tjenesten WhatsApp Cloud Archiver ved at scanne en QR-kode på TeleMessage-webstedet. Du kan få flere oplysninger under [WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Den bruger, der opretter en Verizon Network-connector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-whatsapp-archiver-connector"></a>Opret en WhatsApp Archiver-connector

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette WhatsApp-connectoren på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre WhatsApp-dataene til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsWhatsApp** >  **Archiver**.

2. Klik på **Tilføj connector** på siden **WhatsApp Archiver-produktbeskrivelse**

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
