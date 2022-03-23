---
title: Konfigurer en forbindelse til at arkivere EML-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere EML-data fra Veritas i Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: aafa253cc4a507946acd56cfbd52af79d8250ee6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591645"
---
# <a name="set-up-a-connector-to-archive-eml-data"></a>Konfigurer en forbindelse til at arkivere EML-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere EML-data til brugerpostkasser i Microsoft 365 organisation. EML er filtypenavnet for en mail, der er gemt i en fil. Forbindelsen konverterer indholdet af et element fra kildeformatet til et mailformat og importerer derefter elementet til en brugerpostkasse.

Når EML-meddelelser er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery og opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger en EML-forbindelse til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-eml-data"></a>Oversigt over arkivering af EML-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere EML-data Microsoft 365.

![Arkivering af arbejdsproces for EML-data.](../media/EMLConnectorWorkflow.png)

1. Din organisation arbejder sammen med EML-kilden for at konfigurere et EML-websted.

2. Én gang i døgnet kopieres indholdselementer fra EML-kilden til webstedet Veritas Merge1. Under denne proces konverteres indholdet af en EML-fil til et mailformat.

3. EML-forbindelsen, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede meddelelseselementer til postkasser for bestemte brugere ved hjælp af værdien af  egenskaben Mail for den automatiske brugertilknytningsproces, der er beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Under denne proces oprettes en undermappe i mappen Indbakke med navnet **EML'er** i brugerpostkasserne, og EML-elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hver meddelelse indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i indholdselementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter EML-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-an-eml-connector"></a>Trin 1: Konfigurer en EML-forbindelse

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til EML-data.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserEML** > .

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse **for EML**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-eml-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer EML-forbindelsen på webstedet Veritas Merge1

Det andet trin er at konfigurere EML-forbindelsen på veritas Merge1-webstedet. Du kan finde oplysninger om konfiguration af [EML-forbindelsen i Brugervejledning til forbindelser fra tredjeparter](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20EML%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt eksterne brugere Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere. EML-kildeelementerne indeholder en egenskab *kaldet Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til en Microsoft 365 bruger, importeres EML-elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-eml-connector"></a>Trin 4: Overvåg EML-forbindelsen

Når du har oprettet EML-forbindelsen, kan du få vist forbindelsens status Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser,** og vælg derefter **EML-forbindelsen** for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om de data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.