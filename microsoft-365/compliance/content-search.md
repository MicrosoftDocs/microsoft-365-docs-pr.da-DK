---
title: Opret og kør en indholdssøgning på Microsoft Purview-overholdelsesportalen
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Brug eDiscovery-værktøjet til indholdssøgning i Overholdelsescenter til at søge efter indhold i forskellige Microsoft 365 tjenester.
ms.openlocfilehash: 90b1ce142b5d629be86ba058071af906485e765f
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231709"
---
# <a name="create-a-content-search"></a>Opret en indholdssøgning

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge eDiscovery-værktøjet til indholdssøgning på Microsoft Purview-overholdelsesportalen til at søge efter indhold på stedet, f.eks. mail, dokumenter og chatsamtaler i din organisation. Brug dette værktøj til at søge efter indhold i disse skybaserede Microsoft 365 datakilder:
  
- Exchange Online postkasser

- SharePoint onlinewebsteder og OneDrive for Business konti

- Microsoft Teams

- Microsoft 365-grupper

- Yammer grupper

Når du har kørt en søgning, vises antallet af indholdsplaceringer og et anslået antal søgeresultater på søgevinduet. Du kan hurtigt få vist statistikker, f.eks. de indholdsplaceringer, der har flest elementer, der svarer til søgeforespørgslen. Når du har kørt en søgning, kan du få vist resultaterne eller eksportere dem til en lokal computer.

## <a name="before-you-run-a-search"></a>Før du kører en søgning

- Hvis du vil have adgang til indholdssøgeværktøjet på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> (for at køre søgninger og få vist resultater og eksportere resultater), skal en administrator, overholdelsesofficer eller eDiscovery-leder være medlem af rollegruppen eDiscovery Manager i overholdelsesportalen. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- I en Exchange hybridinstallation kan du ikke bruge søgeværktøjet Indhold til at søge efter mails i postkasser i det lokale miljø. Du kan kun bruge værktøjet til at søge i skybaserede postkasser.

- I en Exchange hybridinstallation kan du søge efter Teams chatdata i postkasser i det lokale miljø. Du kan få flere oplysninger under [Teams chatdata for brugere i det lokale miljø](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users?view=o365-worldwide).

## <a name="create-and-run-a-search"></a>Opret og kør en søgning
  
1. Gå til , <https://compliance.microsoft.com> og log på ved hjælp af legitimationsoplysningerne for en konto, der er tildelt de relevante tilladelser.

2. Klik på **Indholdssøgning** i navigationsruden til venstre på overholdelsesportalen.

3. Klik på **Ny søgning** på siden **Indholdssøgning**.

4. Skriv et navn til søgningen. En valgfri beskrivelse, der hjælper med at identificere søgningen. Navnet på søgningen skal være entydigt i din organisation.

