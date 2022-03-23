---
title: Konfigurer en forbindelse til at arkivere Slack eDiscovery-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere data fra Veritas Slack eDiscovery i Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 666834c370d0aee146c7fc0603297f4e2b7527d7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594314"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Konfigurer en forbindelse til at arkivere Slack eDiscovery-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra sociale medier, chat og samarbejdsplatforme for dokumenter til postkasser i Microsoft 365 organisation. Veritas indeholder en [Slæk-forbindelse](https://globanet.com/slack/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og derefter importere disse elementer til Microsoft 365. Slæk trækker meddelelser og filer fra Slack API'en og konverterer dem til et mailformat og importerer derefter elementet til brugerpostkasser.

Når Slack eDiscovery-data er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsmærkater samt overholdelse af regler og standarder i forbindelse med kommunikation. Brug af en Slækforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Oversigt over arkivering af Slack eDiscovery-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere slækoplysningerne Microsoft 365.

![Arbejdsproces for arkivering af slæk.](../media/SlackConnectorWorkflow.png)

1. Din organisation arbejder med Slæk for at konfigurere et Slæk-websted.

2. Én gang i døgnet kopieres chatmeddelelser fra Slack eDiscovery til webstedet Veritas Merge1. Forbindelsen konverterer også indholdet af en chatmeddelelse til et mailformat.

3. Den Slack eDiscovery-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører chatmeddelelserne til et sikkert Azure Storage placering i Microsoft-skyen.

4. Forbindelsen importerer de konverterede chatbeskedelementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail og automatisk brugertilknytning, som beskrevet i trin 3. Der oprettes en ny undermappe i mappen Indbakke med navnet **Slack eDiscovery** i brugerpostkasserne, og chatmeddelelseselementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hver chatmeddelelse indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i chatmeddelelsen.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Hent brugernavnet og adgangskoden til din organisations Slack-virksomhedskonto. Du skal logge på denne konto i trin 2, når du konfigurerer Slæk.

- Den bruger, der opretter Slack eDiscovery-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>Trin 1: Konfigurer Slack eDiscovery-forbindelsen

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til Slækdata.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserSlack** >  **eDiscovery**.

2. På siden **Slack eDiscovery-produktbeskrivelse** skal du klikke på **Tilføj forbindelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-slack-ediscovery"></a>Trin 2: Konfigurer Slack eDiscovery

Det andet trin er at konfigurere Slack eDiscovery-forbindelsen på Flet1-webstedet. Du kan finde flere oplysninger om, hvordan du konfigurerer Slack eDiscovery-forbindelsen på webstedet Veritas Merge1 i [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

1. På siden **Tilknyt eksterne brugere Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere.

   Slack eDiscovery-elementer omfatter en egenskab *kaldet Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Trin 4: Overvåg Slack eDiscovery-forbindelsen

Når du har oprettet Slack eDiscovery-forbindelsen, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **Slack eDiscovery-forbindelsen** for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om de data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.