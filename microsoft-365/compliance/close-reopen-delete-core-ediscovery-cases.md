---
title: Luk, genåbn og slet eDiscovery-sager (Standard)
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
description: I denne artikel beskrives det, hvordan du administrerer eDiscovery-sager (Standard). Dette omfatter lukning af en sag, genåbning af en lukket sag og sletning af en sag.
ms.openlocfilehash: ee18a169ace43f03a0407b87c8ae70705af2f43c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992364"
---
# <a name="close-reopen-and-delete-a-ediscovery-standard-case"></a>Luk, genåbn og slet en eDiscovery-sag (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel beskrives det, hvordan du lukker, genåbner og sletter Microsoft Purview eDiscovery-sager (Standard) i Microsoft 365.

## <a name="close-a-case"></a>Luk en sag

Når den juridiske sag eller undersøgelse, der understøttes af en eDiscovery-sag (Standard), er fuldført, kan du lukke sagen. Her er, hvad der sker, når du lukker en sag:
  
- Hvis sagen indeholder eDiscovery-ventepositioner, deaktiveres de. Når ventepositionen er slået fra, anvendes der en 30-dages udvidet periode (kaldet *forsinkelsesventetid*) på indholdsplaceringer, der var i venteposition. Dette hjælper med at forhindre, at indhold slettes med det samme, og giver administratorer mulighed for at søge efter og gendanne indhold, før det kan slettes permanent, når forsinkelsesperioden udløber. Du kan finde flere oplysninger under [Fjernelse af indholdsplaceringer fra eDiscovery-venteposition](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Hvis du lukker en sag, deaktiveres de ventepositioner, der er knyttet til den pågældende sag, kun. Hvis andre ventepositioner placeres på en indholdsplacering (f.eks. en procesførelsesholdning, en opbevaringspolitik eller en venteposition fra en anden eDiscovery(Standard)-sag, bevares disse ventepositioner stadig.

- Sagen vises stadig på siden eDiscovery (Standard) på Microsoft Purview-overholdelsesportalen. Detaljer, ventepositioner, søgninger og medlemmer af en lukket sag bevares.

- Du kan redigere en sag, når den er lukket. Du kan f.eks. tilføje eller fjerne medlemmer, oprette søgninger og eksportere søgeresultater. Den primære forskel mellem aktive og lukkede sager er, at eDiscovery-ventepositioner er slået fra, når en sag lukkes.

Sådan lukker du en sag:
  
1. Klik på **eDiscoveryCore** >  på overholdelsesportalen for at få vist listen over eDiscovery-sager (Standard) i din organisation.

2. Klik på navnet på den sag, du vil lukke.

   ![Luk sag på startsiden for sagen.](../media/eDiscoveryCaseHomePage.png)

3. Klik på **Luk sag** under **Status** på startsiden.

    Der vises en advarsel om, at de ventepositioner, der er knyttet til sagen, deaktiveres.

4. Klik på **Ja** for at lukke sagen.

    Status på startsiden for sagen ændres fra **Aktiv** til **Lukning**.

5. På siden **eDiscovery (Standard)** skal du klikke på **Opdater** for at opdatere status for den lukkede sag. Det kan tage op til 60 minutter, før lukningsprocessen er fuldført.

    Når processen er fuldført, ændres status for sagen til **Lukket** på siden **eDiscovery (Standard).**

## <a name="reopen-a-closed-case"></a>Åbn en lukket sag igen

Når du genåbner en sag, genindsættes eDiscovery-ventepositioner, der var på plads, da sagen blev afsluttet, ikke automatisk. Når sagen er genåbnet, skal du gå til siden **Ventepositioner** og slå de forrige ventepositioner til. Hvis du vil slå en venteposition til, skal du vælge den for at få vist pop op-siden og derefter angive **Status** til **Til**.
  
1. Klik på **eDiscoveryCore** >  på overholdelsesportalen for at få vist listen over eDiscovery-sager (Standard) i din organisation.

2. Klik på navnet på den sag, du vil åbne igen.

   ![Åbn en lukket sag igen.](../media/eDiscoveryCaseHomePageReopen.png)

3. Klik på **Genåbn sag** under **Status** på startsiden.

    Der vises en advarsel om, at de ventepositioner, der var knyttet til sagen, da den blev lukket, ikke aktiveres automatisk.

4. Klik på **Ja** for at åbne sagen igen.

    Status på startsiden for sagen ændres fra **Lukket** til **Aktiv**.

5. På siden **eDiscovery (Standard)** skal du klikke på **Opdater** for at opdatere status for den genåbnede sag. Det kan tage op til 60 minutter, før genåbningsprocessen er fuldført. 

    Når processen er fuldført, ændres status for sagen til **Aktiv** på siden **eDiscovery (Standard).**

6. (Valgfrit) Hvis du vil slå ventepositioner, der er knyttet til den genåbnede sag, til, skal du gå til fanen **Ventepositioner** , vælge en venteposition og derefter markere afkrydsningsfeltet under **Status** på pop op-siden for venteposition.
  
## <a name="delete-a-case"></a>Slet en sag

Du kan også slette aktive og lukkede eDiscovery-sager (Standard). Når du sletter en sag, slettes alle søgninger og eksporter i sagen, og sagen fjernes fra listen over sager på siden **eDiscovery (Standard)** på overholdelsesportalen. Du kan ikke åbne en slettet sag igen.

Før du kan slette en sag (uanset om den er aktiv eller lukket), skal du først slette *alle* eDiscovery-ventepositioner, der er knyttet til sagen. Det omfatter sletning af ventepositioner med statussen **Fra**. 

Sådan sletter du en eDiscovery-venteposition:

1. Gå til fanen **Ventepositioner** i det tilfælde, du vil slette.

2. Vælg den venteposition, du vil slette.

3. Klik på **Slet** på pop op-siden.

      ![Slet en eDiscovery-venteposition.](../media/DeleteeDiscoveryHold.png)

Sådan sletter du en sag:

1. Klik på **eDiscoveryCore** >  på overholdelsesportalen for at få vist listen over eDiscovery-sager (Standard) i din organisation.

2. Klik på navnet på den sag, du vil slette.

3. Klik på **Slet sag** under **Status** på startsiden for sagen.

      ![Slet en sag.](../media/eDiscoveryCaseHomePageDelete.png)

Hvis den sag, du forsøger at slette, stadig indeholder eDiscovery-ventepositioner, får du vist en fejlmeddelelse. Du skal slette alle ventepositioner, der er knyttet til sagen, og derefter prøve igen for at slette sagen.
