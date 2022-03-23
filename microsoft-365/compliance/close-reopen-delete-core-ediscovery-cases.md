---
title: Luk, genåå og slet Core eDiscovery-sager
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
description: I denne artikel beskrives det, hvordan du administrerer kerne eDiscovery-sager. Dette omfatter lukning af en sag, genåbning af en lukket sag og sletning af en sag.
ms.openlocfilehash: a210a06da2effb0b17d526a09499a65fa59bfeb4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588409"
---
# <a name="close-reopen-and-delete-a-core-ediscovery-case"></a>Lukke, genåbne og slette en Core eDiscovery-sag

Denne artikel beskriver, hvordan du lukker, genåbner og sletter Core eDiscovery-sager Microsoft 365.

## <a name="close-a-case"></a>Luk en sag

Når den juridiske sag eller undersøgelse, der understøttes af en core eDiscovery-sag, er afsluttet, kan du lukke sagen. Her er, hvad der sker, når du lukker en sag:
  
- Hvis sagen indeholder eDiscovery-ventende elementer, deaktiveres de. Når ventepositionen er deaktiveret, anvendes en udvidet periode på 30 dage (kaldet *forsinkelse) på* indholdsplaceringer, der var i venteposition. Dette er med til at forhindre, at indhold slettes med det samme, og giver administratorer mulighed for at søge efter og gendanne indhold, før det kan slettes permanent, når perioden for forsinkelse udløber. Få mere at vide under [Fjern indholdsplaceringer fra en eDiscovery-venteposition](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Når du lukker en sag, deaktiveres kun de ventende, der er knyttet til den pågældende sag. Hvis andre ventepositioner er placeret på en indholdsplacering (f.eks. retslig tilbageholdelse, en opbevaringspolitik eller venteposition fra en anden Core eDiscovery-sag), bevares disse ventepositioner stadig.

- Sagen er stadig anført på Core eDiscovery-siden i Microsoft 365 Overholdelsescenter. Detaljer, vente hold, søgninger og medlemmer af en lukket sag bevares.

- Du kan redigere en sag, efter den er lukket. Du kan f.eks. tilføje eller fjerne medlemmer, oprette søgninger og eksportere søgeresultater. Den primære forskel mellem aktive og lukkede sager er, at eDiscovery-ventende sager er slået fra, når en sag lukkes.

Sådan lukker du en sag:
  
1. I Microsoft 365 Overholdelsescenter skal du klikke **på eDiscoveryCore** >  for at få vist listen over kerne eDiscovery-sager i din organisation.

2. Klik på navnet på den sag, du vil lukke.

   ![Luk sag på startsiden for store/små bogstaver.](../media/eDiscoveryCaseHomePage.png)

3. Klik på Luk sag under **Status** på **startsiden**.

    Der vises en advarsel, der fortæller, at de ventende ord, der er knyttet til sagen, deaktiveres.

4. Klik **på Ja** for at lukke sagen.

    Status på case-startsiden ændres fra **Aktiv** til **Lukning**.

5. På siden **Core eDiscovery** skal du klikke **på Opdater** for at opdatere status for den lukkede sag. Det kan tage op til 60 minutter, før afslutningsprocessen er fuldført.

    Når processen er fuldført, ændres sagens status til **Lukket på** core **eDiscovery-siden** .

## <a name="reopen-a-closed-case"></a>Genåbne en lukket sag

Når du genåbner en sag, genaktiveres eventuelle eDiscovery-ventende oplysninger, der var på plads, da sagen blev lukket, ikke automatisk. Når sagen er genåbnet, skal du gå til siden **Ventende og** aktivere de forrige ventende indstillinger. Hvis du vil aktivere en venteposition, skal du markere den for at få vist pop op-siden og derefter indstille **Status** til **Til**.
  
1. I Microsoft 365 Overholdelsescenter skal du klikke **på eDiscoveryCore** >  for at få vist listen over kerne eDiscovery-sager i din organisation.

2. Klik på navnet på den sag, du vil genåbne.

   ![Åbn en lukket sag igen.](../media/eDiscoveryCaseHomePageReopen.png)

3. Klik på Åbn store og små bogstaver **igen under Status** **på startsiden**.

    Der vises en advarsel, der fortæller, at de ventende ord, der var knyttet til sagen, da den blev lukket, ikke bliver slået til automatisk.

4. Klik **på Ja** for at genåbne sagen.

    Status på pop op-siden med case-startsiden ændres fra **Lukket** til **Aktiv**.

5. På core **eDiscovery-siden** skal du klikke **på Opdater** for at opdatere status for den genåbnede sag. Det kan tage op til 60 minutter, før genåbningsprocessen er fuldført. 

    Når processen er fuldført, ændres sagens status til **Aktiv** på **siden Core eDiscovery** .

6. (Valgfrit) Hvis du vil aktivere ventepositioner, der er knyttet til den genåbnede sag, skal du gå til fanen Ventepositioner, vælge en venteposition og derefter markere afkrydsningsfeltet under **Status** på pop op-siden til venteposition.
  
## <a name="delete-a-case"></a>Slet en sag

Du kan også slette aktive og lukkede Core eDiscovery-sager. Når du sletter en sag, slettes alle søgninger og eksporter i sagen, og sagen fjernes fra listen over sager på **siden Core eDiscovery** i Microsoft 365 Overholdelsescenter. Du kan ikke genåbne en slettet sag.

Før du kan slette en sag (uanset om den er aktiv eller lukket), skal du først slette *alle de* eDiscovery-ventende filer, der er knyttet til sagen. Det omfatter sletning af ventende filer med statussen **Fra**. 

Sådan sletter du en eDiscovery-venteposition:

1. Gå til fanen **Ventende** filer i det tilfælde, du vil slette.

2. Markér den venteposition, du vil slette.

3. Klik på Slet på pop **op-siden**.

      ![Slet en eDiscovery-venteposition.](../media/DeleteeDiscoveryHold.png)

Sådan sletter du en sag:

1. I Microsoft 365 Overholdelsescenter skal du klikke **på eDiscoveryCore** >  for at få vist listen over kerne eDiscovery-sager i din organisation.

2. Klik på navnet på den sag, du vil slette.

3. Klik på Slet store og små bogstaver under **Status** på **startsiden for store og små bogstaver**.

      ![Slet en sag.](../media/eDiscoveryCaseHomePageDelete.png)

Hvis den sag, du forsøger at slette, stadig indeholder eDiscovery-ventende elementer, modtager du en fejlmeddelelse. Du skal slette alle ventende filer, der er knyttet til sagen, og derefter prøve igen for at slette sagen.
