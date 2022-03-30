---
title: Indsigt i automatisk videresendte meddelelser
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Administratorer kan få mere at vide om rapporten om automatisk videresendte meddelelser i dashboardet for mailflow i & Compliance Center.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 05ad934fbc7736c0cfbb86f7411a2ca73705112f
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680154"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Indsigt i automatisk videresendte meddelelser i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Den **automatiske videresendte** meddelelses indsigt i [dashboardet til mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) viser oplysninger om meddelelser, der automatisk videresendes fra organisationen til modtagere i eksterne domæner.

![Widgetten Automatisk videresendte meddelelser i Security & Compliance Center.](../../media/mfi-auto-forwarded-messages.png)

## <a name="auto-forwarded-messages-details"></a>Oplysninger om automatisk videresendte meddelelser

Når du klikker på antallet af meddelelser i widgetten, vises en pop op-rude, der viser flere oplysninger om de automatisk videresendte meddelelser:

- **Automatisk videresendte meddelelser ved hjælp af videresendelsesmetoder**:

  - **Efter regler for mailflow**
  - **Efter indbakkeregler**
  - **Med SMTP-videresendelse**: Denne metode angiver automatisk videresendelse, som administratorer kan konfigurere for en postkasse som beskrevet i Konfigurer videresendelse af mail [for en postkasse](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Et link til rapporten [om videresendelse for at](view-mail-flow-reports.md#forwarding-report) få flere oplysninger.

- **Automatisk videresendte meddelelser efter domæner og brugere**:

  - **Top 5 domæner videresendt til**
  - **Nye domæner (sidste uge)**
  - **De 5 hyppigste brugere til videresendelse**
  - **Nye brugere (sidste uge)**
  - Et link til rapporten [videresendelse af ændringer for at](mfi-new-users-forwarding-email.md#forwarding-modifications-report) få flere oplysninger.

![Pop op-mail med oplysninger om rapporten om automatisk videresendte meddelelser i & Security & Compliance Center.](../../media/mfi-auto-forwarded-messages-details.png)

## <a name="insights"></a>Insights

Der genereres to indsigter baseret på rapportdataene:

- [Nye brugere, der videresender mail](mfi-new-users-forwarding-email.md)
- [Nye domæner, der videresendes mail](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).