5. Vælg de **indholdsplaceringer** , du vil søge efter, på siden Placeringer. Du kan søge i postkasser, websteder og offentlige mapper.

    ![Vælg de indholdsplaceringer, der skal placeres i venteposition.](../media/ContentSearchLocations.png)
  
   1. **Exchange postkasser**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg brugere, grupper eller teams** for at angive de postkasser, der skal sættes i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper. Du kan også søge i den postkasse, der er knyttet til et Microsoft-team (efter kanalmeddelelser), Office 365 gruppe og Yammer gruppe. Du kan finde flere oplysninger om de programdata, der er gemt i postkasser, [under Indhold, der er gemt i postkasser til eDiscovery](what-is-stored-in-exo-mailbox.md).

   2. **SharePoint websteder**: Angiv til/fra-knappen til **Til**, og klik derefter på **Vælg websteder** for at angive, SharePoint websteder og OneDrive konti, der skal sættes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til det SharePoint websted for et Microsoft-team, en Office 365-gruppe eller en Yammer-gruppe.
  
   3. **Exchange offentlige mapper**: Indstil til/fra-knappen til **Til** for at sætte alle offentlige mapper i din Exchange Online organisation i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-knappen være slået fra, hvis du ikke vil sætte offentlige mapper i venteposition.
  
   4. Markér dette afkrydsningsfelt for at søge efter Teams indhold til brugere i det lokale miljø. Hvis du f.eks. søger i alle Exchange postkasser i organisationen, og dette afkrydsningsfelt er markeret, medtages det skybaserede lager, der bruges til at gemme Teams chatdata for brugere i det lokale miljø, i søgeområdet. Du kan finde flere oplysninger under [Søg efter Teams chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

6. På siden **Definer dine søgebetingelser** skal du skrive en nøgleordsforespørgsel og føje betingelser til søgeforespørgslen, hvis det er nødvendigt.

   ![Konfigurer søgeforespørgslen.](../media/ContentSearchQuery.png)

   1. Angiv nøgleord, meddelelsesegenskaber, f.eks. datoer for afsendelse og modtagelse, eller dokumentegenskaber, f.eks. filnavne eller den dato, hvor et dokument sidst blev ændret. Du kan bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks **. AND**, **OR**, **NOT** og **NEAR**. Hvis du lader nøgleordsfeltet være tomt, medtages alt indhold, der er placeret på de angivne indholdsplaceringer, i søgeresultaterne. Du kan finde flere oplysninger under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

   2. Du kan også klikke på afkrydsningsfeltet **Vis nøgleordsliste** og skrive et nøgleord i hver række. Hvis du gør dette, forbindes nøgleordene på hver række af en logisk operator (**c:s**), der har samme funktionalitet som operatoren **OR** i den søgeforespørgsel, der er oprettet.

      Hvorfor bruge nøgleordslisten? Du kan få statistikker, der viser, hvor mange elementer der matcher hvert nøgleord. Dette kan hjælpe dig med hurtigt at identificere, hvilke nøgleord der er de mest (og mindst) effektive. Du kan også bruge et nøgleordsudtryk (omgivet af parenteser) i en række. Du kan finde flere oplysninger om nøgleordslisten og søgestatistikken under [Hent nøgleordsstatistik for søgninger](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches).

      > [!NOTE]
      > For at hjælpe med at reducere problemer, der skyldes store nøgleordslister, er du begrænset til maksimalt 20 rækker på listen over nøgleord.

   3. Du kan tilføje søgebetingelser for at indsnævre en søgning og returnere et mere raffineret sæt resultater. Hver betingelse føjer en delsætning til den søgeforespørgsel, der oprettes og køres, når du starter søgningen. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i nøgleordsfeltet) af en logisk operator (**c:c**), der har samme funktionalitet som **AND-operatoren** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og en eller flere betingelser for at blive inkluderet i resultaterne. Sådan hjælper betingelser med at indsnævre dine resultater. Du kan finde en liste over og en beskrivelse af de betingelser, du kan bruge i en søgeforespørgsel, under [Søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions).

7. Gennemse søgeindstillingerne (og rediger om nødvendigt), og send derefter søgningen for at starte den.
  
Hvis du vil have adgang til denne indholdssøgning igen eller få adgang til andre indholdssøgninger, der er angivet på siden **Indholdssøgning** , skal du markere søgningen og derefter klikke på **Åbn**.

## <a name="next-steps"></a>Næste trin

Her er en liste over de næste trin, du skal udføre, når du har oprettet og kørt en indholdssøgning.

- [Vis søgeresultater](preview-ediscovery-search-results.md)

- [Vis statistik for søgeresultater](view-keyword-statistics-for-content-search.md)

- [Eksportér søgeresultater](export-search-results.md)

- [Eksportér en søgerapport](export-a-content-search-report.md)

## <a name="more-information"></a>Flere oplysninger

Du kan finde flere oplysninger om indholdssøgning, f.eks. søgning efter indhold i forskellige Microsoft 365 tjenester, under [Reference til funktion for indholdssøgning](content-search-reference.md).
