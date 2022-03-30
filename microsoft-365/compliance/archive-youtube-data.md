---
title: Konfigurer en forbindelse til at arkivere YouTube-data i Microsoft 365
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere YouTube-data fra Veritas til Microsoft 365. Med denne forbindelse kan du arkivere data fra tredjeparts datakilder i Microsoft 365. Når du har arkiveret disse data, kan du bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, eDiscovery og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 0441299c7c0d58855685393526504e2e355343ad
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598486"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>Konfigurer en forbindelse til at arkivere YouTube-data

Brug en Veritas-forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra YouTube til brugerpostkasser i Microsoft 365 organisation. Veritas indeholder en forbindelse, der er konfigureret til at hente elementer fra en datakilde fra en tredjepart og importere disse elementer til Microsoft 365. Forbindelsen konverterer indhold som chatsamtaler, vedhæftede filer, opgaver, noter og indlæg fra YouTube til et mailmeddelelsesformat og importerer derefter disse elementer til brugernes postkasser i Microsoft 365.

Når YouTube-data er gemt i brugerpostkasser, kan du anvende Microsoft 365 overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, opbevaringspolitikker og opbevaringsetiketter. Brug af en YouTube-forbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-youtube-data"></a>Oversigt over arkivering af YouTube-data

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere YouTube-data Microsoft 365.

![Arkivering af arbejdsproces for YouTube-data.](../media/YouTubeConnectorWorkflow.png)

1. Din organisation arbejder sammen med YouTube om at konfigurere et YouTube-websted.

2. Én gang i døgnet kopieres YouTube-elementer til Veritas Merge1-webstedet. Forbindelsen konverterer også YouTube-elementer til et mailformat.

3. Den YouTube-forbindelse, du opretter på Microsoft 365 Overholdelsescenter, opretter forbindelse til webstedet Veritas Merge1 hver dag og overfører YouTube-indholdet til en sikker placering Azure Storage Microsoft-skyen.

4. Forbindelsen importerer de konverterede elementer til postkasser for bestemte brugere ved hjælp af værdien af egenskaben  Mail for den automatiske brugertilknytning som beskrevet [i trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **YouTube** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Forbindelsen bestemmer, hvilken postkasse der skal importeres elementer til, ud fra værdien *af egenskaben Mail* . Alle YouTube-elementer indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i elementet.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Opret en Flet1-konto til Microsoft-forbindelser. Kontakt [Veritas kundesupport for at oprette denne konto](https://www.veritas.com/form/requestacall/ms-connectors-contact). Du skal logge på denne konto, når du opretter forbindelsen i trin 1.

- Opret et YouTube-program for at hente data fra din YouTube-konto. Du kan finde en trinvis vejledning til oprettelse af programmet under [Brugervejledning til forbindelser fra tredjepart](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

- Den bruger, der opretter YouTube-forbindelsen i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>Trin 1: Konfigurer YouTube-forbindelsen

Det første trin er at få adgang til **siden Dataforbindelser i** Microsoft 365 Overholdelsescenter og oprette en forbindelse til YouTube-data.

1. Gå til og <https://compliance.microsoft.com> klik derefter **på DataforbindelserYouTube** > .

2. Klik på **Tilføj forbindelse på** siden produktbeskrivelse **på YouTube**.

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**.

5. Log på din Flet1-konto for at konfigurere forbindelsen.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer YouTube på webstedet Veritas Merge1

Det andet trin er at konfigurere YouTube-forbindelsen på webstedet Veritas Merge1. Du kan finde oplysninger om, hvordan du konfigurerer [YouTube-forbindelsen, under Brugervejledning til forbindelser fra tredjepart Flet1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

Når du har **klikket &,** vises siden Brugertilknytning i Microsoft 365 Overholdelsescenter forbindelse.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Hvis du vil tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter, skal du følge disse trin:

1. På siden **Tilknyt YouTube-brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning. YouTube-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser for brugere i organisationen. Hvis forbindelsen kan knytte denne adresse til Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. Klik **på** Næste, gennemgå dine indstillinger, og gå derefter til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse.

## <a name="step-4-monitor-the-youtube-connector"></a>Trin 4: Overvåg YouTube-forbindelsen

Når du har oprettet YouTube-forbindelsen, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com/> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **YouTube-forbindelsen** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
