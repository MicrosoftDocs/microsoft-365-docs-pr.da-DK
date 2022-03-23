---
title: Konfigurer en forbindelse til at arkivere WhatsApp-data i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere WhatsApp-data i Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: b94d22b787e88de241bee404774caaabf5ac02ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591545"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>Konfigurer en forbindelse til at arkivere WhatsApp-data

Brug teleMessage-forbindelsen i Microsoft 365 Overholdelsescenter til at importere og arkivere WhatsApp-opkald, chats, vedhæftede filer, filer og slettede meddelelser. Når du har konfigureret og konfigureret en forbindelse, oprettes der forbindelse til din organisations TeleMessage-konto én gang hver dag, og den importerer den mobile kommunikation for medarbejdere ved hjælp af TeleMessage WhatsApp Telefon Archiver eller TeleMessage WhatsApp Cloud Archiver til postkasser i Microsoft 365.

Når WhatsApp-data er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365-opbevaringspolitikker til WhatsApp-data. Du kan f.eks. søge efter WhatsApp-meddelelser ved hjælp af indholdssøgning eller tilknytte den postkasse, der indeholder WhatsApp-meddelelser, med en medarbejder i en Advanced eDiscovery sag. Hvis du bruger en WhatsApp-forbindelse til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-whatsapp-data"></a>Oversigt over arkivering af WhatsApp-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere WhatsApp-data Microsoft 365.

![WhatsApp-arkiveringsarbejdsproces.](../media/WhatsAppConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelseskomponent til WhatsApp Archiver. Du kan finde flere oplysninger [under WhatsApp Archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. I realtid kopieres din organisations WhatsApp-data til TeleMessage-webstedet.

3. The WhatsApp connector that you create in the Microsoft 365 Overholdelsescenter connects to the TeleMessage site every day and transfer WhatsApp data from the previous 24 hours to a secure Azure Storage location in the Microsoft cloud. Forbindelsen konverterer også indholdet WhatsApp-data til et mailmeddelelsesformat.

4. Forbindelsen importerer WhatsApp-data til en bestemt brugers postkasse. Der oprettes en **ny mappe med navnet WhatsApp Archiver** i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen gør denne tilknytning ved hjælp af værdien af *egenskaben Brugers* mailadresse. Alle WhatsApp-meddelelser indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i meddelelsen.

   Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også implementere brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og Microsoft 365 mailadressen for brugere i organisationen. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert WhatsApp-element. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobiltelefonnummer, bruger forbindelsen værdierne i mailadresseegenskaben for det element, den forsøger at importere. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller i mailadresseegenskaben for WhatsApp-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere WhatsApp-kommunikationsdata er eksterne i forhold til Microsoft 365 og skal udføres, før du kan oprette forbindelsen i overholdelsescenteret.

- Bestil [WhatsApp Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto for din organisation. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Registrer alle brugere, der kræver Arkivering af WhatsApp i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Installer TeleMessage [WhatsApp Telefon Archiver-appen](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) på dine medarbejderes mobiltelefoner, og aktivér den. Alternativt kan du installere de almindelige WhatsApp- eller WhatsApp Business-apps på dine medarbejderes mobiltelefoner og aktivere WhatsApp Cloud Archiver-tjenesten ved at scanne en QR-kode på TeleMessage-webstedet. Du kan finde flere oplysninger [under WhatsApp Cloud Archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- Den bruger, der opretter en Verizon-netværksforbindelse, skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-whatsapp-archiver-connector"></a>Opret en WhatsApp Archiver-forbindelse

Når du har gennemført de betingelser, der er beskrevet i forrige afsnit, kan du oprette WhatsApp-forbindelsen i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre WhatsApp-dataene til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserHvadsApp-arkivator** > .

2. På siden **produktbeskrivelse for WhatsApp Archiver** skal du klikke på **Tilføj forbindelse**

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. På siden **Login på TeleMessage under** Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

   - **Brugernavn:** Dit TeleMessage-brugernavn.

   - **Adgangskode:** Din TeleMessage-adgangskode.

5. Når forbindelsen er oprettet, kan du lukke pop op-vinduet og gå til den næste side.

6. På siden **Brugertilknytning** skal du aktivere automatisk brugertilknytning og klikke **på Næste**. Hvis du har brug for brugerdefineret tilknytning, skal du overføre en CSV-fil og klikke på **Næste**.

7. Gennemse dine indstillinger, og klik derefter på **Udfør** for at oprette forbindelsen.

8. Gå til fanen Forbindelser på siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
