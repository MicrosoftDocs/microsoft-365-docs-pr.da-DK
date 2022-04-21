---
title: Konfigurer en connector til arkivering af WeChat-data i Microsoft 365
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
description: Konfigurer og brug en connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere WeChat-data i Microsoft 365.
ms.openlocfilehash: 8d87cbaf25396dc9af1497737450126e90b54a7a
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997202"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>Konfigurer en connector til arkivering af WeChat-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug TeleMessage-connectoren på Microsoft Purview-overholdelsesportalen til at importere og arkivere WeChat- og WeCom-opkald, chats, vedhæftede filer, filer og tilbagekaldte meddelelser. Når du har konfigureret en connector, oprettes der forbindelse til din organisations TeleMessage-konto, og medarbejdernes mobilkommunikation importeres ved hjælp af TeleMessage WeChat Archiver til postkasser i Microsoft 365.

Når WeChat Archiver-connectordata er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner, f.eks. Litigation Hold, eDiscovery, In-Place Archiving, Auditing, Communication compliance og Microsoft 365 retention policies på WeChat-kommunikationsdata. Du kan f.eks. søge i WeChat-kommunikation ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder WeChat Archiver-connectordataene, til en tilsynsførende i en eDiscovery-sag (Premium). Hvis du bruger en WeChat Archiver-connector til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde reglerne for virksomhedsstyring og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-wechat-communication-data"></a>Oversigt over arkivering af WeChat-kommunikationsdata

I følgende oversigt forklares processen med at bruge en connector til at arkivere WeChat-kommunikationsdata i Microsoft 365.

![Arkivering af arbejdsproces for WeChat Archiver-data.](../media/WeChatConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en WeChat Archiver-connector.

2. I realtid kopieres din organisations WeChat-data til TeleMessage-webstedet.

3. Den WeChat Archiver-connector, du opretter i overholdelsesportalen, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mailmeddelelserne fra de forrige 24 timer til et sikkert Azure Storage område i Microsoft Cloud.

4. Connectoren importerer mobilkommunikationselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet WeChat Archiver i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren tilknytter ved hjælp af værdien for *brugerens mailadresseegenskab* . Alle mails indeholder denne egenskab, som udfyldes med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning ved hjælp af værdien for *brugerens mailadresseegenskab* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers mobilnummer, bruger connectoren brugerens mailadresseegenskab for mailelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede *tilknytningsfil eller brugerens mailadresseegenskab* for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Arbejd med TeleMessage for at konfigurere en WeChat-arkivconnector. Du kan få flere oplysninger under [Aktivering af TeleMessage WeChat Archiver til Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- Konfigurer en TeleMessage-connector til Microsoft 365, og få en gyldig firmaadministrationskonto. Du kan få flere oplysninger under [Bestil Microsoft 365 Mobilarkivering](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/).

- Registrer alle brugere, der kræver WeChat-arkivering, på TeleMessage-kontoen med den samme mailadresse, som bruges til brugerens Microsoft 365 konto.

- Du skal installere Tencent WeCom-appen på mobiltelefoner for brugere i din organisation og aktivere den. Med WeCom-appen kan brugerne kommunikere og chatte med andre WeChat- og WeCom-brugere.

- Den bruger, der opretter en WeChat Archiver-connector på overholdelsesportalen, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataconnector er tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="create-a-wechat-archiver-connector"></a>Opret en WeChat Archiver-connector

Følg trinnene i dette afsnit for at oprette en WeChat Archiver-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre WeChat-kommunikationsdata til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **DataconnectorsWeChat** >  **Archiver**.

2. Klik på **Tilføj connector** på siden **WeChat Archiver-produktbeskrivelse**

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. På siden **Log på TeleMessage** under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

    - **Brugernavn**: Dit TeleMessage-brugernavn.

    - **Adgangskode**: Din TeleMessage-adgangskode.

5. Når connectoren er oprettet, kan du lukke pop op-vinduet gå til næste side.

6. Aktivér automatisk brugertilknytning på siden **Brugertilknytning** . Du kan også uploade en brugerdefineret CSV-fil til brugertilknytning.

7. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til fanen **Forbindelser** på siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
