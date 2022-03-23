---
title: Arkivér Slack eDiscovery-data for at Microsoft 365 brug af en dataforbindelse leveret af Microsoft
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
description: Få mere at vide om, hvordan du konfigurerer og bruger en Slack eDiscovery-dataforbindelse, der leveres af Microsoft til at importere og arkivere chatdata.
ms.openlocfilehash: 2bd4df859d5bb3a4ccd048c83a864d44f81f33bc
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594709"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Konfigurer en forbindelse til at arkivere Slack eDiscovery-data (forhåndsvisning)

Slack eDiscovery-dataforbindelse leveret af Microsoft hjælper dig med at importere og arkivere chatdata (f.eks. meddelelser, vedhæftede filer, links og ændringer) fra din organisations Slæk-arbejdsområder til at Microsoft 365. Dataforbindelse trækker data fra Slack API'en, konverterer dem til et mailformat og importerer derefter disse elementer til brugerpostkasser i Microsoft 365. Når slækdataene er importeret, kan du anvende overholdelsesløsninger, f.eks Retslig tilbageholdelse, retslig tilbageholdelse Advanced eDiscovery, Overholdelse af kommunikation og opbevaringsindstillinger for indholdet af Slæk. Brug af en Slack eDiscovery-dataforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Oversigt over arkivering af Slack eDiscovery-data

Følgende oversigt beskriver processen med at bruge en Microsoft-dataforbindelse til at arkivere Slækdata Microsoft 365.

![Arbejdsproces for arkivering af slæk i eDiscovery.](../media/SlackMSFTConnectorWorkflow.png)

1. Din organisation arbejder med Slæk for at konfigurere et Slæk-arbejdsområde.

2. Når dataforbindelse er konfigureret, kopieres meddelelser fra organisationens Slæk-arbejdsområder til brugerpostkasser Microsoft 365. Dataforbindelsesforbindelse konverterer også indholdet af en chatmeddelelse til et mailformat.

