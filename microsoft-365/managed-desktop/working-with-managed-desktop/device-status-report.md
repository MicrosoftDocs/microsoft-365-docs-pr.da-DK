---
title: Statusrapport for enhed
description: Forklarer enhedsstatus
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: be685d39bbda3b96f689c13a3bc3485c011f1ec8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592531"
---
# <a name="device-status-report"></a>Statusrapport for enhed

Denne rapport aggregerer status for alle dine registrerede enheder for at vise din brug af Microsoft Managed Desktop-tjenesten.

Vi kategoriserer enheder ud fra deres aktivitet i løbet af de seneste 28 dage og efter vores mulighed for at holde enheden opdateret.

For at blive opdateret Windows Opdater så hurtigt som muligt skal en enhed:

- Have forbindelse til internettet.
- Ikke dvaletilstand.
- Ikke midlertidigt afbrudt i mindst seks timer, hvoraf to skal være fortløbende.

Selvom det er muligt, at en enhed, der ikke opfylder disse krav, opdateres. Enheder, der opfylder dem, har den højeste sandsynlighed for at blive opdateret.

:::image type="content" source="../../media/mmd-device-status.png" alt-text="Rapport, der viser et donutdiagram over enhedens aktivitetsstatus øverst til venstre, få vist filtre øverst til højre med en knap til at generere rapporten og en tabel med detaljer langs bunden":::

## <a name="device-status-labels"></a>Navne på enhedsstatus

Vi rapporterer enhedsstatus ved hjælp af følgende mærkater:

| Enhedsstatusmærkat | Beskrivelse |
| ------ | ------ |
| Klar til brug | Enheder, der er registreret med vores tjeneste og klar til at blive givet til en bruger.|
| Aktiv | Enheder, der bruges. <ul><li>De har opfyldt aktivitetskriterierne (seks timer, to fortløbende) for den seneste udgivelse af sikkerhedsopdateringer.</li> <li>De har tjekket ind med Microsoft Intune gang inden for de seneste fem dage.</li></ul> |
| Synkroniseret | Enheder, der bruges og har været tjekket ind med Intune inden for de seneste 28 dage.
| Ikke synkroniseret | Enheder, der bruges, men ikke har tjekket ind med Intune inden for de seneste 28 dage. |
| Andet | Etiketten samler flere fejl tilstande, der kan opstå, typisk under enhedsregistrering. Du kan finde flere oplysninger under [Fejlfinding af enhedsregistrering](../get-started/manual-registration.md#troubleshooting-device-registration). |
