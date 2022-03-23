---
title: Konfigurer en forbindelse til at arkivere Verizon-netværksdata i Microsoft 365
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
description: Administratorer kan konfigurere en TeleMessage-forbindelse til at importere og arkivere sms- og mms-data fra Verizon-netværket Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 3f9ae6d64a1cd89da580f84fa03add0ef0f54183
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590930"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Konfigurer en forbindelse til at arkivere Verizon Network-data

Brug forbindelsesforbindelsen TeleMessage i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Verizon Network (Short Messaging Service) og Multimedia Messaging Service (mms). Når du konfigurerer en forbindelse, opretter den forbindelse til din organisations Verizon-netværk én gang hver dag og importerer sms- og mms-data til postkasser i Microsoft 365.

Når Verizon Network-forbindelsesdata er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning og Microsoft 365 opbevaringspolitikker til Verizon-data. Du kan f.eks. søge efter Verizon-sms- og mms-meddelelser ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder Verizon-netværksdata, til en person, der er tilknyttet en Advanced eDiscovery sag. Brug af en Verizon-netværksforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-verizon-network-data"></a>Oversigt over arkivering af Verizon Network-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Verizon-netværksdata i Microsoft 365.

![Arbejdsprocessen for arkivering af Verizon-netværk.](../media/VerizonNetworkConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage og Verizon om at konfigurere en Verizon-netværksforbindelse. Du kan finde flere oplysninger [under Verizon Network Archiver](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. Én gang i døgnet kopieres sms- og mms-beskeder fra din organisations Verizon-netværk til TeleMessage-webstedet.

3. Den Verizon Network-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører sms- og mms-meddelelser fra de foregående 24 timer til en sikker Azure Storage-placering i Microsoft-skyen. Forbindelsen konverterer også indholdet af sms- og mms-beskeder til et mailformat.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. En ny mappe med navnet **Verizon SMS/MMS Network Archiver** oprettes i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen gør denne tilknytning ved hjælp af værdien af *egenskaben Brugers* mailadresse. Alle sms'er og mms-meddelelser indeholder denne egenskab, som er udfyldt med mailadressen på hver deltager i meddelelsen.

   Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også implementere brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil indeholder mobiltelefonnummeret og Microsoft 365 mailadressen for brugere i organisationen. Hvis du aktiverer både automatisk brugertilknytning og brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert Verizon-element. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobiltelefonnummer, bruger forbindelsen værdierne i mailadresseegenskaben for det element, den forsøger at importere. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller i egenskaben Mailadresse for Verizon-elementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere Verizon-netværksdata er eksterne Microsoft 365 og skal udføres, før du kan oprette en forbindelse i overholdelsescenteret.

- Bestil [Verizon Network Archiver-tjenesten fra TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) , og få en gyldig administrationskonto for din organisation. Du skal logge på denne konto, når du opretter forbindelsen i overholdelsescenter.

- Hent dine Verizon Network-konto- og faktureringskontaktoplysninger, så du kan udfylde onboardingformularerne til TeleMessage og bestille meddelelsesarkivtjenesten fra Verizon.

- Registrer alle brugere, der kræver Verizon-sms- og MMS-arkivering i TeleMessage-kontoen. Når du registrerer brugere, skal du sørge for at bruge den samme mailadresse, der bruges til deres Microsoft 365-konto.

- Dine medarbejdere skal have mobiltelefoner, der ejes af virksomheder og er ansvarlige for virksomheden, på Verizon-mobilnetværket. Arkivering af meddelelser Microsoft 365 ikke tilgængelig for medarbejderejede enheder eller BYOD-enheder (Bring Your Own Devices).

- Den bruger, der opretter en Verizon-netværksforbindelse, skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-verizon-network-connector"></a>Oprette en Verizon-netværksforbindelse

Når du har fuldført de forudsætninger, der er beskrevet i forrige afsnit, kan du oprette Verizon-netværksforbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre sms- og mms-meddelelser til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik derefter **på DataforbindelserVerizon** >  **Network**.

2. På siden **produktbeskrivelse for Verizon-netværket** skal du klikke **på Tilføj forbindelse**

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