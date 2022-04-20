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
description: Få mere at vide om, hvordan du konfigurerer og bruger en CellTrust SL2-dataconnector til at importere og arkivere mobilkommunikationsdata.
ms.openlocfilehash: 286546950c29732e1d33738ffbe7a74f2f6dcca2
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940681"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>Arkivér data fra CellTrust SL2 til Microsoft 365

CellTrust SL2 henter mobilkommunikationsdata og integreres med de førende arkiveringsteknologier for at opfylde kravene til elektronisk registrering i forbindelse med regler som FINRA, HIPAA, FOIA og TCPA. SL2 Data Connector importerer elementer til mobilkommunikation for at Microsoft 365. I denne artikel beskrives processen til integration af SL2 med Microsoft 365 ved hjælp af CellTrust SL2 Data Connector til arkivering. Fuldførelse af denne proces forudsætter, at du abonnerer på CellTrust SL2-tjenesten og har kendskab til SL2-arkitekturen. Du kan få oplysninger om CellTrust SL2 under <https://www.celltrust.com>.

Når data er importeret til brugerpostkasser i Microsoft 365, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, Microsoft 365 opbevaringspolitikker og kommunikation med overholdelse af angivne standarder. Brug af CellTrust SL2 Data Connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>Oversigt over arkivering med CellTrust SL2 Data Connector

CellTrusts SL2-platform henter kommunikationsdata fra flere kilder. SL2-datakilder er enten Person-til-person (P2P) eller Application-to-Person (A2P). Den proces, der er beskrevet i denne artikel, vedrører kun P2P-datakilder. For alle P2P-datakilder er mindst én part i samarbejdet en SL2-bruger, der abonnerer på SL2-tjenesten. I følgende oversigt forklares processen med at bruge CellTrust SL2 Data Connector i Microsoft 365.

![Arkivering af arbejdsproces for CellTrust SL2-tjenesten.](../media/CellTrustSL2ConnectorWorkflow.png)

1. SL2-brugere sender og modtager data til og fra SL2-tjenester i Microsoft Azure.

2. Din organisation har et SL2-domæne i CellTrust's SL2 Cloud Service-miljø. Dit domæne kan have en eller flere organisationsenheder . SL2 Cloud Service overfører dine data til et meget sikkert område på den Microsoft Azure platform, så dine data aldrig forlader Microsoft Azure miljø. Afhængigt af din SL2-plan (Enterprise, SMB eller Government) hostes dit domæne enten på Microsoft Azure Global eller Microsoft Azure Government.

3. Når du har oprettet CellTrust SL2-dataconnectoren, begynder dit domæne og dine eksterne enheder (uanset din SL2-plan) at sende data til Microsoft 365. Datafeedet er struktureret til at understøtte rapportering baseret på datakilder, AFHÆNGIGE'er eller domænet i sig selv. Derfor har din organisation kun brug for én connector til at sende alle dine datakilder til Microsoft 365.

