---
title: Ret mulig indsigt i mailløkken
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du bruger Fix possible mail loop insight i Mail flow dashboard i Security & Compliance Center til at identificere og rette mailløkker i deres organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a80555f438ceb9431638e727ff0b84c3268ac1c1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679692"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Ret mulig indsigt i mailløkken i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Mailløkker er dårlige, fordi:

- De er spild af systemressourcer.
- De forbruger din organisations kvote for mailmængde.
- De sender forvirrende rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om ikke-leveret mail) til de oprindelige meddelelsesafsendere.

Fix **possible mail loop** insight in the **Recommended for you** area of the [Mail flow dashboard](mail-flow-insights-v2.md) in [the Security & Compliance Center](https://protection.office.com) (Ret mulig mail loop) giver dig besked, når en mailløkke registreres i din organisation.

Dette indsigt vises kun, når betingelsen er registreret (hvis du ikke har nogen mailløkker, kan du ikke se indsigten).

![Ret indsigt i regler for langsomt mailflow i området Anbefalet til dig i dashboardet for mailflow.](../../media/mfi-fix-possible-mail-loop.png)

Når du klikker **på Vis detaljer** på widgetten, vises en pop op-meddelelse med flere oplysninger:

- **Domæne**
- **Antal meddelelser: Du** kan klikke på  Vis eksempelmeddelelser for at få [](message-trace-scc.md) vist resultaterne for meddelelsessporing for en stikprøve af de meddelelser, der blev påvirket af løkken.
- **Domænetype**" Eksempelvis Autoritativ eller Ikke-autoritativ.
- **MX-post**: Værdierne **for vært (Mailserver**) **og Prioritet** for MX-posten for domænet.
- **Årsagen til** **løkken og Sådan** løser du det: Vi identificerer de mest almindelige scenarier for mailløkker og leverer anbefalede handlinger til at rette løkken.

![Pop op-vindue med detaljer, der vises, når du klikker på Vis detaljer i få mere at vide om Fix possible mail loop.](../../media/mfi-fix-possible-mail-loop-details.png)

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
