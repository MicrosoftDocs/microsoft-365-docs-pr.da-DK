---
title: Konfigurer en forbindelse til at arkivere Communications Data i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere Communications Data fra Exchange Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 2fbe0a97572d13b6d2ba6e26ac02fd5ee8817b8a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599446"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Konfigurer en forbindelse til at arkivere Communications Data fra Ellers

Brug teleMessage-forbindelsen i Microsoft 365 Overholdelsescenter til at importere og arkivere chatsamtaler, vedhæftede filer, filer og slettede meddelelser og opkald. Når du har konfigureret og konfigureret en forbindelse, oprettes der forbindelse til din organisations TeleMessage-konto, og den importerer mobilkommunikation af medarbejdere ved hjælp af Den tilsvarer-arkivator til postkasser i Microsoft 365.

Når indholdsarkivets forbindelsesdata er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til arkiveringsdata. Du kan f.eks. søge efter modtagerkommunikation ved hjælp af indholdssøgning eller tilknytte den postkasse, der indeholder arkiveringsforbindelsesdataene fra Archiver, med en leder i Advanced eDiscovery sag. Hvis du bruger en forbindelse til arkiveringsarkivet til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde gældende love og standarder.

## <a name="overview-of-archiving-telegram-communications-data"></a>Oversigt over arkivering af arkiveringsdata for kommunikation

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Communications Data i Microsoft 365.

![Arbejdsprocesser for arkivering af kommunikation.](../media/TelegramConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelseskomponent til Arkivering. Du kan finde flere oplysninger [under Aktivering af TeleMessage Archiver for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. I realtid kopieres organisationensgramdata til TeleMessage-webstedet.

3. Den forbindelseskomponent til Arkiver, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mails fra de foregående 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet arkivering til arkivering, som oprettes i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen gør denne tilknytning ved hjælp af værdien af *egenskaben Brugers* mailadresse. Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen.

> Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger forbindelsen brugerens mailadresseegenskab for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller brugerens mailadresseegenskab for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Bestil [arkiveringstjenesten for arkivering af arkivering hos TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) , og få en gyldig administrationskonto for organisationen. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Registrer alle brugere, der kræver Arkivering i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Installér appen for arkivering på dine medarbejderes mobiltelefoner, og aktivér den. Appen Arkivering giver dem mulighed for at kommunikere og chatte med andre Arkiver-brugere.

- Den bruger, der opretter en archiver-forbindelse til arkivering i trin 3, skal have tildelt rollen som Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-telegram-archiver-connector"></a>Oprette en arkiveringsforbindelse

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette forbindelsesmappen Archiver i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overfører Indholdet-kommunikationsdata til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på Dataforbindelser >** **Telegram Archiver**.

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **arkivering**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. På siden **Login på TeleMessage under** Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

    - **Brugernavn:** Dit TeleMessage-brugernavn.

    - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når forbindelsen er oprettet, kan du lukke pop op-vinduet og gå til den næste side.

6. På siden **Brugertilknytning** skal du aktivere automatisk brugertilknytning. Hvis du vil aktivere brugerdefineret tilknytning, skal du overføre en CSV-fil, der indeholder brugertilknytningsoplysningerne, og derefter klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette forbindelsen.

8. Gå til fanen Forbindelser på siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
