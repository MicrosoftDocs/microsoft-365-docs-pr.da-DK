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
ms.localizationpriority: medium
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du kan bruge indsigt i Ret regler for langsom mailflow i Security & Compliance Center til at identificere og løse ineffektiv eller ødelagte regler for mailflow (også kaldet transportregler) i deres organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9866761e683e15d34d81b8ea0962d974b0b474da
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589559"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Ret indsigt i regler for langsomt mailflow i Sikkerheds- & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ineffektiv regler for mailflow (også kaldet transportregler) kan medføre forsinkelser i mailflowet i organisationen. Dette indsigt rapporterer regler for mailflow, der har indvirkning på organisationens mailflow. Eksempler på disse typer regler omfatter:

- Betingelser, der **bruger Er medlem af** for store grupper.
- Betingelser, der bruger matchende komplekse regulære udtryk (regex).
- Betingelser, der bruger indholdskontrol i vedhæftede filer.

**Du kan** finde oplysninger om regler for rettelse af langsom mailflow i området Anbefalet til dig i [dashboardet for mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com), når det tager for lang tid at gennemføre en regel **for** mailflow.

Dette indsigt vises kun, når betingelsen er registreret (hvis du ikke har nogen mailløkker, kan du ikke se indsigten).

Du kan bruge denne meddelelse til at hjælpe dig med at identificere og finjustere regler for mailflow for at reducere forsinkelser i mailflowet.

![Ret indsigt i regler for langsomt mailflow i området Anbefalet til dig i dashboardet for mailflow.](../../media/mfi-fix-slow-mail-flow-rules.png)

Når du klikker **på Vis detaljer** på widgetten, vises en pop op-meddelelse med flere oplysninger:

- **Regel**: Du kan holde markøren over oversigten for at se alle reglens betingelser, undtagelser og handlinger. Du kan klikke på oversigten for at redigere reglen i Exchange Administration (EAC) på <https://admin.exchange.microsoft.com/#/transportrules>.
- **Antal meddelelser, der er** evalueret:  Du kan klikke på Vis eksempelmeddelelser for at få vist resultaterne af meddelelsessporing for en stikprøve af de meddelelser, der blev påvirket af reglen.[](message-trace-scc.md)
- **Gennemsnitlig tid brugt på hver meddelelse**
- **Mediantid brugt på en meddelelse**: Den midterste værdi, der adskiller den øverste halvdel fra den nederste halvdel af tidsdataene.

![Pop op-vindue med detaljer, der vises, når du klikker på Vis detaljer i indsigten Ret regler for langsom mailflow.](../../media/mfi-fix-slow-mail-flow-rules-details.png)

Du kan finde flere oplysninger om betingelser og undtagelser i regler for mailflow i Betingelser og undtagelser [(prædikater) for mailflowregler Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).