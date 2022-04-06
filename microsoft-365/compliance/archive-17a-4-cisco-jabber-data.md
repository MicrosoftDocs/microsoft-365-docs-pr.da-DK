---
title: Konfigurer en forbindelse til at arkivere Cisco Jabber-data Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en 17a-4 Cisco Jabber DataParser-forbindelse til at importere og arkivere Cisco Jabber-data Microsoft 365.
ms.openlocfilehash: 4236b64c805a2524eac080663cdf4fe1e77a595a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606600"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>Konfigurer en forbindelse til at arkivere Cisco Jabber-data

Brug [Cisco Jabber DataParser](https://www.17a-4.com/jabber-dataparser/) fra 17a-4 LLC til at importere og arkivere data fra Cisco Jabber til brugerpostkasser i Microsoft 365 organisation. DataParser indeholder en Cisco Jabber-forbindelse, der er konfigureret til at hente elementer fra en tredjeparts datakilde og importere disse elementer til Microsoft 365. Cisco Jabber DataParser-forbindelsen konverterer Cisco Jabber-data til et mailmeddelelsesformat og importerer derefter disse elementer til brugerpostkasser Microsoft 365.

Når Cisco Jabber-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder og kommunikation. Brug af en Cisco Jabber-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Oversigt over arkivering af Cisco Jabber-data

Følgende oversigt beskriver processen med at bruge en dataforbindelse til at arkivere Cisco Jabber-data Microsoft 365.

![Arkiveringsarbejdsproces for Cisco Jabber-data fra 17a-4.](../media/CiscoJabberDataParserConnectorWorkflow.png)

1. Din organisation arbejder sammen med 17a-4 om at konfigurere Cisco Jabber DataParser.

2. Cisco Jabber-elementer indsamles regelmæssigt af DataParser. Dataparser konverterer også indholdet af en meddelelse til et mailformat.

3. Den Cisco Jabber DataParser-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til DataParser og overfører meddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Der oprettes en undermappe i mappen Indbakke med navnet **Cisco Jabber DataParser** i brugerpostkasserne, og Cisco Jabber-elementerne importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle Cisco Jabber-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Opret en DataParser-konto til Microsoft-forbindelser. For at gøre dette skal du [kontakte 17a-4 LLC](https://www.17a-4.com/contact/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter forbindelsen Cisco Jabber DataParser i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne 17a-4-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-a-cisco-jabber-dataparser-connector"></a>Trin 1: Konfigurer en Cisco Jabber DataParser-forbindelse

Det første trin er at få adgang til siden Dataforbindelser i Microsoft 365 Overholdelsescenter og oprette en 17a-4-forbindelse til Cisco Jabber-data.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på DataforbindelserCisco** >  **Jabber DataParser**.

2. Klik på **Tilføj forbindelse på siden produktbeskrivelse for Cisco Jabber DataParser**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din 17a-4-konto, og fuldfør trinnene i guiden til Cisco Jabber DataParser-forbindelse.

## <a name="step-2-configure-the-cisco-jabber-dataparser-connector"></a>Trin 2: Konfigurer forbindelsen Cisco Jabber DataParser

Arbejd med understøttelse af 17a-4 for at konfigurere Cisco Jabber DataParser-forbindelsen.

## <a name="step-3-map-users"></a>Trin 3: Tilknyt brugere

Cisco Jabber DataParser-forbindelsen vil automatisk knytte brugere til deres Microsoft 365 mailadresser, før der importeres data Microsoft 365.

## <a name="step-4-monitor-the-cisco-jabber-dataparser-connector"></a>Trin 4: Overvåg Cisco Jabber DataParser-forbindelsen

Når du har oprettet en Cisco Jabber DataParser-forbindelse, kan du få vist forbindelsens status Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter den Cisco Jabber DataParser-forbindelse, du har oprettet, for at få vist pop op-siden, som indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
