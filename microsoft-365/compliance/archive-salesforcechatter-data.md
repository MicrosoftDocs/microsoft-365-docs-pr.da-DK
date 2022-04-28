---
title: Konfigurer en connector til arkivering af Salesforce Chatter-data i Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en connector til at importere og arkivere Salesforce Chatter-data fra Veritas til Microsoft 365. Med denne connector kan du arkivere data fra datakilder fra tredjepart i Microsoft 365. Når du har arkiveret disse data, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere tredjepartsdata.
ms.openlocfilehash: 3bb1ebc10594e0b1f5cff603cdf893a010557343
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098642"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>Konfigurer en connector til arkivering af Salesforce Chatter-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en Veritas-connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Salesforce Chatter-platformen til brugerpostkasser i din Microsoft 365 organisation. Veritas leverer en [Salesforce Chatter-connector](http://globanet.com/chatter/), der henter elementer fra tredjepartsdatakilden og importerer disse elementer til Microsoft 365. Connectoren konverterer indholdet, f.eks. chats, vedhæftede filer og indlæg fra Salesforce Chatter, til et mailformat og importerer derefter disse elementer til brugerens postkasse i Microsoft 365.

Når Salesforce Chatter-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. litigation hold, eDiscovery, opbevaringspolitikker og opbevaringsmærkater. Brug af en Salesforce Chatter-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Oversigt over arkivering af Salesforce Chatter-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Salesforce Chatter-dataene i Microsoft 365.

![Arkivering af arbejdsproces for Salesforce Chatter-data.](../media/SalesforceChatterConnectorWorkflow.png)

1. Din organisation arbejder sammen med Salesforce Chatter om at konfigurere et Salesforce Chatter-websted.

2. En gang hver 24 timer kopieres Salesforce Chatter-elementer til Veritas Merge1-webstedet. Connectoren også Salesforce Chatter-elementer til et mailmeddelelsesformat.

3. Salesforce Chatter-connectoren, som du opretter på overholdelsesportalen, opretter forbindelse til Veritas Merge1-webstedet hver dag og overfører Chatter-indholdet til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

4. Connectoren importerer de konverterede elementer til postkasserne for bestemte brugere ved hjælp af værdien af egenskaben *Mail* for den automatiske brugertilknytning som beskrevet i [trin 3](#step-3-map-users-and-complete-the-connector-setup). Der oprettes en undermappe i mappen Indbakke med navnet **Salesforce Chatter** i brugerpostkasserne, og elementer importeres til den pågældende mappe. Connectoren bestemmer, hvilken postkasse der skal importeres elementer til ved hjælp af værdien for egenskaben *Mail* . Alle Chatter-elementer indeholder denne egenskab, som udfyldes med mailadressen på alle deltagere i elementet.

## <a name="before-you-begin"></a>Før du begynder

- Opret en Flet1-konto til Microsoft-connectors. Hvis du vil oprette en konto, skal du kontakte [Veritas Kundesupport](https://www.veritas.com/content/support/). Du skal logge på denne konto, når du opretter connectoren i trin 1.

- Opret et Salesforce-program, og hent et token på [https://salesforce.com](https://salesforce.com). Du skal logge på Salesforce-kontoen som administrator og få et personligt brugertoken til at importere data. Udløsere skal også publiceres på Chatter-webstedet for at registrere opdateringer, sletninger og redigeringer. Disse udløsere opretter et indlæg på en kanal, og Merge1 henter oplysningerne fra kanalen. Hvis du vil have en trinvis vejledning i, hvordan du opretter programmet og henter tokenet, skal du se [Brugervejledning til flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- Den bruger, der opretter Salesforce Chatter-connectoren i trin 1 (og fuldfører den i trin 3), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne Veritas-dataconnector fås som offentlig prøveversion i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>Trin 1: Konfigurer Connectoren Salesforce Chatter

Det første trin er at få adgang til siden **DataConnectors på overholdelsesportalen** og oprette en connector til Chatter-data.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik derefter på **DataconnectorsSalesforce** >  **Chatter**.

2. Klik på **Tilføj connector** på siden **Salesforce Chatter-produktbeskrivelse**.

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**.

5. Log på din Merge1-konto for at konfigurere connectoren.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>Trin 2: Konfigurer Salesforce Chatter på Veritas Merge1-webstedet

Det andet trin er at konfigurere Salesforce Chatter-connectoren på Veritas Merge1-webstedet. Du kan få mere at vide om, hvordan du konfigurerer Salesforce Chatter-connectoren, i [Brugervejledningen til Flette1 tredjepartsconnectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

Når du klikker på **Gem & Udfør,** vises siden **Brugertilknytning** i connectorguiden på overholdelsesportalen.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Trin 3: Tilknyt brugere, og fuldfør connectorkonfigurationen

Hvis du vil tilknytte brugere og fuldføre connectorkonfigurationen på overholdelsesportalen, skal du følge disse trin:

1. Aktivér automatisk brugertilknytning på siden **Map Salesforce Chatter for at Microsoft 365 brugere**. Salesforce Chatter-elementerne indeholder en egenskab kaldet *Mail*, som indeholder mailadresser til brugere i din organisation. Hvis connectoren kan knytte denne adresse til en Microsoft 365 bruger, importeres elementerne til den pågældende brugers postkasse.

2. klik på **Næste**, gennemse dine indstillinger, og gå derefter til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>Trin 4: Overvåg Connectoren Salesforce Chatter

Når du har oprettet connectoren Salesforce Chatter, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik på **Dataconnectors** i venstre navigationsrude.

2. klik på fanen **Forbindelser,** og klik derefter på connectoren **Salesforce Chatter** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder data, der er importeret til Microsoft-cloudmiljøet.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.