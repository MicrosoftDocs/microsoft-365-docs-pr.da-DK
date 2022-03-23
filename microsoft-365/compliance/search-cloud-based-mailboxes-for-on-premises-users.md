---
title: Søge efter Teams chatdata for lokale brugere
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
description: Administratorer kan bruge eDiscovery-værktøjer i Microsoft 365 til at søge efter og eksportere Teams-chatdata for lokale brugere i en Exchange-hybridinstallation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fdd142783313418c8c65c04f9b5e344ff325ec2c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589176"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Søge efter Teams chatdata for lokale brugere

Hvis din organisation har en Exchange-hybridinstallation (eller din organisation synkroniserer en lokal Exchange-organisation med Office 365) og har aktiveret Microsoft Teams, kan lokale brugere bruge Teams-chatprogrammet til chat. For en skybaseret bruger gemmes Teams chatdata (også kaldet *1x1- eller 1xN-chatsamtaler*) i deres primære skybaserede postkasse. Når en lokal bruger Teams-chatprogrammet, kan deres chatmeddelelser ikke gemmes i deres primære postkasse, som er placeret lokalt. For at løse denne begrænsning har Microsoft udgivet en ny funktion, hvor et skybaseret lagringsområde oprettes, så du kan bruge eDiscovery-værktøjer til at søge efter og eksportere Teams-chatdata til lokale brugere.
  
Her er kravene og begrænsningerne for aktivering af skybaseret lagerplads for lokale brugere:
  
- Brugerkontiene i din lokale katalogtjeneste (f.eks. Active Directory) skal synkroniseres med Azure Active Directory, katalogtjenesten i Microsoft 365. Det betyder, at der oprettes en mailbrugerkonto i Microsoft 365 og er knyttet til en bruger, hvis primære postkasse er placeret i den lokale organisation.

- Den bruger, hvis primære postkasse er placeret i den lokale organisation, skal have tildelt en Microsoft Teams-licens og som minimum en Exchange Online Plan 1-licens.

- Hvis din organisation ikke har en Exchange hybridinstallation, skal du synkronisere dit lokale Exchange med Azure Active Directory. Hvis du ikke gør dette, risikerer du muligvis at oprette duplikerede skybaserede postkasser i Exchange Online for brugere, der har en postkasse i din lokale Exchange organisation.

- Det er Teams, der er knyttet til en lokal bruger, der gemmes i det skybaserede lagringsområde. En lokal bruger kan ikke få adgang til dette lagringsområde på nogen måde.

> [!NOTE]
> Teams til kanalsamtaler altid i den skybaserede postkasse, der er knyttet til teamet, hvilket betyder, at du kan søge efter kanalsamtaler. Du kan finde flere oplysninger Teams at søge i Microsoft Teams [og Microsoft 365 kanalsamtaler](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups).
  
## <a name="how-it-works"></a>Sådan fungerer det

Hvis en Microsoft Teams-aktiveret bruger har en lokal postkasse, og brugerens brugerkonto/identitet er blevet synkroniseret til skyen, opretter Microsoft skybaseret lager til at knytte den lokale brugers 1xN-Teams-chatdata til. Teams chatdata for lokale brugere indekseres til søgning. Det gør det muligt at bruge indholdssøgning (og søgninger, der er knyttet til Core eDiscovery og Advanced eDiscovery-sager) til at søge, få vist og eksportere Teams-chatdata til lokale brugere. Du kan også bruge **\*** ComplianceSearch-cmdlet'er i Security & Compliance Center PowerShell til Teams søge efter chatdata for lokale brugere.
  
Følgende grafik viser arbejdsprocessen for, Teams chatdata for lokale brugere er tilgængelige til søgning, eksempelvisning og eksport.
  
![Skybaseret lagerplads for lokale brugere i Microsoft Teams.](../media/EHAMShard1.png)
  
Ud over denne funktionalitet kan du også bruge eDiscovery-værktøjer til at søge, få vist og eksportere Teams-indhold i det skybaserede SharePoint-websted og Exchange-postkasse, der er knyttet til hvert Microsoft Team og 1xN Teams-chatdata i Exchange Online-postkassen for skybaserede brugere.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Søgning efter Teams chatindhold for lokale brugere

Sådan bruger du indholdssøgning i Microsoft 365 Overholdelsescenter til at Teams chatdata for lokale brugere. Du kan også bruge søgeværktøjet i Core eDiscovery til at søge efter chatdata for lokale brugere.
  
1. I Microsoft 365 Overholdelsescenter skal du gå til **Indholdssøgning**.

2. Klik på **Ny søgning** under fanen **Søgninger**, og navngive den nye søgning.

