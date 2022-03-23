---
title: Konfigurer en forbindelse til at arkivere data fra MS SQL Database
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere data fra MS SQL Database. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: f00b76cb2199d1af9daca58e86ad7cd2009c2031
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591731"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>Konfigurer en forbindelse til at arkivere data fra MS SQL Database

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra MS SQL Database til brugerpostkasser i Microsoft 365 organisation. Veritas giver dig en MS SQL Database Importer-forbindelse, der er konfigureret til at hente elementer fra en database ved hjælp af en XML-konfigurationsfil og importere disse elementer til Microsoft 365. Forbindelsen konverterer indhold fra MS SQL Database til et mailmeddelelsesformat og importerer derefter disse elementer til brugerpostkasser Microsoft 365.

Når indhold fra MS SQL Database i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger en MS SQL Database-forbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-the-ms-sql-data"></a>Oversigt over arkivering af MS SQL data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere MS SQL data i Microsoft 365.

![Arkivering af arbejdsproces for MS SQL data.](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Din organisation arbejder sammen med en MS SQL Database-udbyder for at konfigurere et MS SQL Database websted.

2. Én gang i døgnet kopieres MS SQL Database elementer til webstedet Veritas Merge1. Forbindelsen konverterer også dette indhold til et mailformat.

3. Forbindelsen MS SQL Database Importer, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede MS SQL Database til postkasser for bestemte brugere med værdien af egenskaben Mail for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **MS SQL Database Importer** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hvert element fra MS-SQL Database indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter forbindelsen MS SQL Database-importprogram i trin 1 (og fuldfører den i trin 3), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>Trin 1: Konfigurer forbindelsen MS SQL Database importprogram

Det første trin er at få adgang til siden **Dataforbindelser** i Microsoft 365 Overholdelsescenter og oprette en forbindelse til MS SQL Database.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik derefter **på DataforbindelserMS** >  **SQL Database Importprogram**.

2. Klik på **Tilføj SQL Database** forbindelse på siden **Produktbeskrivelse for MS-importprogram**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer forbindelsen MS SQL Database Importer på webstedet Veritas Merge1

Det andet trin er at konfigurere forbindelsen MS SQL Database importprogram på webstedet Flet1. Hvis du vil have mere at vide om, hvordan du konfigurerer MS SQL Database-importprogram, skal du [se Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Følg disse trin for at tilknytte brugere og fuldføre konfigurationen af forbindelsen:

1. På siden **Tilknyt MS SQL Database brugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. MS-SQL Database indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>Trin 4: Overvåg forbindelsen MS SQL Database Importprogram

Når du har oprettet forbindelsen MS SQL Database importprogram, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com/> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser**, og vælg derefter **forbindelsen MS SQL Database** **Importer** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.