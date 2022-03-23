---
title: Arkivér data fra CellTrust SL2-platformen for at Microsoft 365
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en CellTrust SL2-dataforbindelse til at importere og arkivere mobilkommunikationsdata.
ms.openlocfilehash: 420da07fcb878f047d8252b713360be122c85870
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592461"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>Arkivér data fra CellTrust SL2 for at Microsoft 365

CellTrust SL2 registrerer mobilkommunikationsdata og integreres med de førende arkiveringsteknologier for at opfylde kravene til elektronisk registrering for bestemmelser som FINRA, HIPAA, FOIA og TCPA. SL2 Data Connector importerer mobile kommunikationselementer til Microsoft 365. I denne artikel beskrives processen for integrering af SL2 Microsoft 365 dataforbindelse ved hjælp af CellTrust SL2 Data Connector til arkivering. Når du gennemfører denne proces, antages det, at du abonnerer på CellTrust SL2-tjenesten og er bekendt med SL2-arkitekturen. Du kan finde oplysninger om CellTrust SL2 i <https://www.celltrust.com>.

Når data er importeret til brugerpostkasser i Microsoft 365, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, Microsoft 365 opbevaringspolitikker og overholdelse af kommunikation. Hvis du bruger CellTrust SL2 Data Connector til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>Oversigt over arkivering med CellTrust SL2 Data Connector

CellTrusts SL2-platform registrerer kommunikationsdata fra flere kilder. SL2-datakilder er enten Person-til-Person (P2P) eller Application-to-Person (A2P). Den proces, der er beskrevet i denne artikel, gælder kun for P2P-datakilder. For alle P2P-datakilder er mindst én part i samarbejdet SL2-brugeren, der abonnerer på SL2-tjenesten. Følgende oversigt beskriver processen med at bruge CellTrust SL2-dataforbindelse i Microsoft 365.

![Arkiveringsarbejdsproces for CellTrust SL2-tjenesten.](../media/CellTrustSL2ConnectorWorkflow.png)

1. SL2-brugere sender og modtager data til og fra SL2-tjenester i Microsoft Azure.

2. Din organisation har et SL2-domæne i CellTrusts SL2 Cloud Service-miljø. Dit domæne kan have en eller flere organisationsenheder (OUs). SL2-skytjenesten overfører dine data til et meget sikkert område på Microsoft Azure-platformen, så dine data aldrig forlader Microsoft Azure miljøet. Afhængigt af dit SL2-abonnement (Enterprise, SMB eller Government) er dit domæne enten hostet på Microsoft Azure Global eller Microsoft Azure Government.

3. Når du har oprettet CellTrust SL2-dataforbindelse, dit domæne og dine OUs (uanset SL2-planen), skal du begynde at sende data Microsoft 365. Datafeedet er struktureret til at understøtte rapportering baseret på datakilder, brugere eller domænet alene. Det betyder, at din organisation kun skal bruge én forbindelse for at kunne feede alle dine datakilder for Microsoft 365.

