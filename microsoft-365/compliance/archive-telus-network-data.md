---
title: Konfigurer en forbindelse til at arkivere TELUS-netværksdata i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere sms-data fra TELUS-netværket Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 7aca24c39f9eba5dba532f1224ad68d5ff1d4568
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601551"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>Konfigurer en forbindelse til at arkivere TELUS-netværksdata

Brug teleMessage-forbindelsen i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra din organisations TELUS-netværk (Short Messaging Service). Når du har konfigureret en forbindelse, oprettes der forbindelse til din organisations TELUS-netværk én gang dagligt, og der importeres sms-data til postkasser Microsoft 365.

Når sms'er er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til TELUS-data. Du kan f.eks. søge efter TELUS-sms'er ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder TELUS-dataene, til en assistent i en Advanced eDiscovery sag. Brug af en TELUS-netværksforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-telus-network-data"></a>Oversigt over arkivering af TELUS-netværksdata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere TELUS-netværksdata i Microsoft 365.

![Arbejdsproces for arkivering af TELUS-netværk.](../media/TelusNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og TELUS om at konfigurere en TELUS-netværksforbindelse. Du kan finde flere oplysninger [under TELUS Network Archiver](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. I realtid kopieres sms-beskeder fra din organisations TELUS-netværk til TeleMessage-webstedet.

3. Den TELUS-netværksforbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører sms-beskeder fra de foregående 24 timer til et sikkert Azure Storage-sted i Microsoft-skyen. Forbindelsen konverterer også indholdet af sms-beskeder til et mailformat.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. Der oprettes en **ny mappe med navnet TELUS SMS Network Archiver** i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen tilknytter ved hjælp af værdien af *brugerens mailadresseegenskab* . Alle sms'er indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i sms-beskeden.

   Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også implementere brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og Microsoft 365 mailadressen for brugere i organisationen. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert TELUS-element. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobiltelefonnummer, bruger forbindelsen værdierne i mailadresseegenskaben for det element, den forsøger at importere. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller i mailadresseegenskaben for TELUS-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere TELUS-netværksdata, er eksterne i forhold til Microsoft 365 og skal udføres, før du kan oprette en forbindelse i overholdelsescenteret.

- Bestil [tjenesten TELUS Network Archiver fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto til din organisation. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Hent dine TELUS Network-konto- og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne til TeleMessage og bestille meddelelsesarkivtjenesten fra TELUS.

- Registrer alle brugere, der kræver arkivering af TELUS SMS Network i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Dine medarbejdere skal have mobiltelefoner, der ejes af virksomheder og er ansvarlige for virksomheden, påTELUS-mobilnetværket. Arkivering af meddelelser Microsoft 365 ikke tilgængelig for medarbejderejede enheder eller BYOD-enheder (Bring Your Own Devices).

- Den bruger, der opretter en TELUS-netværksforbindelse, skal have tildelt rollen som Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-telus-network-connector"></a>Opret en TELUS-netværksforbindelse

Når du har gennemført de betingelser, der er beskrevet i forrige afsnit, kan du oprette TELUS Network-forbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre sms-beskeder til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserTELUS-netværk** > .

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **TELUS-netværket**

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
