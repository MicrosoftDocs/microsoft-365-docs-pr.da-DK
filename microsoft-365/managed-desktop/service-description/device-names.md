---
title: Enhedsnavne
description: Sådan administrerer Microsoft Managed Desktop enhedsnavne
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: fe29027dab3b3395c14729ee7e04cbe7cebf7261
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63595906"
---
# <a name="device-names"></a>Enhedsnavne

Microsoft Managed Desktop bruger Windows Autopilot, Azure Active Directory og Microsoft Intune.

For at disse tjenester kan samarbejde problemfrit, skal enheder have ensartede, standardiserede navne. Microsoft Managed Desktop anvender et standardiseret navneformat (i formularen `MMD-%RAND11`), når enheder er tilmeldt. Windows Autopilot tildeler disse navne. Du kan finde flere oplysninger om Autopilot i [Første kørselsoplevelse med Autopilot og Statussiden For tilmelding](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Automatiserede navneændringer

Hvis en enhed omdøbes senere, omdøber Microsoft Managed Desktop den automatisk til et nyt navn i det standardiserede format. Denne proces sker hver fjerde time. Navneændringen finder sted, næste gang brugeren genstarter enheden.

> [!IMPORTANT]
> Hvis dit miljø afhænger af bestemte enhedsnavne (f.eks. for at understøtte en bestemt netværkskonfiguration), skal du undersøge mulighederne for at fjerne denne afhængighed, før du tilmelder dig Microsoft Managed Desktop.<br><br>Hvis du skal bevare navneafhængigheden, kan du sende en anmodning via administrationsportalen for at deaktivere funktionen til omdøbning og bruge det ønskede navneformat.[](../working-with-managed-desktop/admin-support.md)
