---
title: Konfigurer en forbindelse til at arkivere data fra TeleMessage Enterprise Number Archiver
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere sms- og mms-data fra TeleMessage Enterprise-nummerarkivet. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 58450875c418c0ea2327d78c7dcadd3c4992fb77
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589700"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Konfigurer en forbindelse til at arkivere virksomhedsnummerdata

Brug en TeleMessage-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere SMS- og multimedia messaging servicemeddelelser (MMS), chatbeskeder, stemmeopkaldsoptagelser og stemmeopkaldslogge fra Enterprise Number Archiver. Når du konfigurerer en forbindelse, opretter den forbindelse til din organisations TeleMessage-konto én gang hver dag og importerer mobilkommunikationsdata for medarbejdere ved hjælp af TeleMessage Enterprise Number Archiver til postkasser i Microsoft 365.

Når forbindelsesdataene for TeleMessage Enterprise Number Archiver er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning, In-Place arkivering, overvågning, overholdelse af regler og standarder i kommunikation og Microsoft 365-opbevaringspolitikker på virksomhedsnummerarkivdata. Du kan f.eks. søge i TeleMessage Enterprise Number Archiver SMS, MMS og Voice Call ved hjælp af indholdssøgning eller tilknytte den postkasse, der indeholder forbindelsesdataene fra Enterprise Number Archiver, til en leder i Advanced eDiscovery sag. Ved hjælp af en forbindelseskomponent til Enterprise-nummerarkiv til at importere og arkivere data i Microsoft 365 kan din organisation holde sig i overensstemmelse med offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-enterprise-number-data"></a>Oversigt over arkivering af Enterprise Number-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Enterprise Network-data Microsoft 365.

![Arbejdsprocessen for arkivering af virksomhedsnummer.](../media/EnterpriseNumberConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelse til Enterprise Number Archiver. Du kan finde flere [oplysninger her.](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/)

2. Forbindelsen Enterprise Number Archiver, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mails fra de foregående 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

3. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet Enterprise Number Archiver i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen tilknytter ved hjælp af værdien af *brugerens mailadresseegenskab* . Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger forbindelsen brugerens mailadresseegenskab for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller brugerens mailadresseegenskab for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere data fra Enterprise Number Archiver, er eksterne Microsoft 365 og skal udføres, før du kan oprette forbindelsen i overholdelsescenteret.

- Bestil [Enterprise Number Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto for organisationen. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Registrer alle brugere, der kræver arkivering af SMS/MMS Network med Enterprise Number i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Installér og aktivér TeleMessage Enterprise Number Archiver-appen på dine medarbejderes mobiltelefoner.

- Den bruger, der opretter en forbindelse til et enterprise-nummerarkiv, skal være tildelt rollen Som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-an-enterprise-number-archiver-connector"></a>Opret en forbindelseskomponent til virksomhedsnummerarkiv

Når du har gennemført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette en forbindelse til Enterprise-nummerarkiver i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre sms-, mms- og taleopkaldsmeddelelser til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik derefter **på Dataforbindelser** **Enterprise-nummerarkiver**\>.

2. På **produktbeskrivelsen for Enterprise Number Archiver** skal du klikke på **Tilføj forbindelse**

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