4. Forbindelsen opretter en mappe under hver tilknyttet bruger med en passende Office 365 med titlen **CellTrust SL2**. Denne tilknytning forbinder en CellTrust SL2-bruger til en Office 365 postkasse ved hjælp af en mailadresse. Hvis et bruger-id i CellTrust SL2 ikke stemmer overens Office 365, arkiveres brugerens data ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Kontrollér, at du har et domæne i cellTrust SL2-skytjenestemiljøet. For yderligere oplysninger om anskaffelse af en produktion eller prøveversion SL2 domæne, [Kontakt CellTrust](https://www.celltrust.com/contact-us/#form).

- Hent legitimationsoplysningerne for at få adgang til administratorkontoen for dit SL2-domæne.

- Den bruger, der opretter cellTrust SL2-dataforbindelse i trin 1 (og fuldfører den i trin 3), skal have tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne CellTrust-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>Trin 1: Opret en CellTrust SL2-forbindelse

Det første trin er at oprette en dataforbindelse i Microsoft 365 Overholdelsescenter.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser i venstre navigationsrude** .

2. På fanen **Oversigt** skal du klikke **på Filtrer** **og vælge Efter CelleSand** og derefter anvende filteret.

   ![Konfigurer filter for at vise CellTrust-forbindelser.](../media/DataConnectorsFilter.png)

3. Klik **på CellTrust SL2 (preview)**.

4. Klik på **Tilføj forbindelse på siden Produktbeskrivelse for CellTrust SL2 (****preview).**

5. Klik **på Acceptér på** siden **Servicebetingelser**.

6. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**. Det navn, du angiver, identificerer forbindelsen på siden **Dataforbindelser** , når du har oprettet den.

7. På siden **Log på din CellTrust-konto skal** du klikke på **Log på CellTrust**. Du bliver omdirigeret til **CellTrust-portalen for Microsoft 365** i et nyt browservindue.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>Trin 2: Vælg de domæner eller OUs, der skal arkiveres

Næste trin er at logge på en administratorkonto for dit CellTrust SL2-domæne og vælge de domæner og brugerkonti, der skal arkiveres i Microsoft 365.

1. På siden CellTrust **Microsoft 365 Connector** skal du vælge dit miljø i SL2-skytjenesten for at få vist en logonside.

   Du bør typisk se en indstilling, der repræsenterer dit miljø. Men hvis du har domæner i mere end ét miljø, får du vist indstillinger for hvert miljø. Når du har valgt en konto, bliver du omdirigeret til SL2-logonsiden.

2. Log på med legitimationsoplysningerne til dit domæne eller din OU-administratorkonto.

   Hvis du logger på som SL2-domæneadministrator, får du vist navnet på dit domæne og OUs i det pågældende domæne. Hvis du ikke har OUs, kan du kun se navnet på dit domæne. Hvis du logger på som OU-administrator, kan du kun se navnet på din OU.

3. Aktivér de forretningsenheder, du vil arkivere. Når du vælger domænet, vælges der ikke automatisk OUs. Du skal aktivere hver OU separat for at arkivere den.

   ![Aktivér OUs for at arkivere.](../media/EnableCellTrustOUs.png)

4. Når du er færdig med dine valg, skal du lukke browservinduet og vende tilbage til siden med guiden Microsoft 365 Overholdelsescenter. Efter et par sekunder går guiden automatisk videre til næste trin til tilknytning af brugere.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør konfigurationen af forbindelsen

Det sidste trin er at tilknytte brugere og fuldføre konfigurationen af forbindelsen i Microsoft 365 Overholdelsescenter.

1. På siden **Brugertilknytning** **skal du vælge** Aktivér automatisk brugertilknytning, hvis mailadressen for brugere er den samme i både SL2 og Microsoft 365. Ellers skal du manuelt bruge mailadresser ved at uploade en CSV-fil, der knytter brugernes SL2-adresse til deres Microsoft 365 adresse.

2. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

   Den nye forbindelse føjes til listen på **siden Dataforbindelser** .

## <a name="get-help-from-celltrust"></a>Få hjælp fra CellTrust

Se [siden CellTrust-kundesupport](https://www.celltrust.com/contact-us/#support) for at få mere at vide om at kontakte CellTrust for at få hjælp til konfiguration af en CellTrust SL2-dataforbindelse.

## <a name="more-information"></a>Flere oplysninger

- En domæneadministrator kan konfigurere en forbindelse for domænet eller en hvilken som helst OUs i det pågældende domæne. Hvis du bruger OU-administratorkontoen, kan du kun konfigurere en forbindelse for den pågældende OU.

- For at fuldføre trinnene ovenfor skal du være tildelt en Microsoft 365 E5-licens og have de rette Microsoft Office administratorrettigheder.

- Hvis du vil teste den nye forbindelse, skal du sende en sms ved hjælp af SL2-mobilappen eller fra SL2-portalen. Gå til din Microsoft 365 postkasse, og åbn **mappen CellTrust SL2** i din Indbakke. Det kan tage et par minutter, før sms'er vises i din postkasse.

- Mange love og bestemmelser kræver elektronisk kommunikation for at kunne bevares på en sådan måde, at den kan frembringes som beviser, når der anmodes om det. Electronic Discovery (eDiscovery) bruges til at overholde produktion af elektronisk kommunikation. Enterprise Information Archiving-løsninger (EIA) er designet til at udføre eDiscovery og giver funktioner som administration af opbevaringspolitik, dataklassificering og indholdsovervågning. Microsoft 365 en langsigtet opbevaringsløsning til overholdelse af de regler og standarder, der påvirker din organisation.

- Udtrykket *arkivering som* anvendt i dette dokument henviser til arkivering i forbindelse med brug i en løsning til arkivering af virksomhedsoplysninger (EIA). EIA-løsninger har eDiscovery-funktioner, der frembringer dokumenter til procesførelse, procesførelse, revision og undersøgelser. Arkivering i forbindelse med sikkerhedskopiering og gendannelse, der bruges til genoprettelse efter nedbrud og forretningskontinuitet, er ikke den tilsigtede brug af ordet i dette dokument.
