---
title: Nye domæner, der videresendes mailindsigt
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Administratorer kan få mere at vide om, hvordan de bruger mailindsigt om nye domæner i mailflowdashboardet i Security & Compliance Center til at undersøge, hvornår deres brugere videresender meddelelser til eksterne domæner, der aldrig er blevet videresendt til.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: df4f9e79439d435059374dd066a5298ba73d329b
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679648"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Nye domæner, der videresendes mailindsigt i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Der er gyldige forretningsmæssige grunde til at videresende mails til eksterne modtagere i bestemte domæner. Det er dog mistænkeligt, når brugerne i organisationen pludselig begynder at videresende meddelelser til et domæne, hvor ingen i organisationen nogensinde har videresendt meddelelser til (et nyt domæne).

Denne betingelse kan angive, at brugerkontiene er kompromitteret. Hvis du har mistanke om, at kontiene er blevet kompromitteret, skal [du se Svare på en kompromitteret mailkonto](responding-to-a-compromised-email-account.md).

De **nye domæner,** der videresendes mailindsigt [i Security & Compliance Center](https://protection.office.com) , giver dig besked, når brugere i organisationen videresender meddelelser til nye domæner.

Dette indsigt vises kun, når problemet er registreret, og det vises på [rapportsiden for videresendelse](view-mail-flow-reports.md#forwarding-report) .

![Nye domæner, der videresendes mailindsigt.](../../media/mfi-new-domains-being-forwarded.png)

Når du klikker på widgetten, vises en pop op-meddelelse, hvor du kan finde flere oplysninger om de videresendte meddelelser, herunder et link tilbage til [rapporten om videresendelse](view-mail-flow-reports.md#forwarding-report).

![Pop op-vindue med detaljer, der vises, når du klikker på indsigt i nye domæner, der videresendes til mail.](../../media/mfi-new-domains-being-forwarded-details.png)

Du kan også få adgang til denne detaljeside, når du vælger indsigten,  når du klikker på Vis alle i området **Top insights & anbefalinger** på (**Dashboard for** \> **rapporter eller ).** <https://protection.office.com/insightdashboard>

Hvis du vil forhindre automatisk videresendelse af meddelelser til eksterne domæner, skal du konfigurere et eksternt domæne for nogle eller alle eksterne domæner. Få mere at vide under [Administrer eksterne domæner i Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).