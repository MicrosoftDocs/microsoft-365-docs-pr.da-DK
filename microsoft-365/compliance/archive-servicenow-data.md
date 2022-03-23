---
title: Konfigurer en forbindelse til at arkivere ServiceNow data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere ServiceNow-data fra Veritas til Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks. retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 985fbdd173be020a00353452d4289fe214351976
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591523"
---
# <a name="set-up-a-connector-to-archive-servicenow-data"></a>Konfigurer en forbindelse til at arkivere ServiceNow-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra ServiceNow-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas leverer en [ServiceNow-forbindelse](https://globanet.com/servicenow/), der registrerer elementer fra tredjepartsdatakilden og importerer disse elementer til Microsoft 365. Forbindelsen konverterer indholdet som f.eks. livemeddelelser, vedhæftede filer og indlæg fra ServiceNow til et mailmeddelelsesformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når ServiceNow data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Brug af en ServiceNow-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-servicenow-data"></a>Oversigt over arkivering af ServiceNow-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere ServiceNow-dataene Microsoft 365.

![Arkiveringsarbejdsproces for ServiceNow-data.](../media/ServiceNowConnectorWorkflow.png)

1. Din organisation arbejder sammen med ServiceNow at konfigurere et ServiceNow-websted.

2. Én gang i døgnet kopieres ServiceNow-elementer til webstedet Veritas Merge1. Forbindelsen konverterer også ServiceNow-elementer til et mailmeddelelsesformat.

3. Den ServiceNow-forbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører ServiceNow-indholdet til en sikker Azure Storage placering i Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). En undermappe i mappen Indbakke med navnet **ServiceNow** oprettes i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Hvert ServiceNow-element indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette en konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Opret et ServiceNow-program til at hente data fra din ServiceNow-konto. Du kan finde en trinvis vejledning til oprettelse af programmet under [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

- Den bruger, der opretter ServiceNow-forbindelsen i trin 1 (og fuldfører den i trin 3), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-servicenow-connector"></a>Trin 1: Konfigurer forbindelsen ServiceNow

Det første trin er at få adgang til **siden Dataforbindelser** i Microsoft 365 Overholdelsescenter og oprette en forbindelse til ServiceNow-data.

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter **på DataforbindelserServiceNow** > .

2. På siden **TjenesteNow produktbeskrivelse** skal du klikke **på Tilføj forbindelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-servicenow-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer ServiceNow på webstedet Veritas Merge1

Det andet trin er at konfigurere ServiceNow-forbindelsen på webstedet Veritas Merge1. Du kan finde oplysninger om, hvordan du konfigurerer ServiceNow-forbindelsen, under [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

Når du har **klikket &,** vises siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelse.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt tjenesteTilknyt brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. ServiceNow-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-servicenow-connector"></a>Trin 4: Overvåg serviceNow-forbindelsen

Når du har oprettet forbindelsen ServiceNow, kan du få vist forbindelsesstatus i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **ServiceNow-forbindelsen** for at få vist pop op-siden, som indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.