---
title: Konfigurer en forbindelse til at arkivere O2-netværksdata i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere sms- og mms-data fra O2-mobilnetværket i Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: cf3e7f42f8497b2bbba06ccda4e84956b731ede2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588464"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Konfigurere en forbindelse til at arkivere O2-netværksdata

Brug en TeleMessage-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere SMS-beskeder og taleopkald fra O2-mobilnetværket. Når du konfigurerer en forbindelse, opretter den forbindelse til organisationens O2-netværk én gang dagligt og importerer sms'er og taleopkald til postkasser i Microsoft 365.

Når sms'er og taleopkald er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til O2-netværksdata. Du kan f.eks. søge efter O2-netværks-sms'er og taleopkald ved hjælp af Indholdssøgning eller knytte den postkasse, der indeholder O2-netværksdata, til en medarbejder, der er tilknyttet en Advanced eDiscovery sag. Brug af en O2-netværksforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-o2-network-data"></a>Oversigt over arkivering af O2-netværksdata

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere O2-netværksdata Microsoft 365.

![O2 Arbejdsproces for netværksarkivering.](../media/O2NetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og O2 om at konfigurere en O2-netværksforbindelse. Du kan finde flere oplysninger [i O2 Network Archiver](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Én gang i døgnet kopieres sms-beskeder og taleopkald fra din organisations O2-netværk til TeleMessage-webstedet.

3. Den O2-netværksforbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører sms'er og taleopkald fra de foregående 24 timer til en sikker Azure Storage-placering i Microsoft-skyen. Forbindelsen konverterer også indholdet af sms-beskeder og taleopkald til et mailformat.

4. Forbindelsen importerer elementer fra mobilkommunikation til postkassen for bestemte brugere. En ny mappe med **navnet O2 SMS and Voice Network Archiver** oprettes i en bestemt brugers postkasse, og elementerne importeres til den. Forbindelsen gør denne tilknytning ved hjælp af værdien af *egenskaben Brugers* mailadresse. Alle sms'er og taleopkald indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i meddelelsen.

   Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og Microsoft 365 mailadressen for brugere i organisationen. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert O2-element. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobiltelefonnummer, bruger forbindelsen værdierne i mailadresseegenskaben for det element, den forsøger at importere. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller i O2-elementets mailadresseegenskab, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere O2-netværksdata, er eksterne i forhold til Microsoft 365 og skal udføres, før du kan oprette en forbindelse i overholdelsescenteret.

- Bestil [O2 Network Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) , og få en gyldig administrationskonto for organisationen. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Hent dine O2 Network-konto- og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne til TeleMessage og bestille meddelelsesarkivtjenesten fra O2.

- Registrer alle brugere, der kræver arkivering af O2-sms og Talenetværk i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Dine medarbejdere skal have mobiltelefoner, der ejes af virksomheder og kan holdes ansvarlige for virksomheden, på O2-mobilnetværket. Arkivering af meddelelser Microsoft 365 ikke tilgængelig for medarbejderejede enheder eller "Medbring dine egne enheder (BYOD)-enheder.

- Den bruger, der opretter en O2-netværksforbindelse, skal have tildelt rollen som Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-an-o2-network-connector"></a>Oprette en O2-netværksforbindelse

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette en O2-netværksforbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen bruger de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre sms'er og taleopkald til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik derefter **på Dataforbindelser** \> **O2-netværk**.

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **O2-netværk**

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