---
title: Søg efter indhold i en eDiscovery-sag (Standard)
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
search.appverid:
- MOE150
- MET150
description: Søg efter indhold, der kan være relevant for en eDiscovery-sag (Standard).
ms.openlocfilehash: 372f8beba2567c24e8af75acf4d11e3fe6220f2c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090401"
---
# <a name="search-for-content-in-a-ediscovery-standard-case"></a>Søg efter indhold i en eDiscovery-sag (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når der er oprettet en Microsoft Purview eDiscovery (Standard)-sag, og personer af interesse for sagen er sat i venteposition, kan du oprette og køre en eller flere søgninger efter indhold, der er relevant for sagen. Søgninger, der er knyttet til en eDiscovery-sag (Standard), vises ikke på siden **Indholdssøgning** på Microsoft Purview-overholdelsesportalen. Disse søgninger vises på siden **Søgninger** i eDiscover-kernecasen, som søgninger er knyttet til. Det betyder også, at sagsmedlemmer kun kan få adgang til søgninger, der er knyttet til en sag.

Sådan opretter du en eDiscovery-søgning (Standard):
  
1. Gå til , <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for den brugerkonto, der er tildelt de relevante eDiscovery-tilladelser, og som er medlem af sagen.

2. Klik på **Vis alle** i navigationsruden til venstre på overholdelsesportalen, og klik derefter på **eDiscovery > Core**.

3. På siden **eDiscovery (Standard)** skal du vælge den sag, du vil oprette en tilknyttet søgning, og derefter klikke på **Åbn sag**.

4. Klik **på fanen** **Søgninger** på startsiden for sagen, og klik derefter på **Ny søgning**.

   ![Klik på Ny søgning for at oprette en eDiscovery-søgning (Standard).](../media/CoreeDiscoverySearch1.png)

5. I guiden **Ny søgning** skal du skrive et navn til søgningen og en valgfri beskrivelse, der hjælper med at identificere søgningen. Navnet på søgningen skal være entydigt i din organisation.

6. Vælg de **indholdsplaceringer** , du vil søge efter, på siden Placeringer. Du kan søge i postkasser, websteder og offentlige mapper.

    ![Vælg de indholdsplaceringer, der skal placeres i venteposition.](../media/ContentSearchLocations.png)
  
   1. **Exchange postkasser**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg brugere, grupper eller teams** for at angive de postkasser, der skal sættes i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition på gruppemedlemmernes postkasser) til at placere dem i venteposition. Du kan også søge i den postkasse, der er knyttet til et Microsoft-team (efter kanalmeddelelser), Office 365 gruppe og Yammer gruppe. Du kan finde flere oplysninger om de programdata, der er gemt i postkasser, [under Indhold, der er gemt i postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg websteder** for at angive, SharePoint websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til det SharePoint websted for et Microsoft-team, en Office 365-gruppe eller en Yammer-gruppe.
  
   3. **Exchange offentlige mapper**: Indstil til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online organisation i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-knappen være slået fra, hvis du ikke vil sætte offentlige mapper i venteposition.
  
   4. Markér dette afkrydsningsfelt for at søge efter Teams indhold til brugere i det lokale miljø. Hvis du f.eks. søger i alle Exchange postkasser i organisationen, og dette afkrydsningsfelt er markeret, medtages det skybaserede lager, der bruges til at gemme Teams chatdata for brugere i det lokale miljø, i søgeområdet. Du kan finde flere oplysninger under [Søg efter Teams chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

7. På siden **Definer dine søgebetingelser** skal du skrive en nøgleordsforespørgsel og føje betingelser til søgeforespørgslen, hvis det er nødvendigt.

   ![Konfigurer søgeforespørgslen.](../media/ContentSearchQuery.png)

   1. Angiv nøgleord, meddelelsesegenskaber, f.eks. datoer for afsendelse og modtagelse, eller dokumentegenskaber, f.eks. filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks **. AND**, **OR**, **NOT** og **NEAR**. Hvis du lader nøgleordsfeltet være tomt, medtages alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne. Du kan finde flere oplysninger under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

   2. Du kan også klikke på afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord i hver række. Hvis du gør dette, forbindes nøgleordene på hver række af en logisk operator (**c:s**), der har samme funktionalitet som operatoren **OR** i den søgeforespørgsel, der er oprettet.

      Hvorfor bruge nøgleordslisten? Du kan få statistikker, der viser, hvor mange elementer der matcher hvert nøgleord. Dette kan hjælpe dig med hurtigt at identificere, hvilke nøgleord der er de mest (og mindst) effektive. Du kan også bruge et nøgleordsudtryk (omgivet af parenteser) i en række. Du kan finde flere oplysninger om nøgleordslisten og søgestatistikken under [Hent nøgleordsstatistik for søgninger](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > For at hjælpe med at reducere problemer, der skyldes store nøgleordslister, er du begrænset til maksimalt 20 rækker på listen over nøgleord.

   3. Du kan tilføje søgebetingelser for at indsnævre en søgning og returnere et mere raffineret sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i nøgleordsfeltet) af en logisk operator (**c:c**), der har samme funktionalitet som **AND-operatoren** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser for at blive inkluderet i resultaterne. Sådan hjælper betingelser med at indsnævre dine resultater. Du kan finde en liste over og en beskrivelse af de betingelser, du kan bruge i en søgeforespørgsel, under [Søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).

8. Gennemse søgeindstillingerne (og rediger om nødvendigt), og send derefter søgningen for at starte den.

Når søgningen er fuldført, kan du få vist søgeresultaterne. Hvis det er nødvendigt, skal du klikke på **Opdater** på siden **Søgninger** for at få vist den søgning, du har oprettet.

## <a name="more-information-about-searching-content-locations"></a>Flere oplysninger om søgning efter indholdsplaceringer

- Når du klikker på **Vælg brugere, grupper eller teams** for at angive postkasser, der skal søges i, er den postkassevælger, der vises, tom. Dette er tilsigtet for at forbedre ydeevnen. Hvis du vil føje modtagere til denne liste, skal du klikke på **Vælg brugere, grupper eller teams**, skrive et navn (mindst tre tegn) i søgefeltet, markere afkrydsningsfeltet ud for navnet og derefter klikke på **Vælg**.

- Du kan føje inaktive postkasser, Microsoft Teams, Yammer Grupper, Office 365 Grupper og distributionsgrupper til listen over postkasser, der skal søges i. Dynamiske distributionsgrupper understøttes ikke. Hvis du tilføjer Microsoft Teams, Yammer grupper eller Office 365 grupper, søges der i gruppens eller teampostkassen. Der søges ikke i gruppemedlemmernes postkasser.

- Hvis du vil føje websteder til søgningen, skal du slå til/fra-knappen til og derefter klikke på **Vælg websteder**. Skriv URL-adressen for hvert websted, du vil søge efter. Du kan også tilføje URL-adressen til det SharePoint websted for et Microsoft-team, en Yammer-gruppe eller en Office 365 gruppe.
