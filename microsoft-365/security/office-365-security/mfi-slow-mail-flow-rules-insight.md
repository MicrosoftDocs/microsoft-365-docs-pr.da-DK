---
title: Ret indsigt i regler for langsomt mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan de kan bruge indsigten Fix slow mail flow rules i Security & Compliance Center til at identificere og løse ineffektive eller brudte regler for mailflows (også kaldet transportregler) i deres organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 650389529f2a5d811f71b7c3f755d93e7e734d81
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128734"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Løs indsigt i regler for langsomme mailflows i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ineffektive regler for mailflow (også kaldet transportregler) kan føre til forsinkelser i mailflowet for din organisation. Denne indsigt rapporterer regler for mailflow, der har indflydelse på organisationens mailflow. Eksempler på disse typer regler omfatter:

- Betingelser, der bruger **Er medlem af** for store grupper.
- Betingelser, der bruger et komplekst regulært udtryk (regex)-mønstermatch.
- Betingelser, der bruger indholdskontrol i vedhæftede filer.

Indsigten **Fix slow mail flow rules** i området **Anbefalet for dig** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) giver dig besked, når det tager for lang tid at fuldføre en regel for et mailflow.

Denne indsigt vises først, når betingelsen er registreret (hvis du ikke har nogen mailløkker, kan du ikke se indsigten).

Du kan bruge denne meddelelse til at hjælpe dig med at identificere og finjustere regler for mailflow for at hjælpe med at reducere forsinkelser i mailflowet.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules.png" alt-text="Indsigten Ret regler for langsomme mailflows i området Anbefalet for dig på dashboardet Mailflow" lightbox="../../media/mfi-fix-slow-mail-flow-rules.png":::

Når du klikker på **Vis detaljer** på widgetten, vises der et pop op-vindue med flere oplysninger:

- **Regel**: Du kan holde markøren over oversigten for at se alle betingelserne, undtagelserne og handlingerne for reglen. Du kan klikke på oversigten for at redigere reglen i Exchange Administration på <https://admin.exchange.microsoft.com/#/transportrules>.
- **Antal meddelelser, der evalueres**: Du kan klikke på **Vis eksempelmeddelelser** for at se [resultaterne af meddelelsessporingen](message-trace-scc.md) for et eksempel på de meddelelser, der blev påvirket af reglen.
- **Den gennemsnitlige tid, der er brugt på hver meddelelse**
- **Mediantid brugt på en meddelelse**: Den midterste værdi, der adskiller den øverste halvdel fra den nederste halvdel af tidsdata.

:::image type="content" source="../../media/mfi-fix-slow-mail-flow-rules-details.png" alt-text="Pop op-vinduet Detaljer, der vises, når du har klikket på Vis detaljer i indsigten Ret regler for langsomme mailflow" lightbox="../../media/mfi-fix-slow-mail-flow-rules-details.png":::

Du kan få flere oplysninger om betingelser og undtagelser i regler for mailflow under [Betingelser og undtagelser (prædikater) for mailflowregler i Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Se også

Du kan få oplysninger om anden indsigt i dashboardet Mailflow under [Mailflowindsigt i Security & Compliance Center](mail-flow-insights-v2.md).
