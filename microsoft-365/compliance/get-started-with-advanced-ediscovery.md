---
title: Konfigurer eDiscovery (Premium) i Microsoft Purview
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives det, hvordan du konfigurerer eDiscovery (Premium), så du kan begynde at oprette og administrere sager. Den indeholder også en beskrivelse af de påkrævede Microsoft-abonnementer og -licenser. Når du har udført nogle få hurtige trin, er værktøjet eDiscovery (Premium) klar til brug.
ms.openlocfilehash: 29805066c2db26aca6992dc34ad8bf8c0966ceb7
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939911"
---
# <a name="set-up-microsoft-purview-ediscovery-premium"></a>Konfigurer Microsoft Purview eDiscovery (Premium)

Microsoft Purview eDiscovery (Premium) indeholder en komplette arbejdsproces til at bevare, indsamle, gennemse, analysere og eksportere data, der reagerer på din organisations interne og eksterne undersøgelser. Der kræves intet for at udrulle eDiscovery (Premium), men der er nogle påkrævede opgaver, som en it-administrator og eDiscovery-leder skal udføre, før organisationen kan begynde at oprette og bruge eDiscovery-sager (Premium) til at administrere dine undersøgelser.

I denne artikel beskrives følgende trin, der er nødvendige for at konfigurere eDiscovery (Premium).

![Trin til konfiguration af eDiscovery (Premium).](../media/set-up-advanced-ediscovery.png)

Dette omfatter sikring af den korrekte licens, der kræves for at få adgang til eDiscovery (Premium) og føje vogtere til sager og tildele tilladelser til dit juridiske team og undersøgelsesteam, så de kan få adgang til og administrere sager.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Trin 1: Bekræft og tildel relevante licenser

Licenser til eDiscovery (Premium) kræver det relevante organisationsabonnement og licenser pr. bruger. Du kan finde en liste over licenskrav til eDiscovery (Premium) under [Abonnementer og licenser](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>Trin 2: Tildel eDiscovery-tilladelser

Hvis du vil have adgang til eDiscovery (Premium) eller tilføjes som medlem af en eDiscovery-sag (Premium), skal en bruger tildeles de relevante tilladelser. En bruger skal specifikt tilføjes som medlem af rollegruppen eDiscovery Manager på Microsoft Purview-overholdelsesportalen. Medlemmer af denne rollegruppe kan oprette og administrere eDiscovery-sager (Premium). De kan tilføje og fjerne medlemmer, placere tilsynsførende og indholdsplaceringer i venteposition, administrere meddelelser om juridisk venteposition, oprette og redigere søgninger, der er tilknyttet i en sag, føje søgeresultater til et gennemsynssæt, analysere data i et korrektursæt og eksportere og downloade fra en eDiscovery-sag (Premium).

Fuldfør følgende trin for at føje brugere til rollegruppen eDiscovery Manager:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">overholdelsesportalen</a>, og log på med legitimationsoplysningerne for en administratorkonto i din Microsoft 365 organisation.

2. Vælg rollegruppen **eDiscovery Manager** på siden **Tilladelser**.

3. Klik på **Rediger** ud for sektionen **eDiscovery Manager på eDiscovery Manager-pop** op-siden.

4. Klik på **Vælg eDiscovery Manager på siden Vælg eDiscovery Manager** i guiden **Rediger** rollegruppe.

5. Klik på **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen.

6. Klik på **Tilføj** for at tilføje de valgte brugere, og klik derefter på **Udført**.

7. Klik på **Gem** for at føje brugerne til rollegruppen, og klik derefter på **Luk** for at fuldføre trinnet.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Flere oplysninger om rollegruppen eDiscovery Manager

Der er to undergrupper i rollegruppen eDiscovery Manager. Forskellen mellem disse undergrupper er baseret på område.

- **eDiscovery Manager**: Kan få vist og administrere de eDiscovery-sager (Premium), de opretter eller er medlem af. Hvis en anden eDiscovery Manager opretter en sag, men ikke tilføjer endnu en eDiscovery Manager som medlem af denne sag, kan den anden eDiscovery Manager ikke få vist eller åbne sagen på siden eDiscovery (Premium) i Overholdelsescenter. Generelt kan de fleste personer i din organisation føjes til undergruppen eDiscovery Manager.

- **eDiscovery-administrator**: Kan udføre alle opgaver til sagsstyring, som en eDiscovery Manager kan udføre. En eDiscovery-administrator kan desuden:

  - Få vist alle sager, der er angivet på siden eDiscovery (Premium).
  
  - Administrer alle sager i organisationen, når de tilføjer sig selv som medlem af sagen.

  - Få adgang til og eksportér sagsdata for alle tilfælde i organisationen.

  På grund af det brede adgangsområde bør en organisation kun have nogle få administratorer, der er medlemmer af undergruppen eDiscovery-administratorer.

Du kan finde flere oplysninger om eDiscovery-tilladelser og en beskrivelse af hver rolle, der er tildelt til eDiscovery Manager-rollegruppen, under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-ediscovery-premium"></a>Trin 3: Konfigurer globale indstillinger for eDiscovery (Premium)

Det sidste trin, der skal fuldføres, før personer i din organisation begynder at oprette og bruge sager, er at konfigurere globale indstillinger, der gælder for alle sager i organisationen. På nuværende tidspunkt er den eneste globale indstilling *registrering af rettigheder for advokater og klienter* (flere globale indstillinger vil være tilgængelige i fremtiden). Denne indstilling gør det muligt for rettighedsmodellen for advokater og klienter at køre, når du analyserer data i et anmeldelsessæt. Modellen bruger maskinel indlæring til at bestemme sandsynligheden for, at et dokument indeholder indhold, der er lovligt. Det sammenligner også deltagerne i dokumenter med en advokatliste (som du indsender, når du opretter modellen) for at afgøre, om et dokument har mindst én deltager, der er advokat.

Du kan finde flere oplysninger om konfiguration og brug af modellen til registrering af rettigheder for advokater og klienter under [Konfigurer registrering af rettigheder for advokater og klienter i eDiscovery (Premium)](attorney-privilege-detection.md).

> [!NOTE]
> Dette er et valgfrit trin, som du kan udføre når som helst. Hvis du ikke implementerer modellen til registrering af rettigheder for advokatklienter, forhindrer det dig ikke i at oprette og bruge eDiscovery-sager (Premium).

## <a name="next-steps"></a>Næste trin

Når du har konfigureret eDiscovery (Premium), er du klar til at [oprette en sag](create-and-manage-advanced-ediscoveryv2-case.md).