---
title: Konfigurer en forbindelse til at arkivere data fra Rød side tal i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere rød side, Læs data op fra Veritas for at Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 8c0e3c444bf285f951911a9de6e5ef3480eb6468
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594381"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Konfigurer en forbindelse til at arkivere Redtail Speak-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Redtail Speak til brugerpostkasser i Microsoft 365 organisation. Veritas giver dig en [Redtail Speak-forbindelse](https://globanet.com/redtail/) , der er konfigureret til at hente elementer fra din organisations SFTP-server, hvor elementerne er modtaget fra Redtail. Forbindelsen konverterer indholdet fra Redtail Speak til et mailmeddelelsesformat og importerer derefter disse elementer til brugerens postkasse Microsoft 365.

Når Redtail Speak-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger forbindelseskomponent Redtail Speak til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Oversigt over arkivering af Redtail Speak-data

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Redtail-dataene i Microsoft 365.

![Arkiveringsarbejdsproces for Redtail Læs data op.](../media/RedtailSpeakConnectorWorkflow.png)

1. Din organisation arbejder sammen med Redtail Speak for at konfigurere en SMTP-gateway, hvor meddelelser videresendes fra Redtail Speak til din organisations SFTP-server dagligt.

2. Én gang i døgnet kopieres elementerne Redtail Speak til webstedet Veritas Merge1. Forbindelsen konverterer også elementer i Redtail Speak til et mailformat.

3. Forbindelsen Redtail Speak, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede Redtail Speak-elementer til postkasser for bestemte brugere med værdien af egenskaben Mail  for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Redtail Speak** i brugerpostkasserne, og elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hver Redtail Speak-element indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- I trin 2 skal du angive din organisations SFTP-server. Dette trin er nødvendigt, så Veritas Merge1 kan kontakte den for at indsamle Redtail Speak-data via SFTP.

- Den bruger, der opretter forbindelsen Redtail Speak Importer i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>Trin 1: Konfigurer forbindelsen Redtail Speak

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til Redtail Speak-dataene.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og vælg **Dataforbindelser** &gt; **Redtail Speak**.

2. På siden **Redtail Speak** product description skal du vælge **Add new connector**.

3. På siden **Servicebetingelser skal** du vælge **Acceptér**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og vælg derefter **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer forbindelsen Redtail Speak på webstedet Veritas Merge1

Det andet trin er at konfigurere forbindelsen Redtail Speak på webstedet Flet1. Hvis du vil have mere at vide om, hvordan du konfigurerer forbindelsen Redtail Speak, skal du [se Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

Når du har **valgt &,** vises siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsesguiden.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Følg disse trin for at tilknytte brugere og fuldføre konfigurationen af forbindelsen:

1. På siden **Map Redtail Læs brugere op Microsoft 365 brugere skal** du aktivere automatisk tilknytning af brugere. Elementerne Redtail Speak indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Vælg **Næste**, gennemse dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>Trin 4: Overvåg forbindelsen Redtail Speak

Når du har oprettet forbindelsen Redtail Speak, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og vælg **Dataforbindelser i** venstre navigationslinje.

2. Vælg fanen **Forbindelser,** og vælg derefter forbindelsen **Redtail Speak** for at få vist pop op-siden. Denne side viser egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du vælge **linket Download log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.