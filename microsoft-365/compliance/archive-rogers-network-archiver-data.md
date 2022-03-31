---
title: Konfigurer en forbindelse til at arkivere Rogers-netværksdata i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere Rogers Network-data Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 7ff260640606a2870cefca0de5e8b833018760cc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63600940"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data"></a>Konfigurere en forbindelse til at arkivere Rogers-netværksdata

Brug teleMessage-forbindelsen i Microsoft 365 Overholdelsescenter til at importere og arkivere sms- og mms-data fra Mobilnetværket Rogers. Når du har konfigureret og konfigureret en Connector, der er modtager af Rogers-netværksarkivet, oprettes der forbindelse til organisationens mobile netværk, som også importerer sms- og [mms-data](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/) til postkasser i Microsoft 365.

Når data fra mobilnetværket Rogers er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til dataene. Du kan f.eks. søge efter sms- og mms-meddelelser fra mobilnetværket Rogers ved hjælp af indholdssøgning eller en søgning, der er knyttet til en core eDiscovery-sag. Hvis du bruger en forbindelseskomponent fra Rogers Network Archiver til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde gældende love og lovgivning.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Oversigt over arkivering af Rogers-mobilnetværksdata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Rogers sms- og mms-data Microsoft 365.

![Workflow for arkivering af netværk under Rogers.](../media/RogersNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelseskomponent til Rogers Network Archiver. Du kan finde flere oplysninger [under Aktivering af TeleMessage Rogers Network Archiver for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. I realtid kopieres din organisations mobildata fra Rogers til TeleMessage-webstedet.

3. Connectoren Rogers Network Archiver, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mails fra de foregående 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. En ny mappe med navnet Rogers Sms/MMS Network Archiver oprettes i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen bruges til tilknytningen ved hjælp af værdien af *brugerens mailadresseegenskab* . Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen.

   Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert mailelement. Hvis den ikke finder en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger forbindelsen brugerens mailadresseegenskab for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller brugerens mailadresseegenskab for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Bestil [servicen Rogers Network Archiver fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) , og få en gyldig administrationskonto for din organisation. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Registrer alle brugere, der kræver, at Rogers Network arkiverer i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Dine medarbejdere skal have mobiltelefoner, der ejes af virksomheder og kan holdes ansvarlige for virksomheden, på O2-mobilnetværket. Arkivering af meddelelser Microsoft 365 ikke tilgængelig for medarbejderejede enheder eller "Medbring dine egne enheder (BYOD)-enheder.

- Hent onboardingformularerne til Rogers-kontoen og faktureringskontaktoplysningerne for din organisation, så du kan udfylde onboardingformularerne og bestille arkiveringstjenesten for meddelelser fra Rogers.

- Den bruger, der opretter forbindelsesforbindelsen Rogers-netværksarkiv i trin 3, skal have tildelt administratorrollen Dataforbindelse. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-rogers-network-archiver-connector"></a>Opret en Forbindelse til Network Archiver i Rogers

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette connectoren Rogers Network Archiver i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre Mails SMS/MMS-data til de tilsvarende brugerpostkasser Microsoft 365.

1. Gå til og <https://compliance.microsoft.com> klik derefter **på DataforbindelserRogers** >  **Netværksarkiver**.

2. Klik på **Tilføj forbindelse på siden med produktbeskrivelsen** for Rogers-netværksarkivet.

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
