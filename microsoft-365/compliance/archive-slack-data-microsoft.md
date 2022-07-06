---
title: Arkivér Slack eDiscovery-data til Microsoft 365 ved hjælp af en dataconnector fra Microsoft
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en Slack eDiscovery-dataconnector, der leveres af Microsoft, til at importere og arkivere chatdata.
ms.openlocfilehash: 138a93449b4b2a9ce7b57b4c240f2e42c553d818
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631475"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Konfigurer en connector til at arkivere Slack eDiscovery-data (prøveversion)

Slack eDiscovery-dataconnectoren, der leveres af Microsoft, hjælper dig med at importere og arkivere chatdata (f.eks. meddelelser, vedhæftede filer, links og revisioner) fra organisationens Slack-arbejdsområder til Microsoft 365. Dataconnectoren henter data fra Slack-API'en, konverterer den til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365. Når Slack-dataene er importeret, kan du anvende løsninger til overholdelse af regler og standarder, f.eks. procesførelse, Microsoft Purview eDiscovery (Premium), kommunikation og opbevaringsindstillinger til Slack-indholdet. Brug af en Slack eDiscovery-dataconnector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Oversigt over arkivering af Slack eDiscovery-data

I følgende oversigt forklares processen med at bruge en Microsoft-dataconnector til at arkivere Slack-dataene i Microsoft 365.

![Slack eDiscovery-arkiveringsarbejdsproces.](../media/SlackMSFTConnectorWorkflow.png)

1. Din organisation arbejder sammen med Slack om at konfigurere et Slack-arbejdsområde.

2. Når dataconnectoren er konfigureret, kopieres meddelelser fra organisationens Slack-arbejdsområder til brugerpostkasser i Microsoft 365. Dataconnectoren konverterer også indholdet af en chatmeddelelse til et mailformat.

