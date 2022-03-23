---
title: Konfigurer en forbindelse til at arkivere websidedata i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere websidehentningsdata fra Veritas i Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 27e4491325a712e679cfe47e0ce7b1c8706119a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591088"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Konfigurere en forbindelse til at arkivere websidedata

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra websider til brugerpostkasser i Microsoft 365 organisation. Veritas indeholder en [websideregistreringsforbindelse](https://globanet.com/webpage-capture) , der registrerer bestemte websider (og eventuelle links på disse sider) på et bestemt websted eller et helt domæne. Forbindelsen konverterer websideindholdet til et PDF-, PNG- eller brugerdefineret filformat og vedhæfter derefter de konverterede filer til en mail og importerer derefter disse mailelementer til brugerpostkasser i Microsoft 365.

Når websideindhold er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery og opbevaringspolitikker og opbevaringsetiketter. Brug af en forbindelse til hentning af websider til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-webpage-data"></a>Oversigt over arkivering af websidedata

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere websideindhold Microsoft 365.

![Arkivering af arbejdsproces for websidedata.](../media/WebPageCaptureConnectorWorkflow.png)

1. Din organisation arbejder sammen med websidekilden for at konfigurere et websted til hentning af websider.

2. Én gang i døgnet kopieres websidekildeelementerne til Veritas Merge1-webstedet. Forbindelsen konverterer og vedhæfter også indholdet af en webside i en mail.

3. Forbindelsen Til hentning af websider, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører websideelementerne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede websideelementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben Mail  for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Websideregistrering** i brugerpostkasserne, og websideelementerne importeres til den pågældende mappe. Forbindelsen gør dette ved hjælp af værdien *af egenskaben Mail* . Hvert websideelement indeholder denne egenskab, som er udfyldt med de mailadresser, du har angivet, når du konfigurerer forbindelsen Til websideregistrering [i trin 2](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Du skal arbejde med Veritas-understøttelse for at konfigurere et brugerdefineret filformat til at konvertere websideelementerne til. Du kan få mere at vide [i Brugervejledning til forbindelser fra tredjepart flet1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- Den bruger, der opretter forbindelsen Til hentning af webside i trin 1 (og fuldfører den i trin 3), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Trin 1: Konfigurer forbindelsen Til hentning af websider

Det første trin er at få adgang til **dataforbindelserne** og oprette en forbindelse til websidekildedataene.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik derefter **på DataforbindelserWebsideregistrering** > .

2. Klik på **Tilføj forbindelse på** siden Produktbeskrivelse **for websideregistrering**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer forbindelsen Til fletning af webside på webstedet Veritas Merge1

Det andet trin er at konfigurere forbindelsen Til fletning af websider på webstedet Veritas Merge1. Hvis du vil have mere at vide om, hvordan du konfigurerer forbindelsen Til hentning af websider, skal du [se Brugervejledning til fletning af tredjepartsforbindelser](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge nedenstående trin:

1. På siden **Tilknyt websideopfang brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. The Webpage Capture items include a property called *Email*, which contains email addresses for users in your organization. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Trin 4: Overvåg forbindelsen Til hentning af webside

Når du har oprettet forbindelsen Til hentning af webside, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser,** og vælg derefter forbindelsen **Til hentning** af webside for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.