3. På siden **Placeringer skal** du indstille til/**fra-knappen til Til** for Exchange postkasser.

4. Hvis du vil søge Teams indhold efter bestemte brugere (herunder lokale brugere), skal du vælge Vælg bruger, grupper eller **teams** og vælge bestemte brugere, der skal medtages i søgningen. Hvis du ikke oplister bestemte brugere, vil søgningen omfatte alle brugere, herunder lokale brugere.

5. Sørg for **, at afkrydsningsfeltet Tilføj appindhold for lokale** brugere er markeret. Dette sikrer, at der søges i skybaseret lagerplads for lokale brugere.

    ![Markér afkrydsningsfeltet "Office-app indhold for lokale brugere" på siden med guiden Placeringer.](../media/EHAMShardCheckBox.png)

6. På siden **Definer dine søgebetingelser skal** du oprette en nøgleordsforespørgsel og føje betingelser til søgeforespørgslen, hvis det er nødvendigt. Hvis du kun vil søge efter teamchatdata, kan du tilføje følgende forespørgsel i **feltet** Nøgleord:

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Send og kør søgningen. Eventuelle søgeresultater for lokale brugere kan vises som alle andre søgeresultater. Du kan også eksportere søgeresultaterne (herunder eventuelle Teams chatdata) til en PST-fil. Du kan finde flere oplysninger under:

    - [Opret en søgning](content-search.md)

    - [Få vist søgeresultater](preview-ediscovery-search-results.md)

    - [Eksportér søgeresultater](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>Brug PowerShell til at søge Teams chatdata for lokale brugere

Du kan bruge **New-ComplianceSearch-cmdlet'er** i Security & Compliance Center PowerShell til Teams søge efter chatdata for lokale brugere. Som beskrevet tidligere behøver du ikke at indsende en supportanmodning for at bruge PowerShell til Teams søge efter chatdata for lokale brugere.
  
1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende PowerShell-kommando for at oprette en indholdssøgning, der Teams efter chatdata for lokale brugere.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    *Parameteren IncludeUserAppContent* bruges til at angive det skybaserede lager for den eller de brugere, der er angivet af *parameteren ExchangeLocation*. *AllowNotFoundExchangeLocationsEnabled* giver dig mulighed for at søge efter lokale brugeres skybaserede lager. Når du bruger værdien `$true` for denne parameter, forsøger søgningen ikke at validere eksistensen af postkassen, før den køres. Dette er påkrævet for at søge efter den skybaserede lagerplads for lokale brugere, fordi dette skybaserede lager ikke løses som en almindelig skybaseret postkasse.

    I følgende eksempel søges der Teams chatsamtaler, der indeholder nøgleordet "redstone" i det skybaserede lager for Sara Davis, som er lokal bruger i Contoso-organisationen.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Når du har oprettet en søgning, skal du sørge for at bruge **cmdlet'en Start-ComplianceSearch** til at køre søgningen.
  
Du kan finde flere oplysninger om brug af disse cmdlet'er i:
  
- [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Kendte problemer

- Du kan i øjeblikket søge efter, få vist og Teams chatdata for lokale brugere. Du kan også placere Teams-chatdata for en lokal bruger i venteposition, der er knyttet til en Core- eller Advanced eDiscovery-sag, og anvende en opbevaringspolitik for Teams chats eller kanalmeddelelser for lokale brugere. Men på nuværende tidspunkt kan du ikke anvende en opbevaringspolitik for andre indholdsplaceringer (f.eks Exchange postkasser og SharePoint-websteder) for lokale brugere.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Skal jeg sende en supportanmodning for at søge efter chatmeddelelser for lokale brugere?**

Nej. Denne funktion er aktiveret som standard for alle organisationer. Du skulle på et tidspunkt kontakte Microsoft Support, men det er ikke længere tilfældet.
  
 **Kan eDiscovery-værktøjer finde ældre Teams chatdata for lokale brugere, før det tidspunkt, hvor denne funktion blev aktiveret, som standard for alle organisationer?**
  
Microsoft begyndte at gemme Teams chatdata for lokale brugere den 31. januar 2018. Så hvis identiteten på en lokal Teams-bruger er blevet synkroniseret mellem dig lokalt Active Directory og Azure Active Directory i Microsoft 365 siden denne dato, gemmes deres Teams-chatdata i skyen og kan søges i ved hjælp af eDiscovery-værktøjer.

 **Skal lokale brugere have en licens for at kunne gemme deres Teams chatdata i skyen?**
  
Ja. Hvis du Teams gemme chatdata for en lokal bruger i et skybaseret lager, skal brugeren have tildelt en Microsoft Teams-licens og en Exchange Online-planlicens i Office 365 (eller Microsoft 365).

**Hvor er det skybaserede lager for lokale brugere placeret?**
  
Teams-chatdata gemmes på foretrukken dataplacering (PDL) for en lokal bruger. PDL imødekommes både i Single-Geo og Multi-Geo-miljøer. Du kan finde flere oplysninger [Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

**Er der risiko for at miste Teams chatdata, hvis brugerens lokale postkasse overføres til skyen?**
  
Nej. Når du overfører den primære postkasse for en lokal bruger til skyen, bliver Teams-chatdataene for den pågældende bruger overført til deres nye skybaserede primære postkasse.
  
 **Kan jeg anvende et eDiscovery-venteposition eller opbevaringspolitikker til lokale brugere?**
  
Ja. Du kan anvende ventende eller opbevaringspolitikker for eDiscovery til Teams chatsamtaler og kanalmeddelelser for lokale brugere. Men hvis du vil bevare Teams indhold til lokale brugere, skal en lokal bruger tildeles en Exchange Online Plan 2-licens.
