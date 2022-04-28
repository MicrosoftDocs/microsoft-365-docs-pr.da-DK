---
title: Konfigurer en connector til arkivering af Android-mobildata
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
description: Administratorer kan konfigurere en TeleMessage-connector til at importere og arkivere sms-, MMS- og taleopkald fra Android-mobiltelefoner. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: b250d87ca84360f62467d2e0853384e4fbb1eaef
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65086991"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data"></a>Konfigurer en connector til arkivering af Android-mobildata

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en TeleMessage-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere SMS, MMS, taleopkald og opkaldslogge fra Android-mobiltelefoner. Når du har konfigureret en connector, oprettes der forbindelse til din organisations TeleMessage-konto én gang om dagen, og medarbejdernes mobilkommunikation importeres ved hjælp af TeleMessage Android Archiver til postkasser i Microsoft 365.

Når data fra Android-mobiltelefoner er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, Content Search og Microsoft 365 opbevaringspolitikker, på Android Archiver-data. Du kan f.eks. søge i Mobilkommunikation i Android Archiver ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder Android Archiver-connectordataene, til en tilsynsførende i et eDiscovery-tilfælde (Premium). Brug af en Android Archiver-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-android-mobile-data"></a>Oversigt over arkivering af Android-mobildata

I følgende oversigt forklares processen med at bruge en connector til at arkivere Android-mobildata i Microsoft 365.

![Arbejdsproces for Android Archiver-connector.](../media/AndroidArchiverConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en Android Archiver-connector. Du kan få flere oplysninger under [Android Archiver](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. I realtid kopieres SMS, MMS, taleopkald og opkaldslogfiler fra din organisations Android-mobiltelefoner til TeleMessage-webstedet.

3. Den Android Archiver-connector, du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører Android-dataene fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også Android-dataene til et mailformat.

4. Connectoren importerer mobilkommunikationselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet Android Archiver i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren tilknytter ved hjælp af værdien for *brugerens mailadresseegenskab* . Alle mails indeholder denne egenskab, som udfyldes med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde mobilnummeret og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert mailelement. Hvis den ikke finder en gyldig Microsoft 365 bruger, der svarer til en brugers mobilnummer, bruger connectoren brugerens mailadresseegenskab for mailelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede *tilknytningsfil eller brugerens mailadresseegenskab* for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de trin til implementering, der kræves for at arkivere Android-kommunikationsdata, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette connectoren i Overholdelsescenter.

- Bestil [Android Archiver-tjenesten fra TeleMessage,](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter connectoren.

- Registrer alle brugere, der kræver Android Archiver-tjenesten, på TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365 konto.

- Installér og aktivér appen TeleMessage Android Archiver på dine medarbejderes mobiltelefoner.

- Den bruger, der opretter en Android Archiver-connector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-an-android-archiver-connector"></a>Opret en Android Archiver-connector

Det sidste trin er at oprette en Android Archiver-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til telemeddelelseswebstedet og overføre Android-kommunikation til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com) , og klik på **DataconnectorsAndroid** >  **Archiver**.

2. På siden med **produktbeskrivelser til Android Archiver** skal du klikke på **Tilføj connector**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. På siden **Log på TeleMessage** under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

   - **Brugernavn:** Dit TeleMessage-brugernavn.

   - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når connectoren er oprettet, skal du lukke pop op-vinduet og klikke på **Næste**.

6. Aktivér automatisk **brugertilknytning på siden Brugertilknytning** , og klik på **Næste**. Hvis du har brug for brugerdefineret tilknytning, skal du overføre en CSV-fil og klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til fanen Forbindelser på siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
