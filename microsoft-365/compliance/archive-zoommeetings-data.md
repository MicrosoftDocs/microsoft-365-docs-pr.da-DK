---
title: Konfigurer en forbindelse til at arkivere zoommødedata i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere data fra Veritas Zoom-møder i Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: f776fe3d03f8674a698b5c8fe2f355aa5635577f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601548"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Konfigurere en forbindelse til at arkivere zoommødedata

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Zoom-møder til brugerpostkasser Microsoft 365 organisationen. Veritas har en [Zoom Meetings-forbindelse](https://globanet.com/zoom/), der er konfigureret til at hente elementer fra tredjepartsdatakilden (med jævne mellemrum) og importere disse elementer til Microsoft 365. Forbindelsen konverterer indholdet af møder (herunder chatsamtaler, optagede filer og metadata) fra kontoen Zoom-møder til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365.

Når zoom-mødedata er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter samt overholdelse af regler og standarder og kommunikation. Hvis du bruger en Zoom-mødeforbindelse til at importere og arkivere data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Oversigt over arkivering af zoommødedata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere zoom mødedata i Microsoft 365.

![Zoome arbejdsprocessen for arkivering af møder.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Din organisation arbejder med Zoom-møder for at konfigurere et zoommødewebsted.

2. Én gang i døgnet kopieres mødeelementer fra Zoom-møder til webstedet Veritas Merge1. Forbindelsen konverterer også indholdet af møder til et mailformat.

3. Forbindelsen Zoommøder, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til Veritas Merge1 hver dag og overfører mødemeddelelserne til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede mødeelementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail og automatisk brugertilknytning, som beskrevet i trin 3. En ny undermappe i mappen Indbakke med navnet **Zoommøder** oprettes i brugerpostkasser, og mødeelementerne importeres til den pågældende mappe. Forbindelsen gør dette ved hjælp af værdien *af egenskaben Mail* . Hvert mødeelement indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mødet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Veritas Merge1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://globanet.com/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Hent brugernavnet og adgangskoden til din organisations Zoom Business- eller Zoom Enterprise-konto. Du skal logge på denne konto i trin 2, når du konfigurerer forbindelsen Zoom møder.

- Opret følgende programmer på [Zoom Marketplace](https://marketplace.zoom.us):

  - OAuth-program

  - JWT-program

  Når du har oprettet disse programmer, genererer zoomplatformen et sæt unikke legitimationsoplysninger, der bruges til at generere tokens. Disse tokens bruges til at godkende forbindelsen, når den opretter forbindelse til din Zoom-konto, og kopierer elementer til Flet1-webstedet. Du skal bruge disse tokens, når du konfigurerer zoomforbindelse i trin 2.

  For at få en trinvis vejledning til, hvordan du opretter OAuth- og JWT-programmerne, skal du se Brugervejledning til forbindelser [fra tredjeparter](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- Den bruger, der opretter forbindelsen Zoom-møder i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataforbindelse er i offentlig prøveversion i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Trin 1: Konfigurer forbindelsen zoommøder

Det første trin er at få adgang **til dataforbindelserne i** Microsoft 365 Overholdelsescenter og oprette en Zoom-mødeforbindelse.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik derefter **på DataforbindelserZoom-møder** > .

2. Klik på **Tilføj forbindelse på** produktbeskrivelsen for **Zoommøder**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Trin 2: Konfigurer forbindelsen til Zoommøder

Det andet trin er at konfigurere forbindelsen Zoom-møder på Flet1-webstedet. Du kan finde flere oplysninger om, hvordan du konfigurerer forbindelsen [Zoom-møder](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf) på webstedet Veritas Merge1 i Brugervejledning til forbindelser fra tredjepart.

Når du har **klikket & færdig**, **vises** siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelsen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

1. På siden **Tilknyt eksterne brugere Microsoft 365 brugere** skal du aktivere automatisk tilknytning af brugere.

   Zoom-mødeelementer indeholder en egenskab *kaldet Mail* , der indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse

2. Klik **på** Næste, gennemgå dine indstillinger, og gå til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Trin 4: Hold øje med forbindelsen Zoom møder

Når du har oprettet forbindelsen Zoom-møder, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser,** og vælg derefter forbindelsen **Zoom møder for** at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om de data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.

- Hvis zoom-forbindelsen til møder skal fungere, skal du aktivere optagelser, når du konfigurerer Zoom-møder.