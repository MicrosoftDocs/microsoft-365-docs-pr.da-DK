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
description: Administratorer kan få mere at vide om rapporten automatisk videresendte meddelelser på dashboardet Mailflow i Security & Compliance Center.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2f102f4fbea558f0972fbd4f3e8f4a4bea257bf4
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131036"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Indsigt i automatisk videresendte meddelelser i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Indsigten **Automatisk videresendte meddelelser** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) viser oplysninger om meddelelser, der automatisk videresendes fra din organisation til modtagere i eksterne domæner.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Widgetten, nemlig automatisk videresendte meddelelser i Security & Compliance Center" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Oplysninger om automatisk videresendte meddelelser

Når du klikker på antallet af meddelelser i widgetten, vises der en pop op-rude, der viser flere oplysninger om de automatisk videresendte meddelelser:

- **Automatisk videresendte meddelelser ved hjælp af videresendelsesmetoder**:

  - **Efter regler for mailflow**
  - **Efter indbakkeregler**
  - **Ved videresendelse af SMTP**: Denne metode angiver automatisk videresendelse, som administratorer kan konfigurere i en postkasse som beskrevet i [Konfigurer videresendelse af mail for en postkasse](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Et link til [videresendelsesrapporten for at](view-mail-flow-reports.md#forwarding-report) få flere oplysninger.

- **Automatisk videresendte meddelelser af domæner og brugere**:

  - **Top 5-domæner videresendt til**
  - **Nye domæner (sidste uge)**
  - **Top 5-videresendelsesbrugere**
  - **Nye brugere (sidste uge)**
  - Et link til [rapporten Videresendelse af ændringer for at](mfi-new-users-forwarding-email.md#forwarding-modifications-report) få flere oplysninger.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Widgetten Videresendte meddelelser automatisk i Security & Compliance Center" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Insights

Der genereres to indsigter baseret på rapportdataene:

- [Nye brugere videresender mail](mfi-new-users-forwarding-email.md)
- [Nye domæner, der videresendes via mail](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Se også

Du kan få oplysninger om anden indsigt i dashboardet Mailflow under [Mailflowindsigt i Security & Compliance Center](mail-flow-insights-v2.md).
