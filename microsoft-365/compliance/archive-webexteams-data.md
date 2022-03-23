---
title: Konfigurer en forbindelse til Webex Teams data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere data fra Veritas Webex-forbindelseskomponent Teams en Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 0906156f5c0c796deaa5bd72738813d912e30b47
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590408"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Konfigurere en forbindelse til at arkivere Webex Teams data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Webex Teams til brugerpostkasser i Microsoft 365 organisation. Veritas indeholder en [Webex Teams-forbindelse](https://globanet.com/webex-teams/), der er konfigureret til at registrere Webex Teams-kommunikationselementer og importere dem til Microsoft 365. Forbindelsen konverterer indhold fra Webex Teams, f.eks. 1:1-chatsamtaler, gruppesamtaler, kanalsamtaler og vedhæftede filer fra organisationens Webex Teams-konto, til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Webex Teams-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder i forbindelse med kommunikation. Hvis du bruger en Webex Teams-forbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-webex-teams-data"></a>Oversigt over arkivering af Webex Teams data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Webex Teams data i Microsoft 365.

![Arkiveringsarbejdsproces for Webex Teams data.](../media/WebexTeamsConnectorWorkflow.png)

1. Din organisation arbejder sammen med Webex Teams at konfigurere et Webex-Teams-websted.

2. Én gang i døgnet kopieres Webex Teams elementer til webstedet Veritas Merge1. Forbindelsen konverterer også Webex-elementer Teams til et mailformat.

3. Den Webex Teams-forbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til Veritas Merge1 hver dag og overfører Webex Teams-elementerne til en sikker Azure Storage-placering i Microsoft-skyen.

4. Forbindelsen importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben Mail  for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med **navnet Webex Teams** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Forbindelsen gør dette ved hjælp af værdien *af egenskaben Mail* . Hver Webex Teams element indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Opret et program på for at [https://developer.webex.com/](https://developer.webex.com) hente data fra din Webex Teams-konto. Du kan finde en trinvis vejledning til oprettelse af programmet i [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Når du opretter dette program, genererer Webex-platformen et sæt unikke legitimationsoplysninger. Disse legitimationsoplysninger bruges i trin 2, når du konfigurerer Webex Teams-forbindelsen på webstedet Global Flet1.

- Den bruger, der opretter Webex Teams-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Trin 1: Konfigurer Webex Teams forbindelse

Det første trin er at få adgang til **dataforbindelserne** og konfigurere [Webex Teams forbindelse](https://globanet.com/webex-teams/).

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserWebex** >  **Teams**.

2. Klik på **Tilføj Teams** webex-produktbeskrivelse på **siden Produktbeskrivelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Webex Teams-forbindelsen på webstedet Veritas Merge1

Det andet trin er at konfigurere Webex Teams-forbindelsen på webstedet Flet1. Hvis du vil have mere at vide om, hvordan du konfigurerer Webex Teams-forbindelsen, skal du se [Brugervejledning til Flet1 tredjepartsforbindelser](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Map Webex Teams brugere Microsoft 365 aktivere** automatisk tilknytning af brugere. Webex-Teams indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Trin 4: Overvåg WebEx-Teams forbindelseskomponent

Når du har oprettet Webex Teams forbindelse, kan du få vist forbindelsens status på Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser**, og vælg derefter **Webex-forbindelsen Teams** for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om de data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.