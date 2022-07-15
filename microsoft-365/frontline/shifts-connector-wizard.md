---
title: Brug guiden Skifts-connector til at forbinde Shifts med blåt Workforce Management
author: lanachin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du bruger guiden Skifts-connector til at integrere Shifts i Teams med blue yonder-Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 8c4aa1036af00eaaf7d776c267648141bf4db733
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823965"
---
# <a name="use-the-shifts-connector-wizard-to-connect-shifts-to-blue-yonder-workforce-management"></a>Brug guiden Skifts-connector til at forbinde Shifts med blåt Workforce Management

## <a name="overview"></a>Oversigt

Guiden Skifts-connector i Microsoft 365 Administration giver dig mulighed for at integrere Appen Shifts i Microsoft Teams med dit system til administration af arbejdsstyrken (WFM). Når du har konfigureret en forbindelse, kan frontlinjemedarbejderne uden problemer få vist og administrere deres tidsplaner i dit WFM system inde fra Skift.

Guiden konfigurerer Shifts-connectoren, opretter en forbindelse til dit WFM system og anvender de synkroniseringsindstillinger og teamtilknytninger, du vælger. Synkroniseringsindstillinger bestemmer de tidsplanoplysninger, der synkroniseres mellem dit WFM system og Skift. Teamtilknytninger definerer synkroniseringsrelationen mellem dine WFM instanser og teams i Teams. Du kan knytte til eksisterende teams og nye teams.

Du kan konfigurere flere forbindelser, der hver især har forskellige synkroniseringsindstillinger. Hvis din organisation f.eks. har flere placeringer med forskellige tidsplankrav, skal du oprette en forbindelse med entydige synkroniseringsindstillinger for hver placering. Vær opmærksom på, at en WFM forekomst kun kan knyttes til ét team på et givet tidspunkt. Hvis en WFM forekomst allerede er knyttet til et team, kan den ikke knyttes til et andet team.

Med dit WFM system som postsystem kan frontlinjemedarbejderne se og skifte skiftehold, administrere deres tilgængelighed og anmode om fridag i skiftehold på deres enheder. Frontlineadministratorer kan fortsætte med at bruge dit WFM system til at konfigurere tidsplaner.

## <a name="integrate-shifts-with-blue-yonder-workforce-management"></a>Integrer skift med blåt Workforce Management

I øjeblikket understøtter guiden [Microsoft Teams Shifts-connectoren til Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder). Denne connector giver dig mulighed for at integrere Skift med Blue Yonder Workforce Management (Blue Yonder WFM) for at administrere dine tidsplaner og holde dem opdateret. I denne artikel gennemgår vi, hvordan du kører guiden for at konfigurere en forbindelse til Blue Yonder WFM via connectoren.

> [!NOTE]
> Du kan også bruge PowerShell til at integrere Skift med Blue Yonder WFM. Du kan få mere at vide under [Brug PowerShell til at oprette forbindelse mellem Skift og Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md).

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator af Microsoft 365 for at køre guiden.

