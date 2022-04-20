---
title: Søg efter Teams-chatdata for brugere i det lokale miljø
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MST160
- MET150
ms.assetid: 3f7dde1a-a8ea-4366-86da-8ee6777f357c
description: Administratorer kan bruge eDiscovery-værktøjer i Microsoft 365 til at søge efter og eksportere Teams chatdata til brugere i det lokale miljø i en Exchange hybridinstallation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7b77a5178237e7ae25f710c8cc9574449f67a4f2
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945863"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Søg efter Teams-chatdata for brugere i det lokale miljø

Hvis organisationen har en Exchange hybridinstallation (eller din organisation synkroniserer en Exchange organisation i det lokale miljø med Office 365) og har aktiveret Microsoft Teams, kan brugere i det lokale miljø bruge Teams chatprogrammet til chat. For en skybaseret bruger gemmes Teams chatdata (også kaldet *1x1- eller 1xN-chats*) i deres primære skybaserede postkasse. Når en bruger i det lokale miljø bruger Teams chatprogrammet, kan vedkommendes chatbeskeder ikke gemmes i deres primære postkasse, som er placeret i det lokale miljø. For at omgå denne begrænsning har Microsoft udgivet en ny funktion, hvor der oprettes et skybaseret lagerområde, så du bruger eDiscovery-værktøjer til at søge efter og eksportere Teams chatdata til brugere i det lokale miljø.
  
Her er kravene og begrænsningerne for aktivering af cloudbaseret lager for brugere i det lokale miljø:
  
- Brugerkontiene i katalogtjenesten i det lokale miljø (f.eks. Active Directory) skal synkroniseres med Azure Active Directory, katalogtjenesten i Microsoft 365. Det betyder, at der oprettes en mailbrugerkonto i Microsoft 365 og er knyttet til en bruger, hvis primære postkasse er placeret i organisationen i det lokale miljø.

- Den bruger, hvis primære postkasse er placeret i organisationen i det lokale miljø, skal tildeles en Microsoft Teams licens og mindst en Exchange Online Plan 1-licens.

- Hvis din organisation ikke har en Exchange hybridinstallation, skal du synkronisere skemaet for Exchange i det lokale miljø for at Azure Active Directory. Hvis du ikke gør dette, kan du risikere at oprette duplikerede skybaserede postkasser i Exchange Online for brugere, der har en postkasse i din lokale Exchange organisation.

- Det er kun de Teams chatdata, der er knyttet til en bruger i det lokale miljø, der gemmes i det cloudbaserede lagerområde. En bruger i det lokale miljø kan ikke få adgang til dette lagerområde på nogen måde.

> [!NOTE]
> Teams kanalsamtaler gemmes altid i den cloudbaserede postkasse, der er knyttet til teamet, hvilket betyder, at du kan søge efter kanalsamtaler. Du kan finde flere oplysninger om søgning i Teams kanalsamtaler under [Søgning i Microsoft Teams og Microsoft 365-grupper](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups).
  
## <a name="how-it-works"></a>Sådan fungerer det

