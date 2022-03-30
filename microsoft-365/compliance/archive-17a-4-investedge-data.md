---
title: Konfigurer en forbindelse til at arkivere InvestEdge-data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 InvestEdge DataParser-forbindelse til at importere og arkivere InvestEdge-data Microsoft 365.
ms.openlocfilehash: 5ee98f1bd4800685160bf77d5bcbc13ca4fe6c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599454"
---
# <a name="set-up-a-connector-to-archive-investedge-data"></a>Konfigurer en forbindelse til at arkivere InvestEdge-data

Brug [InvestEdge DataParser](https://www.17a-4.com/investedge-dataparser/) fra 17a-4 LLC til at importere og arkivere data fra InvestEdge til brugerpostkasser i Microsoft 365 organisation. DataParser har en InvestEdge-forbindelse, der er konfigureret til at hente elementer fra en tredjeparts datakilde og importere disse elementer til Microsoft 365. InvestEdge DataParser-forbindelsen konverterer InvestEdge-data til et mailmeddelelsesformat og importerer derefter disse elementer til brugerpostkasser Microsoft 365.

Når InvestEdge-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder og kommunikation. Hvis du bruger en InvestEdge-forbindelse til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-investedge-data"></a>Oversigt over arkivering af InvestEdge-data

Følgende oversigt beskriver processen med at bruge en dataforbindelse til at arkivere InvestEdge-data Microsoft 365.

![Arkivering af arbejdsproces for InvestEdge-data fra 17a-4.](../media/InvestEdgeDataParserConnectorWorkflow.png)

1. Din organisation arbejder med 17a-4 til at konfigurere InvestEdge DataParser.

2. InvestEdge-elementer indsamles regelmæssigt af DataParser. Dataparser konverterer også indholdet af en meddelelse til et mailformat.

3. Den InvestEdge DataParser-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til DataParser og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Der oprettes en undermappe i mappen Indbakke med navnet **InvestEdge DataParser** i brugerpostkasserne, og InvestEdge-elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle InvestEdge-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Opret en DataParser-konto til Microsoft-forbindelser. For at gøre dette skal du [kontakte 17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter forbindelsen InvestEdge DataParser i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-a-investedge-dataparser-connector"></a>Trin 1: Konfigurer en InvestEdge DataParser-forbindelse

Det første trin er at få adgang til siden Dataforbindelser i Microsoft 365 Overholdelsescenter og oprette en 17a-4-forbindelse til InvestEdge-data.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på DataforbindelserInvestEdge** >  **DataParser**.

2. Klik på **Tilføj forbindelse på siden med produktbeskrivelsen for InvestEdge DataParser**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden til at oprette forbindelse til InvestEdge DataParser.

## <a name="step-2-configure-the-investedge-dataparser-connector"></a>Trin 2: Konfigurer connectoren InvestEdge DataParser

Arbejd med 17a-4-understøttelse for at konfigurere InvestEdge DataParser-forbindelsen.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

Connectoren InvestEdge DataParser vil automatisk knytte brugere til deres Microsoft 365 mailadresser, før data importeres Microsoft 365.

## <a name="step-4-monitor-the-investedge-dataparser-connector"></a>Trin 4: Overvåg InvestEdge DataParser-forbindelsen

Når du har oprettet en InvestEdge DataParser-forbindelse, kan du få vist forbindelsesstatus på Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter den InvestEdge DataParser-forbindelse, du har oprettet, for at få vist pop op-siden, som indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
