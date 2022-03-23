---
title: Opret og kør en indholdssøgning i Microsoft 365 Overholdelsescenter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Brug værktøjet eDiscovery til indholdssøgning i overholdelsescenteret til at søge efter indhold i Microsoft 365 tjenester.
ms.openlocfilehash: 68270466625cc5f9b76359ae7697536956c727aa
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/30/2021
ms.locfileid: "63589114"
---
# <a name="create-a-content-search"></a>Oprette en indholdssøgning

Du kan bruge værktøjet eDiscovery-indholdssøgning i Microsoft 365 Overholdelsescenter til at søge efter direkte indhold som f.eks. mails, dokumenter og chatsamtaler i din organisation. Brug dette værktøj til at søge efter indhold i disse skybaserede Microsoft 365 datakilder:
  
- Exchange Online postkasser

- SharePoint Onlinewebsteder og -OneDrive for Business-konti

- Microsoft Teams

- Microsoft 365 grupper

- Yammer grupper

Når du har kørt en søgning, vises antallet af placeringer af indhold og et anslået antal søgeresultater på pop op-siden med søgninger. Du kan hurtigt få vist statistik, f.eks. de indholdsplaceringer, der har de fleste elementer, der svarer til søgeforespørgslen. Når du har kørt en søgning, kan du få vist resultaterne eller eksportere dem til en lokal computer.

## <a name="before-you-run-a-search"></a>Før du kører en søgning

- For at få adgang til værktøjet Indholdssøgning i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> (for at køre søgninger og få vist resultater og eksportere resultater), skal en administrator, compliance officer eller eDiscovery-leder være medlem af rollegruppen eDiscovery Manager i Microsoft 365 Overholdelsescenter. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- I en Exchange-hybridinstallation kan du ikke bruge værktøjet Indholdssøgning til at søge i lokale postkasser. Du kan kun bruge værktøjet til at søge i skybaserede postkasser.

## <a name="create-and-run-a-search"></a>Opret og kør en søgning
  
1. Gå til <https://compliance.microsoft.com> og log på med legitimationsoplysningerne for en konto, der er blevet tildelt de relevante tilladelser.

2. Klik på Indholdssøgning i venstre navigationsrude Microsoft 365 Overholdelsescenter **navigationsruden**.

3. Klik på **Ny søgning** på siden **Indholdssøgning**.

4. Skriv et navn til søgningen, en valgfri beskrivelse, der hjælper med at identificere søgningen. Navnet på søgningen skal være entydigt i din organisation.

5. På siden **Placeringer skal** du vælge de indholdsplaceringer, du vil søge efter. Du kan søge i postkasser, websteder og offentlige mapper.

    ![Vælg de indholdsplaceringer, der skal være i venteposition.](../media/ContentSearchLocations.png)
  
   1. **Exchange postkasser**: Indstil til/fra-knappen  til Til, og klik derefter på Vælg brugere, grupper eller teams for at angive **,** hvilke postkasser der skal være i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper. Du kan også søge i den postkasse, der er knyttet til et Microsoft-team (efter kanalmeddelelser Office 365 gruppen og Yammer gruppe. Du kan finde flere oplysninger om de programdata, der er gemt i postkasser, [under Indhold, der er gemt i postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til Til, og klik derefter  på Vælg websteder for at angive, SharePoint-websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til SharePoint for et Microsoft-team, en Office 365-gruppe eller Yammer gruppe.
  
   3. **Exchange offentlige mapper**: Sæt til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Slå til/fra-knappen fra, hvis du ikke vil sætte offentlige mapper i venteposition.
  
   4. Sørg for, at dette afkrydsningsfelt er markeret for Teams efter indhold i det lokale miljø. Hvis du f.eks. søger i alle Exchange-postkasser i organisationen, og dette afkrydsningsfelt er markeret, medtages det skybaserede lager, der bruges til at gemme Teams-chatdata for lokale brugere, i søgeområdet. Du kan finde flere [oplysninger i Teams oplysninger om chatsamtaler for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

6. Skriv en **nøgleordsforespørgsel på siden Definer** dine søgebetingelser, og føj betingelser til søgeforespørgslen, hvis det er nødvendigt.

   ![Konfigurer søgeforespørgslen.](../media/ContentSearchQuery.png)

   1. Angiv nøgleord, meddelelsesegenskaber som f.eks. datoerne sendt og modtaget, eller dokumentegenskaber som filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. **OG**, **ELLER**, **IKKE** og **I NÆRHEDEN**. Hvis du lader feltet nøgleord være tomt, medtages alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne. Få mere at vide under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

   2. Alternativt kan du klikke på afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord i hver række. Hvis du gør dette, forbindes nøgleordene i hver række af en logisk operator (**c:s**), der i funktionaliteten svarer til **ELLER-operatoren** i den søgeforespørgsel, der oprettes.

      Hvorfor bruge listen over nøgleord? Du kan få vist statistik, der viser, hvor mange elementer der svarer til hvert nøgleord. Dette kan hjælpe dig med hurtigt at identificere, hvilke nøgleord der er mest (og mindst) effektive. Du kan også bruge et nøgleordsudtryk (omgivet af parenteser) i en række. Du kan finde flere oplysninger om nøgleordslisten og søgestatistik [i Få nøgleordsstatistik for søgninger](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > For at reducere problemer, der skyldes lister med store nøgleord, er du begrænset til maksimalt 20 rækker på listen med nøgleord.

   3. Du kan tilføje søgebetingelser for at indsnævre en søgning og returnere et mere elegant sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i feltet nøgleord) af en logisk operator (**c:c**), der svarer i funktionalitet til **og-operatoren** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser, der skal medtages i resultaterne. Det er sådan, betingelser kan hjælpe dig med at indsnævre dine resultater. Du kan finde en liste og beskrivelse af betingelser, du kan bruge i en søgeforespørgsel, under [Søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).

7. Gennemse søgeindstillingerne (og rediger om nødvendigt), og send derefter søgningen for at starte den.
  
Hvis du vil have adgang til denne indholdssøgning igen eller få adgang til  andre indholdssøgninger, der er angivet på siden Indholdssøgning, skal du vælge søgningen og derefter klikke på **Åbn**.

## <a name="next-steps"></a>Næste trin

Her er en liste over de næste trin, du skal udføre, når du har oprettet og kørt en indholdssøgning.

- [Få vist søgeresultater](preview-ediscovery-search-results.md)

- [Få vist statistik for søgeresultater](view-keyword-statistics-for-content-search.md)

- [Eksportér søgeresultater](export-search-results.md)

- [Eksportér en søgerapport](export-a-content-search-report.md)

## <a name="more-information"></a>Flere oplysninger

Du kan finde flere oplysninger om indholdssøgning, f.eks. søgning efter indhold Microsoft 365 forskellige tjenester, under [Funktionsreference til indholdssøgning](content-search-reference.md).
