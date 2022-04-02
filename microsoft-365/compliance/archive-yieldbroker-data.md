---
title: Konfigurer en forbindelse til at arkivere Yieldbroker-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere Yieldbroker-data fra Veritas til Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 4a3c56659b4229774af6804d1dc3a6f30aa85039
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63602964"
---
# <a name="set-up-a-connector-to-archive-yieldbroker-data"></a>Konfigurer en forbindelse til at arkivere Yieldbroker-data

Brug en Veritas-forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Yieldbroker til brugerpostkasser i Microsoft 365 organisation. Veritas giver dig en [Yieldbroker-forbindelse](https://globanet.com/yieldbroker/), der er konfigureret til at hente elementer fra datakilden fra tredjeparten og importere disse elementer til Microsoft 365. Forbindelsen konverterer indholdet fra Yieldbroker til et mailformat og importerer derefter disse elementer til brugerens postkasse Microsoft 365.

Når Yieldbroker er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger en Yieldbroker-forbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-yieldbroker-data"></a>Oversigt over arkivering af Yieldbroker-data

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Yieldbroker-dataene Microsoft 365.

![Arkivering af arbejdsproces for Afkastbroker-data.](../media/YieldbrokerConnectorWorkflow.png)

1. Din organisation arbejder sammen med Yieldbroker om at konfigurere et websted med afkastbroker.

2. Én gang hver 24 timer kopieres Yieldbroker-elementer til webstedet Veritas Merge1. Forbindelsen konverterer også indholdet til et mailformat.

3. Den Yieldbroker-forbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede Yieldbroker-elementer til postkasser for bestemte brugere ved hjælp af værdien af  egenskaben Mail for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Afkastbruder** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hvert Afkastbroker indeholder denne egenskab, som er udfyldt med mailadressen på hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter forbindelsen Afkastbroker i trin 1 (og fuldfører den i trin 3), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-yieldbroker-connector"></a>Trin 1: Konfigurer forbindelsen Afkastbroker

Det første trin er at få adgang til **siden Dataforbindelser** i Microsoft 365 Overholdelsescenter og oprette en forbindelse til Yieldbroker.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på Dataforbindelser** &gt; **Yieldbroker**.

2. Klik på **Tilføj ny forbindelse** på siden produktbeskrivelse **for Afkastbruder**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-yieldbroker-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer forbindelsen Yieldbroker på webstedet Veritas Merge1

Det andet trin er at konfigurere forbindelsen Afkastbroker på webstedet Merge1. Du kan finde oplysninger om, hvordan du konfigurerer Afkastbroker, under [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Yieldbroker%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Følg disse trin for at tilknytte brugere og fuldføre konfigurationen af forbindelsen:

1. På siden **Map Yieldbroker users to Microsoft 365 users** skal du aktivere automatisk brugertilknytning. Yieldbroker-elementer indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-yieldbroker-connector"></a>Trin 4: Overvåg forbindelsen Afkastbroker

Når du har oprettet forbindelsen Afkastbroker, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **forbindelsen Yieldbroker** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.