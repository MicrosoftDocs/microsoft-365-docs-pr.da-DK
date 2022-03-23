---
title: Søge efter indhold i en grundlæggende eDiscovery-sag
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
search.appverid:
- MOE150
- MET150
description: Søg efter indhold, der kan være relevant for en core eDiscovery-sag.
ms.openlocfilehash: 57ea95458df568de3687e1b0d38a70991b09a850
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/30/2021
ms.locfileid: "63588411"
---
# <a name="search-for-content-in-a-core-ediscovery-case"></a>Søge efter indhold i en core eDiscovery-sag

Når der oprettes en central eDiscovery-sag, og personer af interesse i sagen er sat i venteposition, kan du oprette og køre en eller flere søgninger efter indhold, der er relevant for sagen. Søgninger, der er knyttet til en core eDiscovery-sag, er ikke  angivet på siden Indholdssøgning i Microsoft 365 Overholdelsescenter. Disse søgninger er angivet på **søgesiden i det** centrale eDiscover-tilfælde, som søgninger er knyttet til. Det betyder også, at søgninger, der er knyttet til en sag, kun kan åbnes af sagsmedlemmer.

Sådan opretter du en core eDiscovery-søgning:
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne til brugerkontoen, som har fået tildelt de relevante eDiscovery-tilladelser og er medlem af sagen.

2. Klik på Vis Microsoft 365 Overholdelsescenter navigationsruden i venstre navigationsrude **, og** klik derefter på **eDiscovery > Core**.

3. På siden **Kerne eDiscovery skal** du vælge den sag, du vil oprette en tilknyttet søgning for, og derefter klikke på **Åbn sag**.

4. På **startsiden** for sagen skal du klikke på **fanen Søgninger** og derefter klikke på **Ny søgning**.

   ![Klik på Ny søgning for at oprette en Core eDiscovery-søgning.](../media/CoreeDiscoverySearch1.png)

5. I guiden **Ny søgning** skal du skrive et navn til søgningen og en valgfri beskrivelse, der hjælper med at identificere søgningen. Navnet på søgningen skal være entydigt i din organisation.

6. På siden **Placeringer skal** du vælge de indholdsplaceringer, du vil søge efter. Du kan søge i postkasser, websteder og offentlige mapper.

    ![Vælg de indholdsplaceringer, der skal være i venteposition.](../media/ContentSearchLocations.png)
  
   1. **Exchange postkasser**: Indstil til/fra-knappen  til Til, og klik derefter på Vælg brugere, grupper eller teams for at angive **,** hvilke postkasser der skal være i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition i gruppemedlemmers postkasser) for at placere dem i venteposition. Du kan også søge i den postkasse, der er knyttet til et Microsoft-team (efter kanalmeddelelser Office 365 gruppen og Yammer gruppe. Du kan finde flere oplysninger om de programdata, der er gemt i postkasser, [under Indhold, der er gemt i postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til Til, og klik derefter  på Vælg websteder for at angive, SharePoint-websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til SharePoint for et Microsoft-team, en Office 365-gruppe eller Yammer gruppe.
  
   3. **Exchange offentlige mapper**: Sæt til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Slå til/fra-knappen fra, hvis du ikke vil sætte offentlige mapper i venteposition.
  
   4. Sørg for, at dette afkrydsningsfelt er markeret for Teams efter indhold i det lokale miljø. Hvis du f.eks. søger i alle Exchange-postkasser i organisationen, og dette afkrydsningsfelt er markeret, medtages det skybaserede lager, der bruges til at gemme Teams-chatdata for lokale brugere, i søgeområdet. Du kan finde flere [oplysninger i Teams oplysninger om chatsamtaler for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

7. Skriv en **nøgleordsforespørgsel på siden Definer** dine søgebetingelser, og føj betingelser til søgeforespørgslen, hvis det er nødvendigt.

   ![Konfigurer søgeforespørgslen.](../media/ContentSearchQuery.png)

   1. Angiv nøgleord, meddelelsesegenskaber som f.eks. datoerne sendt og modtaget, eller dokumentegenskaber som filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. **OG**, **ELLER**, **IKKE** og **I NÆRHEDEN**. Hvis du lader feltet nøgleord være tomt, medtages alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne. Få mere at vide under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

   2. Alternativt kan du klikke på afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord i hver række. Hvis du gør dette, forbindes nøgleordene i hver række af en logisk operator (**c:s**), der i funktionaliteten svarer til **ELLER-operatoren** i den søgeforespørgsel, der oprettes.

      Hvorfor bruge listen over nøgleord? Du kan få vist statistik, der viser, hvor mange elementer der svarer til hvert nøgleord. Dette kan hjælpe dig med hurtigt at identificere, hvilke nøgleord der er mest (og mindst) effektive. Du kan også bruge et nøgleordsudtryk (omgivet af parenteser) i en række. Du kan finde flere oplysninger om nøgleordslisten og søgestatistik [i Få nøgleordsstatistik for søgninger](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > For at reducere problemer, der skyldes lister med store nøgleord, er du begrænset til maksimalt 20 rækker på listen med nøgleord.

   3. Du kan tilføje søgebetingelser for at indsnævre en søgning og returnere et mere elegant sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i feltet nøgleord) af en logisk operator (**c:c**), der svarer i funktionalitet til **og-operatoren** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser, der skal medtages i resultaterne. Det er sådan, betingelser kan hjælpe dig med at indsnævre dine resultater. Du kan finde en liste og beskrivelse af betingelser, du kan bruge i en søgeforespørgsel, under [Søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).

8. Gennemse søgeindstillingerne (og rediger om nødvendigt), og send derefter søgningen for at starte den.

Når søgningen er fuldført, kan du få vist søgeresultaterne. Hvis det er nødvendigt, **skal du klikke** på **Opdater på siden Søgninger** for at få vist den søgning, du har oprettet.

## <a name="more-information-about-searching-content-locations"></a>Flere oplysninger om søgning af indholdsplaceringer

- Når du klikker **på Vælg brugere, grupper eller teams** for at angive postkasser, der skal søges i, er postkassevælgeren, der vises, tom. Dette er med henblik på at forbedre ydeevnen. Hvis du vil føje modtagere til denne liste, skal du klikke på Vælg brugere, grupper eller **teams**, skrive et navn (mindst tre tegn) i søgefeltet, markere afkrydsningsfeltet ud for navnet og derefter klikke på **Vælg**.

- Du kan føje inaktive postkasser, Microsoft Teams, Yammer grupper, Office 365-grupper og distributionsgrupper til listen over postkasser, der skal søges i. Dynamiske distributionsgrupper understøttes ikke. Hvis du tilføjer Microsoft Teams, Yammer Groups eller Office 365 Groups, søges der i gruppen eller teampostkassen. Der søges ikke i gruppemedlemmers postkasser.

- Hvis du vil føje websteder til søgningen, skal du slå til/fra-knappen til og derefter klikke **på Vælg websteder**. Skriv URL-adressen for hvert websted, du vil søge efter. Du kan også tilføje URL-adressen til SharePoint for et Microsoft-team, en Yammer-gruppe eller en Office 365 gruppe.
