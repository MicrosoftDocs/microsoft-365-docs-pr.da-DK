---
title: Øverste indsigt i domænets mailflowstatus i dashboardet for mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du bruger det øverste indsigt i mailflowstatus i mailflowdashboardet i Security & Compliance Center til fejlfinding af problemer med mailflow i forbindelse med deres MX-poster.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e4ed59e31cd21826eebf306e566610d54635f0c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589160"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Øverste indsigt i domænemailflowstatus i Sikkerheds- & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Det **Øverste indsigt i domænemailflowstatus** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) giver dig den aktuelle mailflowstatus for organisationen.

Dette indsigt hjælper dig med at identificere og foretage fejlfinding af domæner, der oplever ***problemer med mailflow*** . Domænet kan f.eks. ikke modtage ekstern mail, fordi domænet er udløbet, eller domænet har en forkert MX-post.

![Øverste widget for domæneflowstatus i dashboardet mailflow i & Compliance Center.](../../media/mfi-top-domain-mail-flow-status-widget.png)

Når du klikker **på Vis detaljer** i widgetten, vises **en** pop op-vindue med domænestatus, der viser dig flere oplysninger om status for hvert domæne:

- **Domæne**
- **Forrige MX-post**
- **Aktuel MX-post**
- **Modtagestatus for mail**
- **Domænestatus**: En grøn markering angiver den aktuelle MX-post (på det tidspunkt, du klikkede på widgetten) svarer til den værdi, vi har registreret, og domænet har modtaget mail i løbet af de seneste to timer.

  Et rødt X angiver, at MX-posten er blevet ændret, og at domænet ikke har modtaget nogen mail inden for de seneste seks timer. Dette indikerer sandsynligvis, at dit domæne er udløbet, eller at MX-posten er blevet opdateret forkert. Kontakt din domæneregistrator eller DNS-hostingtjeneste for at finde ud af, om domænet er udløbet, eller om domænets MX-post er forkert.

Du kan klikke **på Vis flere** for at få vist de samme oplysninger om flere domæner.

![Pop op-meddelelse med detaljer i mailflowstatus for det øverste domæne.](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
