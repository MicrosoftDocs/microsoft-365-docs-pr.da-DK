---
title: Konfigurer en forbindelse til at arkivere WeChat-data i Microsoft 365
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
description: Konfigurer og brug en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere WeChat-data Microsoft 365.
ms.openlocfilehash: f2adb42dfd8145658e8861c752cfb9c11e306f52
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593902"
---
# <a name="set-up-a-connector-to-archive-wechat-data"></a>Konfigurer en forbindelse til at arkivere WeChat-data

Brug teleMessage-forbindelsen i Microsoft 365 Overholdelsescenter til at importere og arkivere WeChat- og WeCom-opkald, chats, vedhæftede filer, filer og tilbagekaldte meddelelser. Når du har konfigureret en forbindelse, oprettes der forbindelse til organisationens TeleMessage-konto, og den importerer den mobile kommunikation for medarbejdere ved hjælp af TeleMessage WeChat Archiver til postkasser i Microsoft 365.

Når WeChat Archiver-forbindelsesdata er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, eDiscovery, In-Place Arkivering, Overvågning, Overholdelse af kommunikation og Microsoft 365-opbevaringspolitikker til WeChat-kommunikationsdata. Du kan f.eks. søge i WeChat-kommunikation ved hjælp af Indholdssøgning eller knytte den postkasse, der indeholder forbindelsesdata fra WeChat-arkivet, til en person, der er tilknyttet en Advanced eDiscovery sag. Hvis du bruger en WeChat Archiver-forbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde regler og standarder inden for virksomhedsstyring og lovgivning.

## <a name="overview-of-archiving-wechat-communication-data"></a>Oversigt over arkivering af WeChat-kommunikationsdata

Følgende oversigt forklarer processen med at bruge en forbindelse til at arkivere WeChat-kommunikationsdata Microsoft 365.

![Arkivering af arbejdsproces for WeChat-arkivdata.](../media/WeChatConnectorWorkflow.png)

1. Din organisation arbejder sammen med TeleMessage om at konfigurere en forbindelseskomponent til WeChat Archiver.

2. I realtid kopieres din organisations WeChat-data til TeleMessage-webstedet.

3. Den WeChat Archiver-forbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til TeleMessage-webstedet hver dag og overfører mails fra de foregående 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

4. Forbindelsen importerer elementer fra mobilkommunikation til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet WeChat-arkiv i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen tilknytter ved hjælp af værdien af *brugerens mailadresseegenskab* . Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning med værdien af  brugerens mailadresseegenskab kan du også definere en brugerdefineret tilknytning ved at overføre en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde brugerens mobilnummer og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, ser forbindelsen først på brugerdefineret tilknytningsfil for hvert mailelement. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers mobilnummer, bruger forbindelsen brugerens mailadresseegenskab for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller brugerens mailadresseegenskab for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Arbejd med TeleMessage for at konfigurere en WeChat-arkivforbindelse. Du kan finde flere oplysninger [under Aktivering af TeleMessage WeChat-arkivet for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-wechat-archiver/).

- Konfigurer en TeleMessage-forbindelse til Microsoft 365 få en gyldig firmaadministrationskonto. Du kan få mere at [vide under Microsoft 365 til mobilarkivering](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-microsoft-365/).

- Registrer alle brugere, der kræver WeChat-arkivering, på TeleMessage-kontoen med den samme mailadresse, der bruges til brugerens Microsoft 365 konto.

- Du skal installere Tencent WeCom-appen på brugernes mobiltelefoner i organisationen og aktivere den. WeCom-appen giver brugerne mulighed for at kommunikere og chatte med andre WeChat- og WeCom-brugere.

- Den bruger, der opretter en WeChat-arkivr-forbindelse i Microsoft 365 Overholdelsescenter, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Denne TeleMessage-dataforbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="create-a-wechat-archiver-connector"></a>Opret en WeChat Archiver-forbindelse

Følg trinnene i dette afsnit for at oprette en WeChat Archiver-forbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til TeleMessage-webstedet og overføre WeChat-kommunikationsdata til de tilsvarende brugerpostkasser Microsoft 365.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på DataforbindelserWeChat** >  **Archiver**.

2. På siden **produktbeskrivelse for WeChat-arkiv skal** du klikke på **Tilføj forbindelse**

3. Klik **på Acceptér på** siden **Servicebetingelser**.

4. På siden **Login på TeleMessage under** Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Næste**.

    - **Brugernavn**: Dit TeleMessage-brugernavn.

    - **Adgangskode**: Din TeleMessage-adgangskode.

5. Når forbindelsen er oprettet, kan du lukke pop op-vinduet, gå til den næste side.

6. På siden **Brugertilknytning** skal du aktivere automatisk brugertilknytning. Du kan også overføre en brugerdefineret CSV-fil til brugertilknytning.

7. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

8. Gå til fanen **Forbindelser på** **siden Dataforbindelser for** at se status for importprocessen for den nye forbindelse.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