3. Connectoren importerer de konverterede chatmeddelelser til bestemte brugeres postkasser. Der oprettes en undermappe i mappen Indbakke med navnet **Slack eDiscovery** i brugerpostkasserne, og chatmeddelelseselementerne importeres til den pågældende mappe.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Din organisation skal bruge Enterprise Grid-abonnementet for Slack. Du kan få flere oplysninger under [Slack-abonnementer og -funktioner](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Den bruger, der opretter dataconnectoren, skal tildeles programrollen **Organisationsejere** i deres Slack-organisation. Du kan få flere oplysninger under [Typer af roller i Slack](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Hent brugernavnet og adgangskoden til din organisations Slack-virksomhedskonto. Du kan bruge disse legitimationsoplysninger til at logge på denne konto, når du opretter dataconnectoren. Det anbefales også, at du har automatiseret brugerklargøring i din Slack-organisation konfigureret til at bruge enkeltlogon (SSO). [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Den bruger, der opretter Slack eDiscovery-connectoren, skal tildeles rollen Data Connector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors** i Microsoft Purview-compliance-portal. Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-a-slack-ediscovery-connector"></a>Trin 1: Opret en Slack eDiscovery-connector

1. Gå til <https://compliance.microsoft.com> , og klik på **Dataconnectors** i venstre navigationsrude.

2. På fanen **Oversigt** skal du klikke på **Filtrer** og vælge **Efter Microsoft** og derefter anvende filteret.

3. Klik på **Slack eDiscovery (prøveversion)**.

4. Klik på **Tilføj connector** på siden **Slack eDiscovery (prøveversion)** produktbeskrivelse.

5. Klik på **Acceptér** på siden **med guiden Vilkår for tjeneste**.

6. Angiv et entydigt navn, der identificerer connectoren, og klik derefter på **Næste**. Det navn, du angiver, identificerer connectoren på siden **Dataconnectors,** når du har oprettet den.

## <a name="step-2-sign-into-your-slack-organization"></a>Trin 2: Log på din Slack-organisation

1. Klik på **Log på Slack** på siden **Med guiden Log på Slack** for at logge på organisationens Slack-arbejdsområde.

2. Skriv navnet på det arbejdsområde, du vil arkivere data fra, på siden **Slack Log på dit arbejdsområde** , og klik derefter på **Fortsæt**.

   Der vises en side med navnet på dit Slack-arbejdsområde og en meddelelse om at logge på.

3. Klik på linket i strengen **Organisationsejere kan også logge på her**.

4. På logonsiden for arbejdsområdet skal du angive mailadressen og adgangskoden for din organisations Slack-virksomhedskonto og derefter klikke på **Log på**.

   Når du er logget på, vises en side, der anmoder om tilladelse til at få adgang til din Slack-organisation via connectorappen.

5. Klik på **Tillad** for at tillade, at appen administrerer din organisation.

   Når du har klikket på **Tillad**, lukkes slack-siden og **eDiscovery-brugernes Map Slack-brugere til Microsoft 365-brugere** i connectorguiden.

## <a name="step-3-specify-the-users-to-import-data-for"></a>Trin 3: Angiv de brugere, der skal importeres data for

Vælg en af følgende indstillinger for at angive, hvilke brugere hvis Slack eDiscovery-data du vil importere.

- **Alle brugere i din organisation**. Vælg denne indstilling for at importere data for alle brugere.

- **Kun brugere, der er i strid med procesførelse**. Vælg denne indstilling, hvis du kun vil importere data for brugere, hvis postkasser er sat i strid med procesførelse. Denne indstilling importerer data til brugerpostkasser, hvor egenskaben LitigationHoldEnabled er angivet til Sand. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

## <a name="step-4-map-users-and-select-data-types-to-import"></a>Trin 4: Tilknyt brugere, og vælg de datatyper, der skal importeres

1. Konfigurer en eller begge af følgende indstillinger for at knytte Slack-brugere til deres Microsoft 365-postkasser.

   - **Automatisk brugertilknytning**. Vælg denne indstilling for automatisk at knytte Slack-brugernavne til Microsoft 365-postkasser. Det gør connectoren ved hjælp af værdien af egenskaben Mail, som alle *Slack-meddelelser* eller -elementer indeholder. Denne egenskab udfyldes med en mailadresse på hver deltager i meddelelsen. Hvis connectoren kan knytte mailadresserne til de tilsvarende Microsoft 365-brugere, importeres elementet til disse brugeres Microsoft 365-postkasse. Hvis du vil bruge denne indstilling, skal du have SSO konfigureret for din Slack-organisation.

   - **Brugerdefineret brugertilknytning**. Du har også mulighed for at bruge brugerdefineret brugertilknytning i stedet for (eller ud over) automatisk brugertilknytning. Med denne indstilling skal du oprette og derefter uploade en CSV-fil, der knytter brugernes Slack-medlems-id til deres Microsoft 365-mailadresse. Det gør du ved at klikke på **Download CSV-tilknytningsskabelon**, udfylde CSV-filen med Slack-medlems-id'et og Microsoft 365-mailadressen for alle brugere i din organisation og derefter vælge og overføre CSV-filen til guiden. Sørg for ikke at ændre kolonneoverskrifterne i CSV-filen. Her er et eksempel på CSV-tilknytningsfilen:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Medlems-id'er for brugere kan fås ved at klikke på ... Knappen Mere i en brugers profil, og vælg derefter **Kopiér medlems-id**. Du kan også bruge [metoden Slack users.list API](https://api.slack.com/methods/users.list) til at hente id'erne for alle medlemmer af et Slack-team.

   Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytningsfil, kigger connectoren først på den brugerdefinerede tilknytningsfil for at knytte Slack-brugeren til en Microsoft 365-postkasse. Hvis connectoren ikke finder en gyldig Microsoft 365-bruger, der svarer til Slack-brugeren, bruger connectoren egenskaben Mail for *Slack-elementet* . Hvis connectoren ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben *Mail* for meddelelseselementet, importeres elementet ikke.

2. Vælg de Slack-datatyper, du vil importere, på siden **Vælg datatyper, der skal importeres** . Hvis du vil importere meddelelser fra alle kanaler, skal du vælge alle indstillinger. Ellers skal du kun vælge de datatyper, du vil importere.

     Ud over Slack-meddelelser kan du også angive andre typer Slack-indhold, der skal importeres til Microsoft 365. 

3. Når du har konfigureret de datatyper, der skal importeres, skal du klikke på **Næste**, gennemse connectorindstillingerne og derefter klikke på **Udfør** for at oprette connectoren.

## <a name="step-5-monitor-the-slack-ediscovery-connector"></a>Trin 5: Overvåg Slack eDiscovery-connectoren

Når du har oprettet Slack eDiscovery-connectoren, kan du få vist connectorstatussen på overholdelsesportalen.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com/) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter **Slack eDiscovery-connectoren** for at få vist pop op-siden, som indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Forbindelsesstatus med kilde** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om de data, der er importeret til Microsoft-cloudmiljøet. Du kan finde flere oplysninger under [Få vist administratorlogge for dataconnectors](data-connector-admin-logs.md).

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer vil være tilgængelig på et senere tidspunkt.
