---
title: Konfigurer Advanced eDiscovery i Microsoft 365
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
description: Denne artikel beskriver, hvordan du konfigurerer en Advanced eDiscovery du kan begynde at oprette og administrere sager. Den beskriver også de nødvendige Microsoft-abonnementer og -licenser. Når du har gennemført et par hurtige trin, Advanced eDiscovery værktøjet klar til brug.
ms.openlocfilehash: cf2d7c6bc770dd6125777c895771b3b61c8ee593
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588390"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>Konfigurer Microsoft 365 Advanced eDiscovery

Advanced eDiscovery i Microsoft 365 indeholder en ende-til-ende-arbejdsproces til at bevare, indsamle, gennemse, analysere og eksportere data, der er dynamiske på organisationens interne og eksterne undersøgelser. Der er ikke brug for noget for at installere Advanced eDiscovery, men der er nogle nødvendige opgaver, som en it-administrator og eDiscovery-leder skal udføre, før din organisation kan begynde at oprette og bruge Advanced eDiscovery-sager til at administrere dine undersøgelser.

I denne artikel beskrives følgende nødvendige trin for at konfigurere Advanced eDiscovery.

![Trin til at konfigurere Advanced eDiscovery.](../media/set-up-advanced-ediscovery.png)

Dette omfatter at sikre den korrekte licensering, der kræves for at få adgang til Advanced eDiscovery og føje brugere til sager og tildele tilladelser til dit juridiske team og undersøgelsesteamet, så de kan få adgang til og administrere sager.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>Trin 1: Bekræft og tildel de relevante licenser

Licenser til Advanced eDiscovery kræver det relevante organisationsabonnement og pr. bruger-licensering. Hvis du vil have en liste over licenskrav Advanced eDiscovery, skal [du se Abonnementer og licenser](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>Trin 2: Tildel eDiscovery-tilladelser

For at Advanced eDiscovery adgang til en bruger eller tilføjet som medlem Advanced eDiscovery en sag, skal en bruger have tildelt de relevante tilladelser. Specifikt skal en bruger tilføjes som medlem af rollegruppen eDiscovery Manager i Microsoft 365 Overholdelsescenter. Medlemmer af denne rollegruppe kan oprette og administrere Advanced eDiscovery sager. De kan tilføje og fjerne medlemmer, placere familiemedlemmer og indholdsplaceringer i venteposition, administrere meddelelser om retslig venteposition, oprette og redigere søgninger, der er knyttet til en sag, føje søgeresultater til et korrektursæt, analysere data i et korrektursæt og eksportere og downloade fra en Advanced eDiscovery-sag.

Udfør følgende trin for at føje brugere til rollegruppen eDiscovery Manager:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft 365 Overholdelsescenter</a> og log på med legitimationsoplysningerne for en administratorkonto i din Microsoft 365 organisation.

2. På siden **Tilladelser skal** du vælge **rollegruppen eDiscovery Manager** .

3. På pop op-siden eDiscovery Manager skal du klikke **på Rediger** ud for **afsnittet eDiscovery Manager** .

4. På siden **Vælg eDiscovery Manager i** guiden til redigering af rollegruppe skal du klikke **på Vælg eDiscovery Manager**.

5. Klik **på** Tilføj, og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen.

6. Klik **på Tilføj** for at tilføje de valgte brugere, og klik derefter på **Udført**.

7. Klik **på** Gem for at føje brugerne til rollegruppen, og klik derefter **på Luk** for at fuldføre trinnet.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>Flere oplysninger om rollegruppen eDiscovery Manager

Der er to undergrupper i rollegruppen eDiscovery Manager. Forskellen mellem disse undergrupper er baseret på omfang.

- **eDiscovery-leder**: Kan få vist og administrere de Advanced eDiscovery sager, de opretter eller er medlem af. Hvis en anden eDiscovery-leder opretter en sag, men ikke tilføjer en anden eDiscovery-leder som medlem af den pågældende sag, vil den anden eDiscovery-leder ikke kunne se eller åbne sagen på siden Advanced eDiscovery i overholdelsescenteret. Generelt kan de fleste personer i organisationen føjes til undergruppen eDiscovery Manager.

- **eDiscovery-administrator**: Kan udføre alle sagsstyringsopgaver, som en eDiscovery-leder kan udføre. Desuden kan en eDiscovery-administrator:

  - Få vist alle tilfælde, der er angivet Advanced eDiscovery siden.
  
  - Administrer alle sager i organisationen, når de tilføjer sig selv som medlem af sagen.

  - Få adgang til og eksportér sagsdata for alle tilfælde i organisationen.

  På grund af den brede adgang bør en organisation kun have nogle få administratorer, der er medlem af undergruppen eDiscovery-administratorer.

Du kan finde flere oplysninger om eDiscovery-tilladelser og en beskrivelse af hver rolle, der er tildelt rollegruppen eDiscovery-leder, under Tildele [eDiscovery-tilladelser](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>Trin 3: Konfigurer globale indstillinger for Advanced eDiscovery

Det sidste trin, der skal fuldføres, før personer i organisationen begynder at oprette og bruge sager, er at konfigurere globale indstillinger, der gælder for alle sager i organisationen. På nuværende tidspunkt er den eneste globale indstilling *registrering af advokat-klient-rettigheder* (flere globale indstillinger vil være tilgængelige i fremtiden). Denne indstilling gør det muligt for attorney-client privilege model at køre, når du analyserer data i et gennemsynssæt. Modellen bruger maskinlæring til at afgøre sandsynligheden for, at et dokument indeholder indhold af juridisk karakter. It also compares the participants of documents with an attorney list (that you submit when setting up the model) to determine if a document has mindst one participant who is an attorney.

Du kan finde flere oplysninger om at konfigurere og bruge registreringsmodellen for attorney-client privilege i Konfigurer registrering af [advokat-klientrettigheder i Advanced eDiscovery](attorney-privilege-detection.md).

> [!NOTE]
> Dette er et valgfrit trin, du kan udføre når som helst. Ikke implementering af attorney-client privilege detection model doesn't prevent you from creating and using Advanced eDiscovery cases.

## <a name="next-steps"></a>Næste trin

Når du har konfigureret Advanced eDiscovery, er du klar til at [oprette en sag](create-and-manage-advanced-ediscoveryv2-case.md).