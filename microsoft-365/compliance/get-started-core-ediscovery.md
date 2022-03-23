---
title: Kom i gang med Core eDiscovery-sager Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Beskriver, hvordan du kommer i gang med at bruge Core eDiscovery Microsoft 365. Når du tildeler eDiscovery-tilladelser og opretter en sag, kan du tilføje medlemmer, oprette eDiscovery-ventende dokumenter og derefter søge efter og eksportere indhold, der er relevant for din undersøgelse.
ms.openlocfilehash: ff2baf1e4844532ba53f3aa32ae02b7a7c49f00e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590241"
---
# <a name="get-started-with-core-ediscovery-in-microsoft-365"></a>Introduktion til Core eDiscovery i Microsoft 365

Core eDiscovery i Microsoft 365 giver et grundlæggende eDiscovery-værktøj, som organisationer kan bruge til at søge efter og eksportere indhold i Microsoft 365 og Office 365. Du kan også bruge Core eDiscovery til at placere et eDiscovery-venteposition på indholdsplaceringer, f.eks Exchange-postkasser, SharePoint-websteder, OneDrive-konti og Microsoft Teams. Der er ikke behov for noget for at implementere Core eDiscovery, men der er nogle nødvendige opgaver, som en it-administrator og eDiscovery-leder skal udføre, før din organisation kan begynde at bruge Core eDiscovery til at søge, eksportere og bevare indhold.

I denne artikel beskrives de nødvendige trin til at konfigurere Core eDiscovery. Dette omfatter at sikre de rette licenser, der kræves for at få adgang til Core eDiscovery og placere en eDiscovery-venteposition på indholdsplaceringer samt tildele tilladelser til it-, juridiske og undersøgelsesteamet, så de kan få adgang til og administrere sager. Denne artikel indeholder også en detaljeret oversigt over brugen af sager til at søge efter og eksportere indhold.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Trin 1: Bekræft og tildel de relevante licenser

Licenser til core eDiscovery kræver det relevante organisationsabonnement og pr. bruger-licensering.

- **Organisationsabonnement:** For at få adgang til Core eDiscovery i Microsoft 365 Overholdelsescenter og bruge ventepositions- og eksportfunktionerne skal din organisation have et Microsoft 365 E3-Office 365 E3-abonnement eller nyere. Microsoft 365 Frontline-organisationer skal have et F5-abonnement.

- **Pr. bruger-licensering:** For at placere en eDiscovery-venteposition på postkasser og websteder skal brugerne have tildelt en af følgende licenser afhængigt af dit organisationsabonnement:

  - En Microsoft 365 E3-Office 365 E3-licens eller nyere

   ELLER

  - Office 365 E1 licens med en Exchange Online Plan 2 eller Exchange Online-arkivering-tilføjelseslicens

   ELLER

  - Microsoft 365 Frontline F5 Compliance- eller F5 Security &-licens til tilføjelsesprogrammet Overholdelse af regler og standarder  

  AND

  - Office 365 E1 licens med en SharePoint Online Plan 2 eller OneDrive for Business licens til Plan 2-tilføjelsesprogrammet
  
  Du kan finde oplysninger om, hvordan du tildeler licenser [, under Tildel licenser til brugere](../admin/manage/assign-licenses-to-users.md).

For oplysninger og vejledning om sikkerhed og overholdelse af regler og standarder:

- Download og se afsnittet eDiscovery og overvågning i tabellen [Microsoft 365 Comparison](https://aka.ms/M365EnterprisePlans).

- Se vejledningen [Microsoft 365 om sikkerhed og & - Tjenestebeskrivelser | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>Trin 2: Tildel eDiscovery-tilladelser

For at få adgang til Core eDiscovery eller blive tilføjet som medlem af en core eDiscovery-sag skal en bruger tildeles de relevante tilladelser. Specifikt skal en bruger tilføjes som medlem af rollegruppen eDiscovery Manager i Microsoft 365 Overholdelsescenter. Medlemmer af denne rollegruppe kan oprette og administrere centrale eDiscovery-sager. De kan tilføje og fjerne medlemmer, placere en eDiscovery-venteposition for brugere, oprette og redigere søgninger og eksportere indhold fra en core eDiscovery-sag.

Udfør følgende trin for at føje brugere til rollegruppen eDiscovery Manager:

1. Gå til siden Microsoft 365 Overholdelsescenter og log på med legitimationsoplysningerne for en administratorkonto i din Microsoft 365 eller Office 365 organisation.

2. På siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser skal**</a> du vælge **rollegruppen eDiscovery Manager** .

3. På pop op-siden eDiscovery Manager skal du klikke **på Rediger** ud for **afsnittet eDiscovery Manager** .

4. På siden **Vælg eDiscovery Manager i** guiden til redigering af rollegruppe skal du klikke **på Vælg Discovery Manager**.

5. Klik **på** Tilføj, og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen.

6. Klik **på Tilføj** for at tilføje de valgte brugere, og klik derefter på **Udført**.

7. Klik **på** Gem for at føje brugerne til rollegruppen, og klik derefter **på Luk** for at fuldføre trinnet.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Flere oplysninger om rollegruppen eDiscovery Manager

Der er to undergrupper i rollegruppen eDiscovery Manager. Forskellen mellem disse undergrupper er baseret på omfang.

- **eDiscovery-leder**: Kan få vist og administrere de Core eDiscovery-sager, de opretter eller er medlem af. Hvis en anden eDiscovery-manager opretter en sag, men ikke tilføjer en anden eDiscovery-leder som medlem af den pågældende sag, vil den anden eDiscovery-leder ikke kunne se eller åbne sagen på siden Core eDiscovery i overholdelsescenteret. Generelt kan de fleste personer i organisationen føjes til undergruppen eDiscovery Manager.

- **eDiscovery-administrator**: Kan udføre alle sagsstyringsopgaver, som en eDiscovery-leder kan udføre. Desuden kan en eDiscovery-administrator:

  - Få vist alle tilfælde, der er angivet på Core eDiscovery-siden.
  
  - Administrer alle sager i organisationen, når de tilføjer sig selv som medlem af sagen.

  - Få adgang til og eksportér sagsdata for alle tilfælde i organisationen.
  
  - Fjern medlemmer fra en eDiscovery-sag. Kun en eDiscovery-administrator kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, heller ikke selvom brugeren har oprettet sagen.

  På grund af den brede adgang bør en organisation kun have nogle få administratorer, der er medlem af undergruppen eDiscovery-administratorer.

Du kan finde flere oplysninger om eDiscovery-tilladelser og en beskrivelse af hver rolle, der er tildelt rollegruppen eDiscovery-leder, under Tildele [eDiscovery-tilladelser](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-core-ediscovery-case"></a>Trin 3: Opret en Core eDiscovery-sag

Det næste trin er at oprette en sag og begynde at bruge Core eDiscovery. Udfør følgende trin for at oprette en sag og tilføje medlemmer. Den bruger, der opretter sagen, tilføjes automatisk som medlem.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for en brugerkonto, der har fået tildelt de relevante eDiscovery-tilladelser. Medlemmer af rollegruppen Organisationsadministration kan også oprette centrale eDiscovery-sager.

2. Klik på Vis Microsoft 365 Overholdelsescenter navigationsruden i venstre **navigationsrude**, og klik derefter **på eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Klik på **Opret en sag på siden Core eDiscovery**.

4. På pop **op-siden** Ny sag skal du give sagen et navn (påkrævet) og derefter angive en valgfri beskrivelse. Casenavnet skal være entydigt i din organisation.

5. Klik **på Gem** for at oprette sagen.

   Den nye sag oprettes og vises på Core eDiscovery-siden. Du skal muligvis klikke på Opdater **for at** få vist den nye sag.

## <a name="step-4-optional-add-members-to-a-core-ediscovery-case"></a>Trin 4 (valgfrit): Føj medlemmer til en Core eDiscovery-sag

Hvis du opretter en sag i trin 3, og du er den eneste, der skal bruge sagen, behøver du ikke at udføre dette trin. Du kan begynde at bruge sagen til at oprette eDiscovery-ventende indhold, søge efter indhold og eksportere søgeresultater. Udfør dette trin, hvis du vil give andre brugere (eller rollegruppen) adgang til sagen.

1. På siden **Core eDiscovery** i Microsoft 365 Overholdelsescenter skal du klikke på navnet på den sag, du vil føje medlemmer til.

2. På startsiden for sagen skal du **vælge Indstillinger** og derefter **vælge Access & tilladelser**.

3. På siden **Adgangstilladelser &** du klikke på **Tilføj under Medlemmer** **for at** føje medlemmer til sagen.

    Du kan også vælge at tilføje rollegrupper som medlemmer af en sag. Klik **på Tilføj** under **Rollegrupper**. Du kan kun tildele de rollegrupper, du er medlem af, til en sag. Det skyldes, at rollegrupper styrer, hvem der kan tildele medlemmer til en eDiscovery-sag.

4. På listen over personer eller rollegrupper, der kan tilføjes som medlemmer af sagen, skal du klikke til venstre for navnet på de personer (eller rollegrupper), du vil tilføje. Hvis du har en stor liste over personer eller rollegrupper, der kan tilføjes som medlemmer, skal  du bruge feltet Søg til at søge efter en bestemt person eller rollegruppe på listen.
  
5. Når du har valgt de personer eller rollegrupper, der skal tilføjes som medlemmer af sagen, skal du klikke på **Gem** for at gemme de nye medlemmer eller rollegrupper.

> [!IMPORTANT]
>
>- Hvis en rolle tilføjes eller fjernes fra en rollegruppe, du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller hvis rollegruppen er medlem af). Dette skyldes, at du beskytter din organisation mod utilsigtet at give ekstra tilladelser til medlemmer af en sag. På samme måde vil en rollegruppe, hvis den slettes, blive fjernet fra alle tilfælde, den var medlem af. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Som tidligere beskrevet er det kun en eDiscovery-administrator, der kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, heller ikke selvom brugeren har oprettet sagen.
>

## <a name="explore-the-core-ediscovery-workflow"></a>Udforsk den centrale eDiscovery-arbejdsproces

Her er en simpel arbejdsproces til oprettelse af eDiscovery-ventende indhold til personer af interesse, søgning efter indhold, der er relevant for din undersøgelse, og derefter eksport af disse data til yderligere gennemgang. I hvert af disse trin fremhæver vi også nogle udvidede Core eDiscovery-funktioner, som du kan udforske.

![Grundlæggende eDiscovery-arbejdsproces.](../media/CoreEdiscoveryWorkflow.png)

1. **[Opret en eDiscovery-venteposition](create-ediscovery-holds.md)**. Det første trin efter oprettelsen af en sag er at sætte en venteposition (også kaldet *en eDiscovery-venteposition*) på indholdsplaceringerne for personer med interesse i din undersøgelse. Indholdsplaceringer omfatter Exchange postkasser, SharePoint websteder, OneDrive konti og postkasser og websteder, der er knyttet Microsoft Teams og Microsoft 365 grupper. Selvom dette trin er valgfrit, bevarer oprettelse af en eDiscovery-venteposition indhold, der kan være relevant for sagen under undersøgelsen. Når du opretter en eDiscovery-venteposition, kan du bevare alt indhold på bestemte placeringer af indhold, eller du kan oprette en forespørgselsbaseret venteposition for kun at bevare det indhold, der svarer til en ventepositionsforespørgsel. Ud over at bevare indhold er en anden god grund til at oprette eDiscovery-ventepositioner at hurtigt søge på indholdsplaceringer i venteposition (i stedet for at skulle vælge hver placering at søge på), når du opretter og kører søgninger i næste trin. Når du har afsluttet undersøgelsen, kan du frigive den venteposition, du har oprettet.

2. **[Søge efter indhold](search-for-content-in-core-ediscovery.md)**. Når du har oprettet eDiscovery-ventepositioner, kan du bruge det indbyggede søgeværktøj til at søge på indholdsplaceringer i venteposition. Du kan også søge efter data, der kan være relevante for sagen, på andre indholdsplaceringer. Du kan oprette og køre forskellige søgninger, der er knyttet til sagen. Du bruger nøgleord, egenskaber og betingelser til at [](keyword-queries-and-search-conditions.md) opbygge søgeforespørgsler, der returnerer søgeresultater med de data, der er mest sandsynlige for sagen. Du kan også:

   - Få vist søgestatistik, som kan hjælpe dig med at indskrænke en søgeforespørgsel for at indsnævre resultaterne.

   - Få vist søgeresultaterne for hurtigt at bekræfte, om de relevante data bliver fundet.

   - Revyp en forespørgsel, og kør søgningen igen.

3. **[Eksportér og download søgeresultater](export-content-in-core-ediscovery.md)**. Når du søger efter og finder data, der er relevante for din undersøgelse, kan du eksportere dem ud af Office 365 til gennemgang af personer uden for undersøgelsesteamet. Eksport af data er en totrinsproces. Det første trin er at eksportere resultaterne af en søgning i tilfælde af, at de er Office 365. Dette opnås ved at kopiere resultaterne af en søgning til en microsoft-leveret Azure Storage placering. Det næste trin er at bruge værktøjet eDiscovery-eksport til at downloade indholdet til en lokal computer. Ud over de eksporterede datafiler indeholder eksportpakken en eksportrapport, en oversigtsrapport og en fejlrapport.
