---
title: Øverste indsigt i domænets mailflowstatus i dashboardet for mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du bruger det øverste indsigt i mailflowstatus i mailflowdashboardet i Security & Compliance Center til fejlfinding af problemer med mailflow i forbindelse med deres MX-poster.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3994859c1d5a4e0026f61dcc24a9735c6122ad15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465415"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Øverste indsigt i domænemailflowstatus i Sikkerheds- & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Det **Øverste indsigt i domænemailflowstatus** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) giver dig den aktuelle mailflowstatus for organisationen.

Dette indsigt hjælper dig med at identificere og foretage fejlfinding af domæner, der oplever ***problemer med mailflow*** . Domænet kan f.eks. ikke modtage ekstern mail, fordi domænet er udløbet, eller domænet har en forkert MX-post.

:::image type="content" source="../../media/mfi-top-domain-mail-flow-status-widget.png" alt-text="Den øverste widget for domæneflowstatus i dashboardet Mailflow i & Compliance Center" lightbox="../../media/mfi-top-domain-mail-flow-status-widget.png":::

Når du klikker **på Vis detaljer** i widgetten, vises **en** pop op-vindue med domænestatus, der viser dig flere oplysninger om status for hvert domæne:

- **Domæne**
- **Forrige MX-post**
- **Aktuel MX-post**
- **Modtagestatus for mail**
- **Domænestatus**: En grøn markering angiver den aktuelle MX-post (på det tidspunkt, du klikkede på widgetten) svarer til den værdi, vi har registreret, og domænet har modtaget mail i løbet af de seneste to timer.

  Et rødt X angiver, at MX-posten er blevet ændret, og at domænet ikke har modtaget nogen mail inden for de seneste seks timer. Dette indikerer sandsynligvis, at dit domæne er udløbet, eller at MX-posten er blevet opdateret forkert. Kontakt din domæneregistrator eller DNS-hostingtjeneste for at finde ud af, om domænet er udløbet, eller om domænets MX-post er forkert.

Du kan klikke **på Vis flere** for at få vist de samme oplysninger om flere domæner.

:::image type="content" source="../../media/mfi-top-domain-mail-flow-status-view-details.png" alt-text="Pop op-pop op-pop-op-pop-op'en Detaljer i statussen for mailflowet Øverst på domænet" lightbox="../../media/mfi-top-domain-mail-flow-status-view-details.png":::

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
