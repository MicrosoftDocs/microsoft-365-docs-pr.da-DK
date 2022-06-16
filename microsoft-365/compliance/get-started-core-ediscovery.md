---
title: Kom i gang med eDiscovery-sager (Standard) i Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Beskriver, hvordan du kommer i gang med at bruge eDiscovery (Standard) i Microsoft Purview. Når du har tildelt eDiscovery-tilladelser og oprettet en sag, kan du tilføje medlemmer, oprette eDiscovery-ventepositioner og derefter søge efter og eksportere indhold, der er relevant for din undersøgelse.
ms.openlocfilehash: c8a3ca883191c450ebc20ddb555018b8b480199b
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115867"
---
# <a name="get-started-with-ediscovery-standard-in-microsoft-purview"></a>Kom i gang med eDiscovery (Standard) i Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eDiscovery (Standard) i Microsoft Purview indeholder et grundlæggende eDiscovery-værktøj, som organisationer kan bruge til at søge efter og eksportere indhold i Microsoft 365 og Office 365. Du kan også bruge eDiscovery (Standard) til at placere en eDiscovery-venteposition på indholdsplaceringer, f.eks. Exchange postkasser, SharePoint websteder, OneDrive konti og Microsoft Teams. Der kræves intet for at udrulle eDiscovery (Standard), men der er nogle forudsætningsopgaver, som en it-administrator og eDiscovery-chef skal udføre, før din organisation kan begynde at bruge eDiscovery (Standard) til at søge efter, eksportere og bevare indhold.

I denne artikel beskrives de trin, der er nødvendige for at konfigurere eDiscovery (Standard). Dette omfatter sikring af den korrekte licens, der kræves for at få adgang til eDiscovery (Standard), og placere eDiscovery-venteposition på indholdsplaceringer samt tildeling af tilladelser til it-, juridiske og undersøgelsesteamet, så de kan få adgang til og administrere sager. Denne artikel indeholder også en overordnet oversigt over, hvordan du bruger sager til at søge efter og eksportere indhold.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Trin 1: Bekræft og tildel relevante licenser

Licenser til eDiscovery (Standard) kræver det relevante organisationsabonnement og licenser pr. bruger.

- **Organisationsabonnement:** Hvis du vil have adgang til eDiscovery (Standard) i Microsoft Purview-compliance-portal og bruge ventepositions- og eksportfunktionerne, skal din organisation have et Exchange onlineabonnement på Plan 2 eller Microsoft 365 E3 eller Office 365 E3 abonnement eller nyere. Microsoft 365 Frontline-organisationer skal have et F5-abonnement.

- **Licenser pr. bruger:** Hvis du vil placere en eDiscovery-venteposition på postkasser og websteder, skal brugerne tildeles en af følgende licenser, afhængigt af dit organisationsabonnement:

  -  Exchange online Plan 2-licens

   ELLER
   
  - En Microsoft 365 E3 eller Office 365 E3 licens eller nyere

   ELLER

  - Office 365 E1 licens med en Exchange Online Plan 2- eller Exchange Online-arkivering-tilføjelsesprogramlicens

   ELLER

  - Microsoft 365 licens til Frontline F5 Compliance eller F5 Security & Compliance  

  OG

  - Office 365 E1 licens med en SharePoint Online Plan 2- eller OneDrive for Business Plan 2-tilføjelsesprogramlicens
  
  Du kan få oplysninger om, hvordan du tildeler licenser, under [Tildel licenser til brugere](../admin/manage/assign-licenses-to-users.md).

Du kan finde oplysninger og vejledning om sikkerhed og overholdelse af angivne standarder:

- Download og se afsnittet eDiscovery og overvågning i tabellen [Microsoft 365 Sammenligning](https://aka.ms/M365EnterprisePlans).

- Se [Microsoft 365 vejledning til overholdelse af & sikkerhed – tjenestebeskrivelser | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>Trin 2: Tildel eDiscovery-tilladelser

Hvis du vil have adgang til eDiscovery (Standard) eller tilføjes som medlem af en eDiscovery-sag (Standard), skal en bruger tildeles de relevante tilladelser. En bruger skal specifikt tilføjes som medlem af rollegruppen eDiscovery Manager på overholdelsesportalen. Medlemmer af denne rollegruppe kan oprette og administrere eDiscovery-sager (Standard). De kan tilføje og fjerne medlemmer, placere eDiscovery-venteposition på brugere, oprette og redigere søgninger og eksportere indhold fra en eDiscovery-sag (Standard).

Fuldfør følgende trin for at føje brugere til rollegruppen eDiscovery Manager:

1. Gå til overholdelsesportalen, og log på med legitimationsoplysningerne for en administratorkonto i din Microsoft 365 eller Office 365 organisation.

2. Vælg rollegruppen **eDiscovery Manager** på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a>.

3. Klik på **Rediger** ud for sektionen **eDiscovery Manager på eDiscovery Manager-pop** op-siden.

4. Klik på **Vælg registreringsstyring** på siden **Vælg eDiscovery Manager** i guiden Rediger rollegruppe.

5. Klik på **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen.

6. Klik på **Tilføj** for at tilføje de valgte brugere, og klik derefter på **Udført**.

7. Klik på **Gem** for at føje brugerne til rollegruppen, og klik derefter på **Luk** for at fuldføre trinnet.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Flere oplysninger om rollegruppen eDiscovery Manager

Der er to undergrupper i rollegruppen eDiscovery Manager. Forskellen mellem disse undergrupper er baseret på område.

- **eDiscovery Manager**: Kan få vist og administrere de eDiscovery-sager (Standard), de opretter eller er medlem af. Hvis en anden eDiscovery Manager opretter en sag, men ikke tilføjer endnu en eDiscovery Manager som medlem af denne sag, kan den anden eDiscovery Manager ikke få vist eller åbne sagen på siden eDiscovery (Standard) i Overholdelsescenter. Generelt kan de fleste personer i din organisation føjes til undergruppen eDiscovery Manager.

- **eDiscovery-administrator**: Kan udføre alle opgaver til sagsstyring, som en eDiscovery Manager kan udføre. En eDiscovery-administrator kan desuden:

  - Få vist alle sager, der er angivet på siden eDiscovery (Standard).
  
  - Administrer alle sager i organisationen, når de tilføjer sig selv som medlem af sagen.

  - Få adgang til og eksportér sagsdata for alle tilfælde i organisationen.
  
  - Fjern medlemmer fra en eDiscovery-sag. Det er kun en eDiscovery-administrator, der kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, selvom brugeren har oprettet sagen.

  På grund af det brede adgangsområde bør en organisation kun have nogle få administratorer, der er medlemmer af undergruppen eDiscovery-administratorer.

Du kan finde flere oplysninger om eDiscovery-tilladelser og en beskrivelse af hver rolle, der er tildelt til eDiscovery Manager-rollegruppen, under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-ediscovery-standard-case"></a>Trin 3: Opret en eDiscovery-sag (Standard)

Det næste trin er at oprette en sag og begynde at bruge eDiscovery (Standard). Udfør følgende trin for at oprette en sag og tilføje medlemmer. Den bruger, der opretter sagen, tilføjes automatisk som medlem.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> , og log på med legitimationsoplysningerne for en brugerkonto, der er tildelt de relevante eDiscovery-tilladelser. Medlemmer af rollegruppen Organisationsadministration kan også oprette eDiscovery-sager (Standard).

2. Klik på **Vis alle** i navigationsruden til venstre på overholdelsesportalen, og klik derefter på **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**Core**</a>.

3. Klik på **Opret en sag** på siden **eDiscovery (Standard**).

4. På siden **Nyt case-vindue** skal du give sagen et navn (obligatorisk) og derefter skrive en valgfri beskrivelse. Sagsnavnet skal være entydigt i din organisation.

5. Klik på **Gem** for at oprette sagen.

   Den nye sag oprettes og vises på siden eDiscovery (Standard). Du skal muligvis klikke på **Opdater** for at få vist den nye sag.

## <a name="step-4-optional-add-members-to-a-ediscovery-standard-case"></a>Trin 4 (valgfrit): Føj medlemmer til en eDiscovery-sag (Standard)

Hvis du opretter en sag i trin 3, og du er den eneste person, der skal bruge sagen, behøver du ikke at udføre dette trin. Du kan begynde at bruge sagen til at oprette eDiscovery-ventepositioner, søge efter indhold og eksportere søgeresultater. Udfør dette trin, hvis du vil give andre brugere (eller rollegruppen) adgang til sagen.

1. Klik på navnet på den sag, du vil føje medlemmer til, på siden **eDiscovery (Standard)** på overholdelsesportalen.

2. På startsiden for sagen skal du vælge fanen **Indstillinger** og derefter vælge **Adgang & tilladelser**.

3. På pop **op-vinduet Adgang & tilladelser** under **Medlemmer** skal du klikke på **Tilføj** for at føje medlemmer til sagen.

    Du kan også vælge at tilføje rollegrupper som medlemmer af en sag. Klik på **Tilføj** under **Rollegrupper**. Du kan kun tildele de rollegrupper, du er medlem af, til en sag. Det skyldes, at rollegrupper styrer, hvem der kan tildele medlemmer til en eDiscovery-sag.

4. På listen over personer eller rollegrupper, der kan tilføjes som medlemmer af sagen, skal du klikke til venstre for navnet på de personer (eller rollegrupper), du vil tilføje. Hvis du har en stor liste over personer eller rollegrupper, der kan tilføjes som medlemmer, kan du **bruge søgefeltet** til at søge efter en bestemt person eller rollegruppe på listen.
  
5. Når du har valgt de personer eller rollegrupper, der skal tilføjes som medlemmer af sagen, skal du klikke på **Gem** for at gemme de nye medlemmer eller rollegrupper.

> [!IMPORTANT]
>
>- Hvis en rolle tilføjes eller fjernes fra en rollegruppe, som du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller i alle tilfælde rollegruppen er medlem af). Årsagen til dette er at beskytte din organisation mod utilsigtet at give yderligere tilladelser til medlemmer af en sag. Hvis en rollegruppe slettes, fjernes den på samme måde fra alle de sager, den var medlem af. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Som tidligere forklaret er det kun en eDiscovery-administrator, der kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, selvom brugeren har oprettet sagen.
>

## <a name="explore-the-ediscovery-standard-workflow"></a>Udforsk eDiscovery-arbejdsprocessen (Standard)

Her er en enkel arbejdsproces, hvor du kan oprette eDiscovery-ventepositioner for interessante personer, søge efter indhold, der er relevant for din undersøgelse, og derefter eksportere dataene til yderligere gennemgang. I hvert af disse trin fremhæver vi også nogle udvidede funktioner i eDiscovery (Standard), som du kan udforske.

![eDiscovery-arbejdsproces (Standard).](../media/CoreEdiscoveryWorkflow.png)

1. **[Opret en eDiscovery-venteposition](create-ediscovery-holds.md)**. Det første trin, når du har oprettet en sag, er at placere en venteposition (også kaldet *eDiscovery-venteposition*) på indholdsplaceringerne for de personer, der er interesseret i din undersøgelse. Indholdsplaceringer omfatter Exchange postkasser, SharePoint websteder, OneDrive konti og de postkasser og websteder, der er knyttet til Microsoft Teams og Microsoft 365-grupper. Selvom dette trin er valgfrit, bevarer oprettelse af eDiscovery-venteposition indhold, der kan være relevant for sagen under undersøgelsen. Når du opretter en eDiscovery-venteposition, kan du bevare alt indhold på bestemte indholdsplaceringer, eller du kan oprette en forespørgselsbaseret venteposition for kun at bevare det indhold, der svarer til en ventepositionsforespørgsel. Ud over at bevare indhold er en anden god grund til at oprette eDiscovery-ventepositioner hurtigt at søge efter indholdsplaceringer i venteposition (i stedet for at skulle vælge hver placering, der skal søges efter), når du opretter og kører søgninger i næste trin. Når du har fuldført din undersøgelse, kan du frigive enhver venteposition, du har oprettet.

2. **[Søg efter indhold](search-for-content-in-core-ediscovery.md)**. Når du har oprettet eDiscovery-ventepositioner, skal du bruge det indbyggede søgeværktøj til at søge efter indholdsplaceringer i venteposition. Du kan også søge på andre indholdsplaceringer efter data, der kan være relevante for sagen. Du kan oprette og køre forskellige søgninger, der er knyttet til sagen. Du kan bruge nøgleord, egenskaber og betingelser til at [oprette søgeforespørgsler](keyword-queries-and-search-conditions.md) , der returnerer søgeresultater med de data, der er mest relevante for sagen. Du kan også:

   - Få vist søgestatistik, der kan hjælpe dig med at afgrænse en søgeforespørgsel for at indsnævre resultaterne.

   - Gennemse søgeresultaterne for hurtigt at kontrollere, om de relevante data findes.

   - Rediger en forespørgsel, og kør søgningen igen.

3. **[Eksportér og download søgeresultater](export-content-in-core-ediscovery.md)**. Når du har søgt efter og fundet data, der er relevante for din undersøgelse, kan du eksportere dem ud af Office 365 til gennemsyn af personer uden for undersøgelsesteamet. Eksport af data er en proces med to trin. Det første trin er at eksportere resultaterne af en søgning i tilfælde af Office 365. Dette opnås ved at kopiere resultaterne af en søgning til en Microsoft-leveret Azure Storage placering. Det næste trin er at bruge værktøjet eDiscovery-eksport til at downloade indholdet til en lokal computer. Ud over de eksporterede datafiler indeholder eksportpakken en eksportrapport, en oversigtsrapport og en fejlrapport.
