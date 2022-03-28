---
title: Konfigurer en forbindelse til at arkivere Twitter-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere Twitter-data fra Veritas for at Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, eDiscovery og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: c1a6839187c98ade3fc53307522420835c204b09
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596982"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Konfigurer en forbindelseskomponent til at arkivere Twitter-data (forhåndsvisning)

Brug en Veritas-forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Twitter-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas leverer en [](https://www.veritas.com/insights/merge1/twitter) Twitter-forbindelseskomponent, der er konfigureret til at hente elementer fra en datakilde fra en tredjepart og importere disse elementer til Microsoft 365. Forbindelsen konverterer indhold som tweets, retweets og kommentarer fra Twitter til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når Twitter-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Brug af en Twitter-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-twitter-data"></a>Oversigt over arkivering af Twitter-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Twitter-data Microsoft 365.

![Arkivering af arbejdsproces for Twitter-data.](../media/VeritasTwitterConnectorWorkflow.png)

1. Din organisation arbejder sammen med Twitter om at konfigurere et Twitter-websted. Din organisation arbejder også sammen med Veritas om at konfigurere et Flet1-websted.

2. Én gang hver 24 timer, kopieres Twitter-elementer til Veritas Merge1-webstedet. Forbindelsen konverterer også Twitter-elementer til et mailformat.

3. Den Twitter-forbindelse, du opretter på Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører Twitter-indholdet til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). En undermappe i mappen Indbakke med navnet **Twitter** oprettes i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle Twitter-elementer indeholder denne egenskab, som er udfyldt med mailadressen til hver deltager i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://www.veritas.com/form/requestacall/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Opret en Twitter-app på for at <https://developer.twitter.com> hente data fra din Twitter-konto. Du kan finde en trinvis vejledning til oprettelse af programmet under [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

- Den bruger, der opretter YouTube-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-twitter-connector"></a>Trin 1: Konfigurer Twitter-forbindelsen

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til Twitter-data.

1. Gå til <https://compliance.microsoft.com> , og klik **derefter på Data-forbindelser** >  **Vitter.**

2. Klik på **Tilføj** forbindelse på siden med **produktbeskrivelse på Twitter**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-twitter-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Twitter på webstedet Veritas Merge1

Det andet trin er at konfigurere Twitter-forbindelsen på webstedet Veritas Merge1. Hvis du vil have mere at vide om, hvordan du konfigurerer [Twitter-forbindelsen, skal du se Brugervejledning til forbindelser fra tredjepart Flet1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

Når du har **klikket &,** vises siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelse.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Twitter-brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. Twitter-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-twitter-connector"></a>Trin 4: Overvåg Twitter-forbindelsen

Når du har oprettet Twitter-forbindelsen, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com/> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **Twitter-forbindelsen** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
