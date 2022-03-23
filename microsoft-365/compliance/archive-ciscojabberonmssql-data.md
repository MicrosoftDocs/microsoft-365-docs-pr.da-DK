---
title: Konfigurer en forbindelse til at arkivere Cisco Jabber på MS SQL data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere Cisco Jabber på MS SQL data fra Veritas Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 66f09f2fafcd33d8bc73bdaed61b41354e9633f7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591694"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Konfigurer en forbindelse til at arkivere Cisco Jabber på MS SQL data

Brug en Veritas-forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Cisco Jabber-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas giver dig en [Cisco Jabber-forbindelse](https://globanet.com/jabber/), der er konfigureret til at hente elementer fra Jabbers MS SQL Database, f.eks. 1:1-chatbeskeder og gruppechats, og derefter importere disse elementer til Microsoft 365. Forbindelsen henter data fra Cisco Jabbers MS SQL Database, behandler den, og indholdet konverteres fra en brugers Cisco Jabber-konto til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Cisco Jabber-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder og kommunikation. Brug af en Cisco Jabber-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Oversigt over arkivering af Cisco Jabber-data

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Cisco Jabber på MS SQL data Microsoft 365.

![Arkivering af arbejdsproces for Cisco Jabber-data.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Din organisation arbejder sammen med Cisco om at konfigurere en Cisco Jabber på MS SQL Database.

2. Hver 24. time kopieres Cisco Jabber-elementer fra MS-SQL Database til webstedet Veritas Merge1. Forbindelsen konverterer også indholdet af chatmeddelelser til et mailformat.

3. Den Cisco Jabber-forbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører elementerne til en sikker placering Azure Storage Microsoft-skyen.

4. Den automatiske brugertilknytning som forbindelse importerer elementer til bestemte brugeres postkasser ved hjælp af  værdien af egenskaben Mail for den beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber på MS SQL** i brugerpostkasserne, og meddelelseselementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle Cisco Jabber-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Konfigurer en MS-SQL Database at hente Jabber-elementer fra, før du opretter forbindelsen i trin 1. Du skal angive forbindelsesindstillingerne for MS-forbindelsen SQL Database du konfigurerer Cisco Jabber-forbindelsen i trin 2. Du kan få mere at vide [i Brugervejledning til forbindelser fra tredjepart flet1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- Den bruger, der opretter Cisco Jabber-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Trin 1: Konfigurer Cisco Jabber på MS SQL forbindelseskomponent

Det første trin er at få adgang til **dataforbindelserne** i Microsoft 365 Overholdelsescenter og oprette en forbindelse til Cisco Jabber på MS SQL data.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/)og klik derefter **på DataforbindelserCisco** >  **Jabber på MS SQL**.

2. På siden **Cisco Jabber på MS SQL** skal du klikke på **Tilføj forbindelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Cisco Jabber på MS SQL-forbindelsen på webstedet Veritas Merge1

Det andet trin er at konfigurere Cisco Jabber på MS SQL-forbindelsen på webstedet Veritas Merge1. Hvis du vil have mere at vide om, hvordan du konfigurerer Cisco Jabber på MS SQL-forbindelsen, skal du se Brugervejledning til [forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre forbindelsen, der er konfigureret i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Cisco Jabber på MS SQL brugere Microsoft 365 at** aktivere automatisk tilknytning af brugere. Cisco Jabber på MS SQL elementer omfatter en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Trin 4: Overvåg Cisco Jabber-forbindelsen

Når du har oprettet Cisco Jabber på MS SQL forbindelse, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser**, og vælg derefter **Cisco Jabber på MS SQL** forbindelse for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
