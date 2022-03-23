---
title: Konfigurer en forbindelse til at arkivere Salesforce Chatter-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere Salesforce Chatter-data fra Veritas til Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: bb52bd95d11a93c2bbb6816ed189ef5e0594ffac
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594382"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>Konfigurer en forbindelse til at arkivere Salesforce Chatter-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Salesforce Chatter-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas har [en Salesforce Chatter-forbindelse](http://globanet.com/chatter/), der henter elementer fra datakilden fra tredjeparten og importerer disse elementer Microsoft 365. Forbindelsen konverterer indholdet som chatsamtaler, vedhæftede filer og indlæg fra Salesforce Chatter til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Salesforce Chatter-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger en Salesforce Chatter-forbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Oversigt over arkivering af Salesforce Chatter-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Salesforce Chatter-dataene Microsoft 365.

![Arkivering af arbejdsproces for Salesforce Chatter-data.](../media/SalesforceChatterConnectorWorkflow.png)

1. Din organisation arbejder sammen med Salesforce Chatter om at konfigurere et Salesforce Chatter-websted.

2. Én gang i døgnet kopieres Salesforce Chatter-elementer til webstedet Veritas Merge1. Forbindelsen også Salesforce Chatter-elementer til et mailformat.

3. Den Salesforce Chatter-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører Chatter-indholdet til et sikkert Azure Storage placering i Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Salesforce Chatter** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle Chatter-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Opret et Salesforce-program, og få et token på [https://salesforce.com](https://salesforce.com). Du skal logge på Salesforce-kontoen som administrator og have et personligt brugertoken for at importere data. Desuden skal udløsere publiceres på Chatter-webstedet for at registrere opdateringer, sletninger og redigeringer. Disse udløsere opretter et indlæg på en kanal, og Flet1 registrerer oplysningerne fra kanalen. Du kan finde en trinvis vejledning til, hvordan du opretter programmet og køber tokenet, under Brugervejledning til forbindelser [fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- Den bruger, der opretter forbindelseskomponent til Salesforce Chatter i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>Trin 1: Konfigurer Salesforce Chatter-forbindelsen

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til Chatter-data.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserSalgsforce** >  **Chatter**.

2. Klik på **Tilføj forbindelse på siden produktbeskrivelse for Salesforce Chatter****.**

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Salesforce Chatter på webstedet Veritas Merge1

Det andet trin er at konfigurere Salesforce Chatter-forbindelsen på Veritas Merge1-webstedet. Hvis du vil have mere at vide om, hvordan du konfigurerer Salesforce Chatter-forbindelsen, skal du se [Brugervejledning til forbindelse fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

Når du har **klikket &,** vises siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelse.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Salesforce Chatter-brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. Salesforce Chatter-elementer indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>Trin 4: Overvåg Forbindelseskomponent til Salesforce Chatter

Når du har oprettet forbindelseslinjen Salesforce Chatter, kan du få vist forbindelsens status Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og klik derefter på **Salesforce Chatter-forbindelsen** for at få vist pop op-siden, som indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.