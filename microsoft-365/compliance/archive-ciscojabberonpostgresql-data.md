---
title: Konfigurer en forbindelse til at arkivere Cisco Jabber på PostgreSQL-data Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan du konfigurerer og bruger en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Cisco Jabber på PostgreSQL Microsoft 365.
ms.openlocfilehash: 946a43155ed085575e9aef97b04f0828338963e5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606514"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>Konfigurer en forbindelse til at arkivere Cisco Jabber på PostgreSQL-data

Brug en Veritas-forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Cisco Jabber-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas leverer en [Cisco Jabber på PostgreSQL-forbindelse](https://www.veritas.com/insights/merge1/jabber), der er konfigureret til at registrere elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Forbindelsen konverterer indholdet som f.eks. meddelelser, chatsamtaler og delt indhold fra Cisco Jabber på PostgreSQL til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Cisco Jabber på PostgreSQL-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Brug af en Cisco Jabber på PostgreSQL-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>Oversigt over arkivering af Cisco Jabber på PostgreSQL-data

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Cisco Jabber på PostgreSQL-data Microsoft 365.

![Arkiveringsarbejdsproces for Cisco Jabber på PostgreSQL-data.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Din organisation samarbejder med Cisco Jabber på PostgreSQL om at konfigurere en Cisco Jabber på PostgreSQL-webstedet.

2. Hver 24. time kopieres Cisco Jabber på PostgreSQL-elementer til webstedet Veritas Merge1. Forbindelsen konverterer også Cisco Jabber på PostgreSQL-elementer til et mailformat.

3. Den Cisco Jabber på PostgreSQL-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører Jabber-indholdet til et sikkert Azure Storage sted i Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber på PostgreSQL** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen gør dette ved hjælp af værdien *af egenskaben Mail* . Alle Jabber-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at gøre dette](https://www.veritas.com/content/support/en_US). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter Cisco Jabber på PostgreSQL-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>Trin 1: Konfigurer Cisco Jabber på PostgreSQL-forbindelsen

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til Jabber-data.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på Dataforbindelser** &gt; **Cisco Jabber på PostgreSQL**.

2. På siden **Cisco Jabber på siden med produktbeskrivelsen af PostgreSQL** skal du klikke **på Tilføj forbindelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Cisco Jabber på PostgreSQL på webstedet Veritas Merge1

Det andet trin er at konfigurere Cisco Jabber på PostgreSQL-forbindelsen på webstedet Veritas Merge1. Du kan finde oplysninger om, hvordan du konfigurerer Cisco Jabber på PostgreSQL-forbindelsen i [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Cisco Jabber på PostgreSQL-brugere Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere. Cisco Jabber på PostgreSQL-elementer indeholder en egenskab kaldet *Mail*, der indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>Trin 4: Overvåg Cisco Jabber på PostgreSQL-forbindelsen

Når du har oprettet Cisco Jabber på PostgreSQL-forbindelsen, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com/> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **Cisco Jabber på PostgreSQL-forbindelsen** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
