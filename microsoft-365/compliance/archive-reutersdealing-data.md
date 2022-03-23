---
title: Konfigurer en forbindelse til at arkivere Reuters Dealing-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere Reuters Dealing-data fra Veritas Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 7e978af3c0916b277fcf97d9fe58c9b7cea08d43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591730"
---
# <a name="set-up-a-connector-to-archive-reuters-dealing-data"></a>Konfigurer en forbindelse til at arkivere Reuters dealing-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra platformen reuters dealing til brugerpostkasser i Microsoft 365 organisation. Veritas giver dig en [reuters dealing-forbindelse](https://globanet.com/reuters-dealing/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og derefter importere disse elementer til Microsoft 365. Forbindelsen konverterer dealing communications from the Reuters Dealing account to an email message format and then import those items to the user's mailbox in Microsoft 365.

Når reuters dealing-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder og kommunikation. Hvis du bruger en forbindelseskomponent til Reuters-håndtering til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-reuters-dealing-data"></a>Oversigt over arkivering af reuters håndteringsdata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere reuters dealing-data Microsoft 365.

![Arkiveringsarbejdsproces for Reuters-håndteringsdata.](../media/ReuetersDealingConnectorWorkflow.png)

1. Din organisation arbejder sammen med Reuters Dealing for at konfigurere et websted til håndtering af reuters.

2. Én gang i døgnet kopieres Reuters Dealing-elementer til webstedet Veritas Merge1. Forbindelsen konverterer også elementerne til et mailformat.

3. Den forbindelseskomponent Reuters Dealing, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører indholdet til en sikker Azure Storage placering i Microsoft-skyen.

4. Forbindelsen importerer elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben Mail  for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Reuters Dealing** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle Reuters Dealing-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://globanet.com/contact-us). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter forbindelsen Reuters Dealing i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-reuters-dealing-connector"></a>Trin 1: Konfigurer forbindelsen Reuters Dealing

Det første trin er at få adgang til **siden Dataforbindelser** i Microsoft 365 og oprette en forbindelse til Reuters dealing data.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserReuters** >  **Dealing**.

2. Klik på **Tilføj forbindelse på siden Produktbeskrivelse for Reuters Dealing**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-reuters-dealing-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer forbindelsen Reuters Dealing på webstedet Veritas Merge1

Det andet trin er at konfigurere forbindelsen Reuters Dealing på Veritas webstedet Merge1. Hvis du vil have mere at vide om konfiguration af forbindelsen Reuters Dealing, skal [du se Brugervejledning til forbindelse fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Dealing%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Brugere, der håndterer Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere.

   Reuters Dealing items include a property *called Email*, which contains email addresses for users in your organization. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-reuters-dealing-connector"></a>Trin 4: Overvåg forbindelsen Reuters Dealing

Når du har oprettet forbindelsen Reuters Dealing, kan du få vist forbindelsesstatus i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter forbindelsen **Reuters Dealing** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.