4. Connectoren opretter en mappe under hver tilknyttet bruger med en passende Office 365 licens med titlen **CellTrust SL2**. Denne tilknytning forbinder en CellTrust SL2-bruger med en Office 365 postkasse ved hjælp af en mailadresse. Hvis et bruger-id i CellTrust SL2 ikke stemmer overens i Office 365, arkiveres brugerens data ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Kontrollér, at du har et domæne i cloudtjenestemiljøet CellTrust SL2. [Kontakt CellTrust](https://www.celltrust.com/contact-us/#form) for at få flere oplysninger om, hvordan du henter et SL2-produktions- eller prøvedomæne.

- Hent legitimationsoplysningerne for at få adgang til administratorkontoen for dit SL2-domæne.

- Den bruger, der opretter CellTrust SL2-dataconnectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors** på Microsoft Purview-overholdelsesportalen. Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne CellTrust-dataconnector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>Trin 1: Opret en CellTrust SL2-connector

Det første trin er at oprette en dataconnector på overholdelsesportalen.

1. Gå til <https://compliance.microsoft.com> , og klik på **Dataconnectors** i venstre navigationsrude.

2. På fanen **Oversigt** skal du klikke på **Filtrer** og vælge **Efter CelleTiltro** og derefter anvende filteret.

   ![Konfigurer filter til at vise CellTrust-connectors.](../media/DataConnectorsFilter.png)

3. Klik på **CellTrust SL2 (eksempelvisning)**.

4. Klik på **Tilføj connector** på siden **CellTrust SL2 (prøveversion)** af produktbeskrivelsen.

5. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

6. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**. Det navn, du angiver, identificerer connectoren på siden **Dataconnectors,** når du har oprettet den.

7. Klik på **Log på CellTrust** på siden **Log på din CellTrust-konto**. Du bliver omdirigeret til **CellTrust-portalen for Microsoft 365** i et nyt browservindue.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>Trin 2: Vælg de domæner eller GV'er, der skal arkiveres

Det næste trin er at logge på en administratorkonto for dit CellTrust SL2-domæne og vælge de domæner og OU'er, der skal arkiveres i Microsoft 365.

1. På siden CellTrust **Microsoft 365 Connector** skal du vælge dit miljø i SL2-cloudtjenesten for at få vist en logonside.

   Du får typisk vist én indstilling, der repræsenterer dit miljø. Men hvis du har domæner i mere end ét miljø, får du vist indstillinger for hvert miljø. Når du har foretaget et valg, omdirigeres du til SL2-logonsiden.

2. Log på med legitimationsoplysningerne for din domæne- eller organisationsadministratorkonto.

   Hvis du logger på som SL2-domæneadministrator, får du vist navnet på dit domæne og DE'er i det pågældende domæne. Hvis du ikke har GV'er, kan du kun se navnet på dit domæne. Hvis du logger på som OU-administrator, kan du kun se navnet på din organisationsenhed.

3. Aktivér de afdelinger, du vil arkivere. Hvis du vælger domænet, vælges de ikke automatisk. Du skal aktivere hver OU separat for at arkivere den.

   ![Aktivér OUs for at arkivere.](../media/EnableCellTrustOUs.png)

4. Når du er færdig med dine valg, skal du lukke browservinduet og vende tilbage til guidesiden i overholdelsesportalen. Efter et par sekunder går guiden automatisk videre til næste trin i tilknytningen af brugere.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Det sidste trin er at tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen.

1. På siden **Brugertilknytning** skal du vælge **Aktivér automatisk brugertilknytning**, hvis mailadressen for brugerne er den samme i både SL2 og Microsoft 365. Ellers skal du manuelt bruge mailadresser ved at uploade en CSV-fil, der knytter brugernes SL2-adresse til deres Microsoft 365 adresse.

2. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

   Den nye connector føjes til listen på siden **Dataconnectors** .

## <a name="get-help-from-celltrust"></a>Få hjælp fra CellTrust

Se [siden CellTrust Kundesupport](https://www.celltrust.com/contact-us/#support) for at få oplysninger om at kontakte CellTrust for at få hjælp til at konfigurere en CellTrust SL2-dataconnector.

## <a name="more-information"></a>Flere oplysninger

- En domæneadministrator kan konfigurere en connector for domænet eller en hvilken som helst anden domænecontroller i det pågældende domæne. Hvis du bruger OU-administratorkontoen, kan du kun konfigurere en connector for den pågældende OU.

- Hvis du vil fuldføre ovenstående trin, skal du have tildelt en Microsoft 365 E5-licens og have de korrekte Microsoft Office administratorrettigheder.

- Hvis du vil teste den nye connector, skal du sende en sms ved hjælp af sl2-mobilappen eller fra SL2-portalen. Gå til din Microsoft 365 postkasse, og åbn mappen **CellTrust SL2** i indbakken. Det kan tage et par minutter, før tekstmeddelelserne vises i din postkasse.

- Mange love og bestemmelser kræver, at elektronisk kommunikation bevares på en sådan måde, at den kan fremstilles som bevis, når der anmodes om det. EDiscovery (Electronic Discovery) bruges til at overholde produktionen af elektronisk kommunikation. EIA-løsninger (Enterprise Information Archiving) er udviklet til at udføre eDiscovery og indeholder funktioner som administration af opbevaringspolitik, dataklassificering og indholdsovervågning. Microsoft 365 tilbyder en langsigtet opbevaringsløsning til overholdelse af de regler og standarder, der påvirker din organisation.

- Udtrykket *arkivering* , som bruges i dette dokument, henviser til arkivering i forbindelse med brug i en EIA-løsning (Enterprise Information Archiving). EIA-løsninger har eDiscovery-funktioner, der opretter dokumenter til retssager, procesførelser, revisioner og undersøgelser. Arkivering i forbindelse med sikkerhedskopiering og gendannelse, der bruges til it-katastrofeberedskab og forretningskontinuitet, er ikke den tilsigtede brug af udtrykket i dette dokument.