Hvis en Microsoft Teams-aktiveret bruger har en postkasse i det lokale miljø, og brugerens brugerkonto/identitet er synkroniseret til cloudmiljøet, opretter Microsoft et cloudbaseret lager, der knytter brugerens 1xN-Teams chatdata til i det lokale miljø. Teams chatdata for brugere i det lokale miljø indekseres til søgning. Dette giver dig mulighed for at bruge indholdssøgning (og søgninger, der er knyttet til Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery -sager (Premium) til at søge efter, få vist og eksportere Teams chatdata til lokale brugere. Du kan også bruge **\*** ComplianceSearch-cmdlet'er i Security & Compliance Center PowerShell til at søge efter Teams chatdata for brugere i det lokale miljø.
  
Følgende grafik viser arbejdsprocessen for, hvordan Teams chatdata for brugere i det lokale miljø er tilgængelige til søgning, visning og eksport.
  
![Cloudbaseret lager til brugere i det lokale miljø i Microsoft Teams.](../media/EHAMShard1.png)
  
Ud over denne funktion kan du også bruge eDiscovery-værktøjer til at søge efter, få vist og eksportere Teams indhold på det skybaserede SharePoint websted og Exchange postkasse, der er knyttet til de enkelte Microsoft Team- og 1xN-Teams chatdata i den Exchange Online postkasse til skybaserede brugere.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Søgning efter Teams chatindhold for brugere i det lokale miljø

Sådan bruger du indholdssøgning på Microsoft Purview-overholdelsesportalen til at søge efter Teams chatdata for brugere i det lokale miljø. Du kan også bruge søgeværktøjet i eDiscovery (Standard) til at søge efter chatdata for brugere i det lokale miljø.
  
1. Gå til **Indholdssøgning** på overholdelsesportalen.

2. Klik på **Ny søgning** under fanen **Søgninger**, og navngiv den nye søgning.

3. På siden **Placeringer** skal du angive til/fra-knappen til **Til** for Exchange postkasser.

4. Hvis du vil søge efter Teams indhold for bestemte brugere (herunder brugere i det lokale miljø), skal du vælge **Vælg bruger, grupper eller teams** og vælge bestemte brugere, der skal medtages i søgningen. Hvis du ikke angiver bestemte brugere, omfatter søgningen alle brugere, herunder brugere i det lokale miljø.

5. Sørg for, at afkrydsningsfeltet **Tilføj appindhold for brugere i det lokale** miljø er markeret. Dette sikrer, at der søges i cloudbaselageret for brugere i det lokale miljø.

    ![Markér afkrydsningsfeltet "Tilføj Office-app indhold til brugere i det lokale miljø" på siden med guiden Placeringer.](../media/EHAMShardCheckBox.png)

6. På siden **Definer dine søgebetingelser** skal du oprette en nøgleordsforespørgsel og føje betingelser til søgeforespørgslen, hvis det er nødvendigt. Hvis du kun vil søge efter teamchatdata, kan du tilføje følgende forespørgsel i feltet **Nøgleord** :

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Send og kør søgningen. Alle søgeresultater for brugere i det lokale miljø kan vises som alle andre søgeresultater. Du kan også eksportere søgeresultaterne (herunder alle Teams chatdata) til en PST-fil. Du kan finde flere oplysninger under:

    - [Opret en søgning](content-search.md)

    - [Vis søgeresultater](preview-ediscovery-search-results.md)

    - [Eksportér søgeresultater](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>Brug af PowerShell til at søge efter Teams chatdata for brugere i det lokale miljø

Du kan bruge **New-ComplianceSearch-cmdlet'erne** i Security & Compliance Center PowerShell til at søge efter Teams chatdata for brugere i det lokale miljø. Som tidligere forklaret behøver du ikke indsende en supportanmodning for at bruge PowerShell til at søge efter Teams chatdata for brugere i det lokale miljø.
  
1. [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende PowerShell-kommando for at oprette en indholdssøgning, der søger efter Teams chatdata for brugere i det lokale miljø.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    Parameteren *IncludeUserAppContent*  bruges til at angive det skybaserede lager for den eller de brugere, der er angivet i parameteren  *ExchangeLocation*  . *AllowNotFoundExchangeLocationsEnabled* giver dig mulighed for at søge i det cloudbaserede lager for brugere i det lokale miljø. Når du bruger værdien `$true` for denne parameter, forsøger søgningen ikke at validere, om postkassen findes, før den kører. Dette er påkrævet for at søge i det cloudbaserede lager efter brugere i det lokale miljø, fordi dette skybaserede lager ikke fortolkes som en almindelig skybaseret postkasse.

    I følgende eksempel søges der efter Teams chats, der indeholder nøgleordet "redstone" i det cloudbaserede lager for Sara Davis, som er en bruger i det lokale miljø i Contoso-organisationen.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Når du har oprettet en søgning, skal du sørge for at bruge **Start-ComplianceSearch-cmdlet'en** til at køre søgningen.
  
Du kan få flere oplysninger om brug af disse cmdlet'er under:
  
- [Nyt overholdelsessøg](/powershell/module/exchange/new-compliancesearch)

- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Kendte problemer

- I øjeblikket kan du søge efter, få vist og eksportere Teams chatdata for brugere i det lokale miljø. Du kan også placere Teams chatdata for en bruger i det lokale miljø i en venteposition, der er knyttet til en kerne- eller eDiscovery-sag (Premium), og anvende en opbevaringspolitik for Teams chats eller kanalmeddelelser til brugere i det lokale miljø. På nuværende tidspunkt kan du dog ikke anvende en opbevaringspolitik for andre indholdsplaceringer (f.eks. Exchange postkasser og SharePoint websteder) for brugere i det lokale miljø.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Skal jeg sende en supportanmodning for at søge efter chatbeskeder for brugere i det lokale miljø?**

Nej. Denne funktion er som standard aktiveret for alle organisationer. På et tidspunkt var du nødt til at kontakte Microsoft Support, men det er ikke længere tilfældet.
  
 **Kan eDiscovery-værktøjer finde ældre Teams chatdata for brugere i det lokale miljø, før denne funktion som standard blev aktiveret for alle organisationer?**
  
Microsoft begyndte at gemme de Teams chatdata for brugere i det lokale miljø den 31. januar 2018. Så hvis identiteten for en Teams bruger i det lokale miljø er blevet synkroniseret mellem dig, Active Directory i det lokale miljø og Azure Active Directory i Microsoft 365 siden denne dato, så deres Teams  chatdata gemmes i cloudmiljøet og kan søges i ved hjælp af eDiscovery-værktøjer.

 **Skal brugerne i det lokale miljø have en licens til at gemme deres Teams chatdata i cloudmiljøet?**
  
Ja. Hvis du vil gemme Teams chatdata for en bruger i det lokale miljø i et cloudbaseret lager, skal brugeren have tildelt en Microsoft Teams licens og en Exchange Online Plan-licens i Office 365 (eller Microsoft 365).

**Hvor er det cloudbaserede lager til brugere i det lokale miljø placeret?**
  
Teams chatdata gemmes i PDL (Preferred Data Location) for en bruger i det lokale miljø. PDL er hædret i både Single-Geo- og Multi-Geo-miljøer. Du kan få flere oplysninger [under Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

**Er der risiko for at miste Teams chatdata, hvis brugerens lokale postkasse migreres til cloudmiljøet?**
  
Nej. Når du overfører den primære postkasse for en bruger i det lokale miljø til cloudmiljøet, overføres de Teams chatdata for den pågældende bruger til den nye skybaserede primære postkasse.
  
 **Kan jeg anvende en eDiscovery-venteposition eller opbevaringspolitikker på brugere i det lokale miljø?**
  
Ja. Du kan anvende eDiscovery-ventepositioner eller opbevaringspolitikker for Teams chats og kanalmeddelelser fra brugere i det lokale miljø. Men hvis du vil bevare Teams indhold for brugere i det lokale miljø, skal en bruger i det lokale miljø tildeles en Exchange Online Plan 2-licens.