3. Forbindelsen importerer de konverterede chatmeddelelser til postkasser for bestemte brugere. Der oprettes en undermappe i mappen Indbakke med navnet **Slack eDiscovery** i brugerpostkasserne, og chatmeddelelseselementerne importeres til den pågældende mappe.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Din organisation skal bruge Enterprise Grid-abonnementet til Slæk. Få mere at vide under [Slæk-abonnementer og -funktioner](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Den bruger, der opretter dataforbindelse, skal have tildelt **programrollen Org-ejere** i deres Slæk-organisation. Få mere at vide under [Typer af roller i Slæk](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Hent brugernavnet og adgangskoden til din organisations Slack-virksomhedskonto. Du bruger disse legitimationsoplysninger til at logge på denne konto, når du opretter dataforbindelse. Det anbefales også, at du har automatiseret bruger klargøring i din Slæk-organisation konfigureret til at bruge enkelt logon (SSO). [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Den bruger, der opretter Slæk-eDiscovery-forbindelsen, skal være tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-a-slack-ediscovery-connector"></a>Trin 1: Opret en Slæk-eDiscovery-forbindelse

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser i venstre navigationsrude** .

2. På fanen **Oversigt** skal du klikke **på Filtrer** og **vælge Efter Microsoft** og derefter anvende filteret.

3. Klik **på Slæk eDiscovery (forhåndsvisning)**.

4. På siden **Slack eDiscovery (preview) produktbeskrivelse** skal du klikke **på Tilføj forbindelse**.

5. Klik **på Acceptér på** siden med guiden **Servicebetingelser**.

6. Angiv et entydigt navn, der identificerer forbindelsen, og klik derefter på **Næste**. Det navn, du angiver, identificerer forbindelsen på siden **Dataforbindelser** , når du har oprettet den.

## <a name="step-2-sign-into-your-slack-organization"></a>Trin 2: Log på din Slæk-organisation

1. Klik på **Log på Slæk** på siden i guiden **Slæk** for at logge på organisationens Slæk-arbejdsområde.

2. På siden **Slæk log på arbejdsområdet** skal du skrive navnet på det arbejdsområde, du vil arkivere data fra, og derefter klikke på **Fortsæt**.

   Der vises en side med navnet på dit Slæk-arbejdsområde og en prompt om at logge på.

3. Klik på linket i strengen **Org-ejere kan også logge på her**.

4. På logonsiden til arbejdsområdet skal du angive mailadressen og adgangskoden til organisationens Slack-virksomhedskonto og derefter klikke på **Log på**.

   Når du er logget på, vises en side, der anmoder om tilladelse til at få adgang til organisationen Slæk fra forbindelsesappen.

5. Klik **på Tillad** for at tillade, at appen administrerer din organisation.

   Når du har **klikket** på Tillad, lukkes siden Slæk, og siden Slæk i slæk for **eDiscovery-brugere Microsoft 365** brugere i forbindelsesguiden vises.

## <a name="step-3-map-users-and-select-data-types-to-import"></a>Trin 3: Tilknyt brugere, og vælg de datatyper, der skal importeres

1. Konfigurer en eller begge af følgende indstillinger for at knytte Slækbrugere til deres Microsoft 365 postkasser.

   - **Automatisk brugertilknytning**. Markér denne indstilling for automatisk at knytte Slæk-brugernavne til Microsoft 365 postkasser. Forbindelsen gør ved hjælp af værdien af egenskaben *Mail* , som alle Slæk-meddelelser eller -elementer indeholder. Denne egenskab udfyldes med en mailadresse for hver deltager i meddelelsen. Hvis forbindelsen kan knytte mailadresserne til Microsoft 365 brugere, importeres elementet til Microsoft 365 disse brugeres postkasse. Hvis du vil bruge denne indstilling, skal du have SSO konfigureret for din Slæk-organisation.

   - **Brugerdefineret brugertilknytning**. Du kan også vælge at bruge brugerdefineret brugertilknytning i stedet for (eller som et supplement til) automatisk brugertilknytning. Med denne indstilling skal du oprette og derefter overføre en CSV-fil, der knytter brugernes Slæk-medlems-id til deres Microsoft 365 mailadresse. Det gør du ved at klikke på **Download CSV-tilknytningsskabelon**, udfylde CSV-filen med Slæk-medlems-id og Microsoft 365-mailadresse for alle brugere i organisationen og derefter vælge og uploade CSV-filen til guiden. Sørg for ikke at ændre kolonneoverskrifterne i CSV-filen. Her er et eksempel på CSV-tilknytningsfilen:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Medlems-i-data for brugere kan fås ved at klikke på ... Knappen Mere i en brugers profil og derefter vælge **Kopiér medlems-id**. Alternativt kan du bruge metoden Slack [users.list API](https://api.slack.com/methods/users.list) til at hente disse til alle medlemmer af et Slæk-team.

   Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytningsfil, ser forbindelsen først på den brugerdefinerede tilknytningsfil for at knytte slækbrugeren til en Microsoft 365 postkasse. Hvis forbindelsen ikke finder en gyldig Microsoft 365, der svarer til Slæk-brugeren, bruger forbindelsen egenskaben Mail for elementet Slæk. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller mailegenskaben for meddelelseselementet, importeres elementet ikke.

2. På siden **Vælg de datatyper, der skal** importeres i guiden skal du vælge de Slækdatatyper, du vil importere. Hvis du vil importere meddelelser fra alle kanaler, skal du vælge alle indstillinger. Ellers skal du kun vælge de datatyper, du vil importere.

     Ud over slækmeddelelser kan du også angive andre typer slækindhold, der skal importeres Microsoft 365. 

3. Når du har konfigureret de datatyper, der **skal importeres**, skal du klikke på Næste, gennemse indstillingerne for forbindelsen og derefter klikke **på Udfør** for at oprette forbindelsen.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Trin 4: Overvåg Slack eDiscovery-forbindelsen

Når du har oprettet Slack eDiscovery-forbindelsen, kan du få vist forbindelsens status i Microsoft 365 Overholdelsescenter.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com/) klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter **Slack eDiscovery-forbindelsen** for at få vist pop op-siden, der indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Forbindelsesstatus med kilde skal** du klikke **på linket Hent log** for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder data, der er blevet importeret til Microsoft-skyen.

## <a name="known-issues"></a>Kendte problemer

- På nuværende tidspunkt understøtter vi ikke import af vedhæftede filer eller elementer, der er større end 10 MB. Understøttelse af større elementer bliver tilgængelig på et senere tidspunkt.