### <a name="prerequisites"></a>Forudsætninger
<a name="prerequisites"> </a>
[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

- De teams, du vil tilknytte, har ingen tidsplaner. Hvis et team har en eksisterende tidsplan, skal du [fjerne tidsplanen fra teamet](#remove-schedules-from-teams-you-want-to-map), før du knytter en Blue Yonder-forekomst WFM forekomst til den. Ellers kan du se dublerede skift.

## <a name="remove-schedules-from-teams-you-want-to-map"></a>Fjern tidsplaner fra de teams, du vil tilknytte
<a name="remove_schedules"> </a>

> [!NOTE]
> Fuldfør dette trin, hvis du knytter Blue Yonder WFM forekomster til eksisterende teams, der har tidsplaner. Hvis du tilknytter til teams, der ikke har nogen tidsplaner, eller hvis du opretter nye teams, der skal tilknyttes, kan du springe dette trin over.

Brug PowerShell til at fjerne tidsplaner fra teams.

1. Først skal du installere PowerShell-modulerne og konfigurere dem. Følg trinnene for at [konfigurere dit miljø](shifts-connector-powershell-manage.md#set-up-your-environment).
1. Kør følgende kommando:

    ```powershell
    Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate <end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
    ```

    Hvis du vil hente en liste over scenarier for `EntityType` parameteren, skal du køre [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector). Planlægningsdata fjernes for den dato og det tidsinterval, du angiver.

Du kan få mere at vide under [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord).

## <a name="run-the-wizard"></a>Kør guiden

### <a name="get-started"></a>Kom i gang

1. I venstre navigationsrude i [Microsoft 365 Administration](https://admin.microsoft.com/) skal du vælge **Konfiguration** og derefter gå til afsnittet **Apps og mail**.
1. Vælg **Opret forbindelse til administrationssystemet for din arbejdsstyrke**. Her kan du få mere at vide om Shifts-forbindelser og frontlinjemedarbejder- og lederoplevelsen, når du forbinder Shifts til dit WFM system.
    :::image type="content" source="media/shifts-connector-wizard-get-started.png" alt-text="Skærmbillede af detaljesiden for guiden Skifts-connector i Microsoft 365 Administration." lightbox="media/shifts-connector-wizard-get-started.png":::
1. Når du er klar, skal du vælge **Kom i gang**.
1. Vælg **Næste** for at oprette en blå yonder-WFM forbindelse.

### <a name="enter-connection-details"></a>Angiv forbindelsesoplysninger
<a name="connection_details"> </a>

1. På siden Forbindelsesoplysninger skal du give din forbindelse et entydigt navn. Den må ikke være længere end 128 tegn eller indeholde specialtegn.
    :::image type="content" source="media/shifts-connector-wizard-connection-details.png" alt-text="Skærmbillede af siden Forbindelsesoplysninger i guiden, der viser forbindelsesindstillinger." lightbox="media/shifts-connector-wizard-connection-details.png":::
1. Angiv navnet på din Blue Yonder-WFM tjenestekonto samt url-adresser til adgangskode og tjeneste.
1. Når du er færdig, skal du vælge **Næste** for at teste forbindelsen med de indstillinger, du har angivet.

### <a name="choose-sync-settings"></a>Vælg synkroniseringsindstillinger
<a name="sync"> </a>

På siden Synkroniseringsindstillinger skal du vælge de oplysninger, der skal synkroniseres fra Blue Yonder WFM til Skift, synkroniseringshyppigheden, og om Skift-brugere kan foretage ændringer af dataene.

1. Angiv din Microsoft 365-systemkonto.
    :::image type="content" source="media/shifts-connector-wizard-sync-settings.png" alt-text="Skærmbillede af siden Synkroniseringsindstillinger i guiden, der viser synkroniseringsindstillinger." lightbox="media/shifts-connector-wizard-sync-settings.png":::
<a name="email"> </a>
1. Under **Modtagere af mailmeddelelser** skal du vælge, hvem der modtager mailmeddelelser om denne forbindelse. Du kan tilføje individuelle brugere og grupper. Mailmeddelelserne indeholder oplysninger om konfigurationsstatus for forbindelsen og eventuelle problemer eller fejl, der kan opstå, når forbindelsen er konfigureret.
1. Vælg dine synkroniseringsindstillinger:
    1. Under **Tidsplan og vagter** skal du vælge den blå yonder-WFM data, som Shifts-brugere kan se eller ændre, og derefter angive synkroniseringshyppigheden.
    2. Under **Anmodninger** skal du vælge de typer anmodninger, som Skift-brugere kan se og oprette.

    > [!IMPORTANT]
    > Hvis du vælger en af følgende muligheder for at deaktivere åbne skiftehold, anmodninger om åbning af skiftehold, swapanmodninger eller anmodninger om fridag, er der endnu et trin, du skal gøre for at skjule funktionen i Skift.
    >
    > - Åbne skiftehold: **Brugerne får ikke vist blue yonder WFM data**
    > - Swapanmodninger: **Funktionen er deaktiveret for alle brugere**
    > - Anmodninger om fridag: **Funktionen er deaktiveret for alle brugere**
    >
    > Når du har kørt guiden, skal du sørge for at følge trinnene i afsnittet [Deaktiver åbne skiftehold, åbne skiftanmodninger, bytte anmodninger og anmodninger om fridag](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) senere i denne artikel.
 
1. Når du er færdig med at vælge dine indstillinger, skal du vælge **Opret forbindelse**.

### <a name="map-blue-yonder-workforce-management-instances-to-teams"></a>Map Blue Yonder Workforce Management forekomster til teams
<a name="sites"> </a>

Vælg de blå yonder-WFM instanser, du vil oprette forbindelse til Skift, og knyt derefter hver forekomst til et team i Teams. Du kan tilknytte op til 100 forekomster. Du kan gøre dette på to måder:

- [Knyt forekomster manuelt til teams](#manually-map-instances-to-teams)
- [Forbered og upload en CSV-fil, der definerer dine tilknytninger](#use-a-csv-file-to-map-instances-to-teams)

#### <a name="manually-map-instances-to-teams"></a>Knyt forekomster manuelt til teams

Vælg de forekomster, du vil tilknytte.

:::image type="content" source="media/shifts-connector-wizard-sites.png" alt-text="Skærmbillede af guiden, der viser listen over forekomster af Blue Yonder WFM." lightbox="media/shifts-connector-wizard-sites.png":::
<a name="mapping"> </a>
<a name="search_teams"> </a> Knyt derefter hver forekomst til et team i Teams. Du kan knytte en forekomst til et eksisterende team, eller du kan oprette et nyt team.
:::image type="content" source="media/shifts-connector-wizard-search-team.png" alt-text="Skærmbillede af ruden, der viser indstillingen for søgeteamet og opretter en ny teamindstilling." lightbox="media/shifts-connector-wizard-search-team.png":::

##### <a name="to-map-an-instance-to-an-existing-team"></a>Sådan knyttes en forekomst til et eksisterende team

1. Vælg navnet på forekomsten.
2. Søg efter teamet i ruden, og vælg det derefter. Vær opmærksom på, at teams, der allerede er knyttet til en forekomst i denne forbindelse, ikke vises i søgningen.
3. Vælg tidszonen og den nærmeste by.
4. Vælg **Gem**, og vælg derefter **Næste**.

##### <a name="to-map-an-instance-to-a-new-team"></a>Sådan knyttes en forekomst til et nyt team

1. Vælg navnet på forekomsten.
2. Vælg **Opret et nyt team** i ruden. Du føres til en ny fane i din browser, hvor du kan oprette et nyt team i Microsoft 365 Administration.
    1. Angiv et navn og en valgfri beskrivelse af teamet.
    1. Tilføj en eller flere teamejere. Sørg for at tilføje Microsoft 365-systemkontoen som ejer.
    1. Tilføj teammedlemmer.
    1. Tilføj en teammailadresse, og vælg en indstilling for beskyttelse af personlige oplysninger.
    1. Gennemse dine indstillinger, og vælg derefter **Tilføj team**. Når dit team er oprettet, skal du vælge **Luk**.
3. Gå tilbage til guiden, søg efter, og vælg derefter det nye team, du har oprettet.
4. Vælg tidszonen og den nærmeste by.
5. Vælg **Gem**, og vælg derefter **Næste**.

#### <a name="use-a-csv-file-to-map-instances-to-teams"></a>Brug en CSV-fil til at knytte instanser til teams

1. Vælg **Skift til massetilstand**.
1. Vælg **Download en skabelonfil** for at downloade en tilknytningsskabelon, som du kan bruge til at definere dine tilknytninger.

    :::image type="content" source="media/shifts-connector-wizard-mapping-file.png" alt-text="Skærmbillede af siden Overfør tilknytningsfil i guiden." lightbox="media/shifts-connector-wizard-mapping-file.png":::

1. Brug skabelonen til at oprette tilknytningsfilen. Den indeholder disse kolonner i følgende rækkefølge, startende med den første kolonne. En stjerne (*) angiver en påkrævet kolonne.

    |Kolonnenavn  |Beskrivelse  |
    |---------|---------|
    |**Blåt forekomst-id for yonder*** |Blue Yonder WFM forekomst-id.|
    |**Navn på forekomst af blåt år**|Navnet på forekomsten Blue Yonder WFM.|
    |**Team-id*** |Team-id'et.|
    |**Teamnavn**|Teamnavnet.|
    |**Tidszone*** |Tidszonen i tz-databaseformat. For eksempel Europa/London.|

    > [!NOTE]
    > Du skal kun udfylde de påkrævede kolonner (blåt forekomst-id for Yonder, team-id, tidszone) for at knytte forekomster til teams.

    Her er et eksempel på, hvordan en tilknytningsfil ser ud.

    |Blåt forekomst-id for yonder|Navn på forekomst af blåt år|Team-id|Teamnavn|Tidszone|
    |---------|---------|---------|---------|---------|
    |2111|Contoso US Team|3a4d78a-2261|US Team|Amerika/Los_Angeles|
    |3212|Contoso UK Team|2d1f6c2e-5272|UK Team|Europa/London|
    |4865||bfa6o89e-1328||Amerika/Toronto|

1. Når du har oprettet tilknytningsfilen, skal du vælge **Gennemse** for at uploade den. Guiden validerer filen. Hvis den finder fejl, får du vist en liste over fejlene og en meddelelse, hvor du bliver bedt om at rette dem. Ellers får du vist en meddelelse om, at du vil fortsætte til næste trin.  
1. Vælg **Næste**.

### <a name="review-and-finish"></a>Gennemse og afslut

Gennemse dine indstillinger. Hvis du har brug for at foretage ændringer i gruppetilknytninger, skal du vælge **Rediger** for at gøre det. Når du er klar, skal du vælge **Udfør**.

:::image type="content" source="media/shifts-connector-wizard-review.png" alt-text="Skærmbillede af siden Gennemse i guiden, der viser tilknytninger." lightbox="media/shifts-connector-wizard-review.png":::

Du får vist en meddelelse, der bekræfter, at vi har modtaget din anmodning sammen med et handlings-id. Notér handlings-id'et. Du skal bruge den til at kontrollere konfigurationsstatussen for din forbindelse.

:::image type="content" source="media/shifts-connector-wizard-operation-id.png" alt-text="Skærmbillede af guidesiden, der viser bekræftelsesmeddelelsen og handlings-id'et." lightbox="media/shifts-connector-wizard-operation-id.png":::

Guiden starter processen for at konfigurere forbindelsen og knytte forekomsterne til de teams, du har valgt. Det kan tage noget tid at fuldføre denne proces. De modtagere, du vælger, modtager mailmeddelelser om konfigurationsstatus.

Vælg **Udført** for at afslutte guiden.

Du er på vej, men du er ikke færdig endnu! Sørg for at kontrollere din mail. Du modtager en bekræftelse på, at vi har modtaget din anmodning sammen med et [link](shifts-connector-powershell-manage.md#check-connection-setup-status) til, hvordan du kan kontrollere konfigurationsstatus.

> [!NOTE]
> Hvis der opstår et problem eller en fejl i en forbindelse, når den er konfigureret, får du besked i en mail. Følg instruktionerne i mailen for at foretage fejlfinding af problemet.

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>Deaktiver åbne skiftehold, anmodninger om åbne skiftehold, byt om på anmodninger og anmodninger om fridag

> [!IMPORTANT]
> Følg kun disse trin, hvis du har valgt en af følgende indstillinger til at deaktivere åbne skiftehold, åbne skiftanmodninger, skifte anmodninger eller anmodninger om fridag i guiden. Når du fuldfører dette trin, skjules funktionen i Skift.
>
> - Åbne skiftehold: **Brugerne får ikke vist blue yonder WFM data**
> - Swapanmodninger: **Funktionen er deaktiveret for alle brugere**
> - Anmodninger om fridag: **Funktionen er deaktiveret for alle brugere**
>
> Uden dette andet trin kan brugerne stadig se funktionen i Skift og får vist fejlmeddelelsen "ikke-understøttet handling", hvis de forsøger at bruge den.

Hvis du vil skjule åbne skiftehold, bytte om på anmodninger og anmodninger om fridag i Skift, skal du bruge Graph [API-planlægningsressourcetypen](/graph/api/resources/schedule) til at angive følgende parametre for ```false``` hvert team, du har knyttet til en Blue Yonder-WFM forekomst:

- Åbne skiftehold: ```openShiftsEnabled```
- Byt om på anmodninger:  ```swapShiftsRequestsEnabled```
- Anmodninger om fridag: ```timeOffRequestsEnabled```

Hvis du vil skjule anmodninger om åbne skiftehold i Skiftehold, skal du gå til **Indstillinger** i Skift og derefter slå indstillingen **Åbn skift** fra.

## <a name="if-you-need-to-make-changes-to-a-connection"></a>Hvis du har brug for at foretage ændringer af en forbindelse
<a name="update_connection"> </a>

Når en forbindelse er konfigureret, kan du bruge PowerShell til at foretage ændringer af den. Du kan f.eks. opdatere synkroniseringsindstillinger, teamtilknytninger og deaktivere synkronisering for en forbindelse. Du kan finde en trinvis vejledning under [Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder-Workforce Management](shifts-connector-powershell-manage.md).

## <a name="related-articles"></a>Relaterede artikler

- [Skifter forbindelse](shifts-connectors.md)
- [Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder-Workforce Management](shifts-connector-powershell-manage.md)
- [Administrer appen Skift i Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
