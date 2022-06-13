---
title: Beskyt din c-pakke med prioritetskontobeskyttelse i Microsoft Defender for Office 365 Plan 2
description: Trinnene til beskyttelse af din c-suite med prioriteret kontobeskyttelse. Hvis du mærker en konto som en prioritetskonto, kan du få den ekstra beskyttelse, der er tilpasset mønstrene for mailflowet, som er målrettet virksomhedens direktører, sammen med ekstra synlighed i rapporter, beskeder og undersøgelser.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 99bfcd9003d55ced96364f033080992fa4447188
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042927"
---
# <a name="protect-your-c-suite-with-priority-account-protection"></a>Beskyt din c-suite med prioritetskontobeskyttelse

Prioritetskontobeskyttelse hjælper it- og sikkerhedsteams med at sikre en høj kvalitet af service og beskyttelse for de kritiske personer i din organisation. Hvis du mærker en konto som en prioriteret konto, kan du opnå den ekstra beskyttelse, der er tilpasset mønstrene for mailflowet, som er målrettet virksomhedens direktører, sammen med ekstra synlighed i rapporter, beskeder og undersøgelser.

## <a name="what-youll-need"></a>Det skal du bruge
- Microsoft Defender for Office 365 Plan 2 (inkluderet som en del af E5-planer)
- Tilstrækkelige tilladelser (rolle som sikkerhedsadministrator)
- 5 minutter til at udføre nedenstående trin.

## <a name="tag-priority-users"></a>Brugere med mærkeprioritet
1. Identificer de brugere, grupper eller domæner, du vil mærke som prioritetskonti.
1. Log på [Microsoft Security Portal](https://security.microsoft.com/), og naviger til Indstillinger på navigationslinjen til venstre.
1. Vælg Mail & samarbejde på den side, der indlæses, og klik derefter på Brugerkoder
1. På siden Brugerkoder skal du vælge kontomærket Prioritet og trykke på Rediger mærke
1. På det pop op-vindue, der vises, skal du vælge Tilføj medlemmer
1. Søg efter de brugere, du vil tagge, vælg en eller flere brugere, og tryk på Tilføj
1. Gennemse de medlemmer, du har valgt, og tryk på Næste
1. Tryk på Send for at bekræfte ændringerne

Hvis du vil vide mere om, hvilke prioritetskontotags der er, skal du se [Administrer og overvåg prioritetskonti – Microsoft 365 administrator | Microsoft Docs](../../../admin/setup/priority-accounts.md).

## <a name="next-steps"></a>Næste trin
[Gennemse den differentierede beskyttelse for brugere, der er mærket som prioritetskonti](../../office-365-security/configure-review-priority-account.md).

## <a name="powershell-configuration"></a>PowerShell-konfiguration
Hvis du vil udføre disse trin via [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), kan du gøre dette ved hjælp af følgende cmdlet'er:
1. Få vist en liste over prioritetskonti: **Hent bruger -IsVIP | vælg Identitet**
1. Føj bruger til listen over prioritetskonti: **Set-User -VIP:$true -Identity \<Identity\>**
1. Fjern brugeren fra listen over prioritetskonti: **Set-User -VIP:$false -Identity \<Identity\>**
