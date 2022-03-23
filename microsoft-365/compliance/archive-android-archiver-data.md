---
title: Konfigurer en forbindelse til at arkivere Android-mobildata
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere sms-, mms- og taleopkald fra Android-mobiltelefoner. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 78eb94bb23b5b6f1b0801bcbfad4a6fc43022398
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589702"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data"></a>Konfigurer en forbindelse til at arkivere Android-mobildata

Brug en TeleMessage-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere sms-, mms-, taleopkalds- og opkaldslogge fra Android-mobiltelefoner. Når du konfigurerer en forbindelse, oprettes der forbindelse til din organisations TeleMessage-konto én gang dagligt, og den importerer mobilkommunikation for medarbejdere ved hjælp af TeleMessage Android Archiver til postkasser i Microsoft 365.

Når data fra Android-mobiltelefoner er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til Android Archiver-data. Du kan f.eks. søge efter mobilkommunikation i Android Archiver ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder android-arkivarkivets forbindelsesdata, til en person, der er tilknyttet en Advanced eDiscovery sag. Hvis du bruger en Android Archiver-forbindelse til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-android-mobile-data"></a>Oversigt over arkivering af Android-mobildata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Android-mobildata i Microsoft 365.

![Arbejdsproces for Android Archiver-forbindelse.](../media/AndroidArchiverConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelse til Android Archiver. Du kan finde flere oplysninger [i Android-arkivering](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. I realtid kopieres sms-, mms-, taleopkalds- og opkaldslogge fra din organisations Android-mobiltelefoner til TeleMessage-webstedet.

3. Den Android Archiver-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører Android-dataene fra de foregående 24 timer til en sikker Azure Storage-placering i Microsoft-skyen. Forbindelsen konverterer også Android-dataene til et mailformat.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet Android-arkivator i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen tilknytter ved hjælp af værdien af *brugerens mailadresseegenskab* . Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde mobilnummeret og den Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert mailelement. Hvis den ikke finder en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger forbindelsen brugerens mailadresseegenskab for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben Brugers  mailadresse for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere Android-kommunikationsdata, er eksterne Microsoft 365 og skal udføres, før du kan oprette forbindelsen i overholdelsescenteret.

- Bestil [Android Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto for din organisation. Du skal logge på denne konto, når du opretter forbindelsen.

- Registrer alle brugere, der kræver Android Archiver-tjenesten i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Installér og aktivér TeleMessage Android Archiver-appen på dine medarbejderes mobiltelefoner.

- Den bruger, der opretter en Android-arkiveringsforbindelse, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-an-android-archiver-connector"></a>Opret en Android Archiver-forbindelse

Det sidste trin er at oprette en Android Archiver-forbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre Android-kommunikation til de tilsvarende postkassefelter for brugere Microsoft 365.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik **på DataforbindelserAndroid** >  **Archiver**.

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **Android-arkivering**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. På siden **Login på TeleMessage under** Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

   - **Brugernavn:** Dit TeleMessage-brugernavn.

   - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når forbindelsen er oprettet, skal du lukke pop op-vinduet og klikke på **Næste**.

6. På siden **Brugertilknytning** skal du aktivere automatisk brugertilknytning og klikke **på Næste**. Hvis du har brug for brugerdefineret tilknytning, skal du overføre en CSV-fil og klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette forbindelsen.

8. Gå til fanen Forbindelser på siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
