---
title: Konfigurer en forbindelse til at arkivere Skype for Business data i Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Skype for Business til Microsoft 365.
ms.openlocfilehash: a783ad4bea9b06fcef3f7da4f67a98c17310a38e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597977"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Konfigurer en forbindelse til at arkivere Skype for Business data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Skype for Business-platformen til brugerpostkasser i Microsoft 365 organisation. Veritas indeholder [en Skype for Business-forbindelse](https://www.veritas.com/en/au/insights/merge1/skype-for-business), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Forbindelsen konverterer indholdet som f.eks. meddelelser mellem brugere, faste chatsamtaler og mødemeddelelser fra Skype for Business til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Skype for Business data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Hvis du bruger Skype for Business forbindelseskomponent til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-skype-for-business-data"></a>Oversigt over arkivering Skype for Business data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere Skype for Business data Microsoft 365.

![Arkivering af arbejdsproces for Skype for Business data.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Din organisation arbejder sammen Skype for Business at konfigurere og konfigurere et Skype for Business websted.

2. Én gang i døgnet kopieres Skype for Business elementer til webstedet Veritas Merge1. Forbindelsen konverterer også Skype for Business til et mailformat.

3. Den Skype for Business forbindelse, du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører Skype for Business-indholdet til en sikker Azure Storage placering i Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen **Indbakke med Skype for Business** navn i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen gør dette ved hjælp af værdien *af egenskaben Mail* . Hver Skype for Business element indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at gøre dette](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Den bruger, der opretter Skype for Business forbindelse i trin 1 (og fuldfører den i trin 3), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>Trin 1: Konfigurer Skype for Business forbindelse

Det første trin er at få adgang til **siden Dataforbindelser** i Microsoft 365 Overholdelsescenter og oprette en forbindelse til Skype for Business data.

1. Gå til <https://compliance.microsoft.com> og klik **på Dataforbindelser Skype for Business** > .

2. På siden **Skype for Business** produktbeskrivelse skal du klikke på **Tilføj forbindelse**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Skype for Business webstedet Veritas Merge1

Det andet trin er at konfigurere Skype for Business på Veritas Merge1-webstedet. Du kan finde oplysninger om, hvordan du konfigurerer Skype for Business forbindelse, i [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt Skype for Business brugere Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere. Posterne Skype for Business en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>Trin 4: Overvåg Skype for Business forbindelse

Når du har oprettet Skype for Business forbindelseskomponent, kan du få vist forbindelsesstatus i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com/> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser**, og vælg derefter **Skype for Business** forbindelse for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
